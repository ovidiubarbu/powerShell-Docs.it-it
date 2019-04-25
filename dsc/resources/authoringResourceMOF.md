---
ms.date: 06/12/2017
keywords: dsc,powershell,configurazione,installazione
title: Scrittura di una risorsa DSC personalizzata con MOF
ms.openlocfilehash: f243c3e3297711e6f6346a0f813a9c017fe227c3
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62076736"
---
# <a name="writing-a-custom-dsc-resource-with-mof"></a><span data-ttu-id="7aa2d-103">Scrittura di una risorsa DSC personalizzata con MOF</span><span class="sxs-lookup"><span data-stu-id="7aa2d-103">Writing a custom DSC resource with MOF</span></span>

> <span data-ttu-id="7aa2d-104">Si applica a: Windows PowerShell 4.0, Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="7aa2d-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

<span data-ttu-id="7aa2d-105">In questo argomento verrà definito lo schema per una risorsa personalizzata di Windows PowerShell DSC (Desired State Configuration) in un file MOF e la risorsa verrà implementata in un file di script di Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="7aa2d-105">In this topic, we will define the schema for a Windows PowerShell Desired State Configuration (DSC) custom resource in a MOF file, and implement the resource in a Windows PowerShell script file.</span></span> <span data-ttu-id="7aa2d-106">Questa risorsa personalizzata consente di creare e gestire un sito Web.</span><span class="sxs-lookup"><span data-stu-id="7aa2d-106">This custom resource is for creating and maintaining a web site.</span></span>

## <a name="creating-the-mof-schema"></a><span data-ttu-id="7aa2d-107">Creazione dello schema MOF</span><span class="sxs-lookup"><span data-stu-id="7aa2d-107">Creating the MOF schema</span></span>

<span data-ttu-id="7aa2d-108">Lo schema definisce le proprietà della risorsa che possono essere configurate da uno script di configurazione DSC.</span><span class="sxs-lookup"><span data-stu-id="7aa2d-108">The schema defines the properties of your resource that can be configured by a DSC configuration script.</span></span>

### <a name="folder-structure-for-a-mof-resource"></a><span data-ttu-id="7aa2d-109">Struttura di cartelle per una risorsa MOF</span><span class="sxs-lookup"><span data-stu-id="7aa2d-109">Folder structure for a MOF resource</span></span>

<span data-ttu-id="7aa2d-110">Per implementare una risorsa DSC personalizzata con uno schema MOF, creare la struttura di cartelle seguente.</span><span class="sxs-lookup"><span data-stu-id="7aa2d-110">To implement a DSC custom resource with a MOF schema, create the following folder structure.</span></span> <span data-ttu-id="7aa2d-111">Lo schema MOF è definito nel file Demo_IISWebsite.schema.mof e lo script di risorsa è definito in Demo_IISWebsite.psm1.</span><span class="sxs-lookup"><span data-stu-id="7aa2d-111">The MOF schema is defined in the file Demo_IISWebsite.schema.mof, and the resource script is defined in Demo_IISWebsite.psm1.</span></span> <span data-ttu-id="7aa2d-112">Facoltativamente, è possibile creare un file manifesto del modulo (con estensione psd1).</span><span class="sxs-lookup"><span data-stu-id="7aa2d-112">Optionally, you can create a module manifest (psd1) file.</span></span>

```
$env:ProgramFiles\WindowsPowerShell\Modules (folder)
    |- MyDscResources (folder)
        |- DSCResources (folder)
            |- Demo_IISWebsite (folder)
                |- Demo_IISWebsite.psd1 (file, optional)
                |- Demo_IISWebsite.psm1 (file, required)
                |- Demo_IISWebsite.schema.mof (file, required)
```

<span data-ttu-id="7aa2d-113">Si noti che è necessario creare una cartella denominata DSCResources nella cartella di primo livello e che la cartella per ogni risorsa deve avere lo stesso nome della risorsa.</span><span class="sxs-lookup"><span data-stu-id="7aa2d-113">Note that it is necessary to create a folder named DSCResources under the top-level folder, and that the folder for each resource must have the same name as the resource.</span></span>

