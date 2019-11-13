---
title: Comunicazione remota di PowerShell su SSH
description: Comunicazione remota in PowerShell Core tramite SSH
ms.date: 09/30/2019
ms.openlocfilehash: 0f2fb13010d62dec5b19b373a24a199bff22665d
ms.sourcegitcommit: 36e4c79afda2ce11febd93951e143687245f0b50
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 11/02/2019
ms.locfileid: "73444369"
---
# <a name="powershell-remoting-over-ssh"></a>Comunicazione remota di PowerShell su SSH

## <a name="overview"></a>Panoramica

La comunicazione remota di PowerShell solitamente usa WinRM per la negoziazione di connessione e il trasporto dei dati. SSH è ora disponibile per le piattaforme Linux e Windows e permette a PowerShell di offrire un'autentica comunicazione remota multipiattaforma.

WinRM offre un solido modello di hosting per sessioni remote di PowerShell. La comunicazione remota basata su SSH attualmente non supporta la configurazione di endpoint remoti e JEA (Just Enough Administration).

La comunicazione remota SSH permette la comunicazione remota di base di sessioni di PowerShell tra computer Windows e Linux. La comunicazione remota SSH crea un processo host di PowerShell nel computer di destinazione come sottosistema SSH. In futuro verrà implementato un modello di hosting generale, simile a WinRM, per supportare la configurazione degli endpoint e JEA.

I cmdlet `New-PSSession`, `Enter-PSSession` e `Invoke-Command` includono ora un nuovo set di parametri per supportare questa nuova connessione di comunicazione remota.

```
[-HostName <string>]  [-UserName <string>]  [-KeyFilePath <string>]
```

Per creare una sessione remota, è necessario specificare il computer di destinazione con il parametro `HostName` e il nome utente con il parametro `UserName`. Quando si eseguono i cmdlet in modo interattivo, viene chiesto di immettere una password. È anche possibile usare l'autenticazione con chiave SSH tramite un file di chiave privata con il parametro `KeyFilePath`.

## <a name="general-setup-information"></a>Informazioni generali di installazione

PowerShell 6 o versione successiva e SSH devono essere installati in tutti i computer. Installare sia il client SSH (`ssh.exe`) sia il server (`sshd.exe`) per rendere possibile la comunicazione remota tra i computer. OpenSSH per Windows è ora disponibile in Windows 10 build 1809 e Windows Server 2019. Per altre informazioni, vedere [Gestire Windows con OpenSSH](/windows-server/administration/openssh/openssh_overview). Per Linux, installare SSH (incluso il server sshd) nel modo appropriato per la piattaforma in uso. È necessario installare anche PowerShell da GitHub per ottenere la funzionalità di comunicazione remota SSH. Il server SSH deve essere configurato per creare un sottosistema SSH in modo da ospitare un processo PowerShell nel computer remoto. È anche necessario abilitare l'autenticazione basata su **password** o **chiave**.

## <a name="set-up-on-a-windows-computer"></a>Eseguire la configurazione in un computer Windows

