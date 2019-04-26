---
title: Elemento FormatString per WideItem per WideControl (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 5bc6ea26-3ca6-4bab-8a13-29189821ba15
caps.latest.revision: 7
ms.openlocfilehash: a1dc145864a6904fd4af6c3b9187819c49e224b0
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62065683"
---
# <a name="formatstring-element-for-wideitem-for-widecontrol-format"></a><span data-ttu-id="2ccf9-102">Elemento FormatString per WideItem per WideControl (formato)</span><span class="sxs-lookup"><span data-stu-id="2ccf9-102">FormatString Element for WideItem for WideControl (Format)</span></span>

<span data-ttu-id="2ccf9-103">Specifica un modello di formato che definisce come viene visualizzato il valore di proprietà o lo script nella visualizzazione.</span><span class="sxs-lookup"><span data-stu-id="2ccf9-103">Specifies a format pattern that defines how the property or script value is displayed in the view.</span></span>

<span data-ttu-id="2ccf9-104">Elemento (formato) elemento ViewDefinitions (formato) visualizzazione elemento (formato) elemento WideControl (formato) elemento WideEntries (formato) WideEntry elemento di configurazione per WideControl (formato) WideItem elemento per elemento FormatString WideControl (formato) per WideItem per WideControl (formato)</span><span class="sxs-lookup"><span data-stu-id="2ccf9-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) WideControl Element (Format) WideEntries Element (Format) WideEntry Element for WideControl (Format) WideItem Element for WideControl (Format) FormatString Element for WideItem for WideControl (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="2ccf9-105">Sintassi</span><span class="sxs-lookup"><span data-stu-id="2ccf9-105">Syntax</span></span>

```xml
<FormatString>PropertyPattern</FormatString>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="2ccf9-106">Elementi e attributi</span><span class="sxs-lookup"><span data-stu-id="2ccf9-106">Attributes and Elements</span></span>

<span data-ttu-id="2ccf9-107">Le sezioni seguenti descrivono gli attributi e gli elementi figlio dell'elemento padre del `FormatString` elemento.</span><span class="sxs-lookup"><span data-stu-id="2ccf9-107">The following sections describe the attributes, child elements, and the parent element of the `FormatString` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="2ccf9-108">Attributes</span><span class="sxs-lookup"><span data-stu-id="2ccf9-108">Attributes</span></span>

<span data-ttu-id="2ccf9-109">Nessuna.</span><span class="sxs-lookup"><span data-stu-id="2ccf9-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="2ccf9-110">Elementi figlio</span><span class="sxs-lookup"><span data-stu-id="2ccf9-110">Child Elements</span></span>

<span data-ttu-id="2ccf9-111">Nessuna.</span><span class="sxs-lookup"><span data-stu-id="2ccf9-111">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="2ccf9-112">Elementi padre</span><span class="sxs-lookup"><span data-stu-id="2ccf9-112">Parent Elements</span></span>

|<span data-ttu-id="2ccf9-113">Elemento</span><span class="sxs-lookup"><span data-stu-id="2ccf9-113">Element</span></span>|<span data-ttu-id="2ccf9-114">Description</span><span class="sxs-lookup"><span data-stu-id="2ccf9-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="2ccf9-115">Elemento WideItem per WideControl (formato)</span><span class="sxs-lookup"><span data-stu-id="2ccf9-115">WideItem Element for WideControl (Format)</span></span>](./wideitem-element-for-widecontrol-format.md)|<span data-ttu-id="2ccf9-116">Definisce proprietà o script il cui valore viene visualizzato in una riga della visualizzazione elenco.</span><span class="sxs-lookup"><span data-stu-id="2ccf9-116">Defines the property or script whose value is displayed in a row of the list view.</span></span>|

## <a name="text-value"></a><span data-ttu-id="2ccf9-117">Valore di testo</span><span class="sxs-lookup"><span data-stu-id="2ccf9-117">Text Value</span></span>

<span data-ttu-id="2ccf9-118">Specificare il modello utilizzato per formattare i dati.</span><span class="sxs-lookup"><span data-stu-id="2ccf9-118">Specify the pattern that is used to format the data.</span></span> <span data-ttu-id="2ccf9-119">Ad esempio, è possibile usare questo modello per formattare il valore di qualsiasi proprietà che è di tipo [System. TimeSpan](/dotnet/api/System.TimeSpan): {0: MMM} {0:dd} {{0:hh}: {0:mm}.</span><span class="sxs-lookup"><span data-stu-id="2ccf9-119">For example, you can use this pattern to format the value of any property that is of type [System.Timespan](/dotnet/api/System.TimeSpan): {0:MMM}{0:dd}{0:HH}:{0:mm}.</span></span>

## <a name="remarks"></a><span data-ttu-id="2ccf9-120">Osservazioni</span><span class="sxs-lookup"><span data-stu-id="2ccf9-120">Remarks</span></span>

<span data-ttu-id="2ccf9-121">Stringhe di formato possono essere usate durante la creazione di viste delle tabelle, elencare le visualizzazioni, visualizzazioni ampie o visualizzazioni personalizzate.</span><span class="sxs-lookup"><span data-stu-id="2ccf9-121">Format strings can be used when creating table views, list views, wide views, or custom views.</span></span> <span data-ttu-id="2ccf9-122">Per altre informazioni sulla formattazione di un valore visualizzato in una vista, vedere [formattazione dei dati visualizzati](./formatting-displayed-data.md).</span><span class="sxs-lookup"><span data-stu-id="2ccf9-122">For more information about formatting a value displayed in a view, see [Formatting Displayed Data](./formatting-displayed-data.md).</span></span>

<span data-ttu-id="2ccf9-123">Per altre informazioni sull'uso di stringhe di formato in visualizzazioni ampie, vedere [creazione di una visualizzazione più ampia](./creating-a-wide-view.md).</span><span class="sxs-lookup"><span data-stu-id="2ccf9-123">For more information about using format strings in wide views, see [Creating a Wide View](./creating-a-wide-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="2ccf9-124">Esempio</span><span class="sxs-lookup"><span data-stu-id="2ccf9-124">Example</span></span>

<span data-ttu-id="2ccf9-125">Nell'esempio seguente viene illustrato come definire una stringa di formattazione per il valore della `StartTime` proprietà.</span><span class="sxs-lookup"><span data-stu-id="2ccf9-125">The following example shows how to define a formatting string for the value of the `StartTime` property.</span></span>

```xml
<WideItem>
  <PropertyName>StartTime</PropertyName>
  <FormatString>{0:MMM} (0:DD) (0:HH):(0:MM)</FormatString>
</WideItem>
```

## <a name="see-also"></a><span data-ttu-id="2ccf9-126">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="2ccf9-126">See Also</span></span>

[<span data-ttu-id="2ccf9-127">Creazione di una visualizzazione più ampia</span><span class="sxs-lookup"><span data-stu-id="2ccf9-127">Creating a Wide View</span></span>](./creating-a-wide-view.md)

[<span data-ttu-id="2ccf9-128">Elemento WideItem per WideControl (formato)</span><span class="sxs-lookup"><span data-stu-id="2ccf9-128">WideItem Element for WideControl (Format)</span></span>](./wideitem-element-for-widecontrol-format.md)

[<span data-ttu-id="2ccf9-129">La scrittura di un metodo di formattazione di Windows PowerShell e i tipi di File</span><span class="sxs-lookup"><span data-stu-id="2ccf9-129">Writing a Windows PowerShell Formatting and Types File</span></span>](./writing-a-powershell-formatting-file.md)
