---
title: Comunicazione remota di PowerShell su SSH
description: Comunicazione remota in PowerShell Core tramite SSH
ms.date: 09/30/2019
ms.openlocfilehash: 0f2fb13010d62dec5b19b373a24a199bff22665d
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 12/05/2019
ms.locfileid: "73444369"
---
# <a name="powershell-remoting-over-ssh"></a><span data-ttu-id="5c05c-103">Comunicazione remota di PowerShell su SSH</span><span class="sxs-lookup"><span data-stu-id="5c05c-103">PowerShell remoting over SSH</span></span>

## <a name="overview"></a><span data-ttu-id="5c05c-104">Panoramica</span><span class="sxs-lookup"><span data-stu-id="5c05c-104">Overview</span></span>

<span data-ttu-id="5c05c-105">La comunicazione remota di PowerShell solitamente usa WinRM per la negoziazione di connessione e il trasporto dei dati.</span><span class="sxs-lookup"><span data-stu-id="5c05c-105">PowerShell remoting normally uses WinRM for connection negotiation and data transport.</span></span> <span data-ttu-id="5c05c-106">SSH è ora disponibile per le piattaforme Linux e Windows e permette a PowerShell di offrire un'autentica comunicazione remota multipiattaforma.</span><span class="sxs-lookup"><span data-stu-id="5c05c-106">SSH is now available for Linux and Windows platforms and allows true multiplatform PowerShell remoting.</span></span>

<span data-ttu-id="5c05c-107">WinRM offre un solido modello di hosting per sessioni remote di PowerShell.</span><span class="sxs-lookup"><span data-stu-id="5c05c-107">WinRM provides a robust hosting model for PowerShell remote sessions.</span></span> <span data-ttu-id="5c05c-108">La comunicazione remota basata su SSH attualmente non supporta la configurazione di endpoint remoti e JEA (Just Enough Administration).</span><span class="sxs-lookup"><span data-stu-id="5c05c-108">SSH-based remoting doesn't currently support remote endpoint configuration and Just Enough Administration (JEA).</span></span>

<span data-ttu-id="5c05c-109">La comunicazione remota SSH permette la comunicazione remota di base di sessioni di PowerShell tra computer Windows e Linux.</span><span class="sxs-lookup"><span data-stu-id="5c05c-109">SSH remoting lets you do basic PowerShell session remoting between Windows and Linux computers.</span></span> <span data-ttu-id="5c05c-110">La comunicazione remota SSH crea un processo host di PowerShell nel computer di destinazione come sottosistema SSH.</span><span class="sxs-lookup"><span data-stu-id="5c05c-110">SSH remoting creates a PowerShell host process on the target computer as an SSH subsystem.</span></span> <span data-ttu-id="5c05c-111">In futuro verrà implementato un modello di hosting generale, simile a WinRM, per supportare la configurazione degli endpoint e JEA.</span><span class="sxs-lookup"><span data-stu-id="5c05c-111">Eventually we'll implement a general hosting model, similar to WinRM, to support endpoint configuration and JEA.</span></span>

<span data-ttu-id="5c05c-112">I cmdlet `New-PSSession`, `Enter-PSSession` e `Invoke-Command` includono ora un nuovo set di parametri per supportare questa nuova connessione di comunicazione remota.</span><span class="sxs-lookup"><span data-stu-id="5c05c-112">The `New-PSSession`, `Enter-PSSession`, and `Invoke-Command` cmdlets now have a new parameter set to support this new remoting connection.</span></span>

```
[-HostName <string>]  [-UserName <string>]  [-KeyFilePath <string>]
```

<span data-ttu-id="5c05c-113">Per creare una sessione remota, è necessario specificare il computer di destinazione con il parametro `HostName` e il nome utente con il parametro `UserName`.</span><span class="sxs-lookup"><span data-stu-id="5c05c-113">To create a remote session, you specify the target computer with the `HostName` parameter and provide the user name with `UserName`.</span></span> <span data-ttu-id="5c05c-114">Quando si eseguono i cmdlet in modo interattivo, viene chiesto di immettere una password.</span><span class="sxs-lookup"><span data-stu-id="5c05c-114">When running the cmdlets interactively, you're prompted for a password.</span></span> <span data-ttu-id="5c05c-115">È anche possibile usare l'autenticazione con chiave SSH tramite un file di chiave privata con il parametro `KeyFilePath`.</span><span class="sxs-lookup"><span data-stu-id="5c05c-115">You can also, use SSH key authentication using a private key file with the `KeyFilePath` parameter.</span></span>

