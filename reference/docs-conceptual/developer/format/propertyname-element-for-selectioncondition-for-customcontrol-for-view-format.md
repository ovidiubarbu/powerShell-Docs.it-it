---
title: Elemento PropertyName per SelectionCondition per CustomControl per View (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: fc48a417-2083-46d4-ac38-16c12e65b6b9
caps.latest.revision: 7
ms.openlocfilehash: e08037d5d051d3be51e90193c7e87cc2e738f78a
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/15/2019
ms.locfileid: "72362350"
---
# <a name="propertyname-element-for-selectioncondition-for-customcontrol-for-view-format"></a><span data-ttu-id="e1cd0-102">Elemento PropertyName per SelectionCondition per CustomControl per View (formato)</span><span class="sxs-lookup"><span data-stu-id="e1cd0-102">PropertyName Element for SelectionCondition for CustomControl for View (Format)</span></span>

<span data-ttu-id="e1cd0-103">Specifica la proprietà .NET che attiva la condizione.</span><span class="sxs-lookup"><span data-stu-id="e1cd0-103">Specifies the .NET property that triggers the condition.</span></span> <span data-ttu-id="e1cd0-104">Quando questa proprietà è presente o quando restituisce `true`, la condizione viene soddisfatta e viene usata la definizione.</span><span class="sxs-lookup"><span data-stu-id="e1cd0-104">When this property is present or when it evaluates to `true`, the condition is met, and the definition is used.</span></span> <span data-ttu-id="e1cd0-105">Questo elemento viene utilizzato quando si definisce una visualizzazione controlli personalizzata.</span><span class="sxs-lookup"><span data-stu-id="e1cd0-105">This element is used when defining a custom control view.</span></span>

<span data-ttu-id="e1cd0-106">Elemento Configuration (Format) elemento ViewDefinitions (Format) elemento View (Format) elemento CustomControl per View (Format) elemento CustomEntries per CustomControl per la visualizzazione (Format) CustomEntry elemento per CustomEntries per CustomControl per la visualizzazione ( Format) elemento CustomItem per CustomEntry per CustomControl per la vista (Format) elemento EntrySelectedBy per CustomEntry per CustomControl per SelectionCondition per la visualizzazione (formato) EntrySelectedBy elemento per CustomControl per per la visualizzazione (Format) PropertyName Elemento per SelectionCondition per CustomControl per View (Format)</span><span class="sxs-lookup"><span data-stu-id="e1cd0-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) CustomControl Element for View (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for CustomControl for View (Format) CustomItem Element for CustomEntry for CustomControl for View (Format) EntrySelectedBy Element for CustomEntry for CustomControl for View (Format) SelectionCondition Element for EntrySelectedBy for CustomControl for View (Format) PropertyName Element for SelectionCondition for CustomControl for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="e1cd0-107">Sintassi</span><span class="sxs-lookup"><span data-stu-id="e1cd0-107">Syntax</span></span>

```xml
<PropertyName>.NetTypeProperty</PropertyName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="e1cd0-108">Attributi ed elementi</span><span class="sxs-lookup"><span data-stu-id="e1cd0-108">Attributes and Elements</span></span>

<span data-ttu-id="e1cd0-109">Nelle sezioni seguenti vengono descritti gli attributi, gli elementi figlio e l'elemento padre dell'elemento `PropertyName`.</span><span class="sxs-lookup"><span data-stu-id="e1cd0-109">The following sections describe attributes, child elements, and the parent element of the `PropertyName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="e1cd0-110">Attributi</span><span class="sxs-lookup"><span data-stu-id="e1cd0-110">Attributes</span></span>

<span data-ttu-id="e1cd0-111">Nessuna.</span><span class="sxs-lookup"><span data-stu-id="e1cd0-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="e1cd0-112">Elementi figlio</span><span class="sxs-lookup"><span data-stu-id="e1cd0-112">Child Elements</span></span>

<span data-ttu-id="e1cd0-113">Nessuna.</span><span class="sxs-lookup"><span data-stu-id="e1cd0-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="e1cd0-114">Elementi padre</span><span class="sxs-lookup"><span data-stu-id="e1cd0-114">Parent Elements</span></span>

|<span data-ttu-id="e1cd0-115">Elemento</span><span class="sxs-lookup"><span data-stu-id="e1cd0-115">Element</span></span>|<span data-ttu-id="e1cd0-116">Description</span><span class="sxs-lookup"><span data-stu-id="e1cd0-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="e1cd0-117">Elemento SelectionCondition per EntrySelectedBy per CustomControl per View (Format)</span><span class="sxs-lookup"><span data-stu-id="e1cd0-117">SelectionCondition Element for EntrySelectedBy for CustomControl for View (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-customcontrol-format.md)|<span data-ttu-id="e1cd0-118">Definisce una condizione che deve esistere per la definizione del controllo da utilizzare.</span><span class="sxs-lookup"><span data-stu-id="e1cd0-118">Defines a condition that must exist for the control definition to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="e1cd0-119">Valore di testo</span><span class="sxs-lookup"><span data-stu-id="e1cd0-119">Text Value</span></span>

<span data-ttu-id="e1cd0-120">Specificare il nome della proprietà .NET.</span><span class="sxs-lookup"><span data-stu-id="e1cd0-120">Specify the .NET property name.</span></span>

## <a name="remarks"></a><span data-ttu-id="e1cd0-121">Osservazioni</span><span class="sxs-lookup"><span data-stu-id="e1cd0-121">Remarks</span></span>

<span data-ttu-id="e1cd0-122">La condizione di selezione deve specificare almeno un nome di proprietà o uno script, ma non è possibile specificarli entrambi.</span><span class="sxs-lookup"><span data-stu-id="e1cd0-122">The selection condition must specify a least one property name or a script, but cannot specify both.</span></span> <span data-ttu-id="e1cd0-123">Per ulteriori informazioni sul modo in cui è possibile utilizzare le condizioni di selezione, vedere [definizione delle condizioni per la visualizzazione dei dati](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="e1cd0-123">For more information about how selection conditions can be used, see [Defining Conditions for Displaying Data](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="e1cd0-124">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="e1cd0-124">See Also</span></span>

[<span data-ttu-id="e1cd0-125">Elemento SelectionCondition per EntrySelectedBy per CustomControl per View (Format)</span><span class="sxs-lookup"><span data-stu-id="e1cd0-125">SelectionCondition Element for EntrySelectedBy for CustomControl for View (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-customcontrol-format.md)

[<span data-ttu-id="e1cd0-126">Scrittura di un file di formattazione di PowerShell</span><span class="sxs-lookup"><span data-stu-id="e1cd0-126">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
