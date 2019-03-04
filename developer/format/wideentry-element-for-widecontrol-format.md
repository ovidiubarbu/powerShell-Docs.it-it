---
title: Elemento WideEntry per WideControl (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 014763cb-7716-4931-899c-8375b5d7a3dd
caps.latest.revision: 15
ms.openlocfilehash: d1d13b5c3436871053353814293d9163ea13c7fb
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/03/2019
ms.locfileid: "56856527"
---
# <a name="wideentry-element-for-widecontrol-format"></a><span data-ttu-id="a27b5-102">Elemento WideEntry per WideControl (formato)</span><span class="sxs-lookup"><span data-stu-id="a27b5-102">WideEntry Element for WideControl (Format)</span></span>

<span data-ttu-id="a27b5-103">Fornisce una definizione della vista wide.</span><span class="sxs-lookup"><span data-stu-id="a27b5-103">Provides a definition of the wide view.</span></span>

<span data-ttu-id="a27b5-104">Elemento (formato) elemento ViewDefinitions (formato) visualizzazione elemento (formato) elemento WideControl (formato) elemento WideEntries (formato) WideEntry elemento di configurazione (formato)</span><span class="sxs-lookup"><span data-stu-id="a27b5-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) WideControl Element (Format) WideEntries Element (Format) WideEntry Element (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="a27b5-105">Sintassi</span><span class="sxs-lookup"><span data-stu-id="a27b5-105">Syntax</span></span>

```xml
<WideEntry>
  <EntrySelectedBy>...</EntrySelectedBy>
  <WideItem>...</WideItem>
</WideEntry>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="a27b5-106">Attributi ed elementi</span><span class="sxs-lookup"><span data-stu-id="a27b5-106">Attributes and Elements</span></span>

<span data-ttu-id="a27b5-107">Le sezioni seguenti descrivono gli attributi e gli elementi figlio dell'elemento padre del `WideEntry` elemento.</span><span class="sxs-lookup"><span data-stu-id="a27b5-107">The following sections describe the attributes, child elements, and the parent element of the `WideEntry` element.</span></span> <span data-ttu-id="a27b5-108">È necessario specificare un singolo `WideItem` elemento figlio.</span><span class="sxs-lookup"><span data-stu-id="a27b5-108">You must specify a single `WideItem` child element.</span></span>

### <a name="attributes"></a><span data-ttu-id="a27b5-109">Attributes</span><span class="sxs-lookup"><span data-stu-id="a27b5-109">Attributes</span></span>

<span data-ttu-id="a27b5-110">Nessuna.</span><span class="sxs-lookup"><span data-stu-id="a27b5-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="a27b5-111">Elementi figlio</span><span class="sxs-lookup"><span data-stu-id="a27b5-111">Child Elements</span></span>

|<span data-ttu-id="a27b5-112">Elemento</span><span class="sxs-lookup"><span data-stu-id="a27b5-112">Element</span></span>|<span data-ttu-id="a27b5-113">Description</span><span class="sxs-lookup"><span data-stu-id="a27b5-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="a27b5-114">Elemento EntrySelectedBy per WideEntry (formato)</span><span class="sxs-lookup"><span data-stu-id="a27b5-114">EntrySelectedBy Element for WideEntry (Format)</span></span>](./entryselectedby-element-for-wideentry-format.md)|<span data-ttu-id="a27b5-115">Elemento facoltativo.</span><span class="sxs-lookup"><span data-stu-id="a27b5-115">Optional element.</span></span><br /><br /> <span data-ttu-id="a27b5-116">Definisce i tipi .NET che usano questa definizione voce ampia o la condizione che deve essere presente per questa definizione da usare.</span><span class="sxs-lookup"><span data-stu-id="a27b5-116">Defines the .NET types that use this wide entry definition or the condition that must exist for this definition to be used.</span></span>|
|[<span data-ttu-id="a27b5-117">Elemento WideItem (formato)</span><span class="sxs-lookup"><span data-stu-id="a27b5-117">WideItem Element (Format)</span></span>](./wideitem-element-for-widecontrol-format.md)|<span data-ttu-id="a27b5-118">Elemento obbligatorio.</span><span class="sxs-lookup"><span data-stu-id="a27b5-118">Required element.</span></span><br /><br /> <span data-ttu-id="a27b5-119">Definisce le proprietà il cui valore viene visualizzato lo script.</span><span class="sxs-lookup"><span data-stu-id="a27b5-119">Defines the property or script whose value is displayed.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="a27b5-120">Elementi padre</span><span class="sxs-lookup"><span data-stu-id="a27b5-120">Parent Elements</span></span>

|<span data-ttu-id="a27b5-121">Elemento</span><span class="sxs-lookup"><span data-stu-id="a27b5-121">Element</span></span>|<span data-ttu-id="a27b5-122">Description</span><span class="sxs-lookup"><span data-stu-id="a27b5-122">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="a27b5-123">Elemento WideEntries (formato)</span><span class="sxs-lookup"><span data-stu-id="a27b5-123">WideEntries Element (Format)</span></span>](./wideentries-element-for-widecontrol-format.md)|<span data-ttu-id="a27b5-124">Fornisce le definizioni di visualizzazione estesa.</span><span class="sxs-lookup"><span data-stu-id="a27b5-124">Provides the definitions of the wide view.</span></span>|

## <a name="remarks"></a><span data-ttu-id="a27b5-125">Osservazioni</span><span class="sxs-lookup"><span data-stu-id="a27b5-125">Remarks</span></span>

<span data-ttu-id="a27b5-126">Una visualizzazione più ampia è un formato di elenco che viene visualizzato un singolo valore di proprietà o script per ogni oggetto.</span><span class="sxs-lookup"><span data-stu-id="a27b5-126">A wide view is a list format that displays a single property value or script value for each object.</span></span> <span data-ttu-id="a27b5-127">A differenza di altri tipi di visualizzazioni, è possibile specificare un solo elemento per ogni definizione della vista.</span><span class="sxs-lookup"><span data-stu-id="a27b5-127">Unlike other types of views, you can specify only one item element for each view definition.</span></span> <span data-ttu-id="a27b5-128">Per altre informazioni su altri componenti di una visualizzazione più ampia, vedere [creazione di una visualizzazione più ampia](./creating-a-wide-view.md).</span><span class="sxs-lookup"><span data-stu-id="a27b5-128">For more information about the other components of a wide view, see [Creating a Wide View](./creating-a-wide-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="a27b5-129">Esempio</span><span class="sxs-lookup"><span data-stu-id="a27b5-129">Example</span></span>

<span data-ttu-id="a27b5-130">L'esempio seguente mostra una `WideEntry` che definisce un singolo elemento `WideItem` elemento.</span><span class="sxs-lookup"><span data-stu-id="a27b5-130">The following example shows a `WideEntry` element that defines a single `WideItem` element.</span></span> <span data-ttu-id="a27b5-131">Il `WideItem` elemento definisce le proprietà il cui valore viene visualizzato nella vista.</span><span class="sxs-lookup"><span data-stu-id="a27b5-131">The `WideItem` element defines the property whose value is displayed in the view.</span></span>

```xml
<WideEntries>
  <WideEntry>
    <WideItem>
      <PropertyName>ProcessName</PropertyName>
    </WideItem>
  </WideEntry>
</WideEntries>

```

<span data-ttu-id="a27b5-132">Per un esempio completo di una visualizzazione più ampia, vedere [visualizzazione più ampia (Basic)](./wide-view-basic.md).</span><span class="sxs-lookup"><span data-stu-id="a27b5-132">For a complete example of a wide view, see [Wide View (Basic)](./wide-view-basic.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="a27b5-133">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="a27b5-133">See Also</span></span>

[<span data-ttu-id="a27b5-134">Creazione di una visualizzazione più ampia</span><span class="sxs-lookup"><span data-stu-id="a27b5-134">Creating a Wide View</span></span>](./creating-a-wide-view.md)

[<span data-ttu-id="a27b5-135">Elemento SelectionCondition per WideEntry (formato)</span><span class="sxs-lookup"><span data-stu-id="a27b5-135">SelectionCondition Element for WideEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-widecontrol-format.md)

[<span data-ttu-id="a27b5-136">Elemento SelectionSetName per WideEntry (formato)</span><span class="sxs-lookup"><span data-stu-id="a27b5-136">SelectionSetName Element for WideEntry (Format)</span></span>](./selectionsetname-element-for-entryselectedby-for-widecontrol-format.md)

[<span data-ttu-id="a27b5-137">Elemento TypeName per WideEntry (formato)</span><span class="sxs-lookup"><span data-stu-id="a27b5-137">TypeName Element for WideEntry (Format)</span></span>](./typename-element-for-entryselectedby-for-wideentry-format.md)

[<span data-ttu-id="a27b5-138">Elemento WideEntries (formato)</span><span class="sxs-lookup"><span data-stu-id="a27b5-138">WideEntries Element (Format)</span></span>](./wideentries-element-for-widecontrol-format.md)

[<span data-ttu-id="a27b5-139">Elemento WideItem (formato)</span><span class="sxs-lookup"><span data-stu-id="a27b5-139">WideItem Element (Format)</span></span>](./wideitem-element-for-widecontrol-format.md)

[<span data-ttu-id="a27b5-140">La scrittura di un File di formattazione di PowerShell</span><span class="sxs-lookup"><span data-stu-id="a27b5-140">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
