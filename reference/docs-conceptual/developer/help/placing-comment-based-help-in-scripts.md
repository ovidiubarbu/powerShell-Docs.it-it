---
title: Inserimento della Guida basata su commenti negli script | Microsoft Docs
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 49f8267c-d887-4d7d-b9b7-80dc624b1261
caps.latest.revision: 4
ms.openlocfilehash: d199c53a748ac57bb2a5f998b5056e39d3e80c0d
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/05/2019
ms.locfileid: "72361180"
---
# <a name="placing-comment-based-help-in-scripts"></a><span data-ttu-id="18f39-102">Inserimento della Guida basata sui commenti negli script</span><span class="sxs-lookup"><span data-stu-id="18f39-102">Placing Comment-Based Help in Scripts</span></span>

<span data-ttu-id="18f39-103">In questo argomento viene illustrato dove posizionare la guida basata su commenti per uno script in modo che il cmdlet `Get-Help` associ l'argomento della guida basato sui commenti con gli script e non con le funzioni eventualmente presenti nello script.</span><span class="sxs-lookup"><span data-stu-id="18f39-103">This topic explains where to place comment-based help for a script so that the `Get-Help` cmdlet associates the comment-based help topic with scripts and not with any functions that might be in the script.</span></span>

## <a name="where-to-place-comment-based-help-for-a-script"></a><span data-ttu-id="18f39-104">Posizione della Guida basata su commenti per uno script</span><span class="sxs-lookup"><span data-stu-id="18f39-104">Where to Place Comment-Based Help for a Script</span></span>

- <span data-ttu-id="18f39-105">All'inizio del file di script.</span><span class="sxs-lookup"><span data-stu-id="18f39-105">At the beginning of the script file.</span></span> <span data-ttu-id="18f39-106">La guida per gli script può essere preceduta dallo script solo da commenti e righe vuote.</span><span class="sxs-lookup"><span data-stu-id="18f39-106">Script Help can be preceded in the script only by comments and blank lines.</span></span>

- <span data-ttu-id="18f39-107">Alla fine del file di script.</span><span class="sxs-lookup"><span data-stu-id="18f39-107">At the end of the script file.</span></span>

  <span data-ttu-id="18f39-108">Se il primo elemento nel corpo dello script (dopo la guida) è una dichiarazione di funzione, devono essere presenti almeno due righe vuote tra la fine della Guida per lo script e la dichiarazione di funzione.</span><span class="sxs-lookup"><span data-stu-id="18f39-108">If the first item in the script body (after the Help) is a function declaration, there must be at least two blank lines between the end of the script Help and the function declaration.</span></span> <span data-ttu-id="18f39-109">In caso contrario, la guida viene interpretata come la guida per la funzione, non per la guida per lo script.</span><span class="sxs-lookup"><span data-stu-id="18f39-109">Otherwise, the Help is interpreted as being Help for the function, not Help for the script.</span></span>

## <a name="examples-of-help-placement-in-a-script"></a><span data-ttu-id="18f39-110">Esempi di posizionamento della Guida in uno script</span><span class="sxs-lookup"><span data-stu-id="18f39-110">Examples of Help Placement in a Script</span></span>

 <span data-ttu-id="18f39-111">Negli esempi seguenti vengono illustrate tutte le opzioni di selezione host per la guida basata su commenti per uno script.</span><span class="sxs-lookup"><span data-stu-id="18f39-111">The following examples show each of the placement options for comment-based help for a script.</span></span>

### <a name="help-at-the-beginning-of-a-script"></a><span data-ttu-id="18f39-112">Guida all'inizio di uno script</span><span class="sxs-lookup"><span data-stu-id="18f39-112">Help at the Beginning of a Script</span></span>

 <span data-ttu-id="18f39-113">Nell'esempio seguente viene illustrato come basato su commenti all'inizio di uno script.</span><span class="sxs-lookup"><span data-stu-id="18f39-113">The following example shows comment-based at the beginning of a script.</span></span>

```
<#
.Description
This script performs a series of network connection tests.
#>

param [string]$ComputerName
...
```

### <a name="help-at-the-end-of-a-script"></a><span data-ttu-id="18f39-114">Guida alla fine di uno script</span><span class="sxs-lookup"><span data-stu-id="18f39-114">Help at the End of a Script</span></span>

 <span data-ttu-id="18f39-115">Nell'esempio seguente viene illustrato come basato su commenti alla fine di uno script.</span><span class="sxs-lookup"><span data-stu-id="18f39-115">The following example shows comment-based at the end of a script.</span></span>

```powershell
...
function Ping { Test-Connection -ComputerName $ComputerName }

<#
.Description
This script performs a series of network connection tests.
#>

```