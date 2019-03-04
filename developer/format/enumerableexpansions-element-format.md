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
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/03/2019
ms.locfileid: "56860257"
---
# <a name="enumerableexpansions-element-format"></a><span data-ttu-id="d5ffb-102">Elemento EnumerableExpansions (formato)</span><span class="sxs-lookup"><span data-stu-id="d5ffb-102">EnumerableExpansions Element (Format)</span></span>

<span data-ttu-id="d5ffb-103">Definisce come oggetti della raccolta .NET vengono espanse quando vengono visualizzati in una vista.</span><span class="sxs-lookup"><span data-stu-id="d5ffb-103">Defines how .NET collection objects are expanded when they are displayed in a view.</span></span>

<span data-ttu-id="d5ffb-104">Configurazione (formato) elemento DefaultSettings (formato) EnumerableExpansions elemento (formato)</span><span class="sxs-lookup"><span data-stu-id="d5ffb-104">Configuration Element (Format) DefaultSettings Element (Format) EnumerableExpansions Element (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="d5ffb-105">Sintassi</span><span class="sxs-lookup"><span data-stu-id="d5ffb-105">Syntax</span></span>

```xml
<EnumerableExpansions>
  <EnumerableExpansion>...</EnumerableExpansion>
</EnumerableExpansions>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="d5ffb-106">Attributi ed elementi</span><span class="sxs-lookup"><span data-stu-id="d5ffb-106">Attributes and Elements</span></span>

<span data-ttu-id="d5ffb-107">Le sezioni seguenti descrivono gli attributi e gli elementi figlio dell'elemento padre del `EnumerableExpansions` elemento.</span><span class="sxs-lookup"><span data-stu-id="d5ffb-107">The following sections describe attributes, child elements, and the parent element of the `EnumerableExpansions` element.</span></span> <span data-ttu-id="d5ffb-108">Non sono previsti limiti al numero di elementi figlio che è possibile usare.</span><span class="sxs-lookup"><span data-stu-id="d5ffb-108">There is no limit to the number of child elements that you can use.</span></span>

### <a name="attributes"></a><span data-ttu-id="d5ffb-109">Attributes</span><span class="sxs-lookup"><span data-stu-id="d5ffb-109">Attributes</span></span>

<span data-ttu-id="d5ffb-110">Nessuna.</span><span class="sxs-lookup"><span data-stu-id="d5ffb-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="d5ffb-111">Elementi figlio</span><span class="sxs-lookup"><span data-stu-id="d5ffb-111">Child Elements</span></span>

|<span data-ttu-id="d5ffb-112">Elemento</span><span class="sxs-lookup"><span data-stu-id="d5ffb-112">Element</span></span>|<span data-ttu-id="d5ffb-113">Description</span><span class="sxs-lookup"><span data-stu-id="d5ffb-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="d5ffb-114">Elemento EnumerableExpansion (formato)</span><span class="sxs-lookup"><span data-stu-id="d5ffb-114">EnumerableExpansion Element (Format)</span></span>](./enumerableexpansion-element-format.md)|<span data-ttu-id="d5ffb-115">Elemento facoltativo.</span><span class="sxs-lookup"><span data-stu-id="d5ffb-115">Optional element.</span></span><br /><br /> <span data-ttu-id="d5ffb-116">Definisce gli oggetti della raccolta .NET specifici che vengono espanse quando vengono visualizzati in una vista.</span><span class="sxs-lookup"><span data-stu-id="d5ffb-116">Defines the specific .NET collection objects that are expanded when they are displayed in a view.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="d5ffb-117">Elementi padre</span><span class="sxs-lookup"><span data-stu-id="d5ffb-117">Parent Elements</span></span>

|<span data-ttu-id="d5ffb-118">Elemento</span><span class="sxs-lookup"><span data-stu-id="d5ffb-118">Element</span></span>|<span data-ttu-id="d5ffb-119">Description</span><span class="sxs-lookup"><span data-stu-id="d5ffb-119">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="d5ffb-120">Elemento DefaultSettings (formato)</span><span class="sxs-lookup"><span data-stu-id="d5ffb-120">DefaultSettings Element (Format)</span></span>](./defaultsettings-element-format.md)|<span data-ttu-id="d5ffb-121">Definisce le impostazioni comuni che si applicano a tutte le visualizzazioni del file di formattazione.</span><span class="sxs-lookup"><span data-stu-id="d5ffb-121">Defines common settings that apply to all the views of the formatting file.</span></span>|

## <a name="remarks"></a><span data-ttu-id="d5ffb-122">Osservazioni</span><span class="sxs-lookup"><span data-stu-id="d5ffb-122">Remarks</span></span>

<span data-ttu-id="d5ffb-123">Questo elemento viene usato per definire come vengono visualizzati gli oggetti raccolta e gli oggetti nella raccolta.</span><span class="sxs-lookup"><span data-stu-id="d5ffb-123">This element is used to define how collection objects and the objects in the collection are displayed.</span></span> <span data-ttu-id="d5ffb-124">In questo caso, un oggetto raccolta fa riferimento a qualsiasi oggetto che supporta il **System.Collections.ICollection** interfaccia.</span><span class="sxs-lookup"><span data-stu-id="d5ffb-124">In this case, a collection object refers to any object that supports the  **System.Collections.ICollection** interface.</span></span>

## <a name="see-also"></a><span data-ttu-id="d5ffb-125">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="d5ffb-125">See Also</span></span>

[<span data-ttu-id="d5ffb-126">La scrittura di un File di formattazione di PowerShell</span><span class="sxs-lookup"><span data-stu-id="d5ffb-126">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
