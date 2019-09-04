---
ms.date: 12/12/2018
keywords: dsc,powershell,configurazione,installazione
title: Uso di Import-DSCResource
ms.openlocfilehash: e1c2c06d756a70c2de516f330e3123235ce740ba
ms.sourcegitcommit: 02eed65c526ef19cf952c2129f280bb5615bf0c8
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 09/03/2019
ms.locfileid: "70215413"
---
# <a name="using-import-dscresource"></a><span data-ttu-id="1272c-103">Uso di Import-DSCResource</span><span class="sxs-lookup"><span data-stu-id="1272c-103">Using Import-DSCResource</span></span>

<span data-ttu-id="1272c-104">`Import-DScResource` è una parola chiave dinamica che può essere usata solo all'interno di un blocco di script di configurazione.</span><span class="sxs-lookup"><span data-stu-id="1272c-104">`Import-DScResource` is a dynamic keyword, which can only be used inside a Configuration script block.</span></span> <span data-ttu-id="1272c-105">La parola chiave `Import-DSCResource` consente di importare le risorse necessarie nella configurazione.</span><span class="sxs-lookup"><span data-stu-id="1272c-105">The `Import-DSCResource` keyword to import any resources needed in your Configuration.</span></span> <span data-ttu-id="1272c-106">Le risorse in `$pshome` vengono importate automaticamente, ma è comunque consigliabile importare in modo esplicito tutte le risorse usate nella [configurazione](Configurations.md).</span><span class="sxs-lookup"><span data-stu-id="1272c-106">Resources under `$pshome` are imported automatically, but it is still considered best practice to explicitly import all resources used in your [Configuration](Configurations.md).</span></span>

<span data-ttu-id="1272c-107">La sintassi per `Import-DSCResource` è illustrata di seguito.</span><span class="sxs-lookup"><span data-stu-id="1272c-107">The syntax for `Import-DSCResource` is shown below.</span></span>  <span data-ttu-id="1272c-108">Quando si specificano moduli in base al nome, è necessario elencarne ognuno in una nuova riga.</span><span class="sxs-lookup"><span data-stu-id="1272c-108">When specifying modules by name, it is a requirement to list each on a new line.</span></span>

```syntax
Import-DscResource [-Name <ResourceName(s)>] [-ModuleName <ModuleName>]
```

|<span data-ttu-id="1272c-109">Parametro</span><span class="sxs-lookup"><span data-stu-id="1272c-109">Parameter</span></span>  |<span data-ttu-id="1272c-110">Description</span><span class="sxs-lookup"><span data-stu-id="1272c-110">Description</span></span>  |
|---------|---------|
|`-Name`|<span data-ttu-id="1272c-111">Nome della risorsa DSC che è necessario importare.</span><span class="sxs-lookup"><span data-stu-id="1272c-111">The DSC resource name(s) that you must import.</span></span> <span data-ttu-id="1272c-112">Se viene specificato il nome del modulo, il comando cerca queste risorse DSC all'interno del modulo; in caso contrario, il comando cerca le risorse DSC in tutti i percorsi delle risorse DSC.</span><span class="sxs-lookup"><span data-stu-id="1272c-112">If the module name is specified, the command searches for these DSC resources within this module; otherwise the command searches the DSC resources in all DSC resource paths.</span></span> <span data-ttu-id="1272c-113">I caratteri jolly sono supportati.</span><span class="sxs-lookup"><span data-stu-id="1272c-113">Wildcards are supported.</span></span>|
|`-ModuleName`|<span data-ttu-id="1272c-114">Nome del modulo o specifica del modulo.</span><span class="sxs-lookup"><span data-stu-id="1272c-114">The module name, or module specification.</span></span>  <span data-ttu-id="1272c-115">Se si specificano risorse per l'importazione da un modulo, il comando tenterà di importare solo queste risorse.</span><span class="sxs-lookup"><span data-stu-id="1272c-115">If you specify resources to import from a module, the command will try to import only those resources.</span></span> <span data-ttu-id="1272c-116">Se si specifica solo il modulo, il comando importa tutte le risorse DSC nel modulo.</span><span class="sxs-lookup"><span data-stu-id="1272c-116">If you specify the module only, the command imports all the DSC resources in the module.</span></span>|

```powershell
Import-DscResource -ModuleName xActiveDirectory;
```

## <a name="example-use-import-dscresource-within-a-configuration"></a><span data-ttu-id="1272c-117">Esempio: Usare Import-DSCResource all'interno di una configurazione</span><span class="sxs-lookup"><span data-stu-id="1272c-117">Example: Use Import-DSCResource within a configuration</span></span>

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
    Import-DSCResource -ModuleName ComputerManagementDsc
