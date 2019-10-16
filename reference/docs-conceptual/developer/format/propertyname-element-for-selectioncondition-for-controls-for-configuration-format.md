---
title: Elemento PropertyName per SelectionCondition per i controlli per la configurazione (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ec048408-e1c6-41ef-b39b-72f4c2dcf2ac
caps.latest.revision: 6
ms.openlocfilehash: b4b2440fdb7171d09fdc16ac7cc4f25ed1a4bb78
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/15/2019
ms.locfileid: "72362400"
---
# <a name="propertyname-element-for-selectioncondition-for-controls-for-configuration-format"></a><span data-ttu-id="4902e-102">Elemento PropertyName per SelectionCondition per Controls per Configuration (formato)</span><span class="sxs-lookup"><span data-stu-id="4902e-102">PropertyName Element for SelectionCondition for Controls for Configuration (Format)</span></span>

<span data-ttu-id="4902e-103">Specifica la proprietà .NET che attiva la condizione.</span><span class="sxs-lookup"><span data-stu-id="4902e-103">Specifies the .NET property that triggers the condition.</span></span> <span data-ttu-id="4902e-104">Quando questa proprietà è presente o quando restituisce `true`, la condizione viene soddisfatta e viene usata la voce.</span><span class="sxs-lookup"><span data-stu-id="4902e-104">When this property is present or when it evaluates to `true`, the condition is met, and the entry is used.</span></span> <span data-ttu-id="4902e-105">Questo elemento viene usato quando si definisce un controllo comune che può essere usato da tutte le visualizzazioni nel file di formattazione.</span><span class="sxs-lookup"><span data-stu-id="4902e-105">This element is used when defining a common control that can be used by all the views in the formatting file.</span></span>

<span data-ttu-id="4902e-106">Elemento di configurazione (Format) controlla l'elemento dell'elemento di controllo Configuration (Format) per i controlli per la configurazione (Format) elemento CustomControl per il controllo per la configurazione (Format) elemento CustomEntries per CustomControl per la configurazione ( Format) elemento CustomEntry per CustomControl per i controlli per la configurazione (Format) elemento EntrySelectedBy per CustomEntry per i controlli per la configurazione (Format) SelectionCondition elemento per EntrySelectedBy per CustomEntry per la configurazione ( Format) elemento PropertyName per SelectionCondition per EntrySelectedBy per ListEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="4902e-106">Configuration Element (Format) Controls Element of Configuration (Format) Control Element for Controls for Configuration (Format) CustomControl Element for Control for Configuration (Format) CustomEntries Element for CustomControl for Configuration (Format) CustomEntry Element for CustomControl for Controls for Configuration (Format) EntrySelectedBy Element for CustomEntry for Controls for Configuration (Format) SelectionCondition Element for EntrySelectedBy for CustomEntry for Configuration (Format) PropertyName Element for SelectionCondition for EntrySelectedBy for ListEntry (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="4902e-107">Sintassi</span><span class="sxs-lookup"><span data-stu-id="4902e-107">Syntax</span></span>

```xml
<PropertyName>.NetTypeProperty</PropertyName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="4902e-108">Attributi ed elementi</span><span class="sxs-lookup"><span data-stu-id="4902e-108">Attributes and Elements</span></span>

<span data-ttu-id="4902e-109">Nelle sezioni seguenti vengono descritti gli attributi, gli elementi figlio e l'elemento padre dell'elemento `PropertyName`.</span><span class="sxs-lookup"><span data-stu-id="4902e-109">The following sections describe attributes, child elements, and the parent element of the `PropertyName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="4902e-110">Attributi</span><span class="sxs-lookup"><span data-stu-id="4902e-110">Attributes</span></span>

<span data-ttu-id="4902e-111">Nessuna.</span><span class="sxs-lookup"><span data-stu-id="4902e-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="4902e-112">Elementi figlio</span><span class="sxs-lookup"><span data-stu-id="4902e-112">Child Elements</span></span>

<span data-ttu-id="4902e-113">Nessuna.</span><span class="sxs-lookup"><span data-stu-id="4902e-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="4902e-114">Elementi padre</span><span class="sxs-lookup"><span data-stu-id="4902e-114">Parent Elements</span></span>

|<span data-ttu-id="4902e-115">Elemento</span><span class="sxs-lookup"><span data-stu-id="4902e-115">Element</span></span>|<span data-ttu-id="4902e-116">Description</span><span class="sxs-lookup"><span data-stu-id="4902e-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="4902e-117">Elemento SelectionCondition per EntrySelectedBy per i controlli per la configurazione (Format)</span><span class="sxs-lookup"><span data-stu-id="4902e-117">SelectionCondition Element for EntrySelectedBy for Controls for Configuration (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-controls-for-configuration-format.md)|<span data-ttu-id="4902e-118">Definisce una condizione che deve esistere per la definizione di un controllo comune da utilizzare.</span><span class="sxs-lookup"><span data-stu-id="4902e-118">Defines a condition that must exist for a common control definition to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="4902e-119">Valore di testo</span><span class="sxs-lookup"><span data-stu-id="4902e-119">Text Value</span></span>

<span data-ttu-id="4902e-120">Specificare il nome della proprietà .NET.</span><span class="sxs-lookup"><span data-stu-id="4902e-120">Specify the .NET property name.</span></span>

## <a name="remarks"></a><span data-ttu-id="4902e-121">Osservazioni</span><span class="sxs-lookup"><span data-stu-id="4902e-121">Remarks</span></span>

<span data-ttu-id="4902e-122">La condizione di selezione deve specificare almeno un nome di proprietà o uno script, ma non è possibile specificarli entrambi.</span><span class="sxs-lookup"><span data-stu-id="4902e-122">The selection condition must specify a least one property name or a script, but cannot specify both.</span></span> <span data-ttu-id="4902e-123">Per ulteriori informazioni sul modo in cui è possibile utilizzare le condizioni di selezione, vedere [definizione delle condizioni per la visualizzazione dei dati](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="4902e-123">For more information about how selection conditions can be used, see [Defining Conditions for Displaying Data](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="4902e-124">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="4902e-124">See Also</span></span>

[<span data-ttu-id="4902e-125">Elemento SelectionCondition per EntrySelectedBy per i controlli per la configurazione (Format)</span><span class="sxs-lookup"><span data-stu-id="4902e-125">SelectionCondition Element for EntrySelectedBy for Controls for Configuration (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-controls-for-configuration-format.md)

[<span data-ttu-id="4902e-126">Scrittura di un file di formattazione di PowerShell</span><span class="sxs-lookup"><span data-stu-id="4902e-126">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
