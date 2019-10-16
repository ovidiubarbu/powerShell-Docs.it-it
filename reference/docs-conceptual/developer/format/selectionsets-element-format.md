---
title: Elemento SelectionSets (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ebbac73a-1c99-4388-9f47-703cd024dc6d
caps.latest.revision: 18
ms.openlocfilehash: a9356635d60d5f8c5d4dec4ec8b7d0aea2b037dd
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/15/2019
ms.locfileid: "72361870"
---
# <a name="selectionsets-element-format"></a><span data-ttu-id="bc1cd-102">Elemento SelectionSet (formato)</span><span class="sxs-lookup"><span data-stu-id="bc1cd-102">SelectionSets Element (Format)</span></span>

<span data-ttu-id="bc1cd-103">Definisce i set comuni di oggetti .NET che possono essere utilizzati da tutte le visualizzazioni del file di formattazione.</span><span class="sxs-lookup"><span data-stu-id="bc1cd-103">Defines the common sets of .NET objects that can be used by all views of the formatting file.</span></span> <span data-ttu-id="bc1cd-104">Le visualizzazioni e i controlli del file di formattazione possono fare riferimento al set completo di oggetti utilizzando solo il nome del set di selezione.</span><span class="sxs-lookup"><span data-stu-id="bc1cd-104">The views and controls of the formatting file can reference the complete set of objects by using only the name of the selection set.</span></span>

<span data-ttu-id="bc1cd-105">Formato dell'elemento SelectionSets dell'elemento di configurazione</span><span class="sxs-lookup"><span data-stu-id="bc1cd-105">Configuration Element SelectionSets Element Format</span></span>

## <a name="syntax"></a><span data-ttu-id="bc1cd-106">Sintassi</span><span class="sxs-lookup"><span data-stu-id="bc1cd-106">Syntax</span></span>

```xml
<SelectionSets>
  <SelectionSet>...</SelectionSet>
</SelectionSets>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="bc1cd-107">Attributi ed elementi</span><span class="sxs-lookup"><span data-stu-id="bc1cd-107">Attributes and Elements</span></span>

<span data-ttu-id="bc1cd-108">Nelle sezioni seguenti vengono descritti gli attributi, gli elementi figlio e l'elemento padre dell'elemento `SelectionSets`.</span><span class="sxs-lookup"><span data-stu-id="bc1cd-108">The following sections describe the attributes, child elements, and parent element of the `SelectionSets` element.</span></span> <span data-ttu-id="bc1cd-109">Ogni elemento figlio definisce un set di oggetti a cui è possibile fare riferimento dal nome del set.</span><span class="sxs-lookup"><span data-stu-id="bc1cd-109">Each child element defines a set of objects that can be referenced by the name of the set.</span></span> <span data-ttu-id="bc1cd-110">L'ordine degli elementi figlio non è significativo.</span><span class="sxs-lookup"><span data-stu-id="bc1cd-110">The order of the child elements is not significant.</span></span>

### <a name="attributes"></a><span data-ttu-id="bc1cd-111">Attributi</span><span class="sxs-lookup"><span data-stu-id="bc1cd-111">Attributes</span></span>

<span data-ttu-id="bc1cd-112">Nessuna.</span><span class="sxs-lookup"><span data-stu-id="bc1cd-112">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="bc1cd-113">Elementi figlio</span><span class="sxs-lookup"><span data-stu-id="bc1cd-113">Child Elements</span></span>

|<span data-ttu-id="bc1cd-114">Elemento</span><span class="sxs-lookup"><span data-stu-id="bc1cd-114">Element</span></span>|<span data-ttu-id="bc1cd-115">Description</span><span class="sxs-lookup"><span data-stu-id="bc1cd-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="bc1cd-116">Elemento SelectionSet (Format)</span><span class="sxs-lookup"><span data-stu-id="bc1cd-116">SelectionSet Element (Format)</span></span>](./selectionset-element-format.md)|<span data-ttu-id="bc1cd-117">Elemento obbligatorio.</span><span class="sxs-lookup"><span data-stu-id="bc1cd-117">Required element.</span></span><br /><br /> <span data-ttu-id="bc1cd-118">Definisce un singolo set di oggetti .NET a cui è possibile fare riferimento dal nome del set.</span><span class="sxs-lookup"><span data-stu-id="bc1cd-118">Defines a single set of .NET objects that can be referenced by the name of the set.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="bc1cd-119">Elementi padre</span><span class="sxs-lookup"><span data-stu-id="bc1cd-119">Parent Elements</span></span>

|<span data-ttu-id="bc1cd-120">Elemento</span><span class="sxs-lookup"><span data-stu-id="bc1cd-120">Element</span></span>|<span data-ttu-id="bc1cd-121">Description</span><span class="sxs-lookup"><span data-stu-id="bc1cd-121">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="bc1cd-122">Elemento Configuration</span><span class="sxs-lookup"><span data-stu-id="bc1cd-122">Configuration Element</span></span>](./configuration-element-format.md)|<span data-ttu-id="bc1cd-123">Rappresenta l'elemento di primo livello di un file di formattazione.</span><span class="sxs-lookup"><span data-stu-id="bc1cd-123">Represents the top-level element of a formatting file.</span></span>|

## <a name="remarks"></a><span data-ttu-id="bc1cd-124">Osservazioni</span><span class="sxs-lookup"><span data-stu-id="bc1cd-124">Remarks</span></span>

<span data-ttu-id="bc1cd-125">È possibile utilizzare i set di selezione quando si dispone di un set di oggetti correlati a cui si desidera fare riferimento utilizzando un solo nome, ad esempio un set di oggetti correlati tramite ereditarietà.</span><span class="sxs-lookup"><span data-stu-id="bc1cd-125">You can use selection sets when you have a set of related objects that you want to reference by using a single name, such as a set of objects that are related through inheritance.</span></span> <span data-ttu-id="bc1cd-126">Quando si definiscono le visualizzazioni, è possibile specificare il set di oggetti utilizzando il nome del set di selezione anziché elencare tutti gli oggetti all'interno di ogni visualizzazione.</span><span class="sxs-lookup"><span data-stu-id="bc1cd-126">When defining your views, you can specify the set of objects by using the name of the selection set instead of listing all the objects within each view.</span></span>

<span data-ttu-id="bc1cd-127">I set di selezione comuni vengono specificati in base al relativo nome quando si definiscono le visualizzazioni del file di formattazione o le definizioni delle viste.</span><span class="sxs-lookup"><span data-stu-id="bc1cd-127">Common selection sets are specified by their name when defining the views of the formatting file or the definitions of the views.</span></span> <span data-ttu-id="bc1cd-128">In questi casi, l'elemento figlio `SelectionSetName` degli elementi `ViewSelectedBy` e `EntrySelectedBy` specifica il set da usare.</span><span class="sxs-lookup"><span data-stu-id="bc1cd-128">In these cases, the `SelectionSetName` child element of the `ViewSelectedBy` and `EntrySelectedBy` elements specifies the set to be used.</span></span> <span data-ttu-id="bc1cd-129">Per ulteriori informazioni sui set di selezione, vedere [definizione di set di oggetti](./defining-selection-sets.md).</span><span class="sxs-lookup"><span data-stu-id="bc1cd-129">For more information about selection sets, see [Defining Sets of Objects](./defining-selection-sets.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="bc1cd-130">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="bc1cd-130">See Also</span></span>

[<span data-ttu-id="bc1cd-131">Elemento Configuration</span><span class="sxs-lookup"><span data-stu-id="bc1cd-131">Configuration Element</span></span>](./configuration-element-format.md)

[<span data-ttu-id="bc1cd-132">Definizione di set di selezione</span><span class="sxs-lookup"><span data-stu-id="bc1cd-132">Defining Selection Sets</span></span>](./defining-selection-sets.md)

[<span data-ttu-id="bc1cd-133">Elemento SelectionSet (Format)</span><span class="sxs-lookup"><span data-stu-id="bc1cd-133">SelectionSet Element (Format)</span></span>](./selectionset-element-format.md)

[<span data-ttu-id="bc1cd-134">Scrittura di un file di formattazione di PowerShell</span><span class="sxs-lookup"><span data-stu-id="bc1cd-134">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