...
```

> [!NOTE]
> <span data-ttu-id="1272c-118">Non è consentito specificare più valori per i nomi delle risorse e i nomi dei moduli nello stesso comando.</span><span class="sxs-lookup"><span data-stu-id="1272c-118">Specifying multiple values for Resource names and modules names in same command are not supported.</span></span> <span data-ttu-id="1272c-119">Può verificarsi un comportamento non deterministico sulla risorsa da caricare dal modulo cui nel caso in cui stessa risorsa sia presente in più moduli.</span><span class="sxs-lookup"><span data-stu-id="1272c-119">It can have non-deterministic behavior about which resource to load from which module in case same resource exists in multiple modules.</span></span> <span data-ttu-id="1272c-120">Il comando seguente genererà un errore durante la compilazione.</span><span class="sxs-lookup"><span data-stu-id="1272c-120">Below command will result in error during compilation.</span></span>
>
> ```powershell
> Import-DscResource -Name UserConfigProvider*,TestLogger1 -ModuleName UserConfigProv,PsModuleForTestLogger
> ```

<span data-ttu-id="1272c-121">Aspetti da considerare quando si usa solo il parametro Name:</span><span class="sxs-lookup"><span data-stu-id="1272c-121">Things to consider when using only the Name parameter:</span></span>

- <span data-ttu-id="1272c-122">È un'operazione a elevato utilizzo di risorse in base al numero di moduli installati nel computer.</span><span class="sxs-lookup"><span data-stu-id="1272c-122">It is a resource-intensive operation depending on the number of modules installed on machine.</span></span>
- <span data-ttu-id="1272c-123">Verrà caricata la prima risorsa trovata con il nome specificato.</span><span class="sxs-lookup"><span data-stu-id="1272c-123">It will load the first resource found with the given name.</span></span> <span data-ttu-id="1272c-124">Nel caso in cui sia installata più di una risorsa con lo stesso nome, potrebbe essere caricata la risorsa non corretta.</span><span class="sxs-lookup"><span data-stu-id="1272c-124">In the case where there is more than one resource with same name installed, it could load the wrong resource.</span></span>

<span data-ttu-id="1272c-125">L'utilizzo consigliato consiste nello specificare `–ModuleName` con il parametro `-Name`, come descritto di seguito.</span><span class="sxs-lookup"><span data-stu-id="1272c-125">The recommended usage is to specify `–ModuleName` with the `-Name` parameter, as described below.</span></span>

<span data-ttu-id="1272c-126">Questo utilizzo offre i vantaggi seguenti:</span><span class="sxs-lookup"><span data-stu-id="1272c-126">This usage has the following benefits:</span></span>

- <span data-ttu-id="1272c-127">Riduce l'impatto sulle prestazioni, limitando l'ambito di ricerca per la risorsa specificata.</span><span class="sxs-lookup"><span data-stu-id="1272c-127">It reduces the performance impact by limiting the search scope for the specified resource.</span></span>
- <span data-ttu-id="1272c-128">Definisce in modo esplicito il modulo di definizione della risorsa, garantendo il caricamento della risorsa corretta.</span><span class="sxs-lookup"><span data-stu-id="1272c-128">It explicitly defines the module defining the resource, ensuring the correct resource is loaded.</span></span>

> [!NOTE]
> <span data-ttu-id="1272c-129">In PowerShell 5.0, le risorse DSC possono avere più versioni e possono essere installate in un computer side-by-side.</span><span class="sxs-lookup"><span data-stu-id="1272c-129">In PowerShell 5.0, DSC resources can have multiple versions, and versions can be installed on a computer side-by-side.</span></span> <span data-ttu-id="1272c-130">Questo significa che più versioni di un modulo risorse sono disponibili nella stessa cartella di moduli.</span><span class="sxs-lookup"><span data-stu-id="1272c-130">This is implemented by having multiple versions of a resource module that are contained in the same module folder.</span></span>
> <span data-ttu-id="1272c-131">Per altre informazioni, vedere [Uso di risorse con più versioni](sxsresource.md).</span><span class="sxs-lookup"><span data-stu-id="1272c-131">For more information, see [Using resources with multiple versions](sxsresource.md).</span></span>

## <a name="intellisense-with-import-dscresource"></a><span data-ttu-id="1272c-132">IntelliSense con Import-DSCResource</span><span class="sxs-lookup"><span data-stu-id="1272c-132">Intellisense with Import-DSCResource</span></span>

<span data-ttu-id="1272c-133">Quando si crea la configurazione DSC in ISE, PowerShell fornisce IntelliSense per le risorse e le proprietà delle risorse.</span><span class="sxs-lookup"><span data-stu-id="1272c-133">When authoring the DSC configuration in ISE, PowerShell provides IntelliSence for resources and resource properties.</span></span> <span data-ttu-id="1272c-134">Le definizioni delle risorse nel percorso del modulo `$pshome` vengono caricate automaticamente.</span><span class="sxs-lookup"><span data-stu-id="1272c-134">Resource definitions under the `$pshome` module path are loaded automatically.</span></span> <span data-ttu-id="1272c-135">Quando si importano risorse con la parola chiave `Import-DSCResource`, le definizioni di risorse specificate vengono aggiunte e IntelliSense viene espanso per includere lo schema della risorsa importata.</span><span class="sxs-lookup"><span data-stu-id="1272c-135">When you import resources using the `Import-DSCResource` keyword, the specified resource definitions are added and Intellisense is expanded to include the imported resource's schema.</span></span>

![Risorsa IntelliSense](../media/resource-intellisense.png)

> [!NOTE]
> <span data-ttu-id="1272c-137">A partire da PowerShell 5.0 è stato aggiunto il completamento tramite TAB a ISE per le risorse DSC e le relative proprietà.</span><span class="sxs-lookup"><span data-stu-id="1272c-137">Beginning in PowerShell 5.0, tab completion was added to the ISE for DSC resources and their properties.</span></span> <span data-ttu-id="1272c-138">Per altre informazioni, vedere [Risorse](../resources/resources.md).</span><span class="sxs-lookup"><span data-stu-id="1272c-138">For more information, see [Resources](../resources/resources.md).</span></span>

<span data-ttu-id="1272c-139">In fase di compilazione della configurazione, PowerShell usa le definizioni delle risorse importate per convalidare tutti i blocchi di risorse nella configurazione.</span><span class="sxs-lookup"><span data-stu-id="1272c-139">When compiling the Configuration, PowerShell uses the imported resource definitions to validate all resource blocks in the configuration.</span></span>
<span data-ttu-id="1272c-140">Ogni blocco di risorse viene convalidato tramite definizione dello schema della risorsa per le regole seguenti.</span><span class="sxs-lookup"><span data-stu-id="1272c-140">Each resource block is validated, using the resource's schema definition, for the following rules.</span></span>

- <span data-ttu-id="1272c-141">Vengono usate solo le proprietà definite nello schema.</span><span class="sxs-lookup"><span data-stu-id="1272c-141">Only properties defined in schema are used.</span></span>
- <span data-ttu-id="1272c-142">I tipi di dati per ogni proprietà sono corretti.</span><span class="sxs-lookup"><span data-stu-id="1272c-142">The data types for each property are correct.</span></span>
- <span data-ttu-id="1272c-143">Sono specificate le proprietà delle chiavi.</span><span class="sxs-lookup"><span data-stu-id="1272c-143">Keys properties are specified.</span></span>
- <span data-ttu-id="1272c-144">Non viene usata alcuna proprietà di sola lettura.</span><span class="sxs-lookup"><span data-stu-id="1272c-144">No read-only property is used.</span></span>
- <span data-ttu-id="1272c-145">La convalida sul valore esegue il mapping di tipi.</span><span class="sxs-lookup"><span data-stu-id="1272c-145">Validation on value maps types.</span></span>

<span data-ttu-id="1272c-146">Considerare la configurazione seguente:</span><span class="sxs-lookup"><span data-stu-id="1272c-146">Consider the following configuration:</span></span>

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
            Name = “Telnet-Client”
            Ensure = “Invalid”
        }
    }
}
```

