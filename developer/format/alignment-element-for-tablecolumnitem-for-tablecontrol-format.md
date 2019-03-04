---
title: Elemento Alignment per TableColumnItem per Table (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: b07a53df-64f1-49b0-8cea-c993b3f1f76b
caps.latest.revision: 10
ms.openlocfilehash: 1bc936b94ee6fd6239e9e3c4afcdb8f14fbe36eb
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/03/2019
ms.locfileid: "56858207"
---
# <a name="alignment-element-for-tablecolumnitem-for-tablecontrol-format"></a><span data-ttu-id="31a22-102">Elemento Alignment per TableColumnItem per TableControl (formato)</span><span class="sxs-lookup"><span data-stu-id="31a22-102">Alignment Element for TableColumnItem for TableControl (Format)</span></span>

<span data-ttu-id="31a22-103">Definisce la modalità di visualizzazione di dati in una colonna della riga.</span><span class="sxs-lookup"><span data-stu-id="31a22-103">Defines how the data in a column of the row is displayed.</span></span>

<span data-ttu-id="31a22-104">Elemento (formato) elemento ViewDefinitions (formato) visualizzazione elemento (formato) elemento Table (formato) elemento TableRowEntries (formato) elemento TableRowEntry (formato) elemento TableColumnItems (formato) TableColumnItem elemento di configurazione (formato) Elemento Alignment per TableColumnItem (formato)</span><span class="sxs-lookup"><span data-stu-id="31a22-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) TableControl Element (Format) TableRowEntries Element (Format) TableRowEntry Element (Format) TableColumnItems Element (Format) TableColumnItem Element (Format) Alignment Element for TableColumnItem (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="31a22-105">Sintassi</span><span class="sxs-lookup"><span data-stu-id="31a22-105">Syntax</span></span>

```xml
<Alignment>AlignmentType</Alignment>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="31a22-106">Attributi ed elementi</span><span class="sxs-lookup"><span data-stu-id="31a22-106">Attributes and Elements</span></span>

<span data-ttu-id="31a22-107">Le sezioni seguenti descrivono gli attributi, elementi figlio ed elemento padre dell'elemento di `Alignment` elemento.</span><span class="sxs-lookup"><span data-stu-id="31a22-107">The following sections describe the attributes, child elements, and parent element of the `Alignment` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="31a22-108">Attributes</span><span class="sxs-lookup"><span data-stu-id="31a22-108">Attributes</span></span>

<span data-ttu-id="31a22-109">Nessuna.</span><span class="sxs-lookup"><span data-stu-id="31a22-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="31a22-110">Elementi figlio</span><span class="sxs-lookup"><span data-stu-id="31a22-110">Child Elements</span></span>

<span data-ttu-id="31a22-111">Nessuna.</span><span class="sxs-lookup"><span data-stu-id="31a22-111">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="31a22-112">Elementi padre</span><span class="sxs-lookup"><span data-stu-id="31a22-112">Parent Elements</span></span>

|<span data-ttu-id="31a22-113">Elemento</span><span class="sxs-lookup"><span data-stu-id="31a22-113">Element</span></span>|<span data-ttu-id="31a22-114">Description</span><span class="sxs-lookup"><span data-stu-id="31a22-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="31a22-115">Elemento TableColumnItem (formato)</span><span class="sxs-lookup"><span data-stu-id="31a22-115">TableColumnItem Element (Format)</span></span>](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md)|<span data-ttu-id="31a22-116">Definisce un'etichetta, la larghezza e l'allineamento dei dati per una colonna della tabella.</span><span class="sxs-lookup"><span data-stu-id="31a22-116">Defines a label, the width, and the alignment of the data for a column of the table.</span></span>|

## <a name="text-value"></a><span data-ttu-id="31a22-117">Valore di testo</span><span class="sxs-lookup"><span data-stu-id="31a22-117">Text Value</span></span>

<span data-ttu-id="31a22-118">Specificare uno dei valori seguenti.</span><span class="sxs-lookup"><span data-stu-id="31a22-118">Specify one of the following values.</span></span> <span data-ttu-id="31a22-119">(Questi valori non sono distinzione maiuscole/minuscole).</span><span class="sxs-lookup"><span data-stu-id="31a22-119">(These values are not case-sensitive.)</span></span>

<span data-ttu-id="31a22-120">Sposta verso sinistra i dati visualizzati nella colonna a sinistra.</span><span class="sxs-lookup"><span data-stu-id="31a22-120">Left Shifts the data displayed in the column to the left.</span></span> <span data-ttu-id="31a22-121">(Questo è il valore predefinito se questo elemento non è specificato).</span><span class="sxs-lookup"><span data-stu-id="31a22-121">(This is the default if this element is not specified.)</span></span>

<span data-ttu-id="31a22-122">Spostamenti a destra i dati visualizzati nella colonna a destra.</span><span class="sxs-lookup"><span data-stu-id="31a22-122">Right Shifts the data displayed in the column to the right.</span></span>

<span data-ttu-id="31a22-123">Centri di centro dati visualizzati nella colonna.</span><span class="sxs-lookup"><span data-stu-id="31a22-123">Center Centers the data displayed in the column.</span></span>

## <a name="remarks"></a><span data-ttu-id="31a22-124">Osservazioni</span><span class="sxs-lookup"><span data-stu-id="31a22-124">Remarks</span></span>

<span data-ttu-id="31a22-125">Per altre informazioni sui componenti di visualizzazione di una tabella, vedere [vista tabella](./creating-a-table-view.md).</span><span class="sxs-lookup"><span data-stu-id="31a22-125">For more information about the components of a table view, see [Table View](./creating-a-table-view.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="31a22-126">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="31a22-126">See Also</span></span>

[<span data-ttu-id="31a22-127">Visualizzazione tabella</span><span class="sxs-lookup"><span data-stu-id="31a22-127">Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="31a22-128">Elemento TableColumnItem (formato)</span><span class="sxs-lookup"><span data-stu-id="31a22-128">TableColumnItem Element (Format)</span></span>](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md)
