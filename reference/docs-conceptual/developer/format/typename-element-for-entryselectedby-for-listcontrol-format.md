---
title: Elemento TypeName per EntrySelectedBy per ListControl (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 33c7345c-b808-4c1e-bd54-cb870b407432
caps.latest.revision: 14
ms.openlocfilehash: 0f7216d4dcc0380bceb47ea7c15b3d4a7e5ceeb2
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/05/2019
ms.locfileid: "72361660"
---
# <a name="typename-element-for-entryselectedby-for-listcontrol-format"></a><span data-ttu-id="0d5a4-102">Elemento TypeName per EntrySelectedBy per ListControl (formato)</span><span class="sxs-lookup"><span data-stu-id="0d5a4-102">TypeName Element for EntrySelectedBy for ListControl (Format)</span></span>

<span data-ttu-id="0d5a4-103">Specifica un tipo .NET che usa questa voce della visualizzazione elenco.</span><span class="sxs-lookup"><span data-stu-id="0d5a4-103">Specifies a .NET type that uses this entry of the list view.</span></span> <span data-ttu-id="0d5a4-104">Non esiste alcun limite al numero di tipi che è possibile specificare per una voce di elenco.</span><span class="sxs-lookup"><span data-stu-id="0d5a4-104">There is no limit to the number of types that can be specified for a list entry.</span></span>

<span data-ttu-id="0d5a4-105">Elemento Configuration (Format) elemento ViewDefinitions (Format) elemento View (Format) elemento ListControl (Format) elemento ListEntries (Format) elemento ListEntry (Format) EntrySelectedBy elemento per ListEntry (Format) TypeName elemento per EntrySelectedBy per ListControl (formato)</span><span class="sxs-lookup"><span data-stu-id="0d5a4-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) ListControl Element (Format) ListEntries Element (Format) ListEntry Element (Format) EntrySelectedBy Element for ListEntry (Format) TypeName Element for EntrySelectedBy for ListControl (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="0d5a4-106">Sintassi</span><span class="sxs-lookup"><span data-stu-id="0d5a4-106">Syntax</span></span>

```xml
<TypeName>Nameof.NetType</TypeName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="0d5a4-107">Attributi ed elementi</span><span class="sxs-lookup"><span data-stu-id="0d5a4-107">Attributes and Elements</span></span>

<span data-ttu-id="0d5a4-108">Nelle sezioni seguenti vengono descritti gli attributi, gli elementi figlio e l'elemento padre dell'elemento `TypeName`.</span><span class="sxs-lookup"><span data-stu-id="0d5a4-108">The following sections describe attributes, child elements, and the parent element of the `TypeName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="0d5a4-109">Attributi</span><span class="sxs-lookup"><span data-stu-id="0d5a4-109">Attributes</span></span>

<span data-ttu-id="0d5a4-110">Nessuna.</span><span class="sxs-lookup"><span data-stu-id="0d5a4-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="0d5a4-111">Elementi figlio</span><span class="sxs-lookup"><span data-stu-id="0d5a4-111">Child Elements</span></span>

<span data-ttu-id="0d5a4-112">Nessuna.</span><span class="sxs-lookup"><span data-stu-id="0d5a4-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="0d5a4-113">Elementi padre</span><span class="sxs-lookup"><span data-stu-id="0d5a4-113">Parent Elements</span></span>

|<span data-ttu-id="0d5a4-114">Elemento</span><span class="sxs-lookup"><span data-stu-id="0d5a4-114">Element</span></span>|<span data-ttu-id="0d5a4-115">Description</span><span class="sxs-lookup"><span data-stu-id="0d5a4-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="0d5a4-116">Elemento EntrySelectedBy per ListEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="0d5a4-116">EntrySelectedBy Element for ListEntry (Format)</span></span>](./entryselectedby-element-for-listentry-for-listcontrol-format.md)|<span data-ttu-id="0d5a4-117">Definisce i tipi .NET che utilizzano questa voce di elenco o la condizione che deve esistere affinché questa voce venga utilizzata.</span><span class="sxs-lookup"><span data-stu-id="0d5a4-117">Defines the .NET types that use this list entry or the condition that must exist for this entry to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="0d5a4-118">Valore testo</span><span class="sxs-lookup"><span data-stu-id="0d5a4-118">Text Value</span></span>

<span data-ttu-id="0d5a4-119">Specificare il nome completo del tipo .NET, ad esempio `System.IO.DirectoryInfo`.</span><span class="sxs-lookup"><span data-stu-id="0d5a4-119">Specify the fully-qualified name of the .NET type, such as `System.IO.DirectoryInfo`.</span></span>

## <a name="remarks"></a><span data-ttu-id="0d5a4-120">Osservazioni</span><span class="sxs-lookup"><span data-stu-id="0d5a4-120">Remarks</span></span>

<span data-ttu-id="0d5a4-121">Per ogni voce di elenco è necessario definire almeno un nome di tipo, un set di selezione o una condizione di selezione.</span><span class="sxs-lookup"><span data-stu-id="0d5a4-121">Each list entry must have at least one type name, selection set, or selection condition defined.</span></span>

<span data-ttu-id="0d5a4-122">Per ulteriori informazioni sull'utilizzo di questo elemento in una visualizzazione elenco, vedere [visualizzazione elenco](./creating-a-list-view.md).</span><span class="sxs-lookup"><span data-stu-id="0d5a4-122">For more information about how this element is used in a list view, see [List View](./creating-a-list-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="0d5a4-123">Esempio</span><span class="sxs-lookup"><span data-stu-id="0d5a4-123">Example</span></span>

<span data-ttu-id="0d5a4-124">Nell'esempio seguente viene illustrato come specificare un set di selezione per una voce di una visualizzazione elenco.</span><span class="sxs-lookup"><span data-stu-id="0d5a4-124">The following example shows how to specify a selection set for an entry of a list view.</span></span>

```xml
<ListEntry>
  <EntrySelectedBy>
    <TypeName>Nameof.NetType</TypeName>
  </EntrySelectedBy>
  <ListItems>...</ListItems>
</ListEntry>
```

## <a name="see-also"></a><span data-ttu-id="0d5a4-125">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="0d5a4-125">See Also</span></span>

[<span data-ttu-id="0d5a4-126">Creazione di una visualizzazione elenco</span><span class="sxs-lookup"><span data-stu-id="0d5a4-126">Creating a List View</span></span>](./creating-a-list-view.md)

[<span data-ttu-id="0d5a4-127">Elemento EntrySelectedBy per ListEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="0d5a4-127">EntrySelectedBy Element for ListEntry (Format)</span></span>](./entryselectedby-element-for-listentry-for-listcontrol-format.md)

[<span data-ttu-id="0d5a4-128">Elemento SelectionSetName per EntrySelectedBy per ListEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="0d5a4-128">SelectionSetName Element for EntrySelectedBy for ListEntry (Format)</span></span>](./selectionsetname-element-for-entryselectedby-for-listcontrol-format.md)

[<span data-ttu-id="0d5a4-129">Scrittura di un file di formattazione di PowerShell</span><span class="sxs-lookup"><span data-stu-id="0d5a4-129">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
