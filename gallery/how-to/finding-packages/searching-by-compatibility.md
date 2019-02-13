---
ms.date: 12/11/2018
contributor: JKeithB, SydneyhSmith
keywords: gallery,powershell,cmdlet,psgallery
title: Pacchetti con sistema operativo o le edizioni di PowerShell compatibili
ms.openlocfilehash: 8230866561d3021379a48cc2c83fb4104a4058c1
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MTE95
ms.contentlocale: it-IT
ms.lasthandoff: 02/03/2019
ms.locfileid: "55680932"
---
# <a name="packages-with-compatible-powershell-editions-or-operating-systems"></a><span data-ttu-id="30790-103">Pacchetti con i sistemi operativi o le edizioni di PowerShell compatibili</span><span class="sxs-lookup"><span data-stu-id="30790-103">Packages with compatible PowerShell Editions or Operating Systems</span></span>

<span data-ttu-id="30790-104">A partire dalla versione 5.1, PowerShell è disponibile in diverse edizioni che indicano vari set di funzionalità e compatibilità della piattaforma.</span><span class="sxs-lookup"><span data-stu-id="30790-104">Starting with version 5.1, PowerShell is available in different editions which denote varying feature sets and platform compatibilities.</span></span>

## <a name="searching-by-powershell-edition"></a><span data-ttu-id="30790-105">La ricerca per edizione di PowerShell</span><span class="sxs-lookup"><span data-stu-id="30790-105">Searching by PowerShell Edition</span></span> 
<span data-ttu-id="30790-106">Le due edizioni di Powershell sono:</span><span class="sxs-lookup"><span data-stu-id="30790-106">The two editions of Powershell are:</span></span>
- <span data-ttu-id="30790-107">**Desktop Edition:** è basata su .NET Framework e fornisce compatibilità con script e moduli destinati a versioni di PowerShell che eseguono edizioni footprint complete di Windows, ad esempio Server Core e Windows Desktop.</span><span class="sxs-lookup"><span data-stu-id="30790-107">**Desktop Edition:** Built on .NET Framework and provides compatibility with scripts and modules targeting versions of PowerShell running on full footprint editions of Windows such as Server Core and Windows Desktop.</span></span>
- <span data-ttu-id="30790-108">**Core Edition:** è basata su .NET Core e fornisce compatibilità con script e moduli destinati a versioni di PowerShell che eseguono edizioni footprint ridotte di Windows, ad esempio Nano Server e Windows IoT.</span><span class="sxs-lookup"><span data-stu-id="30790-108">**Core Edition:** Built on .NET Core and provides compatibility with scripts and modules targeting versions of PowerShell running on reduced footprint editions of Windows such as Nano Server and Windows IoT.</span></span>

### <a name="powershell-gallery-allows-you-to-filter-packages-compatible-for-specific-powershell-editions"></a><span data-ttu-id="30790-109">PowerShell Gallery consente di filtrare i pacchetti compatibili per specifiche le edizioni di PowerShell</span><span class="sxs-lookup"><span data-stu-id="30790-109">PowerShell Gallery allows you to filter packages compatible for specific PowerShell Editions</span></span>

<span data-ttu-id="30790-110">Se dispone di un pacchetto compatibile PSEditions specificato, sono elencati come parte di 'Edizioni di PowerShell' nella pagina di visualizzazione del pacchetto e anche nei risultati di pacchetti.</span><span class="sxs-lookup"><span data-stu-id="30790-110">If a package has compatible PSEditions specified, they are listed as part of 'PowerShell Editions' in the package display page and also in packages results.</span></span>
<span data-ttu-id="30790-111">È anche possibile cercare pacchetti compatibili con PowerShell.</span><span class="sxs-lookup"><span data-stu-id="30790-111">You can also search for compatible packages using PowerShell.</span></span>

