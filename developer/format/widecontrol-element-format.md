---
title: Elemento WideControl (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 715ea055-037b-46ad-b70f-87b3f5134403
caps.latest.revision: 14
ms.openlocfilehash: 2742be0389a1bf04af100a490a59c0d938165811
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/03/2019
ms.locfileid: "56859827"
---
# <a name="widecontrol-element-format"></a><span data-ttu-id="d83c7-102">Elemento WideControl (formato)</span><span class="sxs-lookup"><span data-stu-id="d83c7-102">WideControl Element (Format)</span></span>

<span data-ttu-id="d83c7-103">Definisce un'ampia (valore singolo) formato di elenco per la visualizzazione.</span><span class="sxs-lookup"><span data-stu-id="d83c7-103">Defines a wide (single value) list format for the view.</span></span> <span data-ttu-id="d83c7-104">Questa vista sono riportati un singolo valore di proprietà o valore di uno script per ogni oggetto.</span><span class="sxs-lookup"><span data-stu-id="d83c7-104">This view displays a single property value or script value for each object.</span></span>

<span data-ttu-id="d83c7-105">Configurazione (formato) elemento ViewDefinitions (formato) visualizzazione elemento (formato) WideControl elemento (formato)</span><span class="sxs-lookup"><span data-stu-id="d83c7-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) WideControl Element (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="d83c7-106">Sintassi</span><span class="sxs-lookup"><span data-stu-id="d83c7-106">Syntax</span></span>

```xml
<WideControl>
  <AutoSize/>
  <ColumnNumber>PositiveInteger</ColumnNumber>
  <WideEntries>...</WideEntries>
</WideControl>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="d83c7-107">Attributi ed elementi</span><span class="sxs-lookup"><span data-stu-id="d83c7-107">Attributes and Elements</span></span>

<span data-ttu-id="d83c7-108">Le sezioni seguenti descrivono gli attributi, elementi figlio ed elemento padre dell'elemento di `WideControl` elemento.</span><span class="sxs-lookup"><span data-stu-id="d83c7-108">The following sections describe the attributes, child elements, and parent element of the `WideControl` element.</span></span> <span data-ttu-id="d83c7-109">Non è possibile specificare il `AutoSize` e `ColumnNumber` elementi nello stesso momento.</span><span class="sxs-lookup"><span data-stu-id="d83c7-109">You cannot specify the `AutoSize` and `ColumnNumber` elements at the same time.</span></span>

### <a name="attributes"></a><span data-ttu-id="d83c7-110">Attributes</span><span class="sxs-lookup"><span data-stu-id="d83c7-110">Attributes</span></span>

<span data-ttu-id="d83c7-111">Nessuna.</span><span class="sxs-lookup"><span data-stu-id="d83c7-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="d83c7-112">Elementi figlio</span><span class="sxs-lookup"><span data-stu-id="d83c7-112">Child Elements</span></span>

|<span data-ttu-id="d83c7-113">Elemento</span><span class="sxs-lookup"><span data-stu-id="d83c7-113">Element</span></span>|<span data-ttu-id="d83c7-114">Description</span><span class="sxs-lookup"><span data-stu-id="d83c7-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="d83c7-115">AutoSize (elemento) per WideControl (formato)</span><span class="sxs-lookup"><span data-stu-id="d83c7-115">AutoSize Element for WideControl (Format)</span></span>](./autosize-element-for-widecontrol-format.md)|<span data-ttu-id="d83c7-116">Elemento facoltativo.</span><span class="sxs-lookup"><span data-stu-id="d83c7-116">Optional element.</span></span><br /><br /> <span data-ttu-id="d83c7-117">Specifica se la dimensione della colonna e il numero di colonne vengono adattate in base alla dimensione dei dati.</span><span class="sxs-lookup"><span data-stu-id="d83c7-117">Specifies whether the column size and the number of columns are adjusted based on the size of the data.</span></span>|
|[<span data-ttu-id="d83c7-118">Elemento ColumnNumber per WideControl (formato)</span><span class="sxs-lookup"><span data-stu-id="d83c7-118">ColumnNumber Element for WideControl (Format)</span></span>](./columnnumber-element-for-widecontrol-format.md)|<span data-ttu-id="d83c7-119">Elemento facoltativo.</span><span class="sxs-lookup"><span data-stu-id="d83c7-119">Optional element.</span></span><br /><br /> <span data-ttu-id="d83c7-120">Specifica il numero di colonne visualizzate in visualizzazione estesa.</span><span class="sxs-lookup"><span data-stu-id="d83c7-120">Specifies the number of columns displayed in the wide view.</span></span>|
|[<span data-ttu-id="d83c7-121">Elemento WideEntries (formato)</span><span class="sxs-lookup"><span data-stu-id="d83c7-121">WideEntries Element (Format)</span></span>](./wideentries-element-for-widecontrol-format.md)|<span data-ttu-id="d83c7-122">Elemento obbligatorio.</span><span class="sxs-lookup"><span data-stu-id="d83c7-122">Required element.</span></span><br /><br /> <span data-ttu-id="d83c7-123">Fornisce le definizioni di visualizzazione estesa.</span><span class="sxs-lookup"><span data-stu-id="d83c7-123">Provides the definitions of the wide view.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="d83c7-124">Elementi padre</span><span class="sxs-lookup"><span data-stu-id="d83c7-124">Parent Elements</span></span>

|<span data-ttu-id="d83c7-125">Elemento</span><span class="sxs-lookup"><span data-stu-id="d83c7-125">Element</span></span>|<span data-ttu-id="d83c7-126">Description</span><span class="sxs-lookup"><span data-stu-id="d83c7-126">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="d83c7-127">Elemento di visualizzazione (formato)</span><span class="sxs-lookup"><span data-stu-id="d83c7-127">View Element (Format)</span></span>](./view-element-format.md)|<span data-ttu-id="d83c7-128">Definisce una vista che consente di visualizzare uno o più oggetti .NET.</span><span class="sxs-lookup"><span data-stu-id="d83c7-128">Defines a view that is used to display one or more .NET objects.</span></span>|

## <a name="remarks"></a><span data-ttu-id="d83c7-129">Osservazioni</span><span class="sxs-lookup"><span data-stu-id="d83c7-129">Remarks</span></span>

<span data-ttu-id="d83c7-130">Quando si definisce una visualizzazione più ampia, è possibile aggiungere il `AutoSize` elemento o `ColumnNumber` ma non è possibile aggiungere.</span><span class="sxs-lookup"><span data-stu-id="d83c7-130">When defining a wide view, you can add the `AutoSize` element or the `ColumnNumber` but you cannot add both.</span></span>

<span data-ttu-id="d83c7-131">Nella maggior parte dei casi, è necessaria per ogni visualizzazione estesa una sola definizione, ma è possibile avere più definizioni, se si desidera utilizzare la stessa vista per visualizzare diversi oggetti .NET.</span><span class="sxs-lookup"><span data-stu-id="d83c7-131">In most cases, only one definition is required for each wide view, but it is possible to have multiple definitions if you want to use the same view to display different .NET objects.</span></span> <span data-ttu-id="d83c7-132">In questi casi, è possibile fornire una definizione separata per ogni oggetto o un set di oggetti.</span><span class="sxs-lookup"><span data-stu-id="d83c7-132">In those cases, you can provide a separate definition for each object or set of objects.</span></span>

<span data-ttu-id="d83c7-133">Per altre informazioni sui componenti di una visualizzazione più ampia, vedere [ampia i componenti di visualizzazione](./creating-a-wide-view.md).</span><span class="sxs-lookup"><span data-stu-id="d83c7-133">For more information about the components of a wide view, see [Wide View Components](./creating-a-wide-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="d83c7-134">Esempio</span><span class="sxs-lookup"><span data-stu-id="d83c7-134">Example</span></span>

<span data-ttu-id="d83c7-135">L'esempio seguente mostra una `WideControl` elemento utilizzato per visualizzare una proprietà del [Diagnostics](/dotnet/api/System.Diagnostics.Process) oggetto.</span><span class="sxs-lookup"><span data-stu-id="d83c7-135">The following example shows a `WideControl` element that is used to display a property of the [System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process) object.</span></span>

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

<span data-ttu-id="d83c7-136">Per un esempio completo di una visualizzazione più ampia, vedere [visualizzazione più ampia (Basic)](./wide-view-basic.md).</span><span class="sxs-lookup"><span data-stu-id="d83c7-136">For a complete example of a wide view, see [Wide View (Basic)](./wide-view-basic.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="d83c7-137">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="d83c7-137">See Also</span></span>

[<span data-ttu-id="d83c7-138">AutoSize (elemento) per WideControl (formato)</span><span class="sxs-lookup"><span data-stu-id="d83c7-138">Autosize Element for WideControl (Format)</span></span>](./autosize-element-for-widecontrol-format.md)

[<span data-ttu-id="d83c7-139">Elemento ColumnNumber per WideControl (formato)</span><span class="sxs-lookup"><span data-stu-id="d83c7-139">ColumnNumber Element for WideControl (Format)</span></span>](./columnnumber-element-for-widecontrol-format.md)

[<span data-ttu-id="d83c7-140">Elemento di visualizzazione (formato)</span><span class="sxs-lookup"><span data-stu-id="d83c7-140">View Element (Format)</span></span>](./view-element-format.md)

[<span data-ttu-id="d83c7-141">Elemento WideEntries (formato)</span><span class="sxs-lookup"><span data-stu-id="d83c7-141">WideEntries Element (Format)</span></span>](./wideentries-element-for-widecontrol-format.md)

[<span data-ttu-id="d83c7-142">Visualizzazione più ampia (Basic)</span><span class="sxs-lookup"><span data-stu-id="d83c7-142">Wide View (Basic)</span></span>](./wide-view-basic.md)

[<span data-ttu-id="d83c7-143">Creazione di una visualizzazione più ampia</span><span class="sxs-lookup"><span data-stu-id="d83c7-143">Creating a Wide View</span></span>](./creating-a-wide-view.md)

[<span data-ttu-id="d83c7-144">La scrittura di un File di formattazione di PowerShell</span><span class="sxs-lookup"><span data-stu-id="d83c7-144">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