1. Installare la versione più recente di PowerShell (vedere [Installazione di PowerShell Core in Windows](../../install/installing-powershell-core-on-windows.md#msi)).

   È possibile verificare che PowerShell includa il supporto per la comunicazione remota SSH elencando i set di parametri `New-PSSession`. Si noterà che sono presenti nomi di set di parametri che iniziano con **SSH**. Questi set di parametri includono i parametri **SSH**.

   ```powershell
   (Get-Command New-PSSession).ParameterSets.Name
   ```

   ```Output
   Name
   ----
   SSHHost
   SSHHostHashParam
   ```

1. Installare la versione più recente di OpenSSH Win32. Per le istruzioni di installazione, vedere [Introduzione a OpenSSH](/windows-server/administration/openssh/openssh_install_firstuse).

   > [!NOTE]
   > Se si vuole impostare PowerShell come shell predefinita per OpenSSH, vedere [Configurazione di Windows per OpenSSH](/windows-server/administration/openssh/openssh_server_configuration).

1. Modificare il file `sshd_config` in `$env:ProgramData\ssh`.

   Assicurarsi che l'autenticazione della password sia abilitata:

   ```
   PasswordAuthentication yes
   ```

   Creare il sottosistema SSH che ospita un processo di PowerShell nel computer remoto:

   ```
   Subsystem powershell c:/progra~1/powershell/6/pwsh.exe -sshs -NoLogo -NoProfile
   ```

   > [!NOTE]
   > È necessario usare il nome breve 8.3 per tutti i percorsi di file che contengono spazi. È presente un bug in OpenSSH per Windows che impedisce il funzionamento dei percorsi eseguibili nel sottosistema che contengono spazi. Per altre informazioni, vedere [questo problema in GitHub](https://github.com/PowerShell/Win32-OpenSSH/issues/784).
   >
   > Il nome breve 8.3 per la cartella `Program Files` in Windows è in genere `Progra~1`. È comunque possibile usare il comando seguente per controllare:
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

   Facoltativamente è possibile abilitare l'autenticazione della chiave:

   ```
   PubkeyAuthentication yes
   ```

   Per altre informazioni, vedere [Gestione delle chiavi OpenSSH](/windows-server/administration/openssh/openssh_keymanagement).

1. Riavviare il servizio **sshd**.

   ```powershell
   Restart-Service sshd
   ```

1. Aggiungere il percorso in cui è installato OpenSSH alla variabile di ambiente Path. Ad esempio, `C:\Program Files\OpenSSH\` Questa voce permette di trovare `ssh.exe`.

## <a name="set-up-on-an-ubuntu-1604-linux-computer"></a>Eseguire la configurazione in un computer Linux Ubuntu 16.04

1. Installare la versione più recente di PowerShell (vedere [Installazione di PowerShell Core in Linux](../../install/installing-powershell-core-on-linux.md#ubuntu-1604)).
1. Installare [Ubuntu OpenSSH Server](https://help.ubuntu.com/lts/serverguide/openssh-server.html).

   ```bash
   sudo apt install openssh-client
   sudo apt install openssh-server
   ```

1. Modificare il file `sshd_config` nel percorso `/etc/ssh`.

   Assicurarsi che l'autenticazione della password sia abilitata:

   ```
   PasswordAuthentication yes
   ```

   Aggiungere una voce del sottosistema PowerShell:

   ```
   Subsystem powershell /usr/bin/pwsh -sshs -NoLogo -NoProfile
   ```

   Facoltativamente è possibile abilitare l'autenticazione della chiave:

   ```
   PubkeyAuthentication yes
   ```

1. Riavviare il servizio **sshd**.

   ```bash
   sudo service sshd restart
   ```

## <a name="set-up-on-a-macos-computer"></a>Eseguire la configurazione in un computer macOS

1. Installare la versione più recente di PowerShell (vedere [Installazione di PowerShell Core in macOS](../../install/installing-powershell-core-on-macos.md)).

   Assicurarsi che la comunicazione remota SSH sia abilitata attenendosi alla procedura seguente:

   1. Aprire `System Preferences`.
   1. Fare clic su `Sharing`.
   1. Selezionare `Remote Login` per impostare `Remote Login: On`.
   1. Consentire l'accesso agli utenti appropriati.

1. Modificare il file `sshd_config` nel percorso `/private/etc/ssh/sshd_config`.

   Aprire un editor di testo, come **nano**:

   ```bash
   sudo nano /private/etc/ssh/sshd_config
   ```

   Assicurarsi che l'autenticazione della password sia abilitata:

   ```
   PasswordAuthentication yes
   ```

   Aggiungere una voce del sottosistema PowerShell:

   ```
   Subsystem powershell /usr/local/bin/pwsh -sshs -NoLogo -NoProfile
   ```

   Facoltativamente è possibile abilitare l'autenticazione della chiave:

   ```
   PubkeyAuthentication yes
   ```

1. Riavviare il servizio **sshd**.

   ```bash
   sudo launchctl stop com.openssh.sshd
   sudo launchctl start com.openssh.sshd
   ```

## <a name="authentication"></a>Autenticazione

La comunicazione remota di PowerShell su SSH si affida allo scambio di autenticazioni tra il clienti SSH e il servizio SSH e non implementa alcuno schema di autenticazione. Ciò significa che tutti gli schemi di autenticazione configurati, tra cui l'autenticazione a più fattori, sono gestiti da SSH e indipendenti da PowerShell. Ad esempio, è possibile configurare il servizio SSH per richiedere l'autenticazione con chiave pubblica e una password monouso per maggiore sicurezza. La configurazione dell'autenticazione a più fattori non rientra nell'ambito di questa documentazione. Fare riferimento alla documentazione per SSH su come configurare l'autenticazione a più fattori in modo corretto e verificare se funziona all'esterno di PowerShell prima di provare a usarlo con la comunicazione remota di PowerShell.

## <a name="powershell-remoting-example"></a>Esempio di comunicazione remota di PowerShell

Il modo più semplice per testare la comunicazione remota è provarla su un singolo computer. In questo esempio verrà creata una sessione remota verso lo stesso computer Linux. Poiché i cmdlet di PowerShell vengono usati in modo interattivo, vengono visualizzati prompt di SSH che chiedono di verificare il computer host e di immettere una password. È possibile eseguire la stessa operazione in un computer Windows per verificare il funzionamento della comunicazione remota. Stabilire quindi la comunicazione remota tra i computer modificando il nome host.

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

### <a name="known-issues"></a>Problemi noti

Il comando **sudo** non funziona in una sessione remota verso un computer Linux.

## <a name="see-also"></a>Vedere anche

[Installazione di PowerShell Core in Linux](../../install/installing-powershell-core-on-linux.md#ubuntu-1604)

[Installazione di PowerShell Core in macOS](../../install/installing-powershell-core-on-macos.md)

[Installazione di PowerShell Core in Windows](../../install/installing-powershell-core-on-windows.md#msi)

[Gestire Windows con OpenSSH](/windows-server/administration/openssh/openssh_overview)

[Gestione delle chiavi OpenSSH](/windows-server/administration/openssh/openssh_keymanagement)

[SSH per Ubuntu](https://help.ubuntu.com/lts/serverguide/openssh-server.html)
