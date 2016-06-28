# Miglioramenti per il debug degli script di PowerShell

In PowerShell 5.0 sono stati introdotti numerosi miglioramenti per ottimizzare l'esperienza di debug.

## Interrompi tutto

La console di PowerShell e Windows PowerShell ISE ora consentono di interrompere il debugger per gli script in esecuzione. Questa funzionalità è disponibile sia per le sessioni locali che remote.

Nella console premere **CTRL+INTERR**.

In ISE premere **CTRL+B** oppure usare il comando di menu **Debug -> Interrompi tutto**.

## Debug remoto e modifica dei file remota in Windows PowerShell ISE

Windows PowerShell ISE consente ora di aprire e modificare i file in una sessione remota eseguendo il comando PSEdit.
Ad esempio, è possibile aprire un file per la modifica dalla riga di comando in una sessione remota nel modo seguente:

```powershell
[RemoteComputer1]: PS C:\> PSEdit C:\DebugDemoScripts\Test-GetMutex.ps1
```

Inoltre, è ora possibile modificare e salvare le modifiche in un file remoto che viene aperto automaticamente in Windows PowerShell ISE quando si raggiunge un punto di interruzione.
È ora possibile eseguire il debug di un file di script in esecuzione in un computer remoto, modificare il file per correggere un errore ed eseguire nuovamente lo script modificato.

## Debug avanzato degli script

Sono disponibili nuove funzionalità di debug avanzate che consentono di collegare qualsiasi processo del computer locale che ha caricato Windows PowerShell e di eseguire il debug di spazi di esecuzione arbitrari in tale processo.

### Debug di spazi di esecuzione

Sono stati aggiunti nuovi cmdlet che consentono di elencare gli spazi di esecuzione correnti in un processo e collegare il debugger della console di Windows PowerShell o di ISE a tale spazio di esecuzione per il debug degli script:

-   Get-Runspace
-   Debug-Runspace
-   Enable-RunspaceDebug
-   Disable-RunspaceDebug
-   Get-RunspaceDebug

### Collegarsi a un processo che ospita PowerShell

È ora possibile collegarsi a qualsiasi processo di computer con Windows PowerShell caricato. A tale scopo, si avvia una sessione interattiva con il processo, in modo analogo a come si avvia una sessione remota interattiva eseguendo il cmdlet Enter-PSSession:

-   Enter-PSHostProcess
-   Exit-PSHostProcess

<!--HONumber=Jun16_HO4-->


