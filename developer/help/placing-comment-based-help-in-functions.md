---
title: L'inserimento della Guida basata sui commenti nelle funzioni | Microsoft Docs
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 5ec7159e-e4e9-4b21-95df-94244432f679
caps.latest.revision: 5
ms.openlocfilehash: a663bd69be7825b1685f64ff8d3068bdd8ca3265
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62083196"
---
# <a name="placing-comment-based-help-in-functions"></a><span data-ttu-id="8be24-102">Inserimento della Guida basata sui commenti nelle funzioni</span><span class="sxs-lookup"><span data-stu-id="8be24-102">Placing Comment-Based Help in Functions</span></span>

<span data-ttu-id="8be24-103">Questo argomento viene illustrato dove posizionare la Guida basata su commenti per una funzione in modo che il `Get-Help` cmdlet consente di associare l'argomento della Guida basata sui commenti con la funzione corretta.</span><span class="sxs-lookup"><span data-stu-id="8be24-103">This topic explains where to place comment-based help for a function so that the `Get-Help` cmdlet associates the comment-based help topic with the correct function.</span></span>

## <a name="where-to-place-comment-based-help-for-a-function"></a><span data-ttu-id="8be24-104">La posizione della Guida basata su commenti per una funzione</span><span class="sxs-lookup"><span data-stu-id="8be24-104">Where to Place Comment-Based Help for a Function</span></span>

- <span data-ttu-id="8be24-105">All'inizio del corpo della funzione.</span><span class="sxs-lookup"><span data-stu-id="8be24-105">At the beginning of the function body.</span></span>

- <span data-ttu-id="8be24-106">Alla fine del corpo della funzione.</span><span class="sxs-lookup"><span data-stu-id="8be24-106">At the end of the function body.</span></span>

- <span data-ttu-id="8be24-107">Prima di `Function` (parola chiave).</span><span class="sxs-lookup"><span data-stu-id="8be24-107">Before the `Function` keyword.</span></span> <span data-ttu-id="8be24-108">Quando la funzione è in uno script o un modulo di script, non può esistere più di una riga vuota tra l'ultima riga delle informazioni della Guida basata sui commenti e i `Function` (parola chiave).</span><span class="sxs-lookup"><span data-stu-id="8be24-108">When the function is in a script or script module, there cannot be more than one blank line between the last line of the comment-based help and the `Function` keyword.</span></span> <span data-ttu-id="8be24-109">In caso contrario, `Get-Help` associa la Guida in linea con lo script, non con la funzione.</span><span class="sxs-lookup"><span data-stu-id="8be24-109">Otherwise, `Get-Help` associates the help with the script, not with the function.</span></span>

## <a name="examples-of-help-placement-in-a-function"></a><span data-ttu-id="8be24-110">Esempi di posizionamento della Guida in una funzione</span><span class="sxs-lookup"><span data-stu-id="8be24-110">Examples of Help Placement in a Function</span></span>

 <span data-ttu-id="8be24-111">Gli esempi seguenti illustrano le opzioni di selezione host per tre della Guida basata su commenti per una funzione.</span><span class="sxs-lookup"><span data-stu-id="8be24-111">The following examples show each of the three placement options for comment-based help for a function.</span></span>

### <a name="help-at-the-beginning-of-a-function-body"></a><span data-ttu-id="8be24-112">Guida in linea all'inizio di un corpo di funzione</span><span class="sxs-lookup"><span data-stu-id="8be24-112">Help at the Beginning of a Function Body</span></span>

 <span data-ttu-id="8be24-113">Nell'esempio seguente viene basata sui commenti all'inizio di un corpo della funzione.</span><span class="sxs-lookup"><span data-stu-id="8be24-113">The following example shows comment-based at the beginning of a function body.</span></span>

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

### <a name="help-at-the-end-of-a-function-body"></a><span data-ttu-id="8be24-114">Guida alla fine di un corpo di funzione</span><span class="sxs-lookup"><span data-stu-id="8be24-114">Help at the End of a Function Body</span></span>

 <span data-ttu-id="8be24-115">Nell'esempio seguente viene basata sui commenti alla fine di un corpo della funzione.</span><span class="sxs-lookup"><span data-stu-id="8be24-115">The following example shows comment-based at the end of a function body.</span></span>

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

### <a name="help-before-the-function-keyword"></a><span data-ttu-id="8be24-116">Guida in linea prima della parola chiave (funzione)</span><span class="sxs-lookup"><span data-stu-id="8be24-116">Help Before the Function Keyword</span></span>

 <span data-ttu-id="8be24-117">Gli esempi seguenti mostrano basata sui commenti sulla riga prima della parola chiave di funzione.</span><span class="sxs-lookup"><span data-stu-id="8be24-117">The following examples shows comment-based on the line before the function keyword.</span></span>

```powershell

<#
    .Description
    The MyProcess function gets the Windows PowerShell process.
#>
function MyFunction { Get-Process powershell}

```