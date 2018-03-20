---
ms.date: 2017-06-12
author: JKeithB
ms.topic: reference
keywords: wmf,powershell,installazione
ms.openlocfilehash: 510e1baa2933932cfd4c3bcb4e0973f3eb8095f3
ms.sourcegitcommit: 99227f62dcf827354770eb2c3e95c5cf6a3118b4
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 03/15/2018
---
# <a name="system-requirements"></a>Requisiti di sistema

- Installare gli ultimi aggiornamenti di Windows prima di installare WMF 5.0 RTM.
- È possibile installare WMF 5.0 RTM solo nei sistemi operativi seguenti:

    | Sistema operativo       | Edizioni         | Prerequisiti        |  Collegamenti al pacchetto |
    |------------------------|--------------|------------------|----------------------| --------------|
    | Windows Server 2012 R2 |  |  | [Win8.1AndW2K12R2-KB3134758-x64.msu](http://go.microsoft.com/fwlink/?LinkId=717507) |
    | Windows Server 2012    |  |  | [W2K12-KB3134759-x64.msu](http://go.microsoft.com/fwlink/?LinkId=717506) |
    | Windows Server 2008 R2 SP1 | Tutti, tranne IA64 | [WMF 4.0](http://www.microsoft.com/en-us/download/details.aspx?id=40855) e [.NET Framework 4.5 o versione successiva](https://msdn.microsoft.com/library/5a4x27ek.aspx) sono installati| [Win7AndW2K8R2-KB3134760-x64.msu](http://go.microsoft.com/fwlink/?LinkId=717504)|
    | Windows 8.1 | Pro, Enterprise | | **x64:**  [Win8.1AndW2K12R2-KB3134758-x64.msu](http://go.microsoft.com/fwlink/?LinkId=717507) </br> **x86:**  [Win8.1-KB3134758-x86.msu](http://go.microsoft.com/fwlink/?LinkID=717963)|
    | Windows 7 SP1 | Tutto | [WMF 4.0](http://www.microsoft.com/en-us/download/details.aspx?id=40855) e [.NET Framework 4.5 o versione successiva](https://msdn.microsoft.com/library/5a4x27ek.aspx) sono installati | **x64:**  [Win7AndW2K8R2-KB3134760-x64.msu](http://go.microsoft.com/fwlink/?LinkId=717504)  </br> **x86:**  [Win7-KB3134760-x86.msu](http://go.microsoft.com/fwlink/?LinkID=717962)|

# <a name="installation-instructions"></a>Istruzioni di installazione

### <a name="to-install-wmf-50-from-windows-explorer-or-file-explorer"></a>Per installare WMF 5.0 da Esplora risorse (o Esplora file):

1. Passare alla cartella in cui è stato scaricato il file MSU.

2. Fare doppio clic sul file MSU per eseguirlo.

### <a name="to-install-wmf-50-from-command-prompt"></a>Per installare WMF 5.0 dal prompt dei comandi:

1. Dopo aver scaricato il pacchetto corretto per l'architettura del computer, aprire una finestra del prompt dei comandi con diritti utente elevati (Esegui come amministratore). Con le opzioni di installazione dei componenti di base di Windows Server 2012 R2 o Windows Server 2012 o Windows Server 2008 R2 SP1, il prompt dei comandi viene aperto con diritti utente elevati per impostazione predefinita.

2. Passare alla cartella in cui è stato scaricato o copiato il pacchetto di installazione di WMF 5.0.

3. Eseguire uno dei comandi seguenti:
    - Nei computer con Windows Server 2012 R2 o Windows 8.1 x64 eseguire **Win8.1AndW2K12R2-KB3134758-x64.msu /quiet**.
    - Nei computer con Windows Server 2012 eseguire **W2K12-KB3134759-x64.msu /quiet**.
    - Nei computer con Windows Server 2008 R2 SP1 o Windows 7 SP1 x64 eseguire **Win7AndW2K8R2-KB3134760-x64.msu /quiet**.
    - Nei computer con Windows 8.1 x86 eseguire **Win8.1-KB3134758-x86.msu /quiet**.
    - Nei computer con Windows 7 SP1 x86 eseguire **Win7-KB3134760-x86.msu /quiet**.

### <a name="additional-installation-notes-for-windows-server-2008-r2-sp1-and-windows-7-sp1"></a>Altre note sull'installazione per Windows Server 2008 R2 SP1 e Windows 7 SP1:

Verificare che siano stati soddisfatti i prerequisiti seguenti:
- Il Service Pack più recente è installato.
- [WMF 4.0](http://www.microsoft.com/en-us/download/details.aspx?id=40855) è installato.
- [.NET Framework 4.5 o versione successiva](https://msdn.microsoft.com/library/5a4x27ek.aspx) è installato.

**Dipendenza da WMF 4.0**

I sistemi Windows Server 2008 R2 SP1 e Windows 7 SP1 includono PowerShell 2.0, WinRM e WMI. I pacchetti WMF 3.0 e WMF 4.0, che aggiornano questi componenti predefiniti, sono stati pubblicati dopo il rilascio di Windows Server 2008 R2 SP1 e Windows 7 SP1. Per l'installazione/disinstallazione dei pacchetti WMF 3.0 e WMF 4.0 sono stati rilevati alcuni problemi nel percorso di aggiornamento seguente:

- Versione predefinita --> WMF 4.0
- Versione predefinita --> WMF 3.0 --> WMF4.0. 

Tutti questi problemi sono stati risolti nei pacchetti WMF 4.0. WMF 4.0 rappresenta quindi un prerequisito per l'installazione di WMF 5.0 in Windows Server 2008 R2 SP1 e Windows 7 SP1. Di seguito sono riportati i problemi specifici che potrebbero verificarsi se non si installa WMF 4.0 prima dell'aggiornamento a WMF 5.0:

- Il log degli eventi inoltrati non è disponibile e il log EventCollector non è visualizzato nel Visualizzatore eventi dopo la disinstallazione di WMF 3.0 o WMF 5.0 (senza l'installazione del prerequisito WMF 4.0) in Windows 7 SP1 e in Windows Server 2008 R2 SP1 ([KB2809215](https://support.microsoft.com/en-us/kb/2809215)).
- Eventuali personalizzazioni della variabile di ambiente *PSModulePath* vengono reimpostate sul valore predefinito in caso di aggiornamento diretto dalla versione predefinita di PowerShell 2.0 a WMF 5.0 ([KB2872035](https://support.microsoft.com/en-us/kb/2872035)) o da WMF 3.0 a WMF 5.0. ([KB2872047](https://support.microsoft.com/en-us/kb/2872047)) in Windows 7 SP1 e in Windows Server 2008 R2 SP1.

**Dipendenza da WinRM**

Desired State Configuration (DSC) in Windows PowerShell dipende da WinRM. WinRM non è abilitato per impostazione predefinita in Windows Server 2008 R2 SP1 e Windows 7 SP1. Per abilitare WinRM, in una sessione di Windows PowerShell con privilegi elevati eseguire **Set-WSManQuickConfig**.

# <a name="uninstallation-instructions"></a>Istruzioni di disinstallazione

### <a name="using-command-prompt"></a>Dal prompt dei comandi

1.  Aprire **Prompt dei comandi**.

2.  Eseguire il [programma di avvio di Windows Update autonomo](https://support.microsoft.com/en-us/kb/934307) come indicato di seguito:

In Windows Server 2012 R2 e Windows 8.1:
```powershell
wusa /uninstall /kb:3134758
```
In Windows Server 2012:
```powershell
wusa /uninstall /kb:3134759
```
In Windows Server 2008 R2 SP1 e Windows 7 SP1:
```powershell
wusa /uninstall /kb:3134760
```

### <a name="using-control-panel"></a>Dal Pannello di controllo

1.  Aprire il **Pannello di controllo**.

2.  Aprire **Programmi** e quindi **Disinstalla un programma**.

3.  Fare clic su **Visualizza aggiornamenti installati**.

4.  Selezionare **Windows Management Framework 5.0** nell'elenco degli aggiornamenti installati. Questi aggiornamenti corrispondono a *KB3134758*, *KB3134759* o *KB3134760*. Fare clic su **Disinstalla**.

