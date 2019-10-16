---
title: Elemento TableColumnItems per TableRowEntry per Table ((Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d43684ce-7c3d-4d14-8dbd-061c111ee805
caps.latest.revision: 12
ms.openlocfilehash: d05437aaa9652e7f81d0854d1a746acffe145699
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/15/2019
ms.locfileid: "72361810"
---
# <a name="tablecolumnitems-element-for-tablerowentry-for-tablecontrol-format"></a><span data-ttu-id="98048-102">Elemento TableColumnItems per TableRowEntry per TableControl (formato)</span><span class="sxs-lookup"><span data-stu-id="98048-102">TableColumnItems Element for TableRowEntry for TableControl (Format)</span></span>

<span data-ttu-id="98048-103">Definisce le proprietà o gli script i cui valori sono visualizzati in una riga.</span><span class="sxs-lookup"><span data-stu-id="98048-103">Defines the properties or scripts whose values are displayed in a row.</span></span>

<span data-ttu-id="98048-104">Elemento Configuration (Format) elemento ViewDefinitions (Format) elemento View (Format) elemento Table ((Format) elemento TableRowEntries per Table ((Format) elemento TableRowEntry per TableRowEntries per Table ((Format) Elemento TableColumnItems per TableControlEntry per Table ((Format)</span><span class="sxs-lookup"><span data-stu-id="98048-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) TableControl Element (Format) TableRowEntries Element for TableControl (Format) TableRowEntry Element for TableRowEntries for TableControl (Format) TableColumnItems Element for TableControlEntry for TableControl (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="98048-105">Sintassi</span><span class="sxs-lookup"><span data-stu-id="98048-105">Syntax</span></span>

```xml
TableColumnItems>
  <TableColumnItem>...</TableColumnItem>
</TableColumnItems>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="98048-106">Attributi ed elementi</span><span class="sxs-lookup"><span data-stu-id="98048-106">Attributes and Elements</span></span>

<span data-ttu-id="98048-107">Nelle sezioni seguenti vengono descritti gli attributi, gli elementi figlio e l'elemento padre dell'elemento `TableColumnItems`.</span><span class="sxs-lookup"><span data-stu-id="98048-107">The following sections describe the attributes, child elements, and parent element of the `TableColumnItems` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="98048-108">Attributi</span><span class="sxs-lookup"><span data-stu-id="98048-108">Attributes</span></span>

<span data-ttu-id="98048-109">Nessuna.</span><span class="sxs-lookup"><span data-stu-id="98048-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="98048-110">Elementi figlio</span><span class="sxs-lookup"><span data-stu-id="98048-110">Child Elements</span></span>

|<span data-ttu-id="98048-111">Elemento</span><span class="sxs-lookup"><span data-stu-id="98048-111">Element</span></span>|<span data-ttu-id="98048-112">Description</span><span class="sxs-lookup"><span data-stu-id="98048-112">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="98048-113">Elemento TableColumnItem per TableColumnItems per Table ((Format)</span><span class="sxs-lookup"><span data-stu-id="98048-113">TableColumnItem Element for TableColumnItems for TableControl (Format)</span></span>](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md)|<span data-ttu-id="98048-114">Elemento obbligatorio.</span><span class="sxs-lookup"><span data-stu-id="98048-114">Required element.</span></span><br /><br /> <span data-ttu-id="98048-115">Definisce la proprietà o lo script il cui valore viene visualizzato in una colonna della riga.</span><span class="sxs-lookup"><span data-stu-id="98048-115">Defines the property or script whose value is displayed in a column of the row.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="98048-116">Elementi padre</span><span class="sxs-lookup"><span data-stu-id="98048-116">Parent Elements</span></span>

|<span data-ttu-id="98048-117">Elemento</span><span class="sxs-lookup"><span data-stu-id="98048-117">Element</span></span>|<span data-ttu-id="98048-118">Description</span><span class="sxs-lookup"><span data-stu-id="98048-118">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="98048-119">Elemento TableRowEntry per TableRowEntries per Table ((Format)</span><span class="sxs-lookup"><span data-stu-id="98048-119">TableRowEntry Element for TableRowEntries for TableControl (Format)</span></span>](./tablerowentry-element-for-tablerowentries-for-tablecontrol-format.md)|<span data-ttu-id="98048-120">Definisce i dati visualizzati in una riga della tabella.</span><span class="sxs-lookup"><span data-stu-id="98048-120">Defines the data that is displayed in a row of the table.</span></span>|

## <a name="remarks"></a><span data-ttu-id="98048-121">Osservazioni</span><span class="sxs-lookup"><span data-stu-id="98048-121">Remarks</span></span>

<span data-ttu-id="98048-122">È necessario un elemento `TableColumnItem` per ogni colonna della riga.</span><span class="sxs-lookup"><span data-stu-id="98048-122">A `TableColumnItem` element is required for each column of the row.</span></span> <span data-ttu-id="98048-123">La prima voce viene visualizzata nella prima colonna, nella seconda voce della seconda colonna e così via.</span><span class="sxs-lookup"><span data-stu-id="98048-123">The first entry is displayed in first column, the second entry in the second column, and so on.</span></span>

<span data-ttu-id="98048-124">Per ulteriori informazioni sui componenti di una vista tabella, vedere [creazione di una vista tabella](./creating-a-table-view.md).</span><span class="sxs-lookup"><span data-stu-id="98048-124">For more information about the components of a table view, see [Creating a Table View](./creating-a-table-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="98048-125">Esempio</span><span class="sxs-lookup"><span data-stu-id="98048-125">Example</span></span>

<span data-ttu-id="98048-126">Nell'esempio seguente viene illustrato un elemento `TableColumnItems` che definisce tre proprietà dell'oggetto [System. Diagnostics. Process](/dotnet/api/System.Diagnostics.Process) .</span><span class="sxs-lookup"><span data-stu-id="98048-126">The following example shows a `TableColumnItems` element that defines three properties of the [System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process) object.</span></span>

```xml
<TableColumnItems>
  <TableColumnItem>
    <PropertyName>Status</PropertyName>
  </TableColumnItem>
  <TableColumnItem>
    <PropertyName>Name</PropertyName>
  </TableColumnItem>
  <TableColumnItem>
    <PropertyName>DisplayName</PropertyName>
  </TableColumnItem>
</TableColumnItems>

```

## <a name="see-also"></a><span data-ttu-id="98048-127">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="98048-127">See Also</span></span>

[<span data-ttu-id="98048-128">Creazione di una vista tabella</span><span class="sxs-lookup"><span data-stu-id="98048-128">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="98048-129">Elemento TableColumnItem (Format)</span><span class="sxs-lookup"><span data-stu-id="98048-129">TableColumnItem Element (Format)</span></span>](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md)

[<span data-ttu-id="98048-130">Elemento TableRowEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="98048-130">TableRowEntry Element (Format)</span></span>](./tablerowentry-element-for-tablerowentries-for-tablecontrol-format.md)

[<span data-ttu-id="98048-131">Scrittura di un file di formattazione di PowerShell</span><span class="sxs-lookup"><span data-stu-id="98048-131">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
