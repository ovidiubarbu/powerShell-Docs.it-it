---
ms.date: 2017-06-12
author: eslesar
ms.topic: conceptual
keywords: dsc,powershell,configurazione,impostazione
title: Creare risorse Windows PowerShell DSC (Desired State Configuration) personalizzate
ms.openlocfilehash: 75b494db4ee6e381491decb11d35b60105217a0f
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 06/12/2017
---
<a id="build-custom-windows-powershell-desired-state-configuration-resources" class="xliff"></a>
# Creare risorse Windows PowerShell DSC (Desired State Configuration) personalizzate

> Si applica a: Windows PowerShell 4.0, Windows PowerShell 5.0

Windows PowerShell DSC (Desired State Configuration) include risorse predefinite che è possibile usare per configurare l'ambiente. Per altre informazioni, vedere [Risorse Windows PowerShell DSC (Desired State Configuration) predefinite](builtInResource.md). Questo argomento fornisce una panoramica dello sviluppo di risorse e collegamenti ad argomenti contenenti informazioni specifiche ed esempi.

<a id="dsc-resource-components" class="xliff"></a>
## Componenti delle risorse DSC

Una risorsa DSC è un modulo di Windows PowerShell. Il modulo contiene sia lo schema (la definizione delle proprietà configurabili) sia l'implementazione (il codice che esegue il lavoro effettivo specificato da una configurazione) per la risorsa. Uno schema di risorsa DSC può essere definito in un file MOF e l'implementazione viene eseguita da un modulo di script. Con l'introduzione del supporto delle classi di PowerShell nella versione 5, lo schema e l'implementazione possono essere definiti in una classe. Gli argomenti seguenti descrivono in modo più dettagliato come creare risorse DSC.

* [Scrittura di una risorsa DSC personalizzata con MOF](authoringResourceMOF.md) 
* [Implementazione di una risorsa DSC in C#](authoringResourceMofCS.md) 
* [Scrittura di una risorsa DSC personalizzata con classi di PowerShell](authoringResourceClass.md) 
* [Risorse composite: uso di una configurazione DSC come risorsa](authoringResourceComposite.md) 
* [Uso dello strumento di progettazione risorse](authoringResourceMofDesigner.md) 

