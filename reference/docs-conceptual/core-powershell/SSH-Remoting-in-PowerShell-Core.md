
# <a name="powershell-remoting-over-ssh"></a><span data-ttu-id="a481b-101">Comunicazione remota di PowerShell su SSH</span><span class="sxs-lookup"><span data-stu-id="a481b-101">PowerShell Remoting Over SSH</span></span>

## <a name="overview"></a><span data-ttu-id="a481b-102">Panoramica</span><span class="sxs-lookup"><span data-stu-id="a481b-102">Overview</span></span>

<span data-ttu-id="a481b-103">La comunicazione remota di PowerShell solitamente usa WinRM per la negoziazione di connessione e il trasporto dei dati.</span><span class="sxs-lookup"><span data-stu-id="a481b-103">PowerShell remoting normally uses WinRM for connection negotiation and data transport.</span></span>
<span data-ttu-id="a481b-104">Per questa implementazione di comunicazione remota è stato scelto SSH in quanto è ora disponibile per piattaforme Linux e Windows e consente una vera comunicazione remota multipiattaforma per PowerShell.</span><span class="sxs-lookup"><span data-stu-id="a481b-104">SSH was chosen for this remoting implementation since it is now available for both Linux and Windows platforms and allows true multiplatform PowerShell remoting.</span></span>
<span data-ttu-id="a481b-105">Tuttavia, WinRM offre anche un solido modello di hosting per le sessioni remote di PowerShell che questa implementazione ancora non offre.</span><span class="sxs-lookup"><span data-stu-id="a481b-105">However, WinRM also provides a robust hosting model for PowerShell remote sessions which this implementation does not yet do.</span></span>
<span data-ttu-id="a481b-106">Ciò significa che la configurazione di endpoint remoto e il profilo JEA (Just Enough Administration) di PowerShell non sono ancora supportati in questa implementazione.</span><span class="sxs-lookup"><span data-stu-id="a481b-106">And this means that PowerShell remote endpoint configuration and JEA (Just Enough Administration) is not yet supported in this implementation.</span></span>

<span data-ttu-id="a481b-107">La comunicazione remota SSH per PowerShell consente di eseguire la comunicazione remota di base di sessioni di PowerShell tra computer Windows e Linux.</span><span class="sxs-lookup"><span data-stu-id="a481b-107">PowerShell SSH remoting lets you do basic PowerShell session remoting between Windows and Linux machines.</span></span>
<span data-ttu-id="a481b-108">Ciò avviene creando un processo di hosting di PowerShell nel computer di destinazione come sottosistema SSH.</span><span class="sxs-lookup"><span data-stu-id="a481b-108">This is done by creating a PowerShell hosting process on the target machine as an SSH subsystem.</span></span>
<span data-ttu-id="a481b-109">Infine il processo verrà modificato in un modello di hosting più generale simile al funzionamento di WinRM per supportare la configurazione dell'endpoint e del profilo JEA.</span><span class="sxs-lookup"><span data-stu-id="a481b-109">Eventually this will be changed to a more general hosting model similar to how WinRM works in order to support endpoint configuration and JEA.</span></span>

<span data-ttu-id="a481b-110">I cmdlet `New-PSSession`, `Enter-PSSession` e `Invoke-Command` hanno ora un nuovo set di parametri per semplificare la nuova connessione di comunicazione remota</span><span class="sxs-lookup"><span data-stu-id="a481b-110">The `New-PSSession`, `Enter-PSSession` and `Invoke-Command` cmdlets now have a new parameter set to facilitate this new remoting connection</span></span>

```
[-HostName <string>]  [-UserName <string>]  [-KeyFilePath <string>]
```

<span data-ttu-id="a481b-111">Questo nuovo set di parametri verrà probabilmente modificato, ma per ora consente di creare sessioni Pssession di SSH con cui è possibile interagire dalla riga di comando o da cui è possibile richiamare comandi e script.</span><span class="sxs-lookup"><span data-stu-id="a481b-111">This new parameter set will likely change but for now allows you to create SSH PSSessions that you can interact with from the command line or invoke commands and scripts on.</span></span>
<span data-ttu-id="a481b-112">È necessario specificare il computer di destinazione con il parametro HostName e il nome utente con il parametro UserName.</span><span class="sxs-lookup"><span data-stu-id="a481b-112">You specify the target machine with the HostName parameter and provide the user name with UserName.</span></span>
<span data-ttu-id="a481b-113">Quando si eseguono i cmdlet in modo interattivo dalla riga di comando di PowerShell verrà richiesto di immettere una password.</span><span class="sxs-lookup"><span data-stu-id="a481b-113">When running the cmdlets interactively at the PowerShell command line you will be prompted for a password.</span></span>
<span data-ttu-id="a481b-114">Ma è anche possibile usare l'autenticazione con chiave SSH e specificare un percorso di file di chiave privata con il parametro KeyFilePath.</span><span class="sxs-lookup"><span data-stu-id="a481b-114">But you also have the option to use SSH key authentication and provide a private key file path with the KeyFilePath parameter.</span></span>

