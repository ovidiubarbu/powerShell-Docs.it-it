---
ms.date: 02/28/2020
keywords: dsc,powershell,configurazione,installazione
title: Risorse DSC
ms.openlocfilehash: 863898d910cc3c75c3e5977a5b6b0657ba7ed512
ms.sourcegitcommit: 01c60c0c97542dbad48ae34339cddbd813f1353b
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 03/04/2020
ms.locfileid: "78278248"
---
# <a name="dsc-resources"></a><span data-ttu-id="44cba-103">Risorse DSC</span><span class="sxs-lookup"><span data-stu-id="44cba-103">DSC Resources</span></span>

> <span data-ttu-id="44cba-104">Si applica a Windows PowerShell 4.0 e versioni successive.</span><span class="sxs-lookup"><span data-stu-id="44cba-104">Applies to Windows PowerShell 4.0 and up.</span></span>

## <a name="overview"></a><span data-ttu-id="44cba-105">Panoramica</span><span class="sxs-lookup"><span data-stu-id="44cba-105">Overview</span></span>

<span data-ttu-id="44cba-106">Le risorse DSC (Desired State Configuration) forniscono i blocchi predefiniti per una configurazione DSC.</span><span class="sxs-lookup"><span data-stu-id="44cba-106">Desired State Configuration (DSC) Resources provide the building blocks for a DSC configuration.</span></span> <span data-ttu-id="44cba-107">Una risorsa espone le proprietà che possono essere configurate (schema) e contiene le funzioni di script di PowerShell chiamate da Gestione configurazione locale per assicurare il risultato desiderato.</span><span class="sxs-lookup"><span data-stu-id="44cba-107">A resource exposes properties that can be configured (schema) and contains the PowerShell script functions that the Local Configuration Manager (LCM) calls to "make it so".</span></span>

<span data-ttu-id="44cba-108">Una risorsa può modellare un elemento generico come un file o uno specifico come un'impostazione del server IIS.</span><span class="sxs-lookup"><span data-stu-id="44cba-108">A resource can model something as generic as a file or as specific as an IIS server setting.</span></span> <span data-ttu-id="44cba-109">I gruppi di tali risorse sono combinati in un modulo DSC, che organizza tutti i file necessari in una struttura portatile che include i metadati che permettono di identificare il modo in cui si intende usare le risorse.</span><span class="sxs-lookup"><span data-stu-id="44cba-109">Groups of like resources are combined in to a DSC Module, which organizes all the required files in to a structure that is portable and includes metadata to identify how the resources are intended to be used.</span></span>

<span data-ttu-id="44cba-110">Ogni risorsa dispone di uno \*schema che determina la sintassi necessaria per usare la risorsa in una [configurazione](../configurations/configurations.md).</span><span class="sxs-lookup"><span data-stu-id="44cba-110">Each resource has a \*schema that determines the syntax needed to use the resource in a [Configuration](../configurations/configurations.md).</span></span>
<span data-ttu-id="44cba-111">Lo schema di una risorsa può essere definito nei modi seguenti:</span><span class="sxs-lookup"><span data-stu-id="44cba-111">A resource's schema can be defined in the following ways:</span></span>

