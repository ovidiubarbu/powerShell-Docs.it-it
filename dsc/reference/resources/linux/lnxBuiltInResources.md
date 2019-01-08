---
ms.date: 06/12/2017
keywords: dsc,powershell,configurazione,installazione
title: Risorse DSC (Desired State Configuration) predefinite per Linux
ms.openlocfilehash: ea700d24c7ff4377af671944184abb3f201852e8
ms.sourcegitcommit: e04292a9c10de9a8391d529b7f7aa3753b362dbe
ms.translationtype: MTE95
ms.contentlocale: it-IT
ms.lasthandoff: 01/04/2019
ms.locfileid: "54047704"
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