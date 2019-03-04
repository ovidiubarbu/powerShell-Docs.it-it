---
title: Elemento dei frame per CustomItem per i controlli per la visualizzazione (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: a5729091-78a9-4bc1-abac-210bc20c6dbe
caps.latest.revision: 7
ms.openlocfilehash: f93dc20a9c5f87c14605578062b1e60f5a3d25cf
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/03/2019
ms.locfileid: "56859817"
---
# <a name="frame-element-for-customitem-for-controls-for-view-format"></a><span data-ttu-id="082f4-102">Elemento Frame per CustomItem per Controls per View (formato)</span><span class="sxs-lookup"><span data-stu-id="082f4-102">Frame Element for CustomItem for Controls for View (Format)</span></span>

<span data-ttu-id="082f4-103">Definisce come verranno visualizzati i dati, ad esempio lo spostamento di dati a sinistra o destra.</span><span class="sxs-lookup"><span data-stu-id="082f4-103">Defines how the data is displayed, such as shifting the data to the left or right.</span></span> <span data-ttu-id="082f4-104">Questo elemento viene usato quando si definiscono i controlli che possono essere usati da una vista.</span><span class="sxs-lookup"><span data-stu-id="082f4-104">This element is used when defining controls that can be used by a view.</span></span>

<span data-ttu-id="082f4-105">Elemento (formato) elemento ViewDefinitions (formato) visualizzazione elemento (formato) i controlli elemento (formato) controllo elemento di configurazione per i controlli elemento di visualizzazione (formato) CustomControl per il controllo per i controlli elemento di visualizzazione (formato) CustomEntries per CustomControl elemento di visualizzazione (formato) CustomEntry per CustomEntries per i controlli elemento di visualizzazione (formato) CustomItem per CustomEntry per i controlli elemento di visualizzazione (formato) Frame per CustomItem per i controlli per la visualizzazione (formato)</span><span class="sxs-lookup"><span data-stu-id="082f4-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) Controls Element (Format) Control Element for Controls for View (Format) CustomControl Element for Control for Controls for View (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for Controls for View (Format) CustomItem Element for CustomEntry for Controls for View (Format) Frame Element for CustomItem for Controls for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="082f4-106">Sintassi</span><span class="sxs-lookup"><span data-stu-id="082f4-106">Syntax</span></span>

```xml
<Frame>
  <LeftIndent>NumberOfCharactersToShift</LeftIndent>
  <RightIndent>NumberOfCharactersToShift</RightIndent>
  <FirstLineHanging>NumberOfCharactersToShift</FirstLineHanging>
  <FirstLineIndent>NumberOfCharactersToShift</FirstLineIndent>
  <CustomItem>...</CustomItem>
</Frame>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="082f4-107">Attributi ed elementi</span><span class="sxs-lookup"><span data-stu-id="082f4-107">Attributes and Elements</span></span>

<span data-ttu-id="082f4-108">Le sezioni seguenti descrivono gli attributi e gli elementi figlio dell'elemento padre del `Frame` elemento.</span><span class="sxs-lookup"><span data-stu-id="082f4-108">The following sections describe attributes, child elements, and the parent element of the `Frame` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="082f4-109">Attributes</span><span class="sxs-lookup"><span data-stu-id="082f4-109">Attributes</span></span>

<span data-ttu-id="082f4-110">Nessuna.</span><span class="sxs-lookup"><span data-stu-id="082f4-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="082f4-111">Elementi figlio</span><span class="sxs-lookup"><span data-stu-id="082f4-111">Child Elements</span></span>

|<span data-ttu-id="082f4-112">Elemento</span><span class="sxs-lookup"><span data-stu-id="082f4-112">Element</span></span>|<span data-ttu-id="082f4-113">Description</span><span class="sxs-lookup"><span data-stu-id="082f4-113">Description</span></span>|
|-------------|-----------------|
|`CustomItem Element`|<span data-ttu-id="082f4-114">Elemento obbligatorio</span><span class="sxs-lookup"><span data-stu-id="082f4-114">Required Element</span></span>|
|[<span data-ttu-id="082f4-115">Elemento FirstLineHanging del Frame di controlli di visualizzazione (formato)</span><span class="sxs-lookup"><span data-stu-id="082f4-115">FirstLineHanging Element of Frame of Controls of View (Format)</span></span>](./firstlinehanging-element-for-frame-for-controls-for-view-format.md)|<span data-ttu-id="082f4-116">Elemento facoltativo.</span><span class="sxs-lookup"><span data-stu-id="082f4-116">Optional element.</span></span><br /><br /> <span data-ttu-id="082f4-117">Specifica il numero di caratteri nella prima riga viene spostata a sinistra.</span><span class="sxs-lookup"><span data-stu-id="082f4-117">Specifies how many characters the first line is shifted to the left.</span></span>|
|[<span data-ttu-id="082f4-118">Elemento FirstLineIndent del Frame di controlli di visualizzazione (formato)</span><span class="sxs-lookup"><span data-stu-id="082f4-118">FirstLineIndent Element of Frame of Controls of View (Format)</span></span>](./firstlineindent-element-for-frame-for-controls-for-view-format.md)|<span data-ttu-id="082f4-119">Elemento facoltativo.</span><span class="sxs-lookup"><span data-stu-id="082f4-119">Optional element.</span></span><br /><br /> <span data-ttu-id="082f4-120">Specifica il numero di caratteri nella prima riga viene spostata a destra.</span><span class="sxs-lookup"><span data-stu-id="082f4-120">Specifies how many characters the first line is shifted to the right.</span></span>|
|[<span data-ttu-id="082f4-121">Elemento LeftIndent del Frame di controlli di visualizzazione (formato)</span><span class="sxs-lookup"><span data-stu-id="082f4-121">LeftIndent Element of Frame of Controls of View (Format)</span></span>](./leftindent-element-for-frame-for-controls-for-view-format.md)|<span data-ttu-id="082f4-122">Elemento facoltativo.</span><span class="sxs-lookup"><span data-stu-id="082f4-122">Optional element.</span></span><br /><br /> <span data-ttu-id="082f4-123">Specifica quanti caratteri di dati viene spostati dal margine sinistro.</span><span class="sxs-lookup"><span data-stu-id="082f4-123">Specifies how many characters the data is shifted away from the left margin.</span></span>|
|[<span data-ttu-id="082f4-124">Elemento RightIndent del Frame di controlli di visualizzazione (formato)</span><span class="sxs-lookup"><span data-stu-id="082f4-124">RightIndent Element of Frame of Controls of View (Format)</span></span>](./rightindent-element-for-frame-for-controls-for-view-format.md)|<span data-ttu-id="082f4-125">Elemento facoltativo.</span><span class="sxs-lookup"><span data-stu-id="082f4-125">Optional element.</span></span><br /><br /> <span data-ttu-id="082f4-126">Specifica quanti caratteri di dati viene spostati dal margine destro.</span><span class="sxs-lookup"><span data-stu-id="082f4-126">Specifies how many characters the data is shifted away from the right margin.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="082f4-127">Elementi padre</span><span class="sxs-lookup"><span data-stu-id="082f4-127">Parent Elements</span></span>

|<span data-ttu-id="082f4-128">Elemento</span><span class="sxs-lookup"><span data-stu-id="082f4-128">Element</span></span>|<span data-ttu-id="082f4-129">Description</span><span class="sxs-lookup"><span data-stu-id="082f4-129">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="082f4-130">Elemento CustomItem per CustomEntry per i controlli per la visualizzazione (formato)</span><span class="sxs-lookup"><span data-stu-id="082f4-130">CustomItem Element for CustomEntry for Controls for View (Format)</span></span>](./customitem-element-for-customentry-for-controls-for-view-format.md)|<span data-ttu-id="082f4-131">Definisce i dati che vengano visualizzati dal controllo e la modalità di visualizzazione.</span><span class="sxs-lookup"><span data-stu-id="082f4-131">Defines what data is displayed by the control and how it is displayed.</span></span>|

## <a name="remarks"></a><span data-ttu-id="082f4-132">Osservazioni</span><span class="sxs-lookup"><span data-stu-id="082f4-132">Remarks</span></span>

<span data-ttu-id="082f4-133">Non è possibile specificare il [FirstLineHanging](./firstlinehanging-element-for-frame-for-controls-for-view-format.md) e il [FirstLineIndent](./firstlineindent-element-for-frame-for-controls-for-view-format.md) elementi nello stesso `Frame` elemento.</span><span class="sxs-lookup"><span data-stu-id="082f4-133">You cannot specify the [FirstLineHanging](./firstlinehanging-element-for-frame-for-controls-for-view-format.md) and the [FirstLineIndent](./firstlineindent-element-for-frame-for-controls-for-view-format.md) elements in the same `Frame` element.</span></span>

## <a name="see-also"></a><span data-ttu-id="082f4-134">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="082f4-134">See Also</span></span>

[<span data-ttu-id="082f4-135">Elemento FirstLineHanging del Frame di controlli di visualizzazione (formato)</span><span class="sxs-lookup"><span data-stu-id="082f4-135">FirstLineHanging Element of Frame of Controls of View (Format)</span></span>](./firstlinehanging-element-for-frame-for-controls-for-view-format.md)

[<span data-ttu-id="082f4-136">Elemento FirstLineIndent del Frame di controlli di visualizzazione (formato)</span><span class="sxs-lookup"><span data-stu-id="082f4-136">FirstLineIndent Element of Frame of Controls of View (Format)</span></span>](./firstlineindent-element-for-frame-for-controls-for-view-format.md)

[<span data-ttu-id="082f4-137">Elemento LeftIndent del Frame di controlli di visualizzazione (formato)</span><span class="sxs-lookup"><span data-stu-id="082f4-137">LeftIndent Element of Frame of Controls of View (Format)</span></span>](./leftindent-element-for-frame-for-controls-for-view-format.md)

[<span data-ttu-id="082f4-138">Elemento RightIndent del Frame di controlli di visualizzazione (formato)</span><span class="sxs-lookup"><span data-stu-id="082f4-138">RightIndent Element of Frame of Controls of View (Format)</span></span>](./rightindent-element-for-frame-for-controls-for-view-format.md)

[<span data-ttu-id="082f4-139">Elemento CustomItem per CustomEntry per i controlli per la visualizzazione (formato)</span><span class="sxs-lookup"><span data-stu-id="082f4-139">CustomItem Element for CustomEntry for Controls for View (Format)</span></span>](./customitem-element-for-customentry-for-controls-for-view-format.md)

[<span data-ttu-id="082f4-140">La scrittura di un File di formattazione di PowerShell</span><span class="sxs-lookup"><span data-stu-id="082f4-140">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
