---
title: Installazione di PowerShell Core in Windows
description: Informazioni sull'installazione di PowerShell Core in Windows
ms.date: 08/06/2018
ms.openlocfilehash: ba159a69df7e117e90e21dd26228b61146260475
ms.sourcegitcommit: 221b7daab7f597f8b2e4864cf9b5d9dda9b9879b
ms.translationtype: MTE95
ms.contentlocale: it-IT
ms.lasthandoff: 11/27/2018
ms.locfileid: "52320892"
---
# <a name="installing-powershell-core-on-windows"></a>Installazione di PowerShell Core in Windows

## <a name="msi"></a>MSI

Per installare PowerShell in un client Windows o Windows Server (funziona in Windows 7 SP1, Server 2008 R2 e versioni successive), scaricare il pacchetto MSI dalla pagina delle [versioni][] di GitHub.

Il file MSI è simile al seguente `PowerShell-<version>-win-<os-arch>.msi`
<!-- TODO: should be updated to point to the Download Center as well -->

Dopo averlo scaricato, fare doppio clic sul programma di installazione e seguire i prompt.

Nel menu Start dell'installazione è disponibile un collegamento.

- Per impostazione predefinita, il pacchetto viene installato in `$env:ProgramFiles\PowerShell\<version>`
- È possibile avviare PowerShell tramite il menu Start o `$env:ProgramFiles\PowerShell\<version>\pwsh.exe`

### <a name="prerequisites"></a>Prerequisiti

Per abilitare la comunicazione remota di PowerShell tramite WS-Management, è necessario soddisfare i prerequisiti seguenti:

