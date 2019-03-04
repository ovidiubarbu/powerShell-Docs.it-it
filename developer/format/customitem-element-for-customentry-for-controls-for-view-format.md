---
title: Elemento CustomItem per CustomEntry per i controlli per la visualizzazione (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 33cb5350-73ef-4b79-a879-0edf051869e4
caps.latest.revision: 7
ms.openlocfilehash: 174ba6a14819f823ec39f72e49a626e781221d8c
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/03/2019
ms.locfileid: "56855607"
---
# <a name="customitem-element-for-customentry-for-controls-for-view-format"></a><span data-ttu-id="4923e-102">Elemento CustomItem per CustomEntry per Controls per View (formato)</span><span class="sxs-lookup"><span data-stu-id="4923e-102">CustomItem Element for CustomEntry for Controls for View (Format)</span></span>

<span data-ttu-id="4923e-103">Definisce i dati che vengano visualizzati dal controllo e la modalità di visualizzazione.</span><span class="sxs-lookup"><span data-stu-id="4923e-103">Defines what data is displayed by the control and how it is displayed.</span></span> <span data-ttu-id="4923e-104">Questo elemento viene usato quando si definiscono i controlli che possono essere usati da una vista.</span><span class="sxs-lookup"><span data-stu-id="4923e-104">This element is used when defining controls that can be used by a view.</span></span>

<span data-ttu-id="4923e-105">Elemento (formato) elemento ViewDefinitions (formato) visualizzazione elemento (formato) i controlli elemento (formato) controllo elemento di configurazione per i controlli elemento di visualizzazione (formato) CustomControl per il controllo per i controlli elemento di visualizzazione (formato) CustomEntries per CustomControl elemento di visualizzazione (formato) CustomEntry per CustomEntries per i controlli elemento di visualizzazione (formato) CustomItem per CustomEntry per i controlli per la visualizzazione (formato)</span><span class="sxs-lookup"><span data-stu-id="4923e-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) Controls Element (Format) Control Element for Controls for View (Format) CustomControl Element for Control for Controls for View (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for Controls for View (Format) CustomItem Element for CustomEntry for Controls for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="4923e-106">Sintassi</span><span class="sxs-lookup"><span data-stu-id="4923e-106">Syntax</span></span>

```xml
<CustomItem>
  <ExpressionBinding>...</ExpressionBinding>
  <NewLine/>
  <Text>TextToDisplay</Text>
  <Frame>...<Frame>
</CustomItem>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="4923e-107">Attributi ed elementi</span><span class="sxs-lookup"><span data-stu-id="4923e-107">Attributes and Elements</span></span>

<span data-ttu-id="4923e-108">Le sezioni seguenti descrivono gli attributi e gli elementi figlio dell'elemento padre del `CustomItem` elemento.</span><span class="sxs-lookup"><span data-stu-id="4923e-108">The following sections describe attributes, child elements, and the parent element of the `CustomItem` element.</span></span> <span data-ttu-id="4923e-109">Per altre informazioni, vedere la sezione Osservazioni.</span><span class="sxs-lookup"><span data-stu-id="4923e-109">For more information, see Remarks.</span></span>

### <a name="attributes"></a><span data-ttu-id="4923e-110">Attributes</span><span class="sxs-lookup"><span data-stu-id="4923e-110">Attributes</span></span>

<span data-ttu-id="4923e-111">Nessuna.</span><span class="sxs-lookup"><span data-stu-id="4923e-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="4923e-112">Elementi figlio</span><span class="sxs-lookup"><span data-stu-id="4923e-112">Child Elements</span></span>

|<span data-ttu-id="4923e-113">Elemento</span><span class="sxs-lookup"><span data-stu-id="4923e-113">Element</span></span>|<span data-ttu-id="4923e-114">Description</span><span class="sxs-lookup"><span data-stu-id="4923e-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="4923e-115">Elemento ExpressionBinding per CustomItem per i controlli per la visualizzazione (formato)</span><span class="sxs-lookup"><span data-stu-id="4923e-115">ExpressionBinding Element for CustomItem for Controls for View (Format)</span></span>](./expressionbinding-element-for-customitem-for-controls-for-view-format.md)|<span data-ttu-id="4923e-116">Elemento facoltativo.</span><span class="sxs-lookup"><span data-stu-id="4923e-116">Optional element.</span></span><br /><br /> <span data-ttu-id="4923e-117">Definisce i dati che vengano visualizzati dal controllo.</span><span class="sxs-lookup"><span data-stu-id="4923e-117">Defines the data that is displayed by the control.</span></span>|
|[<span data-ttu-id="4923e-118">Elemento frame per CustomItem per i controlli per la visualizzazione (formato)</span><span class="sxs-lookup"><span data-stu-id="4923e-118">Frame Element for CustomItem for Controls for View (Format)</span></span>](./frame-element-for-customitem-for-controls-for-view-format.md)|<span data-ttu-id="4923e-119">Elemento facoltativo.</span><span class="sxs-lookup"><span data-stu-id="4923e-119">Optional element.</span></span><br /><br /> <span data-ttu-id="4923e-120">Definisce come verranno visualizzati i dati, ad esempio lo spostamento di dati a sinistra o destra.</span><span class="sxs-lookup"><span data-stu-id="4923e-120">Defines how the data is displayed, such as shifting the data to the left or right.</span></span>|
|[<span data-ttu-id="4923e-121">Elemento di una nuova riga per CustomItem per i controlli per la visualizzazione (formato)</span><span class="sxs-lookup"><span data-stu-id="4923e-121">NewLine Element for CustomItem for Controls for View (Format)</span></span>](./newline-element-for-customitem-for-controls-for-view-format.md)|<span data-ttu-id="4923e-122">Elemento facoltativo.</span><span class="sxs-lookup"><span data-stu-id="4923e-122">Optional element.</span></span><br /><br /> <span data-ttu-id="4923e-123">Aggiunge una riga vuota alla visualizzazione del controllo.</span><span class="sxs-lookup"><span data-stu-id="4923e-123">Adds a blank line to the display of the control.</span></span>|
|[<span data-ttu-id="4923e-124">Elemento di testo per CustomItem per i controlli per la visualizzazione (formato)</span><span class="sxs-lookup"><span data-stu-id="4923e-124">Text Element for CustomItem for Controls for View (Format)</span></span>](./text-element-for-customitem-for-controls-for-view-format.md)|<span data-ttu-id="4923e-125">Elemento facoltativo.</span><span class="sxs-lookup"><span data-stu-id="4923e-125">Optional element.</span></span><br /><br /> <span data-ttu-id="4923e-126">Aggiunge testo, ad esempio parentesi o parentesi quadre, alla visualizzazione del controllo.</span><span class="sxs-lookup"><span data-stu-id="4923e-126">Adds text, such as parentheses or brackets, to the display of the control.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="4923e-127">Elementi padre</span><span class="sxs-lookup"><span data-stu-id="4923e-127">Parent Elements</span></span>

|<span data-ttu-id="4923e-128">Elemento</span><span class="sxs-lookup"><span data-stu-id="4923e-128">Element</span></span>|<span data-ttu-id="4923e-129">Description</span><span class="sxs-lookup"><span data-stu-id="4923e-129">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="4923e-130">Elemento CustomEntry per CustomEntries per i controlli per la visualizzazione (formato)</span><span class="sxs-lookup"><span data-stu-id="4923e-130">CustomEntry Element for CustomEntries for Controls for View (Format)</span></span>](./customentry-element-for-customentries-for-controls-for-view-format.md)|<span data-ttu-id="4923e-131">Fornisce una definizione del controllo.</span><span class="sxs-lookup"><span data-stu-id="4923e-131">Provides a definition of the control.</span></span>|

## <a name="remarks"></a><span data-ttu-id="4923e-132">Osservazioni</span><span class="sxs-lookup"><span data-stu-id="4923e-132">Remarks</span></span>

<span data-ttu-id="4923e-133">Quando si specificano gli elementi figlio del `CustomItem` elemento, tenere presente quanto segue:</span><span class="sxs-lookup"><span data-stu-id="4923e-133">When specifying the child elements of the `CustomItem` element, keep the following in mind:</span></span>

- <span data-ttu-id="4923e-134">Gli elementi figlio devono essere aggiunti nella sequenza seguente: `ExpressionBinding`, `NewLine`, `Text`, e `Frame`.</span><span class="sxs-lookup"><span data-stu-id="4923e-134">The child elements must be added in the following sequence: `ExpressionBinding`, `NewLine`, `Text`, and `Frame`.</span></span>

- <span data-ttu-id="4923e-135">Non è definito alcun limite massimo al numero di sequenze che è possibile specificare.</span><span class="sxs-lookup"><span data-stu-id="4923e-135">There is no maximum limit to the number of sequences that you can specify.</span></span>

- <span data-ttu-id="4923e-136">In ogni sequenza, non è definito alcun limite massimo al numero di `ExpressionBinding` gli elementi che è possibile usare.</span><span class="sxs-lookup"><span data-stu-id="4923e-136">In each sequence, there is no maximum limit to the number of `ExpressionBinding` elements that you can use.</span></span>

## <a name="see-also"></a><span data-ttu-id="4923e-137">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="4923e-137">See Also</span></span>

[<span data-ttu-id="4923e-138">Elemento ExpressionBinding per CustomItem per i controlli per la visualizzazione (formato)</span><span class="sxs-lookup"><span data-stu-id="4923e-138">ExpressionBinding Element for CustomItem for Controls for View (Format)</span></span>](./expressionbinding-element-for-customitem-for-controls-for-view-format.md)

[<span data-ttu-id="4923e-139">Elemento frame per CustomItem per i controlli per la visualizzazione (formato)</span><span class="sxs-lookup"><span data-stu-id="4923e-139">Frame Element for CustomItem for Controls for View (Format)</span></span>](./frame-element-for-customitem-for-controls-for-view-format.md)

[<span data-ttu-id="4923e-140">Elemento di una nuova riga per CustomItem per i controlli per la visualizzazione (formato)</span><span class="sxs-lookup"><span data-stu-id="4923e-140">NewLine Element for CustomItem for Controls for View (Format)</span></span>](./newline-element-for-customitem-for-controls-for-view-format.md)

[<span data-ttu-id="4923e-141">Elemento di testo per CustomItem per i controlli per la visualizzazione (formato)</span><span class="sxs-lookup"><span data-stu-id="4923e-141">Text Element for CustomItem for Controls for View (Format)</span></span>](./text-element-for-customitem-for-controls-for-view-format.md)

[<span data-ttu-id="4923e-142">La scrittura di un File di formattazione di PowerShell</span><span class="sxs-lookup"><span data-stu-id="4923e-142">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
