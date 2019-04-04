---
title: Installazione di PowerShell Core in Windows
description: Informazioni sull'installazione di PowerShell Core in Windows
ms.date: 08/06/2018
ms.openlocfilehash: 450a38a1ef2e2890059094774fcc3f2ad4fcda6e
ms.sourcegitcommit: 8dd4394cf867005a8b9ef0bb74b744c964fbc332
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 03/30/2019
ms.locfileid: "58748962"
---
# <a name="installing-powershell-core-on-windows"></a><span data-ttu-id="46824-103">Installazione di PowerShell Core in Windows</span><span class="sxs-lookup"><span data-stu-id="46824-103">Installing PowerShell Core on Windows</span></span>

## <a name="msi"></a><span data-ttu-id="46824-104">MSI</span><span class="sxs-lookup"><span data-stu-id="46824-104">MSI</span></span>

<span data-ttu-id="46824-105">Per installare PowerShell in un client Windows o Windows Server (funziona in Windows 7 SP1, Server 2008 R2 e versioni successive), scaricare il pacchetto MSI dalla pagina delle [versioni][] di GitHub.</span><span class="sxs-lookup"><span data-stu-id="46824-105">To install PowerShell on a Windows client or Windows Server (works on Windows 7 SP1, Server 2008 R2, and later), download the MSI package from our GitHub [releases][] page.</span></span>  <span data-ttu-id="46824-106">Scorrere verso il basso fino alla sezione **Assets** della versione da installare.</span><span class="sxs-lookup"><span data-stu-id="46824-106">Scroll down to the **Assets** section of the Release you want to install.</span></span>  <span data-ttu-id="46824-107">È possibile che la sezione Assets sia compressa, quindi potrebbe essere necessario fare clic per espanderla.</span><span class="sxs-lookup"><span data-stu-id="46824-107">The Assets section may be collapsed, so you may need to click to expand it.</span></span>

<span data-ttu-id="46824-108">Il file MSI è simile al seguente `PowerShell-<version>-win-<os-arch>.msi`</span><span class="sxs-lookup"><span data-stu-id="46824-108">The MSI file looks like this - `PowerShell-<version>-win-<os-arch>.msi`</span></span>
<!-- TODO: should be updated to point to the Download Center as well -->

<span data-ttu-id="46824-109">Dopo averlo scaricato, fare doppio clic sul programma di installazione e seguire i prompt.</span><span class="sxs-lookup"><span data-stu-id="46824-109">Once downloaded, double-click the installer and follow the prompts.</span></span>

<span data-ttu-id="46824-110">Nel menu Start dell'installazione è disponibile un collegamento.</span><span class="sxs-lookup"><span data-stu-id="46824-110">There is a shortcut placed in the Start Menu upon installation.</span></span>

- <span data-ttu-id="46824-111">Per impostazione predefinita, il pacchetto viene installato in `$env:ProgramFiles\PowerShell\<version>`</span><span class="sxs-lookup"><span data-stu-id="46824-111">By default the package is installed to `$env:ProgramFiles\PowerShell\<version>`</span></span>
- <span data-ttu-id="46824-112">È possibile avviare PowerShell tramite il menu Start o `$env:ProgramFiles\PowerShell\<version>\pwsh.exe`</span><span class="sxs-lookup"><span data-stu-id="46824-112">You can launch PowerShell via the Start Menu or `$env:ProgramFiles\PowerShell\<version>\pwsh.exe`</span></span>

### <a name="prerequisites"></a><span data-ttu-id="46824-113">Prerequisiti</span><span class="sxs-lookup"><span data-stu-id="46824-113">Prerequisites</span></span>

<span data-ttu-id="46824-114">Per abilitare la comunicazione remota di PowerShell tramite WS-Management, è necessario soddisfare i prerequisiti seguenti:</span><span class="sxs-lookup"><span data-stu-id="46824-114">To enable PowerShell remoting over WSMan, the following prerequisites need to be met:</span></span>

