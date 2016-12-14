# <a name="installation-instructions"></a>Istruzioni di installazione

Scaricare il pacchetto corretto per il sistema operativo e l'architettura in uso:

| Sistema operativo       | Architettura | Nome pacchetto              | 
|------------------------|--------------|---------------------------| 
| Windows Server 2012 R2 | x64      | [Win8.1AndW2K12R2-KB3134758-x64.msu](http://go.microsoft.com/fwlink/?LinkId=717507) | 
| Windows Server 2012    | x64      | [W2K12-KB3134759-x64.msu](http://go.microsoft.com/fwlink/?LinkId=717506) | 
| Windows Server 2008 R2 | x64      | [Win7AndW2K8R2-KB3134760-x64.msu](http://go.microsoft.com/fwlink/?LinkId=717504) |
| Windows 8.1            | x64          | [Win8.1AndW2K12R2-KB3134758-x64.msu](http://go.microsoft.com/fwlink/?LinkId=717507) |
| Windows 8.1            | x86          | [Win8.1-KB3134758-x86.msu](http://go.microsoft.com/fwlink/?LinkID=717963) |
| Windows 7 SP1          | x64          | [Win7AndW2K8R2-KB3134760-x64.msu](http://go.microsoft.com/fwlink/?LinkId=717504) |
| Windows 7 SP1          | x86          | [Win7-KB3134760-x86.msu](http://go.microsoft.com/fwlink/?LinkID=717962) |


**Per installare WMF 5.0 da Esplora risorse (o Esplora file in Windows Server 2012 R2 e Windows 8.1):**

1. Passare alla cartella in cui è stato scaricato il file MSU.

2. Fare doppio clic sul file MSU per eseguirlo.

**Per installare WMF 5.0 dal prompt dei comandi:** 

1. Dopo aver scaricato il pacchetto corretto per l'architettura del computer, aprire una finestra del prompt dei comandi con diritti utente elevati (Esegui come amministratore). Con le opzioni di installazione dei componenti di base di Windows Server 2012 R2 o Windows Server 2012 o Windows Server 2008 R2 SP1, il prompt dei comandi viene aperto con diritti utente elevati per impostazione predefinita.

2. Passare alla cartella in cui è stato scaricato o copiato il pacchetto di installazione di WMF 5.0.

3. Eseguire uno dei comandi seguenti:
    - Nei computer con Windows Server 2012 R2 o Windows 8.1 x64 eseguire **Win8.1AndW2K12R2-KB3134758-x64.msu /quiet**.
    - Nei computer con Windows Server 2012 eseguire **W2K12-KB3134759-x64.msu /quiet**.
    - Nei computer con Windows Server 2008 R2 SP1 o Windows 7 SP1 x64 eseguire **Win7AndW2K8R2-KB3134760-x64.msu /quiet**.
    - Nei computer con Windows 8.1 x86 eseguire **Win8.1-KB3134758-x86.msu /quiet**.
    - Nei computer con Windows 7 SP1 x86 eseguire **Win7-KB3134760-x86.msu /quiet**.

**Altre note sull'installazione per Windows Server 2008 SP1 e Windows 7 SP1:**

Verificare che siano stati soddisfatti i prerequisiti seguenti:
- Il Service Pack più recente è installato.
- [WMF 4.0](http://www.microsoft.com/en-us/download/details.aspx?id=40855) è installato

*Dipendenza da WnRM:* il servizio di configurazione dello stato desiderato tramite Windows PowerShell dipende da WinRM. WinRM non è abilitato per impostazione predefinita in Windows Server 2008 R2 e Windows 7. Per abilitare WinRM, in una sessione di Windows PowerShell con privilegi elevati eseguire **Set-WSManQuickConfig**.


