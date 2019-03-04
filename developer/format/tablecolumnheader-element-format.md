---
title: Elemento TableColumnHeader (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 49ff3062-6396-4aa8-919b-3fd3ac60899a
caps.latest.revision: 19
ms.openlocfilehash: 15f47c97ac5d55cb76e153af86672b3ffaf176c9
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/03/2019
ms.locfileid: "56858597"
---
# <a name="tablecolumnheader-element-format"></a><span data-ttu-id="d388e-102">Elemento TableColumnHeader (formato)</span><span class="sxs-lookup"><span data-stu-id="d388e-102">TableColumnHeader Element (Format)</span></span>

<span data-ttu-id="d388e-103">Definisce l'etichetta, la larghezza della colonna e l'allineamento dell'etichetta per una colonna della tabella.</span><span class="sxs-lookup"><span data-stu-id="d388e-103">Defines the label, the width of the column, and the alignment of the label for a column of the table.</span></span>

<span data-ttu-id="d388e-104">Elemento (formato) elemento ViewDefinitions (formato) visualizzazione elemento (formato) elemento Table (formato) TableHeaders elemento di configurazione per Table (formato) TableColumnHeader elemento TableHeaders per Table (formato)</span><span class="sxs-lookup"><span data-stu-id="d388e-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) TableControl Element (Format) TableHeaders Element for TableControl (Format) TableColumnHeader Element for TableHeaders for TableControl (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="d388e-105">Sintassi</span><span class="sxs-lookup"><span data-stu-id="d388e-105">Syntax</span></span>

```xml
<TableColumnHeader>
  <Label>DisplayedLabel</Label>
  <Width>NumberOfCharacters</Width>
  <Alignment>Left, Right, or Centered</Alignment>
</TableColumnHeader>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="d388e-106">Attributi ed elementi</span><span class="sxs-lookup"><span data-stu-id="d388e-106">Attributes and Elements</span></span>

<span data-ttu-id="d388e-107">Le sezioni seguenti descrivono gli attributi e gli elementi figlio dell'elemento padre del `TableColumnHeader` elemento.</span><span class="sxs-lookup"><span data-stu-id="d388e-107">The following sections describe attributes, child elements, and the parent element of the `TableColumnHeader` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="d388e-108">Attributes</span><span class="sxs-lookup"><span data-stu-id="d388e-108">Attributes</span></span>

<span data-ttu-id="d388e-109">Nessuna.</span><span class="sxs-lookup"><span data-stu-id="d388e-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="d388e-110">Elementi figlio</span><span class="sxs-lookup"><span data-stu-id="d388e-110">Child Elements</span></span>

|<span data-ttu-id="d388e-111">Elemento</span><span class="sxs-lookup"><span data-stu-id="d388e-111">Element</span></span>|<span data-ttu-id="d388e-112">Description</span><span class="sxs-lookup"><span data-stu-id="d388e-112">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="d388e-113">Elemento Label per TableColumnHeader per Table (formato)</span><span class="sxs-lookup"><span data-stu-id="d388e-113">Label Element For TableColumnHeader for TableControl (Format)</span></span>](./label-element-for-tablecolumnheader-for-tablecontrol-format.md)|<span data-ttu-id="d388e-114">Elemento facoltativo.</span><span class="sxs-lookup"><span data-stu-id="d388e-114">Optional element.</span></span><br /><br /> <span data-ttu-id="d388e-115">Definisce l'etichetta che viene visualizzato nella parte superiore della colonna.</span><span class="sxs-lookup"><span data-stu-id="d388e-115">Defines the label that is displayed at the top of the column.</span></span> <span data-ttu-id="d388e-116">Se viene specificata alcuna etichetta, viene utilizzato il nome della proprietà il cui valore viene visualizzato nelle righe.</span><span class="sxs-lookup"><span data-stu-id="d388e-116">If no label is specified, the name of the property whose value is displayed in the rows is used.</span></span>|
|[<span data-ttu-id="d388e-117">Elemento larghezza per TableColumnHeader per Table (formato)</span><span class="sxs-lookup"><span data-stu-id="d388e-117">Width Element for TableColumnHeader for TableControl (Format)</span></span>](./width-element-for-tablecolumnheader-for-tablecontrol-format.md)|<span data-ttu-id="d388e-118">Elemento obbligatorio.</span><span class="sxs-lookup"><span data-stu-id="d388e-118">Required element.</span></span><br /><br /> <span data-ttu-id="d388e-119">Specifica la larghezza (in caratteri) della colonna.</span><span class="sxs-lookup"><span data-stu-id="d388e-119">Specifies the width (in characters) of the column.</span></span>|
|[<span data-ttu-id="d388e-120">Elemento Alignment per TableColumbnHeader per Table (formato)</span><span class="sxs-lookup"><span data-stu-id="d388e-120">Alignment Element for TableColumbnHeader for TableControl (Format)</span></span>](./alignment-element-for-tablecolumnheader-for-tablecontrol-format.md)|<span data-ttu-id="d388e-121">Elemento facoltativo.</span><span class="sxs-lookup"><span data-stu-id="d388e-121">Optional element.</span></span><br /><br /> <span data-ttu-id="d388e-122">Specifica come viene visualizzata l'etichetta della colonna.</span><span class="sxs-lookup"><span data-stu-id="d388e-122">Specifies how the label of the column is displayed.</span></span> <span data-ttu-id="d388e-123">Se non viene specificato alcun allineamento, l'etichetta è allineata a sinistra.</span><span class="sxs-lookup"><span data-stu-id="d388e-123">If no alignment is specified, the label is aligned on the left.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="d388e-124">Elementi padre</span><span class="sxs-lookup"><span data-stu-id="d388e-124">Parent Elements</span></span>

|<span data-ttu-id="d388e-125">Elemento</span><span class="sxs-lookup"><span data-stu-id="d388e-125">Element</span></span>|<span data-ttu-id="d388e-126">Description</span><span class="sxs-lookup"><span data-stu-id="d388e-126">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="d388e-127">Elemento TableHeaders (formato)</span><span class="sxs-lookup"><span data-stu-id="d388e-127">TableHeaders Element (Format)</span></span>](./tableheaders-element-format.md)|<span data-ttu-id="d388e-128">Definisce le colonne di una visualizzazione tabella.</span><span class="sxs-lookup"><span data-stu-id="d388e-128">Defines the columns of a table view.</span></span>|

## <a name="remarks"></a><span data-ttu-id="d388e-129">Osservazioni</span><span class="sxs-lookup"><span data-stu-id="d388e-129">Remarks</span></span>

<span data-ttu-id="d388e-130">Specificare un'intestazione per ogni colonna della tabella.</span><span class="sxs-lookup"><span data-stu-id="d388e-130">Specify a header for each column of the table.</span></span> <span data-ttu-id="d388e-131">Le colonne vengono visualizzate nell'ordine in cui il `TableColumnHeader` vengono definiti gli elementi.</span><span class="sxs-lookup"><span data-stu-id="d388e-131">The columns are displayed in the order in which the `TableColumnHeader` elements are defined.</span></span>

<span data-ttu-id="d388e-132">Una tabella deve avere lo stesso numero di `TableColumnHeader` elementi come `TableRowEntry` elementi.</span><span class="sxs-lookup"><span data-stu-id="d388e-132">A table must have the same number of `TableColumnHeader` elements as `TableRowEntry` elements.</span></span> <span data-ttu-id="d388e-133">L'intestazione di colonna definisce come viene visualizzato il testo nella parte superiore della tabella.</span><span class="sxs-lookup"><span data-stu-id="d388e-133">The column header defines how the text at the top of the table is displayed.</span></span> <span data-ttu-id="d388e-134">Le voci di riga definiscono quali dati vengono visualizzati nelle righe della tabella.</span><span class="sxs-lookup"><span data-stu-id="d388e-134">The row entries define what data is displayed in the rows of the table.</span></span>

<span data-ttu-id="d388e-135">Per altre informazioni sui componenti di visualizzazione di una tabella, vedere [vista tabella](./creating-a-table-view.md).</span><span class="sxs-lookup"><span data-stu-id="d388e-135">For more information about the components of a table view, see [Table View](./creating-a-table-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="d388e-136">Esempio</span><span class="sxs-lookup"><span data-stu-id="d388e-136">Example</span></span>

<span data-ttu-id="d388e-137">Nell'esempio seguente vengono illustrati due `TableColumnHeader` elementi.</span><span class="sxs-lookup"><span data-stu-id="d388e-137">The following example shows two `TableColumnHeader` elements.</span></span> <span data-ttu-id="d388e-138">Il primo elemento definisce una colonna con etichetta "Column 1", ha una larghezza pari a 16 caratteri e la cui etichetta è allineata a sinistra.</span><span class="sxs-lookup"><span data-stu-id="d388e-138">The first element defines a column whose label is "Column 1", has a width of 16 characters, and whose label is aligned on the left.</span></span> <span data-ttu-id="d388e-139">Il secondo elemento definisce una colonna la cui etichetta è "2 Column", ha una larghezza pari a 10 caratteri e la cui etichetta è centrato nella colonna.</span><span class="sxs-lookup"><span data-stu-id="d388e-139">The second element defines a column whose label is "Column 2", has a width of 10 characters, and whose label is centered in the column.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="d388e-140">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="d388e-140">See Also</span></span>

[<span data-ttu-id="d388e-141">Elemento Alignment per TableColumnHeader per TableContrl (formato)</span><span class="sxs-lookup"><span data-stu-id="d388e-141">Alignment Element for TableColumnHeader for TableContrl (Format)</span></span>](./alignment-element-for-tablecolumnheader-for-tablecontrol-format.md)

[<span data-ttu-id="d388e-142">Creazione di una visualizzazione tabella</span><span class="sxs-lookup"><span data-stu-id="d388e-142">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="d388e-143">Elemento Label per TableColumnHeader per Table (formato)</span><span class="sxs-lookup"><span data-stu-id="d388e-143">Label Element for TableColumnHeader for TableControl (Format)</span></span>](./label-element-for-tablecolumnheader-for-tablecontrol-format.md)

[<span data-ttu-id="d388e-144">Elemento TableHeaders per Table (formato)</span><span class="sxs-lookup"><span data-stu-id="d388e-144">TableHeaders Element for TableControl (Format)</span></span>](./tableheaders-element-format.md)

[<span data-ttu-id="d388e-145">Larghezza per TableColumnHeader per elemento Table (formato)</span><span class="sxs-lookup"><span data-stu-id="d388e-145">Width for TableColumnHeader for TableControl Element (Format)</span></span>](./width-element-for-tablecolumnheader-for-tablecontrol-format.md)

[<span data-ttu-id="d388e-146">La scrittura di un File di formattazione di PowerShell</span><span class="sxs-lookup"><span data-stu-id="d388e-146">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
