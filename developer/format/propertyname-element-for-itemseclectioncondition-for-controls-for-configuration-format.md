---
title: Elemento PropertyName per ItemSeclectionCondition per i controlli per la configurazione (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ad8ab181-c559-492e-a0cf-299e381fdcc3
caps.latest.revision: 6
ms.openlocfilehash: ce25789bdfc2679372ca9e42f99dcc6a30ae2def
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62064904"
---
# <a name="propertyname-element-for-itemseclectioncondition-for-controls-for-configuration-format"></a><span data-ttu-id="69b34-102">Elemento PropertyName per ItemSelectionCondition per Controls per Configuration (formato)</span><span class="sxs-lookup"><span data-stu-id="69b34-102">PropertyName Element for ItemSeclectionCondition for Controls for Configuration (Format)</span></span>

<span data-ttu-id="69b34-103">Specifica la proprietà .NET che attiva la condizione.</span><span class="sxs-lookup"><span data-stu-id="69b34-103">Specifies the .NET property that triggers the condition.</span></span> <span data-ttu-id="69b34-104">Quando questa proprietà è presente o quando viene restituito `true`, viene soddisfatta la condizione e viene utilizzato il controllo.</span><span class="sxs-lookup"><span data-stu-id="69b34-104">When this property is present or when it evaluates to `true`, the condition is met, and the control is used.</span></span> <span data-ttu-id="69b34-105">Questo elemento viene usato quando si definisce un controllo comune che può essere usato da tutte le visualizzazioni nel file di formattazione.</span><span class="sxs-lookup"><span data-stu-id="69b34-105">This element is used when defining a common control that can be used by all the views in the formatting file.</span></span>

<span data-ttu-id="69b34-106">Configurazione (formato) i controlli elemento di configurazione (formato) elemento di controllo per i controlli di configurazione (formato) CustomControl elemento per il controllo per elemento di configurazione (formato) CustomEntries per CustomControl per Configuration ( Elemento CustomEntry Format) per CustomControl per i controlli per elemento di configurazione (formato) CustomItem per CustomEntry per i controlli per configurazione ExpressionBinding elemento CustomItem per i controlli per la configurazione (formato) Elemento ItemSelectionCondition per ExpressionBinding per i controlli per elemento di configurazione (formato) PropertyName per ItemSeclectionCondition per i controlli per la configurazione (formato)</span><span class="sxs-lookup"><span data-stu-id="69b34-106">Configuration Element (Format) Controls Element of Configuration (Format) Control Element for Controls for Configuration (Format) CustomControl Element for Control for Configuration (Format) CustomEntries Element for CustomControl for Configuration (Format) CustomEntry Element for CustomControl for Controls for Configuration (Format) CustomItem Element for CustomEntry for Controls for Configuration ExpressionBinding Element for CustomItem for Controls for Configuration (Format) ItemSelectionCondition Element for ExpressionBinding for Controls for Configuration (Format) PropertyName Element for ItemSeclectionCondition for Controls for Configuration (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="69b34-107">Sintassi</span><span class="sxs-lookup"><span data-stu-id="69b34-107">Syntax</span></span>

```xml
<PropertyName>.NetTypeProperty</PropertyName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="69b34-108">Elementi e attributi</span><span class="sxs-lookup"><span data-stu-id="69b34-108">Attributes and Elements</span></span>

<span data-ttu-id="69b34-109">Le sezioni seguenti descrivono gli attributi e gli elementi figlio dell'elemento padre del `PropertyName` elemento.</span><span class="sxs-lookup"><span data-stu-id="69b34-109">The following sections describe attributes, child elements, and the parent element of the `PropertyName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="69b34-110">Attributes</span><span class="sxs-lookup"><span data-stu-id="69b34-110">Attributes</span></span>

<span data-ttu-id="69b34-111">Nessuna.</span><span class="sxs-lookup"><span data-stu-id="69b34-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="69b34-112">Elementi figlio</span><span class="sxs-lookup"><span data-stu-id="69b34-112">Child Elements</span></span>

<span data-ttu-id="69b34-113">Nessuna.</span><span class="sxs-lookup"><span data-stu-id="69b34-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="69b34-114">Elementi padre</span><span class="sxs-lookup"><span data-stu-id="69b34-114">Parent Elements</span></span>

|<span data-ttu-id="69b34-115">Elemento</span><span class="sxs-lookup"><span data-stu-id="69b34-115">Element</span></span>|<span data-ttu-id="69b34-116">Description</span><span class="sxs-lookup"><span data-stu-id="69b34-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="69b34-117">Elemento ItemSelectionCondition per ExpressionBinding per i controlli per la configurazione (formato)</span><span class="sxs-lookup"><span data-stu-id="69b34-117">ItemSelectionCondition Element for ExpressionBinding for Controls for Configuration (Format)</span></span>](./itemselectioncondition-element-for-expressionbinding-for-controls-for-configuration-format.md)|<span data-ttu-id="69b34-118">Definisce la condizione che deve essere presente per questo controllo da utilizzare.</span><span class="sxs-lookup"><span data-stu-id="69b34-118">Defines the condition that must exist for this control to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="69b34-119">Valore di testo</span><span class="sxs-lookup"><span data-stu-id="69b34-119">Text Value</span></span>

<span data-ttu-id="69b34-120">Specificare il nome della proprietà .NET che attiva la condizione.</span><span class="sxs-lookup"><span data-stu-id="69b34-120">Specify the name of the .NET property that triggers the condition.</span></span>

## <a name="remarks"></a><span data-ttu-id="69b34-121">Osservazioni</span><span class="sxs-lookup"><span data-stu-id="69b34-121">Remarks</span></span>

<span data-ttu-id="69b34-122">Se questo elemento viene usato, è possibile specificare il [ScriptBlock](./scriptblock-element-for-itemseclectioncondition-for-controls-for-configuration-format.md) elemento quando si definisce la condizione di selezione.</span><span class="sxs-lookup"><span data-stu-id="69b34-122">If this element is used, you cannot specify the [ScriptBlock](./scriptblock-element-for-itemseclectioncondition-for-controls-for-configuration-format.md) element when defining the selection condition.</span></span>

## <a name="see-also"></a><span data-ttu-id="69b34-123">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="69b34-123">See Also</span></span>

[<span data-ttu-id="69b34-124">Elemento ScriptBlock per ItemSeclectionCondition per i controlli per la configurazione (formato)</span><span class="sxs-lookup"><span data-stu-id="69b34-124">ScriptBlock Element for ItemSeclectionCondition for Controls for Configuration (Format)</span></span>](./scriptblock-element-for-itemseclectioncondition-for-controls-for-configuration-format.md)

[<span data-ttu-id="69b34-125">Elemento ItemSelectionCondition per ExpressionBinding per i controlli per la configurazione (formato)</span><span class="sxs-lookup"><span data-stu-id="69b34-125">ItemSelectionCondition Element for ExpressionBinding for Controls for Configuration (Format)</span></span>](./itemselectioncondition-element-for-expressionbinding-for-controls-for-configuration-format.md)

[<span data-ttu-id="69b34-126">La scrittura di un File di formattazione di PowerShell</span><span class="sxs-lookup"><span data-stu-id="69b34-126">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
