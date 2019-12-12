---
title: Elemento frame per CustomItem per GroupBy (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ab2a5379-299d-4c97-86a2-b639ea890fae
caps.latest.revision: 6
ms.openlocfilehash: 7f9066c0fe0954fadff9dc8f0c35a62c6710f516
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/05/2019
ms.locfileid: "72362950"
---
# <a name="frame-element-for-customitem-for-groupby-format"></a><span data-ttu-id="5838a-102">Elemento Frame per CustomItem per GroupBy (formato)</span><span class="sxs-lookup"><span data-stu-id="5838a-102">Frame Element for CustomItem for GroupBy (Format)</span></span>

<span data-ttu-id="5838a-103">Definisce la modalità di visualizzazione dei dati, ad esempio lo spostamento dei dati verso sinistra o verso destra.</span><span class="sxs-lookup"><span data-stu-id="5838a-103">Defines how the data is displayed, such as shifting the data to the left or right.</span></span> <span data-ttu-id="5838a-104">Questo elemento viene utilizzato quando si definisce la modalità di visualizzazione di un nuovo gruppo di oggetti.</span><span class="sxs-lookup"><span data-stu-id="5838a-104">This element is used when defining how a new group of objects is displayed.</span></span>

<span data-ttu-id="5838a-105">Elemento Configuration (Format) elemento ViewDefinitions (Format) elemento View (Format) elemento GroupBy per View (Format) elemento CustomControl per l'elemento GroupBy (Format) CustomEntries per CustomControl per l'elemento GroupBy (Format) CustomEntry per CustomControl per GroupBy (Format) elemento CustomItem per CustomEntry per l'elemento frame GroupBy (Format) per CustomItem per GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="5838a-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) GroupBy Element for View (Format) CustomControl Element for GroupBy (Format) CustomEntries Element for CustomControl for GroupBy (Format) CustomEntry Element for CustomControl for GroupBy (Format) CustomItem Element for CustomEntry for GroupBy (Format) Frame Element for CustomItem for GroupBy (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="5838a-106">Sintassi</span><span class="sxs-lookup"><span data-stu-id="5838a-106">Syntax</span></span>

```xml
<Frame>
  <LeftIndent>NumberOfCharactersToShift</LeftIndent>
  <RightIndent>NumberOfCharactersToShift</RightIndent>
  <FirstLineHanging>NumberOfCharactersToShift</FirstLineHanging>
  <FirstLineIndent>NumberOfCharactersToShift</FirstLineIndent>
  <CustomItem>...</CustomItem>
</Frame>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="5838a-107">Attributi ed elementi</span><span class="sxs-lookup"><span data-stu-id="5838a-107">Attributes and Elements</span></span>

<span data-ttu-id="5838a-108">Nelle sezioni seguenti vengono descritti gli attributi, gli elementi figlio e l'elemento padre dell'elemento `Frame`.</span><span class="sxs-lookup"><span data-stu-id="5838a-108">The following sections describe attributes, child elements, and the parent element of the `Frame` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="5838a-109">Attributi</span><span class="sxs-lookup"><span data-stu-id="5838a-109">Attributes</span></span>

<span data-ttu-id="5838a-110">Nessuna.</span><span class="sxs-lookup"><span data-stu-id="5838a-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="5838a-111">Elementi figlio</span><span class="sxs-lookup"><span data-stu-id="5838a-111">Child Elements</span></span>

|<span data-ttu-id="5838a-112">Elemento</span><span class="sxs-lookup"><span data-stu-id="5838a-112">Element</span></span>|<span data-ttu-id="5838a-113">Description</span><span class="sxs-lookup"><span data-stu-id="5838a-113">Description</span></span>|
|-------------|-----------------|
|`CustomItem Element`|<span data-ttu-id="5838a-114">Elemento obbligatorio</span><span class="sxs-lookup"><span data-stu-id="5838a-114">Required Element</span></span>|
|[<span data-ttu-id="5838a-115">Elemento FirstLineHanging per frame per GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="5838a-115">FirstLineHanging Element for Frame for GroupBy (Format)</span></span>](./firstlinehanging-element-for-frame-for-groupby-format.md)|<span data-ttu-id="5838a-116">Elemento facoltativo.</span><span class="sxs-lookup"><span data-stu-id="5838a-116">Optional element.</span></span><br /><br /> <span data-ttu-id="5838a-117">Specifica il numero di caratteri che la prima riga di dati viene spostata a sinistra.</span><span class="sxs-lookup"><span data-stu-id="5838a-117">Specifies how many characters the first line of data is shifted to the left.</span></span>|
|[<span data-ttu-id="5838a-118">Elemento FirstLineIndent per frame per GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="5838a-118">FirstLineIndent Element for Frame for GroupBy (Format)</span></span>](./firstlineindent-element-for-frame-for-groupby-format.md)|<span data-ttu-id="5838a-119">Elemento facoltativo.</span><span class="sxs-lookup"><span data-stu-id="5838a-119">Optional element.</span></span><br /><br /> <span data-ttu-id="5838a-120">Specifica il numero di caratteri che la prima riga di dati viene spostata a destra.</span><span class="sxs-lookup"><span data-stu-id="5838a-120">Specifies how many characters the first line of data is shifted to the right.</span></span>|
|[<span data-ttu-id="5838a-121">Elemento LeftIndent per frame per GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="5838a-121">LeftIndent Element for Frame for GroupBy (Format)</span></span>](./leftindent-element-for-frame-for-groupby-format.md)|<span data-ttu-id="5838a-122">Elemento facoltativo.</span><span class="sxs-lookup"><span data-stu-id="5838a-122">Optional element.</span></span><br /><br /> <span data-ttu-id="5838a-123">Specifica il numero di caratteri spostati al di fuori del margine sinistro.</span><span class="sxs-lookup"><span data-stu-id="5838a-123">Specifies how many characters the data is shifted away from the left margin.</span></span>|
|<span data-ttu-id="5838a-124">[Elemento RightIndent per frame per GroupBy (Format)](./rightindent-element-for-frame-for-groupby-format.md) Elemento RightIndent</span><span class="sxs-lookup"><span data-stu-id="5838a-124">[RightIndent Element for Frame for GroupBy (Format)](./rightindent-element-for-frame-for-groupby-format.md)RightIndent Element</span></span>|<span data-ttu-id="5838a-125">Elemento facoltativo.</span><span class="sxs-lookup"><span data-stu-id="5838a-125">Optional element.</span></span><br /><br /> <span data-ttu-id="5838a-126">Specifica il numero di caratteri spostati al di fuori del margine destro da parte dei dati.</span><span class="sxs-lookup"><span data-stu-id="5838a-126">Specifies how many characters the data is shifted away from the right margin.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="5838a-127">Elementi padre</span><span class="sxs-lookup"><span data-stu-id="5838a-127">Parent Elements</span></span>

|<span data-ttu-id="5838a-128">Elemento</span><span class="sxs-lookup"><span data-stu-id="5838a-128">Element</span></span>|<span data-ttu-id="5838a-129">Description</span><span class="sxs-lookup"><span data-stu-id="5838a-129">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="5838a-130">Elemento CustomItem per CustomEntry per GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="5838a-130">CustomItem Element for CustomEntry for GroupBy (Format)</span></span>](./customitem-element-for-customentry-for-groupby-format.md)|<span data-ttu-id="5838a-131">Definisce quali dati vengono visualizzati dal controllo e come vengono visualizzati.</span><span class="sxs-lookup"><span data-stu-id="5838a-131">Defines what data is displayed by the control and how it is displayed.</span></span>|

## <a name="remarks"></a><span data-ttu-id="5838a-132">Osservazioni</span><span class="sxs-lookup"><span data-stu-id="5838a-132">Remarks</span></span>

<span data-ttu-id="5838a-133">Non è possibile specificare gli elementi [FirstLineHanging](./firstlinehanging-element-for-frame-for-groupby-format.md) e [FirstLineIndent](./firstlineindent-element-for-frame-for-groupby-format.md) nello stesso elemento `Frame`.</span><span class="sxs-lookup"><span data-stu-id="5838a-133">You cannot specify the [FirstLineHanging](./firstlinehanging-element-for-frame-for-groupby-format.md) and the [FirstLineIndent](./firstlineindent-element-for-frame-for-groupby-format.md) elements in the same `Frame` element.</span></span>

## <a name="see-also"></a><span data-ttu-id="5838a-134">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="5838a-134">See Also</span></span>

[<span data-ttu-id="5838a-135">Elemento FirstLineHanging per frame per GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="5838a-135">FirstLineHanging Element for Frame for GroupBy (Format)</span></span>](./firstlinehanging-element-for-frame-for-groupby-format.md)

[<span data-ttu-id="5838a-136">Elemento FirstLineIndent per frame per GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="5838a-136">FirstLineIndent Element for Frame for GroupBy (Format)</span></span>](./firstlineindent-element-for-frame-for-groupby-format.md)

[<span data-ttu-id="5838a-137">Elemento LeftIndent per frame per GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="5838a-137">LeftIndent Element for Frame for GroupBy (Format)</span></span>](./leftindent-element-for-frame-for-groupby-format.md)

[<span data-ttu-id="5838a-138">Elemento RightIndent per frame per GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="5838a-138">RightIndent Element for Frame for GroupBy (Format)</span></span>](./rightindent-element-for-frame-for-groupby-format.md)

[<span data-ttu-id="5838a-139">Elemento CustomItem per CustomEntry per GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="5838a-139">CustomItem Element for CustomEntry for GroupBy (Format)</span></span>](./customitem-element-for-customentry-for-groupby-format.md)

[<span data-ttu-id="5838a-140">Scrittura di un file di formattazione di PowerShell</span><span class="sxs-lookup"><span data-stu-id="5838a-140">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
