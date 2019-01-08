---
ms.date: 12/12/2018
keywords: dsc,powershell,configurazione,installazione
title: Pacchetti di caricamento delle risorse a un Server di Pull
ms.openlocfilehash: 29a62f96393a53c9e7da57a5e51732dcb0937194
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MTE95
ms.contentlocale: it-IT
ms.lasthandoff: 12/14/2018
ms.locfileid: "53401237"
---
# <a name="package-and-upload-resources-to-a-pull-server"></a><span data-ttu-id="665ed-103">Pacchetti di caricamento delle risorse a un Server di Pull</span><span class="sxs-lookup"><span data-stu-id="665ed-103">Package and Upload Resources to a Pull Server</span></span>

<span data-ttu-id="665ed-104">Le sezioni seguenti presuppongono che già stato impostato in un Server di Pull.</span><span class="sxs-lookup"><span data-stu-id="665ed-104">The sections below assume that you have already set up a Pull Server.</span></span> <span data-ttu-id="665ed-105">Se non è stato configurato il Server di Pull, è possibile usare le guide seguenti:</span><span class="sxs-lookup"><span data-stu-id="665ed-105">If you have not set up your Pull Server, you can use the following guides:</span></span>

- [<span data-ttu-id="665ed-106">Configurare un server di pull SMB DSC</span><span class="sxs-lookup"><span data-stu-id="665ed-106">Set up a DSC SMB Pull Server</span></span>](pullServerSmb.md)
- [<span data-ttu-id="665ed-107">Configurare un server di pull HTTP DSC</span><span class="sxs-lookup"><span data-stu-id="665ed-107">Set up a DSC HTTP Pull Server</span></span>](pullServer.md)

<span data-ttu-id="665ed-108">Ogni nodo di destinazione può essere configurato per scaricare le configurazioni, risorse e anche segnalare lo stato.</span><span class="sxs-lookup"><span data-stu-id="665ed-108">Each target node can be configured to download configurations, resources, and even report its status.</span></span> <span data-ttu-id="665ed-109">Questo articolo illustrerà come caricare risorse in modo che siano disponibili per essere scaricato e configurare i client per scaricare automaticamente le risorse.</span><span class="sxs-lookup"><span data-stu-id="665ed-109">This article will show you how to upload resources so they are available to be downloaded, and configure clients to download resources automatically.</span></span> <span data-ttu-id="665ed-110">Quando il nodo riceve una configurazione assegnata, attraverso **Pull** oppure **Push** (v5), scarica automaticamente le risorse richieste dalla configurazione dal percorso specificato in Gestione configurazione locale.</span><span class="sxs-lookup"><span data-stu-id="665ed-110">When the Node's receives an assigned Configuration, through **Pull** or **Push** (v5), it automatically downloads any resources required by the Configuration from the location specified in the LCM.</span></span>

## <a name="package-resource-modules"></a><span data-ttu-id="665ed-111">Moduli delle risorse del pacchetto</span><span class="sxs-lookup"><span data-stu-id="665ed-111">Package Resource Modules</span></span>

<span data-ttu-id="665ed-112">Ogni risorsa disponibile per un client di scaricare deve essere archiviato in un file "ZIP".</span><span class="sxs-lookup"><span data-stu-id="665ed-112">Each resource available for a client to download must be stored in a ".zip" file.</span></span> <span data-ttu-id="665ed-113">L'esempio seguente verrà illustra i passaggi necessari usando il [xPSDesiredStateConfiguration](https://www.powershellgallery.com/packages/xPSDesiredStateConfiguration/8.4.0.0) risorsa.</span><span class="sxs-lookup"><span data-stu-id="665ed-113">The example below will show the required steps using the [xPSDesiredStateConfiguration](https://www.powershellgallery.com/packages/xPSDesiredStateConfiguration/8.4.0.0) resource.</span></span>

