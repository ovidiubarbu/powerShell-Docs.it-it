---
title: Elemento TableRowEntry per TableRowEntries per Table (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 18d86af7-7ff9-4968-81be-2caa61937d49
caps.latest.revision: 10
ms.openlocfilehash: 946ffb3fe857503c02b9000238a86775969abbd6
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62075325"
---
# <a name="tablerowentry-element-for-tablerowentries-for-tablecontrol-format"></a><span data-ttu-id="0f109-102">Elemento TableRowEntry per TableRowEntries per TableControl (formato)</span><span class="sxs-lookup"><span data-stu-id="0f109-102">TableRowEntry Element for TableRowEntries for TableControl (Format)</span></span>

<span data-ttu-id="0f109-103">Definisce i dati che viene visualizzati in una riga della tabella.</span><span class="sxs-lookup"><span data-stu-id="0f109-103">Defines the data that is displayed in a row of the table.</span></span>

<span data-ttu-id="0f109-104">Elemento (formato) elemento ViewDefinitions (formato) visualizzazione elemento (formato) elemento Table (formato) TableRowEntries elemento di configurazione per Table (formato) TableRowEntry elemento TableRowEntries per Table (formato)</span><span class="sxs-lookup"><span data-stu-id="0f109-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) TableControl Element (Format) TableRowEntries Element for TableControl (Format) TableRowEntry Element for TableRowEntries for TableControl (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="0f109-105">Sintassi</span><span class="sxs-lookup"><span data-stu-id="0f109-105">Syntax</span></span>

```xml
<TableRowEntry>
  <Wrap/>
  <EntrySelectedBy>...</EntrySelectedBy>
  <TableColumnItems>...</TableColumnItems>
</TableRowEntry>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="0f109-106">Elementi e attributi</span><span class="sxs-lookup"><span data-stu-id="0f109-106">Attributes and Elements</span></span>

<span data-ttu-id="0f109-107">Le sezioni seguenti descrivono l'elemento padre di attributi e gli elementi figlio di `TableRowEntry` elemento.</span><span class="sxs-lookup"><span data-stu-id="0f109-107">The following sections describe attributes, child elements, and parent element of the `TableRowEntry` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="0f109-108">Attributes</span><span class="sxs-lookup"><span data-stu-id="0f109-108">Attributes</span></span>

<span data-ttu-id="0f109-109">Nessuna.</span><span class="sxs-lookup"><span data-stu-id="0f109-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="0f109-110">Elementi figlio</span><span class="sxs-lookup"><span data-stu-id="0f109-110">Child Elements</span></span>

|<span data-ttu-id="0f109-111">Elemento</span><span class="sxs-lookup"><span data-stu-id="0f109-111">Element</span></span>|<span data-ttu-id="0f109-112">Description</span><span class="sxs-lookup"><span data-stu-id="0f109-112">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="0f109-113">Elemento EntrySelectedBy per TableRowEntry per Table (formato)</span><span class="sxs-lookup"><span data-stu-id="0f109-113">EntrySelectedBy Element for TableRowEntry for TableControl (Format)</span></span>](./entryselectedby-element-for-tablerowentry-for-tablecontrol-format.md)|<span data-ttu-id="0f109-114">Elemento obbligatorio.</span><span class="sxs-lookup"><span data-stu-id="0f109-114">Required element.</span></span><br /><br /> <span data-ttu-id="0f109-115">Definisce gli oggetti i cui valori di proprietà vengono visualizzati nella riga.</span><span class="sxs-lookup"><span data-stu-id="0f109-115">Defines the objects whose property values are displayed in the row.</span></span>|
|[<span data-ttu-id="0f109-116">Elemento TableColumnItems per TableRowEntry per Table (formato)</span><span class="sxs-lookup"><span data-stu-id="0f109-116">TableColumnItems Element for TableRowEntry for TableControl (Format)</span></span>](./tablecolumnitems-element-for-tablerowentry-for-tablecontrol-format.md)|<span data-ttu-id="0f109-117">Elemento obbligatorio.</span><span class="sxs-lookup"><span data-stu-id="0f109-117">Required element.</span></span><br /><br /> <span data-ttu-id="0f109-118">Definisce le proprietà o gli script i cui valori vengono visualizzati.</span><span class="sxs-lookup"><span data-stu-id="0f109-118">Defines the properties or scripts whose values are displayed.</span></span>|
|[<span data-ttu-id="0f109-119">Eseguire il wrapping di elemento per TableRowEntry per Table (formato)</span><span class="sxs-lookup"><span data-stu-id="0f109-119">Wrap Element for TableRowEntry for TableControl (Format)</span></span>](./wrap-element-for-tablerowentry-for-tablecontrol-format.md)|<span data-ttu-id="0f109-120">Elemento facoltativo.</span><span class="sxs-lookup"><span data-stu-id="0f109-120">Optional element.</span></span><br /><br /> <span data-ttu-id="0f109-121">Specifica che il testo che supera la larghezza della colonna viene visualizzato nella riga successiva.</span><span class="sxs-lookup"><span data-stu-id="0f109-121">Specifies that text that exceeds the column width is displayed on the next line.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="0f109-122">Elementi padre</span><span class="sxs-lookup"><span data-stu-id="0f109-122">Parent Elements</span></span>

|<span data-ttu-id="0f109-123">Elemento</span><span class="sxs-lookup"><span data-stu-id="0f109-123">Element</span></span>|<span data-ttu-id="0f109-124">Description</span><span class="sxs-lookup"><span data-stu-id="0f109-124">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="0f109-125">Elemento TableRowEntries per Table (formato)</span><span class="sxs-lookup"><span data-stu-id="0f109-125">TableRowEntries Element for TableControl (Format)</span></span>](./tablerowentries-element-for-tablecontrol-format.md)|<span data-ttu-id="0f109-126">Definire le righe della tabella.</span><span class="sxs-lookup"><span data-stu-id="0f109-126">Defines the rows of the table.</span></span>|

## <a name="remarks"></a><span data-ttu-id="0f109-127">Osservazioni</span><span class="sxs-lookup"><span data-stu-id="0f109-127">Remarks</span></span>

<span data-ttu-id="0f109-128">Uno `TableColumnItems` elemento e l'altra `EntrySelectedBy` elemento deve essere specificato.</span><span class="sxs-lookup"><span data-stu-id="0f109-128">One `TableColumnItems` element and one `EntrySelectedBy` element must be specified.</span></span>

<span data-ttu-id="0f109-129">Per altre informazioni sui componenti di visualizzazione di una tabella, vedere [creazione di una visualizzazione tabella](./creating-a-table-view.md).</span><span class="sxs-lookup"><span data-stu-id="0f109-129">For more information about the components of a table view, see [Creating a Table View](./creating-a-table-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="0f109-130">Esempio</span><span class="sxs-lookup"><span data-stu-id="0f109-130">Example</span></span>

<span data-ttu-id="0f109-131">L'esempio seguente mostra una `TableRowEntry` elemento che definisce una riga che visualizza i valori delle due proprietà del [Diagnostics](/dotnet/api/System.Diagnostics.Process) oggetto.</span><span class="sxs-lookup"><span data-stu-id="0f109-131">The following example shows a `TableRowEntry` element that defines a row that displays the values of two properties of the [System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process) object.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="0f109-132">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="0f109-132">See Also</span></span>

[<span data-ttu-id="0f109-133">Creazione di una visualizzazione tabella</span><span class="sxs-lookup"><span data-stu-id="0f109-133">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="0f109-134">Elemento EntrySelectedBy per TableRowEntry per Table (formato)</span><span class="sxs-lookup"><span data-stu-id="0f109-134">EntrySelectedBy Element for TableRowEntry for TableControl (Format)</span></span>](./entryselectedby-element-for-tablerowentry-for-tablecontrol-format.md)

[<span data-ttu-id="0f109-135">Elemento TableColumnItems per TableRowEntry per Table (formato)</span><span class="sxs-lookup"><span data-stu-id="0f109-135">TableColumnItems Element for TableRowEntry for TableControl (Format)</span></span>](./tablecolumnitems-element-for-tablerowentry-for-tablecontrol-format.md)

[<span data-ttu-id="0f109-136">Elemento TableRowEntries per Table (formato)</span><span class="sxs-lookup"><span data-stu-id="0f109-136">TableRowEntries Element for TableControl (Format)</span></span>](./tablerowentries-element-for-tablecontrol-format.md)

[<span data-ttu-id="0f109-137">Eseguire il wrapping di elemento per TableRowEntry per Table (formato)</span><span class="sxs-lookup"><span data-stu-id="0f109-137">Wrap Element for TableRowEntry for TableControl (Format)</span></span>](./wrap-element-for-tablerowentry-for-tablecontrol-format.md)

[<span data-ttu-id="0f109-138">La scrittura di un File di formattazione di PowerShell</span><span class="sxs-lookup"><span data-stu-id="0f109-138">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
