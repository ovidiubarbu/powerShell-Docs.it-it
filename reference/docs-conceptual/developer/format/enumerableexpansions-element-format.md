---
title: Elemento EnumerableExpansions (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 50c33892-2ade-44c2-906c-81e5f5ca21f2
caps.latest.revision: 9
ms.openlocfilehash: 1ecbda8a3b623757517019105e3b1ee46ccbb55c
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/15/2019
ms.locfileid: "72363300"
---
# <a name="enumerableexpansions-element-format"></a><span data-ttu-id="e3bdc-102">Elemento EnumerableExpansions (formato)</span><span class="sxs-lookup"><span data-stu-id="e3bdc-102">EnumerableExpansions Element (Format)</span></span>

<span data-ttu-id="e3bdc-103">Definisce la modalità di espansione degli oggetti raccolta .NET quando vengono visualizzati in una visualizzazione.</span><span class="sxs-lookup"><span data-stu-id="e3bdc-103">Defines how .NET collection objects are expanded when they are displayed in a view.</span></span>

<span data-ttu-id="e3bdc-104">Elemento Configuration (Format) elemento DefaultSettings (Format) elemento EnumerableExpansions (Format)</span><span class="sxs-lookup"><span data-stu-id="e3bdc-104">Configuration Element (Format) DefaultSettings Element (Format) EnumerableExpansions Element (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="e3bdc-105">Sintassi</span><span class="sxs-lookup"><span data-stu-id="e3bdc-105">Syntax</span></span>

```xml
<EnumerableExpansions>
  <EnumerableExpansion>...</EnumerableExpansion>
</EnumerableExpansions>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="e3bdc-106">Attributi ed elementi</span><span class="sxs-lookup"><span data-stu-id="e3bdc-106">Attributes and Elements</span></span>

<span data-ttu-id="e3bdc-107">Nelle sezioni seguenti vengono descritti gli attributi, gli elementi figlio e l'elemento padre dell'elemento `EnumerableExpansions`.</span><span class="sxs-lookup"><span data-stu-id="e3bdc-107">The following sections describe attributes, child elements, and the parent element of the `EnumerableExpansions` element.</span></span> <span data-ttu-id="e3bdc-108">Non esiste alcun limite al numero di elementi figlio che è possibile utilizzare.</span><span class="sxs-lookup"><span data-stu-id="e3bdc-108">There is no limit to the number of child elements that you can use.</span></span>

### <a name="attributes"></a><span data-ttu-id="e3bdc-109">Attributi</span><span class="sxs-lookup"><span data-stu-id="e3bdc-109">Attributes</span></span>

<span data-ttu-id="e3bdc-110">Nessuna.</span><span class="sxs-lookup"><span data-stu-id="e3bdc-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="e3bdc-111">Elementi figlio</span><span class="sxs-lookup"><span data-stu-id="e3bdc-111">Child Elements</span></span>

|<span data-ttu-id="e3bdc-112">Elemento</span><span class="sxs-lookup"><span data-stu-id="e3bdc-112">Element</span></span>|<span data-ttu-id="e3bdc-113">Description</span><span class="sxs-lookup"><span data-stu-id="e3bdc-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="e3bdc-114">Elemento EnumerableExpansion (Format)</span><span class="sxs-lookup"><span data-stu-id="e3bdc-114">EnumerableExpansion Element (Format)</span></span>](./enumerableexpansion-element-format.md)|<span data-ttu-id="e3bdc-115">Elemento facoltativo.</span><span class="sxs-lookup"><span data-stu-id="e3bdc-115">Optional element.</span></span><br /><br /> <span data-ttu-id="e3bdc-116">Definisce gli oggetti della raccolta .NET specifici che vengono espansi quando vengono visualizzati in una visualizzazione.</span><span class="sxs-lookup"><span data-stu-id="e3bdc-116">Defines the specific .NET collection objects that are expanded when they are displayed in a view.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="e3bdc-117">Elementi padre</span><span class="sxs-lookup"><span data-stu-id="e3bdc-117">Parent Elements</span></span>

|<span data-ttu-id="e3bdc-118">Elemento</span><span class="sxs-lookup"><span data-stu-id="e3bdc-118">Element</span></span>|<span data-ttu-id="e3bdc-119">Description</span><span class="sxs-lookup"><span data-stu-id="e3bdc-119">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="e3bdc-120">Elemento DefaultSettings (Format)</span><span class="sxs-lookup"><span data-stu-id="e3bdc-120">DefaultSettings Element (Format)</span></span>](./defaultsettings-element-format.md)|<span data-ttu-id="e3bdc-121">Definisce le impostazioni comuni che si applicano a tutte le visualizzazioni del file di formattazione.</span><span class="sxs-lookup"><span data-stu-id="e3bdc-121">Defines common settings that apply to all the views of the formatting file.</span></span>|

## <a name="remarks"></a><span data-ttu-id="e3bdc-122">Osservazioni</span><span class="sxs-lookup"><span data-stu-id="e3bdc-122">Remarks</span></span>

<span data-ttu-id="e3bdc-123">Questo elemento viene utilizzato per definire la modalità di visualizzazione degli oggetti raccolta e degli oggetti nella raccolta.</span><span class="sxs-lookup"><span data-stu-id="e3bdc-123">This element is used to define how collection objects and the objects in the collection are displayed.</span></span> <span data-ttu-id="e3bdc-124">In questo caso, un oggetto della raccolta fa riferimento a qualsiasi oggetto che supporta l'interfaccia **System. Collections. ICollection** .</span><span class="sxs-lookup"><span data-stu-id="e3bdc-124">In this case, a collection object refers to any object that supports the  **System.Collections.ICollection** interface.</span></span>

## <a name="see-also"></a><span data-ttu-id="e3bdc-125">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="e3bdc-125">See Also</span></span>

[<span data-ttu-id="e3bdc-126">Scrittura di un file di formattazione di PowerShell</span><span class="sxs-lookup"><span data-stu-id="e3bdc-126">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
