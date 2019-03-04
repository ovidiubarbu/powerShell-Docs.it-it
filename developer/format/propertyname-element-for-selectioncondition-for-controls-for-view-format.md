---
title: Elemento PropertyName per SelectionCondition per i controlli per la visualizzazione (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 92c4237d-c2b2-4908-82ac-f36070f89d26
caps.latest.revision: 6
ms.openlocfilehash: 79859bed3d762948182e03babf71d4270278bae7
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/03/2019
ms.locfileid: "56853527"
---
# <a name="propertyname-element-for-selectioncondition-for-controls-for-view-format"></a><span data-ttu-id="c3f39-102">Elemento PropertyName per SelectionCondition per Controls per View (formato)</span><span class="sxs-lookup"><span data-stu-id="c3f39-102">PropertyName Element for SelectionCondition for Controls for View (Format)</span></span>

<span data-ttu-id="c3f39-103">Specifica la proprietà .NET che attiva la condizione.</span><span class="sxs-lookup"><span data-stu-id="c3f39-103">Specifies the .NET property that triggers the condition.</span></span> <span data-ttu-id="c3f39-104">Quando questa proprietà è presente o quando viene restituito `true`, viene soddisfatta la condizione e la voce viene usata.</span><span class="sxs-lookup"><span data-stu-id="c3f39-104">When this property is present or when it evaluates to `true`, the condition is met, and the entry is used.</span></span> <span data-ttu-id="c3f39-105">Questo elemento viene usato quando si definiscono i controlli che possono essere usati da una vista.</span><span class="sxs-lookup"><span data-stu-id="c3f39-105">This element is used when defining controls that can be used by a view.</span></span>

<span data-ttu-id="c3f39-106">Elemento (formato) elemento ViewDefinitions (formato) visualizzazione elemento (formato) i controlli elemento (formato) controllo elemento di configurazione per i controlli elemento di visualizzazione (formato) CustomControl per il controllo per i controlli elemento di visualizzazione (formato) CustomEntries per CustomControl per i controlli elemento di visualizzazione (formato) CustomEntry per CustomEntries per i controlli elemento di visualizzazione (formato) EntrySelectedBy per CustomEntry per i controlli elemento di visualizzazione (formato) SelectionCondition per EntrySelectedBy per i controlli per la visualizzazione ( Elemento PropertyName Format) per SelectionCondition per i controlli per la visualizzazione (formato)</span><span class="sxs-lookup"><span data-stu-id="c3f39-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) Controls Element (Format) Control Element for Controls for View (Format) CustomControl Element for Control for Controls for View (Format) CustomEntries Element for CustomControl for Controls for View (Format) CustomEntry Element for CustomEntries for Controls for View (Format) EntrySelectedBy Element for CustomEntry for Controls for View (Format) SelectionCondition Element for EntrySelectedBy for Controls for View (Format) PropertyName Element for SelectionCondition for Controls for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="c3f39-107">Sintassi</span><span class="sxs-lookup"><span data-stu-id="c3f39-107">Syntax</span></span>

```xml
<PropertyName>.NetTypeProperty</PropertyName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="c3f39-108">Attributi ed elementi</span><span class="sxs-lookup"><span data-stu-id="c3f39-108">Attributes and Elements</span></span>

<span data-ttu-id="c3f39-109">Le sezioni seguenti descrivono gli attributi e gli elementi figlio dell'elemento padre del `PropertyName` elemento.</span><span class="sxs-lookup"><span data-stu-id="c3f39-109">The following sections describe attributes, child elements, and the parent element of the `PropertyName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="c3f39-110">Attributes</span><span class="sxs-lookup"><span data-stu-id="c3f39-110">Attributes</span></span>

<span data-ttu-id="c3f39-111">Nessuna.</span><span class="sxs-lookup"><span data-stu-id="c3f39-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="c3f39-112">Elementi figlio</span><span class="sxs-lookup"><span data-stu-id="c3f39-112">Child Elements</span></span>

<span data-ttu-id="c3f39-113">Nessuna.</span><span class="sxs-lookup"><span data-stu-id="c3f39-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="c3f39-114">Elementi padre</span><span class="sxs-lookup"><span data-stu-id="c3f39-114">Parent Elements</span></span>

|<span data-ttu-id="c3f39-115">Elemento</span><span class="sxs-lookup"><span data-stu-id="c3f39-115">Element</span></span>|<span data-ttu-id="c3f39-116">Description</span><span class="sxs-lookup"><span data-stu-id="c3f39-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="c3f39-117">Elemento SelectionCondition per EntrySelectedBy per i controlli per la visualizzazione (formato)</span><span class="sxs-lookup"><span data-stu-id="c3f39-117">SelectionCondition Element for EntrySelectedBy for Controls for View (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-controls-for-view-format.md)|<span data-ttu-id="c3f39-118">Definisce una condizione che deve essere presente per la definizione di controllo da utilizzare.</span><span class="sxs-lookup"><span data-stu-id="c3f39-118">Defines a condition that must exist for the control definition to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="c3f39-119">Valore di testo</span><span class="sxs-lookup"><span data-stu-id="c3f39-119">Text Value</span></span>

<span data-ttu-id="c3f39-120">Specificare il nome della proprietà .NET.</span><span class="sxs-lookup"><span data-stu-id="c3f39-120">Specify the .NET property name.</span></span>

## <a name="remarks"></a><span data-ttu-id="c3f39-121">Osservazioni</span><span class="sxs-lookup"><span data-stu-id="c3f39-121">Remarks</span></span>

<span data-ttu-id="c3f39-122">La condizione di selezione è necessario specificare un nome di una proprietà minimi o uno script, ma non è possibile specificare entrambi.</span><span class="sxs-lookup"><span data-stu-id="c3f39-122">The selection condition must specify a least one property name or a script, but cannot specify both.</span></span> <span data-ttu-id="c3f39-123">Per altre informazioni sull'utilizzo di condizioni di selezione, vedere [che definisce le condizioni per la visualizzazione dei dati](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="c3f39-123">For more information about how selection conditions can be used, see [Defining Conditions for Displaying Data](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="c3f39-124">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="c3f39-124">See Also</span></span>

[<span data-ttu-id="c3f39-125">Elemento SelectionCondition per EntrySelectedBy per i controlli per la visualizzazione (formato)</span><span class="sxs-lookup"><span data-stu-id="c3f39-125">SelectionCondition Element for EntrySelectedBy for Controls for View (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-controls-for-view-format.md)

[<span data-ttu-id="c3f39-126">La scrittura di un File di formattazione di PowerShell</span><span class="sxs-lookup"><span data-stu-id="c3f39-126">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
