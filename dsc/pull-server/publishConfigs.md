---
ms.date: 12/12/2018
keywords: dsc,powershell,configurazione,installazione
title: Pubblicare in un Server di Pull usando gli ID di configurazione (v4/v5)
ms.openlocfilehash: 0144fec43d7a8d65b79891567cc0dc3952175343
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MTE95
ms.contentlocale: it-IT
ms.lasthandoff: 12/14/2018
ms.locfileid: "53401314"
---
# <a name="publish-to-a-pull-server-using-configuration-ids-v4v5"></a><span data-ttu-id="a1059-103">Pubblicare in un Server di Pull usando gli ID di configurazione (v4/v5)</span><span class="sxs-lookup"><span data-stu-id="a1059-103">Publish to a Pull Server using Configuration IDs (v4/v5)</span></span>

<span data-ttu-id="a1059-104">Le sezioni seguenti presuppongono che già stato impostato in un Server di Pull.</span><span class="sxs-lookup"><span data-stu-id="a1059-104">The sections below assume that you have already set up a Pull Server.</span></span> <span data-ttu-id="a1059-105">Se non è stato configurato il Server di Pull, è possibile usare le guide seguenti:</span><span class="sxs-lookup"><span data-stu-id="a1059-105">If you have not set up your Pull Server, you can use the following guides:</span></span>

- [<span data-ttu-id="a1059-106">Configurare un server di pull SMB DSC</span><span class="sxs-lookup"><span data-stu-id="a1059-106">Set up a DSC SMB Pull Server</span></span>](pullServerSmb.md)
- [<span data-ttu-id="a1059-107">Configurare un server di pull HTTP DSC</span><span class="sxs-lookup"><span data-stu-id="a1059-107">Set up a DSC HTTP Pull Server</span></span>](pullServer.md)

<span data-ttu-id="a1059-108">Ogni nodo di destinazione può essere configurato per scaricare le configurazioni, risorse e anche segnalare lo stato.</span><span class="sxs-lookup"><span data-stu-id="a1059-108">Each target node can be configured to download configurations, resources, and even report its status.</span></span> <span data-ttu-id="a1059-109">Questo articolo illustrerà come caricare risorse in modo che siano disponibili per essere scaricato e configurare i client per scaricare automaticamente le risorse.</span><span class="sxs-lookup"><span data-stu-id="a1059-109">This article will show you how to upload resources so they are available to be downloaded, and configure clients to download resources automatically.</span></span> <span data-ttu-id="a1059-110">Quando il nodo riceve una configurazione assegnata, attraverso **Pull** oppure **Push** (v5), scarica automaticamente le risorse richieste dalla configurazione dal percorso specificato in Gestione configurazione locale.</span><span class="sxs-lookup"><span data-stu-id="a1059-110">When the Node's receives an assigned Configuration, through **Pull** or **Push** (v5), it automatically downloads any resources required by the Configuration from the location specified in the LCM.</span></span>

## <a name="compile-configurations"></a><span data-ttu-id="a1059-111">Compilare configurazioni</span><span class="sxs-lookup"><span data-stu-id="a1059-111">Compile Configurations</span></span>

<span data-ttu-id="a1059-112">Il primo passaggio per la memorizzazione [configurazioni](../configurations/configurations.md) in un Server di Pull è per compilarle in file con "estensione MOF".</span><span class="sxs-lookup"><span data-stu-id="a1059-112">The first step to storing [Configurations](../configurations/configurations.md) on a Pull Server, is to compile them into ".mof" files.</span></span> <span data-ttu-id="a1059-113">Per rendere una configurazione generica e applicabili a più client, usare `localhost` in blocco di nodo.</span><span class="sxs-lookup"><span data-stu-id="a1059-113">To make a configuration generic, and applicable to more clients, use `localhost` in your Node block.</span></span> <span data-ttu-id="a1059-114">L'esempio seguente mostra una shell di configurazione che usa `localhost` anziché un nome specifico client.</span><span class="sxs-lookup"><span data-stu-id="a1059-114">The example below shows a Configuration shell that uses `localhost` instead of a specific client name.</span></span>

```powershell
Configuration GenericConfig
{
    Node localhost
    {

    }
}
GenericConfig
```

<span data-ttu-id="a1059-115">Dopo aver compilato la configurazione generica, è necessario avere un file "localhost.mof".</span><span class="sxs-lookup"><span data-stu-id="a1059-115">Once you have compiled your generic configuration, you should have a "localhost.mof" file.</span></span>

