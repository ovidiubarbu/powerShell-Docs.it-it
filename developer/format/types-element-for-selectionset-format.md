---
title: I tipi di elemento per SelectionSet (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 4606fec0-ff31-4d36-af68-227405335ec3
caps.latest.revision: 15
ms.openlocfilehash: 0427367efa2c8a7e352d718706d1341a0c8e3621
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/03/2019
ms.locfileid: "56862377"
---
# <a name="types-element-for-selectionset-format"></a><span data-ttu-id="f593f-102">Elemento Types per SelectionSet (formato)</span><span class="sxs-lookup"><span data-stu-id="f593f-102">Types Element for SelectionSet (Format)</span></span>

<span data-ttu-id="f593f-103">Definisce gli oggetti .NET nella selezione impostate.</span><span class="sxs-lookup"><span data-stu-id="f593f-103">Defines the .NET objects that are in the selection set.</span></span>

<span data-ttu-id="f593f-104">Configurazione (formato) elemento SelectionSets (formato) SelectionSet elemento (formato) i tipi di elemento (formato)</span><span class="sxs-lookup"><span data-stu-id="f593f-104">Configuration Element (Format) SelectionSets Element (Format) SelectionSet Element (Format) Types Element (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="f593f-105">Sintassi</span><span class="sxs-lookup"><span data-stu-id="f593f-105">Syntax</span></span>

```xml
<Types>
  <TypeName>Nameof.NetType</TypeName>
</Types>

```

## <a name="attributes-and-elements"></a><span data-ttu-id="f593f-106">Attributi ed elementi</span><span class="sxs-lookup"><span data-stu-id="f593f-106">Attributes and Elements</span></span>

<span data-ttu-id="f593f-107">Le sezioni seguenti descrivono gli attributi e gli elementi figlio dell'elemento padre del `Types` elemento.</span><span class="sxs-lookup"><span data-stu-id="f593f-107">The following sections describe the attributes, child elements, and the parent element of the `Types` element.</span></span> <span data-ttu-id="f593f-108">Deve esistere almeno un elemento figlio, ma non è definito alcun limite massimo al numero di elementi figlio che possono essere aggiunti.</span><span class="sxs-lookup"><span data-stu-id="f593f-108">There must be at least one child element, but there is no maximum limit to the number of child elements that can be added.</span></span>

### <a name="attributes"></a><span data-ttu-id="f593f-109">Attributes</span><span class="sxs-lookup"><span data-stu-id="f593f-109">Attributes</span></span>

<span data-ttu-id="f593f-110">Nessuna.</span><span class="sxs-lookup"><span data-stu-id="f593f-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="f593f-111">Elementi figlio</span><span class="sxs-lookup"><span data-stu-id="f593f-111">Child Elements</span></span>

|<span data-ttu-id="f593f-112">Elemento</span><span class="sxs-lookup"><span data-stu-id="f593f-112">Element</span></span>|<span data-ttu-id="f593f-113">Description</span><span class="sxs-lookup"><span data-stu-id="f593f-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="f593f-114">Elemento TypeName di tipi (formato)</span><span class="sxs-lookup"><span data-stu-id="f593f-114">TypeName Element of Types (Format)</span></span>](./typename-element-for-types-format.md)|<span data-ttu-id="f593f-115">Elemento obbligatorio.</span><span class="sxs-lookup"><span data-stu-id="f593f-115">Required element.</span></span><br /><br /> <span data-ttu-id="f593f-116">Specifica l'oggetto .NET a cui appartiene il set di selezione.</span><span class="sxs-lookup"><span data-stu-id="f593f-116">Specifies the .NET object that belongs to the selection set.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="f593f-117">Elementi padre</span><span class="sxs-lookup"><span data-stu-id="f593f-117">Parent Elements</span></span>

|<span data-ttu-id="f593f-118">Elemento</span><span class="sxs-lookup"><span data-stu-id="f593f-118">Element</span></span>|<span data-ttu-id="f593f-119">Description</span><span class="sxs-lookup"><span data-stu-id="f593f-119">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="f593f-120">Elemento SelectionSet (formato)</span><span class="sxs-lookup"><span data-stu-id="f593f-120">SelectionSet Element (Format)</span></span>](./selectionset-element-format.md)|<span data-ttu-id="f593f-121">Definisce un set di oggetti .NET che possono fare riferimento il nome del set.</span><span class="sxs-lookup"><span data-stu-id="f593f-121">Defines a set of .NET objects that can be referenced by the name of the set.</span></span>|

## <a name="remarks"></a><span data-ttu-id="f593f-122">Osservazioni</span><span class="sxs-lookup"><span data-stu-id="f593f-122">Remarks</span></span>

<span data-ttu-id="f593f-123">Gli oggetti definiti da questo elemento costituiscono un set di selezione che può essere utilizzato da una visualizzazione, da una definizione di una vista (visualizzazioni possono avere più definizioni,) o quando si specifica una condizione di selezione.</span><span class="sxs-lookup"><span data-stu-id="f593f-123">The objects defined by this element make up a selection set that can be used by a view, by a definition of a view (views can have multiple definitions), or when specifying a selection condition.</span></span>  <span data-ttu-id="f593f-124">Per altre informazioni sui set di selezione, vedere [definizione imposta di oggetti](./defining-selection-sets.md).</span><span class="sxs-lookup"><span data-stu-id="f593f-124">For more information about selection sets, see [Defining Sets of Objects](./defining-selection-sets.md).</span></span>

## <a name="example"></a><span data-ttu-id="f593f-125">Esempio</span><span class="sxs-lookup"><span data-stu-id="f593f-125">Example</span></span>

<span data-ttu-id="f593f-126">Questo esempio viene illustrato un `SelectionSet` elemento che definisce i quattro tipi di .NET.</span><span class="sxs-lookup"><span data-stu-id="f593f-126">This example shows a `SelectionSet` element that defines four .NET types.</span></span>

```xml
<SelectionSets>
  <SelectionSet>
    <Name>FileSystemTypes</Name>
    <Types>
     <TypeName>System.IO.DirectoryInfo</TypeName>
     <TypeName>System.IO.FileInfo</TypeName>
     <TypeName>Deserialized.System.IO.DirectoryInfo</TypeName>
     <TypeName>Deserialized.System.IO.FileInfo</TypeName>
    </Types>
  </SelectionSet>
</SelectionSets>
```

## <a name="see-also"></a><span data-ttu-id="f593f-127">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="f593f-127">See Also</span></span>

[<span data-ttu-id="f593f-128">La definizione di set di oggetti</span><span class="sxs-lookup"><span data-stu-id="f593f-128">Defining Sets of Objects</span></span>](./defining-selection-sets.md)

[<span data-ttu-id="f593f-129">Elemento SelectionSet (formato)</span><span class="sxs-lookup"><span data-stu-id="f593f-129">SelectionSet Element (Format)</span></span>](./selectionset-element-format.md)

[<span data-ttu-id="f593f-130">Elemento TypeName di tipi (formato)</span><span class="sxs-lookup"><span data-stu-id="f593f-130">TypeName Element of Types (Format)</span></span>](./typename-element-for-types-format.md)

[<span data-ttu-id="f593f-131">La scrittura di un File di formattazione di PowerShell</span><span class="sxs-lookup"><span data-stu-id="f593f-131">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
