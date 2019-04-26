---
title: Elemento EnumerableExpansions (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 50c33892-2ade-44c2-906c-81e5f5ca21f2
caps.latest.revision: 9
ms.openlocfilehash: 1ecbda8a3b623757517019105e3b1ee46ccbb55c
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62066091"
---
# <a name="enumerableexpansions-element-format"></a><span data-ttu-id="b9745-102">Elemento EnumerableExpansions (formato)</span><span class="sxs-lookup"><span data-stu-id="b9745-102">EnumerableExpansions Element (Format)</span></span>

<span data-ttu-id="b9745-103">Definisce come oggetti della raccolta .NET vengono espanse quando vengono visualizzati in una vista.</span><span class="sxs-lookup"><span data-stu-id="b9745-103">Defines how .NET collection objects are expanded when they are displayed in a view.</span></span>

<span data-ttu-id="b9745-104">Configurazione (formato) elemento DefaultSettings (formato) EnumerableExpansions elemento (formato)</span><span class="sxs-lookup"><span data-stu-id="b9745-104">Configuration Element (Format) DefaultSettings Element (Format) EnumerableExpansions Element (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="b9745-105">Sintassi</span><span class="sxs-lookup"><span data-stu-id="b9745-105">Syntax</span></span>

```xml
<EnumerableExpansions>
  <EnumerableExpansion>...</EnumerableExpansion>
</EnumerableExpansions>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="b9745-106">Elementi e attributi</span><span class="sxs-lookup"><span data-stu-id="b9745-106">Attributes and Elements</span></span>

<span data-ttu-id="b9745-107">Le sezioni seguenti descrivono gli attributi e gli elementi figlio dell'elemento padre del `EnumerableExpansions` elemento.</span><span class="sxs-lookup"><span data-stu-id="b9745-107">The following sections describe attributes, child elements, and the parent element of the `EnumerableExpansions` element.</span></span> <span data-ttu-id="b9745-108">Non sono previsti limiti al numero di elementi figlio che è possibile usare.</span><span class="sxs-lookup"><span data-stu-id="b9745-108">There is no limit to the number of child elements that you can use.</span></span>

### <a name="attributes"></a><span data-ttu-id="b9745-109">Attributes</span><span class="sxs-lookup"><span data-stu-id="b9745-109">Attributes</span></span>

<span data-ttu-id="b9745-110">Nessuna.</span><span class="sxs-lookup"><span data-stu-id="b9745-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="b9745-111">Elementi figlio</span><span class="sxs-lookup"><span data-stu-id="b9745-111">Child Elements</span></span>

|<span data-ttu-id="b9745-112">Elemento</span><span class="sxs-lookup"><span data-stu-id="b9745-112">Element</span></span>|<span data-ttu-id="b9745-113">Description</span><span class="sxs-lookup"><span data-stu-id="b9745-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="b9745-114">Elemento EnumerableExpansion (formato)</span><span class="sxs-lookup"><span data-stu-id="b9745-114">EnumerableExpansion Element (Format)</span></span>](./enumerableexpansion-element-format.md)|<span data-ttu-id="b9745-115">Elemento facoltativo.</span><span class="sxs-lookup"><span data-stu-id="b9745-115">Optional element.</span></span><br /><br /> <span data-ttu-id="b9745-116">Definisce gli oggetti della raccolta .NET specifici che vengono espanse quando vengono visualizzati in una vista.</span><span class="sxs-lookup"><span data-stu-id="b9745-116">Defines the specific .NET collection objects that are expanded when they are displayed in a view.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="b9745-117">Elementi padre</span><span class="sxs-lookup"><span data-stu-id="b9745-117">Parent Elements</span></span>

|<span data-ttu-id="b9745-118">Elemento</span><span class="sxs-lookup"><span data-stu-id="b9745-118">Element</span></span>|<span data-ttu-id="b9745-119">Description</span><span class="sxs-lookup"><span data-stu-id="b9745-119">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="b9745-120">Elemento DefaultSettings (formato)</span><span class="sxs-lookup"><span data-stu-id="b9745-120">DefaultSettings Element (Format)</span></span>](./defaultsettings-element-format.md)|<span data-ttu-id="b9745-121">Definisce le impostazioni comuni che si applicano a tutte le visualizzazioni del file di formattazione.</span><span class="sxs-lookup"><span data-stu-id="b9745-121">Defines common settings that apply to all the views of the formatting file.</span></span>|

## <a name="remarks"></a><span data-ttu-id="b9745-122">Osservazioni</span><span class="sxs-lookup"><span data-stu-id="b9745-122">Remarks</span></span>

<span data-ttu-id="b9745-123">Questo elemento viene usato per definire come vengono visualizzati gli oggetti raccolta e gli oggetti nella raccolta.</span><span class="sxs-lookup"><span data-stu-id="b9745-123">This element is used to define how collection objects and the objects in the collection are displayed.</span></span> <span data-ttu-id="b9745-124">In questo caso, un oggetto raccolta fa riferimento a qualsiasi oggetto che supporta il **System.Collections.ICollection** interfaccia.</span><span class="sxs-lookup"><span data-stu-id="b9745-124">In this case, a collection object refers to any object that supports the  **System.Collections.ICollection** interface.</span></span>

## <a name="see-also"></a><span data-ttu-id="b9745-125">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="b9745-125">See Also</span></span>

[<span data-ttu-id="b9745-126">La scrittura di un File di formattazione di PowerShell</span><span class="sxs-lookup"><span data-stu-id="b9745-126">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
