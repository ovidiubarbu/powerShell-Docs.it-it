---
title: Elemento Name per SelectionSet (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 914917f7-0efc-4d1f-88bd-de714bedd98f
caps.latest.revision: 15
ms.openlocfilehash: 29dbdbd335511e4ca2706a625541554825838f23
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/15/2019
ms.locfileid: "72362670"
---
# <a name="name-element-for-selectionset-format"></a><span data-ttu-id="54b38-102">Elemento Name per SelectionSet (formato)</span><span class="sxs-lookup"><span data-stu-id="54b38-102">Name Element for SelectionSet (Format)</span></span>

<span data-ttu-id="54b38-103">Specifica il nome utilizzato per fare riferimento al set di selezione.</span><span class="sxs-lookup"><span data-stu-id="54b38-103">Specifies the name used to reference the selection set.</span></span>

<span data-ttu-id="54b38-104">Elemento Configuration (Format) elemento SelectionSets (Format) elemento SelectionSet (Format) elemento Name di SelectionSet (Format)</span><span class="sxs-lookup"><span data-stu-id="54b38-104">Configuration Element (Format) SelectionSets Element (Format) SelectionSet Element (Format) Name Element of SelectionSet (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="54b38-105">Sintassi</span><span class="sxs-lookup"><span data-stu-id="54b38-105">Syntax</span></span>

```xml
<Name>Name of selection set</Name>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="54b38-106">Attributi ed elementi</span><span class="sxs-lookup"><span data-stu-id="54b38-106">Attributes and Elements</span></span>

<span data-ttu-id="54b38-107">Nelle sezioni seguenti vengono descritti gli attributi, gli elementi figlio e l'elemento padre dell'elemento `Name`.</span><span class="sxs-lookup"><span data-stu-id="54b38-107">The following sections describe the attributes, child elements, and parent element of the `Name` Element.</span></span>

### <a name="attributes"></a><span data-ttu-id="54b38-108">Attributi</span><span class="sxs-lookup"><span data-stu-id="54b38-108">Attributes</span></span>

<span data-ttu-id="54b38-109">Nessuna.</span><span class="sxs-lookup"><span data-stu-id="54b38-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="54b38-110">Elementi figlio</span><span class="sxs-lookup"><span data-stu-id="54b38-110">Child Elements</span></span>

<span data-ttu-id="54b38-111">Nessuna.</span><span class="sxs-lookup"><span data-stu-id="54b38-111">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="54b38-112">Elementi padre</span><span class="sxs-lookup"><span data-stu-id="54b38-112">Parent Elements</span></span>

|<span data-ttu-id="54b38-113">Elemento</span><span class="sxs-lookup"><span data-stu-id="54b38-113">Element</span></span>|<span data-ttu-id="54b38-114">Description</span><span class="sxs-lookup"><span data-stu-id="54b38-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="54b38-115">Elemento SelectionSet (Format)</span><span class="sxs-lookup"><span data-stu-id="54b38-115">SelectionSet Element (Format)</span></span>](./selectionset-element-format.md)|<span data-ttu-id="54b38-116">Definisce un singolo set di oggetti .NET a cui è possibile fare riferimento dal nome del set.</span><span class="sxs-lookup"><span data-stu-id="54b38-116">Defines a single set of .NET objects that can be referenced by the name of the set.</span></span>|

## <a name="text-value"></a><span data-ttu-id="54b38-117">Valore di testo</span><span class="sxs-lookup"><span data-stu-id="54b38-117">Text Value</span></span>

<span data-ttu-id="54b38-118">Specificare il nome per fare riferimento al set di selezione.</span><span class="sxs-lookup"><span data-stu-id="54b38-118">Specify the name to reference the selection set.</span></span> <span data-ttu-id="54b38-119">Non esistono restrizioni per quanto riguarda i caratteri che possono essere usati.</span><span class="sxs-lookup"><span data-stu-id="54b38-119">There are no restrictions as to what characters can be used.</span></span>

## <a name="remarks"></a><span data-ttu-id="54b38-120">Osservazioni</span><span class="sxs-lookup"><span data-stu-id="54b38-120">Remarks</span></span>

<span data-ttu-id="54b38-121">Il nome specificato qui viene usato nell'elemento `SelectionSetName`.</span><span class="sxs-lookup"><span data-stu-id="54b38-121">The name specified here is used in the `SelectionSetName` element.</span></span> <span data-ttu-id="54b38-122">Set di selezione che può essere utilizzato da una vista, da una definizione di una vista (le visualizzazioni possono avere più definizioni) o quando si specifica una condizione di selezione.</span><span class="sxs-lookup"><span data-stu-id="54b38-122">The selection set that can be used by a view, by a definition of a view (views can have multiple definitions), or when specifying a selection condition.</span></span> <span data-ttu-id="54b38-123">Per ulteriori informazioni sui set di selezione, vedere [definizione di set di oggetti](./defining-selection-sets.md).</span><span class="sxs-lookup"><span data-stu-id="54b38-123">For more information about selection sets, see [Defining Sets of Objects](./defining-selection-sets.md).</span></span>

## <a name="example"></a><span data-ttu-id="54b38-124">Esempio</span><span class="sxs-lookup"><span data-stu-id="54b38-124">Example</span></span>

<span data-ttu-id="54b38-125">Questo esempio mostra un elemento `SelectionSet` che definisce quattro tipi .NET.</span><span class="sxs-lookup"><span data-stu-id="54b38-125">This example shows a `SelectionSet` element that defines four .NET types.</span></span> <span data-ttu-id="54b38-126">Il nome del set di selezione è "FileSystemTypes".</span><span class="sxs-lookup"><span data-stu-id="54b38-126">The name of the selection set is "FileSystemTypes".</span></span>

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

## <a name="see-also"></a><span data-ttu-id="54b38-127">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="54b38-127">See Also</span></span>

[<span data-ttu-id="54b38-128">Definizione di set di selezione</span><span class="sxs-lookup"><span data-stu-id="54b38-128">Defining Selection Sets</span></span>](./defining-selection-sets.md)

[<span data-ttu-id="54b38-129">Elemento SelectionSet (Format)</span><span class="sxs-lookup"><span data-stu-id="54b38-129">SelectionSet Element (Format)</span></span>](./selectionset-element-format.md)

[<span data-ttu-id="54b38-130">Scrittura di un file di formattazione di PowerShell</span><span class="sxs-lookup"><span data-stu-id="54b38-130">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