- <span data-ttu-id="46824-115">Installare [Universal C Runtime](https://www.microsoft.com/download/details.aspx?id=50410) nelle versioni di Windows precedenti a Windows 10.</span><span class="sxs-lookup"><span data-stu-id="46824-115">Install the [Universal C Runtime](https://www.microsoft.com/download/details.aspx?id=50410) on Windows versions prior to Windows 10.</span></span>
  <span data-ttu-id="46824-116">È disponibile tramite download diretto o Windows Update.</span><span class="sxs-lookup"><span data-stu-id="46824-116">It is available via direct download or Windows Update.</span></span>
  <span data-ttu-id="46824-117">Nei sistemi supportati, in cui sono state applicate tutte le patch (inclusi i pacchetti facoltativi), è già installato.</span><span class="sxs-lookup"><span data-stu-id="46824-117">Fully patched (including optional packages), supported systems will already have this installed.</span></span>
- <span data-ttu-id="46824-118">Installare Windows Management Framework (WMF) 4.0 o versione successiva in Windows 7 e Windows Server 2008 R2.</span><span class="sxs-lookup"><span data-stu-id="46824-118">Install the Windows Management Framework (WMF) 4.0 or newer on Windows 7 and Windows Server 2008 R2.</span></span>

## <a name="zip"></a><span data-ttu-id="46824-119">ZIP</span><span class="sxs-lookup"><span data-stu-id="46824-119">ZIP</span></span>

<span data-ttu-id="46824-120">Sono disponibili archivi ZIP di file binari di PowerShell per abilitare scenari di distribuzione avanzati.</span><span class="sxs-lookup"><span data-stu-id="46824-120">PowerShell binary ZIP archives are provided to enable advanced deployment scenarios.</span></span>
<span data-ttu-id="46824-121">Si noti che quando si usa l'archivio ZIP, non viene eseguito il controllo dei prerequisiti come nel pacchetto MSI.</span><span class="sxs-lookup"><span data-stu-id="46824-121">Be noted that when using the ZIP archive, you won't get the prerequisites check as in the MSI package.</span></span>
<span data-ttu-id="46824-122">Perché la comunicazione remota tramite WS-Management funzioni correttamente in versioni di Windows precedenti a Windows 10, è necessario assicurarsi che i [prerequisiti](#prerequisites) siano soddisfatti.</span><span class="sxs-lookup"><span data-stu-id="46824-122">So in order for remoting over WSMan to work properly on Windows versions prior to Windows 10, you need to make sure the [prerequisites](#prerequisites) are met.</span></span>

## <a name="deploying-on-windows-iot"></a><span data-ttu-id="46824-123">Distribuzione in Windows IoT</span><span class="sxs-lookup"><span data-stu-id="46824-123">Deploying on Windows IoT</span></span>

<span data-ttu-id="46824-124">Windows IoT include già Windows PowerShell, che verrà usato per distribuire PowerShell Core 6.</span><span class="sxs-lookup"><span data-stu-id="46824-124">Windows IoT already comes with Windows PowerShell which we will use to deploy PowerShell Core 6.</span></span>

1. <span data-ttu-id="46824-125">Creare `PSSession` per il dispositivo di destinazione</span><span class="sxs-lookup"><span data-stu-id="46824-125">Create `PSSession` to target device</span></span>

   ```powershell
   $s = New-PSSession -ComputerName <deviceIp> -Credential Administrator
   ```

2. <span data-ttu-id="46824-126">Copiare il pacchetto ZIP nel dispositivo</span><span class="sxs-lookup"><span data-stu-id="46824-126">Copy the ZIP package to the device</span></span>

   ```powershell
   # change the destination to however you had partitioned it with sufficient
   # space for the zip and the unzipped contents
   # the path should be local to the device
   Copy-Item .\PowerShell-<version>-win-<os-arch>.zip -Destination u:\users\administrator\Downloads -ToSession $s
   ```

3. <span data-ttu-id="46824-127">Connettersi al dispositivo ed espandere l'archivio</span><span class="sxs-lookup"><span data-stu-id="46824-127">Connect to the device and expand the archive</span></span>

   ```powershell
   Enter-PSSession $s
   Set-Location u:\users\administrator\downloads
   Expand-Archive .\PowerShell-<version>-win-<os-arch>.zip
   ```

4. <span data-ttu-id="46824-128">Configurare la comunicazione remota con PowerShell Core 6</span><span class="sxs-lookup"><span data-stu-id="46824-128">Setup remoting to PowerShell Core 6</span></span>

   ```powershell
   Set-Location .\PowerShell-<version>-win-<os-arch>
   # Be sure to use the -PowerShellHome parameter otherwise it'll try to create a new
   # endpoint with Windows PowerShell 5.1
   .\Install-PowerShellRemoting.ps1 -PowerShellHome .
   # You'll get an error message and will be disconnected from the device because it has to restart WinRM
   ```

5. <span data-ttu-id="46824-129">Connettersi all'endpoint di PowerShell Core 6 nel dispositivo</span><span class="sxs-lookup"><span data-stu-id="46824-129">Connect to PowerShell Core 6 endpoint on device</span></span>

   ```powershell
   # Be sure to use the -Configuration parameter.  If you omit it, you will connect to Windows PowerShell 5.1
   Enter-PSSession -ComputerName <deviceIp> -Credential Administrator -Configuration powershell.<version>
   ```

## <a name="deploying-on-nano-server"></a><span data-ttu-id="46824-130">Distribuzione in Nano Server</span><span class="sxs-lookup"><span data-stu-id="46824-130">Deploying on Nano Server</span></span>

<span data-ttu-id="46824-131">Queste istruzioni presuppongono che una versione di PowerShell sia già in esecuzione nell'immagine Nano Server e che sia stato generato da [Nano Server Image Builder](/windows-server/get-started/deploy-nano-server).</span><span class="sxs-lookup"><span data-stu-id="46824-131">These instructions assume that a version of PowerShell is already running on the Nano Server image and that it has been generated by the [Nano Server Image Builder](/windows-server/get-started/deploy-nano-server).</span></span>
<span data-ttu-id="46824-132">Nano Server è un sistema operativo "headless".</span><span class="sxs-lookup"><span data-stu-id="46824-132">Nano Server is a "headless" OS.</span></span> <span data-ttu-id="46824-133">È possibile distribuire i file binari di PowerShell Core usando due metodi diversi.</span><span class="sxs-lookup"><span data-stu-id="46824-133">Core binaries can be deploy using two different methods.</span></span>

1. <span data-ttu-id="46824-134">Offline: montare il disco rigido virtuale di Nano Server e decomprimere il contenuto del file ZIP nella posizione prescelta all'interno dell'immagine montata.</span><span class="sxs-lookup"><span data-stu-id="46824-134">Offline - Mount the Nano Server VHD and unzip the contents of the zip file to your chosen location within the mounted image.</span></span>
2. <span data-ttu-id="46824-135">Online: trasferire il file ZIP in una sessione di PowerShell e decomprimerlo nella posizione prescelta.</span><span class="sxs-lookup"><span data-stu-id="46824-135">Online - Transfer the zip file over a PowerShell Session and unzip it in your chosen location.</span></span>

<span data-ttu-id="46824-136">In entrambi i casi è necessario usare il pacchetto ZIP della versione x64 di Windows 10 ed eseguire i comandi all'interno di un'istanza di PowerShell come "amministratore".</span><span class="sxs-lookup"><span data-stu-id="46824-136">In both cases, you will need the Windows 10 x64 ZIP release package and will need to run the commands within an "Administrator" PowerShell instance.</span></span>

### <a name="offline-deployment-of-powershell-core"></a><span data-ttu-id="46824-137">Distribuzione offline di PowerShell Core</span><span class="sxs-lookup"><span data-stu-id="46824-137">Offline Deployment of PowerShell Core</span></span>

1. <span data-ttu-id="46824-138">Usare l'utilità ZIP preferita per decomprimere il pacchetto in una directory all'interno dell'immagine montata di Nano Server.</span><span class="sxs-lookup"><span data-stu-id="46824-138">Use your favorite zip utility to unzip the package to a directory within the mounted Nano Server image.</span></span>
2. <span data-ttu-id="46824-139">Smontare l'immagine e riavviarla.</span><span class="sxs-lookup"><span data-stu-id="46824-139">Unmount the image and boot it.</span></span>
3. <span data-ttu-id="46824-140">Connettersi all'istanza di Posta in arrivo di Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="46824-140">Connect to the inbox instance of Windows PowerShell.</span></span>
4. <span data-ttu-id="46824-141">Seguire le istruzioni per creare un endpoint di comunicazione remota usando un'[altra tecnica di istanza](../learn/remoting/wsman-remoting-in-powershell-core.md#executed-by-another-instance-of-powershell-on-behalf-of-the-instance-that-it-will-register).</span><span class="sxs-lookup"><span data-stu-id="46824-141">Follow the instructions to create a remoting endpoint using the ["another instance technique"](../learn/remoting/wsman-remoting-in-powershell-core.md#executed-by-another-instance-of-powershell-on-behalf-of-the-instance-that-it-will-register).</span></span>

### <a name="online-deployment-of-powershell-core"></a><span data-ttu-id="46824-142">Distribuzione online di PowerShell Core</span><span class="sxs-lookup"><span data-stu-id="46824-142">Online Deployment of PowerShell Core</span></span>

<span data-ttu-id="46824-143">La procedura seguente consente di eseguire la distribuzione di PowerShell Core in un'istanza in esecuzione di Nano Server e di configurarne l'endpoint remoto.</span><span class="sxs-lookup"><span data-stu-id="46824-143">The following steps guide you through the deployment of PowerShell Core to a running instance of Nano Server and the configuration of its remote endpoint.</span></span>

- <span data-ttu-id="46824-144">Connettersi all'istanza di Posta in arrivo di Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="46824-144">Connect to the inbox instance of Windows PowerShell</span></span>

  ```powershell
  $session = New-PSSession -ComputerName <Nano Server IP address> -Credential <An Administrator account on the system>
  ```

- <span data-ttu-id="46824-145">Copiare il file nell'istanza di Nano Server</span><span class="sxs-lookup"><span data-stu-id="46824-145">Copy the file to the Nano Server instance</span></span>

  ```powershell
  Copy-Item <local PS Core download location>\powershell-<version>-win-x64.zip c:\ -ToSession $session
  ```

- <span data-ttu-id="46824-146">Immettere la sessione</span><span class="sxs-lookup"><span data-stu-id="46824-146">Enter the session</span></span>

  ```powershell
  Enter-PSSession $session
  ```

- <span data-ttu-id="46824-147">Estrarre il file ZIP</span><span class="sxs-lookup"><span data-stu-id="46824-147">Extract the ZIP file</span></span>

  ```powershell
  # Insert the appropriate version.
  Expand-Archive -Path C:\powershell-<version>-win-x64.zip -DestinationPath "C:\PowerShellCore_<version>"
  ```

- <span data-ttu-id="46824-148">Perché la comunicazione remota si basi su WS-Management, seguire le istruzioni seguenti per creare un endpoint di comunicazione remota tramite un'[altra tecnica di istanza](../learn/remoting/WSMan-Remoting-in-PowerShell-Core.md#executed-by-another-instance-of-powershell-on-behalf-of-the-instance-that-it-will-register).</span><span class="sxs-lookup"><span data-stu-id="46824-148">If you want WSMan-based remoting, follow the instructions to create a remoting endpoint using the ["another instance technique"](../learn/remoting/WSMan-Remoting-in-PowerShell-Core.md#executed-by-another-instance-of-powershell-on-behalf-of-the-instance-that-it-will-register).</span></span>

## <a name="instructions-to-create-a-remoting-endpoint"></a><span data-ttu-id="46824-149">Istruzioni per creare un endpoint di comunicazione remota</span><span class="sxs-lookup"><span data-stu-id="46824-149">Instructions to Create a Remoting Endpoint</span></span>

<span data-ttu-id="46824-150">PowerShell Core supporta il protocollo di comunicazione remota di PowerShell (PSRP) tramite WS-Management e SSH.</span><span class="sxs-lookup"><span data-stu-id="46824-150">PowerShell Core supports the PowerShell Remoting Protocol (PSRP) over both WSMan and SSH.</span></span>
<span data-ttu-id="46824-151">Per altre informazioni, vedere:</span><span class="sxs-lookup"><span data-stu-id="46824-151">For more information, see:</span></span>

- <span data-ttu-id="46824-152">[SSH Remoting in PowerShell Core][ssh-remoting] (Comunicazione remota SSH in PowerShell Core)</span><span class="sxs-lookup"><span data-stu-id="46824-152">[SSH Remoting in PowerShell Core][ssh-remoting]</span></span>
- <span data-ttu-id="46824-153">[WSMan Remoting in PowerShell Core][wsman-remoting] (Comunicazione remota WS-Management in PowerShell Core)</span><span class="sxs-lookup"><span data-stu-id="46824-153">[WSMan Remoting in PowerShell Core][wsman-remoting]</span></span>

## <a name="artifact-installation-instructions"></a><span data-ttu-id="46824-154">Istruzioni di installazione dell'artefatto</span><span class="sxs-lookup"><span data-stu-id="46824-154">Artifact Installation Instructions</span></span>

<span data-ttu-id="46824-155">Un archivio con i bit di CoreCL viene pubblicato per ogni build CI tramite [AppVeyor][].</span><span class="sxs-lookup"><span data-stu-id="46824-155">We publish an archive with CoreCLR bits on every CI build with [AppVeyor][].</span></span>

<span data-ttu-id="46824-156">Per installare PowerShell Core dall'artefatto CoreCLR:</span><span class="sxs-lookup"><span data-stu-id="46824-156">To install PowerShell Core from the CoreCLR Artifact:</span></span>

1. <span data-ttu-id="46824-157">Scaricare il pacchetto ZIP dalla scheda **artifacts** (artefatti) della build specifica.</span><span class="sxs-lookup"><span data-stu-id="46824-157">Download ZIP package from **artifacts** tab of the particular build.</span></span>
2. <span data-ttu-id="46824-158">Sbloccare il file ZIP: fare clic con il pulsante destro del mouse in Esplora file -> Proprietà -> selezionare la casella "Sblocca" -> applicare</span><span class="sxs-lookup"><span data-stu-id="46824-158">Unblock ZIP file: right-click in File Explorer -> Properties -> check 'Unblock' box -> apply</span></span>
3. <span data-ttu-id="46824-159">Estrarre il file ZIP nella directory `bin`</span><span class="sxs-lookup"><span data-stu-id="46824-159">Extract zip file to `bin` directory</span></span>
4. `./bin/pwsh.exe`

<!-- [download-center]: TODO -->

[versioni]: https://github.com/PowerShell/PowerShell/releases
[releases]: https://github.com/PowerShell/PowerShell/releases
[ssh-remoting]: ../core-powershell/SSH-Remoting-in-PowerShell-Core.md
[wsman-remoting]: ../core-powershell/WSMan-Remoting-in-PowerShell-Core.md
[AppVeyor]: https://ci.appveyor.com/project/PowerShell/powershell
