---
title: Elemento EntrySelectedBy per CustomEntry per i controlli per la visualizzazione (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: b3d80a7d-3797-4c46-ae74-ae5cda79b24f
caps.latest.revision: 8
ms.openlocfilehash: efb20c3f2077547e6eb3cb28240512b444f9c481
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/03/2019
ms.locfileid: "56859537"
---
# <a name="entryselectedby-element-for-customentry-for-controls-for-view-format"></a><span data-ttu-id="cc931-102">Elemento EntrySelectedBy per CustomEntry per Controls per View (formato)</span><span class="sxs-lookup"><span data-stu-id="cc931-102">EntrySelectedBy Element for CustomEntry for Controls for View (Format)</span></span>

<span data-ttu-id="cc931-103">Definisce i tipi .NET che usano questa definizione di controllo o la condizione che deve essere presente per questa definizione da usare.</span><span class="sxs-lookup"><span data-stu-id="cc931-103">Defines the .NET types that use this control definition or the condition that must exist for this definition to be used.</span></span> <span data-ttu-id="cc931-104">Questo elemento viene usato quando si definiscono i controlli che possono essere usati da una vista.</span><span class="sxs-lookup"><span data-stu-id="cc931-104">This element is used when defining controls that can be used by a view.</span></span>

<span data-ttu-id="cc931-105">Elemento (formato) elemento ViewDefinitions (formato) visualizzazione elemento (formato) i controlli elemento (formato) controllo elemento di configurazione per i controlli elemento di visualizzazione (formato) CustomControl per il controllo per i controlli elemento di visualizzazione (formato) CustomEntries per CustomControl per i controlli elemento di visualizzazione (formato) CustomEntry per CustomEntries per i controlli elemento di visualizzazione (formato) EntrySelectedBy per CustomEntry per i controlli per la visualizzazione (formato)</span><span class="sxs-lookup"><span data-stu-id="cc931-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) Controls Element (Format) Control Element for Controls for View (Format) CustomControl Element for Control for Controls for View (Format) CustomEntries Element for CustomControl for Controls for View (Format) CustomEntry Element for CustomEntries for Controls for View (Format) EntrySelectedBy Element for CustomEntry for Controls for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="cc931-106">Sintassi</span><span class="sxs-lookup"><span data-stu-id="cc931-106">Syntax</span></span>

```xml
<EntrySelectedBy>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>NameofSelectionSet</SelectionSetName>
  <SelectionCondition>...</SelectionCondition>
</EntrySelectedBy>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="cc931-107">Attributi ed elementi</span><span class="sxs-lookup"><span data-stu-id="cc931-107">Attributes and Elements</span></span>

<span data-ttu-id="cc931-108">Le sezioni seguenti descrivono l'elemento padre di attributi e gli elementi figlio di `EntrySelectedBy` elemento.</span><span class="sxs-lookup"><span data-stu-id="cc931-108">The following sections describe attributes, child elements, and parent element of the `EntrySelectedBy` element.</span></span> <span data-ttu-id="cc931-109">È necessario specificare almeno un tipo, set di selezione o condizione di selezione per una definizione.</span><span class="sxs-lookup"><span data-stu-id="cc931-109">You must specify at least one type, selection set, or selection condition for a definition.</span></span> <span data-ttu-id="cc931-110">Non è definito alcun limite massimo al numero di elementi figlio che è possibile usare.</span><span class="sxs-lookup"><span data-stu-id="cc931-110">There is no maximum limit to the number of child elements that you can use.</span></span>

### <a name="attributes"></a><span data-ttu-id="cc931-111">Attributes</span><span class="sxs-lookup"><span data-stu-id="cc931-111">Attributes</span></span>

<span data-ttu-id="cc931-112">Nessuna.</span><span class="sxs-lookup"><span data-stu-id="cc931-112">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="cc931-113">Elementi figlio</span><span class="sxs-lookup"><span data-stu-id="cc931-113">Child Elements</span></span>

|<span data-ttu-id="cc931-114">Elemento</span><span class="sxs-lookup"><span data-stu-id="cc931-114">Element</span></span>|<span data-ttu-id="cc931-115">Description</span><span class="sxs-lookup"><span data-stu-id="cc931-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="cc931-116">Elemento SelectionCondition per EntrySelectedBy per i controlli per la visualizzazione (formato)</span><span class="sxs-lookup"><span data-stu-id="cc931-116">SelectionCondition Element for EntrySelectedBy for Controls for View (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-controls-for-view-format.md)|<span data-ttu-id="cc931-117">Elemento facoltativo.</span><span class="sxs-lookup"><span data-stu-id="cc931-117">Optional element.</span></span><br /><br /> <span data-ttu-id="cc931-118">Definisce la condizione che deve essere presente per questa definizione da usare.</span><span class="sxs-lookup"><span data-stu-id="cc931-118">Defines the condition that must exist for this definition to be used.</span></span>|
|[<span data-ttu-id="cc931-119">Elemento SelectionSetName per EntrySelectedBy per i controlli per la visualizzazione (formato)</span><span class="sxs-lookup"><span data-stu-id="cc931-119">SelectionSetName Element for EntrySelectedBy for Controls for View (Format)</span></span>](./selectionsetname-element-for-entryselectedby-for-controls-for-view-format.md)|<span data-ttu-id="cc931-120">Elemento facoltativo.</span><span class="sxs-lookup"><span data-stu-id="cc931-120">Optional element.</span></span><br /><br /> <span data-ttu-id="cc931-121">Specifica un set di tipi .NET che usano questa definizione del controllo.</span><span class="sxs-lookup"><span data-stu-id="cc931-121">Specifies a set of .NET types that use this definition of the control.</span></span>|
|[<span data-ttu-id="cc931-122">Elemento TypeName per EntrySelectedBy per i controlli per la visualizzazione (formato)</span><span class="sxs-lookup"><span data-stu-id="cc931-122">TypeName Element for EntrySelectedBy for Controls for View (Format)</span></span>](./typename-element-for-entryselectedby-for-controls-for-view-format.md)|<span data-ttu-id="cc931-123">Elemento facoltativo.</span><span class="sxs-lookup"><span data-stu-id="cc931-123">Optional element.</span></span><br /><br /> <span data-ttu-id="cc931-124">Specifica un tipo .NET che usa questa definizione del controllo.</span><span class="sxs-lookup"><span data-stu-id="cc931-124">Specifies a .NET type that uses this definition of the control.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="cc931-125">Elementi padre</span><span class="sxs-lookup"><span data-stu-id="cc931-125">Parent Elements</span></span>

|<span data-ttu-id="cc931-126">Elemento</span><span class="sxs-lookup"><span data-stu-id="cc931-126">Element</span></span>|<span data-ttu-id="cc931-127">Description</span><span class="sxs-lookup"><span data-stu-id="cc931-127">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="cc931-128">Elemento CustomEntry per CustomEntries per i controlli per la visualizzazione (formato)</span><span class="sxs-lookup"><span data-stu-id="cc931-128">CustomEntry Element for CustomEntries for Controls for View (Format)</span></span>](./customentry-element-for-customentries-for-controls-for-view-format.md)|<span data-ttu-id="cc931-129">Fornisce una definizione del controllo.</span><span class="sxs-lookup"><span data-stu-id="cc931-129">Provides a definition of the control.</span></span>|

## <a name="remarks"></a><span data-ttu-id="cc931-130">Osservazioni</span><span class="sxs-lookup"><span data-stu-id="cc931-130">Remarks</span></span>

<span data-ttu-id="cc931-131">Condizioni di selezione vengono usate per definire una condizione che deve essere presente per la definizione da usare, ad esempio quando un oggetto dispone di una proprietà specifica o quando un valore di proprietà specifica o lo script restituisce `true`.</span><span class="sxs-lookup"><span data-stu-id="cc931-131">Selection conditions are used to define a condition that must exist for the definition to be used, such as when an object has a specific property or when a specific property value or script evaluates to `true`.</span></span> <span data-ttu-id="cc931-132">Per altre informazioni sulle condizioni di selezione, vedere [definizione di condizioni per quando una voce di visualizzazione o viene usato l'elemento](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="cc931-132">For more information about selection conditions, see [Defining Conditions for when a View Entry or Item is Used](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="cc931-133">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="cc931-133">See Also</span></span>

[<span data-ttu-id="cc931-134">Elemento CustomEntry per CustomEntries per i controlli per la visualizzazione (formato)</span><span class="sxs-lookup"><span data-stu-id="cc931-134">CustomEntry Element for CustomEntries for Controls for View (Format)</span></span>](./customentry-element-for-customentries-for-controls-for-view-format.md)

[<span data-ttu-id="cc931-135">La scrittura di un File di formattazione di PowerShell</span><span class="sxs-lookup"><span data-stu-id="cc931-135">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
