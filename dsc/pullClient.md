---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: dsc,powershell,configurazione,installazione
title: Configurazione di un client di pull DSC
ms.openlocfilehash: 4c56671313b93cc12ce9460ce41e1710e0d6a526
ms.sourcegitcommit: ece1794c94be4880a2af5a2605ed4721593643b6
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="setting-up-a-dsc-pull-client"></a>Configurazione di un client di pull DSC

> Si applica a: Windows PowerShell 4.0, Windows PowerShell 5.0

> [!IMPORTANT]
> Il server di pull (funzionalità di Windows *servizio DSC*) è un componente supportato di Windows Server, tuttavia non si prevede di offrire nuove caratteristiche o funzionalità. È consigliabile avviare la transizione dei client gestiti ad [Automation DSC per Azure](/azure/automation/automation-dsc-getting-started) (include funzionalità superiori al server di pull in Windows Server) o a una delle soluzioni della community riportate [qui](pullserver.md#community-solutions-for-pull-service).

Per ogni nodo di destinazione è necessario specificare che venga usata la modalità pull e fornire l'URL o il percorso di file per contattare il server di pull da cui ottenere le configurazioni e le risorse, oltre alla posizione in cui inviare i dati di report.

Gli argomenti seguenti illustrano come configurare i client di pull:

* [Configurazione di un client di pull usando nomi di configurazione](pullClientConfigNames.md)
* [Configurazione di un client di pull usando un ID configurazione](pullClientConfigID.md)

> **Nota**: questi argomenti si applicano a PowerShell 5.0. Per configurare un client di pull in PowerShell 4.0, vedere [Configurazione di un client di pull usando un ID configurazione in PowerShell 4.0](pullClientConfigID4.md).