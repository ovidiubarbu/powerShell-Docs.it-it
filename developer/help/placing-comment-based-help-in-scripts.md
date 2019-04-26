---
title: L'inserimento della Guida basata sui commenti negli script | Microsoft Docs
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 49f8267c-d887-4d7d-b9b7-80dc624b1261
caps.latest.revision: 4
ms.openlocfilehash: d199c53a748ac57bb2a5f998b5056e39d3e80c0d
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62083230"
---
# <a name="placing-comment-based-help-in-scripts"></a><span data-ttu-id="356d0-102">Inserimento della Guida basata sui commenti negli script</span><span class="sxs-lookup"><span data-stu-id="356d0-102">Placing Comment-Based Help in Scripts</span></span>

<span data-ttu-id="356d0-103">Questo argomento viene illustrato dove posizionare la Guida basata su commenti per uno script in modo che il `Get-Help` cmdlet consente di associare l'argomento della Guida basata sui commenti con gli script e non con le funzioni che potrebbero essere nello script.</span><span class="sxs-lookup"><span data-stu-id="356d0-103">This topic explains where to place comment-based help for a script so that the `Get-Help` cmdlet associates the comment-based help topic with scripts and not with any functions that might be in the script.</span></span>

## <a name="where-to-place-comment-based-help-for-a-script"></a><span data-ttu-id="356d0-104">La posizione della Guida basata su commenti per uno Script</span><span class="sxs-lookup"><span data-stu-id="356d0-104">Where to Place Comment-Based Help for a Script</span></span>

- <span data-ttu-id="356d0-105">All'inizio del file di script.</span><span class="sxs-lookup"><span data-stu-id="356d0-105">At the beginning of the script file.</span></span> <span data-ttu-id="356d0-106">Lo script Help può essere preceduto nello script solo per i commenti e le righe vuote.</span><span class="sxs-lookup"><span data-stu-id="356d0-106">Script Help can be preceded in the script only by comments and blank lines.</span></span>

- <span data-ttu-id="356d0-107">Alla fine del file di script.</span><span class="sxs-lookup"><span data-stu-id="356d0-107">At the end of the script file.</span></span>

  <span data-ttu-id="356d0-108">Se il primo elemento nel corpo dello script (dopo la Guida in linea) è una dichiarazione di funzione, deve esserci almeno due righe vuote tra la fine dello script della Guida in linea e la dichiarazione di funzione.</span><span class="sxs-lookup"><span data-stu-id="356d0-108">If the first item in the script body (after the Help) is a function declaration, there must be at least two blank lines between the end of the script Help and the function declaration.</span></span> <span data-ttu-id="356d0-109">In caso contrario, la Guida in linea viene interpretato come guida per la funzione, non della Guida per lo script.</span><span class="sxs-lookup"><span data-stu-id="356d0-109">Otherwise, the Help is interpreted as being Help for the function, not Help for the script.</span></span>

## <a name="examples-of-help-placement-in-a-script"></a><span data-ttu-id="356d0-110">Esempi di posizionamento della Guida in uno Script</span><span class="sxs-lookup"><span data-stu-id="356d0-110">Examples of Help Placement in a Script</span></span>

 <span data-ttu-id="356d0-111">Gli esempi seguenti illustrano le opzioni di posizionamento della Guida basata su commenti per uno script.</span><span class="sxs-lookup"><span data-stu-id="356d0-111">The following examples show each of the placement options for comment-based help for a script.</span></span>

### <a name="help-at-the-beginning-of-a-script"></a><span data-ttu-id="356d0-112">Guida in linea all'inizio di uno Script</span><span class="sxs-lookup"><span data-stu-id="356d0-112">Help at the Beginning of a Script</span></span>

 <span data-ttu-id="356d0-113">Nell'esempio seguente viene basata sui commenti all'inizio di uno script.</span><span class="sxs-lookup"><span data-stu-id="356d0-113">The following example shows comment-based at the beginning of a script.</span></span>

```
<#
.Description
This script performs a series of network connection tests.
#>

param [string]$ComputerName
...
```

### <a name="help-at-the-end-of-a-script"></a><span data-ttu-id="356d0-114">Guida alla fine di uno Script</span><span class="sxs-lookup"><span data-stu-id="356d0-114">Help at the End of a Script</span></span>

 <span data-ttu-id="356d0-115">Nell'esempio seguente viene basata sui commenti alla fine di uno script.</span><span class="sxs-lookup"><span data-stu-id="356d0-115">The following example shows comment-based at the end of a script.</span></span>

```powershell
...
function Ping { Test-Connection -ComputerName $ComputerName }

<#
.Description
This script performs a series of network connection tests.
#>

```