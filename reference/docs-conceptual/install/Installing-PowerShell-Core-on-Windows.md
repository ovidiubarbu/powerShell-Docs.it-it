---
title: Installazione di PowerShell in Windows
description: Informazioni sull'installazione di PowerShell in Windows
ms.date: 08/06/2018
ms.openlocfilehash: ea5432725f4baea8c688fb8e67482910e2c3981e
ms.sourcegitcommit: b6cf10224eb9f32919a505cdffbe5968241c18a1
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 03/28/2020
ms.locfileid: "80374888"
---
# <a name="installing-powershell-on-windows"></a><span data-ttu-id="5a70d-103">Installazione di PowerShell in Windows</span><span class="sxs-lookup"><span data-stu-id="5a70d-103">Installing PowerShell on Windows</span></span>

<span data-ttu-id="5a70d-104">Esistono diversi modi per installare PowerShell in Windows.</span><span class="sxs-lookup"><span data-stu-id="5a70d-104">There are multiple ways to install PowerShell in Windows.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="5a70d-105">Prerequisiti</span><span class="sxs-lookup"><span data-stu-id="5a70d-105">Prerequisites</span></span>

<span data-ttu-id="5a70d-106">La versione più recente di PowerShell è supportata in Windows 7 SP1, Server 2008 R2 e versioni successive.</span><span class="sxs-lookup"><span data-stu-id="5a70d-106">The latest release of PowerShell is supported on Windows 7 SP1, Server 2008 R2, and later versions.</span></span>

<span data-ttu-id="5a70d-107">Per abilitare la comunicazione remota di PowerShell tramite WS-Management, è necessario soddisfare i prerequisiti seguenti:</span><span class="sxs-lookup"><span data-stu-id="5a70d-107">To enable PowerShell remoting over WSMan, the following prerequisites need to be met:</span></span>

