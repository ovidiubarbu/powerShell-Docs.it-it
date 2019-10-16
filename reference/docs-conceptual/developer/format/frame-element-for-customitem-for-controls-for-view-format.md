---
title: Elemento frame per CustomItem per i controlli per la visualizzazione (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: a5729091-78a9-4bc1-abac-210bc20c6dbe
caps.latest.revision: 7
ms.openlocfilehash: f93dc20a9c5f87c14605578062b1e60f5a3d25cf
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/15/2019
ms.locfileid: "72363650"
---
# <a name="frame-element-for-customitem-for-controls-for-view-format"></a><span data-ttu-id="d8606-102">Elemento Frame per CustomItem per Controls per View (formato)</span><span class="sxs-lookup"><span data-stu-id="d8606-102">Frame Element for CustomItem for Controls for View (Format)</span></span>

<span data-ttu-id="d8606-103">Definisce la modalità di visualizzazione dei dati, ad esempio lo spostamento dei dati verso sinistra o verso destra.</span><span class="sxs-lookup"><span data-stu-id="d8606-103">Defines how the data is displayed, such as shifting the data to the left or right.</span></span> <span data-ttu-id="d8606-104">Questo elemento viene utilizzato per la definizione di controlli che possono essere utilizzati da una visualizzazione.</span><span class="sxs-lookup"><span data-stu-id="d8606-104">This element is used when defining controls that can be used by a view.</span></span>

<span data-ttu-id="d8606-105">Elemento di configurazione (Format) elemento ViewDefinitions (Format) elemento di visualizzazione (Format) controlli elemento (Format) elemento di controllo per i controlli per la visualizzazione (formato) elemento CustomControl per il controllo per i controlli per la visualizzazione (formato) elemento CustomEntries per CustomControl per la visualizzazione (Format) elemento CustomEntry per CustomEntries per i controlli per la visualizzazione (formato) CustomItem elemento per CustomEntry per i controlli per la visualizzazione (formato) elemento frame per CustomItem per i controlli per la visualizzazione (formato)</span><span class="sxs-lookup"><span data-stu-id="d8606-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) Controls Element (Format) Control Element for Controls for View (Format) CustomControl Element for Control for Controls for View (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for Controls for View (Format) CustomItem Element for CustomEntry for Controls for View (Format) Frame Element for CustomItem for Controls for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="d8606-106">Sintassi</span><span class="sxs-lookup"><span data-stu-id="d8606-106">Syntax</span></span>

```xml
<Frame>
  <LeftIndent>NumberOfCharactersToShift</LeftIndent>
  <RightIndent>NumberOfCharactersToShift</RightIndent>
  <FirstLineHanging>NumberOfCharactersToShift</FirstLineHanging>
  <FirstLineIndent>NumberOfCharactersToShift</FirstLineIndent>
  <CustomItem>...</CustomItem>
</Frame>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="d8606-107">Attributi ed elementi</span><span class="sxs-lookup"><span data-stu-id="d8606-107">Attributes and Elements</span></span>

<span data-ttu-id="d8606-108">Nelle sezioni seguenti vengono descritti gli attributi, gli elementi figlio e l'elemento padre dell'elemento `Frame`.</span><span class="sxs-lookup"><span data-stu-id="d8606-108">The following sections describe attributes, child elements, and the parent element of the `Frame` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="d8606-109">Attributi</span><span class="sxs-lookup"><span data-stu-id="d8606-109">Attributes</span></span>

<span data-ttu-id="d8606-110">Nessuna.</span><span class="sxs-lookup"><span data-stu-id="d8606-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="d8606-111">Elementi figlio</span><span class="sxs-lookup"><span data-stu-id="d8606-111">Child Elements</span></span>

|<span data-ttu-id="d8606-112">Elemento</span><span class="sxs-lookup"><span data-stu-id="d8606-112">Element</span></span>|<span data-ttu-id="d8606-113">Description</span><span class="sxs-lookup"><span data-stu-id="d8606-113">Description</span></span>|
|-------------|-----------------|
|`CustomItem Element`|<span data-ttu-id="d8606-114">Elemento obbligatorio</span><span class="sxs-lookup"><span data-stu-id="d8606-114">Required Element</span></span>|
|[<span data-ttu-id="d8606-115">Elemento FirstLineHanging del frame di controlli della visualizzazione (Format)</span><span class="sxs-lookup"><span data-stu-id="d8606-115">FirstLineHanging Element of Frame of Controls of View (Format)</span></span>](./firstlinehanging-element-for-frame-for-controls-for-view-format.md)|<span data-ttu-id="d8606-116">Elemento facoltativo.</span><span class="sxs-lookup"><span data-stu-id="d8606-116">Optional element.</span></span><br /><br /> <span data-ttu-id="d8606-117">Specifica il numero di caratteri che la prima riga viene spostata a sinistra.</span><span class="sxs-lookup"><span data-stu-id="d8606-117">Specifies how many characters the first line is shifted to the left.</span></span>|
|[<span data-ttu-id="d8606-118">Elemento FirstLineIndent del frame di controlli della visualizzazione (Format)</span><span class="sxs-lookup"><span data-stu-id="d8606-118">FirstLineIndent Element of Frame of Controls of View (Format)</span></span>](./firstlineindent-element-for-frame-for-controls-for-view-format.md)|<span data-ttu-id="d8606-119">Elemento facoltativo.</span><span class="sxs-lookup"><span data-stu-id="d8606-119">Optional element.</span></span><br /><br /> <span data-ttu-id="d8606-120">Specifica il numero di caratteri che la prima riga viene spostata a destra.</span><span class="sxs-lookup"><span data-stu-id="d8606-120">Specifies how many characters the first line is shifted to the right.</span></span>|
|[<span data-ttu-id="d8606-121">Elemento LeftIndent del frame di controlli della visualizzazione (Format)</span><span class="sxs-lookup"><span data-stu-id="d8606-121">LeftIndent Element of Frame of Controls of View (Format)</span></span>](./leftindent-element-for-frame-for-controls-for-view-format.md)|<span data-ttu-id="d8606-122">Elemento facoltativo.</span><span class="sxs-lookup"><span data-stu-id="d8606-122">Optional element.</span></span><br /><br /> <span data-ttu-id="d8606-123">Specifica il numero di caratteri spostati al di fuori del margine sinistro.</span><span class="sxs-lookup"><span data-stu-id="d8606-123">Specifies how many characters the data is shifted away from the left margin.</span></span>|
|[<span data-ttu-id="d8606-124">Elemento RightIndent del frame di controlli della visualizzazione (Format)</span><span class="sxs-lookup"><span data-stu-id="d8606-124">RightIndent Element of Frame of Controls of View (Format)</span></span>](./rightindent-element-for-frame-for-controls-for-view-format.md)|<span data-ttu-id="d8606-125">Elemento facoltativo.</span><span class="sxs-lookup"><span data-stu-id="d8606-125">Optional element.</span></span><br /><br /> <span data-ttu-id="d8606-126">Specifica il numero di caratteri spostati al di fuori del margine destro da parte dei dati.</span><span class="sxs-lookup"><span data-stu-id="d8606-126">Specifies how many characters the data is shifted away from the right margin.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="d8606-127">Elementi padre</span><span class="sxs-lookup"><span data-stu-id="d8606-127">Parent Elements</span></span>

|<span data-ttu-id="d8606-128">Elemento</span><span class="sxs-lookup"><span data-stu-id="d8606-128">Element</span></span>|<span data-ttu-id="d8606-129">Description</span><span class="sxs-lookup"><span data-stu-id="d8606-129">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="d8606-130">Elemento CustomItem per CustomEntry per i controlli per la visualizzazione (Format)</span><span class="sxs-lookup"><span data-stu-id="d8606-130">CustomItem Element for CustomEntry for Controls for View (Format)</span></span>](./customitem-element-for-customentry-for-controls-for-view-format.md)|<span data-ttu-id="d8606-131">Definisce quali dati vengono visualizzati dal controllo e come vengono visualizzati.</span><span class="sxs-lookup"><span data-stu-id="d8606-131">Defines what data is displayed by the control and how it is displayed.</span></span>|

## <a name="remarks"></a><span data-ttu-id="d8606-132">Osservazioni</span><span class="sxs-lookup"><span data-stu-id="d8606-132">Remarks</span></span>

<span data-ttu-id="d8606-133">Non è possibile specificare gli elementi [FirstLineHanging](./firstlinehanging-element-for-frame-for-controls-for-view-format.md) e [FirstLineIndent](./firstlineindent-element-for-frame-for-controls-for-view-format.md) nello stesso elemento `Frame`.</span><span class="sxs-lookup"><span data-stu-id="d8606-133">You cannot specify the [FirstLineHanging](./firstlinehanging-element-for-frame-for-controls-for-view-format.md) and the [FirstLineIndent](./firstlineindent-element-for-frame-for-controls-for-view-format.md) elements in the same `Frame` element.</span></span>

## <a name="see-also"></a><span data-ttu-id="d8606-134">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="d8606-134">See Also</span></span>

[<span data-ttu-id="d8606-135">Elemento FirstLineHanging del frame di controlli della visualizzazione (Format)</span><span class="sxs-lookup"><span data-stu-id="d8606-135">FirstLineHanging Element of Frame of Controls of View (Format)</span></span>](./firstlinehanging-element-for-frame-for-controls-for-view-format.md)

[<span data-ttu-id="d8606-136">Elemento FirstLineIndent del frame di controlli della visualizzazione (Format)</span><span class="sxs-lookup"><span data-stu-id="d8606-136">FirstLineIndent Element of Frame of Controls of View (Format)</span></span>](./firstlineindent-element-for-frame-for-controls-for-view-format.md)

[<span data-ttu-id="d8606-137">Elemento LeftIndent del frame di controlli della visualizzazione (Format)</span><span class="sxs-lookup"><span data-stu-id="d8606-137">LeftIndent Element of Frame of Controls of View (Format)</span></span>](./leftindent-element-for-frame-for-controls-for-view-format.md)

[<span data-ttu-id="d8606-138">Elemento RightIndent del frame di controlli della visualizzazione (Format)</span><span class="sxs-lookup"><span data-stu-id="d8606-138">RightIndent Element of Frame of Controls of View (Format)</span></span>](./rightindent-element-for-frame-for-controls-for-view-format.md)

[<span data-ttu-id="d8606-139">Elemento CustomItem per CustomEntry per i controlli per la visualizzazione (Format)</span><span class="sxs-lookup"><span data-stu-id="d8606-139">CustomItem Element for CustomEntry for Controls for View (Format)</span></span>](./customitem-element-for-customentry-for-controls-for-view-format.md)

[<span data-ttu-id="d8606-140">Scrittura di un file di formattazione di PowerShell</span><span class="sxs-lookup"><span data-stu-id="d8606-140">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
