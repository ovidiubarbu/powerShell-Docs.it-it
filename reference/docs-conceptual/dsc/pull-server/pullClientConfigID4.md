---
ms.date: 12/12/2018
keywords: dsc,powershell,configurazione,installazione
title: Configurare un client di pull usando ID configurazione in PowerShell 4.0
ms.openlocfilehash: 9259c624c8725f7d76f61e9ad7caa42e1bfa308c
ms.sourcegitcommit: 6545c60578f7745be015111052fd7769f8289296
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/22/2020
ms.locfileid: "71955148"
---
# <a name="set-up-a-pull-client-using-configuration-ids-in-powershell-40"></a>Configurare un client di pull usando ID configurazione in PowerShell 4.0

>Si applica a: Windows PowerShell 4.0, Windows PowerShell 5.0

> [!IMPORTANT]
> Il server di pull (funzionalità di Windows *servizio DSC*) è un componente supportato di Windows Server, tuttavia non si prevede di offrire nuove caratteristiche o funzionalità. È consigliabile avviare la transizione dei client gestiti ad [Automation DSC per Azure](/azure/automation/automation-dsc-getting-started) (include funzionalità superiori al server di pull in Windows Server) o a una delle soluzioni della community riportate [qui](pullserver.md#community-solutions-for-pull-service).

Prima di configurare un client di pull, è necessario configurare un server di pull. Anche se quest'ordine non è obbligatorio, facilita la risoluzione dei problemi e agevola la riuscita della registrazione. Per configurare un server di pull, è possibile usare le guide seguenti:

- [Configurare un server di pull SMB DSC](pullServerSmb.md)
- [Configurare un server di pull HTTP DSC](pullServer.md)

Ogni nodo di destinazione può essere configurato in modo che possa scaricare configurazioni e risorse e persino segnalare il proprio stato. Le sezioni seguenti illustrano come configurare un client di pull con una condivisione SMB o on server di pull DSC HTTP. Quando Gestione configurazione locale del nodo si aggiorna, contatta la posizione configurata per scaricare tutte le configurazioni assegnate. Se una o più risorse necessarie non sono presenti nel nodo, le scarica automaticamente dalla posizione configurata. Se il nodo è configurato con un [server di report](reportServer.md), segnala quindi lo stato dell'operazione.

## <a name="configure-the-pull-client-lcm"></a>Configurare Gestione configurazione locale del client di pull

L'esecuzione di uno degli esempi che seguono crea una nuova cartella di output denominata **PullClientConfigID** e inserisce in questa cartella un file MOF di metaconfigurazione. In questo caso, il file MOF di metaconfigurazione sarà denominato `localhost.meta.mof`.

Per applicare la configurazione, chiamare il cmdlet **Set-DscLocalConfigurationManager**, con il valore di **Path** impostato sul percorso del file MOF di metaconfigurazione. Ad esempio:

```powershell
Set-DSCLocalConfigurationManager –ComputerName localhost –Path .\PullClientConfigId –Verbose.
```

## <a name="configuration-id"></a>ID configurazione

Gli esempi che seguono impostano la proprietà **ConfigurationID** di Gestione configurazione locale su un **GUID** creato in precedenza per questo scopo. Il valore di **ConfigurationID** viene usato da Gestione configurazione locale per trovare la configurazione appropriata nel server di pull. Il file MOF di configurazione nel server di pull deve essere denominato `ConfigurationID.mof`, dove *ConfigurationID* è il valore della proprietà **ConfigurationID** di Gestione configurazione locale del nodo di destinazione. Per altre informazioni, vedere [Pubblicare le configurazioni in un server di pull (v4/v5)](publishConfigs.md).

È possibile creare un **GUID** casuale usando l'esempio seguente.

```powershell
[System.Guid]::NewGuid()
```

## <a name="set-up-a-pull-client-to-download-configurations"></a>Configurare un client di pull per scaricare configurazioni

Ogni client deve essere configurato in modalità **Pull** e deve ricevere l'URL del server di pull in cui è archiviata la sua configurazione. A tale scopo, è necessario configurare Gestione configurazione locale con le informazioni richieste. Per configurare Gestione configurazione locale, è necessario creare un tipo speciale di configurazione con il blocco **LocalConfigurationManager**. Per altre informazioni sulla configurazione di Gestione configurazione locale, vedere [Configurazione di Gestione configurazione locale](../managing-nodes/metaConfig4.md).

## <a name="http-dsc-pull-server"></a>Server di pull DSC HTTP

Se il server di pull è configurato come servizio Web, impostare **DownloadManagerName** su **WebDownloadManager**. **WebDownloadManager** richiede la specifica di un **ServerUrl** per la chiave **DownloadManagerCustomData**. È anche possibile specificare un valore per **AllowUnsecureConnection**, come nell'esempio seguente. Lo script seguente configura Gestione configurazione locale per il pull delle configurazioni da un server denominato "PullServer".

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
        DownloadManagerCustomData = @{ServerUrl = "http://PullServer:8080/PSDSCPullServer/PSDSCPullServer.svc"; AllowUnsecureConnection = "TRUE"}
    }
}
PullClientConfigId -Output "."
```

## <a name="smb-share"></a>Condivisione SMB

Se il server di pull viene configurato come condivisione file SMB, piuttosto che come servizio Web, impostare **DownloadManagerName** su **DscFileDownloadManager** anziché su **WebDownLoadManager**. **DscFileDownloadManager** richiede la specifica della proprietà **SourcePath** in **DownloadManagerCustomData**. Lo script seguente configura Gestione configurazione locale per il pull da una condivisione SMB denominata "SmbDscShare" su un server chiamato "CONTOSO-SERVER".

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

Dopo la configurazione del client di pull, per eseguire i passaggi successivi è possibile usare le guide seguenti:

- [Pubblicare le configurazioni in un server di pull (v4/v5)](publishConfigs.md)
- [Creare un pacchetto e caricare le risorse in un server di pull (v4)](package-upload-resources.md)

## <a name="see-also"></a>Vedere anche

- [Configurare un server di pull Web DSC](pullServer.md)
- [Configurare un server di pull SMB DSC](pullServerSMB.md)