## <a name="general-setup-information"></a><span data-ttu-id="5c05c-116">Informazioni generali di installazione</span><span class="sxs-lookup"><span data-stu-id="5c05c-116">General setup information</span></span>

<span data-ttu-id="5c05c-117">PowerShell 6 o versione successiva e SSH devono essere installati in tutti i computer.</span><span class="sxs-lookup"><span data-stu-id="5c05c-117">PowerShell 6 or higher, and SSH must be installed on all computers.</span></span> <span data-ttu-id="5c05c-118">Installare sia il client SSH (`ssh.exe`) sia il server (`sshd.exe`) per rendere possibile la comunicazione remota tra i computer.</span><span class="sxs-lookup"><span data-stu-id="5c05c-118">Install both the SSH client (`ssh.exe`) and server (`sshd.exe`) so that you can remote to and from the computers.</span></span> <span data-ttu-id="5c05c-119">OpenSSH per Windows è ora disponibile in Windows 10 build 1809 e Windows Server 2019.</span><span class="sxs-lookup"><span data-stu-id="5c05c-119">OpenSSH for Windows is now available in Windows 10 build 1809 and Windows Server 2019.</span></span> <span data-ttu-id="5c05c-120">Per altre informazioni, vedere [Gestire Windows con OpenSSH](/windows-server/administration/openssh/openssh_overview).</span><span class="sxs-lookup"><span data-stu-id="5c05c-120">For more information, see [Manage Windows with OpenSSH](/windows-server/administration/openssh/openssh_overview).</span></span> <span data-ttu-id="5c05c-121">Per Linux, installare SSH (incluso il server sshd) nel modo appropriato per la piattaforma in uso.</span><span class="sxs-lookup"><span data-stu-id="5c05c-121">For Linux, install SSH, including sshd server, that's appropriate for your platform.</span></span> <span data-ttu-id="5c05c-122">È necessario installare anche PowerShell da GitHub per ottenere la funzionalità di comunicazione remota SSH.</span><span class="sxs-lookup"><span data-stu-id="5c05c-122">You also need to install PowerShell from GitHub to get the SSH remoting feature.</span></span> <span data-ttu-id="5c05c-123">Il server SSH deve essere configurato per creare un sottosistema SSH in modo da ospitare un processo PowerShell nel computer remoto.</span><span class="sxs-lookup"><span data-stu-id="5c05c-123">The SSH server must be configured to create an SSH subsystem to host a PowerShell process on the remote computer.</span></span> <span data-ttu-id="5c05c-124">È anche necessario abilitare l'autenticazione basata su **password** o **chiave**.</span><span class="sxs-lookup"><span data-stu-id="5c05c-124">And, you must enable **password** or **key-based** authentication.</span></span>

## <a name="set-up-on-a-windows-computer"></a><span data-ttu-id="5c05c-125">Eseguire la configurazione in un computer Windows</span><span class="sxs-lookup"><span data-stu-id="5c05c-125">Set up on a Windows computer</span></span>

