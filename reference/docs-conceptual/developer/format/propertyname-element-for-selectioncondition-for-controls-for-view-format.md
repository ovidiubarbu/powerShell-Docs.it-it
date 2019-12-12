---
title: Elemento PropertyName per SelectionCondition per i controlli per la visualizzazione (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 92c4237d-c2b2-4908-82ac-f36070f89d26
caps.latest.revision: 6
ms.openlocfilehash: 79859bed3d762948182e03babf71d4270278bae7
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/05/2019
ms.locfileid: "72362360"
---
# <a name="propertyname-element-for-selectioncondition-for-controls-for-view-format"></a><span data-ttu-id="311b6-102">Elemento PropertyName per SelectionCondition per Controls per View (formato)</span><span class="sxs-lookup"><span data-stu-id="311b6-102">PropertyName Element for SelectionCondition for Controls for View (Format)</span></span>

<span data-ttu-id="311b6-103">Specifica la proprietà .NET che attiva la condizione.</span><span class="sxs-lookup"><span data-stu-id="311b6-103">Specifies the .NET property that triggers the condition.</span></span> <span data-ttu-id="311b6-104">Quando questa proprietà è presente o quando restituisce `true`, la condizione viene soddisfatta e viene usata la voce.</span><span class="sxs-lookup"><span data-stu-id="311b6-104">When this property is present or when it evaluates to `true`, the condition is met, and the entry is used.</span></span> <span data-ttu-id="311b6-105">Questo elemento viene utilizzato per la definizione di controlli che possono essere utilizzati da una visualizzazione.</span><span class="sxs-lookup"><span data-stu-id="311b6-105">This element is used when defining controls that can be used by a view.</span></span>

<span data-ttu-id="311b6-106">Elemento di configurazione (Format) elemento ViewDefinitions (Format) elemento di visualizzazione (Format) controlli elemento (Format) elemento di controllo per i controlli per la visualizzazione (formato) elemento CustomControl per il controllo per i controlli per la visualizzazione (formato) elemento CustomEntries per CustomControl per i controlli per la visualizzazione (formato) elemento CustomEntry per CustomEntries per i controlli per la visualizzazione (formato) EntrySelectedBy elemento per CustomEntry per i controlli per la visualizzazione (formato) SelectionCondition elemento per EntrySelectedBy per i controlli per la visualizzazione ( Format) elemento PropertyName per SelectionCondition per i controlli per la visualizzazione (Format)</span><span class="sxs-lookup"><span data-stu-id="311b6-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) Controls Element (Format) Control Element for Controls for View (Format) CustomControl Element for Control for Controls for View (Format) CustomEntries Element for CustomControl for Controls for View (Format) CustomEntry Element for CustomEntries for Controls for View (Format) EntrySelectedBy Element for CustomEntry for Controls for View (Format) SelectionCondition Element for EntrySelectedBy for Controls for View (Format) PropertyName Element for SelectionCondition for Controls for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="311b6-107">Sintassi</span><span class="sxs-lookup"><span data-stu-id="311b6-107">Syntax</span></span>

```xml
<PropertyName>.NetTypeProperty</PropertyName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="311b6-108">Attributi ed elementi</span><span class="sxs-lookup"><span data-stu-id="311b6-108">Attributes and Elements</span></span>

<span data-ttu-id="311b6-109">Nelle sezioni seguenti vengono descritti gli attributi, gli elementi figlio e l'elemento padre dell'elemento `PropertyName`.</span><span class="sxs-lookup"><span data-stu-id="311b6-109">The following sections describe attributes, child elements, and the parent element of the `PropertyName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="311b6-110">Attributi</span><span class="sxs-lookup"><span data-stu-id="311b6-110">Attributes</span></span>

<span data-ttu-id="311b6-111">Nessuna.</span><span class="sxs-lookup"><span data-stu-id="311b6-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="311b6-112">Elementi figlio</span><span class="sxs-lookup"><span data-stu-id="311b6-112">Child Elements</span></span>

<span data-ttu-id="311b6-113">Nessuna.</span><span class="sxs-lookup"><span data-stu-id="311b6-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="311b6-114">Elementi padre</span><span class="sxs-lookup"><span data-stu-id="311b6-114">Parent Elements</span></span>

|<span data-ttu-id="311b6-115">Elemento</span><span class="sxs-lookup"><span data-stu-id="311b6-115">Element</span></span>|<span data-ttu-id="311b6-116">Description</span><span class="sxs-lookup"><span data-stu-id="311b6-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="311b6-117">Elemento SelectionCondition per EntrySelectedBy per i controlli per la visualizzazione (Format)</span><span class="sxs-lookup"><span data-stu-id="311b6-117">SelectionCondition Element for EntrySelectedBy for Controls for View (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-controls-for-view-format.md)|<span data-ttu-id="311b6-118">Definisce una condizione che deve esistere per la definizione del controllo da utilizzare.</span><span class="sxs-lookup"><span data-stu-id="311b6-118">Defines a condition that must exist for the control definition to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="311b6-119">Valore testo</span><span class="sxs-lookup"><span data-stu-id="311b6-119">Text Value</span></span>

<span data-ttu-id="311b6-120">Specificare il nome della proprietà .NET.</span><span class="sxs-lookup"><span data-stu-id="311b6-120">Specify the .NET property name.</span></span>

## <a name="remarks"></a><span data-ttu-id="311b6-121">Osservazioni</span><span class="sxs-lookup"><span data-stu-id="311b6-121">Remarks</span></span>

<span data-ttu-id="311b6-122">La condizione di selezione deve specificare almeno un nome di proprietà o uno script, ma non è possibile specificarli entrambi.</span><span class="sxs-lookup"><span data-stu-id="311b6-122">The selection condition must specify a least one property name or a script, but cannot specify both.</span></span> <span data-ttu-id="311b6-123">Per ulteriori informazioni sul modo in cui è possibile utilizzare le condizioni di selezione, vedere [definizione delle condizioni per la visualizzazione dei dati](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="311b6-123">For more information about how selection conditions can be used, see [Defining Conditions for Displaying Data](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="311b6-124">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="311b6-124">See Also</span></span>

[<span data-ttu-id="311b6-125">Elemento SelectionCondition per EntrySelectedBy per i controlli per la visualizzazione (Format)</span><span class="sxs-lookup"><span data-stu-id="311b6-125">SelectionCondition Element for EntrySelectedBy for Controls for View (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-controls-for-view-format.md)

[<span data-ttu-id="311b6-126">Scrittura di un file di formattazione di PowerShell</span><span class="sxs-lookup"><span data-stu-id="311b6-126">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
