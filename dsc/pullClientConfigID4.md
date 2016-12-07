---
title: Configurazione di un client di pull usando un ID configurazione in PowerShell 4.0
ms.date: 2016-05-16
keywords: powershell,DSC
description: 
ms.topic: article
author: eslesar
manager: dongill
ms.prod: powershell
ms.openlocfilehash: 730f2f26e2811996e79cf0073a4ef65cad390687
ms.sourcegitcommit: c732e3ee6d2e0e9cd8c40105d6fbfd4d207b730d
translationtype: HT
---
# <a name="setting-up-a-pull-client-using-configuration-id-in-powershell-40"></a>Configurazione di un client di pull usando un ID configurazione in PowerShell 4.0

>Si applica a: Windows PowerShell 4.0, Windows PowerShell 5.0

Per ogni nodo di destinazione è necessario specificare che venga usata la modalità pull e fornire l'URL per contattare il server di pull da cui ottenere le configurazioni. A tale scopo, è necessario configurare Gestione configurazione locale con le informazioni richieste. Per configurare Gestione configurazione locale, è necessario creare un tipo speciale di configurazione detto "metaconfigurazione". Per altre informazioni sulla configurazione di Gestione configurazione locale, vedere [Gestione configurazione locale di Windows PowerShell 4.0 DSC (Desired State Configuration)](metaConfig4.md).

Lo script seguente configura Gestione configurazione locale per il pull delle configurazioni da un server denominato "PullServer":

```powershell
Configuration SimpleMetaConfigurationForPull 
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
SimpleMetaConfigurationForPull -Output "."
```

Nello script, **DownloadManagerCustomData** passa l'URL del server di pull e (per questo esempio) consente una connessione non protetta. 

Dopo essere stato eseguito, questo script crea una nuova cartella di output denominata **SimpleMetaConfigurationForPull** e inserisce in questa cartella un file MOF di metaconfigurazione.

Per applicare la configurazione, usare **Set-DscLocalConfigurationManager** con i parametri per **ComputerName** (usare "localhost") e **Path** (percorso del file localhost.meta.mof nel nodo di destinazione). Ad esempio: 
```powershell
Set-DSCLocalConfigurationManager –ComputerName localhost –Path . –Verbose.
```

## <a name="configuration-id"></a>ID configurazione
Lo script imposta la proprietà **ConfigurationID** di Gestione configurazione locale su un GUID creato in precedenza per questo scopo (è possibile creare un GUID usando il cmdlet **New-Guid**). Il valore di **ConfigurationID** viene usato da Gestione configurazione locale per trovare la configurazione appropriata nel server di pull. Il file MOF di configurazione nel server di pull deve essere denominato `ConfigurationID.mof`, dove *ConfigurationID* è il valore della proprietà **ConfigurationID** di Gestione configurazione locale del nodo di destinazione.

## <a name="pulling-from-an-smb-server"></a>Pull da un server SMB

Se il server di pull viene configurato come condivisione file SMB, piuttosto che come servizio Web, specificare **DscFileDownloadManager** invece di **WebDownLoadManager**.
**DscFileDownloadManager** accetta una proprietà **SourcePath** invece di **ServerUrl**. Lo script seguente configura Gestione configurazione locale per il pull da una condivisione SMB denominata "SmbDscShare" su un server chiamato "CONTOSO-SERVER":

```powershell
Configuration SimpleMetaConfigurationForPull 
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
SimpleMetaConfigurationForPull -Output "."
```

## <a name="see-also"></a>Vedere anche

- [Configurazione di un server di pull Web DSC](pullServer.md)
- [Configurazione di un server di pull SMB DSC](pullServerSMB.md)

