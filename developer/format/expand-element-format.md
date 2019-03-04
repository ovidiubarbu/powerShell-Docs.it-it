---
title: Espandere l'elemento (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: faa0314b-f6f1-44fd-ad2b-b00cbe38923f
caps.latest.revision: 9
ms.openlocfilehash: 8b924c989133b47e4d95d8429778003c76595d58
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/03/2019
ms.locfileid: "56858577"
---
# <a name="expand-element-format"></a><span data-ttu-id="6589f-102">Elemento Expand (formato)</span><span class="sxs-lookup"><span data-stu-id="6589f-102">Expand Element (Format)</span></span>

<span data-ttu-id="6589f-103">Specifica come viene espanso l'oggetto raccolta per questa definizione.</span><span class="sxs-lookup"><span data-stu-id="6589f-103">Specifies how the collection object is expanded for this definition.</span></span>

<span data-ttu-id="6589f-104">Configurazione (formato) elemento DefaultSettings (formato) elemento EnumerableExpansions (formato) EnumerableExpansion elemento (formato) espandere l'elemento (formato)</span><span class="sxs-lookup"><span data-stu-id="6589f-104">Configuration Element (Format) DefaultSettings Element (Format) EnumerableExpansions Element (Format) EnumerableExpansion Element (Format) Expand Element (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="6589f-105">Sintassi</span><span class="sxs-lookup"><span data-stu-id="6589f-105">Syntax</span></span>

```xml
<Expand>EnumOnly, CoreOnly, Both</Expand>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="6589f-106">Attributi ed elementi</span><span class="sxs-lookup"><span data-stu-id="6589f-106">Attributes and Elements</span></span>

<span data-ttu-id="6589f-107">Le sezioni seguenti descrivono gli attributi e gli elementi figlio dell'elemento padre del `Expand` elemento.</span><span class="sxs-lookup"><span data-stu-id="6589f-107">The following sections describe attributes, child elements, and the parent element of the `Expand` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="6589f-108">Attributes</span><span class="sxs-lookup"><span data-stu-id="6589f-108">Attributes</span></span>

<span data-ttu-id="6589f-109">Nessuna.</span><span class="sxs-lookup"><span data-stu-id="6589f-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="6589f-110">Elementi figlio</span><span class="sxs-lookup"><span data-stu-id="6589f-110">Child Elements</span></span>

<span data-ttu-id="6589f-111">Nessuna.</span><span class="sxs-lookup"><span data-stu-id="6589f-111">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="6589f-112">Elementi padre</span><span class="sxs-lookup"><span data-stu-id="6589f-112">Parent Elements</span></span>

|<span data-ttu-id="6589f-113">Elemento</span><span class="sxs-lookup"><span data-stu-id="6589f-113">Element</span></span>|<span data-ttu-id="6589f-114">Description</span><span class="sxs-lookup"><span data-stu-id="6589f-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="6589f-115">Elemento EnumerableExpansion (formato)</span><span class="sxs-lookup"><span data-stu-id="6589f-115">EnumerableExpansion Element (Format)</span></span>](./enumerableexpansion-element-format.md)|<span data-ttu-id="6589f-116">Definisce una raccolta .NET come specifica gli oggetti vengono espansi quando vengono visualizzati in una vista.</span><span class="sxs-lookup"><span data-stu-id="6589f-116">Defines how specific .NET collection objects are expanded when they are displayed in a view.</span></span>|

## <a name="text-value"></a><span data-ttu-id="6589f-117">Valore di testo</span><span class="sxs-lookup"><span data-stu-id="6589f-117">Text Value</span></span>

<span data-ttu-id="6589f-118">Specificare uno dei valori seguenti:</span><span class="sxs-lookup"><span data-stu-id="6589f-118">Specify one of the following values:</span></span>

- <span data-ttu-id="6589f-119">EnumOnly: Visualizza solo le proprietà degli oggetti nella raccolta.</span><span class="sxs-lookup"><span data-stu-id="6589f-119">EnumOnly: Displays only the properties of the objects in the collection.</span></span>

- <span data-ttu-id="6589f-120">CoreOnly: Visualizza solo le proprietà dell'oggetto della raccolta.</span><span class="sxs-lookup"><span data-stu-id="6589f-120">CoreOnly: Displays only the properties of the collection object.</span></span>

- <span data-ttu-id="6589f-121">Entrambi: Visualizza le proprietà degli oggetti nella raccolta e le proprietà dell'oggetto della raccolta.</span><span class="sxs-lookup"><span data-stu-id="6589f-121">Both: Displays the properties of the objects in the collection and the properties of the collection object.</span></span>

## <a name="remarks"></a><span data-ttu-id="6589f-122">Osservazioni</span><span class="sxs-lookup"><span data-stu-id="6589f-122">Remarks</span></span>

<span data-ttu-id="6589f-123">Questo elemento viene usato per definire come vengono visualizzati gli oggetti raccolta e gli oggetti nella raccolta.</span><span class="sxs-lookup"><span data-stu-id="6589f-123">This element is used to define how collection objects and the objects in the collection are displayed.</span></span> <span data-ttu-id="6589f-124">In questo caso, un oggetto raccolta fa riferimento a qualsiasi oggetto che supporta il **System.Collections.ICollection** interfaccia.</span><span class="sxs-lookup"><span data-stu-id="6589f-124">In this case, a collection object refers to any object that supports the  **System.Collections.ICollection** interface.</span></span>

<span data-ttu-id="6589f-125">Il comportamento predefinito è per visualizzare solo le proprietà degli oggetti nella raccolta.</span><span class="sxs-lookup"><span data-stu-id="6589f-125">The default behavior is to display only the properties of the objects in the collection.</span></span>

## <a name="see-also"></a><span data-ttu-id="6589f-126">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="6589f-126">See Also</span></span>

[<span data-ttu-id="6589f-127">La scrittura di un File di formattazione di PowerShell</span><span class="sxs-lookup"><span data-stu-id="6589f-127">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
