---
title: Elemento SelectionSetName per EntrySelectedBy per EnumerableExpansion (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 936d09f2-2c48-49e8-ab2d-0c8729199a2e
caps.latest.revision: 8
ms.openlocfilehash: 8ba8931ea5e34f610878351396cad42023393ad6
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/15/2019
ms.locfileid: "72368330"
---
# <a name="selectionsetname-element-for-entryselectedby-for-enumerableexpansion-format"></a><span data-ttu-id="1de20-102">Elemento SelectionSetName per EntrySelectedBy per EnumerableExpansion (formato)</span><span class="sxs-lookup"><span data-stu-id="1de20-102">SelectionSetName Element for EntrySelectedBy for EnumerableExpansion (Format)</span></span>

<span data-ttu-id="1de20-103">Specifica il set di tipi .NET espansi da questa definizione.</span><span class="sxs-lookup"><span data-stu-id="1de20-103">Specifies the set of .NET types that are expanded by this definition.</span></span>

<span data-ttu-id="1de20-104">Elemento Configuration (Format) elemento DefaultSettings (Format) elemento EnumerableExpansions (Format) elemento EnumerableExpansion (Format) elemento EntrySelectedBy per EnumerableExpansion (Format) SelectionSetName elemento per EntrySelectedBy per EnumerableExpansion (formato)</span><span class="sxs-lookup"><span data-stu-id="1de20-104">Configuration Element (Format) DefaultSettings Element (Format) EnumerableExpansions Element (Format) EnumerableExpansion Element (Format) EntrySelectedBy Element for EnumerableExpansion (Format) SelectionSetName Element for EntrySelectedBy for EnumerableExpansion (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="1de20-105">Sintassi</span><span class="sxs-lookup"><span data-stu-id="1de20-105">Syntax</span></span>

```xml
<SelectionSetName>NameofSelectionSet</SelectionSetName>

```

## <a name="attributes-and-elements"></a><span data-ttu-id="1de20-106">Attributi ed elementi</span><span class="sxs-lookup"><span data-stu-id="1de20-106">Attributes and Elements</span></span>

<span data-ttu-id="1de20-107">Nelle sezioni seguenti vengono descritti gli attributi, gli elementi figlio e l'elemento padre dell'elemento `SelectionSetName`.</span><span class="sxs-lookup"><span data-stu-id="1de20-107">The following sections describe attributes, child elements, and the parent element of the `SelectionSetName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="1de20-108">Attributi</span><span class="sxs-lookup"><span data-stu-id="1de20-108">Attributes</span></span>

<span data-ttu-id="1de20-109">Nessuna.</span><span class="sxs-lookup"><span data-stu-id="1de20-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="1de20-110">Elementi figlio</span><span class="sxs-lookup"><span data-stu-id="1de20-110">Child Elements</span></span>

<span data-ttu-id="1de20-111">Nessuna.</span><span class="sxs-lookup"><span data-stu-id="1de20-111">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="1de20-112">Elementi padre</span><span class="sxs-lookup"><span data-stu-id="1de20-112">Parent Elements</span></span>

|<span data-ttu-id="1de20-113">Elemento</span><span class="sxs-lookup"><span data-stu-id="1de20-113">Element</span></span>|<span data-ttu-id="1de20-114">Description</span><span class="sxs-lookup"><span data-stu-id="1de20-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="1de20-115">Elemento EntrySelectedBy per EnumerableExpansion (Format)</span><span class="sxs-lookup"><span data-stu-id="1de20-115">EntrySelectedBy Element for EnumerableExpansion (Format)</span></span>](./entryselectedby-element-for-enumerableexpansion-format.md)|<span data-ttu-id="1de20-116">Definisce gli oggetti della raccolta .NET espansi da questa definizione.</span><span class="sxs-lookup"><span data-stu-id="1de20-116">Defines the .NET collection objects that are expanded by this definition.</span></span>|

## <a name="text-value"></a><span data-ttu-id="1de20-117">Valore di testo</span><span class="sxs-lookup"><span data-stu-id="1de20-117">Text Value</span></span>

<span data-ttu-id="1de20-118">Consente di specificare il nome del set di selezione.</span><span class="sxs-lookup"><span data-stu-id="1de20-118">Specify the name of the selection set.</span></span>

## <a name="remarks"></a><span data-ttu-id="1de20-119">Osservazioni</span><span class="sxs-lookup"><span data-stu-id="1de20-119">Remarks</span></span>

<span data-ttu-id="1de20-120">Ogni definizione deve specificare uno o più nomi di tipo, un set di selezione o una condizione di selezione.</span><span class="sxs-lookup"><span data-stu-id="1de20-120">Each definition must specify one or more type names, a selection set, or a selection condition.</span></span>

<span data-ttu-id="1de20-121">I set di selezione vengono in genere utilizzati quando si desidera definire un gruppo di oggetti utilizzati in più viste.</span><span class="sxs-lookup"><span data-stu-id="1de20-121">Selection sets are typically used when you want to define a group of objects that are used in multiple views.</span></span> <span data-ttu-id="1de20-122">Ad esempio, potrebbe essere necessario creare una visualizzazione tabella e una visualizzazione elenco per lo stesso set di oggetti.</span><span class="sxs-lookup"><span data-stu-id="1de20-122">For example, you might want to create a table view and a list view for the same set of objects.</span></span> <span data-ttu-id="1de20-123">Per ulteriori informazioni sulla definizione di set di selezione, vedere [definizione di set di oggetti per una vista](./defining-selection-sets.md).</span><span class="sxs-lookup"><span data-stu-id="1de20-123">For more information about defining selection sets, see [Defining Sets of Objects for a View](./defining-selection-sets.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="1de20-124">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="1de20-124">See Also</span></span>

[<span data-ttu-id="1de20-125">Definizione di set di selezione</span><span class="sxs-lookup"><span data-stu-id="1de20-125">Defining Selection Sets</span></span>](./defining-selection-sets.md)

[<span data-ttu-id="1de20-126">Elemento EntrySelectedBy per EnumerableExpansion (Format)</span><span class="sxs-lookup"><span data-stu-id="1de20-126">EntrySelectedBy Element for EnumerableExpansion (Format)</span></span>](./entryselectedby-element-for-enumerableexpansion-format.md)

[<span data-ttu-id="1de20-127">Scrittura di un file di formattazione di PowerShell</span><span class="sxs-lookup"><span data-stu-id="1de20-127">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
