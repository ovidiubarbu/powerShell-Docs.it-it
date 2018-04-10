---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: dsc,powershell,configurazione,installazione
title: Panoramica di Windows PowerShell DSC (Desired State Configuration)
ms.openlocfilehash: 3f357ea11a388a05b73539a63e52e639ee906f68
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/09/2018
---
# <a name="windows-powershell-desired-state-configuration-overview"></a>Panoramica di Windows PowerShell DSC (Desired State Configuration)

> Si applica a: Windows PowerShell 4.0, Windows PowerShell 5.0

DSC è una piattaforma di gestione di PowerShell che consente di gestire l'infrastruttura IT e di sviluppo con la configurazione come codice.

- Per una panoramica dei vantaggi aziendali dell'uso di DSC, vedere [Panoramica di DSC (Desired State Configuration) per decision maker](decisionMaker.md).
- Per una panoramica dei vantaggi a livello tecnico dell'uso di DSC, vedere [Panoramica di DSC (Desired State Configuration) per tecnici](DscForEngineers.md).
- Per iniziare a usare rapidamente DSC, vedere [Introduzione a DSC](quickStart.md).

## <a name="key-concepts"></a>Concetti chiave

DSC è una piattaforma dichiarativa usata per la configurazione, la distribuzione e la gestione dei sistemi. È costituita da tre componenti principali:

- Le [configurazioni](configurations.md) sono script di PowerShell dichiarativi che definiscono e configurano le istanze delle risorse.
    Quando viene eseguita la configurazione, DSC (e le risorse chiamate dalla configurazione) si assicurano semplicemente che il risultato sia quello desiderato, facendo in modo che lo stato del sistema corrisponda a quanto definito dalla configurazione.
    Le configurazioni DSC sono inoltre idempotenti: Gestione configurazione locale continua a garantire che i computer siano configurati in base a qualsiasi stato dichiarato dalla configurazione.
- Le [risorse](resources.md) sono la parte attiva di DSC. e contengono il codice per mettere la destinazione di una configurazione nello stato specificato e mantenerla in tale stato.
    Le risorse si trovano all'interno dei moduli di PowerShell e possono essere scritte per modellare un elemento generico, come un file o un processo di Windows, o un elemento specifico, come un server IIS o una VM in esecuzione in Azure.
- [Gestione configurazione locale](metaConfig.md) è il motore usato da DSC per semplificare l'interazione tra risorse e configurazioni.
    Gestione configurazione locale esegue regolarmente il polling del sistema usando il flusso di controllo implementato dalle risorse per garantire che lo stato definito da una configurazione venga mantenuto.
    Se lo stato del sistema non è quello previsto, Gestione configurazione locale effettua chiamate al codice nelle risorse per ottenere il risultato desiderato, in base alla configurazione.

## <a name="see-also"></a>Vedere anche

- [Configurazioni DSC](configurations.md)
- [Risorse DSC](resources.md)
- [Configurazione di Gestione configurazione locale](metaConfig.md)