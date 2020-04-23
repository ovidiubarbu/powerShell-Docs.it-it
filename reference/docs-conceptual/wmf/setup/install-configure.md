---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: wmf,powershell,installazione
contributor: keithb
title: Installare e configurare WMF 5.1
ms.openlocfilehash: 241f52be011e1afc87d25c9a934db0c1e0361b76
ms.sourcegitcommit: 6545c60578f7745be015111052fd7769f8289296
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/22/2020
ms.locfileid: "79402368"
---
# <a name="install-and-configure-wmf-51"></a>Installare e configurare WMF 5.1

> [!IMPORTANT]
> WMF 5.0 è stato sostituito da WMF 5.1. Gli utenti con WMF 5.0 devono eseguire l'aggiornamento a WMF 5.1 per ricevere supporto.
> **WMF 5.1 richiede .NET Framework 4.5.2** (o versione successiva). Se .NET 4.5.2 (o versione successiva) non è disponibile, WMF verrà installato correttamente, ma le funzionalità principali non verranno eseguite.

## <a name="download-and-install-the-wmf-51-package"></a>Scaricare e installare il pacchetto WMF 5.1

Scaricare il pacchetto WMF 5.1 per il sistema operativo e l'architettura in cui si vuole eseguire l'installazione:

| Sistema operativo       | Prerequisiti           | Collegamenti al pacchetto                          |
|------------------------|-------------------------|----------------------------------------|
| Windows Server 2012 R2 |                         | [Win8.1AndW2K12R2-KB3191564-x64.msu][] |
| Windows Server 2012    |                         | [W2K12-KB3191565-x64.msu][]            |
| Windows Server 2008 R2 | [.NET Framework 4.5.2][]| [Win7AndW2K8R2-KB3191566-x64.ZIP][]    |
| Windows 8.1            |                         | **x64:** [Win8.1AndW2K12R2-KB3191564-x64.msu][]</br>**x86:** [Win8.1-KB3191564-x86.msu][] |
| Windows 7 SP1          | [.NET Framework 4.5.2][]| **x64:** [Win7AndW2K8R2-KB3191566-x64.ZIP][]</br>**x86:** [Win7-KB3191566-x86.ZIP][] |

[.NET Framework 4.5.2]: https://www.microsoft.com/download/details.aspx?id=42642
[W2K12-KB3191565-x64.msu]: https://go.microsoft.com/fwlink/?linkid=839513
[Win7-KB3191566-x86.ZIP]: https://go.microsoft.com/fwlink/?linkid=839522
[Win7AndW2K8R2-KB3191566-x64.ZIP]: https://go.microsoft.com/fwlink/?linkid=839523
[Win8.1-KB3191564-x86.msu]: https://go.microsoft.com/fwlink/?linkid=839521
[Win8.1AndW2K12R2-KB3191564-x64.msu]: https://go.microsoft.com/fwlink/?linkid=839516

- WMF 5.1 deve essere disinstallato prima dell'installazione WMF 5.1 RTM.
- È possibile installare WMF 5.1 direttamente su WMF 5.0 o WMF 4.0.
- **Non è necessario** installare WMF 4.0 prima di installare WMF 5.1 in Windows 7 e Windows Server 2008 R2.

## <a name="install-wmf-51-for-windows-server-2008-r2-and-windows-7"></a>Installare WMF 5.1 per Windows Server 2008 R2 e Windows 7

> [!NOTE]
> Le istruzioni di installazione per Windows Server 2008 R2 e Windows 7 sono cambiate e sono diverse dalle istruzioni per gli altri pacchetti. Le istruzioni di installazione per Windows Server 2012 R2, Windows Server 2012 e Windows 8.1 sono riportate di seguito.

### <a name="wmf-51-prerequisites-for-windows-server-2008-r2-sp1-and-windows-7-sp1"></a>Prerequisiti di WMF 5.1 per Windows Server 2008 R2 SP1 e Windows 7 SP1

Per l'installazione di WMF 5.1 in Windows Server 2008 R2 SP1 o Windows 7 SP1 esistono i prerequisiti seguenti:

