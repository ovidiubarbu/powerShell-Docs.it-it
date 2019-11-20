---
title: Elemento EnumerableExpansion (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 93d27173-9ae4-46e5-bb78-90525915cd70
caps.latest.revision: 9
ms.openlocfilehash: bc1e58c00ca8419f9204076f0a46050281e704db
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/15/2019
ms.locfileid: "72368750"
---
# <a name="enumerableexpansion-element-format"></a><span data-ttu-id="b936f-102">Elemento EnumerableExpansion (formato)</span><span class="sxs-lookup"><span data-stu-id="b936f-102">EnumerableExpansion Element (Format)</span></span>

<span data-ttu-id="b936f-103">Definisce la modalità di espansione degli oggetti raccolta .NET specifici quando vengono visualizzati in una visualizzazione.</span><span class="sxs-lookup"><span data-stu-id="b936f-103">Defines how specific .NET collection objects are expanded when they are displayed in a view.</span></span>

<span data-ttu-id="b936f-104">Elemento Configuration (Format) elemento DefaultSettings (Format) elemento EnumerableExpansions (Format) elemento EnumerableExpansion (Format)</span><span class="sxs-lookup"><span data-stu-id="b936f-104">Configuration Element (Format) DefaultSettings Element (Format) EnumerableExpansions Element (Format) EnumerableExpansion Element (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="b936f-105">Sintassi</span><span class="sxs-lookup"><span data-stu-id="b936f-105">Syntax</span></span>

```xml
<EnumerableExpansion>
  <EntrySelectedBy>...</EntrySelectedBy>
  <Expand>EnumOnly, CoreOnly, Both</Expand>
</EnumerableExpansion>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="b936f-106">Attributi ed elementi</span><span class="sxs-lookup"><span data-stu-id="b936f-106">Attributes and Elements</span></span>

<span data-ttu-id="b936f-107">Nelle sezioni seguenti vengono descritti gli attributi, gli elementi figlio e l'elemento padre dell'elemento `EnumerableExpansion`.</span><span class="sxs-lookup"><span data-stu-id="b936f-107">The following sections describe attributes, child elements, and the parent element of the `EnumerableExpansion` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="b936f-108">Attributi</span><span class="sxs-lookup"><span data-stu-id="b936f-108">Attributes</span></span>

<span data-ttu-id="b936f-109">Nessuna.</span><span class="sxs-lookup"><span data-stu-id="b936f-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="b936f-110">Elementi figlio</span><span class="sxs-lookup"><span data-stu-id="b936f-110">Child Elements</span></span>

|<span data-ttu-id="b936f-111">Elemento</span><span class="sxs-lookup"><span data-stu-id="b936f-111">Element</span></span>|<span data-ttu-id="b936f-112">Description</span><span class="sxs-lookup"><span data-stu-id="b936f-112">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="b936f-113">Elemento EntrySelectedBy per EnumerableExpansion (Format)</span><span class="sxs-lookup"><span data-stu-id="b936f-113">EntrySelectedBy Element for EnumerableExpansion (Format)</span></span>](./entryselectedby-element-for-enumerableexpansion-format.md)|<span data-ttu-id="b936f-114">Elemento facoltativo.</span><span class="sxs-lookup"><span data-stu-id="b936f-114">Optional element.</span></span><br /><br /> <span data-ttu-id="b936f-115">Definisce gli oggetti della raccolta .NET espansi da questa definizione.</span><span class="sxs-lookup"><span data-stu-id="b936f-115">Defines which .NET collection objects are expanded by this definition.</span></span>|
|[<span data-ttu-id="b936f-116">Elemento Expand (Format)</span><span class="sxs-lookup"><span data-stu-id="b936f-116">Expand Element (Format)</span></span>](./expand-element-format.md)|<span data-ttu-id="b936f-117">Specifica la modalità di espansione dell'oggetto raccolta per questa definizione.</span><span class="sxs-lookup"><span data-stu-id="b936f-117">Specifies how the collection object is expanded for this definition.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="b936f-118">Elementi padre</span><span class="sxs-lookup"><span data-stu-id="b936f-118">Parent Elements</span></span>

|<span data-ttu-id="b936f-119">Elemento</span><span class="sxs-lookup"><span data-stu-id="b936f-119">Element</span></span>|<span data-ttu-id="b936f-120">Description</span><span class="sxs-lookup"><span data-stu-id="b936f-120">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="b936f-121">Elemento EnumerableExpansions (Format)</span><span class="sxs-lookup"><span data-stu-id="b936f-121">EnumerableExpansions Element (Format)</span></span>](./enumerableexpansions-element-format.md)|<span data-ttu-id="b936f-122">Definisce le diverse modalità di espansione degli oggetti raccolta .NET quando vengono visualizzati in una visualizzazione.</span><span class="sxs-lookup"><span data-stu-id="b936f-122">Defines the different ways that .NET collection objects are expanded when they are displayed in a view.</span></span>|

## <a name="remarks"></a><span data-ttu-id="b936f-123">Osservazioni</span><span class="sxs-lookup"><span data-stu-id="b936f-123">Remarks</span></span>

<span data-ttu-id="b936f-124">Questo elemento viene utilizzato per definire la modalità di visualizzazione degli oggetti raccolta e degli oggetti nella raccolta.</span><span class="sxs-lookup"><span data-stu-id="b936f-124">This element is used to define how collection objects and the objects in the collection are displayed.</span></span> <span data-ttu-id="b936f-125">In questo caso, un oggetto della raccolta fa riferimento a qualsiasi oggetto che supporta l'interfaccia **System. Collections. ICollection** .</span><span class="sxs-lookup"><span data-stu-id="b936f-125">In this case, a collection object refers to any object that supports the  **System.Collections.ICollection** interface.</span></span>

<span data-ttu-id="b936f-126">Il comportamento predefinito consiste nel visualizzare solo le proprietà degli oggetti nella raccolta.</span><span class="sxs-lookup"><span data-stu-id="b936f-126">The default behavior is to display only the properties of the objects in the collection.</span></span>

## <a name="see-also"></a><span data-ttu-id="b936f-127">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="b936f-127">See Also</span></span>

[<span data-ttu-id="b936f-128">Scrittura di un file di formattazione di PowerShell</span><span class="sxs-lookup"><span data-stu-id="b936f-128">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)