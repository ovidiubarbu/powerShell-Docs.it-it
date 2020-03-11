---
ms.date: 12/12/2018
keywords: dsc,powershell,configurazione,installazione
title: Creare un pacchetto e caricare le risorse in un server di pull
ms.openlocfilehash: 8aac343d7495ecda94ed76d1d97079397eecd65f
ms.sourcegitcommit: 01c60c0c97542dbad48ae34339cddbd813f1353b
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 03/04/2020
ms.locfileid: "78278503"
---
# <a name="package-and-upload-resources-to-a-pull-server"></a><span data-ttu-id="d4508-103">Creare un pacchetto e caricare le risorse in un server di pull</span><span class="sxs-lookup"><span data-stu-id="d4508-103">Package and Upload Resources to a Pull Server</span></span>

<span data-ttu-id="d4508-104">Le sezioni seguenti presuppongono che sia già stato configurato un server di pull.</span><span class="sxs-lookup"><span data-stu-id="d4508-104">The sections below assume that you have already set up a Pull Server.</span></span> <span data-ttu-id="d4508-105">Per configurare un server di pull, è possibile usare le guide seguenti:</span><span class="sxs-lookup"><span data-stu-id="d4508-105">If you have not set up your Pull Server, you can use the following guides:</span></span>

- [<span data-ttu-id="d4508-106">Configurare un server di pull SMB DSC</span><span class="sxs-lookup"><span data-stu-id="d4508-106">Set up a DSC SMB Pull Server</span></span>](pullServerSmb.md)
- [<span data-ttu-id="d4508-107">Configurare un server di pull HTTP DSC</span><span class="sxs-lookup"><span data-stu-id="d4508-107">Set up a DSC HTTP Pull Server</span></span>](pullServer.md)

<span data-ttu-id="d4508-108">Ogni nodo di destinazione può essere configurato in modo che possa scaricare configurazioni e risorse e persino segnalare il proprio stato.</span><span class="sxs-lookup"><span data-stu-id="d4508-108">Each target node can be configured to download configurations, resources, and even report its status.</span></span> <span data-ttu-id="d4508-109">Questo articolo illustra come caricare risorse in modo che siano disponibili per essere scaricate e come configurare i client per scaricare automaticamente le risorse.</span><span class="sxs-lookup"><span data-stu-id="d4508-109">This article will show you how to upload resources so they are available to be downloaded, and configure clients to download resources automatically.</span></span> <span data-ttu-id="d4508-110">Quando il nodo riceve una configurazione assegnata, attraverso **Pull** o **Push** (v5), scarica automaticamente le risorse richieste dalla configurazione dal percorso specificato in Gestione configurazione locale (LCM).</span><span class="sxs-lookup"><span data-stu-id="d4508-110">When the Node's receives an assigned Configuration, through **Pull** or **Push** (v5), it automatically downloads any resources required by the Configuration from the location specified in the LCM.</span></span>

## <a name="package-resource-modules"></a><span data-ttu-id="d4508-111">Creare il pacchetto dei moduli delle risorse</span><span class="sxs-lookup"><span data-stu-id="d4508-111">Package Resource Modules</span></span>

<span data-ttu-id="d4508-112">Ogni risorsa disponibile per il download da un client deve essere archiviata in un file "ZIP".</span><span class="sxs-lookup"><span data-stu-id="d4508-112">Each resource available for a client to download must be stored in a ".zip" file.</span></span> <span data-ttu-id="d4508-113">L'esempio seguente illustra i passaggi necessari usando la risorsa [xPSDesiredStateConfiguration](https://www.powershellgallery.com/packages/xPSDesiredStateConfiguration/8.4.0.0).</span><span class="sxs-lookup"><span data-stu-id="d4508-113">The example below will show the required steps using the [xPSDesiredStateConfiguration](https://www.powershellgallery.com/packages/xPSDesiredStateConfiguration/8.4.0.0) resource.</span></span>

