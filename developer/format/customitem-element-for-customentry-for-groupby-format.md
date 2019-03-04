---
title: Elemento CustomItem per CustomEntry per GroupBy (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f7c517aa-24f5-41ae-b82d-cb0fac81a245
caps.latest.revision: 7
ms.openlocfilehash: 2d821f5e3bc8d0f81ef8a8a040c6f9bcb1658bee
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/03/2019
ms.locfileid: "56856927"
---
# <a name="customitem-element-for-customentry-for-groupby-format"></a><span data-ttu-id="e8f5f-102">Elemento CustomItem per CustomEntry per GroupBy (formato)</span><span class="sxs-lookup"><span data-stu-id="e8f5f-102">CustomItem Element for CustomEntry for GroupBy (Format)</span></span>

<span data-ttu-id="e8f5f-103">Definisce i dati visualizzati dalla visualizzazione del controllo personalizzato e modalità di visualizzazione.</span><span class="sxs-lookup"><span data-stu-id="e8f5f-103">Defines what data is displayed by the custom control view and how it is displayed.</span></span> <span data-ttu-id="e8f5f-104">Questo elemento viene usato quando si definisce come viene visualizzato un nuovo gruppo di oggetti.</span><span class="sxs-lookup"><span data-stu-id="e8f5f-104">This element is used when defining how a new group of objects is displayed.</span></span>

<span data-ttu-id="e8f5f-105">Elemento di GroupBy elemento (formato) per la visualizzazione elemento ViewDefinitions (formato) configurazione elemento (formato) per visualizzazione (formato) CustomControl elemento per elemento CustomEntries GroupBy (formato) per CustomControl per elemento CustomItem GroupBy (formato) CustomEntry per GroupBy (formato)</span><span class="sxs-lookup"><span data-stu-id="e8f5f-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) GroupBy Element for View (Format) CustomControl Element for GroupBy (Format) CustomEntries Element for CustomControl for GroupBy (Format) CustomItem Element for CustomEntry for GroupBy (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="e8f5f-106">Sintassi</span><span class="sxs-lookup"><span data-stu-id="e8f5f-106">Syntax</span></span>

```xml
<CustomItem>
  <ExpressionBinding>...</ExpressionBinding>
  <Frame>...</Frame>
  <NewLine/>
  <Text>TextToDisplay</Text>
</CustomItem>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="e8f5f-107">Attributi ed elementi</span><span class="sxs-lookup"><span data-stu-id="e8f5f-107">Attributes and Elements</span></span>

<span data-ttu-id="e8f5f-108">Le sezioni seguenti descrivono gli attributi e gli elementi figlio dell'elemento padre del `CustomItem` elemento.</span><span class="sxs-lookup"><span data-stu-id="e8f5f-108">The following sections describe attributes, child elements, and the parent element of the `CustomItem` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="e8f5f-109">Attributes</span><span class="sxs-lookup"><span data-stu-id="e8f5f-109">Attributes</span></span>

<span data-ttu-id="e8f5f-110">Nessuna.</span><span class="sxs-lookup"><span data-stu-id="e8f5f-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="e8f5f-111">Elementi figlio</span><span class="sxs-lookup"><span data-stu-id="e8f5f-111">Child Elements</span></span>

|<span data-ttu-id="e8f5f-112">Elemento</span><span class="sxs-lookup"><span data-stu-id="e8f5f-112">Element</span></span>|<span data-ttu-id="e8f5f-113">Description</span><span class="sxs-lookup"><span data-stu-id="e8f5f-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="e8f5f-114">Elemento ExpressionBinding per CustomItem per GroupBy (formato)</span><span class="sxs-lookup"><span data-stu-id="e8f5f-114">ExpressionBinding Element for CustomItem for GroupBy (Format)</span></span>](./expressionbinding-element-for-customitem-for-groupby-format.md)|<span data-ttu-id="e8f5f-115">Elemento facoltativo.</span><span class="sxs-lookup"><span data-stu-id="e8f5f-115">Optional element.</span></span><br /><br /> <span data-ttu-id="e8f5f-116">Definisce i dati che vengano visualizzati dal controllo.</span><span class="sxs-lookup"><span data-stu-id="e8f5f-116">Defines the data that is displayed by the control.</span></span>|
|[<span data-ttu-id="e8f5f-117">Elemento frame per CustomItem per GroupBy (formato)</span><span class="sxs-lookup"><span data-stu-id="e8f5f-117">Frame Element for CustomItem for GroupBy (Format)</span></span>](./frame-element-for-customitem-for-groupby-format.md)|<span data-ttu-id="e8f5f-118">Elemento facoltativo.</span><span class="sxs-lookup"><span data-stu-id="e8f5f-118">Optional element.</span></span><br /><br /> <span data-ttu-id="e8f5f-119">Definisce i dati visualizzati dalla visualizzazione del controllo personalizzato e modalità di visualizzazione.</span><span class="sxs-lookup"><span data-stu-id="e8f5f-119">Defines what data is displayed by the custom control view and how it is displayed.</span></span>|
|[<span data-ttu-id="e8f5f-120">Elemento di una nuova riga per CustomItem per GroupBy (formato)</span><span class="sxs-lookup"><span data-stu-id="e8f5f-120">NewLine Element for CustomItem for GroupBy (Format)</span></span>](./newline-element-for-customitem-for-groupby-format.md)|<span data-ttu-id="e8f5f-121">Elemento facoltativo.</span><span class="sxs-lookup"><span data-stu-id="e8f5f-121">Optional element.</span></span><br /><br /> <span data-ttu-id="e8f5f-122">Aggiunge una riga vuota alla visualizzazione del controllo.</span><span class="sxs-lookup"><span data-stu-id="e8f5f-122">Adds a blank line to the display of the control.</span></span>|
|[<span data-ttu-id="e8f5f-123">Elemento di testo per CustomItem per GroupBy (formato)</span><span class="sxs-lookup"><span data-stu-id="e8f5f-123">Text Element for CustomItem for GroupBy (Format)</span></span>](./text-element-for-customitem-for-groupby-format.md)|<span data-ttu-id="e8f5f-124">Elemento facoltativo.</span><span class="sxs-lookup"><span data-stu-id="e8f5f-124">Optional element.</span></span><br /><br /> <span data-ttu-id="e8f5f-125">Specifica il testo aggiuntivo per i dati visualizzati dal controllo.</span><span class="sxs-lookup"><span data-stu-id="e8f5f-125">Specifies additional text to the data displayed by the control.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="e8f5f-126">Elementi padre</span><span class="sxs-lookup"><span data-stu-id="e8f5f-126">Parent Elements</span></span>

|<span data-ttu-id="e8f5f-127">Elemento</span><span class="sxs-lookup"><span data-stu-id="e8f5f-127">Element</span></span>|<span data-ttu-id="e8f5f-128">Description</span><span class="sxs-lookup"><span data-stu-id="e8f5f-128">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="e8f5f-129">Elemento CustomEntry per CustomControl per GroupBy (formato)</span><span class="sxs-lookup"><span data-stu-id="e8f5f-129">CustomEntry Element for CustomControl for GroupBy (Format)</span></span>](./customentry-element-for-customcontrol-for-groupby-format.md)|<span data-ttu-id="e8f5f-130">Fornisce una definizione della vista del controllo personalizzato.</span><span class="sxs-lookup"><span data-stu-id="e8f5f-130">Provides a definition of the custom control view.</span></span>|

## <a name="remarks"></a><span data-ttu-id="e8f5f-131">Osservazioni</span><span class="sxs-lookup"><span data-stu-id="e8f5f-131">Remarks</span></span>

## <a name="see-also"></a><span data-ttu-id="e8f5f-132">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="e8f5f-132">See Also</span></span>

[<span data-ttu-id="e8f5f-133">Elemento CustomEntry per CustomControl per GroupBy (formato)</span><span class="sxs-lookup"><span data-stu-id="e8f5f-133">CustomEntry Element for CustomControl for GroupBy (Format)</span></span>](./customentry-element-for-customcontrol-for-groupby-format.md)

[<span data-ttu-id="e8f5f-134">Elemento ExpressionBinding per CustomItem per GroupBy (formato)</span><span class="sxs-lookup"><span data-stu-id="e8f5f-134">ExpressionBinding Element for CustomItem for GroupBy (Format)</span></span>](./expressionbinding-element-for-customitem-for-groupby-format.md)

[<span data-ttu-id="e8f5f-135">Elemento frame per CustomItem per GroupBy (formato)</span><span class="sxs-lookup"><span data-stu-id="e8f5f-135">Frame Element for CustomItem for GroupBy (Format)</span></span>](./frame-element-for-customitem-for-groupby-format.md)

[<span data-ttu-id="e8f5f-136">Elemento di una nuova riga per CustomItem per GroupBy (formato)</span><span class="sxs-lookup"><span data-stu-id="e8f5f-136">NewLine Element for CustomItem for GroupBy (Format)</span></span>](./newline-element-for-customitem-for-groupby-format.md)

[<span data-ttu-id="e8f5f-137">Elemento di testo per CustomItem per GroupBy (formato)</span><span class="sxs-lookup"><span data-stu-id="e8f5f-137">Text Element for CustomItem for GroupBy (Format)</span></span>](./text-element-for-customitem-for-groupby-format.md)

[<span data-ttu-id="e8f5f-138">La scrittura di un File di formattazione di PowerShell</span><span class="sxs-lookup"><span data-stu-id="e8f5f-138">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