## <a name="general-setup-information"></a><span data-ttu-id="a481b-115">Informazioni generali di installazione</span><span class="sxs-lookup"><span data-stu-id="a481b-115">General setup information</span></span>

<span data-ttu-id="a481b-116">SSH deve essere installato in tutti i computer.</span><span class="sxs-lookup"><span data-stu-id="a481b-116">SSH is required to be installed on all machines.</span></span>
<span data-ttu-id="a481b-117">È necessario installare sia il client (`ssh.exe`) che il server (`sshd.exe`) in modo da poter provare la comunicazione remota da e verso i computer.</span><span class="sxs-lookup"><span data-stu-id="a481b-117">You should install both client (`ssh.exe`) and server (`sshd.exe`) so that you can experiment with remoting to and from the machines.</span></span>
<span data-ttu-id="a481b-118">Per Windows è necessario installare [OpenSSH - Win32 da GitHub](https://github.com/PowerShell/Win32-OpenSSH/releases).</span><span class="sxs-lookup"><span data-stu-id="a481b-118">For Windows you will need to install [Win32 OpenSSH from GitHub](https://github.com/PowerShell/Win32-OpenSSH/releases).</span></span>
<span data-ttu-id="a481b-119">Per Linux è necessario installare SSH, incluso il server sshd, appropriato per la piattaforma in uso.</span><span class="sxs-lookup"><span data-stu-id="a481b-119">For Linux you will need to install SSH (including sshd server) appropriate to your platform.</span></span>
<span data-ttu-id="a481b-120">Sono necessari anche una build o un pacchetto di PowerShell recenti da GitHub con la funzionalità di comunicazione remota SSH.</span><span class="sxs-lookup"><span data-stu-id="a481b-120">You will also need a recent PowerShell build or package from GitHub having the SSH remoting feature.</span></span>
<span data-ttu-id="a481b-121">I sottosistemi SSH vengono usati per stabilire un processo PowerShell nel computer remoto quindi il server SSH dovrà essere configurato a tale scopo.</span><span class="sxs-lookup"><span data-stu-id="a481b-121">SSH subsystems is used to establish a PowerShell process on the remote machine and the SSH server will need to be configured for that.</span></span>
<span data-ttu-id="a481b-122">È anche necessario abilitare l'autenticazione della password e, facoltativamente, l'autenticazione basata su chiavi.</span><span class="sxs-lookup"><span data-stu-id="a481b-122">In addition you will need to enable password authentication and optionally key based authentication.</span></span>

## <a name="setup-on-windows-machine"></a><span data-ttu-id="a481b-123">Installazione in computer Windows</span><span class="sxs-lookup"><span data-stu-id="a481b-123">Setup on Windows Machine</span></span>

1. <span data-ttu-id="a481b-124">Installare la versione più recente di [PowerShell Core per Windows]</span><span class="sxs-lookup"><span data-stu-id="a481b-124">Install the latest version of [PowerShell Core for Windows]</span></span>
   - <span data-ttu-id="a481b-125">È possibile stabilire se la comunicazione remota SSH è supportata esaminando i set di parametri per `New-PSSession`</span><span class="sxs-lookup"><span data-stu-id="a481b-125">You can tell if it has the SSH remoting support by looking at the parameter sets for `New-PSSession`</span></span>

   ```powershell
   Get-Command New-PSSession -syntax
   ```

   ```output
   New-PSSession [-HostName] <string[]> [-Name <string[]>] [-UserName <string>] [-KeyFilePath <string>] [-SSHTransport] [<CommonParameters>]
   ```

2. <span data-ttu-id="a481b-126">Installare la build più recente di [OpenSSH - Win32] da GitHub usando le istruzioni di [installazione]</span><span class="sxs-lookup"><span data-stu-id="a481b-126">Install the latest [Win32 OpenSSH] build from GitHub using the [installation] instructions</span></span>
3. <span data-ttu-id="a481b-127">Modificare il file sshd_config nel percorso in cui è installato OpenSSH - Win32</span><span class="sxs-lookup"><span data-stu-id="a481b-127">Edit the sshd_config file at the location where you installed Win32 OpenSSH</span></span>
   - <span data-ttu-id="a481b-128">Verificare che l'autenticazione della password sia abilitata</span><span class="sxs-lookup"><span data-stu-id="a481b-128">Make sure password authentication is enabled</span></span>

   ```
   PasswordAuthentication yes
   ```

    ```
    Subsystem    powershell c:/program files/powershell/6.0.0/pwsh.exe -sshs -NoLogo -NoProfile
    ```

    > [!NOTE]
    <span data-ttu-id="a481b-129">È presente un bug in OpenSSH per Windows che impedisce il funzionamento dei percorsi eseguibili nel sottosistema che contengono spazi.</span><span class="sxs-lookup"><span data-stu-id="a481b-129">There is a bug in OpenSSH for Windows that prevents spaces from working in subsystem executable paths.</span></span>
    <span data-ttu-id="a481b-130">Per ottenere altre informazioni, vedere [questo problema in GitHub](https://github.com/PowerShell/Win32-OpenSSH/issues/784).</span><span class="sxs-lookup"><span data-stu-id="a481b-130">See [this issue on GitHub for more information](https://github.com/PowerShell/Win32-OpenSSH/issues/784).</span></span>

    <span data-ttu-id="a481b-131">Una soluzione consiste nel creare un collegamento simbolico alla directory di installazione di Powershell che non contenga spazi:</span><span class="sxs-lookup"><span data-stu-id="a481b-131">One solution is to create a symlink to the Powershell installation directory that does not contain spaces:</span></span>

    ```powershell
    mklink /D c:\pwsh "C:\Program Files\PowerShell\6.0.0"
    ```

    <span data-ttu-id="a481b-132">e quindi immetterlo nel sottosistema:</span><span class="sxs-lookup"><span data-stu-id="a481b-132">and then enter it in the subsystem:</span></span>

    ```
    Subsystem    powershell c:\pwsh\pwsh.exe -sshs -NoLogo -NoProfile
    ```

   ```
   Subsystem    powershell c:/program files/powershell/6.0.0/pwsh.exe -sshs -NoLogo -NoProfile
   ```

   - <span data-ttu-id="a481b-133">Facoltativamente è possibile abilitare l'autenticazione della chiave</span><span class="sxs-lookup"><span data-stu-id="a481b-133">Optionally enable key authentication</span></span>

   ```
   PubkeyAuthentication yes
   ```

4. <span data-ttu-id="a481b-134">Riavviare il servizio sshd</span><span class="sxs-lookup"><span data-stu-id="a481b-134">Restart the sshd service</span></span>

   ```powershell
   Restart-Service sshd
   ```

5. <span data-ttu-id="a481b-135">Aggiungere il percorso in cui è installato OpenSSH alla variabile di percorso Env</span><span class="sxs-lookup"><span data-stu-id="a481b-135">Add the path where OpenSSH is installed to your Path Env Variable</span></span>
   - <span data-ttu-id="a481b-136">Dovrebbe trovarsi nelle righe di `C:\Program Files\OpenSSH\`</span><span class="sxs-lookup"><span data-stu-id="a481b-136">This should be along the lines of `C:\Program Files\OpenSSH\`</span></span>
   - <span data-ttu-id="a481b-137">In questo modo ssh.exe può essere individuato</span><span class="sxs-lookup"><span data-stu-id="a481b-137">This allows for the ssh.exe to be found</span></span>

## <a name="setup-on-linux-ubuntu-1404-machine"></a><span data-ttu-id="a481b-138">Installazione in computer Linux (Ubuntu 14.04)</span><span class="sxs-lookup"><span data-stu-id="a481b-138">Setup on Linux (Ubuntu 14.04) Machine</span></span>

1. <span data-ttu-id="a481b-139">Installare la build più recente di [PowerShell Core per Linux] da GitHub</span><span class="sxs-lookup"><span data-stu-id="a481b-139">Install the latest [PowerShell Core for Linux] build from GitHub</span></span>
2. <span data-ttu-id="a481b-140">Installare [SSH per Ubuntu] in base alle esigenze</span><span class="sxs-lookup"><span data-stu-id="a481b-140">Install [Ubuntu SSH] as needed</span></span>

   ```bash
   sudo apt install openssh-client
   sudo apt install openssh-server
   ```

3. <span data-ttu-id="a481b-141">Modificare il file sshd_config nel percorso /etc/ssh</span><span class="sxs-lookup"><span data-stu-id="a481b-141">Edit the sshd_config file at location /etc/ssh</span></span>
   - <span data-ttu-id="a481b-142">Verificare che l'autenticazione della password sia abilitata</span><span class="sxs-lookup"><span data-stu-id="a481b-142">Make sure password authentication is enabled</span></span>

   ```
   PasswordAuthentication yes
   ```

   - <span data-ttu-id="a481b-143">Aggiungere una voce del sottosistema PowerShell</span><span class="sxs-lookup"><span data-stu-id="a481b-143">Add a PowerShell subsystem entry</span></span>

   ```
   Subsystem powershell /usr/bin/pwsh -sshs -NoLogo -NoProfile
   ```

   - <span data-ttu-id="a481b-144">Facoltativamente è possibile abilitare l'autenticazione della chiave</span><span class="sxs-lookup"><span data-stu-id="a481b-144">Optionally enable key authentication</span></span>

   ```
   PubkeyAuthentication yes
   ```

4. <span data-ttu-id="a481b-145">Riavviare il servizio sshd</span><span class="sxs-lookup"><span data-stu-id="a481b-145">Restart the sshd service</span></span>

   ```bash
   sudo service sshd restart
   ```

## <a name="setup-on-macos-machine"></a><span data-ttu-id="a481b-146">Installazione in computer MacOS</span><span class="sxs-lookup"><span data-stu-id="a481b-146">Setup on MacOS Machine</span></span>

1. <span data-ttu-id="a481b-147">Installare la build più recente di [PowerShell Core per MacOS]</span><span class="sxs-lookup"><span data-stu-id="a481b-147">Install the latest [PowerShell Core for MacOS] build</span></span>
   - <span data-ttu-id="a481b-148">Assicurarsi che la comunicazione remota SSH sia abilitata attenendosi alla procedura seguente:</span><span class="sxs-lookup"><span data-stu-id="a481b-148">Make sure SSH Remoting is enabled by following these steps:</span></span>
     - <span data-ttu-id="a481b-149">Aprire `System Preferences`</span><span class="sxs-lookup"><span data-stu-id="a481b-149">Open `System Preferences`</span></span>
     - <span data-ttu-id="a481b-150">Fare clic su `Sharing`</span><span class="sxs-lookup"><span data-stu-id="a481b-150">Click on `Sharing`</span></span>
     - <span data-ttu-id="a481b-151">Controllare `Remote Login`: deve indicare `Remote Login: On`</span><span class="sxs-lookup"><span data-stu-id="a481b-151">Check `Remote Login` - Should say `Remote Login: On`</span></span>
     - <span data-ttu-id="a481b-152">Consentire l'accesso agli utenti appropriati</span><span class="sxs-lookup"><span data-stu-id="a481b-152">Allow access to appropriate users</span></span>
2. <span data-ttu-id="a481b-153">Modificare il file `sshd_config` nel percorso `/private/etc/ssh/sshd_config`</span><span class="sxs-lookup"><span data-stu-id="a481b-153">Edit the `sshd_config` file at location `/private/etc/ssh/sshd_config`</span></span>
   - <span data-ttu-id="a481b-154">Usare l'editor preferito o</span><span class="sxs-lookup"><span data-stu-id="a481b-154">Use your favorite editor or</span></span>

     ```bash
     sudo nano /private/etc/ssh/sshd_config
     ```

   - <span data-ttu-id="a481b-155">Verificare che l'autenticazione della password sia abilitata</span><span class="sxs-lookup"><span data-stu-id="a481b-155">Make sure password authentication is enabled</span></span>

     ```
     PasswordAuthentication yes
     ```

   - <span data-ttu-id="a481b-156">Aggiungere una voce del sottosistema PowerShell</span><span class="sxs-lookup"><span data-stu-id="a481b-156">Add a PowerShell subsystem entry</span></span>

     ```
     Subsystem powershell /usr/local/bin/pwsh -sshs -NoLogo -NoProfile
     ```

   - <span data-ttu-id="a481b-157">Facoltativamente è possibile abilitare l'autenticazione della chiave</span><span class="sxs-lookup"><span data-stu-id="a481b-157">Optionally enable key authentication</span></span>

     ```
     PubkeyAuthentication yes
     ```

3. <span data-ttu-id="a481b-158">Riavviare il servizio sshd</span><span class="sxs-lookup"><span data-stu-id="a481b-158">Restart the sshd service</span></span>

   ```bash
   sudo launchctl stop com.openssh.sshd
   sudo launchctl start com.openssh.sshd
   ```

## <a name="powershell-remoting-example"></a><span data-ttu-id="a481b-159">Esempio di comunicazione remota di PowerShell</span><span class="sxs-lookup"><span data-stu-id="a481b-159">PowerShell Remoting Example</span></span>

<span data-ttu-id="a481b-160">Il modo più semplice per testare la comunicazione remota è semplicemente provarla su un singolo computer.</span><span class="sxs-lookup"><span data-stu-id="a481b-160">The easiest way to test remoting is to just try it on a single machine.</span></span>
<span data-ttu-id="a481b-161">Qui verrà creata una sessione remota verso lo stesso computer in Linux.</span><span class="sxs-lookup"><span data-stu-id="a481b-161">Here I will create a remote session back to the same machine on a Linux box.</span></span>
<span data-ttu-id="a481b-162">Si noti che vengono usati i cmdlet di PowerShell da un prompt dei comandi in modo che siano visibili i prompt di SSH che chiedono di verificare il computer host, nonché le richieste di password.</span><span class="sxs-lookup"><span data-stu-id="a481b-162">Notice that I am using PowerShell cmdlets from a command prompt so we see prompts from SSH asking to verify the host computer as well as password prompts.</span></span>
<span data-ttu-id="a481b-163">È possibile eseguire la stessa operazione in un computer Windows per assicurarsi che la comunicazione remota funzioni e quindi eseguirla tra i computer cambiando semplicemente il nome host.</span><span class="sxs-lookup"><span data-stu-id="a481b-163">You can do the same thing on a Windows machine to ensure remoting is working there and then remote between machines by simply changing the host name.</span></span>

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
 Id Name            ComputerName    ComputerType    State         ConfigurationName     Availability
 -- ----            ------------    ------------    -----         -----------------     ------------
  1 SSH1            UbuntuVM1       RemoteMachine   Opened        DefaultShell             Available
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

### <a name="known-issues"></a><span data-ttu-id="a481b-164">Problemi noti</span><span class="sxs-lookup"><span data-stu-id="a481b-164">Known Issues</span></span>

- <span data-ttu-id="a481b-165">Il comando sudo non funziona nella sessione remota per computer Linux.</span><span class="sxs-lookup"><span data-stu-id="a481b-165">sudo command does not work in remote session to Linux machine.</span></span>

## <a name="see-also"></a><span data-ttu-id="a481b-166">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="a481b-166">See Also</span></span>

[<span data-ttu-id="a481b-167">PowerShell Core per Windows</span><span class="sxs-lookup"><span data-stu-id="a481b-167">PowerShell Core for Windows</span></span>](../setup/installing-powershell-core-on-windows.md#msi)

[<span data-ttu-id="a481b-168">PowerShell Core per Linux</span><span class="sxs-lookup"><span data-stu-id="a481b-168">PowerShell Core for Linux</span></span>](../setup/installing-powershell-core-on-linux.md#ubuntu-1404)

[<span data-ttu-id="a481b-169">PowerShell Core per MacOS</span><span class="sxs-lookup"><span data-stu-id="a481b-169">PowerShell Core for MacOS</span></span>](../setup/installing-powershell-core-on-macos.md)

[<span data-ttu-id="a481b-170">OpenSSH - Win32</span><span class="sxs-lookup"><span data-stu-id="a481b-170">Win32 OpenSSH</span></span>](https://github.com/PowerShell/Win32-OpenSSH/releases)

[<span data-ttu-id="a481b-171">installazione</span><span class="sxs-lookup"><span data-stu-id="a481b-171">installation</span></span>](https://github.com/PowerShell/Win32-OpenSSH/wiki/Install-Win32-OpenSSH)

[<span data-ttu-id="a481b-172">SSH per Ubuntu</span><span class="sxs-lookup"><span data-stu-id="a481b-172">Ubuntu SSH</span></span>](https://help.ubuntu.com/lts/serverguide/openssh-server.html)