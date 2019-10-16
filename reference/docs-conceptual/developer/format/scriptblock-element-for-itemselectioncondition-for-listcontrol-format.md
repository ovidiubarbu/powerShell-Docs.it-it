---
title: Elemento ScriptBlock per ItemSelectionCondition per ListControl (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: c929a6df-d050-416a-9de0-e913dd5a035c
caps.latest.revision: 8
ms.openlocfilehash: a0768a9c1ac66cd9dcf1848c4b031ccbc722b4c2
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/15/2019
ms.locfileid: "72362100"
---
# <a name="scriptblock-element-for-itemselectioncondition-for-listcontrol-format"></a><span data-ttu-id="804e8-102">Elemento ScriptBlock per ItemSelectionCondition per ListControl (formato)</span><span class="sxs-lookup"><span data-stu-id="804e8-102">ScriptBlock Element for ItemSelectionCondition for ListControl (Format)</span></span>

<span data-ttu-id="804e8-103">Specifica lo script che attiva la condizione.</span><span class="sxs-lookup"><span data-stu-id="804e8-103">Specifies the script that triggers the condition.</span></span> <span data-ttu-id="804e8-104">Quando questo script viene valutato `true`, la condizione viene soddisfatta e viene utilizzato l'elemento dell'elenco.</span><span class="sxs-lookup"><span data-stu-id="804e8-104">When this script is evaluated to `true`, the condition is met, and the list item is used.</span></span> <span data-ttu-id="804e8-105">Questo elemento viene utilizzato quando si definisce una visualizzazione elenco.</span><span class="sxs-lookup"><span data-stu-id="804e8-105">This element is used when defining a list view.</span></span>

<span data-ttu-id="804e8-106">Elemento Configuration (Format) elemento ViewDefinitions (Format) elemento View (Format) elemento ListControl (Format) elemento ListEntries per l'elemento ListControl (Format) ListEntry per ListEntries per l'elemento ListItem (Format) ListItems per ListEntry per l'elemento ListItem (Format) ListItem per ListItems per il controllo elenco (Format) elemento ItemSelectionCondition per ListItem per ListControl (Format) elemento ScriptBlock per ItemSelectionCondition per ListControl (Format)</span><span class="sxs-lookup"><span data-stu-id="804e8-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) ListControl Element (Format) ListEntries Element for ListControl (Format) ListEntry Element for ListEntries for ListControl (Format) ListItems Element for ListEntry for ListControl (Format) ListItem Element for ListItems for List Control (Format) ItemSelectionCondition Element for ListItem for ListControl (Format) ScriptBlock Element for ItemSelectionCondition for ListControl  (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="804e8-107">Sintassi</span><span class="sxs-lookup"><span data-stu-id="804e8-107">Syntax</span></span>

```xml
<ScriptBlock>ScriptToEvaluate</ScriptBlock>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="804e8-108">Attributi ed elementi</span><span class="sxs-lookup"><span data-stu-id="804e8-108">Attributes and Elements</span></span>

<span data-ttu-id="804e8-109">Nelle sezioni seguenti vengono descritti gli attributi, gli elementi figlio e gli elementi padre dell'elemento `ScriptBlock`.</span><span class="sxs-lookup"><span data-stu-id="804e8-109">The following sections describe attributes, child elements, and the parent elements of the `ScriptBlock` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="804e8-110">Attributi</span><span class="sxs-lookup"><span data-stu-id="804e8-110">Attributes</span></span>

<span data-ttu-id="804e8-111">Nessuna.</span><span class="sxs-lookup"><span data-stu-id="804e8-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="804e8-112">Elementi figlio</span><span class="sxs-lookup"><span data-stu-id="804e8-112">Child Elements</span></span>

<span data-ttu-id="804e8-113">Nessuna.</span><span class="sxs-lookup"><span data-stu-id="804e8-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="804e8-114">Elementi padre</span><span class="sxs-lookup"><span data-stu-id="804e8-114">Parent Elements</span></span>

|<span data-ttu-id="804e8-115">Elemento</span><span class="sxs-lookup"><span data-stu-id="804e8-115">Element</span></span>|<span data-ttu-id="804e8-116">Description</span><span class="sxs-lookup"><span data-stu-id="804e8-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="804e8-117">Elemento ItemSelectionCondition per ListItem per ListControl (Format)</span><span class="sxs-lookup"><span data-stu-id="804e8-117">ItemSelectionCondition Element for ListItem for ListControl (Format)</span></span>](./itemselectioncondition-element-for-listitem-for-listcontrol-format.md)|<span data-ttu-id="804e8-118">Definisce la condizione che deve esistere per l'uso di questo elemento elenco.</span><span class="sxs-lookup"><span data-stu-id="804e8-118">Defines the condition that must exist for this list item to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="804e8-119">Valore di testo</span><span class="sxs-lookup"><span data-stu-id="804e8-119">Text Value</span></span>

<span data-ttu-id="804e8-120">Specificare lo script che viene valutato.</span><span class="sxs-lookup"><span data-stu-id="804e8-120">Specify the script that is evaluated.</span></span>

## <a name="remarks"></a><span data-ttu-id="804e8-121">Osservazioni</span><span class="sxs-lookup"><span data-stu-id="804e8-121">Remarks</span></span>

<span data-ttu-id="804e8-122">Se viene usato questo elemento, non è possibile specificare l'elemento `PropertyName` quando si definisce la condizione di selezione.</span><span class="sxs-lookup"><span data-stu-id="804e8-122">If this element is used, you cannot specify the `PropertyName` element when defining the selection condition.</span></span>

## <a name="see-also"></a><span data-ttu-id="804e8-123">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="804e8-123">See Also</span></span>

[<span data-ttu-id="804e8-124">Scrittura di un file di formattazione di PowerShell</span><span class="sxs-lookup"><span data-stu-id="804e8-124">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
