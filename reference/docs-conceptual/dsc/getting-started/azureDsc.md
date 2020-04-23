---
ms.date: 03/15/2018
keywords: dsc,powershell,configurazione,installazione
title: Uso di DSC in Microsoft Azure
ms.openlocfilehash: 6d71b69eea78e775a3e5aaac64bccfa10092b8e6
ms.sourcegitcommit: 6545c60578f7745be015111052fd7769f8289296
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/22/2020
ms.locfileid: "75870830"
---
# <a name="using-dsc-on-microsoft-azure"></a><span data-ttu-id="3ee1b-103">Uso di DSC in Microsoft Azure</span><span class="sxs-lookup"><span data-stu-id="3ee1b-103">Using DSC on Microsoft Azure</span></span>

<span data-ttu-id="3ee1b-104">La configurazione dello stato desiderato (DSC, Desired State Configuration) è supportata in Microsoft Azure tramite il [gestore dell'estensione DSC di Azure](/azure/virtual-machines/extensions/dsc-overview) e [Automation DSC di Azure](/azure/automation/automation-dsc-overview).</span><span class="sxs-lookup"><span data-stu-id="3ee1b-104">Desired State Configuration (DSC) is supported in Microsoft Azure through the [Azure Desired State Configuration extension handler](/azure/virtual-machines/extensions/dsc-overview) and through [Azure Automation DSC](/azure/automation/automation-dsc-overview).</span></span>

## <a name="azure-desired-state-configuration-extension-handler"></a><span data-ttu-id="3ee1b-105">Gestore dell'estensione DSC (Desired State Configuration) di Azure</span><span class="sxs-lookup"><span data-stu-id="3ee1b-105">Azure Desired State Configuration extension handler</span></span>

<span data-ttu-id="3ee1b-106">L'estensione DSC di Azure consente di gestire con DSC le macchine virtuali ospitate in Microsoft Azure.</span><span class="sxs-lookup"><span data-stu-id="3ee1b-106">The Azure DSC extension allows VMs hosted in Microsoft Azure to be managed with DSC.</span></span> <span data-ttu-id="3ee1b-107">Per altre informazioni, vedere gli argomenti seguenti:</span><span class="sxs-lookup"><span data-stu-id="3ee1b-107">For more information, see the following topics:</span></span>

- [<span data-ttu-id="3ee1b-108">Introduzione al gestore dell'estensione DSC (Desired State Configuration) di Azure</span><span class="sxs-lookup"><span data-stu-id="3ee1b-108">Azure Desired State Configuration extension handler</span></span>](/azure/virtual-machines/extensions/dsc-overview)
- [<span data-ttu-id="3ee1b-109">Set di scalabilità di macchine virtuali (VMSS) Windows e Desired State Configuration (DSC) con modelli di Azure Resource Manager</span><span class="sxs-lookup"><span data-stu-id="3ee1b-109">Windows VMSS and Desired State Configuration with Azure Resource Manager templates</span></span>](/azure/virtual-machines/extensions/dsc-template)
- [<span data-ttu-id="3ee1b-110">Passaggio di credenziali al gestore estensione DSC di Azure</span><span class="sxs-lookup"><span data-stu-id="3ee1b-110">Passing credentials to the Azure DSC extension handler</span></span>](/azure/virtual-machines/extensions/dsc-credentials)
- [<span data-ttu-id="3ee1b-111">Cronologia dell'estensione DSC (Desired State Configuration) di Azure</span><span class="sxs-lookup"><span data-stu-id="3ee1b-111">Azure Desired State Configuration extension history</span></span>](azureDscexthistory.md)

## <a name="azure-automation-dsc"></a><span data-ttu-id="3ee1b-112">Automation DSC per Azure</span><span class="sxs-lookup"><span data-stu-id="3ee1b-112">Azure Automation DSC</span></span>

<span data-ttu-id="3ee1b-113">Il [servizio di automazione di Azure](https://azure.microsoft.com/services/automation/) consente di gestire configurazioni, risorse e nodi gestiti DSC all'interno di Azure.</span><span class="sxs-lookup"><span data-stu-id="3ee1b-113">The [Azure Automation service](https://azure.microsoft.com/services/automation/) allows you to manage DSC configurations, resources, and managed nodes from within Azure.</span></span> <span data-ttu-id="3ee1b-114">Per altre informazioni, vedere gli argomenti seguenti:</span><span class="sxs-lookup"><span data-stu-id="3ee1b-114">For more information, see the following topics:</span></span>

- [<span data-ttu-id="3ee1b-115">Panoramica della piattaforma DSC di Automazione di Azure</span><span class="sxs-lookup"><span data-stu-id="3ee1b-115">Azure Automation DSC</span></span>](/azure/automation/automation-dsc-overview)
- [<span data-ttu-id="3ee1b-116">Caricamento di computer per la gestione con Automation DSC per Azure</span><span class="sxs-lookup"><span data-stu-id="3ee1b-116">Getting started with Azure Automation DSC</span></span>](/azure/automation/automation-dsc-getting-started)
- [<span data-ttu-id="3ee1b-117">Caricamento di computer per la gestione con Automation DSC per Azure</span><span class="sxs-lookup"><span data-stu-id="3ee1b-117">Onboarding machines for management by Azure Automation DSC</span></span>](/azure/automation/automation-dsc-onboarding)