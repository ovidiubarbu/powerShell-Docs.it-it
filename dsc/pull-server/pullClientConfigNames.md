---
ms.date: 06/12/2017
keywords: dsc,powershell,configurazione,installazione
title: Configurare un client di pull usando nomi di configurazione in PowerShell 5.0 e versioni successive
ms.openlocfilehash: d591e2a757130ccecaf4eaf9f363f607fca82b93
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62079388"
---
# <a name="set-up-a-pull-client-using-configuration-names-in-powershell-50-and-later"></a>Configurare un client di pull usando nomi di configurazione in PowerShell 5.0 e versioni successive

> Si applica a: Windows PowerShell 5.0

> [!IMPORTANT]
> Il server di pull (funzionalità di Windows *servizio DSC*) è un componente supportato di Windows Server, tuttavia non si prevede di offrire nuove caratteristiche o funzionalità. È consigliabile avviare la transizione dei client gestiti ad [Automation DSC per Azure](/azure/automation/automation-dsc-getting-started) (include funzionalità superiori al server di pull in Windows Server) o a una delle soluzioni della community riportate [qui](pullserver.md#community-solutions-for-pull-service).

Prima di configurare un client di pull, è necessario configurare un server di pull. Anche se quest'ordine non è obbligatorio, facilita la risoluzione dei problemi e agevola la riuscita della registrazione. Per configurare un server di pull, è possibile usare le guide seguenti:

- [Configurare un server di pull SMB DSC](pullServerSmb.md)
- [Configurare un server di pull HTTP DSC](pullServer.md)

Ogni nodo di destinazione può essere configurato in modo che possa scaricare configurazioni e risorse e persino segnalare il proprio stato. Le sezioni seguenti illustrano come configurare un client di pull con una condivisione SMB o on server di pull DSC HTTP. Quando Gestione configurazione locale del nodo si aggiorna, contatta la posizione configurata per scaricare tutte le configurazioni assegnate. Se una o più risorse necessarie non sono presenti nel nodo, le scarica automaticamente dalla posizione configurata. Se il nodo è configurato con un [server di report](reportServer.md), segnala quindi lo stato dell'operazione.

> [!NOTE]
> Questo argomento si applica a PowerShell 5.0.
> Per informazioni sulla configurazione di un client di pull in PowerShell 4.0, vedere [Configurare un client di pull usando un ID configurazione in PowerShell 4.0](pullClientConfigID4.md)

## <a name="configure-the-pull-client-lcm"></a>Configurare Gestione configurazione locale del client di pull

L'esecuzione di uno degli esempi che seguono crea una nuova cartella di output denominata **PullClientConfigName** e inserisce in questa cartella un file MOF di metaconfigurazione. In questo caso, il file MOF di metaconfigurazione sarà denominato `localhost.meta.mof`.

Per applicare la configurazione, chiamare il cmdlet **Set-DscLocalConfigurationManager**, con il valore di **Path** impostato sul percorso del file MOF di metaconfigurazione. Ad esempio:

```powershell
Set-DSCLocalConfigurationManager –ComputerName localhost –Path .\PullClientConfigName –Verbose.
```

## <a name="configuration-name"></a>Nome della configurazione

Gli esempi seguenti impostano la proprietà **ConfigurationName** di Gestione configurazione locale sul nome di una configurazione compilata in precedenza, creato per questo scopo. Il valore di **ConfigurationName** viene usato da Gestione configurazione locale per trovare la configurazione appropriata nel server di pull. Il nome del file MOF di configurazione nel server di pull deve essere `<ConfigurationName>.mof`, in questo caso, "ClientConfig.mof". Per altre informazioni, vedere [Pubblicare le configurazioni in un server di pull (v4/v5)](publishConfigs.md).

## <a name="set-up-a-pull-client-to-download-configurations"></a>Configurare un client di pull per scaricare configurazioni

Ogni client deve essere configurato in modalità **Pull** e deve ricevere l'URL del server di pull in cui è archiviata la sua configurazione. A tale scopo, è necessario configurare Gestione configurazione locale con le informazioni richieste. Per configurare Gestione configurazione locale, è necessario creare un tipo speciale di configurazione usando l'attributo **DSCLocalConfigurationManager**. Per altre informazioni sulla configurazione di Gestione configurazione locale, vedere [Configurazione di Gestione configurazione locale](../managing-nodes/metaConfig.md).

Lo script seguente configura Gestione configurazione locale per il pull delle configurazioni da un server denominato "CONTOSO-PullSrv".

- Nello script il blocco **ConfigurationRepositoryWeb** definisce il server di pull. La proprietà **ServerURL** specifica l'endpoint per il server di pull.

- La proprietà **RegistrationKey** è una chiave condivisa tra tutti i nodi client per un server di pull e il server di pull stesso. Lo stesso valore viene archiviato in un file nel server di pull.
  > [!NOTE]
  > Le chiavi di registrazione funzionano solo con i server di pull **Web**. Con un server di pull **SMB** è necessario usare **ConfigurationID**.
  > Per informazioni sulla configurazione di un server di pull usando **ConfigurationID**, vedere [Configurazione di un client di pull usando un ID configurazione](pullClientConfigId.md).

- La proprietà **ConfigurationNames** è una matrice che specifica i nomi delle configurazioni per il nodo client.
  >**Nota:** se si specifica più di un valore in **ConfigurationNames**, è necessario specificare anche i blocchi **PartialConfiguration** nella configurazione.
  >Per informazioni sulle configurazioni parziali, vedere [configurazioni parziali di PowerShell DSC](partialConfigs.md).

```powershell
[DSCLocalConfigurationManager()]
configuration PullClientConfigNames
{
    Node localhost
    {
        Settings
        {
            RefreshMode = 'Pull'
            RefreshFrequencyMins = 30
            RebootNodeIfNeeded = $true
        }
        ConfigurationRepositoryWeb CONTOSO-PullSrv
        {
            ServerURL = 'https://CONTOSO-PullSrv:8080/PSDSCPullServer.svc'
            RegistrationKey = '140a952b-b9d6-406b-b416-e0f759c9c0e4'
            ConfigurationNames = @('ClientConfig')
        }
    }
}
PullClientConfigNames
```

## <a name="set-up-a-pull-client-to-download-resources"></a>Configurare un client di pull per scaricare risorse

Se si specifica solo un blocco **ConfigurationRepositoryWeb** o **ConfigurationRepositoryShare** nella configurazione di Gestione configurazione locale, come nell'esempio precedente, il client di pull eseguirà il pull delle risorse dalla stessa posizione in cui sono archiviati i file con estensione "mof". È anche possibile specificare posizioni diverse per il download delle risorse da parte dei client. Per specificare un server delle risorse, usare un blocco **ResourceRepositoryWeb** (per un server di pull Web) o **ResourceRepositoryShare** (per un server di pull SMB).

L'esempio seguente illustra una metaconfigurazione che configura un client per il download di configurazioni da un server di pull e per il download di risorse da una condivisione SMB.

```powershell
[DSCLocalConfigurationManager()]
configuration PullClientConfigNames
{
    Node localhost
    {
        Settings
        {
            RefreshMode = 'Pull'
            RefreshFrequencyMins = 30
            RebootNodeIfNeeded = $true
        }

        ConfigurationRepositoryWeb CONTOSO-PullSrv
        {
            ServerURL = 'https://CONTOSO-PullSrv:8080/PSDSCPullServer.svc'
            RegistrationKey = 'fbc6ef09-ad98-4aad-a062-92b0e0327562'
        }

        ResourceRepositoryShare SMBResources
        {
            SourcePath = '\\SMBPullServer\Resources'
        }
    }
}
PullClientConfigNames
```

## <a name="set-up-a-pull-client-to-report-status"></a>Configurare un client di pull per la segnalazione dello stato

È possibile usare un unico server di pull per le configurazioni, le risorse e i report. Per impostazione predefinita, la creazione di report non è configurata per i client. Per configurare un client per la segnalazione dello stato, è necessario creare un blocco **ReportRepositoryWeb**. Nell'esempio seguente viene illustrata una metaconfigurazione che configura un client per il pull di configurazioni e risorse e per l'invio di dati di report a un singolo server di pull.

> [!NOTE]
> Un server di report non può fungere da condivisione SMB.

```powershell
[DSCLocalConfigurationManager()]
configuration PullClientConfigNames
{
    Node localhost
    {
        Settings
        {
            RefreshMode = 'Pull'
            RefreshFrequencyMins = 30
            RebootNodeIfNeeded = $true
        }

        ConfigurationRepositoryWeb CONTOSO-PullSrv
        {
            ServerURL = 'https://CONTOSO-PullSrv:8080/PSDSCPullServer.svc'
            RegistrationKey = 'fbc6ef09-ad98-4aad-a062-92b0e0327562'
        }

        ReportServerWeb CONTOSO-PullSrv
        {
            ServerURL = 'https://CONTOSO-PullSrv:8080/PSDSCPullServer.svc'
            RegistrationKey = 'fbc6ef09-ad98-4aad-a062-92b0e0327562'
        }
    }
}
PullClientConfigNames
```

## <a name="see-also"></a>Vedere anche

* [Configurazione di un client di pull usando un ID configurazione](PullClientConfigNames.md)
* [Configurazione di un server di pull Web DSC](pullServer.md)
