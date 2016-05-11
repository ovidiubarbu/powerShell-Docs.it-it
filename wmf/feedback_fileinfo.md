# Aggiornamenti dell'oggetto FileInfo
Le informazioni sulla versione dei file possono essere fuorvianti, in particolare in seguito all'applicazione di patch ai file. Questa versione di WMF 5.0 aggiunge nuove **FileVersionRaw** e **ProductVersionRaw** 
proprietà di script degli oggetti FileInfo. Ecco le proprietà come vengono visualizzate per powershell.exe (presupponendo che $pid è l'ID del processo di PowerShell):

```powershell
PS C:\> Get-Process -Id $pid -FileVersionInfo | fl *version* -Force


FileVersionRaw    : 10.0.10586.117
ProductVersionRaw : 10.0.10586.117
FileVersion       : 10.0.10586.117 (th2_release.160212-2359)
ProductVersion    : 10.0.10586.117


<!--HONumber=Apr16_HO3-->


