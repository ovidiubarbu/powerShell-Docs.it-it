---
title: Elemento CustomItem per CustomEntry per CustomControl per visualizzazione (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 98708c1d-6f39-4a76-b454-31153a6ade8c
caps.latest.revision: 12
ms.openlocfilehash: 3c110bd5fe3ef2f790ef136556afa7c29d0b5b29
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/03/2019
ms.locfileid: "56856187"
---
# <a name="customitem-element-for-customentry-for-customcontrol-for-view-format"></a><span data-ttu-id="86467-102">Elemento CustomItem per CustomEntry per CustomControl per View (formato)</span><span class="sxs-lookup"><span data-stu-id="86467-102">CustomItem Element for CustomEntry for CustomControl for View (Format)</span></span>

<span data-ttu-id="86467-103">Definisce i dati visualizzati dalla visualizzazione del controllo personalizzato e modalità di visualizzazione.</span><span class="sxs-lookup"><span data-stu-id="86467-103">Defines what data is displayed by the custom control view and how it is displayed.</span></span> <span data-ttu-id="86467-104">Questo elemento viene usato quando si definisce una vista di controllo personalizzato.</span><span class="sxs-lookup"><span data-stu-id="86467-104">This element is used when defining a custom control view.</span></span>

<span data-ttu-id="86467-105">Elemento (formato) elemento ViewDefinitions (formato) visualizzazione elemento (formato) elemento CustomControl (formato) CustomEntries elemento di configurazione per CustomControl elemento di visualizzazione (formato) CustomEntry per CustomEntries per elemento CustomItem visualizzazione (formato) CustomEntry per visualizzazione (formato)</span><span class="sxs-lookup"><span data-stu-id="86467-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) CustomControl Element (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for View (Format) CustomItem Element for CustomEntry for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="86467-106">Sintassi</span><span class="sxs-lookup"><span data-stu-id="86467-106">Syntax</span></span>

```xml
<CustomItem>
  <ExpressionBinding>...</ExpressionBinding>
  <Frame>...</Frame>
  <NewLine/>
  <Text>TextToDisplay</Text>
</CustomItem>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="86467-107">Attributi ed elementi</span><span class="sxs-lookup"><span data-stu-id="86467-107">Attributes and Elements</span></span>

<span data-ttu-id="86467-108">Le sezioni seguenti descrivono gli attributi e gli elementi figlio dell'elemento padre del `CustomItem` elemento.</span><span class="sxs-lookup"><span data-stu-id="86467-108">The following sections describe attributes, child elements, and the parent element of the `CustomItem` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="86467-109">Attributes</span><span class="sxs-lookup"><span data-stu-id="86467-109">Attributes</span></span>

<span data-ttu-id="86467-110">Nessuna.</span><span class="sxs-lookup"><span data-stu-id="86467-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="86467-111">Elementi figlio</span><span class="sxs-lookup"><span data-stu-id="86467-111">Child Elements</span></span>

|<span data-ttu-id="86467-112">Elemento</span><span class="sxs-lookup"><span data-stu-id="86467-112">Element</span></span>|<span data-ttu-id="86467-113">Description</span><span class="sxs-lookup"><span data-stu-id="86467-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="86467-114">Elemento ExpressionBinding per CustomItem per CustomControl per visualizzazione (formato)</span><span class="sxs-lookup"><span data-stu-id="86467-114">ExpressionBinding Element for CustomItem for CustomControl for View (Format)</span></span>](./expressionbinding-element-for-customitem-for-customcontrol-for-view-format.md)|<span data-ttu-id="86467-115">Elemento facoltativo.</span><span class="sxs-lookup"><span data-stu-id="86467-115">Optional element.</span></span><br /><br /> <span data-ttu-id="86467-116">Definisce i dati che vengano visualizzati dal controllo.</span><span class="sxs-lookup"><span data-stu-id="86467-116">Defines the data that is displayed by the control.</span></span>|
|[<span data-ttu-id="86467-117">Elemento frame per CustomItem per CustomControl per visualizzazione (formato)</span><span class="sxs-lookup"><span data-stu-id="86467-117">Frame Element for CustomItem for CustomControl for View (Format)</span></span>](./frame-element-for-customitem-for-customcontrol-for-view-format.md)|<span data-ttu-id="86467-118">Elemento facoltativo.</span><span class="sxs-lookup"><span data-stu-id="86467-118">Optional element.</span></span><br /><br /> <span data-ttu-id="86467-119">Definisce i dati visualizzati dalla visualizzazione del controllo personalizzato e modalità di visualizzazione.</span><span class="sxs-lookup"><span data-stu-id="86467-119">Defines what data is displayed by the custom control view and how it is displayed.</span></span>|
|[<span data-ttu-id="86467-120">Elemento di una nuova riga per CustomItem per un controllo personalizzato per la visualizzazione (formato)</span><span class="sxs-lookup"><span data-stu-id="86467-120">NewLine Element for CustomItem for Custom Control for View (Format)</span></span>](./newline-element-for-customitem-for-customcontrol-for-view-format.md)|<span data-ttu-id="86467-121">Elemento facoltativo.</span><span class="sxs-lookup"><span data-stu-id="86467-121">Optional element.</span></span><br /><br /> <span data-ttu-id="86467-122">Aggiunge una riga vuota alla visualizzazione del controllo.</span><span class="sxs-lookup"><span data-stu-id="86467-122">Adds a blank line to the display of the control.</span></span>|
|[<span data-ttu-id="86467-123">Elemento di testo per CustomItem per CustomControl per visualizzazione (formato)</span><span class="sxs-lookup"><span data-stu-id="86467-123">Text Element for CustomItem for CustomControl for View (Format)</span></span>](./text-element-for-customitem-for-customview-for-view-format.md)|<span data-ttu-id="86467-124">Elemento facoltativo.</span><span class="sxs-lookup"><span data-stu-id="86467-124">Optional element.</span></span><br /><br /> <span data-ttu-id="86467-125">Specifica il testo aggiuntivo per i dati visualizzati dal controllo.</span><span class="sxs-lookup"><span data-stu-id="86467-125">Specifies additional text to the data displayed by the control.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="86467-126">Elementi padre</span><span class="sxs-lookup"><span data-stu-id="86467-126">Parent Elements</span></span>

|<span data-ttu-id="86467-127">Elemento</span><span class="sxs-lookup"><span data-stu-id="86467-127">Element</span></span>|<span data-ttu-id="86467-128">Description</span><span class="sxs-lookup"><span data-stu-id="86467-128">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="86467-129">Elemento CustomEntry per CustomEntries per CustomControl per visualizzazione (formato)</span><span class="sxs-lookup"><span data-stu-id="86467-129">CustomEntry Element for CustomEntries for CustomControl for View (Format)</span></span>](./customentry-element-for-customentries-for-customcontrol-for-view-format.md)|<span data-ttu-id="86467-130">Fornisce una definizione della vista del controllo personalizzato.</span><span class="sxs-lookup"><span data-stu-id="86467-130">Provides a definition of the custom control view.</span></span>|

## <a name="remarks"></a><span data-ttu-id="86467-131">Osservazioni</span><span class="sxs-lookup"><span data-stu-id="86467-131">Remarks</span></span>

## <a name="see-also"></a><span data-ttu-id="86467-132">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="86467-132">See Also</span></span>

[<span data-ttu-id="86467-133">Elemento CustomEntry per CustomEntries per visualizzazione (formato)</span><span class="sxs-lookup"><span data-stu-id="86467-133">CustomEntry Element for CustomEntries for View (Format)</span></span>](./customentry-element-for-customentries-for-customcontrol-for-view-format.md)

[<span data-ttu-id="86467-134">Elemento ExpressionBinding per CustomItem per CustomControl per visualizzazione (formato)</span><span class="sxs-lookup"><span data-stu-id="86467-134">ExpressionBinding Element for CustomItem for CustomControl for View (Format)</span></span>](./expressionbinding-element-for-customitem-for-customcontrol-for-view-format.md)

[<span data-ttu-id="86467-135">Elemento frame per CustomItem per CustomControl per visualizzazione (formato)</span><span class="sxs-lookup"><span data-stu-id="86467-135">Frame Element for CustomItem for CustomControl for View (Format)</span></span>](./frame-element-for-customitem-for-customcontrol-for-view-format.md)

[<span data-ttu-id="86467-136">Elemento di una nuova riga per CustomItem per CustomControl per visualizzazione (formato)</span><span class="sxs-lookup"><span data-stu-id="86467-136">NewLine Element for CustomItem for CustomControl for View (Format)</span></span>](./newline-element-for-customitem-for-customcontrol-for-view-format.md)

[<span data-ttu-id="86467-137">Elemento di testo per CustomItem per CustomControl per visualizzazione (formato)</span><span class="sxs-lookup"><span data-stu-id="86467-137">Text Element for CustomItem for CustomControl for View (Format)</span></span>](./text-element-for-customitem-for-customview-for-view-format.md)

[<span data-ttu-id="86467-138">La scrittura di un File di formattazione di PowerShell</span><span class="sxs-lookup"><span data-stu-id="86467-138">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
