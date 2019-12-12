---
title: Elemento TableColumnHeader (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 49ff3062-6396-4aa8-919b-3fd3ac60899a
caps.latest.revision: 19
ms.openlocfilehash: d3ad7fa563def17d43ce4dc64d155b65b650521f
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/05/2019
ms.locfileid: "72361850"
---
# <a name="tablecolumnheader-element-format"></a><span data-ttu-id="e9436-102">Elemento TableColumnHeader (formato)</span><span class="sxs-lookup"><span data-stu-id="e9436-102">TableColumnHeader Element (Format)</span></span>

<span data-ttu-id="e9436-103">Definisce l'etichetta, la larghezza della colonna e l'allineamento dell'etichetta per una colonna della tabella.</span><span class="sxs-lookup"><span data-stu-id="e9436-103">Defines the label, the width of the column, and the alignment of the label for a column of the table.</span></span>

<span data-ttu-id="e9436-104">Elemento Configuration (Format) elemento ViewDefinitions (Format) elemento View (Format) elemento Table ((Format) elemento TableHeaders per Table ((Format) elemento TableColumnHeader per TableHeaders per Table ((Format)</span><span class="sxs-lookup"><span data-stu-id="e9436-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) TableControl Element (Format) TableHeaders Element for TableControl (Format) TableColumnHeader Element for TableHeaders for TableControl (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="e9436-105">Sintassi</span><span class="sxs-lookup"><span data-stu-id="e9436-105">Syntax</span></span>

```xml
<TableColumnHeader>
  <Label>DisplayedLabel</Label>
  <Width>NumberOfCharacters</Width>
  <Alignment>Left, Right, or Centered</Alignment>
</TableColumnHeader>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="e9436-106">Attributi ed elementi</span><span class="sxs-lookup"><span data-stu-id="e9436-106">Attributes and Elements</span></span>

<span data-ttu-id="e9436-107">Nelle sezioni seguenti vengono descritti gli attributi, gli elementi figlio e l'elemento padre dell'elemento `TableColumnHeader`.</span><span class="sxs-lookup"><span data-stu-id="e9436-107">The following sections describe attributes, child elements, and the parent element of the `TableColumnHeader` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="e9436-108">Attributi</span><span class="sxs-lookup"><span data-stu-id="e9436-108">Attributes</span></span>

<span data-ttu-id="e9436-109">Nessuna.</span><span class="sxs-lookup"><span data-stu-id="e9436-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="e9436-110">Elementi figlio</span><span class="sxs-lookup"><span data-stu-id="e9436-110">Child Elements</span></span>

|<span data-ttu-id="e9436-111">Elemento</span><span class="sxs-lookup"><span data-stu-id="e9436-111">Element</span></span>|<span data-ttu-id="e9436-112">Description</span><span class="sxs-lookup"><span data-stu-id="e9436-112">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="e9436-113">Elemento label per TableColumnHeader per Table ((Format)</span><span class="sxs-lookup"><span data-stu-id="e9436-113">Label Element For TableColumnHeader for TableControl (Format)</span></span>](./label-element-for-tablecolumnheader-for-tablecontrol-format.md)|<span data-ttu-id="e9436-114">Elemento facoltativo.</span><span class="sxs-lookup"><span data-stu-id="e9436-114">Optional element.</span></span><br /><br /> <span data-ttu-id="e9436-115">Definisce l'etichetta visualizzata nella parte superiore della colonna.</span><span class="sxs-lookup"><span data-stu-id="e9436-115">Defines the label that is displayed at the top of the column.</span></span> <span data-ttu-id="e9436-116">Se non viene specificata alcuna etichetta, viene usato il nome della proprietà il cui valore viene visualizzato nelle righe.</span><span class="sxs-lookup"><span data-stu-id="e9436-116">If no label is specified, the name of the property whose value is displayed in the rows is used.</span></span>|
|[<span data-ttu-id="e9436-117">Elemento Width per TableColumnHeader per Table ((Format)</span><span class="sxs-lookup"><span data-stu-id="e9436-117">Width Element for TableColumnHeader for TableControl (Format)</span></span>](./width-element-for-tablecolumnheader-for-tablecontrol-format.md)|<span data-ttu-id="e9436-118">Elemento obbligatorio.</span><span class="sxs-lookup"><span data-stu-id="e9436-118">Required element.</span></span><br /><br /> <span data-ttu-id="e9436-119">Specifica la larghezza (in caratteri) della colonna.</span><span class="sxs-lookup"><span data-stu-id="e9436-119">Specifies the width (in characters) of the column.</span></span>|
|[<span data-ttu-id="e9436-120">Elemento Alignment per TableColumnHeader per Table ((Format)</span><span class="sxs-lookup"><span data-stu-id="e9436-120">Alignment Element for TableColumnHeader for TableControl (Format)</span></span>](./alignment-element-for-tablecolumnheader-for-tablecontrol-format.md)|<span data-ttu-id="e9436-121">Elemento facoltativo.</span><span class="sxs-lookup"><span data-stu-id="e9436-121">Optional element.</span></span><br /><br /> <span data-ttu-id="e9436-122">Specifica la modalità di visualizzazione dell'etichetta della colonna.</span><span class="sxs-lookup"><span data-stu-id="e9436-122">Specifies how the label of the column is displayed.</span></span> <span data-ttu-id="e9436-123">Se non viene specificato alcun allineamento, l'etichetta viene allineata a sinistra.</span><span class="sxs-lookup"><span data-stu-id="e9436-123">If no alignment is specified, the label is aligned on the left.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="e9436-124">Elementi padre</span><span class="sxs-lookup"><span data-stu-id="e9436-124">Parent Elements</span></span>

|<span data-ttu-id="e9436-125">Elemento</span><span class="sxs-lookup"><span data-stu-id="e9436-125">Element</span></span>|<span data-ttu-id="e9436-126">Description</span><span class="sxs-lookup"><span data-stu-id="e9436-126">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="e9436-127">Elemento TableHeaders (Format)</span><span class="sxs-lookup"><span data-stu-id="e9436-127">TableHeaders Element (Format)</span></span>](./tableheaders-element-format.md)|<span data-ttu-id="e9436-128">Definisce le colonne di una visualizzazione tabella.</span><span class="sxs-lookup"><span data-stu-id="e9436-128">Defines the columns of a table view.</span></span>|

## <a name="remarks"></a><span data-ttu-id="e9436-129">Osservazioni</span><span class="sxs-lookup"><span data-stu-id="e9436-129">Remarks</span></span>

<span data-ttu-id="e9436-130">Specificare un'intestazione per ogni colonna della tabella.</span><span class="sxs-lookup"><span data-stu-id="e9436-130">Specify a header for each column of the table.</span></span> <span data-ttu-id="e9436-131">Le colonne vengono visualizzate nell'ordine in cui sono definiti gli elementi `TableColumnHeader`.</span><span class="sxs-lookup"><span data-stu-id="e9436-131">The columns are displayed in the order in which the `TableColumnHeader` elements are defined.</span></span>

<span data-ttu-id="e9436-132">Una tabella deve avere lo stesso numero di elementi `TableColumnHeader` `TableRowEntry` elementi.</span><span class="sxs-lookup"><span data-stu-id="e9436-132">A table must have the same number of `TableColumnHeader` elements as `TableRowEntry` elements.</span></span> <span data-ttu-id="e9436-133">L'intestazione di colonna definisce il modo in cui viene visualizzato il testo nella parte superiore della tabella.</span><span class="sxs-lookup"><span data-stu-id="e9436-133">The column header defines how the text at the top of the table is displayed.</span></span> <span data-ttu-id="e9436-134">Le voci di riga definiscono quali dati vengono visualizzati nelle righe della tabella.</span><span class="sxs-lookup"><span data-stu-id="e9436-134">The row entries define what data is displayed in the rows of the table.</span></span>

<span data-ttu-id="e9436-135">Per ulteriori informazioni sui componenti di una vista tabella, vedere [visualizzazione tabella](./creating-a-table-view.md).</span><span class="sxs-lookup"><span data-stu-id="e9436-135">For more information about the components of a table view, see [Table View](./creating-a-table-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="e9436-136">Esempio</span><span class="sxs-lookup"><span data-stu-id="e9436-136">Example</span></span>

<span data-ttu-id="e9436-137">Nell'esempio seguente vengono illustrati due elementi `TableColumnHeader`.</span><span class="sxs-lookup"><span data-stu-id="e9436-137">The following example shows two `TableColumnHeader` elements.</span></span> <span data-ttu-id="e9436-138">Il primo elemento definisce una colonna la cui etichetta è "Column 1", ha una larghezza di 16 caratteri e la cui etichetta è allineata a sinistra.</span><span class="sxs-lookup"><span data-stu-id="e9436-138">The first element defines a column whose label is "Column 1", has a width of 16 characters, and whose label is aligned on the left.</span></span> <span data-ttu-id="e9436-139">Il secondo elemento definisce una colonna la cui etichetta è "Column 2", ha una larghezza di 10 caratteri e la cui etichetta è centrata nella colonna.</span><span class="sxs-lookup"><span data-stu-id="e9436-139">The second element defines a column whose label is "Column 2", has a width of 10 characters, and whose label is centered in the column.</span></span>

```xml
<TableHeaders>
  <TableColumnHeader>
    <Label>Column 1</Label)
    <Width>16</Width>
    <Alignment>Left</Alignment>
  </TableColumnHeader>
    <TableColumnHeader>
    <Label>Column 2</Label)
    <Width>10</Width>
    <Alignment>Centered</Alignment>
  </TableColumnHeader>
</TableHeaders>
```

## <a name="see-also"></a><span data-ttu-id="e9436-140">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="e9436-140">See Also</span></span>

[<span data-ttu-id="e9436-141">Elemento Alignment per TableColumnHeader per Table ((Format)</span><span class="sxs-lookup"><span data-stu-id="e9436-141">Alignment Element for TableColumnHeader for TableControl (Format)</span></span>](./alignment-element-for-tablecolumnheader-for-tablecontrol-format.md)

[<span data-ttu-id="e9436-142">Creazione di una vista tabella</span><span class="sxs-lookup"><span data-stu-id="e9436-142">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="e9436-143">Elemento label per TableColumnHeader per Table ((Format)</span><span class="sxs-lookup"><span data-stu-id="e9436-143">Label Element for TableColumnHeader for TableControl (Format)</span></span>](./label-element-for-tablecolumnheader-for-tablecontrol-format.md)

[<span data-ttu-id="e9436-144">Elemento TableHeaders per Table ((Format)</span><span class="sxs-lookup"><span data-stu-id="e9436-144">TableHeaders Element for TableControl (Format)</span></span>](./tableheaders-element-format.md)

[<span data-ttu-id="e9436-145">Width per TableColumnHeader per l'elemento Table ((Format)</span><span class="sxs-lookup"><span data-stu-id="e9436-145">Width for TableColumnHeader for TableControl Element (Format)</span></span>](./width-element-for-tablecolumnheader-for-tablecontrol-format.md)

[<span data-ttu-id="e9436-146">Scrittura di un file di formattazione di PowerShell</span><span class="sxs-lookup"><span data-stu-id="e9436-146">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
