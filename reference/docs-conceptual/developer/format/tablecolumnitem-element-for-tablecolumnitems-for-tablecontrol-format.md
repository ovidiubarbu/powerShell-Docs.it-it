---
title: Elemento TableColumnItem per TableColumnItems per Table ((Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ef8395aa-4b31-48c0-a0b8-b481fd0b3738
caps.latest.revision: 15
ms.openlocfilehash: 9e6cffc7476ef01124d95ecbf287d9788b0324c9
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/15/2019
ms.locfileid: "72368230"
---
# <a name="tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format"></a><span data-ttu-id="fda4e-102">Elemento TableColumnItem per TableColumnItems per TableControl (formato)</span><span class="sxs-lookup"><span data-stu-id="fda4e-102">TableColumnItem Element for TableColumnItems for TableControl (Format)</span></span>

<span data-ttu-id="fda4e-103">Definisce la proprietà o lo script il cui valore viene visualizzato nella colonna della riga.</span><span class="sxs-lookup"><span data-stu-id="fda4e-103">Defines the property or script whose value is displayed in the column of the row.</span></span>

<span data-ttu-id="fda4e-104">Elemento Configuration (Format) elemento ViewDefinitions (Format) elemento View (Format) elemento Table ((Format) elemento TableRowEntries per Table ((Format) elemento TableRowEntry per TableRowEntries per Table ((Format) Elemento TableColumnItems per TableControlEntry per l'elemento TableColumnItem di Table ((Format) per TableColumnItems per Table ((Format)</span><span class="sxs-lookup"><span data-stu-id="fda4e-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) TableControl Element (Format) TableRowEntries Element for TableControl (Format) TableRowEntry Element for TableRowEntries for TableControl (Format) TableColumnItems Element for TableControlEntry for TableControl (Format) TableColumnItem Element for TableColumnItems for TableControl (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="fda4e-105">Sintassi</span><span class="sxs-lookup"><span data-stu-id="fda4e-105">Syntax</span></span>

```xml
<TableColumnItem>
  <Alignment>Left, Right, or Center</Alignment>
  <FormatString>FormatPattern</FormatString>
  <PropertyName>Nameof.NetProperty</PropertyName>
  <ScriptBlock>ScriptToEvaluate</ScriptBlock>
</TableColumnItem>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="fda4e-106">Attributi ed elementi</span><span class="sxs-lookup"><span data-stu-id="fda4e-106">Attributes and Elements</span></span>

<span data-ttu-id="fda4e-107">Nelle sezioni seguenti vengono descritti gli attributi, gli elementi figlio e l'elemento padre dell'elemento `TableColumnItem`.</span><span class="sxs-lookup"><span data-stu-id="fda4e-107">The following sections describe the attributes, child elements, and parent element of the `TableColumnItem` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="fda4e-108">Attributi</span><span class="sxs-lookup"><span data-stu-id="fda4e-108">Attributes</span></span>

<span data-ttu-id="fda4e-109">Nessuna.</span><span class="sxs-lookup"><span data-stu-id="fda4e-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="fda4e-110">Elementi figlio</span><span class="sxs-lookup"><span data-stu-id="fda4e-110">Child Elements</span></span>

|<span data-ttu-id="fda4e-111">Elemento</span><span class="sxs-lookup"><span data-stu-id="fda4e-111">Element</span></span>|<span data-ttu-id="fda4e-112">Description</span><span class="sxs-lookup"><span data-stu-id="fda4e-112">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="fda4e-113">Elemento Alignment per TableColumnItem per Table ((Format)</span><span class="sxs-lookup"><span data-stu-id="fda4e-113">Alignment Element for TableColumnItem for TableControl (Format)</span></span>](./alignment-element-for-tablecolumnitem-for-tablecontrol-format.md)|<span data-ttu-id="fda4e-114">Elemento facoltativo.</span><span class="sxs-lookup"><span data-stu-id="fda4e-114">Optional element.</span></span><br /><br /> <span data-ttu-id="fda4e-115">Definisce la modalità di visualizzazione dei dati in una colonna della riga.</span><span class="sxs-lookup"><span data-stu-id="fda4e-115">Defines how the data in a column of the row is displayed.</span></span>|
|[<span data-ttu-id="fda4e-116">Elemento FormatString per TableColumnItem per Table ((Format)</span><span class="sxs-lookup"><span data-stu-id="fda4e-116">FormatString Element for TableColumnItem for TableControl (Format)</span></span>](./formatstring-element-for-tablecolumnitem-for-tablecontrol-format.md)|<span data-ttu-id="fda4e-117">Specifica un modello di formato utilizzato per formattare i dati nella colonna della riga.</span><span class="sxs-lookup"><span data-stu-id="fda4e-117">Specifies a format pattern that is used to format the data in the column of the row.</span></span>|
|[<span data-ttu-id="fda4e-118">Elemento PropertyName per TableColumnItem per Table ((Format)</span><span class="sxs-lookup"><span data-stu-id="fda4e-118">PropertyName Element for TableColumnItem for TableControl (Format)</span></span>](./propertyname-element-for-tablecolumnitem-for-tablecontrol-format.md)|<span data-ttu-id="fda4e-119">Elemento facoltativo.</span><span class="sxs-lookup"><span data-stu-id="fda4e-119">Optional element.</span></span><br /><br /> <span data-ttu-id="fda4e-120">Specifica il nome della proprietà di cui viene visualizzato il valore.</span><span class="sxs-lookup"><span data-stu-id="fda4e-120">Specifies the name of the property whose value is displayed.</span></span>|
|[<span data-ttu-id="fda4e-121">Elemento ScriptBlock per TableColumnItem per Table ((Format)</span><span class="sxs-lookup"><span data-stu-id="fda4e-121">ScriptBlock Element for TableColumnItem for TableControl (Format)</span></span>](./scriptblock-element-for-tablecolumnitem-for-tablecontrol-format.md)|<span data-ttu-id="fda4e-122">Elemento facoltativo.</span><span class="sxs-lookup"><span data-stu-id="fda4e-122">Optional element.</span></span><br /><br /> <span data-ttu-id="fda4e-123">Specifica lo script il cui valore viene visualizzato nella colonna di una riga.</span><span class="sxs-lookup"><span data-stu-id="fda4e-123">Specifies the script whose value is displayed in the column of a row.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="fda4e-124">Elementi padre</span><span class="sxs-lookup"><span data-stu-id="fda4e-124">Parent Elements</span></span>

|<span data-ttu-id="fda4e-125">Elemento</span><span class="sxs-lookup"><span data-stu-id="fda4e-125">Element</span></span>|<span data-ttu-id="fda4e-126">Description</span><span class="sxs-lookup"><span data-stu-id="fda4e-126">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="fda4e-127">Elemento TableColumnItems per TableControlEntry per Table ((Format)</span><span class="sxs-lookup"><span data-stu-id="fda4e-127">TableColumnItems Element for TableControlEntry for TableControl (Format)</span></span>](./tablecolumnitems-element-for-tablerowentry-for-tablecontrol-format.md)|<span data-ttu-id="fda4e-128">Definisce le proprietà o gli script i cui valori vengono visualizzati nella riga.</span><span class="sxs-lookup"><span data-stu-id="fda4e-128">Defines the properties or scripts whose values are displayed in the row.</span></span>|

## <a name="remarks"></a><span data-ttu-id="fda4e-129">Osservazioni</span><span class="sxs-lookup"><span data-stu-id="fda4e-129">Remarks</span></span>

<span data-ttu-id="fda4e-130">È possibile specificare una proprietà di un oggetto o di uno script in ogni colonna della riga.</span><span class="sxs-lookup"><span data-stu-id="fda4e-130">You can specify a property of an object or a script in each column of the row.</span></span> <span data-ttu-id="fda4e-131">Se non vengono specificati elementi figlio, l'elemento è un segnaposto e non viene visualizzato alcun dato.</span><span class="sxs-lookup"><span data-stu-id="fda4e-131">If no child elements are specified, the item is a placeholder, and no data is displayed.</span></span>

<span data-ttu-id="fda4e-132">Per ulteriori informazioni sui componenti di una vista tabella, vedere [creazione di una vista tabella](./creating-a-table-view.md).</span><span class="sxs-lookup"><span data-stu-id="fda4e-132">For more information about the components of a table view, see [Creating a Table View](./creating-a-table-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="fda4e-133">Esempio</span><span class="sxs-lookup"><span data-stu-id="fda4e-133">Example</span></span>

<span data-ttu-id="fda4e-134">Questo esempio mostra un elemento `TableColumnItem` che Visualizza il valore della proprietà `Status` dell'oggetto [System. Diagnostics. Process](/dotnet/api/System.Diagnostics.Process) .</span><span class="sxs-lookup"><span data-stu-id="fda4e-134">This example shows a `TableColumnItem` element that displays the value of the `Status` property of the [System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process) object.</span></span>

```xml
<TableColumnItem>
   <Alignment>Centered</Alignment>
  <PropertyName>Status</PropertyName>
</TableColumnItem>

```

## <a name="see-also"></a><span data-ttu-id="fda4e-135">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="fda4e-135">See Also</span></span>

[<span data-ttu-id="fda4e-136">Creazione di una vista tabella</span><span class="sxs-lookup"><span data-stu-id="fda4e-136">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="fda4e-137">Elemento Alignment per TableColumnItem per Table ((Format)</span><span class="sxs-lookup"><span data-stu-id="fda4e-137">Alignment Element for TableColumnItem for TableControl (Format)</span></span>](./alignment-element-for-tablecolumnitem-for-tablecontrol-format.md)

[<span data-ttu-id="fda4e-138">Elemento TableColumnItems (Format)</span><span class="sxs-lookup"><span data-stu-id="fda4e-138">TableColumnItems Element (Format)</span></span>](./tablecolumnitems-element-for-tablerowentry-for-tablecontrol-format.md)

[<span data-ttu-id="fda4e-139">Elemento FormatString per TableColumnItem per Table ((Format)</span><span class="sxs-lookup"><span data-stu-id="fda4e-139">FormatString Element for TableColumnItem for TableControl (Format)</span></span>](./formatstring-element-for-tablecolumnitem-for-tablecontrol-format.md)

[<span data-ttu-id="fda4e-140">Elemento PropertyName per TableColumnItem per Table ((Format)</span><span class="sxs-lookup"><span data-stu-id="fda4e-140">PropertyName Element for TableColumnItem for TableControl (Format)</span></span>](./propertyname-element-for-tablecolumnitem-for-tablecontrol-format.md)

[<span data-ttu-id="fda4e-141">Elemento ScriptBlock per TableColumnItem per Table ((Format)</span><span class="sxs-lookup"><span data-stu-id="fda4e-141">ScriptBlock Element for TableColumnItem for TableControl (Format)</span></span>](./scriptblock-element-for-tablecolumnitem-for-tablecontrol-format.md)

[<span data-ttu-id="fda4e-142">Scrittura di un file di formattazione di PowerShell</span><span class="sxs-lookup"><span data-stu-id="fda4e-142">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
