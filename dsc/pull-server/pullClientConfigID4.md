---
ms.date: 12/12/2018
keywords: dsc,powershell,configurazione,installazione
title: Configurare un Client di Pull usando gli ID di configurazione in PowerShell 4.0
ms.openlocfilehash: 9adc767e91ff19d373c122a0d493e7b8703d5476
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MTE95
ms.contentlocale: it-IT
ms.lasthandoff: 02/03/2019
ms.locfileid: "55680592"
---
# <a name="set-up-a-pull-client-using-configuration-ids-in-powershell-40"></a>Configurare un Client di Pull usando gli ID di configurazione in PowerShell 4.0

>Si applica a: Windows PowerShell 4.0, Windows PowerShell 5.0

> [!IMPORTANT]
> Il server di pull (funzionalità di Windows *servizio DSC*) è un componente supportato di Windows Server, tuttavia non si prevede di offrire nuove caratteristiche o funzionalità. È consigliabile avviare la transizione dei client gestiti ad [Automation DSC per Azure](/azure/automation/automation-dsc-getting-started) (include funzionalità superiori al server di pull in Windows Server) o a una delle soluzioni della community riportate [qui](pullserver.md#community-solutions-for-pull-service).

Prima di configurare un client di pull, è necessario configurare un server di pull. Anche se quest'ordine non sia obbligatorio, consente la risoluzione dei problemi e consente di assicurarsi che la registrazione è riuscita. Per configurare un server di pull, è possibile usare le guide seguenti:

- [Configurare un server di pull SMB DSC](pullServerSmb.md)
- [Configurare un server di pull HTTP DSC](pullServer.md)

Ogni nodo di destinazione può essere configurato per scaricare le configurazioni, risorse e anche segnalare lo stato. Le sezioni seguenti illustrano come configurare un client di pull con una condivisione SMB o HTTP Server di Pull DSC. Quando Gestione configurazione locale del nodo viene aggiornato, ti contatterà per il percorso configurato per scaricare eventuali configurazioni assegnate. Se tutte le risorse necessarie non sono presenti nel nodo, verrà automaticamente scaricato li dal percorso configurato. Se il nodo è configurato con un [Server di Report](reportServer.md), quindi segnala lo stato dell'operazione.

## <a name="configure-the-pull-client-lcm"></a>Configurare il client di pull Gestione configurazione locale

L'esecuzione di uno degli esempi seguenti viene creata una nuova cartella di output denominata **PullClientConfigID** e inserisce un file MOF di metaconfigurazione esiste. In questo caso, il file MOF di metaconfigurazione sarà denominato `localhost.meta.mof`.

Per applicare la configurazione, chiamare il cmdlet **Set-DscLocalConfigurationManager**, con il valore di **Path** impostato sul percorso del file MOF di metaconfigurazione. Ad esempio:

```powershell
Set-DSCLocalConfigurationManager –ComputerName localhost –Path .\PullClientConfigId –Verbose.
```

## <a name="configuration-id"></a>ID configurazione

Gli esempi seguenti set di **ConfigurationID** proprietà di Gestione configurazione locale per un **Guid** che fosse stato creato in precedenza per questo scopo. Il valore di **ConfigurationID** viene usato da Gestione configurazione locale per trovare la configurazione appropriata nel server di pull. Il file MOF di configurazione nel server di pull deve essere denominato `ConfigurationID.mof`, dove *ConfigurationID* è il valore della proprietà **ConfigurationID** di Gestione configurazione locale del nodo di destinazione. Per altre informazioni, vedere [pubblicare le configurazioni a un Server di Pull (v4/v5)](publishConfigs.md).

È possibile creare uno casuale **Guid** usando l'esempio seguente.

```powershell
[System.Guid]::NewGuid()
```

## <a name="set-up-a-pull-client-to-download-configurations"></a>Configurare un Client di Pull per scaricare le configurazioni

Ogni client deve essere configurato **Pull** modalità e fornire l'url di server di pull in cui la configurazione viene archiviata. A tale scopo, è necessario configurare Gestione configurazione locale con le informazioni richieste. Per configurare Gestione configurazione locale, si crea un tipo speciale di configurazione, con un **LocalConfigurationManager** blocco. Per altre informazioni sulla configurazione di Gestione configurazione locale, vedere [Configurazione di Gestione configurazione locale](../managing-nodes/metaConfig4.md).

## <a name="http-dsc-pull-server"></a>Server di Pull DSC HTTP

Se il server di pull è configurato come un servizio web, si imposta la **DownloadManagerName** al **WebDownloadManager**. Il **WebDownloadManager** richiede la specifica di un **ServerUrl** per il **DownloadManagerCustomData** chiave. È anche possibile specificare un valore per **AllowUnsecureConnection**, come illustrato nell'esempio riportato di seguito. Lo script seguente configura Gestione configurazione locale per il pull delle configurazioni da un server denominato "PullServer".

```powershell
Configuration PullClientConfigId
{
    LocalConfigurationManager
    {
        ConfigurationID = "1C707B86-EF8E-4C29-B7C1-34DA2190AE24";
        RefreshMode = "PULL";
        DownloadManagerName = "WebDownloadManager";
        RebootNodeIfNeeded = $true;
        RefreshFrequencyMins = 30;
        ConfigurationModeFrequencyMins = 30;
        ConfigurationMode = "ApplyAndAutoCorrect";
        DownloadManagerCustomData = @{ServerUrl = "http://PullServer:8080/PSDSCPullServer/PSDSCPullServer.svc"; AllowUnsecureConnection = “TRUE”}
    }
}
PullClientConfigId -Output "."
```

## <a name="smb-share"></a>SMB Share

Se il server di pull è configurato come una condivisione file SMB, piuttosto che un servizio web, si imposta la **DownloadManagerName** al **DscFileDownloadManager** anziché il **WebDownLoadManager**. Il **DscFileDownloadManager** richiede la specifica di un **SourcePath** proprietà nel **DownloadManagerCustomData**. Lo script seguente configura Gestione configurazione locale per il pull da una condivisione SMB denominata "SmbDscShare" su un server chiamato "CONTOSO-SERVER".

```powershell
Configuration PullClientConfigId
{
    LocalConfigurationManager
    {
        ConfigurationID = "1C707B86-EF8E-4C29-B7C1-34DA2190AE24";
        RefreshMode = "PULL";
        DownloadManagerName = "DscFileDownloadManager";
        RebootNodeIfNeeded = $true;
        RefreshFrequencyMins = 30;
        ConfigurationModeFrequencyMins = 30;
        ConfigurationMode = "ApplyAndAutoCorrect";
        DownloadManagerCustomData = @{ServerUrl = "\\CONTOSO-SERVER\SmbDscShare"}
    }
}
PullClientConfigId -Output "."
```

## <a name="next-steps"></a>Passaggi successivi

Dopo aver configurato il client di pull, è possibile utilizzare le guide seguenti per eseguire i passaggi successivi:

- [Pubblicare le configurazioni in un server di pull (v4/v5)](publishConfigs.md)
- [Creare un pacchetto e caricare le risorse in un server di pull (v4)](package-upload-resources.md)

## <a name="see-also"></a>Vedere anche

- [Configurare un server di pull web DSC](pullServer.md)
- [Configurare un server di pull SMB DSC](pullServerSMB.md)
