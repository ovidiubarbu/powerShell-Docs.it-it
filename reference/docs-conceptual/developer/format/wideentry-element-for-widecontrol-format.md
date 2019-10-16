---
title: Elemento WideEntry per WideControl (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 014763cb-7716-4931-899c-8375b5d7a3dd
caps.latest.revision: 15
ms.openlocfilehash: d1d13b5c3436871053353814293d9163ea13c7fb
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/15/2019
ms.locfileid: "72367900"
---
# <a name="wideentry-element-for-widecontrol-format"></a><span data-ttu-id="f6869-102">Elemento WideEntry per WideControl (formato)</span><span class="sxs-lookup"><span data-stu-id="f6869-102">WideEntry Element for WideControl (Format)</span></span>

<span data-ttu-id="f6869-103">Fornisce una definizione dell'ampia visualizzazione.</span><span class="sxs-lookup"><span data-stu-id="f6869-103">Provides a definition of the wide view.</span></span>

<span data-ttu-id="f6869-104">Elemento Configuration (Format) elemento ViewDefinitions (Format) elemento View (Format) elemento WideControl (Format) elemento WideEntries (Format) elemento WideEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="f6869-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) WideControl Element (Format) WideEntries Element (Format) WideEntry Element (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="f6869-105">Sintassi</span><span class="sxs-lookup"><span data-stu-id="f6869-105">Syntax</span></span>

```xml
<WideEntry>
  <EntrySelectedBy>...</EntrySelectedBy>
  <WideItem>...</WideItem>
</WideEntry>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="f6869-106">Attributi ed elementi</span><span class="sxs-lookup"><span data-stu-id="f6869-106">Attributes and Elements</span></span>

<span data-ttu-id="f6869-107">Nelle sezioni seguenti vengono descritti gli attributi, gli elementi figlio e l'elemento padre dell'elemento `WideEntry`.</span><span class="sxs-lookup"><span data-stu-id="f6869-107">The following sections describe the attributes, child elements, and the parent element of the `WideEntry` element.</span></span> <span data-ttu-id="f6869-108">È necessario specificare un singolo elemento figlio `WideItem`.</span><span class="sxs-lookup"><span data-stu-id="f6869-108">You must specify a single `WideItem` child element.</span></span>

### <a name="attributes"></a><span data-ttu-id="f6869-109">Attributi</span><span class="sxs-lookup"><span data-stu-id="f6869-109">Attributes</span></span>

<span data-ttu-id="f6869-110">Nessuna.</span><span class="sxs-lookup"><span data-stu-id="f6869-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="f6869-111">Elementi figlio</span><span class="sxs-lookup"><span data-stu-id="f6869-111">Child Elements</span></span>

|<span data-ttu-id="f6869-112">Elemento</span><span class="sxs-lookup"><span data-stu-id="f6869-112">Element</span></span>|<span data-ttu-id="f6869-113">Description</span><span class="sxs-lookup"><span data-stu-id="f6869-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="f6869-114">Elemento EntrySelectedBy per WideEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="f6869-114">EntrySelectedBy Element for WideEntry (Format)</span></span>](./entryselectedby-element-for-wideentry-format.md)|<span data-ttu-id="f6869-115">Elemento facoltativo.</span><span class="sxs-lookup"><span data-stu-id="f6869-115">Optional element.</span></span><br /><br /> <span data-ttu-id="f6869-116">Definisce i tipi .NET che utilizzano questa definizione di voce estesa o la condizione che deve esistere affinché questa definizione venga utilizzata.</span><span class="sxs-lookup"><span data-stu-id="f6869-116">Defines the .NET types that use this wide entry definition or the condition that must exist for this definition to be used.</span></span>|
|[<span data-ttu-id="f6869-117">Elemento WideItem (Format)</span><span class="sxs-lookup"><span data-stu-id="f6869-117">WideItem Element (Format)</span></span>](./wideitem-element-for-widecontrol-format.md)|<span data-ttu-id="f6869-118">Elemento obbligatorio.</span><span class="sxs-lookup"><span data-stu-id="f6869-118">Required element.</span></span><br /><br /> <span data-ttu-id="f6869-119">Definisce la proprietà o lo script di cui viene visualizzato il valore.</span><span class="sxs-lookup"><span data-stu-id="f6869-119">Defines the property or script whose value is displayed.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="f6869-120">Elementi padre</span><span class="sxs-lookup"><span data-stu-id="f6869-120">Parent Elements</span></span>

|<span data-ttu-id="f6869-121">Elemento</span><span class="sxs-lookup"><span data-stu-id="f6869-121">Element</span></span>|<span data-ttu-id="f6869-122">Description</span><span class="sxs-lookup"><span data-stu-id="f6869-122">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="f6869-123">Elemento WideEntries (Format)</span><span class="sxs-lookup"><span data-stu-id="f6869-123">WideEntries Element (Format)</span></span>](./wideentries-element-for-widecontrol-format.md)|<span data-ttu-id="f6869-124">Fornisce le definizioni della visualizzazione estesa.</span><span class="sxs-lookup"><span data-stu-id="f6869-124">Provides the definitions of the wide view.</span></span>|

## <a name="remarks"></a><span data-ttu-id="f6869-125">Osservazioni</span><span class="sxs-lookup"><span data-stu-id="f6869-125">Remarks</span></span>

<span data-ttu-id="f6869-126">Una visualizzazione estesa è un formato di elenco che consente di visualizzare un singolo valore di proprietà o un valore di script per ogni oggetto.</span><span class="sxs-lookup"><span data-stu-id="f6869-126">A wide view is a list format that displays a single property value or script value for each object.</span></span> <span data-ttu-id="f6869-127">Diversamente da altri tipi di viste, è possibile specificare un solo elemento Item per ogni definizione della vista.</span><span class="sxs-lookup"><span data-stu-id="f6869-127">Unlike other types of views, you can specify only one item element for each view definition.</span></span> <span data-ttu-id="f6869-128">Per ulteriori informazioni sugli altri componenti di una visualizzazione estesa, vedere [creazione di un'ampia visualizzazione](./creating-a-wide-view.md).</span><span class="sxs-lookup"><span data-stu-id="f6869-128">For more information about the other components of a wide view, see [Creating a Wide View](./creating-a-wide-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="f6869-129">Esempio</span><span class="sxs-lookup"><span data-stu-id="f6869-129">Example</span></span>

<span data-ttu-id="f6869-130">Nell'esempio seguente viene illustrato un elemento `WideEntry` che definisce un singolo elemento `WideItem`.</span><span class="sxs-lookup"><span data-stu-id="f6869-130">The following example shows a `WideEntry` element that defines a single `WideItem` element.</span></span> <span data-ttu-id="f6869-131">L'elemento `WideItem` definisce la proprietà il cui valore viene visualizzato nella visualizzazione.</span><span class="sxs-lookup"><span data-stu-id="f6869-131">The `WideItem` element defines the property whose value is displayed in the view.</span></span>

```xml
<WideEntries>
  <WideEntry>
    <WideItem>
      <PropertyName>ProcessName</PropertyName>
    </WideItem>
  </WideEntry>
</WideEntries>

```

<span data-ttu-id="f6869-132">Per un esempio completo di una visualizzazione estesa, vedere [Wide View (Basic)](./wide-view-basic.md).</span><span class="sxs-lookup"><span data-stu-id="f6869-132">For a complete example of a wide view, see [Wide View (Basic)](./wide-view-basic.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="f6869-133">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="f6869-133">See Also</span></span>

[<span data-ttu-id="f6869-134">Creazione di una visualizzazione estesa</span><span class="sxs-lookup"><span data-stu-id="f6869-134">Creating a Wide View</span></span>](./creating-a-wide-view.md)

[<span data-ttu-id="f6869-135">Elemento SelectionCondition per WideEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="f6869-135">SelectionCondition Element for WideEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-widecontrol-format.md)

[<span data-ttu-id="f6869-136">Elemento SelectionSetName per WideEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="f6869-136">SelectionSetName Element for WideEntry (Format)</span></span>](./selectionsetname-element-for-entryselectedby-for-widecontrol-format.md)

[<span data-ttu-id="f6869-137">Elemento TypeName per WideEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="f6869-137">TypeName Element for WideEntry (Format)</span></span>](./typename-element-for-entryselectedby-for-wideentry-format.md)

[<span data-ttu-id="f6869-138">Elemento WideEntries (Format)</span><span class="sxs-lookup"><span data-stu-id="f6869-138">WideEntries Element (Format)</span></span>](./wideentries-element-for-widecontrol-format.md)

[<span data-ttu-id="f6869-139">Elemento WideItem (Format)</span><span class="sxs-lookup"><span data-stu-id="f6869-139">WideItem Element (Format)</span></span>](./wideitem-element-for-widecontrol-format.md)

[<span data-ttu-id="f6869-140">Scrittura di un file di formattazione di PowerShell</span><span class="sxs-lookup"><span data-stu-id="f6869-140">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
