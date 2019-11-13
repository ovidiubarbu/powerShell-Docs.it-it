---
title: Installazione di PowerShell Core in Windows
description: Informazioni sull'installazione di PowerShell Core in Windows
ms.date: 08/06/2018
ms.openlocfilehash: c06eba06e376c3f795ab9c0fae9270cf6cf8f2ce
ms.sourcegitcommit: 36e4c79afda2ce11febd93951e143687245f0b50
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 11/02/2019
ms.locfileid: "73444448"
---
# <a name="installing-powershell-core-on-windows"></a><span data-ttu-id="3a939-103">Installazione di PowerShell Core in Windows</span><span class="sxs-lookup"><span data-stu-id="3a939-103">Installing PowerShell Core on Windows</span></span>

<span data-ttu-id="3a939-104">Esistono diversi modi per installare PowerShell Core in Windows.</span><span class="sxs-lookup"><span data-stu-id="3a939-104">There are multiple ways to install PowerShell Core in Windows.</span></span>

> [!TIP]
> <span data-ttu-id="3a939-105">Se [.NET Core SDK](/dotnet/core/sdk) è già installato, è facile installare PowerShell come [strumento globale .NET](/dotnet/core/tools/global-tools).</span><span class="sxs-lookup"><span data-stu-id="3a939-105">If you already have the [.NET Core SDK](/dotnet/core/sdk) installed, it’s easy to install PowerShell as a [.NET Global tool](/dotnet/core/tools/global-tools).</span></span>
>
> ```
> dotnet tool install --global PowerShell
> ```

## <a name="prerequisites"></a><span data-ttu-id="3a939-106">Prerequisiti</span><span class="sxs-lookup"><span data-stu-id="3a939-106">Prerequisites</span></span>

<span data-ttu-id="3a939-107">Per abilitare la comunicazione remota di PowerShell tramite WS-Management, è necessario soddisfare i prerequisiti seguenti:</span><span class="sxs-lookup"><span data-stu-id="3a939-107">To enable PowerShell remoting over WSMan, the following prerequisites need to be met:</span></span>

