---
title: Elemento FormatString per TableColumnItem per Table (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 8a150731-d4b4-4d63-8db5-f14d463c8c37
caps.latest.revision: 13
ms.openlocfilehash: b7e1d0adc43254141056a729e1c1cc9699b6ac9b
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/03/2019
ms.locfileid: "56854327"
---
# <a name="formatstring-element-for-tablecolumnitem-for-tablecontrol-format"></a><span data-ttu-id="13785-102">Elemento FormatString per TableColumnItem per TableControl (formato)</span><span class="sxs-lookup"><span data-stu-id="13785-102">FormatString Element for TableColumnItem for TableControl (Format)</span></span>

<span data-ttu-id="13785-103">Specifica un modello di formato che definisce come viene visualizzato il valore di proprietà o lo script della tabella.</span><span class="sxs-lookup"><span data-stu-id="13785-103">Specifies a format pattern that defines how the property or script value of the table is displayed.</span></span>

<span data-ttu-id="13785-104">Elemento (formato) elemento ViewDefinitions (formato) visualizzazione elemento (formato) elemento Table (formato) elemento TableRowEntries (formato) elemento TableRowEntry (formato) elemento TableColumnItems (formato) TableColumnItem elemento di configurazione (formato) Elemento FormatString per TableColumnItem (formato)</span><span class="sxs-lookup"><span data-stu-id="13785-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) TableControl Element (Format) TableRowEntries Element (Format) TableRowEntry Element (Format) TableColumnItems Element (Format) TableColumnItem Element (Format) FormatString Element for TableColumnItem (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="13785-105">Sintassi</span><span class="sxs-lookup"><span data-stu-id="13785-105">Syntax</span></span>

```xml
<FormatString>FormatPattern</FormatString>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="13785-106">Attributi ed elementi</span><span class="sxs-lookup"><span data-stu-id="13785-106">Attributes and Elements</span></span>

<span data-ttu-id="13785-107">Le sezioni seguenti descrivono gli attributi e gli elementi figlio dell'elemento padre del `FormatString` elemento.</span><span class="sxs-lookup"><span data-stu-id="13785-107">The following sections describe attributes, child elements, and the parent element of the `FormatString` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="13785-108">Attributes</span><span class="sxs-lookup"><span data-stu-id="13785-108">Attributes</span></span>

<span data-ttu-id="13785-109">Nessuna.</span><span class="sxs-lookup"><span data-stu-id="13785-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="13785-110">Elementi figlio</span><span class="sxs-lookup"><span data-stu-id="13785-110">Child Elements</span></span>

<span data-ttu-id="13785-111">Nessuna.</span><span class="sxs-lookup"><span data-stu-id="13785-111">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="13785-112">Elementi padre</span><span class="sxs-lookup"><span data-stu-id="13785-112">Parent Elements</span></span>

|<span data-ttu-id="13785-113">Elemento</span><span class="sxs-lookup"><span data-stu-id="13785-113">Element</span></span>|<span data-ttu-id="13785-114">Description</span><span class="sxs-lookup"><span data-stu-id="13785-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="13785-115">Elemento TableColumnItem (formato)</span><span class="sxs-lookup"><span data-stu-id="13785-115">TableColumnItem Element (Format)</span></span>](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md)|<span data-ttu-id="13785-116">Definisce le proprietà il cui valore viene visualizzato nella colonna della riga di script.</span><span class="sxs-lookup"><span data-stu-id="13785-116">Defines the property or script whose value is displayed in the column of the row.</span></span>|

## <a name="text-value"></a><span data-ttu-id="13785-117">Valore di testo</span><span class="sxs-lookup"><span data-stu-id="13785-117">Text Value</span></span>

<span data-ttu-id="13785-118">Specificare il modello utilizzato per formattare i dati.</span><span class="sxs-lookup"><span data-stu-id="13785-118">Specify the pattern that is used to format the data.</span></span> <span data-ttu-id="13785-119">Ad esempio, questo modello è utilizzabile per formattare il valore di qualsiasi proprietà che è di tipo [System. TimeSpan](/dotnet/api/System.TimeSpan): {0: MMM} {0:dd} {{0:hh}: {0:mm}.</span><span class="sxs-lookup"><span data-stu-id="13785-119">For example, this pattern can be used to format the value of any property that is of type [System.Timespan](/dotnet/api/System.TimeSpan): {0:MMM}{0:dd}{0:HH}:{0:mm}.</span></span>

## <a name="remarks"></a><span data-ttu-id="13785-120">Osservazioni</span><span class="sxs-lookup"><span data-stu-id="13785-120">Remarks</span></span>

<span data-ttu-id="13785-121">Stringhe di formato possono essere usate durante la creazione di viste delle tabelle, elencare le visualizzazioni, visualizzazioni ampie o visualizzazioni personalizzate.</span><span class="sxs-lookup"><span data-stu-id="13785-121">Format strings can be used when creating table views, list views, wide views, or custom views.</span></span> <span data-ttu-id="13785-122">Per altre informazioni sulla formattazione di un valore visualizzato in una vista, vedere [formattazione dei dati visualizzati](./formatting-displayed-data.md).</span><span class="sxs-lookup"><span data-stu-id="13785-122">For more information about formatting a value displayed in a view, see [Formatting Displayed Data](./formatting-displayed-data.md).</span></span>

<span data-ttu-id="13785-123">Per altre informazioni sui componenti di visualizzazione di una tabella, vedere [vista tabella](./creating-a-table-view.md).</span><span class="sxs-lookup"><span data-stu-id="13785-123">For more information about the components of a table view, see [Table View](./creating-a-table-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="13785-124">Esempio</span><span class="sxs-lookup"><span data-stu-id="13785-124">Example</span></span>

<span data-ttu-id="13785-125">Nell'esempio seguente viene illustrato come definire una stringa di formattazione per il valore della `StartTime` proprietà.</span><span class="sxs-lookup"><span data-stu-id="13785-125">The following example shows how to define a formatting string for the value of the `StartTime` property.</span></span>

```xml
<TableColumnItem>
  <PropertyName>StartTime</PropertyName>
  <FormatString>{0:MMM} (0:DD) (0:HH):(0:MM)</FormatString>
</TableColumnItem>
```

## <a name="see-also"></a><span data-ttu-id="13785-126">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="13785-126">See Also</span></span>

[<span data-ttu-id="13785-127">Creazione di una visualizzazione tabella</span><span class="sxs-lookup"><span data-stu-id="13785-127">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="13785-128">Formattazione dei dati visualizzati</span><span class="sxs-lookup"><span data-stu-id="13785-128">Formatting Displayed Data</span></span>](./formatting-displayed-data.md)

[<span data-ttu-id="13785-129">Elemento TableColumnItem (formato)</span><span class="sxs-lookup"><span data-stu-id="13785-129">TableColumnItem Element (Format)</span></span>](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md)

[<span data-ttu-id="13785-130">La scrittura di un File di formattazione di PowerShell</span><span class="sxs-lookup"><span data-stu-id="13785-130">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
