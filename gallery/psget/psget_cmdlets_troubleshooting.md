## Come risolvere il problema segnalato da un messaggio simile a: "AVVISO: Impossibile scaricare il pacchetto 'nome pacchetto'"




È stato segnalato che il cmdlet Install-Module o Update-Module a volte genera un errore in alcuni computer.
In base alle ricerche effettuate, il problema ha probabilmente a che fare con la connessione di rete.
Di recente è stato aggiornato il provider NuGet per assicurare il download affidabile dei pacchetti.
È possibile usare le istruzioni riportate di seguito per installare la build più recente del provider NuGet e quindi installare o aggiornare il proprio modulo.
Nell'esempio viene usato il modulo 'Azure'.

```powershell
Install-PackageProvider NuGet -MinimumVersion 2.8.5.206 -Force
Launch new PowerShell Console
Update-Module Azure -Verbose
```


<!--HONumber=Aug16_HO3-->


