---
ms.date: 12/12/2018
keywords: dsc,powershell,configurazione,installazione
title: Uso di Import-DSCResource
ms.openlocfilehash: a041169ad557becf7ca87641d9ce5222ee8f6beb
ms.sourcegitcommit: c97dcf1e00ef540e7464c36c88f841474060044c
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 03/15/2020
ms.locfileid: "79402448"
---
# <a name="using-import-dscresource"></a><span data-ttu-id="b9c1c-103">Uso di Import-DSCResource</span><span class="sxs-lookup"><span data-stu-id="b9c1c-103">Using Import-DSCResource</span></span>

<span data-ttu-id="b9c1c-104">`Import-DScResource` è una parola chiave dinamica che può essere usata solo all'interno di un blocco di script di configurazione.</span><span class="sxs-lookup"><span data-stu-id="b9c1c-104">`Import-DScResource` is a dynamic keyword, which can only be used inside a Configuration script block.</span></span> <span data-ttu-id="b9c1c-105">La parola chiave `Import-DSCResource` consente di importare le risorse necessarie nella configurazione.</span><span class="sxs-lookup"><span data-stu-id="b9c1c-105">The `Import-DSCResource` keyword to import any resources needed in your Configuration.</span></span> <span data-ttu-id="b9c1c-106">Le risorse in `$pshome` vengono importate automaticamente, ma è comunque consigliabile importare in modo esplicito tutte le risorse usate nella [configurazione](Configurations.md).</span><span class="sxs-lookup"><span data-stu-id="b9c1c-106">Resources under `$pshome` are imported automatically, but it is still considered best practice to explicitly import all resources used in your [Configuration](Configurations.md).</span></span>

<span data-ttu-id="b9c1c-107">La sintassi per `Import-DSCResource` è illustrata di seguito.</span><span class="sxs-lookup"><span data-stu-id="b9c1c-107">The syntax for `Import-DSCResource` is shown below.</span></span>  <span data-ttu-id="b9c1c-108">Quando si specificano moduli in base al nome, è necessario elencarne ognuno in una nuova riga.</span><span class="sxs-lookup"><span data-stu-id="b9c1c-108">When specifying modules by name, it is a requirement to list each on a new line.</span></span>

```syntax
Import-DscResource [-Name <ResourceName(s)>] [-ModuleName <ModuleName>] [-ModuleVersion <ModuleVersion>]
```

|<span data-ttu-id="b9c1c-109">Parametro</span><span class="sxs-lookup"><span data-stu-id="b9c1c-109">Parameter</span></span>  |<span data-ttu-id="b9c1c-110">Descrizione</span><span class="sxs-lookup"><span data-stu-id="b9c1c-110">Description</span></span>  |
|---------|---------|
|`-Name`|<span data-ttu-id="b9c1c-111">Nome della risorsa DSC che è necessario importare.</span><span class="sxs-lookup"><span data-stu-id="b9c1c-111">The DSC resource name(s) that you must import.</span></span> <span data-ttu-id="b9c1c-112">Se viene specificato il nome del modulo, il comando cerca queste risorse DSC all'interno del modulo; in caso contrario, il comando cerca le risorse DSC in tutti i percorsi delle risorse DSC.</span><span class="sxs-lookup"><span data-stu-id="b9c1c-112">If the module name is specified, the command searches for these DSC resources within this module; otherwise the command searches the DSC resources in all DSC resource paths.</span></span> <span data-ttu-id="b9c1c-113">Sono supportati caratteri jolly.</span><span class="sxs-lookup"><span data-stu-id="b9c1c-113">Wildcards are supported.</span></span>|
|`-ModuleName`|<span data-ttu-id="b9c1c-114">Nome del modulo o specifica del modulo.</span><span class="sxs-lookup"><span data-stu-id="b9c1c-114">The module name, or module specification.</span></span>  <span data-ttu-id="b9c1c-115">Se si specificano risorse per l'importazione da un modulo, il comando tenterà di importare solo queste risorse.</span><span class="sxs-lookup"><span data-stu-id="b9c1c-115">If you specify resources to import from a module, the command will try to import only those resources.</span></span> <span data-ttu-id="b9c1c-116">Se si specifica solo il modulo, il comando importa tutte le risorse DSC nel modulo.</span><span class="sxs-lookup"><span data-stu-id="b9c1c-116">If you specify the module only, the command imports all the DSC resources in the module.</span></span>|
|`-ModuleVersion`|<span data-ttu-id="b9c1c-117">A partire da PowerShell 5,0, è possibile specificare la versione di un modulo che deve essere usata da una configurazione.</span><span class="sxs-lookup"><span data-stu-id="b9c1c-117">Beginning in PowerShell 5.0, you can specify which version of a module a configuration should use.</span></span> <span data-ttu-id="b9c1c-118">Per altre informazioni, vedere [Importare una versione specifica di una risorsa installata](sxsresource.md).</span><span class="sxs-lookup"><span data-stu-id="b9c1c-118">For more information, see [Import a specific version of an installed resource](sxsresource.md).</span></span>|

