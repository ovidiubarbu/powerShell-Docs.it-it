---
title: Elemento Table (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 1550b068-dfbc-4ae0-9aa1-72c9a680ec59
caps.latest.revision: 15
ms.openlocfilehash: 3942c008e026b0b99db3c77af4a0152b50fffc4e
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62063829"
---
# <a name="tablecontrol-element-format"></a><span data-ttu-id="91802-102">Elemento TableControl (formato)</span><span class="sxs-lookup"><span data-stu-id="91802-102">TableControl Element (Format)</span></span>

<span data-ttu-id="91802-103">Definisce un formato di tabella per una visualizzazione.</span><span class="sxs-lookup"><span data-stu-id="91802-103">Defines a table format for a view.</span></span>

<span data-ttu-id="91802-104">Elemento TABLE di elemento (formato) visualizzazione elemento ViewDefinitions (formato) (formato)</span><span class="sxs-lookup"><span data-stu-id="91802-104">ViewDefinitions Element (Format) View Element (Format) TableControl Element (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="91802-105">Sintassi</span><span class="sxs-lookup"><span data-stu-id="91802-105">Syntax</span></span>

```xml
<TableControl>
  <AutoSize/>
  <HideTableHeaders/>
  <TableHeaders>...</TableHeaders>
  <TableRowEntries>...</TableRowEntries>
</TableControl>

```

## <a name="attributes-and-elements"></a><span data-ttu-id="91802-106">Elementi e attributi</span><span class="sxs-lookup"><span data-stu-id="91802-106">Attributes and Elements</span></span>

<span data-ttu-id="91802-107">Le sezioni seguenti descrivono l'elemento padre di attributi e gli elementi figlio di `TableControl` elemento.</span><span class="sxs-lookup"><span data-stu-id="91802-107">The following sections describe attributes, child elements, and parent element of the `TableControl` element.</span></span> <span data-ttu-id="91802-108">È necessario specificare le righe della tabella.</span><span class="sxs-lookup"><span data-stu-id="91802-108">You must specify the rows of the table.</span></span> <span data-ttu-id="91802-109">Tutti gli elementi figlio sono facoltativi.</span><span class="sxs-lookup"><span data-stu-id="91802-109">All other child elements are optional.</span></span>

### <a name="attributes"></a><span data-ttu-id="91802-110">Attributes</span><span class="sxs-lookup"><span data-stu-id="91802-110">Attributes</span></span>

<span data-ttu-id="91802-111">Nessuna.</span><span class="sxs-lookup"><span data-stu-id="91802-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="91802-112">Elementi figlio</span><span class="sxs-lookup"><span data-stu-id="91802-112">Child Elements</span></span>

|<span data-ttu-id="91802-113">Elemento</span><span class="sxs-lookup"><span data-stu-id="91802-113">Element</span></span>|<span data-ttu-id="91802-114">Description</span><span class="sxs-lookup"><span data-stu-id="91802-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="91802-115">AutoSize (elemento) per Table (formato)</span><span class="sxs-lookup"><span data-stu-id="91802-115">AutoSize Element for TableControl (Format)</span></span>](./autosize-element-for-tablecontrol-format.md)|<span data-ttu-id="91802-116">Elemento facoltativo.</span><span class="sxs-lookup"><span data-stu-id="91802-116">Optional element.</span></span><br /><br /> <span data-ttu-id="91802-117">Specifica se la dimensione della colonna e il numero di colonne vengono adattate in base alla dimensione dei dati.</span><span class="sxs-lookup"><span data-stu-id="91802-117">Specifies whether the column size and the number of columns are adjusted based on the size of the data.</span></span>|
|[<span data-ttu-id="91802-118">Elemento HideTableHeaders per Table (formato)</span><span class="sxs-lookup"><span data-stu-id="91802-118">HideTableHeaders Element for TableControl (Format)</span></span>](./hidetableheaders-element-format.md)|<span data-ttu-id="91802-119">Elemento facoltativo.</span><span class="sxs-lookup"><span data-stu-id="91802-119">Optional element.</span></span><br /><br /> <span data-ttu-id="91802-120">Indica se l'intestazione della tabella non viene visualizzato.</span><span class="sxs-lookup"><span data-stu-id="91802-120">Indicates whether the header of the table is not displayed.</span></span>|
|[<span data-ttu-id="91802-121">Elemento TableHeaders per Table (formato)</span><span class="sxs-lookup"><span data-stu-id="91802-121">TableHeaders Element for TableControl (Format)</span></span>](./tableheaders-element-format.md)|<span data-ttu-id="91802-122">Elemento obbligatorio.</span><span class="sxs-lookup"><span data-stu-id="91802-122">Required element.</span></span><br /><br /> <span data-ttu-id="91802-123">Definisce le etichette, la larghezza e l'allineamento dei dati per le colonne della visualizzazione della tabella.</span><span class="sxs-lookup"><span data-stu-id="91802-123">Defines the labels, the widths, and the alignment of the data for the columns of the table view.</span></span>|
|[<span data-ttu-id="91802-124">Elemento TableRowEntries per Table (formato)</span><span class="sxs-lookup"><span data-stu-id="91802-124">TableRowEntries Element for TableControl (Format)</span></span>](./tablerowentries-element-for-tablecontrol-format.md)|<span data-ttu-id="91802-125">Elemento facoltativo.</span><span class="sxs-lookup"><span data-stu-id="91802-125">Optional element.</span></span><br /><br /> <span data-ttu-id="91802-126">Fornisce le definizioni della visualizzazione della tabella.</span><span class="sxs-lookup"><span data-stu-id="91802-126">Provides the definitions of the table view.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="91802-127">Elementi padre</span><span class="sxs-lookup"><span data-stu-id="91802-127">Parent Elements</span></span>

|<span data-ttu-id="91802-128">Elemento</span><span class="sxs-lookup"><span data-stu-id="91802-128">Element</span></span>|<span data-ttu-id="91802-129">Description</span><span class="sxs-lookup"><span data-stu-id="91802-129">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="91802-130">Elemento di visualizzazione (formato)</span><span class="sxs-lookup"><span data-stu-id="91802-130">View Element (Format)</span></span>](./view-element-format.md)|<span data-ttu-id="91802-131">Definisce una vista che consente di visualizzare i membri di uno o più oggetti.</span><span class="sxs-lookup"><span data-stu-id="91802-131">Defines a view that is used to display the members of one or more objects.</span></span>|

## <a name="remarks"></a><span data-ttu-id="91802-132">Osservazioni</span><span class="sxs-lookup"><span data-stu-id="91802-132">Remarks</span></span>

<span data-ttu-id="91802-133">Per altre informazioni sui componenti di visualizzazione di una tabella, vedere [creazione di una visualizzazione tabella](./creating-a-table-view.md).</span><span class="sxs-lookup"><span data-stu-id="91802-133">For more information about the components of a table view, see [Creating a Table View](./creating-a-table-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="91802-134">Esempio</span><span class="sxs-lookup"><span data-stu-id="91802-134">Example</span></span>

<span data-ttu-id="91802-135">Questo esempio viene illustrato un `TableControl` che consente di visualizzare le proprietà dell'elemento il [System.Serviceprocess.Servicecontroller](/dotnet/api/System.ServiceProcess.ServiceController) oggetto.</span><span class="sxs-lookup"><span data-stu-id="91802-135">This example shows a `TableControl` element that is used to display the properties of the [System.Serviceprocess.Servicecontroller](/dotnet/api/System.ServiceProcess.ServiceController) object.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="91802-136">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="91802-136">See Also</span></span>

[<span data-ttu-id="91802-137">Creazione di una visualizzazione tabella</span><span class="sxs-lookup"><span data-stu-id="91802-137">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="91802-138">Elemento di visualizzazione (formato)</span><span class="sxs-lookup"><span data-stu-id="91802-138">View Element (Format)</span></span>](./view-element-format.md)

[<span data-ttu-id="91802-139">AutoSize (elemento) per Table (formato)</span><span class="sxs-lookup"><span data-stu-id="91802-139">AutoSize Element for TableControl (Format)</span></span>](./autosize-element-for-tablecontrol-format.md)

[<span data-ttu-id="91802-140">Elemento HideTableHeaders (formato)</span><span class="sxs-lookup"><span data-stu-id="91802-140">HideTableHeaders Element (Format)</span></span>](./hidetableheaders-element-format.md)

[<span data-ttu-id="91802-141">Elemento TableHeaders (formato)</span><span class="sxs-lookup"><span data-stu-id="91802-141">TableHeaders Element (Format)</span></span>](./tableheaders-element-format.md)

[<span data-ttu-id="91802-142">Elemento TableRowEntries (formato)</span><span class="sxs-lookup"><span data-stu-id="91802-142">TableRowEntries Element (Format)</span></span>](./tablerowentries-element-for-tablecontrol-format.md)

[<span data-ttu-id="91802-143">La scrittura di un File di formattazione di PowerShell</span><span class="sxs-lookup"><span data-stu-id="91802-143">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
