---
title: Elemento dei frame per CustomItem per CustomControl per visualizzazione (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e1a13100-41a4-4847-9f07-458c85783505
caps.latest.revision: 6
ms.openlocfilehash: 925ef86e61801f5a66f89dd25e0756f00dd35155
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62065581"
---
# <a name="frame-element-for-customitem-for-customcontrol-for-view-format"></a><span data-ttu-id="c9982-102">Elemento Frame per CustomItem per CustomControl per View (formato)</span><span class="sxs-lookup"><span data-stu-id="c9982-102">Frame Element for CustomItem for CustomControl for View (Format)</span></span>

<span data-ttu-id="c9982-103">Definisce come verranno visualizzati i dati, ad esempio lo spostamento di dati a sinistra o destra.</span><span class="sxs-lookup"><span data-stu-id="c9982-103">Defines how the data is displayed, such as shifting the data to the left or right.</span></span> <span data-ttu-id="c9982-104">Questo elemento viene usato quando si definisce una vista di controllo personalizzato.</span><span class="sxs-lookup"><span data-stu-id="c9982-104">This element is used when defining a custom control view.</span></span>

<span data-ttu-id="c9982-105">Elemento (formato) elemento ViewDefinitions (formato) visualizzazione elemento (formato) elemento CustomControl (formato) CustomEntries elemento di configurazione per CustomControl elemento di visualizzazione (formato) CustomEntry per CustomEntries per elemento CustomItem visualizzazione (formato) CustomEntry per elemento Frame CustomControlView (formato) per CustomItem per CustomControl per visualizzazione (formato)</span><span class="sxs-lookup"><span data-stu-id="c9982-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) CustomControl Element (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for View (Format) CustomItem Element for CustomEntry for CustomControlView (Format) Frame Element for CustomItem for CustomControl for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="c9982-106">Sintassi</span><span class="sxs-lookup"><span data-stu-id="c9982-106">Syntax</span></span>

```xml
<Frame>
  <LeftIndent>NumberOfCharactersToShift</LeftIndent>
  <RightIndent>NumberOfCharactersToShift</RightIndent>
  <FirstLineHanging>NumberOfCharactersToShift</FirstLineHanging>
  <FirstLineIndent>NumberOfCharactersToShift</FirstLineIndent>
  <CustomItem>...</CustomItem>
</Frame>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="c9982-107">Elementi e attributi</span><span class="sxs-lookup"><span data-stu-id="c9982-107">Attributes and Elements</span></span>

<span data-ttu-id="c9982-108">Le sezioni seguenti descrivono gli attributi e gli elementi figlio dell'elemento padre del `Frame` elemento.</span><span class="sxs-lookup"><span data-stu-id="c9982-108">The following sections describe attributes, child elements, and the parent element of the `Frame` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="c9982-109">Attributes</span><span class="sxs-lookup"><span data-stu-id="c9982-109">Attributes</span></span>

<span data-ttu-id="c9982-110">Nessuna.</span><span class="sxs-lookup"><span data-stu-id="c9982-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="c9982-111">Elementi figlio</span><span class="sxs-lookup"><span data-stu-id="c9982-111">Child Elements</span></span>

|<span data-ttu-id="c9982-112">Elemento</span><span class="sxs-lookup"><span data-stu-id="c9982-112">Element</span></span>|<span data-ttu-id="c9982-113">Description</span><span class="sxs-lookup"><span data-stu-id="c9982-113">Description</span></span>|
|-------------|-----------------|
|`CustomItem Element`|<span data-ttu-id="c9982-114">Elemento obbligatorio</span><span class="sxs-lookup"><span data-stu-id="c9982-114">Required Element</span></span>|
|[<span data-ttu-id="c9982-115">Elemento FirstLineHanging</span><span class="sxs-lookup"><span data-stu-id="c9982-115">FirstLineHanging Element</span></span>](./firstlinehanging-element-for-frame-for-customcontrol-for-view-format.md)|<span data-ttu-id="c9982-116">Elemento facoltativo.</span><span class="sxs-lookup"><span data-stu-id="c9982-116">Optional element.</span></span><br /><br /> <span data-ttu-id="c9982-117">Specifica il numero di caratteri la prima riga di dati verrà spostata a sinistra.</span><span class="sxs-lookup"><span data-stu-id="c9982-117">Specifies how many characters the first line of data is shifted to the left.</span></span>|
|[<span data-ttu-id="c9982-118">Elemento FirstLineIndent</span><span class="sxs-lookup"><span data-stu-id="c9982-118">FirstLineIndent Element</span></span>](./firstlineindent-element-for-frame-for-customcontrol-for-view-format.md)|<span data-ttu-id="c9982-119">Elemento facoltativo.</span><span class="sxs-lookup"><span data-stu-id="c9982-119">Optional element.</span></span><br /><br /> <span data-ttu-id="c9982-120">Specifica il numero di caratteri la prima riga di dati verrà spostata a destra.</span><span class="sxs-lookup"><span data-stu-id="c9982-120">Specifies how many characters the first line of data is shifted to the right.</span></span>|
|[<span data-ttu-id="c9982-121">Elemento LeftIndent</span><span class="sxs-lookup"><span data-stu-id="c9982-121">LeftIndent Element</span></span>](./leftindent-element-for-frame-for-customcontrol-for-view-format.md)|<span data-ttu-id="c9982-122">Elemento facoltativo.</span><span class="sxs-lookup"><span data-stu-id="c9982-122">Optional element.</span></span><br /><br /> <span data-ttu-id="c9982-123">Specifica quanti caratteri di dati viene spostati dal margine sinistro.</span><span class="sxs-lookup"><span data-stu-id="c9982-123">Specifies how many characters the data is shifted away from the left margin.</span></span>|
|[<span data-ttu-id="c9982-124">Elemento RightIndent</span><span class="sxs-lookup"><span data-stu-id="c9982-124">RightIndent Element</span></span>](./rightindent-element-for-frame-for-customcontrol-for-view-format.md)|<span data-ttu-id="c9982-125">Elemento facoltativo.</span><span class="sxs-lookup"><span data-stu-id="c9982-125">Optional element.</span></span><br /><br /> <span data-ttu-id="c9982-126">Specifica quanti caratteri di dati viene spostati dal margine destro.</span><span class="sxs-lookup"><span data-stu-id="c9982-126">Specifies how many characters the data is shifted away from the right margin.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="c9982-127">Elementi padre</span><span class="sxs-lookup"><span data-stu-id="c9982-127">Parent Elements</span></span>

|<span data-ttu-id="c9982-128">Elemento</span><span class="sxs-lookup"><span data-stu-id="c9982-128">Element</span></span>|<span data-ttu-id="c9982-129">Description</span><span class="sxs-lookup"><span data-stu-id="c9982-129">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="c9982-130">Elemento CustomItem per CustomEntry per visualizzazione (formato)</span><span class="sxs-lookup"><span data-stu-id="c9982-130">CustomItem Element for CustomEntry for View (Format)</span></span>](./customitem-element-for-customentry-for-customcontrol-for-view-format.md)|<span data-ttu-id="c9982-131">Definisce i dati che vengano visualizzati dal controllo e la modalità di visualizzazione.</span><span class="sxs-lookup"><span data-stu-id="c9982-131">Defines what data is displayed by the control and how it is displayed.</span></span>|

## <a name="remarks"></a><span data-ttu-id="c9982-132">Osservazioni</span><span class="sxs-lookup"><span data-stu-id="c9982-132">Remarks</span></span>

<span data-ttu-id="c9982-133">Non è possibile specificare il [FirstLineHanging](./firstlinehanging-element-for-frame-for-customcontrol-for-view-format.md) e il [FirstLineIndent](./firstlineindent-element-for-frame-for-customcontrol-for-view-format.md) elementi nello stesso `Frame` elemento.</span><span class="sxs-lookup"><span data-stu-id="c9982-133">You cannot specify the [FirstLineHanging](./firstlinehanging-element-for-frame-for-customcontrol-for-view-format.md) and the [FirstLineIndent](./firstlineindent-element-for-frame-for-customcontrol-for-view-format.md) elements in the same `Frame` element.</span></span>

## <a name="see-also"></a><span data-ttu-id="c9982-134">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="c9982-134">See Also</span></span>

[<span data-ttu-id="c9982-135">Elemento FirstLineHanging</span><span class="sxs-lookup"><span data-stu-id="c9982-135">FirstLineHanging Element</span></span>](./firstlinehanging-element-for-frame-for-customcontrol-for-view-format.md)

[<span data-ttu-id="c9982-136">Elemento FirstLineIndent</span><span class="sxs-lookup"><span data-stu-id="c9982-136">FirstLineIndent Element</span></span>](./firstlineindent-element-for-frame-for-customcontrol-for-view-format.md)

[<span data-ttu-id="c9982-137">Elemento LeftIndent</span><span class="sxs-lookup"><span data-stu-id="c9982-137">LeftIndent Element</span></span>](./leftindent-element-for-frame-for-customcontrol-for-view-format.md)

[<span data-ttu-id="c9982-138">Elemento RightIndent</span><span class="sxs-lookup"><span data-stu-id="c9982-138">RightIndent Element</span></span>](./rightindent-element-for-frame-for-customcontrol-for-view-format.md)

[<span data-ttu-id="c9982-139">Elemento CustomItem per CustomEntry per visualizzazione (formato)</span><span class="sxs-lookup"><span data-stu-id="c9982-139">CustomItem Element for CustomEntry for View (Format)</span></span>](./customitem-element-for-customentry-for-customcontrol-for-view-format.md)

[<span data-ttu-id="c9982-140">La scrittura di un File di formattazione di PowerShell</span><span class="sxs-lookup"><span data-stu-id="c9982-140">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
