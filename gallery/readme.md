---
ms.date: 2017-06-12
contributor: JKeithB
ms.topic: conceptual
keywords: raccolta,powershell,cmdlet,psgallery, psget
title: PowerShell Gallery
ms.openlocfilehash: 3e324f15b251822163c3ea9b6655767419a5ac4e
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 06/12/2017
---
# <a name="the-powershell-gallery"></a><span data-ttu-id="506d8-103">PowerShell Gallery</span><span class="sxs-lookup"><span data-stu-id="506d8-103">The PowerShell Gallery</span></span>

<span data-ttu-id="506d8-104">PowerShell Gallery è il repository centrale per i contenuti PowerShell.</span><span class="sxs-lookup"><span data-stu-id="506d8-104">The PowerShell Gallery is the central repository for PowerShell content.</span></span> <span data-ttu-id="506d8-105">In PowerShell Gallery è possibile trovare nuovi comandi di PowerShell o risorse DSC (Desired State Configuration).</span><span class="sxs-lookup"><span data-stu-id="506d8-105">You can find new PowerShell commands or Desired State Configuration (DSC) resources in the Gallery.</span></span>

## <a name="powershellget-overview"></a><span data-ttu-id="506d8-106">Panoramica di PowerShellGet</span><span class="sxs-lookup"><span data-stu-id="506d8-106">PowerShellGet Overview</span></span>

<span data-ttu-id="506d8-107">Il modulo PowerShellGet contiene i cmdlet per l'individuazione, l'installazione, l'aggiornamento e la pubblicazione di elementi PowerShell quali moduli, risorse DSC, capacità del ruolo e script di https://www.PowerShellGallery.com e altri repository privati.</span><span class="sxs-lookup"><span data-stu-id="506d8-107">PowerShellGet module contains cmdlets for discovering, installing, updating and publishing the PowerShell artifacts like Modules, DSC Resources, Role Capabilities and Scripts from the https://www.PowerShellGallery.com and other private repositories.</span></span>

## <a name="getting-started-with-the-gallery"></a><span data-ttu-id="506d8-108">Introduzione a PowerShell Gallery</span><span class="sxs-lookup"><span data-stu-id="506d8-108">Getting Started with the Gallery</span></span>

<span data-ttu-id="506d8-109">L'installazione degli elementi di PowerShell Gallery richiede la versione più recente del modulo PowerShellGet, disponibile in Windows 10, in Windows Management Framework (WMF) 5.0 o nel programma di installazione basato su MSI (per PowerShell 3 e 4).</span><span class="sxs-lookup"><span data-stu-id="506d8-109">Installing items from the Gallery requires the latest version of the PowerShellGet module, which is available in Windows 10, in Windows Management Framework (WMF) 5.0, or in the MSI-based installer (for PowerShell 3 and 4).</span></span>

