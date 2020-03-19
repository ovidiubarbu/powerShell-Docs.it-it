---
title: Installazione di PowerShell in Windows
description: Informazioni sull'installazione di PowerShell in Windows
ms.date: 08/06/2018
ms.openlocfilehash: df05a16bcf7a81d43d24535e50517fa217f82e7a
ms.sourcegitcommit: c97dcf1e00ef540e7464c36c88f841474060044c
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 03/15/2020
ms.locfileid: "79402418"
---
# <a name="installing-powershell-on-windows"></a><span data-ttu-id="cb928-103">Installazione di PowerShell in Windows</span><span class="sxs-lookup"><span data-stu-id="cb928-103">Installing PowerShell on Windows</span></span>

<span data-ttu-id="cb928-104">Esistono diversi modi per installare PowerShell in Windows.</span><span class="sxs-lookup"><span data-stu-id="cb928-104">There are multiple ways to install PowerShell in Windows.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="cb928-105">Prerequisiti</span><span class="sxs-lookup"><span data-stu-id="cb928-105">Prerequisites</span></span>

<span data-ttu-id="cb928-106">Per abilitare la comunicazione remota di PowerShell tramite WS-Management, è necessario soddisfare i prerequisiti seguenti:</span><span class="sxs-lookup"><span data-stu-id="cb928-106">To enable PowerShell remoting over WSMan, the following prerequisites need to be met:</span></span>

