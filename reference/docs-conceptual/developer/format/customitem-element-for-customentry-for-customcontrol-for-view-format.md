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
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/05/2019
ms.locfileid: "72363950"
---
# <a name="customitem-element-for-customentry-for-customcontrol-for-view-format"></a><span data-ttu-id="75866-102">Elemento CustomItem per CustomEntry per CustomControl per View (formato)</span><span class="sxs-lookup"><span data-stu-id="75866-102">CustomItem Element for CustomEntry for CustomControl for View (Format)</span></span>

<span data-ttu-id="75866-103">Definisce quali dati vengono visualizzati dalla visualizzazione controlli personalizzati e come vengono visualizzati.</span><span class="sxs-lookup"><span data-stu-id="75866-103">Defines what data is displayed by the custom control view and how it is displayed.</span></span> <span data-ttu-id="75866-104">Questo elemento viene utilizzato quando si definisce una visualizzazione controlli personalizzata.</span><span class="sxs-lookup"><span data-stu-id="75866-104">This element is used when defining a custom control view.</span></span>

<span data-ttu-id="75866-105">Elemento Configuration (Format) elemento ViewDefinitions (Format) elemento View (Format) elemento CustomControl (Format) elemento CustomEntries per CustomControl per la vista (Format) CustomEntry elemento per CustomEntries per la visualizzazione (Format) CustomItem elemento per CustomEntry per la visualizzazione (formato)</span><span class="sxs-lookup"><span data-stu-id="75866-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) CustomControl Element (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for View (Format) CustomItem Element for CustomEntry for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="75866-106">Sintassi</span><span class="sxs-lookup"><span data-stu-id="75866-106">Syntax</span></span>

