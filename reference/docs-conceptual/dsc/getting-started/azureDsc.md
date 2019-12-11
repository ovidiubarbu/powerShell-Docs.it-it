---
ms.date: 03/15/2018
keywords: dsc,powershell,configurazione,installazione
title: Uso di DSC in Microsoft Azure
ms.openlocfilehash: 54a317a415ff12c3d270897f414cba88716f0728
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 12/05/2019
ms.locfileid: "71953958"
---
# <a name="using-dsc-on-microsoft-azure"></a><span data-ttu-id="2b1bf-103">Uso di DSC in Microsoft Azure</span><span class="sxs-lookup"><span data-stu-id="2b1bf-103">Using DSC on Microsoft Azure</span></span>

<span data-ttu-id="2b1bf-104">La configurazione dello stato desiderato (DSC, Desired State Configuration) è supportata in Microsoft Azure tramite il [gestore dell'estensione DSC di Azure](/azure/virtual-machines/extensions/dsc-overview) e [Automation DSC di Azure](/azure/automation/automation-dsc-overview).</span><span class="sxs-lookup"><span data-stu-id="2b1bf-104">Desired State Configuration (DSC) is supported in Microsoft Azure through the [Azure Desired State Configuration extension handler](/azure/virtual-machines/extensions/dsc-overview) and through [Azure Automation DSC](/azure/automation/automation-dsc-overview).</span></span>

## <a name="azure-desired-state-configuration-extension-handler"></a><span data-ttu-id="2b1bf-105">Gestore dell'estensione DSC (Desired State Configuration) di Azure</span><span class="sxs-lookup"><span data-stu-id="2b1bf-105">Azure Desired State Configuration extension handler</span></span>

<span data-ttu-id="2b1bf-106">L'estensione DSC di Azure consente di gestire con DSC le macchine virtuali ospitate in Microsoft Azure.</span><span class="sxs-lookup"><span data-stu-id="2b1bf-106">The Azure DSC extension allows VMs hosted in Microsoft Azure to be managed with DSC.</span></span>
<span data-ttu-id="2b1bf-107">Per altre informazioni, vedere gli argomenti seguenti:</span><span class="sxs-lookup"><span data-stu-id="2b1bf-107">For more information, see the following topics:</span></span>

- [<span data-ttu-id="2b1bf-108">Introduzione al gestore dell'estensione DSC (Desired State Configuration) di Azure</span><span class="sxs-lookup"><span data-stu-id="2b1bf-108">Azure Desired State Configuration extension handler</span></span>](/azure/virtual-machines/extensions/dsc-overview)
- [<span data-ttu-id="2b1bf-109">Set di scalabilità di macchine virtuali (VMSS) Windows e Desired State Configuration (DSC) con modelli di Azure Resource Manager</span><span class="sxs-lookup"><span data-stu-id="2b1bf-109">Windows VMSS and Desired State Configuration with Azure Resource Manager templates</span></span>](/azure/virtual-machines/extensions/dsc-template)
- [<span data-ttu-id="2b1bf-110">Passaggio di credenziali al gestore estensione DSC di Azure</span><span class="sxs-lookup"><span data-stu-id="2b1bf-110">Passing credentials to the Azure DSC extension handler</span></span>](/azure/virtual-machines/extensions/dsc-credentials)
- [<span data-ttu-id="2b1bf-111">Cronologia dell'estensione DSC (Desired State Configuration) di Azure</span><span class="sxs-lookup"><span data-stu-id="2b1bf-111">Azure Desired State Configuration extension history</span></span>](azureDscexthistory.md)

## <a name="azure-automation-dsc"></a><span data-ttu-id="2b1bf-112">Automation DSC di Azure</span><span class="sxs-lookup"><span data-stu-id="2b1bf-112">Azure Automation DSC</span></span>

<span data-ttu-id="2b1bf-113">Il [servizio di automazione di Azure](https://azure.microsoft.com/en-us/services/automation/) consente di gestire configurazioni, risorse e nodi gestiti DSC all'interno di Azure.</span><span class="sxs-lookup"><span data-stu-id="2b1bf-113">The [Azure Automation service](https://azure.microsoft.com/en-us/services/automation/) allows you to manage DSC configurations, resources, and managed nodes from within Azure.</span></span> <span data-ttu-id="2b1bf-114">Per altre informazioni, vedere gli argomenti seguenti:</span><span class="sxs-lookup"><span data-stu-id="2b1bf-114">For more information, see the following topics:</span></span>

- [<span data-ttu-id="2b1bf-115">Panoramica della piattaforma DSC di Automazione di Azure</span><span class="sxs-lookup"><span data-stu-id="2b1bf-115">Azure Automation DSC</span></span>](/azure/automation/automation-dsc-overview)
- [<span data-ttu-id="2b1bf-116">Caricamento di computer per la gestione con Automation DSC per Azure</span><span class="sxs-lookup"><span data-stu-id="2b1bf-116">Getting started with Azure Automation DSC</span></span>](/azure/automation/automation-dsc-getting-started)
- [<span data-ttu-id="2b1bf-117">Caricamento di computer per la gestione con Automation DSC per Azure</span><span class="sxs-lookup"><span data-stu-id="2b1bf-117">Onboarding machines for management by Azure Automation DSC</span></span>](/azure/automation/automation-dsc-onboarding)