---
ms.date: 06/12/2017
contributor: JKeithB
keywords: gallery,powershell,cmdlet,psgallery
title: Sintassi di ricerca di PowerShell Gallery
ms.openlocfilehash: aabcaa1f1b5b641ab5033c9ba2e358477c84a23b
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 12/05/2019
ms.locfileid: "71328452"
---
# <a name="gallery-search-syntax"></a><span data-ttu-id="cb683-103">Sintassi di ricerca di PowerShell Gallery</span><span class="sxs-lookup"><span data-stu-id="cb683-103">Gallery Search Syntax</span></span>

<span data-ttu-id="cb683-104">È possibile eseguire una ricerca in PowerShell Gallery tramite il [sito Web di PowerShell Gallery](https://www.powershellgallery.com/).</span><span class="sxs-lookup"><span data-stu-id="cb683-104">You can search the PowerShell Gallery using the [PowerShell Gallery's web site](https://www.powershellgallery.com/).</span></span>
<span data-ttu-id="cb683-105">Il sito Web di PowerShell Gallery offre una casella di ricerca di testo in cui è possibile usare parole, frasi ed espressioni con parole chiave per restringere i risultati della ricerca.</span><span class="sxs-lookup"><span data-stu-id="cb683-105">PowerShell Gallery web site offers a text searchbox where you can use words, phrases and keyword expressions to narrow down search results.</span></span>

## <a name="search-by-keywords"></a><span data-ttu-id="cb683-106">Ricerca per parole chiave</span><span class="sxs-lookup"><span data-stu-id="cb683-106">Search by Keywords</span></span>

    dsc azure sql

<span data-ttu-id="cb683-107">La funzionalità di ricerca tenta di trovare i documenti rilevanti che contengono tutte e 3 le parole chiave e restituisce i documenti corrispondenti.</span><span class="sxs-lookup"><span data-stu-id="cb683-107">Search attempts to find relevant documents containing all 3 keywords, and return matching documents.</span></span>

## <a name="search-using-phrases-and-keywords"></a><span data-ttu-id="cb683-108">Ricerca per frasi e parole chiave</span><span class="sxs-lookup"><span data-stu-id="cb683-108">Search using Phrases and keywords</span></span>

    "azure sql" deployment

<span data-ttu-id="cb683-109">Se si immette una frase tra virgolette (""), la modalità di ricerca cambia e viene cercata la specifica frase e non le singole parole chiave.</span><span class="sxs-lookup"><span data-stu-id="cb683-109">Entering a phrase between quotation marks ("") change the search to look for the particular phrase instead of separate keywords.</span></span>
<span data-ttu-id="cb683-110">I documenti corrispondenti in genere contengono la frase esatta "azure sql", incluse le varianti relative alle lettere maiuscole/minuscole, ad esempio "Azure SQL", e la parola 'deployment'.</span><span class="sxs-lookup"><span data-stu-id="cb683-110">Matching documents should usually contain the exact phrase "azure sql", including variations on capitalization e.g. "Azure SQL", and also usually contain the word 'deployment'.</span></span>

## <a name="filtering-on-fields"></a><span data-ttu-id="cb683-111">Filtri relativi ai campi</span><span class="sxs-lookup"><span data-stu-id="cb683-111">Filtering on fields</span></span>

<span data-ttu-id="cb683-112">È possibile cercare l'ID (oppure le varianti 'Id' o 'id') di un pacchetto specifico o alcuni altri campi anteponendo il nome del campo ai termini della ricerca.</span><span class="sxs-lookup"><span data-stu-id="cb683-112">You can search for a specific package ID (or 'Id' or 'id'), or certain other fields by prefixing search terms with the field name.</span></span>

<span data-ttu-id="cb683-113">Attualmente, i campi su cui è possibile eseguire la ricerca sono 'Id', 'Version', 'Tags', 'Author', 'Owner', 'Functions', 'Cmdlets', 'DscResources' e 'PowerShellVersion'.</span><span class="sxs-lookup"><span data-stu-id="cb683-113">Currently the searchable fields are 'Id', 'Version', 'Tags', 'Author', 'Owner', 'Functions', 'Cmdlets', 'DscResources' and 'PowerShellVersion'.</span></span>

<span data-ttu-id="cb683-114">Qual è la differenza tra ID e Title?</span><span class="sxs-lookup"><span data-stu-id="cb683-114">[What's the difference between ID and Title?</span></span> <span data-ttu-id="cb683-115">ID è il nome usato nella console.</span><span class="sxs-lookup"><span data-stu-id="cb683-115">ID is the name you use in the console.</span></span> <span data-ttu-id="cb683-116">Title è ciò che viene visualizzato nella parte superiore della pagina del pacchetto nei risultati della ricerca.</span><span class="sxs-lookup"><span data-stu-id="cb683-116">Title is what is shown at the top of the package page in search results.]</span></span>

## <a name="examples"></a><span data-ttu-id="cb683-117">Esempi</span><span class="sxs-lookup"><span data-stu-id="cb683-117">Examples</span></span>

    ID:PSReadline
    
<span data-ttu-id="cb683-118">trova i pacchetti con ID contenente "PSReadline".</span><span class="sxs-lookup"><span data-stu-id="cb683-118">finds packages with an ID containing "PSReadline".</span></span>

    Id:"AzureRM.Profile"

<span data-ttu-id="cb683-119">è un altro modo per trovare i pacchetti con "AzureRM.Profile" nel campo ID.</span><span class="sxs-lookup"><span data-stu-id="cb683-119">is another way to find packages with "AzureRM.Profile" in their ID field.</span></span>

<span data-ttu-id="cb683-120">Il filtro 'Id' è una corrispondenza della sottostringa, quindi se si cerca:</span><span class="sxs-lookup"><span data-stu-id="cb683-120">The 'Id' filter is a substring match, so if you search for the following:</span></span>

    Id:"azure"

<span data-ttu-id="cb683-121">Si ottengono risultati che includono AzureRM.Profile' e 'Azure.Storage'.</span><span class="sxs-lookup"><span data-stu-id="cb683-121">This provides results that include AzureRM.Profile' and 'Azure.Storage'.</span></span>

<span data-ttu-id="cb683-122">È possibile cercare anche più parole chiave in un singolo campo.</span><span class="sxs-lookup"><span data-stu-id="cb683-122">You can also search for multiple keywords in a single field.</span></span> 

    id:azure tags:intellisense

<span data-ttu-id="cb683-123">Ed è possibile eseguire ricerche di frasi usando le virgolette doppie:</span><span class="sxs-lookup"><span data-stu-id="cb683-123">And you can perform phrase searches using double quotes:</span></span>

    id:"azure.storage"

<span data-ttu-id="cb683-124">Per cercare tutti i pacchetti con tag DSC.</span><span class="sxs-lookup"><span data-stu-id="cb683-124">To search all packages with DSC tag.</span></span>

    Tags:DSC

<span data-ttu-id="cb683-125">Per cercare tutti i pacchetti con la funzione specificata.</span><span class="sxs-lookup"><span data-stu-id="cb683-125">To search all packages with the specified function.</span></span>

    Functions:Get-TreeSize

<span data-ttu-id="cb683-126">Per cercare tutti i pacchetti con il cmdlet specificato.</span><span class="sxs-lookup"><span data-stu-id="cb683-126">To search all packages with the specified cmdlet.</span></span>

    Cmdlets:Get-AzureRmEnvironment

<span data-ttu-id="cb683-127">Per cercare tutti i pacchetti con il nome di risorsa DSC specificato.</span><span class="sxs-lookup"><span data-stu-id="cb683-127">To search all packages with the specified DSC Resource name.</span></span>

    DscResources:xArchive

<span data-ttu-id="cb683-128">Per cercare tutti i pacchetti con il valore PowerShellVersion specificato</span><span class="sxs-lookup"><span data-stu-id="cb683-128">To search all packages with the specified PowerShellVersion</span></span>

    PowerShellVersion:2.0

<span data-ttu-id="cb683-129">Infine, se si usa un campo non supportato, ad esempio 'commands', il campo verrà semplicemente ignorato e la ricerca verrà eseguita su tutti i campi.</span><span class="sxs-lookup"><span data-stu-id="cb683-129">Finally, if you use a field we don't support, such as 'commands', we'll just ignore it and search all the fields.</span></span> <span data-ttu-id="cb683-130">Quindi, la query seguente</span><span class="sxs-lookup"><span data-stu-id="cb683-130">So the following query</span></span>

    commands:blobs storage

<span data-ttu-id="cb683-131">viene interpretata esattamente come questa query:</span><span class="sxs-lookup"><span data-stu-id="cb683-131">Is interpreted exactly the same as this query:</span></span>

    blobs storage
