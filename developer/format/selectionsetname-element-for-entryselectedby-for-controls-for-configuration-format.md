---
title: Elemento SelectionSetName per EntrySelectedBy per i controlli per la configurazione (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 42143d1e-7cda-4c4a-b568-fa1951bb9417
caps.latest.revision: 6
ms.openlocfilehash: 9060ee54d6f88c7f910b16cf5c9b87f37844b736
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/03/2019
ms.locfileid: "56860907"
---
# <a name="selectionsetname-element-for-entryselectedby-for-controls-for-configuration-format"></a><span data-ttu-id="9a7f0-102">Elemento SelectionSetName per EntrySelectedBy per Controls per Configuration (formato)</span><span class="sxs-lookup"><span data-stu-id="9a7f0-102">SelectionSetName Element for EntrySelectedBy for Controls for Configuration (Format)</span></span>

<span data-ttu-id="9a7f0-103">Specifica un set di tipi .NET che usano questa definizione del controllo.</span><span class="sxs-lookup"><span data-stu-id="9a7f0-103">Specifies a set of .NET types that use this definition of the control.</span></span> <span data-ttu-id="9a7f0-104">Questo elemento viene usato quando si definisce un controllo comune che può essere usato da tutte le visualizzazioni nel file di formattazione.</span><span class="sxs-lookup"><span data-stu-id="9a7f0-104">This element is used when defining a common control that can be used by all the views in the formatting file.</span></span>

<span data-ttu-id="9a7f0-105">Configurazione (formato) i controlli elemento di configurazione (formato) elemento di controllo per i controlli di configurazione (formato) CustomControl elemento per il controllo per elemento di configurazione (formato) CustomEntries per CustomControl per Configuration ( Elemento CustomEntry Format) per CustomControl per i controlli per elemento di configurazione (formato) EntrySelectedBy per CustomEntry per i controlli per elemento di configurazione (formato) SelectionSetName per EntrySelectedBy per i controlli per la configurazione (formato)</span><span class="sxs-lookup"><span data-stu-id="9a7f0-105">Configuration Element (Format) Controls Element of Configuration (Format) Control Element for Controls for Configuration (Format) CustomControl Element for Control for Configuration (Format) CustomEntries Element for CustomControl for Configuration (Format) CustomEntry Element for CustomControl for Controls for Configuration (Format) EntrySelectedBy Element for CustomEntry for Controls for Configuration (Format) SelectionSetName Element for EntrySelectedBy for Controls for Configuration (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="9a7f0-106">Sintassi</span><span class="sxs-lookup"><span data-stu-id="9a7f0-106">Syntax</span></span>

```xml
<SelectionSetName>NameofSelectionSet</SelectionSetName>

```

## <a name="attributes-and-elements"></a><span data-ttu-id="9a7f0-107">Attributi ed elementi</span><span class="sxs-lookup"><span data-stu-id="9a7f0-107">Attributes and Elements</span></span>

<span data-ttu-id="9a7f0-108">Le sezioni seguenti descrivono gli attributi e gli elementi figlio dell'elemento padre del `SelectionSetName` elemento.</span><span class="sxs-lookup"><span data-stu-id="9a7f0-108">The following sections describe attributes, child elements, and the parent element of the `SelectionSetName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="9a7f0-109">Attributes</span><span class="sxs-lookup"><span data-stu-id="9a7f0-109">Attributes</span></span>

<span data-ttu-id="9a7f0-110">Nessuno</span><span class="sxs-lookup"><span data-stu-id="9a7f0-110">None</span></span>

### <a name="child-elements"></a><span data-ttu-id="9a7f0-111">Elementi figlio</span><span class="sxs-lookup"><span data-stu-id="9a7f0-111">Child Elements</span></span>

<span data-ttu-id="9a7f0-112">Nessuna.</span><span class="sxs-lookup"><span data-stu-id="9a7f0-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="9a7f0-113">Elementi padre</span><span class="sxs-lookup"><span data-stu-id="9a7f0-113">Parent Elements</span></span>

|<span data-ttu-id="9a7f0-114">Elemento</span><span class="sxs-lookup"><span data-stu-id="9a7f0-114">Element</span></span>|<span data-ttu-id="9a7f0-115">Description</span><span class="sxs-lookup"><span data-stu-id="9a7f0-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="9a7f0-116">Elemento EntrySelectedBy per CustomEntry per i controlli per la configurazione (formato)</span><span class="sxs-lookup"><span data-stu-id="9a7f0-116">EntrySelectedBy Element for CustomEntry for Controls for Configuration (Format)</span></span>](./entryselectedby-element-for-customentry-for-controls-for-configuration-format.md)|<span data-ttu-id="9a7f0-117">Definisce i tipi .NET che usano questa definizione di controllo o la condizione che deve essere presente per questa definizione da usare.</span><span class="sxs-lookup"><span data-stu-id="9a7f0-117">Defines the .NET types that use this control definition or the condition that must exist for this definition to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="9a7f0-118">Valore di testo</span><span class="sxs-lookup"><span data-stu-id="9a7f0-118">Text Value</span></span>

<span data-ttu-id="9a7f0-119">Specificare il nome del set di selezione.</span><span class="sxs-lookup"><span data-stu-id="9a7f0-119">Specify the name of the selection set.</span></span>

## <a name="remarks"></a><span data-ttu-id="9a7f0-120">Osservazioni</span><span class="sxs-lookup"><span data-stu-id="9a7f0-120">Remarks</span></span>

<span data-ttu-id="9a7f0-121">Ogni definizione di controllo deve avere almeno un nome di tipo, il set di selezione o condizione di selezione definiti.</span><span class="sxs-lookup"><span data-stu-id="9a7f0-121">Each control definition must have at least one type name, selection set, or selection condition defined.</span></span>

<span data-ttu-id="9a7f0-122">Set di selezione vengono usati quando si desidera definire un gruppo di oggetti utilizzati in più viste.</span><span class="sxs-lookup"><span data-stu-id="9a7f0-122">Selection sets are typically used when you want to define a group of objects that are used in multiple views.</span></span> <span data-ttu-id="9a7f0-123">Per altre informazioni sulla definizione di set di selezione, vedere [definizione di selezione imposta](./defining-selection-sets.md).</span><span class="sxs-lookup"><span data-stu-id="9a7f0-123">For more information about defining selection sets, see [Defining Selection Sets](./defining-selection-sets.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="9a7f0-124">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="9a7f0-124">See Also</span></span>

[<span data-ttu-id="9a7f0-125">Elemento EntrySelectedBy per CustomEntry per i controlli per la configurazione (formato)</span><span class="sxs-lookup"><span data-stu-id="9a7f0-125">EntrySelectedBy Element for CustomEntry for Controls for Configuration (Format)</span></span>](./entryselectedby-element-for-customentry-for-controls-for-configuration-format.md)

[<span data-ttu-id="9a7f0-126">La scrittura di un File di formattazione di PowerShell</span><span class="sxs-lookup"><span data-stu-id="9a7f0-126">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
