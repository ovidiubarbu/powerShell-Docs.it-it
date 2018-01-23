---
ms.date: 2017-06-12
ms.topic: conceptual
keywords: dsc,powershell,configurazione,installazione
title: Risorse DSC
ms.openlocfilehash: 0994616673b5e447c69c09154bfdb9b9126a88c8
ms.sourcegitcommit: a444406120e5af4e746cbbc0558fe89a7e78aef6
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/17/2018
---
# <a name="dsc-resources"></a>Risorse DSC

>Si applica a: Windows PowerShell 4.0, Windows PowerShell 5.0

Le risorse DSC (Desired State Configuration) forniscono i blocchi predefiniti per una configurazione DSC. Una risorsa espone le proprietà che possono essere configurate (schema) e contiene le funzioni di script di PowerShell chiamate da Gestione configurazione locale per assicurare il risultato desiderato.

Una risorsa può modellare un elemento generico come un file o uno specifico come un'impostazione del server IIS.  I gruppi di tali risorse sono combinati in un modulo DSC, che organizza tutti i file necessari in una struttura portatile che include i metadati che permettono di identificare il modo in cui si intende usare le risorse.  

Le risorse DSC vengono descritte negli argomenti seguenti:

- [Risorse DSC predefinite](builtInResource.md)
- [Creare risorse DSC personalizzate](authoringResource.md)
- [Risorse DSC predefinite per Linux](lnxBuiltInResources.md)

