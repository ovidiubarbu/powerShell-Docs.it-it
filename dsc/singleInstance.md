---
ms.date: 2017-06-12
ms.topic: conceptual
keywords: dsc,powershell,configurazione,installazione
title: Scrittura di una risorsa DSC a istanza singola (procedura consigliata)
ms.openlocfilehash: 4510bec5b4600334b845831ec6700da01e1a110c
ms.sourcegitcommit: a444406120e5af4e746cbbc0558fe89a7e78aef6
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/17/2018
---
# <a name="writing-a-single-instance-dsc-resource-best-practice"></a>Scrittura di una risorsa DSC a istanza singola (procedura consigliata)

>**Nota:** questo argomento illustra una procedura consigliata per la definizione di una risorsa DSC che consenta solo una singola istanza in una configurazione. Attualmente, non esiste una funzionalità DSC predefinita per eseguire questa operazione. La situazione potrebbe cambiare in futuro.

In alcuni casi non si vuole consentire di usare più volte una risorsa in una configurazione. Ad esempio, in un'implementazione precedente della risorsa [xTimeZone](https://github.com/PowerShell/xTimeZone) una configurazione può chiamare la risorsa più volte, impostando il fuso orario su un'impostazione diversa in ogni blocco di risorse:

```powershell
Configuration SetTimeZone 
{ 
    Param 
    ( 
        [String[]]$NodeName = $env:COMPUTERNAME 

    ) 

    Import-DSCResource -ModuleName xTimeZone 
 
 
    Node $NodeName 
    { 
         xTimeZone TimeZoneExample 
         { 
        
            TimeZone = 'Eastern Standard Time' 
         } 

         xTimeZone TimeZoneExample2
         {

            TimeZone = 'Pacific Standard Time'

         }        

    } 
} 
```