> [!NOTE]
> <span data-ttu-id="d4508-114">Per eventuali client che usano PowerShell 4.0, sarà necessario appiattire la struttura di cartelle delle risorse e rimuovere eventuali cartelle della versione.</span><span class="sxs-lookup"><span data-stu-id="d4508-114">If you have any clients using PowerShell 4.0, you will need to flaten the resource folder structure and remove any version folders.</span></span> <span data-ttu-id="d4508-115">Per altre informazioni, vedere [Più versioni di risorse](../configurations/import-dscresource.md#multiple-resource-versions).</span><span class="sxs-lookup"><span data-stu-id="d4508-115">For more information, see [Multiple Resource Versions](../configurations/import-dscresource.md#multiple-resource-versions).</span></span>

<span data-ttu-id="d4508-116">È possibile comprimere la directory delle risorse usando qualsiasi utilità, script o metodo che si preferisce.</span><span class="sxs-lookup"><span data-stu-id="d4508-116">You can compress the resource directory using any utility, script, or method that you prefer.</span></span> <span data-ttu-id="d4508-117">In Windows, è possibile *fare clic con il pulsante destro del mouse* sulla directory "xPSDesiredStateConfiguration" e scegliere "Invia a", quindi "Cartella compressa".</span><span class="sxs-lookup"><span data-stu-id="d4508-117">In Windows, you can *right-click* on the "xPSDesiredStateConfiguration" directory, and select "Send To", then "Compressed Folder".</span></span>

![Fare clic con il pulsante destro del mouse](media/package-upload-resources/right-click.gif)

### <a name="naming-the-resource-archive"></a><span data-ttu-id="d4508-119">Assegnazione di un nome all'archivio delle risorse</span><span class="sxs-lookup"><span data-stu-id="d4508-119">Naming the Resource Archive</span></span>

<span data-ttu-id="d4508-120">L'archivio delle risorse deve essere denominato con il formato seguente:</span><span class="sxs-lookup"><span data-stu-id="d4508-120">The Resource archive needs to be named with the following format:</span></span>

```
{ModuleName}_{Version}.zip
```

<span data-ttu-id="d4508-121">Nell'esempio precedente, "xPSDesiredStateConfiguration.zip" dovrebbe essere rinominato "xPSDesiredStateConfiguration_8.4.4.0.zip".</span><span class="sxs-lookup"><span data-stu-id="d4508-121">In the example above, "xPSDesiredStateConfiguration.zip" should be renamed "xPSDesiredStateConfiguration_8.4.4.0.zip".</span></span>

### <a name="create-checksums"></a><span data-ttu-id="d4508-122">Creare i valori di checksum</span><span class="sxs-lookup"><span data-stu-id="d4508-122">Create CheckSums</span></span>

<span data-ttu-id="d4508-123">Dopo aver compresso e rinominato il modulo delle risorse, è necessario creare un **CheckSum**.</span><span class="sxs-lookup"><span data-stu-id="d4508-123">Once the Resource module has been compressed and renamed, you need to create a **CheckSum**.</span></span>  <span data-ttu-id="d4508-124">Il **CheckSum** viene usato da Gestione configurazione locale nel client per determinare se la risorsa è stata modificata e deve essere scaricata nuovamente.</span><span class="sxs-lookup"><span data-stu-id="d4508-124">The **CheckSum** is used, by the LCM on the client, to determine if the resource has been changed, and needs to be downloaded again.</span></span> <span data-ttu-id="d4508-125">È possibile creare un **CheckSum** con il cmdlet [New-DSCCheckSum](/powershell/module/PSDesiredStateConfiguration/New-DSCCheckSum), come mostrato nell'esempio seguente.</span><span class="sxs-lookup"><span data-stu-id="d4508-125">You can create a **CheckSum** with the [New-DSCCheckSum](/powershell/module/PSDesiredStateConfiguration/New-DSCCheckSum) cmdlet, as shown in the example below.</span></span>

```powershell
New-DscChecksum -Path .\xPSDesiredStateConfiguration_8.4.4.0.zip
```

<span data-ttu-id="d4508-126">Non verrà visualizzato alcun output, ma dovrebbe essere ora disponibile "xPSDesiredStateConfiguration_8.4.4.0.zip.checksum".</span><span class="sxs-lookup"><span data-stu-id="d4508-126">No output will be shown, but you should now see a "xPSDesiredStateConfiguration_8.4.4.0.zip.checksum".</span></span> <span data-ttu-id="d4508-127">È anche possibile eseguire `New-DSCCheckSum` in una directory di file usando il parametro `-Path`.</span><span class="sxs-lookup"><span data-stu-id="d4508-127">You can also run `New-DSCCheckSum` against a directory of files using the `-Path` parameter.</span></span> <span data-ttu-id="d4508-128">Se esiste già un checksum, è possibile forzare la nuova creazione con il parametro `-Force`.</span><span class="sxs-lookup"><span data-stu-id="d4508-128">If a checksum already exists, you can force it to be re-created with the `-Force` parameter.</span></span>

### <a name="where-to-store-resource-archives"></a><span data-ttu-id="d4508-129">Posizione in cui archiviare gli archivi di risorse</span><span class="sxs-lookup"><span data-stu-id="d4508-129">Where to store Resource Archives</span></span>

#### <a name="on-a-dsc-http-pull-server"></a><span data-ttu-id="d4508-130">In un server di pull HTTP DSC</span><span class="sxs-lookup"><span data-stu-id="d4508-130">On a DSC HTTP Pull Server</span></span>

<span data-ttu-id="d4508-131">Quando si configura il server di pull HTTP, come illustrato in [Configurare un server di pull HTTP DSC](pullServer.md), si specificano le directory per le chiavi **ModulePath** e **ConfigurationPath**.</span><span class="sxs-lookup"><span data-stu-id="d4508-131">When you set up your HTTP Pull Server, as explained in [Set up a DSC HTTP Pull Server](pullServer.md), you specify directories for the **ModulePath** and **ConfigurationPath** keys.</span></span> <span data-ttu-id="d4508-132">La chiave **ConfigurationPath** indica dove devono essere archiviati eventuali file "MOF".</span><span class="sxs-lookup"><span data-stu-id="d4508-132">The **ConfigurationPath** key indicates where any ".mof" files should be stored.</span></span> <span data-ttu-id="d4508-133">La chiave **ModulePath** indica dove devono essere archiviati eventuali moduli di risorse DSC.</span><span class="sxs-lookup"><span data-stu-id="d4508-133">The **ModulePath** indicates where any DSC Resource Modules should be stored.</span></span>

```powershell
    xDscWebService PSDSCPullServer
    {
    ...
        ModulePath              = "$env:PROGRAMFILES\WindowsPowerShell\DscService\Modules"
        ConfigurationPath       = "$env:PROGRAMFILES\WindowsPowerShell\DscService\Configuration"
    ...
    }

```

#### <a name="on-an-smb-share"></a><span data-ttu-id="d4508-134">In una condivisione SMB</span><span class="sxs-lookup"><span data-stu-id="d4508-134">On an SMB Share</span></span>

<span data-ttu-id="d4508-135">Se è stata specificata una **ResourceRepositoryShare** durante la configurazione del client di pull, archiviare gli archivi e i checksum nella directory **SourcePath** dal blocco **ResourceRepositoryShare**.</span><span class="sxs-lookup"><span data-stu-id="d4508-135">If you specified a **ResourceRepositoryShare**, when setting up your Pull Client, store archives and checksums in the **SourcePath** directory from the **ResourceRepositoryShare** block.</span></span>

```powershell
ConfigurationRepositoryShare SMBPullServer
{
    SourcePath = '\\SMBPullServer\Configurations'
}

ResourceRepositoryShare SMBResourceServer
{
    SourcePath = '\\SMBPullServer\Resources'
}
```

<span data-ttu-id="d4508-136">Se è stata specificata solo una **ConfigurationRepositoryShare** durante la configurazione del client di pull, archiviare gli archivi e i checksum nella directory **SourcePath** dal blocco **ConfigurationRepositoryShare**.</span><span class="sxs-lookup"><span data-stu-id="d4508-136">If you specified only a **ConfigurationRepositoryShare**, when setting up your Pull Client, store archives and checksums in the **SourcePath** directory from the **ConfigurationRepositoryShare** block.</span></span>

```powershell
ConfigurationRepositoryShare SMBPullServer
{
    SourcePath = '\\SMBPullServer\Pull'
}
```

#### <a name="updating-resources"></a><span data-ttu-id="d4508-137">Aggiornamento delle risorse</span><span class="sxs-lookup"><span data-stu-id="d4508-137">Updating resources</span></span>

<span data-ttu-id="d4508-138">È possibile forzare un nodo ad aggiornare le relative risorse modificando il numero di versione nel nome dell'archivio o creando un nuovo checksum.</span><span class="sxs-lookup"><span data-stu-id="d4508-138">You can force a Node to update its resources by changing the version number in the archive's name, or by creating a new checksum.</span></span> <span data-ttu-id="d4508-139">Il client di pull controllerà se sono disponibili versioni più recenti delle risorse necessarie, nonché checksum aggiornati, quando viene aggiornata l'istanza corrispondente di Gestione configurazione locale.</span><span class="sxs-lookup"><span data-stu-id="d4508-139">The Pull Client will check for newer versions of required resources, as well as updated checksums, when its LCM refreshes.</span></span>

## <a name="see-also"></a><span data-ttu-id="d4508-140">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="d4508-140">See also</span></span>

- [<span data-ttu-id="d4508-141">Configurare un server di pull SMB DSC</span><span class="sxs-lookup"><span data-stu-id="d4508-141">Set up a DSC SMB Pull Server</span></span>](pullServerSmb.md)
- [<span data-ttu-id="d4508-142">Configurare un server di pull HTTP DSC</span><span class="sxs-lookup"><span data-stu-id="d4508-142">Set up a DSC HTTP Pull Server</span></span>](pullServer.md)
