---
title: Comunicazione remota di PowerShell su SSH
description: Comunicazione remota in PowerShell Core tramite SSH
ms.date: 08/14/2018
ms.openlocfilehash: 1de034d667aa9a377e5460e7eb474402c690cb42
ms.sourcegitcommit: 56b9be8503a5a1342c0b85b36f5ba6f57c281b63
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 08/21/2018
ms.locfileid: "43133104"
---
# <a name="powershell-remoting-over-ssh"></a>Comunicazione remota di PowerShell su SSH

## <a name="overview"></a>Panoramica

La comunicazione remota di PowerShell solitamente usa WinRM per la negoziazione di connessione e il trasporto dei dati. SSH è ora disponibile per le piattaforme Linux e Windows e permette a PowerShell di offrire un'autentica comunicazione remota multipiattaforma.

WinRM offre un solido modello di hosting per sessioni remote di PowerShell. Questa implementazione di comunicazione remota basata su SSH attualmente non supporta la configurazione di endpoint remoti e JEA (Just Enough Administration).

La comunicazione remota SSH permette la comunicazione remota di base di sessioni di PowerShell tra computer Windows e Linux. La comunicazione remota SSH crea un processo host di PowerShell nel computer di destinazione come sottosistema SSH.
In futuro verrà implementato un modello di hosting generale, simile a WinRM, per supportare la configurazione degli endpoint e JEA.

I cmdlet `New-PSSession`, `Enter-PSSession` e `Invoke-Command` includono ora un nuovo set di parametri per supportare questa nuova connessione di comunicazione remota.

```
[-HostName <string>]  [-UserName <string>]  [-KeyFilePath <string>]
```

Per creare una sessione remota, è necessario specificare il computer di destinazione con il parametro `HostName` e il nome utente con il parametro `UserName`. Quando si eseguono i cmdlet in modo interattivo, viene chiesto di immettere una password. È anche possibile usare l'autenticazione con chiave SSH tramite un file di chiave privata con il parametro `KeyFilePath`.

## <a name="general-setup-information"></a>Informazioni generali di installazione

