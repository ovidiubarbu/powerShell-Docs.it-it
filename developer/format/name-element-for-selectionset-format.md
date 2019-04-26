---
title: Nome elemento SelectionSet (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 914917f7-0efc-4d1f-88bd-de714bedd98f
caps.latest.revision: 15
ms.openlocfilehash: 29dbdbd335511e4ca2706a625541554825838f23
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62065156"
---
# <a name="name-element-for-selectionset-format"></a><span data-ttu-id="045bf-102">Elemento Name per SelectionSet (formato)</span><span class="sxs-lookup"><span data-stu-id="045bf-102">Name Element for SelectionSet (Format)</span></span>

<span data-ttu-id="045bf-103">Specifica il nome utilizzato per fare riferimento il set di selezione.</span><span class="sxs-lookup"><span data-stu-id="045bf-103">Specifies the name used to reference the selection set.</span></span>

<span data-ttu-id="045bf-104">Nome elemento di configurazione elemento (formato) elemento SelectionSets (formato) elemento SelectionSet (formato) di SelectionSet (formato)</span><span class="sxs-lookup"><span data-stu-id="045bf-104">Configuration Element (Format) SelectionSets Element (Format) SelectionSet Element (Format) Name Element of SelectionSet (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="045bf-105">Sintassi</span><span class="sxs-lookup"><span data-stu-id="045bf-105">Syntax</span></span>

```xml
<Name>Name of selection set</Name>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="045bf-106">Elementi e attributi</span><span class="sxs-lookup"><span data-stu-id="045bf-106">Attributes and Elements</span></span>

<span data-ttu-id="045bf-107">Le sezioni seguenti descrivono gli attributi, elementi figlio ed elemento padre dell'elemento di `Name` elemento.</span><span class="sxs-lookup"><span data-stu-id="045bf-107">The following sections describe the attributes, child elements, and parent element of the `Name` Element.</span></span>

### <a name="attributes"></a><span data-ttu-id="045bf-108">Attributes</span><span class="sxs-lookup"><span data-stu-id="045bf-108">Attributes</span></span>

<span data-ttu-id="045bf-109">Nessuna.</span><span class="sxs-lookup"><span data-stu-id="045bf-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="045bf-110">Elementi figlio</span><span class="sxs-lookup"><span data-stu-id="045bf-110">Child Elements</span></span>

<span data-ttu-id="045bf-111">Nessuna.</span><span class="sxs-lookup"><span data-stu-id="045bf-111">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="045bf-112">Elementi padre</span><span class="sxs-lookup"><span data-stu-id="045bf-112">Parent Elements</span></span>

|<span data-ttu-id="045bf-113">Elemento</span><span class="sxs-lookup"><span data-stu-id="045bf-113">Element</span></span>|<span data-ttu-id="045bf-114">Description</span><span class="sxs-lookup"><span data-stu-id="045bf-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="045bf-115">Elemento SelectionSet (formato)</span><span class="sxs-lookup"><span data-stu-id="045bf-115">SelectionSet Element (Format)</span></span>](./selectionset-element-format.md)|<span data-ttu-id="045bf-116">Definisce un singolo set di oggetti .NET che possono fare riferimento il nome del set.</span><span class="sxs-lookup"><span data-stu-id="045bf-116">Defines a single set of .NET objects that can be referenced by the name of the set.</span></span>|

## <a name="text-value"></a><span data-ttu-id="045bf-117">Valore di testo</span><span class="sxs-lookup"><span data-stu-id="045bf-117">Text Value</span></span>

<span data-ttu-id="045bf-118">Specificare il nome per fare riferimento a set di selezione.</span><span class="sxs-lookup"><span data-stu-id="045bf-118">Specify the name to reference the selection set.</span></span> <span data-ttu-id="045bf-119">Sono disponibili non possono essere utilizzati restrizioni per quanto riguarda i caratteri.</span><span class="sxs-lookup"><span data-stu-id="045bf-119">There are no restrictions as to what characters can be used.</span></span>

## <a name="remarks"></a><span data-ttu-id="045bf-120">Osservazioni</span><span class="sxs-lookup"><span data-stu-id="045bf-120">Remarks</span></span>

<span data-ttu-id="045bf-121">Il nome specificato in questo campo viene usato nel `SelectionSetName` elemento.</span><span class="sxs-lookup"><span data-stu-id="045bf-121">The name specified here is used in the `SelectionSetName` element.</span></span> <span data-ttu-id="045bf-122">Il set di selezione che può essere utilizzato da una visualizzazione, da una definizione di una vista (visualizzazioni possono avere più definizioni,) o quando si specifica una condizione di selezione.</span><span class="sxs-lookup"><span data-stu-id="045bf-122">The selection set that can be used by a view, by a definition of a view (views can have multiple definitions), or when specifying a selection condition.</span></span> <span data-ttu-id="045bf-123">Per altre informazioni sui set di selezione, vedere [definizione imposta di oggetti](./defining-selection-sets.md).</span><span class="sxs-lookup"><span data-stu-id="045bf-123">For more information about selection sets, see [Defining Sets of Objects](./defining-selection-sets.md).</span></span>

## <a name="example"></a><span data-ttu-id="045bf-124">Esempio</span><span class="sxs-lookup"><span data-stu-id="045bf-124">Example</span></span>

<span data-ttu-id="045bf-125">Questo esempio viene illustrato un `SelectionSet` elemento che definisce i quattro tipi di .NET.</span><span class="sxs-lookup"><span data-stu-id="045bf-125">This example shows a `SelectionSet` element that defines four .NET types.</span></span> <span data-ttu-id="045bf-126">Il nome del set di selezione è "FileSystemTypes".</span><span class="sxs-lookup"><span data-stu-id="045bf-126">The name of the selection set is "FileSystemTypes".</span></span>

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

## <a name="see-also"></a><span data-ttu-id="045bf-127">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="045bf-127">See Also</span></span>

[<span data-ttu-id="045bf-128">La definizione di set di selezione</span><span class="sxs-lookup"><span data-stu-id="045bf-128">Defining Selection Sets</span></span>](./defining-selection-sets.md)

[<span data-ttu-id="045bf-129">Elemento SelectionSet (formato)</span><span class="sxs-lookup"><span data-stu-id="045bf-129">SelectionSet Element (Format)</span></span>](./selectionset-element-format.md)

[<span data-ttu-id="045bf-130">La scrittura di un File di formattazione di PowerShell</span><span class="sxs-lookup"><span data-stu-id="045bf-130">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