```powershell
Import-DscResource -ModuleName xActiveDirectory
```

## <a name="example-use-import-dscresource-within-a-configuration"></a><span data-ttu-id="b9c1c-119">Esempio: Usare Import-DSCResource all'interno di una configurazione</span><span class="sxs-lookup"><span data-stu-id="b9c1c-119">Example: Use Import-DSCResource within a configuration</span></span>

```powershell
Configuration MSDSCConfiguration
{
    # Search for and imports Service, File, and Registry from the module PSDesiredStateConfiguration.
    Import-DSCResource -ModuleName PSDesiredStateConfiguration -Name Service, File, Registry

    # Search for and import Resource1 from the module that defines it.
    # If only –Name parameter is used then resources can belong to different PowerShell modules as well.
    # TimeZone resource is from the ComputerManagementDSC module which is not installed by default.
    # As a best practice, list each requirement on a different line if possible.  This makes reviewing
    # multiple changes in source control a bit easier.
    Import-DSCResource -Name File
    Import-DSCResource -Name TimeZone

    # Search for and import all DSC resources inside the module PSDesiredStateConfiguration.
    # When specifying the modulename parameter, it is a requirement to list each on a new line.
    Import-DSCResource -ModuleName PSDesiredStateConfiguration
    # In PowerShell 5.0 and later, you can specify a ModuleVersion parameter
    Import-DSCResource -ModuleName ComputerManagementDsc -ModuleVersion 6.0.0.0
...
```

> [!NOTE]
> <span data-ttu-id="b9c1c-120">Non è consentito specificare più valori per i nomi delle risorse e i nomi dei moduli nello stesso comando.</span><span class="sxs-lookup"><span data-stu-id="b9c1c-120">Specifying multiple values for Resource names and modules names in same command are not supported.</span></span> <span data-ttu-id="b9c1c-121">Può verificarsi un comportamento non deterministico sulla risorsa da caricare dal modulo cui nel caso in cui stessa risorsa sia presente in più moduli.</span><span class="sxs-lookup"><span data-stu-id="b9c1c-121">It can have non-deterministic behavior about which resource to load from which module in case same resource exists in multiple modules.</span></span> <span data-ttu-id="b9c1c-122">Il comando seguente genererà un errore durante la compilazione.</span><span class="sxs-lookup"><span data-stu-id="b9c1c-122">Below command will result in error during compilation.</span></span>
>
> ```powershell
> Import-DscResource -Name UserConfigProvider*,TestLogger1 -ModuleName UserConfigProv,PsModuleForTestLogger
> ```

<span data-ttu-id="b9c1c-123">Aspetti da considerare quando si usa solo il parametro Name:</span><span class="sxs-lookup"><span data-stu-id="b9c1c-123">Things to consider when using only the Name parameter:</span></span>

- <span data-ttu-id="b9c1c-124">È un'operazione a elevato utilizzo di risorse in base al numero di moduli installati nel computer.</span><span class="sxs-lookup"><span data-stu-id="b9c1c-124">It is a resource-intensive operation depending on the number of modules installed on machine.</span></span>
- <span data-ttu-id="b9c1c-125">Verrà caricata la prima risorsa trovata con il nome specificato.</span><span class="sxs-lookup"><span data-stu-id="b9c1c-125">It will load the first resource found with the given name.</span></span> <span data-ttu-id="b9c1c-126">Nel caso in cui sia installata più di una risorsa con lo stesso nome, potrebbe essere caricata la risorsa non corretta.</span><span class="sxs-lookup"><span data-stu-id="b9c1c-126">In the case where there is more than one resource with same name installed, it could load the wrong resource.</span></span>

<span data-ttu-id="b9c1c-127">L'utilizzo consigliato consiste nello specificare `–ModuleName` con il parametro `-Name`, come descritto di seguito.</span><span class="sxs-lookup"><span data-stu-id="b9c1c-127">The recommended usage is to specify `–ModuleName` with the `-Name` parameter, as described below.</span></span>

