---
title: Elemento label per TableColumnHeader per Table ((Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 7196f039-2f6a-41fd-b252-5b1623ebb9f9
caps.latest.revision: 11
ms.openlocfilehash: 09183a538c179f19347c3f1ed45b4ad38c2ca451
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/05/2019
ms.locfileid: "72365170"
---
# <a name="label-element-for-tablecolumnheader-for-tablecontrol-format"></a><span data-ttu-id="b5817-102">Elemento Label per TableColumnHeader per TableControl (formato)</span><span class="sxs-lookup"><span data-stu-id="b5817-102">Label Element for TableColumnHeader for TableControl (Format)</span></span>

<span data-ttu-id="b5817-103">Definisce l'etichetta visualizzata nella parte superiore di una colonna.</span><span class="sxs-lookup"><span data-stu-id="b5817-103">Defines the label that is displayed at the top of a column.</span></span> <span data-ttu-id="b5817-104">Questo elemento viene utilizzato quando si definisce una vista tabella.</span><span class="sxs-lookup"><span data-stu-id="b5817-104">This element is used when defining a table view.</span></span>

<span data-ttu-id="b5817-105">Elemento Configuration (Format) elemento ViewDefinitions (Format) elemento View (Format) elemento Table ((Format) elemento TableHeaders per Table ((Format) elemento TableColumnHeader per TableHeaders per l'elemento label Table ((Format) per TableColumnHeader per Table ((Format)</span><span class="sxs-lookup"><span data-stu-id="b5817-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) TableControl Element (Format) TableHeaders Element for TableControl (Format) TableColumnHeader Element for TableHeaders for TableControl (Format) Label Element  for TableColumnHeader for TableControl (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="b5817-106">Sintassi</span><span class="sxs-lookup"><span data-stu-id="b5817-106">Syntax</span></span>

```xml
<Label>DisplayedLabel</Label>

```

## <a name="attributes-and-elements"></a><span data-ttu-id="b5817-107">Attributi ed elementi</span><span class="sxs-lookup"><span data-stu-id="b5817-107">Attributes and Elements</span></span>

<span data-ttu-id="b5817-108">Nelle sezioni seguenti vengono descritti gli attributi, gli elementi figlio e l'elemento padre dell'elemento `Label`.</span><span class="sxs-lookup"><span data-stu-id="b5817-108">The following sections describe the attributes, child elements, and the parent element of the `Label` element.</span></span> <span data-ttu-id="b5817-109">È consentita una sola etichetta per ogni colonna.</span><span class="sxs-lookup"><span data-stu-id="b5817-109">Only one label is allowed for each column.</span></span>

### <a name="attributes"></a><span data-ttu-id="b5817-110">Attributi</span><span class="sxs-lookup"><span data-stu-id="b5817-110">Attributes</span></span>

<span data-ttu-id="b5817-111">Nessuna.</span><span class="sxs-lookup"><span data-stu-id="b5817-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="b5817-112">Elementi figlio</span><span class="sxs-lookup"><span data-stu-id="b5817-112">Child Elements</span></span>

<span data-ttu-id="b5817-113">Nessuna.</span><span class="sxs-lookup"><span data-stu-id="b5817-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="b5817-114">Elementi padre</span><span class="sxs-lookup"><span data-stu-id="b5817-114">Parent Elements</span></span>

|<span data-ttu-id="b5817-115">Elemento</span><span class="sxs-lookup"><span data-stu-id="b5817-115">Element</span></span>|<span data-ttu-id="b5817-116">Description</span><span class="sxs-lookup"><span data-stu-id="b5817-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="b5817-117">Elemento TableColumnHeader per TableHeaders per Table ((Format)</span><span class="sxs-lookup"><span data-stu-id="b5817-117">TableColumnHeader Element for TableHeaders for TableControl  (Format)</span></span>](./tablecolumnheader-element-format.md)|<span data-ttu-id="b5817-118">Definisce un'etichetta, la larghezza e l'allineamento dei dati per una colonna della tabella.</span><span class="sxs-lookup"><span data-stu-id="b5817-118">Defines a label, the width, and the alignment of the data for a column of the table.</span></span>|

## <a name="text-value"></a><span data-ttu-id="b5817-119">Valore testo</span><span class="sxs-lookup"><span data-stu-id="b5817-119">Text Value</span></span>

<span data-ttu-id="b5817-120">Consente di specificare il testo visualizzato nella parte superiore della colonna della tabella.</span><span class="sxs-lookup"><span data-stu-id="b5817-120">Specify the text that is displayed at the top of the column of the table.</span></span> <span data-ttu-id="b5817-121">Nessun carattere limitato per l'etichetta di colonna.</span><span class="sxs-lookup"><span data-stu-id="b5817-121">There are no restricted characters for the column label.</span></span>

## <a name="remarks"></a><span data-ttu-id="b5817-122">Osservazioni</span><span class="sxs-lookup"><span data-stu-id="b5817-122">Remarks</span></span>

<span data-ttu-id="b5817-123">Se non viene specificata alcuna etichetta, viene usato il nome della proprietà il cui valore viene visualizzato nelle righe.</span><span class="sxs-lookup"><span data-stu-id="b5817-123">If no label is specified, the name of the property whose value is displayed in the rows is used.</span></span>

<span data-ttu-id="b5817-124">Per ulteriori informazioni sui componenti di una vista tabella, vedere [creazione di una vista tabella](./creating-a-table-view.md).</span><span class="sxs-lookup"><span data-stu-id="b5817-124">For more information about the components of a table view, see [Creating a Table View](./creating-a-table-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="b5817-125">Esempio</span><span class="sxs-lookup"><span data-stu-id="b5817-125">Example</span></span>

<span data-ttu-id="b5817-126">In questo esempio viene illustrato un elemento `TableColumnHeader` la cui etichetta è "Column 1".</span><span class="sxs-lookup"><span data-stu-id="b5817-126">This example shows a `TableColumnHeader` element whose label is "Column 1".</span></span>

```xml
<TableColumnHeader>
  <Label>Column 1</Label)
  <Width>16</Width>
  <Alignment>Left</Alignment>
</TableColumnHeader>
```

## <a name="see-also"></a><span data-ttu-id="b5817-127">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="b5817-127">See Also</span></span>

[<span data-ttu-id="b5817-128">Creazione di una vista tabella</span><span class="sxs-lookup"><span data-stu-id="b5817-128">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="b5817-129">Elemento TableColumnHeader (Format)</span><span class="sxs-lookup"><span data-stu-id="b5817-129">TableColumnHeader Element (Format)</span></span>](./tablecolumnheader-element-format.md)

[<span data-ttu-id="b5817-130">Scrittura di un file di formattazione di PowerShell</span><span class="sxs-lookup"><span data-stu-id="b5817-130">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