<span data-ttu-id="1272c-147">La compilazione di questa configurazione genera un errore.</span><span class="sxs-lookup"><span data-stu-id="1272c-147">Compiling this Configuration results in an error.</span></span>

```output
PSDesiredStateConfiguration\WindowsFeature: At least one of the values ‘Invalid’ is not supported or valid for property ‘Ensure’ on class ‘WindowsFeature’. Please specify only supported values: Present, Absent.
```

<span data-ttu-id="1272c-148">IntelliSense e la convalida dello schema consentono di rilevare più errori durante le fasi di analisi e compilazione, evitando complicazioni in fase di esecuzione.</span><span class="sxs-lookup"><span data-stu-id="1272c-148">Intellisense and schema validation allow you to catch more errors during parse and compilation time, avoiding complications at run time.</span></span>

> [!NOTE]
> <span data-ttu-id="1272c-149">Ogni risorsa DSC può avere un nome e un **FriendlyName** definito dallo schema della risorsa.</span><span class="sxs-lookup"><span data-stu-id="1272c-149">Each DSC resource can have a name, and a **FriendlyName** defined by the resource's schema.</span></span> <span data-ttu-id="1272c-150">Di seguito sono riportate le prime due righe di "MSFT_ServiceResource.shema.mof".</span><span class="sxs-lookup"><span data-stu-id="1272c-150">Below are the first two lines of "MSFT_ServiceResource.shema.mof".</span></span>
> ```syntax
> [ClassVersion("1.0.0"),FriendlyName("Service")]
> class MSFT_ServiceResource : OMI_BaseResource
> ```
> <span data-ttu-id="1272c-151">Quando si usa questa risorsa in una configurazione, è possibile specificare **MSFT_ServiceResource** o **Service**.</span><span class="sxs-lookup"><span data-stu-id="1272c-151">When using this resource in a Configuration, you can specify **MSFT_ServiceResource** or **Service**.</span></span>

