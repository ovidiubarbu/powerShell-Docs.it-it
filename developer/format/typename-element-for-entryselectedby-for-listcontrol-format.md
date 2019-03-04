---
title: Elemento TypeName per EntrySelectedBy per ListControl (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 33c7345c-b808-4c1e-bd54-cb870b407432
caps.latest.revision: 14
ms.openlocfilehash: 3f0c0ba1fe85d70557e67a30b3a9a59a33043475
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/03/2019
ms.locfileid: "56856107"
---
# <a name="typename-element-for-entryselectedby-for-listcontrol-format"></a><span data-ttu-id="85c46-102">Elemento TypeName per EntrySelectedBy per ListControl (formato)</span><span class="sxs-lookup"><span data-stu-id="85c46-102">TypeName Element for EntrySelectedBy for ListControl (Format)</span></span>

<span data-ttu-id="85c46-103">Specifica un tipo .NET che usa questa voce della visualizzazione elenco.</span><span class="sxs-lookup"><span data-stu-id="85c46-103">Specifies a .NET type that uses this entry of the list view.</span></span> <span data-ttu-id="85c46-104">Non sono previsti limiti al numero di tipi che possono essere specificati per una voce dell'elenco.</span><span class="sxs-lookup"><span data-stu-id="85c46-104">There is no limit to the number of types that can be specified for a list entry.</span></span>

<span data-ttu-id="85c46-105">Elemento (formato) elemento ViewDefinitions (formato) visualizzazione elemento (formato) elemento dell'oggetto ListControl (formato) elemento ListEntries (formato) elemento ListEntry (formato) EntrySelectedBy elemento di configurazione per elemento TypeName ListEntry (formato) per EntrySelectedBy per ListControl (formato)</span><span class="sxs-lookup"><span data-stu-id="85c46-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) ListControl Element (Format) ListEntries Element (Format) ListEntry Element (Format) EntrySelectedBy Element for ListEntry (Format) TypeName Element for EntrySelectedBy for ListControl (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="85c46-106">Sintassi</span><span class="sxs-lookup"><span data-stu-id="85c46-106">Syntax</span></span>

```xml
<TypeName>Nameof.NetType</TypeName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="85c46-107">Attributi ed elementi</span><span class="sxs-lookup"><span data-stu-id="85c46-107">Attributes and Elements</span></span>

<span data-ttu-id="85c46-108">Le sezioni seguenti descrivono gli attributi e gli elementi figlio dell'elemento padre del `TypeName` elemento.</span><span class="sxs-lookup"><span data-stu-id="85c46-108">The following sections describe attributes, child elements, and the parent element of the `TypeName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="85c46-109">Attributes</span><span class="sxs-lookup"><span data-stu-id="85c46-109">Attributes</span></span>

<span data-ttu-id="85c46-110">Nessuna.</span><span class="sxs-lookup"><span data-stu-id="85c46-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="85c46-111">Elementi figlio</span><span class="sxs-lookup"><span data-stu-id="85c46-111">Child Elements</span></span>

<span data-ttu-id="85c46-112">Nessuna.</span><span class="sxs-lookup"><span data-stu-id="85c46-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="85c46-113">Elementi padre</span><span class="sxs-lookup"><span data-stu-id="85c46-113">Parent Elements</span></span>

|<span data-ttu-id="85c46-114">Elemento</span><span class="sxs-lookup"><span data-stu-id="85c46-114">Element</span></span>|<span data-ttu-id="85c46-115">Description</span><span class="sxs-lookup"><span data-stu-id="85c46-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="85c46-116">Elemento EntrySelectedBy per ListEntry (formato)</span><span class="sxs-lookup"><span data-stu-id="85c46-116">EntrySelectedBy Element for ListEntry (Format)</span></span>](./entryselectedby-element-for-listentry-for-listcontrol-format.md)|<span data-ttu-id="85c46-117">Definisce i tipi .NET che usano questa voce di elenco o la condizione che deve essere presente per questa voce da usare.</span><span class="sxs-lookup"><span data-stu-id="85c46-117">Defines the .NET types that use this list entry or the condition that must exist for this entry to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="85c46-118">Valore di testo</span><span class="sxs-lookup"><span data-stu-id="85c46-118">Text Value</span></span>

<span data-ttu-id="85c46-119">Specificare il nome completo del tipo .NET, ad esempio `System.IO.DirectoryInfo`.</span><span class="sxs-lookup"><span data-stu-id="85c46-119">Specify the fully-qualified name of the .NET type, such as `System.IO.DirectoryInfo`.</span></span>

## <a name="remarks"></a><span data-ttu-id="85c46-120">Osservazioni</span><span class="sxs-lookup"><span data-stu-id="85c46-120">Remarks</span></span>

<span data-ttu-id="85c46-121">Ogni voce dell'elenco deve avere almeno un nome di tipo, il set di selezione o condizione di selezione definiti.</span><span class="sxs-lookup"><span data-stu-id="85c46-121">Each list entry must have at least one type name, selection set, or selection condition defined.</span></span>

<span data-ttu-id="85c46-122">Per altre informazioni sul modo in cui questo elemento viene usato in una visualizzazione elenco, vedere [visualizzazione elenco](./creating-a-list-view.md).</span><span class="sxs-lookup"><span data-stu-id="85c46-122">For more information about how this element is used in a list view, see [List View](./creating-a-list-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="85c46-123">Esempio</span><span class="sxs-lookup"><span data-stu-id="85c46-123">Example</span></span>

<span data-ttu-id="85c46-124">Nell'esempio seguente viene illustrato come specificare un insieme di una voce di una visualizzazione elenco di selezione.</span><span class="sxs-lookup"><span data-stu-id="85c46-124">The following example shows how to specify a selection set for an entry of a list view.</span></span>

```xml
<ListEntry>
  <EntrySelectedBy>
    <TypeName>Nameof.NetType</TypeName>
  </EntrySelectedBy>
  <ListItems>...</ListItems>
</ListEntry>
```

## <a name="see-also"></a><span data-ttu-id="85c46-125">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="85c46-125">See Also</span></span>

[<span data-ttu-id="85c46-126">Creazione di una visualizzazione elenco</span><span class="sxs-lookup"><span data-stu-id="85c46-126">Creating a List View</span></span>](./creating-a-list-view.md)

[<span data-ttu-id="85c46-127">Elemento EntrySelectedBy per ListEntry (formato)</span><span class="sxs-lookup"><span data-stu-id="85c46-127">EntrySelectedBy Element for ListEntry (Format)</span></span>](./entryselectedby-element-for-listentry-for-listcontrol-format.md)

[<span data-ttu-id="85c46-128">Elemento SelectionSetName per EnrtySelectedBy per ListEntry (formato)</span><span class="sxs-lookup"><span data-stu-id="85c46-128">SelectionSetName Element for EnrtySelectedBy for ListEntry (Format)</span></span>](./selectionsetname-element-for-entryselectedby-for-listcontrol-format.md)

[<span data-ttu-id="85c46-129">La scrittura di un File di formattazione di PowerShell</span><span class="sxs-lookup"><span data-stu-id="85c46-129">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
