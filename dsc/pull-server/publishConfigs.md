---
ms.date: 12/12/2018
keywords: dsc,powershell,configurazione,installazione
title: Pubblicare in un server di pull usando gli ID di configurazione (v4/v5)
ms.openlocfilehash: 0144fec43d7a8d65b79891567cc0dc3952175343
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62079507"
---
# <a name="publish-to-a-pull-server-using-configuration-ids-v4v5"></a><span data-ttu-id="b6e7a-103">Pubblicare in un server di pull usando gli ID di configurazione (v4/v5)</span><span class="sxs-lookup"><span data-stu-id="b6e7a-103">Publish to a Pull Server using Configuration IDs (v4/v5)</span></span>

<span data-ttu-id="b6e7a-104">Le sezioni seguenti presuppongono che sia già stato configurato un server di pull.</span><span class="sxs-lookup"><span data-stu-id="b6e7a-104">The sections below assume that you have already set up a Pull Server.</span></span> <span data-ttu-id="b6e7a-105">Per configurare un server di pull, è possibile usare le guide seguenti:</span><span class="sxs-lookup"><span data-stu-id="b6e7a-105">If you have not set up your Pull Server, you can use the following guides:</span></span>

- [<span data-ttu-id="b6e7a-106">Configurare un server di pull SMB DSC</span><span class="sxs-lookup"><span data-stu-id="b6e7a-106">Set up a DSC SMB Pull Server</span></span>](pullServerSmb.md)
- [<span data-ttu-id="b6e7a-107">Configurare un server di pull HTTP DSC</span><span class="sxs-lookup"><span data-stu-id="b6e7a-107">Set up a DSC HTTP Pull Server</span></span>](pullServer.md)

<span data-ttu-id="b6e7a-108">Ogni nodo di destinazione può essere configurato in modo che possa scaricare configurazioni e risorse e persino segnalare il proprio stato.</span><span class="sxs-lookup"><span data-stu-id="b6e7a-108">Each target node can be configured to download configurations, resources, and even report its status.</span></span> <span data-ttu-id="b6e7a-109">Questo articolo illustra come caricare risorse in modo che siano disponibili per essere scaricate e configurare i client per scaricare automaticamente le risorse.</span><span class="sxs-lookup"><span data-stu-id="b6e7a-109">This article will show you how to upload resources so they are available to be downloaded, and configure clients to download resources automatically.</span></span> <span data-ttu-id="b6e7a-110">Quando il nodo riceve una configurazione assegnata, attraverso **Pull** o **Push** (v5), scarica automaticamente le risorse richieste dalla configurazione dal percorso specificato in Gestione configurazione locale (LCM).</span><span class="sxs-lookup"><span data-stu-id="b6e7a-110">When the Node's receives an assigned Configuration, through **Pull** or **Push** (v5), it automatically downloads any resources required by the Configuration from the location specified in the LCM.</span></span>

## <a name="compile-configurations"></a><span data-ttu-id="b6e7a-111">Compilare le configurazioni</span><span class="sxs-lookup"><span data-stu-id="b6e7a-111">Compile Configurations</span></span>

<span data-ttu-id="b6e7a-112">Il primo passaggio per l'archiviazione delle [configurazioni](../configurations/configurations.md) in un server di pull è di compilarle nei file "MOF".</span><span class="sxs-lookup"><span data-stu-id="b6e7a-112">The first step to storing [Configurations](../configurations/configurations.md) on a Pull Server, is to compile them into ".mof" files.</span></span> <span data-ttu-id="b6e7a-113">Per rendere una configurazione generica e applicabili a più client, usare `localhost` nel blocco di nodo.</span><span class="sxs-lookup"><span data-stu-id="b6e7a-113">To make a configuration generic, and applicable to more clients, use `localhost` in your Node block.</span></span> <span data-ttu-id="b6e7a-114">L'esempio seguente mostra una shell di configurazione che usa `localhost` anziché un nome specifico di client.</span><span class="sxs-lookup"><span data-stu-id="b6e7a-114">The example below shows a Configuration shell that uses `localhost` instead of a specific client name.</span></span>

```powershell
Configuration GenericConfig
{
    Node localhost
    {

    }
}
GenericConfig
```

<span data-ttu-id="b6e7a-115">Dopo aver compilato la configurazione generica, si dovrebbe avere un file "localhost.mof".</span><span class="sxs-lookup"><span data-stu-id="b6e7a-115">Once you have compiled your generic configuration, you should have a "localhost.mof" file.</span></span>

