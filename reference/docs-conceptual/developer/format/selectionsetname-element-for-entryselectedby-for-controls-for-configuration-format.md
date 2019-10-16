---
title: Elemento SelectionSetName per EntrySelectedBy per i controlli per la configurazione (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 42143d1e-7cda-4c4a-b568-fa1951bb9417
caps.latest.revision: 6
ms.openlocfilehash: 9060ee54d6f88c7f910b16cf5c9b87f37844b736
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/15/2019
ms.locfileid: "72364790"
---
# <a name="selectionsetname-element-for-entryselectedby-for-controls-for-configuration-format"></a><span data-ttu-id="e527b-102">Elemento SelectionSetName per EntrySelectedBy per Controls per Configuration (formato)</span><span class="sxs-lookup"><span data-stu-id="e527b-102">SelectionSetName Element for EntrySelectedBy for Controls for Configuration (Format)</span></span>

<span data-ttu-id="e527b-103">Specifica un set di tipi .NET che utilizzano questa definizione del controllo.</span><span class="sxs-lookup"><span data-stu-id="e527b-103">Specifies a set of .NET types that use this definition of the control.</span></span> <span data-ttu-id="e527b-104">Questo elemento viene usato quando si definisce un controllo comune che può essere usato da tutte le visualizzazioni nel file di formattazione.</span><span class="sxs-lookup"><span data-stu-id="e527b-104">This element is used when defining a common control that can be used by all the views in the formatting file.</span></span>

<span data-ttu-id="e527b-105">Elemento di configurazione (Format) controlla l'elemento dell'elemento di controllo Configuration (Format) per i controlli per la configurazione (Format) elemento CustomControl per il controllo per la configurazione (Format) elemento CustomEntries per CustomControl per la configurazione ( Format) elemento CustomEntry per CustomControl per i controlli per la configurazione (Format) elemento EntrySelectedBy per CustomEntry per i controlli per la configurazione (Format) SelectionSetName elemento per EntrySelectedBy per i controlli per la configurazione (Format)</span><span class="sxs-lookup"><span data-stu-id="e527b-105">Configuration Element (Format) Controls Element of Configuration (Format) Control Element for Controls for Configuration (Format) CustomControl Element for Control for Configuration (Format) CustomEntries Element for CustomControl for Configuration (Format) CustomEntry Element for CustomControl for Controls for Configuration (Format) EntrySelectedBy Element for CustomEntry for Controls for Configuration (Format) SelectionSetName Element for EntrySelectedBy for Controls for Configuration (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="e527b-106">Sintassi</span><span class="sxs-lookup"><span data-stu-id="e527b-106">Syntax</span></span>

```xml
<SelectionSetName>NameofSelectionSet</SelectionSetName>

```

## <a name="attributes-and-elements"></a><span data-ttu-id="e527b-107">Attributi ed elementi</span><span class="sxs-lookup"><span data-stu-id="e527b-107">Attributes and Elements</span></span>

<span data-ttu-id="e527b-108">Nelle sezioni seguenti vengono descritti gli attributi, gli elementi figlio e l'elemento padre dell'elemento `SelectionSetName`.</span><span class="sxs-lookup"><span data-stu-id="e527b-108">The following sections describe attributes, child elements, and the parent element of the `SelectionSetName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="e527b-109">Attributi</span><span class="sxs-lookup"><span data-stu-id="e527b-109">Attributes</span></span>

<span data-ttu-id="e527b-110">Nessuno</span><span class="sxs-lookup"><span data-stu-id="e527b-110">None</span></span>

### <a name="child-elements"></a><span data-ttu-id="e527b-111">Elementi figlio</span><span class="sxs-lookup"><span data-stu-id="e527b-111">Child Elements</span></span>

<span data-ttu-id="e527b-112">Nessuna.</span><span class="sxs-lookup"><span data-stu-id="e527b-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="e527b-113">Elementi padre</span><span class="sxs-lookup"><span data-stu-id="e527b-113">Parent Elements</span></span>

|<span data-ttu-id="e527b-114">Elemento</span><span class="sxs-lookup"><span data-stu-id="e527b-114">Element</span></span>|<span data-ttu-id="e527b-115">Description</span><span class="sxs-lookup"><span data-stu-id="e527b-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="e527b-116">Elemento EntrySelectedBy per CustomEntry per i controlli per la configurazione (Format)</span><span class="sxs-lookup"><span data-stu-id="e527b-116">EntrySelectedBy Element for CustomEntry for Controls for Configuration (Format)</span></span>](./entryselectedby-element-for-customentry-for-controls-for-configuration-format.md)|<span data-ttu-id="e527b-117">Definisce i tipi .NET che utilizzano questa definizione di controllo o la condizione che deve esistere affinché questa definizione venga utilizzata.</span><span class="sxs-lookup"><span data-stu-id="e527b-117">Defines the .NET types that use this control definition or the condition that must exist for this definition to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="e527b-118">Valore di testo</span><span class="sxs-lookup"><span data-stu-id="e527b-118">Text Value</span></span>

<span data-ttu-id="e527b-119">Consente di specificare il nome del set di selezione.</span><span class="sxs-lookup"><span data-stu-id="e527b-119">Specify the name of the selection set.</span></span>

## <a name="remarks"></a><span data-ttu-id="e527b-120">Osservazioni</span><span class="sxs-lookup"><span data-stu-id="e527b-120">Remarks</span></span>

<span data-ttu-id="e527b-121">Per ogni definizione di controllo deve essere definito almeno un nome di tipo, un set di selezione o una condizione di selezione.</span><span class="sxs-lookup"><span data-stu-id="e527b-121">Each control definition must have at least one type name, selection set, or selection condition defined.</span></span>

<span data-ttu-id="e527b-122">I set di selezione vengono in genere utilizzati quando si desidera definire un gruppo di oggetti utilizzati in più viste.</span><span class="sxs-lookup"><span data-stu-id="e527b-122">Selection sets are typically used when you want to define a group of objects that are used in multiple views.</span></span> <span data-ttu-id="e527b-123">Per ulteriori informazioni sulla definizione di set di selezione, vedere [definizione di set di selezione](./defining-selection-sets.md).</span><span class="sxs-lookup"><span data-stu-id="e527b-123">For more information about defining selection sets, see [Defining Selection Sets](./defining-selection-sets.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="e527b-124">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="e527b-124">See Also</span></span>

[<span data-ttu-id="e527b-125">Elemento EntrySelectedBy per CustomEntry per i controlli per la configurazione (Format)</span><span class="sxs-lookup"><span data-stu-id="e527b-125">EntrySelectedBy Element for CustomEntry for Controls for Configuration (Format)</span></span>](./entryselectedby-element-for-customentry-for-controls-for-configuration-format.md)

[<span data-ttu-id="e527b-126">Scrittura di un file di formattazione di PowerShell</span><span class="sxs-lookup"><span data-stu-id="e527b-126">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
