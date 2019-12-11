---
ms.date: 06/12/2017
keywords: dsc,powershell,configurazione,installazione
title: Scrittura di una risorsa DSC a istanza singola (procedura consigliata)
ms.openlocfilehash: 4d9e07c6aaa064f808a03d4252e8d352b82183ec
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 12/05/2019
ms.locfileid: "71952818"
---
# <a name="writing-a-single-instance-dsc-resource-best-practice"></a><span data-ttu-id="13a12-103">Scrittura di una risorsa DSC a istanza singola (procedura consigliata)</span><span class="sxs-lookup"><span data-stu-id="13a12-103">Writing a single-instance DSC resource (best practice)</span></span>

><span data-ttu-id="13a12-104">**Nota:** questo argomento illustra una procedura consigliata per la definizione di una risorsa DSC che consenta solo una singola istanza in una configurazione.</span><span class="sxs-lookup"><span data-stu-id="13a12-104">**Note:** This topic describes a best practice for defining a DSC resource that allows only a single instance in a configuration.</span></span> <span data-ttu-id="13a12-105">Attualmente, non esiste una funzionalità DSC predefinita per eseguire questa operazione.</span><span class="sxs-lookup"><span data-stu-id="13a12-105">Currently, there is no built-in DSC feature to do this.</span></span> <span data-ttu-id="13a12-106">La situazione potrebbe cambiare in futuro.</span><span class="sxs-lookup"><span data-stu-id="13a12-106">That might change in the future.</span></span>

