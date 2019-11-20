---
ms.date: 06/12/2017
contributor: JKeithB
keywords: raccolta,powershell,cmdlet,psgallery, psget
title: PowerShell Gallery
ms.openlocfilehash: d3e3b9d8bb3d6cefd3a3bfe79b012bb1dc1d8a2d
ms.sourcegitcommit: 4a2cf30351620a58ba95ff5d76b247e601907589
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 09/27/2019
ms.locfileid: "71327862"
---
# <a name="the-powershell-gallery"></a><span data-ttu-id="6fd97-103">PowerShell Gallery</span><span class="sxs-lookup"><span data-stu-id="6fd97-103">The PowerShell Gallery</span></span>

<span data-ttu-id="6fd97-104">PowerShell Gallery è il repository centrale per i contenuti PowerShell.</span><span class="sxs-lookup"><span data-stu-id="6fd97-104">The PowerShell Gallery is the central repository for PowerShell content.</span></span> <span data-ttu-id="6fd97-105">Al suo interno è possibile trovare utili moduli di PowerShell che contengono comandi di PowerShell o risorse DSC (Desired State Configuration).</span><span class="sxs-lookup"><span data-stu-id="6fd97-105">In it, you can find useful PowerShell modules containing PowerShell commands and Desired State Configuration (DSC) resources.</span></span>
<span data-ttu-id="6fd97-106">Sono anche disponibili script di PowerShell, alcuni dei quali possono contenere flussi di lavoro di PowerShell e descrivono e stabiliscono la sequenza di un set di attività.</span><span class="sxs-lookup"><span data-stu-id="6fd97-106">You can also find PowerShell scripts, some of which may contain PowerShell workflows, and which outline a set of tasks and provide sequencing for those tasks.</span></span> <span data-ttu-id="6fd97-107">Alcuni di questi pacchetti sono creati da Microsoft, altri dalla community di PowerShell.</span><span class="sxs-lookup"><span data-stu-id="6fd97-107">Some of these packages are authored by Microsoft, and others are authored by the PowerShell community.</span></span>

## <a name="powershellget-overview"></a><span data-ttu-id="6fd97-108">Panoramica di PowerShellGet</span><span class="sxs-lookup"><span data-stu-id="6fd97-108">PowerShellGet Overview</span></span>

<span data-ttu-id="6fd97-109">Il modulo PowerShellGet contiene i cmdlet per l'individuazione, l'installazione, l'aggiornamento e la pubblicazione di pacchetti di PowerShell che contengono artefatti come moduli, risorse DSC, capacità del ruolo e script da [PowerShell Gallery](https://www.PowerShellGallery.com) e altri repository privati.</span><span class="sxs-lookup"><span data-stu-id="6fd97-109">The PowerShellGet module contains cmdlets for discovering, installing, updating and publishing PowerShell packages which contain artifacts such as Modules, DSC Resources, Role Capabilities and Scripts from the [PowerShell Gallery](https://www.PowerShellGallery.com) and other private repositories.</span></span>

## <a name="getting-started-with-the-gallery"></a><span data-ttu-id="6fd97-110">Introduzione a PowerShell Gallery</span><span class="sxs-lookup"><span data-stu-id="6fd97-110">Getting Started with the Gallery</span></span>

<span data-ttu-id="6fd97-111">L'installazione di pacchetti da PowerShell Gallery richiede la versione più recente del modulo PowerShellGet.</span><span class="sxs-lookup"><span data-stu-id="6fd97-111">Installing packages from the Gallery requires the latest version of the PowerShellGet module.</span></span>
<span data-ttu-id="6fd97-112">Per istruzioni complete, vedere [Installazione di PowerShellGet](installing-psget.md).</span><span class="sxs-lookup"><span data-stu-id="6fd97-112">See [Installing PowerShellGet](installing-psget.md) for complete instructions.</span></span>

<span data-ttu-id="6fd97-113">Per altre informazioni su come usare i comandi PowerShellGet con PowerShell Gallery, consultare la pagina [Introduzione](getting-started.md).</span><span class="sxs-lookup"><span data-stu-id="6fd97-113">Check out the [Getting Started](getting-started.md) page for more information on how to use PowerShellGet commands with the Gallery.</span></span> <span data-ttu-id="6fd97-114">È inoltre possibile eseguire *Update-Help -Module PowerShellGet* per installare la Guida locale per tali comandi.</span><span class="sxs-lookup"><span data-stu-id="6fd97-114">You can also run *Update-Help -Module PowerShellGet* to install local help for these commands.</span></span>

## <a name="supported-operating-systems"></a><span data-ttu-id="6fd97-115">Sistemi operativi supportati</span><span class="sxs-lookup"><span data-stu-id="6fd97-115">Supported Operating Systems</span></span>

<span data-ttu-id="6fd97-116">Il modulo **PowerShellGet** richiede **Windows PowerShell 3.0 o versione successiva** o **PowerShell Core 6.0 o versione successiva**.</span><span class="sxs-lookup"><span data-stu-id="6fd97-116">The **PowerShellGet** module requires **Windows PowerShell 3.0 or newer**, or **PowerShell Core 6.0 or newer**.</span></span>

