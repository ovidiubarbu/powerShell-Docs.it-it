---
title: Elemento CustomItem per CustomEntry per i controlli per la configurazione (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 73fb11ee-0ebd-477a-ac36-acdfbb32e70d
caps.latest.revision: 7
ms.openlocfilehash: bd0cb69770817ec215ddb1862a43a838baddefcf
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/15/2019
ms.locfileid: "72364030"
---
# <a name="customitem-element-for-customentry-for-controls-for-configuration-format"></a><span data-ttu-id="0c2c0-102">Elemento CustomItem per CustomEntry per Controls per Configuration (formato)</span><span class="sxs-lookup"><span data-stu-id="0c2c0-102">CustomItem Element for CustomEntry for Controls for Configuration (Format)</span></span>

<span data-ttu-id="0c2c0-103">Definisce quali dati vengono visualizzati dal controllo e come vengono visualizzati.</span><span class="sxs-lookup"><span data-stu-id="0c2c0-103">Defines what data is displayed by the control and how it is displayed.</span></span> <span data-ttu-id="0c2c0-104">Questo elemento viene usato quando si definisce un controllo comune che può essere usato da tutte le visualizzazioni nel file di formattazione.</span><span class="sxs-lookup"><span data-stu-id="0c2c0-104">This element is used when defining a common control that can be used by all the views in the formatting file.</span></span>

<span data-ttu-id="0c2c0-105">Elemento di configurazione (Format) controlla l'elemento dell'elemento di controllo Configuration (Format) per i controlli per la configurazione (Format) elemento CustomControl per il controllo per la configurazione (Format) elemento CustomEntries per CustomControl per la configurazione ( Format) elemento CustomEntry per CustomControl per i controlli per la configurazione (Format) elemento CustomItem per CustomEntry per i controlli per la configurazione</span><span class="sxs-lookup"><span data-stu-id="0c2c0-105">Configuration Element (Format) Controls Element of Configuration (Format) Control Element for Controls for Configuration (Format) CustomControl Element for Control for Configuration (Format) CustomEntries Element for CustomControl for Configuration (Format) CustomEntry Element for CustomControl for Controls for Configuration (Format) CustomItem Element for CustomEntry for Controls for Configuration</span></span>

## <a name="syntax"></a><span data-ttu-id="0c2c0-106">Sintassi</span><span class="sxs-lookup"><span data-stu-id="0c2c0-106">Syntax</span></span>

```xml
<CustomItem>
  <ExpressionBinding>...</ExpressionBinding>
  <NewLine/>
  <Text>TextToDisplay</Text>
  <Frame>...</Frame>
</CustomItem>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="0c2c0-107">Attributi ed elementi</span><span class="sxs-lookup"><span data-stu-id="0c2c0-107">Attributes and Elements</span></span>

<span data-ttu-id="0c2c0-108">Nelle sezioni seguenti vengono descritti gli attributi, gli elementi figlio e l'elemento padre dell'elemento `CustomItem`.</span><span class="sxs-lookup"><span data-stu-id="0c2c0-108">The following sections describe attributes, child elements, and the parent element of the `CustomItem` element.</span></span> <span data-ttu-id="0c2c0-109">Per ulteriori informazioni, vedere la sezione Osservazioni.</span><span class="sxs-lookup"><span data-stu-id="0c2c0-109">For more information, see Remarks.</span></span>

### <a name="attributes"></a><span data-ttu-id="0c2c0-110">Attributi</span><span class="sxs-lookup"><span data-stu-id="0c2c0-110">Attributes</span></span>

<span data-ttu-id="0c2c0-111">Nessuna.</span><span class="sxs-lookup"><span data-stu-id="0c2c0-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="0c2c0-112">Elementi figlio</span><span class="sxs-lookup"><span data-stu-id="0c2c0-112">Child Elements</span></span>

|<span data-ttu-id="0c2c0-113">Elemento</span><span class="sxs-lookup"><span data-stu-id="0c2c0-113">Element</span></span>|<span data-ttu-id="0c2c0-114">Description</span><span class="sxs-lookup"><span data-stu-id="0c2c0-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="0c2c0-115">Elemento expressiongroup per CustomItem per i controlli per la configurazione (Format)</span><span class="sxs-lookup"><span data-stu-id="0c2c0-115">ExpressionBinding Element for CustomItem for Controls for Configuration (Format)</span></span>](./expressionbinding-element-for-customitem-for-controls-for-configuration-format.md)|<span data-ttu-id="0c2c0-116">Elemento facoltativo.</span><span class="sxs-lookup"><span data-stu-id="0c2c0-116">Optional element.</span></span><br /><br /> <span data-ttu-id="0c2c0-117">Definisce i dati visualizzati dal controllo.</span><span class="sxs-lookup"><span data-stu-id="0c2c0-117">Defines the data that is displayed by the control.</span></span>|
|[<span data-ttu-id="0c2c0-118">Elemento frame per CustomItem per i controlli per la configurazione (Format)</span><span class="sxs-lookup"><span data-stu-id="0c2c0-118">Frame Element for CustomItem for Controls for Configuration (Format)</span></span>](./frame-element-for-customitem-for-controls-for-configuration-format.md)|<span data-ttu-id="0c2c0-119">Elemento facoltativo.</span><span class="sxs-lookup"><span data-stu-id="0c2c0-119">Optional element.</span></span><br /><br /> <span data-ttu-id="0c2c0-120">Definisce la modalità di visualizzazione dei dati, ad esempio lo spostamento dei dati verso sinistra o verso destra.</span><span class="sxs-lookup"><span data-stu-id="0c2c0-120">Defines how the data is displayed, such as shifting the data to the left or right.</span></span>|
|[<span data-ttu-id="0c2c0-121">Elemento NewLine per CustomItem per i controlli per la configurazione (Format)</span><span class="sxs-lookup"><span data-stu-id="0c2c0-121">NewLine Element for CustomItem for Controls for Configuration (Format)</span></span>](./newline-element-for-customitem-for-controls-for-configuration-format.md)|<span data-ttu-id="0c2c0-122">Elemento facoltativo.</span><span class="sxs-lookup"><span data-stu-id="0c2c0-122">Optional element.</span></span><br /><br /> <span data-ttu-id="0c2c0-123">Aggiunge una riga vuota alla visualizzazione del controllo.</span><span class="sxs-lookup"><span data-stu-id="0c2c0-123">Adds a blank line to the display of the control.</span></span>|
|[<span data-ttu-id="0c2c0-124">Elemento text per CustomItem per i controlli per la configurazione (Format)</span><span class="sxs-lookup"><span data-stu-id="0c2c0-124">Text Element for CustomItem for Controls for Configuration (Format)</span></span>](./text-element-for-customitem-for-controls-for-configuration-format.md)|<span data-ttu-id="0c2c0-125">Elemento facoltativo.</span><span class="sxs-lookup"><span data-stu-id="0c2c0-125">Optional element.</span></span><br /><br /> <span data-ttu-id="0c2c0-126">Aggiunge un testo, ad esempio le parentesi o le parentesi, alla visualizzazione del controllo.</span><span class="sxs-lookup"><span data-stu-id="0c2c0-126">Adds text, such as parentheses or brackets, to the display of the control.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="0c2c0-127">Elementi padre</span><span class="sxs-lookup"><span data-stu-id="0c2c0-127">Parent Elements</span></span>

|<span data-ttu-id="0c2c0-128">Elemento</span><span class="sxs-lookup"><span data-stu-id="0c2c0-128">Element</span></span>|<span data-ttu-id="0c2c0-129">Description</span><span class="sxs-lookup"><span data-stu-id="0c2c0-129">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="0c2c0-130">Elemento CustomEntry per CustomControl per i controlli per la configurazione (Format)</span><span class="sxs-lookup"><span data-stu-id="0c2c0-130">CustomEntry Element for CustomControl for Controls for Configuration (Format)</span></span>](./customentry-element-for-customcontrol-for-controls-for-configuration-format.md)|<span data-ttu-id="0c2c0-131">Fornisce una definizione del controllo.</span><span class="sxs-lookup"><span data-stu-id="0c2c0-131">Provides a definition of the control.</span></span>|

## <a name="remarks"></a><span data-ttu-id="0c2c0-132">Osservazioni</span><span class="sxs-lookup"><span data-stu-id="0c2c0-132">Remarks</span></span>

<span data-ttu-id="0c2c0-133">Quando si specificano gli elementi figlio dell'elemento `CustomItem`, tenere presente quanto segue:</span><span class="sxs-lookup"><span data-stu-id="0c2c0-133">When specifying the child elements of the `CustomItem` element, keep the following in mind:</span></span>

- <span data-ttu-id="0c2c0-134">Gli elementi figlio devono essere aggiunti nella sequenza seguente: `ExpressionBinding`, `NewLine`, `Text` e `Frame`.</span><span class="sxs-lookup"><span data-stu-id="0c2c0-134">The child elements must be added in the following sequence: `ExpressionBinding`, `NewLine`, `Text`, and `Frame`.</span></span>

- <span data-ttu-id="0c2c0-135">Non esiste un limite massimo per il numero di sequenze che è possibile specificare.</span><span class="sxs-lookup"><span data-stu-id="0c2c0-135">There is no maximum limit to the number of sequences that you can specify.</span></span>

- <span data-ttu-id="0c2c0-136">In ogni sequenza non esiste alcun limite massimo per il numero di elementi `ExpressionBinding` che è possibile usare.</span><span class="sxs-lookup"><span data-stu-id="0c2c0-136">In each sequence, there is no maximum limit to the number of `ExpressionBinding` elements that you can use.</span></span>

## <a name="see-also"></a><span data-ttu-id="0c2c0-137">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="0c2c0-137">See Also</span></span>

[<span data-ttu-id="0c2c0-138">Elemento expressiongroup per CustomItem per i controlli per la configurazione (Format)</span><span class="sxs-lookup"><span data-stu-id="0c2c0-138">ExpressionBinding Element for CustomItem for Controls for Configuration (Format)</span></span>](./expressionbinding-element-for-customitem-for-controls-for-configuration-format.md)

[<span data-ttu-id="0c2c0-139">Elemento frame per CustomItem per i controlli per la configurazione (Format)</span><span class="sxs-lookup"><span data-stu-id="0c2c0-139">Frame Element for CustomItem for Controls for Configuration (Format)</span></span>](./frame-element-for-customitem-for-controls-for-configuration-format.md)

[<span data-ttu-id="0c2c0-140">Elemento NewLine per CustomItem per i controlli per la configurazione (Format)</span><span class="sxs-lookup"><span data-stu-id="0c2c0-140">NewLine Element for CustomItem for Controls for Configuration (Format)</span></span>](./newline-element-for-customitem-for-controls-for-configuration-format.md)

[<span data-ttu-id="0c2c0-141">Elemento text per CustomItem per i controlli per la configurazione (Format)</span><span class="sxs-lookup"><span data-stu-id="0c2c0-141">Text Element for CustomItem for Controls for Configuration (Format)</span></span>](./text-element-for-customitem-for-controls-for-configuration-format.md)

[<span data-ttu-id="0c2c0-142">Scrittura di un file di formattazione di PowerShell</span><span class="sxs-lookup"><span data-stu-id="0c2c0-142">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)