- <span data-ttu-id="5a70d-108">Installare [Universal C Runtime](https://www.microsoft.com/download/details.aspx?id=50410) nelle versioni di Windows precedenti a Windows 10.</span><span class="sxs-lookup"><span data-stu-id="5a70d-108">Install the [Universal C Runtime](https://www.microsoft.com/download/details.aspx?id=50410) on Windows versions predating Windows 10.</span></span> <span data-ttu-id="5a70d-109">È disponibile tramite download diretto o Windows Update.</span><span class="sxs-lookup"><span data-stu-id="5a70d-109">It's available via direct download or Windows Update.</span></span> <span data-ttu-id="5a70d-110">Questo pacchetto è già installato nei sistemi con patch complete.</span><span class="sxs-lookup"><span data-stu-id="5a70d-110">Fully patched systems already have this package installed.</span></span>
- <span data-ttu-id="5a70d-111">Installare Windows Management Framework (WMF) 4.0 o versione successiva in Windows 7 e Windows Server 2008 R2.</span><span class="sxs-lookup"><span data-stu-id="5a70d-111">Install the Windows Management Framework (WMF) 4.0 or newer on Windows 7 and Windows Server 2008 R2.</span></span> <span data-ttu-id="5a70d-112">Per altre informazioni su WMF, vedere la [panoramica su Windows Management Framework](/powershell/scripting/wmf/overview).</span><span class="sxs-lookup"><span data-stu-id="5a70d-112">For more information about WMF, see [WMF Overview](/powershell/scripting/wmf/overview).</span></span>

## <a name="download-the-installer-package"></a><span data-ttu-id="5a70d-113">Scaricare il pacchetto del programma di installazione</span><span class="sxs-lookup"><span data-stu-id="5a70d-113">Download the installer package</span></span>

<span data-ttu-id="5a70d-114">Per installare PowerShell in Windows, scaricare il pacchetto di installazione dalla pagina delle [versioni][releases] di GitHub.</span><span class="sxs-lookup"><span data-stu-id="5a70d-114">To install PowerShell on Windows, download the install package from our GitHub [releases][releases] page.</span></span> <span data-ttu-id="5a70d-115">Scorrere verso il basso fino alla sezione **Assets** nella pagine delle versioni.</span><span class="sxs-lookup"><span data-stu-id="5a70d-115">Scroll down to the **Assets** section of the Release page.</span></span> <span data-ttu-id="5a70d-116">È possibile che la sezione **Assets** sia compressa, quindi potrebbe essere necessario fare clic per espanderla.</span><span class="sxs-lookup"><span data-stu-id="5a70d-116">The **Assets** section may be collapsed, so you may need to click to expand it.</span></span>

## <a name="installing-the-msi-package"></a><span data-ttu-id="5a70d-117"><a id="msi" />Installazione del pacchetto MSI</span><span class="sxs-lookup"><span data-stu-id="5a70d-117"><a id="msi" />Installing the MSI package</span></span>

<span data-ttu-id="5a70d-118">Il file MSI è simile al seguente `PowerShell-<version>-win-<os-arch>.msi`.</span><span class="sxs-lookup"><span data-stu-id="5a70d-118">The MSI file looks like `PowerShell-<version>-win-<os-arch>.msi`.</span></span> <span data-ttu-id="5a70d-119">Ad esempio:</span><span class="sxs-lookup"><span data-stu-id="5a70d-119">For example:</span></span>

- `PowerShell-7.0.0-win-x64.msi`
- `PowerShell-7.0.0-win-x86.msi`

<span data-ttu-id="5a70d-120">Dopo averlo scaricato, fare doppio clic sul programma di installazione e seguire i prompt.</span><span class="sxs-lookup"><span data-stu-id="5a70d-120">Once downloaded, double-click the installer and follow the prompts.</span></span>

<span data-ttu-id="5a70d-121">Il programma di installazione crea un collegamento nel menu Start di Windows.</span><span class="sxs-lookup"><span data-stu-id="5a70d-121">The installer creates a shortcut in the Windows Start Menu.</span></span>

- <span data-ttu-id="5a70d-122">Per impostazione predefinita, il pacchetto viene installato in `$env:ProgramFiles\PowerShell\<version>`</span><span class="sxs-lookup"><span data-stu-id="5a70d-122">By default the package is installed to `$env:ProgramFiles\PowerShell\<version>`</span></span>
- <span data-ttu-id="5a70d-123">È possibile avviare PowerShell tramite il menu Start o `$env:ProgramFiles\PowerShell\<version>\pwsh.exe`</span><span class="sxs-lookup"><span data-stu-id="5a70d-123">You can launch PowerShell via the Start Menu or `$env:ProgramFiles\PowerShell\<version>\pwsh.exe`</span></span>

> [!NOTE]
> <span data-ttu-id="5a70d-124">PowerShell 7 viene installato in una nuova directory ed eseguito side-by-side con Windows PowerShell 5.1.</span><span class="sxs-lookup"><span data-stu-id="5a70d-124">PowerShell 7 installs to a new directory and runs side-by-side with Windows PowerShell 5.1.</span></span> <span data-ttu-id="5a70d-125">Per PowerShell Core 6.x, PowerShell 7 è un aggiornamento sul posto che rimuove PowerShell Core 6.x.</span><span class="sxs-lookup"><span data-stu-id="5a70d-125">For PowerShell Core 6.x, PowerShell 7 is an in-place upgrade that removes PowerShell Core 6.x.</span></span>
>
> - <span data-ttu-id="5a70d-126">PowerShell 7 è installato in `$env:ProgramFiles\PowerShell\7`</span><span class="sxs-lookup"><span data-stu-id="5a70d-126">PowerShell 7 is installed to `$env:ProgramFiles\PowerShell\7`</span></span>
> - <span data-ttu-id="5a70d-127">La cartella `$env:ProgramFiles\PowerShell\7` viene aggiunta a `$env:PATH`</span><span class="sxs-lookup"><span data-stu-id="5a70d-127">The `$env:ProgramFiles\PowerShell\7` folder is added to `$env:PATH`</span></span>
> - <span data-ttu-id="5a70d-128">La cartella `$env:ProgramFiles\PowerShell\6` viene eliminata</span><span class="sxs-lookup"><span data-stu-id="5a70d-128">The `$env:ProgramFiles\PowerShell\6` folder is deleted</span></span>
>
> <span data-ttu-id="5a70d-129">Se è necessario avere PowerShell 6 insieme a PowerShell 7, reinstallare PowerShell 6 usando il metodo dell'[installazione da ZIP](#zip).</span><span class="sxs-lookup"><span data-stu-id="5a70d-129">If you need to run PowerShell 6 side-by-side with PowerShell 7, reinstall PowerShell 6 using the [ZIP install](#zip) method.</span></span>

### <a name="administrative-install-from-the-command-line"></a><span data-ttu-id="5a70d-130">Installazione amministrativa dalla riga di comando</span><span class="sxs-lookup"><span data-stu-id="5a70d-130">Administrative install from the command line</span></span>

<span data-ttu-id="5a70d-131">I pacchetti MSI possono essere installati dalla riga di comando per consentire agli amministratori di distribuire i pacchetti senza interazione dell'utente.</span><span class="sxs-lookup"><span data-stu-id="5a70d-131">MSI packages can be installed from the command line allowing administrators to deploy packages without user interaction.</span></span> <span data-ttu-id="5a70d-132">Il pacchetto MSI include le proprietà seguenti per controllare le opzioni di installazione:</span><span class="sxs-lookup"><span data-stu-id="5a70d-132">The MSI package includes the following properties to control the installation options:</span></span>

- <span data-ttu-id="5a70d-133">**ADD_EXPLORER_CONTEXT_MENU_OPENPOWERSHELL** - Questa proprietà controlla l'opzione per aggiungere la voce **Apri PowerShell** al menu di scelta rapida in Esplora risorse.</span><span class="sxs-lookup"><span data-stu-id="5a70d-133">**ADD_EXPLORER_CONTEXT_MENU_OPENPOWERSHELL** - This property controls the option for adding the **Open PowerShell** item to the context menu in Windows Explorer.</span></span>
- <span data-ttu-id="5a70d-134">**ENABLE_PSREMOTING** - Questa proprietà controlla l'opzione per l'abilitazione della comunicazione remota di PowerShell durante l'installazione.</span><span class="sxs-lookup"><span data-stu-id="5a70d-134">**ENABLE_PSREMOTING** - This property controls the option for enabling PowerShell remoting during installation.</span></span>
- <span data-ttu-id="5a70d-135">**REGISTER_MANIFEST** - Questa proprietà controlla l'opzione per registrare il manifesto di registrazione degli eventi di Windows.</span><span class="sxs-lookup"><span data-stu-id="5a70d-135">**REGISTER_MANIFEST** - This property controls the option for registering the Windows Event Logging manifest.</span></span>

<span data-ttu-id="5a70d-136">L'esempio seguente illustra come installare PowerShell in modo invisibile all'utente con tutte le opzioni di installazione abilitate.</span><span class="sxs-lookup"><span data-stu-id="5a70d-136">The following example shows how to silently install PowerShell with all the install options enabled.</span></span>

```powershell
msiexec.exe /package PowerShell-7.0.0-win-x64.msi /quiet ADD_EXPLORER_CONTEXT_MENU_OPENPOWERSHELL=1 ENABLE_PSREMOTING=1 REGISTER_MANIFEST=1
```

<span data-ttu-id="5a70d-137">Per un elenco completo delle opzioni della riga di comando per `Msiexec.exe`, vedere [Opzioni della riga di comando](/windows/desktop/Msi/command-line-options).</span><span class="sxs-lookup"><span data-stu-id="5a70d-137">For a full list of command-line options for `Msiexec.exe`, see [Command line options](/windows/desktop/Msi/command-line-options).</span></span>

## <a name="installing-the-msix-package"></a><span data-ttu-id="5a70d-138"><a id="msix" />Installazione del pacchetto MSIX</span><span class="sxs-lookup"><span data-stu-id="5a70d-138"><a id="msix" />Installing the MSIX package</span></span>

<span data-ttu-id="5a70d-139">Per installare manualmente il pacchetto MSIX in un client Windows 10, scaricare il pacchetto dalla pagina [releases][releases] di GitHub.</span><span class="sxs-lookup"><span data-stu-id="5a70d-139">To manually install the MSIX package on a Windows 10 client, download the MSIX package from our GitHub [releases][releases] page.</span></span> <span data-ttu-id="5a70d-140">Scorrere verso il basso fino alla sezione **Assets** della versione da installare.</span><span class="sxs-lookup"><span data-stu-id="5a70d-140">Scroll down to the **Assets** section of the Release you want to install.</span></span> <span data-ttu-id="5a70d-141">È possibile che la sezione Assets sia compressa, quindi potrebbe essere necessario fare clic per espanderla.</span><span class="sxs-lookup"><span data-stu-id="5a70d-141">The Assets section may be collapsed, so you may need to click to expand it.</span></span>

<span data-ttu-id="5a70d-142">Il file MSI è simile al seguente - `PowerShell-<version>-win-<os-arch>.msix`</span><span class="sxs-lookup"><span data-stu-id="5a70d-142">The MSIX file looks like this - `PowerShell-<version>-win-<os-arch>.msix`</span></span>

<span data-ttu-id="5a70d-143">Per installare il pacchetto, è necessario usare il cmdlet `Add-AppxPackage`.</span><span class="sxs-lookup"><span data-stu-id="5a70d-143">To install the package, you must use the `Add-AppxPackage` cmdlet.</span></span>

```powershell
Add-AppxPackage PowerShell-<version>-win-<os-arch>.msix
```

> [!NOTE]
> <span data-ttu-id="5a70d-144">Il pacchetto MSIX non è stato ancora rilasciato.</span><span class="sxs-lookup"><span data-stu-id="5a70d-144">The MSIX package has not been released yet.</span></span> <span data-ttu-id="5a70d-145">Quando sarà rilascio, il pacchetto sarà disponibile in Microsoft Store e nella pagina delle [versioni][releases] di GitHub.</span><span class="sxs-lookup"><span data-stu-id="5a70d-145">When released, the package will be available in the Microsoft Store and from the GitHub [releases][releases] page.</span></span>

## <a name="installing-the-zip-package"></a><span data-ttu-id="5a70d-146"><a id="zip" />Installazione del pacchetto ZIP</span><span class="sxs-lookup"><span data-stu-id="5a70d-146"><a id="zip" />Installing the ZIP package</span></span>

<span data-ttu-id="5a70d-147">Sono disponibili archivi ZIP di file binari di PowerShell per abilitare scenari di distribuzione avanzati.</span><span class="sxs-lookup"><span data-stu-id="5a70d-147">PowerShell binary ZIP archives are provided to enable advanced deployment scenarios.</span></span> <span data-ttu-id="5a70d-148">L'installazione dell'archivio ZIP non controlla i prerequisiti come per i pacchetti MSI.</span><span class="sxs-lookup"><span data-stu-id="5a70d-148">Installing the ZIP archive doesn't check the prerequisites like the MSI packages do.</span></span> <span data-ttu-id="5a70d-149">Per il corretto funzionamento della comunicazione remota su WSMan, verificare che siano soddisfatti i [prerequisiti](#prerequisites).</span><span class="sxs-lookup"><span data-stu-id="5a70d-149">For remoting over WSMan to work properly, ensure that you've met the [prerequisites](#prerequisites).</span></span>

## <a name="deploying-on-windows-iot"></a><span data-ttu-id="5a70d-150">Distribuzione in Windows IoT</span><span class="sxs-lookup"><span data-stu-id="5a70d-150">Deploying on Windows IoT</span></span>

<span data-ttu-id="5a70d-151">Windows IoT include Windows PowerShell, che può essere usato per distribuire PowerShell 7.</span><span class="sxs-lookup"><span data-stu-id="5a70d-151">Windows IoT comes with Windows PowerShell, which we can use to deploy PowerShell 7.</span></span>

1. <span data-ttu-id="5a70d-152">Creare `PSSession` per il dispositivo di destinazione</span><span class="sxs-lookup"><span data-stu-id="5a70d-152">Create `PSSession` to target device</span></span>

   ```powershell
   Set-Item -Path WSMan:\localhost\Client\TrustedHosts <deviceip>
   $S = New-PSSession -ComputerName <deviceIp> -Credential Administrator
   ```

2. <span data-ttu-id="5a70d-153">Copiare il pacchetto ZIP nel dispositivo</span><span class="sxs-lookup"><span data-stu-id="5a70d-153">Copy the ZIP package to the device</span></span>

   ```powershell
   # change the destination to however you had partitioned it with sufficient
   # space for the zip and the unzipped contents
   # the path should be local to the device
   Copy-Item .\PowerShell-<version>-win-<os-arch>.zip -Destination u:\users\administrator\Downloads -ToSession $s
   ```

3. <span data-ttu-id="5a70d-154">Connettersi al dispositivo ed espandere l'archivio</span><span class="sxs-lookup"><span data-stu-id="5a70d-154">Connect to the device and expand the archive</span></span>

   ```powershell
   Enter-PSSession $s
   Set-Location u:\users\administrator\downloads
   Expand-Archive .\PowerShell-<version>-win-<os-arch>.zip
   ```

4. <span data-ttu-id="5a70d-155">Configurare la comunicazione remota con PowerShell 7</span><span class="sxs-lookup"><span data-stu-id="5a70d-155">Set up remoting to PowerShell 7</span></span>

   ```powershell
   Set-Location .\PowerShell-<version>-win-<os-arch>
   # Be sure to use the -PowerShellHome parameter otherwise it'll try to create a new
   # endpoint with Windows PowerShell 5.1
   .\Install-PowerShellRemoting.ps1 -PowerShellHome .
   # You'll get an error message and will be disconnected from the device because it has to restart WinRM
   ```

5. <span data-ttu-id="5a70d-156">Connettersi all'endpoint di PowerShell 7 nel dispositivo</span><span class="sxs-lookup"><span data-stu-id="5a70d-156">Connect to PowerShell 7 endpoint on device</span></span>

   ```powershell
   # Be sure to use the -Configuration parameter.  If you omit it, you will connect to Windows PowerShell 5.1
   Enter-PSSession -ComputerName <deviceIp> -Credential Administrator -Configuration powershell.<version>
   ```

## <a name="deploying-on-nano-server"></a><span data-ttu-id="5a70d-157">Distribuzione in Nano Server</span><span class="sxs-lookup"><span data-stu-id="5a70d-157">Deploying on Nano Server</span></span>

<span data-ttu-id="5a70d-158">Queste istruzioni presuppongono che Nano Server sia un sistema operativo headless con una versione di PowerShell già in esecuzione.</span><span class="sxs-lookup"><span data-stu-id="5a70d-158">These instructions assume that the Nano Server is a "headless" OS that has a version of PowerShell is already running on it.</span></span> <span data-ttu-id="5a70d-159">Per altre informazioni, vedere la documentazione [Nano Server Image Builder](/windows-server/get-started/deploy-nano-server).</span><span class="sxs-lookup"><span data-stu-id="5a70d-159">For more information, see the [Nano Server Image Builder](/windows-server/get-started/deploy-nano-server) documentation.</span></span>

<span data-ttu-id="5a70d-160">È possibile distribuire i file binari di PowerShell usando due metodi diversi.</span><span class="sxs-lookup"><span data-stu-id="5a70d-160">PowerShell binaries can be deployed using two different methods.</span></span>

1. <span data-ttu-id="5a70d-161">Offline: montare il disco rigido virtuale di Nano Server e decomprimere il contenuto del file ZIP nella posizione prescelta all'interno dell'immagine montata.</span><span class="sxs-lookup"><span data-stu-id="5a70d-161">Offline - Mount the Nano Server VHD and unzip the contents of the zip file to your chosen location within the mounted image.</span></span>
2. <span data-ttu-id="5a70d-162">Online: trasferire il file ZIP in una sessione di PowerShell e decomprimerlo nella posizione prescelta.</span><span class="sxs-lookup"><span data-stu-id="5a70d-162">Online - Transfer the zip file over a PowerShell Session and unzip it in your chosen location.</span></span>

<span data-ttu-id="5a70d-163">In entrambi i casi è necessario il pacchetto della versione ZIP di Windows 10 x64.</span><span class="sxs-lookup"><span data-stu-id="5a70d-163">In both cases, you need the Windows 10 x64 ZIP release package.</span></span> <span data-ttu-id="5a70d-164">Eseguire i comandi all'interno di un'istanza "Administrator" di PowerShell.</span><span class="sxs-lookup"><span data-stu-id="5a70d-164">Run the commands within an "Administrator" instance of PowerShell.</span></span>

### <a name="offline-deployment-of-powershell"></a><span data-ttu-id="5a70d-165">Distribuzione offline di PowerShell</span><span class="sxs-lookup"><span data-stu-id="5a70d-165">Offline Deployment of PowerShell</span></span>

1. <span data-ttu-id="5a70d-166">Usare l'utilità ZIP preferita per decomprimere il pacchetto in una directory all'interno dell'immagine montata di Nano Server.</span><span class="sxs-lookup"><span data-stu-id="5a70d-166">Use your favorite zip utility to unzip the package to a directory within the mounted Nano Server image.</span></span>
2. <span data-ttu-id="5a70d-167">Smontare l'immagine e riavviarla.</span><span class="sxs-lookup"><span data-stu-id="5a70d-167">Unmount the image and boot it.</span></span>
3. <span data-ttu-id="5a70d-168">Connettersi all'istanza di Posta in arrivo di Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="5a70d-168">Connect to the inbox instance of Windows PowerShell.</span></span>
4. <span data-ttu-id="5a70d-169">Seguire le istruzioni per creare un endpoint di comunicazione remota usando un'[altra tecnica di istanza](../learn/remoting/wsman-remoting-in-powershell-core.md#executed-by-another-instance-of-powershell-on-behalf-of-the-instance-that-it-will-register).</span><span class="sxs-lookup"><span data-stu-id="5a70d-169">Follow the instructions to create a remoting endpoint using the ["another instance technique"](../learn/remoting/wsman-remoting-in-powershell-core.md#executed-by-another-instance-of-powershell-on-behalf-of-the-instance-that-it-will-register).</span></span>

### <a name="online-deployment-of-powershell"></a><span data-ttu-id="5a70d-170">Distribuzione online di PowerShell</span><span class="sxs-lookup"><span data-stu-id="5a70d-170">Online Deployment of PowerShell</span></span>

<span data-ttu-id="5a70d-171">Distribuire PowerShell in Nano Server seguendo questa procedura.</span><span class="sxs-lookup"><span data-stu-id="5a70d-171">Deploy PowerShell to Nano Server using the following steps.</span></span>

- <span data-ttu-id="5a70d-172">Connettersi all'istanza di Posta in arrivo di Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="5a70d-172">Connect to the inbox instance of Windows PowerShell</span></span>

  ```powershell
  $session = New-PSSession -ComputerName <Nano Server IP address> -Credential <An Administrator account on the system>
  ```

- <span data-ttu-id="5a70d-173">Copiare il file nell'istanza di Nano Server</span><span class="sxs-lookup"><span data-stu-id="5a70d-173">Copy the file to the Nano Server instance</span></span>

  ```powershell
  Copy-Item <local PS Core download location>\powershell-<version>-win-x64.zip c:\ -ToSession $session
  ```

- <span data-ttu-id="5a70d-174">Immettere la sessione</span><span class="sxs-lookup"><span data-stu-id="5a70d-174">Enter the session</span></span>

  ```powershell
  Enter-PSSession $session
  ```

- <span data-ttu-id="5a70d-175">Estrarre il file ZIP</span><span class="sxs-lookup"><span data-stu-id="5a70d-175">Extract the ZIP file</span></span>

  ```powershell
  # Insert the appropriate version.
  Expand-Archive -Path C:\powershell-<version>-win-x64.zip -DestinationPath "C:\PowerShell_<version>"
  ```

- <span data-ttu-id="5a70d-176">Perché la comunicazione remota si basi su WS-Management, seguire le istruzioni seguenti per creare un endpoint di comunicazione remota tramite un'[altra tecnica di istanza](../learn/remoting/WSMan-Remoting-in-PowerShell-Core.md#executed-by-another-instance-of-powershell-on-behalf-of-the-instance-that-it-will-register).</span><span class="sxs-lookup"><span data-stu-id="5a70d-176">If you want WSMan-based remoting, follow the instructions to create a remoting endpoint using the ["another instance technique"](../learn/remoting/WSMan-Remoting-in-PowerShell-Core.md#executed-by-another-instance-of-powershell-on-behalf-of-the-instance-that-it-will-register).</span></span>

## <a name="install-as-a-net-global-tool"></a><span data-ttu-id="5a70d-177">Installare come strumento globale .NET</span><span class="sxs-lookup"><span data-stu-id="5a70d-177">Install as a .NET Global tool</span></span>

<span data-ttu-id="5a70d-178">Se [.NET Core SDK](/dotnet/core/sdk) è già installato, è facile installare PowerShell come [strumento globale .NET](/dotnet/core/tools/global-tools).</span><span class="sxs-lookup"><span data-stu-id="5a70d-178">If you already have the [.NET Core SDK](/dotnet/core/sdk) installed, it's easy to install PowerShell as a [.NET Global tool](/dotnet/core/tools/global-tools).</span></span>

```
dotnet tool install --global PowerShell
```

<span data-ttu-id="5a70d-179">Il programma di installazione dello strumento DotNet aggiunge `$env:USERPROFILE\dotnet\tools` alla variabile di ambiente `$env:PATH`.</span><span class="sxs-lookup"><span data-stu-id="5a70d-179">The dotnet tool installer adds `$env:USERPROFILE\dotnet\tools` to your `$env:PATH` environment variable.</span></span> <span data-ttu-id="5a70d-180">La shell attualmente in esecuzione non dispone tuttavia del parametro `$env:PATH` aggiornato.</span><span class="sxs-lookup"><span data-stu-id="5a70d-180">However, the currently running shell doesn't have the updated `$env:PATH`.</span></span> <span data-ttu-id="5a70d-181">È possibile avviare PowerShell da una nuova shell digitando `pwsh`.</span><span class="sxs-lookup"><span data-stu-id="5a70d-181">You can start PowerShell from a new shell by typing `pwsh`.</span></span>

## <a name="how-to-create-a-remoting-endpoint"></a><span data-ttu-id="5a70d-182">Come creare un endpoint di comunicazione remota</span><span class="sxs-lookup"><span data-stu-id="5a70d-182">How to create a remoting endpoint</span></span>

<span data-ttu-id="5a70d-183">PowerShell supporta il protocollo di comunicazione remota di PowerShell (PSRP) tramite WS-Management e SSH.</span><span class="sxs-lookup"><span data-stu-id="5a70d-183">PowerShell supports the PowerShell Remoting Protocol (PSRP) over both WSMan and SSH.</span></span> <span data-ttu-id="5a70d-184">Per altre informazioni, vedere:</span><span class="sxs-lookup"><span data-stu-id="5a70d-184">For more information, see:</span></span>

- <span data-ttu-id="5a70d-185">[Comunicazione remota di PowerShell su SSH][ssh-remoting]</span><span class="sxs-lookup"><span data-stu-id="5a70d-185">[SSH Remoting in PowerShell Core][ssh-remoting]</span></span>
- <span data-ttu-id="5a70d-186">[Comunicazione remota di WS-Management in PowerShell Core][wsman-remoting]</span><span class="sxs-lookup"><span data-stu-id="5a70d-186">[WSMan Remoting in PowerShell Core][wsman-remoting]</span></span>

<!-- [download-center]: TODO -->

[releases]: https://github.com/PowerShell/PowerShell/releases
[ssh-remoting]: ../learn/remoting/SSH-Remoting-in-PowerShell-Core.md
[wsman-remoting]: ../learn/remoting/WSMan-Remoting-in-PowerShell-Core.md
[AppVeyor]: https://ci.appveyor.com/project/PowerShell/powershell