### <a name="the-contents-of-the-mof-file"></a><span data-ttu-id="7aa2d-114">Contenuto del file MOF</span><span class="sxs-lookup"><span data-stu-id="7aa2d-114">The contents of the MOF file</span></span>

<span data-ttu-id="7aa2d-115">Di seguito è illustrato un esempio di file MOF che è possibile usare per una risorsa di sito Web personalizzata.</span><span class="sxs-lookup"><span data-stu-id="7aa2d-115">Following is an example MOF file that can be used for a custom website resource.</span></span> <span data-ttu-id="7aa2d-116">Per seguire questo esempio, salvare lo schema in un file e denominare il file *Demo_IISWebsite.schema.mof*.</span><span class="sxs-lookup"><span data-stu-id="7aa2d-116">To follow this example, save this schema to a file, and call the file *Demo_IISWebsite.schema.mof*.</span></span>

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

<span data-ttu-id="7aa2d-117">Si noti quanto segue in relazione al codice precedente:</span><span class="sxs-lookup"><span data-stu-id="7aa2d-117">Note the following about the previous code:</span></span>

* <span data-ttu-id="7aa2d-118">`FriendlyName` definisce il nome che è possibile usare per fare riferimento a questa risorsa personalizzata negli script di configurazione DSC.</span><span class="sxs-lookup"><span data-stu-id="7aa2d-118">`FriendlyName` defines the name you can use to refer to this custom resource in DSC configuration scripts.</span></span> <span data-ttu-id="7aa2d-119">In questo esempio `Website` equivale al nome descrittivo `Archive` per la risorsa Archive predefinita.</span><span class="sxs-lookup"><span data-stu-id="7aa2d-119">In this example, `Website` is equivalent to the friendly name `Archive` for the built-in Archive resource.</span></span>
* <span data-ttu-id="7aa2d-120">La classe definita per la risorsa personalizzata deve derivare da `OMI_BaseResource`.</span><span class="sxs-lookup"><span data-stu-id="7aa2d-120">The class you define for your custom resource must derive from `OMI_BaseResource`.</span></span>
* <span data-ttu-id="7aa2d-121">Il qualificatore di tipo, `[Key]`, in una proprietà indica che questa proprietà identificherà in modo univoco l'istanza di risorsa.</span><span class="sxs-lookup"><span data-stu-id="7aa2d-121">The type qualifier, `[Key]`, on a property indicates that this property will uniquely identify the resource instance.</span></span> <span data-ttu-id="7aa2d-122">È obbligatoria almeno una proprietà `[Key]`.</span><span class="sxs-lookup"><span data-stu-id="7aa2d-122">At least one `[Key]` property is required.</span></span>
* <span data-ttu-id="7aa2d-123">Il qualificatore `[Required]` indica che la proprietà è obbligatoria (è necessario specificare un valore in ogni script di configurazione che usa questa risorsa).</span><span class="sxs-lookup"><span data-stu-id="7aa2d-123">The `[Required]` qualifier indicates that the property is required (a value must be specified in any configuration script that uses this resource).</span></span>
* <span data-ttu-id="7aa2d-124">Il qualificatore `[write]` indica che questa proprietà è facoltativa quando si usa la risorsa personalizzata in uno script di configurazione.</span><span class="sxs-lookup"><span data-stu-id="7aa2d-124">The `[write]` qualifier indicates that this property is optional when using the custom resource in a configuration script.</span></span> <span data-ttu-id="7aa2d-125">Il qualificatore `[read]` indica che una proprietà non può essere impostata da una configurazione e serve solo a scopo di creazione di report.</span><span class="sxs-lookup"><span data-stu-id="7aa2d-125">The `[read]` qualifier indicates that a property cannot be set by a configuration, and is for reporting purposes only.</span></span>
* <span data-ttu-id="7aa2d-126">`Values` limita i valori che possono essere assegnati alla proprietà all'elenco di valori definiti in `ValueMap`.</span><span class="sxs-lookup"><span data-stu-id="7aa2d-126">`Values` restricts the values that can be assigned to the property to the list of values defined in `ValueMap`.</span></span> <span data-ttu-id="7aa2d-127">Per altre informazioni, vedere l'articolo relativo ai [qualificatori ValueMap e Value](/windows/desktop/WmiSdk/value-map).</span><span class="sxs-lookup"><span data-stu-id="7aa2d-127">For more information, see [ValueMap and Value Qualifiers](/windows/desktop/WmiSdk/value-map).</span></span>
* <span data-ttu-id="7aa2d-128">È consigliabile includere una proprietà denominata `Ensure` con i valori `Present` e `Absent` nella risorsa per mantenere uno stile coerente con le risorse DSC predefinite.</span><span class="sxs-lookup"><span data-stu-id="7aa2d-128">Including a property called `Ensure` with values `Present` and `Absent` in your resource is recommended as a way to maintain a consistent style with built-in DSC resources.</span></span>
* <span data-ttu-id="7aa2d-129">Assegnare un nome al file di schema per la risorsa personalizzata in base al formato seguente: `classname.schema.mof`, dove `classname` è l'identificatore che segue la parola chiave `class` nella definizione di schema.</span><span class="sxs-lookup"><span data-stu-id="7aa2d-129">Name the schema file for your custom resource as follows: `classname.schema.mof`, where `classname` is the identifier that follows the `class` keyword in your schema definition.</span></span>

