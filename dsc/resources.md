---
ms.date: 2017-06-12
author: eslesar
ms.topic: conceptual
keywords: dsc,powershell,configurazione,impostazione
title: Risorse DSC
ms.openlocfilehash: 62bf352b929d661e585e145e5aab0f44f13010a1
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 06/12/2017
---
# <a name="dsc-resources"></a><span data-ttu-id="b631e-103">Risorse DSC</span><span class="sxs-lookup"><span data-stu-id="b631e-103">DSC Resources</span></span>

><span data-ttu-id="b631e-104">Si applica a: Windows PowerShell 4.0, Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="b631e-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

<span data-ttu-id="b631e-105">Le risorse DSC (Desired State Configuration) forniscono i blocchi predefiniti per una configurazione DSC.</span><span class="sxs-lookup"><span data-stu-id="b631e-105">Desired State Configuration (DSC) Resources provide the building blocks for a DSC configuration.</span></span> <span data-ttu-id="b631e-106">Una risorsa espone le proprietà che possono essere configurate (schema) e contiene le funzioni di script di PowerShell chiamate da Gestione configurazione locale per assicurare il risultato desiderato.</span><span class="sxs-lookup"><span data-stu-id="b631e-106">A resource exposes properties that can be configured (schema) and contains the PowerShell script functions that the Local Configuration Manager (LCM) calls to "make it so".</span></span>

<span data-ttu-id="b631e-107">Una risorsa può modellare un elemento generico come un file o uno specifico come un'impostazione del server IIS.</span><span class="sxs-lookup"><span data-stu-id="b631e-107">A resource can model something as generic as a file or as specific as an IIS server setting.</span></span>  <span data-ttu-id="b631e-108">I gruppi di tali risorse sono combinati in un modulo DSC, che organizza tutti i file necessari in una struttura portatile che include i metadati che permettono di identificare il modo in cui si intende usare le risorse.</span><span class="sxs-lookup"><span data-stu-id="b631e-108">Groups of like resources are combined in to a DSC Module, which organizes all the required files in to a structure that is portable and includes metadata to identify how the resources are intended to be used.</span></span>  

<span data-ttu-id="b631e-109">Le risorse DSC vengono descritte negli argomenti seguenti:</span><span class="sxs-lookup"><span data-stu-id="b631e-109">The following topics describe DSC resources:</span></span>

- [<span data-ttu-id="b631e-110">Risorse DSC predefinite</span><span class="sxs-lookup"><span data-stu-id="b631e-110">Built-In DSC resources</span></span>](builtInResource.md)
- [<span data-ttu-id="b631e-111">Creare risorse DSC personalizzate</span><span class="sxs-lookup"><span data-stu-id="b631e-111">Build custom DSC resources</span></span>](authoringResource.md)
- [<span data-ttu-id="b631e-112">Risorse DSC predefinite per Linux</span><span class="sxs-lookup"><span data-stu-id="b631e-112">Built-In DSC resources for Linux</span></span>](lnxBuiltInResources.md)

