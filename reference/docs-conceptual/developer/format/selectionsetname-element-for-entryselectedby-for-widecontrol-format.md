---
title: Elemento SelectionSetName per EntrySelectedBy per WideControl (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: c9c6e18f-6cca-465c-bd20-3969e7897a96
caps.latest.revision: 10
ms.openlocfilehash: 6b6a4a4647412d11d947f1dc4ea12d1e05ff536e
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/05/2019
ms.locfileid: "72361980"
---
# <a name="selectionsetname-element-for-entryselectedby-for-widecontrol-format"></a><span data-ttu-id="90e0e-102">Elemento SelectionSetName per EntrySelectedBy per WideControl (formato)</span><span class="sxs-lookup"><span data-stu-id="90e0e-102">SelectionSetName Element for EntrySelectedBy for WideControl (Format)</span></span>

<span data-ttu-id="90e0e-103">Specifica un set di oggetti .NET per la definizione.</span><span class="sxs-lookup"><span data-stu-id="90e0e-103">Specifies a set of .NET objects for the definition.</span></span> <span data-ttu-id="90e0e-104">La definizione viene utilizzata ogni volta che viene visualizzato uno di questi oggetti.</span><span class="sxs-lookup"><span data-stu-id="90e0e-104">The definition is used whenever one of these objects is displayed.</span></span>

<span data-ttu-id="90e0e-105">Elemento Configuration (Format) elemento ViewDefinitions (Format) elemento View (Format) elemento WideControl (Format) elemento WideEntries (Format) elemento WideEntry (Format) elemento EntrySelectedBy per WideEntry (Format) SelectionSetName elemento per EntrySelectedBy per WideEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="90e0e-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) WideControl Element (Format) WideEntries Element (Format) WideEntry Element (Format) EntrySelectedBy Element for WideEntry (Format) SelectionSetName Element for EntrySelectedBy for WideEntry (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="90e0e-106">Sintassi</span><span class="sxs-lookup"><span data-stu-id="90e0e-106">Syntax</span></span>

```xml
<SelectionSetName>NameofSelectionSet</SelectionSetName>

```

## <a name="attributes-and-elements"></a><span data-ttu-id="90e0e-107">Attributi ed elementi</span><span class="sxs-lookup"><span data-stu-id="90e0e-107">Attributes and Elements</span></span>

<span data-ttu-id="90e0e-108">Nelle sezioni seguenti vengono descritti gli attributi, gli elementi figlio e l'elemento padre dell'elemento `SelectionSetName`.</span><span class="sxs-lookup"><span data-stu-id="90e0e-108">The following sections describe the attributes, child elements, and the parent element of the `SelectionSetName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="90e0e-109">Attributi</span><span class="sxs-lookup"><span data-stu-id="90e0e-109">Attributes</span></span>

<span data-ttu-id="90e0e-110">Nessuna.</span><span class="sxs-lookup"><span data-stu-id="90e0e-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="90e0e-111">Elementi figlio</span><span class="sxs-lookup"><span data-stu-id="90e0e-111">Child Elements</span></span>

<span data-ttu-id="90e0e-112">Nessuna.</span><span class="sxs-lookup"><span data-stu-id="90e0e-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="90e0e-113">Elementi padre</span><span class="sxs-lookup"><span data-stu-id="90e0e-113">Parent Elements</span></span>

|<span data-ttu-id="90e0e-114">Elemento</span><span class="sxs-lookup"><span data-stu-id="90e0e-114">Element</span></span>|<span data-ttu-id="90e0e-115">Description</span><span class="sxs-lookup"><span data-stu-id="90e0e-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="90e0e-116">Elemento EntrySelectedBy per WideEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="90e0e-116">EntrySelectedBy Element for WideEntry (Format)</span></span>](./entryselectedby-element-for-wideentry-format.md)|<span data-ttu-id="90e0e-117">Definisce i tipi .NET che utilizzano questa voce estesa o la condizione che deve esistere affinché questa voce venga utilizzata.</span><span class="sxs-lookup"><span data-stu-id="90e0e-117">Defines the .NET types that use this wide entry or the condition that must exist for this entry to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="90e0e-118">Valore testo</span><span class="sxs-lookup"><span data-stu-id="90e0e-118">Text Value</span></span>

<span data-ttu-id="90e0e-119">Consente di specificare il nome del set di selezione.</span><span class="sxs-lookup"><span data-stu-id="90e0e-119">Specify the name of the selection set.</span></span>

## <a name="remarks"></a><span data-ttu-id="90e0e-120">Osservazioni</span><span class="sxs-lookup"><span data-stu-id="90e0e-120">Remarks</span></span>

<span data-ttu-id="90e0e-121">Ogni definizione deve specificare un nome di tipo, un set di selezione o una condizione di selezione.</span><span class="sxs-lookup"><span data-stu-id="90e0e-121">Each definition must specify one type name, selection set, or selection condition.</span></span>

<span data-ttu-id="90e0e-122">I set di selezione vengono in genere utilizzati quando si desidera definire un gruppo di oggetti utilizzati in più viste.</span><span class="sxs-lookup"><span data-stu-id="90e0e-122">Selection sets are typically used when you want to define a group of objects that are used in multiple views.</span></span> <span data-ttu-id="90e0e-123">Ad esempio, potrebbe essere necessario creare una visualizzazione tabella e una visualizzazione elenco per lo stesso set di oggetti.</span><span class="sxs-lookup"><span data-stu-id="90e0e-123">For example, you might want to create a table view and a list view for the same set of objects.</span></span> <span data-ttu-id="90e0e-124">Per ulteriori informazioni sulla definizione di set di selezione, vedere [definizione di set di oggetti per una vista](./defining-selection-sets.md).</span><span class="sxs-lookup"><span data-stu-id="90e0e-124">For more information about defining selection sets, see [Defining Sets of Objects for a View](./defining-selection-sets.md).</span></span>

<span data-ttu-id="90e0e-125">Per ulteriori informazioni su altri componenti di una visualizzazione estesa, vedere [creazione di un'ampia visualizzazione](./creating-a-wide-view.md).</span><span class="sxs-lookup"><span data-stu-id="90e0e-125">For more information about other components of a wide view, see [Creating a Wide View](./creating-a-wide-view.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="90e0e-126">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="90e0e-126">See Also</span></span>

[<span data-ttu-id="90e0e-127">Creazione di una visualizzazione estesa</span><span class="sxs-lookup"><span data-stu-id="90e0e-127">Creating a Wide View</span></span>](./creating-a-wide-view.md)

[<span data-ttu-id="90e0e-128">Definizione di set di selezione</span><span class="sxs-lookup"><span data-stu-id="90e0e-128">Defining Selection Sets</span></span>](./defining-selection-sets.md)

[<span data-ttu-id="90e0e-129">Elemento EntrySelectedBy per WideEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="90e0e-129">EntrySelectedBy Element for WideEntry (Format)</span></span>](./entryselectedby-element-for-wideentry-format.md)

[<span data-ttu-id="90e0e-130">Scrittura di un file di formattazione di PowerShell</span><span class="sxs-lookup"><span data-stu-id="90e0e-130">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