<span data-ttu-id="13a12-107">In alcuni casi non si vuole consentire di usare più volte una risorsa in una configurazione.</span><span class="sxs-lookup"><span data-stu-id="13a12-107">There are situations where you don't want to allow a resource to be used multiple times in a configuration.</span></span> <span data-ttu-id="13a12-108">Ad esempio, in un'implementazione precedente della risorsa [xTimeZone](https://github.com/PowerShell/xTimeZone) una configurazione può chiamare la risorsa più volte, impostando il fuso orario su un'impostazione diversa in ogni blocco di risorse:</span><span class="sxs-lookup"><span data-stu-id="13a12-108">For example, in a previous implementation of the [xTimeZone](https://github.com/PowerShell/xTimeZone) resource, a configuration could call the resource multiple times, setting the time zone to a different setting in each resource block:</span></span>

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

<span data-ttu-id="13a12-109">Questo dipende dal funzionamento delle chiavi della risorsa DSC.</span><span class="sxs-lookup"><span data-stu-id="13a12-109">This is because of the way DSC resource keys work.</span></span> <span data-ttu-id="13a12-110">Una risorsa deve avere almeno una proprietà chiave.</span><span class="sxs-lookup"><span data-stu-id="13a12-110">A resource must have at least one key property.</span></span> <span data-ttu-id="13a12-111">L'istanza di una risorsa viene considerata univoca se la combinazione dei valori di tutte le relative proprietà chiave è univoca.</span><span class="sxs-lookup"><span data-stu-id="13a12-111">A resource instance is considered unique if the combination of the values of all of its key properties is unique.</span></span> <span data-ttu-id="13a12-112">Nell'implementazione precedente la risorsa [xTimeZone](https://github.com/PowerShell/xTimeZone) ha una sola proprietà, **TimeZone**, che deve essere necessariamente una chiave.</span><span class="sxs-lookup"><span data-stu-id="13a12-112">In its previous implementation, the [xTimeZone](https://github.com/PowerShell/xTimeZone) resource had only one property--**TimeZone**, which was required to be a key.</span></span> <span data-ttu-id="13a12-113">Per questo motivo, una configurazione come quella illustrata sopra poteva essere compilata ed eseguita senza alcun avviso.</span><span class="sxs-lookup"><span data-stu-id="13a12-113">Because of this, a configuration such as the one above would compile and run without warning.</span></span> <span data-ttu-id="13a12-114">Ogni blocco di risorse **xTimeZone** viene considerato univoco.</span><span class="sxs-lookup"><span data-stu-id="13a12-114">Each of the **xTimeZone** resource blocks is considered unique.</span></span> <span data-ttu-id="13a12-115">Di conseguenza, la configurazione viene applicata ripetutamente al nodo, determinando lo spostamento del fuso orario.</span><span class="sxs-lookup"><span data-stu-id="13a12-115">This would cause the configuration to be repeatedly applied to the node, cycling the timezone back and forth.</span></span>

<span data-ttu-id="13a12-116">Per fare in modo che una configurazione potesse impostare il fuso orario per un nodo di destinazione solo una volta, la risorsa è stata aggiornata per aggiungere una seconda proprietà, **IsSingleInstance**, che è diventata la proprietà chiave.</span><span class="sxs-lookup"><span data-stu-id="13a12-116">To ensure that a configuration could set the time zone for a target node only once, the resource was updated to add a second property, **IsSingleInstance**, that became the key property.</span></span>
<span data-ttu-id="13a12-117">La proprietà **IsSingleInstance** è limitata a un singolo valore, "Yes", tramite **ValueMap**.</span><span class="sxs-lookup"><span data-stu-id="13a12-117">The **IsSingleInstance** was limited to a single value, "Yes" by using a **ValueMap**.</span></span> <span data-ttu-id="13a12-118">Lo schema MOF precedente per la risorsa era:</span><span class="sxs-lookup"><span data-stu-id="13a12-118">The old MOF schema for the resource was:</span></span>

```powershell
[ClassVersion("1.0.0.0"), FriendlyName("xTimeZone")]
class xTimeZone : OMI_BaseResource
{
    [Key, Description("Specifies the TimeZone.")] String TimeZone;
};
```

<span data-ttu-id="13a12-119">Lo schema MOF aggiornato per la risorsa è:</span><span class="sxs-lookup"><span data-stu-id="13a12-119">The updated MOF schema for the resource is:</span></span>

```powershell
[ClassVersion("1.0.0.0"), FriendlyName("xTimeZone")]
class xTimeZone : OMI_BaseResource
{
    [Key, Description("Specifies the resource is a single instance, the value must be 'Yes'"), ValueMap{"Yes"}, Values{"Yes"}] String IsSingleInstance;
    [Required, Description("Specifies the TimeZone.")] String TimeZone;
};
```

<span data-ttu-id="13a12-120">Anche lo script di risorsa è stato aggiornato per usare il nuovo parametro.</span><span class="sxs-lookup"><span data-stu-id="13a12-120">The resource script was also updated to use the new parameter.</span></span> <span data-ttu-id="13a12-121">Ecco come è stato modificato lo script di risorsa:</span><span class="sxs-lookup"><span data-stu-id="13a12-121">Here how the resource script was changed:</span></span>

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
    [CmdletBinding()]
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

    Write-Verbose -Message "Replace the System Time Zone to $TimeZone"
    
    try
    {
        if($CurrentTimeZone -ne $TimeZone)
        {
            Write-Verbose -Verbose "Setting the TimeZone"
            Set-TimeZone -TimeZone $TimeZone
        }
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

<span data-ttu-id="13a12-122">Si noti che la proprietà **TimeZone** non è più una chiave.</span><span class="sxs-lookup"><span data-stu-id="13a12-122">Notice that the **TimeZone** property is no longer a key.</span></span> <span data-ttu-id="13a12-123">Se una configurazione tenta di impostare due volte il fuso orario, usando due blocchi **xTimeZone** diversi con valori **TimeZone** diversi, il tentativo di compilazione della configurazione genererà un errore:</span><span class="sxs-lookup"><span data-stu-id="13a12-123">Now, if a configuration attempts to set the time zone twice (by using two different **xTimeZone** blocks with different **TimeZone** values), attempting to compile the configuration will cause an error:</span></span>

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
