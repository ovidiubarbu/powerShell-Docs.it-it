---
title: Elemento TableRowEntries per Table (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d10b68ca-256c-4c58-b503-73f7777b39ae
caps.latest.revision: 15
ms.openlocfilehash: 88de19be02de4933f892e02093403a82ccdd5788
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/16/2019
ms.locfileid: "58055734"
---
# <a name="tablerowentries-element-for-tablecontrol-format"></a><span data-ttu-id="6ae18-102">Elemento TableRowEntries per TableControl (formato)</span><span class="sxs-lookup"><span data-stu-id="6ae18-102">TableRowEntries Element for TableControl (Format)</span></span>

<span data-ttu-id="6ae18-103">Definire le righe della tabella.</span><span class="sxs-lookup"><span data-stu-id="6ae18-103">Defines the rows of the table.</span></span>

<span data-ttu-id="6ae18-104">Elemento (formato) elemento ViewDefinitions (formato) visualizzazione elemento (formato) elemento Table (formato) TableRowEntries elemento di configurazione per Table (formato)</span><span class="sxs-lookup"><span data-stu-id="6ae18-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) TableControl Element (Format) TableRowEntries Element for TableControl (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="6ae18-105">Sintassi</span><span class="sxs-lookup"><span data-stu-id="6ae18-105">Syntax</span></span>

```xml
<TableRowEntries>
  <TableRowEntry>...</TableRowEntry>
</TableRowEntries>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="6ae18-106">Attributi ed elementi</span><span class="sxs-lookup"><span data-stu-id="6ae18-106">Attributes and Elements</span></span>

<span data-ttu-id="6ae18-107">Le sezioni seguenti descrivono gli attributi, elementi figlio ed elemento padre dell'elemento di `TableRowEntries` elemento.</span><span class="sxs-lookup"><span data-stu-id="6ae18-107">The following sections describe the attributes, child elements, and parent element of the `TableRowEntries` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="6ae18-108">Attributes</span><span class="sxs-lookup"><span data-stu-id="6ae18-108">Attributes</span></span>

<span data-ttu-id="6ae18-109">Nessuna.</span><span class="sxs-lookup"><span data-stu-id="6ae18-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="6ae18-110">Elementi figlio</span><span class="sxs-lookup"><span data-stu-id="6ae18-110">Child Elements</span></span>

|<span data-ttu-id="6ae18-111">Elemento</span><span class="sxs-lookup"><span data-stu-id="6ae18-111">Element</span></span>|<span data-ttu-id="6ae18-112">Description</span><span class="sxs-lookup"><span data-stu-id="6ae18-112">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="6ae18-113">Elemento TableRowEntry per TableRowEntries per Table (formato)</span><span class="sxs-lookup"><span data-stu-id="6ae18-113">TableRowEntry Element for TableRowEntries for TableControl (Format)</span></span>](./tablerowentry-element-for-tablerowentries-for-tablecontrol-format.md)|<span data-ttu-id="6ae18-114">Elemento obbligatorio.</span><span class="sxs-lookup"><span data-stu-id="6ae18-114">Required element.</span></span><br /><br /> <span data-ttu-id="6ae18-115">Definisce i dati che viene visualizzati in una riga della tabella.</span><span class="sxs-lookup"><span data-stu-id="6ae18-115">Defines the data that is displayed in a row of the table.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="6ae18-116">Elementi padre</span><span class="sxs-lookup"><span data-stu-id="6ae18-116">Parent Elements</span></span>

|<span data-ttu-id="6ae18-117">Elemento</span><span class="sxs-lookup"><span data-stu-id="6ae18-117">Element</span></span>|<span data-ttu-id="6ae18-118">Description</span><span class="sxs-lookup"><span data-stu-id="6ae18-118">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="6ae18-119">Elemento Table (formato)</span><span class="sxs-lookup"><span data-stu-id="6ae18-119">TableControl Element (Format)</span></span>](./tablecontrol-element-format.md)|<span data-ttu-id="6ae18-120">Definisce un formato di tabella per una visualizzazione.</span><span class="sxs-lookup"><span data-stu-id="6ae18-120">Defines a table format for a view.</span></span>|

## <a name="remarks"></a><span data-ttu-id="6ae18-121">Osservazioni</span><span class="sxs-lookup"><span data-stu-id="6ae18-121">Remarks</span></span>

<span data-ttu-id="6ae18-122">È necessario specificare uno o più `TableRowEntry` elementi per la visualizzazione di tabella.</span><span class="sxs-lookup"><span data-stu-id="6ae18-122">You must specify one or more `TableRowEntry` elements for the table view.</span></span> <span data-ttu-id="6ae18-123">Non sono previsti limiti al numero di massimo `TableRowEntry` gli elementi che è possibile aggiungere né il relativo ordine significativo.</span><span class="sxs-lookup"><span data-stu-id="6ae18-123">There is no maximum limit to the number of `TableRowEntry` elements that can be added nor is their order significant.</span></span>

<span data-ttu-id="6ae18-124">Per altre informazioni sui componenti di visualizzazione di una tabella, vedere [creazione di una visualizzazione tabella](./creating-a-table-view.md).</span><span class="sxs-lookup"><span data-stu-id="6ae18-124">For more information about the components of a table view, see [Creating a Table View](./creating-a-table-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="6ae18-125">Esempio</span><span class="sxs-lookup"><span data-stu-id="6ae18-125">Example</span></span>

<span data-ttu-id="6ae18-126">L'esempio seguente mostra una `TableRowEntries` elemento che definisce una riga che visualizza i valori delle due proprietà del [Diagnostics](/dotnet/api/System.Diagnostics.Process) oggetto.</span><span class="sxs-lookup"><span data-stu-id="6ae18-126">The following example shows a `TableRowEntries` element that defines a row that displays the values of two properties of the [System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process) object.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="6ae18-127">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="6ae18-127">See Also</span></span>

[<span data-ttu-id="6ae18-128">Creazione di una visualizzazione tabella</span><span class="sxs-lookup"><span data-stu-id="6ae18-128">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="6ae18-129">Elemento Table (formato)</span><span class="sxs-lookup"><span data-stu-id="6ae18-129">TableControl Element (Format)</span></span>](./tablecontrol-element-format.md)

[<span data-ttu-id="6ae18-130">Elemento TableRowEntry (formato)</span><span class="sxs-lookup"><span data-stu-id="6ae18-130">TableRowEntry Element (Format)</span></span>](./tablerowentry-element-for-tablerowentries-for-tablecontrol-format.md)

[<span data-ttu-id="6ae18-131">La scrittura di un File di formattazione di PowerShell</span><span class="sxs-lookup"><span data-stu-id="6ae18-131">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