### <a name="writing-the-resource-script"></a><span data-ttu-id="7aa2d-130">Scrittura dello script di risorsa</span><span class="sxs-lookup"><span data-stu-id="7aa2d-130">Writing the resource script</span></span>

<span data-ttu-id="7aa2d-131">Lo script di risorsa implementa la logica della risorsa.</span><span class="sxs-lookup"><span data-stu-id="7aa2d-131">The resource script implements the logic of the resource.</span></span> <span data-ttu-id="7aa2d-132">In questo modulo è necessario includere tre funzioni denominate **Get-TargetResource**, **Set-TargetResource** e **Test-TargetResource**.</span><span class="sxs-lookup"><span data-stu-id="7aa2d-132">In this module, you must include three functions called **Get-TargetResource**, **Set-TargetResource**, and **Test-TargetResource**.</span></span> <span data-ttu-id="7aa2d-133">Tutte e tre le funzioni devono accettare un set di parametri identico al set di proprietà definito nello schema MOF creato per la risorsa.</span><span class="sxs-lookup"><span data-stu-id="7aa2d-133">All three functions must take a parameter set that is identical to the set of properties defined in the MOF schema that you created for your resource.</span></span> <span data-ttu-id="7aa2d-134">In questo documento il set di proprietà è detto "proprietà della risorsa".</span><span class="sxs-lookup"><span data-stu-id="7aa2d-134">In this document, this set of properties is referred to as the “resource properties.”</span></span> <span data-ttu-id="7aa2d-135">Archiviare queste tre funzioni in un file denominato <ResourceName>.psm1.</span><span class="sxs-lookup"><span data-stu-id="7aa2d-135">Store these three functions in a file called <ResourceName>.psm1.</span></span> <span data-ttu-id="7aa2d-136">Nell'esempio seguente le funzioni vengono archiviate in un file denominato Demo_IISWebsite.psm1.</span><span class="sxs-lookup"><span data-stu-id="7aa2d-136">In the following example, the functions are stored in a file called Demo_IISWebsite.psm1.</span></span>

