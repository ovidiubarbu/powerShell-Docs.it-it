---
title: Comunicazione remota di PowerShell su SSH
description: Comunicazione remota in PowerShell Core tramite SSH
ms.date: 08/14/2018
ms.openlocfilehash: 1d7bcb69c7e784bf745cb5c2633106ea53f6226a
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 03/18/2019
ms.locfileid: "58056533"
---
# <a name="powershell-remoting-over-ssh"></a><span data-ttu-id="3798f-103">Comunicazione remota di PowerShell su SSH</span><span class="sxs-lookup"><span data-stu-id="3798f-103">PowerShell Remoting Over SSH</span></span>

## <a name="overview"></a><span data-ttu-id="3798f-104">Panoramica</span><span class="sxs-lookup"><span data-stu-id="3798f-104">Overview</span></span>

<span data-ttu-id="3798f-105">La comunicazione remota di PowerShell solitamente usa WinRM per la negoziazione di connessione e il trasporto dei dati.</span><span class="sxs-lookup"><span data-stu-id="3798f-105">PowerShell remoting normally uses WinRM for connection negotiation and data transport.</span></span> <span data-ttu-id="3798f-106">SSH è ora disponibile per le piattaforme Linux e Windows e permette a PowerShell di offrire un'autentica comunicazione remota multipiattaforma.</span><span class="sxs-lookup"><span data-stu-id="3798f-106">SSH is now available for Linux and Windows platforms and allows true multiplatform PowerShell remoting.</span></span>

<span data-ttu-id="3798f-107">WinRM offre un solido modello di hosting per sessioni remote di PowerShell.</span><span class="sxs-lookup"><span data-stu-id="3798f-107">WinRM provides a robust hosting model for PowerShell remote sessions.</span></span> <span data-ttu-id="3798f-108">La comunicazione remota basata su SSH attualmente non supporta la configurazione di endpoint remoti e JEA (Just Enough Administration).</span><span class="sxs-lookup"><span data-stu-id="3798f-108">SSH-based remoting doesn't currently support remote endpoint configuration and JEA (Just Enough Administration).</span></span>

<span data-ttu-id="3798f-109">La comunicazione remota SSH permette la comunicazione remota di base di sessioni di PowerShell tra computer Windows e Linux.</span><span class="sxs-lookup"><span data-stu-id="3798f-109">SSH remoting lets you do basic PowerShell session remoting between Windows and Linux machines.</span></span> <span data-ttu-id="3798f-110">La comunicazione remota SSH crea un processo host di PowerShell nel computer di destinazione come sottosistema SSH.</span><span class="sxs-lookup"><span data-stu-id="3798f-110">SSH Remoting creates a PowerShell host process on the target machine as an SSH subsystem.</span></span>
<span data-ttu-id="3798f-111">In futuro verrà implementato un modello di hosting generale, simile a WinRM, per supportare la configurazione degli endpoint e JEA.</span><span class="sxs-lookup"><span data-stu-id="3798f-111">Eventually we'll implement a general hosting model, similar to WinRM, to support endpoint configuration and JEA.</span></span>

<span data-ttu-id="3798f-112">I cmdlet `New-PSSession`, `Enter-PSSession` e `Invoke-Command` includono ora un nuovo set di parametri per supportare questa nuova connessione di comunicazione remota.</span><span class="sxs-lookup"><span data-stu-id="3798f-112">The `New-PSSession`, `Enter-PSSession`, and `Invoke-Command` cmdlets now have a new parameter set to support this new remoting connection.</span></span>

```
[-HostName <string>]  [-UserName <string>]  [-KeyFilePath <string>]
```

<span data-ttu-id="3798f-113">Per creare una sessione remota, è necessario specificare il computer di destinazione con il parametro `HostName` e il nome utente con il parametro `UserName`.</span><span class="sxs-lookup"><span data-stu-id="3798f-113">To create a remote session, you specify the target machine with the `HostName` parameter and provide the user name with `UserName`.</span></span> <span data-ttu-id="3798f-114">Quando si eseguono i cmdlet in modo interattivo, viene chiesto di immettere una password.</span><span class="sxs-lookup"><span data-stu-id="3798f-114">When running the cmdlets interactively, you're prompted for a password.</span></span> <span data-ttu-id="3798f-115">È anche possibile usare l'autenticazione con chiave SSH tramite un file di chiave privata con il parametro `KeyFilePath`.</span><span class="sxs-lookup"><span data-stu-id="3798f-115">You can also, use SSH key authentication using a private key file with the `KeyFilePath` parameter.</span></span>

