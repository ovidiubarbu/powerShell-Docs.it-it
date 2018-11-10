---
ms.date: 06/12/2017
contributor: JKeithB
keywords: gallery,powershell,cmdlet,psgallery
title: Pacchetti con edizioni di PowerShell compatibili
ms.openlocfilehash: e16cfb0ee30e344c9399bec2985baafc5a252fd7
ms.sourcegitcommit: 98b7cfd8ad5718efa8e320526ca76c3cc4141d78
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 10/25/2018
ms.locfileid: "50003786"
---
# <a name="packages-with-compatible-powershell-editions"></a><span data-ttu-id="48a6c-103">Pacchetti con edizioni di PowerShell compatibili</span><span class="sxs-lookup"><span data-stu-id="48a6c-103">Packages with compatible PowerShell Editions</span></span>

<span data-ttu-id="48a6c-104">A partire dalla versione 5.1, PowerShell è disponibile in diverse edizioni che indicano vari set di funzionalità e compatibilità della piattaforma.</span><span class="sxs-lookup"><span data-stu-id="48a6c-104">Starting with version 5.1, PowerShell is available in different editions which denote varying feature sets and platform compatibility.</span></span>

- <span data-ttu-id="48a6c-105">**Desktop Edition:** è basata su .NET Framework e fornisce compatibilità con script e moduli destinati a versioni di PowerShell che eseguono edizioni footprint complete di Windows, ad esempio Server Core e Windows Desktop.</span><span class="sxs-lookup"><span data-stu-id="48a6c-105">**Desktop Edition:** Built on .NET Framework and provides compatibility with scripts and modules targeting versions of PowerShell running on full footprint editions of Windows such as Server Core and Windows Desktop.</span></span>
- <span data-ttu-id="48a6c-106">**Core Edition:** è basata su .NET Core e fornisce compatibilità con script e moduli destinati a versioni di PowerShell che eseguono edizioni footprint ridotte di Windows, ad esempio Nano Server e Windows IoT.</span><span class="sxs-lookup"><span data-stu-id="48a6c-106">**Core Edition:** Built on .NET Core and provides compatibility with scripts and modules targeting versions of PowerShell running on reduced footprint editions of Windows such as Nano Server and Windows IoT.</span></span>

## <a name="powershell-gallery-extracts-supported-pseditions-metadata-and-allows-you-to-filters-the-packages-compatible-for-specific-powershell-editions"></a><span data-ttu-id="48a6c-107">PowerShell Gallery estrae i metadati PSEditions supportati e consente di filtrare i pacchetti compatibili per specifiche edizioni di PowerShell</span><span class="sxs-lookup"><span data-stu-id="48a6c-107">PowerShell Gallery extracts supported PSEditions metadata and allows you to filters the packages compatible for specific PowerShell Editions</span></span>

<span data-ttu-id="48a6c-108">Se per un pacchetto è specificato un valore PSEditions compatibile, verrà elencato come parte di 'PowerShell Editions' (Edizioni di PowerShell) nella pagina di visualizzazione del pacchetto e anche nei risultati dei pacchetti.</span><span class="sxs-lookup"><span data-stu-id="48a6c-108">If a package has compatible PSEditions specified, they will be listed as part of 'PowerShell Editions' in the package display page and also in packages results.</span></span>

![Pagina di visualizzazione dell'elemento con PSEditions](../../Images/manual_package_download.png)

## <a name="search-for-packages-in-the-gallery-ui-which-works-on-powershellcore"></a><span data-ttu-id="48a6c-110">Cercare pacchetti compatibili con PowerShellCore nell'interfaccia utente di PowerShell Gallery</span><span class="sxs-lookup"><span data-stu-id="48a6c-110">Search for packages in the gallery UI which works on PowerShellCore</span></span>

<span data-ttu-id="48a6c-111">Usare Tags:"PSEdition_Desktop" e Tags:"PSEdition_Core" per filtrare i pacchetti in PowerShell Gallery.</span><span class="sxs-lookup"><span data-stu-id="48a6c-111">Use Tags:"PSEdition_Desktop" and Tags:"PSEdition_Core" to filters the packages on PowerShell Gallery.</span></span>

### <a name="use-tagspseditioncore-to-search-items-compatible-with-powershell-core-edition"></a><span data-ttu-id="48a6c-112">Usare Tags:"PSEdition_Core" per cercare elementi compatibili con l'edizione Core di PowerShell.</span><span class="sxs-lookup"><span data-stu-id="48a6c-112">Use Tags:"PSEdition_Core" to search items compatible with PowerShell Core Edition.</span></span>

![Cercare elementi compatibili con l'edizione Core di PowerShell nei risultati](../../Images/SearchResultsWithPSEditions.PNG)

### <a name="use-tagspseditiondesktop-to-search-items-compatible-with-powershell-desktop-edition"></a><span data-ttu-id="48a6c-114">Usare Tags:"PSEdition_Desktop" per cercare elementi compatibili con l'edizione Desktop di PowerShell.</span><span class="sxs-lookup"><span data-stu-id="48a6c-114">Use Tags:"PSEdition_Desktop" to search items compatible with PowerShell Desktop Edition.</span></span>

![Cercare elementi compatibili con l'edizione Desktop di PowerShell nei risultati](../../Images/SearchResultsWithPSEdition-Desktop.PNG)

## <a name="more-details-on-authoring-and-finding-the-packages-with-compatible-powershell-editions"></a><span data-ttu-id="48a6c-116">Altre informazioni sulla creazione e la ricerca di pacchetti con edizioni di PowerShell compatibili</span><span class="sxs-lookup"><span data-stu-id="48a6c-116">More details on authoring and finding the packages with compatible PowerShell Editions</span></span>

- [<span data-ttu-id="48a6c-117">Moduli con edizioni di PS</span><span class="sxs-lookup"><span data-stu-id="48a6c-117">Modules with PSEditions</span></span>](../../concepts/module-psedition-support.md)
- [<span data-ttu-id="48a6c-118">Script con PSEditions</span><span class="sxs-lookup"><span data-stu-id="48a6c-118">Scripts with PSEditions</span></span>](../../concepts/script-psedition-support.md)
