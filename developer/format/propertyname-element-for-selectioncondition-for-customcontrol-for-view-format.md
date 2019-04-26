---
title: Elemento PropertyName per SelectionCondition per CustomControl per visualizzazione (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: fc48a417-2083-46d4-ac38-16c12e65b6b9
caps.latest.revision: 7
ms.openlocfilehash: e08037d5d051d3be51e90193c7e87cc2e738f78a
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62064697"
---
# <a name="propertyname-element-for-selectioncondition-for-customcontrol-for-view-format"></a><span data-ttu-id="0a1cf-102">Elemento PropertyName per SelectionCondition per CustomControl per View (formato)</span><span class="sxs-lookup"><span data-stu-id="0a1cf-102">PropertyName Element for SelectionCondition for CustomControl for View (Format)</span></span>

<span data-ttu-id="0a1cf-103">Specifica la proprietà .NET che attiva la condizione.</span><span class="sxs-lookup"><span data-stu-id="0a1cf-103">Specifies the .NET property that triggers the condition.</span></span> <span data-ttu-id="0a1cf-104">Quando questa proprietà è presente o quando viene restituito `true`, viene soddisfatta la condizione e viene utilizzata la definizione.</span><span class="sxs-lookup"><span data-stu-id="0a1cf-104">When this property is present or when it evaluates to `true`, the condition is met, and the definition is used.</span></span> <span data-ttu-id="0a1cf-105">Questo elemento viene usato quando si definisce una vista di controllo personalizzato.</span><span class="sxs-lookup"><span data-stu-id="0a1cf-105">This element is used when defining a custom control view.</span></span>

<span data-ttu-id="0a1cf-106">Elemento di CustomControl elemento (formato) per la visualizzazione elemento ViewDefinitions (formato) configurazione elemento (formato) elemento di visualizzazione (formato) CustomEntries per CustomControl elemento di visualizzazione (formato) CustomEntry per CustomEntries per CustomControl per visualizzazione ( Elemento CustomItem Format) per CustomEntry per CustomControl elemento di visualizzazione (formato) EntrySelectedBy per CustomEntry per CustomControl elemento di visualizzazione (formato) SelectionCondition per EntrySelectedBy per CustomControl per PropertyName visualizzazione (formato) Elemento per SelectionCondition per CustomControl per visualizzazione (formato)</span><span class="sxs-lookup"><span data-stu-id="0a1cf-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) CustomControl Element for View (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for CustomControl for View (Format) CustomItem Element for CustomEntry for CustomControl for View (Format) EntrySelectedBy Element for CustomEntry for CustomControl for View (Format) SelectionCondition Element for EntrySelectedBy for CustomControl for View (Format) PropertyName Element for SelectionCondition for CustomControl for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="0a1cf-107">Sintassi</span><span class="sxs-lookup"><span data-stu-id="0a1cf-107">Syntax</span></span>

```xml
<PropertyName>.NetTypeProperty</PropertyName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="0a1cf-108">Elementi e attributi</span><span class="sxs-lookup"><span data-stu-id="0a1cf-108">Attributes and Elements</span></span>

<span data-ttu-id="0a1cf-109">Le sezioni seguenti descrivono gli attributi e gli elementi figlio dell'elemento padre del `PropertyName` elemento.</span><span class="sxs-lookup"><span data-stu-id="0a1cf-109">The following sections describe attributes, child elements, and the parent element of the `PropertyName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="0a1cf-110">Attributes</span><span class="sxs-lookup"><span data-stu-id="0a1cf-110">Attributes</span></span>

<span data-ttu-id="0a1cf-111">Nessuna.</span><span class="sxs-lookup"><span data-stu-id="0a1cf-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="0a1cf-112">Elementi figlio</span><span class="sxs-lookup"><span data-stu-id="0a1cf-112">Child Elements</span></span>

<span data-ttu-id="0a1cf-113">Nessuna.</span><span class="sxs-lookup"><span data-stu-id="0a1cf-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="0a1cf-114">Elementi padre</span><span class="sxs-lookup"><span data-stu-id="0a1cf-114">Parent Elements</span></span>

|<span data-ttu-id="0a1cf-115">Elemento</span><span class="sxs-lookup"><span data-stu-id="0a1cf-115">Element</span></span>|<span data-ttu-id="0a1cf-116">Description</span><span class="sxs-lookup"><span data-stu-id="0a1cf-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="0a1cf-117">Elemento SelectionCondition per EntrySelectedBy per CustomControl per visualizzazione (formato)</span><span class="sxs-lookup"><span data-stu-id="0a1cf-117">SelectionCondition Element for EntrySelectedBy for CustomControl for View (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-customcontrol-format.md)|<span data-ttu-id="0a1cf-118">Definisce una condizione che deve essere presente per la definizione di controllo da utilizzare.</span><span class="sxs-lookup"><span data-stu-id="0a1cf-118">Defines a condition that must exist for the control definition to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="0a1cf-119">Valore di testo</span><span class="sxs-lookup"><span data-stu-id="0a1cf-119">Text Value</span></span>

<span data-ttu-id="0a1cf-120">Specificare il nome della proprietà .NET.</span><span class="sxs-lookup"><span data-stu-id="0a1cf-120">Specify the .NET property name.</span></span>

## <a name="remarks"></a><span data-ttu-id="0a1cf-121">Osservazioni</span><span class="sxs-lookup"><span data-stu-id="0a1cf-121">Remarks</span></span>

<span data-ttu-id="0a1cf-122">La condizione di selezione è necessario specificare un nome di una proprietà minimi o uno script, ma non è possibile specificare entrambi.</span><span class="sxs-lookup"><span data-stu-id="0a1cf-122">The selection condition must specify a least one property name or a script, but cannot specify both.</span></span> <span data-ttu-id="0a1cf-123">Per altre informazioni sull'utilizzo di condizioni di selezione, vedere [che definisce le condizioni per la visualizzazione dei dati](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="0a1cf-123">For more information about how selection conditions can be used, see [Defining Conditions for Displaying Data](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="0a1cf-124">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="0a1cf-124">See Also</span></span>

[<span data-ttu-id="0a1cf-125">Elemento SelectionCondition per EntrySelectedBy per CustomControl per visualizzazione (formato)</span><span class="sxs-lookup"><span data-stu-id="0a1cf-125">SelectionCondition Element for EntrySelectedBy for CustomControl for View (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-customcontrol-format.md)

[<span data-ttu-id="0a1cf-126">La scrittura di un File di formattazione di PowerShell</span><span class="sxs-lookup"><span data-stu-id="0a1cf-126">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
