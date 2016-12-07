---
title: Creare risorse Windows PowerShell DSC (Desired State Configuration) personalizzate
ms.date: 2016-05-16
keywords: powershell,DSC
description: 
ms.topic: article
author: eslesar
manager: dongill
ms.prod: powershell
ms.openlocfilehash: fe2697de322be99e9b5dfe79090fda4082a73623
ms.sourcegitcommit: c732e3ee6d2e0e9cd8c40105d6fbfd4d207b730d
translationtype: HT
---
# <a name="build-custom-windows-powershell-desired-state-configuration-resources"></a>Creare risorse Windows PowerShell DSC (Desired State Configuration) personalizzate

> Si applica a: Windows PowerShell 4.0, Windows PowerShell 5.0

Windows PowerShell DSC (Desired State Configuration) include risorse predefinite che è possibile usare per configurare l'ambiente. Per altre informazioni, vedere [Risorse Windows PowerShell DSC (Desired State Configuration) predefinite](builtInResource.md). Questo argomento fornisce una panoramica dello sviluppo di risorse e collegamenti ad argomenti contenenti informazioni specifiche ed esempi.

## <a name="dsc-resource-components"></a>Componenti delle risorse DSC

Una risorsa DSC è un modulo di Windows PowerShell. Il modulo contiene sia lo schema (la definizione delle proprietà configurabili) sia l'implementazione (il codice che esegue il lavoro effettivo specificato da una configurazione) per la risorsa. Uno schema di risorsa DSC può essere definito in un file MOF e l'implementazione viene eseguita da un modulo di script. Con l'introduzione del supporto delle classi di PowerShell nella versione 5, lo schema e l'implementazione possono essere definiti in una classe. Gli argomenti seguenti descrivono in modo più dettagliato come creare risorse DSC.

* [Scrittura di una risorsa DSC personalizzata con MOF](authoringResourceMOF.md) 
* [Implementazione di una risorsa DSC in C#](authoringResourceMofCS.md) 
* [Scrittura di una risorsa DSC personalizzata con classi di PowerShell](authoringResourceClass.md) 
* [Risorse composite: uso di una configurazione DSC come risorsa](authoringResourceComposite.md) 
* [Uso dello strumento di progettazione risorse](authoringResourceMofDesigner.md) 

