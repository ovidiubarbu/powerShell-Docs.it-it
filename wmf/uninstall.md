# Istruzioni di disinstallazione

## Dal prompt dei comandi
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

## Dal Pannello di controllo
1.  Aprire il **Pannello di controllo**.
2.  Aprire **Programmi** e quindi **Disinstalla un programma**.
3.  Fare clic su **Visualizza aggiornamenti installati**.
4.  Selezionare **Windows Management Framework 5.0** nell'elenco degli aggiornamenti installati. Questi aggiornamenti corrispondono a *KB3134758*, *KB3134759* o *KB3134760*. Fare clic su **Disinstalla**.
<!--HONumber=Mar16_HO2-->
