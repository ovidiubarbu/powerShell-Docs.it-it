---
title: Elemento SelectionSetName per SelectionCondition per CustomControl per visualizzazione (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: a52b05a9-762e-4f1c-ad57-9d1710149722
caps.latest.revision: 10
ms.openlocfilehash: 25d46665ca5df3ddf49af5718d513b84c77988c8
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62075580"
---
# <a name="selectionsetname-element-for-selectioncondition-for-customcontrol-for-view-format"></a><span data-ttu-id="cb58e-102">Elemento SelectionSetName per SelectionCondition per CustomControl per View (formato)</span><span class="sxs-lookup"><span data-stu-id="cb58e-102">SelectionSetName Element for SelectionCondition for CustomControl for View (Format)</span></span>

<span data-ttu-id="cb58e-103">Specifica il set di tipi .NET che attivano la condizione.</span><span class="sxs-lookup"><span data-stu-id="cb58e-103">Specifies the set of .NET types that trigger the condition.</span></span> <span data-ttu-id="cb58e-104">Quando uno dei tipi in questo set è presentano, viene soddisfatta la condizione e l'oggetto viene visualizzato l'utilizzo di questo controllo.</span><span class="sxs-lookup"><span data-stu-id="cb58e-104">When any of the types in this set are present, the condition is met and the object is displayed using this control.</span></span> <span data-ttu-id="cb58e-105">Questo elemento viene usato quando si definisce una vista di controllo personalizzato.</span><span class="sxs-lookup"><span data-stu-id="cb58e-105">This element is used when defining a custom control view.</span></span>

<span data-ttu-id="cb58e-106">Elemento (formato) elemento ViewDefinitions (formato) visualizzazione elemento (formato) elemento CustomControl (formato) CustomEntries elemento di configurazione per CustomControl elemento di visualizzazione (formato) CustomEntry per CustomEntries per EntrySelectedBy visualizzazione (formato) Elemento per CustomEntry per visualizzazione (formato)</span><span class="sxs-lookup"><span data-stu-id="cb58e-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) CustomControl Element (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for View (Format) EntrySelectedBy Element for CustomEntry for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="cb58e-107">Sintassi</span><span class="sxs-lookup"><span data-stu-id="cb58e-107">Syntax</span></span>

```xml
<SelectionSetName>NameofSelectionSet</SelectionSetName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="cb58e-108">Elementi e attributi</span><span class="sxs-lookup"><span data-stu-id="cb58e-108">Attributes and Elements</span></span>

<span data-ttu-id="cb58e-109">Le sezioni seguenti descrivono gli attributi e gli elementi figlio dell'elemento padre del `SelectionSetName` elemento.</span><span class="sxs-lookup"><span data-stu-id="cb58e-109">The following sections describe attributes, child elements, and the parent element of the `SelectionSetName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="cb58e-110">Attributes</span><span class="sxs-lookup"><span data-stu-id="cb58e-110">Attributes</span></span>

<span data-ttu-id="cb58e-111">Nessuna.</span><span class="sxs-lookup"><span data-stu-id="cb58e-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="cb58e-112">Elementi figlio</span><span class="sxs-lookup"><span data-stu-id="cb58e-112">Child Elements</span></span>

<span data-ttu-id="cb58e-113">Nessuna.</span><span class="sxs-lookup"><span data-stu-id="cb58e-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="cb58e-114">Elementi padre</span><span class="sxs-lookup"><span data-stu-id="cb58e-114">Parent Elements</span></span>

|<span data-ttu-id="cb58e-115">Elemento</span><span class="sxs-lookup"><span data-stu-id="cb58e-115">Element</span></span>|<span data-ttu-id="cb58e-116">Description</span><span class="sxs-lookup"><span data-stu-id="cb58e-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="cb58e-117">Elemento SelectionCondition per EntrySelectedBy per CustomControl per visualizzazione (formato)</span><span class="sxs-lookup"><span data-stu-id="cb58e-117">SelectionCondition Element for EntrySelectedBy for CustomControl for View (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-customcontrol-format.md)|<span data-ttu-id="cb58e-118">Definisce una condizione che deve essere presente per la definizione di controllo da utilizzare.</span><span class="sxs-lookup"><span data-stu-id="cb58e-118">Defines a condition that must exist for the control definition to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="cb58e-119">Valore di testo</span><span class="sxs-lookup"><span data-stu-id="cb58e-119">Text Value</span></span>

<span data-ttu-id="cb58e-120">Specificare il nome del set di selezione.</span><span class="sxs-lookup"><span data-stu-id="cb58e-120">Specify the name of the selection set.</span></span>

## <a name="remarks"></a><span data-ttu-id="cb58e-121">Osservazioni</span><span class="sxs-lookup"><span data-stu-id="cb58e-121">Remarks</span></span>

<span data-ttu-id="cb58e-122">Set di selezione sono i gruppi di oggetti .NET che possono essere usati da qualsiasi vista che definisce il file di formattazione comuni.</span><span class="sxs-lookup"><span data-stu-id="cb58e-122">Selection sets are common groups of .NET objects that can be used by any view that the formatting file defines.</span></span> <span data-ttu-id="cb58e-123">Per altre informazioni sulla creazione e che fanno riferimento a set di selezione, vedere [definizione imposta di oggetti](./defining-selection-sets.md).</span><span class="sxs-lookup"><span data-stu-id="cb58e-123">For more information about creating and referencing selection sets, see [Defining Sets of Objects](./defining-selection-sets.md).</span></span>

<span data-ttu-id="cb58e-124">La condizione di selezione è possibile specificare un set di selezione o un tipo .NET, ma non è possibile specificare entrambi.</span><span class="sxs-lookup"><span data-stu-id="cb58e-124">The selection condition can specify a selection set or .NET type, but cannot specify both.</span></span> <span data-ttu-id="cb58e-125">Per altre informazioni su come usare le condizioni di selezione, vedere [che definisce le condizioni per quando i dati vengono visualizzati](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="cb58e-125">For more information about how to use selection conditions, see [Defining Conditions for when Data is Displayed](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="cb58e-126">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="cb58e-126">See Also</span></span>

[<span data-ttu-id="cb58e-127">Elemento SelectionCondition per EntrySelectedBy per CustomControl per visualizzazione (formato)</span><span class="sxs-lookup"><span data-stu-id="cb58e-127">SelectionCondition Element for EntrySelectedBy for CustomControl for View (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-customcontrol-format.md)

[<span data-ttu-id="cb58e-128">La definizione delle condizioni per quando i dati vengono visualizzati</span><span class="sxs-lookup"><span data-stu-id="cb58e-128">Defining Conditions for When Data Is Displayed</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="cb58e-129">La definizione di set di selezione</span><span class="sxs-lookup"><span data-stu-id="cb58e-129">Defining Selection Sets</span></span>](./defining-selection-sets.md)

[<span data-ttu-id="cb58e-130">La scrittura di un File di formattazione di PowerShell</span><span class="sxs-lookup"><span data-stu-id="cb58e-130">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
