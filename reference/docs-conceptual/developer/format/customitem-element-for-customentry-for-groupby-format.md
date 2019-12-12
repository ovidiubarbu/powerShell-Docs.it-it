---
title: Elemento CustomItem per CustomEntry per GroupBy (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f7c517aa-24f5-41ae-b82d-cb0fac81a245
caps.latest.revision: 7
ms.openlocfilehash: 2d821f5e3bc8d0f81ef8a8a040c6f9bcb1658bee
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/05/2019
ms.locfileid: "72363880"
---
# <a name="customitem-element-for-customentry-for-groupby-format"></a><span data-ttu-id="5065d-102">Elemento CustomItem per CustomEntry per GroupBy (formato)</span><span class="sxs-lookup"><span data-stu-id="5065d-102">CustomItem Element for CustomEntry for GroupBy (Format)</span></span>

<span data-ttu-id="5065d-103">Definisce quali dati vengono visualizzati dalla visualizzazione controlli personalizzati e come vengono visualizzati.</span><span class="sxs-lookup"><span data-stu-id="5065d-103">Defines what data is displayed by the custom control view and how it is displayed.</span></span> <span data-ttu-id="5065d-104">Questo elemento viene utilizzato quando si definisce la modalità di visualizzazione di un nuovo gruppo di oggetti.</span><span class="sxs-lookup"><span data-stu-id="5065d-104">This element is used when defining how a new group of objects is displayed.</span></span>

<span data-ttu-id="5065d-105">Elemento Configuration (Format) elemento ViewDefinitions (Format) elemento View (Format) elemento GroupBy per View (Format) elemento CustomControl per l'elemento GroupBy (Format) CustomEntries per CustomControl per l'elemento GroupBy (Format) CustomItem per CustomEntry per GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="5065d-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) GroupBy Element for View (Format) CustomControl Element for GroupBy (Format) CustomEntries Element for CustomControl for GroupBy (Format) CustomItem Element for CustomEntry for GroupBy (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="5065d-106">Sintassi</span><span class="sxs-lookup"><span data-stu-id="5065d-106">Syntax</span></span>

```xml
<CustomItem>
  <ExpressionBinding>...</ExpressionBinding>
  <Frame>...</Frame>
  <NewLine/>
  <Text>TextToDisplay</Text>
</CustomItem>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="5065d-107">Attributi ed elementi</span><span class="sxs-lookup"><span data-stu-id="5065d-107">Attributes and Elements</span></span>

<span data-ttu-id="5065d-108">Nelle sezioni seguenti vengono descritti gli attributi, gli elementi figlio e l'elemento padre dell'elemento `CustomItem`.</span><span class="sxs-lookup"><span data-stu-id="5065d-108">The following sections describe attributes, child elements, and the parent element of the `CustomItem` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="5065d-109">Attributi</span><span class="sxs-lookup"><span data-stu-id="5065d-109">Attributes</span></span>

<span data-ttu-id="5065d-110">Nessuna.</span><span class="sxs-lookup"><span data-stu-id="5065d-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="5065d-111">Elementi figlio</span><span class="sxs-lookup"><span data-stu-id="5065d-111">Child Elements</span></span>

|<span data-ttu-id="5065d-112">Elemento</span><span class="sxs-lookup"><span data-stu-id="5065d-112">Element</span></span>|<span data-ttu-id="5065d-113">Description</span><span class="sxs-lookup"><span data-stu-id="5065d-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="5065d-114">Elemento expressiongroup per CustomItem per GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="5065d-114">ExpressionBinding Element for CustomItem for GroupBy (Format)</span></span>](./expressionbinding-element-for-customitem-for-groupby-format.md)|<span data-ttu-id="5065d-115">Elemento facoltativo.</span><span class="sxs-lookup"><span data-stu-id="5065d-115">Optional element.</span></span><br /><br /> <span data-ttu-id="5065d-116">Definisce i dati visualizzati dal controllo.</span><span class="sxs-lookup"><span data-stu-id="5065d-116">Defines the data that is displayed by the control.</span></span>|
|[<span data-ttu-id="5065d-117">Elemento frame per CustomItem per GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="5065d-117">Frame Element for CustomItem for GroupBy (Format)</span></span>](./frame-element-for-customitem-for-groupby-format.md)|<span data-ttu-id="5065d-118">Elemento facoltativo.</span><span class="sxs-lookup"><span data-stu-id="5065d-118">Optional element.</span></span><br /><br /> <span data-ttu-id="5065d-119">Definisce quali dati vengono visualizzati dalla visualizzazione controlli personalizzati e come vengono visualizzati.</span><span class="sxs-lookup"><span data-stu-id="5065d-119">Defines what data is displayed by the custom control view and how it is displayed.</span></span>|
|[<span data-ttu-id="5065d-120">Elemento NewLine per CustomItem per GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="5065d-120">NewLine Element for CustomItem for GroupBy (Format)</span></span>](./newline-element-for-customitem-for-groupby-format.md)|<span data-ttu-id="5065d-121">Elemento facoltativo.</span><span class="sxs-lookup"><span data-stu-id="5065d-121">Optional element.</span></span><br /><br /> <span data-ttu-id="5065d-122">Aggiunge una riga vuota alla visualizzazione del controllo.</span><span class="sxs-lookup"><span data-stu-id="5065d-122">Adds a blank line to the display of the control.</span></span>|
|[<span data-ttu-id="5065d-123">Elemento text per CustomItem per GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="5065d-123">Text Element for CustomItem for GroupBy (Format)</span></span>](./text-element-for-customitem-for-groupby-format.md)|<span data-ttu-id="5065d-124">Elemento facoltativo.</span><span class="sxs-lookup"><span data-stu-id="5065d-124">Optional element.</span></span><br /><br /> <span data-ttu-id="5065d-125">Specifica il testo aggiuntivo per i dati visualizzati dal controllo.</span><span class="sxs-lookup"><span data-stu-id="5065d-125">Specifies additional text to the data displayed by the control.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="5065d-126">Elementi padre</span><span class="sxs-lookup"><span data-stu-id="5065d-126">Parent Elements</span></span>

|<span data-ttu-id="5065d-127">Elemento</span><span class="sxs-lookup"><span data-stu-id="5065d-127">Element</span></span>|<span data-ttu-id="5065d-128">Description</span><span class="sxs-lookup"><span data-stu-id="5065d-128">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="5065d-129">Elemento CustomEntry per CustomControl per GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="5065d-129">CustomEntry Element for CustomControl for GroupBy (Format)</span></span>](./customentry-element-for-customcontrol-for-groupby-format.md)|<span data-ttu-id="5065d-130">Fornisce una definizione della visualizzazione controlli personalizzata.</span><span class="sxs-lookup"><span data-stu-id="5065d-130">Provides a definition of the custom control view.</span></span>|

## <a name="remarks"></a><span data-ttu-id="5065d-131">Osservazioni</span><span class="sxs-lookup"><span data-stu-id="5065d-131">Remarks</span></span>

## <a name="see-also"></a><span data-ttu-id="5065d-132">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="5065d-132">See Also</span></span>

[<span data-ttu-id="5065d-133">Elemento CustomEntry per CustomControl per GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="5065d-133">CustomEntry Element for CustomControl for GroupBy (Format)</span></span>](./customentry-element-for-customcontrol-for-groupby-format.md)

[<span data-ttu-id="5065d-134">Elemento expressiongroup per CustomItem per GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="5065d-134">ExpressionBinding Element for CustomItem for GroupBy (Format)</span></span>](./expressionbinding-element-for-customitem-for-groupby-format.md)

[<span data-ttu-id="5065d-135">Elemento frame per CustomItem per GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="5065d-135">Frame Element for CustomItem for GroupBy (Format)</span></span>](./frame-element-for-customitem-for-groupby-format.md)

[<span data-ttu-id="5065d-136">Elemento NewLine per CustomItem per GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="5065d-136">NewLine Element for CustomItem for GroupBy (Format)</span></span>](./newline-element-for-customitem-for-groupby-format.md)

[<span data-ttu-id="5065d-137">Elemento text per CustomItem per GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="5065d-137">Text Element for CustomItem for GroupBy (Format)</span></span>](./text-element-for-customitem-for-groupby-format.md)

[<span data-ttu-id="5065d-138">Scrittura di un file di formattazione di PowerShell</span><span class="sxs-lookup"><span data-stu-id="5065d-138">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
