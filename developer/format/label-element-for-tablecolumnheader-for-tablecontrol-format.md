---
title: L'etichetta di elemento per TableColumnHeader per Table (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 7196f039-2f6a-41fd-b252-5b1623ebb9f9
caps.latest.revision: 11
ms.openlocfilehash: 09183a538c179f19347c3f1ed45b4ad38c2ca451
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/16/2019
ms.locfileid: "58054510"
---
# <a name="label-element-for-tablecolumnheader-for-tablecontrol-format"></a><span data-ttu-id="0db8f-102">Elemento Label per TableColumnHeader per TableControl (formato)</span><span class="sxs-lookup"><span data-stu-id="0db8f-102">Label Element for TableColumnHeader for TableControl (Format)</span></span>

<span data-ttu-id="0db8f-103">Definisce l'etichetta che viene visualizzato nella parte superiore di una colonna.</span><span class="sxs-lookup"><span data-stu-id="0db8f-103">Defines the label that is displayed at the top of a column.</span></span> <span data-ttu-id="0db8f-104">Questo elemento viene usato quando si definisce una visualizzazione tabella.</span><span class="sxs-lookup"><span data-stu-id="0db8f-104">This element is used when defining a table view.</span></span>

<span data-ttu-id="0db8f-105">Configurazione elemento (formato) elemento ViewDefinitions (formato) visualizzazione elemento (formato) elemento Table (formato) TableHeaders elemento per elemento TableColumnHeader Table (formato) per TableHeaders per elemento etichetta Table (formato) TableColumnHeader per Table (formato)</span><span class="sxs-lookup"><span data-stu-id="0db8f-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) TableControl Element (Format) TableHeaders Element for TableControl (Format) TableColumnHeader Element for TableHeaders for TableControl (Format) Label Element  for TableColumnHeader for TableControl (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="0db8f-106">Sintassi</span><span class="sxs-lookup"><span data-stu-id="0db8f-106">Syntax</span></span>

```xml
<Label>DisplayedLabel</Label>

```

## <a name="attributes-and-elements"></a><span data-ttu-id="0db8f-107">Attributi ed elementi</span><span class="sxs-lookup"><span data-stu-id="0db8f-107">Attributes and Elements</span></span>

<span data-ttu-id="0db8f-108">Le sezioni seguenti descrivono gli attributi e gli elementi figlio dell'elemento padre del `Label` elemento.</span><span class="sxs-lookup"><span data-stu-id="0db8f-108">The following sections describe the attributes, child elements, and the parent element of the `Label` element.</span></span> <span data-ttu-id="0db8f-109">È consentita solo un'etichetta per ogni colonna.</span><span class="sxs-lookup"><span data-stu-id="0db8f-109">Only one label is allowed for each column.</span></span>

### <a name="attributes"></a><span data-ttu-id="0db8f-110">Attributes</span><span class="sxs-lookup"><span data-stu-id="0db8f-110">Attributes</span></span>

<span data-ttu-id="0db8f-111">Nessuna.</span><span class="sxs-lookup"><span data-stu-id="0db8f-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="0db8f-112">Elementi figlio</span><span class="sxs-lookup"><span data-stu-id="0db8f-112">Child Elements</span></span>

<span data-ttu-id="0db8f-113">Nessuna.</span><span class="sxs-lookup"><span data-stu-id="0db8f-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="0db8f-114">Elementi padre</span><span class="sxs-lookup"><span data-stu-id="0db8f-114">Parent Elements</span></span>

|<span data-ttu-id="0db8f-115">Elemento</span><span class="sxs-lookup"><span data-stu-id="0db8f-115">Element</span></span>|<span data-ttu-id="0db8f-116">Description</span><span class="sxs-lookup"><span data-stu-id="0db8f-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="0db8f-117">Elemento TableColumnHeader per TableHeaders per Table (formato)</span><span class="sxs-lookup"><span data-stu-id="0db8f-117">TableColumnHeader Element for TableHeaders for TableControl  (Format)</span></span>](./tablecolumnheader-element-format.md)|<span data-ttu-id="0db8f-118">Definisce un'etichetta, la larghezza e l'allineamento dei dati per una colonna della tabella.</span><span class="sxs-lookup"><span data-stu-id="0db8f-118">Defines a label, the width, and the alignment of the data for a column of the table.</span></span>|

## <a name="text-value"></a><span data-ttu-id="0db8f-119">Valore di testo</span><span class="sxs-lookup"><span data-stu-id="0db8f-119">Text Value</span></span>

<span data-ttu-id="0db8f-120">Specificare il testo visualizzato nella parte superiore della colonna della tabella.</span><span class="sxs-lookup"><span data-stu-id="0db8f-120">Specify the text that is displayed at the top of the column of the table.</span></span> <span data-ttu-id="0db8f-121">Non sono presenti caratteri limitati per l'etichetta di colonna.</span><span class="sxs-lookup"><span data-stu-id="0db8f-121">There are no restricted characters for the column label.</span></span>

## <a name="remarks"></a><span data-ttu-id="0db8f-122">Osservazioni</span><span class="sxs-lookup"><span data-stu-id="0db8f-122">Remarks</span></span>

<span data-ttu-id="0db8f-123">Se viene specificata alcuna etichetta, viene utilizzato il nome della proprietà il cui valore viene visualizzato nelle righe.</span><span class="sxs-lookup"><span data-stu-id="0db8f-123">If no label is specified, the name of the property whose value is displayed in the rows is used.</span></span>

<span data-ttu-id="0db8f-124">Per altre informazioni sui componenti di visualizzazione di una tabella, vedere [creazione di una visualizzazione tabella](./creating-a-table-view.md).</span><span class="sxs-lookup"><span data-stu-id="0db8f-124">For more information about the components of a table view, see [Creating a Table View](./creating-a-table-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="0db8f-125">Esempio</span><span class="sxs-lookup"><span data-stu-id="0db8f-125">Example</span></span>

<span data-ttu-id="0db8f-126">Questo esempio viene illustrato un `TableColumnHeader` elemento la cui etichetta è "Column 1".</span><span class="sxs-lookup"><span data-stu-id="0db8f-126">This example shows a `TableColumnHeader` element whose label is "Column 1".</span></span>

```xml
<TableColumnHeader>
  <Label>Column 1</Label)
  <Width>16</Width>
  <Alignment>Left</Alignment>
</TableColumnHeader>
```

## <a name="see-also"></a><span data-ttu-id="0db8f-127">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="0db8f-127">See Also</span></span>

[<span data-ttu-id="0db8f-128">Creazione di una visualizzazione tabella</span><span class="sxs-lookup"><span data-stu-id="0db8f-128">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="0db8f-129">Elemento TableColumnHeader (formato)</span><span class="sxs-lookup"><span data-stu-id="0db8f-129">TableColumnHeader Element (Format)</span></span>](./tablecolumnheader-element-format.md)

[<span data-ttu-id="0db8f-130">La scrittura di un File di formattazione di PowerShell</span><span class="sxs-lookup"><span data-stu-id="0db8f-130">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
