---
ms.date: 10/11/2017
ms.topic: conceptual
keywords: dsc,powershell,configurazione,installazione
title: Configurazione di Gestione configurazione locale
ms.openlocfilehash: d5a2584b23abd8eb0f1359bc452d16c7380dbaac
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/09/2018
---
# <a name="configuring-the-local-configuration-manager"></a>Configurazione di Gestione configurazione locale

> Si applica a: Windows PowerShell 5.0

Gestione configurazione locale è il motore di DSC (Desired State Configuration).
Gestione configurazione locale viene eseguito in ogni nodo di destinazione ed è responsabile dell'analisi e dell'applicazione delle configurazioni inviate al nodo.
È anche responsabile di alcuni altri aspetti di DSC, tra cui i seguenti.

- Determinazione della modalità di aggiornamento (push o pull).
- Definizione della frequenza in cui un nodo effettua il pull delle configurazioni e le applica.
- Associazione del nodo al servizio di pull.
- Definizione di configurazioni parziali.

Per configurare Gestione configurazione locale in modo da specificare ognuno di questi comportamenti, è necessario usare un tipo speciale di configurazione.
Le sezioni seguenti descrivono come configurare Gestione configurazione locale.

In Windows PowerShell 5.0 sono state introdotte nuove impostazioni per la gestione di Gestione configurazione locale.
Per informazioni sulla configurazione di Gestione configurazione locale in Windows PowerShell 4.0, vedere [Configurazione di Gestione configurazione locale nelle versioni precedenti di Windows PowerShell](metaconfig4.md).

## <a name="writing-and-enacting-an-lcm-configuration"></a>Scrittura e applicazione di una configurazione di Gestione configurazione locale

Per configurare Gestione configurazione locale, è necessario creare ed eseguire un tipo speciale di configurazione che applica le impostazioni di Gestione configurazione locale.
Per specificare una configurazione di Gestione configurazione locale, usare l'attributo DscLocalConfigurationManager.
Di seguito viene mostrata una semplice configurazione che imposta Gestione configurazione locale in modalità push.

```powershell
[DSCLocalConfigurationManager()]
configuration LCMConfig
{
    Node localhost
    {
        Settings
        {
            RefreshMode = 'Push'
        }
    }
}
```

