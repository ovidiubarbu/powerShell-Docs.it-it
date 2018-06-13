---
ms.date: 06/12/2017
contributor: JKeithB
keywords: raccolta,powershell,cmdlet,psgallery, psget
title: PowerShell Gallery
ms.openlocfilehash: dc7e8dd7e4d96d8424a62cb3256c3164b63a3684
ms.sourcegitcommit: 01d6985ed190a222e9da1da41596f524f607a5bc
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 06/07/2018
ms.locfileid: "34482931"
---
# <a name="the-powershell-gallery"></a><span data-ttu-id="32124-103">PowerShell Gallery</span><span class="sxs-lookup"><span data-stu-id="32124-103">The PowerShell Gallery</span></span>

<span data-ttu-id="32124-104">PowerShell Gallery è il repository centrale per i contenuti PowerShell.</span><span class="sxs-lookup"><span data-stu-id="32124-104">The PowerShell Gallery is the central repository for PowerShell content.</span></span> <span data-ttu-id="32124-105">Al suo interno è possibile trovare utili moduli di PowerShell che contengono comandi di PowerShell o risorse DSC (Desired State Configuration).</span><span class="sxs-lookup"><span data-stu-id="32124-105">In it, you can find useful PowerShell modules containing PowerShell commands and Desired State Configuration (DSC) resources.</span></span>
<span data-ttu-id="32124-106">Sono anche disponibili script di PowerShell, alcuni dei quali possono contenere flussi di lavoro di PowerShell e descrivono e stabiliscono la sequenza di un set di attività.</span><span class="sxs-lookup"><span data-stu-id="32124-106">You can also find PowerShell scripts, some of which may contain PowerShell workflows, and which outline a set of tasks and provide sequencing for those tasks.</span></span> <span data-ttu-id="32124-107">Alcuni di questi elementi vengono creati da Microsoft, altri dalla community di PowerShell.</span><span class="sxs-lookup"><span data-stu-id="32124-107">Some of these items are authored by Microsoft, and others are authored by the PowerShell community.</span></span>

## <a name="powershellget-overview"></a><span data-ttu-id="32124-108">Panoramica di PowerShellGet</span><span class="sxs-lookup"><span data-stu-id="32124-108">PowerShellGet Overview</span></span>

<span data-ttu-id="32124-109">Il modulo PowerShellGet contiene i cmdlet per l'individuazione, l'installazione, l'aggiornamento e la pubblicazione di elementi PowerShell quali moduli, risorse DSC, capacità del ruolo e script da [PowerShell Gallery](https://www.PowerShellGallery.com) e altri repository privati.</span><span class="sxs-lookup"><span data-stu-id="32124-109">The PowerShellGet module contains cmdlets for discovering, installing, updating and publishing PowerShell artifacts such as Modules, DSC Resources, Role Capabilities and Scripts from the [PowerShell Gallery](https://www.PowerShellGallery.com) and other private repositories.</span></span>

## <a name="getting-started-with-the-gallery"></a><span data-ttu-id="32124-110">Introduzione a PowerShell Gallery</span><span class="sxs-lookup"><span data-stu-id="32124-110">Getting Started with the Gallery</span></span>

<span data-ttu-id="32124-111">L'installazione di elementi di Gallery richiede la versione più recente del modulo PowerShellGet.</span><span class="sxs-lookup"><span data-stu-id="32124-111">Installing items from the Gallery requires the latest version of the PowerShellGet module.</span></span>
<span data-ttu-id="32124-112">Per istruzioni complete, vedere [Installazione di PowerShellGet](installing-psget.md).</span><span class="sxs-lookup"><span data-stu-id="32124-112">See [Installing PowerShellGet](installing-psget.md) for complete instructions.</span></span>

<span data-ttu-id="32124-113">Per altre informazioni su come usare i comandi PowerShellGet con PowerShell Gallery, consultare la pagina [Introduzione](getting-started.md).</span><span class="sxs-lookup"><span data-stu-id="32124-113">Check out the [Getting Started](getting-started.md) page for more information on how to use PowerShellGet commands with the Gallery.</span></span> <span data-ttu-id="32124-114">È inoltre possibile eseguire *Update-Help -Module PowerShellGet* per installare la Guida locale per tali comandi.</span><span class="sxs-lookup"><span data-stu-id="32124-114">You can also run *Update-Help -Module PowerShellGet* to install local help for these commands.</span></span>

## <a name="supported-operating-systems"></a><span data-ttu-id="32124-115">Sistemi operativi supportati</span><span class="sxs-lookup"><span data-stu-id="32124-115">Supported Operating Systems</span></span>

