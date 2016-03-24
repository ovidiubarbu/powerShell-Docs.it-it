# Requisiti di sistema

- Installare gli ultimi aggiornamenti di Windows prima di installare WMF 5.0 RTM.
- È possibile installare WMF 5.0 RTM solo nei sistemi operativi seguenti:

    | Sistema operativo       | Edizioni         | Prerequisiti        | Collegamenti al pacchetto |
    |------------------------|--------------|------------------|----------------------| --------------|
    | Windows Server 2012 R2 |  |  | [Win8.1AndW2K12R2-KB3134758-x64.msu](http://go.microsoft.com/fwlink/?LinkId=717507) |
    | Windows Server 2012    |  |  | [W2K12-KB3134759-x64.msu](http://go.microsoft.com/fwlink/?LinkId=717506) |
    | Windows Server 2008 R2 SP1 | Tutte, ad eccezione di IA64 | Installazione di [WMF 4.0](http://www.microsoft.com/en-us/download/details.aspx?id=40855) e [.NET Framework 4.5 o versioni successive](https://msdn.microsoft.com/en-us/library/5a4x27ek.aspx)| [Win7AndW2K8R2-KB3134760-x64.msu](http://go.microsoft.com/fwlink/?LinkId=717504)|
    | Windows 8.1 | Pro, Enterprise | | **x64:** [Win8.1AndW2K12R2-KB3134758-x64.msu](http://go.microsoft.com/fwlink/?LinkId=717507) </br> **x86:** [Win8.1-KB3134758-x86.msu](http://go.microsoft.com/fwlink/?LinkID=717963)|
    | Windows 7 SP1 | Tutte | Installazione di [WMF 4.0](http://www.microsoft.com/en-us/download/details.aspx?id=40855) e [.NET Framework 4.5 o versioni successive](https://msdn.microsoft.com/en-us/library/5a4x27ek.aspx) | **x64:** [Win7AndW2K8R2-KB3134760-x64.msu](http://go.microsoft.com/fwlink/?LinkId=717504)  </br> **x86:** [Win7-KB3134760-x86.msu](http://go.microsoft.com/fwlink/?LinkID=717962)|

# Istruzioni di installazione

### Per installare WMF 5.0 da Esplora risorse (o Esplora file):

1. Passare alla cartella in cui è stato scaricato il file MSU.

2. Fare doppio clic sul file MSU per eseguirlo.

### Per installare WMF 5.0 dal prompt dei comandi:

1. Dopo aver scaricato il pacchetto corretto per l'architettura del computer, aprire una finestra del prompt dei comandi con diritti utente elevati (Esegui come amministratore). Con le opzioni di installazione dei componenti di base di Windows Server 2012 R2 o Windows Server 2012 o Windows Server 2008 R2 SP1, il prompt dei comandi viene aperto con diritti utente elevati per impostazione predefinita.

2. Passare alla cartella in cui è stato scaricato o copiato il pacchetto di installazione di WMF 5.0.

3. Eseguire uno dei comandi seguenti:
    - Nei computer con Windows Server 2012 R2 o Windows 8.1 x64 eseguire **Win8.1AndW2K12R2-KB3134758-x64.msu /quiet**.
    - Nei computer con Windows Server 2012 eseguire **W2K12-KB3134759-x64.msu /quiet**.
    - Nei computer con Windows Server 2008 R2 SP1 o Windows 7 SP1 x64 eseguire **Win7AndW2K8R2-KB3134760-x64.msu /quiet**.
    - Nei computer con Windows 8.1 x86 eseguire **Win8.1-KB3134758-x86.msu /quiet**.
    - Nei computer con Windows 7 SP1 x86 eseguire **Win7-KB3134760-x86.msu /quiet**.

### Altre note sull'installazione per Windows Server 2008 SP1 e Windows 7 SP1:

Verificare che siano stati soddisfatti i prerequisiti seguenti:
- Il Service Pack più recente è installato.
- [WMF 4.0](http://www.microsoft.com/en-us/download/details.aspx?id=40855) è installato.
- [.NET Framework 4.5 o versione successiva](https://msdn.microsoft.com/en-us/library/5a4x27ek.aspx) è installato.

*Dipendenza di WinRM:*
Desired State Configuration (DSC) in Windows PowerShell dipende da WinRM. WinRM non è abilitato per impostazione predefinita in Windows Server 2008 R2 e Windows 7. Per abilitare WinRM, in una sessione di Windows PowerShell con privilegi elevati eseguire **Set-WSManQuickConfig**.

# Istruzioni di disinstallazione

### Dal prompt dei comandi

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

### Dal Pannello di controllo

1.  Aprire il **Pannello di controllo**.

2.  Aprire **Programmi** e quindi **Disinstalla un programma**.

3.  Fare clic su **Visualizza aggiornamenti installati**.

4.  Selezionare **Windows Management Framework 5.0** nell'elenco degli aggiornamenti installati. Questi aggiornamenti corrispondono a *KB3134758*, *KB3134759* o *KB3134760*. Fare clic su **Disinstalla**.
<!--HONumber=Mar16_HO2-->