> [!NOTE]
> <span data-ttu-id="7aa2d-137">quando si esegue lo stesso script di configurazione nella risorsa più volte, non devono essere generati errori e la risorsa deve rimanere nello stesso stato impostato quando si esegue lo script una sola volta.</span><span class="sxs-lookup"><span data-stu-id="7aa2d-137">When you run the same configuration script on your resource more than once, you should receive no errors and the resource should remain in the same state as running the script once.</span></span> <span data-ttu-id="7aa2d-138">A tale scopo, verificare che le funzioni **Get-TargetResource** e **Test-TargetResource** non modifichino la risorsa e che richiamando la funzione **Set-TargetResource** più di una volta in una sequenza con gli stessi valori dei parametri si ottenga lo stesso risultato che si ottiene richiamandola una sola volta.</span><span class="sxs-lookup"><span data-stu-id="7aa2d-138">To accomplish this, ensure that your **Get-TargetResource** and **Test-TargetResource** functions leave the resource unchanged, and that invoking the **Set-TargetResource** function more than once in a sequence with the same parameter values is always equivalent to invoking it once.</span></span>

<span data-ttu-id="7aa2d-139">Nell'implementazione della funzione **Get-TargetResource** usare i valori delle proprietà chiave della risorsa forniti come parametri per controllare lo stato dell'istanza di risorsa specificata.</span><span class="sxs-lookup"><span data-stu-id="7aa2d-139">In the **Get-TargetResource** function implementation, use the key resource property values that are provided as parameters to check the status of the specified resource instance.</span></span> <span data-ttu-id="7aa2d-140">Questa funzione deve restituire una tabella hash che elenca tutte le proprietà della risorsa come chiavi e i valori effettivi di queste proprietà come valori corrispondenti.</span><span class="sxs-lookup"><span data-stu-id="7aa2d-140">This function must return a hash table that lists all the resource properties as keys and the actual values of these properties as the corresponding values.</span></span> <span data-ttu-id="7aa2d-141">Il codice seguente fornisce un esempio.</span><span class="sxs-lookup"><span data-stu-id="7aa2d-141">The following code provides an example.</span></span>

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

<span data-ttu-id="7aa2d-142">A seconda dei valori specificati per le proprietà della risorsa nello script di configurazione, **Set-TargetResource** deve eseguire una delle operazioni seguenti:</span><span class="sxs-lookup"><span data-stu-id="7aa2d-142">Depending on the values that are specified for the resource properties in the configuration script, the **Set-TargetResource** must do one of the following:</span></span>

* <span data-ttu-id="7aa2d-143">Creare un nuovo sito Web</span><span class="sxs-lookup"><span data-stu-id="7aa2d-143">Create a new website</span></span>
* <span data-ttu-id="7aa2d-144">Aggiornare un sito Web esistente</span><span class="sxs-lookup"><span data-stu-id="7aa2d-144">Update an existing website</span></span>
* <span data-ttu-id="7aa2d-145">Eliminare un sito Web esistente</span><span class="sxs-lookup"><span data-stu-id="7aa2d-145">Delete an existing website</span></span>

<span data-ttu-id="7aa2d-146">Ciò è illustrato nell'esempio seguente.</span><span class="sxs-lookup"><span data-stu-id="7aa2d-146">The following example illustrates this.</span></span>

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

<span data-ttu-id="7aa2d-147">Infine, la funzione **Test-TargetResource** deve accettare lo stesso set di parametri di **Get-TargetResource** e **Set-TargetResource**.</span><span class="sxs-lookup"><span data-stu-id="7aa2d-147">Finally, the **Test-TargetResource** function must take the same parameter set as **Get-TargetResource** and **Set-TargetResource**.</span></span> <span data-ttu-id="7aa2d-148">Nell'implementazione di **Test-TargetResource** controllare lo stato dell'istanza di risorsa specificato nei parametri chiave.</span><span class="sxs-lookup"><span data-stu-id="7aa2d-148">In your implementation of **Test-TargetResource**, check the status of the resource instance that is specified in the key parameters.</span></span> <span data-ttu-id="7aa2d-149">Se lo stato effettivo dell'istanza di risorsa non corrisponde ai valori specificati nel set di parametri, restituire **$false**.</span><span class="sxs-lookup"><span data-stu-id="7aa2d-149">If the actual status of the resource instance does not match the values specified in the parameter set, return **$false**.</span></span> <span data-ttu-id="7aa2d-150">In caso contrario, restituire **$true**.</span><span class="sxs-lookup"><span data-stu-id="7aa2d-150">Otherwise, return **$true**.</span></span>