- Installare [Universal C Runtime](https://www.microsoft.com/download/details.aspx?id=50410) nelle versioni di Windows precedenti a Windows 10.
  È disponibile tramite download diretto o Windows Update.
  Nei sistemi supportati, in cui sono state applicate tutte le patch (inclusi i pacchetti facoltativi), è già installato.
- Installare Windows Management Framework (WMF) 4.0 o versione successiva in Windows 7 e Windows Server 2008 R2.

## <a name="zip"></a>ZIP

Sono disponibili archivi ZIP di file binari di PowerShell per abilitare scenari di distribuzione avanzati.
Si noti che quando si usa l'archivio ZIP, non viene eseguito il controllo dei prerequisiti come nel pacchetto MSI.
Perché la comunicazione remota tramite WS-Management funzioni correttamente in versioni di Windows precedenti a Windows 10, è necessario assicurarsi che i [prerequisiti](#prerequisites) siano soddisfatti.

## <a name="deploying-on-windows-iot"></a>Distribuzione in Windows IoT

Windows IoT include già Windows PowerShell, che verrà usato per distribuire PowerShell Core 6.

1. Creare `PSSession` per il dispositivo di destinazione

   ```powershell
   $s = New-PSSession -ComputerName <deviceIp> -Credential Administrator
   ```

2. Copiare il pacchetto ZIP nel dispositivo

   ```powershell
   # change the destination to however you had partitioned it with sufficient
   # space for the zip and the unzipped contents
   # the path should be local to the device
   Copy-Item .\PowerShell-6.1.0-win-arm32.zip -Destination u:\users\administrator\Downloads -ToSession $s
   ```

3. Connettersi al dispositivo ed espandere l'archivio

   ```powershell
   Enter-PSSession $s
   Set-Location u:\users\administrator\downloads
   Expand-Archive .\PowerShell-6.1.0-win-arm32.zip
   ```

4. Configurare la comunicazione remota con PowerShell Core 6

   ```powershell
   Set-Location .\PowerShell-6.1.0-win-arm32
   # Be sure to use the -PowerShellHome parameter otherwise it'll try to create a new
   # endpoint with Windows PowerShell 5.1
   .\Install-PowerShellRemoting.ps1 -PowerShellHome .
   # You'll get an error message and will be disconnected from the device because it has to restart WinRM
   ```

5. Connettersi all'endpoint di PowerShell Core 6 nel dispositivo

   ```powershell
   # Be sure to use the -Configuration parameter.  If you omit it, you will connect to Windows PowerShell 5.1
   Enter-PSSession -ComputerName <deviceIp> -Credential Administrator -Configuration powershell.6.1.0
   ```

## <a name="deploying-on-nano-server"></a>Distribuzione in Nano Server

Queste istruzioni presuppongono che una versione di PowerShell sia già in esecuzione nell'immagine Nano Server e che sia stato generato da [Nano Server Image Builder](/windows-server/get-started/deploy-nano-server).
Nano Server è un sistema operativo "headless". È possibile distribuire i file binari di PowerShell Core usando due metodi diversi.

1. Offline: montare il disco rigido virtuale di Nano Server e decomprimere il contenuto del file ZIP nella posizione prescelta all'interno dell'immagine montata.
2. Online: trasferire il file ZIP in una sessione di PowerShell e decomprimerlo nella posizione prescelta.

In entrambi i casi è necessario usare il pacchetto ZIP della versione x64 di Windows 10 ed eseguire i comandi all'interno di un'istanza di PowerShell come "amministratore".

### <a name="offline-deployment-of-powershell-core"></a>Distribuzione offline di PowerShell Core

1. Usare l'utilità ZIP preferita per decomprimere il pacchetto in una directory all'interno dell'immagine montata di Nano Server.
2. Smontare l'immagine e riavviarla.
3. Connettersi all'istanza di Posta in arrivo di Windows PowerShell.
4. Seguire le istruzioni per creare un endpoint di comunicazione remota usando un'[altra tecnica di istanza](../core-powershell/wsman-remoting-in-powershell-core.md#executed-by-another-instance-of-powershell-on-behalf-of-the-instance-that-it-will-register).

### <a name="online-deployment-of-powershell-core"></a>Distribuzione online di PowerShell Core

La procedura seguente consente di eseguire la distribuzione di PowerShell Core in un'istanza in esecuzione di Nano Server e di configurarne l'endpoint remoto.

- Connettersi all'istanza di Posta in arrivo di Windows PowerShell

  ```powershell
  $session = New-PSSession -ComputerName <Nano Server IP address> -Credential <An Administrator account on the system>
  ```

- Copiare il file nell'istanza di Nano Server

  ```powershell
  Copy-Item <local PS Core download location>\powershell-<version>-win-x64.zip c:\ -ToSession $session
  ```

- Immettere la sessione

  ```powershell
  Enter-PSSession $session
  ```

- Estrarre il file ZIP

  ```powershell
  # Insert the appropriate version.
  Expand-Archive -Path C:\powershell-<version>-win-x64.zip -DestinationPath "C:\PowerShellCore_<version>"
  ```

- Perché la comunicazione remota si basi su WS-Management, seguire le istruzioni seguenti per creare un endpoint di comunicazione remota tramite un'[altra tecnica di istanza](../core-powershell/WSMan-Remoting-in-PowerShell-Core.md#executed-by-another-instance-of-powershell-on-behalf-of-the-instance-that-it-will-register).

## <a name="instructions-to-create-a-remoting-endpoint"></a>Istruzioni per creare un endpoint di comunicazione remota

PowerShell Core supporta il protocollo di comunicazione remota di PowerShell (PSRP) tramite WS-Management e SSH.
Per altre informazioni, vedere:

- [SSH Remoting in PowerShell Core][ssh-remoting] (Comunicazione remota SSH in PowerShell Core)
- [WSMan Remoting in PowerShell Core][wsman-remoting] (Comunicazione remota WS-Management in PowerShell Core)

## <a name="artifact-installation-instructions"></a>Istruzioni di installazione dell'artefatto

Un archivio con i bit di CoreCL viene pubblicato per ogni build CI tramite [AppVeyor][].

Per installare PowerShell Core dall'artefatto CoreCLR:

1. Scaricare il pacchetto ZIP dalla scheda **artifacts** (artefatti) della build specifica.
2. Sbloccare il file ZIP: fare clic con il pulsante destro del mouse in Esplora file -> Proprietà -> selezionare la casella "Sblocca" -> applicare
3. Estrarre il file ZIP nella directory `bin`
4. `./bin/pwsh.exe`

<!-- [download-center]: TODO -->

[versioni]: https://github.com/PowerShell/PowerShell/releases
[ssh-remoting]: ../core-powershell/SSH-Remoting-in-PowerShell-Core.md
[wsman-remoting]: ../core-powershell/WSMan-Remoting-in-PowerShell-Core.md
[AppVeyor]: https://ci.appveyor.com/project/PowerShell/powershell