Il processo di applicazione delle impostazioni di Gestione configurazione locale è simile all'applicazione di una configurazione DSC.
Sarà necessario creare una configurazione di Gestione configurazione locale, compilarla in un file MOF e applicarla al nodo.
Diversamente dalle configurazioni DSC, non è possibile applicare una configurazione di Gestione configurazione locale chiamando il cmdlet [Start-DscConfiguration](https://technet.microsoft.com/en-us/library/dn521623.aspx).
Occorre invece chiamare [Set-DscLocalConfigurationManager](https://technet.microsoft.com/en-us/library/dn521621.aspx), specificando il percorso del file MOF di configurazione di Gestione configurazione locale come parametro.
Dopo aver applicato la configurazione di Gestione configurazione locale, è possibile visualizzare le proprietà di Gestione configurazione locale chiamando il cmdlet [Get-DscLocalConfigurationManager](https://technet.microsoft.com/en-us/library/dn407378.aspx).

Una configurazione di Gestione configurazione locale può contenere blocchi solo per un set limitato di risorse.
Nell'esempio precedente l'unica risorsa chiamata è **Settings**.
Le altre risorse disponibili sono le seguenti:

* **ConfigurationRepositoryWeb**: specifica un servizio di pull HTTP per le configurazioni.
* **ConfigurationRepositoryShare**: specifica una condivisione SMB per le configurazioni.
* **ResourceRepositoryWeb**: specifica un servizio di pull HTTP per i moduli.
* **ResourceRepositoryShare**: specifica una condivisione SMB per i moduli.
* **ReportServerWeb**: specifica un servizio di pull HTTP a cui inviare i report.
* **PartialConfiguration**: fornisce dati per consentire configurazioni parziali.

## <a name="basic-settings"></a>Impostazioni di base

Oltre a specificare endpoint/percorsi del servizio di pull e le configurazioni parziali, tutte le altre proprietà di Gestione configurazione locale vengono configurate in un blocco **Settings**.
In un blocco **Settings** sono disponibili le proprietà seguenti.

|  Proprietà  |  Tipo  |  Description   |
|----------- |------- |--------------- |
| ActionAfterReboot| string| Specifica che cosa avviene dopo un riavvio durante l'applicazione di una configurazione. I valori possibili sono __"ContinueConfiguration"__ e __"StopConfiguration"__. <ul><li> __ContinueConfiguration__: continua ad applicare la configurazione corrente dopo il riavvio del computer. Questo è il valore predefinito</li><li>__StopConfiguration__: arresta la configurazione corrente dopo il riavvio del computer.</li></ul>|
| AllowModuleOverwrite| bool| __$TRUE__ se le nuove configurazioni scaricate dal servizio di pull possono sovrascrivere quelle meno recenti nel nodo di destinazione. In caso contrario, $FALSE.|
| CertificateID| string| Identificazione personale di un certificato usato per credenziali protette passate in una configurazione. Per altre informazioni, vedere [Protezione delle credenziali in Windows PowerShell DSC (Desired State Configuration)](http://blogs.msdn.com/b/powershell/archive/2014/01/31/want-to-secure-credentials-in-windows-powershell-desired-state-configuration.aspx). <br> __Nota:__ questo aspetto viene gestito automaticamente se si usa il servizio di pull di Automation DSC di Azure.|
| ConfigurationDownloadManagers| CimInstance[]| Obsoleto. Usare blocchi __ConfigurationRepositoryWeb__ e __ConfigurationRepositoryShare__ per definire gli endpoint del servizio di pull di configurazione.|
| ConfigurationID| string| Per compatibilità con le versioni precedenti del servizio di pull. GUID che identifica il file di configurazione da ottenere da un servizio di pull. Il nodo effettuerà il pull delle configurazioni nel servizio di pull se il nome del file MOF di configurazione è ConfigurationID.mof.<br> __Nota__: se si imposta questa proprietà, la registrazione del nodo in un servizio di pull con __RegistrationKey__ non funziona. Per altre informazioni, vedere [Configurazione di un client di pull con nomi di configurazione](pullClientConfigNames.md).|
| ConfigurationMode| string | Specifica il modo in cui Gestione configurazione locale applica effettivamente la configurazione ai nodi di destinazione. I valori possibili sono __"ApplyOnly"__,__"ApplyAndMonitor"__ e __"ApplyAndAutoCorrect"__. <ul><li>__ApplyOnly__: DSC applica la configurazione e non esegue altre operazioni, tranne nei casi in cui viene effettuato il push di una nuova configurazione nel nodo di destinazione o viene effettuato il pull di una nuova configurazione da un servizio. Dopo l'applicazione iniziale di una nuova configurazione, DSC non verifica l'eventuale desincronizzazione da uno stato configurato in precedenza. Si noti che DSC tenterà di applicare la configurazione fino al suo esito positivo prima che __ApplyOnly__ abbia effetto. </li><li> __ApplyAndMonitor__: questo è il valore predefinito. Gestione configurazione locale applica tutte le nuove configurazioni. Se dopo l'applicazione iniziale di una nuova configurazione il nodo di destinazione non è sincronizzato con lo stato desiderato, DSC segnala la discrepanza nei log. Si noti che DSC tenterà di applicare la configurazione fino al suo esito positivo prima che __ApplyAndMonitor__ abbia effetto.</li><li>__ApplyAndAutoCorrect__: DSC applica le nuove configurazioni. Se dopo l'applicazione iniziale di una nuova configurazione il nodo di destinazione non è sincronizzato con lo stato desiderato, DSC segnala la discrepanza nei log e quindi riapplica la configurazione corrente.</li></ul>|
| ConfigurationModeFrequencyMins| UInt32| Frequenza, in minuti, in base alla quale la configurazione corrente viene controllata e applicata. Questa proprietà viene ignorata se la proprietà ConfigurationMode è impostata su ApplyOnly. Il valore predefinito è 15.|
| DebugMode| string| I valori possibili sono __None__, __ForceModuleImport__ e __All__. <ul><li>Impostare questa proprietà su __None__ per usare risorse memorizzate nella cache. Questa è l'impostazione predefinita e deve essere usata negli scenari di produzione.</li><li>L'impostazione __ForceModuleImport__ fa sì che Gestione configurazione locale ricarichi tutti i moduli di risorse DSC, anche se sono stati caricati e memorizzati nella cache in precedenza. Questa impostazione ha impatto sulle prestazioni delle operazioni di DSC, perché ogni modulo viene ricaricato al momento dell'uso. Questo valore viene in genere usato durante il debug di una risorsa.</li><li>In questa versione __All__ equivale a __ForceModuleImport__.</li></ul> |
| RebootNodeIfNeeded| bool| Impostare questa proprietà su __$true__ per riavviare automaticamente il nodo dopo aver applicato una configurazione che richiede il riavvio. In caso contrario, sarà necessario riavviare manualmente il nodo per qualsiasi configurazione che lo richiede. Il valore predefinito è __$false__. Per usare questa impostazione quando una condizione di ravvio viene applicata da un componente diverso da DSC (ad esempio Windows Installer), combinare questa impostazione con il modulo [xPendingReboot](https://github.com/powershell/xpendingreboot).|
| RefreshMode| string| Specifica il modo in cui Gestione configurazione locale ottiene le configurazioni. I valori possibili sono __"Disabled"__, __"Push"__ e __"Pull"__. <ul><li>__Disabled__: le configurazioni DSC sono disabilitate per questo nodo.</li><li> __Push__: le configurazioni vengono avviate chiamando il cmdlet [Start-DscConfiguration](https://technet.microsoft.com/en-us/library/dn521623.aspx). La configurazione viene applicata immediatamente al nodo. Questo è il valore predefinito.</li><li>__Pull__: il nodo è configurato per controllare regolarmente le configurazioni da un servizio di pull o un percorso SMB. Se questa proprietà è impostata su __Pull__, è necessario specificare un percorso HTTP (servizio) o SMB (condivisione) in un blocco __ConfigurationRepositoryWeb__ o __ConfigurationRepositoryShare__.</li></ul>|
| RefreshFrequencyMins| UInt32| Intervallo di tempo, in minuti, rispettato da Gestione configurazione locale per il controllo di un servizio di pull per ottenere configurazioni aggiornate. Questo valore viene ignorato se Gestione configurazione locale non è configurato in modalità pull. Il valore predefinito è 30.|
| ReportManagers| CimInstance[]| Obsoleto. Usare blocchi __ReportServerWeb__ per definire un endpoint per inviare dati di report a un servizio di pull.|
| ResourceModuleManagers| CimInstance[]| Obsoleto. Usare blocchi __ResourceRepositoryWeb__ e __ResourceRepositoryShare__ per definire rispettivamente gli endpoint HTTP o i percorsi SMB del servizio di pull.|
| PartialConfigurations| CimInstance| Non implementata. Non utilizzare.|
| StatusRetentionTimeInDays | UInt32| Numero di giorni per i quali Gestione configurazione locale mantiene lo stato della configurazione corrente.|

## <a name="pull-service"></a>Servizio di pull

La configurazione di Gestione configurazione locale supporta la definizione dei tipi seguenti di endpoint del servizio di pull:

- **Server di configurazione**: repository per le configurazioni DSC. Per definire i server di configurazione, usare blocchi **ConfigurationRepositoryWeb** (per server basati sul Web) e **ConfigurationRepositoryShare** (per server basati su SMB).
- **Server di risorse**: repository per risorse DSC, incluse in pacchetti come moduli di PowerShell. Per definire i server di risorse, usare blocchi **ResourceRepositoryWeb** (per server basati sul Web) e **ResourceRepositoryShare** (per server basati su SMB).
- **Server di report**: servizio a cui DSC invia dati di report. Per definire i server di report, usare blocchi **ReportServerWeb**. Un server di report deve essere un servizio Web.

Per altri dettagli sul servizio di pull, vedere [Servizio di pull DSC (Desired State Configuration)](pullServer.md).

## <a name="configuration-server-blocks"></a>Blocchi per i server di configurazione

Per definire un server di configurazione basato sul Web, creare un blocco **ConfigurationRepositoryWeb**.
Un blocco **ConfigurationRepositoryWeb** definisce le proprietà seguenti.

|Proprietà|Tipo|Description|
|---|---|---|
|AllowUnsecureConnection|bool|Impostare questa proprietà su **$TRUE** per consentire le connessioni dal nodo al server senza autenticazione. Impostarla su **$FALSE** per richiedere l'autenticazione.|
|CertificateID|string|Identificazione personale usata per eseguire l'autenticazione al server.|
|ConfigurationNames|String[]|Matrice di nomi di configurazioni di cui il nodo di destinazione deve effettuare il pull. Vengono usati solo se il nodo è registrato nel servizio di pull con **RegistrationKey**. Per altre informazioni, vedere [Configurazione di un client di pull con nomi di configurazione](pullClientConfigNames.md).|
|RegistrationKey|string|GUID che registra il nodo nel servizio di pull. Per altre informazioni, vedere [Configurazione di un client di pull con nomi di configurazione](pullClientConfigNames.md).|
|ServerURL|string|URL del servizio di configurazione.|

Per uno script di esempio per semplificare la configurazione del valore ConfigurationRepositoryWeb per i nodi locali, vedere [Generating DSC metaconfigurations](https://docs.microsoft.com/en-us/azure/automation/automation-dsc-onboarding#generating-dsc-metaconfigurations) (Generazione di metaconfigurazioni DSC)

Per definire un server di configurazione basato su SMB, creare un blocco **ConfigurationRepositoryShare**.
Un blocco **ConfigurationRepositoryShare** definisce le proprietà seguenti.

|Proprietà|Tipo|Description|
|---|---|---|
|Credential|MSFT_Credential|Credenziale usata per l'autenticazione nella condivisione SMB.|
|SourcePath|string|Percorso della condivisione SMB.|

## <a name="resource-server-blocks"></a>Blocchi per i server di risorse

Per definire un server di risorse basato sul Web, creare un blocco **ResourceRepositoryWeb**.
Un blocco **ResourceRepositoryWeb** definisce le proprietà seguenti.

|Proprietà|Tipo|Description|
|---|---|---|
|AllowUnsecureConnection|bool|Impostare questa proprietà su **$TRUE** per consentire le connessioni dal nodo al server senza autenticazione. Impostarla su **$FALSE** per richiedere l'autenticazione.|
|CertificateID|string|Identificazione personale usata per eseguire l'autenticazione al server.|
|RegistrationKey|string|GUID che identifica il nodo per il servizio di pull.|
|ServerURL|string|URL del server di configurazione.|

Per uno script di esempio per semplificare la configurazione del valore ResourceRepositoryWeb per i nodi locali, vedere [Generating DSC metaconfigurations](https://docs.microsoft.com/en-us/azure/automation/automation-dsc-onboarding#generating-dsc-metaconfigurations) (Generazione di metaconfigurazioni DSC)

Per definire un server di risorse basato su SMB, creare un blocco **ResourceRepositoryShare**.
Un blocco **ResourceRepositoryShare** definisce le proprietà seguenti.

|Proprietà|Tipo|Description|
|---|---|---|
|Credential|MSFT_Credential|Credenziale usata per l'autenticazione nella condivisione SMB. Per un esempio di passaggio di credenziali, vedere [Configurazione di un server di pull SMB DSC](pullServerSMB.md)|
|SourcePath|string|Percorso della condivisione SMB.|

## <a name="report-server-blocks"></a>Blocchi per i server di report

Per definire un server di report, creare un blocco **ReportServerWeb**.
Il ruolo del server di report non è compatibile con il servizio di pull basato su SMB.
Un blocco **ReportServerWeb** definisce le proprietà seguenti.

|Proprietà|Tipo|Description|
|---|---|---|
|AllowUnsecureConnection|bool|Impostare questa proprietà su **$TRUE** per consentire le connessioni dal nodo al server senza autenticazione. Impostarla su **$FALSE** per richiedere l'autenticazione.|
|CertificateID|string|Identificazione personale usata per eseguire l'autenticazione al server.|
|RegistrationKey|string|GUID che identifica il nodo per il servizio di pull.|
|ServerURL|string|URL del server di configurazione.|

Per uno script di esempio per semplificare la configurazione del valore ReportServerWeb per i nodi locali, vedere [Generating DSC metaconfigurations](https://docs.microsoft.com/en-us/azure/automation/automation-dsc-onboarding#generating-dsc-metaconfigurations) (Generazione di metaconfigurazioni DSC)

## <a name="partial-configurations"></a>Configurazioni parziali

Per definire una configurazione parziale, creare un blocco **PartialConfiguration**.
Per altre informazioni sulle configurazioni parziali, vedere [Configurazioni parziali DSC](partialConfigs.md).
Un blocco **PartialConfiguration** definisce le proprietà seguenti.

|Proprietà|Tipo|Description|
|---|---|---|
|ConfigurationSource|string[]|Matrice di nomi di server di configurazione definiti in precedenza in blocchi **ConfigurationRepositoryWeb** e **ConfigurationRepositoryShare** da cui viene effettuato il pull della configurazione parziale.|
|DependsOn|string{}|Elenco di nomi di altre configurazioni che devono essere completate prima di poter applicare questa configurazione parziale.|
|Description|string|Testo usato per descrivere la configurazione parziale.|
|ExclusiveResources|string[]|Matrice di risorse esclusive per questa configurazione parziale.|
|RefreshMode|string|Specifica il modo in cui Gestione configurazione locale (LCM) ottiene la configurazione parziale. I valori possibili sono __"Disabled"__, __"Push"__ e __"Pull"__. <ul><li>__Disabled__: la configurazione parziale è disabilitata.</li><li> __Push__: viene effettuato il push della configurazione parziale nel nodo chiamando il cmdlet [Publish-DscConfiguration](https://technet.microsoft.com/en-us/library/mt517875.aspx). Dopo il push o il pull di tutte le configurazioni parziali per il nodo da un servizio, la configurazione può essere avviata chiamando `Start-DscConfiguration –UseExisting`. Questo è il valore predefinito.</li><li>__Pull__: il nodo è configurato in modo da controllare regolarmente la configurazione parziale da un servizio di pull. Se questa proprietà è impostata su __Pull__, è necessario specificare un servizio di pull in una proprietà __ConfigurationSource__. Per altre informazioni sul servizio di pull di Automazione di Azure, vedere [Panoramica della piattaforma DSC di Automazione di Azure](https://docs.microsoft.com/en-us/azure/automation/automation-dsc-overview).</li></ul>|
|ResourceModuleSource|string[]|Matrice di nomi dei server di risorse da cui scaricare le risorse necessarie per questa configurazione parziale. Questi nomi devono fare riferimento agli endpoint del servizio definiti in precedenza in blocchi **ResourceRepositoryWeb** e **ResourceRepositoryShare**.|

__Nota:__ le configurazioni parziali sono supportate con Automation DSC di Azure, ma è possibile eseguire il pull di una sola configurazione da ogni account di automazione per ogni nodo.

## <a name="see-also"></a>Vedere anche

### <a name="concepts"></a>Concetti
[Panoramica di DSC (Desired State Configuration)](overview.md)

[Caricamento di computer per la gestione con Automation DSC per Azure](https://docs.microsoft.com/en-us/azure/automation/automation-dsc-getting-started)

### <a name="other-resources"></a>Risorse aggiuntive

[Set-DscLocalConfigurationManager](https://technet.microsoft.com/en-us/library/dn521621.aspx)

[Configurazione di un client di pull con nomi di configurazione](pullClientConfigNames.md)