---
title: Elemento dei frame per CustomItem per i controlli per la configurazione (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d879c8ce-679d-4622-bc43-c207f6413871
caps.latest.revision: 9
ms.openlocfilehash: b11b154a94daccead57bdfb5e579e1de2c190c09
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/03/2019
ms.locfileid: "56862977"
---
# <a name="frame-element-for-customitem-for-controls-for-configuration-format"></a><span data-ttu-id="ca138-102">Elemento Frame per CustomItem per Controls per Configuration (formato)</span><span class="sxs-lookup"><span data-stu-id="ca138-102">Frame Element for CustomItem for Controls for Configuration (Format)</span></span>

<span data-ttu-id="ca138-103">Definisce come verranno visualizzati i dati, ad esempio lo spostamento di dati a sinistra o destra.</span><span class="sxs-lookup"><span data-stu-id="ca138-103">Defines how the data is displayed, such as shifting the data to the left or right.</span></span> <span data-ttu-id="ca138-104">Questo elemento viene usato quando si definisce un controllo comune che può essere usato da tutte le visualizzazioni nel file di formattazione.</span><span class="sxs-lookup"><span data-stu-id="ca138-104">This element is used when defining a common control that can be used by all the views in the formatting file.</span></span>

<span data-ttu-id="ca138-105">Configurazione (formato) i controlli elemento di configurazione (formato) elemento di controllo per i controlli di configurazione (formato) CustomControl elemento per il controllo per elemento di configurazione (formato) CustomEntries per CustomControl per Configuration ( Elemento CustomEntry Format) per CustomControl per i controlli per elemento di configurazione (formato) CustomItem per CustomEntry per i controlli per la configurazione elemento Frame per CustomItem per i controlli per la configurazione (formato)</span><span class="sxs-lookup"><span data-stu-id="ca138-105">Configuration Element (Format) Controls Element of Configuration (Format) Control Element for Controls for Configuration (Format) CustomControl Element for Control for Configuration (Format) CustomEntries Element for CustomControl for Configuration (Format) CustomEntry Element for CustomControl for Controls for Configuration (Format) CustomItem Element for CustomEntry for Controls for Configuration Frame Element for CustomItem for Controls for Configuration (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="ca138-106">Sintassi</span><span class="sxs-lookup"><span data-stu-id="ca138-106">Syntax</span></span>

```xml
<Frame>
  <LeftIndent>NumberOfCharactersToShift</LeftIndent>
  <RightIndent>NumberOfCharactersToShift</RightIndent>
  <FirstLineHanging>NumberOfCharactersToShift</FirstLineHanging>
  <FirstLineIndent>NumberOfCharactersToShift</FirstLineIndent>
  <CustomItem>...</CustomItem>
</Frame>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="ca138-107">Attributi ed elementi</span><span class="sxs-lookup"><span data-stu-id="ca138-107">Attributes and Elements</span></span>

<span data-ttu-id="ca138-108">Le sezioni seguenti descrivono gli attributi e gli elementi figlio dell'elemento padre del `Frame` elemento.</span><span class="sxs-lookup"><span data-stu-id="ca138-108">The following sections describe attributes, child elements, and the parent element of the `Frame` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="ca138-109">Attributes</span><span class="sxs-lookup"><span data-stu-id="ca138-109">Attributes</span></span>

<span data-ttu-id="ca138-110">Nessuna.</span><span class="sxs-lookup"><span data-stu-id="ca138-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="ca138-111">Elementi figlio</span><span class="sxs-lookup"><span data-stu-id="ca138-111">Child Elements</span></span>

|<span data-ttu-id="ca138-112">Elemento</span><span class="sxs-lookup"><span data-stu-id="ca138-112">Element</span></span>|<span data-ttu-id="ca138-113">Description</span><span class="sxs-lookup"><span data-stu-id="ca138-113">Description</span></span>|
|-------------|-----------------|
|`CustomItem Element`|<span data-ttu-id="ca138-114">Elemento obbligatorio</span><span class="sxs-lookup"><span data-stu-id="ca138-114">Required Element</span></span>|
|[<span data-ttu-id="ca138-115">Elemento FirstLineHanging per Frame per i controlli per la configurazione (formato)</span><span class="sxs-lookup"><span data-stu-id="ca138-115">FirstLineHanging Element for Frame for Controls for Configuration (Format)</span></span>](./firstlinehanging-element-for-frame-for-controls-for-configuration-format.md)|<span data-ttu-id="ca138-116">Elemento facoltativo.</span><span class="sxs-lookup"><span data-stu-id="ca138-116">Optional element.</span></span><br /><br /> <span data-ttu-id="ca138-117">Specifica il numero di caratteri la prima riga di dati verrà spostata a sinistra.</span><span class="sxs-lookup"><span data-stu-id="ca138-117">Specifies how many characters the first line of data is shifted to the left.</span></span>|
|[<span data-ttu-id="ca138-118">Elemento FirstLineIndent per Frame per i controlli per la configurazione (formato)</span><span class="sxs-lookup"><span data-stu-id="ca138-118">FirstLineIndent Element for Frame for Controls for Configuration (Format)</span></span>](./firstlineindent-element-for-frame-for-controls-for-configuration-format.md)|<span data-ttu-id="ca138-119">Elemento facoltativo.</span><span class="sxs-lookup"><span data-stu-id="ca138-119">Optional element.</span></span><br /><br /> <span data-ttu-id="ca138-120">Specifica il numero di caratteri la prima riga di dati verrà spostata a destra.</span><span class="sxs-lookup"><span data-stu-id="ca138-120">Specifies how many characters the first line of data is shifted to the right.</span></span>|
|[<span data-ttu-id="ca138-121">Elemento LeftIndent per Frame per i controlli per la configurazione (formato)</span><span class="sxs-lookup"><span data-stu-id="ca138-121">LeftIndent Element for Frame for Controls for Configuration (Format)</span></span>](./leftindent-element-for-frame-for-controls-for-configuration-format.md)|<span data-ttu-id="ca138-122">Elemento facoltativo.</span><span class="sxs-lookup"><span data-stu-id="ca138-122">Optional element.</span></span><br /><br /> <span data-ttu-id="ca138-123">Specifica quanti caratteri di dati viene spostati dal margine sinistro.</span><span class="sxs-lookup"><span data-stu-id="ca138-123">Specifies how many characters the data is shifted away from the left margin.</span></span>|
|[<span data-ttu-id="ca138-124">Elemento RightIndent per Frame per i controlli per la configurazione (formato)</span><span class="sxs-lookup"><span data-stu-id="ca138-124">RightIndent Element for Frame for Controls for Configuration (Format)</span></span>](./rightindent-element-for-frame-for-controls-for-configuration-format.md)|<span data-ttu-id="ca138-125">Elemento facoltativo.</span><span class="sxs-lookup"><span data-stu-id="ca138-125">Optional element.</span></span><br /><br /> <span data-ttu-id="ca138-126">Specifica quanti caratteri di dati viene spostati dal margine destro.</span><span class="sxs-lookup"><span data-stu-id="ca138-126">Specifies how many characters the data is shifted away from the right margin.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="ca138-127">Elementi padre</span><span class="sxs-lookup"><span data-stu-id="ca138-127">Parent Elements</span></span>

|<span data-ttu-id="ca138-128">Elemento</span><span class="sxs-lookup"><span data-stu-id="ca138-128">Element</span></span>|<span data-ttu-id="ca138-129">Description</span><span class="sxs-lookup"><span data-stu-id="ca138-129">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="ca138-130">Elemento CustomItem per CustomEntry per i controlli per la configurazione</span><span class="sxs-lookup"><span data-stu-id="ca138-130">CustomItem Element for CustomEntry for Controls for Configuration</span></span>](./customitem-element-for-customentry-for-controls-for-configuration-format.md)|<span data-ttu-id="ca138-131">Definisce i dati che vengano visualizzati dal controllo e la modalità di visualizzazione.</span><span class="sxs-lookup"><span data-stu-id="ca138-131">Defines what data is displayed by the control and how it is displayed.</span></span>|

## <a name="remarks"></a><span data-ttu-id="ca138-132">Osservazioni</span><span class="sxs-lookup"><span data-stu-id="ca138-132">Remarks</span></span>

<span data-ttu-id="ca138-133">Non è possibile specificare il [FirstLineHanging](./firstlinehanging-element-for-frame-for-controls-for-configuration-format.md) e il [FirstLineIndent](./firstlineindent-element-for-frame-for-controls-for-configuration-format.md) elementi nello stesso `Frame` elemento.</span><span class="sxs-lookup"><span data-stu-id="ca138-133">You cannot specify the [FirstLineHanging](./firstlinehanging-element-for-frame-for-controls-for-configuration-format.md) and the [FirstLineIndent](./firstlineindent-element-for-frame-for-controls-for-configuration-format.md) elements in the same `Frame` element.</span></span>

## <a name="see-also"></a><span data-ttu-id="ca138-134">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="ca138-134">See Also</span></span>

[<span data-ttu-id="ca138-135">Elemento FirstLineHanging per Frame per i controlli per la configurazione (formato)</span><span class="sxs-lookup"><span data-stu-id="ca138-135">FirstLineHanging Element for Frame for Controls for Configuration (Format)</span></span>](./firstlinehanging-element-for-frame-for-controls-for-configuration-format.md)

[<span data-ttu-id="ca138-136">Elemento FirstLineIndent per Frame per i controlli per la configurazione (formato)</span><span class="sxs-lookup"><span data-stu-id="ca138-136">FirstLineIndent Element for Frame for Controls for Configuration (Format)</span></span>](./firstlineindent-element-for-frame-for-controls-for-configuration-format.md)

[<span data-ttu-id="ca138-137">Elemento LeftIndent per Frame per i controlli per la configurazione (formato)</span><span class="sxs-lookup"><span data-stu-id="ca138-137">LeftIndent Element for Frame for Controls for Configuration (Format)</span></span>](./leftindent-element-for-frame-for-controls-for-configuration-format.md)

[<span data-ttu-id="ca138-138">Elemento RightIndent per Frame per i controlli per la configurazione (formato)</span><span class="sxs-lookup"><span data-stu-id="ca138-138">RightIndent Element for Frame for Controls for Configuration (Format)</span></span>](./rightindent-element-for-frame-for-controls-for-configuration-format.md)

[<span data-ttu-id="ca138-139">Elemento CustomItem per CustomEntry per i controlli per la configurazione</span><span class="sxs-lookup"><span data-stu-id="ca138-139">CustomItem Element for CustomEntry for Controls for Configuration</span></span>](./customitem-element-for-customentry-for-controls-for-configuration-format.md)

[<span data-ttu-id="ca138-140">La scrittura di un File di formattazione di PowerShell</span><span class="sxs-lookup"><span data-stu-id="ca138-140">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
