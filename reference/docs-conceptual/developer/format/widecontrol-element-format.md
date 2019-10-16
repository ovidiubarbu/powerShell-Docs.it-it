---
title: Elemento WideControl (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 715ea055-037b-46ad-b70f-87b3f5134403
caps.latest.revision: 14
ms.openlocfilehash: 2742be0389a1bf04af100a490a59c0d938165811
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/15/2019
ms.locfileid: "72367990"
---
# <a name="widecontrol-element-format"></a><span data-ttu-id="80e43-102">Elemento WideControl (formato)</span><span class="sxs-lookup"><span data-stu-id="80e43-102">WideControl Element (Format)</span></span>

<span data-ttu-id="80e43-103">Definisce un formato di elenco Wide (valore singolo) per la visualizzazione.</span><span class="sxs-lookup"><span data-stu-id="80e43-103">Defines a wide (single value) list format for the view.</span></span> <span data-ttu-id="80e43-104">Questa vista consente di visualizzare un singolo valore di proprietà o un valore di script per ogni oggetto.</span><span class="sxs-lookup"><span data-stu-id="80e43-104">This view displays a single property value or script value for each object.</span></span>

<span data-ttu-id="80e43-105">Elemento Configuration (Format) elemento ViewDefinitions (Format) elemento View (Format) elemento WideControl (Format)</span><span class="sxs-lookup"><span data-stu-id="80e43-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) WideControl Element (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="80e43-106">Sintassi</span><span class="sxs-lookup"><span data-stu-id="80e43-106">Syntax</span></span>

```xml
<WideControl>
  <AutoSize/>
  <ColumnNumber>PositiveInteger</ColumnNumber>
  <WideEntries>...</WideEntries>
</WideControl>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="80e43-107">Attributi ed elementi</span><span class="sxs-lookup"><span data-stu-id="80e43-107">Attributes and Elements</span></span>

<span data-ttu-id="80e43-108">Nelle sezioni seguenti vengono descritti gli attributi, gli elementi figlio e l'elemento padre dell'elemento `WideControl`.</span><span class="sxs-lookup"><span data-stu-id="80e43-108">The following sections describe the attributes, child elements, and parent element of the `WideControl` element.</span></span> <span data-ttu-id="80e43-109">Non è possibile specificare contemporaneamente gli elementi `AutoSize` e `ColumnNumber`.</span><span class="sxs-lookup"><span data-stu-id="80e43-109">You cannot specify the `AutoSize` and `ColumnNumber` elements at the same time.</span></span>

### <a name="attributes"></a><span data-ttu-id="80e43-110">Attributi</span><span class="sxs-lookup"><span data-stu-id="80e43-110">Attributes</span></span>

<span data-ttu-id="80e43-111">Nessuna.</span><span class="sxs-lookup"><span data-stu-id="80e43-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="80e43-112">Elementi figlio</span><span class="sxs-lookup"><span data-stu-id="80e43-112">Child Elements</span></span>

|<span data-ttu-id="80e43-113">Elemento</span><span class="sxs-lookup"><span data-stu-id="80e43-113">Element</span></span>|<span data-ttu-id="80e43-114">Description</span><span class="sxs-lookup"><span data-stu-id="80e43-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="80e43-115">Elemento AutoSize per WideControl (Format)</span><span class="sxs-lookup"><span data-stu-id="80e43-115">AutoSize Element for WideControl (Format)</span></span>](./autosize-element-for-widecontrol-format.md)|<span data-ttu-id="80e43-116">Elemento facoltativo.</span><span class="sxs-lookup"><span data-stu-id="80e43-116">Optional element.</span></span><br /><br /> <span data-ttu-id="80e43-117">Specifica se le dimensioni della colonna e il numero di colonne vengono regolate in base alle dimensioni dei dati.</span><span class="sxs-lookup"><span data-stu-id="80e43-117">Specifies whether the column size and the number of columns are adjusted based on the size of the data.</span></span>|
|[<span data-ttu-id="80e43-118">Elemento ColumnNumber per WideControl (Format)</span><span class="sxs-lookup"><span data-stu-id="80e43-118">ColumnNumber Element for WideControl (Format)</span></span>](./columnnumber-element-for-widecontrol-format.md)|<span data-ttu-id="80e43-119">Elemento facoltativo.</span><span class="sxs-lookup"><span data-stu-id="80e43-119">Optional element.</span></span><br /><br /> <span data-ttu-id="80e43-120">Specifica il numero di colonne visualizzate nella visualizzazione estesa.</span><span class="sxs-lookup"><span data-stu-id="80e43-120">Specifies the number of columns displayed in the wide view.</span></span>|
|[<span data-ttu-id="80e43-121">Elemento WideEntries (Format)</span><span class="sxs-lookup"><span data-stu-id="80e43-121">WideEntries Element (Format)</span></span>](./wideentries-element-for-widecontrol-format.md)|<span data-ttu-id="80e43-122">Elemento obbligatorio.</span><span class="sxs-lookup"><span data-stu-id="80e43-122">Required element.</span></span><br /><br /> <span data-ttu-id="80e43-123">Fornisce le definizioni della visualizzazione estesa.</span><span class="sxs-lookup"><span data-stu-id="80e43-123">Provides the definitions of the wide view.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="80e43-124">Elementi padre</span><span class="sxs-lookup"><span data-stu-id="80e43-124">Parent Elements</span></span>

|<span data-ttu-id="80e43-125">Elemento</span><span class="sxs-lookup"><span data-stu-id="80e43-125">Element</span></span>|<span data-ttu-id="80e43-126">Description</span><span class="sxs-lookup"><span data-stu-id="80e43-126">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="80e43-127">Elemento View (Format)</span><span class="sxs-lookup"><span data-stu-id="80e43-127">View Element (Format)</span></span>](./view-element-format.md)|<span data-ttu-id="80e43-128">Definisce una vista utilizzata per visualizzare uno o più oggetti .NET.</span><span class="sxs-lookup"><span data-stu-id="80e43-128">Defines a view that is used to display one or more .NET objects.</span></span>|

## <a name="remarks"></a><span data-ttu-id="80e43-129">Osservazioni</span><span class="sxs-lookup"><span data-stu-id="80e43-129">Remarks</span></span>

<span data-ttu-id="80e43-130">Quando si definisce una visualizzazione estesa, è possibile aggiungere l'elemento `AutoSize` o il `ColumnNumber`, ma non è possibile aggiungerne entrambi.</span><span class="sxs-lookup"><span data-stu-id="80e43-130">When defining a wide view, you can add the `AutoSize` element or the `ColumnNumber` but you cannot add both.</span></span>

<span data-ttu-id="80e43-131">Nella maggior parte dei casi, è necessaria una sola definizione per ogni visualizzazione estesa, ma è possibile avere più definizioni se si vuole usare la stessa visualizzazione per visualizzare oggetti .NET diversi.</span><span class="sxs-lookup"><span data-stu-id="80e43-131">In most cases, only one definition is required for each wide view, but it is possible to have multiple definitions if you want to use the same view to display different .NET objects.</span></span> <span data-ttu-id="80e43-132">In questi casi, è possibile specificare una definizione separata per ogni oggetto o set di oggetti.</span><span class="sxs-lookup"><span data-stu-id="80e43-132">In those cases, you can provide a separate definition for each object or set of objects.</span></span>

<span data-ttu-id="80e43-133">Per ulteriori informazioni sui componenti di una visualizzazione estesa, vedere [componenti di visualizzazione ampia](./creating-a-wide-view.md).</span><span class="sxs-lookup"><span data-stu-id="80e43-133">For more information about the components of a wide view, see [Wide View Components](./creating-a-wide-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="80e43-134">Esempio</span><span class="sxs-lookup"><span data-stu-id="80e43-134">Example</span></span>

<span data-ttu-id="80e43-135">Nell'esempio seguente viene illustrato un elemento `WideControl` utilizzato per visualizzare una proprietà dell'oggetto [System. Diagnostics. Process](/dotnet/api/System.Diagnostics.Process) .</span><span class="sxs-lookup"><span data-stu-id="80e43-135">The following example shows a `WideControl` element that is used to display a property of the [System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process) object.</span></span>

```xml
<View>
  <Name>process</Name>
  <ViewSelectedBy>
    <TypeName>System.Diagnostics.Process</TypeName>
  </ViewSelectedBy>
  <WideControl>
    <WideEntries>...</WideEntries>
  </WideControl>
</View>
```

<span data-ttu-id="80e43-136">Per un esempio completo di una visualizzazione estesa, vedere [Wide View (Basic)](./wide-view-basic.md).</span><span class="sxs-lookup"><span data-stu-id="80e43-136">For a complete example of a wide view, see [Wide View (Basic)](./wide-view-basic.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="80e43-137">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="80e43-137">See Also</span></span>

[<span data-ttu-id="80e43-138">Elemento AutoSize per WideControl (Format)</span><span class="sxs-lookup"><span data-stu-id="80e43-138">Autosize Element for WideControl (Format)</span></span>](./autosize-element-for-widecontrol-format.md)

[<span data-ttu-id="80e43-139">Elemento ColumnNumber per WideControl (Format)</span><span class="sxs-lookup"><span data-stu-id="80e43-139">ColumnNumber Element for WideControl (Format)</span></span>](./columnnumber-element-for-widecontrol-format.md)

[<span data-ttu-id="80e43-140">Elemento View (Format)</span><span class="sxs-lookup"><span data-stu-id="80e43-140">View Element (Format)</span></span>](./view-element-format.md)

[<span data-ttu-id="80e43-141">Elemento WideEntries (Format)</span><span class="sxs-lookup"><span data-stu-id="80e43-141">WideEntries Element (Format)</span></span>](./wideentries-element-for-widecontrol-format.md)

[<span data-ttu-id="80e43-142">Visualizzazione estesa (di base)</span><span class="sxs-lookup"><span data-stu-id="80e43-142">Wide View (Basic)</span></span>](./wide-view-basic.md)

[<span data-ttu-id="80e43-143">Creazione di una visualizzazione estesa</span><span class="sxs-lookup"><span data-stu-id="80e43-143">Creating a Wide View</span></span>](./creating-a-wide-view.md)

[<span data-ttu-id="80e43-144">Scrittura di un file di formattazione di PowerShell</span><span class="sxs-lookup"><span data-stu-id="80e43-144">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
