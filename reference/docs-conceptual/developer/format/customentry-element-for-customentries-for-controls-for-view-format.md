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
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/05/2019
ms.locfileid: "72364050"
---
# <a name="customentry-element-for-customentries-for-controls-for-view-format"></a><span data-ttu-id="46a07-102">Elemento CustomEntry per CustomEntries per Controls per View (formato)</span><span class="sxs-lookup"><span data-stu-id="46a07-102">CustomEntry Element for CustomEntries for Controls for View (Format)</span></span>

<span data-ttu-id="46a07-103">Fornisce una definizione del controllo.</span><span class="sxs-lookup"><span data-stu-id="46a07-103">Provides a definition of the control.</span></span> <span data-ttu-id="46a07-104">Questo elemento viene utilizzato per la definizione di controlli che possono essere utilizzati da una visualizzazione.</span><span class="sxs-lookup"><span data-stu-id="46a07-104">This element is used when defining controls that can be used by a view.</span></span>

<span data-ttu-id="46a07-105">Elemento di configurazione (Format) elemento ViewDefinitions (Format) elemento di visualizzazione (Format) controlli elemento (Format) elemento di controllo per i controlli per la visualizzazione (formato) elemento CustomControl per il controllo per i controlli per la visualizzazione (formato) elemento CustomEntries per CustomControl per la visualizzazione (formato) elemento CustomEntry per CustomEntries per i controlli per la visualizzazione (formato)</span><span class="sxs-lookup"><span data-stu-id="46a07-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) Controls Element (Format) Control Element for Controls for View (Format) CustomControl Element for Control for Controls for View (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for Controls for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="46a07-106">Sintassi</span><span class="sxs-lookup"><span data-stu-id="46a07-106">Syntax</span></span>

```xml
<CustomEntry>
  <EntrySelectedBy>...</EntrySelectedBy>
  <CustomItem>...</CustomItem>
</CustomEntry>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="46a07-107">Attributi ed elementi</span><span class="sxs-lookup"><span data-stu-id="46a07-107">Attributes and Elements</span></span>

<span data-ttu-id="46a07-108">Nelle sezioni seguenti vengono descritti gli attributi, gli elementi figlio e gli elementi padre dell'elemento `CustomEntry`.</span><span class="sxs-lookup"><span data-stu-id="46a07-108">The following sections describe attributes, child elements, and the parent elements of the `CustomEntry` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="46a07-109">Attributi</span><span class="sxs-lookup"><span data-stu-id="46a07-109">Attributes</span></span>

<span data-ttu-id="46a07-110">Nessuna.</span><span class="sxs-lookup"><span data-stu-id="46a07-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="46a07-111">Elementi figlio</span><span class="sxs-lookup"><span data-stu-id="46a07-111">Child Elements</span></span>

|<span data-ttu-id="46a07-112">Elemento</span><span class="sxs-lookup"><span data-stu-id="46a07-112">Element</span></span>|<span data-ttu-id="46a07-113">Description</span><span class="sxs-lookup"><span data-stu-id="46a07-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="46a07-114">Elemento EntrySelectedBy per CustomEntry per i controlli per la visualizzazione (Format)</span><span class="sxs-lookup"><span data-stu-id="46a07-114">EntrySelectedBy Element for CustomEntry for Controls for View (Format)</span></span>](./entryselectedby-element-for-customentry-for-controls-for-view-format.md)|<span data-ttu-id="46a07-115">Elemento facoltativo.</span><span class="sxs-lookup"><span data-stu-id="46a07-115">Optional element.</span></span><br /><br /> <span data-ttu-id="46a07-116">Definisce i tipi .NET che utilizzano questa definizione di controllo o la condizione che deve esistere affinché questa definizione venga utilizzata.</span><span class="sxs-lookup"><span data-stu-id="46a07-116">Defines the .NET types that use this control definition or the condition that must exist for this definition to be used.</span></span>|
|[<span data-ttu-id="46a07-117">Elemento CustomItem per CustomEntry per i controlli per la visualizzazione (Format)</span><span class="sxs-lookup"><span data-stu-id="46a07-117">CustomItem Element for CustomEntry for Controls for View (Format)</span></span>](./customitem-element-for-customentry-for-controls-for-view-format.md)|<span data-ttu-id="46a07-118">Elemento obbligatorio.</span><span class="sxs-lookup"><span data-stu-id="46a07-118">Required element.</span></span><br /><br /> <span data-ttu-id="46a07-119">Definisce la modalità di visualizzazione dei dati da parte del controllo.</span><span class="sxs-lookup"><span data-stu-id="46a07-119">Defines how the control displays the data.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="46a07-120">Elementi padre</span><span class="sxs-lookup"><span data-stu-id="46a07-120">Parent Elements</span></span>

|<span data-ttu-id="46a07-121">Elemento</span><span class="sxs-lookup"><span data-stu-id="46a07-121">Element</span></span>|<span data-ttu-id="46a07-122">Description</span><span class="sxs-lookup"><span data-stu-id="46a07-122">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="46a07-123">Elemento CustomEntries per CustomControl per View (Format)</span><span class="sxs-lookup"><span data-stu-id="46a07-123">CustomEntries Element for CustomControl for View (Format)</span></span>](./customentries-element-for-customcontrol-for-view-format.md)|<span data-ttu-id="46a07-124">Fornisce le definizioni per il controllo.</span><span class="sxs-lookup"><span data-stu-id="46a07-124">Provides the definitions for the control.</span></span>|

## <a name="remarks"></a><span data-ttu-id="46a07-125">Osservazioni</span><span class="sxs-lookup"><span data-stu-id="46a07-125">Remarks</span></span>

## <a name="see-also"></a><span data-ttu-id="46a07-126">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="46a07-126">See Also</span></span>

[<span data-ttu-id="46a07-127">Elemento CustomEntries per CustomControl per View (Format)</span><span class="sxs-lookup"><span data-stu-id="46a07-127">CustomEntries Element for CustomControl for View (Format)</span></span>](./customentries-element-for-customcontrol-for-view-format.md)

[<span data-ttu-id="46a07-128">Scrittura di un file di formattazione di PowerShell</span><span class="sxs-lookup"><span data-stu-id="46a07-128">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