```xml
<CustomItem>
  <ExpressionBinding>...</ExpressionBinding>
  <Frame>...</Frame>
  <NewLine/>
  <Text>TextToDisplay</Text>
</CustomItem>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="75866-107">Attributi ed elementi</span><span class="sxs-lookup"><span data-stu-id="75866-107">Attributes and Elements</span></span>

<span data-ttu-id="75866-108">Nelle sezioni seguenti vengono descritti gli attributi, gli elementi figlio e l'elemento padre dell'elemento `CustomItem`.</span><span class="sxs-lookup"><span data-stu-id="75866-108">The following sections describe attributes, child elements, and the parent element of the `CustomItem` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="75866-109">Attributi</span><span class="sxs-lookup"><span data-stu-id="75866-109">Attributes</span></span>

<span data-ttu-id="75866-110">Nessuna.</span><span class="sxs-lookup"><span data-stu-id="75866-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="75866-111">Elementi figlio</span><span class="sxs-lookup"><span data-stu-id="75866-111">Child Elements</span></span>

|<span data-ttu-id="75866-112">Elemento</span><span class="sxs-lookup"><span data-stu-id="75866-112">Element</span></span>|<span data-ttu-id="75866-113">Description</span><span class="sxs-lookup"><span data-stu-id="75866-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="75866-114">Elemento expressiongroup per CustomItem per CustomControl per View (Format)</span><span class="sxs-lookup"><span data-stu-id="75866-114">ExpressionBinding Element for CustomItem for CustomControl for View (Format)</span></span>](./expressionbinding-element-for-customitem-for-customcontrol-for-view-format.md)|<span data-ttu-id="75866-115">Elemento facoltativo.</span><span class="sxs-lookup"><span data-stu-id="75866-115">Optional element.</span></span><br /><br /> <span data-ttu-id="75866-116">Definisce i dati visualizzati dal controllo.</span><span class="sxs-lookup"><span data-stu-id="75866-116">Defines the data that is displayed by the control.</span></span>|
|[<span data-ttu-id="75866-117">Elemento frame per CustomItem per CustomControl per View (Format)</span><span class="sxs-lookup"><span data-stu-id="75866-117">Frame Element for CustomItem for CustomControl for View (Format)</span></span>](./frame-element-for-customitem-for-customcontrol-for-view-format.md)|<span data-ttu-id="75866-118">Elemento facoltativo.</span><span class="sxs-lookup"><span data-stu-id="75866-118">Optional element.</span></span><br /><br /> <span data-ttu-id="75866-119">Definisce quali dati vengono visualizzati dalla visualizzazione controlli personalizzati e come vengono visualizzati.</span><span class="sxs-lookup"><span data-stu-id="75866-119">Defines what data is displayed by the custom control view and how it is displayed.</span></span>|
|[<span data-ttu-id="75866-120">Elemento NewLine per CustomItem per il controllo personalizzato per la visualizzazione (Format)</span><span class="sxs-lookup"><span data-stu-id="75866-120">NewLine Element for CustomItem for Custom Control for View (Format)</span></span>](./newline-element-for-customitem-for-customcontrol-for-view-format.md)|<span data-ttu-id="75866-121">Elemento facoltativo.</span><span class="sxs-lookup"><span data-stu-id="75866-121">Optional element.</span></span><br /><br /> <span data-ttu-id="75866-122">Aggiunge una riga vuota alla visualizzazione del controllo.</span><span class="sxs-lookup"><span data-stu-id="75866-122">Adds a blank line to the display of the control.</span></span>|
|[<span data-ttu-id="75866-123">Elemento text per CustomItem per CustomControl per View (Format)</span><span class="sxs-lookup"><span data-stu-id="75866-123">Text Element for CustomItem for CustomControl for View (Format)</span></span>](./text-element-for-customitem-for-customview-for-view-format.md)|<span data-ttu-id="75866-124">Elemento facoltativo.</span><span class="sxs-lookup"><span data-stu-id="75866-124">Optional element.</span></span><br /><br /> <span data-ttu-id="75866-125">Specifica il testo aggiuntivo per i dati visualizzati dal controllo.</span><span class="sxs-lookup"><span data-stu-id="75866-125">Specifies additional text to the data displayed by the control.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="75866-126">Elementi padre</span><span class="sxs-lookup"><span data-stu-id="75866-126">Parent Elements</span></span>

|<span data-ttu-id="75866-127">Elemento</span><span class="sxs-lookup"><span data-stu-id="75866-127">Element</span></span>|<span data-ttu-id="75866-128">Description</span><span class="sxs-lookup"><span data-stu-id="75866-128">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="75866-129">Elemento CustomEntry per CustomEntries per CustomControl per View (Format)</span><span class="sxs-lookup"><span data-stu-id="75866-129">CustomEntry Element for CustomEntries for CustomControl for View (Format)</span></span>](./customentry-element-for-customentries-for-customcontrol-for-view-format.md)|<span data-ttu-id="75866-130">Fornisce una definizione della visualizzazione controlli personalizzata.</span><span class="sxs-lookup"><span data-stu-id="75866-130">Provides a definition of the custom control view.</span></span>|

## <a name="remarks"></a><span data-ttu-id="75866-131">Osservazioni</span><span class="sxs-lookup"><span data-stu-id="75866-131">Remarks</span></span>

## <a name="see-also"></a><span data-ttu-id="75866-132">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="75866-132">See Also</span></span>

[<span data-ttu-id="75866-133">Elemento CustomEntry per CustomEntries per View (Format)</span><span class="sxs-lookup"><span data-stu-id="75866-133">CustomEntry Element for CustomEntries for View (Format)</span></span>](./customentry-element-for-customentries-for-customcontrol-for-view-format.md)

[<span data-ttu-id="75866-134">Elemento expressiongroup per CustomItem per CustomControl per View (Format)</span><span class="sxs-lookup"><span data-stu-id="75866-134">ExpressionBinding Element for CustomItem for CustomControl for View (Format)</span></span>](./expressionbinding-element-for-customitem-for-customcontrol-for-view-format.md)

[<span data-ttu-id="75866-135">Elemento frame per CustomItem per CustomControl per View (Format)</span><span class="sxs-lookup"><span data-stu-id="75866-135">Frame Element for CustomItem for CustomControl for View (Format)</span></span>](./frame-element-for-customitem-for-customcontrol-for-view-format.md)

[<span data-ttu-id="75866-136">Elemento NewLine per CustomItem per CustomControl per View (Format)</span><span class="sxs-lookup"><span data-stu-id="75866-136">NewLine Element for CustomItem for CustomControl for View (Format)</span></span>](./newline-element-for-customitem-for-customcontrol-for-view-format.md)

[<span data-ttu-id="75866-137">Elemento text per CustomItem per CustomControl per View (Format)</span><span class="sxs-lookup"><span data-stu-id="75866-137">Text Element for CustomItem for CustomControl for View (Format)</span></span>](./text-element-for-customitem-for-customview-for-view-format.md)

[<span data-ttu-id="75866-138">Scrittura di un file di formattazione di PowerShell</span><span class="sxs-lookup"><span data-stu-id="75866-138">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
