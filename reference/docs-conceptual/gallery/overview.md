---
ms.date: 06/12/2017
contributor: JKeithB
keywords: raccolta,powershell,cmdlet,psgallery, psget
title: PowerShell Gallery
ms.openlocfilehash: e489d2dd4db087b53eb07d2a8793c8f586c9b210
ms.sourcegitcommit: 30ccbbb32915b551c4cd4c91ef1df96b5b7514c4
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/01/2020
ms.locfileid: "80500570"
---
# <a name="the-powershell-gallery"></a><span data-ttu-id="6f14f-103">PowerShell Gallery</span><span class="sxs-lookup"><span data-stu-id="6f14f-103">The PowerShell Gallery</span></span>

<span data-ttu-id="6f14f-104">PowerShell Gallery è il repository centrale per i contenuti PowerShell.</span><span class="sxs-lookup"><span data-stu-id="6f14f-104">The PowerShell Gallery is the central repository for PowerShell content.</span></span> <span data-ttu-id="6f14f-105">Al suo interno è possibile trovare utili moduli di PowerShell che contengono comandi di PowerShell o risorse DSC (Desired State Configuration).</span><span class="sxs-lookup"><span data-stu-id="6f14f-105">In it, you can find useful PowerShell modules containing PowerShell commands and Desired State Configuration (DSC) resources.</span></span>
<span data-ttu-id="6f14f-106">Sono anche disponibili script di PowerShell, alcuni dei quali possono contenere flussi di lavoro di PowerShell e descrivono e stabiliscono la sequenza di un set di attività.</span><span class="sxs-lookup"><span data-stu-id="6f14f-106">You can also find PowerShell scripts, some of which may contain PowerShell workflows, and which outline a set of tasks and provide sequencing for those tasks.</span></span> <span data-ttu-id="6f14f-107">Alcuni di questi pacchetti sono creati da Microsoft, altri dalla community di PowerShell.</span><span class="sxs-lookup"><span data-stu-id="6f14f-107">Some of these packages are authored by Microsoft, and others are authored by the PowerShell community.</span></span>

## <a name="powershellget-overview"></a><span data-ttu-id="6f14f-108">Panoramica di PowerShellGet</span><span class="sxs-lookup"><span data-stu-id="6f14f-108">PowerShellGet Overview</span></span>

<span data-ttu-id="6f14f-109">Il modulo PowerShellGet contiene i cmdlet per l'individuazione, l'installazione, l'aggiornamento e la pubblicazione di pacchetti di PowerShell che contengono artefatti come moduli, risorse DSC, capacità del ruolo e script da [PowerShell Gallery](https://www.PowerShellGallery.com) e altri repository privati.</span><span class="sxs-lookup"><span data-stu-id="6f14f-109">The PowerShellGet module contains cmdlets for discovering, installing, updating and publishing PowerShell packages which contain artifacts such as Modules, DSC Resources, Role Capabilities and Scripts from the [PowerShell Gallery](https://www.PowerShellGallery.com) and other private repositories.</span></span>

## <a name="getting-started-with-the-gallery"></a><span data-ttu-id="6f14f-110">Introduzione a PowerShell Gallery</span><span class="sxs-lookup"><span data-stu-id="6f14f-110">Getting Started with the Gallery</span></span>

<span data-ttu-id="6f14f-111">L'installazione di pacchetti da PowerShell Gallery richiede la versione più recente del modulo PowerShellGet.</span><span class="sxs-lookup"><span data-stu-id="6f14f-111">Installing packages from the Gallery requires the latest version of the PowerShellGet module.</span></span> <span data-ttu-id="6f14f-112">Per istruzioni complete, vedere [Installazione di PowerShellGet](installing-psget.md).</span><span class="sxs-lookup"><span data-stu-id="6f14f-112">See [Installing PowerShellGet](installing-psget.md) for complete instructions.</span></span>

