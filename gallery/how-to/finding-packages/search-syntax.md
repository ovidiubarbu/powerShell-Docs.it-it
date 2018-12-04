---
ms.date: 06/12/2017
contributor: JKeithB
keywords: gallery,powershell,cmdlet,psgallery
title: Sintassi di ricerca di PowerShell Gallery
ms.openlocfilehash: aabcaa1f1b5b641ab5033c9ba2e358477c84a23b
ms.sourcegitcommit: e24525046dd37166b9d83eeecdc534726316f429
ms.translationtype: MTE95
ms.contentlocale: it-IT
ms.lasthandoff: 12/01/2018
ms.locfileid: "52742857"
---
# <a name="gallery-search-syntax"></a><span data-ttu-id="6fe7d-103">Sintassi di ricerca di PowerShell Gallery</span><span class="sxs-lookup"><span data-stu-id="6fe7d-103">Gallery Search Syntax</span></span>

<span data-ttu-id="6fe7d-104">È possibile cercare la PowerShell Gallery usando il [sito web della raccolta di PowerShell](https://www.powershellgallery.com/).</span><span class="sxs-lookup"><span data-stu-id="6fe7d-104">You can search the PowerShell Gallery using the [PowerShell Gallery's web site](https://www.powershellgallery.com/).</span></span>
<span data-ttu-id="6fe7d-105">Sito web di PowerShell Gallery offre searchbox un testo in cui è possibile usare parole, frasi ed espressioni di parole chiave per restringere i risultati della ricerca.</span><span class="sxs-lookup"><span data-stu-id="6fe7d-105">PowerShell Gallery web site offers a text searchbox where you can use words, phrases and keyword expressions to narrow down search results.</span></span>

## <a name="search-by-keywords"></a><span data-ttu-id="6fe7d-106">Ricerca per parole chiave</span><span class="sxs-lookup"><span data-stu-id="6fe7d-106">Search by Keywords</span></span>

    dsc azure sql

<span data-ttu-id="6fe7d-107">Ricerca tenta di trovare documenti rilevanti che contengono tutte le parole 3 chiave e restituire documenti corrispondenti.</span><span class="sxs-lookup"><span data-stu-id="6fe7d-107">Search attempts to find relevant documents containing all 3 keywords, and return matching documents.</span></span>

## <a name="search-using-phrases-and-keywords"></a><span data-ttu-id="6fe7d-108">Ricerca per frasi e parole chiave</span><span class="sxs-lookup"><span data-stu-id="6fe7d-108">Search using Phrases and keywords</span></span>

    "azure sql" deployment

<span data-ttu-id="6fe7d-109">Se si immette una frase tra virgolette (""), la modalità di ricerca cambia e viene cercata la specifica frase e non le singole parole chiave.</span><span class="sxs-lookup"><span data-stu-id="6fe7d-109">Entering a phrase between quotation marks ("") change the search to look for the particular phrase instead of separate keywords.</span></span>
<span data-ttu-id="6fe7d-110">I documenti corrispondenti in genere contengono la frase esatta "azure sql", incluse le varianti relative alle lettere maiuscole/minuscole, ad esempio "Azure SQL", e la parola 'deployment'.</span><span class="sxs-lookup"><span data-stu-id="6fe7d-110">Matching documents should usually contain the exact phrase "azure sql", including variations on capitalization e.g. "Azure SQL", and also usually contain the word 'deployment'.</span></span>

## <a name="filtering-on-fields"></a><span data-ttu-id="6fe7d-111">Filtri relativi ai campi</span><span class="sxs-lookup"><span data-stu-id="6fe7d-111">Filtering on fields</span></span>

<span data-ttu-id="6fe7d-112">È possibile cercare l'ID (oppure le varianti 'Id' o 'id') di un pacchetto specifico o alcuni altri campi anteponendo il nome del campo ai termini della ricerca.</span><span class="sxs-lookup"><span data-stu-id="6fe7d-112">You can search for a specific package ID (or 'Id' or 'id'), or certain other fields by prefixing search terms with the field name.</span></span>

<span data-ttu-id="6fe7d-113">Attualmente, i campi su cui è possibile eseguire la ricerca sono 'Id', 'Version', 'Tags', 'Author', 'Owner', 'Functions', 'Cmdlets', 'DscResources' e 'PowerShellVersion'.</span><span class="sxs-lookup"><span data-stu-id="6fe7d-113">Currently the searchable fields are 'Id', 'Version', 'Tags', 'Author', 'Owner', 'Functions', 'Cmdlets', 'DscResources' and 'PowerShellVersion'.</span></span>

<span data-ttu-id="6fe7d-114">Qual è la differenza tra ID e Title?</span><span class="sxs-lookup"><span data-stu-id="6fe7d-114">[What's the difference between ID and Title?</span></span> <span data-ttu-id="6fe7d-115">ID è il nome usato nella console.</span><span class="sxs-lookup"><span data-stu-id="6fe7d-115">ID is the name you use in the console.</span></span> <span data-ttu-id="6fe7d-116">Title è ciò che viene visualizzato nella parte superiore della pagina del pacchetto nei risultati della ricerca.</span><span class="sxs-lookup"><span data-stu-id="6fe7d-116">Title is what is shown at the top of the package page in search results.]</span></span>

## <a name="examples"></a><span data-ttu-id="6fe7d-117">Esempi</span><span class="sxs-lookup"><span data-stu-id="6fe7d-117">Examples</span></span>

    ID:PSReadline
    
<span data-ttu-id="6fe7d-118">Trova tutti i pacchetti con un ID contenente "PSReadline".</span><span class="sxs-lookup"><span data-stu-id="6fe7d-118">finds packages with an ID containing "PSReadline".</span></span>

    Id:"AzureRM.Profile"

<span data-ttu-id="6fe7d-119">è un altro modo per trovare i pacchetti con "AzureRM.Profile" nel campo ID.</span><span class="sxs-lookup"><span data-stu-id="6fe7d-119">is another way to find packages with "AzureRM.Profile" in their ID field.</span></span>

<span data-ttu-id="6fe7d-120">Il filtro 'Id' è una corrispondenza della sottostringa, quindi se si cerca:</span><span class="sxs-lookup"><span data-stu-id="6fe7d-120">The 'Id' filter is a substring match, so if you search for the following:</span></span>

    Id:"azure"

<span data-ttu-id="6fe7d-121">In questo modo i risultati che includono azurerm. Profile ' e 'Storage'.</span><span class="sxs-lookup"><span data-stu-id="6fe7d-121">This provides results that include AzureRM.Profile' and 'Azure.Storage'.</span></span>

<span data-ttu-id="6fe7d-122">È possibile cercare anche più parole chiave in un singolo campo.</span><span class="sxs-lookup"><span data-stu-id="6fe7d-122">You can also search for multiple keywords in a single field.</span></span> 

    id:azure tags:intellisense

<span data-ttu-id="6fe7d-123">Ed è possibile eseguire ricerche di frasi usando le virgolette doppie:</span><span class="sxs-lookup"><span data-stu-id="6fe7d-123">And you can perform phrase searches using double quotes:</span></span>

    id:"azure.storage"

<span data-ttu-id="6fe7d-124">Per cercare tutti i pacchetti con tag DSC.</span><span class="sxs-lookup"><span data-stu-id="6fe7d-124">To search all packages with DSC tag.</span></span>

    Tags:DSC

<span data-ttu-id="6fe7d-125">Per cercare tutti i pacchetti con la funzione specificata.</span><span class="sxs-lookup"><span data-stu-id="6fe7d-125">To search all packages with the specified function.</span></span>

    Functions:Get-TreeSize

<span data-ttu-id="6fe7d-126">Per cercare tutti i pacchetti con il cmdlet specificato.</span><span class="sxs-lookup"><span data-stu-id="6fe7d-126">To search all packages with the specified cmdlet.</span></span>

    Cmdlets:Get-AzureRmEnvironment

<span data-ttu-id="6fe7d-127">Per cercare tutti i pacchetti con il nome di risorsa DSC specificato.</span><span class="sxs-lookup"><span data-stu-id="6fe7d-127">To search all packages with the specified DSC Resource name.</span></span>

    DscResources:xArchive

<span data-ttu-id="6fe7d-128">Per cercare tutti i pacchetti con il valore PowerShellVersion specificato</span><span class="sxs-lookup"><span data-stu-id="6fe7d-128">To search all packages with the specified PowerShellVersion</span></span>

    PowerShellVersion:2.0

<span data-ttu-id="6fe7d-129">Infine, se si usa un campo non supportato, ad esempio 'commands', il campo verrà semplicemente ignorato e la ricerca verrà eseguita su tutti i campi.</span><span class="sxs-lookup"><span data-stu-id="6fe7d-129">Finally, if you use a field we don't support, such as 'commands', we'll just ignore it and search all the fields.</span></span> <span data-ttu-id="6fe7d-130">Quindi, la query seguente</span><span class="sxs-lookup"><span data-stu-id="6fe7d-130">So the following query</span></span>

    commands:blobs storage

<span data-ttu-id="6fe7d-131">viene interpretata esattamente come questa query:</span><span class="sxs-lookup"><span data-stu-id="6fe7d-131">Is interpreted exactly the same as this query:</span></span>

    blobs storage
