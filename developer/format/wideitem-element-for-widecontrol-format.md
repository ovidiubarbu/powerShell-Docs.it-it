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
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/03/2019
ms.locfileid: "56862627"
---
# <a name="wideitem-element-for-widecontrol-format"></a><span data-ttu-id="39dc1-102">Elemento WideItem per WideControl (formato)</span><span class="sxs-lookup"><span data-stu-id="39dc1-102">WideItem Element for WideControl (Format)</span></span>

<span data-ttu-id="39dc1-103">Definisce le proprietà il cui valore viene visualizzato lo script.</span><span class="sxs-lookup"><span data-stu-id="39dc1-103">Defines the property or script whose value is displayed.</span></span>

<span data-ttu-id="39dc1-104">Elemento (formato) elemento ViewDefinitions (formato) visualizzazione elemento (formato) elemento WideControl (formato) elemento WideEntries (formato) elemento WideEntry (formato) WideItem elemento di configurazione (formato)</span><span class="sxs-lookup"><span data-stu-id="39dc1-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) WideControl Element (Format) WideEntries Element (Format) WideEntry Element (Format) WideItem Element (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="39dc1-105">Sintassi</span><span class="sxs-lookup"><span data-stu-id="39dc1-105">Syntax</span></span>

```xml
<WideItem>
  <PropertyName>.NetTypeProperty</PropertyName>
  <ScriptBlock>ScriptToExecute</ScriptBlock>
  <FormatString>FormatPattern</FormatString>
</WideItem>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="39dc1-106">Attributi ed elementi</span><span class="sxs-lookup"><span data-stu-id="39dc1-106">Attributes and Elements</span></span>

<span data-ttu-id="39dc1-107">Le sezioni seguenti descrivono gli attributi e gli elementi figlio dell'elemento padre del `WideItem` elemento.</span><span class="sxs-lookup"><span data-stu-id="39dc1-107">The following sections describe the attributes, child elements, and the parent element of the `WideItem` element.</span></span> <span data-ttu-id="39dc1-108">L'elemento `FormatString` è facoltativo.</span><span class="sxs-lookup"><span data-stu-id="39dc1-108">The `FormatString` element is optional.</span></span> <span data-ttu-id="39dc1-109">Tuttavia, è necessario specificare una `PropertyName` o `ScriptBlock` elemento, ma è possibile specificare entrambi.</span><span class="sxs-lookup"><span data-stu-id="39dc1-109">However, you must specify a `PropertyName` or `ScriptBlock` element, but you cannot specify both.</span></span>

### <a name="attributes"></a><span data-ttu-id="39dc1-110">Attributes</span><span class="sxs-lookup"><span data-stu-id="39dc1-110">Attributes</span></span>

<span data-ttu-id="39dc1-111">Nessuna.</span><span class="sxs-lookup"><span data-stu-id="39dc1-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="39dc1-112">Elementi figlio</span><span class="sxs-lookup"><span data-stu-id="39dc1-112">Child Elements</span></span>

|<span data-ttu-id="39dc1-113">Elemento</span><span class="sxs-lookup"><span data-stu-id="39dc1-113">Element</span></span>|<span data-ttu-id="39dc1-114">Description</span><span class="sxs-lookup"><span data-stu-id="39dc1-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="39dc1-115">Elemento FormatString per WideItem per WideControl (formato)</span><span class="sxs-lookup"><span data-stu-id="39dc1-115">FormatString Element for WideItem for WideControl (Format)</span></span>](./formatstring-element-for-wideitem-for-widecontrol-format.md)|<span data-ttu-id="39dc1-116">Elemento facoltativo.</span><span class="sxs-lookup"><span data-stu-id="39dc1-116">Optional element.</span></span><br /><br /> <span data-ttu-id="39dc1-117">Specifica un modello di formato che definisce come viene visualizzato il valore di proprietà o lo script nella visualizzazione.</span><span class="sxs-lookup"><span data-stu-id="39dc1-117">Specifies a format pattern that defines how the property or script value is displayed in the view.</span></span>|
|[<span data-ttu-id="39dc1-118">Elemento PropertyName per WideItem (formato)</span><span class="sxs-lookup"><span data-stu-id="39dc1-118">PropertyName Element for WideItem (Format)</span></span>](./propertyname-element-for-wideitem-for-widecontrol-format.md)|<span data-ttu-id="39dc1-119">Specifica la proprietà dell'oggetto il cui valore viene visualizzato in visualizzazione estesa.</span><span class="sxs-lookup"><span data-stu-id="39dc1-119">Specifies the property of the object whose value is displayed in the wide view.</span></span>|
|[<span data-ttu-id="39dc1-120">Elemento ScriptBlock per WideItem (formato)</span><span class="sxs-lookup"><span data-stu-id="39dc1-120">ScriptBlock Element for WideItem (Format)</span></span>](./scriptblock-element-for-wideitem-for-widecontrol-format.md)|<span data-ttu-id="39dc1-121">Specifica lo script il cui valore viene visualizzato in visualizzazione estesa.</span><span class="sxs-lookup"><span data-stu-id="39dc1-121">Specifies the script whose value is displayed in the wide view.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="39dc1-122">Elementi padre</span><span class="sxs-lookup"><span data-stu-id="39dc1-122">Parent Elements</span></span>

|<span data-ttu-id="39dc1-123">Elemento</span><span class="sxs-lookup"><span data-stu-id="39dc1-123">Element</span></span>|<span data-ttu-id="39dc1-124">Description</span><span class="sxs-lookup"><span data-stu-id="39dc1-124">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="39dc1-125">Elemento WideEntry (formato)</span><span class="sxs-lookup"><span data-stu-id="39dc1-125">WideEntry Element (Format)</span></span>](./wideentry-element-for-widecontrol-format.md)|<span data-ttu-id="39dc1-126">Fornisce una definizione della vista wide.</span><span class="sxs-lookup"><span data-stu-id="39dc1-126">Provides a definition of the wide view.</span></span>|

## <a name="remarks"></a><span data-ttu-id="39dc1-127">Osservazioni</span><span class="sxs-lookup"><span data-stu-id="39dc1-127">Remarks</span></span>

<span data-ttu-id="39dc1-128">Per altre informazioni sui componenti di una visualizzazione più ampia, vedere [visualizzazione estesa](./creating-a-wide-view.md).</span><span class="sxs-lookup"><span data-stu-id="39dc1-128">For more information about the components of a wide view, see [Wide View](./creating-a-wide-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="39dc1-129">Esempio</span><span class="sxs-lookup"><span data-stu-id="39dc1-129">Example</span></span>

<span data-ttu-id="39dc1-130">L'esempio seguente mostra una `WideEntry` che definisce un singolo elemento `WideItem` elemento.</span><span class="sxs-lookup"><span data-stu-id="39dc1-130">The following example shows a `WideEntry` element that defines a single `WideItem` element.</span></span> <span data-ttu-id="39dc1-131">Il `WideItem` elemento definisce le proprietà il cui valore viene visualizzato nella visualizzazione script.</span><span class="sxs-lookup"><span data-stu-id="39dc1-131">The `WideItem` element defines the property or script whose value is displayed in the view.</span></span>

```xml
<WideEntry>
  <WideItem>
    <PropertyName>ProcessName</PropertyName>
  </WideItem>
