---
title: Elemento Alignment per TableColumnItem per Table ((Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: b07a53df-64f1-49b0-8cea-c993b3f1f76b
caps.latest.revision: 10
ms.openlocfilehash: 1bc936b94ee6fd6239e9e3c4afcdb8f14fbe36eb
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/05/2019
ms.locfileid: "72369080"
---
# <a name="alignment-element-for-tablecolumnitem-for-tablecontrol-format"></a><span data-ttu-id="48fba-102">Elemento Alignment per TableColumnItem per TableControl (formato)</span><span class="sxs-lookup"><span data-stu-id="48fba-102">Alignment Element for TableColumnItem for TableControl (Format)</span></span>

<span data-ttu-id="48fba-103">Definisce la modalità di visualizzazione dei dati in una colonna della riga.</span><span class="sxs-lookup"><span data-stu-id="48fba-103">Defines how the data in a column of the row is displayed.</span></span>

<span data-ttu-id="48fba-104">Elemento Configuration (Format) elemento ViewDefinitions (Format) elemento View (Format) elemento Table ((Format) elemento TableRowEntries (Format) elemento TableRowEntry (Format) elemento TableColumnItems (Format) elemento TableColumnItem (Format) Elemento Alignment per TableColumnItem (Format)</span><span class="sxs-lookup"><span data-stu-id="48fba-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) TableControl Element (Format) TableRowEntries Element (Format) TableRowEntry Element (Format) TableColumnItems Element (Format) TableColumnItem Element (Format) Alignment Element for TableColumnItem (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="48fba-105">Sintassi</span><span class="sxs-lookup"><span data-stu-id="48fba-105">Syntax</span></span>

```xml
<Alignment>AlignmentType</Alignment>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="48fba-106">Attributi ed elementi</span><span class="sxs-lookup"><span data-stu-id="48fba-106">Attributes and Elements</span></span>

<span data-ttu-id="48fba-107">Nelle sezioni seguenti vengono descritti gli attributi, gli elementi figlio e l'elemento padre dell'elemento `Alignment`.</span><span class="sxs-lookup"><span data-stu-id="48fba-107">The following sections describe the attributes, child elements, and parent element of the `Alignment` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="48fba-108">Attributi</span><span class="sxs-lookup"><span data-stu-id="48fba-108">Attributes</span></span>

<span data-ttu-id="48fba-109">Nessuna.</span><span class="sxs-lookup"><span data-stu-id="48fba-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="48fba-110">Elementi figlio</span><span class="sxs-lookup"><span data-stu-id="48fba-110">Child Elements</span></span>

<span data-ttu-id="48fba-111">Nessuna.</span><span class="sxs-lookup"><span data-stu-id="48fba-111">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="48fba-112">Elementi padre</span><span class="sxs-lookup"><span data-stu-id="48fba-112">Parent Elements</span></span>

|<span data-ttu-id="48fba-113">Elemento</span><span class="sxs-lookup"><span data-stu-id="48fba-113">Element</span></span>|<span data-ttu-id="48fba-114">Description</span><span class="sxs-lookup"><span data-stu-id="48fba-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="48fba-115">Elemento TableColumnItem (Format)</span><span class="sxs-lookup"><span data-stu-id="48fba-115">TableColumnItem Element (Format)</span></span>](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md)|<span data-ttu-id="48fba-116">Definisce un'etichetta, la larghezza e l'allineamento dei dati per una colonna della tabella.</span><span class="sxs-lookup"><span data-stu-id="48fba-116">Defines a label, the width, and the alignment of the data for a column of the table.</span></span>|

## <a name="text-value"></a><span data-ttu-id="48fba-117">Valore testo</span><span class="sxs-lookup"><span data-stu-id="48fba-117">Text Value</span></span>

<span data-ttu-id="48fba-118">Specificare uno dei valori seguenti.</span><span class="sxs-lookup"><span data-stu-id="48fba-118">Specify one of the following values.</span></span> <span data-ttu-id="48fba-119">(Questi valori non fanno distinzione tra maiuscole e minuscole).</span><span class="sxs-lookup"><span data-stu-id="48fba-119">(These values are not case-sensitive.)</span></span>

<span data-ttu-id="48fba-120">Left sposta i dati visualizzati nella colonna a sinistra.</span><span class="sxs-lookup"><span data-stu-id="48fba-120">Left Shifts the data displayed in the column to the left.</span></span> <span data-ttu-id="48fba-121">Questo è il valore predefinito se questo elemento non è specificato.</span><span class="sxs-lookup"><span data-stu-id="48fba-121">(This is the default if this element is not specified.)</span></span>

<span data-ttu-id="48fba-122">Sposta a destra i dati visualizzati nella colonna a destra.</span><span class="sxs-lookup"><span data-stu-id="48fba-122">Right Shifts the data displayed in the column to the right.</span></span>

<span data-ttu-id="48fba-123">Allinea al centro i dati visualizzati nella colonna.</span><span class="sxs-lookup"><span data-stu-id="48fba-123">Center Centers the data displayed in the column.</span></span>

## <a name="remarks"></a><span data-ttu-id="48fba-124">Osservazioni</span><span class="sxs-lookup"><span data-stu-id="48fba-124">Remarks</span></span>

<span data-ttu-id="48fba-125">Per ulteriori informazioni sui componenti di una vista tabella, vedere [visualizzazione tabella](./creating-a-table-view.md).</span><span class="sxs-lookup"><span data-stu-id="48fba-125">For more information about the components of a table view, see [Table View](./creating-a-table-view.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="48fba-126">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="48fba-126">See Also</span></span>

[<span data-ttu-id="48fba-127">Visualizzazione tabella</span><span class="sxs-lookup"><span data-stu-id="48fba-127">Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="48fba-128">Elemento TableColumnItem (Format)</span><span class="sxs-lookup"><span data-stu-id="48fba-128">TableColumnItem Element (Format)</span></span>](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md)
