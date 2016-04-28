# Requisiti di sistema

- Installare gli ultimi aggiornamenti di Windows prima di installare WMF 5.0 RTM.
- È possibile installare WMF 5.0 RTM solo nei sistemi operativi seguenti:

    | Sistema operativo       | Edizioni         | Prerequisiti        | Collegamenti al pacchetto |
    |------------------------|--------------|------------------|----------------------| --------------|
    | Windows Server 2012 R2 |  |  | <ctype="x-NOTFOUND" mdpre="[" mdpost="](http://go.microsoft.com/fwlink/?LinkId=717507)">Win8.1AndW2K12R2-KB3134758-x64.msu</ctype="x-NOTFOUND"> |
    | Windows Server 2012    |  |  | <ctype="x-NOTFOUND" mdpre="[" mdpost="](http://go.microsoft.com/fwlink/?LinkId=717506)">W2K12-KB3134759-x64.msu</ctype="x-NOTFOUND"> |
    | Windows Server 2008 R2 SP1 | Tutte, ad eccezione di IA64 | Installazione di <ctype="x-NOTFOUND" mdpre="[" mdpost="](http://www.microsoft.com/en-us/download/details.aspx?id=40855)">WMF 4.0</ctype="x-NOTFOUND"> e <ctype="x-NOTFOUND" mdpre="[" mdpost="](https://msdn.microsoft.com/en-us/library/5a4x27ek.aspx)">.NET Framework 4.5 o versioni successive</ctype="x-NOTFOUND">| <ctype="x-NOTFOUND" mdpre="[" mdpost="](http://go.microsoft.com/fwlink/?LinkId=717504)">Win7AndW2K8R2-KB3134760-x64.msu</ctype="x-NOTFOUND">|
    | Windows 8.1 | Pro, Enterprise | | <ctype="x-NOTFOUND" mdpre="**" mdpost="**">x64:</ctype="x-NOTFOUND">  <ctype="x-NOTFOUND" mdpre="[" mdpost="](http://go.microsoft.com/fwlink/?LinkId=717507)">Win8.1AndW2K12R2-KB3134758-x64.msu</ctype="x-NOTFOUND"> </br> <ctype="x-NOTFOUND" mdpre="**" mdpost="**">x86:</ctype="x-NOTFOUND">  <ctype="x-NOTFOUND" mdpre="[" mdpost="](http://go.microsoft.com/fwlink/?LinkID=717963)">Win8.1-KB3134758-x86.msu</ctype="x-NOTFOUND">|
    | Windows 7 SP1 | Tutte | Installazione di <ctype="x-NOTFOUND" mdpre="[" mdpost="](http://www.microsoft.com/en-us/download/details.aspx?id=40855)">WMF 4.0</ctype="x-NOTFOUND"> e <ctype="x-NOTFOUND" mdpre="[" mdpost="](https://msdn.microsoft.com/en-us/library/5a4x27ek.aspx)">.NET Framework 4.5 o versioni successive </ctype="x-NOTFOUND">| <ctype="x-NOTFOUND" mdpre="**" mdpost="**">x64:</ctype="x-NOTFOUND"> <ctype="x-NOTFOUND" mdpre="[" mdpost="](http://go.microsoft.com/fwlink/?LinkId=717504)">Win7AndW2K8R2-KB3134760-x64.msu</ctype="x-NOTFOUND">  </br> <ctype="x-NOTFOUND" mdpre="**" mdpost="**">x86:</ctype="x-NOTFOUND">  <ctype="x-NOTFOUND" mdpre="[" mdpost="](http://go.microsoft.com/fwlink/?LinkID=717962)">Win7-KB3134760-x86.msu</ctype="x-NOTFOUND">|

# Istruzioni di installazione

### Per installare WMF 5.0 da Esplora risorse (o Esplora file):

1. Passare alla cartella in cui è stato scaricato il file MSU.

2. Fare doppio clic sul file MSU per eseguirlo.

### Per installare WMF 5.0 dal prompt dei comandi:

1. Dopo aver scaricato il pacchetto corretto per l'architettura del computer, aprire una finestra del prompt dei comandi con diritti utente elevati (Esegui come amministratore). Con le opzioni di installazione dei componenti di base di Windows Server 2012 R2 o Windows Server 2012 o Windows Server 2008 R2 SP1, il prompt dei comandi viene aperto con diritti utente elevati per impostazione predefinita.

2. Passare alla cartella in cui è stato scaricato o copiato il pacchetto di installazione di WMF 5.0.

3. Eseguire uno dei comandi seguenti:
    - Nei computer con Windows Server 2012 R2 o Windows 8.1 x64 eseguire <ctype="x-NOTFOUND" mdpre="**" mdpost="**">Win8.1AndW2K12R2-KB3134758-x64.msu /quiet</ctype="x-NOTFOUND">.
    - Nei computer con Windows Server 2012 eseguire <ctype="x-NOTFOUND" mdpre="**" mdpost="**">W2K12-KB3134759-x64.msu /quiet</ctype="x-NOTFOUND">.
    - Nei computer con Windows Server 2008 R2 SP1 o Windows 7 SP1 x64 eseguire <ctype="x-NOTFOUND" mdpre="**" mdpost="**">Win7AndW2K8R2-KB3134760-x64.msu /quiet</ctype="x-NOTFOUND">.
    - Nei computer con Windows 8.1 x86 eseguire <ctype="x-NOTFOUND" mdpre="**" mdpost="**">Win8.1-KB3134758-x86.msu /quiet</ctype="x-NOTFOUND">.
    - Nei computer con Windows 7 SP1 x86 eseguire <ctype="x-NOTFOUND" mdpre="**" mdpost="**">Win7-KB3134760-x86.msu /quiet</ctype="x-NOTFOUND">.

