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
# <a name="installing-powershell-on-windows"></a>Installazione di PowerShell in Windows

Esistono diversi modi per installare PowerShell in Windows.

## <a name="prerequisites"></a>Prerequisiti

Per abilitare la comunicazione remota di PowerShell tramite WS-Management, è necessario soddisfare i prerequisiti seguenti:

- Installare [Universal C Runtime](https://www.microsoft.com/download/details.aspx?id=50410) nelle versioni di Windows precedenti a Windows 10. È disponibile tramite download diretto o Windows Update. Nei sistemi supportati, in cui sono state applicate tutte le patch (inclusi i pacchetti facoltativi), è già installato.
- Installare Windows Management Framework (WMF) 4.0 o versione successiva in Windows 7 e Windows Server 2008 R2. Per altre informazioni su WMF, vedere la [panoramica su Windows Management Framework](/powershell/scripting/wmf/overview).

## <a name="a-idmsi-installing-the-msi-package"></a><a id="msi" />Installazione del pacchetto MSI

Per installare PowerShell in un client Windows o Windows Server (funziona in Windows 7 SP1, Server 2008 R2 e versioni successive), scaricare il pacchetto MSI dalla pagina delle [versioni][releases] di GitHub. Scorrere verso il basso fino alla sezione **Assets** della versione da installare. È possibile che la sezione Assets sia compressa, quindi potrebbe essere necessario fare clic per espanderla.

Il file MSI è simile al seguente `PowerShell-<version>-win-<os-arch>.msi`

Dopo averlo scaricato, fare doppio clic sul programma di installazione e seguire i prompt.

Il programma di installazione crea un collegamento nel menu Start di Windows.

- Per impostazione predefinita, il pacchetto viene installato in `$env:ProgramFiles\PowerShell\<version>`
- È possibile avviare PowerShell tramite il menu Start o `$env:ProgramFiles\PowerShell\<version>\pwsh.exe`

> [!NOTE]
> PowerShell 7 viene installato in una nuova directory ed eseguito side-by-side con Windows PowerShell 5.1. Per PowerShell Core 6.x, PowerShell 7 è un aggiornamento sul posto che rimuove PowerShell Core 6.x.
>
> - PowerShell 7 è installato in `%programfiles%\PowerShell\7`
> - La cartella `%programfiles%\PowerShell\7` viene aggiunta a `$env:PATH`
> - La cartella `%programfiles%\PowerShell\6` viene eliminata
>
> Se è necessario avere PowerShell 6 insieme a PowerShell 7, reinstallare PowerShell 6 usando il metodo dell'[installazione da ZIP](#zip).

### <a name="administrative-install-from-the-command-line"></a>Installazione amministrativa dalla riga di comando

I pacchetti MSI possono essere installati dalla riga di comando. Ciò consente agli amministratori di distribuire i pacchetti senza interazione con l'utente. Il pacchetto MSI per PowerShell include le proprietà seguenti per controllare le opzioni di installazione:

- **ADD_EXPLORER_CONTEXT_MENU_OPENPOWERSHELL** - Questa proprietà controlla l'opzione per aggiungere la voce **Apri PowerShell** al menu di scelta rapida in Esplora risorse.
- **ENABLE_PSREMOTING** - Questa proprietà controlla l'opzione per l'abilitazione della comunicazione remota di PowerShell durante l'installazione.
- **REGISTER_MANIFEST** - Questa proprietà controlla l'opzione per registrare il manifesto di registrazione degli eventi di Windows.

Gli esempi seguenti illustrano come installare PowerShell in modo invisibile all'utente con tutte le opzioni di installazione abilitate.

```powershell
msiexec.exe /package PowerShell-<version>-win-<os-arch>.msi /quiet ADD_EXPLORER_CONTEXT_MENU_OPENPOWERSHELL=1 ENABLE_PSREMOTING=1 REGISTER_MANIFEST=1
```

Per un elenco completo delle opzioni della riga di comando per Msiexec.exe, vedere [Opzioni della riga di comando](/windows/desktop/Msi/command-line-options).

## <a name="a-idmsix-installing-the-msix-package"></a><a id="msix" />Installazione del pacchetto MSIX

Per installare manualmente il pacchetto MSIX in un client Windows 10, scaricare il pacchetto dalla pagina [releases][releases] di GitHub. Scorrere verso il basso fino alla sezione **Assets** della versione da installare. È possibile che la sezione Assets sia compressa, quindi potrebbe essere necessario fare clic per espanderla.

Il file MSI è simile al seguente - `PowerShell-<version>-win-<os-arch>.msix`

Dopo il download non è sufficiente fare doppio clic sul programma di installazione, perché questo pacchetto richiede l'uso di risorse non virtualizzate.  Per l'installazione è necessario usare il cmdlet `Add-AppxPackage`:

```powershell
Add-AppxPackage PowerShell-<version>-win-<os-arch>.msix
```

## <a name="a-idzip-installing-the-zip-package"></a><a id="zip" />Installazione del pacchetto ZIP

Sono disponibili archivi ZIP di file binari di PowerShell per abilitare scenari di distribuzione avanzati. Si noti che quando si usa l'archivio ZIP, non viene eseguito il controllo dei prerequisiti come nel pacchetto MSI. Per il corretto funzionamento della comunicazione remota su WSMan, verificare che siano soddisfatti i [prerequisiti](#prerequisites).

## <a name="deploying-on-windows-iot"></a>Distribuzione in Windows IoT

Windows IoT include già Windows PowerShell, che può essere usato per distribuire PowerShell 7.

1. Creare `PSSession` per il dispositivo di destinazione

   ```powershell
   $s = New-PSSession -ComputerName <deviceIp> -Credential Administrator
   ```

2. Copiare il pacchetto ZIP nel dispositivo

   ```powershell
   # change the destination to however you had partitioned it with sufficient
   # space for the zip and the unzipped contents
   # the path should be local to the device
   Copy-Item .\PowerShell-<version>-win-<os-arch>.zip -Destination u:\users\administrator\Downloads -ToSession $s
   ```

3. Connettersi al dispositivo ed espandere l'archivio

   ```powershell
   Enter-PSSession $s
   Set-Location u:\users\administrator\downloads
   Expand-Archive .\PowerShell-<version>-win-<os-arch>.zip
   ```

4. Configurare la comunicazione remota con PowerShell 7

   ```powershell
   Set-Location .\PowerShell-<version>-win-<os-arch>
   # Be sure to use the -PowerShellHome parameter otherwise it'll try to create a new
   # endpoint with Windows PowerShell 5.1
   .\Install-PowerShellRemoting.ps1 -PowerShellHome .
   # You'll get an error message and will be disconnected from the device because it has to restart WinRM
   ```

5. Connettersi all'endpoint di PowerShell 7 nel dispositivo

   ```powershell
   # Be sure to use the -Configuration parameter.  If you omit it, you will connect to Windows PowerShell 5.1
   Enter-PSSession -ComputerName <deviceIp> -Credential Administrator -Configuration powershell.<version>
   ```

## <a name="deploying-on-nano-server"></a>Distribuzione in Nano Server

Queste istruzioni presuppongono che una versione di PowerShell sia già in esecuzione nell'immagine Nano Server e che sia stato generato da [Nano Server Image Builder](/windows-server/get-started/deploy-nano-server).
Nano Server è un sistema operativo "headless". È possibile distribuire i file binari di PowerShell usando due metodi diversi.

1. Offline: montare il disco rigido virtuale di Nano Server e decomprimere il contenuto del file ZIP nella posizione prescelta all'interno dell'immagine montata.
2. Online: trasferire il file ZIP in una sessione di PowerShell e decomprimerlo nella posizione prescelta.

In entrambi i casi è necessario usare il pacchetto ZIP della versione x64 di Windows 10 ed eseguire i comandi all'interno di un'istanza di PowerShell come "amministratore".

### <a name="offline-deployment-of-powershell"></a>Distribuzione offline di PowerShell

1. Usare l'utilità ZIP preferita per decomprimere il pacchetto in una directory all'interno dell'immagine montata di Nano Server.
2. Smontare l'immagine e riavviarla.
3. Connettersi all'istanza di Posta in arrivo di Windows PowerShell.
4. Seguire le istruzioni per creare un endpoint di comunicazione remota usando un'[altra tecnica di istanza](../learn/remoting/wsman-remoting-in-powershell-core.md#executed-by-another-instance-of-powershell-on-behalf-of-the-instance-that-it-will-register).

### <a name="online-deployment-of-powershell"></a>Distribuzione online di PowerShell

La procedura seguente consente di eseguire la distribuzione di PowerShell in un'istanza in esecuzione di Nano Server e di configurarne l'endpoint remoto.

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
  Expand-Archive -Path C:\powershell-<version>-win-x64.zip -DestinationPath "C:\PowerShell_<version>"
  ```

- Perché la comunicazione remota si basi su WS-Management, seguire le istruzioni seguenti per creare un endpoint di comunicazione remota tramite un'[altra tecnica di istanza](../learn/remoting/WSMan-Remoting-in-PowerShell-Core.md#executed-by-another-instance-of-powershell-on-behalf-of-the-instance-that-it-will-register).

## <a name="install-as-a-net-global-tool"></a>Installare come strumento globale .NET

Se [.NET Core SDK](/dotnet/core/sdk) è già installato, è facile installare PowerShell come [strumento globale .NET](/dotnet/core/tools/global-tools).

```
dotnet tool install --global PowerShell
```

## <a name="how-to-create-a-remoting-endpoint"></a>Come creare un endpoint di comunicazione remota

PowerShell supporta il protocollo di comunicazione remota di PowerShell (PSRP) tramite WS-Management e SSH. Per altre informazioni, vedere:

- [Comunicazione remota di PowerShell su SSH][ssh-remoting]
- [Comunicazione remota di WS-Management in PowerShell Core][wsman-remoting]

<!-- [download-center]: TODO -->

[releases]: https://github.com/PowerShell/PowerShell/releases
[ssh-remoting]: ../learn/remoting/SSH-Remoting-in-PowerShell-Core.md
[wsman-remoting]: ../learn/remoting/WSMan-Remoting-in-PowerShell-Core.md
[AppVeyor]: https://ci.appveyor.com/project/PowerShell/powershell