- <span data-ttu-id="44cba-112">File **'Schema.Mof'** : la maggior parte delle risorse definisce lo _schema_ in un file 'schema.mof' con [Managed Object Format](/windows/desktop/wmisdk/managed-object-format--mof-).</span><span class="sxs-lookup"><span data-stu-id="44cba-112">**'Schema.Mof'** file: Most resources define their _schema_ in a 'schema.mof' file, using [Managed Object Format](/windows/desktop/wmisdk/managed-object-format--mof-).</span></span>
- <span data-ttu-id="44cba-113">File **'\<Nome risorsa\>.schema.psm1'** : le [risorse composite](../configurations/compositeConfigs.md) definiscono lo *schema* in un file '<ResourceName>.schema.psm1' file con un [blocco di parametri](/powershell/module/microsoft.powershell.core/about/about_functions?view=powershell-6#functions-with-parameters).</span><span class="sxs-lookup"><span data-stu-id="44cba-113">**'\<Resource Name\>.schema.psm1'** file: [Composite Resources](../configurations/compositeConfigs.md) define their *schema* in a '<ResourceName>.schema.psm1' file using a [Parameter Block](/powershell/module/microsoft.powershell.core/about/about_functions?view=powershell-6#functions-with-parameters).</span></span>
- <span data-ttu-id="44cba-114">File **'\<Nome risorsa\>.psm1'** : le risorse DSC basate su classe definiscono lo _schema_ nella definizione della classe.</span><span class="sxs-lookup"><span data-stu-id="44cba-114">**'\<Resource Name\>.psm1'** file: Class based DSC resources define their _schema_ in the class definition.</span></span> <span data-ttu-id="44cba-115">Gli elementi della sintassi sono contrassegnati come proprietà della classe.</span><span class="sxs-lookup"><span data-stu-id="44cba-115">Syntax items are denoted as Class properties.</span></span> <span data-ttu-id="44cba-116">Per altre informazioni, vedere [about_Classes](/powershell/module/psdesiredstateconfiguration/about/about_classes_and_dsc).</span><span class="sxs-lookup"><span data-stu-id="44cba-116">For more information, see [about_Classes](/powershell/module/psdesiredstateconfiguration/about/about_classes_and_dsc).</span></span>

<span data-ttu-id="44cba-117">Per recuperare la sintassi per una risorsa DSC, usare il cmdlet [Get-DSCResource](/powershell/module/PSDesiredStateConfiguration/Get-DscResource) con il parametro `-Syntax`.</span><span class="sxs-lookup"><span data-stu-id="44cba-117">To retrieve the syntax for a DSC resource, use the [Get-DSCResource](/powershell/module/PSDesiredStateConfiguration/Get-DscResource) cmdlet with the `-Syntax` parameter.</span></span> <span data-ttu-id="44cba-118">Questo utilizzo è simile all'uso di [Get-Command](/powershell/module/microsoft.powershell.core/get-command) con il parametro `-Syntax` per ottenere la sintassi del cmdlet.</span><span class="sxs-lookup"><span data-stu-id="44cba-118">This usage is similar to using [Get-Command](/powershell/module/microsoft.powershell.core/get-command) with the `-Syntax` parameter to get cmdlet syntax.</span></span> <span data-ttu-id="44cba-119">L'output visualizzato indicherà il modello usato per un blocco di risorse per la risorsa specificata.</span><span class="sxs-lookup"><span data-stu-id="44cba-119">The output you see will show the template used for a resource block for the resource you specify.</span></span>

```powershell
Get-DscResource -Syntax Service
```

<span data-ttu-id="44cba-120">L'output visualizzato dovrebbe essere simile all'output seguente, anche se la sintassi di questa risorsa potrebbe cambiare in futuro.</span><span class="sxs-lookup"><span data-stu-id="44cba-120">The output you see should be similar to the output below, though this resource's syntax could change in the future.</span></span> <span data-ttu-id="44cba-121">Come nella sintassi dei cmdlet, le _chiavi_ racchiuse tra parentesi quadre sono facoltative.</span><span class="sxs-lookup"><span data-stu-id="44cba-121">Like cmdlet syntax, the _keys_ seen in square brackets, are optional.</span></span> <span data-ttu-id="44cba-122">I tipi specificano il tipo di dati previsto da ogni chiave.</span><span class="sxs-lookup"><span data-stu-id="44cba-122">The types specify the type of data each key expects.</span></span>

> [!NOTE]
> <span data-ttu-id="44cba-123">La chiave **Ensure** è facoltativa perché l'impostazione predefinita è "Present".</span><span class="sxs-lookup"><span data-stu-id="44cba-123">The **Ensure** key is optional because it defaults to "Present".</span></span>

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

<span data-ttu-id="44cba-124">All'interno di una configurazione, un blocco di risorse **Service** potrebbe avere questo aspetto per assicurare (**Ensure**) che il servizio spooler sia in esecuzione.</span><span class="sxs-lookup"><span data-stu-id="44cba-124">Inside a Configuration, a **Service** resource block might look like this to **Ensure** that the Spooler service is running.</span></span>

> [!NOTE]
> <span data-ttu-id="44cba-125">Prima di usare una risorsa in una configurazione, è necessario importarla tramite [Import-DSCResource](../configurations/import-dscresource.md).</span><span class="sxs-lookup"><span data-stu-id="44cba-125">Before using a resource in a Configuration, you must import it using [Import-DSCResource](../configurations/import-dscresource.md).</span></span>

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

<span data-ttu-id="44cba-126">Le configurazioni possono contenere più istanze dello stesso tipo di risorsa.</span><span class="sxs-lookup"><span data-stu-id="44cba-126">Configurations can contain multiple instances of the same resource type.</span></span> <span data-ttu-id="44cba-127">Ogni istanza deve essere denominata in modo univoco.</span><span class="sxs-lookup"><span data-stu-id="44cba-127">Each instance must be uniquely named.</span></span> <span data-ttu-id="44cba-128">Nell'esempio seguente viene aggiunto un secondo blocco di risorse **Service** per configurare il servizio "DHCP".</span><span class="sxs-lookup"><span data-stu-id="44cba-128">In the following example, a second **Service** resource block is added to configure the "DHCP" service.</span></span>

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
> <span data-ttu-id="44cba-129">A partire da PowerShell 5.0, è stato aggiunto IntelliSense per DSC.</span><span class="sxs-lookup"><span data-stu-id="44cba-129">Beginning in PowerShell 5.0, intellisense was added for DSC.</span></span> <span data-ttu-id="44cba-130">Questa nuova funzionalità consente di usare <kbd>TAB</kbd> e <kbd>CTRL</kbd>+<kbd>BARRA SPAZIATRICE</kbd> per il completamento automatico dei nomi delle chiavi.</span><span class="sxs-lookup"><span data-stu-id="44cba-130">This new feature allows you to use <kbd>TAB</kbd> and <kbd>Ctr</kbd>+<kbd>Space</kbd> to auto-complete key names.</span></span>

![Completamento tramite TAB delle risorse](media/resources/resource-tabcompletion.png)

## <a name="types-of-resources"></a><span data-ttu-id="44cba-132">Tipi di risorse</span><span class="sxs-lookup"><span data-stu-id="44cba-132">Types of resources</span></span>

<span data-ttu-id="44cba-133">Windows include risorse predefinite e Linux ha risorse specifiche del sistema operativo.</span><span class="sxs-lookup"><span data-stu-id="44cba-133">Windows comes with built in resources and Linux has OS specific resources.</span></span> <span data-ttu-id="44cba-134">Sono disponibili risorse per le [dipendenze tra nodi](../configurations/crossNodeDependencies.md), risorse di gestione dei pacchetti, nonché [risorse gestite e di proprietà della community](https://github.com/dsccommunity).</span><span class="sxs-lookup"><span data-stu-id="44cba-134">There are resources for [cross-node dependencies](../configurations/crossNodeDependencies.md), package management resources, as well as[community owned and maintained resources](https://github.com/dsccommunity).</span></span> <span data-ttu-id="44cba-135">È possibile usare i passaggi precedenti per determinare la sintassi di queste risorse e come usarle.</span><span class="sxs-lookup"><span data-stu-id="44cba-135">You can use the above steps to determine the syntax of these resources and how to use them.</span></span> <span data-ttu-id="44cba-136">Le pagine relative a queste risorse sono archiviate in **Riferimento**.</span><span class="sxs-lookup"><span data-stu-id="44cba-136">The pages that serve these resources have been archived under **Reference**.</span></span>

### <a name="windows-built-in-resources"></a><span data-ttu-id="44cba-137">Risorse predefinite di Windows</span><span class="sxs-lookup"><span data-stu-id="44cba-137">Windows built-in resources</span></span>

- [<span data-ttu-id="44cba-138">Risorsa Archive</span><span class="sxs-lookup"><span data-stu-id="44cba-138">Archive Resource</span></span>](../reference/resources/windows/archiveResource.md)
- [<span data-ttu-id="44cba-139">Risorsa Environment</span><span class="sxs-lookup"><span data-stu-id="44cba-139">Environment Resource</span></span>](../reference/resources/windows/environmentResource.md)
- [<span data-ttu-id="44cba-140">Risorsa File</span><span class="sxs-lookup"><span data-stu-id="44cba-140">File Resource</span></span>](../reference/resources/windows/fileResource.md)
- [<span data-ttu-id="44cba-141">Risorsa Group</span><span class="sxs-lookup"><span data-stu-id="44cba-141">Group Resource</span></span>](../reference/resources/windows/groupResource.md)
- [<span data-ttu-id="44cba-142">Risorsa GroupSet</span><span class="sxs-lookup"><span data-stu-id="44cba-142">GroupSet Resource</span></span>](../reference/resources/windows/groupSetResource.md)
- [<span data-ttu-id="44cba-143">Risorsa Log</span><span class="sxs-lookup"><span data-stu-id="44cba-143">Log Resource</span></span>](../reference/resources/windows/logResource.md)
- [<span data-ttu-id="44cba-144">Risorsa Package</span><span class="sxs-lookup"><span data-stu-id="44cba-144">Package Resource</span></span>](../reference/resources/windows/packageResource.md)
- [<span data-ttu-id="44cba-145">Risorsa ProcessSet</span><span class="sxs-lookup"><span data-stu-id="44cba-145">ProcessSet Resource</span></span>](../reference/resources/windows/ProcessSetResource.md)
- [<span data-ttu-id="44cba-146">Risorsa Registry</span><span class="sxs-lookup"><span data-stu-id="44cba-146">Registry Resource</span></span>](../reference/resources/windows/registryResource.md)
- [<span data-ttu-id="44cba-147">Risorsa Script</span><span class="sxs-lookup"><span data-stu-id="44cba-147">Script Resource</span></span>](../reference/resources/windows/scriptResource.md)
- [<span data-ttu-id="44cba-148">Risorsa Service</span><span class="sxs-lookup"><span data-stu-id="44cba-148">Service Resource</span></span>](../reference/resources/windows/serviceResource.md)
- [<span data-ttu-id="44cba-149">Risorsa ServiceSet</span><span class="sxs-lookup"><span data-stu-id="44cba-149">ServiceSet Resource</span></span>](../reference/resources/windows/serviceSetResource.md)
- [<span data-ttu-id="44cba-150">Risorsa User</span><span class="sxs-lookup"><span data-stu-id="44cba-150">User Resource</span></span>](../reference/resources/windows/userResource.md)
- [<span data-ttu-id="44cba-151">Risorsa WindowsFeature</span><span class="sxs-lookup"><span data-stu-id="44cba-151">WindowsFeature Resource</span></span>](../reference/resources/windows/windowsFeatureResource.md)
- [<span data-ttu-id="44cba-152">Risorsa WindowsFeatureSet</span><span class="sxs-lookup"><span data-stu-id="44cba-152">WindowsFeatureSet Resource</span></span>](../reference/resources/windows/windowsFeatureSetResource.md)
- [<span data-ttu-id="44cba-153">Risorsa WindowsOptionalFeature</span><span class="sxs-lookup"><span data-stu-id="44cba-153">WindowsOptionalFeature Resource</span></span>](../reference/resources/windows/windowsOptionalFeatureResource.md)
- [<span data-ttu-id="44cba-154">Risorsa WindowsOptionalFeatureSet</span><span class="sxs-lookup"><span data-stu-id="44cba-154">WindowsOptionalFeatureSet Resource</span></span>](../reference/resources/windows/windowsOptionalFeatureSetResource.md)
- [<span data-ttu-id="44cba-155">Risorsa WindowsPackageCabResource</span><span class="sxs-lookup"><span data-stu-id="44cba-155">WindowsPackageCabResource Resource</span></span>](../reference/resources/windows/windowsPackageCabResource.md)
- [<span data-ttu-id="44cba-156">Risorsa WindowsProcess</span><span class="sxs-lookup"><span data-stu-id="44cba-156">WindowsProcess Resource</span></span>](../reference/resources/windows/windowsProcessResource.md)

### <a name="cross-node-dependency-resources"></a><span data-ttu-id="44cba-157">Risorse per le dipendenze tra nodi</span><span class="sxs-lookup"><span data-stu-id="44cba-157">Cross-Node dependency resources</span></span>

- [<span data-ttu-id="44cba-158">Risorsa WaitForAll</span><span class="sxs-lookup"><span data-stu-id="44cba-158">WaitForAll Resource</span></span>](../reference/resources/windows/waitForAllResource.md)
- [<span data-ttu-id="44cba-159">Risorsa WaitForSome</span><span class="sxs-lookup"><span data-stu-id="44cba-159">WaitForSome Resource</span></span>](../reference/resources/windows/waitForSomeResource.md)
- [<span data-ttu-id="44cba-160">Risorsa WaitForAny</span><span class="sxs-lookup"><span data-stu-id="44cba-160">WaitForAny Resource</span></span>](../reference/resources/windows/waitForAnyResource.md)

### <a name="package-management-resources"></a><span data-ttu-id="44cba-161">Risorse di gestione pacchetti</span><span class="sxs-lookup"><span data-stu-id="44cba-161">Package Management resources</span></span>

- [<span data-ttu-id="44cba-162">Risorsa PackageManagement</span><span class="sxs-lookup"><span data-stu-id="44cba-162">PackageManagement Resource</span></span>](../reference/resources/packagemanagement/PackageManagementDscResource.md)
- [<span data-ttu-id="44cba-163">Risorsa PackageManagementSource</span><span class="sxs-lookup"><span data-stu-id="44cba-163">PackageManagementSource Resource</span></span>](../reference/resources/packagemanagement/PackageManagementSourceDscResource.md)

#### <a name="linux-resources"></a><span data-ttu-id="44cba-164">Risorse di Linux</span><span class="sxs-lookup"><span data-stu-id="44cba-164">Linux resources</span></span>

- [<span data-ttu-id="44cba-165">Risorsa Archive Linux</span><span class="sxs-lookup"><span data-stu-id="44cba-165">Linux Archive Resource</span></span>](../reference/resources/linux/lnxArchiveResource.md)
- [<span data-ttu-id="44cba-166">Risorsa Environment Linux</span><span class="sxs-lookup"><span data-stu-id="44cba-166">Linux Environment Resource</span></span>](../reference/resources/linux/lnxEnvironmentResource.md)
- [<span data-ttu-id="44cba-167">Risorsa FileLine Linux</span><span class="sxs-lookup"><span data-stu-id="44cba-167">Linux FileLine Resource</span></span>](../reference/resources/linux/lnxFileLineResource.md)
- [<span data-ttu-id="44cba-168">Risorsa File Linux</span><span class="sxs-lookup"><span data-stu-id="44cba-168">Linux File Resource</span></span>](../reference/resources/linux/lnxFileResource.md)
- [<span data-ttu-id="44cba-169">Risorsa Group Linux</span><span class="sxs-lookup"><span data-stu-id="44cba-169">Linux Group Resource</span></span>](../reference/resources/linux/lnxGroupResource.md)
- [<span data-ttu-id="44cba-170">Risorsa Package Linux</span><span class="sxs-lookup"><span data-stu-id="44cba-170">Linux Package Resource</span></span>](../reference/resources/linux/lnxPackageResource.md)
- [<span data-ttu-id="44cba-171">Risorsa Script Linux</span><span class="sxs-lookup"><span data-stu-id="44cba-171">Linux Script Resource</span></span>](../reference/resources/linux/lnxScriptResource.md)
- [<span data-ttu-id="44cba-172">Risorsa Service Linux</span><span class="sxs-lookup"><span data-stu-id="44cba-172">Linux Service Resource</span></span>](../reference/resources/linux/lnxServiceResource.md)
- [<span data-ttu-id="44cba-173">Risorsa SshAuthorizedKeys Linux</span><span class="sxs-lookup"><span data-stu-id="44cba-173">Linux SshAuthorizedKeys Resource</span></span>](../reference/resources/linux/lnxSshAuthorizedKeysResource.md)
- [<span data-ttu-id="44cba-174">Risorsa User Linux</span><span class="sxs-lookup"><span data-stu-id="44cba-174">Linux User Resource</span></span>](../reference/resources/linux/lnxUserResource.md)
