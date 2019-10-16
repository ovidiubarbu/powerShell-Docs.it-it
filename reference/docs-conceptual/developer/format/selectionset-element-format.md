---
title: Elemento SelectionSet (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 848e7acd-d578-4fd1-a575-c0c3b9b5e68a
caps.latest.revision: 17
ms.openlocfilehash: c809aa6c3a40d16cfd2fd99065a846d265ec0f61
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/15/2019
ms.locfileid: "72368380"
---
# <a name="selectionset-element-format"></a><span data-ttu-id="3d527-102">Elemento SelectionSet (formato)</span><span class="sxs-lookup"><span data-stu-id="3d527-102">SelectionSet Element (Format)</span></span>

<span data-ttu-id="3d527-103">Definisce un set di oggetti .NET a cui è possibile fare riferimento dal nome del set.</span><span class="sxs-lookup"><span data-stu-id="3d527-103">Defines a set of .NET objects that can be referenced by the name of the set.</span></span>

<span data-ttu-id="3d527-104">Elemento Configuration (Format) elemento SelectionSets (Format) elemento SelectionSet (Format)</span><span class="sxs-lookup"><span data-stu-id="3d527-104">Configuration Element (Format) SelectionSets Element (Format) SelectionSet Element (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="3d527-105">Sintassi</span><span class="sxs-lookup"><span data-stu-id="3d527-105">Syntax</span></span>

```xml
<SelectionSet>
  <Name>SelectionSetName</Name>
  <Types>...</Types>
</SelectionSet>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="3d527-106">Attributi ed elementi</span><span class="sxs-lookup"><span data-stu-id="3d527-106">Attributes and Elements</span></span>

<span data-ttu-id="3d527-107">Nelle sezioni seguenti vengono descritti gli attributi, gli elementi figlio e l'elemento padre dell'elemento `SelectionSet`.</span><span class="sxs-lookup"><span data-stu-id="3d527-107">The following sections describe the attributes, child elements, and the parent element of the `SelectionSet` element.</span></span> <span data-ttu-id="3d527-108">Ogni set di selezione deve avere un nome e deve specificare gli oggetti .NET del set.</span><span class="sxs-lookup"><span data-stu-id="3d527-108">Each selection set must have a name, and it must specify the .NET objects of the set.</span></span>

### <a name="attributes"></a><span data-ttu-id="3d527-109">Attributi</span><span class="sxs-lookup"><span data-stu-id="3d527-109">Attributes</span></span>

<span data-ttu-id="3d527-110">Nessuna.</span><span class="sxs-lookup"><span data-stu-id="3d527-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="3d527-111">Elementi figlio</span><span class="sxs-lookup"><span data-stu-id="3d527-111">Child Elements</span></span>

|<span data-ttu-id="3d527-112">Elemento</span><span class="sxs-lookup"><span data-stu-id="3d527-112">Element</span></span>|<span data-ttu-id="3d527-113">Description</span><span class="sxs-lookup"><span data-stu-id="3d527-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="3d527-114">Elemento Name per SelectionSet (Format)</span><span class="sxs-lookup"><span data-stu-id="3d527-114">Name Element for SelectionSet (Format)</span></span>](./name-element-for-selectionset-format.md)|<span data-ttu-id="3d527-115">Elemento obbligatorio.</span><span class="sxs-lookup"><span data-stu-id="3d527-115">Required element.</span></span><br /><br /> <span data-ttu-id="3d527-116">Specifica il nome utilizzato per fare riferimento al set di selezione.</span><span class="sxs-lookup"><span data-stu-id="3d527-116">Specifies the name used to reference the selection set.</span></span>|
|[<span data-ttu-id="3d527-117">Elemento types (Format)</span><span class="sxs-lookup"><span data-stu-id="3d527-117">Types Element (Format)</span></span>](./types-element-for-selectionset-format.md)|<span data-ttu-id="3d527-118">Elemento obbligatorio.</span><span class="sxs-lookup"><span data-stu-id="3d527-118">Required element.</span></span><br /><br /> <span data-ttu-id="3d527-119">Definisce gli oggetti .NET presenti nel set di selezione.</span><span class="sxs-lookup"><span data-stu-id="3d527-119">Defines the .NET objects that are in the selection set.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="3d527-120">Elementi padre</span><span class="sxs-lookup"><span data-stu-id="3d527-120">Parent Elements</span></span>

|<span data-ttu-id="3d527-121">Elemento</span><span class="sxs-lookup"><span data-stu-id="3d527-121">Element</span></span>|<span data-ttu-id="3d527-122">Description</span><span class="sxs-lookup"><span data-stu-id="3d527-122">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="3d527-123">Formato elemento SelectionSets</span><span class="sxs-lookup"><span data-stu-id="3d527-123">SelectionSets Element Format</span></span>](./selectionsets-element-format.md)|<span data-ttu-id="3d527-124">Definisce i set comuni di oggetti .NET che possono essere utilizzati da tutte le visualizzazioni del file di formattazione.</span><span class="sxs-lookup"><span data-stu-id="3d527-124">Defines the common sets of .NET objects that can be used by all views of the formatting file.</span></span>|

## <a name="remarks"></a><span data-ttu-id="3d527-125">Osservazioni</span><span class="sxs-lookup"><span data-stu-id="3d527-125">Remarks</span></span>

<span data-ttu-id="3d527-126">È possibile utilizzare i set di selezione quando si dispone di un set di oggetti correlati a cui si desidera fare riferimento utilizzando un solo nome, ad esempio un set di oggetti correlati tramite ereditarietà.</span><span class="sxs-lookup"><span data-stu-id="3d527-126">You can use selection sets when you have a set of related objects that you want to reference by using a single name, such as a set of objects that are related through inheritance.</span></span> <span data-ttu-id="3d527-127">Quando si definiscono le visualizzazioni, è possibile specificare il set di oggetti utilizzando il nome del set di selezione anziché elencare tutti gli oggetti all'interno di ogni visualizzazione.</span><span class="sxs-lookup"><span data-stu-id="3d527-127">When defining your views, you can specify the set of objects by using the name of the selection set instead of listing all the objects within each view.</span></span>

<span data-ttu-id="3d527-128">I set di selezione comuni vengono specificati in base al relativo nome quando si definiscono le visualizzazioni del file di formattazione o le definizioni delle viste.</span><span class="sxs-lookup"><span data-stu-id="3d527-128">Common selection sets are specified by their name when defining the views of the formatting file or the definitions of the views.</span></span> <span data-ttu-id="3d527-129">In questi casi, l'elemento figlio `SelectionSetName` degli elementi `ViewSelectedBy` e `EntrySelectedBy` specifica il set da usare.</span><span class="sxs-lookup"><span data-stu-id="3d527-129">In these cases, the `SelectionSetName` child element of the `ViewSelectedBy` and `EntrySelectedBy` elements specifies the set to be used.</span></span> <span data-ttu-id="3d527-130">Per ulteriori informazioni sui set di selezione, vedere [definizione di set di oggetti](./defining-selection-sets.md).</span><span class="sxs-lookup"><span data-stu-id="3d527-130">For more information about selection sets, see [Defining Sets of Objects](./defining-selection-sets.md).</span></span>

## <a name="example"></a><span data-ttu-id="3d527-131">Esempio</span><span class="sxs-lookup"><span data-stu-id="3d527-131">Example</span></span>

<span data-ttu-id="3d527-132">Nell'esempio seguente viene illustrato un elemento `SelectionSet` che definisce quattro tipi .NET.</span><span class="sxs-lookup"><span data-stu-id="3d527-132">The following example shows a `SelectionSet` element that defines four .NET types.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="3d527-133">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="3d527-133">See Also</span></span>

[<span data-ttu-id="3d527-134">Definizione di set di selezione</span><span class="sxs-lookup"><span data-stu-id="3d527-134">Defining Selection Sets</span></span>](./defining-selection-sets.md)

[<span data-ttu-id="3d527-135">Elemento Name di SelectionSet (Format)</span><span class="sxs-lookup"><span data-stu-id="3d527-135">Name Element of SelectionSet (Format)</span></span>](./name-element-for-selectionset-format.md)

[<span data-ttu-id="3d527-136">Elemento SelectionSets (Format)</span><span class="sxs-lookup"><span data-stu-id="3d527-136">SelectionSets Element (Format)</span></span>](./selectionsets-element-format.md)

[<span data-ttu-id="3d527-137">Elemento types (Format)</span><span class="sxs-lookup"><span data-stu-id="3d527-137">Types Element (Format)</span></span>](./types-element-for-selectionset-format.md)

[<span data-ttu-id="3d527-138">Scrittura di un file di formattazione di PowerShell</span><span class="sxs-lookup"><span data-stu-id="3d527-138">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
