---
title: Elemento TypeName per SelectionCondition per EntrySelectedBy per ListControl (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: bd025a3a-3780-40db-a068-873e7df38015
caps.latest.revision: 9
ms.openlocfilehash: 2b76b040b39088cc9c3b9d6890c38df3c533b39f
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/05/2019
ms.locfileid: "72361560"
---
# <a name="typename-element-for-selectioncondition-for-entryselectedby-for-listcontrol-format"></a><span data-ttu-id="1f5d3-102">Elemento TypeName per SelectionCondition per EntrySelectedBy per ListControl (formato)</span><span class="sxs-lookup"><span data-stu-id="1f5d3-102">TypeName Element for SelectionCondition for EntrySelectedBy for ListControl (Format)</span></span>

<span data-ttu-id="1f5d3-103">Specifica un tipo .NET che attiva la condizione.</span><span class="sxs-lookup"><span data-stu-id="1f5d3-103">Specifies a .NET type that triggers the condition.</span></span> <span data-ttu-id="1f5d3-104">Quando questo tipo è presente, viene usata la voce dell'elenco.</span><span class="sxs-lookup"><span data-stu-id="1f5d3-104">When this type is present, the list entry is used.</span></span>

<span data-ttu-id="1f5d3-105">Elemento Configuration (Format) elemento ViewDefinitions (Format) elemento View (Format) elemento ListControl (Format) elemento ListEntries per ListControl (Format) elemento ListEntry per ListEntries per l'elemento ListControl (Format) EntrySelectedBy per ListEntry per ListControl (Format) elemento SelectionCondition per EntrySelectedBy per il parametro ListControl (Format) TypeName per SelectionCondition per EntrySelectedBy per ListControl (Format)</span><span class="sxs-lookup"><span data-stu-id="1f5d3-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) ListControl Element (Format) ListEntries Element for ListControl (Format) ListEntry Element for ListEntries for ListControl (Format) EntrySelectedBy Element for ListEntry for ListControl (Format) SelectionCondition Element for EntrySelectedBy for ListControl (Format) TypeName Element for SelectionCondition for EntrySelectedBy for ListControl (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="1f5d3-106">Sintassi</span><span class="sxs-lookup"><span data-stu-id="1f5d3-106">Syntax</span></span>

```xml
<TypeName>Nameof.NetType</TypeName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="1f5d3-107">Attributi ed elementi</span><span class="sxs-lookup"><span data-stu-id="1f5d3-107">Attributes and Elements</span></span>

<span data-ttu-id="1f5d3-108">Nelle sezioni seguenti vengono descritti gli attributi, gli elementi figlio e l'elemento padre dell'elemento `TypeName`.</span><span class="sxs-lookup"><span data-stu-id="1f5d3-108">The following sections describe attributes, child elements, and the parent element of the `TypeName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="1f5d3-109">Attributi</span><span class="sxs-lookup"><span data-stu-id="1f5d3-109">Attributes</span></span>

<span data-ttu-id="1f5d3-110">Nessuna.</span><span class="sxs-lookup"><span data-stu-id="1f5d3-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="1f5d3-111">Elementi figlio</span><span class="sxs-lookup"><span data-stu-id="1f5d3-111">Child Elements</span></span>

<span data-ttu-id="1f5d3-112">Nessuna.</span><span class="sxs-lookup"><span data-stu-id="1f5d3-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="1f5d3-113">Elementi padre</span><span class="sxs-lookup"><span data-stu-id="1f5d3-113">Parent Elements</span></span>

|<span data-ttu-id="1f5d3-114">Elemento</span><span class="sxs-lookup"><span data-stu-id="1f5d3-114">Element</span></span>|<span data-ttu-id="1f5d3-115">Description</span><span class="sxs-lookup"><span data-stu-id="1f5d3-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="1f5d3-116">Elemento SelectionCondition per EntrySelectedBy per ListControl (Format)</span><span class="sxs-lookup"><span data-stu-id="1f5d3-116">SelectionCondition Element for EntrySelectedBy for ListControl (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-listcontrol-format.md)|<span data-ttu-id="1f5d3-117">Definisce la condizione che deve esistere affinché questa voce di elenco venga utilizzata.</span><span class="sxs-lookup"><span data-stu-id="1f5d3-117">Defines the condition that must exist for this list entry to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="1f5d3-118">Valore testo</span><span class="sxs-lookup"><span data-stu-id="1f5d3-118">Text Value</span></span>

<span data-ttu-id="1f5d3-119">Specificare il nome completo del tipo .NET, ad esempio `System.IO.DirectoryInfo`.</span><span class="sxs-lookup"><span data-stu-id="1f5d3-119">Specify the fully qualified name of the .NET type, such as `System.IO.DirectoryInfo`.</span></span>

## <a name="remarks"></a><span data-ttu-id="1f5d3-120">Osservazioni</span><span class="sxs-lookup"><span data-stu-id="1f5d3-120">Remarks</span></span>

<span data-ttu-id="1f5d3-121">La condizione di selezione può specificare un numero qualsiasi di tipi .NET o set di selezione, ma non è possibile specificarli entrambi.</span><span class="sxs-lookup"><span data-stu-id="1f5d3-121">The selection condition can specify any number of .NET types or selection sets, but cannot specify both.</span></span> <span data-ttu-id="1f5d3-122">Per ulteriori informazioni sull'utilizzo delle condizioni di selezione, vedere [definizione di condizioni per la visualizzazione dei dati](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="1f5d3-122">For more information about how to use selection conditions, see [Defining Conditions for when Data is Displayed](./defining-conditions-for-displaying-data.md).</span></span>

<span data-ttu-id="1f5d3-123">Per ulteriori informazioni su altri componenti di una visualizzazione elenco, vedere [creazione di una visualizzazione elenco](./creating-a-list-view.md).</span><span class="sxs-lookup"><span data-stu-id="1f5d3-123">For more information about other the components of a list view, see [Creating a List View](./creating-a-list-view.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="1f5d3-124">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="1f5d3-124">See Also</span></span>

[<span data-ttu-id="1f5d3-125">Creazione di una visualizzazione elenco</span><span class="sxs-lookup"><span data-stu-id="1f5d3-125">Creating a List View</span></span>](./creating-a-list-view.md)

[<span data-ttu-id="1f5d3-126">Definizione delle condizioni per la visualizzazione dei dati</span><span class="sxs-lookup"><span data-stu-id="1f5d3-126">Defining Conditions for When Data Is Displayed</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="1f5d3-127">Elemento SelectionCondition per EntrySelectedBy per ListControl (Format)</span><span class="sxs-lookup"><span data-stu-id="1f5d3-127">SelectionCondition Element for EntrySelectedBy for ListControl (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-listcontrol-format.md)

[<span data-ttu-id="1f5d3-128">Scrittura di un file di formattazione di PowerShell</span><span class="sxs-lookup"><span data-stu-id="1f5d3-128">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
