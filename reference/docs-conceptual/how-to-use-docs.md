---
ms.date: 10/20/2019
keywords: powershell,cmdlet
title: Come usare la documentazione di PowerShell
ms.openlocfilehash: 80f72bb89b3bb82ee7c4d16b8969395f02d7d4ca
ms.sourcegitcommit: ac1ccdd826f112a11db09af9c628cae013f947ab
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 10/20/2019
ms.locfileid: "72676151"
---
# <a name="how-to-use-the-powershell-documentation"></a><span data-ttu-id="d076a-103">Come usare la documentazione di PowerShell</span><span class="sxs-lookup"><span data-stu-id="d076a-103">How to use the PowerShell documentation</span></span>

<span data-ttu-id="d076a-104">Benvenuti nella documentazione online di PowerShell.</span><span class="sxs-lookup"><span data-stu-id="d076a-104">Welcome to the PowerShell online documentation.</span></span> <span data-ttu-id="d076a-105">Questo sito contiene informazioni di riferimento sui cmdlet per le versioni seguenti di PowerShell:</span><span class="sxs-lookup"><span data-stu-id="d076a-105">This site contains cmdlet reference for the following versions of PowerShell:</span></span>

- <span data-ttu-id="d076a-106">PowerShell 7 (anteprima)</span><span class="sxs-lookup"><span data-stu-id="d076a-106">PowerShell 7 (preview)</span></span>
- <span data-ttu-id="d076a-107">PowerShell 6</span><span class="sxs-lookup"><span data-stu-id="d076a-107">PowerShell 6</span></span>
- <span data-ttu-id="d076a-108">PowerShell 5.1</span><span class="sxs-lookup"><span data-stu-id="d076a-108">PowerShell 5.1</span></span>

## <a name="finding-articles-and-selecting-a-version"></a><span data-ttu-id="d076a-109">Ricerca di articoli e selezione di una versione</span><span class="sxs-lookup"><span data-stu-id="d076a-109">Finding articles and selecting a version</span></span>

<span data-ttu-id="d076a-110">Esistono due modi per cercare contenuto in Docs. Il modo più semplice consiste nell'usare la casella di filtro sotto il selettore di versione.</span><span class="sxs-lookup"><span data-stu-id="d076a-110">There are two ways to search for content in Docs. The simplest way is to use the filter box under the version selector.</span></span> <span data-ttu-id="d076a-111">È sufficiente immettere una parola che compare nel titolo di un articolo.</span><span class="sxs-lookup"><span data-stu-id="d076a-111">Just enter a word that appears in the title of an article.</span></span> <span data-ttu-id="d076a-112">Nella pagina viene visualizzato un elenco di articoli corrispondenti.</span><span class="sxs-lookup"><span data-stu-id="d076a-112">The page displays a list of matching articles.</span></span> <span data-ttu-id="d076a-113">È anche possibile selezionare l'opzione per eseguire la ricerca nell'intero sito da tale elenco.</span><span class="sxs-lookup"><span data-stu-id="d076a-113">You can also select the option to search the entire site from that list.</span></span>

<span data-ttu-id="d076a-114">Per impostazione predefinita, il sito visualizza la documentazione per la versione rilasciata più recente di PowerShell.</span><span class="sxs-lookup"><span data-stu-id="d076a-114">By default, this site displays documentation for the latest released version of PowerShell.</span></span> <span data-ttu-id="d076a-115">Alcuni cmdlet funzionano in modo diverso nelle varie versioni di PowerShell.</span><span class="sxs-lookup"><span data-stu-id="d076a-115">Some cmdlets work differently in various versions of PowerShell.</span></span> <span data-ttu-id="d076a-116">Assicurarsi di visualizzare la documentazione per la versione di PowerShell in uso.</span><span class="sxs-lookup"><span data-stu-id="d076a-116">Be sure you are viewing the documentation for the version of PowerShell you are using.</span></span>

<span data-ttu-id="d076a-117">Usare il selettore di versione nella parte superiore della pagina per selezionare la versione di PowerShell desiderata.</span><span class="sxs-lookup"><span data-stu-id="d076a-117">Use the version picker at the top of the page to select the version of PowerShell you want.</span></span>

![Selettore di versione](images/how-to-use-docs/version-search.gif)

<span data-ttu-id="d076a-119">È possibile verificare la versione di PowerShell in uso esaminando il valore `$PSversionTable.PSVersion`.</span><span class="sxs-lookup"><span data-stu-id="d076a-119">You can verify the version of PowerShell you are using by inspecting the `$PSversionTable.PSVersion` value.</span></span> <span data-ttu-id="d076a-120">L'esempio seguente si riferisce all'output per Windows PowerShell v5.1.</span><span class="sxs-lookup"><span data-stu-id="d076a-120">The following example shows the output for Windows PowerShell v5.1.</span></span>

```powershell
$PSVersionTable.PSVersion
```

```Output
Major  Minor  Build  Revision
-----  -----  -----  --------
5      1      18362  145
```
