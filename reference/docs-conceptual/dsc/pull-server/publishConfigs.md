---
ms.date: 12/12/2018
keywords: dsc,powershell,configurazione,installazione
title: Pubblicare in un server di pull usando gli ID di configurazione (v4/v5)
ms.openlocfilehash: c258814f480b91eba75c7ce9abf70c558f1f469e
ms.sourcegitcommit: 18985d07ef024378c8590dc7a983099ff9225672
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 10/04/2019
ms.locfileid: "71953598"
---
# <a name="publish-to-a-pull-server-using-configuration-ids-v4v5"></a><span data-ttu-id="b7837-103">Pubblicare in un server di pull usando gli ID di configurazione (v4/v5)</span><span class="sxs-lookup"><span data-stu-id="b7837-103">Publish to a Pull Server using Configuration IDs (v4/v5)</span></span>

<span data-ttu-id="b7837-104">Le sezioni seguenti presuppongono che sia già stato configurato un server di pull.</span><span class="sxs-lookup"><span data-stu-id="b7837-104">The sections below assume that you have already set up a Pull Server.</span></span> <span data-ttu-id="b7837-105">Per configurare un server di pull, è possibile usare le guide seguenti:</span><span class="sxs-lookup"><span data-stu-id="b7837-105">If you haven't set up your Pull Server, you can use the following guides:</span></span>

- [<span data-ttu-id="b7837-106">Configurare un server di pull SMB DSC</span><span class="sxs-lookup"><span data-stu-id="b7837-106">Set up a DSC SMB Pull Server</span></span>](pullServerSmb.md)
- [<span data-ttu-id="b7837-107">Configurare un server di pull HTTP DSC</span><span class="sxs-lookup"><span data-stu-id="b7837-107">Set up a DSC HTTP Pull Server</span></span>](pullServer.md)

<span data-ttu-id="b7837-108">Ogni nodo di destinazione può essere configurato in modo che possa scaricare configurazioni e risorse e persino segnalare il proprio stato.</span><span class="sxs-lookup"><span data-stu-id="b7837-108">Each target node can be configured to download configurations, resources, and even report its status.</span></span> <span data-ttu-id="b7837-109">Questo articolo illustra come caricare risorse in modo che siano disponibili per essere scaricate e come configurare i client per scaricare automaticamente le risorse.</span><span class="sxs-lookup"><span data-stu-id="b7837-109">This article shows you how to upload resources so they're available to be downloaded, and configure clients to automatically download resources.</span></span> <span data-ttu-id="b7837-110">Quando il nodo riceve una configurazione assegnata, attraverso **Pull** o **Push** (v5), scarica automaticamente le risorse richieste dalla configurazione dal percorso specificato in Gestione configurazione locale (LCM).</span><span class="sxs-lookup"><span data-stu-id="b7837-110">When the node receives an assigned Configuration, through **Pull** or **Push** (v5), it automatically downloads any resources required by the Configuration from the location specified in the Local Configuration Manager (LCM).</span></span>

## <a name="compile-configurations"></a><span data-ttu-id="b7837-111">Compilare le configurazioni</span><span class="sxs-lookup"><span data-stu-id="b7837-111">Compile configurations</span></span>

<span data-ttu-id="b7837-112">Il primo passaggio per l'archiviazione delle [configurazioni](../configurations/configurations.md) in un server di pull è di compilarle in file `.mof`.</span><span class="sxs-lookup"><span data-stu-id="b7837-112">The first step to storing [Configurations](../configurations/configurations.md) on a Pull Server, is to compile them into `.mof` files.</span></span> <span data-ttu-id="b7837-113">Per rendere una configurazione generica e applicabili a più client, usare `localhost` nel blocco di nodo.</span><span class="sxs-lookup"><span data-stu-id="b7837-113">To make a configuration generic, and applicable to more clients, use `localhost` in your Node block.</span></span> <span data-ttu-id="b7837-114">L'esempio seguente mostra una shell di configurazione che usa `localhost` anziché un nome specifico di client.</span><span class="sxs-lookup"><span data-stu-id="b7837-114">The example below shows a Configuration shell that uses `localhost` instead of a specific client name.</span></span>

```powershell
Configuration GenericConfig
{
    Node localhost
    {

    }
}
GenericConfig
```

