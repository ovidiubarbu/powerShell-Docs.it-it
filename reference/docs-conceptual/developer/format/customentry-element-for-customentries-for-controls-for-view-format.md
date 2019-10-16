---
title: Elemento CustomEntry per CustomEntries per i controlli per la visualizzazione (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: c6739205-2bc9-4507-b2af-d19d548c2057
caps.latest.revision: 6
ms.openlocfilehash: b92b99d88992cf13dbf7bfbe88aad603615f3138
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/15/2019
ms.locfileid: "72364050"
---
# <a name="customentry-element-for-customentries-for-controls-for-view-format"></a><span data-ttu-id="e20a1-102">Elemento CustomEntry per CustomEntries per Controls per View (formato)</span><span class="sxs-lookup"><span data-stu-id="e20a1-102">CustomEntry Element for CustomEntries for Controls for View (Format)</span></span>

<span data-ttu-id="e20a1-103">Fornisce una definizione del controllo.</span><span class="sxs-lookup"><span data-stu-id="e20a1-103">Provides a definition of the control.</span></span> <span data-ttu-id="e20a1-104">Questo elemento viene utilizzato per la definizione di controlli che possono essere utilizzati da una visualizzazione.</span><span class="sxs-lookup"><span data-stu-id="e20a1-104">This element is used when defining controls that can be used by a view.</span></span>

<span data-ttu-id="e20a1-105">Elemento di configurazione (Format) elemento ViewDefinitions (Format) elemento di visualizzazione (Format) controlli elemento (Format) elemento di controllo per i controlli per la visualizzazione (formato) elemento CustomControl per il controllo per i controlli per la visualizzazione (formato) elemento CustomEntries per CustomControl per la visualizzazione (formato) elemento CustomEntry per CustomEntries per i controlli per la visualizzazione (formato)</span><span class="sxs-lookup"><span data-stu-id="e20a1-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) Controls Element (Format) Control Element for Controls for View (Format) CustomControl Element for Control for Controls for View (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for Controls for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="e20a1-106">Sintassi</span><span class="sxs-lookup"><span data-stu-id="e20a1-106">Syntax</span></span>

```xml
<CustomEntry>
  <EntrySelectedBy>...</EntrySelectedBy>
  <CustomItem>...</CustomItem>
</CustomEntry>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="e20a1-107">Attributi ed elementi</span><span class="sxs-lookup"><span data-stu-id="e20a1-107">Attributes and Elements</span></span>

<span data-ttu-id="e20a1-108">Nelle sezioni seguenti vengono descritti gli attributi, gli elementi figlio e gli elementi padre dell'elemento `CustomEntry`.</span><span class="sxs-lookup"><span data-stu-id="e20a1-108">The following sections describe attributes, child elements, and the parent elements of the `CustomEntry` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="e20a1-109">Attributi</span><span class="sxs-lookup"><span data-stu-id="e20a1-109">Attributes</span></span>

<span data-ttu-id="e20a1-110">Nessuna.</span><span class="sxs-lookup"><span data-stu-id="e20a1-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="e20a1-111">Elementi figlio</span><span class="sxs-lookup"><span data-stu-id="e20a1-111">Child Elements</span></span>

|<span data-ttu-id="e20a1-112">Elemento</span><span class="sxs-lookup"><span data-stu-id="e20a1-112">Element</span></span>|<span data-ttu-id="e20a1-113">Description</span><span class="sxs-lookup"><span data-stu-id="e20a1-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="e20a1-114">Elemento EntrySelectedBy per CustomEntry per i controlli per la visualizzazione (Format)</span><span class="sxs-lookup"><span data-stu-id="e20a1-114">EntrySelectedBy Element for CustomEntry for Controls for View (Format)</span></span>](./entryselectedby-element-for-customentry-for-controls-for-view-format.md)|<span data-ttu-id="e20a1-115">Elemento facoltativo.</span><span class="sxs-lookup"><span data-stu-id="e20a1-115">Optional element.</span></span><br /><br /> <span data-ttu-id="e20a1-116">Definisce i tipi .NET che utilizzano questa definizione di controllo o la condizione che deve esistere affinché questa definizione venga utilizzata.</span><span class="sxs-lookup"><span data-stu-id="e20a1-116">Defines the .NET types that use this control definition or the condition that must exist for this definition to be used.</span></span>|
|[<span data-ttu-id="e20a1-117">Elemento CustomItem per CustomEntry per i controlli per la visualizzazione (Format)</span><span class="sxs-lookup"><span data-stu-id="e20a1-117">CustomItem Element for CustomEntry for Controls for View (Format)</span></span>](./customitem-element-for-customentry-for-controls-for-view-format.md)|<span data-ttu-id="e20a1-118">Elemento obbligatorio.</span><span class="sxs-lookup"><span data-stu-id="e20a1-118">Required element.</span></span><br /><br /> <span data-ttu-id="e20a1-119">Definisce la modalità di visualizzazione dei dati da parte del controllo.</span><span class="sxs-lookup"><span data-stu-id="e20a1-119">Defines how the control displays the data.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="e20a1-120">Elementi padre</span><span class="sxs-lookup"><span data-stu-id="e20a1-120">Parent Elements</span></span>

|<span data-ttu-id="e20a1-121">Elemento</span><span class="sxs-lookup"><span data-stu-id="e20a1-121">Element</span></span>|<span data-ttu-id="e20a1-122">Description</span><span class="sxs-lookup"><span data-stu-id="e20a1-122">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="e20a1-123">Elemento CustomEntries per CustomControl per View (Format)</span><span class="sxs-lookup"><span data-stu-id="e20a1-123">CustomEntries Element for CustomControl for View (Format)</span></span>](./customentries-element-for-customcontrol-for-view-format.md)|<span data-ttu-id="e20a1-124">Fornisce le definizioni per il controllo.</span><span class="sxs-lookup"><span data-stu-id="e20a1-124">Provides the definitions for the control.</span></span>|

## <a name="remarks"></a><span data-ttu-id="e20a1-125">Osservazioni</span><span class="sxs-lookup"><span data-stu-id="e20a1-125">Remarks</span></span>

## <a name="see-also"></a><span data-ttu-id="e20a1-126">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="e20a1-126">See Also</span></span>

[<span data-ttu-id="e20a1-127">Elemento CustomEntries per CustomControl per View (Format)</span><span class="sxs-lookup"><span data-stu-id="e20a1-127">CustomEntries Element for CustomControl for View (Format)</span></span>](./customentries-element-for-customcontrol-for-view-format.md)

[<span data-ttu-id="e20a1-128">Scrittura di un file di formattazione di PowerShell</span><span class="sxs-lookup"><span data-stu-id="e20a1-128">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
