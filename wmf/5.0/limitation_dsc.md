# Problemi noti e limitazioni di Desired State Configuration (DSC)

Modifica di rilievo: i certificati usati per crittografare/decrittografare le password nelle configurazioni DSC potrebbero non funzionare dopo l'installazione di WMF 5.0 RTM
--------------------------------------------------------------------------------------------------------------------------------

Nelle versioni WMF 4.0 e WMF 5.0 Preview, DSC non consente lunghezze maggiori di 121 caratteri per le password nella configurazione. DSC imponeva l'uso di password brevi anche se erano preferibili password lunghe e complesse. Questa modifica consente una lunghezza arbitraria per le password nella configurazione DSC.

**Soluzione:** creare nuovamente il certificato con utilizzo chiavi Crittografia dati o Crittografia chiavi e l'utilizzo chiavi avanzato Crittografia documento (1.3.6.1.4.1.311.80.1). Per altre informazioni, vedere l'articolo di Technet <https://technet.microsoft.com/en-us/library/dn807171.aspx>.


Potrebbero verificarsi problemi con i cmdlet DSC dopo l'installazione di WMF 5.0 RTM
------------------------------------------------------------------------------------
Start-DscConfiguration e altri cmdlet DSC potrebbero non funzionare dopo l'installazione di WMF 5.0 RTM con l'errore seguente:
```powershell
    LCM failed to retrieve the property PendingJobStep from the object of class dscInternalCache .
    + CategoryInfo : ObjectNotFound: (root/Microsoft/...gurationManager:String) [], CimException
    + FullyQualifiedErrorId : MI RESULT 6
    + PSComputerName : localhost
```

**Soluzione:** eliminare DSCEngineCache.mof eseguendo il comando seguente in una sessione di PowerShell con privilegi elevata (Esegui come amministratore):
    
```powershell
Remove-Item -Path $env:SystemRoot\system32\Configuration\DSCEngineCache.mof
```


I cmdlet DSC potrebbero non funzionare se si installa WMF 5.0 RTM su WMF 5.0 Production Preview
------------------------------------------------------
**Soluzione:** eseguire il comando seguente in una sessione di PowerShell con privilegi elevati (Esegui come amministratore):
```powershell
    mofcomp $env:windir\system32\wbem\DscCoreConfProv.mof
```


Lo stato di Gestione configurazione locale può diventare instabile durante l'uso di Get-DscConfiguration in DebugMode
-------------------------------------------------------------------------------

Se Gestione configurazione locale è in DebugMode, la pressione di CTRL+C per arrestare l'elaborazione di Get-DscConfiguration può causare il passaggio a uno stato instabile per Gestione configurazione locale, nel quale non funzionerà la maggior parte dei cmdlet DSC.

**Soluzione:** non premere CTRL+C durante il debug del cmdlet Get-DscConfiguration.


Stop-DscConfiguration potrebbe bloccarsi in DebugMode
------------------------------------------------------------------------------------------------------------------------
Se Gestione configurazione locale è in DebugMode, Stop-DscConfiguration potrebbe bloccarsi durante il tentativo di arrestare un'operazione avviata da Get-DscConfiguration

**Soluzione:** terminare il debug dell'operazione avviata da Get-DscConfiguration, come illustrato nella sezione [Debug degli script per risorse DSC](#dsc-resource-script-debugging).


In DebugMode non vengono visualizzati messaggi di errore dettagliati
-----------------------------------------------------------------------------------
Se Gestione configurazione locale è in DebugMode, non viene visualizzato alcun messaggio di errore dettagliato da risorse DSC.

**Soluzione:** disabilitare *DebugMode* per visualizzare i messaggi dettagliati dalla risorsa


Le operazioni Invoke-DscResource non possono essere recuperate dal cmdlet Get-DscConfigurationStatus
--------------------------------------------------------------------------------------
Dopo aver usato il cmdlet Invoke-DscResource per richiamare direttamente i metodi di qualsiasi risorsa, i record di tale operazione non possono essere recuperati tramite Get-DscConfigurationStatus in un secondo momento.

**Soluzione:** nessuna.


