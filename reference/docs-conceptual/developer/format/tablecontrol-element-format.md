---
title: Elemento Table ((Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 1550b068-dfbc-4ae0-9aa1-72c9a680ec59
caps.latest.revision: 15
ms.openlocfilehash: 3942c008e026b0b99db3c77af4a0152b50fffc4e
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/15/2019
ms.locfileid: "72368200"
---
# <a name="tablecontrol-element-format"></a><span data-ttu-id="89815-102">Elemento TableControl (formato)</span><span class="sxs-lookup"><span data-stu-id="89815-102">TableControl Element (Format)</span></span>

<span data-ttu-id="89815-103">Definisce un formato di tabella per una visualizzazione.</span><span class="sxs-lookup"><span data-stu-id="89815-103">Defines a table format for a view.</span></span>

<span data-ttu-id="89815-104">Elemento ViewDefinitions (Format) elemento View (Format) elemento Table ((Format)</span><span class="sxs-lookup"><span data-stu-id="89815-104">ViewDefinitions Element (Format) View Element (Format) TableControl Element (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="89815-105">Sintassi</span><span class="sxs-lookup"><span data-stu-id="89815-105">Syntax</span></span>

```xml
<TableControl>
  <AutoSize/>
  <HideTableHeaders/>
  <TableHeaders>...</TableHeaders>
  <TableRowEntries>...</TableRowEntries>
</TableControl>

```

## <a name="attributes-and-elements"></a><span data-ttu-id="89815-106">Attributi ed elementi</span><span class="sxs-lookup"><span data-stu-id="89815-106">Attributes and Elements</span></span>

<span data-ttu-id="89815-107">Nelle sezioni seguenti vengono descritti gli attributi, gli elementi figlio e l'elemento padre dell'elemento `TableControl`.</span><span class="sxs-lookup"><span data-stu-id="89815-107">The following sections describe attributes, child elements, and parent element of the `TableControl` element.</span></span> <span data-ttu-id="89815-108">È necessario specificare le righe della tabella.</span><span class="sxs-lookup"><span data-stu-id="89815-108">You must specify the rows of the table.</span></span> <span data-ttu-id="89815-109">Tutti gli altri elementi figlio sono facoltativi.</span><span class="sxs-lookup"><span data-stu-id="89815-109">All other child elements are optional.</span></span>

### <a name="attributes"></a><span data-ttu-id="89815-110">Attributi</span><span class="sxs-lookup"><span data-stu-id="89815-110">Attributes</span></span>

<span data-ttu-id="89815-111">Nessuna.</span><span class="sxs-lookup"><span data-stu-id="89815-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="89815-112">Elementi figlio</span><span class="sxs-lookup"><span data-stu-id="89815-112">Child Elements</span></span>

|<span data-ttu-id="89815-113">Elemento</span><span class="sxs-lookup"><span data-stu-id="89815-113">Element</span></span>|<span data-ttu-id="89815-114">Description</span><span class="sxs-lookup"><span data-stu-id="89815-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="89815-115">Elemento AutoSize per Table ((Format)</span><span class="sxs-lookup"><span data-stu-id="89815-115">AutoSize Element for TableControl (Format)</span></span>](./autosize-element-for-tablecontrol-format.md)|<span data-ttu-id="89815-116">Elemento facoltativo.</span><span class="sxs-lookup"><span data-stu-id="89815-116">Optional element.</span></span><br /><br /> <span data-ttu-id="89815-117">Specifica se le dimensioni della colonna e il numero di colonne vengono regolate in base alle dimensioni dei dati.</span><span class="sxs-lookup"><span data-stu-id="89815-117">Specifies whether the column size and the number of columns are adjusted based on the size of the data.</span></span>|
|[<span data-ttu-id="89815-118">Elemento HideTableHeaders per Table ((Format)</span><span class="sxs-lookup"><span data-stu-id="89815-118">HideTableHeaders Element for TableControl (Format)</span></span>](./hidetableheaders-element-format.md)|<span data-ttu-id="89815-119">Elemento facoltativo.</span><span class="sxs-lookup"><span data-stu-id="89815-119">Optional element.</span></span><br /><br /> <span data-ttu-id="89815-120">Indica se l'intestazione della tabella non viene visualizzata.</span><span class="sxs-lookup"><span data-stu-id="89815-120">Indicates whether the header of the table is not displayed.</span></span>|
|[<span data-ttu-id="89815-121">Elemento TableHeaders per Table ((Format)</span><span class="sxs-lookup"><span data-stu-id="89815-121">TableHeaders Element for TableControl (Format)</span></span>](./tableheaders-element-format.md)|<span data-ttu-id="89815-122">Elemento obbligatorio.</span><span class="sxs-lookup"><span data-stu-id="89815-122">Required element.</span></span><br /><br /> <span data-ttu-id="89815-123">Definisce le etichette, le larghezze e l'allineamento dei dati per le colonne della visualizzazione tabella.</span><span class="sxs-lookup"><span data-stu-id="89815-123">Defines the labels, the widths, and the alignment of the data for the columns of the table view.</span></span>|
|[<span data-ttu-id="89815-124">Elemento TableRowEntries per Table ((Format)</span><span class="sxs-lookup"><span data-stu-id="89815-124">TableRowEntries Element for TableControl (Format)</span></span>](./tablerowentries-element-for-tablecontrol-format.md)|<span data-ttu-id="89815-125">Elemento facoltativo.</span><span class="sxs-lookup"><span data-stu-id="89815-125">Optional element.</span></span><br /><br /> <span data-ttu-id="89815-126">Fornisce le definizioni della visualizzazione tabella.</span><span class="sxs-lookup"><span data-stu-id="89815-126">Provides the definitions of the table view.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="89815-127">Elementi padre</span><span class="sxs-lookup"><span data-stu-id="89815-127">Parent Elements</span></span>

|<span data-ttu-id="89815-128">Elemento</span><span class="sxs-lookup"><span data-stu-id="89815-128">Element</span></span>|<span data-ttu-id="89815-129">Description</span><span class="sxs-lookup"><span data-stu-id="89815-129">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="89815-130">Elemento View (Format)</span><span class="sxs-lookup"><span data-stu-id="89815-130">View Element (Format)</span></span>](./view-element-format.md)|<span data-ttu-id="89815-131">Definisce una vista utilizzata per visualizzare i membri di uno o più oggetti.</span><span class="sxs-lookup"><span data-stu-id="89815-131">Defines a view that is used to display the members of one or more objects.</span></span>|

## <a name="remarks"></a><span data-ttu-id="89815-132">Osservazioni</span><span class="sxs-lookup"><span data-stu-id="89815-132">Remarks</span></span>

<span data-ttu-id="89815-133">Per ulteriori informazioni sui componenti di una vista tabella, vedere [creazione di una vista tabella](./creating-a-table-view.md).</span><span class="sxs-lookup"><span data-stu-id="89815-133">For more information about the components of a table view, see [Creating a Table View](./creating-a-table-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="89815-134">Esempio</span><span class="sxs-lookup"><span data-stu-id="89815-134">Example</span></span>

<span data-ttu-id="89815-135">Questo esempio mostra un elemento `TableControl` usato per visualizzare le proprietà dell'oggetto [System. ServiceProcess. ServiceController](/dotnet/api/System.ServiceProcess.ServiceController) .</span><span class="sxs-lookup"><span data-stu-id="89815-135">This example shows a `TableControl` element that is used to display the properties of the [System.Serviceprocess.Servicecontroller](/dotnet/api/System.ServiceProcess.ServiceController) object.</span></span>

```xml
<View>
  <Name>service</Name>
  <ViewSelectedBy>
    <TypeName>System.ServiceProcess.ServiceController</TypeName>
  </ViewSelectedBy>
  <TableControl>
    <TableHeaders>...</TableHeaders>
    <TableRowEntries>...</TableRowEntries>
  </TableControl>
</View>

```

## <a name="see-also"></a><span data-ttu-id="89815-136">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="89815-136">See Also</span></span>

[<span data-ttu-id="89815-137">Creazione di una vista tabella</span><span class="sxs-lookup"><span data-stu-id="89815-137">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="89815-138">Elemento View (Format)</span><span class="sxs-lookup"><span data-stu-id="89815-138">View Element (Format)</span></span>](./view-element-format.md)

[<span data-ttu-id="89815-139">Elemento AutoSize per Table ((Format)</span><span class="sxs-lookup"><span data-stu-id="89815-139">AutoSize Element for TableControl (Format)</span></span>](./autosize-element-for-tablecontrol-format.md)

[<span data-ttu-id="89815-140">Elemento HideTableHeaders (Format)</span><span class="sxs-lookup"><span data-stu-id="89815-140">HideTableHeaders Element (Format)</span></span>](./hidetableheaders-element-format.md)

[<span data-ttu-id="89815-141">Elemento TableHeaders (Format)</span><span class="sxs-lookup"><span data-stu-id="89815-141">TableHeaders Element (Format)</span></span>](./tableheaders-element-format.md)

[<span data-ttu-id="89815-142">Elemento TableRowEntries (Format)</span><span class="sxs-lookup"><span data-stu-id="89815-142">TableRowEntries Element (Format)</span></span>](./tablerowentries-element-for-tablecontrol-format.md)

[<span data-ttu-id="89815-143">Scrittura di un file di formattazione di PowerShell</span><span class="sxs-lookup"><span data-stu-id="89815-143">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
