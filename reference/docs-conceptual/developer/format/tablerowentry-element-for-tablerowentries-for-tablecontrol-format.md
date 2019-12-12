---
title: Elemento TableRowEntry per TableRowEntries per Table ((Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 18d86af7-7ff9-4968-81be-2caa61937d49
caps.latest.revision: 10
ms.openlocfilehash: 946ffb3fe857503c02b9000238a86775969abbd6
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/05/2019
ms.locfileid: "72361800"
---
# <a name="tablerowentry-element-for-tablerowentries-for-tablecontrol-format"></a><span data-ttu-id="25521-102">Elemento TableRowEntry per TableRowEntries per TableControl (formato)</span><span class="sxs-lookup"><span data-stu-id="25521-102">TableRowEntry Element for TableRowEntries for TableControl (Format)</span></span>

<span data-ttu-id="25521-103">Definisce i dati visualizzati in una riga della tabella.</span><span class="sxs-lookup"><span data-stu-id="25521-103">Defines the data that is displayed in a row of the table.</span></span>

<span data-ttu-id="25521-104">Elemento Configuration (Format) elemento ViewDefinitions (Format) elemento View (Format) elemento Table ((Format) elemento TableRowEntries per Table ((Format) elemento TableRowEntry per TableRowEntries per Table ((Format)</span><span class="sxs-lookup"><span data-stu-id="25521-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) TableControl Element (Format) TableRowEntries Element for TableControl (Format) TableRowEntry Element for TableRowEntries for TableControl (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="25521-105">Sintassi</span><span class="sxs-lookup"><span data-stu-id="25521-105">Syntax</span></span>

```xml
<TableRowEntry>
  <Wrap/>
  <EntrySelectedBy>...</EntrySelectedBy>
  <TableColumnItems>...</TableColumnItems>
</TableRowEntry>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="25521-106">Attributi ed elementi</span><span class="sxs-lookup"><span data-stu-id="25521-106">Attributes and Elements</span></span>

<span data-ttu-id="25521-107">Nelle sezioni seguenti vengono descritti gli attributi, gli elementi figlio e l'elemento padre dell'elemento `TableRowEntry`.</span><span class="sxs-lookup"><span data-stu-id="25521-107">The following sections describe attributes, child elements, and parent element of the `TableRowEntry` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="25521-108">Attributi</span><span class="sxs-lookup"><span data-stu-id="25521-108">Attributes</span></span>

<span data-ttu-id="25521-109">Nessuna.</span><span class="sxs-lookup"><span data-stu-id="25521-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="25521-110">Elementi figlio</span><span class="sxs-lookup"><span data-stu-id="25521-110">Child Elements</span></span>

|<span data-ttu-id="25521-111">Elemento</span><span class="sxs-lookup"><span data-stu-id="25521-111">Element</span></span>|<span data-ttu-id="25521-112">Description</span><span class="sxs-lookup"><span data-stu-id="25521-112">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="25521-113">Elemento EntrySelectedBy per TableRowEntry per Table ((Format)</span><span class="sxs-lookup"><span data-stu-id="25521-113">EntrySelectedBy Element for TableRowEntry for TableControl (Format)</span></span>](./entryselectedby-element-for-tablerowentry-for-tablecontrol-format.md)|<span data-ttu-id="25521-114">Elemento obbligatorio.</span><span class="sxs-lookup"><span data-stu-id="25521-114">Required element.</span></span><br /><br /> <span data-ttu-id="25521-115">Definisce gli oggetti i cui valori di proprietà vengono visualizzati nella riga.</span><span class="sxs-lookup"><span data-stu-id="25521-115">Defines the objects whose property values are displayed in the row.</span></span>|
|[<span data-ttu-id="25521-116">Elemento TableColumnItems per TableRowEntry per Table ((Format)</span><span class="sxs-lookup"><span data-stu-id="25521-116">TableColumnItems Element for TableRowEntry for TableControl (Format)</span></span>](./tablecolumnitems-element-for-tablerowentry-for-tablecontrol-format.md)|<span data-ttu-id="25521-117">Elemento obbligatorio.</span><span class="sxs-lookup"><span data-stu-id="25521-117">Required element.</span></span><br /><br /> <span data-ttu-id="25521-118">Definisce le proprietà o gli script i cui valori sono visualizzati.</span><span class="sxs-lookup"><span data-stu-id="25521-118">Defines the properties or scripts whose values are displayed.</span></span>|
|[<span data-ttu-id="25521-119">Elemento wrap per TableRowEntry per Table ((Format)</span><span class="sxs-lookup"><span data-stu-id="25521-119">Wrap Element for TableRowEntry for TableControl (Format)</span></span>](./wrap-element-for-tablerowentry-for-tablecontrol-format.md)|<span data-ttu-id="25521-120">Elemento facoltativo.</span><span class="sxs-lookup"><span data-stu-id="25521-120">Optional element.</span></span><br /><br /> <span data-ttu-id="25521-121">Specifica che il testo che supera la larghezza della colonna viene visualizzato nella riga successiva.</span><span class="sxs-lookup"><span data-stu-id="25521-121">Specifies that text that exceeds the column width is displayed on the next line.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="25521-122">Elementi padre</span><span class="sxs-lookup"><span data-stu-id="25521-122">Parent Elements</span></span>

|<span data-ttu-id="25521-123">Elemento</span><span class="sxs-lookup"><span data-stu-id="25521-123">Element</span></span>|<span data-ttu-id="25521-124">Description</span><span class="sxs-lookup"><span data-stu-id="25521-124">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="25521-125">Elemento TableRowEntries per Table ((Format)</span><span class="sxs-lookup"><span data-stu-id="25521-125">TableRowEntries Element for TableControl (Format)</span></span>](./tablerowentries-element-for-tablecontrol-format.md)|<span data-ttu-id="25521-126">Definisce le righe della tabella.</span><span class="sxs-lookup"><span data-stu-id="25521-126">Defines the rows of the table.</span></span>|

## <a name="remarks"></a><span data-ttu-id="25521-127">Osservazioni</span><span class="sxs-lookup"><span data-stu-id="25521-127">Remarks</span></span>

<span data-ttu-id="25521-128">È necessario specificare un elemento `TableColumnItems` e uno `EntrySelectedBy`.</span><span class="sxs-lookup"><span data-stu-id="25521-128">One `TableColumnItems` element and one `EntrySelectedBy` element must be specified.</span></span>

<span data-ttu-id="25521-129">Per ulteriori informazioni sui componenti di una vista tabella, vedere [creazione di una vista tabella](./creating-a-table-view.md).</span><span class="sxs-lookup"><span data-stu-id="25521-129">For more information about the components of a table view, see [Creating a Table View](./creating-a-table-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="25521-130">Esempio</span><span class="sxs-lookup"><span data-stu-id="25521-130">Example</span></span>

<span data-ttu-id="25521-131">Nell'esempio seguente viene illustrato un elemento `TableRowEntry` che definisce una riga in cui vengono visualizzati i valori di due proprietà dell'oggetto [System. Diagnostics. Process](/dotnet/api/System.Diagnostics.Process) .</span><span class="sxs-lookup"><span data-stu-id="25521-131">The following example shows a `TableRowEntry` element that defines a row that displays the values of two properties of the [System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process) object.</span></span>

```xml
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
```

## <a name="see-also"></a><span data-ttu-id="25521-132">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="25521-132">See Also</span></span>

[<span data-ttu-id="25521-133">Creazione di una vista tabella</span><span class="sxs-lookup"><span data-stu-id="25521-133">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="25521-134">Elemento EntrySelectedBy per TableRowEntry per Table ((Format)</span><span class="sxs-lookup"><span data-stu-id="25521-134">EntrySelectedBy Element for TableRowEntry for TableControl (Format)</span></span>](./entryselectedby-element-for-tablerowentry-for-tablecontrol-format.md)

[<span data-ttu-id="25521-135">Elemento TableColumnItems per TableRowEntry per Table ((Format)</span><span class="sxs-lookup"><span data-stu-id="25521-135">TableColumnItems Element for TableRowEntry for TableControl (Format)</span></span>](./tablecolumnitems-element-for-tablerowentry-for-tablecontrol-format.md)

[<span data-ttu-id="25521-136">Elemento TableRowEntries per Table ((Format)</span><span class="sxs-lookup"><span data-stu-id="25521-136">TableRowEntries Element for TableControl (Format)</span></span>](./tablerowentries-element-for-tablecontrol-format.md)

[<span data-ttu-id="25521-137">Elemento wrap per TableRowEntry per Table ((Format)</span><span class="sxs-lookup"><span data-stu-id="25521-137">Wrap Element for TableRowEntry for TableControl (Format)</span></span>](./wrap-element-for-tablerowentry-for-tablecontrol-format.md)

[<span data-ttu-id="25521-138">Scrittura di un file di formattazione di PowerShell</span><span class="sxs-lookup"><span data-stu-id="25521-138">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