Questo dipende dal funzionamento delle chiavi della risorsa DSC. Una risorsa deve avere almeno una proprietà chiave. L'istanza di una risorsa viene considerata univoca se la combinazione dei valori di tutte le relative proprietà chiave è univoca. Nell'implementazione precedente la risorsa [xTimeZone](https://github.com/PowerShell/xTimeZone) ha una sola proprietà, **TimeZone**, che deve essere necessariamente una chiave. Per questo motivo, una configurazione come quella illustrata sopra poteva essere compilata ed eseguita senza alcun avviso. Ogni blocco di risorse **xTimeZone** viene considerato univoco. Di conseguenza, la configurazione viene applicata ripetutamente al nodo, determinando lo spostamento del fuso orario.

Per fare in modo che una configurazione potesse impostare il fuso orario per un nodo di destinazione solo una volta, la risorsa è stata aggiornata per aggiungere una seconda proprietà, **IsSingleInstance**, che è diventata la proprietà chiave. La proprietà **IsSingleInstance** è limitata a un singolo valore, "Yes", tramite **ValueMap**. Lo schema MOF precedente per la risorsa era:

```powershell
[ClassVersion("1.0.0.0"), FriendlyName("xTimeZone")]
class xTimeZone : OMI_BaseResource
{
    [Key, Description("Specifies the TimeZone.")] String TimeZone;
};
```

Lo schema MOF aggiornato per la risorsa è:

```powershell
[ClassVersion("1.0.0.0"), FriendlyName("xTimeZone")]
class xTimeZone : OMI_BaseResource
{
    [Key, Description("Specifies the resource is a single instance, the value must be 'Yes'"), ValueMap{"Yes"}, Values{"Yes"}] String IsSingleInstance;
    [Required, Description("Specifies the TimeZone.")] String TimeZone;
};
```

Anche lo script di risorsa è stato aggiornato per usare il nuovo parametro. Ecco lo script di risorsa precedente:

```powershell
function Get-TargetResource
{
    [CmdletBinding()]
    [OutputType([Hashtable])]
    param
    (
        [parameter(Mandatory = $true)]
        [ValidateSet('Yes')]
        [String]
        $IsSingleInstance,

        [parameter(Mandatory = $true)]
        [ValidateNotNullOrEmpty()]
        [String]
        $TimeZone
    )

    #Get the current TimeZone
    $CurrentTimeZone = Get-TimeZone

    $returnValue = @{
        TimeZone = $CurrentTimeZone
        IsSingleInstance = 'Yes'
    }

    #Output the target resource
    $returnValue
}


function Set-TargetResource
{
    [CmdletBinding(SupportsShouldProcess=$true)]
    param
    (
        [parameter(Mandatory = $true)]
        [ValidateSet('Yes')]
        [String]
        $IsSingleInstance,

        [parameter(Mandatory = $true)]
        [ValidateNotNullOrEmpty()]
        [String]
        $TimeZone
    )
    
    #Output the result of Get-TargetResource function.
    $CurrentTimeZone = Get-TimeZone
    
    if($PSCmdlet.ShouldProcess("'$TimeZone'","Replace the System Time Zone"))
    {
        try
        {
            if($CurrentTimeZone -ne $TimeZone)
            {
                Write-Verbose -Verbose "Setting the TimeZone"
                Set-TimeZone -TimeZone $TimeZone}
            else
            {
                Write-Verbose -Verbose "TimeZone already set to $TimeZone"
            }
        }
        catch
        {
            $ErrorMsg = $_.Exception.Message
            Write-Verbose -Verbose $ErrorMsg
        }
    }
}


function Test-TargetResource
{
    [CmdletBinding()]
    [OutputType([Boolean])]
    param
    (
        [parameter(Mandatory = $true)]
        [ValidateSet('Yes')]
        [String]
        $IsSingleInstance, 

        [parameter(Mandatory = $true)]
        [ValidateNotNullOrEmpty()]
        [String]
        $TimeZone
    )

    #Output from Get-TargetResource
    $CurrentTimeZone = Get-TimeZone

    if($TimeZone -eq $CurrentTimeZone)
    {
        return $true
    }
    else
    {
        return $false
    }
}

Function Get-TimeZone {
    [CmdletBinding()]
    param()

    & tzutil.exe /g
}

Function Set-TimeZone {
    [CmdletBinding()]
    param(
        [Parameter(Mandatory=$true)]
        [System.String]
        $TimeZone
    )

    try
    {
        & tzutil.exe /s $TimeZone
    }
    catch
    {
        $ErrorMsg = $_.Exception.Message
        Write-Verbose $ErrorMsg
    }
}

Export-ModuleMember -Function *-TargetResource
```

Si noti che la proprietà **TimeZone** non è più una chiave. Se una configurazione tenta di impostare due volte il fuso orario, usando due blocchi **xTimeZone** diversi con valori **TimeZone** diversi, il tentativo di compilazione della configurazione genererà un errore:

```powershell
Test-ConflictingResources : A conflict was detected between resources '[xTimeZone]TimeZoneExample (::15::10::xTimeZone)' and 
'[xTimeZone]TimeZoneExample2 (::22::10::xTimeZone)' in node 'CONTOSO-CLIENT'. Resources have identical key properties but there are differences in the 
following non-key properties: 'TimeZone'. Values 'Eastern Standard Time' don't match values 'Pacific Standard Time'. Please update these property 
values so that they are identical in both cases.
At line:271 char:9
+         Test-ConflictingResources $keywordName $canonicalizedValue $k ...
+         ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
    + CategoryInfo          : InvalidOperation: (:) [Write-Error], InvalidOperationException
    + FullyQualifiedErrorId : ConflictingDuplicateResource,Test-ConflictingResources
Errors occurred while processing configuration 'SetTimeZone'.
At C:\WINDOWS\system32\WindowsPowerShell\v1.0\Modules\PSDesiredStateConfiguration\PSDesiredStateConfiguration.psm1:3705 char:5
+     throw $ErrorRecord
+     ~~~~~~~~~~~~~~~~~~
    + CategoryInfo          : InvalidOperation: (SetTimeZone:String) [], InvalidOperationException
    + FullyQualifiedErrorId : FailToProcessConfiguration
```
   
