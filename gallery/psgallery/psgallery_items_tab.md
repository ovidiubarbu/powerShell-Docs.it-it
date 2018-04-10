---
ms.date: 06/12/2017
contributor: JKeithB
ms.topic: conceptual
keywords: gallery,powershell,cmdlet,psgallery
title: psgallery_items_tab
ms.openlocfilehash: 5058253678a4f996b080e43820fee06b35b681f4
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/09/2018
---
# <a name="items-tab"></a><span data-ttu-id="ab665-103">Scheda Items (Elementi)</span><span class="sxs-lookup"><span data-stu-id="ab665-103">Items Tab</span></span>

<span data-ttu-id="ab665-104">La [scheda Items](https://www.powershellgallery.com/items) (Elementi) visualizza tutti gli elementi disponibili in PowerShell Gallery.</span><span class="sxs-lookup"><span data-stu-id="ab665-104">The [Items tab](https://www.powershellgallery.com/items) displays all available items in the PowerShell Gallery.</span></span>

<span data-ttu-id="ab665-105">Esistono diversi modi per filtrare, ordinare e cercare gli elementi.</span><span class="sxs-lookup"><span data-stu-id="ab665-105">There are several ways to filter, sort, and search the items.</span></span>
<span data-ttu-id="ab665-106">Per altri dettagli su un particolare elemento, selezionarlo.</span><span class="sxs-lookup"><span data-stu-id="ab665-106">To see more details about a particular item, click the item.</span></span>

## <a name="filter-by"></a><span data-ttu-id="ab665-107">Filter By (Filtro)</span><span class="sxs-lookup"><span data-stu-id="ab665-107">Filter By</span></span>

<span data-ttu-id="ab665-108">L'elenco a discesa in Filter By (Filtro) consente agli utenti di filtrare i risultati in base a:</span><span class="sxs-lookup"><span data-stu-id="ab665-108">The drop-down under "Filter By" allows users to filter the results by:</span></span>
* <span data-ttu-id="ab665-109">Includi versione preliminare</span><span class="sxs-lookup"><span data-stu-id="ab665-109">Include Prerelease</span></span>
* <span data-ttu-id="ab665-110">Solo stabile</span><span class="sxs-lookup"><span data-stu-id="ab665-110">Stable Only</span></span>

<span data-ttu-id="ab665-111">Per informazioni sui concetti di "versione preliminare" e "versione stabile", vedere [Prerelease Versioning Added to PowerShellGet and PowerShell Gallery](https://blogs.msdn.microsoft.com/powershell/2017/12/05/prerelease-versioning-added-to-powershellget-and-powershell-gallery/) (Aggiunta delle versioni preliminari a PowerShellGet e PowerShell Gallery) nel blog del team di PowerShell.</span><span class="sxs-lookup"><span data-stu-id="ab665-111">For information about "Prerelease" and "Stable", see [Prerelease Versioning Added to PowerShellGet and PowerShell Gallery](https://blogs.msdn.microsoft.com/powershell/2017/12/05/prerelease-versioning-added-to-powershellget-and-powershell-gallery/) in the PowerShell Team Blog.</span></span>

<span data-ttu-id="ab665-112">Le caselle di controllo sotto l'elenco a discesa consentono agli utenti di filtrare i risultati in base a:</span><span class="sxs-lookup"><span data-stu-id="ab665-112">The checkboxes under the drop-down allow users to filter the results by:</span></span>
* <span data-ttu-id="ab665-113">Tipi di elemento</span><span class="sxs-lookup"><span data-stu-id="ab665-113">Item Types</span></span>
  - <span data-ttu-id="ab665-114">Modulo</span><span class="sxs-lookup"><span data-stu-id="ab665-114">Module</span></span>
  - <span data-ttu-id="ab665-115">Script</span><span class="sxs-lookup"><span data-stu-id="ab665-115">Script</span></span>
* <span data-ttu-id="ab665-116">Categorie</span><span class="sxs-lookup"><span data-stu-id="ab665-116">Categories</span></span>
  - <span data-ttu-id="ab665-117">Cmdlet</span><span class="sxs-lookup"><span data-stu-id="ab665-117">Cmdlet</span></span>
  - <span data-ttu-id="ab665-118">DSC Resource (Risorsa DSC)</span><span class="sxs-lookup"><span data-stu-id="ab665-118">DSC Resource</span></span>
  - <span data-ttu-id="ab665-119">Function</span><span class="sxs-lookup"><span data-stu-id="ab665-119">Function</span></span>
  - <span data-ttu-id="ab665-120">Funzionalità di ruolo</span><span class="sxs-lookup"><span data-stu-id="ab665-120">Role Capability</span></span>
  - <span data-ttu-id="ab665-121">Flusso di lavoro</span><span class="sxs-lookup"><span data-stu-id="ab665-121">Workflow</span></span>

<span data-ttu-id="ab665-122">Per visualizzare solo i moduli in PowerShell Gallery, selezionare Module (Modulo) nell'elenco a discesa Item Types (Tipi di elemento).</span><span class="sxs-lookup"><span data-stu-id="ab665-122">To see only modules in the PowerShell Gallery, check Module in the Item Types.</span></span>
<span data-ttu-id="ab665-123">In modo analogo, per visualizzare solo gli script in PowerShell Gallery, selezionare Script nell'elenco a discesa Item Types (Tipi di elemento).</span><span class="sxs-lookup"><span data-stu-id="ab665-123">Similarly, to see only scripts in the PowerShell Gallery, check Script in the Item Types.</span></span>

> [!NOTE]
> <span data-ttu-id="ab665-124">I filtri sono inclusivi.</span><span class="sxs-lookup"><span data-stu-id="ab665-124">Filters are inclusive.</span></span>
> <span data-ttu-id="ab665-125">Esempio: un elemento che include sia cmdlet che funzioni viene visualizzato sia quando è selezionato Cmdlet che Function (o entrambi).</span><span class="sxs-lookup"><span data-stu-id="ab665-125">Example: An item containing both cmdlets and functions will appear if either Cmdlet or Function (or both) are checked.</span></span>
> <span data-ttu-id="ab665-126">Se non è selezionato nessuno dei due tipi, l'elemento non viene visualizzato.</span><span class="sxs-lookup"><span data-stu-id="ab665-126">If neither are selected, the item will not appear.</span></span>
> <span data-ttu-id="ab665-127">Analogamente, se vengono selezionate tutte le categorie, verranno visualizzati solo gli elementi che contengono una di queste categorie.</span><span class="sxs-lookup"><span data-stu-id="ab665-127">Similarly, if all categories are selected, only items containing one of those categories will appear.</span></span>
> <span data-ttu-id="ab665-128">**Non verranno visualizzati gli elementi che non appartengono ad alcuna di queste categorie.**</span><span class="sxs-lookup"><span data-stu-id="ab665-128">**Items that do not belong to any of those categories will not appear.**</span></span>

## <a name="sort-by"></a><span data-ttu-id="ab665-129">Sort By (Ordina per)</span><span class="sxs-lookup"><span data-stu-id="ab665-129">Sort By</span></span>

<span data-ttu-id="ab665-130">L'elenco a discesa Sort By (Ordina per) consente agli utenti di ordinare i risultati in base a:</span><span class="sxs-lookup"><span data-stu-id="ab665-130">The Sort By drop-down allows users to sort the results by:</span></span>
* <span data-ttu-id="ab665-131">Popularity (Popolarità): la popolarità viene determinata dal numero di download</span><span class="sxs-lookup"><span data-stu-id="ab665-131">Popularity - Popularity is determined by Download Count</span></span>
* <span data-ttu-id="ab665-132">A-Z: in ordine alfabetico in base al nome dell'elemento</span><span class="sxs-lookup"><span data-stu-id="ab665-132">A-Z - Alphabetically by item name</span></span>
* <span data-ttu-id="ab665-133">Recent (Recenti): gli elementi vengono ordinati in base alla data di pubblicazione</span><span class="sxs-lookup"><span data-stu-id="ab665-133">Recent - Items appear in order of publish date</span></span>

## <a name="search-box"></a><span data-ttu-id="ab665-134">Casella di ricerca</span><span class="sxs-lookup"><span data-stu-id="ab665-134">Search Box</span></span>

<span data-ttu-id="ab665-135">La casella di ricerca consente di cercare gli elementi in base a parole chiave.</span><span class="sxs-lookup"><span data-stu-id="ab665-135">The Search Box allows users to search the items on keywords.</span></span>
<span data-ttu-id="ab665-136">Per altre informazioni, vedere [Sintassi di ricerca di PowerShell Gallery](psgallery_search_syntax.md).</span><span class="sxs-lookup"><span data-stu-id="ab665-136">For more information, see [Gallery Search Syntax](psgallery_search_syntax.md).</span></span>