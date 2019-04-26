---
title: Elemento PropertyName per SelectionCondition per i controlli per la configurazione (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ec048408-e1c6-41ef-b39b-72f4c2dcf2ac
caps.latest.revision: 6
ms.openlocfilehash: b4b2440fdb7171d09fdc16ac7cc4f25ed1a4bb78
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62064728"
---
# <a name="propertyname-element-for-selectioncondition-for-controls-for-configuration-format"></a><span data-ttu-id="19925-102">Elemento PropertyName per SelectionCondition per Controls per Configuration (formato)</span><span class="sxs-lookup"><span data-stu-id="19925-102">PropertyName Element for SelectionCondition for Controls for Configuration (Format)</span></span>

<span data-ttu-id="19925-103">Specifica la proprietà .NET che attiva la condizione.</span><span class="sxs-lookup"><span data-stu-id="19925-103">Specifies the .NET property that triggers the condition.</span></span> <span data-ttu-id="19925-104">Quando questa proprietà è presente o quando viene restituito `true`, viene soddisfatta la condizione e la voce viene usata.</span><span class="sxs-lookup"><span data-stu-id="19925-104">When this property is present or when it evaluates to `true`, the condition is met, and the entry is used.</span></span> <span data-ttu-id="19925-105">Questo elemento viene usato quando si definisce un controllo comune che può essere usato da tutte le visualizzazioni nel file di formattazione.</span><span class="sxs-lookup"><span data-stu-id="19925-105">This element is used when defining a common control that can be used by all the views in the formatting file.</span></span>

<span data-ttu-id="19925-106">Configurazione (formato) i controlli elemento di configurazione (formato) elemento di controllo per i controlli di configurazione (formato) CustomControl elemento per il controllo per elemento di configurazione (formato) CustomEntries per CustomControl per Configuration ( Elemento CustomEntry Format) per CustomControl per i controlli per CustomEntry per i controlli per elemento di configurazione (formato) SelectionCondition per EntrySelectedBy per CustomEntry per Configuration (configurazione (formato) EntrySelectedBy elemento Elemento PropertyName Format) per SelectionCondition per EntrySelectedBy per ListEntry (formato)</span><span class="sxs-lookup"><span data-stu-id="19925-106">Configuration Element (Format) Controls Element of Configuration (Format) Control Element for Controls for Configuration (Format) CustomControl Element for Control for Configuration (Format) CustomEntries Element for CustomControl for Configuration (Format) CustomEntry Element for CustomControl for Controls for Configuration (Format) EntrySelectedBy Element for CustomEntry for Controls for Configuration (Format) SelectionCondition Element for EntrySelectedBy for CustomEntry for Configuration (Format) PropertyName Element for SelectionCondition for EntrySelectedBy for ListEntry (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="19925-107">Sintassi</span><span class="sxs-lookup"><span data-stu-id="19925-107">Syntax</span></span>

```xml
<PropertyName>.NetTypeProperty</PropertyName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="19925-108">Elementi e attributi</span><span class="sxs-lookup"><span data-stu-id="19925-108">Attributes and Elements</span></span>

<span data-ttu-id="19925-109">Le sezioni seguenti descrivono gli attributi e gli elementi figlio dell'elemento padre del `PropertyName` elemento.</span><span class="sxs-lookup"><span data-stu-id="19925-109">The following sections describe attributes, child elements, and the parent element of the `PropertyName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="19925-110">Attributes</span><span class="sxs-lookup"><span data-stu-id="19925-110">Attributes</span></span>

<span data-ttu-id="19925-111">Nessuna.</span><span class="sxs-lookup"><span data-stu-id="19925-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="19925-112">Elementi figlio</span><span class="sxs-lookup"><span data-stu-id="19925-112">Child Elements</span></span>

<span data-ttu-id="19925-113">Nessuna.</span><span class="sxs-lookup"><span data-stu-id="19925-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="19925-114">Elementi padre</span><span class="sxs-lookup"><span data-stu-id="19925-114">Parent Elements</span></span>

|<span data-ttu-id="19925-115">Elemento</span><span class="sxs-lookup"><span data-stu-id="19925-115">Element</span></span>|<span data-ttu-id="19925-116">Description</span><span class="sxs-lookup"><span data-stu-id="19925-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="19925-117">Elemento SelectionCondition per EntrySelectedBy per i controlli per la configurazione (formato)</span><span class="sxs-lookup"><span data-stu-id="19925-117">SelectionCondition Element for EntrySelectedBy for Controls for Configuration (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-controls-for-configuration-format.md)|<span data-ttu-id="19925-118">Definisce una condizione che deve essere presente per la definizione di un controllo comune da usare.</span><span class="sxs-lookup"><span data-stu-id="19925-118">Defines a condition that must exist for a common control definition to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="19925-119">Valore di testo</span><span class="sxs-lookup"><span data-stu-id="19925-119">Text Value</span></span>

<span data-ttu-id="19925-120">Specificare il nome della proprietà .NET.</span><span class="sxs-lookup"><span data-stu-id="19925-120">Specify the .NET property name.</span></span>

## <a name="remarks"></a><span data-ttu-id="19925-121">Osservazioni</span><span class="sxs-lookup"><span data-stu-id="19925-121">Remarks</span></span>

<span data-ttu-id="19925-122">La condizione di selezione è necessario specificare un nome di una proprietà minimi o uno script, ma non è possibile specificare entrambi.</span><span class="sxs-lookup"><span data-stu-id="19925-122">The selection condition must specify a least one property name or a script, but cannot specify both.</span></span> <span data-ttu-id="19925-123">Per altre informazioni sull'utilizzo di condizioni di selezione, vedere [che definisce le condizioni per la visualizzazione dei dati](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="19925-123">For more information about how selection conditions can be used, see [Defining Conditions for Displaying Data](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="19925-124">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="19925-124">See Also</span></span>

[<span data-ttu-id="19925-125">Elemento SelectionCondition per EntrySelectedBy per i controlli per la configurazione (formato)</span><span class="sxs-lookup"><span data-stu-id="19925-125">SelectionCondition Element for EntrySelectedBy for Controls for Configuration (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-controls-for-configuration-format.md)

[<span data-ttu-id="19925-126">La scrittura di un File di formattazione di PowerShell</span><span class="sxs-lookup"><span data-stu-id="19925-126">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
