---
title: Elemento TypeName per SelectionCondition per EntrySelectedBy per ListControl (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: bd025a3a-3780-40db-a068-873e7df38015
caps.latest.revision: 9
ms.openlocfilehash: 2b76b040b39088cc9c3b9d6890c38df3c533b39f
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/03/2019
ms.locfileid: "56862777"
---
# <a name="typename-element-for-selectioncondition-for-entryselectedby-for-listcontrol-format"></a><span data-ttu-id="2b2ff-102">Elemento TypeName per SelectionCondition per EntrySelectedBy per ListControl (formato)</span><span class="sxs-lookup"><span data-stu-id="2b2ff-102">TypeName Element for SelectionCondition for EntrySelectedBy for ListControl (Format)</span></span>

<span data-ttu-id="2b2ff-103">Specifica un tipo .NET che attiva la condizione.</span><span class="sxs-lookup"><span data-stu-id="2b2ff-103">Specifies a .NET type that triggers the condition.</span></span> <span data-ttu-id="2b2ff-104">Quando questo tipo è presente, viene usata la voce dell'elenco.</span><span class="sxs-lookup"><span data-stu-id="2b2ff-104">When this type is present, the list entry is used.</span></span>

<span data-ttu-id="2b2ff-105">Elemento (formato) elemento ViewDefinitions (formato) visualizzazione elemento (formato) elemento dell'oggetto ListControl (formato) ListEntries elemento di configurazione per elemento dell'oggetto ListControl (formato) ListEntry ListEntries per elemento EntrySelectedBy ListControl (formato) per ListEntry per elemento dell'oggetto ListControl (formato) SelectionCondition EntrySelectedBy per elemento TypeName dell'oggetto ListControl (formato) per SelectionCondition per EntrySelectedBy per ListControl (formato)</span><span class="sxs-lookup"><span data-stu-id="2b2ff-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) ListControl Element (Format) ListEntries Element for ListControl (Format) ListEntry Element for ListEntries for ListControl (Format) EntrySelectedBy Element for ListEntry for ListControl (Format) SelectionCondition Element for EntrySelectedBy for ListControl (Format) TypeName Element for SelectionCondition for EntrySelectedBy for ListControl (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="2b2ff-106">Sintassi</span><span class="sxs-lookup"><span data-stu-id="2b2ff-106">Syntax</span></span>

```xml
<TypeName>Nameof.NetType</TypeName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="2b2ff-107">Attributi ed elementi</span><span class="sxs-lookup"><span data-stu-id="2b2ff-107">Attributes and Elements</span></span>

<span data-ttu-id="2b2ff-108">Le sezioni seguenti descrivono gli attributi e gli elementi figlio dell'elemento padre del `TypeName` elemento.</span><span class="sxs-lookup"><span data-stu-id="2b2ff-108">The following sections describe attributes, child elements, and the parent element of the `TypeName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="2b2ff-109">Attributes</span><span class="sxs-lookup"><span data-stu-id="2b2ff-109">Attributes</span></span>

<span data-ttu-id="2b2ff-110">Nessuna.</span><span class="sxs-lookup"><span data-stu-id="2b2ff-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="2b2ff-111">Elementi figlio</span><span class="sxs-lookup"><span data-stu-id="2b2ff-111">Child Elements</span></span>

<span data-ttu-id="2b2ff-112">Nessuna.</span><span class="sxs-lookup"><span data-stu-id="2b2ff-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="2b2ff-113">Elementi padre</span><span class="sxs-lookup"><span data-stu-id="2b2ff-113">Parent Elements</span></span>

|<span data-ttu-id="2b2ff-114">Elemento</span><span class="sxs-lookup"><span data-stu-id="2b2ff-114">Element</span></span>|<span data-ttu-id="2b2ff-115">Description</span><span class="sxs-lookup"><span data-stu-id="2b2ff-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="2b2ff-116">Elemento SelectionCondition per EntrySelectedBy per ListControl (formato)</span><span class="sxs-lookup"><span data-stu-id="2b2ff-116">SelectionCondition Element for EntrySelectedBy for ListControl (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-listcontrol-format.md)|<span data-ttu-id="2b2ff-117">Definisce la condizione che deve essere presente per questa voce di elenco da utilizzare.</span><span class="sxs-lookup"><span data-stu-id="2b2ff-117">Defines the condition that must exist for this list entry to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="2b2ff-118">Valore di testo</span><span class="sxs-lookup"><span data-stu-id="2b2ff-118">Text Value</span></span>

<span data-ttu-id="2b2ff-119">Specificare il nome completo del tipo .NET, ad esempio `System.IO.DirectoryInfo`.</span><span class="sxs-lookup"><span data-stu-id="2b2ff-119">Specify the fully qualified name of the .NET type, such as `System.IO.DirectoryInfo`.</span></span>

## <a name="remarks"></a><span data-ttu-id="2b2ff-120">Osservazioni</span><span class="sxs-lookup"><span data-stu-id="2b2ff-120">Remarks</span></span>

<span data-ttu-id="2b2ff-121">La condizione di selezione può includere un numero qualsiasi di tipi .NET o selezione imposta, ma non è possibile specificare entrambi.</span><span class="sxs-lookup"><span data-stu-id="2b2ff-121">The selection condition can specify any number of .NET types or selection sets, but cannot specify both.</span></span> <span data-ttu-id="2b2ff-122">Per altre informazioni su come usare le condizioni di selezione, vedere [che definisce le condizioni per quando i dati vengono visualizzati](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="2b2ff-122">For more information about how to use selection conditions, see [Defining Conditions for when Data is Displayed](./defining-conditions-for-displaying-data.md).</span></span>

<span data-ttu-id="2b2ff-123">Per altre informazioni su altri componenti di una visualizzazione elenco, vedere [creazione di una visualizzazione elenco](./creating-a-list-view.md).</span><span class="sxs-lookup"><span data-stu-id="2b2ff-123">For more information about other the components of a list view, see [Creating a List View](./creating-a-list-view.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="2b2ff-124">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="2b2ff-124">See Also</span></span>

[<span data-ttu-id="2b2ff-125">Creazione di una visualizzazione elenco</span><span class="sxs-lookup"><span data-stu-id="2b2ff-125">Creating a List View</span></span>](./creating-a-list-view.md)

[<span data-ttu-id="2b2ff-126">La definizione delle condizioni per quando i dati vengono visualizzati</span><span class="sxs-lookup"><span data-stu-id="2b2ff-126">Defining Conditions for When Data Is Displayed</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="2b2ff-127">Elemento SelectionCondition per EntrySelectedBy per ListControl (formato)</span><span class="sxs-lookup"><span data-stu-id="2b2ff-127">SelectionCondition Element for EntrySelectedBy for ListControl (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-listcontrol-format.md)

[<span data-ttu-id="2b2ff-128">La scrittura di un File di formattazione di PowerShell</span><span class="sxs-lookup"><span data-stu-id="2b2ff-128">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
