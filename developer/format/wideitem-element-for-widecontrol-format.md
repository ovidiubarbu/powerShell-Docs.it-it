---
title: Elemento WideItem per WideControl (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 17352fc4-ba83-4f04-86bc-f591765d85a8
caps.latest.revision: 18
ms.openlocfilehash: fa9eda3ea1028c27dbfb3eb04747af3b817c1a81
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62083638"
---
# <a name="wideitem-element-for-widecontrol-format"></a><span data-ttu-id="e72ec-102">Elemento WideItem per WideControl (formato)</span><span class="sxs-lookup"><span data-stu-id="e72ec-102">WideItem Element for WideControl (Format)</span></span>

<span data-ttu-id="e72ec-103">Definisce le proprietà il cui valore viene visualizzato lo script.</span><span class="sxs-lookup"><span data-stu-id="e72ec-103">Defines the property or script whose value is displayed.</span></span>

<span data-ttu-id="e72ec-104">Elemento (formato) elemento ViewDefinitions (formato) visualizzazione elemento (formato) elemento WideControl (formato) elemento WideEntries (formato) elemento WideEntry (formato) WideItem elemento di configurazione (formato)</span><span class="sxs-lookup"><span data-stu-id="e72ec-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) WideControl Element (Format) WideEntries Element (Format) WideEntry Element (Format) WideItem Element (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="e72ec-105">Sintassi</span><span class="sxs-lookup"><span data-stu-id="e72ec-105">Syntax</span></span>

```xml
<WideItem>
  <PropertyName>.NetTypeProperty</PropertyName>
  <ScriptBlock>ScriptToExecute</ScriptBlock>
  <FormatString>FormatPattern</FormatString>
</WideItem>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="e72ec-106">Elementi e attributi</span><span class="sxs-lookup"><span data-stu-id="e72ec-106">Attributes and Elements</span></span>

<span data-ttu-id="e72ec-107">Le sezioni seguenti descrivono gli attributi e gli elementi figlio dell'elemento padre del `WideItem` elemento.</span><span class="sxs-lookup"><span data-stu-id="e72ec-107">The following sections describe the attributes, child elements, and the parent element of the `WideItem` element.</span></span> <span data-ttu-id="e72ec-108">Il `FormatString` elemento è facoltativo.</span><span class="sxs-lookup"><span data-stu-id="e72ec-108">The `FormatString` element is optional.</span></span> <span data-ttu-id="e72ec-109">Tuttavia, è necessario specificare una `PropertyName` o `ScriptBlock` elemento, ma è possibile specificare entrambi.</span><span class="sxs-lookup"><span data-stu-id="e72ec-109">However, you must specify a `PropertyName` or `ScriptBlock` element, but you cannot specify both.</span></span>

### <a name="attributes"></a><span data-ttu-id="e72ec-110">Attributes</span><span class="sxs-lookup"><span data-stu-id="e72ec-110">Attributes</span></span>

<span data-ttu-id="e72ec-111">Nessuna.</span><span class="sxs-lookup"><span data-stu-id="e72ec-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="e72ec-112">Elementi figlio</span><span class="sxs-lookup"><span data-stu-id="e72ec-112">Child Elements</span></span>

|<span data-ttu-id="e72ec-113">Elemento</span><span class="sxs-lookup"><span data-stu-id="e72ec-113">Element</span></span>|<span data-ttu-id="e72ec-114">Description</span><span class="sxs-lookup"><span data-stu-id="e72ec-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="e72ec-115">Elemento FormatString per WideItem per WideControl (formato)</span><span class="sxs-lookup"><span data-stu-id="e72ec-115">FormatString Element for WideItem for WideControl (Format)</span></span>](./formatstring-element-for-wideitem-for-widecontrol-format.md)|<span data-ttu-id="e72ec-116">Elemento facoltativo.</span><span class="sxs-lookup"><span data-stu-id="e72ec-116">Optional element.</span></span><br /><br /> <span data-ttu-id="e72ec-117">Specifica un modello di formato che definisce come viene visualizzato il valore di proprietà o lo script nella visualizzazione.</span><span class="sxs-lookup"><span data-stu-id="e72ec-117">Specifies a format pattern that defines how the property or script value is displayed in the view.</span></span>|
|[<span data-ttu-id="e72ec-118">Elemento PropertyName per WideItem (formato)</span><span class="sxs-lookup"><span data-stu-id="e72ec-118">PropertyName Element for WideItem (Format)</span></span>](./propertyname-element-for-wideitem-for-widecontrol-format.md)|<span data-ttu-id="e72ec-119">Specifica la proprietà dell'oggetto il cui valore viene visualizzato in visualizzazione estesa.</span><span class="sxs-lookup"><span data-stu-id="e72ec-119">Specifies the property of the object whose value is displayed in the wide view.</span></span>|
|[<span data-ttu-id="e72ec-120">Elemento ScriptBlock per WideItem (formato)</span><span class="sxs-lookup"><span data-stu-id="e72ec-120">ScriptBlock Element for WideItem (Format)</span></span>](./scriptblock-element-for-wideitem-for-widecontrol-format.md)|<span data-ttu-id="e72ec-121">Specifica lo script il cui valore viene visualizzato in visualizzazione estesa.</span><span class="sxs-lookup"><span data-stu-id="e72ec-121">Specifies the script whose value is displayed in the wide view.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="e72ec-122">Elementi padre</span><span class="sxs-lookup"><span data-stu-id="e72ec-122">Parent Elements</span></span>

|<span data-ttu-id="e72ec-123">Elemento</span><span class="sxs-lookup"><span data-stu-id="e72ec-123">Element</span></span>|<span data-ttu-id="e72ec-124">Description</span><span class="sxs-lookup"><span data-stu-id="e72ec-124">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="e72ec-125">Elemento WideEntry (formato)</span><span class="sxs-lookup"><span data-stu-id="e72ec-125">WideEntry Element (Format)</span></span>](./wideentry-element-for-widecontrol-format.md)|<span data-ttu-id="e72ec-126">Fornisce una definizione della vista wide.</span><span class="sxs-lookup"><span data-stu-id="e72ec-126">Provides a definition of the wide view.</span></span>|

## <a name="remarks"></a><span data-ttu-id="e72ec-127">Osservazioni</span><span class="sxs-lookup"><span data-stu-id="e72ec-127">Remarks</span></span>

<span data-ttu-id="e72ec-128">Per altre informazioni sui componenti di una visualizzazione più ampia, vedere [visualizzazione estesa](./creating-a-wide-view.md).</span><span class="sxs-lookup"><span data-stu-id="e72ec-128">For more information about the components of a wide view, see [Wide View](./creating-a-wide-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="e72ec-129">Esempio</span><span class="sxs-lookup"><span data-stu-id="e72ec-129">Example</span></span>

<span data-ttu-id="e72ec-130">L'esempio seguente mostra una `WideEntry` che definisce un singolo elemento `WideItem` elemento.</span><span class="sxs-lookup"><span data-stu-id="e72ec-130">The following example shows a `WideEntry` element that defines a single `WideItem` element.</span></span> <span data-ttu-id="e72ec-131">Il `WideItem` elemento definisce le proprietà il cui valore viene visualizzato nella visualizzazione script.</span><span class="sxs-lookup"><span data-stu-id="e72ec-131">The `WideItem` element defines the property or script whose value is displayed in the view.</span></span>

```xml
<WideEntry>
  <WideItem>
    <PropertyName>ProcessName</PropertyName>
  </WideItem>
</WideEntry>
```

<span data-ttu-id="e72ec-132">Per un esempio completo di una visualizzazione più ampia, vedere [visualizzazione più ampia (Basic)](./wide-view-basic.md).</span><span class="sxs-lookup"><span data-stu-id="e72ec-132">For a complete example of a wide view, see [Wide View (Basic)](./wide-view-basic.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="e72ec-133">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="e72ec-133">See Also</span></span>

[<span data-ttu-id="e72ec-134">Elemento FormatString per WideItem per WideControl (formato)</span><span class="sxs-lookup"><span data-stu-id="e72ec-134">FormatString Element for WideItem for WideControl (Format)</span></span>](./formatstring-element-for-wideitem-for-widecontrol-format.md)

[<span data-ttu-id="e72ec-135">Elemento PropertyName per WideItem (formato)</span><span class="sxs-lookup"><span data-stu-id="e72ec-135">PropertyName Element for WideItem (Format)</span></span>](./propertyname-element-for-wideitem-for-widecontrol-format.md)

[<span data-ttu-id="e72ec-136">Elemento ScriptBlock per WideItem (formato)</span><span class="sxs-lookup"><span data-stu-id="e72ec-136">ScriptBlock Element for WideItem (Format)</span></span>](./scriptblock-element-for-wideitem-for-widecontrol-format.md)

[<span data-ttu-id="e72ec-137">Elemento WideEntry (formato)</span><span class="sxs-lookup"><span data-stu-id="e72ec-137">WideEntry Element (Format)</span></span>](./wideentry-element-for-widecontrol-format.md)

[<span data-ttu-id="e72ec-138">La scrittura di un File di formattazione di PowerShell</span><span class="sxs-lookup"><span data-stu-id="e72ec-138">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
