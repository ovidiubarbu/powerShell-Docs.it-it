---
title: Elemento TypeName per SelectionCondition per EntrySelectedBy per Table ((Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e97d56fb-4e35-447a-9282-26f10d0a4609
caps.latest.revision: 11
ms.openlocfilehash: fe65ac95cead7df0069ffdae666fb34b7309fbb6
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/15/2019
ms.locfileid: "72361470"
---
# <a name="typename-element-for-selectioncondition-for-entryselectedby-for-tablecontrol-format"></a><span data-ttu-id="44dc5-102">Elemento TypeName per SelectionCondition per EntrySelectedBy per TableControl (formato)</span><span class="sxs-lookup"><span data-stu-id="44dc5-102">TypeName Element for SelectionCondition for EntrySelectedBy for TableControl (Format)</span></span>

<span data-ttu-id="44dc5-103">Specifica un tipo .NET che attiva la condizione.</span><span class="sxs-lookup"><span data-stu-id="44dc5-103">Specifies a .NET type that triggers the condition.</span></span> <span data-ttu-id="44dc5-104">Quando questo tipo è presente, la condizione viene soddisfatta e viene utilizzata la riga della tabella.</span><span class="sxs-lookup"><span data-stu-id="44dc5-104">When this type is present, the condition is met, and the table row is used.</span></span>

<span data-ttu-id="44dc5-105">Elemento Configuration (Format) elemento ViewDefinitions (Format) elemento View (Format) elemento Table ((Format) elemento TableRowEntries (Format) elemento TableRowEntry (Format) elemento EntrySelectedBy per TableRowEntry (Format) Elemento SelectionCondition per EntrySelectedBy per l'elemento TableRowEntry (Format) TypeName per SelectionCondition per EntrySelectedBy per TableRowEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="44dc5-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) TableControl Element (Format) TableRowEntries Element (Format) TableRowEntry Element (Format) EntrySelectedBy Element for TableRowEntry (Format) SelectionCondition Element for EntrySelectedBy for TableRowEntry (Format) TypeName Element for SelectionCondition for EntrySelectedBy for TableRowEntry (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="44dc5-106">Sintassi</span><span class="sxs-lookup"><span data-stu-id="44dc5-106">Syntax</span></span>

```xml
<TypeName>Nameof.NetType</TypeName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="44dc5-107">Attributi ed elementi</span><span class="sxs-lookup"><span data-stu-id="44dc5-107">Attributes and Elements</span></span>

<span data-ttu-id="44dc5-108">Nelle sezioni seguenti vengono descritti gli attributi, gli elementi figlio e l'elemento padre dell'elemento `TypeName`.</span><span class="sxs-lookup"><span data-stu-id="44dc5-108">The following sections describe attributes, child elements, and the parent element of the `TypeName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="44dc5-109">Attributi</span><span class="sxs-lookup"><span data-stu-id="44dc5-109">Attributes</span></span>

<span data-ttu-id="44dc5-110">Nessuna.</span><span class="sxs-lookup"><span data-stu-id="44dc5-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="44dc5-111">Elementi figlio</span><span class="sxs-lookup"><span data-stu-id="44dc5-111">Child Elements</span></span>

<span data-ttu-id="44dc5-112">Nessuna.</span><span class="sxs-lookup"><span data-stu-id="44dc5-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="44dc5-113">Elementi padre</span><span class="sxs-lookup"><span data-stu-id="44dc5-113">Parent Elements</span></span>

|<span data-ttu-id="44dc5-114">Elemento</span><span class="sxs-lookup"><span data-stu-id="44dc5-114">Element</span></span>|<span data-ttu-id="44dc5-115">Description</span><span class="sxs-lookup"><span data-stu-id="44dc5-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="44dc5-116">Elemento SelectionCondition per EntrySelectedBy per TableRowEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="44dc5-116">SelectionCondition Element for EntrySelectedBy for TableRowEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-tablecontrol-format.md)|<span data-ttu-id="44dc5-117">Definisce la condizione che deve esistere per la riga della tabella da utilizzare.</span><span class="sxs-lookup"><span data-stu-id="44dc5-117">Defines the condition that must exist for this table row to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="44dc5-118">Valore di testo</span><span class="sxs-lookup"><span data-stu-id="44dc5-118">Text Value</span></span>

<span data-ttu-id="44dc5-119">Specificare il nome completo del tipo .NET, ad esempio `System.IO.DirectoryInfo`.</span><span class="sxs-lookup"><span data-stu-id="44dc5-119">Specify the fully qualified name of the .NET type, such as `System.IO.DirectoryInfo`.</span></span>

## <a name="remarks"></a><span data-ttu-id="44dc5-120">Osservazioni</span><span class="sxs-lookup"><span data-stu-id="44dc5-120">Remarks</span></span>

<span data-ttu-id="44dc5-121">La condizione di selezione può specificare un numero qualsiasi di tipi .NET o set di selezione, ma non è possibile specificarli entrambi.</span><span class="sxs-lookup"><span data-stu-id="44dc5-121">The selection condition can specify any number of .NET types or selection sets, but cannot specify both.</span></span> <span data-ttu-id="44dc5-122">Per ulteriori informazioni sull'utilizzo delle condizioni di selezione, vedere [definizione di condizioni per l'utilizzo di una voce o di un elemento della visualizzazione](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="44dc5-122">For more information about how to use selection conditions, see [Defining Conditions for when a View Entry or Item is Used](./defining-conditions-for-displaying-data.md).</span></span>

<span data-ttu-id="44dc5-123">Per ulteriori informazioni sui componenti di una vista tabella, vedere [creazione di una vista tabella](./creating-a-table-view.md).</span><span class="sxs-lookup"><span data-stu-id="44dc5-123">For more information about the components of a table view, see [Creating a Table View](./creating-a-table-view.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="44dc5-124">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="44dc5-124">See Also</span></span>

[<span data-ttu-id="44dc5-125">Creazione di una vista tabella</span><span class="sxs-lookup"><span data-stu-id="44dc5-125">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="44dc5-126">Definizione delle condizioni per la visualizzazione dei dati</span><span class="sxs-lookup"><span data-stu-id="44dc5-126">Defining Conditions for When Data Is Displayed</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="44dc5-127">Elemento SelectionCondition per EntrySelectedBy per TableRowEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="44dc5-127">SelectionCondition Element for EntrySelectedBy for TableRowEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-tablecontrol-format.md)

[<span data-ttu-id="44dc5-128">Elemento SelectionSetName per SelectionCondition per EntrySelectedBy per TableRowEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="44dc5-128">SelectionSetName Element for SelectionCondition for EntrySelectedBy for TableRowEntry (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-entryselectedby-for-tablecontrol-format.md)

[<span data-ttu-id="44dc5-129">Scrittura di un file di formattazione di PowerShell</span><span class="sxs-lookup"><span data-stu-id="44dc5-129">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
