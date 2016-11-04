# <a name="known-issues-and-limitations"></a>Limitazioni e problemi noti

<a name="powershell-shortcuts-are-broken-when-used-for-the-first-time"></a>I collegamenti per PowerShell non funzionano la prima volta
------------------------------------------------------------

**Soluzione:** eseguire una delle operazioni seguenti:

1.  Fare clic con il pulsante destro del mouse sul collegamento di PowerShell. Selezionare "Windows PowerShell" per avviare il programma in modalità senza privilegi elevati.
2.  Fare clic con il pulsante destro del mouse sul collegamento di PowerShell. Fare clic con il pulsante destro del mouse su "Windows PowerShell" e selezionare "Esegui come amministratore" per avviare il programma in modalità con privilegi elevati.

Dopo aver eseguito una delle azioni precedenti, i collegamenti per PowerShell funzioneranno. Queste azioni devono essere eseguite una sola volta.


<a name="powershell-modules-and-dsc-resources-report-errors-about-executionpolicy-on-windows-7"></a>I moduli di PowerShell e le risorse DSC segnalano errori per ExecutionPolicy in Windows 7
-------------------------------------------------------------------------------------
In Windows 7 l'uso dei moduli di PowerShell e delle risorse DSC potrebbe causare la segnalazione di errori per ExecutionPolicy.

**Soluzione:** impostare ExecutionPolicy su RemoteSigned eseguendo il comando seguente in una sessione di PowerShell con privilegi elevata (Esegui come amministratore):

```powershell
Set-ExecutionPolicy RemoteSigned
```

<a name="connecting-to-an-old-remote-exchange-endpoint-causes-a-crash"></a>La connessione a un endpoint di Exchange remoto precedente causa un arresto anomalo
------------------------------------------------------------

L'endpoint di Exchange precedente reindirizza a un nuovo endpoint. È presente un bug nella logica di reindirizzamento che causa un arresto anomalo.

**Soluzione:** connettersi direttamente al nuovo endpoint.


<a name="software-inventory-logging-feature-is-erroneously-stopped-after-wmf-50-installation-on-windows-server-2012-r2"></a>La funzionalità Registrazione inventario software viene arrestata erroneamente dopo l'installazione di WMF 5.0 in Windows Server 2012 R2
-------------------------------------------------------------------------------------------------------------

Quando si installa WMF 5.0 in un computer Windows Server 2012 R2 in cui è già in esecuzione Registrazione inventario software, questa funzionalità viene arrestata erroneamente dopo l'installazione.

**Soluzione:** eseguire il cmdlet Start-SilLogging una volta dopo l'installazione di WMF, perché il processo di installazione arresta erroneamente la funzionalità Registrazione inventario software.

<a name="getchilditem-does-not-work-if-literalpath-and-recurse-are-used-together"></a>Get-ChildItem non funziona se si usano insieme -LiteralPath e -Recurse
--------------------------------------------------------------------------

Se un nome di directory contiene un carattere jolly non valido, Get-ChildItem non produrrà i risultati previsti quando si usano insieme entrambe le opzioni -LiteralPath e -Recurse.

**Soluzione:** non è ideale, ma la soluzione attuale consiste nell'implementare la ricorsione nello script anziché affidarsi al cmdlet.


<a name="sysprep-fails-after-wmf-50-installation"></a>Sysprep smette di funzionare dopo l'installazione di WMF 5.0
----------------------------------------

Esistono due possibili soluzioni al problema in base alla versione di Windows Server in esecuzione.

**Soluzione:**
- Per i sistemi che eseguono **Windows Server 2008 R2**
  1. Aprire PowerShell come amministratore
  2. Eseguire il comando seguente 
  
  ```powershell
    Set-SilLogging –TargetUri https://BlankTarget –CertificateThumbprint 0123456789
  ```
  3. Eseguire il comando e ignorare l'errore, perché è previsto.
  
  ```powershell
    Publish-SilData
   ```
  4. Eliminare i file nella directory \Windows\System32\Logfiles\SIL\
  
  ```powershell
    Remove-Item -Recurse $env:SystemRoot\System32\Logfiles\SIL\
  ```
  5. Installare tutti gli aggiornamenti Windows importanti disponibili e iniziare a usare Sysyprep normalmente.
  
- Per i sistemi che eseguono **Windows Server 2012**
  1.    Dopo l'installazione di WMF 5.0 nel server in cui usare Sysprep, eseguire l'accesso come amministratore.
  2.    Copiare Generize.xml dalla directory \Windows\System32\Sysprep\ActionFiles\ in un percorso esterno alla directory Windows, ad esempio C:\.
  3.    Aprire la copia Generalize.xml con il Blocco note.
  4.    Trovare e rimuovere il testo seguente, di cui è necessario eliminare ogni istanza (si troveranno verso la fine del documento).

    ```
    <sysprepOrder order="0x3200"></sysprepOrder>
    <sysprepOrder order="0x3300"></sysprepOrder>
    ```

  5.    Salvare la copia modificata del file Generalize.xml e chiuderlo.
  6.    Aprire una finestra del prompt dei comandi come amministratore
  7.    Eseguire il comando seguente per assumere la proprietà del file Generalize.xml nella cartella system32:

    ```
    Takeown /f C:\Windows\System32\Sysprep\ActionFiles\Generalize.xml 
    ```

  8.    Eseguire il comando seguente per impostare le autorizzazioni appropriate sul file:

    ```
    Cacls C:\Windows\System32\ Sysprep\ActionFiles\Generalize.xml /G `<AdministratorUserName>`:F 
    ```
      * Rispondere Sì al prompt di conferma. 
      * Si noti che `<AdministratorUserName>` deve essere sostituito dal nome utente che è l'amministratore nel computer. Ad esempio, "Amministratore".
      
  9.    Copiare il file modificato e salvato nella directory Sysprep usando il comando seguente:

    ```
    xcopy C:\Generalize.xml C:\Windows\System32\Sysprep\ActionFiles\Generalize.xml 
    ```
      * Rispondere Sì per sovrascrivere (se non si riceve alcuna richiesta di conferma della sovrascrittura, controllare il percorso specificato).
      * Si presuppone che la versione modificata del file Generalize.xml sia stata copiata in C:\.

  10.   Il file Generalize.xml è ora aggiornato con la soluzione alternativa. Eseguire Sysprep con l'opzione generalize abilitata.


<!--HONumber=Oct16_HO5-->


