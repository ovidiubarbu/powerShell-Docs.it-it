---
title: Elemento frame per CustomItem per CustomControl per View (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e1a13100-41a4-4847-9f07-458c85783505
caps.latest.revision: 6
ms.openlocfilehash: 925ef86e61801f5a66f89dd25e0756f00dd35155
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/15/2019
ms.locfileid: "72363640"
---
# <a name="frame-element-for-customitem-for-customcontrol-for-view-format"></a><span data-ttu-id="9f8ea-102">Elemento Frame per CustomItem per CustomControl per View (formato)</span><span class="sxs-lookup"><span data-stu-id="9f8ea-102">Frame Element for CustomItem for CustomControl for View (Format)</span></span>

<span data-ttu-id="9f8ea-103">Definisce la modalità di visualizzazione dei dati, ad esempio lo spostamento dei dati verso sinistra o verso destra.</span><span class="sxs-lookup"><span data-stu-id="9f8ea-103">Defines how the data is displayed, such as shifting the data to the left or right.</span></span> <span data-ttu-id="9f8ea-104">Questo elemento viene utilizzato quando si definisce una visualizzazione controlli personalizzata.</span><span class="sxs-lookup"><span data-stu-id="9f8ea-104">This element is used when defining a custom control view.</span></span>

<span data-ttu-id="9f8ea-105">Elemento Configuration (Format) elemento ViewDefinitions (Format) elemento View (Format) elemento CustomControl (Format) elemento CustomEntries per CustomControl per la vista (Format) CustomEntry elemento per CustomEntries per la visualizzazione (Format) CustomItem elemento per CustomEntry per l'elemento frame CustomControlView (Format) per CustomItem per CustomControl per la visualizzazione (Format)</span><span class="sxs-lookup"><span data-stu-id="9f8ea-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) CustomControl Element (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for View (Format) CustomItem Element for CustomEntry for CustomControlView (Format) Frame Element for CustomItem for CustomControl for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="9f8ea-106">Sintassi</span><span class="sxs-lookup"><span data-stu-id="9f8ea-106">Syntax</span></span>

```xml
<Frame>
  <LeftIndent>NumberOfCharactersToShift</LeftIndent>
  <RightIndent>NumberOfCharactersToShift</RightIndent>
  <FirstLineHanging>NumberOfCharactersToShift</FirstLineHanging>
  <FirstLineIndent>NumberOfCharactersToShift</FirstLineIndent>
  <CustomItem>...</CustomItem>
</Frame>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="9f8ea-107">Attributi ed elementi</span><span class="sxs-lookup"><span data-stu-id="9f8ea-107">Attributes and Elements</span></span>

<span data-ttu-id="9f8ea-108">Nelle sezioni seguenti vengono descritti gli attributi, gli elementi figlio e l'elemento padre dell'elemento `Frame`.</span><span class="sxs-lookup"><span data-stu-id="9f8ea-108">The following sections describe attributes, child elements, and the parent element of the `Frame` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="9f8ea-109">Attributi</span><span class="sxs-lookup"><span data-stu-id="9f8ea-109">Attributes</span></span>

<span data-ttu-id="9f8ea-110">Nessuna.</span><span class="sxs-lookup"><span data-stu-id="9f8ea-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="9f8ea-111">Elementi figlio</span><span class="sxs-lookup"><span data-stu-id="9f8ea-111">Child Elements</span></span>

|<span data-ttu-id="9f8ea-112">Elemento</span><span class="sxs-lookup"><span data-stu-id="9f8ea-112">Element</span></span>|<span data-ttu-id="9f8ea-113">Description</span><span class="sxs-lookup"><span data-stu-id="9f8ea-113">Description</span></span>|
|-------------|-----------------|
|`CustomItem Element`|<span data-ttu-id="9f8ea-114">Elemento obbligatorio</span><span class="sxs-lookup"><span data-stu-id="9f8ea-114">Required Element</span></span>|
|[<span data-ttu-id="9f8ea-115">Elemento FirstLineHanging</span><span class="sxs-lookup"><span data-stu-id="9f8ea-115">FirstLineHanging Element</span></span>](./firstlinehanging-element-for-frame-for-customcontrol-for-view-format.md)|<span data-ttu-id="9f8ea-116">Elemento facoltativo.</span><span class="sxs-lookup"><span data-stu-id="9f8ea-116">Optional element.</span></span><br /><br /> <span data-ttu-id="9f8ea-117">Specifica il numero di caratteri che la prima riga di dati viene spostata a sinistra.</span><span class="sxs-lookup"><span data-stu-id="9f8ea-117">Specifies how many characters the first line of data is shifted to the left.</span></span>|
|[<span data-ttu-id="9f8ea-118">Elemento FirstLineIndent</span><span class="sxs-lookup"><span data-stu-id="9f8ea-118">FirstLineIndent Element</span></span>](./firstlineindent-element-for-frame-for-customcontrol-for-view-format.md)|<span data-ttu-id="9f8ea-119">Elemento facoltativo.</span><span class="sxs-lookup"><span data-stu-id="9f8ea-119">Optional element.</span></span><br /><br /> <span data-ttu-id="9f8ea-120">Specifica il numero di caratteri che la prima riga di dati viene spostata a destra.</span><span class="sxs-lookup"><span data-stu-id="9f8ea-120">Specifies how many characters the first line of data is shifted to the right.</span></span>|
|[<span data-ttu-id="9f8ea-121">Elemento LeftIndent</span><span class="sxs-lookup"><span data-stu-id="9f8ea-121">LeftIndent Element</span></span>](./leftindent-element-for-frame-for-customcontrol-for-view-format.md)|<span data-ttu-id="9f8ea-122">Elemento facoltativo.</span><span class="sxs-lookup"><span data-stu-id="9f8ea-122">Optional element.</span></span><br /><br /> <span data-ttu-id="9f8ea-123">Specifica il numero di caratteri spostati al di fuori del margine sinistro.</span><span class="sxs-lookup"><span data-stu-id="9f8ea-123">Specifies how many characters the data is shifted away from the left margin.</span></span>|
|[<span data-ttu-id="9f8ea-124">Elemento RightIndent</span><span class="sxs-lookup"><span data-stu-id="9f8ea-124">RightIndent Element</span></span>](./rightindent-element-for-frame-for-customcontrol-for-view-format.md)|<span data-ttu-id="9f8ea-125">Elemento facoltativo.</span><span class="sxs-lookup"><span data-stu-id="9f8ea-125">Optional element.</span></span><br /><br /> <span data-ttu-id="9f8ea-126">Specifica il numero di caratteri spostati al di fuori del margine destro da parte dei dati.</span><span class="sxs-lookup"><span data-stu-id="9f8ea-126">Specifies how many characters the data is shifted away from the right margin.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="9f8ea-127">Elementi padre</span><span class="sxs-lookup"><span data-stu-id="9f8ea-127">Parent Elements</span></span>

|<span data-ttu-id="9f8ea-128">Elemento</span><span class="sxs-lookup"><span data-stu-id="9f8ea-128">Element</span></span>|<span data-ttu-id="9f8ea-129">Description</span><span class="sxs-lookup"><span data-stu-id="9f8ea-129">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="9f8ea-130">Elemento CustomItem per CustomEntry per View (Format)</span><span class="sxs-lookup"><span data-stu-id="9f8ea-130">CustomItem Element for CustomEntry for View (Format)</span></span>](./customitem-element-for-customentry-for-customcontrol-for-view-format.md)|<span data-ttu-id="9f8ea-131">Definisce quali dati vengono visualizzati dal controllo e come vengono visualizzati.</span><span class="sxs-lookup"><span data-stu-id="9f8ea-131">Defines what data is displayed by the control and how it is displayed.</span></span>|

## <a name="remarks"></a><span data-ttu-id="9f8ea-132">Osservazioni</span><span class="sxs-lookup"><span data-stu-id="9f8ea-132">Remarks</span></span>

<span data-ttu-id="9f8ea-133">Non è possibile specificare gli elementi [FirstLineHanging](./firstlinehanging-element-for-frame-for-customcontrol-for-view-format.md) e [FirstLineIndent](./firstlineindent-element-for-frame-for-customcontrol-for-view-format.md) nello stesso elemento `Frame`.</span><span class="sxs-lookup"><span data-stu-id="9f8ea-133">You cannot specify the [FirstLineHanging](./firstlinehanging-element-for-frame-for-customcontrol-for-view-format.md) and the [FirstLineIndent](./firstlineindent-element-for-frame-for-customcontrol-for-view-format.md) elements in the same `Frame` element.</span></span>

## <a name="see-also"></a><span data-ttu-id="9f8ea-134">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="9f8ea-134">See Also</span></span>

[<span data-ttu-id="9f8ea-135">Elemento FirstLineHanging</span><span class="sxs-lookup"><span data-stu-id="9f8ea-135">FirstLineHanging Element</span></span>](./firstlinehanging-element-for-frame-for-customcontrol-for-view-format.md)

[<span data-ttu-id="9f8ea-136">Elemento FirstLineIndent</span><span class="sxs-lookup"><span data-stu-id="9f8ea-136">FirstLineIndent Element</span></span>](./firstlineindent-element-for-frame-for-customcontrol-for-view-format.md)

[<span data-ttu-id="9f8ea-137">Elemento LeftIndent</span><span class="sxs-lookup"><span data-stu-id="9f8ea-137">LeftIndent Element</span></span>](./leftindent-element-for-frame-for-customcontrol-for-view-format.md)

[<span data-ttu-id="9f8ea-138">Elemento RightIndent</span><span class="sxs-lookup"><span data-stu-id="9f8ea-138">RightIndent Element</span></span>](./rightindent-element-for-frame-for-customcontrol-for-view-format.md)

[<span data-ttu-id="9f8ea-139">Elemento CustomItem per CustomEntry per View (Format)</span><span class="sxs-lookup"><span data-stu-id="9f8ea-139">CustomItem Element for CustomEntry for View (Format)</span></span>](./customitem-element-for-customentry-for-customcontrol-for-view-format.md)

[<span data-ttu-id="9f8ea-140">Scrittura di un file di formattazione di PowerShell</span><span class="sxs-lookup"><span data-stu-id="9f8ea-140">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
