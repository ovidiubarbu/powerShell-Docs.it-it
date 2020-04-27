---
ms.date: 06/12/2017
contributor: JKeithB
keywords: gallery,powershell,cmdlet,psgallery
title: Filtro dei risultati della ricerca
ms.openlocfilehash: 13270a310613a974e1588a9f56d443a936cfebb8
ms.sourcegitcommit: 6545c60578f7745be015111052fd7769f8289296
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/22/2020
ms.locfileid: "71328042"
---
# <a name="filtering-search-results"></a><span data-ttu-id="3f1cf-103">Filtro dei risultati della ricerca</span><span class="sxs-lookup"><span data-stu-id="3f1cf-103">Filtering search results</span></span>

<span data-ttu-id="3f1cf-104">Nella [scheda Packages](https://www.powershellgallery.com/packages) (Pacchetti) vengono visualizzati tutti i pacchetti disponibili in PowerShell Gallery.</span><span class="sxs-lookup"><span data-stu-id="3f1cf-104">The [Packages tab](https://www.powershellgallery.com/packages) displays all available packages in the PowerShell Gallery.</span></span>

<span data-ttu-id="3f1cf-105">Esistono diversi modi per filtrare, ordinare e cercare i pacchetti.</span><span class="sxs-lookup"><span data-stu-id="3f1cf-105">There are several ways to filter, sort, and search the packages.</span></span>
<span data-ttu-id="3f1cf-106">Per visualizzare altri dettagli su un particolare pacchetto, fare clic sul pacchetto.</span><span class="sxs-lookup"><span data-stu-id="3f1cf-106">To see more details about a particular package, click the package.</span></span>

## <a name="filter-by"></a><span data-ttu-id="3f1cf-107">Filter By (Filtro)</span><span class="sxs-lookup"><span data-stu-id="3f1cf-107">Filter By</span></span>

<span data-ttu-id="3f1cf-108">L'elenco a discesa in Filter By (Filtro) consente agli utenti di filtrare i risultati in base a:</span><span class="sxs-lookup"><span data-stu-id="3f1cf-108">The drop-down under "Filter By" allows users to filter the results by:</span></span>
- <span data-ttu-id="3f1cf-109">Includi versione preliminare</span><span class="sxs-lookup"><span data-stu-id="3f1cf-109">Include Prerelease</span></span>
- <span data-ttu-id="3f1cf-110">Solo stabile</span><span class="sxs-lookup"><span data-stu-id="3f1cf-110">Stable Only</span></span>

<span data-ttu-id="3f1cf-111">Per informazioni sui concetti di "versione preliminare" e "versione stabile", vedere [Prerelease Versioning Added to PowerShellGet and PowerShell Gallery](https://blogs.msdn.microsoft.com/powershell/2017/12/05/prerelease-versioning-added-to-powershellget-and-powershell-gallery/) (Aggiunta delle versioni preliminari a PowerShellGet e PowerShell Gallery) nel blog del team di PowerShell.</span><span class="sxs-lookup"><span data-stu-id="3f1cf-111">For information about "Prerelease" and "Stable", see [Prerelease Versioning Added to PowerShellGet and PowerShell Gallery](https://blogs.msdn.microsoft.com/powershell/2017/12/05/prerelease-versioning-added-to-powershellget-and-powershell-gallery/) in the PowerShell Team Blog.</span></span>

<span data-ttu-id="3f1cf-112">Le caselle di controllo sotto l'elenco a discesa consentono agli utenti di filtrare i risultati in base a:</span><span class="sxs-lookup"><span data-stu-id="3f1cf-112">The checkboxes under the drop-down allow users to filter the results by:</span></span>
- <span data-ttu-id="3f1cf-113">Tipi di pacchetto</span><span class="sxs-lookup"><span data-stu-id="3f1cf-113">Package Types</span></span>
  - <span data-ttu-id="3f1cf-114">Modulo</span><span class="sxs-lookup"><span data-stu-id="3f1cf-114">Module</span></span>
  - <span data-ttu-id="3f1cf-115">Script</span><span class="sxs-lookup"><span data-stu-id="3f1cf-115">Script</span></span>
- <span data-ttu-id="3f1cf-116">Categorie</span><span class="sxs-lookup"><span data-stu-id="3f1cf-116">Categories</span></span>
  - <span data-ttu-id="3f1cf-117">Cmdlet</span><span class="sxs-lookup"><span data-stu-id="3f1cf-117">Cmdlet</span></span>
  - <span data-ttu-id="3f1cf-118">DSC Resource (Risorsa DSC)</span><span class="sxs-lookup"><span data-stu-id="3f1cf-118">DSC Resource</span></span>
  - <span data-ttu-id="3f1cf-119">Funzione</span><span class="sxs-lookup"><span data-stu-id="3f1cf-119">Function</span></span>
  - <span data-ttu-id="3f1cf-120">Funzionalità di ruolo</span><span class="sxs-lookup"><span data-stu-id="3f1cf-120">Role Capability</span></span>
  - <span data-ttu-id="3f1cf-121">Flusso di lavoro</span><span class="sxs-lookup"><span data-stu-id="3f1cf-121">Workflow</span></span>

<span data-ttu-id="3f1cf-122">Per visualizzare solo i moduli in PowerShell Gallery, selezionare Module (Modulo) nell'elenco a discesa Package Types (Tipi di pacchetto).</span><span class="sxs-lookup"><span data-stu-id="3f1cf-122">To see only modules in the PowerShell Gallery, check Module in the Package Types.</span></span>
<span data-ttu-id="3f1cf-123">In modo analogo, per visualizzare solo gli script in PowerShell Gallery, selezionare Script nell'elenco a discesa Package Types (Tipi di pacchetto).</span><span class="sxs-lookup"><span data-stu-id="3f1cf-123">Similarly, to see only scripts in the PowerShell Gallery, check Script in the Package Types.</span></span>

> [!NOTE]
> <span data-ttu-id="3f1cf-124">I filtri sono inclusivi.</span><span class="sxs-lookup"><span data-stu-id="3f1cf-124">Filters are inclusive.</span></span>
> <span data-ttu-id="3f1cf-125">Esempio: un pacchetto che include sia cmdlet che funzioni viene visualizzato sia quando è selezionato Cmdlet che Function (o entrambi).</span><span class="sxs-lookup"><span data-stu-id="3f1cf-125">Example: A package containing both cmdlets and functions will appear if either Cmdlet or Function (or both) are checked.</span></span>
> <span data-ttu-id="3f1cf-126">Se non è selezionato nessuno dei due tipi, il pacchetto non viene visualizzato.</span><span class="sxs-lookup"><span data-stu-id="3f1cf-126">If neither are selected, the package will not appear.</span></span>
> <span data-ttu-id="3f1cf-127">Analogamente, se vengono selezionate tutte le categorie, verranno visualizzati solo i pacchetti che contengono una di queste categorie.</span><span class="sxs-lookup"><span data-stu-id="3f1cf-127">Similarly, if all categories are selected, only packages containing one of those categories will appear.</span></span>
> <span data-ttu-id="3f1cf-128">**Non verranno visualizzati i pacchetti che non appartengono ad alcuna di queste categorie.**</span><span class="sxs-lookup"><span data-stu-id="3f1cf-128">**Packages that do not belong to any of those categories will not appear.**</span></span>

## <a name="sort-by"></a><span data-ttu-id="3f1cf-129">Sort By (Ordina per)</span><span class="sxs-lookup"><span data-stu-id="3f1cf-129">Sort By</span></span>

<span data-ttu-id="3f1cf-130">L'elenco a discesa Sort By (Ordina per) consente agli utenti di ordinare i risultati in base a:</span><span class="sxs-lookup"><span data-stu-id="3f1cf-130">The Sort By drop-down allows users to sort the results by:</span></span>
- <span data-ttu-id="3f1cf-131">Popularity (Popolarità): la popolarità viene determinata dal numero di download</span><span class="sxs-lookup"><span data-stu-id="3f1cf-131">Popularity - Popularity is determined by Download Count</span></span>
- <span data-ttu-id="3f1cf-132">A-Z: in ordine alfabetico per nome del pacchetto</span><span class="sxs-lookup"><span data-stu-id="3f1cf-132">A-Z - Alphabetically by package name</span></span>
- <span data-ttu-id="3f1cf-133">Recent (Recenti): i pacchetti vengono ordinati in base alla data di pubblicazione</span><span class="sxs-lookup"><span data-stu-id="3f1cf-133">Recent - Packages appear in order of publish date</span></span>

## <a name="search-box"></a><span data-ttu-id="3f1cf-134">Casella di ricerca</span><span class="sxs-lookup"><span data-stu-id="3f1cf-134">Search Box</span></span>

<span data-ttu-id="3f1cf-135">La casella di ricerca consente di cercare i pacchetti in base a parole chiave.</span><span class="sxs-lookup"><span data-stu-id="3f1cf-135">The Search Box allows users to search the packages on keywords.</span></span>
<span data-ttu-id="3f1cf-136">Per altre informazioni, vedere [Sintassi di ricerca di PowerShell Gallery](search-syntax.md).</span><span class="sxs-lookup"><span data-stu-id="3f1cf-136">For more information, see [Gallery Search Syntax](search-syntax.md).</span></span>
