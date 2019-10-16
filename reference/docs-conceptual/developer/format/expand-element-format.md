---
title: Elemento Expand (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: faa0314b-f6f1-44fd-ad2b-b00cbe38923f
caps.latest.revision: 9
ms.openlocfilehash: 8b924c989133b47e4d95d8429778003c76595d58
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/15/2019
ms.locfileid: "72368740"
---
# <a name="expand-element-format"></a><span data-ttu-id="20cef-102">Elemento Expand (formato)</span><span class="sxs-lookup"><span data-stu-id="20cef-102">Expand Element (Format)</span></span>

<span data-ttu-id="20cef-103">Specifica la modalità di espansione dell'oggetto raccolta per questa definizione.</span><span class="sxs-lookup"><span data-stu-id="20cef-103">Specifies how the collection object is expanded for this definition.</span></span>

<span data-ttu-id="20cef-104">Elemento Configuration (Format) elemento DefaultSettings (Format) elemento EnumerableExpansions (Format) elemento EnumerableExpansion (Format) elemento Expand (Format)</span><span class="sxs-lookup"><span data-stu-id="20cef-104">Configuration Element (Format) DefaultSettings Element (Format) EnumerableExpansions Element (Format) EnumerableExpansion Element (Format) Expand Element (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="20cef-105">Sintassi</span><span class="sxs-lookup"><span data-stu-id="20cef-105">Syntax</span></span>

```xml
<Expand>EnumOnly, CoreOnly, Both</Expand>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="20cef-106">Attributi ed elementi</span><span class="sxs-lookup"><span data-stu-id="20cef-106">Attributes and Elements</span></span>

<span data-ttu-id="20cef-107">Nelle sezioni seguenti vengono descritti gli attributi, gli elementi figlio e l'elemento padre dell'elemento `Expand`.</span><span class="sxs-lookup"><span data-stu-id="20cef-107">The following sections describe attributes, child elements, and the parent element of the `Expand` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="20cef-108">Attributi</span><span class="sxs-lookup"><span data-stu-id="20cef-108">Attributes</span></span>

<span data-ttu-id="20cef-109">Nessuna.</span><span class="sxs-lookup"><span data-stu-id="20cef-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="20cef-110">Elementi figlio</span><span class="sxs-lookup"><span data-stu-id="20cef-110">Child Elements</span></span>

<span data-ttu-id="20cef-111">Nessuna.</span><span class="sxs-lookup"><span data-stu-id="20cef-111">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="20cef-112">Elementi padre</span><span class="sxs-lookup"><span data-stu-id="20cef-112">Parent Elements</span></span>

|<span data-ttu-id="20cef-113">Elemento</span><span class="sxs-lookup"><span data-stu-id="20cef-113">Element</span></span>|<span data-ttu-id="20cef-114">Description</span><span class="sxs-lookup"><span data-stu-id="20cef-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="20cef-115">Elemento EnumerableExpansion (Format)</span><span class="sxs-lookup"><span data-stu-id="20cef-115">EnumerableExpansion Element (Format)</span></span>](./enumerableexpansion-element-format.md)|<span data-ttu-id="20cef-116">Definisce la modalità di espansione degli oggetti raccolta .NET specifici quando vengono visualizzati in una visualizzazione.</span><span class="sxs-lookup"><span data-stu-id="20cef-116">Defines how specific .NET collection objects are expanded when they are displayed in a view.</span></span>|

## <a name="text-value"></a><span data-ttu-id="20cef-117">Valore di testo</span><span class="sxs-lookup"><span data-stu-id="20cef-117">Text Value</span></span>

<span data-ttu-id="20cef-118">Specificare uno dei valori seguenti:</span><span class="sxs-lookup"><span data-stu-id="20cef-118">Specify one of the following values:</span></span>

- <span data-ttu-id="20cef-119">EnumOnly: Visualizza solo le proprietà degli oggetti nella raccolta.</span><span class="sxs-lookup"><span data-stu-id="20cef-119">EnumOnly: Displays only the properties of the objects in the collection.</span></span>

- <span data-ttu-id="20cef-120">CoreOnly: Visualizza solo le proprietà dell'oggetto raccolta.</span><span class="sxs-lookup"><span data-stu-id="20cef-120">CoreOnly: Displays only the properties of the collection object.</span></span>

- <span data-ttu-id="20cef-121">Both: Visualizza le proprietà degli oggetti nella raccolta e le proprietà dell'oggetto raccolta.</span><span class="sxs-lookup"><span data-stu-id="20cef-121">Both: Displays the properties of the objects in the collection and the properties of the collection object.</span></span>

## <a name="remarks"></a><span data-ttu-id="20cef-122">Osservazioni</span><span class="sxs-lookup"><span data-stu-id="20cef-122">Remarks</span></span>

<span data-ttu-id="20cef-123">Questo elemento viene utilizzato per definire la modalità di visualizzazione degli oggetti raccolta e degli oggetti nella raccolta.</span><span class="sxs-lookup"><span data-stu-id="20cef-123">This element is used to define how collection objects and the objects in the collection are displayed.</span></span> <span data-ttu-id="20cef-124">In questo caso, un oggetto della raccolta fa riferimento a qualsiasi oggetto che supporta l'interfaccia **System. Collections. ICollection** .</span><span class="sxs-lookup"><span data-stu-id="20cef-124">In this case, a collection object refers to any object that supports the  **System.Collections.ICollection** interface.</span></span>

<span data-ttu-id="20cef-125">Il comportamento predefinito consiste nel visualizzare solo le proprietà degli oggetti nella raccolta.</span><span class="sxs-lookup"><span data-stu-id="20cef-125">The default behavior is to display only the properties of the objects in the collection.</span></span>

## <a name="see-also"></a><span data-ttu-id="20cef-126">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="20cef-126">See Also</span></span>

[<span data-ttu-id="20cef-127">Scrittura di un file di formattazione di PowerShell</span><span class="sxs-lookup"><span data-stu-id="20cef-127">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
