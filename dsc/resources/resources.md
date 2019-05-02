---
ms.date: 12/12/2018
keywords: dsc,powershell,configurazione,installazione
title: Risorse DSC
ms.openlocfilehash: 1f77b5e6630a2e3de6e1d1a05638f94d2df039ae
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62076637"
---
# <a name="dsc-resources"></a><span data-ttu-id="fd0ee-103">Risorse DSC</span><span class="sxs-lookup"><span data-stu-id="fd0ee-103">DSC Resources</span></span>

><span data-ttu-id="fd0ee-104">Si applica a: Windows PowerShell 4.0, Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="fd0ee-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

<span data-ttu-id="fd0ee-105">Le risorse DSC (Desired State Configuration) forniscono i blocchi predefiniti per una configurazione DSC.</span><span class="sxs-lookup"><span data-stu-id="fd0ee-105">Desired State Configuration (DSC) Resources provide the building blocks for a DSC configuration.</span></span> <span data-ttu-id="fd0ee-106">Una risorsa espone le proprietà che possono essere configurate (schema) e contiene le funzioni di script di PowerShell chiamate da Gestione configurazione locale per assicurare il risultato desiderato.</span><span class="sxs-lookup"><span data-stu-id="fd0ee-106">A resource exposes properties that can be configured (schema) and contains the PowerShell script functions that the Local Configuration Manager (LCM) calls to "make it so".</span></span>

<span data-ttu-id="fd0ee-107">Una risorsa può modellare un elemento generico come un file o uno specifico come un'impostazione del server IIS.</span><span class="sxs-lookup"><span data-stu-id="fd0ee-107">A resource can model something as generic as a file or as specific as an IIS server setting.</span></span>  <span data-ttu-id="fd0ee-108">I gruppi di tali risorse sono combinati in un modulo DSC, che organizza tutti i file necessari in una struttura portatile che include i metadati che permettono di identificare il modo in cui si intende usare le risorse.</span><span class="sxs-lookup"><span data-stu-id="fd0ee-108">Groups of like resources are combined in to a DSC Module, which organizes all the required files in to a structure that is portable and includes metadata to identify how the resources are intended to be used.</span></span>

<span data-ttu-id="fd0ee-109">Ogni risorsa dispone di uno \*schema che determina la sintassi necessaria per usare la risorsa in una [configurazione](../configurations/configurations.md).</span><span class="sxs-lookup"><span data-stu-id="fd0ee-109">Each resource has a \*schema that determines the syntax needed to use the resource in a [Configuration](../configurations/configurations.md).</span></span> <span data-ttu-id="fd0ee-110">Lo schema di una risorsa può essere definito nei modi seguenti:</span><span class="sxs-lookup"><span data-stu-id="fd0ee-110">A resource's schema can be defined in the following ways:</span></span>