<span data-ttu-id="b7837-115">Dopo aver compilato la configurazione generica, si dovrebbe avere un file `localhost.mof`.</span><span class="sxs-lookup"><span data-stu-id="b7837-115">Once you've compiled your generic configuration, you should have a `localhost.mof` file.</span></span>

## <a name="renaming-the-mof-file"></a><span data-ttu-id="b7837-116">Rinominare il file MOF</span><span class="sxs-lookup"><span data-stu-id="b7837-116">Renaming the MOF file</span></span>

<span data-ttu-id="b7837-117">È possibile archiviare i file di configurazione `.mof` in un server di pull in base a **ConfigurationName** o **ConfigurationID**.</span><span class="sxs-lookup"><span data-stu-id="b7837-117">You can store Configuration `.mof` files on a Pull Server by **ConfigurationName** or **ConfigurationID**.</span></span> <span data-ttu-id="b7837-118">A seconda del modo in cui si prevede di configurare i client di pull, è possibile scegliere una delle sezioni seguenti per rinominare in modo corretto i file `.mof` compilati.</span><span class="sxs-lookup"><span data-stu-id="b7837-118">Depending on how you plan to set up your pull clients, you can choose a section below to properly rename your compiled `.mof` files.</span></span>

### <a name="configuration-ids-guid"></a><span data-ttu-id="b7837-119">ID di configurazione (GUID)</span><span class="sxs-lookup"><span data-stu-id="b7837-119">Configuration IDs (GUID)</span></span>

<span data-ttu-id="b7837-120">Sarà necessario rinominare il file `localhost.mof` in un file `<GUID>.mof`.</span><span class="sxs-lookup"><span data-stu-id="b7837-120">You'll need to rename your `localhost.mof` file to `<GUID>.mof` file.</span></span> <span data-ttu-id="b7837-121">È possibile creare un **GUID** casuale usando l'esempio che segue o tramite il cmdlet [New-Guid](/powershell/module/microsoft.powershell.utility/new-guid).</span><span class="sxs-lookup"><span data-stu-id="b7837-121">You can create a random **Guid** using the example below, or by using the [New-Guid](/powershell/module/microsoft.powershell.utility/new-guid) cmdlet.</span></span>

```powershell
[System.Guid]::NewGuid()
```

<span data-ttu-id="b7837-122">Output di esempio</span><span class="sxs-lookup"><span data-stu-id="b7837-122">Sample Output</span></span>

```Output
Guid
----
64856475-939e-41fb-aba5-4469f4006059
```

<span data-ttu-id="b7837-123">Sarà quindi possibile rinominare il file `.mof` usando qualsiasi metodo accettabile.</span><span class="sxs-lookup"><span data-stu-id="b7837-123">You can then rename your `.mof` file using any acceptable method.</span></span> <span data-ttu-id="b7837-124">Nell'esempio riportato di seguito, viene usato il cmdlet [Rename-Item](/powershell/module/microsoft.powershell.management/rename-item).</span><span class="sxs-lookup"><span data-stu-id="b7837-124">The example below, uses the [Rename-Item](/powershell/module/microsoft.powershell.management/rename-item) cmdlet.</span></span>

```powershell
Rename-Item -Path .\localhost.mof -NewName '64856475-939e-41fb-aba5-4469f4006059.mof'
```

