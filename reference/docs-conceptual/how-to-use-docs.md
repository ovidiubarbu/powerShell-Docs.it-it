---
ms.date: 09/25/2019
keywords: powershell,cmdlet
title: Come usare la documentazione di PowerShell
ms.openlocfilehash: 9e3d5828d6bdb4ef14701994f146354a041efaea
ms.sourcegitcommit: a80bb79b85deab8ae3c21de56d1ee432fdd92628
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 10/11/2019
ms.locfileid: "72281642"
---
# <a name="how-to-use-the-powershell-documentation"></a><span data-ttu-id="bff72-103">Come usare la documentazione di PowerShell</span><span class="sxs-lookup"><span data-stu-id="bff72-103">How to use the PowerShell documentation</span></span>

<span data-ttu-id="bff72-104">Benvenuti nella documentazione online di PowerShell.</span><span class="sxs-lookup"><span data-stu-id="bff72-104">Welcome to the PowerShell online documentation.</span></span> <span data-ttu-id="bff72-105">Questo sito contiene informazioni di riferimento sui cmdlet per le versioni seguenti di PowerShell:</span><span class="sxs-lookup"><span data-stu-id="bff72-105">This site contains cmdlet reference for the following versions of PowerShell:</span></span>

- <span data-ttu-id="bff72-106">PowerShell 7 (anteprima)</span><span class="sxs-lookup"><span data-stu-id="bff72-106">PowerShell 7 (preview)</span></span>
- <span data-ttu-id="bff72-107">PowerShell 6</span><span class="sxs-lookup"><span data-stu-id="bff72-107">PowerShell 6</span></span>
- <span data-ttu-id="bff72-108">PowerShell 5.1</span><span class="sxs-lookup"><span data-stu-id="bff72-108">PowerShell 5.1</span></span>
- <span data-ttu-id="bff72-109">PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="bff72-109">PowerShell 5.0</span></span>
- <span data-ttu-id="bff72-110">PowerShell 4.0</span><span class="sxs-lookup"><span data-stu-id="bff72-110">PowerShell 4.0</span></span>
- <span data-ttu-id="bff72-111">PowerShell 3.0</span><span class="sxs-lookup"><span data-stu-id="bff72-111">PowerShell 3.0</span></span>

## <a name="selecting-your-version"></a><span data-ttu-id="bff72-112">Selezione della versione</span><span class="sxs-lookup"><span data-stu-id="bff72-112">Selecting your version</span></span>

<span data-ttu-id="bff72-113">Per impostazione predefinita, il sito visualizza la documentazione per la versione rilasciata più recente di PowerShell.</span><span class="sxs-lookup"><span data-stu-id="bff72-113">By default, this site displays documentation for the latest released version of PowerShell.</span></span> <span data-ttu-id="bff72-114">Alcuni cmdlet funzionano in modo diverso nelle varie versioni di PowerShell.</span><span class="sxs-lookup"><span data-stu-id="bff72-114">Some cmdlets work differently in various versions of PowerShell.</span></span> <span data-ttu-id="bff72-115">Assicurarsi di visualizzare la documentazione per la versione di PowerShell in uso.</span><span class="sxs-lookup"><span data-stu-id="bff72-115">Be sure you are viewing the documentation for the version of PowerShell you are using.</span></span>

<span data-ttu-id="bff72-116">Usare il selettore di versione nella parte superiore della pagina per selezionare la versione di PowerShell desiderata.</span><span class="sxs-lookup"><span data-stu-id="bff72-116">Use the version picker at the top of the page to select the version of PowerShell you want.</span></span>

![Selettore di versione](images/how-to-use-docs/picker-vall.gif)

<span data-ttu-id="bff72-118">È possibile verificare la versione di PowerShell in uso esaminando il valore `$PSversionTable.PSVersion`.</span><span class="sxs-lookup"><span data-stu-id="bff72-118">You can verify the version of PowerShell you are using by inspecting the `$PSversionTable.PSVersion` value.</span></span> <span data-ttu-id="bff72-119">L'esempio seguente si riferisce all'output per Windows PowerShell v5.1.</span><span class="sxs-lookup"><span data-stu-id="bff72-119">The following example shows the output for Windows PowerShell v5.1.</span></span>

```powershell
$PSVersionTable.PSVersion
```

```Output
Major  Minor  Build  Revision
-----  -----  -----  --------
5      1      18362  145
```

## <a name="searching-for-articles"></a><span data-ttu-id="bff72-120">Ricerca di articoli</span><span class="sxs-lookup"><span data-stu-id="bff72-120">Searching for articles</span></span>

<span data-ttu-id="bff72-121">Esistono due modi per cercare contenuto in Docs. Il modo più semplice consiste nell'usare la casella di filtro sotto il selettore di versione.</span><span class="sxs-lookup"><span data-stu-id="bff72-121">There are two ways to search for content in Docs. The simplest way is to use the filter box under the version selector.</span></span> <span data-ttu-id="bff72-122">È sufficiente immettere una parola che compare nel titolo di un articolo.</span><span class="sxs-lookup"><span data-stu-id="bff72-122">Just enter a word that appears in the title of an article.</span></span> <span data-ttu-id="bff72-123">Nella pagina viene visualizzato un elenco di articoli corrispondenti.</span><span class="sxs-lookup"><span data-stu-id="bff72-123">The page displays a list of matching articles.</span></span> <span data-ttu-id="bff72-124">È anche possibile selezionare l'opzione per eseguire la ricerca nell'intero sito da tale elenco.</span><span class="sxs-lookup"><span data-stu-id="bff72-124">You can also select the option to search the entire site from that list.</span></span>

![Casella di filtro](images/how-to-use-docs/filter-search.gif)