<span data-ttu-id="6fd97-117">È disponibile una versione appropriata di **Windows PowerShell** per questi sistemi operativi:</span><span class="sxs-lookup"><span data-stu-id="6fd97-117">A suitable version of **Windows PowerShell** is available for these operating systems:</span></span>

- <span data-ttu-id="6fd97-118">Windows 10</span><span class="sxs-lookup"><span data-stu-id="6fd97-118">Windows 10</span></span>
- <span data-ttu-id="6fd97-119">Windows 8.1 Pro</span><span class="sxs-lookup"><span data-stu-id="6fd97-119">Windows 8.1 Pro</span></span>
- <span data-ttu-id="6fd97-120">Windows 8.1 Enterprise</span><span class="sxs-lookup"><span data-stu-id="6fd97-120">Windows 8.1 Enterprise</span></span>
- <span data-ttu-id="6fd97-121">Windows 7 SP1</span><span class="sxs-lookup"><span data-stu-id="6fd97-121">Windows 7 SP1</span></span>
- <span data-ttu-id="6fd97-122">Windows Server 2019</span><span class="sxs-lookup"><span data-stu-id="6fd97-122">Windows Server 2019</span></span>
- <span data-ttu-id="6fd97-123">Windows Server 2016</span><span class="sxs-lookup"><span data-stu-id="6fd97-123">Windows Server 2016</span></span>
- <span data-ttu-id="6fd97-124">Windows Server 2012 R2</span><span class="sxs-lookup"><span data-stu-id="6fd97-124">Windows Server 2012 R2</span></span>
- <span data-ttu-id="6fd97-125">Windows Server 2008 R2 SP1</span><span class="sxs-lookup"><span data-stu-id="6fd97-125">Windows Server 2008 R2 SP1</span></span>

<span data-ttu-id="6fd97-126">**PowerShellGet** richiede .NET Framework 4.5 o versione successiva.</span><span class="sxs-lookup"><span data-stu-id="6fd97-126">**PowerShellGet** requires .NET Framework 4.5 or above.</span></span> <span data-ttu-id="6fd97-127">È possibile installare .NET Framework 4.5 o versione successiva da [qui](https://msdn.microsoft.com/library/5a4x27ek.aspx).</span><span class="sxs-lookup"><span data-stu-id="6fd97-127">You can install .NET Framework 4.5 or above from [here](https://msdn.microsoft.com/library/5a4x27ek.aspx).</span></span>

<span data-ttu-id="6fd97-128">Poiché **PowerShell Core** è multipiattaforma e questo significa che funziona in Windows, Linux e MacOS, anche **PowerShellGet** è disponibile in tali sistemi.</span><span class="sxs-lookup"><span data-stu-id="6fd97-128">Since **PowerShell Core** is cross-platform and that means it works on Windows, Linux and MacOS, that also makes **PowerShellGet** available on those systems.</span></span> <span data-ttu-id="6fd97-129">Per un elenco completo dei sistemi supportati da **PowerShell Core** vedere [Installazione di varie versioni di PowerShell](/powershell/scripting/setup/installing-powershell).</span><span class="sxs-lookup"><span data-stu-id="6fd97-129">For a full list of systems supported by **PowerShell Core** see [Installing PowerShell](/powershell/scripting/setup/installing-powershell).</span></span>

<span data-ttu-id="6fd97-130">Molti moduli ospitati nella raccolta supporteranno sistemi operativi diversi e hanno requisiti aggiuntivi.</span><span class="sxs-lookup"><span data-stu-id="6fd97-130">Many modules hosted in the gallery will support different OSes and have additional requirements.</span></span> <span data-ttu-id="6fd97-131">Per altre informazioni, vedere la documentazione per i moduli.</span><span class="sxs-lookup"><span data-stu-id="6fd97-131">Please refer to the documentation for the modules for more information.</span></span>

## <a name="got-a-question-have-feedback"></a><span data-ttu-id="6fd97-132">Domande?</span><span class="sxs-lookup"><span data-stu-id="6fd97-132">Got a question?</span></span> <span data-ttu-id="6fd97-133">Commenti e suggerimenti?</span><span class="sxs-lookup"><span data-stu-id="6fd97-133">Have feedback?</span></span>

<span data-ttu-id="6fd97-134">Altre informazioni su PowerShell Gallery e PowerShellGet sono disponibili nella pagina [Introduzione](getting-started.md).</span><span class="sxs-lookup"><span data-stu-id="6fd97-134">More information about the PowerShell Gallery and PowerShellGet can be found in the [Getting Started](getting-started.md) page.</span></span> <span data-ttu-id="6fd97-135">Fornire commenti e suggerimenti e segnalare problemi usando [UserVoice](http://windowsserver.uservoice.com/forums/301869-powershell).</span><span class="sxs-lookup"><span data-stu-id="6fd97-135">Please provide feedback and report issues using [UserVoice](http://windowsserver.uservoice.com/forums/301869-powershell).</span></span>