SSH deve essere installato in tutti i computer. Installare sia il client SSH (`ssh.exe`) sia il server (`sshd.exe`) in modo da poter comunicare in remoto da e verso i computer. Per Windows, installare [Win32-OpenSSH da GitHub](https://github.com/PowerShell/Win32-OpenSSH/releases).
Per Linux, installare SSH (incluso il server sshd) nel modo appropriato per la piattaforma in uso. È necessario installare anche PowerShell Core da GitHub per ottenere la funzionalità di comunicazione remota SSH. Il server SSH deve essere configurato per creare un sottosistema SSH in modo da ospitare un processo PowerShell nel computer remoto. È anche necessario configurare l'autenticazione basata su password o su chiave.

## <a name="set-up-on-windows-machine"></a>Installazione in computer Windows

1. Installare la versione più recente di [PowerShell Core per Windows]

   - È possibile stabilire se la comunicazione remota SSH è supportata esaminando i set di parametri per `New-PSSession`

   ```powershell
   Get-Command New-PSSession -syntax
   ```

   ```output
   New-PSSession [-HostName] <string[]> [-Name <string[]>] [-UserName <string>] [-KeyFilePath <string>] [-SSHTransport] [<CommonParameters>]
   ```

2. Installare la build più recente di [OpenSSH - Win32] da GitHub usando le istruzioni di [installazione]
3. Modificare il file sshd_config nel percorso in cui è installato OpenSSH - Win32

   - Verificare che l'autenticazione della password sia abilitata

     ```
     PasswordAuthentication yes
     ```

     ```
     Subsystem    powershell c:/program files/powershell/6.0.4/pwsh.exe -sshs -NoLogo -NoProfile
     ```

     > [!NOTE]
     > È presente un bug in OpenSSH per Windows che impedisce il funzionamento dei percorsi eseguibili nel sottosistema che contengono spazi. Per altre informazioni, vedere [questo problema in GitHub](https://github.com/PowerShell/Win32-OpenSSH/issues/784).

     Una soluzione consiste nel creare un collegamento simbolico alla directory di installazione di PowerShell senza spazi:

     ```powershell
     mklink /D c:\pwsh "C:\Program Files\PowerShell\6.0.4"
     ```

     e quindi immetterlo nel sottosistema:

     ```
     Subsystem    powershell c:\pwsh\pwsh.exe -sshs -NoLogo -NoProfile
     ```

   - Facoltativamente è possibile abilitare l'autenticazione della chiave

     ```
     PubkeyAuthentication yes
     ```

4. Riavviare il servizio sshd

   ```powershell
   Restart-Service sshd
   ```

5. Aggiungere il percorso in cui è installato OpenSSH alla variabile di ambiente Path. Ad esempio, `C:\Program Files\OpenSSH\` Questa voce permette di trovare ssh.exe.

## <a name="set-up-on-linux-ubuntu-1404-machine"></a>Installazione in computer Linux (Ubuntu 14.04)

1. Installare la build più recente di [PowerShell Core per Linux] da GitHub
2. Installare [SSH per Ubuntu] in base alle esigenze

   ```bash
   sudo apt install openssh-client
   sudo apt install openssh-server
   ```

3. Modificare il file sshd_config nel percorso /etc/ssh

   - Verificare che l'autenticazione della password sia abilitata

   ```
   PasswordAuthentication yes
   ```

   - Aggiungere una voce del sottosistema PowerShell

   ```
   Subsystem powershell /usr/bin/pwsh -sshs -NoLogo -NoProfile
   ```

   - Facoltativamente è possibile abilitare l'autenticazione della chiave

   ```
   PubkeyAuthentication yes
   ```

4. Riavviare il servizio sshd

   ```bash
   sudo service sshd restart
   ```

## <a name="set-up-on-macos-machine"></a>Installazione in computer MacOS

1. Installare la build più recente di [PowerShell Core per MacOS]

   - Assicurarsi che la comunicazione remota SSH sia abilitata attenendosi alla procedura seguente:
     - Aprire `System Preferences`
     - Fare clic su `Sharing`
     - Controllare `Remote Login`: deve indicare `Remote Login: On`
     - Consentire l'accesso agli utenti appropriati

2. Modificare il file `sshd_config` nel percorso `/private/etc/ssh/sshd_config`

   - Usare l'editor preferito o

     ```bash
     sudo nano /private/etc/ssh/sshd_config
     ```

   - Verificare che l'autenticazione della password sia abilitata

     ```
     PasswordAuthentication yes
     ```

   - Aggiungere una voce del sottosistema PowerShell

     ```
     Subsystem powershell /usr/local/bin/pwsh -sshs -NoLogo -NoProfile
     ```

   - Facoltativamente è possibile abilitare l'autenticazione della chiave

     ```
     PubkeyAuthentication yes
     ```

3. Riavviare il servizio sshd

   ```bash
   sudo launchctl stop com.openssh.sshd
   sudo launchctl start com.openssh.sshd
   ```

## <a name="powershell-remoting-example"></a>Esempio di comunicazione remota di PowerShell

Il modo più semplice per testare la comunicazione remota è provarla su un singolo computer. In questo esempio verrà creata una sessione remota verso lo stesso computer Linux. Poiché i cmdlet di PowerShell vengono usati in modo interattivo, vengono visualizzati prompt di SSH che chiedono di verificare il computer host e di immettere una password. È possibile eseguire la stessa operazione in un computer Windows per verificare il funzionamento della comunicazione remota. Stabilire quindi una comunicazione remota tra i computer modificando il nome host.

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

### <a name="known-issues"></a>Problemi noti

Il comando sudo non funziona in una sessione remota verso computer Linux.

## <a name="see-also"></a>Vedere anche

[PowerShell Core per Windows](../setup/installing-powershell-core-on-windows.md#msi)

[PowerShell Core per Linux](../setup/installing-powershell-core-on-linux.md#ubuntu-1404)

[PowerShell Core per MacOS](../setup/installing-powershell-core-on-macos.md)

[OpenSSH - Win32](https://github.com/PowerShell/Win32-OpenSSH/releases)

[installazione](https://github.com/PowerShell/Win32-OpenSSH/wiki/Install-Win32-OpenSSH)

[SSH per Ubuntu](https://help.ubuntu.com/lts/serverguide/openssh-server.html)
