# Aggiornamenti dell'oggetto FileInfo
Le informazioni sulla versione dei file possono essere fuorvianti, in particolare in seguito all'applicazione di patch ai file. In questa versione di WMF Production Preview sono state aggiunte le nuove proprietà di script **FileVersionRaw** e **ProductVersionRaw** per gli oggetti FileInfo. Ecco queste proprietà nel formato visualizzato per powershell.exe:

PS C:\\&gt; Get-Process -Id $pid -FileVersionInfo | fl \*version\* -Force

FileVersionRaw : 10.0.10055.0

ProductVersionRaw : 10.0.10055.0

FileVersion : 10.0.10055.0 (fbl\_srv2.150402-1826)

ProductVersion : 10.0.10055.0
<!--HONumber=Mar16_HO2-->