## <a name="renaming-the-mof-file"></a><span data-ttu-id="b6e7a-116">Rinominare il file MOF</span><span class="sxs-lookup"><span data-stu-id="b6e7a-116">Renaming the MOF file</span></span>

<span data-ttu-id="b6e7a-117">È possibile archiviare i file di configurazione "MOF" in un server di pull in base a **ConfigurationName** o **ConfigurationID**.</span><span class="sxs-lookup"><span data-stu-id="b6e7a-117">You can store Configuration ".mof" files on a Pull Server by **ConfigurationName** or **ConfigurationID**.</span></span> <span data-ttu-id="b6e7a-118">A seconda del modo in cui si prevede di configurare i client di pull, è possibile scegliere una delle sezioni seguenti per rinominare in modo corretto i file "MOF" compilati.</span><span class="sxs-lookup"><span data-stu-id="b6e7a-118">Depending on how you plan to set up your pull clients, you can choose a section below to properly rename your compiled ".mof" files.</span></span>

### <a name="configuration-ids-guid"></a><span data-ttu-id="b6e7a-119">ID di configurazione (GUID)</span><span class="sxs-lookup"><span data-stu-id="b6e7a-119">Configuration IDs (GUID)</span></span>

<span data-ttu-id="b6e7a-120">Sarà necessario rinominare il file "localhost.mof" in un file "<GUID>MOF".</span><span class="sxs-lookup"><span data-stu-id="b6e7a-120">You will need to rename your "localhost.mof" file to "<GUID>.mof" file.</span></span> <span data-ttu-id="b6e7a-121">È possibile creare un **GUID** casuale usando l'esempio che segue o tramite il cmdlet [New-Guid](/powershell/module/microsoft.powershell.utility/new-guid).</span><span class="sxs-lookup"><span data-stu-id="b6e7a-121">You can create a random **Guid** using the example below, or by using the [New-Guid](/powershell/module/microsoft.powershell.utility/new-guid) cmdlet.</span></span>

```powershell
[System.Guid]::NewGuid()
```

<span data-ttu-id="b6e7a-122">Output di esempio</span><span class="sxs-lookup"><span data-stu-id="b6e7a-122">Sample Output</span></span>

```output
Guid
----
64856475-939e-41fb-aba5-4469f4006059
```

<span data-ttu-id="b6e7a-123">Sarà quindi possibile rinominare il file "MOF" usando qualsiasi metodo accettabile.</span><span class="sxs-lookup"><span data-stu-id="b6e7a-123">You can then rename your ".mof" file using any acceptable method.</span></span> <span data-ttu-id="b6e7a-124">Nell'esempio riportato di seguito, viene usato il cmdlet [Rename-Item](/powershell/module/microsoft.powershell.management/rename-item).</span><span class="sxs-lookup"><span data-stu-id="b6e7a-124">The example below, uses the [Rename-Item](/powershell/module/microsoft.powershell.management/rename-item) cmdlet.</span></span>

```powershell
Rename-Item -Path .\localhost.mof -NewName '64856475-939e-41fb-aba5-4469f4006059.mof'
```

