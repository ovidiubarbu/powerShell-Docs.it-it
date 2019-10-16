---
title: Inserimento della Guida basata su commenti in funzioni | Microsoft Docs
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 5ec7159e-e4e9-4b21-95df-94244432f679
caps.latest.revision: 5
ms.openlocfilehash: a663bd69be7825b1685f64ff8d3068bdd8ca3265
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/15/2019
ms.locfileid: "72367780"
---
# <a name="placing-comment-based-help-in-functions"></a><span data-ttu-id="34dff-102">Inserimento della Guida basata sui commenti nelle funzioni</span><span class="sxs-lookup"><span data-stu-id="34dff-102">Placing Comment-Based Help in Functions</span></span>

<span data-ttu-id="34dff-103">Questo argomento spiega dove posizionare la guida basata su commenti per una funzione in modo che il cmdlet `Get-Help` associ l'argomento della guida basato su commenti con la funzione corretta.</span><span class="sxs-lookup"><span data-stu-id="34dff-103">This topic explains where to place comment-based help for a function so that the `Get-Help` cmdlet associates the comment-based help topic with the correct function.</span></span>

## <a name="where-to-place-comment-based-help-for-a-function"></a><span data-ttu-id="34dff-104">Posizione della Guida basata su commenti per una funzione</span><span class="sxs-lookup"><span data-stu-id="34dff-104">Where to Place Comment-Based Help for a Function</span></span>

- <span data-ttu-id="34dff-105">All'inizio del corpo della funzione.</span><span class="sxs-lookup"><span data-stu-id="34dff-105">At the beginning of the function body.</span></span>

- <span data-ttu-id="34dff-106">Alla fine del corpo della funzione.</span><span class="sxs-lookup"><span data-stu-id="34dff-106">At the end of the function body.</span></span>

- <span data-ttu-id="34dff-107">Prima della parola chiave `Function`.</span><span class="sxs-lookup"><span data-stu-id="34dff-107">Before the `Function` keyword.</span></span> <span data-ttu-id="34dff-108">Quando la funzione si trova in uno script o in un modulo di script, non può essere presente più di una riga vuota tra l'ultima riga della Guida basata su commenti e la parola chiave `Function`.</span><span class="sxs-lookup"><span data-stu-id="34dff-108">When the function is in a script or script module, there cannot be more than one blank line between the last line of the comment-based help and the `Function` keyword.</span></span> <span data-ttu-id="34dff-109">In caso contrario, `Get-Help` associa la Guida allo script, non alla funzione.</span><span class="sxs-lookup"><span data-stu-id="34dff-109">Otherwise, `Get-Help` associates the help with the script, not with the function.</span></span>

## <a name="examples-of-help-placement-in-a-function"></a><span data-ttu-id="34dff-110">Esempi di posizionamento della Guida in una funzione</span><span class="sxs-lookup"><span data-stu-id="34dff-110">Examples of Help Placement in a Function</span></span>

 <span data-ttu-id="34dff-111">Gli esempi seguenti illustrano ognuna delle tre opzioni di selezione host per la guida basata su commenti per una funzione.</span><span class="sxs-lookup"><span data-stu-id="34dff-111">The following examples show each of the three placement options for comment-based help for a function.</span></span>

### <a name="help-at-the-beginning-of-a-function-body"></a><span data-ttu-id="34dff-112">Guida all'inizio del corpo di una funzione</span><span class="sxs-lookup"><span data-stu-id="34dff-112">Help at the Beginning of a Function Body</span></span>

 <span data-ttu-id="34dff-113">Nell'esempio seguente viene illustrato l'oggetto basato su commenti all'inizio del corpo di una funzione.</span><span class="sxs-lookup"><span data-stu-id="34dff-113">The following example shows comment-based at the beginning of a function body.</span></span>

```powershell

function MyProcess
{
    <#
       .Description
       The MyProcess function gets the Windows PowerShell process.
    #>

    Get-Process powershell
}

```

### <a name="help-at-the-end-of-a-function-body"></a><span data-ttu-id="34dff-114">Guida alla fine del corpo di una funzione</span><span class="sxs-lookup"><span data-stu-id="34dff-114">Help at the End of a Function Body</span></span>

 <span data-ttu-id="34dff-115">Nell'esempio seguente viene illustrato un oggetto basato su commenti alla fine del corpo di una funzione.</span><span class="sxs-lookup"><span data-stu-id="34dff-115">The following example shows comment-based at the end of a function body.</span></span>

```powershell

function MyFunction
{
    Get-Process powershell

    <#
       .Description
       The MyProcess function gets the Windows PowerShell process.
    #>
}

```

### <a name="help-before-the-function-keyword"></a><span data-ttu-id="34dff-116">Guida prima della parola chiave Function</span><span class="sxs-lookup"><span data-stu-id="34dff-116">Help Before the Function Keyword</span></span>

 <span data-ttu-id="34dff-117">Negli esempi seguenti viene illustrato il commento basato sulla riga prima della parola chiave Function.</span><span class="sxs-lookup"><span data-stu-id="34dff-117">The following examples shows comment-based on the line before the function keyword.</span></span>

```powershell

<#
    .Description
    The MyProcess function gets the Windows PowerShell process.
#>
function MyFunction { Get-Process powershell}

```