Get-DscConfigurationStatus restituisce le operazioni del ciclo di pull come operazioni di tipo *Consistency*
---------------------------------------------------------------------------------
Quando un nodo viene impostato sulla modalità di aggiornamento PULL, per ogni operazione pull eseguita il cmdlet Get-DscConfigurationStatus restituisce *Consistency* invece di *Initial* come tipo di operazione.

**Soluzione:** nessuna.

Il cmdlet Invoke-DscResource non restituisce i messaggi nell'ordine di generazione
---------------------------------------------------------------------------------
Il cmdlet Invoke-DscResource non restituisce i messaggi dettagliati, di avviso e di errore nell'ordine con cui vengono generati da Gestione configurazione locale o dalla risorsa DSC.

**Soluzione:** nessuna.


Non è possibile eseguire facilmente il debug di risorse DSC usate con Invoke-DscResource
-----------------------------------------------------------------------
Quando Gestione configurazione locale è in esecuzione in modalità di debug (vedere [Debug degli script per risorse DSC](#dsc-resource-script-debugging) per altri dettagli), il cmdlet Invoke-DscResource non fornisce informazioni sullo spazio di esecuzione a cui connettersi per il debug.
**Soluzione:** individuare lo spazio di esecuzione e collegarlo tramite i cmdlet **Get-PSHostProcessInfo**, **Enter-PSHostProcess**, **Get-Runspace** e **Debug-Runspace** per eseguire il debug della risorsa DSC.

```powershell
# Find all the processes hosting PowerShell
Get-PSHostProcessInfo

ProcessName ProcessId AppDomainName
----------- --------- -------------
powershell 3932 DefaultAppDomain
powershell_ise 2304 DefaultAppDomain
WmiPrvSE 3396 DscPsPluginWkr_AppDomain

# Enter the process that is hosting DSC engine (WMI process with DscPsPluginWkr_Appdomain)
Enter-PSHostProcess -Id 3396 -AppDomainName DscPsPluginWkr_AppDomain

# Find all the available rusnspaces in that process
Get-Runspace

Id Name ComputerName Type State Availability
-- ---- ------------ ---- ----- ------------
2 Runspace2 localhost Local Opened InBreakpoint
5 RemoteHost localhost Local Opened Busy

# Debug the runspace that is in **InBreakpoint** availability state
Debug-Runspace -Id 2
```


Documenti di configurazioni parziali diversi per lo stesso nodo non possono avere nomi di risorse identici
------------------------------------------------------------------------------------------

Nel caso di più configurazioni parziali distribuite in un singolo nodo, la presenza di nomi identici per le risorse può causare un errore di runtime.

**Soluzione:** usare nomi diversi anche per le stesse risorse in configurazioni parziali diverse.


Start-DscConfiguration -UseExisting non funziona con -Credential
------------------------------------------------------------------

Quando si usa Start-DscConfiguration con il parametro -UseExisting, il parametro -Credential viene ignorato. DSC usa l'identità del processo predefinita per continuare l'operazione. Ciò causa un errore quando sono necessarie credenziali diverse per procedere nel nodo remoto.

**Soluzione:** usare una sessione CIM sessione per operazioni DSC remote:
```powershell
$session = New-CimSession -ComputerName $node -Credential $credential
Start-DscConfiguration -UseExisting -CimSession $session
```


Indirizzi IPv6 come nomi di nodo in configurazioni DSC
--------------------------------------------------
Gli indirizzi IPv6 come nomi dei nodi negli script di configurazione DSC non sono supportati in questa versione.

**Soluzione:** nessuna.


Debug di risorse DSC basate su classi
--------------------------------------
Il debug di risorse DSC basate su classi non è supportato in questa versione.

**Soluzione:** nessuna.


Le variabili e le funzioni definite nell'ambito $script per le risorse DSC basate su classi non vengono mantenute per più chiamate a una risorsa DSC 
-------------------------------------------------------------------------------------------------------------------------------------

Più chiamate consecutive di Start-DSCConfiguration avranno esito negativo se la configurazione usa qualsiasi risorsa basata su classi con variabili o funzioni definite nell'ambito $script.

**Soluzione:** definire tutte le variabili e le funzioni nella classe della risorsa DSC. Nessuna variabile/funzione con ambito $script.


Debug delle risorse DSC quando una risorsa usa PSDscRunAsCredential
----------------------------------------------------------------------
Il debug delle risorse DSC quando una risorsa usa la proprietà *PSDscRunAsCredential* nella configurazione non è supportato in questa versione.

**Soluzione:** nessuna.


La proprietà PsDscRunAsCredential non è supportata per le risorse DSC composite
----------------------------------------------------------------

**Soluzione:** usare la proprietà Credential, se disponibile. WindowsFeatureSet e ServiceSet di esempio


*Get-DscResource -Syntax* non rappresenta correttamente PsDscRunAsCredential
-------------------------------------------------------------------------
Get-DscResource -Syntax non rappresenta correttamente PsDscRunAsCredential quando la risorsa contrassegna la proprietà come obbligatoria o non la supporta.

**Soluzione:** nessuna. Tuttavia, con la creazione della configurazione in ISE vengono usati i metadati corretti della proprietà PsDscRunAsCredential quando si usa IntelliSense.


WindowsOptionalFeature non è disponibile in Windows 7
-----------------------------------------------------

La risorsa DSC WindowsOptionalFeature non è disponibile in Windows 7. La risorsa richiede il modulo Gestione e manutenzione immagini distribuzione e i cmdlet di Gestione e manutenzione immagini distribuzione disponibili a partire da Windows 8 e nelle versioni più recenti del sistema operativo Windows.

Per le risorse DSC basate su classi, Import-DscResource -ModuleVersion potrebbe non funzionare come previsto   
------------------------------------------------------------------------------------------
Se il nodo di compilazione include più versioni di un modulo di risorse DSC basato su classi, `Import-DscResource -ModuleVersion` non recupera la versione specificata e genera l'errore di compilazione seguente.

```
ImportClassResourcesFromModule : Exception calling "ImportClassResourcesFromModule" with "3" argument(s): "Keyword 'MyTestResource' already defined in the configuration."
At C:\Windows\system32\WindowsPowerShell\v1.0\Modules\PSDesiredStateConfiguration\PSDesiredStateConfiguration.psm1:2035 char:35
+ ... rcesFound = ImportClassResourcesFromModule -Module $mod -Resources $r ...
+                 ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
    + CategoryInfo          : NotSpecified: (:) [ImportClassResourcesFromModule], MethodInvocationException
    + FullyQualifiedErrorId : PSInvalidOperationException,ImportClassResourcesFromModule
```

**Soluzione:** importare la versione richiesta definendo l'oggetto *ModuleSpecification* in `-ModuleName` con la chiave `RequiredVersion` specificata come riportato di seguito:
``` PowerShell  
Import-DscResource -ModuleName @{ModuleName='MyModuleName';RequiredVersion='1.2'}  
```  

Alcune risorse DSC, come la risorsa Registry, potrebbero iniziare a richiedere molto tempo per elaborare la richiesta.
--------------------------------------------------------------------------------------------------------------------------------

**Soluzione 1**: creare un'attività di pianificazione che pulisce periodicamente la cartella seguente.
``` PowerShell 
$env:windir\system32\config\systemprofile\AppData\Local\Microsoft\Windows\PowerShell\CommandAnalysis 
```

**Soluzione 2**: modificare la configurazione DSC per pulire la cartella *CommandAnalysis* al termine della configurazione.
``` PowerShell
Configuration $configName
{

   # User Data
    Registry SetRegisteredOwner
    {
        Ensure = 'Present'
        Force = $True
        Key = $Node.RegisteredKey
        ValueName = $Node.RegisteredOwnerValue
        ValueType = 'String'
        ValueData = $Node.RegisteredOwnerData
    }
    #
    # Script to delete the config 
    #
    script DeleteCommandAnalysisCache
    {
        DependsOn="[Registry]SetRegisteredOwner"
        getscript="@{}"
        testscript = 'Remove-Item -Path $env:windir\system32\config\systemprofile\AppData\Local\Microsoft\Windows\PowerShell\CommandAnalysis -Force -Recurse -ErrorAction SilentlyContinue -ErrorVariable ev | out-null;$true'
        setscript = '$true'
    }
}
```


<!--HONumber=Aug16_HO3-->