<span data-ttu-id="b9c1c-128">Questo utilizzo offre i vantaggi seguenti:</span><span class="sxs-lookup"><span data-stu-id="b9c1c-128">This usage has the following benefits:</span></span>

- <span data-ttu-id="b9c1c-129">Riduce l'impatto sulle prestazioni, limitando l'ambito di ricerca per la risorsa specificata.</span><span class="sxs-lookup"><span data-stu-id="b9c1c-129">It reduces the performance impact by limiting the search scope for the specified resource.</span></span>
- <span data-ttu-id="b9c1c-130">Definisce in modo esplicito il modulo di definizione della risorsa, garantendo il caricamento della risorsa corretta.</span><span class="sxs-lookup"><span data-stu-id="b9c1c-130">It explicitly defines the module defining the resource, ensuring the correct resource is loaded.</span></span>

> [!NOTE]
> <span data-ttu-id="b9c1c-131">In PowerShell 5.0, le risorse DSC possono avere più versioni e possono essere installate in un computer side-by-side.</span><span class="sxs-lookup"><span data-stu-id="b9c1c-131">In PowerShell 5.0, DSC resources can have multiple versions, and versions can be installed on a computer side-by-side.</span></span> <span data-ttu-id="b9c1c-132">Questo significa che più versioni di un modulo risorse sono disponibili nella stessa cartella di moduli.</span><span class="sxs-lookup"><span data-stu-id="b9c1c-132">This is implemented by having multiple versions of a resource module that are contained in the same module folder.</span></span>
> <span data-ttu-id="b9c1c-133">Per altre informazioni, vedere [Uso di risorse con più versioni](sxsresource.md).</span><span class="sxs-lookup"><span data-stu-id="b9c1c-133">For more information, see [Using resources with multiple versions](sxsresource.md).</span></span>

## <a name="intellisense-with-import-dscresource"></a><span data-ttu-id="b9c1c-134">IntelliSense con Import-DSCResource</span><span class="sxs-lookup"><span data-stu-id="b9c1c-134">Intellisense with Import-DSCResource</span></span>

<span data-ttu-id="b9c1c-135">Quando si crea la configurazione DSC in ISE, PowerShell fornisce IntelliSense per le risorse e le proprietà delle risorse.</span><span class="sxs-lookup"><span data-stu-id="b9c1c-135">When authoring the DSC configuration in ISE, PowerShell provides IntelliSence for resources and resource properties.</span></span> <span data-ttu-id="b9c1c-136">Le definizioni delle risorse nel percorso del modulo `$pshome` vengono caricate automaticamente.</span><span class="sxs-lookup"><span data-stu-id="b9c1c-136">Resource definitions under the `$pshome` module path are loaded automatically.</span></span> <span data-ttu-id="b9c1c-137">Quando si importano risorse con la parola chiave `Import-DSCResource`, le definizioni di risorse specificate vengono aggiunte e IntelliSense viene espanso per includere lo schema della risorsa importata.</span><span class="sxs-lookup"><span data-stu-id="b9c1c-137">When you import resources using the `Import-DSCResource` keyword, the specified resource definitions are added and Intellisense is expanded to include the imported resource's schema.</span></span>

![Risorsa IntelliSense](media/import-dscresource/resource-intellisense.png)

> [!NOTE]
> <span data-ttu-id="b9c1c-139">A partire da PowerShell 5.0 è stato aggiunto il completamento tramite TAB a ISE per le risorse DSC e le relative proprietà.</span><span class="sxs-lookup"><span data-stu-id="b9c1c-139">Beginning in PowerShell 5.0, tab completion was added to the ISE for DSC resources and their properties.</span></span> <span data-ttu-id="b9c1c-140">Per altre informazioni, vedere [Risorse](../resources/resources.md).</span><span class="sxs-lookup"><span data-stu-id="b9c1c-140">For more information, see [Resources](../resources/resources.md).</span></span>

<span data-ttu-id="b9c1c-141">In fase di compilazione della configurazione, PowerShell usa le definizioni delle risorse importate per convalidare tutti i blocchi di risorse nella configurazione.</span><span class="sxs-lookup"><span data-stu-id="b9c1c-141">When compiling the Configuration, PowerShell uses the imported resource definitions to validate all resource blocks in the configuration.</span></span>
<span data-ttu-id="b9c1c-142">Ogni blocco di risorse viene convalidato tramite definizione dello schema della risorsa per le regole seguenti.</span><span class="sxs-lookup"><span data-stu-id="b9c1c-142">Each resource block is validated, using the resource's schema definition, for the following rules.</span></span>

