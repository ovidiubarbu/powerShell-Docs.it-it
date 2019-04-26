---
title: Elemento SelectionSetName per EntrySelectedBy per i controlli per la visualizzazione (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: b594a064-746f-4900-99e4-7be7bf5aa5a2
caps.latest.revision: 7
ms.openlocfilehash: d540c99707f4e0796b2d408f2161a9208257ab32
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62075648"
---
# <a name="selectionsetname-element-for-entryselectedby-for-controls-for-view-format"></a><span data-ttu-id="d3d19-102">Elemento SelectionSetName per EntrySelectedBy per Controls per View (formato)</span><span class="sxs-lookup"><span data-stu-id="d3d19-102">SelectionSetName Element for EntrySelectedBy for Controls for View (Format)</span></span>

<span data-ttu-id="d3d19-103">Specifica un set di tipi .NET che usano questa definizione del controllo.</span><span class="sxs-lookup"><span data-stu-id="d3d19-103">Specifies a set of .NET types that use this definition of the control.</span></span> <span data-ttu-id="d3d19-104">Questo elemento viene usato quando si definiscono i controlli che possono essere usati da una vista.</span><span class="sxs-lookup"><span data-stu-id="d3d19-104">This element is used when defining controls that can be used by a view.</span></span>

<span data-ttu-id="d3d19-105">Elemento (formato) elemento ViewDefinitions (formato) visualizzazione elemento (formato) i controlli elemento (formato) controllo elemento di configurazione per i controlli elemento di visualizzazione (formato) CustomControl per il controllo per i controlli elemento di visualizzazione (formato) CustomEntries per CustomControl per i controlli elemento di visualizzazione (formato) CustomEntry per CustomEntries per i controlli elemento di visualizzazione (formato) EntrySelectedBy per CustomEntry per i controlli elemento di visualizzazione (formato) SelectionSetName per EntrySelectedBy per i controlli per la visualizzazione ( Formato)</span><span class="sxs-lookup"><span data-stu-id="d3d19-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) Controls Element (Format) Control Element for Controls for View (Format) CustomControl Element for Control for Controls for View (Format) CustomEntries Element for CustomControl for Controls for View (Format) CustomEntry Element for CustomEntries for Controls for View (Format) EntrySelectedBy Element for CustomEntry for Controls for View (Format) SelectionSetName Element for EntrySelectedBy for Controls for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="d3d19-106">Sintassi</span><span class="sxs-lookup"><span data-stu-id="d3d19-106">Syntax</span></span>

```xml
<SelectionSetName>NameofSelectionSet</SelectionSetName>

```

## <a name="attributes-and-elements"></a><span data-ttu-id="d3d19-107">Elementi e attributi</span><span class="sxs-lookup"><span data-stu-id="d3d19-107">Attributes and Elements</span></span>

<span data-ttu-id="d3d19-108">Le sezioni seguenti descrivono gli attributi e gli elementi figlio dell'elemento padre del `SelectionSetName` elemento.</span><span class="sxs-lookup"><span data-stu-id="d3d19-108">The following sections describe attributes, child elements, and the parent element of the `SelectionSetName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="d3d19-109">Attributes</span><span class="sxs-lookup"><span data-stu-id="d3d19-109">Attributes</span></span>

<span data-ttu-id="d3d19-110">Nessuno</span><span class="sxs-lookup"><span data-stu-id="d3d19-110">None</span></span>

### <a name="child-elements"></a><span data-ttu-id="d3d19-111">Elementi figlio</span><span class="sxs-lookup"><span data-stu-id="d3d19-111">Child Elements</span></span>

<span data-ttu-id="d3d19-112">Nessuna.</span><span class="sxs-lookup"><span data-stu-id="d3d19-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="d3d19-113">Elementi padre</span><span class="sxs-lookup"><span data-stu-id="d3d19-113">Parent Elements</span></span>

|<span data-ttu-id="d3d19-114">Elemento</span><span class="sxs-lookup"><span data-stu-id="d3d19-114">Element</span></span>|<span data-ttu-id="d3d19-115">Description</span><span class="sxs-lookup"><span data-stu-id="d3d19-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="d3d19-116">Elemento EntrySelectedBy per CustomEntry per i controlli per la visualizzazione (formato)</span><span class="sxs-lookup"><span data-stu-id="d3d19-116">EntrySelectedBy Element for CustomEntry for Controls for View (Format)</span></span>](./entryselectedby-element-for-customentry-for-controls-for-view-format.md)|<span data-ttu-id="d3d19-117">Definisce i tipi .NET che usano questa definizione di controllo o la condizione che deve essere presente per questa definizione da usare.</span><span class="sxs-lookup"><span data-stu-id="d3d19-117">Defines the .NET types that use this control definition or the condition that must exist for this definition to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="d3d19-118">Valore di testo</span><span class="sxs-lookup"><span data-stu-id="d3d19-118">Text Value</span></span>

<span data-ttu-id="d3d19-119">Specificare il nome del set di selezione.</span><span class="sxs-lookup"><span data-stu-id="d3d19-119">Specify the name of the selection set.</span></span>

## <a name="remarks"></a><span data-ttu-id="d3d19-120">Osservazioni</span><span class="sxs-lookup"><span data-stu-id="d3d19-120">Remarks</span></span>

<span data-ttu-id="d3d19-121">Ogni definizione di controllo deve avere almeno un nome di tipo, il set di selezione o condizione di selezione definiti.</span><span class="sxs-lookup"><span data-stu-id="d3d19-121">Each control definition must have at least one type name, selection set, or selection condition defined.</span></span>

<span data-ttu-id="d3d19-122">Set di selezione vengono usati quando si desidera definire un gruppo di oggetti utilizzati in più viste.</span><span class="sxs-lookup"><span data-stu-id="d3d19-122">Selection sets are typically used when you want to define a group of objects that are used in multiple views.</span></span> <span data-ttu-id="d3d19-123">Per altre informazioni sulla definizione di set di selezione, vedere [definizione di selezione imposta](./defining-selection-sets.md).</span><span class="sxs-lookup"><span data-stu-id="d3d19-123">For more information about defining selection sets, see [Defining Selection Sets](./defining-selection-sets.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="d3d19-124">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="d3d19-124">See Also</span></span>

[<span data-ttu-id="d3d19-125">Elemento EntrySelectedBy per CustomEntry per i controlli per la visualizzazione (formato)</span><span class="sxs-lookup"><span data-stu-id="d3d19-125">EntrySelectedBy Element for CustomEntry for Controls for View (Format)</span></span>](./entryselectedby-element-for-customentry-for-controls-for-view-format.md)

[<span data-ttu-id="d3d19-126">La scrittura di un File di formattazione di PowerShell</span><span class="sxs-lookup"><span data-stu-id="d3d19-126">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
