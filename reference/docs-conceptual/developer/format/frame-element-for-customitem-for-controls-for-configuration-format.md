---
title: Elemento frame per CustomItem per i controlli per la configurazione (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d879c8ce-679d-4622-bc43-c207f6413871
caps.latest.revision: 9
ms.openlocfilehash: b11b154a94daccead57bdfb5e579e1de2c190c09
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/15/2019
ms.locfileid: "72363660"
---
# <a name="frame-element-for-customitem-for-controls-for-configuration-format"></a><span data-ttu-id="4f558-102">Elemento Frame per CustomItem per Controls per Configuration (formato)</span><span class="sxs-lookup"><span data-stu-id="4f558-102">Frame Element for CustomItem for Controls for Configuration (Format)</span></span>

<span data-ttu-id="4f558-103">Definisce la modalità di visualizzazione dei dati, ad esempio lo spostamento dei dati verso sinistra o verso destra.</span><span class="sxs-lookup"><span data-stu-id="4f558-103">Defines how the data is displayed, such as shifting the data to the left or right.</span></span> <span data-ttu-id="4f558-104">Questo elemento viene usato quando si definisce un controllo comune che può essere usato da tutte le visualizzazioni nel file di formattazione.</span><span class="sxs-lookup"><span data-stu-id="4f558-104">This element is used when defining a common control that can be used by all the views in the formatting file.</span></span>

<span data-ttu-id="4f558-105">Elemento di configurazione (Format) controlla l'elemento dell'elemento di controllo Configuration (Format) per i controlli per la configurazione (Format) elemento CustomControl per il controllo per la configurazione (Format) elemento CustomEntries per CustomControl per la configurazione ( Format) elemento CustomEntry per CustomControl per i controlli per la configurazione (Format) elemento CustomItem per CustomEntry per i controlli per l'elemento del frame di configurazione per CustomItem per i controlli per la configurazione (Format)</span><span class="sxs-lookup"><span data-stu-id="4f558-105">Configuration Element (Format) Controls Element of Configuration (Format) Control Element for Controls for Configuration (Format) CustomControl Element for Control for Configuration (Format) CustomEntries Element for CustomControl for Configuration (Format) CustomEntry Element for CustomControl for Controls for Configuration (Format) CustomItem Element for CustomEntry for Controls for Configuration Frame Element for CustomItem for Controls for Configuration (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="4f558-106">Sintassi</span><span class="sxs-lookup"><span data-stu-id="4f558-106">Syntax</span></span>

```xml
<Frame>
  <LeftIndent>NumberOfCharactersToShift</LeftIndent>
  <RightIndent>NumberOfCharactersToShift</RightIndent>
  <FirstLineHanging>NumberOfCharactersToShift</FirstLineHanging>
  <FirstLineIndent>NumberOfCharactersToShift</FirstLineIndent>
  <CustomItem>...</CustomItem>
</Frame>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="4f558-107">Attributi ed elementi</span><span class="sxs-lookup"><span data-stu-id="4f558-107">Attributes and Elements</span></span>

<span data-ttu-id="4f558-108">Nelle sezioni seguenti vengono descritti gli attributi, gli elementi figlio e l'elemento padre dell'elemento `Frame`.</span><span class="sxs-lookup"><span data-stu-id="4f558-108">The following sections describe attributes, child elements, and the parent element of the `Frame` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="4f558-109">Attributi</span><span class="sxs-lookup"><span data-stu-id="4f558-109">Attributes</span></span>

<span data-ttu-id="4f558-110">Nessuna.</span><span class="sxs-lookup"><span data-stu-id="4f558-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="4f558-111">Elementi figlio</span><span class="sxs-lookup"><span data-stu-id="4f558-111">Child Elements</span></span>

|<span data-ttu-id="4f558-112">Elemento</span><span class="sxs-lookup"><span data-stu-id="4f558-112">Element</span></span>|<span data-ttu-id="4f558-113">Description</span><span class="sxs-lookup"><span data-stu-id="4f558-113">Description</span></span>|
|-------------|-----------------|
|`CustomItem Element`|<span data-ttu-id="4f558-114">Elemento obbligatorio</span><span class="sxs-lookup"><span data-stu-id="4f558-114">Required Element</span></span>|
|[<span data-ttu-id="4f558-115">Elemento FirstLineHanging per il frame per i controlli per la configurazione (Format)</span><span class="sxs-lookup"><span data-stu-id="4f558-115">FirstLineHanging Element for Frame for Controls for Configuration (Format)</span></span>](./firstlinehanging-element-for-frame-for-controls-for-configuration-format.md)|<span data-ttu-id="4f558-116">Elemento facoltativo.</span><span class="sxs-lookup"><span data-stu-id="4f558-116">Optional element.</span></span><br /><br /> <span data-ttu-id="4f558-117">Specifica il numero di caratteri che la prima riga di dati viene spostata a sinistra.</span><span class="sxs-lookup"><span data-stu-id="4f558-117">Specifies how many characters the first line of data is shifted to the left.</span></span>|
|[<span data-ttu-id="4f558-118">Elemento FirstLineIndent per il frame per i controlli per la configurazione (Format)</span><span class="sxs-lookup"><span data-stu-id="4f558-118">FirstLineIndent Element for Frame for Controls for Configuration (Format)</span></span>](./firstlineindent-element-for-frame-for-controls-for-configuration-format.md)|<span data-ttu-id="4f558-119">Elemento facoltativo.</span><span class="sxs-lookup"><span data-stu-id="4f558-119">Optional element.</span></span><br /><br /> <span data-ttu-id="4f558-120">Specifica il numero di caratteri che la prima riga di dati viene spostata a destra.</span><span class="sxs-lookup"><span data-stu-id="4f558-120">Specifies how many characters the first line of data is shifted to the right.</span></span>|
|[<span data-ttu-id="4f558-121">Elemento LeftIndent per il frame per i controlli per la configurazione (Format)</span><span class="sxs-lookup"><span data-stu-id="4f558-121">LeftIndent Element for Frame for Controls for Configuration (Format)</span></span>](./leftindent-element-for-frame-for-controls-for-configuration-format.md)|<span data-ttu-id="4f558-122">Elemento facoltativo.</span><span class="sxs-lookup"><span data-stu-id="4f558-122">Optional element.</span></span><br /><br /> <span data-ttu-id="4f558-123">Specifica il numero di caratteri spostati al di fuori del margine sinistro.</span><span class="sxs-lookup"><span data-stu-id="4f558-123">Specifies how many characters the data is shifted away from the left margin.</span></span>|
|[<span data-ttu-id="4f558-124">Elemento RightIndent per il frame per i controlli per la configurazione (Format)</span><span class="sxs-lookup"><span data-stu-id="4f558-124">RightIndent Element for Frame for Controls for Configuration (Format)</span></span>](./rightindent-element-for-frame-for-controls-for-configuration-format.md)|<span data-ttu-id="4f558-125">Elemento facoltativo.</span><span class="sxs-lookup"><span data-stu-id="4f558-125">Optional element.</span></span><br /><br /> <span data-ttu-id="4f558-126">Specifica il numero di caratteri spostati al di fuori del margine destro da parte dei dati.</span><span class="sxs-lookup"><span data-stu-id="4f558-126">Specifies how many characters the data is shifted away from the right margin.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="4f558-127">Elementi padre</span><span class="sxs-lookup"><span data-stu-id="4f558-127">Parent Elements</span></span>

|<span data-ttu-id="4f558-128">Elemento</span><span class="sxs-lookup"><span data-stu-id="4f558-128">Element</span></span>|<span data-ttu-id="4f558-129">Description</span><span class="sxs-lookup"><span data-stu-id="4f558-129">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="4f558-130">Elemento CustomItem per CustomEntry per i controlli per la configurazione</span><span class="sxs-lookup"><span data-stu-id="4f558-130">CustomItem Element for CustomEntry for Controls for Configuration</span></span>](./customitem-element-for-customentry-for-controls-for-configuration-format.md)|<span data-ttu-id="4f558-131">Definisce quali dati vengono visualizzati dal controllo e come vengono visualizzati.</span><span class="sxs-lookup"><span data-stu-id="4f558-131">Defines what data is displayed by the control and how it is displayed.</span></span>|

## <a name="remarks"></a><span data-ttu-id="4f558-132">Osservazioni</span><span class="sxs-lookup"><span data-stu-id="4f558-132">Remarks</span></span>

<span data-ttu-id="4f558-133">Non è possibile specificare gli elementi [FirstLineHanging](./firstlinehanging-element-for-frame-for-controls-for-configuration-format.md) e [FirstLineIndent](./firstlineindent-element-for-frame-for-controls-for-configuration-format.md) nello stesso elemento `Frame`.</span><span class="sxs-lookup"><span data-stu-id="4f558-133">You cannot specify the [FirstLineHanging](./firstlinehanging-element-for-frame-for-controls-for-configuration-format.md) and the [FirstLineIndent](./firstlineindent-element-for-frame-for-controls-for-configuration-format.md) elements in the same `Frame` element.</span></span>

## <a name="see-also"></a><span data-ttu-id="4f558-134">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="4f558-134">See Also</span></span>

[<span data-ttu-id="4f558-135">Elemento FirstLineHanging per il frame per i controlli per la configurazione (Format)</span><span class="sxs-lookup"><span data-stu-id="4f558-135">FirstLineHanging Element for Frame for Controls for Configuration (Format)</span></span>](./firstlinehanging-element-for-frame-for-controls-for-configuration-format.md)

[<span data-ttu-id="4f558-136">Elemento FirstLineIndent per il frame per i controlli per la configurazione (Format)</span><span class="sxs-lookup"><span data-stu-id="4f558-136">FirstLineIndent Element for Frame for Controls for Configuration (Format)</span></span>](./firstlineindent-element-for-frame-for-controls-for-configuration-format.md)

[<span data-ttu-id="4f558-137">Elemento LeftIndent per il frame per i controlli per la configurazione (Format)</span><span class="sxs-lookup"><span data-stu-id="4f558-137">LeftIndent Element for Frame for Controls for Configuration (Format)</span></span>](./leftindent-element-for-frame-for-controls-for-configuration-format.md)

[<span data-ttu-id="4f558-138">Elemento RightIndent per il frame per i controlli per la configurazione (Format)</span><span class="sxs-lookup"><span data-stu-id="4f558-138">RightIndent Element for Frame for Controls for Configuration (Format)</span></span>](./rightindent-element-for-frame-for-controls-for-configuration-format.md)

[<span data-ttu-id="4f558-139">Elemento CustomItem per CustomEntry per i controlli per la configurazione</span><span class="sxs-lookup"><span data-stu-id="4f558-139">CustomItem Element for CustomEntry for Controls for Configuration</span></span>](./customitem-element-for-customentry-for-controls-for-configuration-format.md)

[<span data-ttu-id="4f558-140">Scrittura di un file di formattazione di PowerShell</span><span class="sxs-lookup"><span data-stu-id="4f558-140">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
