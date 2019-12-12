---
title: Elemento FormatString per TableColumnItem per Table ((Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 8a150731-d4b4-4d63-8db5-f14d463c8c37
caps.latest.revision: 13
ms.openlocfilehash: b7e1d0adc43254141056a729e1c1cc9699b6ac9b
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/05/2019
ms.locfileid: "72363710"
---
# <a name="formatstring-element-for-tablecolumnitem-for-tablecontrol-format"></a><span data-ttu-id="f5ac7-102">Elemento FormatString per TableColumnItem per TableControl (formato)</span><span class="sxs-lookup"><span data-stu-id="f5ac7-102">FormatString Element for TableColumnItem for TableControl (Format)</span></span>

<span data-ttu-id="f5ac7-103">Specifica un modello di formato che definisce come viene visualizzato il valore della proprietà o dello script della tabella.</span><span class="sxs-lookup"><span data-stu-id="f5ac7-103">Specifies a format pattern that defines how the property or script value of the table is displayed.</span></span>

<span data-ttu-id="f5ac7-104">Elemento Configuration (Format) elemento ViewDefinitions (Format) elemento View (Format) elemento Table ((Format) elemento TableRowEntries (Format) elemento TableRowEntry (Format) elemento TableColumnItems (Format) elemento TableColumnItem (Format) Elemento FormatString per TableColumnItem (Format)</span><span class="sxs-lookup"><span data-stu-id="f5ac7-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) TableControl Element (Format) TableRowEntries Element (Format) TableRowEntry Element (Format) TableColumnItems Element (Format) TableColumnItem Element (Format) FormatString Element for TableColumnItem (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="f5ac7-105">Sintassi</span><span class="sxs-lookup"><span data-stu-id="f5ac7-105">Syntax</span></span>

```xml
<FormatString>FormatPattern</FormatString>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="f5ac7-106">Attributi ed elementi</span><span class="sxs-lookup"><span data-stu-id="f5ac7-106">Attributes and Elements</span></span>

<span data-ttu-id="f5ac7-107">Nelle sezioni seguenti vengono descritti gli attributi, gli elementi figlio e l'elemento padre dell'elemento `FormatString`.</span><span class="sxs-lookup"><span data-stu-id="f5ac7-107">The following sections describe attributes, child elements, and the parent element of the `FormatString` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="f5ac7-108">Attributi</span><span class="sxs-lookup"><span data-stu-id="f5ac7-108">Attributes</span></span>

<span data-ttu-id="f5ac7-109">Nessuna.</span><span class="sxs-lookup"><span data-stu-id="f5ac7-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="f5ac7-110">Elementi figlio</span><span class="sxs-lookup"><span data-stu-id="f5ac7-110">Child Elements</span></span>

<span data-ttu-id="f5ac7-111">Nessuna.</span><span class="sxs-lookup"><span data-stu-id="f5ac7-111">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="f5ac7-112">Elementi padre</span><span class="sxs-lookup"><span data-stu-id="f5ac7-112">Parent Elements</span></span>

|<span data-ttu-id="f5ac7-113">Elemento</span><span class="sxs-lookup"><span data-stu-id="f5ac7-113">Element</span></span>|<span data-ttu-id="f5ac7-114">Description</span><span class="sxs-lookup"><span data-stu-id="f5ac7-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="f5ac7-115">Elemento TableColumnItem (Format)</span><span class="sxs-lookup"><span data-stu-id="f5ac7-115">TableColumnItem Element (Format)</span></span>](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md)|<span data-ttu-id="f5ac7-116">Definisce la proprietà o lo script il cui valore viene visualizzato nella colonna della riga.</span><span class="sxs-lookup"><span data-stu-id="f5ac7-116">Defines the property or script whose value is displayed in the column of the row.</span></span>|

## <a name="text-value"></a><span data-ttu-id="f5ac7-117">Valore testo</span><span class="sxs-lookup"><span data-stu-id="f5ac7-117">Text Value</span></span>

<span data-ttu-id="f5ac7-118">Specificare il modello usato per formattare i dati.</span><span class="sxs-lookup"><span data-stu-id="f5ac7-118">Specify the pattern that is used to format the data.</span></span> <span data-ttu-id="f5ac7-119">Questo modello, ad esempio, può essere utilizzato per formattare il valore di qualsiasi proprietà di tipo [System. TimeSpan](/dotnet/api/System.TimeSpan): {0: mmm} {0: dd} {0: HH}: {0: mm}.</span><span class="sxs-lookup"><span data-stu-id="f5ac7-119">For example, this pattern can be used to format the value of any property that is of type [System.Timespan](/dotnet/api/System.TimeSpan): {0:MMM}{0:dd}{0:HH}:{0:mm}.</span></span>

## <a name="remarks"></a><span data-ttu-id="f5ac7-120">Osservazioni</span><span class="sxs-lookup"><span data-stu-id="f5ac7-120">Remarks</span></span>

<span data-ttu-id="f5ac7-121">Le stringhe di formato possono essere utilizzate durante la creazione di visualizzazioni di tabella, visualizzazioni di elenchi, visualizzazioni estese o visualizzazioni personalizzate.</span><span class="sxs-lookup"><span data-stu-id="f5ac7-121">Format strings can be used when creating table views, list views, wide views, or custom views.</span></span> <span data-ttu-id="f5ac7-122">Per ulteriori informazioni sulla formattazione di un valore visualizzato in una visualizzazione, vedere [formattazione dei dati visualizzati](./formatting-displayed-data.md).</span><span class="sxs-lookup"><span data-stu-id="f5ac7-122">For more information about formatting a value displayed in a view, see [Formatting Displayed Data](./formatting-displayed-data.md).</span></span>

<span data-ttu-id="f5ac7-123">Per ulteriori informazioni sui componenti di una vista tabella, vedere [visualizzazione tabella](./creating-a-table-view.md).</span><span class="sxs-lookup"><span data-stu-id="f5ac7-123">For more information about the components of a table view, see [Table View](./creating-a-table-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="f5ac7-124">Esempio</span><span class="sxs-lookup"><span data-stu-id="f5ac7-124">Example</span></span>

<span data-ttu-id="f5ac7-125">Nell'esempio seguente viene illustrato come definire una stringa di formattazione per il valore della proprietà `StartTime`.</span><span class="sxs-lookup"><span data-stu-id="f5ac7-125">The following example shows how to define a formatting string for the value of the `StartTime` property.</span></span>

```xml
<TableColumnItem>
  <PropertyName>StartTime</PropertyName>
  <FormatString>{0:MMM} (0:DD) (0:HH):(0:MM)</FormatString>
</TableColumnItem>
```

## <a name="see-also"></a><span data-ttu-id="f5ac7-126">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="f5ac7-126">See Also</span></span>

[<span data-ttu-id="f5ac7-127">Creazione di una vista tabella</span><span class="sxs-lookup"><span data-stu-id="f5ac7-127">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="f5ac7-128">Formattazione dei dati visualizzati</span><span class="sxs-lookup"><span data-stu-id="f5ac7-128">Formatting Displayed Data</span></span>](./formatting-displayed-data.md)

[<span data-ttu-id="f5ac7-129">Elemento TableColumnItem (Format)</span><span class="sxs-lookup"><span data-stu-id="f5ac7-129">TableColumnItem Element (Format)</span></span>](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md)

[<span data-ttu-id="f5ac7-130">Scrittura di un file di formattazione di PowerShell</span><span class="sxs-lookup"><span data-stu-id="f5ac7-130">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
