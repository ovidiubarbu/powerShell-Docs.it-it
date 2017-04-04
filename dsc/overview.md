---
title: Panoramica di Windows PowerShell DSC (Desired State Configuration)
ms.date: 2016-05-16
keywords: powershell,DSC
description: 
ms.topic: article
author: eslesar
manager: dongill
ms.prod: powershell
ms.openlocfilehash: ec773688540a3f4a2f128f66d311926fd5b9a935
ms.sourcegitcommit: 6d27d6db5ab0e2d5b6c7229e2e2d2e57915ea22d
translationtype: HT
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
- Le risorse sono la parte attiva di DSC e contengono il codice per mettere la destinazione di una configurazione nello stato specificato e mantenerla in tale stato. 
    Le risorse si trovano all'interno dei moduli di PowerShell e possono essere scritte per modellare un elemento generico, come un file o un processo di Windows, o un elemento specifico, come un server IIS o una VM in esecuzione in Azure.
- Gestione configurazione locale è il motore usato da DSC per semplificare l'interazione tra risorse e configurazioni. 
    Gestione configurazione locale esegue regolarmente il polling del sistema usando il flusso di controllo implementato dalle risorse per garantire che lo stato definito da una configurazione venga mantenuto. 
    Se lo stato del sistema non è quello previsto, Gestione configurazione locale effettua chiamate al codice nelle risorse per ottenere il risultato desiderato, in base alla configurazione. 

## <a name="see-also"></a>Vedere anche

- [Configurazioni DSC](configurations.md)
- [Risorse DSC](resources.md)
- [Configurazione di Gestione configurazione locale](metaConfig.md)

