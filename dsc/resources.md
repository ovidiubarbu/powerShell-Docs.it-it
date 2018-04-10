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
# <a name="dsc-resources"></a><span data-ttu-id="be419-103">Risorse DSC</span><span class="sxs-lookup"><span data-stu-id="be419-103">DSC Resources</span></span>

><span data-ttu-id="be419-104">Si applica a: Windows PowerShell 4.0, Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="be419-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

<span data-ttu-id="be419-105">Le risorse DSC (Desired State Configuration) forniscono i blocchi predefiniti per una configurazione DSC.</span><span class="sxs-lookup"><span data-stu-id="be419-105">Desired State Configuration (DSC) Resources provide the building blocks for a DSC configuration.</span></span> <span data-ttu-id="be419-106">Una risorsa espone le proprietà che possono essere configurate (schema) e contiene le funzioni di script di PowerShell chiamate da Gestione configurazione locale per assicurare il risultato desiderato.</span><span class="sxs-lookup"><span data-stu-id="be419-106">A resource exposes properties that can be configured (schema) and contains the PowerShell script functions that the Local Configuration Manager (LCM) calls to "make it so".</span></span>

<span data-ttu-id="be419-107">Una risorsa può modellare un elemento generico come un file o uno specifico come un'impostazione del server IIS.</span><span class="sxs-lookup"><span data-stu-id="be419-107">A resource can model something as generic as a file or as specific as an IIS server setting.</span></span>  <span data-ttu-id="be419-108">I gruppi di tali risorse sono combinati in un modulo DSC, che organizza tutti i file necessari in una struttura portatile che include i metadati che permettono di identificare il modo in cui si intende usare le risorse.</span><span class="sxs-lookup"><span data-stu-id="be419-108">Groups of like resources are combined in to a DSC Module, which organizes all the required files in to a structure that is portable and includes metadata to identify how the resources are intended to be used.</span></span>

<span data-ttu-id="be419-109">Le risorse DSC vengono descritte negli argomenti seguenti:</span><span class="sxs-lookup"><span data-stu-id="be419-109">The following topics describe DSC resources:</span></span>

- [<span data-ttu-id="be419-110">Risorse DSC predefinite</span><span class="sxs-lookup"><span data-stu-id="be419-110">Built-In DSC resources</span></span>](builtInResource.md)
- [<span data-ttu-id="be419-111">Creare risorse DSC personalizzate</span><span class="sxs-lookup"><span data-stu-id="be419-111">Build custom DSC resources</span></span>](authoringResource.md)
- [<span data-ttu-id="be419-112">Risorse DSC predefinite per Linux</span><span class="sxs-lookup"><span data-stu-id="be419-112">Built-In DSC resources for Linux</span></span>](lnxBuiltInResources.md)