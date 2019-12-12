---
title: Elemento ScriptBlock per ItemSeclectionCondition per i controlli per la configurazione (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 51f7aec9-7b01-4370-84f4-1e58508a851f
caps.latest.revision: 6
ms.openlocfilehash: e92b2dfff07358132c480c47c34279e5365fe400
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/05/2019
ms.locfileid: "72362120"
---
# <a name="scriptblock-element-for-itemseclectioncondition-for-controls-for-configuration-format"></a><span data-ttu-id="67a65-102">Elemento ScriptBlock per ItemSelectionCondition per Controls per Configuration (formato)</span><span class="sxs-lookup"><span data-stu-id="67a65-102">ScriptBlock Element for ItemSeclectionCondition for Controls for Configuration (Format)</span></span>

<span data-ttu-id="67a65-103">Specifica lo script che attiva la condizione.</span><span class="sxs-lookup"><span data-stu-id="67a65-103">Specifies the script that triggers the condition.</span></span> <span data-ttu-id="67a65-104">Quando questo script viene valutato `true`, la condizione viene soddisfatta e viene utilizzato il controllo.</span><span class="sxs-lookup"><span data-stu-id="67a65-104">When this script is evaluated to `true`, the condition is met, and the control is used.</span></span> <span data-ttu-id="67a65-105">Questo elemento viene usato quando si definisce un controllo comune che può essere usato da tutte le visualizzazioni nel file di formattazione.</span><span class="sxs-lookup"><span data-stu-id="67a65-105">This element is used when defining a common control that can be used by all the views in the formatting file.</span></span>

<span data-ttu-id="67a65-106">Elemento di configurazione (Format) controlla l'elemento dell'elemento di controllo Configuration (Format) per i controlli per la configurazione (Format) elemento CustomControl per il controllo per la configurazione (Format) elemento CustomEntries per CustomControl per la configurazione ( Format) elemento CustomEntry per CustomControl per i controlli per la configurazione (Format) elemento CustomItem per CustomEntry per i controlli per l'elemento Expressionation di Configuration per CustomItem per i controlli per la configurazione (Format) Elemento ItemSelectionCondition per Expression per i controlli per la configurazione (Format) elemento ScriptBlock per ItemSelectionCondition per i controlli per la configurazione (Format)</span><span class="sxs-lookup"><span data-stu-id="67a65-106">Configuration Element (Format) Controls Element of Configuration (Format) Control Element for Controls for Configuration (Format) CustomControl Element for Control for Configuration (Format) CustomEntries Element for CustomControl for Configuration (Format) CustomEntry Element for CustomControl for Controls for Configuration (Format) CustomItem Element for CustomEntry for Controls for Configuration ExpressionBinding Element for CustomItem for Controls for Configuration (Format) ItemSelectionCondition Element for ExpressionBinding for Controls for Configuration (Format) ScriptBlock Element for ItemSelectionCondition for Controls for Configuration (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="67a65-107">Sintassi</span><span class="sxs-lookup"><span data-stu-id="67a65-107">Syntax</span></span>

```xml
<ScriptBlock>ScriptToEvaluate</ScriptBlock>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="67a65-108">Attributi ed elementi</span><span class="sxs-lookup"><span data-stu-id="67a65-108">Attributes and Elements</span></span>

<span data-ttu-id="67a65-109">Nelle sezioni seguenti vengono descritti gli attributi, gli elementi figlio e l'elemento padre dell'elemento `ScriptBlock`.</span><span class="sxs-lookup"><span data-stu-id="67a65-109">The following sections describe attributes, child elements, and the parent element of the `ScriptBlock` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="67a65-110">Attributi</span><span class="sxs-lookup"><span data-stu-id="67a65-110">Attributes</span></span>

<span data-ttu-id="67a65-111">Nessuna.</span><span class="sxs-lookup"><span data-stu-id="67a65-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="67a65-112">Elementi figlio</span><span class="sxs-lookup"><span data-stu-id="67a65-112">Child Elements</span></span>

<span data-ttu-id="67a65-113">Nessuna.</span><span class="sxs-lookup"><span data-stu-id="67a65-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="67a65-114">Elementi padre</span><span class="sxs-lookup"><span data-stu-id="67a65-114">Parent Elements</span></span>

|<span data-ttu-id="67a65-115">Elemento</span><span class="sxs-lookup"><span data-stu-id="67a65-115">Element</span></span>|<span data-ttu-id="67a65-116">Description</span><span class="sxs-lookup"><span data-stu-id="67a65-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="67a65-117">Elemento ItemSelectionCondition per ExpressionName per i controlli per la configurazione (Format)</span><span class="sxs-lookup"><span data-stu-id="67a65-117">ItemSelectionCondition Element for ExpressionBinding for Controls for Configuration (Format)</span></span>](./itemselectioncondition-element-for-expressionbinding-for-controls-for-configuration-format.md)|<span data-ttu-id="67a65-118">Definisce la condizione che deve esistere per il controllo da utilizzare.</span><span class="sxs-lookup"><span data-stu-id="67a65-118">Defines the condition that must exist for this control to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="67a65-119">Valore testo</span><span class="sxs-lookup"><span data-stu-id="67a65-119">Text Value</span></span>

<span data-ttu-id="67a65-120">Specificare lo script che viene valutato.</span><span class="sxs-lookup"><span data-stu-id="67a65-120">Specify the script that is evaluated.</span></span>

## <a name="remarks"></a><span data-ttu-id="67a65-121">Osservazioni</span><span class="sxs-lookup"><span data-stu-id="67a65-121">Remarks</span></span>

<span data-ttu-id="67a65-122">Se viene usato questo elemento, non è possibile specificare l'elemento [PropertyName](./propertyname-element-for-itemseclectioncondition-for-controls-for-configuration-format.md) quando si definisce la condizione di selezione.</span><span class="sxs-lookup"><span data-stu-id="67a65-122">If this element is used, you cannot specify the [PropertyName](./propertyname-element-for-itemseclectioncondition-for-controls-for-configuration-format.md) element when defining the selection condition.</span></span>

## <a name="see-also"></a><span data-ttu-id="67a65-123">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="67a65-123">See Also</span></span>

[<span data-ttu-id="67a65-124">Elemento PropertyName per ItemSeclectionCondition per i controlli per la configurazione (Format)</span><span class="sxs-lookup"><span data-stu-id="67a65-124">PropertyName Element for ItemSeclectionCondition for Controls for Configuration (Format)</span></span>](./propertyname-element-for-itemseclectioncondition-for-controls-for-configuration-format.md)

[<span data-ttu-id="67a65-125">Elemento ItemSelectionCondition per ExpressionName per i controlli per la configurazione (Format)</span><span class="sxs-lookup"><span data-stu-id="67a65-125">ItemSelectionCondition Element for ExpressionBinding for Controls for Configuration (Format)</span></span>](./itemselectioncondition-element-for-expressionbinding-for-controls-for-configuration-format.md)

[<span data-ttu-id="67a65-126">Scrittura di un file di formattazione di PowerShell</span><span class="sxs-lookup"><span data-stu-id="67a65-126">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