<span data-ttu-id="7aa2d-151">Il codice seguente implementa la funzione **Test-TargetResource**.</span><span class="sxs-lookup"><span data-stu-id="7aa2d-151">The following code implements the **Test-TargetResource** function.</span></span>

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

<span data-ttu-id="7aa2d-152">**Nota**: per semplificare il debug, usare il cmdlet **Write-Verbose** nell'implementazione delle tre funzioni precedenti.</span><span class="sxs-lookup"><span data-stu-id="7aa2d-152">**Note**: For easier debugging, use the **Write-Verbose** cmdlet in your implementation of the previous three functions.</span></span>
><span data-ttu-id="7aa2d-153">Questo cmdlet scrive il testo nel flusso di messaggi dettagliati.</span><span class="sxs-lookup"><span data-stu-id="7aa2d-153">This cmdlet writes text to the verbose message stream.</span></span>
><span data-ttu-id="7aa2d-154">Per impostazione predefinita, il flusso di messaggi dettagliati non viene visualizzato, ma è possibile visualizzarlo modificando il valore della variabile **$VerbosePreference** o usando il parametro **Verbose** nei cmdlet DSC = new.</span><span class="sxs-lookup"><span data-stu-id="7aa2d-154">By default, the verbose message stream is not displayed, but you can display it by changing the value of the **$VerbosePreference** variable or by using the **Verbose** parameter in the DSC cmdlets = new.</span></span>

### <a name="creating-the-module-manifest"></a><span data-ttu-id="7aa2d-155">Creazione del manifesto del modulo</span><span class="sxs-lookup"><span data-stu-id="7aa2d-155">Creating the module manifest</span></span>

<span data-ttu-id="7aa2d-156">Usare infine il cmdlet **New-ModuleManifest** per definire un file <ResourceName>.psd1 per il modulo della risorsa personalizzata.</span><span class="sxs-lookup"><span data-stu-id="7aa2d-156">Finally, use the **New-ModuleManifest** cmdlet to define a <ResourceName>.psd1 file for your custom resource module.</span></span> <span data-ttu-id="7aa2d-157">Quando si richiama questo cmdlet, fare riferimento al file di modulo di script (con estensione psm1) descritto nella sezione precedente.</span><span class="sxs-lookup"><span data-stu-id="7aa2d-157">When you invoke this cmdlet, reference the script module (.psm1) file described in the previous section.</span></span> <span data-ttu-id="7aa2d-158">Includere **Get-TargetResource**, **Set-TargetResource** e **Test-TargetResource** nell'elenco delle funzioni da esportare.</span><span class="sxs-lookup"><span data-stu-id="7aa2d-158">Include **Get-TargetResource**, **Set-TargetResource**, and **Test-TargetResource** in the list of functions to export.</span></span> <span data-ttu-id="7aa2d-159">Di seguito è riportato un file manifesto di esempio.</span><span class="sxs-lookup"><span data-stu-id="7aa2d-159">Following is an example manifest file.</span></span>

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

## <a name="supporting-psdscrunascredential"></a><span data-ttu-id="7aa2d-160">Supporto di PsDscRunAsCredential</span><span class="sxs-lookup"><span data-stu-id="7aa2d-160">Supporting PsDscRunAsCredential</span></span>

><span data-ttu-id="7aa2d-161">**Nota:** **PsDscRunAsCredential** è supportato in PowerShell 5.0 e versioni successive.</span><span class="sxs-lookup"><span data-stu-id="7aa2d-161">**Note:** **PsDscRunAsCredential** is supported in PowerShell 5.0 and later.</span></span>

