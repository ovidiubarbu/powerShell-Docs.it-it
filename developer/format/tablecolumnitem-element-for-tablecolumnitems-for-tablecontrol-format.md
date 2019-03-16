---
title: Elemento TableColumnItem per TableColumnItems per Table (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ef8395aa-4b31-48c0-a0b8-b481fd0b3738
caps.latest.revision: 15
ms.openlocfilehash: 159f943f6bfb33c5403b5714380631351523789f
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/16/2019
ms.locfileid: "58056992"
---
# <a name="tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format"></a><span data-ttu-id="fe2fa-102">Elemento TableColumnItem per TableColumnItems per TableControl (formato)</span><span class="sxs-lookup"><span data-stu-id="fe2fa-102">TableColumnItem Element for TableColumnItems for TableControl (Format)</span></span>

<span data-ttu-id="fe2fa-103">Definisce le proprietà il cui valore viene visualizzato nella colonna della riga di script.</span><span class="sxs-lookup"><span data-stu-id="fe2fa-103">Defines the property or script whose value is displayed in the column of the row.</span></span>

<span data-ttu-id="fe2fa-104">Elemento (formato) elemento ViewDefinitions (formato) visualizzazione elemento (formato) elemento Table (formato) TableRowEntries elemento di configurazione per Table (formato) TableRowEntry elemento TableRowEntries per Table (formato) Elemento TableColumnItems per TableControlEntry per Table (formato) TableColumnItem elemento TableColumnItems per Table (formato)</span><span class="sxs-lookup"><span data-stu-id="fe2fa-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) TableControl Element (Format) TableRowEntries Element for TableControl (Format) TableRowEntry Element for TableRowEntries for TableControl (Format) TableColumnItems Element for TableControlEntry for TableControl (Format) TableColumnItem Element for TableColumnItems for TableControl (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="fe2fa-105">Sintassi</span><span class="sxs-lookup"><span data-stu-id="fe2fa-105">Syntax</span></span>

```xml
<TableColumnItem>
  <Alignment>Left, Right, or Center</Alignment>
  <PropertyName>Nameof.NetProperty</PropertyName>
  <ScriptBlock>ScriptToEvaluate</ScriptBlock>
</TableColumnItem>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="fe2fa-106">Attributi ed elementi</span><span class="sxs-lookup"><span data-stu-id="fe2fa-106">Attributes and Elements</span></span>

<span data-ttu-id="fe2fa-107">Le sezioni seguenti descrivono gli attributi, elementi figlio ed elemento padre dell'elemento di `TableColumnItem` elemento.</span><span class="sxs-lookup"><span data-stu-id="fe2fa-107">The following sections describe the attributes, child elements, and parent element of the `TableColumnItem` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="fe2fa-108">Attributes</span><span class="sxs-lookup"><span data-stu-id="fe2fa-108">Attributes</span></span>

<span data-ttu-id="fe2fa-109">Nessuna.</span><span class="sxs-lookup"><span data-stu-id="fe2fa-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="fe2fa-110">Elementi figlio</span><span class="sxs-lookup"><span data-stu-id="fe2fa-110">Child Elements</span></span>

|<span data-ttu-id="fe2fa-111">Elemento</span><span class="sxs-lookup"><span data-stu-id="fe2fa-111">Element</span></span>|<span data-ttu-id="fe2fa-112">Description</span><span class="sxs-lookup"><span data-stu-id="fe2fa-112">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="fe2fa-113">Elemento Alignment per TableColumnItem per Table (formato)</span><span class="sxs-lookup"><span data-stu-id="fe2fa-113">Alignment Element for TableColumnItem for TableControl (Format)</span></span>](./alignment-element-for-tablecolumnitem-for-tablecontrol-format.md)|<span data-ttu-id="fe2fa-114">Elemento facoltativo.</span><span class="sxs-lookup"><span data-stu-id="fe2fa-114">Optional element.</span></span><br /><br /> <span data-ttu-id="fe2fa-115">Definisce la modalità di visualizzazione di dati in una colonna della riga.</span><span class="sxs-lookup"><span data-stu-id="fe2fa-115">Defines how the data in a column of the row is displayed.</span></span>|
|[<span data-ttu-id="fe2fa-116">Elemento FormatString per TableColumnItem per Table (formato)</span><span class="sxs-lookup"><span data-stu-id="fe2fa-116">FormatString Element for TableColumnItem for TableControl (Format)</span></span>](./formatstring-element-for-tablecolumnitem-for-tablecontrol-format.md)|<span data-ttu-id="fe2fa-117">Specifica uno schema di formattazione che consente di formattare i dati della colonna della riga.</span><span class="sxs-lookup"><span data-stu-id="fe2fa-117">Specifies a format pattern that is used to format the data in the column of the row.</span></span>|
|[<span data-ttu-id="fe2fa-118">Elemento PropertyName per TableColumnItem per Table (formato)</span><span class="sxs-lookup"><span data-stu-id="fe2fa-118">PropertyName Element for TableColumnItem for TableControl (Format)</span></span>](./propertyname-element-for-tablecolumnitem-for-tablecontrol-format.md)|<span data-ttu-id="fe2fa-119">Elemento facoltativo.</span><span class="sxs-lookup"><span data-stu-id="fe2fa-119">Optional element.</span></span><br /><br /> <span data-ttu-id="fe2fa-120">Specifica il nome della proprietà il cui valore viene visualizzato.</span><span class="sxs-lookup"><span data-stu-id="fe2fa-120">Specifies the name of the property whose value is displayed.</span></span>|
|[<span data-ttu-id="fe2fa-121">Elemento ScriptBlock per TableColumnItem per Table (formato)</span><span class="sxs-lookup"><span data-stu-id="fe2fa-121">ScriptBlock Element for TableColumnItem for TableControl (Format)</span></span>](./scriptblock-element-for-tablecolumnitem-for-tablecontrol-format.md)|<span data-ttu-id="fe2fa-122">Elemento facoltativo.</span><span class="sxs-lookup"><span data-stu-id="fe2fa-122">Optional element.</span></span><br /><br /> <span data-ttu-id="fe2fa-123">Specifica lo script il cui valore viene visualizzato nella colonna di una riga.</span><span class="sxs-lookup"><span data-stu-id="fe2fa-123">Specifies the script whose value is displayed in the column of a row.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="fe2fa-124">Elementi padre</span><span class="sxs-lookup"><span data-stu-id="fe2fa-124">Parent Elements</span></span>

|<span data-ttu-id="fe2fa-125">Elemento</span><span class="sxs-lookup"><span data-stu-id="fe2fa-125">Element</span></span>|<span data-ttu-id="fe2fa-126">Description</span><span class="sxs-lookup"><span data-stu-id="fe2fa-126">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="fe2fa-127">Elemento TableColumnItems per TableControlEntry per Table (formato)</span><span class="sxs-lookup"><span data-stu-id="fe2fa-127">TableColumnItems Element for TableControlEntry for TableControl (Format)</span></span>](./tablecolumnitems-element-for-tablerowentry-for-tablecontrol-format.md)|<span data-ttu-id="fe2fa-128">Definisce le proprietà o gli script i cui valori vengono visualizzati nella riga.</span><span class="sxs-lookup"><span data-stu-id="fe2fa-128">Defines the properties or scripts whose values are displayed in the row.</span></span>|

## <a name="remarks"></a><span data-ttu-id="fe2fa-129">Osservazioni</span><span class="sxs-lookup"><span data-stu-id="fe2fa-129">Remarks</span></span>

<span data-ttu-id="fe2fa-130">È possibile specificare una proprietà di un oggetto o uno script in ogni colonna della riga.</span><span class="sxs-lookup"><span data-stu-id="fe2fa-130">You can specify a property of an object or a script in each column of the row.</span></span> <span data-ttu-id="fe2fa-131">Se nessun elemento figlio viene specificato, l'elemento è un segnaposto e non vengono visualizzati dati.</span><span class="sxs-lookup"><span data-stu-id="fe2fa-131">If no child elements are specified, the item is a placeholder, and no data is displayed.</span></span>

<span data-ttu-id="fe2fa-132">Per altre informazioni sui componenti di visualizzazione di una tabella, vedere [creazione di una visualizzazione tabella](./creating-a-table-view.md).</span><span class="sxs-lookup"><span data-stu-id="fe2fa-132">For more information about the components of a table view, see [Creating a Table View](./creating-a-table-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="fe2fa-133">Esempio</span><span class="sxs-lookup"><span data-stu-id="fe2fa-133">Example</span></span>

<span data-ttu-id="fe2fa-134">Questo esempio viene illustrato un `TableColumnItem` elemento che viene visualizzato il valore della `Status` proprietà del [Diagnostics](/dotnet/api/System.Diagnostics.Process) oggetto.</span><span class="sxs-lookup"><span data-stu-id="fe2fa-134">This example shows a `TableColumnItem` element that displays the value of the `Status` property of the [System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process) object.</span></span>

```xml
<TableColumnItem>
   <Alignment>Centered</Alignment>
  <PropertyName>Status</PropertyName>
</TableColumnItem>

```

## <a name="see-also"></a><span data-ttu-id="fe2fa-135">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="fe2fa-135">See Also</span></span>

[<span data-ttu-id="fe2fa-136">Creazione di una visualizzazione tabella</span><span class="sxs-lookup"><span data-stu-id="fe2fa-136">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="fe2fa-137">Elemento Alignment per TableColumnItem per Table (formato)</span><span class="sxs-lookup"><span data-stu-id="fe2fa-137">Alignment Element for TableColumnItem for TableControl (Format)</span></span>](./alignment-element-for-tablecolumnitem-for-tablecontrol-format.md)

[<span data-ttu-id="fe2fa-138">Elemento TableColumnItems (formato)</span><span class="sxs-lookup"><span data-stu-id="fe2fa-138">TableColumnItems Element (Format)</span></span>](./tablecolumnitems-element-for-tablerowentry-for-tablecontrol-format.md)

[<span data-ttu-id="fe2fa-139">Elemento FormatString per TableColumnItem per Table (formato)</span><span class="sxs-lookup"><span data-stu-id="fe2fa-139">FormatString Element for TableColumnItem for TableControl (Format)</span></span>](./formatstring-element-for-tablecolumnitem-for-tablecontrol-format.md)

[<span data-ttu-id="fe2fa-140">Elemento PropertyName per TableColumnItem per Table (formato)</span><span class="sxs-lookup"><span data-stu-id="fe2fa-140">PropertyName Element for TableColumnItem for TableControl (Format)</span></span>](./propertyname-element-for-tablecolumnitem-for-tablecontrol-format.md)

[<span data-ttu-id="fe2fa-141">Elemento ScriptBlock per TableColumnItem per Table (formato)</span><span class="sxs-lookup"><span data-stu-id="fe2fa-141">ScriptBlock Element for TableColumnItem for TableControl (Format)</span></span>](./scriptblock-element-for-tablecolumnitem-for-tablecontrol-format.md)

[<span data-ttu-id="fe2fa-142">La scrittura di un File di formattazione di PowerShell</span><span class="sxs-lookup"><span data-stu-id="fe2fa-142">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
