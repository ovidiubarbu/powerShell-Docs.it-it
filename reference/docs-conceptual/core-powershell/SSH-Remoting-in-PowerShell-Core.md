---
title: Comunicazione remota di PowerShell su SSH
description: Comunicazione remota in PowerShell Core tramite SSH
ms.date: 08/06/2018
ms.openlocfilehash: 27a8fc5623796a270a2ea67aa550c9a0998e766b
ms.sourcegitcommit: 01ac77cd0b00e4e5e964504563a9212e8002e5e0
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 08/07/2018
ms.locfileid: "39587500"
---
# <a name="powershell-remoting-over-ssh"></a>Comunicazione remota di PowerShell su SSH

## <a name="overview"></a>Panoramica

La comunicazione remota di PowerShell solitamente usa WinRM per la negoziazione di connessione e il trasporto dei dati. Per questa implementazione di comunicazione remota è stato scelto SSH in quanto è ora disponibile per piattaforme Linux e Windows e consente una vera comunicazione remota multipiattaforma per PowerShell. Tuttavia, WinRM offre anche un solido modello di hosting per le sessioni remote di PowerShell che questa implementazione ancora non offre. Ciò significa che la configurazione di endpoint remoto e il profilo JEA (Just Enough Administration) di PowerShell non sono ancora supportati in questa implementazione.

La comunicazione remota SSH per PowerShell consente di eseguire la comunicazione remota di base di sessioni di PowerShell tra computer Windows e Linux. Ciò avviene creando un processo di hosting di PowerShell nel computer di destinazione come sottosistema SSH. Infine il processo verrà modificato in un modello di hosting più generale simile al funzionamento di WinRM per supportare la configurazione dell'endpoint e del profilo JEA.

I cmdlet `New-PSSession`, `Enter-PSSession` e `Invoke-Command` hanno ora un nuovo set di parametri per semplificare la nuova connessione di comunicazione remota

```
[-HostName <string>]  [-UserName <string>]  [-KeyFilePath <string>]
```

Questo nuovo set di parametri verrà probabilmente modificato, ma per ora consente di creare sessioni Pssession di SSH con cui è possibile interagire dalla riga di comando o da cui è possibile richiamare comandi e script. È necessario specificare il computer di destinazione con il parametro HostName e il nome utente con il parametro UserName. Quando si eseguono i cmdlet in modo interattivo dalla riga di comando di PowerShell verrà richiesto di immettere una password. Ma è anche possibile usare l'autenticazione con chiave SSH e specificare un percorso di file di chiave privata con il parametro KeyFilePath.

## <a name="general-setup-information"></a>Informazioni generali di installazione

SSH deve essere installato in tutti i computer. È necessario installare sia il client (`ssh.exe`) che il server (`sshd.exe`) in modo da poter provare la comunicazione remota da e verso i computer. Per Windows è necessario installare [OpenSSH - Win32 da GitHub](https://github.com/PowerShell/Win32-OpenSSH/releases).
Per Linux è necessario installare SSH, incluso il server sshd, appropriato per la piattaforma in uso. Sono necessari anche una build o un pacchetto di PowerShell recenti da GitHub con la funzionalità di comunicazione remota SSH.
I sottosistemi SSH vengono usati per stabilire un processo PowerShell nel computer remoto quindi il server SSH dovrà essere configurato a tale scopo. È anche necessario abilitare l'autenticazione della password e, facoltativamente, l'autenticazione basata su chiavi.

## <a name="setup-on-windows-machine"></a>Installazione in computer Windows

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
     Subsystem    powershell c:/program files/powershell/6.0.0/pwsh.exe -sshs -NoLogo -NoProfile
     ```

     > [!NOTE]
     > È presente un bug in OpenSSH per Windows che impedisce il funzionamento dei percorsi eseguibili nel sottosistema che contengono spazi.
     > Per ottenere altre informazioni, vedere [questo problema in GitHub](https://github.com/PowerShell/Win32-OpenSSH/issues/784).

     Una soluzione consiste nel creare un collegamento simbolico alla directory di installazione di Powershell che non contenga spazi:

     ```powershell
     mklink /D c:\pwsh "C:\Program Files\PowerShell\6.0.0"
     ```

     e quindi immetterlo nel sottosistema:

     ```
     Subsystem    powershell c:\pwsh\pwsh.exe -sshs -NoLogo -NoProfile
     ```

     ```
     Subsystem    powershell c:/program files/powershell/6.0.0/pwsh.exe -sshs -NoLogo -NoProfile
     ```

   - Facoltativamente è possibile abilitare l'autenticazione della chiave

     ```
     PubkeyAuthentication yes
     ```

4. Riavviare il servizio sshd

   ```powershell
   Restart-Service sshd
   ```

5. Aggiungere il percorso in cui è installato OpenSSH alla variabile di percorso Env

   - Dovrebbe trovarsi nelle righe di `C:\Program Files\OpenSSH\`
   - In questo modo ssh.exe può essere individuato

## <a name="setup-on-linux-ubuntu-1404-machine"></a>Installazione in computer Linux (Ubuntu 14.04)

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

## <a name="setup-on-macos-machine"></a>Installazione in computer MacOS

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

Il modo più semplice per testare la comunicazione remota è semplicemente provarla su un singolo computer. Qui verrà creata una sessione remota verso lo stesso computer in Linux. Si noti che vengono usati i cmdlet di PowerShell da un prompt dei comandi in modo che siano visibili i prompt di SSH che chiedono di verificare il computer host, nonché le richieste di password. È possibile eseguire la stessa operazione in un computer Windows per assicurarsi che la comunicazione remota funzioni e quindi eseguirla tra i computer cambiando semplicemente il nome host.

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

### <a name="known-issues"></a>Problemi noti

Il comando sudo non funziona nella sessione remota per computer Linux.

## <a name="see-also"></a>Vedere anche

[PowerShell Core per Windows](../setup/installing-powershell-core-on-windows.md#msi)

[PowerShell Core per Linux](../setup/installing-powershell-core-on-linux.md#ubuntu-1404)

[PowerShell Core per MacOS](../setup/installing-powershell-core-on-macos.md)

[OpenSSH - Win32](https://github.com/PowerShell/Win32-OpenSSH/releases)

[installazione](https://github.com/PowerShell/Win32-OpenSSH/wiki/Install-Win32-OpenSSH)

[SSH per Ubuntu](https://help.ubuntu.com/lts/serverguide/openssh-server.html)