## <a name="powershell-v4-and-v5-differences"></a><span data-ttu-id="1272c-152">Differenze tra PowerShell v4 e v5</span><span class="sxs-lookup"><span data-stu-id="1272c-152">PowerShell v4 and v5 differences</span></span>

<span data-ttu-id="1272c-153">Sussistono varie differenze nell'ambito della creazione di configurazioni in PowerShell 4.0 e PowerShell 5.0 e versioni successive.</span><span class="sxs-lookup"><span data-stu-id="1272c-153">There are multiple differences you see when authoring Configurations in PowerShell 4.0 vs. PowerShell 5.0 and later.</span></span> <span data-ttu-id="1272c-154">Questa sezione evidenzia le differenze pertinenti a questo articolo.</span><span class="sxs-lookup"><span data-stu-id="1272c-154">This section will highlight the differences that you see relevant to this article.</span></span>

### <a name="multiple-resource-versions"></a><span data-ttu-id="1272c-155">Più versioni di risorse</span><span class="sxs-lookup"><span data-stu-id="1272c-155">Multiple Resource Versions</span></span>

<span data-ttu-id="1272c-156">L'installazione e l'utilizzo di più versioni di risorse affiancate non sono supportati in PowerShell 4.0.</span><span class="sxs-lookup"><span data-stu-id="1272c-156">Installing and using multiple versions of resources side by side was not supported in PowerShell 4.0.</span></span> <span data-ttu-id="1272c-157">Se si verificano problemi di importazione delle risorse nella configurazione, assicurarsi di avere solo una versione della risorsa installata.</span><span class="sxs-lookup"><span data-stu-id="1272c-157">If you notice issues importing resources into your Configuration, ensure that you only have one version of the resource installed.</span></span>

<span data-ttu-id="1272c-158">Nell'immagine seguente sono installare due versioni del modulo **xPSDesiredStateConfiguration**.</span><span class="sxs-lookup"><span data-stu-id="1272c-158">In the image below, two versions of the **xPSDesiredStateConfiguration** module are installed.</span></span>

![Più versioni di risorse corrette](../media/multiple-resource-versions-broken.png)

<span data-ttu-id="1272c-160">Copiare il contenuto della versione del modulo desiderata nel livello superiore della directory del modulo.</span><span class="sxs-lookup"><span data-stu-id="1272c-160">Copy the contents of your desired module version to the top level of the module directory.</span></span>

![Più versioni di risorse corrette](../media/multiple-resource-versions-fixed.png)

### <a name="resource-location"></a><span data-ttu-id="1272c-162">Posizione risorsa</span><span class="sxs-lookup"><span data-stu-id="1272c-162">Resource location</span></span>

<span data-ttu-id="1272c-163">Durante la creazione e la compilazione di configurazioni, le risorse possono essere archiviate in qualsiasi directory specificata mediante [PSModulePath](/powershell/developer/module/modifying-the-psmodulepath-installation-path).</span><span class="sxs-lookup"><span data-stu-id="1272c-163">When authoring and compiling Configurations, your resources can be stored in any directory specified by your [PSModulePath](/powershell/developer/module/modifying-the-psmodulepath-installation-path).</span></span> <span data-ttu-id="1272c-164">In PowerShell 4.0, Gestione configurazione locale richiede che tutti i moduli delle risorse DSC siano archiviati in "Programmi\WindowsPowerShell\Modules" o `$pshome\Modules`.</span><span class="sxs-lookup"><span data-stu-id="1272c-164">In PowerShell 4.0, the LCM requires all DSC resource modules to be stored under "Program Files\WindowsPowerShell\Modules" or `$pshome\Modules`.</span></span> <span data-ttu-id="1272c-165">A partire da PowerShell 5.0, questo requisito è stato rimosso e i moduli delle risorse possono essere archiviati in qualsiasi directory specificata mediante `PSModulePath`.</span><span class="sxs-lookup"><span data-stu-id="1272c-165">Beginning in PowerShell 5.0, this requirement was removed, and resource modules can be stored in any directory specified by `PSModulePath`.</span></span>

## <a name="see-also"></a><span data-ttu-id="1272c-166">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="1272c-166">See also</span></span>

- [<span data-ttu-id="1272c-167">Risorse</span><span class="sxs-lookup"><span data-stu-id="1272c-167">Resources</span></span>](../resources/resources.md)
