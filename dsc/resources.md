---
title: Risorse DSC
ms.date: 2016-05-16
keywords: powershell,DSC
description: 
ms.topic: article
author: eslesar
manager: dongill
ms.prod: powershell
translationtype: Human Translation
ms.sourcegitcommit: 6477ae8575c83fc24150f9502515ff5b82bc8198
ms.openlocfilehash: 0a27a40b995393c41f0496a5f7fa3f56fbd865dd

---

# Risorse DSC

>Si applica a: Windows PowerShell 4.0, Windows PowerShell 5.0

Le risorse DSC (Desired State Configuration) forniscono i blocchi predefiniti per una configurazione DSC. Una risorsa espone le proprietà che possono essere configurate (schema) e contiene le funzioni di script di PowerShell chiamate da Gestione configurazione locale per assicurare il risultato desiderato.

Una risorsa può modellare un elemento generico come un file o uno specifico come un'impostazione del server IIS.  I gruppi di tali risorse sono combinati in un modulo DSC, che organizza tutti i file necessari in una struttura portatile che include i metadati che permettono di identificare il modo in cui si intende usare le risorse.  

Le risorse DSC vengono descritte negli argomenti seguenti:

- [Risorse Windows PowerShell DSC (Desired State Configuration) predefinite](builtInResource.md)
- [Creare risorse Windows PowerShell DSC (Desired State Configuration) personalizzate](authoringResource.md)
- [Risorse DSC (Desired State Configuration) predefinite per Linux](lnxBuiltInResources.md)




<!--HONumber=Jun16_HO4-->