<span data-ttu-id="b7837-125">Per altre informazioni sull'uso di **GUID** nell'ambiente in uso, vedere [Pianificare per i GUID](/powershell/dsc/secureserver#guids).</span><span class="sxs-lookup"><span data-stu-id="b7837-125">For more information about using **Guids** in your environment, see [Plan for Guids](/powershell/dsc/secureserver#guids).</span></span>

### <a name="configuration-names"></a><span data-ttu-id="b7837-126">Nomi di configurazione</span><span class="sxs-lookup"><span data-stu-id="b7837-126">Configuration names</span></span>

<span data-ttu-id="b7837-127">Sarà necessario rinominare il file `localhost.mof` in un file `<Configuration Name>.mof`.</span><span class="sxs-lookup"><span data-stu-id="b7837-127">You'll need to rename your `localhost.mof` file to `<Configuration Name>.mof` file.</span></span> <span data-ttu-id="b7837-128">Nell'esempio seguente viene usato il nome della configurazione della sezione precedente.</span><span class="sxs-lookup"><span data-stu-id="b7837-128">In the following example, the configuration name from the previous section is used.</span></span> <span data-ttu-id="b7837-129">Sarà quindi possibile rinominare il file `.mof` usando qualsiasi metodo accettabile.</span><span class="sxs-lookup"><span data-stu-id="b7837-129">You can then rename your `.mof` file using any acceptable method.</span></span> <span data-ttu-id="b7837-130">Nell'esempio riportato di seguito, viene usato il cmdlet [Rename-Item](/powershell/module/microsoft.powershell.management/rename-item).</span><span class="sxs-lookup"><span data-stu-id="b7837-130">The example below, uses the [Rename-Item](/powershell/module/microsoft.powershell.management/rename-item) cmdlet.</span></span>

```powershell
Rename-Item -Path .\localhost.mof -NewName 'GenericConfig.mof'
```

## <a name="create-the-checksum"></a><span data-ttu-id="b7837-131">Creare il file CheckSum</span><span class="sxs-lookup"><span data-stu-id="b7837-131">Create the checkSum</span></span>

<span data-ttu-id="b7837-132">Ogni file `.mof` archiviato in un server di pull o una condivisione SMB deve avere un file `.checksum` associato.</span><span class="sxs-lookup"><span data-stu-id="b7837-132">Each `.mof` file stored on a Pull Server, or SMB share needs to have an associated `.checksum` file.</span></span>
<span data-ttu-id="b7837-133">Questo file consente ai client di sapere quando il file `.mof` associato è stato modificato e deve essere scaricato nuovamente.</span><span class="sxs-lookup"><span data-stu-id="b7837-133">This file lets clients know when the associated `.mof` file has changed and should be downloaded again.</span></span>

<span data-ttu-id="b7837-134">È possibile creare un **CheckSum** con il cmdlet [New-DSCCheckSum](/powershell/module/psdesiredstateconfiguration/new-dscchecksum).</span><span class="sxs-lookup"><span data-stu-id="b7837-134">You can create a **CheckSum** with the [New-DSCCheckSum](/powershell/module/psdesiredstateconfiguration/new-dscchecksum) cmdlet.</span></span> <span data-ttu-id="b7837-135">È anche possibile eseguire `New-DSCCheckSum` in una directory di file usando il parametro `-Path`.</span><span class="sxs-lookup"><span data-stu-id="b7837-135">You can also run `New-DSCCheckSum` against a directory of files using the `-Path` parameter.</span></span>
<span data-ttu-id="b7837-136">Se esiste già un checksum, è possibile forzare la nuova creazione con il parametro `-Force`.</span><span class="sxs-lookup"><span data-stu-id="b7837-136">If a checksum already exists, you can force it to be re-created with the `-Force` parameter.</span></span> <span data-ttu-id="b7837-137">L'esempio seguente specifica una directory contenente il file `.mof` della sezione precedente e usa il parametro `-Force`.</span><span class="sxs-lookup"><span data-stu-id="b7837-137">The following example specified a directory containing the `.mof` file from the previous section, and uses the `-Force` parameter.</span></span>

```powershell
New-DscChecksum -Path '.\' -Force
```

<span data-ttu-id="b7837-138">Non verrà visualizzato alcun output, ma a questo punto dovrebbe essere visualizzato un file `<GUID or Configuration Name>.mof.checksum`.</span><span class="sxs-lookup"><span data-stu-id="b7837-138">No output will be shown, but you should now see a `<GUID or Configuration Name>.mof.checksum` file.</span></span>

## <a name="where-to-store-mof-files-and-checksums"></a><span data-ttu-id="b7837-139">Posizione in cui archiviare i file MOF e CheckSum</span><span class="sxs-lookup"><span data-stu-id="b7837-139">Where to store MOF files and checkSums</span></span>

### <a name="on-a-dsc-http-pull-server"></a><span data-ttu-id="b7837-140">In un server di pull HTTP DSC</span><span class="sxs-lookup"><span data-stu-id="b7837-140">On a DSC HTTP Pull Server</span></span>

<span data-ttu-id="b7837-141">Quando si configura il server di pull HTTP, come illustrato in [Configurare un server di pull HTTP DSC](pullServer.md), si specificano le directory per le chiavi **ModulePath** e **ConfigurationPath**.</span><span class="sxs-lookup"><span data-stu-id="b7837-141">When you set up your HTTP Pull Server, as explained in [Set up a DSC HTTP Pull Server](pullServer.md), you specify directories for the **ModulePath** and **ConfigurationPath** keys.</span></span> <span data-ttu-id="b7837-142">La chiave **ModulePath** indica dove devono essere archiviati i file `.zip` di un modulo.</span><span class="sxs-lookup"><span data-stu-id="b7837-142">The **ModulePath** key indicates where a module's packaged `.zip` files should be stored.</span></span> <span data-ttu-id="b7837-143">**ConfigurationPath** indica dove devono essere archiviati eventuali file `.mof` e `.checksum`.</span><span class="sxs-lookup"><span data-stu-id="b7837-143">The **ConfigurationPath** indicates where any `.mof` files and `.checksum` files should be stored.</span></span>

```powershell
    xDscWebService PSDSCPullServer
    {
    ...
        ModulePath              = "$env:PROGRAMFILES\WindowsPowerShell\DscService\Modules"
        ConfigurationPath       = "$env:PROGRAMFILES\WindowsPowerShell\DscService\Configuration"
    ...
    }

```

### <a name="on-an-smb-share"></a><span data-ttu-id="b7837-144">In una condivisione SMB</span><span class="sxs-lookup"><span data-stu-id="b7837-144">On an SMB share</span></span>

<span data-ttu-id="b7837-145">Quando si configura un client di pull per usare una condivisione SMB, si specifica **ConfigurationRepositoryShare**.</span><span class="sxs-lookup"><span data-stu-id="b7837-145">When you set up a Pull Client to use an SMB share, you specify a **ConfigurationRepositoryShare**.</span></span>
<span data-ttu-id="b7837-146">Tutti i file `.mof` e `.checksum` devono quindi essere archiviati nella directory **SourcePath** del blocco **ConfigurationRepositoryShare**.</span><span class="sxs-lookup"><span data-stu-id="b7837-146">All `.mof` files and `.checksum` files should be stored in the **SourcePath** directory from the **ConfigurationRepositoryShare** block.</span></span>

```powershell
ConfigurationRepositoryShare SMBPullServer
{
    SourcePath = '\\SMBPullServer\Pull'
}
```

## <a name="next-steps"></a><span data-ttu-id="b7837-147">Passaggi successivi</span><span class="sxs-lookup"><span data-stu-id="b7837-147">Next steps</span></span>

<span data-ttu-id="b7837-148">Successivamente verranno configurati i client pull per eseguire il pull della configurazione specificata.</span><span class="sxs-lookup"><span data-stu-id="b7837-148">Next, you'll want to configure Pull Clients to pull the specified configuration.</span></span> <span data-ttu-id="b7837-149">Per altre informazioni, vedere le seguenti guide:</span><span class="sxs-lookup"><span data-stu-id="b7837-149">For more information, see one of the following guides:</span></span>

- [<span data-ttu-id="b7837-150">Configurare un client di pull usando gli ID di configurazione (v4)</span><span class="sxs-lookup"><span data-stu-id="b7837-150">Set up a Pull Client using Configuration IDs (v4)</span></span>](pullClientConfigId4.md)
- [<span data-ttu-id="b7837-151">Configurare un client di pull usando gli ID di configurazione (v5)</span><span class="sxs-lookup"><span data-stu-id="b7837-151">Set up a Pull Client using Configuration IDs (v5)</span></span>](pullClientConfigId.md)
- [<span data-ttu-id="b7837-152">Configurare un client di pull usando i nomi di configurazione (v5)</span><span class="sxs-lookup"><span data-stu-id="b7837-152">Set up a Pull Client using Configuration Names (v5)</span></span>](pullClientConfigNames.md)

## <a name="see-also"></a><span data-ttu-id="b7837-153">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="b7837-153">See also</span></span>

- [<span data-ttu-id="b7837-154">Configurare un server di pull SMB DSC</span><span class="sxs-lookup"><span data-stu-id="b7837-154">Set up a DSC SMB Pull Server</span></span>](pullServerSmb.md)
- [<span data-ttu-id="b7837-155">Configurare un server di pull HTTP DSC</span><span class="sxs-lookup"><span data-stu-id="b7837-155">Set up a DSC HTTP Pull Server</span></span>](pullServer.md)
- [<span data-ttu-id="b7837-156">Creare un pacchetto e caricare le risorse in un server di pull</span><span class="sxs-lookup"><span data-stu-id="b7837-156">Package and Upload Resources to a Pull Server</span></span>](package-upload-resources.md)
