---
title: Elemento EnumerableExpansion (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 93d27173-9ae4-46e5-bb78-90525915cd70
caps.latest.revision: 9
ms.openlocfilehash: bc1e58c00ca8419f9204076f0a46050281e704db
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/03/2019
ms.locfileid: "56856837"
---
# <a name="enumerableexpansion-element-format"></a><span data-ttu-id="35254-102">Elemento EnumerableExpansion (formato)</span><span class="sxs-lookup"><span data-stu-id="35254-102">EnumerableExpansion Element (Format)</span></span>

<span data-ttu-id="35254-103">Definisce una raccolta .NET come specifica gli oggetti vengono espansi quando vengono visualizzati in una vista.</span><span class="sxs-lookup"><span data-stu-id="35254-103">Defines how specific .NET collection objects are expanded when they are displayed in a view.</span></span>

<span data-ttu-id="35254-104">Configurazione (formato) elemento DefaultSettings (formato) elemento EnumerableExpansions (formato) EnumerableExpansion elemento (formato)</span><span class="sxs-lookup"><span data-stu-id="35254-104">Configuration Element (Format) DefaultSettings Element (Format) EnumerableExpansions Element (Format) EnumerableExpansion Element (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="35254-105">Sintassi</span><span class="sxs-lookup"><span data-stu-id="35254-105">Syntax</span></span>

```xml
<EnumerableExpansion>
  <EntrySelectedBy>...</EntrySelectedBy>
  <Expand>EnumOnly, CoreOnly, Both</Expand>
</EnumerableExpansion>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="35254-106">Attributi ed elementi</span><span class="sxs-lookup"><span data-stu-id="35254-106">Attributes and Elements</span></span>

<span data-ttu-id="35254-107">Le sezioni seguenti descrivono gli attributi e gli elementi figlio dell'elemento padre del `EnumerableExpansion` elemento.</span><span class="sxs-lookup"><span data-stu-id="35254-107">The following sections describe attributes, child elements, and the parent element of the `EnumerableExpansion` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="35254-108">Attributes</span><span class="sxs-lookup"><span data-stu-id="35254-108">Attributes</span></span>

<span data-ttu-id="35254-109">Nessuna.</span><span class="sxs-lookup"><span data-stu-id="35254-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="35254-110">Elementi figlio</span><span class="sxs-lookup"><span data-stu-id="35254-110">Child Elements</span></span>

|<span data-ttu-id="35254-111">Elemento</span><span class="sxs-lookup"><span data-stu-id="35254-111">Element</span></span>|<span data-ttu-id="35254-112">Description</span><span class="sxs-lookup"><span data-stu-id="35254-112">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="35254-113">Elemento EntrySelectedBy per EnumerableExpansion (formato)</span><span class="sxs-lookup"><span data-stu-id="35254-113">EntrySelectedBy Element for EnumerableExpansion (Format)</span></span>](./entryselectedby-element-for-enumerableexpansion-format.md)|<span data-ttu-id="35254-114">Elemento facoltativo.</span><span class="sxs-lookup"><span data-stu-id="35254-114">Optional element.</span></span><br /><br /> <span data-ttu-id="35254-115">Definisce quali oggetti della raccolta .NET vengono espanse per questa definizione.</span><span class="sxs-lookup"><span data-stu-id="35254-115">Defines which .NET collection objects are expanded by this definition.</span></span>|
|[<span data-ttu-id="35254-116">Espandere l'elemento (formato)</span><span class="sxs-lookup"><span data-stu-id="35254-116">Expand Element (Format)</span></span>](./expand-element-format.md)|<span data-ttu-id="35254-117">Specifica come viene espanso l'oggetto raccolta per questa definizione.</span><span class="sxs-lookup"><span data-stu-id="35254-117">Specifies how the collection object is expanded for this definition.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="35254-118">Elementi padre</span><span class="sxs-lookup"><span data-stu-id="35254-118">Parent Elements</span></span>

|<span data-ttu-id="35254-119">Elemento</span><span class="sxs-lookup"><span data-stu-id="35254-119">Element</span></span>|<span data-ttu-id="35254-120">Description</span><span class="sxs-lookup"><span data-stu-id="35254-120">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="35254-121">Elemento EnumerableExpansions (formato)</span><span class="sxs-lookup"><span data-stu-id="35254-121">EnumerableExpansions Element (Format)</span></span>](./enumerableexpansions-element-format.md)|<span data-ttu-id="35254-122">Definisce i diversi modi di tale raccolta .NET gli oggetti vengono espansi quando vengono visualizzati in una vista.</span><span class="sxs-lookup"><span data-stu-id="35254-122">Defines the different ways that .NET collection objects are expanded when they are displayed in a view.</span></span>|

## <a name="remarks"></a><span data-ttu-id="35254-123">Osservazioni</span><span class="sxs-lookup"><span data-stu-id="35254-123">Remarks</span></span>

<span data-ttu-id="35254-124">Questo elemento viene usato per definire come vengono visualizzati gli oggetti raccolta e gli oggetti nella raccolta.</span><span class="sxs-lookup"><span data-stu-id="35254-124">This element is used to define how collection objects and the objects in the collection are displayed.</span></span> <span data-ttu-id="35254-125">In questo caso, un oggetto raccolta fa riferimento a qualsiasi oggetto che supporta il **System.Collections.ICollection** interfaccia.</span><span class="sxs-lookup"><span data-stu-id="35254-125">In this case, a collection object refers to any object that supports the  **System.Collections.ICollection** interface.</span></span>

<span data-ttu-id="35254-126">Il comportamento predefinito è per visualizzare solo le proprietà degli oggetti nella raccolta.</span><span class="sxs-lookup"><span data-stu-id="35254-126">The default behavior is to display only the properties of the objects in the collection.</span></span>

## <a name="see-also"></a><span data-ttu-id="35254-127">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="35254-127">See Also</span></span>

[<span data-ttu-id="35254-128">La scrittura di un File di formattazione di PowerShell</span><span class="sxs-lookup"><span data-stu-id="35254-128">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
