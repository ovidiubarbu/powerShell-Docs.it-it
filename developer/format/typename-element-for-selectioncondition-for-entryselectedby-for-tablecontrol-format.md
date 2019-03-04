---
title: Elemento TypeName per SelectionCondition per EntrySelectedBy per Table (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e97d56fb-4e35-447a-9282-26f10d0a4609
caps.latest.revision: 11
ms.openlocfilehash: fe65ac95cead7df0069ffdae666fb34b7309fbb6
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/03/2019
ms.locfileid: "56856497"
---
# <a name="typename-element-for-selectioncondition-for-entryselectedby-for-tablecontrol-format"></a><span data-ttu-id="f26e1-102">Elemento TypeName per SelectionCondition per EntrySelectedBy per TableControl (formato)</span><span class="sxs-lookup"><span data-stu-id="f26e1-102">TypeName Element for SelectionCondition for EntrySelectedBy for TableControl (Format)</span></span>

<span data-ttu-id="f26e1-103">Specifica un tipo .NET che attiva la condizione.</span><span class="sxs-lookup"><span data-stu-id="f26e1-103">Specifies a .NET type that triggers the condition.</span></span> <span data-ttu-id="f26e1-104">Quando questo tipo è presente, viene soddisfatta la condizione e viene utilizzata la riga della tabella.</span><span class="sxs-lookup"><span data-stu-id="f26e1-104">When this type is present, the condition is met, and the table row is used.</span></span>

<span data-ttu-id="f26e1-105">Elemento (formato) elemento ViewDefinitions (formato) visualizzazione elemento (formato) elemento Table (formato) elemento TableRowEntries (formato) elemento TableRowEntry (formato) EntrySelectedBy elemento di configurazione per TableRowEntry (formato) Elemento SelectionCondition per EntrySelectedBy per elemento TypeName TableRowEntry (formato) per SelectionCondition per EntrySelectedBy per TableRowEntry (formato)</span><span class="sxs-lookup"><span data-stu-id="f26e1-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) TableControl Element (Format) TableRowEntries Element (Format) TableRowEntry Element (Format) EntrySelectedBy Element for TableRowEntry (Format) SelectionCondition Element for EntrySelectedBy for TableRowEntry (Format) TypeName Element for SelectionCondition for EntrySelectedBy for TableRowEntry (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="f26e1-106">Sintassi</span><span class="sxs-lookup"><span data-stu-id="f26e1-106">Syntax</span></span>

```xml
<TypeName>Nameof.NetType</TypeName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="f26e1-107">Attributi ed elementi</span><span class="sxs-lookup"><span data-stu-id="f26e1-107">Attributes and Elements</span></span>

<span data-ttu-id="f26e1-108">Le sezioni seguenti descrivono gli attributi e gli elementi figlio dell'elemento padre del `TypeName` elemento.</span><span class="sxs-lookup"><span data-stu-id="f26e1-108">The following sections describe attributes, child elements, and the parent element of the `TypeName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="f26e1-109">Attributes</span><span class="sxs-lookup"><span data-stu-id="f26e1-109">Attributes</span></span>

<span data-ttu-id="f26e1-110">Nessuna.</span><span class="sxs-lookup"><span data-stu-id="f26e1-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="f26e1-111">Elementi figlio</span><span class="sxs-lookup"><span data-stu-id="f26e1-111">Child Elements</span></span>

<span data-ttu-id="f26e1-112">Nessuna.</span><span class="sxs-lookup"><span data-stu-id="f26e1-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="f26e1-113">Elementi padre</span><span class="sxs-lookup"><span data-stu-id="f26e1-113">Parent Elements</span></span>

|<span data-ttu-id="f26e1-114">Elemento</span><span class="sxs-lookup"><span data-stu-id="f26e1-114">Element</span></span>|<span data-ttu-id="f26e1-115">Description</span><span class="sxs-lookup"><span data-stu-id="f26e1-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="f26e1-116">Elemento SelectionCondition per EntrySelectedBy per TableRowEntry (formato)</span><span class="sxs-lookup"><span data-stu-id="f26e1-116">SelectionCondition Element for EntrySelectedBy for TableRowEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-tablecontrol-format.md)|<span data-ttu-id="f26e1-117">Definisce la condizione che deve essere presente per questa riga di tabella da utilizzare.</span><span class="sxs-lookup"><span data-stu-id="f26e1-117">Defines the condition that must exist for this table row to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="f26e1-118">Valore di testo</span><span class="sxs-lookup"><span data-stu-id="f26e1-118">Text Value</span></span>

<span data-ttu-id="f26e1-119">Specificare il nome completo del tipo .NET, ad esempio `System.IO.DirectoryInfo`.</span><span class="sxs-lookup"><span data-stu-id="f26e1-119">Specify the fully qualified name of the .NET type, such as `System.IO.DirectoryInfo`.</span></span>

## <a name="remarks"></a><span data-ttu-id="f26e1-120">Osservazioni</span><span class="sxs-lookup"><span data-stu-id="f26e1-120">Remarks</span></span>

<span data-ttu-id="f26e1-121">La condizione di selezione può includere un numero qualsiasi di tipi .NET o selezione imposta, ma non è possibile specificare entrambi.</span><span class="sxs-lookup"><span data-stu-id="f26e1-121">The selection condition can specify any number of .NET types or selection sets, but cannot specify both.</span></span> <span data-ttu-id="f26e1-122">Per altre informazioni su come usare le condizioni di selezione, vedere [definizione di condizioni per quando una voce di visualizzazione o viene usato l'elemento](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="f26e1-122">For more information about how to use selection conditions, see [Defining Conditions for when a View Entry or Item is Used](./defining-conditions-for-displaying-data.md).</span></span>

<span data-ttu-id="f26e1-123">Per altre informazioni sui componenti di visualizzazione di una tabella, vedere [creazione di una visualizzazione tabella](./creating-a-table-view.md).</span><span class="sxs-lookup"><span data-stu-id="f26e1-123">For more information about the components of a table view, see [Creating a Table View](./creating-a-table-view.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="f26e1-124">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="f26e1-124">See Also</span></span>

[<span data-ttu-id="f26e1-125">Creazione di una visualizzazione tabella</span><span class="sxs-lookup"><span data-stu-id="f26e1-125">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="f26e1-126">La definizione delle condizioni per quando i dati vengono visualizzati</span><span class="sxs-lookup"><span data-stu-id="f26e1-126">Defining Conditions for When Data Is Displayed</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="f26e1-127">Elemento SelectionCondition per EntrySelectedBy per TableRowEntry (formato)</span><span class="sxs-lookup"><span data-stu-id="f26e1-127">SelectionCondition Element for EntrySelectedBy for TableRowEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-tablecontrol-format.md)

[<span data-ttu-id="f26e1-128">Elemento SelectionSetName per SelectionCondition per EntrySelectedBy per TableRowEntry (formato)</span><span class="sxs-lookup"><span data-stu-id="f26e1-128">SelectionSetName Element for SelectionCondition for EntrySelectedBy for TableRowEntry (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-entryselectedby-for-tablecontrol-format.md)

[<span data-ttu-id="f26e1-129">La scrittura di un File di formattazione di PowerShell</span><span class="sxs-lookup"><span data-stu-id="f26e1-129">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
