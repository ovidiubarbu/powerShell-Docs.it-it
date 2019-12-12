---
title: Elemento FormatString per WideItem per WideControl (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 5bc6ea26-3ca6-4bab-8a13-29189821ba15
caps.latest.revision: 7
ms.openlocfilehash: a1dc145864a6904fd4af6c3b9187819c49e224b0
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/05/2019
ms.locfileid: "72363030"
---
# <a name="formatstring-element-for-wideitem-for-widecontrol-format"></a><span data-ttu-id="78217-102">Elemento FormatString per WideItem per WideControl (formato)</span><span class="sxs-lookup"><span data-stu-id="78217-102">FormatString Element for WideItem for WideControl (Format)</span></span>

<span data-ttu-id="78217-103">Specifica un modello di formato che definisce come viene visualizzato il valore della proprietà o dello script nella visualizzazione.</span><span class="sxs-lookup"><span data-stu-id="78217-103">Specifies a format pattern that defines how the property or script value is displayed in the view.</span></span>

<span data-ttu-id="78217-104">Elemento Configuration (Format) elemento ViewDefinitions (Format) elemento View (Format) elemento WideControl (Format) elemento WideEntries (Format) elemento WideEntry per WideControl (Format) elemento WideItem per WideControl (Format) elemento FormatString per WideItem per WideControl (Format)</span><span class="sxs-lookup"><span data-stu-id="78217-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) WideControl Element (Format) WideEntries Element (Format) WideEntry Element for WideControl (Format) WideItem Element for WideControl (Format) FormatString Element for WideItem for WideControl (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="78217-105">Sintassi</span><span class="sxs-lookup"><span data-stu-id="78217-105">Syntax</span></span>

```xml
<FormatString>PropertyPattern</FormatString>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="78217-106">Attributi ed elementi</span><span class="sxs-lookup"><span data-stu-id="78217-106">Attributes and Elements</span></span>

<span data-ttu-id="78217-107">Nelle sezioni seguenti vengono descritti gli attributi, gli elementi figlio e l'elemento padre dell'elemento `FormatString`.</span><span class="sxs-lookup"><span data-stu-id="78217-107">The following sections describe the attributes, child elements, and the parent element of the `FormatString` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="78217-108">Attributi</span><span class="sxs-lookup"><span data-stu-id="78217-108">Attributes</span></span>

<span data-ttu-id="78217-109">Nessuna.</span><span class="sxs-lookup"><span data-stu-id="78217-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="78217-110">Elementi figlio</span><span class="sxs-lookup"><span data-stu-id="78217-110">Child Elements</span></span>

<span data-ttu-id="78217-111">Nessuna.</span><span class="sxs-lookup"><span data-stu-id="78217-111">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="78217-112">Elementi padre</span><span class="sxs-lookup"><span data-stu-id="78217-112">Parent Elements</span></span>

|<span data-ttu-id="78217-113">Elemento</span><span class="sxs-lookup"><span data-stu-id="78217-113">Element</span></span>|<span data-ttu-id="78217-114">Description</span><span class="sxs-lookup"><span data-stu-id="78217-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="78217-115">Elemento WideItem per WideControl (Format)</span><span class="sxs-lookup"><span data-stu-id="78217-115">WideItem Element for WideControl (Format)</span></span>](./wideitem-element-for-widecontrol-format.md)|<span data-ttu-id="78217-116">Definisce la proprietà o lo script il cui valore viene visualizzato in una riga della visualizzazione elenco.</span><span class="sxs-lookup"><span data-stu-id="78217-116">Defines the property or script whose value is displayed in a row of the list view.</span></span>|

## <a name="text-value"></a><span data-ttu-id="78217-117">Valore testo</span><span class="sxs-lookup"><span data-stu-id="78217-117">Text Value</span></span>

<span data-ttu-id="78217-118">Specificare il modello usato per formattare i dati.</span><span class="sxs-lookup"><span data-stu-id="78217-118">Specify the pattern that is used to format the data.</span></span> <span data-ttu-id="78217-119">Ad esempio, è possibile usare questo modello per formattare il valore di qualsiasi proprietà di tipo [System. TimeSpan](/dotnet/api/System.TimeSpan): {0: mmm} {0: dd} {0: HH}: {0: mm}.</span><span class="sxs-lookup"><span data-stu-id="78217-119">For example, you can use this pattern to format the value of any property that is of type [System.Timespan](/dotnet/api/System.TimeSpan): {0:MMM}{0:dd}{0:HH}:{0:mm}.</span></span>

## <a name="remarks"></a><span data-ttu-id="78217-120">Osservazioni</span><span class="sxs-lookup"><span data-stu-id="78217-120">Remarks</span></span>

<span data-ttu-id="78217-121">Le stringhe di formato possono essere utilizzate durante la creazione di visualizzazioni di tabella, visualizzazioni di elenchi, visualizzazioni estese o visualizzazioni personalizzate.</span><span class="sxs-lookup"><span data-stu-id="78217-121">Format strings can be used when creating table views, list views, wide views, or custom views.</span></span> <span data-ttu-id="78217-122">Per ulteriori informazioni sulla formattazione di un valore visualizzato in una visualizzazione, vedere [formattazione dei dati visualizzati](./formatting-displayed-data.md).</span><span class="sxs-lookup"><span data-stu-id="78217-122">For more information about formatting a value displayed in a view, see [Formatting Displayed Data](./formatting-displayed-data.md).</span></span>

<span data-ttu-id="78217-123">Per ulteriori informazioni sull'utilizzo di stringhe di formato in visualizzazioni estese, vedere [creazione di un'ampia visualizzazione](./creating-a-wide-view.md).</span><span class="sxs-lookup"><span data-stu-id="78217-123">For more information about using format strings in wide views, see [Creating a Wide View](./creating-a-wide-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="78217-124">Esempio</span><span class="sxs-lookup"><span data-stu-id="78217-124">Example</span></span>

<span data-ttu-id="78217-125">Nell'esempio seguente viene illustrato come definire una stringa di formattazione per il valore della proprietà `StartTime`.</span><span class="sxs-lookup"><span data-stu-id="78217-125">The following example shows how to define a formatting string for the value of the `StartTime` property.</span></span>

```xml
<WideItem>
  <PropertyName>StartTime</PropertyName>
  <FormatString>{0:MMM} (0:DD) (0:HH):(0:MM)</FormatString>
</WideItem>
```

## <a name="see-also"></a><span data-ttu-id="78217-126">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="78217-126">See Also</span></span>

[<span data-ttu-id="78217-127">Creazione di una visualizzazione estesa</span><span class="sxs-lookup"><span data-stu-id="78217-127">Creating a Wide View</span></span>](./creating-a-wide-view.md)

[<span data-ttu-id="78217-128">Elemento WideItem per WideControl (Format)</span><span class="sxs-lookup"><span data-stu-id="78217-128">WideItem Element for WideControl (Format)</span></span>](./wideitem-element-for-widecontrol-format.md)

[<span data-ttu-id="78217-129">Scrittura di un file di formattazione e di tipi di Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="78217-129">Writing a Windows PowerShell Formatting and Types File</span></span>](./writing-a-powershell-formatting-file.md)
