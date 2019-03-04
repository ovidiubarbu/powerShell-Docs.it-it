---
title: Elemento PropertyName per ItemSelectionCondition per ListControl (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d5e707ae-3c84-4ceb-ba31-56b3ffde6d6c
caps.latest.revision: 7
ms.openlocfilehash: b15e26e18126f69eee7c3a857f9a461d4bdf5848
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/03/2019
ms.locfileid: "56855537"
---
# <a name="propertyname-element-for-itemselectioncondition-for-listcontrol-format"></a><span data-ttu-id="895e6-102">Elemento PropertyName per ItemSelectionCondition per ListControl (formato)</span><span class="sxs-lookup"><span data-stu-id="895e6-102">PropertyName Element for ItemSelectionCondition for ListControl (Format)</span></span>

<span data-ttu-id="895e6-103">Specifica la proprietà .NET che attiva la condizione.</span><span class="sxs-lookup"><span data-stu-id="895e6-103">Specifies the .NET property that triggers the condition.</span></span> <span data-ttu-id="895e6-104">Quando questa proprietà è presente o quando viene restituito `true`, viene soddisfatta la condizione e viene utilizzata la vista.</span><span class="sxs-lookup"><span data-stu-id="895e6-104">When this property is present or when it evaluates to `true`, the condition is met, and the view is used.</span></span> <span data-ttu-id="895e6-105">Questo elemento viene usato quando si definisce una visualizzazione elenco.</span><span class="sxs-lookup"><span data-stu-id="895e6-105">This element is used when defining a list view.</span></span>

<span data-ttu-id="895e6-106">Configurazione elemento (formato) elemento ViewDefinitions (formato) visualizzazione elemento (formato) elemento dell'oggetto ListControl (formato) ListEntries (formato) ListEntry elemento per elemento ListItems dell'oggetto ListControl (formato) per ListEntry per ListItem ListControl (formato) Elemento ListItems per elemento dell'oggetto ListControl (formato) ItemSelectionCondition ListItem per elemento PropertyName ListControls ItemSelectionCondition per ListControl (formato)</span><span class="sxs-lookup"><span data-stu-id="895e6-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) ListControl Element (Format) ListEntries Element (Format) ListEntry Element for ListControl (Format) ListItems Element for ListEntry for ListControl (Format) ListItem Element for ListItems for ListControl (Format) ItemSelectionCondition Element for ListItem for ListControls PropertyName Element for ItemSelectionCondition for ListControl (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="895e6-107">Sintassi</span><span class="sxs-lookup"><span data-stu-id="895e6-107">Syntax</span></span>

```xml
<PropertyName>.NetTypeProperty</PropertyName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="895e6-108">Attributi ed elementi</span><span class="sxs-lookup"><span data-stu-id="895e6-108">Attributes and Elements</span></span>

<span data-ttu-id="895e6-109">Le sezioni seguenti descrivono gli attributi, elementi figlio e gli elementi padre del `PropertyName` elemento.</span><span class="sxs-lookup"><span data-stu-id="895e6-109">The following sections describe attributes, child elements, and the parent elements of the `PropertyName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="895e6-110">Attributes</span><span class="sxs-lookup"><span data-stu-id="895e6-110">Attributes</span></span>

<span data-ttu-id="895e6-111">Nessuna.</span><span class="sxs-lookup"><span data-stu-id="895e6-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="895e6-112">Elementi figlio</span><span class="sxs-lookup"><span data-stu-id="895e6-112">Child Elements</span></span>

<span data-ttu-id="895e6-113">Nessuna.</span><span class="sxs-lookup"><span data-stu-id="895e6-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="895e6-114">Elementi padre</span><span class="sxs-lookup"><span data-stu-id="895e6-114">Parent Elements</span></span>

|<span data-ttu-id="895e6-115">Elemento</span><span class="sxs-lookup"><span data-stu-id="895e6-115">Element</span></span>|<span data-ttu-id="895e6-116">Description</span><span class="sxs-lookup"><span data-stu-id="895e6-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="895e6-117">Elemento ItemSelectionCondition per ListItem per ListControl (formato)</span><span class="sxs-lookup"><span data-stu-id="895e6-117">ItemSelectionCondition Element for ListItem for ListControl (Format)</span></span>](./itemselectioncondition-element-for-listitem-for-listcontrol-format.md)||

## <a name="text-value"></a><span data-ttu-id="895e6-118">Valore di testo</span><span class="sxs-lookup"><span data-stu-id="895e6-118">Text Value</span></span>

<span data-ttu-id="895e6-119">Specificare il nome della proprietà il cui valore viene visualizzato.</span><span class="sxs-lookup"><span data-stu-id="895e6-119">Specify the name of the property whose value is displayed.</span></span>

## <a name="remarks"></a><span data-ttu-id="895e6-120">Osservazioni</span><span class="sxs-lookup"><span data-stu-id="895e6-120">Remarks</span></span>

<span data-ttu-id="895e6-121">Se questo elemento viene usato, è possibile specificare il [ScriptBlock](./scriptblock-element-for-itemselectioncondition-for-listcontrol-format.md) elemento quando si definisce la condizione di selezione.</span><span class="sxs-lookup"><span data-stu-id="895e6-121">If this element is used, you cannot specify the [ScriptBlock](./scriptblock-element-for-itemselectioncondition-for-listcontrol-format.md) element when defining the selection condition.</span></span>

## <a name="see-also"></a><span data-ttu-id="895e6-122">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="895e6-122">See Also</span></span>

[<span data-ttu-id="895e6-123">Elemento ScriptBlock per ItemSelectionCondition per ListIControl (formato)</span><span class="sxs-lookup"><span data-stu-id="895e6-123">ScriptBlock Element for ItemSelectionCondition for ListIControl (Format)</span></span>](./scriptblock-element-for-itemselectioncondition-for-listcontrol-format.md)

[<span data-ttu-id="895e6-124">Elemento ItemSelectionCondition per ListItem per ListControl (formato)</span><span class="sxs-lookup"><span data-stu-id="895e6-124">ItemSelectionCondition Element for ListItem for ListControl (Format)</span></span>](./itemselectioncondition-element-for-listitem-for-listcontrol-format.md)

[<span data-ttu-id="895e6-125">La scrittura di un File di formattazione di PowerShell</span><span class="sxs-lookup"><span data-stu-id="895e6-125">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