<span data-ttu-id="6f14f-113">Per altre informazioni su come usare i comandi PowerShellGet con PowerShell Gallery, consultare la pagina [Introduzione](getting-started.md).</span><span class="sxs-lookup"><span data-stu-id="6f14f-113">Check out the [Getting Started](getting-started.md) page for more information on how to use PowerShellGet commands with the Gallery.</span></span> <span data-ttu-id="6f14f-114">È inoltre possibile eseguire *Update-Help -Module PowerShellGet* per installare la Guida locale per tali comandi.</span><span class="sxs-lookup"><span data-stu-id="6f14f-114">You can also run *Update-Help -Module PowerShellGet* to install local help for these commands.</span></span>

## <a name="supported-operating-systems"></a><span data-ttu-id="6f14f-115">Sistemi operativi supportati</span><span class="sxs-lookup"><span data-stu-id="6f14f-115">Supported Operating Systems</span></span>

<span data-ttu-id="6f14f-116">Il modulo **PowerShellGet** richiede **PowerShell 3.0 o versione successiva**.</span><span class="sxs-lookup"><span data-stu-id="6f14f-116">The **PowerShellGet** module requires **PowerShell 3.0 or newer**.</span></span>

<span data-ttu-id="6f14f-117">**PowerShellGet** richiede .NET Framework 4.5 o versione successiva.</span><span class="sxs-lookup"><span data-stu-id="6f14f-117">**PowerShellGet** requires .NET Framework 4.5 or above.</span></span> <span data-ttu-id="6f14f-118">È possibile installare .NET Framework 4.5 o versione successiva da [qui](https://msdn.microsoft.com/library/5a4x27ek.aspx).</span><span class="sxs-lookup"><span data-stu-id="6f14f-118">You can install .NET Framework 4.5 or above from [here](https://msdn.microsoft.com/library/5a4x27ek.aspx).</span></span>

<span data-ttu-id="6f14f-119">Poiché **PowerShell Core** è multipiattaforma e questo significa che funziona in Windows, Linux e MacOS, anche **PowerShellGet** è disponibile in tali sistemi.</span><span class="sxs-lookup"><span data-stu-id="6f14f-119">Since **PowerShell Core** is cross-platform and that means it works on Windows, Linux and MacOS, that also makes **PowerShellGet** available on those systems.</span></span> <span data-ttu-id="6f14f-120">Per un elenco completo dei sistemi supportati da **PowerShell Core** vedere [Installazione di varie versioni di PowerShell](/powershell/scripting/install/installing-powershell).</span><span class="sxs-lookup"><span data-stu-id="6f14f-120">For a full list of systems supported by **PowerShell Core** see [Installing PowerShell](/powershell/scripting/install/installing-powershell).</span></span>

<span data-ttu-id="6f14f-121">Molti moduli ospitati nella raccolta supporteranno sistemi operativi diversi e hanno requisiti aggiuntivi.</span><span class="sxs-lookup"><span data-stu-id="6f14f-121">Many modules hosted in the gallery will support different OSes and have additional requirements.</span></span>
<span data-ttu-id="6f14f-122">Per altre informazioni, vedere la documentazione per i moduli.</span><span class="sxs-lookup"><span data-stu-id="6f14f-122">Please refer to the documentation for the modules for more information.</span></span>

## <a name="got-a-question-have-feedback"></a><span data-ttu-id="6f14f-123">Domande?</span><span class="sxs-lookup"><span data-stu-id="6f14f-123">Got a question?</span></span> <span data-ttu-id="6f14f-124">Commenti e suggerimenti?</span><span class="sxs-lookup"><span data-stu-id="6f14f-124">Have feedback?</span></span>

<span data-ttu-id="6f14f-125">Altre informazioni su PowerShell Gallery e PowerShellGet sono disponibili nella pagina [Introduzione](getting-started.md).</span><span class="sxs-lookup"><span data-stu-id="6f14f-125">More information about the PowerShell Gallery and PowerShellGet can be found in the [Getting Started](getting-started.md) page.</span></span> <span data-ttu-id="6f14f-126">Fornire commenti e suggerimenti e segnalare problemi usando [UserVoice](http://windowsserver.uservoice.com/forums/301869-powershell).</span><span class="sxs-lookup"><span data-stu-id="6f14f-126">Please provide feedback and report issues using [UserVoice](http://windowsserver.uservoice.com/forums/301869-powershell).</span></span>
