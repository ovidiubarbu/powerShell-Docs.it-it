---
title: Elemento TypeName per EntrySelectedBy per Table ((Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: fd872ada-d476-4c4d-a788-ccac3f983070
caps.latest.revision: 10
ms.openlocfilehash: 7bbb47268a23fcb37a34e2287a6ce949313a13bb
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/15/2019
ms.locfileid: "72361630"
---
# <a name="typename-element-for-entryselectedby-for-tablecontrol-format"></a><span data-ttu-id="17203-102">Elemento TypeName per EntrySelectedBy per TableControl (formato)</span><span class="sxs-lookup"><span data-stu-id="17203-102">TypeName Element for EntrySelectedBy for TableControl (Format)</span></span>

<span data-ttu-id="17203-103">Specifica un tipo .NET che usa questa voce della visualizzazione tabella.</span><span class="sxs-lookup"><span data-stu-id="17203-103">Specifies a .NET type that uses this entry of the table view.</span></span> <span data-ttu-id="17203-104">Non esiste alcun limite al numero di tipi che è possibile specificare per una voce di tabella.</span><span class="sxs-lookup"><span data-stu-id="17203-104">There is no limit to the number of types that can be specified for a table entry.</span></span>

<span data-ttu-id="17203-105">Elemento Configuration (Format) elemento ViewDefinitions (Format) elemento View (Format) elemento Table ((Format) elemento TableRowEntries (Format) elemento TableRowEntry (Format) elemento EntrySelectedBy (Format) elemento TypeName per EntrySelectedBy per TableRowEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="17203-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) TableControl Element (Format) TableRowEntries Element (Format) TableRowEntry Element (Format) EntrySelectedBy Element (Format) TypeName Element for EntrySelectedBy for TableRowEntry (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="17203-106">Sintassi</span><span class="sxs-lookup"><span data-stu-id="17203-106">Syntax</span></span>

```xml
<TypeName>Nameof.NetType</TypeName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="17203-107">Attributi ed elementi</span><span class="sxs-lookup"><span data-stu-id="17203-107">Attributes and Elements</span></span>

<span data-ttu-id="17203-108">Nelle sezioni seguenti vengono descritti gli attributi, gli elementi figlio e l'elemento padre dell'elemento `TypeName`.</span><span class="sxs-lookup"><span data-stu-id="17203-108">The following sections describe attributes, child elements, and the parent element of the `TypeName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="17203-109">Attributi</span><span class="sxs-lookup"><span data-stu-id="17203-109">Attributes</span></span>

<span data-ttu-id="17203-110">Nessuna.</span><span class="sxs-lookup"><span data-stu-id="17203-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="17203-111">Elementi figlio</span><span class="sxs-lookup"><span data-stu-id="17203-111">Child Elements</span></span>

<span data-ttu-id="17203-112">Nessuna.</span><span class="sxs-lookup"><span data-stu-id="17203-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="17203-113">Elementi padre</span><span class="sxs-lookup"><span data-stu-id="17203-113">Parent Elements</span></span>

|<span data-ttu-id="17203-114">Elemento</span><span class="sxs-lookup"><span data-stu-id="17203-114">Element</span></span>|<span data-ttu-id="17203-115">Description</span><span class="sxs-lookup"><span data-stu-id="17203-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="17203-116">Elemento EntrySelectedBy (Format)</span><span class="sxs-lookup"><span data-stu-id="17203-116">EntrySelectedBy Element (Format)</span></span>](./entryselectedby-element-for-tablerowentry-for-tablecontrol-format.md)|<span data-ttu-id="17203-117">Definisce i tipi .NET che utilizzano questa voce o la condizione che deve esistere affinché questa voce venga utilizzata.</span><span class="sxs-lookup"><span data-stu-id="17203-117">Defines the .NET types that use this entry or the condition that must exist for this entry to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="17203-118">Valore di testo</span><span class="sxs-lookup"><span data-stu-id="17203-118">Text Value</span></span>

<span data-ttu-id="17203-119">Specificare il nome del tipo .NET.</span><span class="sxs-lookup"><span data-stu-id="17203-119">Specify the name of the .NET type.</span></span>

## <a name="remarks"></a><span data-ttu-id="17203-120">Osservazioni</span><span class="sxs-lookup"><span data-stu-id="17203-120">Remarks</span></span>

<span data-ttu-id="17203-121">Per ogni voce di elenco è necessario definire almeno un nome di tipo, un set di selezione o una condizione di selezione.</span><span class="sxs-lookup"><span data-stu-id="17203-121">Each list entry must have at least one type name, selection set, or selection condition defined.</span></span>

<span data-ttu-id="17203-122">Per ulteriori informazioni sui componenti di una vista tabella, vedere [creazione di una vista tabella](./creating-a-table-view.md).</span><span class="sxs-lookup"><span data-stu-id="17203-122">For more information about the components of a table view, see [Creating a Table View](./creating-a-table-view.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="17203-123">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="17203-123">See Also</span></span>

[<span data-ttu-id="17203-124">Creazione di una vista tabella</span><span class="sxs-lookup"><span data-stu-id="17203-124">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="17203-125">Elemento EntrySelectedBy (Format)</span><span class="sxs-lookup"><span data-stu-id="17203-125">EntrySelectedBy Element (Format)</span></span>](./entryselectedby-element-for-tablerowentry-for-tablecontrol-format.md)

[<span data-ttu-id="17203-126">Scrittura di un file di formattazione di PowerShell</span><span class="sxs-lookup"><span data-stu-id="17203-126">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