<span data-ttu-id="32124-116">Il modulo **PowerShellGet** richiede **Windows PowerShell 3.0 o versione successiva** o **PowerShell Core 6.0 o versione successiva**.</span><span class="sxs-lookup"><span data-stu-id="32124-116">The **PowerShellGet** module requires **Windows PowerShell 3.0 or newer**, or **PowerShell Core 6.0 or newer**.</span></span>

<span data-ttu-id="32124-117">È disponibile una versione appropriata di **Windows PowerShell** per questi sistemi operativi:</span><span class="sxs-lookup"><span data-stu-id="32124-117">A suitable version of **Windows PowerShell** is available for these operating systems:</span></span>

- <span data-ttu-id="32124-118">Windows 10</span><span class="sxs-lookup"><span data-stu-id="32124-118">Windows 10</span></span>
- <span data-ttu-id="32124-119">Windows 8.1 Pro</span><span class="sxs-lookup"><span data-stu-id="32124-119">Windows 8.1 Pro</span></span>
- <span data-ttu-id="32124-120">Windows 8.1 Enterprise</span><span class="sxs-lookup"><span data-stu-id="32124-120">Windows 8.1 Enterprise</span></span>
- <span data-ttu-id="32124-121">Windows 7 SP1</span><span class="sxs-lookup"><span data-stu-id="32124-121">Windows 7 SP1</span></span>
- <span data-ttu-id="32124-122">Windows Server 2016</span><span class="sxs-lookup"><span data-stu-id="32124-122">Windows Server 2016</span></span>
- <span data-ttu-id="32124-123">Windows Server 2012 R2</span><span class="sxs-lookup"><span data-stu-id="32124-123">Windows Server 2012 R2</span></span>
- <span data-ttu-id="32124-124">Windows Server 2008 R2 SP1</span><span class="sxs-lookup"><span data-stu-id="32124-124">Windows Server 2008 R2 SP1</span></span>

<span data-ttu-id="32124-125">**PowerShellGet** richiede anche .NET Framework 4.5 o versione successiva.</span><span class="sxs-lookup"><span data-stu-id="32124-125">**PowerShellGet** also requires .NET Framework 4.5 or above.</span></span> <span data-ttu-id="32124-126">È possibile installare .NET Framework 4.5 o versione successiva da [qui](https://msdn.microsoft.com/library/5a4x27ek.aspx).</span><span class="sxs-lookup"><span data-stu-id="32124-126">You can install .NET Framework 4.5 or above from [here](https://msdn.microsoft.com/library/5a4x27ek.aspx).</span></span>

<span data-ttu-id="32124-127">**PowerShell Core** supporta molti sistemi operativi.</span><span class="sxs-lookup"><span data-stu-id="32124-127">**PowerShell Core** supports many operating systems.</span></span> <span data-ttu-id="32124-128">Vedere [questo articolo](https://blogs.msdn.microsoft.com/powershell/2018/01/10/powershell-core-6-0-generally-available-ga-and-supported/) per un elenco completo.</span><span class="sxs-lookup"><span data-stu-id="32124-128">See [this article](https://blogs.msdn.microsoft.com/powershell/2018/01/10/powershell-core-6-0-generally-available-ga-and-supported/) for a full list.</span></span>

<span data-ttu-id="32124-129">Molti moduli ospitati nella raccolta supporteranno sistemi operativi diversi e hanno requisiti aggiuntivi.</span><span class="sxs-lookup"><span data-stu-id="32124-129">Many modules hosted in the gallery will support different OSes and have additional requirements.</span></span> <span data-ttu-id="32124-130">Per altre informazioni, vedere la documentazione per i moduli.</span><span class="sxs-lookup"><span data-stu-id="32124-130">Please refer to the documentation for the modules for more information.</span></span>

## <a name="got-a-question-have-feedback"></a><span data-ttu-id="32124-131">Domande?</span><span class="sxs-lookup"><span data-stu-id="32124-131">Got a question?</span></span> <span data-ttu-id="32124-132">Commenti e suggerimenti?</span><span class="sxs-lookup"><span data-stu-id="32124-132">Have feedback?</span></span>

<span data-ttu-id="32124-133">Altre informazioni su PowerShell Gallery e PowerShellGet sono disponibili nella pagina [Introduzione](getting-started.md).</span><span class="sxs-lookup"><span data-stu-id="32124-133">More information about the PowerShell Gallery and PowerShellGet can be found in the [Getting Started](getting-started.md) page.</span></span> <span data-ttu-id="32124-134">Fornire commenti e suggerimenti e segnalare problemi usando [UserVoice](http://windowsserver.uservoice.com/forums/301869-powershell).</span><span class="sxs-lookup"><span data-stu-id="32124-134">Please provide feedback and report issues using [UserVoice](http://windowsserver.uservoice.com/forums/301869-powershell).</span></span>
