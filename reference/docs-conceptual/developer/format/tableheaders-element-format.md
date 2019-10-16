---
title: Elemento TableHeaders (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f9fa2b6f-b99a-42de-9779-44e9cb583f71
caps.latest.revision: 15
ms.openlocfilehash: bd44fcf4878c858afe81fb071ce72f627ac465dc
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/15/2019
ms.locfileid: "72361820"
---
# <a name="tableheaders-element-format"></a><span data-ttu-id="ae9c7-102">Elemento TableHeaders (formato)</span><span class="sxs-lookup"><span data-stu-id="ae9c7-102">TableHeaders Element (Format)</span></span>

<span data-ttu-id="ae9c7-103">Definisce le intestazioni per le colonne di una tabella.</span><span class="sxs-lookup"><span data-stu-id="ae9c7-103">Defines the headers for the columns of a table.</span></span>

<span data-ttu-id="ae9c7-104">Elemento ViewDefinitions (Format) elemento View (Format) elemento Table ((Format) elemento TableHeaders per Table ((Format)</span><span class="sxs-lookup"><span data-stu-id="ae9c7-104">ViewDefinitions Element (Format) View Element (Format) TableControl Element (Format) TableHeaders Element for TableControl (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="ae9c7-105">Sintassi</span><span class="sxs-lookup"><span data-stu-id="ae9c7-105">Syntax</span></span>

```xml
<TableHeaders>
  <TableColumnHeader>...</TableColumnHeader>
</TableHeaders>

```

## <a name="attributes-and-elements"></a><span data-ttu-id="ae9c7-106">Attributi ed elementi</span><span class="sxs-lookup"><span data-stu-id="ae9c7-106">Attributes and Elements</span></span>

<span data-ttu-id="ae9c7-107">Nelle sezioni seguenti vengono descritti gli attributi, gli elementi figlio e gli elementi padre dell'elemento `TableHeaders`.</span><span class="sxs-lookup"><span data-stu-id="ae9c7-107">The following sections describe the attributes, child elements, and parent elements of the `TableHeaders` element.</span></span> <span data-ttu-id="ae9c7-108">Deve essere presente un elemento figlio per ogni proprietà dell'oggetto che deve essere visualizzato.</span><span class="sxs-lookup"><span data-stu-id="ae9c7-108">There must be a child element for each property of the object that is to be displayed.</span></span> <span data-ttu-id="ae9c7-109">Le informazioni sull'intestazione di colonna vengono visualizzate nell'ordine in cui sono specificati gli elementi figlio.</span><span class="sxs-lookup"><span data-stu-id="ae9c7-109">The column header information is displayed in the order that the child elements are specified.</span></span>

### <a name="attributes"></a><span data-ttu-id="ae9c7-110">Attributi</span><span class="sxs-lookup"><span data-stu-id="ae9c7-110">Attributes</span></span>

<span data-ttu-id="ae9c7-111">Nessuna.</span><span class="sxs-lookup"><span data-stu-id="ae9c7-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="ae9c7-112">Elementi figlio</span><span class="sxs-lookup"><span data-stu-id="ae9c7-112">Child Elements</span></span>

|<span data-ttu-id="ae9c7-113">Elemento</span><span class="sxs-lookup"><span data-stu-id="ae9c7-113">Element</span></span>|<span data-ttu-id="ae9c7-114">Description</span><span class="sxs-lookup"><span data-stu-id="ae9c7-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="ae9c7-115">Elemento TableColumnHeader (Format)</span><span class="sxs-lookup"><span data-stu-id="ae9c7-115">TableColumnHeader Element (Format)</span></span>](./tablecolumnheader-element-format.md)|<span data-ttu-id="ae9c7-116">Elemento facoltativo.</span><span class="sxs-lookup"><span data-stu-id="ae9c7-116">Optional element.</span></span><br /><br /> <span data-ttu-id="ae9c7-117">Definisce l'etichetta, la larghezza e l'allineamento dei dati per una colonna di una vista tabella.</span><span class="sxs-lookup"><span data-stu-id="ae9c7-117">Defines the label, the width, and the alignment of the data for a column of a table view.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="ae9c7-118">Elementi padre</span><span class="sxs-lookup"><span data-stu-id="ae9c7-118">Parent Elements</span></span>

|<span data-ttu-id="ae9c7-119">Elemento</span><span class="sxs-lookup"><span data-stu-id="ae9c7-119">Element</span></span>|<span data-ttu-id="ae9c7-120">Description</span><span class="sxs-lookup"><span data-stu-id="ae9c7-120">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="ae9c7-121">Elemento Table ((Format)</span><span class="sxs-lookup"><span data-stu-id="ae9c7-121">TableControl Element (Format)</span></span>](./tablecontrol-element-format.md)|<span data-ttu-id="ae9c7-122">Definisce un formato di tabella per una visualizzazione.</span><span class="sxs-lookup"><span data-stu-id="ae9c7-122">Defines a table format for a view.</span></span>|

## <a name="remarks"></a><span data-ttu-id="ae9c7-123">Osservazioni</span><span class="sxs-lookup"><span data-stu-id="ae9c7-123">Remarks</span></span>

<span data-ttu-id="ae9c7-124">Per ulteriori informazioni sui componenti di una vista tabella, vedere [creazione di una vista tabella](./creating-a-table-view.md).</span><span class="sxs-lookup"><span data-stu-id="ae9c7-124">For more information about the components of a table view, see [Creating a Table View](./creating-a-table-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="ae9c7-125">Esempio</span><span class="sxs-lookup"><span data-stu-id="ae9c7-125">Example</span></span>

<span data-ttu-id="ae9c7-126">Questo esempio mostra un elemento `TableHeaders` che definisce due intestazioni di colonna.</span><span class="sxs-lookup"><span data-stu-id="ae9c7-126">This example shows a `TableHeaders` element that defines two column headers.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="ae9c7-127">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="ae9c7-127">See Also</span></span>

[<span data-ttu-id="ae9c7-128">Creazione di una vista tabella</span><span class="sxs-lookup"><span data-stu-id="ae9c7-128">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="ae9c7-129">Elemento TableColumnHeader (Format)</span><span class="sxs-lookup"><span data-stu-id="ae9c7-129">TableColumnHeader Element (Format)</span></span>](./tablecolumnheader-element-format.md)

[<span data-ttu-id="ae9c7-130">Elemento Table ((Format)</span><span class="sxs-lookup"><span data-stu-id="ae9c7-130">TableControl Element (Format)</span></span>](./tablecontrol-element-format.md)

[<span data-ttu-id="ae9c7-131">Scrittura di un file di formattazione di PowerShell</span><span class="sxs-lookup"><span data-stu-id="ae9c7-131">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
