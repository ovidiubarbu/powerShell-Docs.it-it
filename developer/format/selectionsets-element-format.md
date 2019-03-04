---
title: Elemento SelectionSets (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ebbac73a-1c99-4388-9f47-703cd024dc6d
caps.latest.revision: 18
ms.openlocfilehash: a9356635d60d5f8c5d4dec4ec8b7d0aea2b037dd
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/03/2019
ms.locfileid: "56853567"
---
# <a name="selectionsets-element-format"></a><span data-ttu-id="bc259-102">Elemento SelectionSet (formato)</span><span class="sxs-lookup"><span data-stu-id="bc259-102">SelectionSets Element (Format)</span></span>

<span data-ttu-id="bc259-103">Definisce il set di oggetti .NET che possono essere usati da tutte le visualizzazioni del file di formattazione comuni.</span><span class="sxs-lookup"><span data-stu-id="bc259-103">Defines the common sets of .NET objects that can be used by all views of the formatting file.</span></span> <span data-ttu-id="bc259-104">I controlli del file di formattazione e le visualizzazioni possono fare riferimento il set completo di oggetti utilizzando solo il nome del set di selezione.</span><span class="sxs-lookup"><span data-stu-id="bc259-104">The views and controls of the formatting file can reference the complete set of objects by using only the name of the selection set.</span></span>

<span data-ttu-id="bc259-105">Formato elemento SelectionSets elemento di configurazione</span><span class="sxs-lookup"><span data-stu-id="bc259-105">Configuration Element SelectionSets Element Format</span></span>

## <a name="syntax"></a><span data-ttu-id="bc259-106">Sintassi</span><span class="sxs-lookup"><span data-stu-id="bc259-106">Syntax</span></span>

```xml
<SelectionSets>
  <SelectionSet>...</SelectionSet>
</SelectionSets>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="bc259-107">Attributi ed elementi</span><span class="sxs-lookup"><span data-stu-id="bc259-107">Attributes and Elements</span></span>

<span data-ttu-id="bc259-108">Le sezioni seguenti descrivono gli attributi, elementi figlio ed elemento padre dell'elemento di `SelectionSets` elemento.</span><span class="sxs-lookup"><span data-stu-id="bc259-108">The following sections describe the attributes, child elements, and parent element of the `SelectionSets` element.</span></span> <span data-ttu-id="bc259-109">Ogni elemento figlio definisce un set di oggetti che possono fare riferimento il nome del set.</span><span class="sxs-lookup"><span data-stu-id="bc259-109">Each child element defines a set of objects that can be referenced by the name of the set.</span></span> <span data-ttu-id="bc259-110">L'ordine degli elementi figlio non è significativo.</span><span class="sxs-lookup"><span data-stu-id="bc259-110">The order of the child elements is not significant.</span></span>

### <a name="attributes"></a><span data-ttu-id="bc259-111">Attributes</span><span class="sxs-lookup"><span data-stu-id="bc259-111">Attributes</span></span>

<span data-ttu-id="bc259-112">Nessuna.</span><span class="sxs-lookup"><span data-stu-id="bc259-112">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="bc259-113">Elementi figlio</span><span class="sxs-lookup"><span data-stu-id="bc259-113">Child Elements</span></span>

|<span data-ttu-id="bc259-114">Elemento</span><span class="sxs-lookup"><span data-stu-id="bc259-114">Element</span></span>|<span data-ttu-id="bc259-115">Description</span><span class="sxs-lookup"><span data-stu-id="bc259-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="bc259-116">Elemento SelectionSet (formato)</span><span class="sxs-lookup"><span data-stu-id="bc259-116">SelectionSet Element (Format)</span></span>](./selectionset-element-format.md)|<span data-ttu-id="bc259-117">Elemento obbligatorio.</span><span class="sxs-lookup"><span data-stu-id="bc259-117">Required element.</span></span><br /><br /> <span data-ttu-id="bc259-118">Definisce un singolo set di oggetti .NET che possono fare riferimento il nome del set.</span><span class="sxs-lookup"><span data-stu-id="bc259-118">Defines a single set of .NET objects that can be referenced by the name of the set.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="bc259-119">Elementi padre</span><span class="sxs-lookup"><span data-stu-id="bc259-119">Parent Elements</span></span>

|<span data-ttu-id="bc259-120">Elemento</span><span class="sxs-lookup"><span data-stu-id="bc259-120">Element</span></span>|<span data-ttu-id="bc259-121">Description</span><span class="sxs-lookup"><span data-stu-id="bc259-121">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="bc259-122">Elemento di configurazione</span><span class="sxs-lookup"><span data-stu-id="bc259-122">Configuration Element</span></span>](./configuration-element-format.md)|<span data-ttu-id="bc259-123">Rappresenta l'elemento di livello superiore di un file di formattazione.</span><span class="sxs-lookup"><span data-stu-id="bc259-123">Represents the top-level element of a formatting file.</span></span>|

## <a name="remarks"></a><span data-ttu-id="bc259-124">Osservazioni</span><span class="sxs-lookup"><span data-stu-id="bc259-124">Remarks</span></span>

<span data-ttu-id="bc259-125">Quando si dispone di un set di oggetti correlati che si desidera fare riferimento tramite un solo nome, ad esempio un set di oggetti che sono correlati tramite l'ereditarietà, è possibile usare set di selezione.</span><span class="sxs-lookup"><span data-stu-id="bc259-125">You can use selection sets when you have a set of related objects that you want to reference by using a single name, such as a set of objects that are related through inheritance.</span></span> <span data-ttu-id="bc259-126">Quando si definiscono le visualizzazioni, è possibile specificare il set di oggetti utilizzando il nome della selezione set anziché elencare tutti gli oggetti all'interno di ogni visualizzazione.</span><span class="sxs-lookup"><span data-stu-id="bc259-126">When defining your views, you can specify the set of objects by using the name of the selection set instead of listing all the objects within each view.</span></span>

<span data-ttu-id="bc259-127">Set di selezione comune vengono specificati in base al nome quando si definisce le viste del file di formattazione e le definizioni delle viste.</span><span class="sxs-lookup"><span data-stu-id="bc259-127">Common selection sets are specified by their name when defining the views of the formatting file or the definitions of the views.</span></span> <span data-ttu-id="bc259-128">In questi casi, il `SelectionSetName` elemento figlio dell'elemento di `ViewSelectedBy` e `EntrySelectedBy` elementi specifica il set da utilizzare.</span><span class="sxs-lookup"><span data-stu-id="bc259-128">In these cases, the `SelectionSetName` child element of the `ViewSelectedBy` and `EntrySelectedBy` elements specifies the set to be used.</span></span> <span data-ttu-id="bc259-129">Per altre informazioni sui set di selezione, vedere [definizione imposta di oggetti](./defining-selection-sets.md).</span><span class="sxs-lookup"><span data-stu-id="bc259-129">For more information about selection sets, see [Defining Sets of Objects](./defining-selection-sets.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="bc259-130">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="bc259-130">See Also</span></span>

[<span data-ttu-id="bc259-131">Elemento di configurazione</span><span class="sxs-lookup"><span data-stu-id="bc259-131">Configuration Element</span></span>](./configuration-element-format.md)

[<span data-ttu-id="bc259-132">La definizione di set di selezione</span><span class="sxs-lookup"><span data-stu-id="bc259-132">Defining Selection Sets</span></span>](./defining-selection-sets.md)

[<span data-ttu-id="bc259-133">Elemento SelectionSet (formato)</span><span class="sxs-lookup"><span data-stu-id="bc259-133">SelectionSet Element (Format)</span></span>](./selectionset-element-format.md)

[<span data-ttu-id="bc259-134">La scrittura di un File di formattazione di PowerShell</span><span class="sxs-lookup"><span data-stu-id="bc259-134">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