### Altre note sull'installazione per Windows Server 2008 R2 SP1 e Windows 7 SP1:

Verificare che siano stati soddisfatti i prerequisiti seguenti:
- Il Service Pack più recente è installato.
- <ctype="x-NOTFOUND" mdpre="[" mdpost="](http://www.microsoft.com/en-us/download/details.aspx?id=40855)">WMF 4.0</ctype="x-NOTFOUND"> è installato.
- <ctype="x-NOTFOUND" mdpre="[" mdpost="](https://msdn.microsoft.com/en-us/library/5a4x27ek.aspx)">.NET Framework 4.5 o versione successiva</ctype="x-NOTFOUND"> è installato.

**Dipendenza da WMF 4.0**

I sistemi Windows Server 2008 R2 SP1 e Windows 7 SP1 includono PowerShell 2.0, WinRM e WMI. I pacchetti WMF 3.0 e WMF 4.0, che aggiornano questi componenti predefiniti, sono stati pubblicati dopo il rilascio di Windows Server 2008 R2 SP1 e Windows 7 SP1. Per l'installazione/disinstallazione dei pacchetti WMF 3.0 e WMF 4.0 sono stati rilevati alcuni problemi nel percorso di aggiornamento seguente:

- Versione predefinita --> WMF 4.0
- Versione predefinita --> WMF 3.0 --> WMF4.0. 

Tutti questi problemi sono stati risolti nei pacchetti WMF 4.0. WMF 4.0 rappresenta quindi un prerequisito per l'installazione di WMF 5.0 in Windows Server 2008 R2 SP1 e Windows 7 SP1. Di seguito sono riportati i problemi specifici che potrebbero verificarsi se non si installa WMF 4.0 prima dell'aggiornamento a WMF 5.0:

- Il log degli eventi inoltrati non è disponibile e il log EventCollector non è visualizzato nel Visualizzatore eventi dopo la disinstallazione di WMF 3.0 o WMF 5.0 (senza l'installazione del prerequisito WMF 4.0) in Windows 7 SP1 e in Windows Server 2008 R2 SP1 (<ctype="x-NOTFOUND" mdpre="[" mdpost="](https://support.microsoft.com/en-us/kb/2809215)">KB2809215</ctype="x-NOTFOUND">).
- Eventuali personalizzazioni della variabile di ambiente <ctype="x-NOTFOUND" mdpre="*" mdpost="*">PSModulePath</ctype="x-NOTFOUND"> vengono reimpostate sul valore predefinito in caso di aggiornamento diretto dalla versione predefinita di PowerShell 2.0 a WMF 5.0 (<ctype="x-NOTFOUND" mdpre="[" mdpost="](https://support.microsoft.com/en-us/kb/2872035)">KB2872035</ctype="x-NOTFOUND">) o da WMF 3.0 a WMF 5.0. (<ctype="x-NOTFOUND" mdpre="[" mdpost="](https://support.microsoft.com/en-us/kb/2872047)">KB2872047</ctype="x-NOTFOUND">) in Windows 7 SP1 e in Windows Server 2008 R2 SP1.

**Dipendenza da WinRM**

Desired State Configuration (DSC) in Windows PowerShell dipende da WinRM. WinRM non è abilitato per impostazione predefinita in Windows Server 2008 R2 SP1 e Windows 7 SP1. Per abilitare WinRM, in una sessione di Windows PowerShell con privilegi elevati eseguire <ctype="x-NOTFOUND" mdpre="**" mdpost="**">Set-WSManQuickConfig</ctype="x-NOTFOUND">.

# Istruzioni di disinstallazione

### Dal prompt dei comandi

1.  Aprire <ctype="x-NOTFOUND" mdpre="**" mdpost="**">Prompt dei comandi</ctype="x-NOTFOUND">.

2.  Eseguire il <ctype="x-NOTFOUND" mdpre="[" mdpost="](https://support.microsoft.com/en-us/kb/934307)">programma di avvio di Windows Update autonomo</ctype="x-NOTFOUND"> come indicato di seguito:

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

### Dal Pannello di controllo

1.  Aprire il <ctype="x-NOTFOUND" mdpre="**" mdpost="**">Pannello di controllo</ctype="x-NOTFOUND">.

2.  Aprire <ctype="x-NOTFOUND" mdpre="**" mdpost="**">Programmi</ctype="x-NOTFOUND"> e quindi <ctype="x-NOTFOUND" mdpre="**" mdpost="**">Disinstalla un programma</ctype="x-NOTFOUND">.

3.  Fare clic su <ctype="x-NOTFOUND" mdpre="**" mdpost="**">Visualizza aggiornamenti installati</ctype="x-NOTFOUND">.

4.  Selezionare <ctype="x-NOTFOUND" mdpre="**" mdpost="**">Windows Management Framework 5.0</ctype="x-NOTFOUND"> nell'elenco degli aggiornamenti installati. Corrisponde a <ctype="x-NOTFOUND" mdpre="*" mdpost="*">KB3134758</ctype="x-NOTFOUND">, <ctype="x-NOTFOUND" mdpre="*" mdpost="*">KB3134759</ctype="x-NOTFOUND"> o <ctype="x-NOTFOUND" mdpre="*" mdpost="*">KB3134760</ctype="x-NOTFOUND">. Fare clic su <ctype="x-NOTFOUND" mdpre="**" mdpost="**">Disinstalla</ctype="x-NOTFOUND">.


<!--HONumber=Mar16_HO4-->


