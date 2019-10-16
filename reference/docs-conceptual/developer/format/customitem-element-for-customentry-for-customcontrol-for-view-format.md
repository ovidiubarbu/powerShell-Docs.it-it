---
title: Elemento CustomItem per CustomEntry per CustomControl per View (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 98708c1d-6f39-4a76-b454-31153a6ade8c
caps.latest.revision: 12
ms.openlocfilehash: 3c110bd5fe3ef2f790ef136556afa7c29d0b5b29
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/15/2019
ms.locfileid: "72363950"
---
# <a name="customitem-element-for-customentry-for-customcontrol-for-view-format"></a><span data-ttu-id="3b6eb-102">Elemento CustomItem per CustomEntry per CustomControl per View (formato)</span><span class="sxs-lookup"><span data-stu-id="3b6eb-102">CustomItem Element for CustomEntry for CustomControl for View (Format)</span></span>

<span data-ttu-id="3b6eb-103">Definisce quali dati vengono visualizzati dalla visualizzazione controlli personalizzati e come vengono visualizzati.</span><span class="sxs-lookup"><span data-stu-id="3b6eb-103">Defines what data is displayed by the custom control view and how it is displayed.</span></span> <span data-ttu-id="3b6eb-104">Questo elemento viene utilizzato quando si definisce una visualizzazione controlli personalizzata.</span><span class="sxs-lookup"><span data-stu-id="3b6eb-104">This element is used when defining a custom control view.</span></span>

<span data-ttu-id="3b6eb-105">Elemento Configuration (Format) elemento ViewDefinitions (Format) elemento View (Format) elemento CustomControl (Format) elemento CustomEntries per CustomControl per la vista (Format) CustomEntry elemento per CustomEntries per la visualizzazione (Format) CustomItem elemento per CustomEntry per la visualizzazione (formato)</span><span class="sxs-lookup"><span data-stu-id="3b6eb-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) CustomControl Element (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for View (Format) CustomItem Element for CustomEntry for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="3b6eb-106">Sintassi</span><span class="sxs-lookup"><span data-stu-id="3b6eb-106">Syntax</span></span>

```xml
<CustomItem>
  <ExpressionBinding>...</ExpressionBinding>
  <Frame>...</Frame>
  <NewLine/>
  <Text>TextToDisplay</Text>
</CustomItem>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="3b6eb-107">Attributi ed elementi</span><span class="sxs-lookup"><span data-stu-id="3b6eb-107">Attributes and Elements</span></span>

<span data-ttu-id="3b6eb-108">Nelle sezioni seguenti vengono descritti gli attributi, gli elementi figlio e l'elemento padre dell'elemento `CustomItem`.</span><span class="sxs-lookup"><span data-stu-id="3b6eb-108">The following sections describe attributes, child elements, and the parent element of the `CustomItem` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="3b6eb-109">Attributi</span><span class="sxs-lookup"><span data-stu-id="3b6eb-109">Attributes</span></span>

<span data-ttu-id="3b6eb-110">Nessuna.</span><span class="sxs-lookup"><span data-stu-id="3b6eb-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="3b6eb-111">Elementi figlio</span><span class="sxs-lookup"><span data-stu-id="3b6eb-111">Child Elements</span></span>

|<span data-ttu-id="3b6eb-112">Elemento</span><span class="sxs-lookup"><span data-stu-id="3b6eb-112">Element</span></span>|<span data-ttu-id="3b6eb-113">Description</span><span class="sxs-lookup"><span data-stu-id="3b6eb-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="3b6eb-114">Elemento expressiongroup per CustomItem per CustomControl per View (Format)</span><span class="sxs-lookup"><span data-stu-id="3b6eb-114">ExpressionBinding Element for CustomItem for CustomControl for View (Format)</span></span>](./expressionbinding-element-for-customitem-for-customcontrol-for-view-format.md)|<span data-ttu-id="3b6eb-115">Elemento facoltativo.</span><span class="sxs-lookup"><span data-stu-id="3b6eb-115">Optional element.</span></span><br /><br /> <span data-ttu-id="3b6eb-116">Definisce i dati visualizzati dal controllo.</span><span class="sxs-lookup"><span data-stu-id="3b6eb-116">Defines the data that is displayed by the control.</span></span>|
|[<span data-ttu-id="3b6eb-117">Elemento frame per CustomItem per CustomControl per View (Format)</span><span class="sxs-lookup"><span data-stu-id="3b6eb-117">Frame Element for CustomItem for CustomControl for View (Format)</span></span>](./frame-element-for-customitem-for-customcontrol-for-view-format.md)|<span data-ttu-id="3b6eb-118">Elemento facoltativo.</span><span class="sxs-lookup"><span data-stu-id="3b6eb-118">Optional element.</span></span><br /><br /> <span data-ttu-id="3b6eb-119">Definisce quali dati vengono visualizzati dalla visualizzazione controlli personalizzati e come vengono visualizzati.</span><span class="sxs-lookup"><span data-stu-id="3b6eb-119">Defines what data is displayed by the custom control view and how it is displayed.</span></span>|
|[<span data-ttu-id="3b6eb-120">Elemento NewLine per CustomItem per il controllo personalizzato per la visualizzazione (Format)</span><span class="sxs-lookup"><span data-stu-id="3b6eb-120">NewLine Element for CustomItem for Custom Control for View (Format)</span></span>](./newline-element-for-customitem-for-customcontrol-for-view-format.md)|<span data-ttu-id="3b6eb-121">Elemento facoltativo.</span><span class="sxs-lookup"><span data-stu-id="3b6eb-121">Optional element.</span></span><br /><br /> <span data-ttu-id="3b6eb-122">Aggiunge una riga vuota alla visualizzazione del controllo.</span><span class="sxs-lookup"><span data-stu-id="3b6eb-122">Adds a blank line to the display of the control.</span></span>|
|[<span data-ttu-id="3b6eb-123">Elemento text per CustomItem per CustomControl per View (Format)</span><span class="sxs-lookup"><span data-stu-id="3b6eb-123">Text Element for CustomItem for CustomControl for View (Format)</span></span>](./text-element-for-customitem-for-customview-for-view-format.md)|<span data-ttu-id="3b6eb-124">Elemento facoltativo.</span><span class="sxs-lookup"><span data-stu-id="3b6eb-124">Optional element.</span></span><br /><br /> <span data-ttu-id="3b6eb-125">Specifica il testo aggiuntivo per i dati visualizzati dal controllo.</span><span class="sxs-lookup"><span data-stu-id="3b6eb-125">Specifies additional text to the data displayed by the control.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="3b6eb-126">Elementi padre</span><span class="sxs-lookup"><span data-stu-id="3b6eb-126">Parent Elements</span></span>

|<span data-ttu-id="3b6eb-127">Elemento</span><span class="sxs-lookup"><span data-stu-id="3b6eb-127">Element</span></span>|<span data-ttu-id="3b6eb-128">Description</span><span class="sxs-lookup"><span data-stu-id="3b6eb-128">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="3b6eb-129">Elemento CustomEntry per CustomEntries per CustomControl per View (Format)</span><span class="sxs-lookup"><span data-stu-id="3b6eb-129">CustomEntry Element for CustomEntries for CustomControl for View (Format)</span></span>](./customentry-element-for-customentries-for-customcontrol-for-view-format.md)|<span data-ttu-id="3b6eb-130">Fornisce una definizione della visualizzazione controlli personalizzata.</span><span class="sxs-lookup"><span data-stu-id="3b6eb-130">Provides a definition of the custom control view.</span></span>|

## <a name="remarks"></a><span data-ttu-id="3b6eb-131">Osservazioni</span><span class="sxs-lookup"><span data-stu-id="3b6eb-131">Remarks</span></span>

## <a name="see-also"></a><span data-ttu-id="3b6eb-132">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="3b6eb-132">See Also</span></span>

[<span data-ttu-id="3b6eb-133">Elemento CustomEntry per CustomEntries per View (Format)</span><span class="sxs-lookup"><span data-stu-id="3b6eb-133">CustomEntry Element for CustomEntries for View (Format)</span></span>](./customentry-element-for-customentries-for-customcontrol-for-view-format.md)

[<span data-ttu-id="3b6eb-134">Elemento expressiongroup per CustomItem per CustomControl per View (Format)</span><span class="sxs-lookup"><span data-stu-id="3b6eb-134">ExpressionBinding Element for CustomItem for CustomControl for View (Format)</span></span>](./expressionbinding-element-for-customitem-for-customcontrol-for-view-format.md)

[<span data-ttu-id="3b6eb-135">Elemento frame per CustomItem per CustomControl per View (Format)</span><span class="sxs-lookup"><span data-stu-id="3b6eb-135">Frame Element for CustomItem for CustomControl for View (Format)</span></span>](./frame-element-for-customitem-for-customcontrol-for-view-format.md)

[<span data-ttu-id="3b6eb-136">Elemento NewLine per CustomItem per CustomControl per View (Format)</span><span class="sxs-lookup"><span data-stu-id="3b6eb-136">NewLine Element for CustomItem for CustomControl for View (Format)</span></span>](./newline-element-for-customitem-for-customcontrol-for-view-format.md)

[<span data-ttu-id="3b6eb-137">Elemento text per CustomItem per CustomControl per View (Format)</span><span class="sxs-lookup"><span data-stu-id="3b6eb-137">Text Element for CustomItem for CustomControl for View (Format)</span></span>](./text-element-for-customitem-for-customview-for-view-format.md)

[<span data-ttu-id="3b6eb-138">Scrittura di un file di formattazione di PowerShell</span><span class="sxs-lookup"><span data-stu-id="3b6eb-138">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
