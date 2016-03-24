# Limitazioni e problemi noti

I collegamenti per PowerShell non funzionano la prima volta
------------------------------------------------------------

**Soluzione:** eseguire una delle operazioni seguenti:

1.  Fare clic con il pulsante destro del mouse sul collegamento di PowerShell. Selezionare "Windows PowerShell" per avviare il programma in modalità senza privilegi elevati.
2.  Fare clic con il pulsante destro del mouse sul collegamento di PowerShell. Fare clic con il pulsante destro del mouse su "Windows PowerShell" e selezionare "Esegui come amministratore" per avviare il programma in modalità con privilegi elevati.

Dopo aver eseguito una delle azioni precedenti, i collegamenti per PowerShell funzioneranno. Queste azioni devono essere eseguite una sola volta.


I moduli di PowerShell e le risorse DSC segnalano errori per ExecutionPolicy in Windows 7
-------------------------------------------------------------------------------------
In Windows 7 l'uso dei moduli di PowerShell e delle risorse DSC potrebbe causare la segnalazione di errori per ExecutionPolicy.

**Soluzione:** impostare ExecutionPolicy su RemoteSigned eseguendo il comando seguente in una sessione di PowerShell con privilegi elevata (Esegui come amministratore):

```powershell
Set-ExecutionPolicy RemoteSigned
```

La connessione a un endpoint di Exchange remoto precedente causa un arresto anomalo
------------------------------------------------------------

L'endpoint di Exchange precedente reindirizza a un nuovo endpoint. È presente un bug nella logica di reindirizzamento che causa un arresto anomalo.

**Soluzione:** connettersi direttamente al nuovo endpoint.


La funzionalità Registrazione inventario software viene arrestata erroneamente dopo l'installazione di WMF 5.0 in Windows Server 2012 R2
-------------------------------------------------------------------------------------------------------------

Quando si installa WMF 5.0 in un computer Windows Server 2012 R2 in cui è già in esecuzione Registrazione inventario software, questa funzionalità viene arrestata erroneamente dopo l'installazione.

**Soluzione:** eseguire il cmdlet Start-SilLogging una volta dopo l'installazione di WMF, perché il processo di installazione arresta erroneamente la funzionalità Registrazione inventario software.

Get-ChildItem non funziona se si usano insieme -LiteralPath e -Recurse
--------------------------------------------------------------------------

Se un nome di directory contiene un carattere jolly non valido, Get-ChildItem non produrrà i risultati previsti quando si usano insieme entrambe le opzioni
-LiteralPath e - Recurse.

**Soluzione:** non è ideale, ma la soluzione attuale consiste nell'implementare la ricorsione nello script anziché affidarsi al cmdlet.
<!--HONumber=Mar16_HO2-->
