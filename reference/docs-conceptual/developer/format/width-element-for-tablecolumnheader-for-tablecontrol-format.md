---
title: Elemento Width per TableColumnHeader per Table ((Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 94eb0535-8002-4f17-9a2b-4be75ec20e5c
caps.latest.revision: 18
ms.openlocfilehash: 4a25c9d81df670dc10955065bfb66766cdb1bd33
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/05/2019
ms.locfileid: "72367870"
---
# <a name="width-element-for-tablecolumnheader-for-tablecontrol-format"></a><span data-ttu-id="94c23-102">Elemento Width per TableColumnHeader per TableControl (formato)</span><span class="sxs-lookup"><span data-stu-id="94c23-102">Width Element for TableColumnHeader for TableControl (Format)</span></span>

<span data-ttu-id="94c23-103">Definisce la larghezza (in caratteri) di una colonna.</span><span class="sxs-lookup"><span data-stu-id="94c23-103">Defines the width (in characters) of a column.</span></span>

<span data-ttu-id="94c23-104">Elemento Configuration (Format) elemento ViewDefinitions (Format) elemento View (Format) elemento Table ((Format) elemento TableHeaders per Table ((Format) TableColumnHeader elemento TableHeaders per Table ((Format) elemento Width per TableColumnHeader per Table ((Format)</span><span class="sxs-lookup"><span data-stu-id="94c23-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) TableControl Element (Format) TableHeaders Element for TableControl (Format) TableColumnHeader Element TableHeaders for TableControl (Format) Width Element for TableColumnHeader for TableControl (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="94c23-105">Sintassi</span><span class="sxs-lookup"><span data-stu-id="94c23-105">Syntax</span></span>

```xml
<Width>NumberOfCharacters</Width>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="94c23-106">Attributi ed elementi</span><span class="sxs-lookup"><span data-stu-id="94c23-106">Attributes and Elements</span></span>

<span data-ttu-id="94c23-107">Le sezioni seguenti descrivono gli attributi, gli elementi figlio e l'elemento padre dell'elemento `Width` usato durante la definizione delle intestazioni di colonna.</span><span class="sxs-lookup"><span data-stu-id="94c23-107">The following sections describe the attributes, child elements, and parent element of the `Width` element used when defining column headers.</span></span>

### <a name="attributes"></a><span data-ttu-id="94c23-108">Attributi</span><span class="sxs-lookup"><span data-stu-id="94c23-108">Attributes</span></span>

<span data-ttu-id="94c23-109">Nessuna.</span><span class="sxs-lookup"><span data-stu-id="94c23-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="94c23-110">Elementi figlio</span><span class="sxs-lookup"><span data-stu-id="94c23-110">Child Elements</span></span>

<span data-ttu-id="94c23-111">Nessuna.</span><span class="sxs-lookup"><span data-stu-id="94c23-111">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="94c23-112">Elementi padre</span><span class="sxs-lookup"><span data-stu-id="94c23-112">Parent Elements</span></span>

|<span data-ttu-id="94c23-113">Elemento</span><span class="sxs-lookup"><span data-stu-id="94c23-113">Element</span></span>|<span data-ttu-id="94c23-114">Description</span><span class="sxs-lookup"><span data-stu-id="94c23-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="94c23-115">Elemento TableColumnHeader per TableHeaders per Table ((Format)</span><span class="sxs-lookup"><span data-stu-id="94c23-115">TableColumnHeader Element for TableHeaders for TableControl (Format)</span></span>](./tablecolumnheader-element-format.md)|<span data-ttu-id="94c23-116">Definisce un'etichetta, la larghezza e l'allineamento dei dati per una colonna della tabella.</span><span class="sxs-lookup"><span data-stu-id="94c23-116">Defines a label, width, and alignment of the data for a column of the table.</span></span>|

## <a name="text-value"></a><span data-ttu-id="94c23-117">Valore testo</span><span class="sxs-lookup"><span data-stu-id="94c23-117">Text Value</span></span>

<span data-ttu-id="94c23-118">Quando possibile, specificare una larghezza (in caratteri) maggiore della lunghezza dei valori delle proprietà visualizzate.</span><span class="sxs-lookup"><span data-stu-id="94c23-118">When at all possible, specify a width (in characters) that is greater than the length of the displayed property values.</span></span>

## <a name="remarks"></a><span data-ttu-id="94c23-119">Osservazioni</span><span class="sxs-lookup"><span data-stu-id="94c23-119">Remarks</span></span>

<span data-ttu-id="94c23-120">Per ulteriori informazioni sui componenti di una vista tabella, vedere [creazione di una vista tabella](./creating-a-table-view.md).</span><span class="sxs-lookup"><span data-stu-id="94c23-120">For more information about the components of a table view, see [Creating a Table View](./creating-a-table-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="94c23-121">Esempio</span><span class="sxs-lookup"><span data-stu-id="94c23-121">Example</span></span>

<span data-ttu-id="94c23-122">Nell'esempio seguente viene illustrato un elemento `TableColumnHeader` la cui larghezza è 16 caratteri.</span><span class="sxs-lookup"><span data-stu-id="94c23-122">The following example shows a `TableColumnHeader` element whose width is 16 characters.</span></span>

```xml
<TableColumnHeader>
  <Label>Column 1</Label)
  <Width>16</Width>
  <Alignment>Left</Alignment>
</TableColumnHeader>
```

## <a name="see-also"></a><span data-ttu-id="94c23-123">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="94c23-123">See Also</span></span>

[<span data-ttu-id="94c23-124">Creazione di una vista tabella</span><span class="sxs-lookup"><span data-stu-id="94c23-124">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="94c23-125">Elemento TableColumnHeader per TableHeader per Table ((Format)</span><span class="sxs-lookup"><span data-stu-id="94c23-125">TableColumnHeader Element for TableHeader for TableControl (Format)</span></span>](./tablecolumnheader-element-format.md)

[<span data-ttu-id="94c23-126">Scrittura di un file di formattazione di PowerShell</span><span class="sxs-lookup"><span data-stu-id="94c23-126">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