1. <span data-ttu-id="5c05c-126">Installare la versione più recente di PowerShell (vedere [Installazione di PowerShell Core in Windows](../../install/installing-powershell-core-on-windows.md#msi)).</span><span class="sxs-lookup"><span data-stu-id="5c05c-126">Install the latest version of PowerShell, see [Installing PowerShell Core on Windows](../../install/installing-powershell-core-on-windows.md#msi).</span></span>

   <span data-ttu-id="5c05c-127">È possibile verificare che PowerShell includa il supporto per la comunicazione remota SSH elencando i set di parametri `New-PSSession`.</span><span class="sxs-lookup"><span data-stu-id="5c05c-127">You can confirm that PowerShell has SSH remoting support by listing the `New-PSSession` parameter sets.</span></span> <span data-ttu-id="5c05c-128">Si noterà che sono presenti nomi di set di parametri che iniziano con **SSH**.</span><span class="sxs-lookup"><span data-stu-id="5c05c-128">You'll notice there are parameter set names that begin with **SSH**.</span></span> <span data-ttu-id="5c05c-129">Questi set di parametri includono i parametri **SSH**.</span><span class="sxs-lookup"><span data-stu-id="5c05c-129">Those parameter sets include **SSH** parameters.</span></span>

   ```powershell
   (Get-Command New-PSSession).ParameterSets.Name
   ```

   ```Output
   Name
   ----
   SSHHost
   SSHHostHashParam
   ```

1. <span data-ttu-id="5c05c-130">Installare la versione più recente di OpenSSH Win32.</span><span class="sxs-lookup"><span data-stu-id="5c05c-130">Install the latest Win32 OpenSSH.</span></span> <span data-ttu-id="5c05c-131">Per le istruzioni di installazione, vedere [Introduzione a OpenSSH](/windows-server/administration/openssh/openssh_install_firstuse).</span><span class="sxs-lookup"><span data-stu-id="5c05c-131">For installation instructions, see [Getting started with OpenSSH](/windows-server/administration/openssh/openssh_install_firstuse).</span></span>

   > [!NOTE]
   > <span data-ttu-id="5c05c-132">Se si vuole impostare PowerShell come shell predefinita per OpenSSH, vedere [Configurazione di Windows per OpenSSH](/windows-server/administration/openssh/openssh_server_configuration).</span><span class="sxs-lookup"><span data-stu-id="5c05c-132">If you want to set PowerShell as the default shell for OpenSSH, see [Configuring Windows for OpenSSH](/windows-server/administration/openssh/openssh_server_configuration).</span></span>

1. <span data-ttu-id="5c05c-133">Modificare il file `sshd_config` in `$env:ProgramData\ssh`.</span><span class="sxs-lookup"><span data-stu-id="5c05c-133">Edit the `sshd_config` file located at `$env:ProgramData\ssh`.</span></span>

   <span data-ttu-id="5c05c-134">Assicurarsi che l'autenticazione della password sia abilitata:</span><span class="sxs-lookup"><span data-stu-id="5c05c-134">Make sure password authentication is enabled:</span></span>

   ```
   PasswordAuthentication yes
   ```

   <span data-ttu-id="5c05c-135">Creare il sottosistema SSH che ospita un processo di PowerShell nel computer remoto:</span><span class="sxs-lookup"><span data-stu-id="5c05c-135">Create the SSH subsystem that hosts a PowerShell process on the remote computer:</span></span>

   ```
   Subsystem powershell c:/progra~1/powershell/6/pwsh.exe -sshs -NoLogo -NoProfile
   ```

   > [!NOTE]
   > <span data-ttu-id="5c05c-136">È necessario usare il nome breve 8.3 per tutti i percorsi di file che contengono spazi.</span><span class="sxs-lookup"><span data-stu-id="5c05c-136">You must use the 8.3 short name for any file paths that contain spaces.</span></span> <span data-ttu-id="5c05c-137">È presente un bug in OpenSSH per Windows che impedisce il funzionamento dei percorsi eseguibili nel sottosistema che contengono spazi.</span><span class="sxs-lookup"><span data-stu-id="5c05c-137">There's a bug in OpenSSH for Windows that prevents spaces from working in subsystem executable paths.</span></span> <span data-ttu-id="5c05c-138">Per altre informazioni, vedere [questo problema in GitHub](https://github.com/PowerShell/Win32-OpenSSH/issues/784).</span><span class="sxs-lookup"><span data-stu-id="5c05c-138">For more information, see this [GitHub issue](https://github.com/PowerShell/Win32-OpenSSH/issues/784).</span></span>
   >
   > <span data-ttu-id="5c05c-139">Il nome breve 8.3 per la cartella `Program Files` in Windows è in genere `Progra~1`.</span><span class="sxs-lookup"><span data-stu-id="5c05c-139">The 8.3 short name for the `Program Files` folder in Windows is usually `Progra~1`.</span></span> <span data-ttu-id="5c05c-140">È comunque possibile usare il comando seguente per controllare:</span><span class="sxs-lookup"><span data-stu-id="5c05c-140">However, you can use the following command to make sure:</span></span>
   >
   > ```powershell
   > Get-CimInstance Win32_Directory -Filter 'Name="C:\\Program Files"' |
   >   Select-Object EightDotThreeFileName
   > ```
   >
   > ```Output
   > EightDotThreeFileName
   > ---------------------
   > c:\progra~1
   > ```

   <span data-ttu-id="5c05c-141">Facoltativamente è possibile abilitare l'autenticazione della chiave:</span><span class="sxs-lookup"><span data-stu-id="5c05c-141">Optionally, enable key authentication:</span></span>

   ```
   PubkeyAuthentication yes
   ```

   <span data-ttu-id="5c05c-142">Per altre informazioni, vedere [Gestione delle chiavi OpenSSH](/windows-server/administration/openssh/openssh_keymanagement).</span><span class="sxs-lookup"><span data-stu-id="5c05c-142">For more information, see [Managing OpenSSH Keys](/windows-server/administration/openssh/openssh_keymanagement).</span></span>

1. <span data-ttu-id="5c05c-143">Riavviare il servizio **sshd**.</span><span class="sxs-lookup"><span data-stu-id="5c05c-143">Restart the **sshd** service.</span></span>

   ```powershell
   Restart-Service sshd
   ```

1. <span data-ttu-id="5c05c-144">Aggiungere il percorso in cui è installato OpenSSH alla variabile di ambiente Path.</span><span class="sxs-lookup"><span data-stu-id="5c05c-144">Add the path where OpenSSH is installed to your Path environment variable.</span></span> <span data-ttu-id="5c05c-145">Ad esempio, `C:\Program Files\OpenSSH\`</span><span class="sxs-lookup"><span data-stu-id="5c05c-145">For example, `C:\Program Files\OpenSSH\`.</span></span> <span data-ttu-id="5c05c-146">Questa voce permette di trovare `ssh.exe`.</span><span class="sxs-lookup"><span data-stu-id="5c05c-146">This entry allows for the `ssh.exe` to be found.</span></span>

## <a name="set-up-on-an-ubuntu-1604-linux-computer"></a><span data-ttu-id="5c05c-147">Eseguire la configurazione in un computer Linux Ubuntu 16.04</span><span class="sxs-lookup"><span data-stu-id="5c05c-147">Set up on an Ubuntu 16.04 Linux computer</span></span>

1. <span data-ttu-id="5c05c-148">Installare la versione più recente di PowerShell (vedere [Installazione di PowerShell Core in Linux](../../install/installing-powershell-core-on-linux.md#ubuntu-1604)).</span><span class="sxs-lookup"><span data-stu-id="5c05c-148">Install the latest version of PowerShell, see [Installing PowerShell Core on Linux](../../install/installing-powershell-core-on-linux.md#ubuntu-1604).</span></span>
1. <span data-ttu-id="5c05c-149">Installare [Ubuntu OpenSSH Server](https://help.ubuntu.com/lts/serverguide/openssh-server.html).</span><span class="sxs-lookup"><span data-stu-id="5c05c-149">Install [Ubuntu OpenSSH Server](https://help.ubuntu.com/lts/serverguide/openssh-server.html).</span></span>

   ```bash
   sudo apt install openssh-client
   sudo apt install openssh-server
   ```

1. <span data-ttu-id="5c05c-150">Modificare il file `sshd_config` nel percorso `/etc/ssh`.</span><span class="sxs-lookup"><span data-stu-id="5c05c-150">Edit the `sshd_config` file at location `/etc/ssh`.</span></span>

   <span data-ttu-id="5c05c-151">Assicurarsi che l'autenticazione della password sia abilitata:</span><span class="sxs-lookup"><span data-stu-id="5c05c-151">Make sure password authentication is enabled:</span></span>

   ```
   PasswordAuthentication yes
   ```

   <span data-ttu-id="5c05c-152">Aggiungere una voce del sottosistema PowerShell:</span><span class="sxs-lookup"><span data-stu-id="5c05c-152">Add a PowerShell subsystem entry:</span></span>

   ```
   Subsystem powershell /usr/bin/pwsh -sshs -NoLogo -NoProfile
   ```

   <span data-ttu-id="5c05c-153">Facoltativamente è possibile abilitare l'autenticazione della chiave:</span><span class="sxs-lookup"><span data-stu-id="5c05c-153">Optionally, enable key authentication:</span></span>

   ```
   PubkeyAuthentication yes
   ```

1. <span data-ttu-id="5c05c-154">Riavviare il servizio **sshd**.</span><span class="sxs-lookup"><span data-stu-id="5c05c-154">Restart the **sshd** service.</span></span>

   ```bash
   sudo service sshd restart
   ```

## <a name="set-up-on-a-macos-computer"></a><span data-ttu-id="5c05c-155">Eseguire la configurazione in un computer macOS</span><span class="sxs-lookup"><span data-stu-id="5c05c-155">Set up on a macOS computer</span></span>

1. <span data-ttu-id="5c05c-156">Installare la versione più recente di PowerShell (vedere [Installazione di PowerShell Core in macOS](../../install/installing-powershell-core-on-macos.md)).</span><span class="sxs-lookup"><span data-stu-id="5c05c-156">Install the latest version of PowerShell, see [Installing PowerShell Core on macOS](../../install/installing-powershell-core-on-macos.md).</span></span>

   <span data-ttu-id="5c05c-157">Assicurarsi che la comunicazione remota SSH sia abilitata attenendosi alla procedura seguente:</span><span class="sxs-lookup"><span data-stu-id="5c05c-157">Make sure SSH Remoting is enabled by following these steps:</span></span>

   1. <span data-ttu-id="5c05c-158">Aprire `System Preferences`.</span><span class="sxs-lookup"><span data-stu-id="5c05c-158">Open `System Preferences`.</span></span>
   1. <span data-ttu-id="5c05c-159">Fare clic su `Sharing`.</span><span class="sxs-lookup"><span data-stu-id="5c05c-159">Click on `Sharing`.</span></span>
   1. <span data-ttu-id="5c05c-160">Selezionare `Remote Login` per impostare `Remote Login: On`.</span><span class="sxs-lookup"><span data-stu-id="5c05c-160">Check `Remote Login` to set `Remote Login: On`.</span></span>
   1. <span data-ttu-id="5c05c-161">Consentire l'accesso agli utenti appropriati.</span><span class="sxs-lookup"><span data-stu-id="5c05c-161">Allow access to the appropriate users.</span></span>

1. <span data-ttu-id="5c05c-162">Modificare il file `sshd_config` nel percorso `/private/etc/ssh/sshd_config`.</span><span class="sxs-lookup"><span data-stu-id="5c05c-162">Edit the `sshd_config` file at location `/private/etc/ssh/sshd_config`.</span></span>

   <span data-ttu-id="5c05c-163">Aprire un editor di testo, come **nano**:</span><span class="sxs-lookup"><span data-stu-id="5c05c-163">Use a text editor such as **nano**:</span></span>

   ```bash
   sudo nano /private/etc/ssh/sshd_config
   ```

   <span data-ttu-id="5c05c-164">Assicurarsi che l'autenticazione della password sia abilitata:</span><span class="sxs-lookup"><span data-stu-id="5c05c-164">Make sure password authentication is enabled:</span></span>

   ```
   PasswordAuthentication yes
   ```

   <span data-ttu-id="5c05c-165">Aggiungere una voce del sottosistema PowerShell:</span><span class="sxs-lookup"><span data-stu-id="5c05c-165">Add a PowerShell subsystem entry:</span></span>

   ```
   Subsystem powershell /usr/local/bin/pwsh -sshs -NoLogo -NoProfile
   ```

   <span data-ttu-id="5c05c-166">Facoltativamente è possibile abilitare l'autenticazione della chiave:</span><span class="sxs-lookup"><span data-stu-id="5c05c-166">Optionally, enable key authentication:</span></span>

   ```
   PubkeyAuthentication yes
   ```

1. <span data-ttu-id="5c05c-167">Riavviare il servizio **sshd**.</span><span class="sxs-lookup"><span data-stu-id="5c05c-167">Restart the **sshd** service.</span></span>

   ```bash
   sudo launchctl stop com.openssh.sshd
   sudo launchctl start com.openssh.sshd
   ```

## <a name="authentication"></a><span data-ttu-id="5c05c-168">Autenticazione</span><span class="sxs-lookup"><span data-stu-id="5c05c-168">Authentication</span></span>

<span data-ttu-id="5c05c-169">La comunicazione remota di PowerShell su SSH si affida allo scambio di autenticazioni tra il clienti SSH e il servizio SSH e non implementa alcuno schema di autenticazione.</span><span class="sxs-lookup"><span data-stu-id="5c05c-169">PowerShell remoting over SSH relies on the authentication exchange between the SSH client and SSH service and doesn't implement any authentication schemes itself.</span></span> <span data-ttu-id="5c05c-170">Ciò significa che tutti gli schemi di autenticazione configurati, tra cui l'autenticazione a più fattori, sono gestiti da SSH e indipendenti da PowerShell.</span><span class="sxs-lookup"><span data-stu-id="5c05c-170">The result is that any configured authentication schemes including multi-factor authentication are handled by SSH and independent of PowerShell.</span></span> <span data-ttu-id="5c05c-171">Ad esempio, è possibile configurare il servizio SSH per richiedere l'autenticazione con chiave pubblica e una password monouso per maggiore sicurezza.</span><span class="sxs-lookup"><span data-stu-id="5c05c-171">For example, you can configure the SSH service to require public key authentication and a one-time password for added security.</span></span> <span data-ttu-id="5c05c-172">La configurazione dell'autenticazione a più fattori non rientra nell'ambito di questa documentazione.</span><span class="sxs-lookup"><span data-stu-id="5c05c-172">Configuration of multi-factor authentication is outside the scope of this documentation.</span></span> <span data-ttu-id="5c05c-173">Fare riferimento alla documentazione per SSH su come configurare l'autenticazione a più fattori in modo corretto e verificare se funziona all'esterno di PowerShell prima di provare a usarlo con la comunicazione remota di PowerShell.</span><span class="sxs-lookup"><span data-stu-id="5c05c-173">Refer to documentation for SSH on how to correctly configure multi-factor authentication and validate it works outside of PowerShell before attempting to use it with PowerShell remoting.</span></span>

## <a name="powershell-remoting-example"></a><span data-ttu-id="5c05c-174">Esempio di comunicazione remota di PowerShell</span><span class="sxs-lookup"><span data-stu-id="5c05c-174">PowerShell remoting example</span></span>

<span data-ttu-id="5c05c-175">Il modo più semplice per testare la comunicazione remota è provarla su un singolo computer.</span><span class="sxs-lookup"><span data-stu-id="5c05c-175">The easiest way to test remoting is to try it on a single computer.</span></span> <span data-ttu-id="5c05c-176">In questo esempio verrà creata una sessione remota verso lo stesso computer Linux.</span><span class="sxs-lookup"><span data-stu-id="5c05c-176">In this example, we create a remote session back to the same Linux computer.</span></span> <span data-ttu-id="5c05c-177">Poiché i cmdlet di PowerShell vengono usati in modo interattivo, vengono visualizzati prompt di SSH che chiedono di verificare il computer host e di immettere una password.</span><span class="sxs-lookup"><span data-stu-id="5c05c-177">We're using PowerShell cmdlets interactively so we see prompts from SSH asking to verify the host computer and prompting for a password.</span></span> <span data-ttu-id="5c05c-178">È possibile eseguire la stessa operazione in un computer Windows per verificare il funzionamento della comunicazione remota.</span><span class="sxs-lookup"><span data-stu-id="5c05c-178">You can do the same thing on a Windows computer to ensure remoting is working.</span></span> <span data-ttu-id="5c05c-179">Stabilire quindi la comunicazione remota tra i computer modificando il nome host.</span><span class="sxs-lookup"><span data-stu-id="5c05c-179">Then, remote between computers by changing the host name.</span></span>

```powershell
#
# Linux to Linux
#
$session = New-PSSession -HostName UbuntuVM1 -UserName TestUser
```

```Output
The authenticity of host 'UbuntuVM1 (9.129.17.107)' cannot be established.
ECDSA key fingerprint is SHA256:2kCbnhT2dUE6WCGgVJ8Hyfu1z2wE4lifaJXLO7QJy0Y.
Are you sure you want to continue connecting (yes/no)?
TestUser@UbuntuVM1s password:
```

```powershell
$session
```

```Output
 Id Name   ComputerName    ComputerType    State    ConfigurationName     Availability
 -- ----   ------------    ------------    -----    -----------------     ------------
  1 SSH1   UbuntuVM1       RemoteMachine   Opened   DefaultShell             Available
```

```powershell
Enter-PSSession $session
```

```Output
[UbuntuVM1]: PS /home/TestUser> uname -a
Linux TestUser-UbuntuVM1 4.2.0-42-generic 49~16.04.1-Ubuntu SMP Wed Jun 29 20:22:11 UTC 2016 x86_64 x86_64 x86_64 GNU/Linux

[UbuntuVM1]: PS /home/TestUser> Exit-PSSession
```

```powershell
Invoke-Command $session -ScriptBlock { Get-Process powershell }
```

```Output
Handles  NPM(K)    PM(K)      WS(K)     CPU(s)     Id  SI ProcessName                    PSComputerName
-------  ------    -----      -----     ------     --  -- -----------                    --------------
      0       0        0         19       3.23  10635 635 powershell                     UbuntuVM1
      0       0        0         21       4.92  11033 017 powershell                     UbuntuVM1
      0       0        0         20       3.07  11076 076 powershell                     UbuntuVM1
```

```powershell
#
# Linux to Windows
#
Enter-PSSession -HostName WinVM1 -UserName PTestName
```

```Output
PTestName@WinVM1s password:
```

```powershell
[WinVM1]: PS C:\Users\PTestName\Documents> cmd /c ver
```

```Output
Microsoft Windows [Version 10.0.10586]
```

```powershell
#
# Windows to Windows
#
C:\Users\PSUser\Documents>pwsh.exe
```

```Output
PowerShell
Copyright (c) Microsoft Corporation. All rights reserved.
```

```powershell
$session = New-PSSession -HostName WinVM2 -UserName PSRemoteUser
```

```Output
The authenticity of host 'WinVM2 (10.13.37.3)' can't be established.
ECDSA key fingerprint is SHA256:kSU6slAROyQVMEynVIXAdxSiZpwDBigpAF/TXjjWjmw.
Are you sure you want to continue connecting (yes/no)?
Warning: Permanently added 'WinVM2,10.13.37.3' (ECDSA) to the list of known hosts.
PSRemoteUser@WinVM2's password:
```

```powershell
$session
```

```Output
 Id Name            ComputerName    ComputerType    State         ConfigurationName     Availability
 -- ----            ------------    ------------    -----         -----------------     ------------
  1 SSH1            WinVM2          RemoteMachine   Opened        DefaultShell             Available
```

```powershell
Enter-PSSession -Session $session
```

```Output
[WinVM2]: PS C:\Users\PSRemoteUser\Documents> $PSVersionTable

Name                           Value
----                           -----
PSEdition                      Core
PSCompatibleVersions           {1.0, 2.0, 3.0, 4.0...}
SerializationVersion           1.1.0.1
BuildVersion                   3.0.0.0
CLRVersion
PSVersion                      6.0.0-alpha
WSManStackVersion              3.0
PSRemotingProtocolVersion      2.3
GitCommitId                    v6.0.0-alpha.17


[WinVM2]: PS C:\Users\PSRemoteUser\Documents>
```

### <a name="known-issues"></a><span data-ttu-id="5c05c-180">Problemi noti</span><span class="sxs-lookup"><span data-stu-id="5c05c-180">Known issues</span></span>

<span data-ttu-id="5c05c-181">Il comando **sudo** non funziona in una sessione remota verso un computer Linux.</span><span class="sxs-lookup"><span data-stu-id="5c05c-181">The **sudo** command doesn't work in a remote session to a Linux computer.</span></span>

## <a name="see-also"></a><span data-ttu-id="5c05c-182">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="5c05c-182">See also</span></span>

[<span data-ttu-id="5c05c-183">Installazione di PowerShell Core in Linux</span><span class="sxs-lookup"><span data-stu-id="5c05c-183">Installing PowerShell Core on Linux</span></span>](../../install/installing-powershell-core-on-linux.md#ubuntu-1604)

[<span data-ttu-id="5c05c-184">Installazione di PowerShell Core in macOS</span><span class="sxs-lookup"><span data-stu-id="5c05c-184">Installing PowerShell Core on macOS</span></span>](../../install/installing-powershell-core-on-macos.md)

[<span data-ttu-id="5c05c-185">Installazione di PowerShell Core in Windows</span><span class="sxs-lookup"><span data-stu-id="5c05c-185">Installing PowerShell Core on Windows</span></span>](../../install/installing-powershell-core-on-windows.md#msi)

[<span data-ttu-id="5c05c-186">Gestire Windows con OpenSSH</span><span class="sxs-lookup"><span data-stu-id="5c05c-186">Manage Windows with OpenSSH</span></span>](/windows-server/administration/openssh/openssh_overview)

[<span data-ttu-id="5c05c-187">Gestione delle chiavi OpenSSH</span><span class="sxs-lookup"><span data-stu-id="5c05c-187">Managing OpenSSH Keys</span></span>](/windows-server/administration/openssh/openssh_keymanagement)

[<span data-ttu-id="5c05c-188">SSH per Ubuntu</span><span class="sxs-lookup"><span data-stu-id="5c05c-188">Ubuntu SSH</span></span>](https://help.ubuntu.com/lts/serverguide/openssh-server.html)
