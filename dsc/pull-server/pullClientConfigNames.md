---
ms.date: 06/12/2017
keywords: dsc,powershell,configurazione,installazione
title: Configurare un Client di Pull usando nomi di configurazione in PowerShell 5.0 e versioni successive
ms.openlocfilehash: fd038a105da7a83ecad9b571e611b65c8ec847b3
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MTE95
ms.contentlocale: it-IT
ms.lasthandoff: 12/14/2018
ms.locfileid: "53401788"
---
# <a name="set-up-a-pull-client-using-configuration-names-in-powershell-50-and-later"></a>Configurare un Client di Pull usando nomi di configurazione in PowerShell 5.0 e versioni successive

> Si applica a: Windows PowerShell 5.0

> [!IMPORTANT]
> Il server di pull (funzionalità di Windows *servizio DSC*) è un componente supportato di Windows Server, tuttavia non si prevede di offrire nuove caratteristiche o funzionalità. È consigliabile avviare la transizione dei client gestiti ad [Automation DSC per Azure](/azure/automation/automation-dsc-getting-started) (include funzionalità superiori al server di pull in Windows Server) o a una delle soluzioni della community riportate [qui](pullserver.md#community-solutions-for-pull-service).

Prima di configurare un client di pull, è necessario configurare un server di pull. Anche se quest'ordine non sia obbligatorio, consente la risoluzione dei problemi e consente di assicurarsi che la registrazione è riuscita. Per configurare un server di pull, è possibile usare le guide seguenti:

- [Configurare un server di pull SMB DSC](pullServerSmb.md)
- [Configurare un server di pull HTTP DSC](pullServer.md)

Ogni nodo di destinazione può essere configurato per scaricare le configurazioni, risorse e anche segnalare lo stato. Le sezioni seguenti illustrano come configurare un client di pull con una condivisione SMB o HTTP Server di Pull DSC. Quando Gestione configurazione locale del nodo viene aggiornato, ti contatterà per il percorso configurato per scaricare eventuali configurazioni assegnate. Se tutte le risorse necessarie non sono presenti nel nodo, verrà automaticamente scaricato li dal percorso configurato. Se il nodo è configurato con un [Server di Report](reportServer.md), quindi segnala lo stato dell'operazione.

> **Nota**: Questo argomento si applica a PowerShell 5.0.
Per informazioni sulla configurazione di un client di pull in PowerShell 4.0, vedere [configurare un client di pull usando un ID configurazione in PowerShell 4.0](pullClientConfigID4.md)

## <a name="configure-the-pull-client-lcm"></a>Configurare il client di pull Gestione configurazione locale

L'esecuzione di uno degli esempi seguenti viene creata una nuova cartella di output denominata **PullClientConfigName** e inserisce un file MOF di metaconfigurazione esiste. In questo caso, il file MOF di metaconfigurazione sarà denominato `localhost.meta.mof`.

Per applicare la configurazione, chiamare il cmdlet **Set-DscLocalConfigurationManager**, con il valore di **Path** impostato sul percorso del file MOF di metaconfigurazione. Ad esempio:

```powershell
Set-DSCLocalConfigurationManager –ComputerName localhost –Path .\PullClientConfigName –Verbose.
```

## <a name="configuration-name"></a>Nome della configurazione

Gli esempi seguenti set di **ConfigurationName** proprietà di Gestione configurazione locale per il nome di una configurazione compilata in precedenza, creato per questo scopo. Il **ConfigurationName** viene usato Gestione configurazione locale per trovare la configurazione appropriata nel server di pull. Il file MOF di configurazione nel server di pull deve essere denominato `<ConfigurationName>.mof`, in questo caso, "ClientConfig.mof". Per altre informazioni, vedere [pubblicare le configurazioni a un Server di Pull (v4/v5)](publishConfigs.md).

## <a name="set-up-a-pull-client-to-download-configurations"></a>Configurare un Client di Pull per scaricare le configurazioni

Ogni client deve essere configurato **Pull** modalità e fornire l'url di server di pull in cui la configurazione viene archiviata. A tale scopo, è necessario configurare Gestione configurazione locale con le informazioni richieste. Per configurare Gestione configurazione locale, è necessario creare un tipo speciale di configurazione usando l'attributo **DSCLocalConfigurationManager**. Per altre informazioni sulla configurazione di Gestione configurazione locale, vedere [Configurazione di Gestione configurazione locale](../managing-nodes/metaConfig.md).

Lo script seguente configura Gestione configurazione locale per il pull delle configurazioni da un server denominato "CONTOSO-PullSrv".

- Nello script il blocco **ConfigurationRepositoryWeb** definisce il server di pull. La proprietà **ServerURL** specifica l'endpoint per il server di pull.

- La proprietà **RegistrationKey** è una chiave condivisa tra tutti i nodi client per un server di pull e il server di pull stesso. Lo stesso valore viene archiviato in un file nel server di pull.
  > **Nota**: Le chiavi di registrazione funzionano solo con **web** i server di pull. Con un server di pull **SMB** è necessario usare **ConfigurationID**.
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

## <a name="set-up-a-pull-client-to-download-resources"></a>Configurare un Client di Pull per scaricare le risorse

Se si specifica solo un **ConfigurationRepositoryWeb** oppure **ConfigurationRepositoryShare** nella configurazione di Gestione configurazione locale (come nell'esempio precedente), il client di pull effettuerà il pull delle risorse da parte dello stesso posizione in cui sono archiviati i file "MOF". È anche possibile specificare percorsi diversi in cui i client possono scaricare le risorse. Per specificare un server delle risorse, usare un blocco **ResourceRepositoryWeb** (per un server di pull Web) o **ResourceRepositoryShare** (per un server di pull SMB).

Nell'esempio seguente viene illustrata una metaconfigurazione che configura un client di scaricare le configurazioni da un Server di Pull e le risorse da una condivisione SMB.

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

## <a name="set-up-a-pull-client-to-report-status"></a>Configurare un Client di Pull per segnalare lo stato

È possibile usare un singolo server di pull per le configurazioni, risorse e i report. Creazione di report non è configurato per i client per impostazione predefinita. Per configurare un client per segnalare lo stato, è necessario creare un **ReportRepositoryWeb** blocco. Nell'esempio seguente viene illustrata una metaconfigurazione che configura un client per il pull di configurazioni e risorse e per l'invio di dati di report a un singolo server di pull.

> [!NOTE]
> Un server di report non può essere una condivisione SMB.

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
