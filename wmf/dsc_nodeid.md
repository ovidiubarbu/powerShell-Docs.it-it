# Separazione degli ID per nodi e configurazioni

## Panoramica

Per garantire un'esperienza più flessibile e semplificata durante l'uso di DSC in modalità Pull, in questa versione sono state aggiunte numerose funzionalità. Queste funzionalità sono progettate in modo da offrire la flessibilità necessaria per configurare e distribuire le configurazioni su più nodi, offrendo allo stesso tempo la possibilità di tenere traccia dello stato e di creare report di informazioni per ogni nodo singolarmente. Queste funzionalità sono le seguenti:

* Un nome di configurazione che identifica la configurazione per un computer. Questo nome può essere condiviso da più nodi di destinazione 
* Un ID di agente che identifica in modo univoco un singolo nodo
* Un passaggio di registrazione che si verifica solo la prima volta che un nodo di destinazione si connette a un server di pull

**Nota:** queste caratteristiche e funzionalità sono state aggiunte e non sostituiscono i concetti e le funzionalità esistenti relativi al pull. È possibile usare queste nuove funzionalità o quelle meno recenti con il nuovo server di pull incluso in questa versione.

## ID dell'agente

Questa funzionalità è destinata agli utenti che non vogliono configurare e gestire identificatori univoci per ogni nodo di destinazione. Ora non è più necessario tenere traccia dei GUID. DSC genera automaticamente un ID di agente che viene usato durante la comunicazione con il server di pull. Questo ID viene usato dal server di pull per identificare in modo univoco tutte le informazioni con un determinato nodo. Significa anche che non è necessario configurare ogni nodo di destinazione con una metaconfigurazione univoca contenente un ID univoco, pertanto una singola metaconfigurazione può essere usata da molti nodi di destinazione, pur mantenendo l'identità univoca di ogni nodo. 

## Nome della configurazione

Il nome della configurazione è un nome descrittivo che definisce il nome della configurazione che verrà applicata da un nodo di destinazione. Le modifiche associate a questo aspetto sono le seguenti:  

### Uso di nomi descrittivi

Si può usare qualsiasi stringa. Non è necessario che abbia il formato di un GUID, quindi una configurazione usata per SQL Server può essere semplicemente denominata 'SQL_Server'. In questo modo è molto più semplice identificare gli scopi di una determinata configurazione.

### Assegnazione

La configurazione assegnata a un nodo di destinazione viene gestita in modo centralizzato nel server di pull. L'avvio può essere gestito definendo la proprietà ConfigurationName nella metaconfigurazione, ma queste informazioni vengono usate solo durante la registrazione. Dopo la registrazione, il server indica al nodo di destinazione quale configurazione riceverà. Per il server di pull locale, questo mapping tra le configurazioni e i nodi di destinazione può essere eseguito solo durante la registrazione, ma in Automazione di Azure queste modifiche possono essere facilmente eseguite nell'interfaccia utente o tramite i cmdlet. Per modificare la configurazione assegnata a un nodo di destinazione per il server di pull locale, è possibile eseguire nuovamente la registrazione.

### Configurazioni multiple/parziali

Se a un nodo di destinazione vengono assegnati più nomi di configurazione, essi verranno gestiti come configurazioni parziali. Perché tutto ciò funzioni, la metaconfigurazione nel nodo di destinazione deve essere configurata per accettare configurazioni parziali. **Nota:** questa funzionalità è supportata solo nel server di pull locale. Automazione di Azure non supporta le configurazioni parziali.

## Registrazione

Poiché i nomi di configurazione non sono più GUID, ma nomi descrittivi, chiunque può indovinarli. Per limitare i problemi di sicurezza intrinseci, è stato aggiunto un passaggio di registrazione prima che un nodo possa iniziare a richiedere configurazioni da un server. Un nodo si registra nel server di pull con un segreto condiviso (già noto sia per il nodo che per il server) e, facoltativamente, con il nome della configurazione che richiederà. Il segreto condiviso non deve essere univoco per ogni computer. Presupposto: il segreto condiviso è un identificatore difficile da indovinare, come un GUID. Il segreto condiviso viene definito dalla proprietà **RegistrationKey** nella metaconfigurazione del nodo di destinazione.

### Metaconfigurazione di esempio

```powershell
[DscLocalConfigurationManager()]
Configuration SampleMetaConfig
{
    Settings
    {
        RefreshMode = "PULL";
        AllowModuleOverwrite = $true;
        RebootNodeIfNeeded = $true;
        ConfigurationModeFrequencyMins = 60;
    }

    ConfigurationRepositoryWeb ConfigurationManager
    {
        ServerURL = “https://PullServerMachine:8080/psdscpullserver.svc”
        RegistrationKey = "140a952b-b9d6-406b-b416-e0f759c9c0e4"
        ConfigurationNames = @(“WebRole”)
    }
}

SampleMetaConfig
```

Il valore di RegistrationKey deve essere definito nel server di pull. A questo scopo, durante la configurazione del server di pull creare un file di testo con il nome **RegistrationKeys.txt** in una posizione specifica e quindi impostare questo percorso nel file web.config del server di pull, come illustrato di seguito.  

```XML
<add key="ConfigurationPath" value="C:\Program Files\WindowsPowerShell\DscService\Configuration">

<add key="ModulePath" value="C:\Program Files\WindowsPowerShell\DscService\Modules">

<add key="RegistrationKeyPath" value="C:\Program Files\WindowsPowerShell\DscService">
```

Usare l'ultima versione della risorsa DSC xDSCWebService per la distribuzione completa di un server di pull locale da usare con questa funzionalità. Vedere [Configurazione di esempio](https://github.com/grayzu/PSSummitEU2015/blob/master/PullServer/02%20-%20PullServer%20Config.ps1) per una configurazione completa.

**Nota:** questa funzionalità non è supportata quando il server di pull è configurato per essere una condivisione file. È supportata solo per il server di pull basato sul Web.<!--HONumber=Mar16_HO2-->
