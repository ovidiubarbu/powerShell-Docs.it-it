---
title: Elemento CustomEntry per CustomEntries per i controlli per la visualizzazione (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: c6739205-2bc9-4507-b2af-d19d548c2057
caps.latest.revision: 6
ms.openlocfilehash: b92b99d88992cf13dbf7bfbe88aad603615f3138
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62066499"
---
# <a name="customentry-element-for-customentries-for-controls-for-view-format"></a><span data-ttu-id="6b4c0-102">Elemento CustomEntry per CustomEntries per Controls per View (formato)</span><span class="sxs-lookup"><span data-stu-id="6b4c0-102">CustomEntry Element for CustomEntries for Controls for View (Format)</span></span>

<span data-ttu-id="6b4c0-103">Fornisce una definizione del controllo.</span><span class="sxs-lookup"><span data-stu-id="6b4c0-103">Provides a definition of the control.</span></span> <span data-ttu-id="6b4c0-104">Questo elemento viene usato quando si definiscono i controlli che possono essere usati da una vista.</span><span class="sxs-lookup"><span data-stu-id="6b4c0-104">This element is used when defining controls that can be used by a view.</span></span>

<span data-ttu-id="6b4c0-105">Elemento (formato) elemento ViewDefinitions (formato) visualizzazione elemento (formato) i controlli elemento (formato) controllo elemento di configurazione per i controlli elemento di visualizzazione (formato) CustomControl per il controllo per i controlli elemento di visualizzazione (formato) CustomEntries per CustomControl elemento di visualizzazione (formato) CustomEntry per CustomEntries per i controlli per la visualizzazione (formato)</span><span class="sxs-lookup"><span data-stu-id="6b4c0-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) Controls Element (Format) Control Element for Controls for View (Format) CustomControl Element for Control for Controls for View (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for Controls for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="6b4c0-106">Sintassi</span><span class="sxs-lookup"><span data-stu-id="6b4c0-106">Syntax</span></span>

```xml
<CustomEntry>
  <EntrySelectedBy>...</EntrySelectedBy>
  <CustomItem>...</CustomItem>
</CustomEntry>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="6b4c0-107">Elementi e attributi</span><span class="sxs-lookup"><span data-stu-id="6b4c0-107">Attributes and Elements</span></span>

<span data-ttu-id="6b4c0-108">Le sezioni seguenti descrivono gli attributi, elementi figlio e gli elementi padre del `CustomEntry` elemento.</span><span class="sxs-lookup"><span data-stu-id="6b4c0-108">The following sections describe attributes, child elements, and the parent elements of the `CustomEntry` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="6b4c0-109">Attributes</span><span class="sxs-lookup"><span data-stu-id="6b4c0-109">Attributes</span></span>

<span data-ttu-id="6b4c0-110">Nessuna.</span><span class="sxs-lookup"><span data-stu-id="6b4c0-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="6b4c0-111">Elementi figlio</span><span class="sxs-lookup"><span data-stu-id="6b4c0-111">Child Elements</span></span>

|<span data-ttu-id="6b4c0-112">Elemento</span><span class="sxs-lookup"><span data-stu-id="6b4c0-112">Element</span></span>|<span data-ttu-id="6b4c0-113">Description</span><span class="sxs-lookup"><span data-stu-id="6b4c0-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="6b4c0-114">Elemento EntrySelectedBy per CustomEntry per i controlli per la visualizzazione (formato)</span><span class="sxs-lookup"><span data-stu-id="6b4c0-114">EntrySelectedBy Element for CustomEntry for Controls for View (Format)</span></span>](./entryselectedby-element-for-customentry-for-controls-for-view-format.md)|<span data-ttu-id="6b4c0-115">Elemento facoltativo.</span><span class="sxs-lookup"><span data-stu-id="6b4c0-115">Optional element.</span></span><br /><br /> <span data-ttu-id="6b4c0-116">Definisce i tipi .NET che usano questa definizione di controllo o la condizione che deve essere presente per questa definizione da usare.</span><span class="sxs-lookup"><span data-stu-id="6b4c0-116">Defines the .NET types that use this control definition or the condition that must exist for this definition to be used.</span></span>|
|[<span data-ttu-id="6b4c0-117">Elemento CustomItem per CustomEntry per i controlli per la visualizzazione (formato)</span><span class="sxs-lookup"><span data-stu-id="6b4c0-117">CustomItem Element for CustomEntry for Controls for View (Format)</span></span>](./customitem-element-for-customentry-for-controls-for-view-format.md)|<span data-ttu-id="6b4c0-118">Elemento obbligatorio.</span><span class="sxs-lookup"><span data-stu-id="6b4c0-118">Required element.</span></span><br /><br /> <span data-ttu-id="6b4c0-119">Definisce come il controllo Visualizza i dati.</span><span class="sxs-lookup"><span data-stu-id="6b4c0-119">Defines how the control displays the data.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="6b4c0-120">Elementi padre</span><span class="sxs-lookup"><span data-stu-id="6b4c0-120">Parent Elements</span></span>

|<span data-ttu-id="6b4c0-121">Elemento</span><span class="sxs-lookup"><span data-stu-id="6b4c0-121">Element</span></span>|<span data-ttu-id="6b4c0-122">Description</span><span class="sxs-lookup"><span data-stu-id="6b4c0-122">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="6b4c0-123">Elemento CustomEntries per CustomControl per visualizzazione (formato)</span><span class="sxs-lookup"><span data-stu-id="6b4c0-123">CustomEntries Element for CustomControl for View (Format)</span></span>](./customentries-element-for-customcontrol-for-view-format.md)|<span data-ttu-id="6b4c0-124">Fornisce le definizioni per il controllo.</span><span class="sxs-lookup"><span data-stu-id="6b4c0-124">Provides the definitions for the control.</span></span>|

## <a name="remarks"></a><span data-ttu-id="6b4c0-125">Osservazioni</span><span class="sxs-lookup"><span data-stu-id="6b4c0-125">Remarks</span></span>

## <a name="see-also"></a><span data-ttu-id="6b4c0-126">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="6b4c0-126">See Also</span></span>

[<span data-ttu-id="6b4c0-127">Elemento CustomEntries per CustomControl per visualizzazione (formato)</span><span class="sxs-lookup"><span data-stu-id="6b4c0-127">CustomEntries Element for CustomControl for View (Format)</span></span>](./customentries-element-for-customcontrol-for-view-format.md)

[<span data-ttu-id="6b4c0-128">La scrittura di un File di formattazione di PowerShell</span><span class="sxs-lookup"><span data-stu-id="6b4c0-128">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