<span data-ttu-id="7aa2d-162">La proprietà **PsDscRunAsCredential** può essere usata nel blocco di risorsa delle [configurazioni DSC](../configurations/configurations.md) per specificare che la risorsa deve essere eseguita in un insieme di credenziali specificato.</span><span class="sxs-lookup"><span data-stu-id="7aa2d-162">The **PsDscRunAsCredential** property can be used in [DSC configurations](../configurations/configurations.md) resource block to specify that the resource should be run under a specified set of credentials.</span></span>
<span data-ttu-id="7aa2d-163">Per altre informazioni, vedere [Esecuzione di DSC con le credenziali dell'utente](../configurations/runAsUser.md).</span><span class="sxs-lookup"><span data-stu-id="7aa2d-163">For more information, see [Running DSC with user credentials](../configurations/runAsUser.md).</span></span>

<span data-ttu-id="7aa2d-164">Per accedere al contesto utente dall'interno di una risorsa personalizzata è possibile usare la variabile automatica `$PsDscContext`.</span><span class="sxs-lookup"><span data-stu-id="7aa2d-164">To access the user context from within a custom resource, you can use the automatic variable `$PsDscContext`.</span></span>

<span data-ttu-id="7aa2d-165">Ad esempio il codice seguente scrive il contesto utente in cui viene eseguita la risorsa nel flusso di output dettagliato:</span><span class="sxs-lookup"><span data-stu-id="7aa2d-165">For example the following code would write the user context under which the resource is running to the verbose output stream:</span></span>

```powershell
if (PsDscContext.RunAsUser) {
    Write-Verbose "User: $PsDscContext.RunAsUser";
}
```

## <a name="rebooting-the-node"></a><span data-ttu-id="7aa2d-166">Riavvio del nodo</span><span class="sxs-lookup"><span data-stu-id="7aa2d-166">Rebooting the Node</span></span>

<span data-ttu-id="7aa2d-167">Se le azioni eseguite nella funzione `Set-TargetResource` richiedono un riavvio, è possibile usare il flag globale per indicare alla Gestione configurazione locale di riavviare il nodo.</span><span class="sxs-lookup"><span data-stu-id="7aa2d-167">If the actions taken in your `Set-TargetResource` function require a reboot, you can use a global flag to tell the LCM to reboot the Node.</span></span> <span data-ttu-id="7aa2d-168">Il riavvio avviene direttamente dopo che la funzione `Set-TargetResource` è stata completata.</span><span class="sxs-lookup"><span data-stu-id="7aa2d-168">This reboot occurs directly after the `Set-TargetResource` function completes.</span></span>

<span data-ttu-id="7aa2d-169">All'interno della funzione `Set-TargetResource` aggiungere la riga di codice seguente.</span><span class="sxs-lookup"><span data-stu-id="7aa2d-169">Inside your `Set-TargetResource` function, add the following line of code.</span></span>

```powershell
# Include this line if the resource requires a system reboot.
$global:DSCMachineStatus = 1
```

<span data-ttu-id="7aa2d-170">Affinché la Gestione configurazione locale riavvi il nodo, è necessario che il flag **RebootNodeIfNeeded** sia impostato su `$true`.</span><span class="sxs-lookup"><span data-stu-id="7aa2d-170">In order for the LCM to reboot the Node, the **RebootNodeIfNeeded** flag needs to be set to `$true`.</span></span> <span data-ttu-id="7aa2d-171">È anche necessario che l'opzione **ActionAfterReboot** sia impostata sul valore predefinito **ContinueConfiguration**.</span><span class="sxs-lookup"><span data-stu-id="7aa2d-171">The **ActionAfterReboot** setting should also be set to **ContinueConfiguration**, which is the default.</span></span> <span data-ttu-id="7aa2d-172">Per altre informazioni sulla configurazione della Gestione configurazione locale, vedere [Configurazione di Gestione configurazione locale](../managing-nodes/metaConfig.md) o [Configurazione di Gestione configurazione locale (v4)](../managing-nodes/metaConfig4.md).</span><span class="sxs-lookup"><span data-stu-id="7aa2d-172">For more information on configuring the LCM, see [Configuring the Local Configuration Manager](../managing-nodes/metaConfig.md), or [Configuring the Local Configuration Manager (v4)](../managing-nodes/metaConfig4.md).</span></span>
