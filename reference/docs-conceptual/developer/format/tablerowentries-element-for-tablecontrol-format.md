---
title: Elemento TableRowEntries per Table ((Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d10b68ca-256c-4c58-b503-73f7777b39ae
caps.latest.revision: 15
ms.openlocfilehash: 88de19be02de4933f892e02093403a82ccdd5788
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/05/2019
ms.locfileid: "72368150"
---
# <a name="tablerowentries-element-for-tablecontrol-format"></a><span data-ttu-id="66c5b-102">Elemento TableRowEntries per TableControl (formato)</span><span class="sxs-lookup"><span data-stu-id="66c5b-102">TableRowEntries Element for TableControl (Format)</span></span>

<span data-ttu-id="66c5b-103">Definisce le righe della tabella.</span><span class="sxs-lookup"><span data-stu-id="66c5b-103">Defines the rows of the table.</span></span>

<span data-ttu-id="66c5b-104">Elemento Configuration (Format) elemento ViewDefinitions (Format) elemento View (Format) elemento Table ((Format) elemento TableRowEntries per Table ((Format)</span><span class="sxs-lookup"><span data-stu-id="66c5b-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) TableControl Element (Format) TableRowEntries Element for TableControl (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="66c5b-105">Sintassi</span><span class="sxs-lookup"><span data-stu-id="66c5b-105">Syntax</span></span>

```xml
<TableRowEntries>
  <TableRowEntry>...</TableRowEntry>
</TableRowEntries>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="66c5b-106">Attributi ed elementi</span><span class="sxs-lookup"><span data-stu-id="66c5b-106">Attributes and Elements</span></span>

<span data-ttu-id="66c5b-107">Nelle sezioni seguenti vengono descritti gli attributi, gli elementi figlio e l'elemento padre dell'elemento `TableRowEntries`.</span><span class="sxs-lookup"><span data-stu-id="66c5b-107">The following sections describe the attributes, child elements, and parent element of the `TableRowEntries` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="66c5b-108">Attributi</span><span class="sxs-lookup"><span data-stu-id="66c5b-108">Attributes</span></span>

<span data-ttu-id="66c5b-109">Nessuna.</span><span class="sxs-lookup"><span data-stu-id="66c5b-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="66c5b-110">Elementi figlio</span><span class="sxs-lookup"><span data-stu-id="66c5b-110">Child Elements</span></span>

|<span data-ttu-id="66c5b-111">Elemento</span><span class="sxs-lookup"><span data-stu-id="66c5b-111">Element</span></span>|<span data-ttu-id="66c5b-112">Description</span><span class="sxs-lookup"><span data-stu-id="66c5b-112">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="66c5b-113">Elemento TableRowEntry per TableRowEntries per Table ((Format)</span><span class="sxs-lookup"><span data-stu-id="66c5b-113">TableRowEntry Element for TableRowEntries for TableControl (Format)</span></span>](./tablerowentry-element-for-tablerowentries-for-tablecontrol-format.md)|<span data-ttu-id="66c5b-114">Elemento obbligatorio.</span><span class="sxs-lookup"><span data-stu-id="66c5b-114">Required element.</span></span><br /><br /> <span data-ttu-id="66c5b-115">Definisce i dati visualizzati in una riga della tabella.</span><span class="sxs-lookup"><span data-stu-id="66c5b-115">Defines the data that is displayed in a row of the table.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="66c5b-116">Elementi padre</span><span class="sxs-lookup"><span data-stu-id="66c5b-116">Parent Elements</span></span>

|<span data-ttu-id="66c5b-117">Elemento</span><span class="sxs-lookup"><span data-stu-id="66c5b-117">Element</span></span>|<span data-ttu-id="66c5b-118">Description</span><span class="sxs-lookup"><span data-stu-id="66c5b-118">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="66c5b-119">Elemento Table ((Format)</span><span class="sxs-lookup"><span data-stu-id="66c5b-119">TableControl Element (Format)</span></span>](./tablecontrol-element-format.md)|<span data-ttu-id="66c5b-120">Definisce un formato di tabella per una visualizzazione.</span><span class="sxs-lookup"><span data-stu-id="66c5b-120">Defines a table format for a view.</span></span>|

## <a name="remarks"></a><span data-ttu-id="66c5b-121">Osservazioni</span><span class="sxs-lookup"><span data-stu-id="66c5b-121">Remarks</span></span>

<span data-ttu-id="66c5b-122">È necessario specificare uno o più elementi `TableRowEntry` per la visualizzazione tabella.</span><span class="sxs-lookup"><span data-stu-id="66c5b-122">You must specify one or more `TableRowEntry` elements for the table view.</span></span> <span data-ttu-id="66c5b-123">Non esiste un limite massimo per il numero di elementi `TableRowEntry` che possono essere aggiunti, né l'ordine significativo.</span><span class="sxs-lookup"><span data-stu-id="66c5b-123">There is no maximum limit to the number of `TableRowEntry` elements that can be added nor is their order significant.</span></span>

<span data-ttu-id="66c5b-124">Per ulteriori informazioni sui componenti di una vista tabella, vedere [creazione di una vista tabella](./creating-a-table-view.md).</span><span class="sxs-lookup"><span data-stu-id="66c5b-124">For more information about the components of a table view, see [Creating a Table View](./creating-a-table-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="66c5b-125">Esempio</span><span class="sxs-lookup"><span data-stu-id="66c5b-125">Example</span></span>

<span data-ttu-id="66c5b-126">Nell'esempio seguente viene illustrato un elemento `TableRowEntries` che definisce una riga in cui vengono visualizzati i valori di due proprietà dell'oggetto [System. Diagnostics. Process](/dotnet/api/System.Diagnostics.Process) .</span><span class="sxs-lookup"><span data-stu-id="66c5b-126">The following example shows a `TableRowEntries` element that defines a row that displays the values of two properties of the [System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process) object.</span></span>

```xml
<TableRowEntries>
  <TableRowEntry>
    <EntrySelectedBy>
      <TypeName>System.Diagnostics.Process</TypeName>
    </EntrySelectedBy>
    <TableColumnItems>
      <TableColumnItem>
        <PropertyName> Property for first column</PropertyName>
      </TableColumnItem>
      <TableColumnItem>
        <PropertyName> Property for second column</PropertyName>
      </TableColumnItem>
    </TableColumnItems>
  </TableRowEntry>
</TableRowEntries>

```

## <a name="see-also"></a><span data-ttu-id="66c5b-127">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="66c5b-127">See Also</span></span>

[<span data-ttu-id="66c5b-128">Creazione di una vista tabella</span><span class="sxs-lookup"><span data-stu-id="66c5b-128">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="66c5b-129">Elemento Table ((Format)</span><span class="sxs-lookup"><span data-stu-id="66c5b-129">TableControl Element (Format)</span></span>](./tablecontrol-element-format.md)

[<span data-ttu-id="66c5b-130">Elemento TableRowEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="66c5b-130">TableRowEntry Element (Format)</span></span>](./tablerowentry-element-for-tablerowentries-for-tablecontrol-format.md)

[<span data-ttu-id="66c5b-131">Scrittura di un file di formattazione di PowerShell</span><span class="sxs-lookup"><span data-stu-id="66c5b-131">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