- <span data-ttu-id="fd0ee-111">File **'Schema.Mof'**: la maggior parte delle risorse definisce lo *schema* in un file 'schema.mof' con [Managed Object Format](/windows/desktop/wmisdk/managed-object-format--mof-).</span><span class="sxs-lookup"><span data-stu-id="fd0ee-111">**'Schema.Mof'** file: Most resources define their *schema* in a 'schema.mof' file, using [Managed Object Format](/windows/desktop/wmisdk/managed-object-format--mof-).</span></span>
- <span data-ttu-id="fd0ee-112">File **'\<Nome risorsa\>.schema.psm1'**: le [risorse composite](../configurations/compositeConfigs.md) definiscono lo *schema* in un file '<ResourceName>.schema.psm1' file con un [blocco di parametri](/powershell/module/microsoft.powershell.core/about/about_functions?view=powershell-6#functions-with-parameters).</span><span class="sxs-lookup"><span data-stu-id="fd0ee-112">**'\<Resource Name\>.schema.psm1'** file: [Composite Resources](../configurations/compositeConfigs.md) define their *schema* in a '<ResourceName>.schema.psm1' file using a [Parameter Block](/powershell/module/microsoft.powershell.core/about/about_functions?view=powershell-6#functions-with-parameters).</span></span>
- <span data-ttu-id="fd0ee-113">File **'\<Nome risorsa\>.psm1'**: le risorse DSC basate su classe definiscono lo *schema* nella definizione della classe.</span><span class="sxs-lookup"><span data-stu-id="fd0ee-113">**'\<Resource Name\>.psm1'** file: Class based DSC resources define their *schema* in the class definition.</span></span> <span data-ttu-id="fd0ee-114">Gli elementi della sintassi sono contrassegnati come proprietà della classe.</span><span class="sxs-lookup"><span data-stu-id="fd0ee-114">Syntax items are denoted as Class properties.</span></span> <span data-ttu-id="fd0ee-115">Per altre informazioni, vedere [about_Classes](/powershell/module/psdesiredstateconfiguration/about/about_classes_and_dsc).</span><span class="sxs-lookup"><span data-stu-id="fd0ee-115">For more information, see [about_Classes](/powershell/module/psdesiredstateconfiguration/about/about_classes_and_dsc).</span></span>

<span data-ttu-id="fd0ee-116">Per recuperare la sintassi per una risorsa DSC, usare il cmdlet [Get-DSCResource](/powershell/module/PSDesiredStateConfiguration/Get-DscResource) con il parametro `-Syntax`.</span><span class="sxs-lookup"><span data-stu-id="fd0ee-116">To retrieve the syntax for a DSC resource, use the [Get-DSCResource](/powershell/module/PSDesiredStateConfiguration/Get-DscResource) cmdlet with the `-Syntax` parameter.</span></span> <span data-ttu-id="fd0ee-117">Questo utilizzo è simile all'uso di [Get-Command](/powershell/module/microsoft.powershell.core/get-command) con il parametro `-Syntax` per ottenere la sintassi del cmdlet.</span><span class="sxs-lookup"><span data-stu-id="fd0ee-117">This usage is similar to using [Get-Command](/powershell/module/microsoft.powershell.core/get-command) with the `-Syntax` parameter to get cmdlet syntax.</span></span> <span data-ttu-id="fd0ee-118">L'output visualizzato indicherà il modello usato per un blocco di risorse per la risorsa specificata.</span><span class="sxs-lookup"><span data-stu-id="fd0ee-118">The output you see will show the template used for a resource block for the resource you specify.</span></span>

```powershell
Get-DscResource -Syntax Service
```

<span data-ttu-id="fd0ee-119">L'output visualizzato dovrebbe essere simile all'output seguente, anche se la sintassi di questa risorsa potrebbe cambiare in futuro.</span><span class="sxs-lookup"><span data-stu-id="fd0ee-119">The output you see should be similar to the output below, though this resource's syntax could change in the future.</span></span> <span data-ttu-id="fd0ee-120">Come nella sintassi dei cmdlet, le *chiavi* racchiuse tra parentesi quadre sono facoltative.</span><span class="sxs-lookup"><span data-stu-id="fd0ee-120">Like cmdlet syntax, the *keys* seen in square brackets, are optional.</span></span> <span data-ttu-id="fd0ee-121">I tipi specificano il tipo di dati previsto da ogni chiave.</span><span class="sxs-lookup"><span data-stu-id="fd0ee-121">The types specify the type of data each key expects.</span></span>

> [!NOTE]
> <span data-ttu-id="fd0ee-122">La chiave **Ensure** è facoltativa perché l'impostazione predefinita è "Present".</span><span class="sxs-lookup"><span data-stu-id="fd0ee-122">The **Ensure** key is optional because it defaults to "Present".</span></span>

```output
Service [String] #ResourceName
{
    Name = [string]
    [BuiltInAccount = [string]{ LocalService | LocalSystem | NetworkService }]
    [Credential = [PSCredential]]
    [Dependencies = [string[]]]
    [DependsOn = [string[]]]
    [Description = [string]]
    [DisplayName = [string]]
    [Ensure = [string]{ Absent | Present }]
    [Path = [string]]
    [PsDscRunAsCredential = [PSCredential]]
    [StartupType = [string]{ Automatic | Disabled | Manual }]
    [State = [string]{ Running | Stopped }]
}
```

<span data-ttu-id="fd0ee-123">All'interno di una configurazione, un blocco di risorse **Service** potrebbe avere questo aspetto per assicurare (**Ensure**) che il servizio spooler sia in esecuzione.</span><span class="sxs-lookup"><span data-stu-id="fd0ee-123">Inside a Configuration, a **Service** resource block might look like this to **Ensure** that the Spooler service is running.</span></span>

> [!NOTE]
> <span data-ttu-id="fd0ee-124">Prima di usare una risorsa in una configurazione, è necessario importarla tramite [Import-DSCResource](../configurations/import-dscresource.md).</span><span class="sxs-lookup"><span data-stu-id="fd0ee-124">Before using a resource in a Configuration, you must import it using [Import-DSCResource](../configurations/import-dscresource.md).</span></span>

```powershell
Configuration TestConfig
{
    # It is best practice to always directly import resources, even if the resource is a built-in resource.
    Import-DSCResource -Name Service
    Node localhost
    {
        # The name of this resource block, can be anything you choose, as long as it is of type [String] as indicated by the schema.
        Service "Spooler:Running"
        {
            Name = "Spooler"
            State = "Running"
        }
    }
}
```

<span data-ttu-id="fd0ee-125">Le configurazioni possono contenere più istanze dello stesso tipo di risorsa.</span><span class="sxs-lookup"><span data-stu-id="fd0ee-125">Configurations can contain multiple instances of the same resource type.</span></span> <span data-ttu-id="fd0ee-126">Ogni istanza deve essere denominata in modo univoco.</span><span class="sxs-lookup"><span data-stu-id="fd0ee-126">Each instance must be uniquely named.</span></span> <span data-ttu-id="fd0ee-127">Nell'esempio seguente viene aggiunto un secondo blocco di risorse **Service** per configurare il servizio "DHCP".</span><span class="sxs-lookup"><span data-stu-id="fd0ee-127">In the following example, a second **Service** resource block is added to configure the "DHCP" service.</span></span>

```powershell
Configuration TestConfig
{
    # It is best practice to always directly import resources, even if the resource is a built-in resource.
    Import-DSCResource -Name Service
    Node localhost
    {
        # The name of this resource block, can be anything you choose, as long as it is of type [String] as indicated by the schema.
        Service "Spooler:Running"
        {
            Name = "Spooler"
            State = "Running"
        }

        # To configure a second service resource block, add another Service resource block and use a unique name.
        Service "DHCP:Running"
        {
            Name = "DHCP"
            State = "Running"
        }
    }
}
```

> [!NOTE]
> <span data-ttu-id="fd0ee-128">A partire da PowerShell 5.0, è stato aggiunto IntelliSense per DSC.</span><span class="sxs-lookup"><span data-stu-id="fd0ee-128">Beginning in PowerShell 5.0, intellisense was added for DSC.</span></span> <span data-ttu-id="fd0ee-129">Questa nuova funzionalità consente di usare \<TAB\> e \<CTRL+BARRA SPAZIATRICE\> per il completamento automatico dei nomi delle chiavi.</span><span class="sxs-lookup"><span data-stu-id="fd0ee-129">This new feature allows you to use \<TAB\> and \<Ctrl+Space\> to auto-complete key names.</span></span>

![Completamento tramite TAB delle risorse](../media/resource-tabcompletion.png)

## <a name="built-in-resources"></a><span data-ttu-id="fd0ee-131">Risorse predefinite</span><span class="sxs-lookup"><span data-stu-id="fd0ee-131">Built-in resources</span></span>

<span data-ttu-id="fd0ee-132">Oltre alle risorse della community, esistono risorse predefinite per Windows, risorse per Linux e risorse per la dipendenza tra nodi.</span><span class="sxs-lookup"><span data-stu-id="fd0ee-132">In addition to community resources, there are built-in resources for Windows, resources for Linux, and resources for cross-node dependency.</span></span> <span data-ttu-id="fd0ee-133">È possibile usare i passaggi precedenti per determinare la sintassi di queste risorse e come usarle.</span><span class="sxs-lookup"><span data-stu-id="fd0ee-133">You can use the steps above to determine the syntax of these resources and how to use them.</span></span> <span data-ttu-id="fd0ee-134">Le pagine relative a queste risorse sono archiviate in **Riferimento**.</span><span class="sxs-lookup"><span data-stu-id="fd0ee-134">The pages that serve these resources have been archived under **Reference**.</span></span>

<span data-ttu-id="fd0ee-135">Risorse predefinite di Windows</span><span class="sxs-lookup"><span data-stu-id="fd0ee-135">Windows built-in resources</span></span>

* [<span data-ttu-id="fd0ee-136">Risorsa Archive</span><span class="sxs-lookup"><span data-stu-id="fd0ee-136">Archive Resource</span></span>](../reference/resources/windows/archiveResource.md)
* [<span data-ttu-id="fd0ee-137">Risorsa Environment</span><span class="sxs-lookup"><span data-stu-id="fd0ee-137">Environment Resource</span></span>](../reference/resources/windows/environmentResource.md)
* [<span data-ttu-id="fd0ee-138">Risorsa File</span><span class="sxs-lookup"><span data-stu-id="fd0ee-138">File Resource</span></span>](../reference/resources/windows/fileResource.md)
* [<span data-ttu-id="fd0ee-139">Risorsa Group</span><span class="sxs-lookup"><span data-stu-id="fd0ee-139">Group Resource</span></span>](../reference/resources/windows/groupResource.md)
* [<span data-ttu-id="fd0ee-140">Risorsa GroupSet</span><span class="sxs-lookup"><span data-stu-id="fd0ee-140">GroupSet Resource</span></span>](../reference/resources/windows/groupSetResource.md)
* [<span data-ttu-id="fd0ee-141">Risorsa Log</span><span class="sxs-lookup"><span data-stu-id="fd0ee-141">Log Resource</span></span>](../reference/resources/windows/logResource.md)
* [<span data-ttu-id="fd0ee-142">Risorsa Package</span><span class="sxs-lookup"><span data-stu-id="fd0ee-142">Package Resource</span></span>](../reference/resources/windows/packageResource.md)
* [<span data-ttu-id="fd0ee-143">Risorsa ProcessSet</span><span class="sxs-lookup"><span data-stu-id="fd0ee-143">ProcessSet Resource</span></span>](../reference/resources/windows/ProcessSetResource.md)
* [<span data-ttu-id="fd0ee-144">Risorsa Registry</span><span class="sxs-lookup"><span data-stu-id="fd0ee-144">Registry Resource</span></span>](../reference/resources/windows/registryResource.md)
* [<span data-ttu-id="fd0ee-145">Risorsa Script</span><span class="sxs-lookup"><span data-stu-id="fd0ee-145">Script Resource</span></span>](../reference/resources/windows/scriptResource.md)
* [<span data-ttu-id="fd0ee-146">Risorsa Service</span><span class="sxs-lookup"><span data-stu-id="fd0ee-146">Service Resource</span></span>](../reference/resources/windows/serviceResource.md)
* [<span data-ttu-id="fd0ee-147">Risorsa ServiceSet</span><span class="sxs-lookup"><span data-stu-id="fd0ee-147">ServiceSet Resource</span></span>](../reference/resources/windows/serviceSetResource.md)
* [<span data-ttu-id="fd0ee-148">Risorsa User</span><span class="sxs-lookup"><span data-stu-id="fd0ee-148">User Resource</span></span>](../reference/resources/windows/userResource.md)
* [<span data-ttu-id="fd0ee-149">Risorsa WindowsFeature</span><span class="sxs-lookup"><span data-stu-id="fd0ee-149">WindowsFeature Resource</span></span>](../reference/resources/windows/windowsFeatureResource.md)
* [<span data-ttu-id="fd0ee-150">Risorsa WindowsFeatureSet</span><span class="sxs-lookup"><span data-stu-id="fd0ee-150">WindowsFeatureSet Resource</span></span>](../reference/resources/windows/windowsFeatureSetResource.md)
* [<span data-ttu-id="fd0ee-151">Risorsa WindowsOptionalFeature</span><span class="sxs-lookup"><span data-stu-id="fd0ee-151">WindowsOptionalFeature Resource</span></span>](../reference/resources/windows/windowsOptionalFeatureResource.md)
* [<span data-ttu-id="fd0ee-152">Risorsa WindowsOptionalFeatureSet</span><span class="sxs-lookup"><span data-stu-id="fd0ee-152">WindowsOptionalFeatureSet Resource</span></span>](../reference/resources/windows/windowsOptionalFeatureSetResource.md)
* [<span data-ttu-id="fd0ee-153">Risorsa WindowsPackageCabResource</span><span class="sxs-lookup"><span data-stu-id="fd0ee-153">WindowsPackageCabResource Resource</span></span>](../reference/resources/windows/windowsPackageCabResource.md)
* [<span data-ttu-id="fd0ee-154">Risorsa WindowsProcess</span><span class="sxs-lookup"><span data-stu-id="fd0ee-154">WindowsProcess Resource</span></span>](../reference/resources/windows/windowsProcessResource.md)

<span data-ttu-id="fd0ee-155">Risorse [dipendenza tra nodi](../configurations/crossNodeDependencies.md)</span><span class="sxs-lookup"><span data-stu-id="fd0ee-155">[Cross-Node dependency](../configurations/crossNodeDependencies.md) resources</span></span>

* [<span data-ttu-id="fd0ee-156">Risorsa WaitForAll</span><span class="sxs-lookup"><span data-stu-id="fd0ee-156">WaitForAll Resource</span></span>](../reference/resources/windows/waitForAllResource.md)
* [<span data-ttu-id="fd0ee-157">Risorsa WaitForSome</span><span class="sxs-lookup"><span data-stu-id="fd0ee-157">WaitForSome Resource</span></span>](../reference/resources/windows/waitForSomeResource.md)
* [<span data-ttu-id="fd0ee-158">Risorsa WaitForAny</span><span class="sxs-lookup"><span data-stu-id="fd0ee-158">WaitForAny Resource</span></span>](../reference/resources/windows/waitForAnyResource.md)

<span data-ttu-id="fd0ee-159">Risorse di gestione pacchetti</span><span class="sxs-lookup"><span data-stu-id="fd0ee-159">Package Management resources</span></span>

* [<span data-ttu-id="fd0ee-160">Risorsa PackageManagement</span><span class="sxs-lookup"><span data-stu-id="fd0ee-160">PackageManagement Resource</span></span>](../reference/resources/packagemanagement/PackageManagementDscResource.md)
* [<span data-ttu-id="fd0ee-161">Risorsa PackageManagementSource</span><span class="sxs-lookup"><span data-stu-id="fd0ee-161">PackageManagementSource Resource</span></span>](../reference/resources/packagemanagement/PackageManagementSourceDscResource.md)

<span data-ttu-id="fd0ee-162">Risorse di Linux</span><span class="sxs-lookup"><span data-stu-id="fd0ee-162">Linux resources</span></span>

* [<span data-ttu-id="fd0ee-163">Risorsa Archive Linux</span><span class="sxs-lookup"><span data-stu-id="fd0ee-163">Linux Archive Resource</span></span>](../reference/resources/linux/lnxArchiveResource.md)
* [<span data-ttu-id="fd0ee-164">Risorsa Environment Linux</span><span class="sxs-lookup"><span data-stu-id="fd0ee-164">Linux Environment Resource</span></span>](../reference/resources/linux/lnxEnvironmentResource.md)
* [<span data-ttu-id="fd0ee-165">Risorsa FileLine Linux</span><span class="sxs-lookup"><span data-stu-id="fd0ee-165">Linux FileLine Resource</span></span>](../reference/resources/linux/lnxFileLineResource.md)
* [<span data-ttu-id="fd0ee-166">Risorsa File Linux</span><span class="sxs-lookup"><span data-stu-id="fd0ee-166">Linux File Resource</span></span>](../reference/resources/linux/lnxFileResource.md)
* [<span data-ttu-id="fd0ee-167">Risorsa Group Linux</span><span class="sxs-lookup"><span data-stu-id="fd0ee-167">Linux Group Resource</span></span>](../reference/resources/linux/lnxGroupResource.md)
* [<span data-ttu-id="fd0ee-168">Risorsa Package Linux</span><span class="sxs-lookup"><span data-stu-id="fd0ee-168">Linux Package Resource</span></span>](../reference/resources/linux/lnxPackageResource.md)
* [<span data-ttu-id="fd0ee-169">Risorsa Script Linux</span><span class="sxs-lookup"><span data-stu-id="fd0ee-169">Linux Script Resource</span></span>](../reference/resources/linux/lnxScriptResource.md)
* [<span data-ttu-id="fd0ee-170">Risorsa Service Linux</span><span class="sxs-lookup"><span data-stu-id="fd0ee-170">Linux Service Resource</span></span>](../reference/resources/linux/lnxServiceResource.md)
* [<span data-ttu-id="fd0ee-171">Risorsa SshAuthorizedKeys Linux</span><span class="sxs-lookup"><span data-stu-id="fd0ee-171">Linux SshAuthorizedKeys Resource</span></span>](../reference/resources/linux/lnxSshAuthorizedKeysResource.md)
* [<span data-ttu-id="fd0ee-172">Risorsa User Linux</span><span class="sxs-lookup"><span data-stu-id="fd0ee-172">Linux User Resource</span></span>](../reference/resources/linux/lnxUserResource.md)