- <span data-ttu-id="b9c1c-143">Vengono usate solo le proprietà definite nello schema.</span><span class="sxs-lookup"><span data-stu-id="b9c1c-143">Only properties defined in schema are used.</span></span>
- <span data-ttu-id="b9c1c-144">I tipi di dati per ogni proprietà sono corretti.</span><span class="sxs-lookup"><span data-stu-id="b9c1c-144">The data types for each property are correct.</span></span>
- <span data-ttu-id="b9c1c-145">Sono specificate le proprietà delle chiavi.</span><span class="sxs-lookup"><span data-stu-id="b9c1c-145">Keys properties are specified.</span></span>
- <span data-ttu-id="b9c1c-146">Non viene usata alcuna proprietà di sola lettura.</span><span class="sxs-lookup"><span data-stu-id="b9c1c-146">No read-only property is used.</span></span>
- <span data-ttu-id="b9c1c-147">La convalida sul valore esegue il mapping di tipi.</span><span class="sxs-lookup"><span data-stu-id="b9c1c-147">Validation on value maps types.</span></span>

<span data-ttu-id="b9c1c-148">Considerare la configurazione seguente:</span><span class="sxs-lookup"><span data-stu-id="b9c1c-148">Consider the following configuration:</span></span>

```powershell
Configuration SchemaValidationInCorrectEnumValue
{
    # It is best practice to explicitly import all resources used in your Configuration.
    # This includes resources that are imported automatically, like WindowsFeature.
    Import-DSCResource -Name WindowsFeature
    Node localhost
    {
        WindowsFeature ROLE1
        {
            Name = "Telnet-Client"
            Ensure = "Invalid"
        }
    }
}
```

<span data-ttu-id="b9c1c-149">La compilazione di questa configurazione genera un errore.</span><span class="sxs-lookup"><span data-stu-id="b9c1c-149">Compiling this Configuration results in an error.</span></span>

```output
PSDesiredStateConfiguration\WindowsFeature: At least one of the values 'Invalid' is not supported or valid for property 'Ensure' on class 'WindowsFeature'. Please specify only supported values: Present, Absent.
```

<span data-ttu-id="b9c1c-150">IntelliSense e la convalida dello schema consentono di rilevare più errori durante le fasi di analisi e compilazione, evitando complicazioni in fase di esecuzione.</span><span class="sxs-lookup"><span data-stu-id="b9c1c-150">Intellisense and schema validation allow you to catch more errors during parse and compilation time, avoiding complications at run time.</span></span>

> [!NOTE]
> <span data-ttu-id="b9c1c-151">Ogni risorsa DSC può avere un nome e un **FriendlyName** definito dallo schema della risorsa.</span><span class="sxs-lookup"><span data-stu-id="b9c1c-151">Each DSC resource can have a name, and a **FriendlyName** defined by the resource's schema.</span></span> <span data-ttu-id="b9c1c-152">Di seguito sono riportate le prime due righe di "MSFT_ServiceResource.shema.mof".</span><span class="sxs-lookup"><span data-stu-id="b9c1c-152">Below are the first two lines of "MSFT_ServiceResource.shema.mof".</span></span>
> ```syntax
> [ClassVersion("1.0.0"),FriendlyName("Service")]
> class MSFT_ServiceResource : OMI_BaseResource
> ```
> <span data-ttu-id="b9c1c-153">Quando si usa questa risorsa in una configurazione, è possibile specificare **MSFT_ServiceResource** o **Service**.</span><span class="sxs-lookup"><span data-stu-id="b9c1c-153">When using this resource in a Configuration, you can specify **MSFT_ServiceResource** or **Service**.</span></span>

## <a name="powershell-v4-and-v5-differences"></a><span data-ttu-id="b9c1c-154">Differenze tra PowerShell v4 e v5</span><span class="sxs-lookup"><span data-stu-id="b9c1c-154">PowerShell v4 and v5 differences</span></span>

<span data-ttu-id="b9c1c-155">Sussistono varie differenze nell'ambito della creazione di configurazioni in PowerShell 4.0 e PowerShell 5.0 e versioni successive.</span><span class="sxs-lookup"><span data-stu-id="b9c1c-155">There are multiple differences you see when authoring Configurations in PowerShell 4.0 vs. PowerShell 5.0 and later.</span></span> <span data-ttu-id="b9c1c-156">Questa sezione evidenzia le differenze pertinenti a questo articolo.</span><span class="sxs-lookup"><span data-stu-id="b9c1c-156">This section will highlight the differences that you see relevant to this article.</span></span>

