---
ms.date: 06/12/2017
keywords: dsc,powershell,configurazione,installazione
title: Configurazione di un client di pull DSC
ms.openlocfilehash: 54c68ac26e5388260e252ce01418170e26ddecde
ms.sourcegitcommit: 18985d07ef024378c8590dc7a983099ff9225672
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 10/04/2019
ms.locfileid: "71955168"
---
# <a name="setting-up-a-dsc-pull-client"></a>Configurazione di un client di pull DSC

> Si applica a: Windows PowerShell 4.0, Windows PowerShell 5.0

> [!IMPORTANT]
> Il server di pull (funzionalità di Windows *servizio DSC*) è un componente supportato di Windows Server, tuttavia non si prevede di offrire nuove caratteristiche o funzionalità. È consigliabile avviare la transizione dei client gestiti ad [Automation DSC per Azure](/azure/automation/automation-dsc-getting-started) (include funzionalità superiori al server di pull in Windows Server) o a una delle soluzioni della community riportate [qui](pullserver.md#community-solutions-for-pull-service).

Per ogni nodo di destinazione è necessario specificare che venga usata la modalità pull e fornire l'URL o il percorso di file per contattare il server di pull da cui ottenere le configurazioni e le risorse, oltre alla posizione in cui inviare i dati di report.

Gli argomenti seguenti illustrano come configurare i client di pull:

* [Configurazione di un client di pull usando nomi di configurazione](pullClientConfigNames.md)
* [Configurazione di un client di pull usando un ID configurazione](pullClientConfigID.md)

> [!NOTE]
> Questi argomenti si applicano a PowerShell 5.0. Per configurare un client di pull in PowerShell 4.0, vedere [Configurazione di un client di pull usando un ID configurazione in PowerShell 4.0](pullClientConfigID4.md).