---
title: Elemento SelectionSet (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 848e7acd-d578-4fd1-a575-c0c3b9b5e68a
caps.latest.revision: 17
ms.openlocfilehash: c809aa6c3a40d16cfd2fd99065a846d265ec0f61
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62076311"
---
# <a name="selectionset-element-format"></a><span data-ttu-id="3c0f4-102">Elemento SelectionSet (formato)</span><span class="sxs-lookup"><span data-stu-id="3c0f4-102">SelectionSet Element (Format)</span></span>

<span data-ttu-id="3c0f4-103">Definisce un set di oggetti .NET che possono fare riferimento il nome del set.</span><span class="sxs-lookup"><span data-stu-id="3c0f4-103">Defines a set of .NET objects that can be referenced by the name of the set.</span></span>

<span data-ttu-id="3c0f4-104">Configurazione (formato) elemento SelectionSets (formato) SelectionSet elemento (formato)</span><span class="sxs-lookup"><span data-stu-id="3c0f4-104">Configuration Element (Format) SelectionSets Element (Format) SelectionSet Element (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="3c0f4-105">Sintassi</span><span class="sxs-lookup"><span data-stu-id="3c0f4-105">Syntax</span></span>

```xml
<SelectionSet>
  <Name>SelectionSetName</Name>
  <Types>...</Types>
</SelectionSet>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="3c0f4-106">Elementi e attributi</span><span class="sxs-lookup"><span data-stu-id="3c0f4-106">Attributes and Elements</span></span>

<span data-ttu-id="3c0f4-107">Le sezioni seguenti descrivono gli attributi e gli elementi figlio dell'elemento padre del `SelectionSet` elemento.</span><span class="sxs-lookup"><span data-stu-id="3c0f4-107">The following sections describe the attributes, child elements, and the parent element of the `SelectionSet` element.</span></span> <span data-ttu-id="3c0f4-108">Ogni set di selezione deve avere un nome e deve specificare gli oggetti .NET del set.</span><span class="sxs-lookup"><span data-stu-id="3c0f4-108">Each selection set must have a name, and it must specify the .NET objects of the set.</span></span>

### <a name="attributes"></a><span data-ttu-id="3c0f4-109">Attributes</span><span class="sxs-lookup"><span data-stu-id="3c0f4-109">Attributes</span></span>

<span data-ttu-id="3c0f4-110">Nessuna.</span><span class="sxs-lookup"><span data-stu-id="3c0f4-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="3c0f4-111">Elementi figlio</span><span class="sxs-lookup"><span data-stu-id="3c0f4-111">Child Elements</span></span>

|<span data-ttu-id="3c0f4-112">Elemento</span><span class="sxs-lookup"><span data-stu-id="3c0f4-112">Element</span></span>|<span data-ttu-id="3c0f4-113">Description</span><span class="sxs-lookup"><span data-stu-id="3c0f4-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="3c0f4-114">Elemento Name per SelectionSet (formato)</span><span class="sxs-lookup"><span data-stu-id="3c0f4-114">Name Element for SelectionSet (Format)</span></span>](./name-element-for-selectionset-format.md)|<span data-ttu-id="3c0f4-115">Elemento obbligatorio.</span><span class="sxs-lookup"><span data-stu-id="3c0f4-115">Required element.</span></span><br /><br /> <span data-ttu-id="3c0f4-116">Specifica il nome utilizzato per fare riferimento il set di selezione.</span><span class="sxs-lookup"><span data-stu-id="3c0f4-116">Specifies the name used to reference the selection set.</span></span>|
|[<span data-ttu-id="3c0f4-117">Elemento di Types (formato)</span><span class="sxs-lookup"><span data-stu-id="3c0f4-117">Types Element (Format)</span></span>](./types-element-for-selectionset-format.md)|<span data-ttu-id="3c0f4-118">Elemento obbligatorio.</span><span class="sxs-lookup"><span data-stu-id="3c0f4-118">Required element.</span></span><br /><br /> <span data-ttu-id="3c0f4-119">Definisce gli oggetti .NET nella selezione impostate.</span><span class="sxs-lookup"><span data-stu-id="3c0f4-119">Defines the .NET objects that are in the selection set.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="3c0f4-120">Elementi padre</span><span class="sxs-lookup"><span data-stu-id="3c0f4-120">Parent Elements</span></span>

|<span data-ttu-id="3c0f4-121">Elemento</span><span class="sxs-lookup"><span data-stu-id="3c0f4-121">Element</span></span>|<span data-ttu-id="3c0f4-122">Description</span><span class="sxs-lookup"><span data-stu-id="3c0f4-122">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="3c0f4-123">Formato elemento SelectionSets</span><span class="sxs-lookup"><span data-stu-id="3c0f4-123">SelectionSets Element Format</span></span>](./selectionsets-element-format.md)|<span data-ttu-id="3c0f4-124">Definisce il set di oggetti .NET che possono essere usati da tutte le visualizzazioni del file di formattazione comuni.</span><span class="sxs-lookup"><span data-stu-id="3c0f4-124">Defines the common sets of .NET objects that can be used by all views of the formatting file.</span></span>|

## <a name="remarks"></a><span data-ttu-id="3c0f4-125">Osservazioni</span><span class="sxs-lookup"><span data-stu-id="3c0f4-125">Remarks</span></span>

<span data-ttu-id="3c0f4-126">Quando si dispone di un set di oggetti correlati che si desidera fare riferimento tramite un solo nome, ad esempio un set di oggetti che sono correlati tramite l'ereditarietà, è possibile usare set di selezione.</span><span class="sxs-lookup"><span data-stu-id="3c0f4-126">You can use selection sets when you have a set of related objects that you want to reference by using a single name, such as a set of objects that are related through inheritance.</span></span> <span data-ttu-id="3c0f4-127">Quando si definiscono le visualizzazioni, è possibile specificare il set di oggetti utilizzando il nome della selezione set anziché elencare tutti gli oggetti all'interno di ogni visualizzazione.</span><span class="sxs-lookup"><span data-stu-id="3c0f4-127">When defining your views, you can specify the set of objects by using the name of the selection set instead of listing all the objects within each view.</span></span>

<span data-ttu-id="3c0f4-128">Set di selezione comune vengono specificati in base al nome quando si definisce le viste del file di formattazione e le definizioni delle viste.</span><span class="sxs-lookup"><span data-stu-id="3c0f4-128">Common selection sets are specified by their name when defining the views of the formatting file or the definitions of the views.</span></span> <span data-ttu-id="3c0f4-129">In questi casi, il `SelectionSetName` elemento figlio dell'elemento di `ViewSelectedBy` e `EntrySelectedBy` elementi specifica il set da utilizzare.</span><span class="sxs-lookup"><span data-stu-id="3c0f4-129">In these cases, the `SelectionSetName` child element of the `ViewSelectedBy` and `EntrySelectedBy` elements specifies the set to be used.</span></span> <span data-ttu-id="3c0f4-130">Per altre informazioni sui set di selezione, vedere [definizione imposta di oggetti](./defining-selection-sets.md).</span><span class="sxs-lookup"><span data-stu-id="3c0f4-130">For more information about selection sets, see [Defining Sets of Objects](./defining-selection-sets.md).</span></span>

## <a name="example"></a><span data-ttu-id="3c0f4-131">Esempio</span><span class="sxs-lookup"><span data-stu-id="3c0f4-131">Example</span></span>

<span data-ttu-id="3c0f4-132">L'esempio seguente mostra un `SelectionSet` elemento che definisce i quattro tipi di .NET.</span><span class="sxs-lookup"><span data-stu-id="3c0f4-132">The following example shows a `SelectionSet` element that defines four .NET types.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="3c0f4-133">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="3c0f4-133">See Also</span></span>

[<span data-ttu-id="3c0f4-134">La definizione di set di selezione</span><span class="sxs-lookup"><span data-stu-id="3c0f4-134">Defining Selection Sets</span></span>](./defining-selection-sets.md)

[<span data-ttu-id="3c0f4-135">Elemento Name di SelectionSet (formato)</span><span class="sxs-lookup"><span data-stu-id="3c0f4-135">Name Element of SelectionSet (Format)</span></span>](./name-element-for-selectionset-format.md)

[<span data-ttu-id="3c0f4-136">Elemento SelectionSets (formato)</span><span class="sxs-lookup"><span data-stu-id="3c0f4-136">SelectionSets Element (Format)</span></span>](./selectionsets-element-format.md)

[<span data-ttu-id="3c0f4-137">Elemento di Types (formato)</span><span class="sxs-lookup"><span data-stu-id="3c0f4-137">Types Element (Format)</span></span>](./types-element-for-selectionset-format.md)

[<span data-ttu-id="3c0f4-138">La scrittura di un File di formattazione di PowerShell</span><span class="sxs-lookup"><span data-stu-id="3c0f4-138">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
