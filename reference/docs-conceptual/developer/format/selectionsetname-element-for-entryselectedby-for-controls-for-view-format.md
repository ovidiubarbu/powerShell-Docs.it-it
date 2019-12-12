---
title: Elemento SelectionSetName per EntrySelectedBy per i controlli per la visualizzazione (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: b594a064-746f-4900-99e4-7be7bf5aa5a2
caps.latest.revision: 7
ms.openlocfilehash: d540c99707f4e0796b2d408f2161a9208257ab32
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/05/2019
ms.locfileid: "72368350"
---
# <a name="selectionsetname-element-for-entryselectedby-for-controls-for-view-format"></a><span data-ttu-id="00779-102">Elemento SelectionSetName per EntrySelectedBy per Controls per View (formato)</span><span class="sxs-lookup"><span data-stu-id="00779-102">SelectionSetName Element for EntrySelectedBy for Controls for View (Format)</span></span>

<span data-ttu-id="00779-103">Specifica un set di tipi .NET che utilizzano questa definizione del controllo.</span><span class="sxs-lookup"><span data-stu-id="00779-103">Specifies a set of .NET types that use this definition of the control.</span></span> <span data-ttu-id="00779-104">Questo elemento viene utilizzato per la definizione di controlli che possono essere utilizzati da una visualizzazione.</span><span class="sxs-lookup"><span data-stu-id="00779-104">This element is used when defining controls that can be used by a view.</span></span>

<span data-ttu-id="00779-105">Elemento di configurazione (Format) elemento ViewDefinitions (Format) elemento di visualizzazione (Format) controlli elemento (Format) elemento di controllo per i controlli per la visualizzazione (formato) elemento CustomControl per il controllo per i controlli per la visualizzazione (formato) elemento CustomEntries per CustomControl per i controlli per la visualizzazione (formato) elemento CustomEntry per CustomEntries per i controlli per la visualizzazione (formato) EntrySelectedBy elemento per CustomEntry per i controlli per la visualizzazione (formato) SelectionSetName elemento per EntrySelectedBy per i controlli per la visualizzazione ( Formato</span><span class="sxs-lookup"><span data-stu-id="00779-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) Controls Element (Format) Control Element for Controls for View (Format) CustomControl Element for Control for Controls for View (Format) CustomEntries Element for CustomControl for Controls for View (Format) CustomEntry Element for CustomEntries for Controls for View (Format) EntrySelectedBy Element for CustomEntry for Controls for View (Format) SelectionSetName Element for EntrySelectedBy for Controls for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="00779-106">Sintassi</span><span class="sxs-lookup"><span data-stu-id="00779-106">Syntax</span></span>

```xml
<SelectionSetName>NameofSelectionSet</SelectionSetName>

```

## <a name="attributes-and-elements"></a><span data-ttu-id="00779-107">Attributi ed elementi</span><span class="sxs-lookup"><span data-stu-id="00779-107">Attributes and Elements</span></span>

<span data-ttu-id="00779-108">Nelle sezioni seguenti vengono descritti gli attributi, gli elementi figlio e l'elemento padre dell'elemento `SelectionSetName`.</span><span class="sxs-lookup"><span data-stu-id="00779-108">The following sections describe attributes, child elements, and the parent element of the `SelectionSetName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="00779-109">Attributi</span><span class="sxs-lookup"><span data-stu-id="00779-109">Attributes</span></span>

<span data-ttu-id="00779-110">Nessuno</span><span class="sxs-lookup"><span data-stu-id="00779-110">None</span></span>

### <a name="child-elements"></a><span data-ttu-id="00779-111">Elementi figlio</span><span class="sxs-lookup"><span data-stu-id="00779-111">Child Elements</span></span>

<span data-ttu-id="00779-112">Nessuna.</span><span class="sxs-lookup"><span data-stu-id="00779-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="00779-113">Elementi padre</span><span class="sxs-lookup"><span data-stu-id="00779-113">Parent Elements</span></span>

|<span data-ttu-id="00779-114">Elemento</span><span class="sxs-lookup"><span data-stu-id="00779-114">Element</span></span>|<span data-ttu-id="00779-115">Description</span><span class="sxs-lookup"><span data-stu-id="00779-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="00779-116">Elemento EntrySelectedBy per CustomEntry per i controlli per la visualizzazione (Format)</span><span class="sxs-lookup"><span data-stu-id="00779-116">EntrySelectedBy Element for CustomEntry for Controls for View (Format)</span></span>](./entryselectedby-element-for-customentry-for-controls-for-view-format.md)|<span data-ttu-id="00779-117">Definisce i tipi .NET che utilizzano questa definizione di controllo o la condizione che deve esistere affinché questa definizione venga utilizzata.</span><span class="sxs-lookup"><span data-stu-id="00779-117">Defines the .NET types that use this control definition or the condition that must exist for this definition to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="00779-118">Valore testo</span><span class="sxs-lookup"><span data-stu-id="00779-118">Text Value</span></span>

<span data-ttu-id="00779-119">Consente di specificare il nome del set di selezione.</span><span class="sxs-lookup"><span data-stu-id="00779-119">Specify the name of the selection set.</span></span>

## <a name="remarks"></a><span data-ttu-id="00779-120">Osservazioni</span><span class="sxs-lookup"><span data-stu-id="00779-120">Remarks</span></span>

<span data-ttu-id="00779-121">Per ogni definizione di controllo deve essere definito almeno un nome di tipo, un set di selezione o una condizione di selezione.</span><span class="sxs-lookup"><span data-stu-id="00779-121">Each control definition must have at least one type name, selection set, or selection condition defined.</span></span>

<span data-ttu-id="00779-122">I set di selezione vengono in genere utilizzati quando si desidera definire un gruppo di oggetti utilizzati in più viste.</span><span class="sxs-lookup"><span data-stu-id="00779-122">Selection sets are typically used when you want to define a group of objects that are used in multiple views.</span></span> <span data-ttu-id="00779-123">Per ulteriori informazioni sulla definizione di set di selezione, vedere [definizione di set di selezione](./defining-selection-sets.md).</span><span class="sxs-lookup"><span data-stu-id="00779-123">For more information about defining selection sets, see [Defining Selection Sets](./defining-selection-sets.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="00779-124">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="00779-124">See Also</span></span>

[<span data-ttu-id="00779-125">Elemento EntrySelectedBy per CustomEntry per i controlli per la visualizzazione (Format)</span><span class="sxs-lookup"><span data-stu-id="00779-125">EntrySelectedBy Element for CustomEntry for Controls for View (Format)</span></span>](./entryselectedby-element-for-customentry-for-controls-for-view-format.md)

[<span data-ttu-id="00779-126">Scrittura di un file di formattazione di PowerShell</span><span class="sxs-lookup"><span data-stu-id="00779-126">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
