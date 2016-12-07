---
title: Risorse DSC (Desired State Configuration) predefinite per Linux
ms.date: 2016-05-16
keywords: powershell,DSC
description: 
ms.topic: article
author: eslesar
manager: dongill
ms.prod: powershell
ms.openlocfilehash: 6b001c12885022006003ef3ffe91b7aede07bd17
ms.sourcegitcommit: c732e3ee6d2e0e9cd8c40105d6fbfd4d207b730d
translationtype: HT
---
# <a name="built-in-desired-state-configuration-resources-for-linux"></a>Risorse DSC (Desired State Configuration) predefinite per Linux

Le risorse sono blocchi predefiniti che è possibile usare per scrivere uno script di PowerShell DSC (Desired State Configuration). DSC per Linux include un set di funzionalità predefinite per la configurazione di risorse come file e cartelle, pacchetti, variabili di ambiente e servizi e processi.

## <a name="built-in-resources"></a>Risorse predefinite 

La tabella seguente contiene un elenco di queste risorse, insieme ai collegamenti agli argomenti che le descrivono dettagliatamente.

* [Risorsa nxArchive](lnxArchiveResource.md): fornisce un meccanismo per decomprimere file di archivio (ZIP) in un percorso specifico.
* [Risorsa nxEnvironment](lnxEnvironmentResource.md): gestisce le variabili di ambiente nei nodi di destinazione. 
* [Risorsa nxFile](lnxFileResource.md): gestisce i file e le directory di Linux. 
* [Risorsa nxFileLine](lnxFileLineResource.md): gestisce singole righe in un file di Linux. 
* [Risorsa nxGroup](lnxGroupResource.md): gestisce i gruppi locali di Linux. 
* [Risorsa nxPackage](lnxPackageResource.md): gestisce i pacchetti in nodi di Linux.
* [Risorsa nxScript](lnxScriptResource.md): esegue gli script nei nodi di destinazione.
* [Risorsa nxService](lnxServiceResource.md): gestisce i servizi Linux (daemon).
* [Risorsa nxSshAuthorizedKeys](lnxSshAuthorizedKeysResource.md): gestisce le chiavi ssh pubbliche per un utente di Linux. 
* [Risorsa nxUser](lnxUserResource.md): gestisce gli utenti locali di Linux. 
  
