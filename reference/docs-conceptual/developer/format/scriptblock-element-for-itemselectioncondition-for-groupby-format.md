---
title: Elemento ScriptBlock per ItemSelectionCondition per GroupBy (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 58d25835-4636-4c58-9f6c-0332b9318051
caps.latest.revision: 6
ms.openlocfilehash: 4045196e306e766cd805b3e7ae31bfcb3de184ee
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/05/2019
ms.locfileid: "72364830"
---
# <a name="scriptblock-element-for-itemselectioncondition-for-groupby-format"></a><span data-ttu-id="404bd-102">Elemento ScriptBlock per ItemSelectionCondition per GroupBy (formato)</span><span class="sxs-lookup"><span data-stu-id="404bd-102">ScriptBlock Element for ItemSelectionCondition for GroupBy (Format)</span></span>

<span data-ttu-id="404bd-103">Specifica lo script che attiva la condizione.</span><span class="sxs-lookup"><span data-stu-id="404bd-103">Specifies the script that triggers the condition.</span></span> <span data-ttu-id="404bd-104">Quando questo script viene valutato `true`, la condizione viene soddisfatta e viene utilizzato il controllo.</span><span class="sxs-lookup"><span data-stu-id="404bd-104">When this script is evaluated to `true`, the condition is met, and the control is used.</span></span> <span data-ttu-id="404bd-105">Questo elemento viene utilizzato quando si definisce la modalità di visualizzazione di un nuovo gruppo di oggetti.</span><span class="sxs-lookup"><span data-stu-id="404bd-105">This element is used when defining how a new group of objects is displayed.</span></span>

<span data-ttu-id="404bd-106">Elemento Configuration (Format) elemento ViewDefinitions (Format) elemento View (Format) elemento GroupBy per View (Format) elemento CustomControl per l'elemento GroupBy (Format) CustomEntries per CustomControl per l'elemento GroupBy (Format) CustomEntry per CustomControl per l'elemento CustomItem di GroupBy (Format) per CustomEntry per l'elemento di espressione GroupBy (Format) per CustomItem per l'elemento GroupBy (Format) ItemSelectionCondition per Expression per l'elemento GroupBy (Format) ScriptBlock per ItemSelectionCondition per GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="404bd-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) GroupBy Element for View (Format) CustomControl Element for GroupBy (Format) CustomEntries Element for CustomControl for GroupBy (Format) CustomEntry Element for CustomControl for GroupBy (Format) CustomItem Element for CustomEntry for GroupBy (Format) ExpressionBinding Element for CustomItem for GroupBy (Format) ItemSelectionCondition Element for ExpressionBinding for GroupBy (Format) ScriptBlock Element for ItemSelectionCondition for GroupBy (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="404bd-107">Sintassi</span><span class="sxs-lookup"><span data-stu-id="404bd-107">Syntax</span></span>

```xml
<ScriptBlock>ScriptToEvaluate</ScriptBlock>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="404bd-108">Attributi ed elementi</span><span class="sxs-lookup"><span data-stu-id="404bd-108">Attributes and Elements</span></span>

<span data-ttu-id="404bd-109">Nelle sezioni seguenti vengono descritti gli attributi, gli elementi figlio e l'elemento padre dell'elemento `ScriptBlock`.</span><span class="sxs-lookup"><span data-stu-id="404bd-109">The following sections describe attributes, child elements, and the parent element of the `ScriptBlock` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="404bd-110">Attributi</span><span class="sxs-lookup"><span data-stu-id="404bd-110">Attributes</span></span>

<span data-ttu-id="404bd-111">Nessuna.</span><span class="sxs-lookup"><span data-stu-id="404bd-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="404bd-112">Elementi figlio</span><span class="sxs-lookup"><span data-stu-id="404bd-112">Child Elements</span></span>

<span data-ttu-id="404bd-113">Nessuna.</span><span class="sxs-lookup"><span data-stu-id="404bd-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="404bd-114">Elementi padre</span><span class="sxs-lookup"><span data-stu-id="404bd-114">Parent Elements</span></span>

|<span data-ttu-id="404bd-115">Elemento</span><span class="sxs-lookup"><span data-stu-id="404bd-115">Element</span></span>|<span data-ttu-id="404bd-116">Description</span><span class="sxs-lookup"><span data-stu-id="404bd-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="404bd-117">Elemento ItemSelectionCondition per Expressiongroup per GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="404bd-117">ItemSelectionCondition Element for ExpressionBinding for GroupBy (Format)</span></span>](./itemselectioncondition-element-for-expressionbinding-for-groupby-format.md)|<span data-ttu-id="404bd-118">Definisce la condizione che deve esistere per il controllo da utilizzare.</span><span class="sxs-lookup"><span data-stu-id="404bd-118">Defines the condition that must exist for this control to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="404bd-119">Valore testo</span><span class="sxs-lookup"><span data-stu-id="404bd-119">Text Value</span></span>

<span data-ttu-id="404bd-120">Specificare lo script che viene valutato.</span><span class="sxs-lookup"><span data-stu-id="404bd-120">Specify the script that is evaluated.</span></span>

## <a name="remarks"></a><span data-ttu-id="404bd-121">Osservazioni</span><span class="sxs-lookup"><span data-stu-id="404bd-121">Remarks</span></span>

<span data-ttu-id="404bd-122">Se viene usato questo elemento, non è possibile specificare l'elemento [PropertyName](./propertyname-element-for-itemselectioncondition-for-groupby-format.md) quando si definisce la condizione di selezione.</span><span class="sxs-lookup"><span data-stu-id="404bd-122">If this element is used, you cannot specify the [PropertyName](./propertyname-element-for-itemselectioncondition-for-groupby-format.md) element when defining the selection condition.</span></span>

## <a name="see-also"></a><span data-ttu-id="404bd-123">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="404bd-123">See Also</span></span>

[<span data-ttu-id="404bd-124">Elemento ItemSelectionCondition per Expressiongroup per GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="404bd-124">ItemSelectionCondition Element for ExpressionBinding for GroupBy (Format)</span></span>](./itemselectioncondition-element-for-expressionbinding-for-groupby-format.md)

[<span data-ttu-id="404bd-125">Elemento PropertyName per ItemSelectionCondition per GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="404bd-125">PropertyName Element for ItemSelectionCondition for GroupBy (Format)</span></span>](./propertyname-element-for-itemselectioncondition-for-groupby-format.md)

[<span data-ttu-id="404bd-126">Scrittura di un file di formattazione di PowerShell</span><span class="sxs-lookup"><span data-stu-id="404bd-126">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
