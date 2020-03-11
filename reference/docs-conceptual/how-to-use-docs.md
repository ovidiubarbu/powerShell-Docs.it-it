---
ms.date: 10/20/2019
keywords: powershell,cmdlet
title: Come usare la documentazione di PowerShell
ms.openlocfilehash: 7b73bc82f32e3ce1e6015822e0cc82078183931b
ms.sourcegitcommit: 01c60c0c97542dbad48ae34339cddbd813f1353b
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 03/04/2020
ms.locfileid: "78279308"
---
# <a name="how-to-use-the-powershell-documentation"></a><span data-ttu-id="3497f-103">Come usare la documentazione di PowerShell</span><span class="sxs-lookup"><span data-stu-id="3497f-103">How to use the PowerShell documentation</span></span>

<span data-ttu-id="3497f-104">Benvenuti nella documentazione online di PowerShell.</span><span class="sxs-lookup"><span data-stu-id="3497f-104">Welcome to the PowerShell online documentation.</span></span> <span data-ttu-id="3497f-105">Questo sito contiene informazioni di riferimento sui cmdlet per le versioni seguenti di PowerShell:</span><span class="sxs-lookup"><span data-stu-id="3497f-105">This site contains cmdlet reference for the following versions of PowerShell:</span></span>

- <span data-ttu-id="3497f-106">PowerShell 7 (anteprima)</span><span class="sxs-lookup"><span data-stu-id="3497f-106">PowerShell 7 (preview)</span></span>
- <span data-ttu-id="3497f-107">PowerShell 6</span><span class="sxs-lookup"><span data-stu-id="3497f-107">PowerShell 6</span></span>
- <span data-ttu-id="3497f-108">PowerShell 5.1</span><span class="sxs-lookup"><span data-stu-id="3497f-108">PowerShell 5.1</span></span>

## <a name="finding-articles-and-selecting-a-version"></a><span data-ttu-id="3497f-109">Ricerca di articoli e selezione di una versione</span><span class="sxs-lookup"><span data-stu-id="3497f-109">Finding articles and selecting a version</span></span>

<span data-ttu-id="3497f-110">Esistono due modi per cercare contenuto in Docs. Il modo più semplice consiste nell'usare la casella di filtro sotto il selettore di versione.</span><span class="sxs-lookup"><span data-stu-id="3497f-110">There are two ways to search for content in Docs. The simplest way is to use the filter box under the version selector.</span></span> <span data-ttu-id="3497f-111">È sufficiente immettere una parola che compare nel titolo di un articolo.</span><span class="sxs-lookup"><span data-stu-id="3497f-111">Just enter a word that appears in the title of an article.</span></span> <span data-ttu-id="3497f-112">Nella pagina viene visualizzato un elenco di articoli corrispondenti.</span><span class="sxs-lookup"><span data-stu-id="3497f-112">The page displays a list of matching articles.</span></span> <span data-ttu-id="3497f-113">È anche possibile selezionare l'opzione per eseguire la ricerca nell'intero sito da tale elenco.</span><span class="sxs-lookup"><span data-stu-id="3497f-113">You can also select the option to search the entire site from that list.</span></span>

<span data-ttu-id="3497f-114">Per impostazione predefinita, il sito visualizza la documentazione per la versione rilasciata più recente di PowerShell.</span><span class="sxs-lookup"><span data-stu-id="3497f-114">By default, this site displays documentation for the latest released version of PowerShell.</span></span> <span data-ttu-id="3497f-115">Alcuni cmdlet funzionano in modo diverso nelle varie versioni di PowerShell.</span><span class="sxs-lookup"><span data-stu-id="3497f-115">Some cmdlets work differently in various versions of PowerShell.</span></span> <span data-ttu-id="3497f-116">Assicurarsi di visualizzare la documentazione per la versione di PowerShell in uso.</span><span class="sxs-lookup"><span data-stu-id="3497f-116">Be sure you are viewing the documentation for the version of PowerShell you are using.</span></span>

<span data-ttu-id="3497f-117">Usare il selettore di versione nella parte superiore della pagina per selezionare la versione di PowerShell desiderata.</span><span class="sxs-lookup"><span data-stu-id="3497f-117">Use the version picker at the top of the page to select the version of PowerShell you want.</span></span>

![Selettore di versione](media/how-to-use-docs/version-search.gif)

<span data-ttu-id="3497f-119">È possibile verificare la versione di PowerShell in uso esaminando il valore `$PSversionTable.PSVersion`.</span><span class="sxs-lookup"><span data-stu-id="3497f-119">You can verify the version of PowerShell you are using by inspecting the `$PSversionTable.PSVersion` value.</span></span> <span data-ttu-id="3497f-120">L'esempio seguente si riferisce all'output per Windows PowerShell v5.1.</span><span class="sxs-lookup"><span data-stu-id="3497f-120">The following example shows the output for Windows PowerShell v5.1.</span></span>

```powershell
$PSVersionTable.PSVersion
```

```Output
Major  Minor  Build  Revision
-----  -----  -----  --------
5      1      18362  145
```