## <a name="renaming-the-mof-file"></a><span data-ttu-id="a1059-116">Ridenominazione del file MOF</span><span class="sxs-lookup"><span data-stu-id="a1059-116">Renaming the MOF file</span></span>

<span data-ttu-id="a1059-117">È possibile archiviare i file di configurazione "MOF" in un Server di Pull da **ConfigurationName** oppure **ConfigurationID**.</span><span class="sxs-lookup"><span data-stu-id="a1059-117">You can store Configuration ".mof" files on a Pull Server by **ConfigurationName** or **ConfigurationID**.</span></span> <span data-ttu-id="a1059-118">A seconda del modo in cui si prevede di configurare i client di pull, è possibile scegliere delle sezioni seguenti in modo corretto rinominare i file compilati "MOF".</span><span class="sxs-lookup"><span data-stu-id="a1059-118">Depending on how you plan to set up your pull clients, you can choose a section below to properly rename your compiled ".mof" files.</span></span>

### <a name="configuration-ids-guid"></a><span data-ttu-id="a1059-119">ID di configurazione (GUID)</span><span class="sxs-lookup"><span data-stu-id="a1059-119">Configuration IDs (GUID)</span></span>

<span data-ttu-id="a1059-120">Sarà necessario rinominare il file "localhost.mof" a "<GUID>MOF" file.</span><span class="sxs-lookup"><span data-stu-id="a1059-120">You will need to rename your "localhost.mof" file to "<GUID>.mof" file.</span></span> <span data-ttu-id="a1059-121">È possibile creare uno casuale **Guid** usando l'esempio sotto, o tramite il [New-Guid](/powershell/module/microsoft.powershell.utility/new-guid) cmdlet.</span><span class="sxs-lookup"><span data-stu-id="a1059-121">You can create a random **Guid** using the example below, or by using the [New-Guid](/powershell/module/microsoft.powershell.utility/new-guid) cmdlet.</span></span>

```powershell
[System.Guid]::NewGuid()
```

<span data-ttu-id="a1059-122">Output di esempio</span><span class="sxs-lookup"><span data-stu-id="a1059-122">Sample Output</span></span>

```output
Guid
----
64856475-939e-41fb-aba5-4469f4006059
```

<span data-ttu-id="a1059-123">Sarà quindi possibile rinominare il file "MOF" usando qualsiasi metodo accettabile.</span><span class="sxs-lookup"><span data-stu-id="a1059-123">You can then rename your ".mof" file using any acceptable method.</span></span> <span data-ttu-id="a1059-124">Nell'esempio riportato di seguito, viene usato il [Rename-Item](/powershell/module/microsoft.powershell.management/rename-item) cmdlet.</span><span class="sxs-lookup"><span data-stu-id="a1059-124">The example below, uses the [Rename-Item](/powershell/module/microsoft.powershell.management/rename-item) cmdlet.</span></span>

```powershell
Rename-Item -Path .\localhost.mof -NewName '64856475-939e-41fb-aba5-4469f4006059.mof'
```