> [!NOTE]
> <span data-ttu-id="665ed-114">Se si dispone di tutti i client che usano PowerShell 4.0, si sarà necessario flaten la struttura di cartelle di risorse e rimuovere eventuali cartelle della versione.</span><span class="sxs-lookup"><span data-stu-id="665ed-114">If you have any clients using PowerShell 4.0, you will need to flaten the resource folder structure and remove any version folders.</span></span> <span data-ttu-id="665ed-115">Per altre informazioni, vedere [più versioni di risorse](../configurations/import-dscresource.md#multiple-resource-versions).</span><span class="sxs-lookup"><span data-stu-id="665ed-115">For more information, see [Multiple Resource Versions](../configurations/import-dscresource.md#multiple-resource-versions).</span></span>

<span data-ttu-id="665ed-116">È possibile comprimere la directory delle risorse usando qualsiasi utilità, script o metodo che si preferisce.</span><span class="sxs-lookup"><span data-stu-id="665ed-116">You can compress the resource directory using any utility, script, or method that you prefer.</span></span> <span data-ttu-id="665ed-117">In Windows, è possibile *destro* nella directory "xPSDesiredStateConfiguration" e selezionare "Invia a", quindi "Cartella compressa".</span><span class="sxs-lookup"><span data-stu-id="665ed-117">In Windows, you can *right-click* on the "xPSDesiredStateConfiguration" directory, and select "Send To", then "Compressed Folder".</span></span>

![Fare clic con il pulsante destro del mouse](../media/right-click.gif)

### <a name="naming-the-resource-archive"></a><span data-ttu-id="665ed-119">L'archivio di risorse di denominazione</span><span class="sxs-lookup"><span data-stu-id="665ed-119">Naming the Resource Archive</span></span>

<span data-ttu-id="665ed-120">L'archivio di risorse deve essere denominato con il formato seguente:</span><span class="sxs-lookup"><span data-stu-id="665ed-120">The Resource archive needs to be named with the following format:</span></span>

```
{ModuleName}_{Version}.zip
```

<span data-ttu-id="665ed-121">Nell'esempio precedente, "xPSDesiredStateConfiguration.zip" deve essere rinominato "xPSDesiredStateConfiguration_8.4.4.0.zip".</span><span class="sxs-lookup"><span data-stu-id="665ed-121">In the example above, "xPSDesiredStateConfiguration.zip" should be renamed "xPSDesiredStateConfiguration_8.4.4.0.zip".</span></span>

### <a name="create-checksums"></a><span data-ttu-id="665ed-122">Creare i valori di checksum</span><span class="sxs-lookup"><span data-stu-id="665ed-122">Create CheckSums</span></span>

<span data-ttu-id="665ed-123">Dopo aver compresso ed rinominato il modulo di risorse, è necessario creare un **CheckSum**.</span><span class="sxs-lookup"><span data-stu-id="665ed-123">Once the Resource module has been compressed and renamed, you need to create a **CheckSum**.</span></span>  <span data-ttu-id="665ed-124">Il **CheckSum** viene usato, da Gestione configurazione locale nel client, per determinare se la risorsa è stata modificata e deve essere scaricato nuovamente.</span><span class="sxs-lookup"><span data-stu-id="665ed-124">The **CheckSum** is used, by the LCM on the client, to determine if the resource has been changed, and needs to be downloaded again.</span></span> <span data-ttu-id="665ed-125">È possibile creare un **CheckSum** con il [New-DSCCheckSum](/powershell/module/PSDesiredStateConfiguration/New-DSCCheckSum) cmdlet come mostrato nell'esempio seguente.</span><span class="sxs-lookup"><span data-stu-id="665ed-125">You can create a **CheckSum** with the [New-DSCCheckSum](/powershell/module/PSDesiredStateConfiguration/New-DSCCheckSum) cmdlet, as shown in the example below.</span></span>

```powershell
New-DscChecksum -Path .\xPSDesiredStateConfiguration_8.4.4.0.zip
```

<span data-ttu-id="665ed-126">Non verrà visualizzato alcun output, ma si noterà ora un "xPSDesiredStateConfiguration_8.4.4.0.zip.checksum".</span><span class="sxs-lookup"><span data-stu-id="665ed-126">No output will be shown, but you should now see a "xPSDesiredStateConfiguration_8.4.4.0.zip.checksum".</span></span> <span data-ttu-id="665ed-127">È anche possibile eseguire `New-DSCCheckSum` in una directory di file usando il `-Path` parametro.</span><span class="sxs-lookup"><span data-stu-id="665ed-127">You can also run `New-DSCCheckSum` against a directory of files using the `-Path` parameter.</span></span> <span data-ttu-id="665ed-128">Se esiste già un checksum, è possibile applicarlo a essere ricreate con la `-Force` parametro.</span><span class="sxs-lookup"><span data-stu-id="665ed-128">If a checksum already exists, you can force it to be re-created with the `-Force` parameter.</span></span>

### <a name="where-to-store-resource-archives"></a><span data-ttu-id="665ed-129">Posizione in cui archiviare gli archivi di risorse</span><span class="sxs-lookup"><span data-stu-id="665ed-129">Where to store Resource Archives</span></span>

#### <a name="on-a-dsc-http-pull-server"></a><span data-ttu-id="665ed-130">In un Server di Pull HTTP DSC</span><span class="sxs-lookup"><span data-stu-id="665ed-130">On a DSC HTTP Pull Server</span></span>

<span data-ttu-id="665ed-131">Quando si configura il Server di Pull HTTP, come illustrato in [configurare un Server di Pull DSC HTTP](pullServer.md), si specificano directory per il **ModulePath** e **ConfigurationPath** chiavi.</span><span class="sxs-lookup"><span data-stu-id="665ed-131">When you set up your HTTP Pull Server, as explained in [Set up a DSC HTTP Pull Server](pullServer.md), you specify directories for the **ModulePath** and **ConfigurationPath** keys.</span></span> <span data-ttu-id="665ed-132">Il **ConfigurationPath** chiave indica dove devono essere archiviati i file "MOF".</span><span class="sxs-lookup"><span data-stu-id="665ed-132">The **ConfigurationPath** key indicates where any ".mof" files should be stored.</span></span> <span data-ttu-id="665ed-133">Il **ModulePath** indica dove devono essere archiviati tutti i moduli risorsa DSC.</span><span class="sxs-lookup"><span data-stu-id="665ed-133">The **ModulePath** indicates where any DSC Resource Modules should be stored.</span></span>

```powershell
    xDscWebService PSDSCPullServer
    {
    ...
        ModulePath              = "$env:PROGRAMFILES\WindowsPowerShell\DscService\Modules"
        ConfigurationPath       = "$env:PROGRAMFILES\WindowsPowerShell\DscService\Configuration"
    ...
    }

```

#### <a name="on-an-smb-share"></a><span data-ttu-id="665ed-134">In una condivisione SMB</span><span class="sxs-lookup"><span data-stu-id="665ed-134">On an SMB Share</span></span>

<span data-ttu-id="665ed-135">Se è stata specificata una **ResourceRepositoryShare**, quando configurare il Client di Pull, archiviare gli archivi e checksum nel **SourcePath** nella directory di **ResourceRepositoryShare** blocco.</span><span class="sxs-lookup"><span data-stu-id="665ed-135">If you specified a **ResourceRepositoryShare**, when setting up your Pull Client, store archives and checksums in the **SourcePath** directory from the **ResourceRepositoryShare** block.</span></span>

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

<span data-ttu-id="665ed-136">Se è stata specificata solo una **ConfigurationRepositoryShare**, quando configurare il Client di Pull, archiviare gli archivi e checksum nel **SourcePath** nella directory di  **ConfigurationRepositoryShare** blocco.</span><span class="sxs-lookup"><span data-stu-id="665ed-136">If you specified only a **ConfigurationRepositoryShare**, when setting up your Pull Client, store archives and checksums in the **SourcePath** directory from the **ConfigurationRepositoryShare** block.</span></span>

```powershell
ConfigurationRepositoryShare SMBPullServer
{
    SourcePath = '\\SMBPullServer\Pull'
}
```

#### <a name="updating-resources"></a><span data-ttu-id="665ed-137">Aggiornamento delle risorse</span><span class="sxs-lookup"><span data-stu-id="665ed-137">Updating resources</span></span>

<span data-ttu-id="665ed-138">È possibile forzare un nodo per aggiornare le relative risorse modificando il numero di versione nel nome dell'archivio, o creando un nuovo checksum.</span><span class="sxs-lookup"><span data-stu-id="665ed-138">You can force a Node to update its resources by changing the version number in the archive's name, or by creating a new checksum.</span></span> <span data-ttu-id="665ed-139">Il Client di Pull deve ricercare le versioni più recenti delle risorse necessarie, nonché aggiornato i valori di checksum, quando viene aggiornata la gestione configurazione locale.</span><span class="sxs-lookup"><span data-stu-id="665ed-139">The Pull Client will check for newer versions of required resources, as well as updated checksums, when its LCM refreshes.</span></span>

## <a name="see-also"></a><span data-ttu-id="665ed-140">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="665ed-140">See also</span></span>

- [<span data-ttu-id="665ed-141">Configurare un server di pull SMB DSC</span><span class="sxs-lookup"><span data-stu-id="665ed-141">Set up a DSC SMB Pull Server</span></span>](pullServerSmb.md)
- [<span data-ttu-id="665ed-142">Configurare un server di pull HTTP DSC</span><span class="sxs-lookup"><span data-stu-id="665ed-142">Set up a DSC HTTP Pull Server</span></span>](pullServer.md)