![Pagina di visualizzazione dell'elemento con PSEditions](../../Images/packagedisplaypagewithpseditions.PNG)

### <a name="search-for-packages-in-the-gallery-ui-that-work-on-powershell-core"></a><span data-ttu-id="30790-113">Cercare i pacchetti nell'interfaccia utente della raccolta che funzionano in PowerShell Core</span><span class="sxs-lookup"><span data-stu-id="30790-113">Search for packages in the gallery UI that work on PowerShell Core</span></span>

<span data-ttu-id="30790-114">Usare Tags:"PSEdition_Desktop" e Tags:"PSEdition_Core" per filtrare i pacchetti in PowerShell Gallery.</span><span class="sxs-lookup"><span data-stu-id="30790-114">Use Tags:"PSEdition_Desktop" and Tags:"PSEdition_Core" to filters the packages on PowerShell Gallery.</span></span>

### <a name="use-tagspseditioncore-to-search-items-compatible-with-powershell-core-edition"></a><span data-ttu-id="30790-115">Usare Tags:"PSEdition_Core" per cercare elementi compatibili con l'edizione Core di PowerShell.</span><span class="sxs-lookup"><span data-stu-id="30790-115">Use Tags:"PSEdition_Core" to search items compatible with PowerShell Core Edition.</span></span>

![Cercare elementi compatibili con l'edizione Core di PowerShell nei risultati](../../Images/searchresultswithpseditions.PNG)

### <a name="use-tagspseditiondesktop-to-search-items-compatible-with-powershell-desktop-edition"></a><span data-ttu-id="30790-117">Usare Tags:"PSEdition_Desktop" per cercare elementi compatibili con l'edizione Desktop di PowerShell.</span><span class="sxs-lookup"><span data-stu-id="30790-117">Use Tags:"PSEdition_Desktop" to search items compatible with PowerShell Desktop Edition.</span></span>

![Cercare elementi compatibili con l'edizione Desktop di PowerShell nei risultati](../../Images/searchresultswithpseditionsdesktop.PNG)

### <a name="search-for-packages-to-find-compatible-editions-using-powershell"></a><span data-ttu-id="30790-119">Cercare i pacchetti da trovare compatibili con PowerShell</span><span class="sxs-lookup"><span data-stu-id="30790-119">Search for packages to find compatible editions using PowerShell</span></span>
<span data-ttu-id="30790-120">È possibile specificare i tag per filtrare per l'edizione di PowerShell e il sistema operativo.</span><span class="sxs-lookup"><span data-stu-id="30790-120">You can specify tags to filter for the PowerShell edition and OS.</span></span> <span data-ttu-id="30790-121">Si utilizza il `Find-Package` cmdlet specificando il `-Tag` parametro per specificare l'edizione (e sistemi operativi) di destinazione.</span><span class="sxs-lookup"><span data-stu-id="30790-121">You use the `Find-Package` cmdlet specifying the `-Tag` parameter to specify the edition (and OS) you are targeting.</span></span>
<span data-ttu-id="30790-122">Così:</span><span class="sxs-lookup"><span data-stu-id="30790-122">Like this:</span></span>

```powershell
# Find modules compatible with PowerShell Core:
Find-Module -Tag PSEdition_Core

# Find modules compatible with PowerShell Core on Linux:
Find-Module -Tag PSEdition_Core, Linux
```

## <a name="searching-by-operating-system"></a><span data-ttu-id="30790-123">La ricerca dal sistema operativo</span><span class="sxs-lookup"><span data-stu-id="30790-123">Searching by Operating System</span></span> 

<span data-ttu-id="30790-124">Poiché PowerShell Core è disponibile per Windows, Linux e MacOS, nella raccolta di pacchetti possono essere progettati per qualsiasi combinazione di questi sistemi operativi.</span><span class="sxs-lookup"><span data-stu-id="30790-124">Since PowerShell Core is available for Windows, Linux, and MacOS, packages in the Gallery may be designed for any combination of these operating systems.</span></span> <span data-ttu-id="30790-125">Interfaccia utente della raccolta utilizzare i tag seguenti di ricerca per trovare i pacchetti contrassegnati dal sistema operativo:</span><span class="sxs-lookup"><span data-stu-id="30790-125">In the gallery UI use the following searchs tags to find packages tagged by operating system:</span></span>

- <span data-ttu-id="30790-126">Tag: "Windows"</span><span class="sxs-lookup"><span data-stu-id="30790-126">Tags: "Windows"</span></span>
- <span data-ttu-id="30790-127">Tag: "Linux"</span><span class="sxs-lookup"><span data-stu-id="30790-127">Tags: "Linux"</span></span>
- <span data-ttu-id="30790-128">Tag: "MacOS"</span><span class="sxs-lookup"><span data-stu-id="30790-128">Tags: "MacOS"</span></span> 

<span data-ttu-id="30790-129">È possibile specificare questi tag nella `Find-Module` e altri cmdlet nel modulo PowerShellGet, simile al seguente:</span><span class="sxs-lookup"><span data-stu-id="30790-129">You can specify these tags on `Find-Module` (and other cmdlets in the PowerShellGet module), like this:</span></span>

```powershell
# Find Modules compatible with Windows
Find-Module -Tag Linux
```

## <a name="searching-for-multiple-compatibilities"></a><span data-ttu-id="30790-130">La ricerca di compatibilità più</span><span class="sxs-lookup"><span data-stu-id="30790-130">Searching for Multiple Compatibilities</span></span>

<span data-ttu-id="30790-131">È possibile cercare un pacchetto con più di compatibilità usando la sintassi:</span><span class="sxs-lookup"><span data-stu-id="30790-131">You can look for a package that has multiple compatibilities by using the syntax:</span></span> 

<span data-ttu-id="30790-132">Tag: "Compatibility1" "Compatibility2"</span><span class="sxs-lookup"><span data-stu-id="30790-132">Tags: "Compatibility1" "Compatibility2"</span></span> 

<span data-ttu-id="30790-133">Ad esempio, se si sta cercando un pacchetto con compatibilità di Core di PowerShell che viene eseguito nei computer personali Windows e Linux, usare i tag di ricerca:</span><span class="sxs-lookup"><span data-stu-id="30790-133">For example, if you are looking for a package with PowerShell Core Compatibility that runs on both my Windows and Linux machines, use the search tags:</span></span>

<span data-ttu-id="30790-134">Tag: "PSEdition_Core" "Windows" "Linux"</span><span class="sxs-lookup"><span data-stu-id="30790-134">Tags: "PSEdition_Core" "Windows" "Linux"</span></span> 

<span data-ttu-id="30790-135">Per eseguire una ricerca tramite PowerShell, è possibile usare il `Find-Module` e gli altri cmdlet nel modulo PowerShellGet, simile al seguente:</span><span class="sxs-lookup"><span data-stu-id="30790-135">To search using PowerShell, you can use the `Find-Module` (and the other cmdlets in the PowerShellGet module), like this:</span></span>

```powewrshell
# Find scripts compatible with PowerShell Core, Windows, and Linux
Find-Script -Tag PSEdition_Core,Linux,Windows

# Find modules compatible with PowerSHellCore and MacOS
Find-Module -Tag PSEdition_Core,MacOS
```

## <a name="more-details-on-authoring-and-finding-the-packages-with-compatible-powershell-editions"></a><span data-ttu-id="30790-136">Altre informazioni sulla creazione e la ricerca di pacchetti con edizioni di PowerShell compatibili</span><span class="sxs-lookup"><span data-stu-id="30790-136">More details on authoring and finding the packages with compatible PowerShell Editions</span></span>

- [<span data-ttu-id="30790-137">Moduli con edizioni di PS</span><span class="sxs-lookup"><span data-stu-id="30790-137">Modules with PSEditions</span></span>](../../concepts/module-psedition-support.md)
- [<span data-ttu-id="30790-138">Script con PSEditions</span><span class="sxs-lookup"><span data-stu-id="30790-138">Scripts with PSEditions</span></span>](../../concepts/script-psedition-support.md)
