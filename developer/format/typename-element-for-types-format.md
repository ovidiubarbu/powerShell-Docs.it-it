---
title: TypeName (elemento) per tipi (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 0595b99e-b438-4240-b47b-555cf0316f33
caps.latest.revision: 15
ms.openlocfilehash: bd5baa03c2050b2c3bbe1d7697c253d923175d39
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/16/2019
ms.locfileid: "58057927"
---
# <a name="typename-element-for-types-format"></a><span data-ttu-id="c33ae-102">Elemento TypeName per Types (formato)</span><span class="sxs-lookup"><span data-stu-id="c33ae-102">TypeName Element for Types (Format)</span></span>

<span data-ttu-id="c33ae-103">Specifica il tipo .NET dell'oggetto che appartiene al set di selezione.</span><span class="sxs-lookup"><span data-stu-id="c33ae-103">Specifies the .NET type of an object that belongs to the selection set.</span></span>

<span data-ttu-id="c33ae-104">Configurazione (formato) elemento SelectionSets (formato) SelectionSet elemento (formato) i tipi di elemento (formato) elemento TypeName di tipi (formato)</span><span class="sxs-lookup"><span data-stu-id="c33ae-104">Configuration Element (Format) SelectionSets Element (Format) SelectionSet Element (Format) Types Element (Format) TypeName Element of Types (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="c33ae-105">Sintassi</span><span class="sxs-lookup"><span data-stu-id="c33ae-105">Syntax</span></span>

```xml
<TypeName>Nameof.NetType</Name>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="c33ae-106">Attributi ed elementi</span><span class="sxs-lookup"><span data-stu-id="c33ae-106">Attributes and Elements</span></span>

<span data-ttu-id="c33ae-107">Le sezioni seguenti descrivono gli attributi e gli elementi figlio dell'elemento padre del `TypeName` elemento.</span><span class="sxs-lookup"><span data-stu-id="c33ae-107">The following sections describe the attributes, child elements, and the parent element of the `TypeName` element.</span></span> <span data-ttu-id="c33ae-108">Almeno un `TypeName` elemento deve essere incluso nel set di selezione.</span><span class="sxs-lookup"><span data-stu-id="c33ae-108">At least one `TypeName` element must be included in the selection set.</span></span>

### <a name="attributes"></a><span data-ttu-id="c33ae-109">Attributes</span><span class="sxs-lookup"><span data-stu-id="c33ae-109">Attributes</span></span>

<span data-ttu-id="c33ae-110">Nessuna.</span><span class="sxs-lookup"><span data-stu-id="c33ae-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="c33ae-111">Elementi figlio</span><span class="sxs-lookup"><span data-stu-id="c33ae-111">Child Elements</span></span>

<span data-ttu-id="c33ae-112">Nessuna.</span><span class="sxs-lookup"><span data-stu-id="c33ae-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="c33ae-113">Elementi padre</span><span class="sxs-lookup"><span data-stu-id="c33ae-113">Parent Elements</span></span>

|<span data-ttu-id="c33ae-114">Elemento</span><span class="sxs-lookup"><span data-stu-id="c33ae-114">Element</span></span>|<span data-ttu-id="c33ae-115">Description</span><span class="sxs-lookup"><span data-stu-id="c33ae-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="c33ae-116">Elemento di Types (formato)</span><span class="sxs-lookup"><span data-stu-id="c33ae-116">Types Element (Format)</span></span>](./types-element-for-selectionset-format.md)|<span data-ttu-id="c33ae-117">Definisce gli oggetti .NET nella selezione impostate.</span><span class="sxs-lookup"><span data-stu-id="c33ae-117">Defines the .NET objects that are in the selection set.</span></span>|

## <a name="text-value"></a><span data-ttu-id="c33ae-118">Valore di testo</span><span class="sxs-lookup"><span data-stu-id="c33ae-118">Text Value</span></span>

<span data-ttu-id="c33ae-119">Specificare il nome completo per il tipo .NET.</span><span class="sxs-lookup"><span data-stu-id="c33ae-119">Specify the fully qualified name for the .NET type.</span></span>

## <a name="remarks"></a><span data-ttu-id="c33ae-120">Osservazioni</span><span class="sxs-lookup"><span data-stu-id="c33ae-120">Remarks</span></span>

<span data-ttu-id="c33ae-121">Quando si dispone di un set di oggetti correlati che si desidera fare riferimento tramite un solo nome, ad esempio un set di oggetti che sono correlati tramite l'ereditarietà, è possibile usare set di selezione.</span><span class="sxs-lookup"><span data-stu-id="c33ae-121">You can use selection sets when you have a set of related objects that you want to reference by using a single name, such as a set of objects that are related through inheritance.</span></span> <span data-ttu-id="c33ae-122">Quando si definiscono le visualizzazioni, è possibile specificare il set di oggetti utilizzando il nome della selezione set anziché elencare tutti gli oggetti all'interno di ogni visualizzazione.</span><span class="sxs-lookup"><span data-stu-id="c33ae-122">When defining your views, you can specify the set of objects by using the name of the selection set instead of listing all the objects within each view.</span></span>

<span data-ttu-id="c33ae-123">Set di selezione comune vengono specificati in base al nome quando si definisce le viste del file di formattazione.</span><span class="sxs-lookup"><span data-stu-id="c33ae-123">Common selection sets are specified by their name when defining the views of the formatting file.</span></span> <span data-ttu-id="c33ae-124">In questi casi, il `SelectionSetName` elemento figlio dell'elemento di `ViewSelectedBy` (elemento) per la visualizzazione specifica del set.</span><span class="sxs-lookup"><span data-stu-id="c33ae-124">In these cases, the `SelectionSetName` child element of the `ViewSelectedBy` element for the view specifies the set.</span></span> <span data-ttu-id="c33ae-125">Tuttavia, diverse voci di una vista possono anche specificare un set di selezione che viene applicata solo tale voce della visualizzazione.</span><span class="sxs-lookup"><span data-stu-id="c33ae-125">However, different entries of a view can also specify a selection set that applies to only that entry of the view.</span></span> <span data-ttu-id="c33ae-126">Per altre informazioni sui set di selezione, vedere [definizione imposta di oggetti](./defining-selection-sets.md).</span><span class="sxs-lookup"><span data-stu-id="c33ae-126">For more information about selection sets, see [Defining Sets of Objects](./defining-selection-sets.md).</span></span>

## <a name="example"></a><span data-ttu-id="c33ae-127">Esempio</span><span class="sxs-lookup"><span data-stu-id="c33ae-127">Example</span></span>

<span data-ttu-id="c33ae-128">L'esempio seguente mostra un `SelectionSet` elemento che definisce i quattro tipi di .NET.</span><span class="sxs-lookup"><span data-stu-id="c33ae-128">The following example shows a `SelectionSet` element that defines four .NET types.</span></span>

```
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

## <a name="see-also"></a><span data-ttu-id="c33ae-129">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="c33ae-129">See Also</span></span>

[<span data-ttu-id="c33ae-130">La definizione di set di selezione</span><span class="sxs-lookup"><span data-stu-id="c33ae-130">Defining Selection Sets</span></span>](./defining-selection-sets.md)

[<span data-ttu-id="c33ae-131">Elemento SelectionSet (formato)</span><span class="sxs-lookup"><span data-stu-id="c33ae-131">SelectionSet Element (Format)</span></span>](./selectionset-element-format.md)

[<span data-ttu-id="c33ae-132">Elemento SelectionSets (formato)</span><span class="sxs-lookup"><span data-stu-id="c33ae-132">SelectionSets Element (Format)</span></span>](./selectionsets-element-format.md)

[<span data-ttu-id="c33ae-133">Elemento di Types (formato)</span><span class="sxs-lookup"><span data-stu-id="c33ae-133">Types Element (Format)</span></span>](./types-element-for-selectionset-format.md)

[<span data-ttu-id="c33ae-134">La scrittura di un File di formattazione di Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="c33ae-134">Writing a Windows PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
