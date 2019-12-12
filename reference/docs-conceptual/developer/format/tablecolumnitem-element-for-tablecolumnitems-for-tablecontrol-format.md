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
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/05/2019
ms.locfileid: "72368230"
---
# <a name="tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format"></a><span data-ttu-id="0970b-102">Elemento TableColumnItem per TableColumnItems per TableControl (formato)</span><span class="sxs-lookup"><span data-stu-id="0970b-102">TableColumnItem Element for TableColumnItems for TableControl (Format)</span></span>

<span data-ttu-id="0970b-103">Definisce la proprietà o lo script il cui valore viene visualizzato nella colonna della riga.</span><span class="sxs-lookup"><span data-stu-id="0970b-103">Defines the property or script whose value is displayed in the column of the row.</span></span>

<span data-ttu-id="0970b-104">Elemento Configuration (Format) elemento ViewDefinitions (Format) elemento View (Format) elemento Table ((Format) elemento TableRowEntries per Table ((Format) elemento TableRowEntry per TableRowEntries per Table ((Format) Elemento TableColumnItems per TableControlEntry per l'elemento TableColumnItem di Table ((Format) per TableColumnItems per Table ((Format)</span><span class="sxs-lookup"><span data-stu-id="0970b-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) TableControl Element (Format) TableRowEntries Element for TableControl (Format) TableRowEntry Element for TableRowEntries for TableControl (Format) TableColumnItems Element for TableControlEntry for TableControl (Format) TableColumnItem Element for TableColumnItems for TableControl (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="0970b-105">Sintassi</span><span class="sxs-lookup"><span data-stu-id="0970b-105">Syntax</span></span>

```xml
<TableColumnItem>
  <Alignment>Left, Right, or Center</Alignment>
  <FormatString>FormatPattern</FormatString>
  <PropertyName>Nameof.NetProperty</PropertyName>
  <ScriptBlock>ScriptToEvaluate</ScriptBlock>
</TableColumnItem>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="0970b-106">Attributi ed elementi</span><span class="sxs-lookup"><span data-stu-id="0970b-106">Attributes and Elements</span></span>

<span data-ttu-id="0970b-107">Nelle sezioni seguenti vengono descritti gli attributi, gli elementi figlio e l'elemento padre dell'elemento `TableColumnItem`.</span><span class="sxs-lookup"><span data-stu-id="0970b-107">The following sections describe the attributes, child elements, and parent element of the `TableColumnItem` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="0970b-108">Attributi</span><span class="sxs-lookup"><span data-stu-id="0970b-108">Attributes</span></span>

<span data-ttu-id="0970b-109">Nessuna.</span><span class="sxs-lookup"><span data-stu-id="0970b-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="0970b-110">Elementi figlio</span><span class="sxs-lookup"><span data-stu-id="0970b-110">Child Elements</span></span>

|<span data-ttu-id="0970b-111">Elemento</span><span class="sxs-lookup"><span data-stu-id="0970b-111">Element</span></span>|<span data-ttu-id="0970b-112">Description</span><span class="sxs-lookup"><span data-stu-id="0970b-112">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="0970b-113">Elemento Alignment per TableColumnItem per Table ((Format)</span><span class="sxs-lookup"><span data-stu-id="0970b-113">Alignment Element for TableColumnItem for TableControl (Format)</span></span>](./alignment-element-for-tablecolumnitem-for-tablecontrol-format.md)|<span data-ttu-id="0970b-114">Elemento facoltativo.</span><span class="sxs-lookup"><span data-stu-id="0970b-114">Optional element.</span></span><br /><br /> <span data-ttu-id="0970b-115">Definisce la modalità di visualizzazione dei dati in una colonna della riga.</span><span class="sxs-lookup"><span data-stu-id="0970b-115">Defines how the data in a column of the row is displayed.</span></span>|
|[<span data-ttu-id="0970b-116">Elemento FormatString per TableColumnItem per Table ((Format)</span><span class="sxs-lookup"><span data-stu-id="0970b-116">FormatString Element for TableColumnItem for TableControl (Format)</span></span>](./formatstring-element-for-tablecolumnitem-for-tablecontrol-format.md)|<span data-ttu-id="0970b-117">Specifica un modello di formato utilizzato per formattare i dati nella colonna della riga.</span><span class="sxs-lookup"><span data-stu-id="0970b-117">Specifies a format pattern that is used to format the data in the column of the row.</span></span>|
|[<span data-ttu-id="0970b-118">Elemento PropertyName per TableColumnItem per Table ((Format)</span><span class="sxs-lookup"><span data-stu-id="0970b-118">PropertyName Element for TableColumnItem for TableControl (Format)</span></span>](./propertyname-element-for-tablecolumnitem-for-tablecontrol-format.md)|<span data-ttu-id="0970b-119">Elemento facoltativo.</span><span class="sxs-lookup"><span data-stu-id="0970b-119">Optional element.</span></span><br /><br /> <span data-ttu-id="0970b-120">Specifica il nome della proprietà di cui viene visualizzato il valore.</span><span class="sxs-lookup"><span data-stu-id="0970b-120">Specifies the name of the property whose value is displayed.</span></span>|
|[<span data-ttu-id="0970b-121">Elemento ScriptBlock per TableColumnItem per Table ((Format)</span><span class="sxs-lookup"><span data-stu-id="0970b-121">ScriptBlock Element for TableColumnItem for TableControl (Format)</span></span>](./scriptblock-element-for-tablecolumnitem-for-tablecontrol-format.md)|<span data-ttu-id="0970b-122">Elemento facoltativo.</span><span class="sxs-lookup"><span data-stu-id="0970b-122">Optional element.</span></span><br /><br /> <span data-ttu-id="0970b-123">Specifica lo script il cui valore viene visualizzato nella colonna di una riga.</span><span class="sxs-lookup"><span data-stu-id="0970b-123">Specifies the script whose value is displayed in the column of a row.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="0970b-124">Elementi padre</span><span class="sxs-lookup"><span data-stu-id="0970b-124">Parent Elements</span></span>

|<span data-ttu-id="0970b-125">Elemento</span><span class="sxs-lookup"><span data-stu-id="0970b-125">Element</span></span>|<span data-ttu-id="0970b-126">Description</span><span class="sxs-lookup"><span data-stu-id="0970b-126">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="0970b-127">Elemento TableColumnItems per TableControlEntry per Table ((Format)</span><span class="sxs-lookup"><span data-stu-id="0970b-127">TableColumnItems Element for TableControlEntry for TableControl (Format)</span></span>](./tablecolumnitems-element-for-tablerowentry-for-tablecontrol-format.md)|<span data-ttu-id="0970b-128">Definisce le proprietà o gli script i cui valori vengono visualizzati nella riga.</span><span class="sxs-lookup"><span data-stu-id="0970b-128">Defines the properties or scripts whose values are displayed in the row.</span></span>|

## <a name="remarks"></a><span data-ttu-id="0970b-129">Osservazioni</span><span class="sxs-lookup"><span data-stu-id="0970b-129">Remarks</span></span>

<span data-ttu-id="0970b-130">È possibile specificare una proprietà di un oggetto o di uno script in ogni colonna della riga.</span><span class="sxs-lookup"><span data-stu-id="0970b-130">You can specify a property of an object or a script in each column of the row.</span></span> <span data-ttu-id="0970b-131">Se non vengono specificati elementi figlio, l'elemento è un segnaposto e non viene visualizzato alcun dato.</span><span class="sxs-lookup"><span data-stu-id="0970b-131">If no child elements are specified, the item is a placeholder, and no data is displayed.</span></span>

<span data-ttu-id="0970b-132">Per ulteriori informazioni sui componenti di una vista tabella, vedere [creazione di una vista tabella](./creating-a-table-view.md).</span><span class="sxs-lookup"><span data-stu-id="0970b-132">For more information about the components of a table view, see [Creating a Table View](./creating-a-table-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="0970b-133">Esempio</span><span class="sxs-lookup"><span data-stu-id="0970b-133">Example</span></span>

<span data-ttu-id="0970b-134">Questo esempio illustra un elemento `TableColumnItem` che Visualizza il valore della proprietà `Status` dell'oggetto [System. Diagnostics. Process](/dotnet/api/System.Diagnostics.Process) .</span><span class="sxs-lookup"><span data-stu-id="0970b-134">This example shows a `TableColumnItem` element that displays the value of the `Status` property of the [System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process) object.</span></span>

```xml
<TableColumnItem>
   <Alignment>Centered</Alignment>
  <PropertyName>Status</PropertyName>
</TableColumnItem>

```

## <a name="see-also"></a><span data-ttu-id="0970b-135">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="0970b-135">See Also</span></span>

[<span data-ttu-id="0970b-136">Creazione di una vista tabella</span><span class="sxs-lookup"><span data-stu-id="0970b-136">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="0970b-137">Elemento Alignment per TableColumnItem per Table ((Format)</span><span class="sxs-lookup"><span data-stu-id="0970b-137">Alignment Element for TableColumnItem for TableControl (Format)</span></span>](./alignment-element-for-tablecolumnitem-for-tablecontrol-format.md)

[<span data-ttu-id="0970b-138">Elemento TableColumnItems (Format)</span><span class="sxs-lookup"><span data-stu-id="0970b-138">TableColumnItems Element (Format)</span></span>](./tablecolumnitems-element-for-tablerowentry-for-tablecontrol-format.md)

[<span data-ttu-id="0970b-139">Elemento FormatString per TableColumnItem per Table ((Format)</span><span class="sxs-lookup"><span data-stu-id="0970b-139">FormatString Element for TableColumnItem for TableControl (Format)</span></span>](./formatstring-element-for-tablecolumnitem-for-tablecontrol-format.md)

[<span data-ttu-id="0970b-140">Elemento PropertyName per TableColumnItem per Table ((Format)</span><span class="sxs-lookup"><span data-stu-id="0970b-140">PropertyName Element for TableColumnItem for TableControl (Format)</span></span>](./propertyname-element-for-tablecolumnitem-for-tablecontrol-format.md)

[<span data-ttu-id="0970b-141">Elemento ScriptBlock per TableColumnItem per Table ((Format)</span><span class="sxs-lookup"><span data-stu-id="0970b-141">ScriptBlock Element for TableColumnItem for TableControl (Format)</span></span>](./scriptblock-element-for-tablecolumnitem-for-tablecontrol-format.md)

[<span data-ttu-id="0970b-142">Scrittura di un file di formattazione di PowerShell</span><span class="sxs-lookup"><span data-stu-id="0970b-142">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