<span data-ttu-id="a1059-125">Per altre informazioni sull'uso **GUID** nell'ambiente in uso, vedere [pianificare GUID](/powershell/dsc/secureserver#guids).</span><span class="sxs-lookup"><span data-stu-id="a1059-125">For more information about using **Guids** in your environment, see [Plan for Guids](/powershell/dsc/secureserver#guids).</span></span>

### <a name="configuration-names"></a><span data-ttu-id="a1059-126">Nomi di configurazione</span><span class="sxs-lookup"><span data-stu-id="a1059-126">Configuration Names</span></span>

<span data-ttu-id="a1059-127">Sarà necessario rinominare il file "localhost.mof" a "<Configuration Name>MOF" file.</span><span class="sxs-lookup"><span data-stu-id="a1059-127">You will need to rename your "localhost.mof" file to "<Configuration Name>.mof" file.</span></span> <span data-ttu-id="a1059-128">Nell'esempio seguente viene utilizzato il nome della configurazione nella sezione precedente.</span><span class="sxs-lookup"><span data-stu-id="a1059-128">In the following example, the configuration name from the previous section is used.</span></span> <span data-ttu-id="a1059-129">Sarà quindi possibile rinominare il file "MOF" usando qualsiasi metodo accettabile.</span><span class="sxs-lookup"><span data-stu-id="a1059-129">You can then rename your ".mof" file using any acceptable method.</span></span> <span data-ttu-id="a1059-130">Nell'esempio riportato di seguito, viene usato il [Rename-Item](/powershell/module/microsoft.powershell.management/rename-item) cmdlet.</span><span class="sxs-lookup"><span data-stu-id="a1059-130">The example below, uses the [Rename-Item](/powershell/module/microsoft.powershell.management/rename-item) cmdlet.</span></span>

```powershell
Rename-Item -Path .\localhost.mof -NewName 'GenericConfig.mof'
```

## <a name="create-the-checksum"></a><span data-ttu-id="a1059-131">Creare il valore di CheckSum</span><span class="sxs-lookup"><span data-stu-id="a1059-131">Create the CheckSum</span></span>

<span data-ttu-id="a1059-132">Ogni file "MOF" archiviato in un Server di Pull, o una condivisione SMB deve avere un file associato ".checksum".</span><span class="sxs-lookup"><span data-stu-id="a1059-132">Each ".mof" file stored on a Pull Server, or SMB share needs to have an associated ".checksum" file.</span></span> <span data-ttu-id="a1059-133">Questo file consente ai client di sapere quando il file associato "MOF" è stato modificato e deve essere scaricato nuovamente.</span><span class="sxs-lookup"><span data-stu-id="a1059-133">This file lets clients know when the associated ".mof" file has changed and should be downloaded again.</span></span>

<span data-ttu-id="a1059-134">È possibile creare un **CheckSum** con il [New-DSCCheckSum](/powershell/module/psdesiredstateconfiguration/new-dscchecksum) cmdlet.</span><span class="sxs-lookup"><span data-stu-id="a1059-134">You can create a **CheckSum** with the [New-DSCCheckSum](/powershell/module/psdesiredstateconfiguration/new-dscchecksum) cmdlet.</span></span> <span data-ttu-id="a1059-135">È anche possibile eseguire `New-DSCCheckSum` in una directory di file usando il `-Path` parametro.</span><span class="sxs-lookup"><span data-stu-id="a1059-135">You can also run `New-DSCCheckSum` against a directory of files using the `-Path` parameter.</span></span> <span data-ttu-id="a1059-136">Se esiste già un checksum, è possibile applicarlo a essere ricreate con la `-Force` parametro.</span><span class="sxs-lookup"><span data-stu-id="a1059-136">If a checksum already exists, you can force it to be re-created with the `-Force` parameter.</span></span> <span data-ttu-id="a1059-137">Nell'esempio seguente specifica una directory contenente il file "MOF" nella sezione precedente e viene utilizzato il `-Force` parametro.</span><span class="sxs-lookup"><span data-stu-id="a1059-137">The following example specified a directory containing the ".mof" file from the previous section, and uses the `-Force` parameter.</span></span>

```powershell
New-DscChecksum -Path '.\' -Force
```

<span data-ttu-id="a1059-138">Non verrà visualizzato alcun output, ma si noterà ora un "<GUID or Configuration Name>. mof.checksum" file.</span><span class="sxs-lookup"><span data-stu-id="a1059-138">No output will be shown, but you should now see a "<GUID or Configuration Name>.mof.checksum" file.</span></span>

## <a name="where-to-store-mof-files-and-checksums"></a><span data-ttu-id="a1059-139">Posizione in cui archiviare i file MOF e i valori di checksum</span><span class="sxs-lookup"><span data-stu-id="a1059-139">Where to store MOF files and CheckSums</span></span>

### <a name="on-a-dsc-http-pull-server"></a><span data-ttu-id="a1059-140">In un Server di Pull HTTP DSC</span><span class="sxs-lookup"><span data-stu-id="a1059-140">On a DSC HTTP Pull Server</span></span>

<span data-ttu-id="a1059-141">Quando si configura il Server di Pull HTTP, come illustrato in [configurare un Server di Pull DSC HTTP](pullServer.md), si specificano directory per il **ModulePath** e **ConfigurationPath** chiavi.</span><span class="sxs-lookup"><span data-stu-id="a1059-141">When you set up your HTTP Pull Server, as explained in [Set up a DSC HTTP Pull Server](pullServer.md), you specify directories for the **ModulePath** and **ConfigurationPath** keys.</span></span> <span data-ttu-id="a1059-142">Il **ConfigurationPath** chiave indica dove devono essere archiviati i file "MOF".</span><span class="sxs-lookup"><span data-stu-id="a1059-142">The **ConfigurationPath** key indicates where any ".mof" files should be stored.</span></span> <span data-ttu-id="a1059-143">Il **ConfigurationPath** indica dove devono essere archiviati tutti i file "MOF" e ".checksum" file.</span><span class="sxs-lookup"><span data-stu-id="a1059-143">The **ConfigurationPath** indicates where any ".mof" files and ".checksum" files should be stored.</span></span>

```powershell
    xDscWebService PSDSCPullServer
    {
    ...
        ModulePath              = "$env:PROGRAMFILES\WindowsPowerShell\DscService\Modules"
        ConfigurationPath       = "$env:PROGRAMFILES\WindowsPowerShell\DscService\Configuration"
    ...
    }

```

### <a name="on-an-smb-share"></a><span data-ttu-id="a1059-144">In una condivisione SMB</span><span class="sxs-lookup"><span data-stu-id="a1059-144">On an SMB Share</span></span>

<span data-ttu-id="a1059-145">Quando si configura un Client di Pull per usare una condivisione SMB, si specifica un **ConfigurationRepositoryShare**.</span><span class="sxs-lookup"><span data-stu-id="a1059-145">When you set up a Pull Client to use an SMB share, you specify a **ConfigurationRepositoryShare**.</span></span> <span data-ttu-id="a1059-146">Tutti i file "MOF" e ".checksum" quindi devono essere archiviati nel **SourcePath** nella directory le **ConfigurationRepositoryShare** blocco.</span><span class="sxs-lookup"><span data-stu-id="a1059-146">All ".mof" files and ".checksum" files should then be stored in the **SourcePath** directory from the **ConfigurationRepositoryShare** block.</span></span>

```powershell
ConfigurationRepositoryShare SMBPullServer
{
    SourcePath = '\\SMBPullServer\Pull'
}
```

## <a name="next-steps"></a><span data-ttu-id="a1059-147">Passaggi successivi</span><span class="sxs-lookup"><span data-stu-id="a1059-147">Next Steps</span></span>

<span data-ttu-id="a1059-148">Successivamente, è consigliabile configurare i client di Pull per eseguire il pull di configurazione specificato.</span><span class="sxs-lookup"><span data-stu-id="a1059-148">Next, you will want to configure Pull Clients to pull the specified configuration.</span></span> <span data-ttu-id="a1059-149">Per altre informazioni, vedere una delle guide seguenti:</span><span class="sxs-lookup"><span data-stu-id="a1059-149">For more information, see one of the following guides:</span></span>

- [<span data-ttu-id="a1059-150">Configurare un Client di Pull usando un ID di configurazione (v4)</span><span class="sxs-lookup"><span data-stu-id="a1059-150">Set up a Pull Client using Configuration IDs (v4)</span></span>](pullClientConfigId4.md)
- [<span data-ttu-id="a1059-151">Configurare un Client di Pull usando un ID di configurazione (v5)</span><span class="sxs-lookup"><span data-stu-id="a1059-151">Set up a Pull Client using Configuration IDs (v5)</span></span>](pullClientConfigId.md)
- [<span data-ttu-id="a1059-152">Configurare un Client di Pull usando nomi di configurazione (v5)</span><span class="sxs-lookup"><span data-stu-id="a1059-152">Set up a Pull Client using Configuration Names (v5)</span></span>](pullClientConfigNames.md)

## <a name="see-also"></a><span data-ttu-id="a1059-153">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="a1059-153">See also</span></span>

- [<span data-ttu-id="a1059-154">Configurare un server di pull SMB DSC</span><span class="sxs-lookup"><span data-stu-id="a1059-154">Set up a DSC SMB Pull Server</span></span>](pullServerSmb.md)
- [<span data-ttu-id="a1059-155">Configurare un server di pull HTTP DSC</span><span class="sxs-lookup"><span data-stu-id="a1059-155">Set up a DSC HTTP Pull Server</span></span>](pullServer.md)
- [<span data-ttu-id="a1059-156">Pacchetti di caricamento delle risorse a un Server di Pull</span><span class="sxs-lookup"><span data-stu-id="a1059-156">Package and Upload Resources to a Pull Server</span></span>](package-upload-resources.md)