- <span data-ttu-id="cb928-107">Installare [Universal C Runtime](https://www.microsoft.com/download/details.aspx?id=50410) nelle versioni di Windows precedenti a Windows 10.</span><span class="sxs-lookup"><span data-stu-id="cb928-107">Install the [Universal C Runtime](https://www.microsoft.com/download/details.aspx?id=50410) on Windows versions prior to Windows 10.</span></span> <span data-ttu-id="cb928-108">È disponibile tramite download diretto o Windows Update.</span><span class="sxs-lookup"><span data-stu-id="cb928-108">It is available via direct download or Windows Update.</span></span> <span data-ttu-id="cb928-109">Nei sistemi supportati, in cui sono state applicate tutte le patch (inclusi i pacchetti facoltativi), è già installato.</span><span class="sxs-lookup"><span data-stu-id="cb928-109">Fully patched (including optional packages), supported systems will already have this installed.</span></span>
- <span data-ttu-id="cb928-110">Installare Windows Management Framework (WMF) 4.0 o versione successiva in Windows 7 e Windows Server 2008 R2.</span><span class="sxs-lookup"><span data-stu-id="cb928-110">Install the Windows Management Framework (WMF) 4.0 or newer on Windows 7 and Windows Server 2008 R2.</span></span> <span data-ttu-id="cb928-111">Per altre informazioni su WMF, vedere la [panoramica su Windows Management Framework](/powershell/scripting/wmf/overview).</span><span class="sxs-lookup"><span data-stu-id="cb928-111">For more information about WMF, see [WMF Overview](/powershell/scripting/wmf/overview).</span></span>

## <a name="a-idmsi-installing-the-msi-package"></a><span data-ttu-id="cb928-112"><a id="msi" />Installazione del pacchetto MSI</span><span class="sxs-lookup"><span data-stu-id="cb928-112"><a id="msi" />Installing the MSI package</span></span>

<span data-ttu-id="cb928-113">Per installare PowerShell in un client Windows o Windows Server (funziona in Windows 7 SP1, Server 2008 R2 e versioni successive), scaricare il pacchetto MSI dalla pagina delle [versioni][releases] di GitHub.</span><span class="sxs-lookup"><span data-stu-id="cb928-113">To install PowerShell on a Windows client or Windows Server (works on Windows 7 SP1, Server 2008 R2, and later), download the MSI package from our GitHub [releases][releases] page.</span></span> <span data-ttu-id="cb928-114">Scorrere verso il basso fino alla sezione **Assets** della versione da installare.</span><span class="sxs-lookup"><span data-stu-id="cb928-114">Scroll down to the **Assets** section of the Release you want to install.</span></span> <span data-ttu-id="cb928-115">È possibile che la sezione Assets sia compressa, quindi potrebbe essere necessario fare clic per espanderla.</span><span class="sxs-lookup"><span data-stu-id="cb928-115">The Assets section may be collapsed, so you may need to click to expand it.</span></span>

<span data-ttu-id="cb928-116">Il file MSI è simile al seguente `PowerShell-<version>-win-<os-arch>.msi`</span><span class="sxs-lookup"><span data-stu-id="cb928-116">The MSI file looks like this - `PowerShell-<version>-win-<os-arch>.msi`</span></span>

<span data-ttu-id="cb928-117">Dopo averlo scaricato, fare doppio clic sul programma di installazione e seguire i prompt.</span><span class="sxs-lookup"><span data-stu-id="cb928-117">Once downloaded, double-click the installer and follow the prompts.</span></span>

<span data-ttu-id="cb928-118">Il programma di installazione crea un collegamento nel menu Start di Windows.</span><span class="sxs-lookup"><span data-stu-id="cb928-118">The installer creates a shortcut in the Windows Start Menu.</span></span>

- <span data-ttu-id="cb928-119">Per impostazione predefinita, il pacchetto viene installato in `$env:ProgramFiles\PowerShell\<version>`</span><span class="sxs-lookup"><span data-stu-id="cb928-119">By default the package is installed to `$env:ProgramFiles\PowerShell\<version>`</span></span>
- <span data-ttu-id="cb928-120">È possibile avviare PowerShell tramite il menu Start o `$env:ProgramFiles\PowerShell\<version>\pwsh.exe`</span><span class="sxs-lookup"><span data-stu-id="cb928-120">You can launch PowerShell via the Start Menu or `$env:ProgramFiles\PowerShell\<version>\pwsh.exe`</span></span>

> [!NOTE]
> <span data-ttu-id="cb928-121">PowerShell 7 viene installato in una nuova directory ed eseguito side-by-side con Windows PowerShell 5.1.</span><span class="sxs-lookup"><span data-stu-id="cb928-121">PowerShell 7 installs to a new directory and runs side-by-side with Windows PowerShell 5.1.</span></span> <span data-ttu-id="cb928-122">Per PowerShell Core 6.x, PowerShell 7 è un aggiornamento sul posto che rimuove PowerShell Core 6.x.</span><span class="sxs-lookup"><span data-stu-id="cb928-122">For PowerShell Core 6.x, PowerShell 7 is an in-place upgrade that removes PowerShell Core 6.x.</span></span>
>
> - <span data-ttu-id="cb928-123">PowerShell 7 è installato in `%programfiles%\PowerShell\7`</span><span class="sxs-lookup"><span data-stu-id="cb928-123">PowerShell 7 is installed to `%programfiles%\PowerShell\7`</span></span>
> - <span data-ttu-id="cb928-124">La cartella `%programfiles%\PowerShell\7` viene aggiunta a `$env:PATH`</span><span class="sxs-lookup"><span data-stu-id="cb928-124">The `%programfiles%\PowerShell\7` folder is added to `$env:PATH`</span></span>
> - <span data-ttu-id="cb928-125">La cartella `%programfiles%\PowerShell\6` viene eliminata</span><span class="sxs-lookup"><span data-stu-id="cb928-125">The `%programfiles%\PowerShell\6` folder is deleted</span></span>
>
> <span data-ttu-id="cb928-126">Se è necessario avere PowerShell 6 insieme a PowerShell 7, reinstallare PowerShell 6 usando il metodo dell'[installazione da ZIP](#zip).</span><span class="sxs-lookup"><span data-stu-id="cb928-126">If you need to run PowerShell 6 side-by-side with PowerShell 7, reinstall PowerShell 6 using the [ZIP install](#zip) method.</span></span>

### <a name="administrative-install-from-the-command-line"></a><span data-ttu-id="cb928-127">Installazione amministrativa dalla riga di comando</span><span class="sxs-lookup"><span data-stu-id="cb928-127">Administrative install from the command line</span></span>

<span data-ttu-id="cb928-128">I pacchetti MSI possono essere installati dalla riga di comando.</span><span class="sxs-lookup"><span data-stu-id="cb928-128">MSI packages can be installed from the command line.</span></span> <span data-ttu-id="cb928-129">Ciò consente agli amministratori di distribuire i pacchetti senza interazione con l'utente.</span><span class="sxs-lookup"><span data-stu-id="cb928-129">This allows administrators to deploy packages without user interaction.</span></span> <span data-ttu-id="cb928-130">Il pacchetto MSI per PowerShell include le proprietà seguenti per controllare le opzioni di installazione:</span><span class="sxs-lookup"><span data-stu-id="cb928-130">The MSI package for PowerShell includes the following properties to control the installation options:</span></span>

- <span data-ttu-id="cb928-131">**ADD_EXPLORER_CONTEXT_MENU_OPENPOWERSHELL** - Questa proprietà controlla l'opzione per aggiungere la voce **Apri PowerShell** al menu di scelta rapida in Esplora risorse.</span><span class="sxs-lookup"><span data-stu-id="cb928-131">**ADD_EXPLORER_CONTEXT_MENU_OPENPOWERSHELL** - This property controls the option for adding the **Open PowerShell** item to the context menu in Windows Explorer.</span></span>
- <span data-ttu-id="cb928-132">**ENABLE_PSREMOTING** - Questa proprietà controlla l'opzione per l'abilitazione della comunicazione remota di PowerShell durante l'installazione.</span><span class="sxs-lookup"><span data-stu-id="cb928-132">**ENABLE_PSREMOTING** - This property controls the option for enabling PowerShell remoting during installation.</span></span>
- <span data-ttu-id="cb928-133">**REGISTER_MANIFEST** - Questa proprietà controlla l'opzione per registrare il manifesto di registrazione degli eventi di Windows.</span><span class="sxs-lookup"><span data-stu-id="cb928-133">**REGISTER_MANIFEST** - This property controls the option for registering the Windows Event Logging manifest.</span></span>

<span data-ttu-id="cb928-134">Gli esempi seguenti illustrano come installare PowerShell in modo invisibile all'utente con tutte le opzioni di installazione abilitate.</span><span class="sxs-lookup"><span data-stu-id="cb928-134">The following examples shows how to silently install PowerShell with all the install options enabled.</span></span>

```powershell
msiexec.exe /package PowerShell-<version>-win-<os-arch>.msi /quiet ADD_EXPLORER_CONTEXT_MENU_OPENPOWERSHELL=1 ENABLE_PSREMOTING=1 REGISTER_MANIFEST=1
```

<span data-ttu-id="cb928-135">Per un elenco completo delle opzioni della riga di comando per Msiexec.exe, vedere [Opzioni della riga di comando](/windows/desktop/Msi/command-line-options).</span><span class="sxs-lookup"><span data-stu-id="cb928-135">For a full list of command line options for Msiexec.exe, see [Command line options](/windows/desktop/Msi/command-line-options).</span></span>

## <a name="a-idmsix-installing-the-msix-package"></a><span data-ttu-id="cb928-136"><a id="msix" />Installazione del pacchetto MSIX</span><span class="sxs-lookup"><span data-stu-id="cb928-136"><a id="msix" />Installing the MSIX package</span></span>

<span data-ttu-id="cb928-137">Per installare manualmente il pacchetto MSIX in un client Windows 10, scaricare il pacchetto dalla pagina [releases][releases] di GitHub.</span><span class="sxs-lookup"><span data-stu-id="cb928-137">To manually install the MSIX package on a Windows 10 client, download the MSIX package from our GitHub [releases][releases] page.</span></span> <span data-ttu-id="cb928-138">Scorrere verso il basso fino alla sezione **Assets** della versione da installare.</span><span class="sxs-lookup"><span data-stu-id="cb928-138">Scroll down to the **Assets** section of the Release you want to install.</span></span> <span data-ttu-id="cb928-139">È possibile che la sezione Assets sia compressa, quindi potrebbe essere necessario fare clic per espanderla.</span><span class="sxs-lookup"><span data-stu-id="cb928-139">The Assets section may be collapsed, so you may need to click to expand it.</span></span>

<span data-ttu-id="cb928-140">Il file MSI è simile al seguente - `PowerShell-<version>-win-<os-arch>.msix`</span><span class="sxs-lookup"><span data-stu-id="cb928-140">The MSIX file looks like this - `PowerShell-<version>-win-<os-arch>.msix`</span></span>

<span data-ttu-id="cb928-141">Dopo il download non è sufficiente fare doppio clic sul programma di installazione, perché questo pacchetto richiede l'uso di risorse non virtualizzate.</span><span class="sxs-lookup"><span data-stu-id="cb928-141">Once downloaded, you cannot simply double-click on the installer as this package requires use of un-virtualized resources.</span></span>  <span data-ttu-id="cb928-142">Per l'installazione è necessario usare il cmdlet `Add-AppxPackage`:</span><span class="sxs-lookup"><span data-stu-id="cb928-142">To install, you must use the `Add-AppxPackage` cmdlet:</span></span>

```powershell
Add-AppxPackage PowerShell-<version>-win-<os-arch>.msix
```

## <a name="a-idzip-installing-the-zip-package"></a><span data-ttu-id="cb928-143"><a id="zip" />Installazione del pacchetto ZIP</span><span class="sxs-lookup"><span data-stu-id="cb928-143"><a id="zip" />Installing the ZIP package</span></span>

<span data-ttu-id="cb928-144">Sono disponibili archivi ZIP di file binari di PowerShell per abilitare scenari di distribuzione avanzati.</span><span class="sxs-lookup"><span data-stu-id="cb928-144">PowerShell binary ZIP archives are provided to enable advanced deployment scenarios.</span></span> <span data-ttu-id="cb928-145">Si noti che quando si usa l'archivio ZIP, non viene eseguito il controllo dei prerequisiti come nel pacchetto MSI.</span><span class="sxs-lookup"><span data-stu-id="cb928-145">Be noted that when using the ZIP archive, you won't get the prerequisites check as in the MSI package.</span></span> <span data-ttu-id="cb928-146">Per il corretto funzionamento della comunicazione remota su WSMan, verificare che siano soddisfatti i [prerequisiti](#prerequisites).</span><span class="sxs-lookup"><span data-stu-id="cb928-146">For remoting over WSMan to work properly, ensure that you have met the [prerequisites](#prerequisites).</span></span>

## <a name="deploying-on-windows-iot"></a><span data-ttu-id="cb928-147">Distribuzione in Windows IoT</span><span class="sxs-lookup"><span data-stu-id="cb928-147">Deploying on Windows IoT</span></span>

<span data-ttu-id="cb928-148">Windows IoT include già Windows PowerShell, che può essere usato per distribuire PowerShell 7.</span><span class="sxs-lookup"><span data-stu-id="cb928-148">Windows IoT already comes with Windows PowerShell which we can use to deploy PowerShell 7.</span></span>

1. <span data-ttu-id="cb928-149">Creare `PSSession` per il dispositivo di destinazione</span><span class="sxs-lookup"><span data-stu-id="cb928-149">Create `PSSession` to target device</span></span>

   ```powershell
   $s = New-PSSession -ComputerName <deviceIp> -Credential Administrator
   ```

2. <span data-ttu-id="cb928-150">Copiare il pacchetto ZIP nel dispositivo</span><span class="sxs-lookup"><span data-stu-id="cb928-150">Copy the ZIP package to the device</span></span>

   ```powershell
   # change the destination to however you had partitioned it with sufficient
   # space for the zip and the unzipped contents
   # the path should be local to the device
   Copy-Item .\PowerShell-<version>-win-<os-arch>.zip -Destination u:\users\administrator\Downloads -ToSession $s
   ```

3. <span data-ttu-id="cb928-151">Connettersi al dispositivo ed espandere l'archivio</span><span class="sxs-lookup"><span data-stu-id="cb928-151">Connect to the device and expand the archive</span></span>

   ```powershell
   Enter-PSSession $s
   Set-Location u:\users\administrator\downloads
   Expand-Archive .\PowerShell-<version>-win-<os-arch>.zip
   ```

4. <span data-ttu-id="cb928-152">Configurare la comunicazione remota con PowerShell 7</span><span class="sxs-lookup"><span data-stu-id="cb928-152">Setup remoting to PowerShell 7</span></span>

   ```powershell
   Set-Location .\PowerShell-<version>-win-<os-arch>
   # Be sure to use the -PowerShellHome parameter otherwise it'll try to create a new
   # endpoint with Windows PowerShell 5.1
   .\Install-PowerShellRemoting.ps1 -PowerShellHome .
   # You'll get an error message and will be disconnected from the device because it has to restart WinRM
   ```

5. <span data-ttu-id="cb928-153">Connettersi all'endpoint di PowerShell 7 nel dispositivo</span><span class="sxs-lookup"><span data-stu-id="cb928-153">Connect to PowerShell 7 endpoint on device</span></span>

   ```powershell
   # Be sure to use the -Configuration parameter.  If you omit it, you will connect to Windows PowerShell 5.1
   Enter-PSSession -ComputerName <deviceIp> -Credential Administrator -Configuration powershell.<version>
   ```

## <a name="deploying-on-nano-server"></a><span data-ttu-id="cb928-154">Distribuzione in Nano Server</span><span class="sxs-lookup"><span data-stu-id="cb928-154">Deploying on Nano Server</span></span>

<span data-ttu-id="cb928-155">Queste istruzioni presuppongono che una versione di PowerShell sia già in esecuzione nell'immagine Nano Server e che sia stato generato da [Nano Server Image Builder](/windows-server/get-started/deploy-nano-server).</span><span class="sxs-lookup"><span data-stu-id="cb928-155">These instructions assume that a version of PowerShell is already running on the Nano Server image and that it has been generated by the [Nano Server Image Builder](/windows-server/get-started/deploy-nano-server).</span></span>
<span data-ttu-id="cb928-156">Nano Server è un sistema operativo "headless".</span><span class="sxs-lookup"><span data-stu-id="cb928-156">Nano Server is a "headless" OS.</span></span> <span data-ttu-id="cb928-157">È possibile distribuire i file binari di PowerShell usando due metodi diversi.</span><span class="sxs-lookup"><span data-stu-id="cb928-157">PowerShell binaries can be deploy using two different methods.</span></span>

1. <span data-ttu-id="cb928-158">Offline: montare il disco rigido virtuale di Nano Server e decomprimere il contenuto del file ZIP nella posizione prescelta all'interno dell'immagine montata.</span><span class="sxs-lookup"><span data-stu-id="cb928-158">Offline - Mount the Nano Server VHD and unzip the contents of the zip file to your chosen location within the mounted image.</span></span>
2. <span data-ttu-id="cb928-159">Online: trasferire il file ZIP in una sessione di PowerShell e decomprimerlo nella posizione prescelta.</span><span class="sxs-lookup"><span data-stu-id="cb928-159">Online - Transfer the zip file over a PowerShell Session and unzip it in your chosen location.</span></span>

<span data-ttu-id="cb928-160">In entrambi i casi è necessario usare il pacchetto ZIP della versione x64 di Windows 10 ed eseguire i comandi all'interno di un'istanza di PowerShell come "amministratore".</span><span class="sxs-lookup"><span data-stu-id="cb928-160">In both cases, you will need the Windows 10 x64 ZIP release package and will need to run the commands within an "Administrator" PowerShell instance.</span></span>

### <a name="offline-deployment-of-powershell"></a><span data-ttu-id="cb928-161">Distribuzione offline di PowerShell</span><span class="sxs-lookup"><span data-stu-id="cb928-161">Offline Deployment of PowerShell</span></span>

1. <span data-ttu-id="cb928-162">Usare l'utilità ZIP preferita per decomprimere il pacchetto in una directory all'interno dell'immagine montata di Nano Server.</span><span class="sxs-lookup"><span data-stu-id="cb928-162">Use your favorite zip utility to unzip the package to a directory within the mounted Nano Server image.</span></span>
2. <span data-ttu-id="cb928-163">Smontare l'immagine e riavviarla.</span><span class="sxs-lookup"><span data-stu-id="cb928-163">Unmount the image and boot it.</span></span>
3. <span data-ttu-id="cb928-164">Connettersi all'istanza di Posta in arrivo di Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="cb928-164">Connect to the inbox instance of Windows PowerShell.</span></span>
4. <span data-ttu-id="cb928-165">Seguire le istruzioni per creare un endpoint di comunicazione remota usando un'[altra tecnica di istanza](../learn/remoting/wsman-remoting-in-powershell-core.md#executed-by-another-instance-of-powershell-on-behalf-of-the-instance-that-it-will-register).</span><span class="sxs-lookup"><span data-stu-id="cb928-165">Follow the instructions to create a remoting endpoint using the ["another instance technique"](../learn/remoting/wsman-remoting-in-powershell-core.md#executed-by-another-instance-of-powershell-on-behalf-of-the-instance-that-it-will-register).</span></span>

### <a name="online-deployment-of-powershell"></a><span data-ttu-id="cb928-166">Distribuzione online di PowerShell</span><span class="sxs-lookup"><span data-stu-id="cb928-166">Online Deployment of PowerShell</span></span>

<span data-ttu-id="cb928-167">La procedura seguente consente di eseguire la distribuzione di PowerShell in un'istanza in esecuzione di Nano Server e di configurarne l'endpoint remoto.</span><span class="sxs-lookup"><span data-stu-id="cb928-167">The following steps guide you through the deployment of PowerShell to a running instance of Nano Server and the configuration of its remote endpoint.</span></span>

- <span data-ttu-id="cb928-168">Connettersi all'istanza di Posta in arrivo di Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="cb928-168">Connect to the inbox instance of Windows PowerShell</span></span>

  ```powershell
  $session = New-PSSession -ComputerName <Nano Server IP address> -Credential <An Administrator account on the system>
  ```

- <span data-ttu-id="cb928-169">Copiare il file nell'istanza di Nano Server</span><span class="sxs-lookup"><span data-stu-id="cb928-169">Copy the file to the Nano Server instance</span></span>

  ```powershell
  Copy-Item <local PS Core download location>\powershell-<version>-win-x64.zip c:\ -ToSession $session
  ```

- <span data-ttu-id="cb928-170">Immettere la sessione</span><span class="sxs-lookup"><span data-stu-id="cb928-170">Enter the session</span></span>

  ```powershell
  Enter-PSSession $session
  ```

- <span data-ttu-id="cb928-171">Estrarre il file ZIP</span><span class="sxs-lookup"><span data-stu-id="cb928-171">Extract the ZIP file</span></span>

  ```powershell
  # Insert the appropriate version.
  Expand-Archive -Path C:\powershell-<version>-win-x64.zip -DestinationPath "C:\PowerShell_<version>"
  ```

- <span data-ttu-id="cb928-172">Perché la comunicazione remota si basi su WS-Management, seguire le istruzioni seguenti per creare un endpoint di comunicazione remota tramite un'[altra tecnica di istanza](../learn/remoting/WSMan-Remoting-in-PowerShell-Core.md#executed-by-another-instance-of-powershell-on-behalf-of-the-instance-that-it-will-register).</span><span class="sxs-lookup"><span data-stu-id="cb928-172">If you want WSMan-based remoting, follow the instructions to create a remoting endpoint using the ["another instance technique"](../learn/remoting/WSMan-Remoting-in-PowerShell-Core.md#executed-by-another-instance-of-powershell-on-behalf-of-the-instance-that-it-will-register).</span></span>

## <a name="install-as-a-net-global-tool"></a><span data-ttu-id="cb928-173">Installare come strumento globale .NET</span><span class="sxs-lookup"><span data-stu-id="cb928-173">Install as a .NET Global tool</span></span>

<span data-ttu-id="cb928-174">Se [.NET Core SDK](/dotnet/core/sdk) è già installato, è facile installare PowerShell come [strumento globale .NET](/dotnet/core/tools/global-tools).</span><span class="sxs-lookup"><span data-stu-id="cb928-174">If you already have the [.NET Core SDK](/dotnet/core/sdk) installed, it's easy to install PowerShell as a [.NET Global tool](/dotnet/core/tools/global-tools).</span></span>

```
dotnet tool install --global PowerShell
```

## <a name="how-to-create-a-remoting-endpoint"></a><span data-ttu-id="cb928-175">Come creare un endpoint di comunicazione remota</span><span class="sxs-lookup"><span data-stu-id="cb928-175">How to create a remoting endpoint</span></span>

<span data-ttu-id="cb928-176">PowerShell supporta il protocollo di comunicazione remota di PowerShell (PSRP) tramite WS-Management e SSH.</span><span class="sxs-lookup"><span data-stu-id="cb928-176">PowerShell supports the PowerShell Remoting Protocol (PSRP) over both WSMan and SSH.</span></span> <span data-ttu-id="cb928-177">Per altre informazioni, vedere:</span><span class="sxs-lookup"><span data-stu-id="cb928-177">For more information, see:</span></span>

- <span data-ttu-id="cb928-178">[Comunicazione remota di PowerShell su SSH][ssh-remoting]</span><span class="sxs-lookup"><span data-stu-id="cb928-178">[SSH Remoting in PowerShell Core][ssh-remoting]</span></span>
- <span data-ttu-id="cb928-179">[Comunicazione remota di WS-Management in PowerShell Core][wsman-remoting]</span><span class="sxs-lookup"><span data-stu-id="cb928-179">[WSMan Remoting in PowerShell Core][wsman-remoting]</span></span>

<!-- [download-center]: TODO -->

[releases]: https://github.com/PowerShell/PowerShell/releases
[ssh-remoting]: ../learn/remoting/SSH-Remoting-in-PowerShell-Core.md
[wsman-remoting]: ../learn/remoting/WSMan-Remoting-in-PowerShell-Core.md
[AppVeyor]: https://ci.appveyor.com/project/PowerShell/powershell
