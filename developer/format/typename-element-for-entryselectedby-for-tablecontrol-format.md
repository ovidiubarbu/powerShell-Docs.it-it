---
title: Elemento TypeName per EntrySelectedBy per Table (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: fd872ada-d476-4c4d-a788-ccac3f983070
caps.latest.revision: 10
ms.openlocfilehash: 7bbb47268a23fcb37a34e2287a6ce949313a13bb
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/03/2019
ms.locfileid: "56855727"
---
# <a name="typename-element-for-entryselectedby-for-tablecontrol-format"></a><span data-ttu-id="9d738-102">Elemento TypeName per EntrySelectedBy per TableControl (formato)</span><span class="sxs-lookup"><span data-stu-id="9d738-102">TypeName Element for EntrySelectedBy for TableControl (Format)</span></span>

<span data-ttu-id="9d738-103">Specifica un tipo .NET che usa questa voce della visualizzazione della tabella.</span><span class="sxs-lookup"><span data-stu-id="9d738-103">Specifies a .NET type that uses this entry of the table view.</span></span> <span data-ttu-id="9d738-104">Non sono previsti limiti al numero di tipi che possono essere specificati per una voce della tabella.</span><span class="sxs-lookup"><span data-stu-id="9d738-104">There is no limit to the number of types that can be specified for a table entry.</span></span>

<span data-ttu-id="9d738-105">Elemento (formato) elemento ViewDefinitions (formato) visualizzazione elemento (formato) elemento Table (formato) elemento TableRowEntries (formato) elemento TableRowEntry (formato) elemento EntrySelectedBy (formato) TypeName elemento di configurazione per EntrySelectedBy per TableRowEntry (formato)</span><span class="sxs-lookup"><span data-stu-id="9d738-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) TableControl Element (Format) TableRowEntries Element (Format) TableRowEntry Element (Format) EntrySelectedBy Element (Format) TypeName Element for EntrySelectedBy for TableRowEntry (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="9d738-106">Sintassi</span><span class="sxs-lookup"><span data-stu-id="9d738-106">Syntax</span></span>

```xml
<TypeName>Nameof.NetType</TypeName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="9d738-107">Attributi ed elementi</span><span class="sxs-lookup"><span data-stu-id="9d738-107">Attributes and Elements</span></span>

<span data-ttu-id="9d738-108">Le sezioni seguenti descrivono gli attributi e gli elementi figlio dell'elemento padre del `TypeName` elemento.</span><span class="sxs-lookup"><span data-stu-id="9d738-108">The following sections describe attributes, child elements, and the parent element of the `TypeName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="9d738-109">Attributes</span><span class="sxs-lookup"><span data-stu-id="9d738-109">Attributes</span></span>

<span data-ttu-id="9d738-110">Nessuna.</span><span class="sxs-lookup"><span data-stu-id="9d738-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="9d738-111">Elementi figlio</span><span class="sxs-lookup"><span data-stu-id="9d738-111">Child Elements</span></span>

<span data-ttu-id="9d738-112">Nessuna.</span><span class="sxs-lookup"><span data-stu-id="9d738-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="9d738-113">Elementi padre</span><span class="sxs-lookup"><span data-stu-id="9d738-113">Parent Elements</span></span>

|<span data-ttu-id="9d738-114">Elemento</span><span class="sxs-lookup"><span data-stu-id="9d738-114">Element</span></span>|<span data-ttu-id="9d738-115">Description</span><span class="sxs-lookup"><span data-stu-id="9d738-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="9d738-116">Elemento EntrySelectedBy (formato)</span><span class="sxs-lookup"><span data-stu-id="9d738-116">EntrySelectedBy Element (Format)</span></span>](./entryselectedby-element-for-tablerowentry-for-tablecontrol-format.md)|<span data-ttu-id="9d738-117">Definisce i tipi .NET che usano questa voce o la condizione che deve essere presente per questa voce da usare.</span><span class="sxs-lookup"><span data-stu-id="9d738-117">Defines the .NET types that use this entry or the condition that must exist for this entry to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="9d738-118">Valore di testo</span><span class="sxs-lookup"><span data-stu-id="9d738-118">Text Value</span></span>

<span data-ttu-id="9d738-119">Specificare il nome del tipo .NET.</span><span class="sxs-lookup"><span data-stu-id="9d738-119">Specify the name of the .NET type.</span></span>

## <a name="remarks"></a><span data-ttu-id="9d738-120">Osservazioni</span><span class="sxs-lookup"><span data-stu-id="9d738-120">Remarks</span></span>

<span data-ttu-id="9d738-121">Ogni voce dell'elenco deve avere almeno un nome di tipo, il set di selezione o condizione di selezione definiti.</span><span class="sxs-lookup"><span data-stu-id="9d738-121">Each list entry must have at least one type name, selection set, or selection condition defined.</span></span>

<span data-ttu-id="9d738-122">Per altre informazioni sui componenti di visualizzazione di una tabella, vedere [creazione di una visualizzazione tabella](./creating-a-table-view.md).</span><span class="sxs-lookup"><span data-stu-id="9d738-122">For more information about the components of a table view, see [Creating a Table View](./creating-a-table-view.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="9d738-123">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="9d738-123">See Also</span></span>

[<span data-ttu-id="9d738-124">Creazione di una visualizzazione tabella</span><span class="sxs-lookup"><span data-stu-id="9d738-124">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="9d738-125">Elemento EntrySelectedBy (formato)</span><span class="sxs-lookup"><span data-stu-id="9d738-125">EntrySelectedBy Element (Format)</span></span>](./entryselectedby-element-for-tablerowentry-for-tablecontrol-format.md)

[<span data-ttu-id="9d738-126">La scrittura di un File di formattazione di PowerShell</span><span class="sxs-lookup"><span data-stu-id="9d738-126">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
