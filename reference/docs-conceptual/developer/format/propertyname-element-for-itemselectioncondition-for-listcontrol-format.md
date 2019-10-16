---
title: Elemento PropertyName per ItemSelectionCondition per ListControl (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d5e707ae-3c84-4ceb-ba31-56b3ffde6d6c
caps.latest.revision: 7
ms.openlocfilehash: b15e26e18126f69eee7c3a857f9a461d4bdf5848
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/15/2019
ms.locfileid: "72362390"
---
# <a name="propertyname-element-for-itemselectioncondition-for-listcontrol-format"></a><span data-ttu-id="34982-102">Elemento PropertyName per ItemSelectionCondition per ListControl (formato)</span><span class="sxs-lookup"><span data-stu-id="34982-102">PropertyName Element for ItemSelectionCondition for ListControl (Format)</span></span>

<span data-ttu-id="34982-103">Specifica la proprietà .NET che attiva la condizione.</span><span class="sxs-lookup"><span data-stu-id="34982-103">Specifies the .NET property that triggers the condition.</span></span> <span data-ttu-id="34982-104">Quando questa proprietà è presente o quando restituisce `true`, la condizione viene soddisfatta e viene utilizzata la vista.</span><span class="sxs-lookup"><span data-stu-id="34982-104">When this property is present or when it evaluates to `true`, the condition is met, and the view is used.</span></span> <span data-ttu-id="34982-105">Questo elemento viene utilizzato quando si definisce una visualizzazione elenco.</span><span class="sxs-lookup"><span data-stu-id="34982-105">This element is used when defining a list view.</span></span>

<span data-ttu-id="34982-106">Elemento di configurazione (Format) elemento ViewDefinitions (Format) elemento View (Format) elemento ListControl (Format) elemento ListEntries (Format) elemento ListEntry per ListControl (Format) elemento ListItems per ListEntry per ListControl (Format) ListItem Elemento per ListItems per ListControl (Format) elemento ItemSelectionCondition per ListItem per elemento ListControls PropertyName per ItemSelectionCondition per ListControl (Format)</span><span class="sxs-lookup"><span data-stu-id="34982-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) ListControl Element (Format) ListEntries Element (Format) ListEntry Element for ListControl (Format) ListItems Element for ListEntry for ListControl (Format) ListItem Element for ListItems for ListControl (Format) ItemSelectionCondition Element for ListItem for ListControls PropertyName Element for ItemSelectionCondition for ListControl (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="34982-107">Sintassi</span><span class="sxs-lookup"><span data-stu-id="34982-107">Syntax</span></span>

```xml
<PropertyName>.NetTypeProperty</PropertyName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="34982-108">Attributi ed elementi</span><span class="sxs-lookup"><span data-stu-id="34982-108">Attributes and Elements</span></span>

<span data-ttu-id="34982-109">Nelle sezioni seguenti vengono descritti gli attributi, gli elementi figlio e gli elementi padre dell'elemento `PropertyName`.</span><span class="sxs-lookup"><span data-stu-id="34982-109">The following sections describe attributes, child elements, and the parent elements of the `PropertyName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="34982-110">Attributi</span><span class="sxs-lookup"><span data-stu-id="34982-110">Attributes</span></span>

<span data-ttu-id="34982-111">Nessuna.</span><span class="sxs-lookup"><span data-stu-id="34982-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="34982-112">Elementi figlio</span><span class="sxs-lookup"><span data-stu-id="34982-112">Child Elements</span></span>

<span data-ttu-id="34982-113">Nessuna.</span><span class="sxs-lookup"><span data-stu-id="34982-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="34982-114">Elementi padre</span><span class="sxs-lookup"><span data-stu-id="34982-114">Parent Elements</span></span>

|<span data-ttu-id="34982-115">Elemento</span><span class="sxs-lookup"><span data-stu-id="34982-115">Element</span></span>|<span data-ttu-id="34982-116">Description</span><span class="sxs-lookup"><span data-stu-id="34982-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="34982-117">Elemento ItemSelectionCondition per ListItem per ListControl (Format)</span><span class="sxs-lookup"><span data-stu-id="34982-117">ItemSelectionCondition Element for ListItem for ListControl (Format)</span></span>](./itemselectioncondition-element-for-listitem-for-listcontrol-format.md)||

## <a name="text-value"></a><span data-ttu-id="34982-118">Valore di testo</span><span class="sxs-lookup"><span data-stu-id="34982-118">Text Value</span></span>

<span data-ttu-id="34982-119">Consente di specificare il nome della proprietà di cui viene visualizzato il valore.</span><span class="sxs-lookup"><span data-stu-id="34982-119">Specify the name of the property whose value is displayed.</span></span>

## <a name="remarks"></a><span data-ttu-id="34982-120">Osservazioni</span><span class="sxs-lookup"><span data-stu-id="34982-120">Remarks</span></span>

<span data-ttu-id="34982-121">Se viene usato questo elemento, non è possibile specificare l'elemento [scriptblock](./scriptblock-element-for-itemselectioncondition-for-listcontrol-format.md) quando si definisce la condizione di selezione.</span><span class="sxs-lookup"><span data-stu-id="34982-121">If this element is used, you cannot specify the [ScriptBlock](./scriptblock-element-for-itemselectioncondition-for-listcontrol-format.md) element when defining the selection condition.</span></span>

## <a name="see-also"></a><span data-ttu-id="34982-122">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="34982-122">See Also</span></span>

[<span data-ttu-id="34982-123">Elemento ScriptBlock per ItemSelectionCondition per ListIControl (Format)</span><span class="sxs-lookup"><span data-stu-id="34982-123">ScriptBlock Element for ItemSelectionCondition for ListIControl (Format)</span></span>](./scriptblock-element-for-itemselectioncondition-for-listcontrol-format.md)

[<span data-ttu-id="34982-124">Elemento ItemSelectionCondition per ListItem per ListControl (Format)</span><span class="sxs-lookup"><span data-stu-id="34982-124">ItemSelectionCondition Element for ListItem for ListControl (Format)</span></span>](./itemselectioncondition-element-for-listitem-for-listcontrol-format.md)

[<span data-ttu-id="34982-125">Scrittura di un file di formattazione di PowerShell</span><span class="sxs-lookup"><span data-stu-id="34982-125">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
