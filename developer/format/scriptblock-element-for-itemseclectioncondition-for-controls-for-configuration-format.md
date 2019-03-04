---
title: Elemento ScriptBlock per ItemSeclectionCondition per i controlli per la configurazione (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 51f7aec9-7b01-4370-84f4-1e58508a851f
caps.latest.revision: 6
ms.openlocfilehash: e92b2dfff07358132c480c47c34279e5365fe400
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/03/2019
ms.locfileid: "56861857"
---
# <a name="scriptblock-element-for-itemseclectioncondition-for-controls-for-configuration-format"></a><span data-ttu-id="2b3ba-102">Elemento ScriptBlock per ItemSelectionCondition per Controls per Configuration (formato)</span><span class="sxs-lookup"><span data-stu-id="2b3ba-102">ScriptBlock Element for ItemSeclectionCondition for Controls for Configuration (Format)</span></span>

<span data-ttu-id="2b3ba-103">Specifica lo script che genera la condizione.</span><span class="sxs-lookup"><span data-stu-id="2b3ba-103">Specifies the script that triggers the condition.</span></span> <span data-ttu-id="2b3ba-104">Quando questo script viene valutato per `true`, viene soddisfatta la condizione e viene utilizzato il controllo.</span><span class="sxs-lookup"><span data-stu-id="2b3ba-104">When this script is evaluated to `true`, the condition is met, and the control is used.</span></span> <span data-ttu-id="2b3ba-105">Questo elemento viene usato quando si definisce un controllo comune che può essere usato da tutte le visualizzazioni nel file di formattazione.</span><span class="sxs-lookup"><span data-stu-id="2b3ba-105">This element is used when defining a common control that can be used by all the views in the formatting file.</span></span>

<span data-ttu-id="2b3ba-106">Configurazione (formato) i controlli elemento di configurazione (formato) elemento di controllo per i controlli di configurazione (formato) CustomControl elemento per il controllo per elemento di configurazione (formato) CustomEntries per CustomControl per Configuration ( Elemento CustomEntry Format) per CustomControl per i controlli per elemento di configurazione (formato) CustomItem per CustomEntry per i controlli per configurazione ExpressionBinding elemento CustomItem per i controlli per la configurazione (formato) Elemento ItemSelectionCondition per ExpressionBinding per i controlli per elemento di configurazione (formato) ScriptBlock per ItemSelectionCondition per i controlli per la configurazione (formato)</span><span class="sxs-lookup"><span data-stu-id="2b3ba-106">Configuration Element (Format) Controls Element of Configuration (Format) Control Element for Controls for Configuration (Format) CustomControl Element for Control for Configuration (Format) CustomEntries Element for CustomControl for Configuration (Format) CustomEntry Element for CustomControl for Controls for Configuration (Format) CustomItem Element for CustomEntry for Controls for Configuration ExpressionBinding Element for CustomItem for Controls for Configuration (Format) ItemSelectionCondition Element for ExpressionBinding for Controls for Configuration (Format) ScriptBlock Element for ItemSelectionCondition for Controls for Configuration (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="2b3ba-107">Sintassi</span><span class="sxs-lookup"><span data-stu-id="2b3ba-107">Syntax</span></span>

```xml
<ScriptBlock>ScriptToEvaluate</ScriptBlock>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="2b3ba-108">Attributi ed elementi</span><span class="sxs-lookup"><span data-stu-id="2b3ba-108">Attributes and Elements</span></span>

<span data-ttu-id="2b3ba-109">Le sezioni seguenti descrivono gli attributi e gli elementi figlio dell'elemento padre del `ScriptBlock` elemento.</span><span class="sxs-lookup"><span data-stu-id="2b3ba-109">The following sections describe attributes, child elements, and the parent element of the `ScriptBlock` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="2b3ba-110">Attributes</span><span class="sxs-lookup"><span data-stu-id="2b3ba-110">Attributes</span></span>

<span data-ttu-id="2b3ba-111">Nessuna.</span><span class="sxs-lookup"><span data-stu-id="2b3ba-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="2b3ba-112">Elementi figlio</span><span class="sxs-lookup"><span data-stu-id="2b3ba-112">Child Elements</span></span>

<span data-ttu-id="2b3ba-113">Nessuna.</span><span class="sxs-lookup"><span data-stu-id="2b3ba-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="2b3ba-114">Elementi padre</span><span class="sxs-lookup"><span data-stu-id="2b3ba-114">Parent Elements</span></span>

|<span data-ttu-id="2b3ba-115">Elemento</span><span class="sxs-lookup"><span data-stu-id="2b3ba-115">Element</span></span>|<span data-ttu-id="2b3ba-116">Description</span><span class="sxs-lookup"><span data-stu-id="2b3ba-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="2b3ba-117">Elemento ItemSelectionCondition per ExpressionBinding per i controlli per la configurazione (formato)</span><span class="sxs-lookup"><span data-stu-id="2b3ba-117">ItemSelectionCondition Element for ExpressionBinding for Controls for Configuration (Format)</span></span>](./itemselectioncondition-element-for-expressionbinding-for-controls-for-configuration-format.md)|<span data-ttu-id="2b3ba-118">Definisce la condizione che deve essere presente per questo controllo da utilizzare.</span><span class="sxs-lookup"><span data-stu-id="2b3ba-118">Defines the condition that must exist for this control to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="2b3ba-119">Valore di testo</span><span class="sxs-lookup"><span data-stu-id="2b3ba-119">Text Value</span></span>

<span data-ttu-id="2b3ba-120">Specificare lo script che viene valutato.</span><span class="sxs-lookup"><span data-stu-id="2b3ba-120">Specify the script that is evaluated.</span></span>

## <a name="remarks"></a><span data-ttu-id="2b3ba-121">Osservazioni</span><span class="sxs-lookup"><span data-stu-id="2b3ba-121">Remarks</span></span>

<span data-ttu-id="2b3ba-122">Se questo elemento viene usato, è possibile specificare il [PropertyName](./propertyname-element-for-itemseclectioncondition-for-controls-for-configuration-format.md) elemento quando si definisce la condizione di selezione.</span><span class="sxs-lookup"><span data-stu-id="2b3ba-122">If this element is used, you cannot specify the [PropertyName](./propertyname-element-for-itemseclectioncondition-for-controls-for-configuration-format.md) element when defining the selection condition.</span></span>

## <a name="see-also"></a><span data-ttu-id="2b3ba-123">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="2b3ba-123">See Also</span></span>

[<span data-ttu-id="2b3ba-124">Elemento PropertyName per ItemSeclectionCondition per i controlli per la configurazione (formato)</span><span class="sxs-lookup"><span data-stu-id="2b3ba-124">PropertyName Element for ItemSeclectionCondition for Controls for Configuration (Format)</span></span>](./propertyname-element-for-itemseclectioncondition-for-controls-for-configuration-format.md)

[<span data-ttu-id="2b3ba-125">Elemento ItemSelectionCondition per ExpressionBinding per i controlli per la configurazione (formato)</span><span class="sxs-lookup"><span data-stu-id="2b3ba-125">ItemSelectionCondition Element for ExpressionBinding for Controls for Configuration (Format)</span></span>](./itemselectioncondition-element-for-expressionbinding-for-controls-for-configuration-format.md)

[<span data-ttu-id="2b3ba-126">La scrittura di un File di formattazione di PowerShell</span><span class="sxs-lookup"><span data-stu-id="2b3ba-126">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