<span data-ttu-id="b6e7a-125">Per altre informazioni sull'uso di **GUID** nell'ambiente in uso, vedere [Pianificare per i GUID](/powershell/dsc/secureserver#guids).</span><span class="sxs-lookup"><span data-stu-id="b6e7a-125">For more information about using **Guids** in your environment, see [Plan for Guids](/powershell/dsc/secureserver#guids).</span></span>

### <a name="configuration-names"></a><span data-ttu-id="b6e7a-126">Nomi di configurazione</span><span class="sxs-lookup"><span data-stu-id="b6e7a-126">Configuration Names</span></span>

<span data-ttu-id="b6e7a-127">Sarà necessario rinominare il file "localhost.mof" in un file "<Configuration Name>MOF".</span><span class="sxs-lookup"><span data-stu-id="b6e7a-127">You will need to rename your "localhost.mof" file to "<Configuration Name>.mof" file.</span></span> <span data-ttu-id="b6e7a-128">Nell'esempio seguente viene usato il nome della configurazione della sezione precedente.</span><span class="sxs-lookup"><span data-stu-id="b6e7a-128">In the following example, the configuration name from the previous section is used.</span></span> <span data-ttu-id="b6e7a-129">Sarà quindi possibile rinominare il file "MOF" usando qualsiasi metodo accettabile.</span><span class="sxs-lookup"><span data-stu-id="b6e7a-129">You can then rename your ".mof" file using any acceptable method.</span></span> <span data-ttu-id="b6e7a-130">Nell'esempio riportato di seguito, viene usato il cmdlet [Rename-Item](/powershell/module/microsoft.powershell.management/rename-item).</span><span class="sxs-lookup"><span data-stu-id="b6e7a-130">The example below, uses the [Rename-Item](/powershell/module/microsoft.powershell.management/rename-item) cmdlet.</span></span>

```powershell
Rename-Item -Path .\localhost.mof -NewName 'GenericConfig.mof'
```

## <a name="create-the-checksum"></a><span data-ttu-id="b6e7a-131">Creare il valore checksum</span><span class="sxs-lookup"><span data-stu-id="b6e7a-131">Create the CheckSum</span></span>

<span data-ttu-id="b6e7a-132">Ogni file "MOF" archiviato in un server di pull o una condivisione SMB deve avere un file "CHECKSUM" associato.</span><span class="sxs-lookup"><span data-stu-id="b6e7a-132">Each ".mof" file stored on a Pull Server, or SMB share needs to have an associated ".checksum" file.</span></span> <span data-ttu-id="b6e7a-133">Questo file consente ai client di sapere quando il file "MOF" associato è stato modificato e deve essere scaricato nuovamente.</span><span class="sxs-lookup"><span data-stu-id="b6e7a-133">This file lets clients know when the associated ".mof" file has changed and should be downloaded again.</span></span>

<span data-ttu-id="b6e7a-134">È possibile creare un **CheckSum** con il cmdlet [New-DSCCheckSum](/powershell/module/psdesiredstateconfiguration/new-dscchecksum).</span><span class="sxs-lookup"><span data-stu-id="b6e7a-134">You can create a **CheckSum** with the [New-DSCCheckSum](/powershell/module/psdesiredstateconfiguration/new-dscchecksum) cmdlet.</span></span> <span data-ttu-id="b6e7a-135">È anche possibile eseguire `New-DSCCheckSum` in una directory di file usando il parametro `-Path`.</span><span class="sxs-lookup"><span data-stu-id="b6e7a-135">You can also run `New-DSCCheckSum` against a directory of files using the `-Path` parameter.</span></span> <span data-ttu-id="b6e7a-136">Se esiste già un checksum, è possibile forzare la nuova creazione con il parametro `-Force`.</span><span class="sxs-lookup"><span data-stu-id="b6e7a-136">If a checksum already exists, you can force it to be re-created with the `-Force` parameter.</span></span> <span data-ttu-id="b6e7a-137">L'esempio seguente specifica una directory contenente il file "MOF" della sezione precedente e usa il parametro `-Force`.</span><span class="sxs-lookup"><span data-stu-id="b6e7a-137">The following example specified a directory containing the ".mof" file from the previous section, and uses the `-Force` parameter.</span></span>

```powershell
New-DscChecksum -Path '.\' -Force
```

<span data-ttu-id="b6e7a-138">Non verrà visualizzato alcun output, ma si visualizzerà ora un file "<GUID or Configuration Name>. mof.checksum".</span><span class="sxs-lookup"><span data-stu-id="b6e7a-138">No output will be shown, but you should now see a "<GUID or Configuration Name>.mof.checksum" file.</span></span>

## <a name="where-to-store-mof-files-and-checksums"></a><span data-ttu-id="b6e7a-139">Posizione in cui archiviare i file MOF e CheckSum</span><span class="sxs-lookup"><span data-stu-id="b6e7a-139">Where to store MOF files and CheckSums</span></span>

### <a name="on-a-dsc-http-pull-server"></a><span data-ttu-id="b6e7a-140">In un server di pull HTTP DSC</span><span class="sxs-lookup"><span data-stu-id="b6e7a-140">On a DSC HTTP Pull Server</span></span>

<span data-ttu-id="b6e7a-141">Quando si configura il server di pull HTTP, come illustrato nella [configurazione di un server di pull HTTP DSC](pullServer.md), si specificano le directory per le chiavi **ModulePath** e **ConfigurationPath**.</span><span class="sxs-lookup"><span data-stu-id="b6e7a-141">When you set up your HTTP Pull Server, as explained in [Set up a DSC HTTP Pull Server](pullServer.md), you specify directories for the **ModulePath** and **ConfigurationPath** keys.</span></span> <span data-ttu-id="b6e7a-142">La chiave **ConfigurationPath** indica dove devono essere archiviati eventuali file "MOF".</span><span class="sxs-lookup"><span data-stu-id="b6e7a-142">The **ConfigurationPath** key indicates where any ".mof" files should be stored.</span></span> <span data-ttu-id="b6e7a-143">**ConfigurationPath** indica dove devono essere archiviati eventuali file "MOF" e "CHECKSUM".</span><span class="sxs-lookup"><span data-stu-id="b6e7a-143">The **ConfigurationPath** indicates where any ".mof" files and ".checksum" files should be stored.</span></span>

```powershell
    xDscWebService PSDSCPullServer
    {
    ...
        ModulePath              = "$env:PROGRAMFILES\WindowsPowerShell\DscService\Modules"
        ConfigurationPath       = "$env:PROGRAMFILES\WindowsPowerShell\DscService\Configuration"
    ...
    }

```

### <a name="on-an-smb-share"></a><span data-ttu-id="b6e7a-144">In una condivisione SMB</span><span class="sxs-lookup"><span data-stu-id="b6e7a-144">On an SMB Share</span></span>

<span data-ttu-id="b6e7a-145">Quando si configura un client di pull per usare una condivisione SMB, si specifica **ConfigurationRepositoryShare**.</span><span class="sxs-lookup"><span data-stu-id="b6e7a-145">When you set up a Pull Client to use an SMB share, you specify a **ConfigurationRepositoryShare**.</span></span> <span data-ttu-id="b6e7a-146">Tutti i file "MOF" e "CHECKSUM" devono quindi essere archiviati nella directory **SourcePath** del blocco **ConfigurationRepositoryShare**.</span><span class="sxs-lookup"><span data-stu-id="b6e7a-146">All ".mof" files and ".checksum" files should then be stored in the **SourcePath** directory from the **ConfigurationRepositoryShare** block.</span></span>

```powershell
ConfigurationRepositoryShare SMBPullServer
{
    SourcePath = '\\SMBPullServer\Pull'
}
```

## <a name="next-steps"></a><span data-ttu-id="b6e7a-147">Passaggi successivi</span><span class="sxs-lookup"><span data-stu-id="b6e7a-147">Next Steps</span></span>

<span data-ttu-id="b6e7a-148">Successivamente vengono configurati i client pull per eseguire il pull della configurazione specificata.</span><span class="sxs-lookup"><span data-stu-id="b6e7a-148">Next, you will want to configure Pull Clients to pull the specified configuration.</span></span> <span data-ttu-id="b6e7a-149">Per altre informazioni, vedere le seguenti guide:</span><span class="sxs-lookup"><span data-stu-id="b6e7a-149">For more information, see one of the following guides:</span></span>

- [<span data-ttu-id="b6e7a-150">Configurare un client di pull usando gli ID di configurazione (v4)</span><span class="sxs-lookup"><span data-stu-id="b6e7a-150">Set up a Pull Client using Configuration IDs (v4)</span></span>](pullClientConfigId4.md)
- [<span data-ttu-id="b6e7a-151">Configurare un client di pull usando gli ID di configurazione (v5)</span><span class="sxs-lookup"><span data-stu-id="b6e7a-151">Set up a Pull Client using Configuration IDs (v5)</span></span>](pullClientConfigId.md)
- [<span data-ttu-id="b6e7a-152">Configurare un client di pull usando i nomi di configurazione (v5)</span><span class="sxs-lookup"><span data-stu-id="b6e7a-152">Set up a Pull Client using Configuration Names (v5)</span></span>](pullClientConfigNames.md)

## <a name="see-also"></a><span data-ttu-id="b6e7a-153">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="b6e7a-153">See also</span></span>

- [<span data-ttu-id="b6e7a-154">Configurare un server di pull SMB DSC</span><span class="sxs-lookup"><span data-stu-id="b6e7a-154">Set up a DSC SMB Pull Server</span></span>](pullServerSmb.md)
- [<span data-ttu-id="b6e7a-155">Configurare un server di pull HTTP DSC</span><span class="sxs-lookup"><span data-stu-id="b6e7a-155">Set up a DSC HTTP Pull Server</span></span>](pullServer.md)
- [<span data-ttu-id="b6e7a-156">Creare un pacchetto e caricare le risorse in un server di pull</span><span class="sxs-lookup"><span data-stu-id="b6e7a-156">Package and Upload Resources to a Pull Server</span></span>](package-upload-resources.md)