- <span data-ttu-id="3a939-108">Installare [Universal C Runtime](https://www.microsoft.com/download/details.aspx?id=50410) nelle versioni di Windows precedenti a Windows 10.</span><span class="sxs-lookup"><span data-stu-id="3a939-108">Install the [Universal C Runtime](https://www.microsoft.com/download/details.aspx?id=50410) on Windows versions prior to Windows 10.</span></span> <span data-ttu-id="3a939-109">È disponibile tramite download diretto o Windows Update.</span><span class="sxs-lookup"><span data-stu-id="3a939-109">It is available via direct download or Windows Update.</span></span> <span data-ttu-id="3a939-110">Nei sistemi supportati, in cui sono state applicate tutte le patch (inclusi i pacchetti facoltativi), è già installato.</span><span class="sxs-lookup"><span data-stu-id="3a939-110">Fully patched (including optional packages), supported systems will already have this installed.</span></span>
- <span data-ttu-id="3a939-111">Installare Windows Management Framework (WMF) 4.0 o versione successiva in Windows 7 e Windows Server 2008 R2.</span><span class="sxs-lookup"><span data-stu-id="3a939-111">Install the Windows Management Framework (WMF) 4.0 or newer on Windows 7 and Windows Server 2008 R2.</span></span> <span data-ttu-id="3a939-112">Per altre informazioni su WMF, vedere la [panoramica su Windows Management Framework](/powershell/wmf/overview).</span><span class="sxs-lookup"><span data-stu-id="3a939-112">For more information about WMF, see [WMF Overview](/powershell/wmf/overview).</span></span>

## <a name="a-idmsi-installing-the-msi-package"></a><span data-ttu-id="3a939-113"><a id="msi" />Installazione del pacchetto MSI</span><span class="sxs-lookup"><span data-stu-id="3a939-113"><a id="msi" />Installing the MSI package</span></span>

<span data-ttu-id="3a939-114">Per installare PowerShell in un client Windows o Windows Server (funziona in Windows 7 SP1, Server 2008 R2 e versioni successive), scaricare il pacchetto MSI dalla pagina delle [versioni][releases] di GitHub.</span><span class="sxs-lookup"><span data-stu-id="3a939-114">To install PowerShell on a Windows client or Windows Server (works on Windows 7 SP1, Server 2008 R2, and later), download the MSI package from our GitHub [releases][releases] page.</span></span> <span data-ttu-id="3a939-115">Scorrere verso il basso fino alla sezione **Assets** della versione da installare.</span><span class="sxs-lookup"><span data-stu-id="3a939-115">Scroll down to the **Assets** section of the Release you want to install.</span></span> <span data-ttu-id="3a939-116">È possibile che la sezione Assets sia compressa, quindi potrebbe essere necessario fare clic per espanderla.</span><span class="sxs-lookup"><span data-stu-id="3a939-116">The Assets section may be collapsed, so you may need to click to expand it.</span></span>

<span data-ttu-id="3a939-117">Il file MSI è simile al seguente `PowerShell-<version>-win-<os-arch>.msi`</span><span class="sxs-lookup"><span data-stu-id="3a939-117">The MSI file looks like this - `PowerShell-<version>-win-<os-arch>.msi`</span></span>
<!-- TODO: should be updated to point to the Download Center as well -->

<span data-ttu-id="3a939-118">Dopo averlo scaricato, fare doppio clic sul programma di installazione e seguire i prompt.</span><span class="sxs-lookup"><span data-stu-id="3a939-118">Once downloaded, double-click the installer and follow the prompts.</span></span>

<span data-ttu-id="3a939-119">Il programma di installazione crea un collegamento nel menu Start di Windows.</span><span class="sxs-lookup"><span data-stu-id="3a939-119">The installer creates a shortcut in the Windows Start Menu.</span></span>

- <span data-ttu-id="3a939-120">Per impostazione predefinita, il pacchetto viene installato in `$env:ProgramFiles\PowerShell\<version>`</span><span class="sxs-lookup"><span data-stu-id="3a939-120">By default the package is installed to `$env:ProgramFiles\PowerShell\<version>`</span></span>
- <span data-ttu-id="3a939-121">È possibile avviare PowerShell tramite il menu Start o `$env:ProgramFiles\PowerShell\<version>\pwsh.exe`</span><span class="sxs-lookup"><span data-stu-id="3a939-121">You can launch PowerShell via the Start Menu or `$env:ProgramFiles\PowerShell\<version>\pwsh.exe`</span></span>

### <a name="administrative-install-from-the-command-line"></a><span data-ttu-id="3a939-122">Installazione amministrativa dalla riga di comando</span><span class="sxs-lookup"><span data-stu-id="3a939-122">Administrative install from the command line</span></span>

<span data-ttu-id="3a939-123">I pacchetti MSI possono essere installati dalla riga di comando.</span><span class="sxs-lookup"><span data-stu-id="3a939-123">MSI packages can be installed from the command line.</span></span> <span data-ttu-id="3a939-124">Ciò consente agli amministratori di distribuire i pacchetti senza interazione con l'utente.</span><span class="sxs-lookup"><span data-stu-id="3a939-124">This allows administrators to deploy packages without user interaction.</span></span> <span data-ttu-id="3a939-125">Il pacchetto MSI per PowerShell include le proprietà seguenti per controllare le opzioni di installazione:</span><span class="sxs-lookup"><span data-stu-id="3a939-125">The MSI package for PowerShell includes the following properties to control the installation options:</span></span>

- <span data-ttu-id="3a939-126">**ADD_EXPLORER_CONTEXT_MENU_OPENPOWERSHELL** - Questa proprietà controlla l'opzione per aggiungere la voce **Apri PowerShell** al menu di scelta rapida in Esplora risorse.</span><span class="sxs-lookup"><span data-stu-id="3a939-126">**ADD_EXPLORER_CONTEXT_MENU_OPENPOWERSHELL** - This property controls the option for adding the **Open PowerShell** item to the context menu in Windows Explorer.</span></span>
- <span data-ttu-id="3a939-127">**ENABLE_PSREMOTING** - Questa proprietà controlla l'opzione per l'abilitazione della comunicazione remota di PowerShell durante l'installazione.</span><span class="sxs-lookup"><span data-stu-id="3a939-127">**ENABLE_PSREMOTING** - This property controls the option for enabling PowerShell remoting during installation.</span></span>
- <span data-ttu-id="3a939-128">**REGISTER_MANIFEST** - Questa proprietà controlla l'opzione per registrare il manifesto di registrazione degli eventi di Windows.</span><span class="sxs-lookup"><span data-stu-id="3a939-128">**REGISTER_MANIFEST** - This property controls the option for registering the Windows Event Logging manifest.</span></span>

<span data-ttu-id="3a939-129">Negli esempi seguenti viene illustrato come installare PowerShell Core in modo invisibile all'utente con tutte le opzioni di installazione abilitate.</span><span class="sxs-lookup"><span data-stu-id="3a939-129">The following examples shows how to silently install PowerShell Core with all the install options enabled.</span></span>

```powershell
msiexec.exe /package PowerShell-<version>-win-<os-arch>.msi /quiet ADD_EXPLORER_CONTEXT_MENU_OPENPOWERSHELL=1 ENABLE_PSREMOTING=1 REGISTER_MANIFEST=1
```

<span data-ttu-id="3a939-130">Per un elenco completo delle opzioni della riga di comando per Msiexec.exe, vedere [Opzioni della riga di comando](/windows/desktop/Msi/command-line-options).</span><span class="sxs-lookup"><span data-stu-id="3a939-130">For a full list of command line options for Msiexec.exe, see [Command line options](/windows/desktop/Msi/command-line-options).</span></span>

## <a name="a-idzip-installing-the-zip-package"></a><span data-ttu-id="3a939-131"><a id="zip" />Installazione del pacchetto ZIP</span><span class="sxs-lookup"><span data-stu-id="3a939-131"><a id="zip" />Installing the ZIP package</span></span>

<span data-ttu-id="3a939-132">Sono disponibili archivi ZIP di file binari di PowerShell per abilitare scenari di distribuzione avanzati.</span><span class="sxs-lookup"><span data-stu-id="3a939-132">PowerShell binary ZIP archives are provided to enable advanced deployment scenarios.</span></span> <span data-ttu-id="3a939-133">Si noti che quando si usa l'archivio ZIP, non viene eseguito il controllo dei prerequisiti come nel pacchetto MSI.</span><span class="sxs-lookup"><span data-stu-id="3a939-133">Be noted that when using the ZIP archive, you won't get the prerequisites check as in the MSI package.</span></span> <span data-ttu-id="3a939-134">Per il corretto funzionamento della comunicazione remota su WSMan, verificare che siano soddisfatti i [prerequisiti](#prerequisites).</span><span class="sxs-lookup"><span data-stu-id="3a939-134">For remoting over WSMan to work properly, ensure that you have met the [prerequisites](#prerequisites).</span></span>

## <a name="deploying-on-windows-iot"></a><span data-ttu-id="3a939-135">Distribuzione in Windows IoT</span><span class="sxs-lookup"><span data-stu-id="3a939-135">Deploying on Windows IoT</span></span>

<span data-ttu-id="3a939-136">Windows IoT include già Windows PowerShell, che verrà usato per distribuire PowerShell Core 6.</span><span class="sxs-lookup"><span data-stu-id="3a939-136">Windows IoT already comes with Windows PowerShell which we will use to deploy PowerShell Core 6.</span></span>

1. <span data-ttu-id="3a939-137">Creare `PSSession` per il dispositivo di destinazione</span><span class="sxs-lookup"><span data-stu-id="3a939-137">Create `PSSession` to target device</span></span>

   ```powershell
   $s = New-PSSession -ComputerName <deviceIp> -Credential Administrator
   ```

2. <span data-ttu-id="3a939-138">Copiare il pacchetto ZIP nel dispositivo</span><span class="sxs-lookup"><span data-stu-id="3a939-138">Copy the ZIP package to the device</span></span>

   ```powershell
   # change the destination to however you had partitioned it with sufficient
   # space for the zip and the unzipped contents
   # the path should be local to the device
   Copy-Item .\PowerShell-<version>-win-<os-arch>.zip -Destination u:\users\administrator\Downloads -ToSession $s
   ```

3. <span data-ttu-id="3a939-139">Connettersi al dispositivo ed espandere l'archivio</span><span class="sxs-lookup"><span data-stu-id="3a939-139">Connect to the device and expand the archive</span></span>

   ```powershell
   Enter-PSSession $s
   Set-Location u:\users\administrator\downloads
   Expand-Archive .\PowerShell-<version>-win-<os-arch>.zip
   ```

4. <span data-ttu-id="3a939-140">Configurare la comunicazione remota con PowerShell Core 6</span><span class="sxs-lookup"><span data-stu-id="3a939-140">Setup remoting to PowerShell Core 6</span></span>

   ```powershell
   Set-Location .\PowerShell-<version>-win-<os-arch>
   # Be sure to use the -PowerShellHome parameter otherwise it'll try to create a new
   # endpoint with Windows PowerShell 5.1
   .\Install-PowerShellRemoting.ps1 -PowerShellHome .
   # You'll get an error message and will be disconnected from the device because it has to restart WinRM
   ```

5. <span data-ttu-id="3a939-141">Connettersi all'endpoint di PowerShell Core 6 nel dispositivo</span><span class="sxs-lookup"><span data-stu-id="3a939-141">Connect to PowerShell Core 6 endpoint on device</span></span>

   ```powershell
   # Be sure to use the -Configuration parameter.  If you omit it, you will connect to Windows PowerShell 5.1
   Enter-PSSession -ComputerName <deviceIp> -Credential Administrator -Configuration powershell.<version>
   ```

## <a name="deploying-on-nano-server"></a><span data-ttu-id="3a939-142">Distribuzione in Nano Server</span><span class="sxs-lookup"><span data-stu-id="3a939-142">Deploying on Nano Server</span></span>

<span data-ttu-id="3a939-143">Queste istruzioni presuppongono che una versione di PowerShell sia già in esecuzione nell'immagine Nano Server e che sia stato generato da [Nano Server Image Builder](/windows-server/get-started/deploy-nano-server).</span><span class="sxs-lookup"><span data-stu-id="3a939-143">These instructions assume that a version of PowerShell is already running on the Nano Server image and that it has been generated by the [Nano Server Image Builder](/windows-server/get-started/deploy-nano-server).</span></span>
<span data-ttu-id="3a939-144">Nano Server è un sistema operativo "headless".</span><span class="sxs-lookup"><span data-stu-id="3a939-144">Nano Server is a "headless" OS.</span></span> <span data-ttu-id="3a939-145">È possibile distribuire i file binari di PowerShell Core usando due metodi diversi.</span><span class="sxs-lookup"><span data-stu-id="3a939-145">Core binaries can be deploy using two different methods.</span></span>

1. <span data-ttu-id="3a939-146">Offline: montare il disco rigido virtuale di Nano Server e decomprimere il contenuto del file ZIP nella posizione prescelta all'interno dell'immagine montata.</span><span class="sxs-lookup"><span data-stu-id="3a939-146">Offline - Mount the Nano Server VHD and unzip the contents of the zip file to your chosen location within the mounted image.</span></span>
2. <span data-ttu-id="3a939-147">Online: trasferire il file ZIP in una sessione di PowerShell e decomprimerlo nella posizione prescelta.</span><span class="sxs-lookup"><span data-stu-id="3a939-147">Online - Transfer the zip file over a PowerShell Session and unzip it in your chosen location.</span></span>

<span data-ttu-id="3a939-148">In entrambi i casi è necessario usare il pacchetto ZIP della versione x64 di Windows 10 ed eseguire i comandi all'interno di un'istanza di PowerShell come "amministratore".</span><span class="sxs-lookup"><span data-stu-id="3a939-148">In both cases, you will need the Windows 10 x64 ZIP release package and will need to run the commands within an "Administrator" PowerShell instance.</span></span>

### <a name="offline-deployment-of-powershell-core"></a><span data-ttu-id="3a939-149">Distribuzione offline di PowerShell Core</span><span class="sxs-lookup"><span data-stu-id="3a939-149">Offline Deployment of PowerShell Core</span></span>

1. <span data-ttu-id="3a939-150">Usare l'utilità ZIP preferita per decomprimere il pacchetto in una directory all'interno dell'immagine montata di Nano Server.</span><span class="sxs-lookup"><span data-stu-id="3a939-150">Use your favorite zip utility to unzip the package to a directory within the mounted Nano Server image.</span></span>
2. <span data-ttu-id="3a939-151">Smontare l'immagine e riavviarla.</span><span class="sxs-lookup"><span data-stu-id="3a939-151">Unmount the image and boot it.</span></span>
3. <span data-ttu-id="3a939-152">Connettersi all'istanza di Posta in arrivo di Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="3a939-152">Connect to the inbox instance of Windows PowerShell.</span></span>
4. <span data-ttu-id="3a939-153">Seguire le istruzioni per creare un endpoint di comunicazione remota usando un'[altra tecnica di istanza](../learn/remoting/wsman-remoting-in-powershell-core.md#executed-by-another-instance-of-powershell-on-behalf-of-the-instance-that-it-will-register).</span><span class="sxs-lookup"><span data-stu-id="3a939-153">Follow the instructions to create a remoting endpoint using the ["another instance technique"](../learn/remoting/wsman-remoting-in-powershell-core.md#executed-by-another-instance-of-powershell-on-behalf-of-the-instance-that-it-will-register).</span></span>

### <a name="online-deployment-of-powershell-core"></a><span data-ttu-id="3a939-154">Distribuzione online di PowerShell Core</span><span class="sxs-lookup"><span data-stu-id="3a939-154">Online Deployment of PowerShell Core</span></span>

<span data-ttu-id="3a939-155">La procedura seguente consente di eseguire la distribuzione di PowerShell Core in un'istanza in esecuzione di Nano Server e di configurarne l'endpoint remoto.</span><span class="sxs-lookup"><span data-stu-id="3a939-155">The following steps guide you through the deployment of PowerShell Core to a running instance of Nano Server and the configuration of its remote endpoint.</span></span>

- <span data-ttu-id="3a939-156">Connettersi all'istanza di Posta in arrivo di Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="3a939-156">Connect to the inbox instance of Windows PowerShell</span></span>

  ```powershell
  $session = New-PSSession -ComputerName <Nano Server IP address> -Credential <An Administrator account on the system>
  ```

- <span data-ttu-id="3a939-157">Copiare il file nell'istanza di Nano Server</span><span class="sxs-lookup"><span data-stu-id="3a939-157">Copy the file to the Nano Server instance</span></span>

  ```powershell
  Copy-Item <local PS Core download location>\powershell-<version>-win-x64.zip c:\ -ToSession $session
  ```

- <span data-ttu-id="3a939-158">Immettere la sessione</span><span class="sxs-lookup"><span data-stu-id="3a939-158">Enter the session</span></span>

  ```powershell
  Enter-PSSession $session
  ```

- <span data-ttu-id="3a939-159">Estrarre il file ZIP</span><span class="sxs-lookup"><span data-stu-id="3a939-159">Extract the ZIP file</span></span>

  ```powershell
  # Insert the appropriate version.
  Expand-Archive -Path C:\powershell-<version>-win-x64.zip -DestinationPath "C:\PowerShellCore_<version>"
  ```

- <span data-ttu-id="3a939-160">Perché la comunicazione remota si basi su WS-Management, seguire le istruzioni seguenti per creare un endpoint di comunicazione remota tramite un'[altra tecnica di istanza](../learn/remoting/WSMan-Remoting-in-PowerShell-Core.md#executed-by-another-instance-of-powershell-on-behalf-of-the-instance-that-it-will-register).</span><span class="sxs-lookup"><span data-stu-id="3a939-160">If you want WSMan-based remoting, follow the instructions to create a remoting endpoint using the ["another instance technique"](../learn/remoting/WSMan-Remoting-in-PowerShell-Core.md#executed-by-another-instance-of-powershell-on-behalf-of-the-instance-that-it-will-register).</span></span>

## <a name="how-to-create-a-remoting-endpoint"></a><span data-ttu-id="3a939-161">Come creare un endpoint di comunicazione remota</span><span class="sxs-lookup"><span data-stu-id="3a939-161">How to create a remoting endpoint</span></span>

<span data-ttu-id="3a939-162">PowerShell Core supporta il protocollo di comunicazione remota di PowerShell (PSRP) tramite WS-Management e SSH.</span><span class="sxs-lookup"><span data-stu-id="3a939-162">PowerShell Core supports the PowerShell Remoting Protocol (PSRP) over both WSMan and SSH.</span></span> <span data-ttu-id="3a939-163">Per altre informazioni, vedere:</span><span class="sxs-lookup"><span data-stu-id="3a939-163">For more information, see:</span></span>

- <span data-ttu-id="3a939-164">[Comunicazione remota di PowerShell su SSH][ssh-remoting]</span><span class="sxs-lookup"><span data-stu-id="3a939-164">[SSH Remoting in PowerShell Core][ssh-remoting]</span></span>
- <span data-ttu-id="3a939-165">[Comunicazione remota di WS-Management in PowerShell Core][wsman-remoting]</span><span class="sxs-lookup"><span data-stu-id="3a939-165">[WSMan Remoting in PowerShell Core][wsman-remoting]</span></span>

<!-- [download-center]: TODO -->

[releases]: https://github.com/PowerShell/PowerShell/releases
[ssh-remoting]: ../learn/remoting/SSH-Remoting-in-PowerShell-Core.md
[wsman-remoting]: ../learn/remoting/WSMan-Remoting-in-PowerShell-Core.md
[AppVeyor]: https://ci.appveyor.com/project/PowerShell/powershell
