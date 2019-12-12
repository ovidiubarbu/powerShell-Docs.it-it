---
title: Elemento TypeName per types (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 0595b99e-b438-4240-b47b-555cf0316f33
caps.latest.revision: 15
ms.openlocfilehash: bd5baa03c2050b2c3bbe1d7697c253d923175d39
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/05/2019
ms.locfileid: "72368030"
---
# <a name="typename-element-for-types-format"></a><span data-ttu-id="2caa7-102">Elemento TypeName per Types (formato)</span><span class="sxs-lookup"><span data-stu-id="2caa7-102">TypeName Element for Types (Format)</span></span>

<span data-ttu-id="2caa7-103">Specifica il tipo .NET di un oggetto che appartiene al set di selezione.</span><span class="sxs-lookup"><span data-stu-id="2caa7-103">Specifies the .NET type of an object that belongs to the selection set.</span></span>

<span data-ttu-id="2caa7-104">Elemento Configuration (Format) elemento SelectionSets (Format) elemento SelectionSet (Format) elemento types (Format) elemento TypeName di tipi (Format)</span><span class="sxs-lookup"><span data-stu-id="2caa7-104">Configuration Element (Format) SelectionSets Element (Format) SelectionSet Element (Format) Types Element (Format) TypeName Element of Types (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="2caa7-105">Sintassi</span><span class="sxs-lookup"><span data-stu-id="2caa7-105">Syntax</span></span>

```xml
<TypeName>Nameof.NetType</Name>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="2caa7-106">Attributi ed elementi</span><span class="sxs-lookup"><span data-stu-id="2caa7-106">Attributes and Elements</span></span>

<span data-ttu-id="2caa7-107">Nelle sezioni seguenti vengono descritti gli attributi, gli elementi figlio e l'elemento padre dell'elemento `TypeName`.</span><span class="sxs-lookup"><span data-stu-id="2caa7-107">The following sections describe the attributes, child elements, and the parent element of the `TypeName` element.</span></span> <span data-ttu-id="2caa7-108">Nel set di selezione deve essere incluso almeno un elemento `TypeName`.</span><span class="sxs-lookup"><span data-stu-id="2caa7-108">At least one `TypeName` element must be included in the selection set.</span></span>

### <a name="attributes"></a><span data-ttu-id="2caa7-109">Attributi</span><span class="sxs-lookup"><span data-stu-id="2caa7-109">Attributes</span></span>

<span data-ttu-id="2caa7-110">Nessuna.</span><span class="sxs-lookup"><span data-stu-id="2caa7-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="2caa7-111">Elementi figlio</span><span class="sxs-lookup"><span data-stu-id="2caa7-111">Child Elements</span></span>

<span data-ttu-id="2caa7-112">Nessuna.</span><span class="sxs-lookup"><span data-stu-id="2caa7-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="2caa7-113">Elementi padre</span><span class="sxs-lookup"><span data-stu-id="2caa7-113">Parent Elements</span></span>

|<span data-ttu-id="2caa7-114">Elemento</span><span class="sxs-lookup"><span data-stu-id="2caa7-114">Element</span></span>|<span data-ttu-id="2caa7-115">Description</span><span class="sxs-lookup"><span data-stu-id="2caa7-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="2caa7-116">Elemento types (Format)</span><span class="sxs-lookup"><span data-stu-id="2caa7-116">Types Element (Format)</span></span>](./types-element-for-selectionset-format.md)|<span data-ttu-id="2caa7-117">Definisce gli oggetti .NET presenti nel set di selezione.</span><span class="sxs-lookup"><span data-stu-id="2caa7-117">Defines the .NET objects that are in the selection set.</span></span>|

## <a name="text-value"></a><span data-ttu-id="2caa7-118">Valore testo</span><span class="sxs-lookup"><span data-stu-id="2caa7-118">Text Value</span></span>

<span data-ttu-id="2caa7-119">Specificare il nome completo per il tipo .NET.</span><span class="sxs-lookup"><span data-stu-id="2caa7-119">Specify the fully qualified name for the .NET type.</span></span>

## <a name="remarks"></a><span data-ttu-id="2caa7-120">Osservazioni</span><span class="sxs-lookup"><span data-stu-id="2caa7-120">Remarks</span></span>

<span data-ttu-id="2caa7-121">È possibile utilizzare i set di selezione quando si dispone di un set di oggetti correlati a cui si desidera fare riferimento utilizzando un solo nome, ad esempio un set di oggetti correlati tramite ereditarietà.</span><span class="sxs-lookup"><span data-stu-id="2caa7-121">You can use selection sets when you have a set of related objects that you want to reference by using a single name, such as a set of objects that are related through inheritance.</span></span> <span data-ttu-id="2caa7-122">Quando si definiscono le visualizzazioni, è possibile specificare il set di oggetti utilizzando il nome del set di selezione anziché elencare tutti gli oggetti all'interno di ogni visualizzazione.</span><span class="sxs-lookup"><span data-stu-id="2caa7-122">When defining your views, you can specify the set of objects by using the name of the selection set instead of listing all the objects within each view.</span></span>

<span data-ttu-id="2caa7-123">I set di selezione comuni vengono specificati in base al relativo nome quando si definiscono le visualizzazioni del file di formattazione.</span><span class="sxs-lookup"><span data-stu-id="2caa7-123">Common selection sets are specified by their name when defining the views of the formatting file.</span></span> <span data-ttu-id="2caa7-124">In questi casi, il `SelectionSetName` elemento figlio dell'elemento `ViewSelectedBy` per la vista specifica il set.</span><span class="sxs-lookup"><span data-stu-id="2caa7-124">In these cases, the `SelectionSetName` child element of the `ViewSelectedBy` element for the view specifies the set.</span></span> <span data-ttu-id="2caa7-125">Tuttavia, voci diverse di una vista possono anche specificare un set di selezione che si applica solo a tale voce della visualizzazione.</span><span class="sxs-lookup"><span data-stu-id="2caa7-125">However, different entries of a view can also specify a selection set that applies to only that entry of the view.</span></span> <span data-ttu-id="2caa7-126">Per ulteriori informazioni sui set di selezione, vedere [definizione di set di oggetti](./defining-selection-sets.md).</span><span class="sxs-lookup"><span data-stu-id="2caa7-126">For more information about selection sets, see [Defining Sets of Objects](./defining-selection-sets.md).</span></span>

## <a name="example"></a><span data-ttu-id="2caa7-127">Esempio</span><span class="sxs-lookup"><span data-stu-id="2caa7-127">Example</span></span>

<span data-ttu-id="2caa7-128">Nell'esempio seguente viene illustrato un elemento `SelectionSet` che definisce quattro tipi .NET.</span><span class="sxs-lookup"><span data-stu-id="2caa7-128">The following example shows a `SelectionSet` element that defines four .NET types.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="2caa7-129">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="2caa7-129">See Also</span></span>

[<span data-ttu-id="2caa7-130">Definizione di set di selezione</span><span class="sxs-lookup"><span data-stu-id="2caa7-130">Defining Selection Sets</span></span>](./defining-selection-sets.md)

[<span data-ttu-id="2caa7-131">Elemento SelectionSet (Format)</span><span class="sxs-lookup"><span data-stu-id="2caa7-131">SelectionSet Element (Format)</span></span>](./selectionset-element-format.md)

[<span data-ttu-id="2caa7-132">Elemento SelectionSets (Format)</span><span class="sxs-lookup"><span data-stu-id="2caa7-132">SelectionSets Element (Format)</span></span>](./selectionsets-element-format.md)

[<span data-ttu-id="2caa7-133">Elemento types (Format)</span><span class="sxs-lookup"><span data-stu-id="2caa7-133">Types Element (Format)</span></span>](./types-element-for-selectionset-format.md)

[<span data-ttu-id="2caa7-134">Scrittura di un file di formattazione di Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="2caa7-134">Writing a Windows PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
