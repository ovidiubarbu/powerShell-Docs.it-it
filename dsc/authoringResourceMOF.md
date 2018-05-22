---
ms.date: 06/12/2017
keywords: dsc,powershell,configurazione,installazione
title: Scrittura di una risorsa DSC personalizzata con MOF
ms.openlocfilehash: 50b5f2eddbac4571f5351b32648d45c54ded167e
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/16/2018
---
# <a name="writing-a-custom-dsc-resource-with-mof"></a>Scrittura di una risorsa DSC personalizzata con MOF

> Si applica a: Windows PowerShell 4.0, Windows PowerShell 5.0

In questo argomento verrà definito lo schema per una risorsa personalizzata di Windows PowerShell DSC (Desired State Configuration) in un file MOF e la risorsa verrà implementata in un file di script di Windows PowerShell. Questa risorsa personalizzata consente di creare e gestire un sito Web.

## <a name="creating-the-mof-schema"></a>Creazione dello schema MOF

Lo schema definisce le proprietà della risorsa che possono essere configurate da uno script di configurazione DSC.

### <a name="folder-structure-for-a-mof-resource"></a>Struttura di cartelle per una risorsa MOF

Per implementare una risorsa DSC personalizzata con uno schema MOF, creare la struttura di cartelle seguente. Lo schema MOF è definito nel file Demo_IISWebsite.schema.mof e lo script di risorsa è definito in Demo_IISWebsite.psm1. Facoltativamente, è possibile creare un file manifesto del modulo (con estensione psd1).

```
$env:ProgramFiles\WindowsPowerShell\Modules (folder)
    |- MyDscResources (folder)
        |- DSCResources (folder)
            |- Demo_IISWebsite (folder)
                |- Demo_IISWebsite.psd1 (file, optional)
                |- Demo_IISWebsite.psm1 (file, required)
                |- Demo_IISWebsite.schema.mof (file, required)
```

Si noti che è necessario creare una cartella denominata DSCResources nella cartella di primo livello e che la cartella per ogni risorsa deve avere lo stesso nome della risorsa.

### <a name="the-contents-of-the-mof-file"></a>Contenuto del file MOF

Di seguito è illustrato un esempio di file MOF che è possibile usare per una risorsa di sito Web personalizzata. Per seguire questo esempio, salvare lo schema in un file e denominare il file *Demo_IISWebsite.schema.mof*.

```
[ClassVersion("1.0.0"), FriendlyName("Website")]
class Demo_IISWebsite : OMI_BaseResource
{
  [Key] string Name;
  [Required] string PhysicalPath;
  [write,ValueMap{"Present", "Absent"},Values{"Present", "Absent"}] string Ensure;
  [write,ValueMap{"Started","Stopped"},Values{"Started", "Stopped"}] string State;
  [write] string Protocol[];
  [write] string BindingInfo[];
  [write] string ApplicationPool;
  [read] string ID;
};
```

Si noti quanto segue in relazione al codice precedente:

