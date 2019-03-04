---
title: Elemento ScriptBlock per ItemSelectionCondition per ListControl (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: c929a6df-d050-416a-9de0-e913dd5a035c
caps.latest.revision: 8
ms.openlocfilehash: a0768a9c1ac66cd9dcf1848c4b031ccbc722b4c2
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/03/2019
ms.locfileid: "56855417"
---
# <a name="scriptblock-element-for-itemselectioncondition-for-listcontrol-format"></a><span data-ttu-id="f8ce7-102">Elemento ScriptBlock per ItemSelectionCondition per ListControl (formato)</span><span class="sxs-lookup"><span data-stu-id="f8ce7-102">ScriptBlock Element for ItemSelectionCondition for ListControl (Format)</span></span>

<span data-ttu-id="f8ce7-103">Specifica lo script che genera la condizione.</span><span class="sxs-lookup"><span data-stu-id="f8ce7-103">Specifies the script that triggers the condition.</span></span> <span data-ttu-id="f8ce7-104">Quando questo script viene valutato per `true`, viene soddisfatta la condizione e viene usato l'elemento dell'elenco.</span><span class="sxs-lookup"><span data-stu-id="f8ce7-104">When this script is evaluated to `true`, the condition is met, and the list item is used.</span></span> <span data-ttu-id="f8ce7-105">Questo elemento viene usato quando si definisce una visualizzazione elenco.</span><span class="sxs-lookup"><span data-stu-id="f8ce7-105">This element is used when defining a list view.</span></span>

<span data-ttu-id="f8ce7-106">Elemento (formato) elemento ViewDefinitions (formato) visualizzazione elemento (formato) elemento dell'oggetto ListControl (formato) ListEntries elemento di configurazione per elemento dell'oggetto ListControl (formato) ListEntry ListEntries per elemento ListItems dell'oggetto ListControl (formato) per ListEntry elemento ListItem ListControl (formato) per ListItems per elenco (Format) ItemSelectionCondition elemento Control per ListItem per elemento dell'oggetto ListControl (formato) ScriptBlock ItemSelectionCondition per ListControl (formato)</span><span class="sxs-lookup"><span data-stu-id="f8ce7-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) ListControl Element (Format) ListEntries Element for ListControl (Format) ListEntry Element for ListEntries for ListControl (Format) ListItems Element for ListEntry for ListControl (Format) ListItem Element for ListItems for List Control (Format) ItemSelectionCondition Element for ListItem for ListControl (Format) ScriptBlock Element for ItemSelectionCondition for ListControl  (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="f8ce7-107">Sintassi</span><span class="sxs-lookup"><span data-stu-id="f8ce7-107">Syntax</span></span>

```xml
<ScriptBlock>ScriptToEvaluate</ScriptBlock>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="f8ce7-108">Attributi ed elementi</span><span class="sxs-lookup"><span data-stu-id="f8ce7-108">Attributes and Elements</span></span>

<span data-ttu-id="f8ce7-109">Le sezioni seguenti descrivono gli attributi, elementi figlio e gli elementi padre del `ScriptBlock` elemento.</span><span class="sxs-lookup"><span data-stu-id="f8ce7-109">The following sections describe attributes, child elements, and the parent elements of the `ScriptBlock` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="f8ce7-110">Attributes</span><span class="sxs-lookup"><span data-stu-id="f8ce7-110">Attributes</span></span>

<span data-ttu-id="f8ce7-111">Nessuna.</span><span class="sxs-lookup"><span data-stu-id="f8ce7-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="f8ce7-112">Elementi figlio</span><span class="sxs-lookup"><span data-stu-id="f8ce7-112">Child Elements</span></span>

<span data-ttu-id="f8ce7-113">Nessuna.</span><span class="sxs-lookup"><span data-stu-id="f8ce7-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="f8ce7-114">Elementi padre</span><span class="sxs-lookup"><span data-stu-id="f8ce7-114">Parent Elements</span></span>

|<span data-ttu-id="f8ce7-115">Elemento</span><span class="sxs-lookup"><span data-stu-id="f8ce7-115">Element</span></span>|<span data-ttu-id="f8ce7-116">Description</span><span class="sxs-lookup"><span data-stu-id="f8ce7-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="f8ce7-117">Elemento ItemSelectionCondition per ListItem per ListControl (formato)</span><span class="sxs-lookup"><span data-stu-id="f8ce7-117">ItemSelectionCondition Element for ListItem for ListControl (Format)</span></span>](./itemselectioncondition-element-for-listitem-for-listcontrol-format.md)|<span data-ttu-id="f8ce7-118">Definisce la condizione che deve essere presente per questo elemento di elenco da utilizzare.</span><span class="sxs-lookup"><span data-stu-id="f8ce7-118">Defines the condition that must exist for this list item to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="f8ce7-119">Valore di testo</span><span class="sxs-lookup"><span data-stu-id="f8ce7-119">Text Value</span></span>

<span data-ttu-id="f8ce7-120">Specificare lo script che viene valutato.</span><span class="sxs-lookup"><span data-stu-id="f8ce7-120">Specify the script that is evaluated.</span></span>

## <a name="remarks"></a><span data-ttu-id="f8ce7-121">Osservazioni</span><span class="sxs-lookup"><span data-stu-id="f8ce7-121">Remarks</span></span>

<span data-ttu-id="f8ce7-122">Se questo elemento viene usato, è possibile specificare il `PropertyName` elemento quando si definisce la condizione di selezione.</span><span class="sxs-lookup"><span data-stu-id="f8ce7-122">If this element is used, you cannot specify the `PropertyName` element when defining the selection condition.</span></span>

## <a name="see-also"></a><span data-ttu-id="f8ce7-123">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="f8ce7-123">See Also</span></span>

[<span data-ttu-id="f8ce7-124">La scrittura di un File di formattazione di PowerShell</span><span class="sxs-lookup"><span data-stu-id="f8ce7-124">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
