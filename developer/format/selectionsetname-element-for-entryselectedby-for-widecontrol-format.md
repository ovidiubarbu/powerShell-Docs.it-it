---
title: Elemento SelectionSetName per EntrySelectedBy per WideControl (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: c9c6e18f-6cca-465c-bd20-3969e7897a96
caps.latest.revision: 10
ms.openlocfilehash: 6b6a4a4647412d11d947f1dc4ea12d1e05ff536e
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62064029"
---
# <a name="selectionsetname-element-for-entryselectedby-for-widecontrol-format"></a><span data-ttu-id="bdb3f-102">Elemento SelectionSetName per EntrySelectedBy per WideControl (formato)</span><span class="sxs-lookup"><span data-stu-id="bdb3f-102">SelectionSetName Element for EntrySelectedBy for WideControl (Format)</span></span>

<span data-ttu-id="bdb3f-103">Specifica un set di oggetti .NET per la definizione.</span><span class="sxs-lookup"><span data-stu-id="bdb3f-103">Specifies a set of .NET objects for the definition.</span></span> <span data-ttu-id="bdb3f-104">La definizione viene utilizzata ogni volta che viene visualizzato uno di questi oggetti.</span><span class="sxs-lookup"><span data-stu-id="bdb3f-104">The definition is used whenever one of these objects is displayed.</span></span>

<span data-ttu-id="bdb3f-105">Elemento (formato) elemento ViewDefinitions (formato) visualizzazione elemento (formato) elemento WideControl (formato) elemento WideEntries (formato) elemento WideEntry (formato) EntrySelectedBy elemento di configurazione per elemento SelectionSetName WideEntry (formato) per EntrySelectedBy per WideEntry (formato)</span><span class="sxs-lookup"><span data-stu-id="bdb3f-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) WideControl Element (Format) WideEntries Element (Format) WideEntry Element (Format) EntrySelectedBy Element for WideEntry (Format) SelectionSetName Element for EntrySelectedBy for WideEntry (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="bdb3f-106">Sintassi</span><span class="sxs-lookup"><span data-stu-id="bdb3f-106">Syntax</span></span>

```xml
<SelectionSetName>NameofSelectionSet</SelectionSetName>

```

## <a name="attributes-and-elements"></a><span data-ttu-id="bdb3f-107">Elementi e attributi</span><span class="sxs-lookup"><span data-stu-id="bdb3f-107">Attributes and Elements</span></span>

<span data-ttu-id="bdb3f-108">Le sezioni seguenti descrivono gli attributi e gli elementi figlio dell'elemento padre del `SelectionSetName` elemento.</span><span class="sxs-lookup"><span data-stu-id="bdb3f-108">The following sections describe the attributes, child elements, and the parent element of the `SelectionSetName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="bdb3f-109">Attributes</span><span class="sxs-lookup"><span data-stu-id="bdb3f-109">Attributes</span></span>

<span data-ttu-id="bdb3f-110">Nessuna.</span><span class="sxs-lookup"><span data-stu-id="bdb3f-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="bdb3f-111">Elementi figlio</span><span class="sxs-lookup"><span data-stu-id="bdb3f-111">Child Elements</span></span>

<span data-ttu-id="bdb3f-112">Nessuna.</span><span class="sxs-lookup"><span data-stu-id="bdb3f-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="bdb3f-113">Elementi padre</span><span class="sxs-lookup"><span data-stu-id="bdb3f-113">Parent Elements</span></span>

|<span data-ttu-id="bdb3f-114">Elemento</span><span class="sxs-lookup"><span data-stu-id="bdb3f-114">Element</span></span>|<span data-ttu-id="bdb3f-115">Description</span><span class="sxs-lookup"><span data-stu-id="bdb3f-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="bdb3f-116">Elemento EntrySelectedBy per WideEntry (formato)</span><span class="sxs-lookup"><span data-stu-id="bdb3f-116">EntrySelectedBy Element for WideEntry (Format)</span></span>](./entryselectedby-element-for-wideentry-format.md)|<span data-ttu-id="bdb3f-117">Definisce i tipi .NET che usano questa voce ampia o la condizione che deve essere presente per questa voce da usare.</span><span class="sxs-lookup"><span data-stu-id="bdb3f-117">Defines the .NET types that use this wide entry or the condition that must exist for this entry to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="bdb3f-118">Valore di testo</span><span class="sxs-lookup"><span data-stu-id="bdb3f-118">Text Value</span></span>

<span data-ttu-id="bdb3f-119">Specificare il nome del set di selezione.</span><span class="sxs-lookup"><span data-stu-id="bdb3f-119">Specify the name of the selection set.</span></span>

## <a name="remarks"></a><span data-ttu-id="bdb3f-120">Osservazioni</span><span class="sxs-lookup"><span data-stu-id="bdb3f-120">Remarks</span></span>

<span data-ttu-id="bdb3f-121">Ogni definizione deve specificare un nome del tipo, il set di selezione o condizione di selezione.</span><span class="sxs-lookup"><span data-stu-id="bdb3f-121">Each definition must specify one type name, selection set, or selection condition.</span></span>

<span data-ttu-id="bdb3f-122">Set di selezione vengono usati quando si desidera definire un gruppo di oggetti utilizzati in più viste.</span><span class="sxs-lookup"><span data-stu-id="bdb3f-122">Selection sets are typically used when you want to define a group of objects that are used in multiple views.</span></span> <span data-ttu-id="bdb3f-123">Ad esempio, è possibile creare una visualizzazione tabella e una visualizzazione elenco per lo stesso set di oggetti.</span><span class="sxs-lookup"><span data-stu-id="bdb3f-123">For example, you might want to create a table view and a list view for the same set of objects.</span></span> <span data-ttu-id="bdb3f-124">Per altre informazioni sulla definizione di set di selezione, vedere [definizione imposta di oggetti per una visualizzazione](./defining-selection-sets.md).</span><span class="sxs-lookup"><span data-stu-id="bdb3f-124">For more information about defining selection sets, see [Defining Sets of Objects for a View](./defining-selection-sets.md).</span></span>

<span data-ttu-id="bdb3f-125">Per altre informazioni sugli altri componenti di una visualizzazione più ampia, vedere [creazione di una visualizzazione più ampia](./creating-a-wide-view.md).</span><span class="sxs-lookup"><span data-stu-id="bdb3f-125">For more information about other components of a wide view, see [Creating a Wide View](./creating-a-wide-view.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="bdb3f-126">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="bdb3f-126">See Also</span></span>

[<span data-ttu-id="bdb3f-127">Creazione di una visualizzazione più ampia</span><span class="sxs-lookup"><span data-stu-id="bdb3f-127">Creating a Wide View</span></span>](./creating-a-wide-view.md)

[<span data-ttu-id="bdb3f-128">La definizione di set di selezione</span><span class="sxs-lookup"><span data-stu-id="bdb3f-128">Defining Selection Sets</span></span>](./defining-selection-sets.md)

[<span data-ttu-id="bdb3f-129">Elemento EntrySelectedBy per WideEntry (formato)</span><span class="sxs-lookup"><span data-stu-id="bdb3f-129">EntrySelectedBy Element for WideEntry (Format)</span></span>](./entryselectedby-element-for-wideentry-format.md)

[<span data-ttu-id="bdb3f-130">La scrittura di un File di formattazione di PowerShell</span><span class="sxs-lookup"><span data-stu-id="bdb3f-130">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