## <a name="general-setup-information"></a><span data-ttu-id="3798f-116">Informazioni generali di installazione</span><span class="sxs-lookup"><span data-stu-id="3798f-116">General setup information</span></span>

<span data-ttu-id="3798f-117">SSH deve essere installato in tutti i computer.</span><span class="sxs-lookup"><span data-stu-id="3798f-117">SSH must be installed on all machines.</span></span> <span data-ttu-id="3798f-118">Installare sia il client SSH (`ssh.exe`) sia il server (`sshd.exe`) in modo da poter comunicare in remoto da e verso i computer.</span><span class="sxs-lookup"><span data-stu-id="3798f-118">Install both the SSH client (`ssh.exe`) and server (`sshd.exe`) so that you can remote to and from the machines.</span></span> <span data-ttu-id="3798f-119">OpenSSH per Windows è ora disponibile in Windows 10 build 1809 e Windows Server 2019.</span><span class="sxs-lookup"><span data-stu-id="3798f-119">OpenSSH for Windows is now availabe in Windows 10 build 1809 and Windows Server 2019.</span></span> <span data-ttu-id="3798f-120">Per altre informazioni, vedere [OpenSSH in Windows](/windows-server/administration/openssh/openssh_overview).</span><span class="sxs-lookup"><span data-stu-id="3798f-120">For more information, see [OpenSSH for Windows](/windows-server/administration/openssh/openssh_overview).</span></span> <span data-ttu-id="3798f-121">Per Linux, installare SSH (incluso il server sshd) nel modo appropriato per la piattaforma in uso.</span><span class="sxs-lookup"><span data-stu-id="3798f-121">For Linux, install SSH (including sshd server) appropriate to your platform.</span></span> <span data-ttu-id="3798f-122">È necessario installare anche PowerShell Core da GitHub per ottenere la funzionalità di comunicazione remota SSH.</span><span class="sxs-lookup"><span data-stu-id="3798f-122">You also need to install PowerShell Core from GitHub to get the SSH remoting feature.</span></span> <span data-ttu-id="3798f-123">Il server SSH deve essere configurato per creare un sottosistema SSH in modo da ospitare un processo PowerShell nel computer remoto.</span><span class="sxs-lookup"><span data-stu-id="3798f-123">The SSH server must be configured to create an SSH subsystem to host a PowerShell process on the remote machine.</span></span> <span data-ttu-id="3798f-124">È anche necessario configurare l'autenticazione basata su password o su chiave.</span><span class="sxs-lookup"><span data-stu-id="3798f-124">You also must configure enable password or key-based authentication.</span></span>

## <a name="set-up-on-windows-machine"></a><span data-ttu-id="3798f-125">Installazione in computer Windows</span><span class="sxs-lookup"><span data-stu-id="3798f-125">Set up on Windows Machine</span></span>

