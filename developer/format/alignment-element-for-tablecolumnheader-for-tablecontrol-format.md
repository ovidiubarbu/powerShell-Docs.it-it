---
title: Elemento Alignment per TableColumnHeader per Table (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ff85e83a-c9c2-4c37-accc-e6a27c182f3c
caps.latest.revision: 19
ms.openlocfilehash: 16b41535109ca503e679a135f5ba30054e33de5b
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62067009"
---
# <a name="alignment-element-for-tablecolumnheader-for-tablecontrol-format"></a><span data-ttu-id="d303b-102">Elemento Alignment per TableColumnHeader per TableControl (formato)</span><span class="sxs-lookup"><span data-stu-id="d303b-102">Alignment Element for TableColumnHeader for TableControl (Format)</span></span>

<span data-ttu-id="d303b-103">Definisce la modalità di visualizzazione dati in un'intestazione di colonna.</span><span class="sxs-lookup"><span data-stu-id="d303b-103">Defines how the data in a column header is displayed.</span></span>

<span data-ttu-id="d303b-104">Elemento (formato) elemento ViewDefinitions (formato) visualizzazione elemento (formato) elemento Table (formato) elemento TableHeaders (formato) elemento TableColumnHeader (formato) allineamento elemento di configurazione per TableColumnHeader (formato)</span><span class="sxs-lookup"><span data-stu-id="d303b-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) TableControl Element (Format) TableHeaders Element (Format) TableColumnHeader Element (Format) Alignment Element for TableColumnHeader (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="d303b-105">Sintassi</span><span class="sxs-lookup"><span data-stu-id="d303b-105">Syntax</span></span>

```xml
<Alignment>AlignmentType</Alignment>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="d303b-106">Elementi e attributi</span><span class="sxs-lookup"><span data-stu-id="d303b-106">Attributes and Elements</span></span>

<span data-ttu-id="d303b-107">Le sezioni seguenti descrivono gli attributi, elementi figlio ed elemento padre dell'elemento di `Alignment` elemento.</span><span class="sxs-lookup"><span data-stu-id="d303b-107">The following sections describe the attributes, child elements, and parent element of the `Alignment` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="d303b-108">Attributes</span><span class="sxs-lookup"><span data-stu-id="d303b-108">Attributes</span></span>

<span data-ttu-id="d303b-109">Nessuna.</span><span class="sxs-lookup"><span data-stu-id="d303b-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="d303b-110">Elementi figlio</span><span class="sxs-lookup"><span data-stu-id="d303b-110">Child Elements</span></span>

<span data-ttu-id="d303b-111">Nessuna.</span><span class="sxs-lookup"><span data-stu-id="d303b-111">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="d303b-112">Elementi padre</span><span class="sxs-lookup"><span data-stu-id="d303b-112">Parent Elements</span></span>

|<span data-ttu-id="d303b-113">Elemento</span><span class="sxs-lookup"><span data-stu-id="d303b-113">Element</span></span>|<span data-ttu-id="d303b-114">Description</span><span class="sxs-lookup"><span data-stu-id="d303b-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="d303b-115">Elemento TableColumnHeader (formato)</span><span class="sxs-lookup"><span data-stu-id="d303b-115">TableColumnHeader Element (Format)</span></span>](./tablecolumnheader-element-format.md)|<span data-ttu-id="d303b-116">Definisce un'etichetta, la larghezza e l'allineamento dei dati per una colonna della tabella.</span><span class="sxs-lookup"><span data-stu-id="d303b-116">Defines a label, the width, and the alignment of the data for a column of the table.</span></span>|

## <a name="text-value"></a><span data-ttu-id="d303b-117">Valore di testo</span><span class="sxs-lookup"><span data-stu-id="d303b-117">Text Value</span></span>

<span data-ttu-id="d303b-118">Specificare uno dei valori seguenti.</span><span class="sxs-lookup"><span data-stu-id="d303b-118">Specify one of the following values.</span></span> <span data-ttu-id="d303b-119">Questi valori non sono tra maiuscole e minuscole.</span><span class="sxs-lookup"><span data-stu-id="d303b-119">These values are not case-sensitive.</span></span>

<span data-ttu-id="d303b-120">Se questo elemento non viene specificato, questo Allinea a sinistra i dati visualizzati nella colonna a sinistra è il valore predefinito.</span><span class="sxs-lookup"><span data-stu-id="d303b-120">Left Aligns the data displayed in the column on the left This is the default if this element is not specified.</span></span>

<span data-ttu-id="d303b-121">Allinea a destra i dati visualizzati nella colonna a destra.</span><span class="sxs-lookup"><span data-stu-id="d303b-121">Right Aligns the data displayed in the column on the right.</span></span>

<span data-ttu-id="d303b-122">Centri di centro dati visualizzati nella colonna.</span><span class="sxs-lookup"><span data-stu-id="d303b-122">Center Centers the data displayed in the column.</span></span>

## <a name="remarks"></a><span data-ttu-id="d303b-123">Osservazioni</span><span class="sxs-lookup"><span data-stu-id="d303b-123">Remarks</span></span>

<span data-ttu-id="d303b-124">Per altre informazioni sui componenti di visualizzazione di una tabella, vedere [creazione di una visualizzazione tabella](./creating-a-table-view.md).</span><span class="sxs-lookup"><span data-stu-id="d303b-124">For more information about the components of a table view, see [Creating a Table View](./creating-a-table-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="d303b-125">Esempio</span><span class="sxs-lookup"><span data-stu-id="d303b-125">Example</span></span>

<span data-ttu-id="d303b-126">Questo esempio viene illustrato un `TableColumnHeader` elemento la cui data è allineato a sinistra.</span><span class="sxs-lookup"><span data-stu-id="d303b-126">This example shows a `TableColumnHeader` element whose data is aligned on the left.</span></span>

```xml
<TableColumnHeader>
  <Label>Column 1</Label)
  <Width>16</Width>
  <Alignment>Left</Alignment>
</TableColumnHeader>
```

## <a name="see-also"></a><span data-ttu-id="d303b-127">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="d303b-127">See Also</span></span>

[<span data-ttu-id="d303b-128">Creazione di una visualizzazione tabella</span><span class="sxs-lookup"><span data-stu-id="d303b-128">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="d303b-129">Elemento TableColumnHeader (formato)</span><span class="sxs-lookup"><span data-stu-id="d303b-129">TableColumnHeader Element (Format)</span></span>](./tablecolumnheader-element-format.md)

[<span data-ttu-id="d303b-130">La scrittura di un File di formattazione di PowerShell</span><span class="sxs-lookup"><span data-stu-id="d303b-130">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
