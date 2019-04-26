---
title: Elemento CustomItem per CustomEntry per i controlli per la configurazione (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 73fb11ee-0ebd-477a-ac36-acdfbb32e70d
caps.latest.revision: 7
ms.openlocfilehash: bd0cb69770817ec215ddb1862a43a838baddefcf
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62066431"
---
# <a name="customitem-element-for-customentry-for-controls-for-configuration-format"></a><span data-ttu-id="2bbb6-102">Elemento CustomItem per CustomEntry per Controls per Configuration (formato)</span><span class="sxs-lookup"><span data-stu-id="2bbb6-102">CustomItem Element for CustomEntry for Controls for Configuration (Format)</span></span>

<span data-ttu-id="2bbb6-103">Definisce i dati che vengano visualizzati dal controllo e la modalità di visualizzazione.</span><span class="sxs-lookup"><span data-stu-id="2bbb6-103">Defines what data is displayed by the control and how it is displayed.</span></span> <span data-ttu-id="2bbb6-104">Questo elemento viene usato quando si definisce un controllo comune che può essere usato da tutte le visualizzazioni nel file di formattazione.</span><span class="sxs-lookup"><span data-stu-id="2bbb6-104">This element is used when defining a common control that can be used by all the views in the formatting file.</span></span>

<span data-ttu-id="2bbb6-105">Configurazione (formato) i controlli elemento di configurazione (formato) elemento di controllo per i controlli di configurazione (formato) CustomControl elemento per il controllo per elemento di configurazione (formato) CustomEntries per CustomControl per Configuration ( Elemento CustomEntry Format) per CustomControl per i controlli per elemento di configurazione (formato) CustomItem per CustomEntry per i controlli per la configurazione</span><span class="sxs-lookup"><span data-stu-id="2bbb6-105">Configuration Element (Format) Controls Element of Configuration (Format) Control Element for Controls for Configuration (Format) CustomControl Element for Control for Configuration (Format) CustomEntries Element for CustomControl for Configuration (Format) CustomEntry Element for CustomControl for Controls for Configuration (Format) CustomItem Element for CustomEntry for Controls for Configuration</span></span>

## <a name="syntax"></a><span data-ttu-id="2bbb6-106">Sintassi</span><span class="sxs-lookup"><span data-stu-id="2bbb6-106">Syntax</span></span>

```xml
<CustomItem>
  <ExpressionBinding>...</ExpressionBinding>
  <NewLine/>
  <Text>TextToDisplay</Text>
  <Frame>...</Frame>
</CustomItem>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="2bbb6-107">Elementi e attributi</span><span class="sxs-lookup"><span data-stu-id="2bbb6-107">Attributes and Elements</span></span>

<span data-ttu-id="2bbb6-108">Le sezioni seguenti descrivono gli attributi e gli elementi figlio dell'elemento padre del `CustomItem` elemento.</span><span class="sxs-lookup"><span data-stu-id="2bbb6-108">The following sections describe attributes, child elements, and the parent element of the `CustomItem` element.</span></span> <span data-ttu-id="2bbb6-109">Per altre informazioni, vedere la sezione Osservazioni.</span><span class="sxs-lookup"><span data-stu-id="2bbb6-109">For more information, see Remarks.</span></span>

### <a name="attributes"></a><span data-ttu-id="2bbb6-110">Attributes</span><span class="sxs-lookup"><span data-stu-id="2bbb6-110">Attributes</span></span>

<span data-ttu-id="2bbb6-111">Nessuna.</span><span class="sxs-lookup"><span data-stu-id="2bbb6-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="2bbb6-112">Elementi figlio</span><span class="sxs-lookup"><span data-stu-id="2bbb6-112">Child Elements</span></span>

|<span data-ttu-id="2bbb6-113">Elemento</span><span class="sxs-lookup"><span data-stu-id="2bbb6-113">Element</span></span>|<span data-ttu-id="2bbb6-114">Description</span><span class="sxs-lookup"><span data-stu-id="2bbb6-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="2bbb6-115">Elemento ExpressionBinding per CustomItem per i controlli per la configurazione (formato)</span><span class="sxs-lookup"><span data-stu-id="2bbb6-115">ExpressionBinding Element for CustomItem for Controls for Configuration (Format)</span></span>](./expressionbinding-element-for-customitem-for-controls-for-configuration-format.md)|<span data-ttu-id="2bbb6-116">Elemento facoltativo.</span><span class="sxs-lookup"><span data-stu-id="2bbb6-116">Optional element.</span></span><br /><br /> <span data-ttu-id="2bbb6-117">Definisce i dati che vengano visualizzati dal controllo.</span><span class="sxs-lookup"><span data-stu-id="2bbb6-117">Defines the data that is displayed by the control.</span></span>|
|[<span data-ttu-id="2bbb6-118">Elemento frame per CustomItem per i controlli per la configurazione (formato)</span><span class="sxs-lookup"><span data-stu-id="2bbb6-118">Frame Element for CustomItem for Controls for Configuration (Format)</span></span>](./frame-element-for-customitem-for-controls-for-configuration-format.md)|<span data-ttu-id="2bbb6-119">Elemento facoltativo.</span><span class="sxs-lookup"><span data-stu-id="2bbb6-119">Optional element.</span></span><br /><br /> <span data-ttu-id="2bbb6-120">Definisce come verranno visualizzati i dati, ad esempio lo spostamento di dati a sinistra o destra.</span><span class="sxs-lookup"><span data-stu-id="2bbb6-120">Defines how the data is displayed, such as shifting the data to the left or right.</span></span>|
|[<span data-ttu-id="2bbb6-121">Elemento di una nuova riga per CustomItem per i controlli per la configurazione (formato)</span><span class="sxs-lookup"><span data-stu-id="2bbb6-121">NewLine Element for CustomItem for Controls for Configuration (Format)</span></span>](./newline-element-for-customitem-for-controls-for-configuration-format.md)|<span data-ttu-id="2bbb6-122">Elemento facoltativo.</span><span class="sxs-lookup"><span data-stu-id="2bbb6-122">Optional element.</span></span><br /><br /> <span data-ttu-id="2bbb6-123">Aggiunge una riga vuota alla visualizzazione del controllo.</span><span class="sxs-lookup"><span data-stu-id="2bbb6-123">Adds a blank line to the display of the control.</span></span>|
|[<span data-ttu-id="2bbb6-124">Elemento di testo per CustomItem per i controlli per la configurazione (formato)</span><span class="sxs-lookup"><span data-stu-id="2bbb6-124">Text Element for CustomItem for Controls for Configuration (Format)</span></span>](./text-element-for-customitem-for-controls-for-configuration-format.md)|<span data-ttu-id="2bbb6-125">Elemento facoltativo.</span><span class="sxs-lookup"><span data-stu-id="2bbb6-125">Optional element.</span></span><br /><br /> <span data-ttu-id="2bbb6-126">Aggiunge testo, ad esempio parentesi o parentesi quadre, alla visualizzazione del controllo.</span><span class="sxs-lookup"><span data-stu-id="2bbb6-126">Adds text, such as parentheses or brackets, to the display of the control.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="2bbb6-127">Elementi padre</span><span class="sxs-lookup"><span data-stu-id="2bbb6-127">Parent Elements</span></span>

|<span data-ttu-id="2bbb6-128">Elemento</span><span class="sxs-lookup"><span data-stu-id="2bbb6-128">Element</span></span>|<span data-ttu-id="2bbb6-129">Description</span><span class="sxs-lookup"><span data-stu-id="2bbb6-129">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="2bbb6-130">Elemento CustomEntry per CustomControl per i controlli per la configurazione (formato)</span><span class="sxs-lookup"><span data-stu-id="2bbb6-130">CustomEntry Element for CustomControl for Controls for Configuration (Format)</span></span>](./customentry-element-for-customcontrol-for-controls-for-configuration-format.md)|<span data-ttu-id="2bbb6-131">Fornisce una definizione del controllo.</span><span class="sxs-lookup"><span data-stu-id="2bbb6-131">Provides a definition of the control.</span></span>|

## <a name="remarks"></a><span data-ttu-id="2bbb6-132">Osservazioni</span><span class="sxs-lookup"><span data-stu-id="2bbb6-132">Remarks</span></span>

<span data-ttu-id="2bbb6-133">Quando si specificano gli elementi figlio del `CustomItem` elemento, tenere presente quanto segue:</span><span class="sxs-lookup"><span data-stu-id="2bbb6-133">When specifying the child elements of the `CustomItem` element, keep the following in mind:</span></span>

- <span data-ttu-id="2bbb6-134">Gli elementi figlio devono essere aggiunti nella sequenza seguente: `ExpressionBinding`, `NewLine`, `Text`, e `Frame`.</span><span class="sxs-lookup"><span data-stu-id="2bbb6-134">The child elements must be added in the following sequence: `ExpressionBinding`, `NewLine`, `Text`, and `Frame`.</span></span>

- <span data-ttu-id="2bbb6-135">Non è definito alcun limite massimo al numero di sequenze che è possibile specificare.</span><span class="sxs-lookup"><span data-stu-id="2bbb6-135">There is no maximum limit to the number of sequences that you can specify.</span></span>

- <span data-ttu-id="2bbb6-136">In ogni sequenza, non è definito alcun limite massimo al numero di `ExpressionBinding` gli elementi che è possibile usare.</span><span class="sxs-lookup"><span data-stu-id="2bbb6-136">In each sequence, there is no maximum limit to the number of `ExpressionBinding` elements that you can use.</span></span>

## <a name="see-also"></a><span data-ttu-id="2bbb6-137">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="2bbb6-137">See Also</span></span>

[<span data-ttu-id="2bbb6-138">Elemento ExpressionBinding per CustomItem per i controlli per la configurazione (formato)</span><span class="sxs-lookup"><span data-stu-id="2bbb6-138">ExpressionBinding Element for CustomItem for Controls for Configuration (Format)</span></span>](./expressionbinding-element-for-customitem-for-controls-for-configuration-format.md)

[<span data-ttu-id="2bbb6-139">Elemento frame per CustomItem per i controlli per la configurazione (formato)</span><span class="sxs-lookup"><span data-stu-id="2bbb6-139">Frame Element for CustomItem for Controls for Configuration (Format)</span></span>](./frame-element-for-customitem-for-controls-for-configuration-format.md)

[<span data-ttu-id="2bbb6-140">Elemento di una nuova riga per CustomItem per i controlli per la configurazione (formato)</span><span class="sxs-lookup"><span data-stu-id="2bbb6-140">NewLine Element for CustomItem for Controls for Configuration (Format)</span></span>](./newline-element-for-customitem-for-controls-for-configuration-format.md)

[<span data-ttu-id="2bbb6-141">Elemento di testo per CustomItem per i controlli per la configurazione (formato)</span><span class="sxs-lookup"><span data-stu-id="2bbb6-141">Text Element for CustomItem for Controls for Configuration (Format)</span></span>](./text-element-for-customitem-for-controls-for-configuration-format.md)

[<span data-ttu-id="2bbb6-142">La scrittura di un File di formattazione di PowerShell</span><span class="sxs-lookup"><span data-stu-id="2bbb6-142">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
