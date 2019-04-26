---
title: Elemento ScriptBlock per SelectionCondition per i controlli per la configurazione (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: bb032dfc-9ef6-403c-b557-5858617e3483
caps.latest.revision: 6
ms.openlocfilehash: 102987970152420896a0c986f0973280ae209623
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62064425"
---
# <a name="scriptblock-element-for-selectioncondition-for-controls-for-configuration-format"></a><span data-ttu-id="f6867-102">Elemento ScriptBlock per SelectionCondition per Controls per Configuration (formato)</span><span class="sxs-lookup"><span data-stu-id="f6867-102">ScriptBlock Element for SelectionCondition for Controls for Configuration (Format)</span></span>

<span data-ttu-id="f6867-103">Specifica lo script che genera la condizione.</span><span class="sxs-lookup"><span data-stu-id="f6867-103">Specifies the script that triggers the condition.</span></span> <span data-ttu-id="f6867-104">Quando questo script viene valutato per `true`, viene soddisfatta la condizione e viene utilizzata la definizione.</span><span class="sxs-lookup"><span data-stu-id="f6867-104">When this script is evaluated to `true`, the condition is met, and the definition is used.</span></span> <span data-ttu-id="f6867-105">Questo elemento viene usato quando si definisce un controllo comune che può essere usato da tutte le visualizzazioni nel file di formattazione.</span><span class="sxs-lookup"><span data-stu-id="f6867-105">This element is used when defining a common control that can be used by all the views in the formatting file.</span></span>

<span data-ttu-id="f6867-106">Configurazione (formato) i controlli elemento di configurazione (formato) elemento di controllo per i controlli di configurazione (formato) CustomControl elemento per il controllo per elemento di configurazione (formato) CustomEntries per CustomControl per Configuration ( Elemento CustomEntry Format) per CustomControl per i controlli per elemento di configurazione (formato) EntrySelectedBy per CustomEntry per i controlli per elemento di configurazione (formato) SelectionCondition per EntrySelectedBy per i controlli per la configurazione (formato) Elemento ScriptBlock per SelectionCondition per i controlli per la configurazione (formato)</span><span class="sxs-lookup"><span data-stu-id="f6867-106">Configuration Element (Format) Controls Element of Configuration (Format) Control Element for Controls for Configuration (Format) CustomControl Element for Control for Configuration (Format) CustomEntries Element for CustomControl for Configuration (Format) CustomEntry Element for CustomControl for Controls for Configuration (Format) EntrySelectedBy Element for CustomEntry for Controls for Configuration (Format) SelectionCondition Element for EntrySelectedBy for Controls for Configuration (Format) ScriptBlock Element for SelectionCondition for Controls for Configuration (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="f6867-107">Sintassi</span><span class="sxs-lookup"><span data-stu-id="f6867-107">Syntax</span></span>

```xml
<ScriptBlock>ScriptToEvaluate</ScriptBlock>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="f6867-108">Elementi e attributi</span><span class="sxs-lookup"><span data-stu-id="f6867-108">Attributes and Elements</span></span>

<span data-ttu-id="f6867-109">Le sezioni seguenti descrivono gli attributi e gli elementi figlio dell'elemento padre del `ScriptBlock` elemento.</span><span class="sxs-lookup"><span data-stu-id="f6867-109">The following sections describe attributes, child elements, and the parent element of the `ScriptBlock` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="f6867-110">Attributes</span><span class="sxs-lookup"><span data-stu-id="f6867-110">Attributes</span></span>

<span data-ttu-id="f6867-111">Nessuna.</span><span class="sxs-lookup"><span data-stu-id="f6867-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="f6867-112">Elementi figlio</span><span class="sxs-lookup"><span data-stu-id="f6867-112">Child Elements</span></span>

<span data-ttu-id="f6867-113">Nessuna.</span><span class="sxs-lookup"><span data-stu-id="f6867-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="f6867-114">Elementi padre</span><span class="sxs-lookup"><span data-stu-id="f6867-114">Parent Elements</span></span>

|<span data-ttu-id="f6867-115">Elemento</span><span class="sxs-lookup"><span data-stu-id="f6867-115">Element</span></span>|<span data-ttu-id="f6867-116">Description</span><span class="sxs-lookup"><span data-stu-id="f6867-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="f6867-117">Elemento SelectionCondition per EntrySelectedBy per i controlli per la configurazione (formato)</span><span class="sxs-lookup"><span data-stu-id="f6867-117">SelectionCondition Element for EntrySelectedBy for Controls for Configuration (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-controls-for-configuration-format.md)|<span data-ttu-id="f6867-118">Definisce una condizione che deve essere presente per la definizione di controllo comuni da usare.</span><span class="sxs-lookup"><span data-stu-id="f6867-118">Defines a condition that must exist for the common control definition to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="f6867-119">Valore di testo</span><span class="sxs-lookup"><span data-stu-id="f6867-119">Text Value</span></span>

<span data-ttu-id="f6867-120">Specificare lo script che viene valutato.</span><span class="sxs-lookup"><span data-stu-id="f6867-120">Specify the script that is evaluated.</span></span>

## <a name="remarks"></a><span data-ttu-id="f6867-121">Osservazioni</span><span class="sxs-lookup"><span data-stu-id="f6867-121">Remarks</span></span>

<span data-ttu-id="f6867-122">La condizione di selezione è necessario specificare un nome di script o proprietà uno minimi per valutare, ma non è possibile specificare entrambi.</span><span class="sxs-lookup"><span data-stu-id="f6867-122">The selection condition must specify a least one script or property name to evaluate, but cannot specify both.</span></span> <span data-ttu-id="f6867-123">Per altre informazioni sull'utilizzo di condizioni di selezione, vedere [che definisce le condizioni per la visualizzazione dei dati](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="f6867-123">For more information about how selection conditions can be used, see [Defining Conditions for Displaying Data](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="f6867-124">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="f6867-124">See Also</span></span>

[<span data-ttu-id="f6867-125">Elemento SelectionCondition per EntrySelectedBy per i controlli per la configurazione (formato)</span><span class="sxs-lookup"><span data-stu-id="f6867-125">SelectionCondition Element for EntrySelectedBy for Controls for Configuration (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-controls-for-configuration-format.md)

[<span data-ttu-id="f6867-126">La scrittura di un File di formattazione di PowerShell</span><span class="sxs-lookup"><span data-stu-id="f6867-126">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
