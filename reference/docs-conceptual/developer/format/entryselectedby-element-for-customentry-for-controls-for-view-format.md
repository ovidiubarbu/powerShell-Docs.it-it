---
title: Elemento EntrySelectedBy per CustomEntry per i controlli per la visualizzazione (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: b3d80a7d-3797-4c46-ae74-ae5cda79b24f
caps.latest.revision: 8
ms.openlocfilehash: efb20c3f2077547e6eb3cb28240512b444f9c481
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/05/2019
ms.locfileid: "72363890"
---
# <a name="entryselectedby-element-for-customentry-for-controls-for-view-format"></a><span data-ttu-id="506ef-102">Elemento EntrySelectedBy per CustomEntry per Controls per View (formato)</span><span class="sxs-lookup"><span data-stu-id="506ef-102">EntrySelectedBy Element for CustomEntry for Controls for View (Format)</span></span>

<span data-ttu-id="506ef-103">Definisce i tipi .NET che utilizzano questa definizione di controllo o la condizione che deve esistere affinché questa definizione venga utilizzata.</span><span class="sxs-lookup"><span data-stu-id="506ef-103">Defines the .NET types that use this control definition or the condition that must exist for this definition to be used.</span></span> <span data-ttu-id="506ef-104">Questo elemento viene utilizzato per la definizione di controlli che possono essere utilizzati da una visualizzazione.</span><span class="sxs-lookup"><span data-stu-id="506ef-104">This element is used when defining controls that can be used by a view.</span></span>

<span data-ttu-id="506ef-105">Elemento di configurazione (Format) elemento ViewDefinitions (Format) elemento di visualizzazione (Format) controlli elemento (Format) elemento di controllo per i controlli per la visualizzazione (formato) elemento CustomControl per il controllo per i controlli per la visualizzazione (formato) elemento CustomEntries per CustomControl per i controlli per la visualizzazione (formato) elemento CustomEntry per CustomEntries per i controlli per la visualizzazione (formato) EntrySelectedBy elemento per CustomEntry per i controlli per la visualizzazione (formato)</span><span class="sxs-lookup"><span data-stu-id="506ef-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) Controls Element (Format) Control Element for Controls for View (Format) CustomControl Element for Control for Controls for View (Format) CustomEntries Element for CustomControl for Controls for View (Format) CustomEntry Element for CustomEntries for Controls for View (Format) EntrySelectedBy Element for CustomEntry for Controls for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="506ef-106">Sintassi</span><span class="sxs-lookup"><span data-stu-id="506ef-106">Syntax</span></span>

```xml
<EntrySelectedBy>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>NameofSelectionSet</SelectionSetName>
  <SelectionCondition>...</SelectionCondition>
</EntrySelectedBy>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="506ef-107">Attributi ed elementi</span><span class="sxs-lookup"><span data-stu-id="506ef-107">Attributes and Elements</span></span>

<span data-ttu-id="506ef-108">Nelle sezioni seguenti vengono descritti gli attributi, gli elementi figlio e l'elemento padre dell'elemento `EntrySelectedBy`.</span><span class="sxs-lookup"><span data-stu-id="506ef-108">The following sections describe attributes, child elements, and parent element of the `EntrySelectedBy` element.</span></span> <span data-ttu-id="506ef-109">Per una definizione è necessario specificare almeno un tipo, un set di selezione o una condizione di selezione.</span><span class="sxs-lookup"><span data-stu-id="506ef-109">You must specify at least one type, selection set, or selection condition for a definition.</span></span> <span data-ttu-id="506ef-110">Non esiste un limite massimo per il numero di elementi figlio che è possibile usare.</span><span class="sxs-lookup"><span data-stu-id="506ef-110">There is no maximum limit to the number of child elements that you can use.</span></span>

### <a name="attributes"></a><span data-ttu-id="506ef-111">Attributi</span><span class="sxs-lookup"><span data-stu-id="506ef-111">Attributes</span></span>

<span data-ttu-id="506ef-112">Nessuna.</span><span class="sxs-lookup"><span data-stu-id="506ef-112">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="506ef-113">Elementi figlio</span><span class="sxs-lookup"><span data-stu-id="506ef-113">Child Elements</span></span>

|<span data-ttu-id="506ef-114">Elemento</span><span class="sxs-lookup"><span data-stu-id="506ef-114">Element</span></span>|<span data-ttu-id="506ef-115">Description</span><span class="sxs-lookup"><span data-stu-id="506ef-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="506ef-116">Elemento SelectionCondition per EntrySelectedBy per i controlli per la visualizzazione (Format)</span><span class="sxs-lookup"><span data-stu-id="506ef-116">SelectionCondition Element for EntrySelectedBy for Controls for View (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-controls-for-view-format.md)|<span data-ttu-id="506ef-117">Elemento facoltativo.</span><span class="sxs-lookup"><span data-stu-id="506ef-117">Optional element.</span></span><br /><br /> <span data-ttu-id="506ef-118">Definisce la condizione che deve esistere affinché questa definizione venga utilizzata.</span><span class="sxs-lookup"><span data-stu-id="506ef-118">Defines the condition that must exist for this definition to be used.</span></span>|
|[<span data-ttu-id="506ef-119">Elemento SelectionSetName per EntrySelectedBy per i controlli per la visualizzazione (Format)</span><span class="sxs-lookup"><span data-stu-id="506ef-119">SelectionSetName Element for EntrySelectedBy for Controls for View (Format)</span></span>](./selectionsetname-element-for-entryselectedby-for-controls-for-view-format.md)|<span data-ttu-id="506ef-120">Elemento facoltativo.</span><span class="sxs-lookup"><span data-stu-id="506ef-120">Optional element.</span></span><br /><br /> <span data-ttu-id="506ef-121">Specifica un set di tipi .NET che utilizzano questa definizione del controllo.</span><span class="sxs-lookup"><span data-stu-id="506ef-121">Specifies a set of .NET types that use this definition of the control.</span></span>|
|[<span data-ttu-id="506ef-122">Elemento TypeName per EntrySelectedBy per i controlli per la visualizzazione (Format)</span><span class="sxs-lookup"><span data-stu-id="506ef-122">TypeName Element for EntrySelectedBy for Controls for View (Format)</span></span>](./typename-element-for-entryselectedby-for-controls-for-view-format.md)|<span data-ttu-id="506ef-123">Elemento facoltativo.</span><span class="sxs-lookup"><span data-stu-id="506ef-123">Optional element.</span></span><br /><br /> <span data-ttu-id="506ef-124">Specifica un tipo .NET che usa questa definizione del controllo.</span><span class="sxs-lookup"><span data-stu-id="506ef-124">Specifies a .NET type that uses this definition of the control.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="506ef-125">Elementi padre</span><span class="sxs-lookup"><span data-stu-id="506ef-125">Parent Elements</span></span>

|<span data-ttu-id="506ef-126">Elemento</span><span class="sxs-lookup"><span data-stu-id="506ef-126">Element</span></span>|<span data-ttu-id="506ef-127">Description</span><span class="sxs-lookup"><span data-stu-id="506ef-127">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="506ef-128">Elemento CustomEntry per CustomEntries per i controlli per la visualizzazione (Format)</span><span class="sxs-lookup"><span data-stu-id="506ef-128">CustomEntry Element for CustomEntries for Controls for View (Format)</span></span>](./customentry-element-for-customentries-for-controls-for-view-format.md)|<span data-ttu-id="506ef-129">Fornisce una definizione del controllo.</span><span class="sxs-lookup"><span data-stu-id="506ef-129">Provides a definition of the control.</span></span>|

## <a name="remarks"></a><span data-ttu-id="506ef-130">Osservazioni</span><span class="sxs-lookup"><span data-stu-id="506ef-130">Remarks</span></span>

<span data-ttu-id="506ef-131">Le condizioni di selezione vengono usate per definire una condizione che deve esistere per la definizione da usare, ad esempio quando un oggetto ha una proprietà specifica o quando uno script o un valore di proprietà specifico restituisce `true`.</span><span class="sxs-lookup"><span data-stu-id="506ef-131">Selection conditions are used to define a condition that must exist for the definition to be used, such as when an object has a specific property or when a specific property value or script evaluates to `true`.</span></span> <span data-ttu-id="506ef-132">Per ulteriori informazioni sulle condizioni di selezione, vedere [definizione di condizioni per l'utilizzo di una voce o di un elemento della visualizzazione](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="506ef-132">For more information about selection conditions, see [Defining Conditions for when a View Entry or Item is Used](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="506ef-133">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="506ef-133">See Also</span></span>

[<span data-ttu-id="506ef-134">Elemento CustomEntry per CustomEntries per i controlli per la visualizzazione (Format)</span><span class="sxs-lookup"><span data-stu-id="506ef-134">CustomEntry Element for CustomEntries for Controls for View (Format)</span></span>](./customentry-element-for-customentries-for-controls-for-view-format.md)

[<span data-ttu-id="506ef-135">Scrittura di un file di formattazione di PowerShell</span><span class="sxs-lookup"><span data-stu-id="506ef-135">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
