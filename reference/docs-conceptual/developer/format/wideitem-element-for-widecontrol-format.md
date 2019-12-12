---
title: Elemento WideItem per WideControl (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 17352fc4-ba83-4f04-86bc-f591765d85a8
caps.latest.revision: 18
ms.openlocfilehash: fa9eda3ea1028c27dbfb3eb04747af3b817c1a81
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/05/2019
ms.locfileid: "72361400"
---
# <a name="wideitem-element-for-widecontrol-format"></a><span data-ttu-id="cf053-102">Elemento WideItem per WideControl (formato)</span><span class="sxs-lookup"><span data-stu-id="cf053-102">WideItem Element for WideControl (Format)</span></span>

<span data-ttu-id="cf053-103">Definisce la proprietà o lo script di cui viene visualizzato il valore.</span><span class="sxs-lookup"><span data-stu-id="cf053-103">Defines the property or script whose value is displayed.</span></span>

<span data-ttu-id="cf053-104">Elemento Configuration (Format) elemento ViewDefinitions (Format) elemento View (Format) elemento WideControl (Format) elemento WideEntries (Format) elemento WideEntry (Format) elemento WideItem (Format)</span><span class="sxs-lookup"><span data-stu-id="cf053-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) WideControl Element (Format) WideEntries Element (Format) WideEntry Element (Format) WideItem Element (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="cf053-105">Sintassi</span><span class="sxs-lookup"><span data-stu-id="cf053-105">Syntax</span></span>

```xml
<WideItem>
  <PropertyName>.NetTypeProperty</PropertyName>
  <ScriptBlock>ScriptToExecute</ScriptBlock>
  <FormatString>FormatPattern</FormatString>
</WideItem>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="cf053-106">Attributi ed elementi</span><span class="sxs-lookup"><span data-stu-id="cf053-106">Attributes and Elements</span></span>

<span data-ttu-id="cf053-107">Nelle sezioni seguenti vengono descritti gli attributi, gli elementi figlio e l'elemento padre dell'elemento `WideItem`.</span><span class="sxs-lookup"><span data-stu-id="cf053-107">The following sections describe the attributes, child elements, and the parent element of the `WideItem` element.</span></span> <span data-ttu-id="cf053-108">L'elemento `FormatString` è facoltativo.</span><span class="sxs-lookup"><span data-stu-id="cf053-108">The `FormatString` element is optional.</span></span> <span data-ttu-id="cf053-109">Tuttavia, è necessario specificare un elemento `PropertyName` o `ScriptBlock`, ma non è possibile specificare entrambi.</span><span class="sxs-lookup"><span data-stu-id="cf053-109">However, you must specify a `PropertyName` or `ScriptBlock` element, but you cannot specify both.</span></span>

### <a name="attributes"></a><span data-ttu-id="cf053-110">Attributi</span><span class="sxs-lookup"><span data-stu-id="cf053-110">Attributes</span></span>

<span data-ttu-id="cf053-111">Nessuna.</span><span class="sxs-lookup"><span data-stu-id="cf053-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="cf053-112">Elementi figlio</span><span class="sxs-lookup"><span data-stu-id="cf053-112">Child Elements</span></span>

|<span data-ttu-id="cf053-113">Elemento</span><span class="sxs-lookup"><span data-stu-id="cf053-113">Element</span></span>|<span data-ttu-id="cf053-114">Description</span><span class="sxs-lookup"><span data-stu-id="cf053-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="cf053-115">Elemento FormatString per WideItem per WideControl (Format)</span><span class="sxs-lookup"><span data-stu-id="cf053-115">FormatString Element for WideItem for WideControl (Format)</span></span>](./formatstring-element-for-wideitem-for-widecontrol-format.md)|<span data-ttu-id="cf053-116">Elemento facoltativo.</span><span class="sxs-lookup"><span data-stu-id="cf053-116">Optional element.</span></span><br /><br /> <span data-ttu-id="cf053-117">Specifica un modello di formato che definisce come viene visualizzato il valore della proprietà o dello script nella visualizzazione.</span><span class="sxs-lookup"><span data-stu-id="cf053-117">Specifies a format pattern that defines how the property or script value is displayed in the view.</span></span>|
|[<span data-ttu-id="cf053-118">Elemento PropertyName per WideItem (Format)</span><span class="sxs-lookup"><span data-stu-id="cf053-118">PropertyName Element for WideItem (Format)</span></span>](./propertyname-element-for-wideitem-for-widecontrol-format.md)|<span data-ttu-id="cf053-119">Specifica la proprietà dell'oggetto il cui valore viene visualizzato nella visualizzazione estesa.</span><span class="sxs-lookup"><span data-stu-id="cf053-119">Specifies the property of the object whose value is displayed in the wide view.</span></span>|
|[<span data-ttu-id="cf053-120">Elemento ScriptBlock per WideItem (Format)</span><span class="sxs-lookup"><span data-stu-id="cf053-120">ScriptBlock Element for WideItem (Format)</span></span>](./scriptblock-element-for-wideitem-for-widecontrol-format.md)|<span data-ttu-id="cf053-121">Specifica lo script il cui valore viene visualizzato nella visualizzazione estesa.</span><span class="sxs-lookup"><span data-stu-id="cf053-121">Specifies the script whose value is displayed in the wide view.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="cf053-122">Elementi padre</span><span class="sxs-lookup"><span data-stu-id="cf053-122">Parent Elements</span></span>

|<span data-ttu-id="cf053-123">Elemento</span><span class="sxs-lookup"><span data-stu-id="cf053-123">Element</span></span>|<span data-ttu-id="cf053-124">Description</span><span class="sxs-lookup"><span data-stu-id="cf053-124">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="cf053-125">Elemento WideEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="cf053-125">WideEntry Element (Format)</span></span>](./wideentry-element-for-widecontrol-format.md)|<span data-ttu-id="cf053-126">Fornisce una definizione dell'ampia visualizzazione.</span><span class="sxs-lookup"><span data-stu-id="cf053-126">Provides a definition of the wide view.</span></span>|

## <a name="remarks"></a><span data-ttu-id="cf053-127">Osservazioni</span><span class="sxs-lookup"><span data-stu-id="cf053-127">Remarks</span></span>

<span data-ttu-id="cf053-128">Per ulteriori informazioni sui componenti di una visualizzazione estesa, vedere [visualizzazione estesa](./creating-a-wide-view.md).</span><span class="sxs-lookup"><span data-stu-id="cf053-128">For more information about the components of a wide view, see [Wide View](./creating-a-wide-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="cf053-129">Esempio</span><span class="sxs-lookup"><span data-stu-id="cf053-129">Example</span></span>

<span data-ttu-id="cf053-130">Nell'esempio seguente viene illustrato un elemento `WideEntry` che definisce un singolo elemento di `WideItem`.</span><span class="sxs-lookup"><span data-stu-id="cf053-130">The following example shows a `WideEntry` element that defines a single `WideItem` element.</span></span> <span data-ttu-id="cf053-131">L'elemento `WideItem` definisce la proprietà o lo script il cui valore viene visualizzato nella visualizzazione.</span><span class="sxs-lookup"><span data-stu-id="cf053-131">The `WideItem` element defines the property or script whose value is displayed in the view.</span></span>

```xml
<WideEntry>
  <WideItem>
    <PropertyName>ProcessName</PropertyName>
  </WideItem>
</WideEntry>
```

<span data-ttu-id="cf053-132">Per un esempio completo di una visualizzazione estesa, vedere [Wide View (Basic)](./wide-view-basic.md).</span><span class="sxs-lookup"><span data-stu-id="cf053-132">For a complete example of a wide view, see [Wide View (Basic)](./wide-view-basic.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="cf053-133">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="cf053-133">See Also</span></span>

[<span data-ttu-id="cf053-134">Elemento FormatString per WideItem per WideControl (Format)</span><span class="sxs-lookup"><span data-stu-id="cf053-134">FormatString Element for WideItem for WideControl (Format)</span></span>](./formatstring-element-for-wideitem-for-widecontrol-format.md)

[<span data-ttu-id="cf053-135">Elemento PropertyName per WideItem (Format)</span><span class="sxs-lookup"><span data-stu-id="cf053-135">PropertyName Element for WideItem (Format)</span></span>](./propertyname-element-for-wideitem-for-widecontrol-format.md)

[<span data-ttu-id="cf053-136">Elemento ScriptBlock per WideItem (Format)</span><span class="sxs-lookup"><span data-stu-id="cf053-136">ScriptBlock Element for WideItem (Format)</span></span>](./scriptblock-element-for-wideitem-for-widecontrol-format.md)

[<span data-ttu-id="cf053-137">Elemento WideEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="cf053-137">WideEntry Element (Format)</span></span>](./wideentry-element-for-widecontrol-format.md)

[<span data-ttu-id="cf053-138">Scrittura di un file di formattazione di PowerShell</span><span class="sxs-lookup"><span data-stu-id="cf053-138">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