1. <span data-ttu-id="3798f-126">Installare la versione più recente di [PowerShell Core per Windows](../../install/installing-powershell-core-on-windows.md#msi)</span><span class="sxs-lookup"><span data-stu-id="3798f-126">Install the latest version of [PowerShell Core for Windows](../../install/installing-powershell-core-on-windows.md#msi)</span></span>

   - <span data-ttu-id="3798f-127">È possibile stabilire se la comunicazione remota SSH è supportata esaminando i set di parametri per `New-PSSession`</span><span class="sxs-lookup"><span data-stu-id="3798f-127">You can tell if it has the SSH remoting support by looking at the parameter sets for `New-PSSession`</span></span>

   ```powershell
   Get-Command New-PSSession -syntax
   ```

   ```output
   New-PSSession [-HostName] <string[]> [-Name <string[]>] [-UserName <string>] [-KeyFilePath <string>] [-SSHTransport] [<CommonParameters>]
   ```

2. <span data-ttu-id="3798f-128">Installare la versione più recente di OpenSSH Win32.</span><span class="sxs-lookup"><span data-stu-id="3798f-128">Install the latest Win32 OpenSSH.</span></span> <span data-ttu-id="3798f-129">Per le istruzioni di installazione, vedere [Installazione di OpenSSH](/windows-server/administration/openssh/openssh_install_firstuse).</span><span class="sxs-lookup"><span data-stu-id="3798f-129">For installation instructions, see [Installation of OpenSSH](/windows-server/administration/openssh/openssh_install_firstuse).</span></span>
3. <span data-ttu-id="3798f-130">Modificare il file `sshd_config` in `$env:ProgramData\ssh`.</span><span class="sxs-lookup"><span data-stu-id="3798f-130">Edit the `sshd_config` file located at `$env:ProgramData\ssh`.</span></span>

   - <span data-ttu-id="3798f-131">Verificare che l'autenticazione della password sia abilitata</span><span class="sxs-lookup"><span data-stu-id="3798f-131">Make sure password authentication is enabled</span></span>

     ```
     PasswordAuthentication yes
     ```

     ```
     Subsystem    powershell c:/program files/powershell/6/pwsh.exe -sshs -NoLogo -NoProfile
     ```

     > [!NOTE]
     > <span data-ttu-id="3798f-132">È presente un bug in OpenSSH per Windows che impedisce il funzionamento dei percorsi eseguibili nel sottosistema che contengono spazi.</span><span class="sxs-lookup"><span data-stu-id="3798f-132">There is a bug in OpenSSH for Windows that prevents spaces from working in subsystem executable paths.</span></span> <span data-ttu-id="3798f-133">Per altre informazioni, vedere [questo problema in GitHub](https://github.com/PowerShell/Win32-OpenSSH/issues/784).</span><span class="sxs-lookup"><span data-stu-id="3798f-133">For more information, see [this GitHub issue](https://github.com/PowerShell/Win32-OpenSSH/issues/784).</span></span>

     <span data-ttu-id="3798f-134">Una soluzione consiste nel creare un collegamento simbolico alla directory di installazione di PowerShell senza spazi:</span><span class="sxs-lookup"><span data-stu-id="3798f-134">One solution is to create a symlink to the PowerShell installation directory that doesn't have spaces:</span></span>

     ```powershell
     mklink /D c:\pwsh "C:\Program Files\PowerShell\6"
     ```

     <span data-ttu-id="3798f-135">e quindi immetterlo nel sottosistema:</span><span class="sxs-lookup"><span data-stu-id="3798f-135">and then enter it in the subsystem:</span></span>

     ```
     Subsystem    powershell c:\pwsh\pwsh.exe -sshs -NoLogo -NoProfile
     ```

   - <span data-ttu-id="3798f-136">Facoltativamente è possibile abilitare l'autenticazione della chiave</span><span class="sxs-lookup"><span data-stu-id="3798f-136">Optionally enable key authentication</span></span>

     ```
     PubkeyAuthentication yes
     ```

4. <span data-ttu-id="3798f-137">Riavviare il servizio sshd</span><span class="sxs-lookup"><span data-stu-id="3798f-137">Restart the sshd service</span></span>

   ```powershell
   Restart-Service sshd
   ```

5. <span data-ttu-id="3798f-138">Aggiungere il percorso in cui è installato OpenSSH alla variabile di ambiente Path.</span><span class="sxs-lookup"><span data-stu-id="3798f-138">Add the path where OpenSSH is installed to your Path environment variable.</span></span> <span data-ttu-id="3798f-139">Ad esempio, `C:\Program Files\OpenSSH\`</span><span class="sxs-lookup"><span data-stu-id="3798f-139">For example, `C:\Program Files\OpenSSH\`.</span></span> <span data-ttu-id="3798f-140">Questa voce permette di trovare ssh.exe.</span><span class="sxs-lookup"><span data-stu-id="3798f-140">This entry allows for the ssh.exe to be found.</span></span>

## <a name="set-up-on-linux-ubuntu-1404-machine"></a><span data-ttu-id="3798f-141">Installazione in computer Linux (Ubuntu 14.04)</span><span class="sxs-lookup"><span data-stu-id="3798f-141">Set up on Linux (Ubuntu 14.04) Machine</span></span>

1. <span data-ttu-id="3798f-142">Installare la versione più recente della build di [PowerShell Core per Linux](../../install/installing-powershell-core-on-linux.md#ubuntu-1404) da GitHub</span><span class="sxs-lookup"><span data-stu-id="3798f-142">Install the latest [PowerShell Core for Linux](../../install/installing-powershell-core-on-linux.md#ubuntu-1404) build from GitHub</span></span>
2. <span data-ttu-id="3798f-143">Installare [SSH per Ubuntu](https://help.ubuntu.com/lts/serverguide/openssh-server.html) in base alle esigenze</span><span class="sxs-lookup"><span data-stu-id="3798f-143">Install [Ubuntu SSH](https://help.ubuntu.com/lts/serverguide/openssh-server.html) as needed</span></span>

   ```bash
   sudo apt install openssh-client
   sudo apt install openssh-server
   ```

3. <span data-ttu-id="3798f-144">Modificare il file sshd_config nel percorso /etc/ssh</span><span class="sxs-lookup"><span data-stu-id="3798f-144">Edit the sshd_config file at location /etc/ssh</span></span>

   - <span data-ttu-id="3798f-145">Verificare che l'autenticazione della password sia abilitata</span><span class="sxs-lookup"><span data-stu-id="3798f-145">Make sure password authentication is enabled</span></span>

   ```
   PasswordAuthentication yes
   ```

   - <span data-ttu-id="3798f-146">Aggiungere una voce del sottosistema PowerShell</span><span class="sxs-lookup"><span data-stu-id="3798f-146">Add a PowerShell subsystem entry</span></span>

   ```
   Subsystem powershell /usr/bin/pwsh -sshs -NoLogo -NoProfile
   ```

   - <span data-ttu-id="3798f-147">Facoltativamente è possibile abilitare l'autenticazione della chiave</span><span class="sxs-lookup"><span data-stu-id="3798f-147">Optionally enable key authentication</span></span>

   ```
   PubkeyAuthentication yes
   ```

4. <span data-ttu-id="3798f-148">Riavviare il servizio sshd</span><span class="sxs-lookup"><span data-stu-id="3798f-148">Restart the sshd service</span></span>

   ```bash
   sudo service sshd restart
   ```

## <a name="set-up-on-macos-machine"></a><span data-ttu-id="3798f-149">Installazione in computer MacOS</span><span class="sxs-lookup"><span data-stu-id="3798f-149">Set up on MacOS Machine</span></span>

1. <span data-ttu-id="3798f-150">Installare la build più recente di [PowerShell Core per MacOS](../../install/installing-powershell-core-on-macos.md)</span><span class="sxs-lookup"><span data-stu-id="3798f-150">Install the latest [PowerShell Core for MacOS](../../install/installing-powershell-core-on-macos.md) build</span></span>

   - <span data-ttu-id="3798f-151">Assicurarsi che la comunicazione remota SSH sia abilitata attenendosi alla procedura seguente:</span><span class="sxs-lookup"><span data-stu-id="3798f-151">Make sure SSH Remoting is enabled by following these steps:</span></span>
     - <span data-ttu-id="3798f-152">Aprire `System Preferences`</span><span class="sxs-lookup"><span data-stu-id="3798f-152">Open `System Preferences`</span></span>
     - <span data-ttu-id="3798f-153">Fare clic su `Sharing`</span><span class="sxs-lookup"><span data-stu-id="3798f-153">Click on `Sharing`</span></span>
     - <span data-ttu-id="3798f-154">Controllare `Remote Login`: deve indicare `Remote Login: On`</span><span class="sxs-lookup"><span data-stu-id="3798f-154">Check `Remote Login` - Should say `Remote Login: On`</span></span>
     - <span data-ttu-id="3798f-155">Consentire l'accesso agli utenti appropriati</span><span class="sxs-lookup"><span data-stu-id="3798f-155">Allow access to appropriate users</span></span>

2. <span data-ttu-id="3798f-156">Modificare il file `sshd_config` nel percorso `/private/etc/ssh/sshd_config`</span><span class="sxs-lookup"><span data-stu-id="3798f-156">Edit the `sshd_config` file at location `/private/etc/ssh/sshd_config`</span></span>

   - <span data-ttu-id="3798f-157">Usare l'editor preferito o</span><span class="sxs-lookup"><span data-stu-id="3798f-157">Use your favorite editor or</span></span>

     ```bash
     sudo nano /private/etc/ssh/sshd_config
     ```

   - <span data-ttu-id="3798f-158">Verificare che l'autenticazione della password sia abilitata</span><span class="sxs-lookup"><span data-stu-id="3798f-158">Make sure password authentication is enabled</span></span>

     ```
     PasswordAuthentication yes
     ```

   - <span data-ttu-id="3798f-159">Aggiungere una voce del sottosistema PowerShell</span><span class="sxs-lookup"><span data-stu-id="3798f-159">Add a PowerShell subsystem entry</span></span>

     ```
     Subsystem powershell /usr/local/bin/pwsh -sshs -NoLogo -NoProfile
     ```

   - <span data-ttu-id="3798f-160">Facoltativamente è possibile abilitare l'autenticazione della chiave</span><span class="sxs-lookup"><span data-stu-id="3798f-160">Optionally enable key authentication</span></span>

     ```
     PubkeyAuthentication yes
     ```

3. <span data-ttu-id="3798f-161">Riavviare il servizio sshd</span><span class="sxs-lookup"><span data-stu-id="3798f-161">Restart the sshd service</span></span>

   ```bash
   sudo launchctl stop com.openssh.sshd
   sudo launchctl start com.openssh.sshd
   ```

## <a name="authentication"></a><span data-ttu-id="3798f-162">Autenticazione</span><span class="sxs-lookup"><span data-stu-id="3798f-162">Authentication</span></span>

<span data-ttu-id="3798f-163">La comunicazione remota di PowerShell su SSH si affida allo scambio di autenticazioni tra il clienti SSH e il servizio SSH e non implementa alcuno schema di autenticazione.</span><span class="sxs-lookup"><span data-stu-id="3798f-163">PowerShell remoting over SSH relies on the authentication exchange between the SSH client and SSH service and does not implement any authentication schemes itself.</span></span>
<span data-ttu-id="3798f-164">Ciò significa che tutti gli schemi di autenticazione configurati, tra cui l'autenticazione a più fattori, sono gestiti da SSH e indipendenti da PowerShell.</span><span class="sxs-lookup"><span data-stu-id="3798f-164">This means that any configured authentication schemes including multi-factor authentication is handled by SSH and independent of PowerShell.</span></span>
<span data-ttu-id="3798f-165">Ad esempio, è possibile configurare il servizio SSH per richiedere l'autenticazione con chiave pubblica e una password monouso per maggiore sicurezza.</span><span class="sxs-lookup"><span data-stu-id="3798f-165">For example, you can configure the SSH service to require public key authentication as well as a one-time password for added security.</span></span>
<span data-ttu-id="3798f-166">La configurazione dell'autenticazione a più fattori non rientra nell'ambito di questa documentazione.</span><span class="sxs-lookup"><span data-stu-id="3798f-166">Configuration of multi-factor authentication is outside the scope of this documentation.</span></span>
<span data-ttu-id="3798f-167">Fare riferimento alla documentazione per SSH su come configurare l'autenticazione a più fattori in modo corretto e verificare se funziona all'esterno di PowerShell prima di provare a usarlo con la comunicazione remota di PowerShell.</span><span class="sxs-lookup"><span data-stu-id="3798f-167">Refer to documentation for SSH on how to correctly configure multi-factor authentication and validate it works outside of PowerShell before attempting to use it with PowerShell remoting.</span></span>

## <a name="powershell-remoting-example"></a><span data-ttu-id="3798f-168">Esempio di comunicazione remota di PowerShell</span><span class="sxs-lookup"><span data-stu-id="3798f-168">PowerShell Remoting Example</span></span>

<span data-ttu-id="3798f-169">Il modo più semplice per testare la comunicazione remota è provarla su un singolo computer.</span><span class="sxs-lookup"><span data-stu-id="3798f-169">The easiest way to test remoting is to try it on a single machine.</span></span> <span data-ttu-id="3798f-170">In questo esempio verrà creata una sessione remota verso lo stesso computer Linux.</span><span class="sxs-lookup"><span data-stu-id="3798f-170">In this example, we create a remote session back to the same Linux machine.</span></span> <span data-ttu-id="3798f-171">Poiché i cmdlet di PowerShell vengono usati in modo interattivo, vengono visualizzati prompt di SSH che chiedono di verificare il computer host e di immettere una password.</span><span class="sxs-lookup"><span data-stu-id="3798f-171">We are using PowerShell cmdlets interactively so we see prompts from SSH asking to verify the host computer and prompting for a password.</span></span> <span data-ttu-id="3798f-172">È possibile eseguire la stessa operazione in un computer Windows per verificare il funzionamento della comunicazione remota.</span><span class="sxs-lookup"><span data-stu-id="3798f-172">You can do the same thing on a Windows machine to ensure remoting is working.</span></span> <span data-ttu-id="3798f-173">Stabilire quindi una comunicazione remota tra i computer modificando il nome host.</span><span class="sxs-lookup"><span data-stu-id="3798f-173">Then remote between machines by changing the host name.</span></span>

```powershell
#
# Linux to Linux
#
$session = New-PSSession -HostName UbuntuVM1 -UserName TestUser
```

```output
The authenticity of host 'UbuntuVM1 (9.129.17.107)' cannot be established.
ECDSA key fingerprint is SHA256:2kCbnhT2dUE6WCGgVJ8Hyfu1z2wE4lifaJXLO7QJy0Y.
Are you sure you want to continue connecting (yes/no)?
TestUser@UbuntuVM1s password:
```

```powershell
$session
```

```output
 Id Name   ComputerName    ComputerType    State    ConfigurationName     Availability
 -- ----   ------------    ------------    -----    -----------------     ------------
  1 SSH1   UbuntuVM1       RemoteMachine   Opened   DefaultShell             Available
```

```powershell
Enter-PSSession $session
```

```output
[UbuntuVM1]: PS /home/TestUser> uname -a
Linux TestUser-UbuntuVM1 4.2.0-42-generic 49~14.04.1-Ubuntu SMP Wed Jun 29 20:22:11 UTC 2016 x86_64 x86_64 x86_64 GNU/Linux

[UbuntuVM1]: PS /home/TestUser> Exit-PSSession
```

```powershell
Invoke-Command $session -ScriptBlock { Get-Process powershell }
```

```output
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

```output
PTestName@WinVM1s password:
```

```powershell
[WinVM1]: PS C:\Users\PTestName\Documents> cmd /c ver
```

```output
Microsoft Windows [Version 10.0.10586]
```

```powershell
#
# Windows to Windows
#
C:\Users\PSUser\Documents>pwsh.exe
```

```output
PowerShell
Copyright (c) Microsoft Corporation. All rights reserved.
```

```powershell
$session = New-PSSession -HostName WinVM2 -UserName PSRemoteUser
```

```output
The authenticity of host 'WinVM2 (10.13.37.3)' can't be established.
ECDSA key fingerprint is SHA256:kSU6slAROyQVMEynVIXAdxSiZpwDBigpAF/TXjjWjmw.
Are you sure you want to continue connecting (yes/no)?
Warning: Permanently added 'WinVM2,10.13.37.3' (ECDSA) to the list of known hosts.
PSRemoteUser@WinVM2's password:
```

```powershell
$session
```

```output
 Id Name            ComputerName    ComputerType    State         ConfigurationName     Availability
 -- ----            ------------    ------------    -----         -----------------     ------------
  1 SSH1            WinVM2          RemoteMachine   Opened        DefaultShell             Available
```

```powershell
Enter-PSSession -Session $session
```

```output
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

### <a name="known-issues"></a><span data-ttu-id="3798f-174">Problemi noti</span><span class="sxs-lookup"><span data-stu-id="3798f-174">Known Issues</span></span>

<span data-ttu-id="3798f-175">Il comando sudo non funziona in una sessione remota verso computer Linux.</span><span class="sxs-lookup"><span data-stu-id="3798f-175">The sudo command doesn't work in remote session to Linux machine.</span></span>

## <a name="see-also"></a><span data-ttu-id="3798f-176">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="3798f-176">See Also</span></span>

[<span data-ttu-id="3798f-177">PowerShell Core per Windows</span><span class="sxs-lookup"><span data-stu-id="3798f-177">PowerShell Core for Windows</span></span>](../../install/installing-powershell-core-on-windows.md#msi)

[<span data-ttu-id="3798f-178">PowerShell Core per Linux</span><span class="sxs-lookup"><span data-stu-id="3798f-178">PowerShell Core for Linux</span></span>](../../install/installing-powershell-core-on-linux.md#ubuntu-1404)

[<span data-ttu-id="3798f-179">PowerShell Core per MacOS</span><span class="sxs-lookup"><span data-stu-id="3798f-179">PowerShell Core for MacOS</span></span>](../../install/installing-powershell-core-on-macos.md)

[<span data-ttu-id="3798f-180">OpenSSH in Windows</span><span class="sxs-lookup"><span data-stu-id="3798f-180">OpenSSH for Windows</span></span>](/windows-server/administration/openssh/openssh_overview)

[<span data-ttu-id="3798f-181">SSH per Ubuntu</span><span class="sxs-lookup"><span data-stu-id="3798f-181">Ubuntu SSH</span></span>](https://help.ubuntu.com/lts/serverguide/openssh-server.html)