- <span data-ttu-id="506d8-110">[**Ottenere Windows 10**](http://go.microsoft.com/fwlink/?LinkID=624830&clcid=0x409),</span><span class="sxs-lookup"><span data-stu-id="506d8-110">[**Get Windows 10**](http://go.microsoft.com/fwlink/?LinkID=624830&clcid=0x409),</span></span>
- <span data-ttu-id="506d8-111">[**Ottenere WMF 5.0**](http://go.microsoft.com/fwlink/?LinkId=398175) o</span><span class="sxs-lookup"><span data-stu-id="506d8-111">[**Get WMF 5.0**](http://go.microsoft.com/fwlink/?LinkId=398175), or</span></span>
- [<span data-ttu-id="506d8-112">**Ottenere il programma di installazione MSI**</span><span class="sxs-lookup"><span data-stu-id="506d8-112">**Get MSI Installer**</span></span>](http://go.microsoft.com/fwlink/?LinkID=746217&clcid=0x409)

<span data-ttu-id="506d8-113">Con la versione più recente del modulo [PowerShellGet](http://go.microsoft.com/fwlink/?LinkID=760387&clcid=0x409), è possibile:</span><span class="sxs-lookup"><span data-stu-id="506d8-113">With the latest [PowerShellGet](http://go.microsoft.com/fwlink/?LinkID=760387&clcid=0x409) module, you can:</span></span>

-   <span data-ttu-id="506d8-114">Cercare elementi in PowerShell Gallery con [**Find-Module**](http://go.microsoft.com/fwlink/?LinkID=760387&clcid=0x409) e [**Find-Script**](http://go.microsoft.com/fwlink/?LinkID=760387&clcid=0x409)</span><span class="sxs-lookup"><span data-stu-id="506d8-114">Search through items in the Gallery with [**Find-Module**](http://go.microsoft.com/fwlink/?LinkID=760387&clcid=0x409) and [**Find-Script**](http://go.microsoft.com/fwlink/?LinkID=760387&clcid=0x409)</span></span>
-   <span data-ttu-id="506d8-115">Salvare elementi nel sistema da PowerShell Gallery con [**Save-Module**](http://go.microsoft.com/fwlink/?LinkID=760387&clcid=0x409) e [**Save-Script**](http://go.microsoft.com/fwlink/?LinkID=760387&clcid=0x409)</span><span class="sxs-lookup"><span data-stu-id="506d8-115">Save items to your system from the Gallery with [**Save-Module**](http://go.microsoft.com/fwlink/?LinkID=760387&clcid=0x409) and [**Save-Script**](http://go.microsoft.com/fwlink/?LinkID=760387&clcid=0x409)</span></span>
-   <span data-ttu-id="506d8-116">Installare elementi da PowerShell Gallery con [**Install-Module**](http://go.microsoft.com/fwlink/?LinkID=760387&clcid=0x409) e [**Install-Script**](http://go.microsoft.com/fwlink/?LinkID=760387&clcid=0x409)</span><span class="sxs-lookup"><span data-stu-id="506d8-116">Install items from the Gallery with [**Install-Module**](http://go.microsoft.com/fwlink/?LinkID=760387&clcid=0x409) and [**Install-Script**](http://go.microsoft.com/fwlink/?LinkID=760387&clcid=0x409)</span></span>
-   <span data-ttu-id="506d8-117">Caricare elementi in PowerShell Gallery con [**Publish-Module**](http://go.microsoft.com/fwlink/?LinkID=760387&clcid=0x409) e [**Publish-Script**](http://go.microsoft.com/fwlink/?LinkID=760387&clcid=0x409)</span><span class="sxs-lookup"><span data-stu-id="506d8-117">Upload items to the Gallery with [**Publish-Module**](http://go.microsoft.com/fwlink/?LinkID=760387&clcid=0x409) and [**Publish-Script**](http://go.microsoft.com/fwlink/?LinkID=760387&clcid=0x409)</span></span>
-   <span data-ttu-id="506d8-118">Aggiungere il proprio repository personalizzato con [**Register-PSRepository**](http://go.microsoft.com/fwlink/?LinkID=760387&clcid=0x409)</span><span class="sxs-lookup"><span data-stu-id="506d8-118">Add your own custom repository with [**Register-PSRepository**](http://go.microsoft.com/fwlink/?LinkID=760387&clcid=0x409)</span></span>

<span data-ttu-id="506d8-119">Per altre informazioni su come usare i comandi PowerShellGet con PowerShell Gallery, consultare la pagina [Introduzione](psgallery/psgallery_gettingstarted.md).</span><span class="sxs-lookup"><span data-stu-id="506d8-119">Check out the [Getting Started](psgallery/psgallery_gettingstarted.md) page for more information on how to use PowerShellGet commands with the Gallery.</span></span> <span data-ttu-id="506d8-120">È inoltre possibile eseguire *Update-Help -Module PowerShellGet* per installare la Guida locale per tali comandi.</span><span class="sxs-lookup"><span data-stu-id="506d8-120">You can also run *Update-Help -Module PowerShellGet* to install local help for these commands.</span></span>

## <a name="supported-operating-systems"></a><span data-ttu-id="506d8-121">Sistemi operativi supportati</span><span class="sxs-lookup"><span data-stu-id="506d8-121">Supported Operating Systems</span></span>

<span data-ttu-id="506d8-122">Il modulo **PowerShellGet** richiede **PowerShell 3.0 o versione successiva**.</span><span class="sxs-lookup"><span data-stu-id="506d8-122">The **PowerShellGet** module requires **PowerShell 3.0 or newer**.</span></span>

<span data-ttu-id="506d8-123">Di conseguenza, **PowerShellGet** richiede uno dei sistemi operativi seguenti:</span><span class="sxs-lookup"><span data-stu-id="506d8-123">Therefore, **PowerShellGet** requires one of the following operating systems:</span></span>

- <span data-ttu-id="506d8-124">Windows 10</span><span class="sxs-lookup"><span data-stu-id="506d8-124">Windows 10</span></span>
- <span data-ttu-id="506d8-125">Windows 8.1 Pro</span><span class="sxs-lookup"><span data-stu-id="506d8-125">Windows 8.1 Pro</span></span>
- <span data-ttu-id="506d8-126">Windows 8.1 Enterprise</span><span class="sxs-lookup"><span data-stu-id="506d8-126">Windows 8.1 Enterprise</span></span>
- <span data-ttu-id="506d8-127">Windows 7 SP1</span><span class="sxs-lookup"><span data-stu-id="506d8-127">Windows 7 SP1</span></span>
- <span data-ttu-id="506d8-128">Windows Server 2016 TP5</span><span class="sxs-lookup"><span data-stu-id="506d8-128">Windows Server 2016 TP5</span></span>
- <span data-ttu-id="506d8-129">Windows Server 2012 R2</span><span class="sxs-lookup"><span data-stu-id="506d8-129">Windows Server 2012 R2</span></span>
- <span data-ttu-id="506d8-130">Windows Server 2008 R2 SP1</span><span class="sxs-lookup"><span data-stu-id="506d8-130">Windows Server 2008 R2 SP1</span></span>

<span data-ttu-id="506d8-131">**PowerShellGet** richiede inoltre .NET Framework 4.5 o versione successiva.</span><span class="sxs-lookup"><span data-stu-id="506d8-131">**PowerShellGet** also  requires .NET Framework 4.5 or above.</span></span> <span data-ttu-id="506d8-132">È possibile installare .NET Framework 4.5 o versione successiva da [qui](https://msdn.microsoft.com/en-us/library/5a4x27ek.aspx).</span><span class="sxs-lookup"><span data-stu-id="506d8-132">You can install .NET Framework 4.5 or above from [here](https://msdn.microsoft.com/en-us/library/5a4x27ek.aspx).</span></span>


## <a name="got-a-question-have-feedback"></a><span data-ttu-id="506d8-133">Domande?</span><span class="sxs-lookup"><span data-stu-id="506d8-133">Got a question?</span></span> <span data-ttu-id="506d8-134">Commenti e suggerimenti?</span><span class="sxs-lookup"><span data-stu-id="506d8-134">Have feedback?</span></span>

<span data-ttu-id="506d8-135">Altre informazioni su PowerShell Gallery e PowerShellGet sono disponibili nella pagina [Introduzione](psgallery/psgallery_gettingstarted.md).</span><span class="sxs-lookup"><span data-stu-id="506d8-135">More information about the PowerShell Gallery and PowerShellGet can be found in the [Getting Started](psgallery/psgallery_gettingstarted.md) page.</span></span> <span data-ttu-id="506d8-136">Fornire commenti e suggerimenti e segnalare problemi usando [UserVoice](http://windowsserver.uservoice.com/forums/301869-powershell).</span><span class="sxs-lookup"><span data-stu-id="506d8-136">Please provide feedback and report issues using [UserVoice](http://windowsserver.uservoice.com/forums/301869-powershell).</span></span>

