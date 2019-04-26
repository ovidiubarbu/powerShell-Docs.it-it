---
title: Elemento PropertyName per ItemSelectionCondition per CustomControl per visualizzazione (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f2b12006-8d52-486b-91a3-e6224ca80e56
caps.latest.revision: 6
ms.openlocfilehash: 52d0b0816eaef6752220e0c3b1249e5a0e44a3ee
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62064867"
---
# <a name="propertyname-element-for-itemselectioncondition-for-customcontrol-for-view-format"></a><span data-ttu-id="35635-102">Elemento PropertyName per ItemSelectionCondition per CustomControl per View (formato)</span><span class="sxs-lookup"><span data-stu-id="35635-102">PropertyName Element for ItemSelectionCondition for CustomControl for View (Format)</span></span>

<span data-ttu-id="35635-103">Specifica la proprietà .NET che attiva la condizione.</span><span class="sxs-lookup"><span data-stu-id="35635-103">Specifies the .NET property that triggers the condition.</span></span> <span data-ttu-id="35635-104">Quando questa proprietà è presente o quando viene restituito `true`, viene soddisfatta la condizione e viene utilizzato il controllo.</span><span class="sxs-lookup"><span data-stu-id="35635-104">When this property is present or when it evaluates to `true`, the condition is met, and the control is used.</span></span> <span data-ttu-id="35635-105">Questo elemento viene usato quando si definisce una vista di controllo personalizzato.</span><span class="sxs-lookup"><span data-stu-id="35635-105">This element is used when defining a custom control view.</span></span>

<span data-ttu-id="35635-106">Elemento (formato) elemento ViewDefinitions (formato) visualizzazione elemento (formato) elemento CustomControl (formato) CustomEntries elemento di configurazione per CustomControl elemento di visualizzazione (formato) CustomEntry per CustomEntries per elemento CustomItem visualizzazione (formato) Elemento di visualizzazione (formato) ExpressionBinding per CustomItem per CustomControl elemento di visualizzazione (formato) ItemSelectionCondition per associazione di espressioni per CustomControl elemento di visualizzazione (formato) PropertyName per ItemSelectionCondition per CustomEntry CustomControl per visualizzazione (formato</span><span class="sxs-lookup"><span data-stu-id="35635-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) CustomControl Element (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for View (Format) CustomItem Element for CustomEntry for View (Format) ExpressionBinding Element for CustomItem for CustomControl for View (Format) ItemSelectionCondition Element for Expression Binding for CustomControl for View (Format) PropertyName Element for ItemSelectionCondition for CustomControl for View (Format</span></span>

## <a name="syntax"></a><span data-ttu-id="35635-107">Sintassi</span><span class="sxs-lookup"><span data-stu-id="35635-107">Syntax</span></span>

```xml
<PropertyName>.NetTypeProperty</PropertyName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="35635-108">Elementi e attributi</span><span class="sxs-lookup"><span data-stu-id="35635-108">Attributes and Elements</span></span>

<span data-ttu-id="35635-109">Le sezioni seguenti descrivono gli attributi e gli elementi figlio dell'elemento padre del `PropertyName` elemento.</span><span class="sxs-lookup"><span data-stu-id="35635-109">The following sections describe attributes, child elements, and the parent element of the `PropertyName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="35635-110">Attributes</span><span class="sxs-lookup"><span data-stu-id="35635-110">Attributes</span></span>

<span data-ttu-id="35635-111">Nessuna.</span><span class="sxs-lookup"><span data-stu-id="35635-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="35635-112">Elementi figlio</span><span class="sxs-lookup"><span data-stu-id="35635-112">Child Elements</span></span>

<span data-ttu-id="35635-113">Nessuna.</span><span class="sxs-lookup"><span data-stu-id="35635-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="35635-114">Elementi padre</span><span class="sxs-lookup"><span data-stu-id="35635-114">Parent Elements</span></span>

|<span data-ttu-id="35635-115">Elemento</span><span class="sxs-lookup"><span data-stu-id="35635-115">Element</span></span>|<span data-ttu-id="35635-116">Description</span><span class="sxs-lookup"><span data-stu-id="35635-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="35635-117">Elemento ItemSelectionCondition per associazione di espressioni per CustomControl per visualizzazione (formato)</span><span class="sxs-lookup"><span data-stu-id="35635-117">ItemSelectionCondition Element for Expression Binding for CustomControl for View (Format)</span></span>](./itemselectioncondition-element-for-expressionbinding-for-customcontrol-format.md)|<span data-ttu-id="35635-118">Definisce la condizione che deve essere presente per questo controllo da utilizzare.</span><span class="sxs-lookup"><span data-stu-id="35635-118">Defines the condition that must exist for this control to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="35635-119">Valore di testo</span><span class="sxs-lookup"><span data-stu-id="35635-119">Text Value</span></span>

<span data-ttu-id="35635-120">Specificare il nome della proprietà .NET che attiva la condizione.</span><span class="sxs-lookup"><span data-stu-id="35635-120">Specify the name of the .NET property that triggers the condition.</span></span>

## <a name="remarks"></a><span data-ttu-id="35635-121">Osservazioni</span><span class="sxs-lookup"><span data-stu-id="35635-121">Remarks</span></span>

<span data-ttu-id="35635-122">Se questo elemento viene usato, è possibile specificare il [ScriptBlock](./scriptblock-element-for-itemselectioncondition-for-customcontrol-for-view-format.md) elemento quando si definisce la condizione di selezione.</span><span class="sxs-lookup"><span data-stu-id="35635-122">If this element is used, you cannot specify the [ScriptBlock](./scriptblock-element-for-itemselectioncondition-for-customcontrol-for-view-format.md) element when defining the selection condition.</span></span>

## <a name="see-also"></a><span data-ttu-id="35635-123">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="35635-123">See Also</span></span>

[<span data-ttu-id="35635-124">Elemento ScriptBlock per ItemSelectionCondition per CustomControl per visualizzazione (formato)</span><span class="sxs-lookup"><span data-stu-id="35635-124">ScriptBlock Element for ItemSelectionCondition for CustomControl for View (Format)</span></span>](./scriptblock-element-for-itemselectioncondition-for-customcontrol-for-view-format.md)

[<span data-ttu-id="35635-125">Elemento ItemSelectionCondition per associazione di espressioni per CustomControl per visualizzazione (formato)</span><span class="sxs-lookup"><span data-stu-id="35635-125">ItemSelectionCondition Element for Expression Binding for CustomControl for View (Format)</span></span>](./itemselectioncondition-element-for-expressionbinding-for-customcontrol-format.md)

[<span data-ttu-id="35635-126">La scrittura di un File di formattazione di PowerShell</span><span class="sxs-lookup"><span data-stu-id="35635-126">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
