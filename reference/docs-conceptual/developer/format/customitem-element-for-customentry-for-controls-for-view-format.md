---
title: Elemento CustomItem per CustomEntry per i controlli per la visualizzazione (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 33cb5350-73ef-4b79-a879-0edf051869e4
caps.latest.revision: 7
ms.openlocfilehash: 174ba6a14819f823ec39f72e49a626e781221d8c
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/15/2019
ms.locfileid: "72363940"
---
# <a name="customitem-element-for-customentry-for-controls-for-view-format"></a><span data-ttu-id="0aee4-102">Elemento CustomItem per CustomEntry per Controls per View (formato)</span><span class="sxs-lookup"><span data-stu-id="0aee4-102">CustomItem Element for CustomEntry for Controls for View (Format)</span></span>

<span data-ttu-id="0aee4-103">Definisce quali dati vengono visualizzati dal controllo e come vengono visualizzati.</span><span class="sxs-lookup"><span data-stu-id="0aee4-103">Defines what data is displayed by the control and how it is displayed.</span></span> <span data-ttu-id="0aee4-104">Questo elemento viene utilizzato per la definizione di controlli che possono essere utilizzati da una visualizzazione.</span><span class="sxs-lookup"><span data-stu-id="0aee4-104">This element is used when defining controls that can be used by a view.</span></span>

<span data-ttu-id="0aee4-105">Elemento di configurazione (Format) elemento ViewDefinitions (Format) elemento di visualizzazione (Format) controlli elemento (Format) elemento di controllo per i controlli per la visualizzazione (formato) elemento CustomControl per il controllo per i controlli per la visualizzazione (formato) elemento CustomEntries per CustomControl per la visualizzazione (formato) elemento CustomEntry per CustomEntries per i controlli per la visualizzazione (formato) CustomItem elemento per CustomEntry per i controlli per la visualizzazione (formato)</span><span class="sxs-lookup"><span data-stu-id="0aee4-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) Controls Element (Format) Control Element for Controls for View (Format) CustomControl Element for Control for Controls for View (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for Controls for View (Format) CustomItem Element for CustomEntry for Controls for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="0aee4-106">Sintassi</span><span class="sxs-lookup"><span data-stu-id="0aee4-106">Syntax</span></span>

```xml
<CustomItem>
  <ExpressionBinding>...</ExpressionBinding>
  <NewLine/>
  <Text>TextToDisplay</Text>
  <Frame>...<Frame>
</CustomItem>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="0aee4-107">Attributi ed elementi</span><span class="sxs-lookup"><span data-stu-id="0aee4-107">Attributes and Elements</span></span>

<span data-ttu-id="0aee4-108">Nelle sezioni seguenti vengono descritti gli attributi, gli elementi figlio e l'elemento padre dell'elemento `CustomItem`.</span><span class="sxs-lookup"><span data-stu-id="0aee4-108">The following sections describe attributes, child elements, and the parent element of the `CustomItem` element.</span></span> <span data-ttu-id="0aee4-109">Per ulteriori informazioni, vedere la sezione Osservazioni.</span><span class="sxs-lookup"><span data-stu-id="0aee4-109">For more information, see Remarks.</span></span>

### <a name="attributes"></a><span data-ttu-id="0aee4-110">Attributi</span><span class="sxs-lookup"><span data-stu-id="0aee4-110">Attributes</span></span>

<span data-ttu-id="0aee4-111">Nessuna.</span><span class="sxs-lookup"><span data-stu-id="0aee4-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="0aee4-112">Elementi figlio</span><span class="sxs-lookup"><span data-stu-id="0aee4-112">Child Elements</span></span>

|<span data-ttu-id="0aee4-113">Elemento</span><span class="sxs-lookup"><span data-stu-id="0aee4-113">Element</span></span>|<span data-ttu-id="0aee4-114">Description</span><span class="sxs-lookup"><span data-stu-id="0aee4-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="0aee4-115">Elemento expressiongroup per CustomItem per i controlli per la visualizzazione (Format)</span><span class="sxs-lookup"><span data-stu-id="0aee4-115">ExpressionBinding Element for CustomItem for Controls for View (Format)</span></span>](./expressionbinding-element-for-customitem-for-controls-for-view-format.md)|<span data-ttu-id="0aee4-116">Elemento facoltativo.</span><span class="sxs-lookup"><span data-stu-id="0aee4-116">Optional element.</span></span><br /><br /> <span data-ttu-id="0aee4-117">Definisce i dati visualizzati dal controllo.</span><span class="sxs-lookup"><span data-stu-id="0aee4-117">Defines the data that is displayed by the control.</span></span>|
|[<span data-ttu-id="0aee4-118">Elemento frame per CustomItem per i controlli per la visualizzazione (Format)</span><span class="sxs-lookup"><span data-stu-id="0aee4-118">Frame Element for CustomItem for Controls for View (Format)</span></span>](./frame-element-for-customitem-for-controls-for-view-format.md)|<span data-ttu-id="0aee4-119">Elemento facoltativo.</span><span class="sxs-lookup"><span data-stu-id="0aee4-119">Optional element.</span></span><br /><br /> <span data-ttu-id="0aee4-120">Definisce la modalità di visualizzazione dei dati, ad esempio lo spostamento dei dati verso sinistra o verso destra.</span><span class="sxs-lookup"><span data-stu-id="0aee4-120">Defines how the data is displayed, such as shifting the data to the left or right.</span></span>|
|[<span data-ttu-id="0aee4-121">Elemento NewLine per CustomItem per i controlli per la visualizzazione (Format)</span><span class="sxs-lookup"><span data-stu-id="0aee4-121">NewLine Element for CustomItem for Controls for View (Format)</span></span>](./newline-element-for-customitem-for-controls-for-view-format.md)|<span data-ttu-id="0aee4-122">Elemento facoltativo.</span><span class="sxs-lookup"><span data-stu-id="0aee4-122">Optional element.</span></span><br /><br /> <span data-ttu-id="0aee4-123">Aggiunge una riga vuota alla visualizzazione del controllo.</span><span class="sxs-lookup"><span data-stu-id="0aee4-123">Adds a blank line to the display of the control.</span></span>|
|[<span data-ttu-id="0aee4-124">Elemento text per CustomItem per i controlli per la visualizzazione (Format)</span><span class="sxs-lookup"><span data-stu-id="0aee4-124">Text Element for CustomItem for Controls for View (Format)</span></span>](./text-element-for-customitem-for-controls-for-view-format.md)|<span data-ttu-id="0aee4-125">Elemento facoltativo.</span><span class="sxs-lookup"><span data-stu-id="0aee4-125">Optional element.</span></span><br /><br /> <span data-ttu-id="0aee4-126">Aggiunge un testo, ad esempio le parentesi o le parentesi, alla visualizzazione del controllo.</span><span class="sxs-lookup"><span data-stu-id="0aee4-126">Adds text, such as parentheses or brackets, to the display of the control.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="0aee4-127">Elementi padre</span><span class="sxs-lookup"><span data-stu-id="0aee4-127">Parent Elements</span></span>

|<span data-ttu-id="0aee4-128">Elemento</span><span class="sxs-lookup"><span data-stu-id="0aee4-128">Element</span></span>|<span data-ttu-id="0aee4-129">Description</span><span class="sxs-lookup"><span data-stu-id="0aee4-129">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="0aee4-130">Elemento CustomEntry per CustomEntries per i controlli per la visualizzazione (Format)</span><span class="sxs-lookup"><span data-stu-id="0aee4-130">CustomEntry Element for CustomEntries for Controls for View (Format)</span></span>](./customentry-element-for-customentries-for-controls-for-view-format.md)|<span data-ttu-id="0aee4-131">Fornisce una definizione del controllo.</span><span class="sxs-lookup"><span data-stu-id="0aee4-131">Provides a definition of the control.</span></span>|

## <a name="remarks"></a><span data-ttu-id="0aee4-132">Osservazioni</span><span class="sxs-lookup"><span data-stu-id="0aee4-132">Remarks</span></span>

<span data-ttu-id="0aee4-133">Quando si specificano gli elementi figlio dell'elemento `CustomItem`, tenere presente quanto segue:</span><span class="sxs-lookup"><span data-stu-id="0aee4-133">When specifying the child elements of the `CustomItem` element, keep the following in mind:</span></span>

- <span data-ttu-id="0aee4-134">Gli elementi figlio devono essere aggiunti nella sequenza seguente: `ExpressionBinding`, `NewLine`, `Text` e `Frame`.</span><span class="sxs-lookup"><span data-stu-id="0aee4-134">The child elements must be added in the following sequence: `ExpressionBinding`, `NewLine`, `Text`, and `Frame`.</span></span>

- <span data-ttu-id="0aee4-135">Non esiste un limite massimo per il numero di sequenze che è possibile specificare.</span><span class="sxs-lookup"><span data-stu-id="0aee4-135">There is no maximum limit to the number of sequences that you can specify.</span></span>

- <span data-ttu-id="0aee4-136">In ogni sequenza non esiste alcun limite massimo per il numero di elementi `ExpressionBinding` che è possibile usare.</span><span class="sxs-lookup"><span data-stu-id="0aee4-136">In each sequence, there is no maximum limit to the number of `ExpressionBinding` elements that you can use.</span></span>

## <a name="see-also"></a><span data-ttu-id="0aee4-137">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="0aee4-137">See Also</span></span>

[<span data-ttu-id="0aee4-138">Elemento expressiongroup per CustomItem per i controlli per la visualizzazione (Format)</span><span class="sxs-lookup"><span data-stu-id="0aee4-138">ExpressionBinding Element for CustomItem for Controls for View (Format)</span></span>](./expressionbinding-element-for-customitem-for-controls-for-view-format.md)

[<span data-ttu-id="0aee4-139">Elemento frame per CustomItem per i controlli per la visualizzazione (Format)</span><span class="sxs-lookup"><span data-stu-id="0aee4-139">Frame Element for CustomItem for Controls for View (Format)</span></span>](./frame-element-for-customitem-for-controls-for-view-format.md)

[<span data-ttu-id="0aee4-140">Elemento NewLine per CustomItem per i controlli per la visualizzazione (Format)</span><span class="sxs-lookup"><span data-stu-id="0aee4-140">NewLine Element for CustomItem for Controls for View (Format)</span></span>](./newline-element-for-customitem-for-controls-for-view-format.md)

[<span data-ttu-id="0aee4-141">Elemento text per CustomItem per i controlli per la visualizzazione (Format)</span><span class="sxs-lookup"><span data-stu-id="0aee4-141">Text Element for CustomItem for Controls for View (Format)</span></span>](./text-element-for-customitem-for-controls-for-view-format.md)

[<span data-ttu-id="0aee4-142">Scrittura di un file di formattazione di PowerShell</span><span class="sxs-lookup"><span data-stu-id="0aee4-142">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
