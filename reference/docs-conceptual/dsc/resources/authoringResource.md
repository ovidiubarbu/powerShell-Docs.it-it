---
ms.date: 06/12/2017
keywords: dsc,powershell,configurazione,installazione
title: Creare risorse Windows PowerShell DSC (Desired State Configuration) personalizzate
ms.openlocfilehash: f0f35e8d0083d302f142f2215c9f28fee411eb07
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 12/05/2019
ms.locfileid: "71952848"
---
# <a name="build-custom-windows-powershell-desired-state-configuration-resources"></a><span data-ttu-id="9a0c7-103">Creare risorse Windows PowerShell DSC (Desired State Configuration) personalizzate</span><span class="sxs-lookup"><span data-stu-id="9a0c7-103">Build Custom Windows PowerShell Desired State Configuration Resources</span></span>

> <span data-ttu-id="9a0c7-104">Si applica a: Windows PowerShell 4.0, Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="9a0c7-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

<span data-ttu-id="9a0c7-105">Windows PowerShell DSC (Desired State Configuration) include risorse predefinite che è possibile usare per configurare l'ambiente.</span><span class="sxs-lookup"><span data-stu-id="9a0c7-105">Windows PowerShell Desired State Configuration (DSC) has built-in resources that you can use to configure your environment.</span></span> <span data-ttu-id="9a0c7-106">Questo argomento fornisce una panoramica dello sviluppo di risorse e collegamenti ad argomenti contenenti informazioni specifiche ed esempi.</span><span class="sxs-lookup"><span data-stu-id="9a0c7-106">This topic provides an overview of developing resources and links to topics with specific information and examples.</span></span>

## <a name="dsc-resource-components"></a><span data-ttu-id="9a0c7-107">Componenti delle risorse DSC</span><span class="sxs-lookup"><span data-stu-id="9a0c7-107">DSC resource components</span></span>

<span data-ttu-id="9a0c7-108">Una risorsa DSC è un modulo di Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="9a0c7-108">A DSC resource is a Windows PowerShell module.</span></span> <span data-ttu-id="9a0c7-109">Il modulo contiene sia lo schema (la definizione delle proprietà configurabili) sia l'implementazione (il codice che esegue il lavoro effettivo specificato da una configurazione) per la risorsa.</span><span class="sxs-lookup"><span data-stu-id="9a0c7-109">The module contains both the schema (the definition of the configurable properties) and the implementation (the code that does the actual work specified by a configuration) for the resource.</span></span> <span data-ttu-id="9a0c7-110">Uno schema di risorsa DSC può essere definito in un file MOF e l'implementazione viene eseguita da un modulo di script.</span><span class="sxs-lookup"><span data-stu-id="9a0c7-110">A DSC resource schema can be defined in a MOF file, and the implementation is performed by a script module.</span></span> <span data-ttu-id="9a0c7-111">Con l'introduzione del supporto delle classi di PowerShell nella versione 5, lo schema e l'implementazione possono essere definiti in una classe.</span><span class="sxs-lookup"><span data-stu-id="9a0c7-111">Beginning with the support of PowerShell classes in version 5, the schema and implementation can both be defined in a class.</span></span> <span data-ttu-id="9a0c7-112">Gli argomenti seguenti descrivono in modo più dettagliato come creare risorse DSC.</span><span class="sxs-lookup"><span data-stu-id="9a0c7-112">The following topics describe in more detail how to create DSC resources.</span></span>

* [<span data-ttu-id="9a0c7-113">Scrittura di una risorsa DSC personalizzata con MOF</span><span class="sxs-lookup"><span data-stu-id="9a0c7-113">Writing a custom DSC resource with MOF</span></span>](authoringResourceMOF.md)
* [<span data-ttu-id="9a0c7-114">Implementazione di una risorsa DSC in C#</span><span class="sxs-lookup"><span data-stu-id="9a0c7-114">Implementing a DSC resource in C#</span></span>](authoringResourceMofCS.md)
* [<span data-ttu-id="9a0c7-115">Scrittura di una risorsa DSC personalizzata con classi di PowerShell</span><span class="sxs-lookup"><span data-stu-id="9a0c7-115">Writing a custom DSC resource with PowerShell classes</span></span>](authoringResourceClass.md)
* [<span data-ttu-id="9a0c7-116">Risorse composite: uso di una configurazione DSC come risorsa</span><span class="sxs-lookup"><span data-stu-id="9a0c7-116">Composite resources: Using a DSC configuration as a resource</span></span>](authoringResourceComposite.md)
* [<span data-ttu-id="9a0c7-117">Uso dello strumento di progettazione risorse</span><span class="sxs-lookup"><span data-stu-id="9a0c7-117">Using the Resource Designer tool</span></span>](authoringResourceMofDesigner.md)