</WideEntry>
```

<span data-ttu-id="39dc1-132">Per un esempio completo di una visualizzazione più ampia, vedere [visualizzazione più ampia (Basic)](./wide-view-basic.md).</span><span class="sxs-lookup"><span data-stu-id="39dc1-132">For a complete example of a wide view, see [Wide View (Basic)](./wide-view-basic.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="39dc1-133">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="39dc1-133">See Also</span></span>

[<span data-ttu-id="39dc1-134">Elemento FormatString per WideItem per WideControl (formato)</span><span class="sxs-lookup"><span data-stu-id="39dc1-134">FormatString Element for WideItem for WideControl (Format)</span></span>](./formatstring-element-for-wideitem-for-widecontrol-format.md)

[<span data-ttu-id="39dc1-135">Elemento PropertyName per WideItem (formato)</span><span class="sxs-lookup"><span data-stu-id="39dc1-135">PropertyName Element for WideItem (Format)</span></span>](./propertyname-element-for-wideitem-for-widecontrol-format.md)

[<span data-ttu-id="39dc1-136">Elemento ScriptBlock per WideItem (formato)</span><span class="sxs-lookup"><span data-stu-id="39dc1-136">ScriptBlock Element for WideItem (Format)</span></span>](./scriptblock-element-for-wideitem-for-widecontrol-format.md)

[<span data-ttu-id="39dc1-137">Elemento WideEntry (formato)</span><span class="sxs-lookup"><span data-stu-id="39dc1-137">WideEntry Element (Format)</span></span>](./wideentry-element-for-widecontrol-format.md)

[<span data-ttu-id="39dc1-138">La scrittura di un File di formattazione di PowerShell</span><span class="sxs-lookup"><span data-stu-id="39dc1-138">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