### <a name="multiple-resource-versions"></a><span data-ttu-id="b9c1c-157">Più versioni di risorse</span><span class="sxs-lookup"><span data-stu-id="b9c1c-157">Multiple Resource Versions</span></span>

<span data-ttu-id="b9c1c-158">L'installazione e l'utilizzo di più versioni di risorse affiancate non sono supportati in PowerShell 4.0.</span><span class="sxs-lookup"><span data-stu-id="b9c1c-158">Installing and using multiple versions of resources side by side was not supported in PowerShell 4.0.</span></span> <span data-ttu-id="b9c1c-159">Se si verificano problemi di importazione delle risorse nella configurazione, assicurarsi di avere solo una versione della risorsa installata.</span><span class="sxs-lookup"><span data-stu-id="b9c1c-159">If you notice issues importing resources into your Configuration, ensure that you only have one version of the resource installed.</span></span>

<span data-ttu-id="b9c1c-160">Nell'immagine seguente sono installare due versioni del modulo **xPSDesiredStateConfiguration**.</span><span class="sxs-lookup"><span data-stu-id="b9c1c-160">In the image below, two versions of the **xPSDesiredStateConfiguration** module are installed.</span></span>

![Più versioni di risorse corrette](media/import-dscresource/multiple-resource-versions-broken.png)

<span data-ttu-id="b9c1c-162">Copiare il contenuto della versione del modulo desiderata nel livello superiore della directory del modulo.</span><span class="sxs-lookup"><span data-stu-id="b9c1c-162">Copy the contents of your desired module version to the top level of the module directory.</span></span>

![Più versioni di risorse corrette](media/import-dscresource/multiple-resource-versions-fixed.png)

### <a name="resource-location"></a><span data-ttu-id="b9c1c-164">Posizione risorsa</span><span class="sxs-lookup"><span data-stu-id="b9c1c-164">Resource location</span></span>

<span data-ttu-id="b9c1c-165">Durante la creazione e la compilazione di configurazioni, le risorse possono essere archiviate in qualsiasi directory specificata mediante [PSModulePath](/powershell/scripting/developer/module/modifying-the-psmodulepath-installation-path).</span><span class="sxs-lookup"><span data-stu-id="b9c1c-165">When authoring and compiling Configurations, your resources can be stored in any directory specified by your [PSModulePath](/powershell/scripting/developer/module/modifying-the-psmodulepath-installation-path).</span></span> <span data-ttu-id="b9c1c-166">In PowerShell 4.0, Gestione configurazione locale richiede che tutti i moduli delle risorse DSC siano archiviati in "Programmi\WindowsPowerShell\Modules" o `$pshome\Modules`.</span><span class="sxs-lookup"><span data-stu-id="b9c1c-166">In PowerShell 4.0, the LCM requires all DSC resource modules to be stored under "Program Files\WindowsPowerShell\Modules" or `$pshome\Modules`.</span></span> <span data-ttu-id="b9c1c-167">A partire da PowerShell 5.0, questo requisito è stato rimosso e i moduli delle risorse possono essere archiviati in qualsiasi directory specificata mediante `PSModulePath`.</span><span class="sxs-lookup"><span data-stu-id="b9c1c-167">Beginning in PowerShell 5.0, this requirement was removed, and resource modules can be stored in any directory specified by `PSModulePath`.</span></span>

### <a name="moduleversion-added"></a><span data-ttu-id="b9c1c-168">Aggiunta di ModuleVersion</span><span class="sxs-lookup"><span data-stu-id="b9c1c-168">ModuleVersion added</span></span>

<span data-ttu-id="b9c1c-169">A partire da PowerShell 5.0, il parametro `-ModuleVersion` consente di specificare la versione di un modulo da usare all'interno della configurazione.</span><span class="sxs-lookup"><span data-stu-id="b9c1c-169">Beginning in PowerShell 5.0, the `-ModuleVersion` parameter allows you to specify which version of a module to use within your configuration.</span></span>

## <a name="see-also"></a><span data-ttu-id="b9c1c-170">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="b9c1c-170">See also</span></span>

- [<span data-ttu-id="b9c1c-171">Risorse</span><span class="sxs-lookup"><span data-stu-id="b9c1c-171">Resources</span></span>](../resources/resources.md)
