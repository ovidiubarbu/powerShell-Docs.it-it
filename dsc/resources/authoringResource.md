---
ms.date: 06/12/2017
keywords: dsc,powershell,configurazione,installazione
title: Creare risorse Windows PowerShell DSC (Desired State Configuration) personalizzate
ms.openlocfilehash: 882b6efed4564d2354183d7472b301e1e1758335
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MTE95
ms.contentlocale: it-IT
ms.lasthandoff: 12/14/2018
ms.locfileid: "53401219"
---
# <a name="build-custom-windows-powershell-desired-state-configuration-resources"></a>Creare risorse Windows PowerShell DSC (Desired State Configuration) personalizzate

> Si applica a: Windows PowerShell 4.0, Windows PowerShell 5.0

Windows PowerShell DSC (Desired State Configuration) include risorse predefinite che è possibile usare per configurare l'ambiente. Questo argomento fornisce una panoramica dello sviluppo di risorse e collegamenti ad argomenti contenenti informazioni specifiche ed esempi.

## <a name="dsc-resource-components"></a>Componenti delle risorse DSC

Una risorsa DSC è un modulo di Windows PowerShell. Il modulo contiene sia lo schema (la definizione delle proprietà configurabili) sia l'implementazione (il codice che esegue il lavoro effettivo specificato da una configurazione) per la risorsa. Uno schema di risorsa DSC può essere definito in un file MOF e l'implementazione viene eseguita da un modulo di script. Con l'introduzione del supporto delle classi di PowerShell nella versione 5, lo schema e l'implementazione possono essere definiti in una classe. Gli argomenti seguenti descrivono in modo più dettagliato come creare risorse DSC.

* [Scrittura di una risorsa DSC personalizzata con MOF](authoringResourceMOF.md)
* [Implementazione di una risorsa DSC in C#](authoringResourceMofCS.md)
* [Scrittura di una risorsa DSC personalizzata con classi di PowerShell](authoringResourceClass.md)
* [Risorse composite: uso di una configurazione DSC come risorsa](authoringResourceComposite.md)
* [Uso dello strumento di progettazione risorse](../authoringResourceMofDesigner.md)