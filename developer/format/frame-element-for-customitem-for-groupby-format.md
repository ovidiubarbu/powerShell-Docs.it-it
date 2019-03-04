---
title: Elemento dei frame per CustomItem per GroupBy (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ab2a5379-299d-4c97-86a2-b639ea890fae
caps.latest.revision: 6
ms.openlocfilehash: 7f9066c0fe0954fadff9dc8f0c35a62c6710f516
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/03/2019
ms.locfileid: "56854847"
---
# <a name="frame-element-for-customitem-for-groupby-format"></a><span data-ttu-id="26d3f-102">Elemento Frame per CustomItem per GroupBy (formato)</span><span class="sxs-lookup"><span data-stu-id="26d3f-102">Frame Element for CustomItem for GroupBy (Format)</span></span>

<span data-ttu-id="26d3f-103">Definisce come verranno visualizzati i dati, ad esempio lo spostamento di dati a sinistra o destra.</span><span class="sxs-lookup"><span data-stu-id="26d3f-103">Defines how the data is displayed, such as shifting the data to the left or right.</span></span> <span data-ttu-id="26d3f-104">Questo elemento viene usato quando si definisce come viene visualizzato un nuovo gruppo di oggetti.</span><span class="sxs-lookup"><span data-stu-id="26d3f-104">This element is used when defining how a new group of objects is displayed.</span></span>

<span data-ttu-id="26d3f-105">Elemento di GroupBy elemento (formato) per la visualizzazione elemento ViewDefinitions (formato) configurazione elemento (formato) per visualizzazione (formato) CustomControl elemento per elemento CustomEntries GroupBy (formato) per CustomControl per elemento CustomEntry GroupBy (formato) CustomControl per elemento CustomItem GroupBy (formato) per CustomEntry per elemento Frame GroupBy (formato) per CustomItem per GroupBy (formato)</span><span class="sxs-lookup"><span data-stu-id="26d3f-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) GroupBy Element for View (Format) CustomControl Element for GroupBy (Format) CustomEntries Element for CustomControl for GroupBy (Format) CustomEntry Element for CustomControl for GroupBy (Format) CustomItem Element for CustomEntry for GroupBy (Format) Frame Element for CustomItem for GroupBy (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="26d3f-106">Sintassi</span><span class="sxs-lookup"><span data-stu-id="26d3f-106">Syntax</span></span>

```xml
<Frame>
  <LeftIndent>NumberOfCharactersToShift</LeftIndent>
  <RightIndent>NumberOfCharactersToShift</RightIndent>
  <FirstLineHanging>NumberOfCharactersToShift</FirstLineHanging>
  <FirstLineIndent>NumberOfCharactersToShift</FirstLineIndent>
  <CustomItem>...</CustomItem>
</Frame>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="26d3f-107">Attributi ed elementi</span><span class="sxs-lookup"><span data-stu-id="26d3f-107">Attributes and Elements</span></span>

<span data-ttu-id="26d3f-108">Le sezioni seguenti descrivono gli attributi e gli elementi figlio dell'elemento padre del `Frame` elemento.</span><span class="sxs-lookup"><span data-stu-id="26d3f-108">The following sections describe attributes, child elements, and the parent element of the `Frame` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="26d3f-109">Attributes</span><span class="sxs-lookup"><span data-stu-id="26d3f-109">Attributes</span></span>

<span data-ttu-id="26d3f-110">Nessuna.</span><span class="sxs-lookup"><span data-stu-id="26d3f-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="26d3f-111">Elementi figlio</span><span class="sxs-lookup"><span data-stu-id="26d3f-111">Child Elements</span></span>

|<span data-ttu-id="26d3f-112">Elemento</span><span class="sxs-lookup"><span data-stu-id="26d3f-112">Element</span></span>|<span data-ttu-id="26d3f-113">Description</span><span class="sxs-lookup"><span data-stu-id="26d3f-113">Description</span></span>|
|-------------|-----------------|
|`CustomItem Element`|<span data-ttu-id="26d3f-114">Elemento obbligatorio</span><span class="sxs-lookup"><span data-stu-id="26d3f-114">Required Element</span></span>|
|[<span data-ttu-id="26d3f-115">Elemento FirstLineHanging per Frame per GroupBy (formato)</span><span class="sxs-lookup"><span data-stu-id="26d3f-115">FirstLineHanging Element for Frame for GroupBy (Format)</span></span>](./firstlinehanging-element-for-frame-for-groupby-format.md)|<span data-ttu-id="26d3f-116">Elemento facoltativo.</span><span class="sxs-lookup"><span data-stu-id="26d3f-116">Optional element.</span></span><br /><br /> <span data-ttu-id="26d3f-117">Specifica il numero di caratteri la prima riga di dati verrà spostata a sinistra.</span><span class="sxs-lookup"><span data-stu-id="26d3f-117">Specifies how many characters the first line of data is shifted to the left.</span></span>|
|[<span data-ttu-id="26d3f-118">Elemento FirstLineIndent per Frame per GroupBy (formato)</span><span class="sxs-lookup"><span data-stu-id="26d3f-118">FirstLineIndent Element for Frame for GroupBy (Format)</span></span>](./firstlineindent-element-for-frame-for-groupby-format.md)|<span data-ttu-id="26d3f-119">Elemento facoltativo.</span><span class="sxs-lookup"><span data-stu-id="26d3f-119">Optional element.</span></span><br /><br /> <span data-ttu-id="26d3f-120">Specifica il numero di caratteri la prima riga di dati verrà spostata a destra.</span><span class="sxs-lookup"><span data-stu-id="26d3f-120">Specifies how many characters the first line of data is shifted to the right.</span></span>|
|[<span data-ttu-id="26d3f-121">Elemento LeftIndent per Frame per GroupBy (formato)</span><span class="sxs-lookup"><span data-stu-id="26d3f-121">LeftIndent Element for Frame for GroupBy (Format)</span></span>](./leftindent-element-for-frame-for-groupby-format.md)|<span data-ttu-id="26d3f-122">Elemento facoltativo.</span><span class="sxs-lookup"><span data-stu-id="26d3f-122">Optional element.</span></span><br /><br /> <span data-ttu-id="26d3f-123">Specifica quanti caratteri di dati viene spostati dal margine sinistro.</span><span class="sxs-lookup"><span data-stu-id="26d3f-123">Specifies how many characters the data is shifted away from the left margin.</span></span>|
|<span data-ttu-id="26d3f-124">[Elemento RightIndent per Frame per GroupBy (formato)](./rightindent-element-for-frame-for-groupby-format.md)RightIndent elemento</span><span class="sxs-lookup"><span data-stu-id="26d3f-124">[RightIndent Element for Frame for GroupBy (Format)](./rightindent-element-for-frame-for-groupby-format.md)RightIndent Element</span></span>|<span data-ttu-id="26d3f-125">Elemento facoltativo.</span><span class="sxs-lookup"><span data-stu-id="26d3f-125">Optional element.</span></span><br /><br /> <span data-ttu-id="26d3f-126">Specifica quanti caratteri di dati viene spostati dal margine destro.</span><span class="sxs-lookup"><span data-stu-id="26d3f-126">Specifies how many characters the data is shifted away from the right margin.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="26d3f-127">Elementi padre</span><span class="sxs-lookup"><span data-stu-id="26d3f-127">Parent Elements</span></span>

|<span data-ttu-id="26d3f-128">Elemento</span><span class="sxs-lookup"><span data-stu-id="26d3f-128">Element</span></span>|<span data-ttu-id="26d3f-129">Description</span><span class="sxs-lookup"><span data-stu-id="26d3f-129">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="26d3f-130">Elemento CustomItem per CustomEntry per GroupBy (formato)</span><span class="sxs-lookup"><span data-stu-id="26d3f-130">CustomItem Element for CustomEntry for GroupBy (Format)</span></span>](./customitem-element-for-customentry-for-groupby-format.md)|<span data-ttu-id="26d3f-131">Definisce i dati che vengano visualizzati dal controllo e la modalità di visualizzazione.</span><span class="sxs-lookup"><span data-stu-id="26d3f-131">Defines what data is displayed by the control and how it is displayed.</span></span>|

## <a name="remarks"></a><span data-ttu-id="26d3f-132">Osservazioni</span><span class="sxs-lookup"><span data-stu-id="26d3f-132">Remarks</span></span>

<span data-ttu-id="26d3f-133">Non è possibile specificare il [FirstLineHanging](./firstlinehanging-element-for-frame-for-groupby-format.md) e il [FirstLineIndent](./firstlineindent-element-for-frame-for-groupby-format.md) elementi nello stesso `Frame` elemento.</span><span class="sxs-lookup"><span data-stu-id="26d3f-133">You cannot specify the [FirstLineHanging](./firstlinehanging-element-for-frame-for-groupby-format.md) and the [FirstLineIndent](./firstlineindent-element-for-frame-for-groupby-format.md) elements in the same `Frame` element.</span></span>

## <a name="see-also"></a><span data-ttu-id="26d3f-134">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="26d3f-134">See Also</span></span>

[<span data-ttu-id="26d3f-135">Elemento FirstLineHanging per Frame per GroupBy (formato)</span><span class="sxs-lookup"><span data-stu-id="26d3f-135">FirstLineHanging Element for Frame for GroupBy (Format)</span></span>](./firstlinehanging-element-for-frame-for-groupby-format.md)

[<span data-ttu-id="26d3f-136">Elemento FirstLineIndent per Frame per GroupBy (formato)</span><span class="sxs-lookup"><span data-stu-id="26d3f-136">FirstLineIndent Element for Frame for GroupBy (Format)</span></span>](./firstlineindent-element-for-frame-for-groupby-format.md)

[<span data-ttu-id="26d3f-137">Elemento LeftIndent per Frame per GroupBy (formato)</span><span class="sxs-lookup"><span data-stu-id="26d3f-137">LeftIndent Element for Frame for GroupBy (Format)</span></span>](./leftindent-element-for-frame-for-groupby-format.md)

[<span data-ttu-id="26d3f-138">Elemento RightIndent per Frame per GroupBy (formato)</span><span class="sxs-lookup"><span data-stu-id="26d3f-138">RightIndent Element for Frame for GroupBy (Format)</span></span>](./rightindent-element-for-frame-for-groupby-format.md)

[<span data-ttu-id="26d3f-139">Elemento CustomItem per CustomEntry per GroupBy (formato)</span><span class="sxs-lookup"><span data-stu-id="26d3f-139">CustomItem Element for CustomEntry for GroupBy (Format)</span></span>](./customitem-element-for-customentry-for-groupby-format.md)

[<span data-ttu-id="26d3f-140">La scrittura di un File di formattazione di PowerShell</span><span class="sxs-lookup"><span data-stu-id="26d3f-140">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
