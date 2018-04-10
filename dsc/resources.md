---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: dsc,powershell,configurazione,installazione
title: Risorse DSC
ms.openlocfilehash: e393c8fe2e1ba8d68ba9aa1b656d1e5ebfad30e8
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/09/2018
---
# <a name="dsc-resources"></a>Risorse DSC

>Si applica a: Windows PowerShell 4.0, Windows PowerShell 5.0

Le risorse DSC (Desired State Configuration) forniscono i blocchi predefiniti per una configurazione DSC. Una risorsa espone le proprietà che possono essere configurate (schema) e contiene le funzioni di script di PowerShell chiamate da Gestione configurazione locale per assicurare il risultato desiderato.

Una risorsa può modellare un elemento generico come un file o uno specifico come un'impostazione del server IIS.  I gruppi di tali risorse sono combinati in un modulo DSC, che organizza tutti i file necessari in una struttura portatile che include i metadati che permettono di identificare il modo in cui si intende usare le risorse.

Le risorse DSC vengono descritte negli argomenti seguenti:

- [Risorse DSC predefinite](builtInResource.md)
- [Creare risorse DSC personalizzate](authoringResource.md)
- [Risorse DSC predefinite per Linux](lnxBuiltInResources.md)