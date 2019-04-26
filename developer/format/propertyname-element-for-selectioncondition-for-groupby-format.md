---
title: Elemento PropertyName per SelectionCondition per GroupBy (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d1707317-6c26-4866-bcc1-8924103c9014
caps.latest.revision: 6
ms.openlocfilehash: 7241ea0ea364befa7ad4ab0af4c4209be72214a7
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62064816"
---
# <a name="propertyname-element-for-selectioncondition-for-groupby-format"></a><span data-ttu-id="7f698-102">Elemento PropertyName per SelectionCondition per GroupBy (formato)</span><span class="sxs-lookup"><span data-stu-id="7f698-102">PropertyName Element for SelectionCondition for GroupBy (Format)</span></span>

<span data-ttu-id="7f698-103">Specifica la proprietà .NET che attiva la condizione.</span><span class="sxs-lookup"><span data-stu-id="7f698-103">Specifies the .NET property that triggers the condition.</span></span> <span data-ttu-id="7f698-104">Quando questa proprietà è presente o quando viene restituito `true`, viene soddisfatta la condizione e viene utilizzata la definizione.</span><span class="sxs-lookup"><span data-stu-id="7f698-104">When this property is present or when it evaluates to `true`, the condition is met, and the definition is used.</span></span> <span data-ttu-id="7f698-105">Questo elemento viene usato quando si definisce come viene visualizzato un nuovo gruppo di oggetti.</span><span class="sxs-lookup"><span data-stu-id="7f698-105">This element is used when defining how a new group of objects is displayed.</span></span>

<span data-ttu-id="7f698-106">Elemento di GroupBy elemento (formato) per la visualizzazione elemento ViewDefinitions (formato) configurazione elemento (formato) per visualizzazione (formato) CustomControl elemento per elemento CustomEntries GroupBy (formato) per CustomControl per elemento CustomEntry GroupBy (formato) CustomControl per elemento EntrySelectedBy GroupBy (formato) per CustomEntry per elemento SelectionCondition GroupBy (formato) per EntrySelectedBy per elemento PropertyName GroupBy (formato) per SelectionCondition per GroupBy (formato)</span><span class="sxs-lookup"><span data-stu-id="7f698-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) GroupBy Element for View (Format) CustomControl Element for GroupBy (Format) CustomEntries Element for CustomControl for GroupBy (Format) CustomEntry Element for CustomControl for GroupBy (Format) EntrySelectedBy Element for CustomEntry for GroupBy (Format) SelectionCondition Element for EntrySelectedBy for GroupBy (Format) PropertyName Element for SelectionCondition for GroupBy (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="7f698-107">Sintassi</span><span class="sxs-lookup"><span data-stu-id="7f698-107">Syntax</span></span>

```xml
<PropertyName>.NetTypeProperty</PropertyName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="7f698-108">Elementi e attributi</span><span class="sxs-lookup"><span data-stu-id="7f698-108">Attributes and Elements</span></span>

<span data-ttu-id="7f698-109">Le sezioni seguenti descrivono gli attributi e gli elementi figlio dell'elemento padre del `PropertyName` elemento.</span><span class="sxs-lookup"><span data-stu-id="7f698-109">The following sections describe attributes, child elements, and the parent element of the `PropertyName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="7f698-110">Attributes</span><span class="sxs-lookup"><span data-stu-id="7f698-110">Attributes</span></span>

<span data-ttu-id="7f698-111">Nessuna.</span><span class="sxs-lookup"><span data-stu-id="7f698-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="7f698-112">Elementi figlio</span><span class="sxs-lookup"><span data-stu-id="7f698-112">Child Elements</span></span>

<span data-ttu-id="7f698-113">Nessuna.</span><span class="sxs-lookup"><span data-stu-id="7f698-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="7f698-114">Elementi padre</span><span class="sxs-lookup"><span data-stu-id="7f698-114">Parent Elements</span></span>

|<span data-ttu-id="7f698-115">Elemento</span><span class="sxs-lookup"><span data-stu-id="7f698-115">Element</span></span>|<span data-ttu-id="7f698-116">Description</span><span class="sxs-lookup"><span data-stu-id="7f698-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="7f698-117">Elemento SelectionCondition per EntrySelectedBy per GroupBy (formato)</span><span class="sxs-lookup"><span data-stu-id="7f698-117">SelectionCondition Element for EntrySelectedBy for GroupBy (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-groupby-format.md)|<span data-ttu-id="7f698-118">Definisce una condizione che deve essere presente per la definizione di controllo da utilizzare.</span><span class="sxs-lookup"><span data-stu-id="7f698-118">Defines a condition that must exist for the control definition to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="7f698-119">Valore di testo</span><span class="sxs-lookup"><span data-stu-id="7f698-119">Text Value</span></span>

<span data-ttu-id="7f698-120">Specificare il nome della proprietà .NET.</span><span class="sxs-lookup"><span data-stu-id="7f698-120">Specify the .NET property name.</span></span>

## <a name="remarks"></a><span data-ttu-id="7f698-121">Osservazioni</span><span class="sxs-lookup"><span data-stu-id="7f698-121">Remarks</span></span>

<span data-ttu-id="7f698-122">La condizione di selezione è necessario specificare un nome di una proprietà minimi o uno script, ma non è possibile specificare entrambi.</span><span class="sxs-lookup"><span data-stu-id="7f698-122">The selection condition must specify a least one property name or a script, but cannot specify both.</span></span> <span data-ttu-id="7f698-123">Per altre informazioni sull'utilizzo di condizioni di selezione, vedere [che definisce le condizioni per la visualizzazione dei dati](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="7f698-123">For more information about how selection conditions can be used, see [Defining Conditions for Displaying Data](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="7f698-124">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="7f698-124">See Also</span></span>

[<span data-ttu-id="7f698-125">Elemento SelectionCondition per EntrySelectedBy per GroupBy (formato)</span><span class="sxs-lookup"><span data-stu-id="7f698-125">SelectionCondition Element for EntrySelectedBy for GroupBy (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-groupby-format.md)

[<span data-ttu-id="7f698-126">La scrittura di un File di formattazione di PowerShell</span><span class="sxs-lookup"><span data-stu-id="7f698-126">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
