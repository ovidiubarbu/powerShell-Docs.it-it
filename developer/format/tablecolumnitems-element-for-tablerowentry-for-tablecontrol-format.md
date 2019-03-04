---
title: Elemento TableColumnItems per TableRowEntry per Table (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d43684ce-7c3d-4d14-8dbd-061c111ee805
caps.latest.revision: 12
ms.openlocfilehash: faa9ba78397e713400f6072df9915f20d966bb37
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/03/2019
ms.locfileid: "56859447"
---
# <a name="tablecolumnitems-element-for-tablerowentry-for-tablecontrol-format"></a><span data-ttu-id="f626c-102">Elemento TableColumnItems per TableRowEntry per TableControl (formato)</span><span class="sxs-lookup"><span data-stu-id="f626c-102">TableColumnItems Element for TableRowEntry for TableControl (Format)</span></span>

<span data-ttu-id="f626c-103">Definisce le proprietà o gli script i cui valori vengono visualizzati in una riga.</span><span class="sxs-lookup"><span data-stu-id="f626c-103">Defines the properties or scripts whose values are displayed in a row.</span></span>

<span data-ttu-id="f626c-104">Elemento (formato) elemento ViewDefinitions (formato) visualizzazione elemento (formato) elemento Table (formato) TableRowEntries elemento di configurazione per Table (formato) TableRowEntry elemento TableRowEntries per Table (formato) Elemento TableColumnItems per TableControlEntry per Table (formato)</span><span class="sxs-lookup"><span data-stu-id="f626c-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) TableControl Element (Format) TableRowEntries Element for TableControl (Format) TableRowEntry Element for TableRowEntries for TableControl (Format) TableColumnItems Element for TableControlEntry for TableControl (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="f626c-105">Sintassi</span><span class="sxs-lookup"><span data-stu-id="f626c-105">Syntax</span></span>

```xml
TableColumnItems>
  <TableColumnItem>...</TableColumnItem>
</TableColumnItems>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="f626c-106">Attributi ed elementi</span><span class="sxs-lookup"><span data-stu-id="f626c-106">Attributes and Elements</span></span>

<span data-ttu-id="f626c-107">Le sezioni seguenti descrivono gli attributi, elementi figlio ed elemento padre dell'elemento di `TableColumnItems` elemento.</span><span class="sxs-lookup"><span data-stu-id="f626c-107">The following sections describe the attributes, child elements, and parent element of the `TableColumnItems` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="f626c-108">Attributes</span><span class="sxs-lookup"><span data-stu-id="f626c-108">Attributes</span></span>

<span data-ttu-id="f626c-109">Nessuna.</span><span class="sxs-lookup"><span data-stu-id="f626c-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="f626c-110">Elementi figlio</span><span class="sxs-lookup"><span data-stu-id="f626c-110">Child Elements</span></span>

|<span data-ttu-id="f626c-111">Elemento</span><span class="sxs-lookup"><span data-stu-id="f626c-111">Element</span></span>|<span data-ttu-id="f626c-112">Description</span><span class="sxs-lookup"><span data-stu-id="f626c-112">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="f626c-113">Elemento TableColumnItem per TableColumnItems per Table (formato)</span><span class="sxs-lookup"><span data-stu-id="f626c-113">TableColumnItem Element for TableColumnItems for TableControl (Format)</span></span>](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md)|<span data-ttu-id="f626c-114">Elemento obbligatorio.</span><span class="sxs-lookup"><span data-stu-id="f626c-114">Required element.</span></span><br /><br /> <span data-ttu-id="f626c-115">Definisce le proprietà il cui valore viene visualizzato in una colonna della riga di script.</span><span class="sxs-lookup"><span data-stu-id="f626c-115">Defines the property or script whose value is displayed in a column of the row.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="f626c-116">Elementi padre</span><span class="sxs-lookup"><span data-stu-id="f626c-116">Parent Elements</span></span>

|<span data-ttu-id="f626c-117">Elemento</span><span class="sxs-lookup"><span data-stu-id="f626c-117">Element</span></span>|<span data-ttu-id="f626c-118">Description</span><span class="sxs-lookup"><span data-stu-id="f626c-118">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="f626c-119">Elemento TableRowEntry per TableRowEntries per Table (formato)</span><span class="sxs-lookup"><span data-stu-id="f626c-119">TableRowEntry Element for TableRowEntries for TableControl (Format)</span></span>](./tablerowentry-element-for-tablerowentroes-for-tablecontrol-format.md)|<span data-ttu-id="f626c-120">Definisce i dati che viene visualizzati in una riga della tabella.</span><span class="sxs-lookup"><span data-stu-id="f626c-120">Defines the data that is displayed in a row of the table.</span></span>|

## <a name="remarks"></a><span data-ttu-id="f626c-121">Osservazioni</span><span class="sxs-lookup"><span data-stu-id="f626c-121">Remarks</span></span>

<span data-ttu-id="f626c-122">Oggetto `TableColumnItem` elemento è obbligatorio per ogni colonna della riga.</span><span class="sxs-lookup"><span data-stu-id="f626c-122">A `TableColumnItem` element is required for each column of the row.</span></span> <span data-ttu-id="f626c-123">La prima voce viene visualizzata nella prima colonna, la seconda voce nella seconda colonna e così via.</span><span class="sxs-lookup"><span data-stu-id="f626c-123">The first entry is displayed in first column, the second entry in the second column, and so on.</span></span>

<span data-ttu-id="f626c-124">Per altre informazioni sui componenti di visualizzazione di una tabella, vedere [creazione di una visualizzazione tabella](./creating-a-table-view.md).</span><span class="sxs-lookup"><span data-stu-id="f626c-124">For more information about the components of a table view, see [Creating a Table View](./creating-a-table-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="f626c-125">Esempio</span><span class="sxs-lookup"><span data-stu-id="f626c-125">Example</span></span>

<span data-ttu-id="f626c-126">L'esempio seguente mostra un `TableColumnItems` che definisce tre proprietà dell'elemento di [Diagnostics](/dotnet/api/System.Diagnostics.Process) oggetto.</span><span class="sxs-lookup"><span data-stu-id="f626c-126">The following example shows a `TableColumnItems` element that defines three properties of the [System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process) object.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="f626c-127">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="f626c-127">See Also</span></span>

[<span data-ttu-id="f626c-128">Creazione di una visualizzazione tabella</span><span class="sxs-lookup"><span data-stu-id="f626c-128">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="f626c-129">Elemento TableColumnItem (formato)</span><span class="sxs-lookup"><span data-stu-id="f626c-129">TableColumnItem Element (Format)</span></span>](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md)

[<span data-ttu-id="f626c-130">Elemento TableRowEntry (formato)</span><span class="sxs-lookup"><span data-stu-id="f626c-130">TableRowEntry Element (Format)</span></span>](./tablerowentry-element-for-tablerowentroes-for-tablecontrol-format.md)

[<span data-ttu-id="f626c-131">La scrittura di un File di formattazione di PowerShell</span><span class="sxs-lookup"><span data-stu-id="f626c-131">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
