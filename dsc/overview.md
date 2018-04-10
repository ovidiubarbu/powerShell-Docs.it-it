---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: dsc,powershell,configurazione,installazione
title: Panoramica di Windows PowerShell DSC (Desired State Configuration)
ms.openlocfilehash: 3f357ea11a388a05b73539a63e52e639ee906f68
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/09/2018
---
# <a name="windows-powershell-desired-state-configuration-overview"></a><span data-ttu-id="c8ce7-103">Panoramica di Windows PowerShell DSC (Desired State Configuration)</span><span class="sxs-lookup"><span data-stu-id="c8ce7-103">Windows PowerShell Desired State Configuration Overview</span></span>

> <span data-ttu-id="c8ce7-104">Si applica a: Windows PowerShell 4.0, Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="c8ce7-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

<span data-ttu-id="c8ce7-105">DSC è una piattaforma di gestione di PowerShell che consente di gestire l'infrastruttura IT e di sviluppo con la configurazione come codice.</span><span class="sxs-lookup"><span data-stu-id="c8ce7-105">DSC is a management platform in PowerShell that enables you to manage your IT and development infrastructure with configuration as code.</span></span>

- <span data-ttu-id="c8ce7-106">Per una panoramica dei vantaggi aziendali dell'uso di DSC, vedere [Panoramica di DSC (Desired State Configuration) per decision maker](decisionMaker.md).</span><span class="sxs-lookup"><span data-stu-id="c8ce7-106">For an overview of the business benefits of using DSC, see [Desired State Configuration Overview for Decision Makers](decisionMaker.md).</span></span>
- <span data-ttu-id="c8ce7-107">Per una panoramica dei vantaggi a livello tecnico dell'uso di DSC, vedere [Panoramica di DSC (Desired State Configuration) per tecnici](DscForEngineers.md).</span><span class="sxs-lookup"><span data-stu-id="c8ce7-107">For an overview of the engineering benefits of using DSC, see [Desired State Configuration Overview for Engineers](DscForEngineers.md).</span></span>
- <span data-ttu-id="c8ce7-108">Per iniziare a usare rapidamente DSC, vedere [Introduzione a DSC](quickStart.md).</span><span class="sxs-lookup"><span data-stu-id="c8ce7-108">To start using DSC quickly, see [DSC quick start](quickStart.md).</span></span>

## <a name="key-concepts"></a><span data-ttu-id="c8ce7-109">Concetti chiave</span><span class="sxs-lookup"><span data-stu-id="c8ce7-109">Key Concepts</span></span>

<span data-ttu-id="c8ce7-110">DSC è una piattaforma dichiarativa usata per la configurazione, la distribuzione e la gestione dei sistemi.</span><span class="sxs-lookup"><span data-stu-id="c8ce7-110">DSC is a declarative platform used for configuration, deployment, and management of systems.</span></span> <span data-ttu-id="c8ce7-111">È costituita da tre componenti principali:</span><span class="sxs-lookup"><span data-stu-id="c8ce7-111">It consists of three primary components:</span></span>

- <span data-ttu-id="c8ce7-112">Le [configurazioni](configurations.md) sono script di PowerShell dichiarativi che definiscono e configurano le istanze delle risorse.</span><span class="sxs-lookup"><span data-stu-id="c8ce7-112">[Configurations](configurations.md) are declarative PowerShell scripts which define and configure instances of resources.</span></span>
    <span data-ttu-id="c8ce7-113">Quando viene eseguita la configurazione, DSC (e le risorse chiamate dalla configurazione) si assicurano semplicemente che il risultato sia quello desiderato, facendo in modo che lo stato del sistema corrisponda a quanto definito dalla configurazione.</span><span class="sxs-lookup"><span data-stu-id="c8ce7-113">Upon running the configuration, DSC (and the resources being called by the configuration) will simply “make it so”, ensuring that the system exists in the state laid out by the configuration.</span></span>
    <span data-ttu-id="c8ce7-114">Le configurazioni DSC sono inoltre idempotenti: Gestione configurazione locale continua a garantire che i computer siano configurati in base a qualsiasi stato dichiarato dalla configurazione.</span><span class="sxs-lookup"><span data-stu-id="c8ce7-114">DSC configurations are also idempotent: the Local Configuration Manager (LCM) will continue to ensure that machines are configured in whatever state the configuration declares.</span></span>
- <span data-ttu-id="c8ce7-115">Le [risorse](resources.md) sono la parte attiva di DSC.</span><span class="sxs-lookup"><span data-stu-id="c8ce7-115">[Resources](resources.md) are the "make it so" part of DSC.</span></span> <span data-ttu-id="c8ce7-116">e contengono il codice per mettere la destinazione di una configurazione nello stato specificato e mantenerla in tale stato.</span><span class="sxs-lookup"><span data-stu-id="c8ce7-116">They contain the code that put and keep the target of a configuration in the specified state.</span></span>
    <span data-ttu-id="c8ce7-117">Le risorse si trovano all'interno dei moduli di PowerShell e possono essere scritte per modellare un elemento generico, come un file o un processo di Windows, o un elemento specifico, come un server IIS o una VM in esecuzione in Azure.</span><span class="sxs-lookup"><span data-stu-id="c8ce7-117">Resources reside in PowerShell modules and can be written to model something as generic as a file or a Windows process, or as specific as an IIS server or a VM running in Azure.</span></span>
- <span data-ttu-id="c8ce7-118">[Gestione configurazione locale](metaConfig.md) è il motore usato da DSC per semplificare l'interazione tra risorse e configurazioni.</span><span class="sxs-lookup"><span data-stu-id="c8ce7-118">The [Local Configuration Manager (LCM)](metaConfig.md) is the engine by which DSC facilitates the interaction between resources and configurations.</span></span>
    <span data-ttu-id="c8ce7-119">Gestione configurazione locale esegue regolarmente il polling del sistema usando il flusso di controllo implementato dalle risorse per garantire che lo stato definito da una configurazione venga mantenuto.</span><span class="sxs-lookup"><span data-stu-id="c8ce7-119">The LCM regularly polls the system using the control flow implemented by resources to ensure that the state defined by a configuration is maintained.</span></span>
    <span data-ttu-id="c8ce7-120">Se lo stato del sistema non è quello previsto, Gestione configurazione locale effettua chiamate al codice nelle risorse per ottenere il risultato desiderato, in base alla configurazione.</span><span class="sxs-lookup"><span data-stu-id="c8ce7-120">If the system is out of state, the LCM makes calls to the code in resources to “make it so” according to the configuration.</span></span>

## <a name="see-also"></a><span data-ttu-id="c8ce7-121">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="c8ce7-121">See Also</span></span>

- [<span data-ttu-id="c8ce7-122">Configurazioni DSC</span><span class="sxs-lookup"><span data-stu-id="c8ce7-122">DSC Configurations</span></span>](configurations.md)
- [<span data-ttu-id="c8ce7-123">Risorse DSC</span><span class="sxs-lookup"><span data-stu-id="c8ce7-123">DSC Resources</span></span>](resources.md)
- [<span data-ttu-id="c8ce7-124">Configurazione di Gestione configurazione locale</span><span class="sxs-lookup"><span data-stu-id="c8ce7-124">Configuring The Local Configuration Manager</span></span>](metaConfig.md)