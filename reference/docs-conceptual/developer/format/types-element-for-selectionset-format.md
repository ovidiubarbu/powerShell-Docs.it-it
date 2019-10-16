---
title: Elemento types per SelectionSet (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 4606fec0-ff31-4d36-af68-227405335ec3
caps.latest.revision: 15
ms.openlocfilehash: 0427367efa2c8a7e352d718706d1341a0c8e3621
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/15/2019
ms.locfileid: "72367960"
---
# <a name="types-element-for-selectionset-format"></a><span data-ttu-id="e6964-102">Elemento Types per SelectionSet (formato)</span><span class="sxs-lookup"><span data-stu-id="e6964-102">Types Element for SelectionSet (Format)</span></span>

<span data-ttu-id="e6964-103">Definisce gli oggetti .NET presenti nel set di selezione.</span><span class="sxs-lookup"><span data-stu-id="e6964-103">Defines the .NET objects that are in the selection set.</span></span>

<span data-ttu-id="e6964-104">Elemento Configuration (Format) elemento SelectionSets (Format) elemento types (Format) elemento SelectionSet (Format)</span><span class="sxs-lookup"><span data-stu-id="e6964-104">Configuration Element (Format) SelectionSets Element (Format) SelectionSet Element (Format) Types Element (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="e6964-105">Sintassi</span><span class="sxs-lookup"><span data-stu-id="e6964-105">Syntax</span></span>

```xml
<Types>
  <TypeName>Nameof.NetType</TypeName>
</Types>

```

## <a name="attributes-and-elements"></a><span data-ttu-id="e6964-106">Attributi ed elementi</span><span class="sxs-lookup"><span data-stu-id="e6964-106">Attributes and Elements</span></span>

<span data-ttu-id="e6964-107">Nelle sezioni seguenti vengono descritti gli attributi, gli elementi figlio e l'elemento padre dell'elemento `Types`.</span><span class="sxs-lookup"><span data-stu-id="e6964-107">The following sections describe the attributes, child elements, and the parent element of the `Types` element.</span></span> <span data-ttu-id="e6964-108">Deve essere presente almeno un elemento figlio, ma non esiste un limite massimo per il numero di elementi figlio che è possibile aggiungere.</span><span class="sxs-lookup"><span data-stu-id="e6964-108">There must be at least one child element, but there is no maximum limit to the number of child elements that can be added.</span></span>

### <a name="attributes"></a><span data-ttu-id="e6964-109">Attributi</span><span class="sxs-lookup"><span data-stu-id="e6964-109">Attributes</span></span>

<span data-ttu-id="e6964-110">Nessuna.</span><span class="sxs-lookup"><span data-stu-id="e6964-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="e6964-111">Elementi figlio</span><span class="sxs-lookup"><span data-stu-id="e6964-111">Child Elements</span></span>

|<span data-ttu-id="e6964-112">Elemento</span><span class="sxs-lookup"><span data-stu-id="e6964-112">Element</span></span>|<span data-ttu-id="e6964-113">Description</span><span class="sxs-lookup"><span data-stu-id="e6964-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="e6964-114">Elemento TypeName dei tipi (Format)</span><span class="sxs-lookup"><span data-stu-id="e6964-114">TypeName Element of Types (Format)</span></span>](./typename-element-for-types-format.md)|<span data-ttu-id="e6964-115">Elemento obbligatorio.</span><span class="sxs-lookup"><span data-stu-id="e6964-115">Required element.</span></span><br /><br /> <span data-ttu-id="e6964-116">Specifica l'oggetto .NET che appartiene al set di selezione.</span><span class="sxs-lookup"><span data-stu-id="e6964-116">Specifies the .NET object that belongs to the selection set.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="e6964-117">Elementi padre</span><span class="sxs-lookup"><span data-stu-id="e6964-117">Parent Elements</span></span>

|<span data-ttu-id="e6964-118">Elemento</span><span class="sxs-lookup"><span data-stu-id="e6964-118">Element</span></span>|<span data-ttu-id="e6964-119">Description</span><span class="sxs-lookup"><span data-stu-id="e6964-119">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="e6964-120">Elemento SelectionSet (Format)</span><span class="sxs-lookup"><span data-stu-id="e6964-120">SelectionSet Element (Format)</span></span>](./selectionset-element-format.md)|<span data-ttu-id="e6964-121">Definisce un set di oggetti .NET a cui è possibile fare riferimento dal nome del set.</span><span class="sxs-lookup"><span data-stu-id="e6964-121">Defines a set of .NET objects that can be referenced by the name of the set.</span></span>|

## <a name="remarks"></a><span data-ttu-id="e6964-122">Osservazioni</span><span class="sxs-lookup"><span data-stu-id="e6964-122">Remarks</span></span>

<span data-ttu-id="e6964-123">Gli oggetti definiti da questo elemento costituiscono un set di selezione che può essere utilizzato da una vista, da una definizione di una vista (le visualizzazioni possono avere più definizioni) o quando si specifica una condizione di selezione.</span><span class="sxs-lookup"><span data-stu-id="e6964-123">The objects defined by this element make up a selection set that can be used by a view, by a definition of a view (views can have multiple definitions), or when specifying a selection condition.</span></span>  <span data-ttu-id="e6964-124">Per ulteriori informazioni sui set di selezione, vedere [definizione di set di oggetti](./defining-selection-sets.md).</span><span class="sxs-lookup"><span data-stu-id="e6964-124">For more information about selection sets, see [Defining Sets of Objects](./defining-selection-sets.md).</span></span>

## <a name="example"></a><span data-ttu-id="e6964-125">Esempio</span><span class="sxs-lookup"><span data-stu-id="e6964-125">Example</span></span>

<span data-ttu-id="e6964-126">Questo esempio mostra un elemento `SelectionSet` che definisce quattro tipi .NET.</span><span class="sxs-lookup"><span data-stu-id="e6964-126">This example shows a `SelectionSet` element that defines four .NET types.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="e6964-127">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="e6964-127">See Also</span></span>

[<span data-ttu-id="e6964-128">Definizione di set di oggetti</span><span class="sxs-lookup"><span data-stu-id="e6964-128">Defining Sets of Objects</span></span>](./defining-selection-sets.md)

[<span data-ttu-id="e6964-129">Elemento SelectionSet (Format)</span><span class="sxs-lookup"><span data-stu-id="e6964-129">SelectionSet Element (Format)</span></span>](./selectionset-element-format.md)

[<span data-ttu-id="e6964-130">Elemento TypeName dei tipi (Format)</span><span class="sxs-lookup"><span data-stu-id="e6964-130">TypeName Element of Types (Format)</span></span>](./typename-element-for-types-format.md)

[<span data-ttu-id="e6964-131">Scrittura di un file di formattazione di PowerShell</span><span class="sxs-lookup"><span data-stu-id="e6964-131">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