- Installazione del Service Pack più recente.
- WMF 3.0 **non deve** essere installato. L'installazione di WMF 5.1 su WMF 3.0 causerà la perdita di **PSModulePath** (`$env:PSModulePath`) e ciò può causare errori in altre applicazioni. Prima di installare WMF 5.1, è necessario disinstallare WMF 3.0 o salvare **PSModulePath** e quindi ripristinarlo manualmente al termine dell'installazione di WMF 5.1.
- WMF 5.1 richiede almeno [.NET Framework 4.5.2](https://www.microsoft.com/download/details.aspx?id=42642).
  È possibile installare Microsoft .NET Framework 4.5.2 seguendo le istruzioni disponibili nel percorso di download.

### <a name="installing-wmf-51-on-windows-server-2008-r2-and-windows-7"></a>Installazione di WMF 5.1 in Windows Server 2008 R2 e Windows 7

1. Passare alla cartella in cui è stato scaricato il file ZIP.

2. Fare clic con il pulsante destro del mouse sul file ZIP e scegliere **Estrai tutto**. Il file ZIP contiene due file: un file MSU e il file di script `Install-WMF5.1.ps1`. Dopo aver decompresso il file ZIP, è possibile copiare il contenuto in qualsiasi computer che esegue Windows 7 o Windows Server 2008 R2.

3. Dopo aver estratto il contenuto del file ZIP, aprire PowerShell come amministratore e quindi passare alla cartella con il contenuto del file ZIP.

4. Eseguire lo script `Install-WMF5.1.ps1` in tale cartella e seguire le istruzioni. Questo script verifica i prerequisiti nel computer locale e installa WMF 5.1 se i prerequisiti sono soddisfatti. I prerequisiti sono elencati di seguito.

   `Install-WMF5.1.ps1` accetta i parametri seguenti per semplificare l'automazione dell'installazione in Windows Server 2008 R2 e Windows 7:

   - **AcceptEula**: Se si include questo parametro, il contratto di licenza con l'utente finale viene accettato automaticamente e non verrà visualizzato.
   - **AllowRestart**: Questo parametro può essere usato solo se si specifica AcceptEula. Se si include questo parametro ed è necessario un riavvio dopo l'installazione di WMF 5.1, il riavvio verrà eseguito senza chiedere conferma subito dopo il completamento dell'installazione.

## <a name="winrm-dependency"></a>Dipendenza da WinRM

Desired State Configuration (DSC) in Windows PowerShell dipende da WinRM. WinRM non è abilitato per impostazione predefinita in Windows Server 2008 R2 e Windows 7. Per abilitare WinRM, eseguire `Set-WSManQuickConfig` in una sessione di Windows PowerShell con privilegi elevati.

## <a name="install-wmf-51-for-windows-server-2012-r2-windows-server-2012-and-windows-81"></a>Installare WMF 5.1 per Windows Server 2012 R2, Windows Server 2012 e Windows 8.1

### <a name="install-from-windows-file-explorer"></a>Installazione da Esplora file

1. Passare alla cartella in cui è stato scaricato il file MSU.
2. Fare doppio clic sul file MSU per eseguirlo.

### <a name="installing-from-the-command-prompt"></a>Installazione dal prompt dei comandi

1. Dopo aver scaricato il pacchetto corretto per l'architettura del computer, aprire una finestra del prompt dei comandi con diritti utente elevati (Esegui come amministratore). Con le opzioni di installazione dei componenti di base di Windows Server 2012 R2, Windows Server 2012 o Windows Server 2008 R2 SP1, il prompt dei comandi viene aperto con diritti utente elevati per impostazione predefinita.
2. Passare alla cartella in cui è stato scaricato o copiato il pacchetto di installazione di WMF 5.1.
3. Eseguire uno dei comandi seguenti:
   - Nei computer che eseguono Windows Server 2012 R2 o Windows 8.1 x64 eseguire `Win8.1AndW2K12R2-KB3191564-x64.msu /quiet`.
   - Nei computer che eseguono Windows Server 2012 eseguire `W2K12-KB3191565-x64.msu /quiet`.
   - Nei computer che eseguono Windows 8.1 x86 eseguire `Win8.1-KB3191564-x86.msu /quiet`.

> [!NOTE]
> L'installazione di WMF 5.1 richiede un riavvio. Se si usa l'opzione `/quiet`, il sistema verrà riavviato senza alcun avviso. Usare l'opzione `/norestart` per evitare il riavvio. WMF 5.1 non verrà tuttavia installato fino a quando non si riavvia il sistema.