* `FriendlyName` definisce il nome che è possibile usare per fare riferimento a questa risorsa personalizzata negli script di configurazione DSC. In questo esempio `Website` equivale al nome descrittivo `Archive` per la risorsa Archive predefinita.
* La classe definita per la risorsa personalizzata deve derivare da `OMI_BaseResource`.
* Il qualificatore di tipo, `[Key]`, in una proprietà indica che questa proprietà identificherà in modo univoco l'istanza di risorsa. È obbligatoria almeno una proprietà `[Key]`.
* Il qualificatore `[Required]` indica che la proprietà è obbligatoria (è necessario specificare un valore in ogni script di configurazione che usa questa risorsa).
* Il qualificatore `[write]` indica che questa proprietà è facoltativa quando si usa la risorsa personalizzata in uno script di configurazione. Il qualificatore `[read]` indica che una proprietà non può essere impostata da una configurazione e serve solo a scopo di creazione di report.
* `Values` limita i valori che possono essere assegnati alla proprietà all'elenco di valori definiti in `ValueMap`. Per altre informazioni, vedere l'articolo relativo ai [qualificatori ValueMap e Value](https://msdn.microsoft.com/library/windows/desktop/aa393965.aspx).
* È consigliabile includere una proprietà denominata `Ensure` con i valori `Present` e `Absent` nella risorsa per mantenere uno stile coerente con le risorse DSC predefinite.
* Assegnare un nome al file di schema per la risorsa personalizzata in base al formato seguente: `classname.schema.mof`, dove `classname` è l'identificatore che segue la parola chiave `class` nella definizione di schema.

### <a name="writing-the-resource-script"></a>Scrittura dello script di risorsa

Lo script di risorsa implementa la logica della risorsa. In questo modulo è necessario includere tre funzioni denominate **Get-TargetResource**, **Set-TargetResource** e **Test-TargetResource**. Tutte e tre le funzioni devono accettare un set di parametri identico al set di proprietà definito nello schema MOF creato per la risorsa. In questo documento il set di proprietà è detto "proprietà della risorsa". Archiviare queste tre funzioni in un file denominato <ResourceName>.psm1. Nell'esempio seguente le funzioni vengono archiviate in un file denominato Demo_IISWebsite.psm1.

> **Nota**: quando si esegue lo stesso script di configurazione nella risorsa più volte, non devono venire generati errori e la risorsa deve rimanere nello stesso stato impostato quando si esegue lo script una sola volta. A tale scopo, verificare che le funzioni **Get-TargetResource** e **Test-TargetResource** non modifichino la risorsa e che richiamando la funzione **Set-TargetResource** più di una volta in una sequenza con gli stessi valori dei parametri si ottenga lo stesso risultato che si ottiene richiamandola una sola volta.

Nell'implementazione della funzione **Get-TargetResource** usare i valori delle proprietà chiave della risorsa forniti come parametri per controllare lo stato dell'istanza di risorsa specificata. Questa funzione deve restituire una tabella hash che elenca tutte le proprietà della risorsa come chiavi e i valori effettivi di queste proprietà come valori corrispondenti. Il codice seguente fornisce un esempio.

```powershell
# DSC uses the Get-TargetResource function to fetch the status of the resource instance specified in the parameters for the target machine
function Get-TargetResource
{
    param
    (
        [ValidateSet("Present", "Absent")]
        [string]$Ensure = "Present",

        [Parameter(Mandatory)]
        [ValidateNotNullOrEmpty()]
        [string]$Name,

        [Parameter(Mandatory)]
        [ValidateNotNullOrEmpty()]
        [string]$PhysicalPath,

        [ValidateSet("Started", "Stopped")]
        [string]$State = "Started",

        [string]$ApplicationPool,

        [string[]]$BindingInfo,

        [string[]]$Protocol
    )

        $getTargetResourceResult = $null;

        <# Insert logic that uses the mandatory parameter values to get the website and assign it to a variable called $Website #>
        <# Set $ensureResult to "Present" if the requested website exists and to "Absent" otherwise #>

        # Add all Website properties to the hash table
        # This simple example assumes that $Website is not null
        $getTargetResourceResult = @{
                                      Name = $Website.Name;
                                        Ensure = $ensureResult;
                                        PhysicalPath = $Website.physicalPath;
                                        State = $Website.state;
                                        ID = $Website.id;
                                        ApplicationPool = $Website.applicationPool;
                                        Protocol = $Website.bindings.Collection.protocol;
                                        Binding = $Website.bindings.Collection.bindingInformation;
                                    }

        $getTargetResourceResult;
}
```

A seconda dei valori specificati per le proprietà della risorsa nello script di configurazione, **Set-TargetResource** deve eseguire una delle operazioni seguenti:

* Creare un nuovo sito Web
* Aggiornare un sito Web esistente
* Eliminare un sito Web esistente

Ciò è illustrato nell'esempio seguente.

```powershell
# The Set-TargetResource function is used to create, delete or configure a website on the target machine.
function Set-TargetResource
{
    [CmdletBinding(SupportsShouldProcess=$true)]
    param
    (
        [ValidateSet("Present", "Absent")]
        [string]$Ensure = "Present",

        [Parameter(Mandatory)]
        [ValidateNotNullOrEmpty()]
        [string]$Name,

        [Parameter(Mandatory)]
        [ValidateNotNullOrEmpty()]
        [string]$PhysicalPath,

        [ValidateSet("Started", "Stopped")]
        [string]$State = "Started",

        [string]$ApplicationPool,

        [string[]]$BindingInfo,

        [string[]]$Protocol
    )

    <# If Ensure is set to "Present" and the website specified in the mandatory input parameters does not exist, then create it using the specified parameter values #>
    <# Else, if Ensure is set to "Present" and the website does exist, then update its properties to match the values provided in the non-mandatory parameter values #>
    <# Else, if Ensure is set to "Absent" and the website does not exist, then do nothing #>
    <# Else, if Ensure is set to "Absent" and the website does exist, then delete the website #>
}
```

Infine, la funzione **Test-TargetResource** deve accettare lo stesso set di parametri di **Get-TargetResource** e **Set-TargetResource**. Nell'implementazione di **Test-TargetResource** controllare lo stato dell'istanza di risorsa specificato nei parametri chiave. Se lo stato effettivo dell'istanza di risorsa non corrisponde ai valori specificati nel set di parametri, restituire **$false**. In caso contrario, restituire **$true**.

Il codice seguente implementa la funzione **Test-TargetResource**.

```powershell
function Test-TargetResource
{
[CmdletBinding()]
[OutputType([System.Boolean])]
param
(
[ValidateSet("Present","Absent")]
[System.String]
$Ensure,

[parameter(Mandatory = $true)]
[System.String]
$Name,

[parameter(Mandatory = $true)]
[System.String]
$PhysicalPath,

[ValidateSet("Started","Stopped")]
[System.String]
$State,

[System.String[]]
$Protocol,

[System.String[]]
$BindingData,

[System.String]
$ApplicationPool
)

#Write-Verbose "Use this cmdlet to deliver information about command processing."

#Write-Debug "Use this cmdlet to write debug information while troubleshooting."


#Include logic to
$result = [System.Boolean]
#Add logic to test whether the website is present and its status mathes the supplied parameter values. If it does, return true. If it does not, return false.
$result
}
```

**Nota**: per semplificare il debug, usare il cmdlet **Write-Verbose** nell'implementazione delle tre funzioni precedenti.
>Questo cmdlet scrive il testo nel flusso di messaggi dettagliati.
>Per impostazione predefinita, il flusso di messaggi dettagliati non viene visualizzato, ma è possibile visualizzarlo modificando il valore della variabile **$VerbosePreference** o usando il parametro **Verbose** nei cmdlet DSC = new.

### <a name="creating-the-module-manifest"></a>Creazione del manifesto del modulo

Usare infine il cmdlet **New-ModuleManifest** per definire un file <ResourceName>.psd1 per il modulo della risorsa personalizzata. Quando si richiama questo cmdlet, fare riferimento al file di modulo di script (con estensione psm1) descritto nella sezione precedente. Includere **Get-TargetResource**, **Set-TargetResource** e **Test-TargetResource** nell'elenco delle funzioni da esportare. Di seguito è riportato un file manifesto di esempio.

```powershell
# Module manifest for module 'Demo.IIS.Website'
#
# Generated on: 1/10/2013
#

@{

# Script module or binary module file associated with this manifest.
# RootModule = ''

# Version number of this module.
ModuleVersion = '1.0'

# ID used to uniquely identify this module
GUID = '6AB5ED33-E923-41d8-A3A4-5ADDA2B301DE'

# Author of this module
Author = 'Contoso'

# Company or vendor of this module
CompanyName = 'Contoso'

# Copyright statement for this module
Copyright = 'Contoso. All rights reserved.'

# Description of the functionality provided by this module
Description = 'This Module is used to support the creation and configuration of IIS Websites through Get, Set and Test API on the DSC managed nodes.'

# Minimum version of the Windows PowerShell engine required by this module
PowerShellVersion = '4.0'

# Minimum version of the common language runtime (CLR) required by this module
CLRVersion = '4.0'

# Modules that must be imported into the global environment prior to importing this module
RequiredModules = @("WebAdministration")

# Modules to import as nested modules of the module specified in RootModule/ModuleToProcess
NestedModules = @("Demo_IISWebsite.psm1")

# Functions to export from this module
FunctionsToExport = @("Get-TargetResource", "Set-TargetResource", "Test-TargetResource")

# Cmdlets to export from this module
#CmdletsToExport = '*'

# HelpInfo URI of this module
# HelpInfoURI = ''
}
```

## <a name="supporting-psdscrunascredential"></a>Supporto di PsDscRunAsCredential

>**Nota:** **PsDscRunAsCredential** è supportato in PowerShell 5.0 e versioni successive.

La proprietà **PsDscRunAsCredential** può essere usata nel blocco di risorsa delle [configurazioni DSC](configurations.md) per specificare che la risorsa deve essere eseguita in un insieme di credenziali specificato.
Per altre informazioni, vedere [Esecuzione di DSC con le credenziali dell'utente](runAsUser.md).

Per accedere al contesto utente dall'interno di una risorsa personalizzata è possibile usare la variabile automatica `$PsDscContext`.

Ad esempio il codice seguente scrive il contesto utente in cui viene eseguita la risorsa nel flusso di output dettagliato:

```powershell
if (PsDscContext.RunAsUser) {
    Write-Verbose "User: $PsDscContext.RunAsUser";
}
```