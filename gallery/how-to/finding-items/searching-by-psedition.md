---
ms.date: 06/12/2017
contributor: JKeithB
ms.topic: conceptual
keywords: gallery,powershell,cmdlet,psgallery
title: Elementi con versioni di PowerShell compatibili
ms.openlocfilehash: dd2c67417994e960845f7cef09320a0f688a0212
ms.sourcegitcommit: e9ad4d85fd7eb72fb5bc37f6ca3ae1282ae3c6d7
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/10/2018
---
# <a name="items-with-compatible-powershell-editions"></a><span data-ttu-id="9b8d5-103">Elementi con versioni di PowerShell compatibili</span><span class="sxs-lookup"><span data-stu-id="9b8d5-103">Items with compatible PowerShell Editions</span></span>

<span data-ttu-id="9b8d5-104">A partire dalla versione 5.1, PowerShell è disponibile in diverse edizioni che indicano vari set di funzionalità e compatibilità della piattaforma.</span><span class="sxs-lookup"><span data-stu-id="9b8d5-104">Starting with version 5.1, PowerShell is available in different editions which denote varying feature sets and platform compatibility.</span></span>

- <span data-ttu-id="9b8d5-105">**Desktop Edition:** è basata su .NET Framework e fornisce compatibilità con script e moduli destinati a versioni di PowerShell che eseguono edizioni footprint complete di Windows, ad esempio Server Core e Windows Desktop.</span><span class="sxs-lookup"><span data-stu-id="9b8d5-105">**Desktop Edition:** Built on .NET Framework and provides compatibility with scripts and modules targeting versions of PowerShell running on full footprint editions of Windows such as Server Core and Windows Desktop.</span></span>
- <span data-ttu-id="9b8d5-106">**Core Edition:** è basata su .NET Core e fornisce compatibilità con script e moduli destinati a versioni di PowerShell che eseguono edizioni footprint ridotte di Windows, ad esempio Nano Server e Windows IoT.</span><span class="sxs-lookup"><span data-stu-id="9b8d5-106">**Core Edition:** Built on .NET Core and provides compatibility with scripts and modules targeting versions of PowerShell running on reduced footprint editions of Windows such as Nano Server and Windows IoT.</span></span>

## <a name="powershell-gallery-extracts-supported-pseditions-metadata-and-allows-you-to-filters-the-items-compatible-for-specific-powershell-editions"></a><span data-ttu-id="9b8d5-107">PowerShell Gallery estrae i metadati PSEditions supportati e consente di filtrare gli elementi compatibili per specifiche le edizioni di PowerShell</span><span class="sxs-lookup"><span data-stu-id="9b8d5-107">PowerShell Gallery extracts supported PSEditions metadata and allows you to filters the items compatible for specific PowerShell Editions</span></span>

<span data-ttu-id="9b8d5-108">Se per un elemento è specificato un valore PSEditions compatibile, verrà elencato come parte di "Edizioni di PowerShell" nella pagina di visualizzazione dell'elemento e anche nei risultati degli elementi.</span><span class="sxs-lookup"><span data-stu-id="9b8d5-108">If an item has compatible PSEditions specified, they will be listed as part of 'PowerShell Editions' in the item display page and also in items results.</span></span>

![Pagina di visualizzazione dell'elemento con PSEditions](../../Images/ItemDisplayPageWithPSEditions.PNG)

## <a name="search-for-items-in-the-gallery-ui-which-works-on-powershellcore"></a><span data-ttu-id="9b8d5-110">Cercare elementi compatibili con PowerShellCore nell'interfaccia utente della raccolta</span><span class="sxs-lookup"><span data-stu-id="9b8d5-110">Search for items in the gallery UI which works on PowerShellCore</span></span>

<span data-ttu-id="9b8d5-111">Usare Tags:"PSEdition_Desktop" e Tags:"PSEdition_Core" per filtrare gli elementi in PowerShell Gallery.</span><span class="sxs-lookup"><span data-stu-id="9b8d5-111">Use Tags:"PSEdition_Desktop" and Tags:"PSEdition_Core" to filters the items on PowerShell Gallery.</span></span>

### <a name="use-tagspseditioncore-to-search-items-compatible-with-powershell-core-edition"></a><span data-ttu-id="9b8d5-112">Usare Tags:"PSEdition_Core" per cercare elementi compatibili con l'edizione Core di PowerShell.</span><span class="sxs-lookup"><span data-stu-id="9b8d5-112">Use Tags:"PSEdition_Core" to search items compatible with PowerShell Core Edition.</span></span>

![Cercare elementi compatibili con l'edizione Core di PowerShell nei risultati](../../Images/SearchResultsWithPSEditions.PNG)

### <a name="use-tagspseditiondesktop-to-search-items-compatible-with-powershell-desktop-edition"></a><span data-ttu-id="9b8d5-114">Usare Tags:"PSEdition_Desktop" per cercare elementi compatibili con l'edizione Desktop di PowerShell.</span><span class="sxs-lookup"><span data-stu-id="9b8d5-114">Use Tags:"PSEdition_Desktop" to search items compatible with PowerShell Desktop Edition.</span></span>

![Cercare elementi compatibili con l'edizione Desktop di PowerShell nei risultati](../../Images/SearchResultsWithPSEdition-Desktop.PNG)

## <a name="more-details-on-authoring-and-finding-the-items-with-compatible-powershell-editions"></a><span data-ttu-id="9b8d5-116">Altre informazioni sulla creazione e la ricerca di elementi con versioni di PowerShell compatibili</span><span class="sxs-lookup"><span data-stu-id="9b8d5-116">More details on authoring and finding the items with compatible PowerShell Editions</span></span>

- [<span data-ttu-id="9b8d5-117">Moduli con edizioni di PS</span><span class="sxs-lookup"><span data-stu-id="9b8d5-117">Modules with PSEditions</span></span>](../../concepts/module-psedition-support.md)
- [<span data-ttu-id="9b8d5-118">Script con PSEditions</span><span class="sxs-lookup"><span data-stu-id="9b8d5-118">Scripts with PSEditions</span></span>](../../concepts/script-psedition-support.md)