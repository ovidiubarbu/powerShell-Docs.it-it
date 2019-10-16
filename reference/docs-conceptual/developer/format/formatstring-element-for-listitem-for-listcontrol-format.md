---
title: Elemento FormatString per ListItem per ListControl (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: fd2cac66-88bb-449f-9d47-bd2cd4fe1801
caps.latest.revision: 13
ms.openlocfilehash: e6024ec4f7fc490c92408047c8c15c775e45bf9d
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/15/2019
ms.locfileid: "72363020"
---
# <a name="formatstring-element-for-listitem-for-listcontrol--format"></a><span data-ttu-id="25dc5-102">Elemento FormatString per ListItem per ListControl (formato)</span><span class="sxs-lookup"><span data-stu-id="25dc5-102">FormatString Element for ListItem for ListControl  (Format)</span></span>

<span data-ttu-id="25dc5-103">Specifica un modello di formato che definisce come viene visualizzato il valore della proprietà o dello script.</span><span class="sxs-lookup"><span data-stu-id="25dc5-103">Specifies a format pattern that defines how the property or script value is displayed.</span></span>

<span data-ttu-id="25dc5-104">Elemento Configuration (Format) elemento ViewDefinitions (Format) elemento View (Format) elemento ListControl (Format) elemento ListEntries per ListControl (Format) elemento ListEntry per ListControl (Format) elemento ListItems per ListControl (Format) Elemento ListItem per ListControl (Format) elemento FormatString per ListItem per ListControl (Format)</span><span class="sxs-lookup"><span data-stu-id="25dc5-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) ListControl Element (Format) ListEntries Element for ListControl (Format) ListEntry Element for ListControl (Format) ListItems Element for ListControl (Format) ListItem Element for ListControl (Format) FormatString Element for ListItem for ListControl (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="25dc5-105">Sintassi</span><span class="sxs-lookup"><span data-stu-id="25dc5-105">Syntax</span></span>

```xml
<FormatString>PropertyPattern</FormatString>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="25dc5-106">Attributi ed elementi</span><span class="sxs-lookup"><span data-stu-id="25dc5-106">Attributes and Elements</span></span>

<span data-ttu-id="25dc5-107">Nelle sezioni seguenti vengono descritti gli attributi, gli elementi figlio e l'elemento padre dell'elemento `FormatString`.</span><span class="sxs-lookup"><span data-stu-id="25dc5-107">The following sections describe the attributes, child elements, and the parent element of the `FormatString` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="25dc5-108">Attributi</span><span class="sxs-lookup"><span data-stu-id="25dc5-108">Attributes</span></span>

<span data-ttu-id="25dc5-109">Nessuna.</span><span class="sxs-lookup"><span data-stu-id="25dc5-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="25dc5-110">Elementi figlio</span><span class="sxs-lookup"><span data-stu-id="25dc5-110">Child Elements</span></span>

<span data-ttu-id="25dc5-111">Nessuna.</span><span class="sxs-lookup"><span data-stu-id="25dc5-111">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="25dc5-112">Elementi padre</span><span class="sxs-lookup"><span data-stu-id="25dc5-112">Parent Elements</span></span>

|<span data-ttu-id="25dc5-113">Elemento</span><span class="sxs-lookup"><span data-stu-id="25dc5-113">Element</span></span>|<span data-ttu-id="25dc5-114">Description</span><span class="sxs-lookup"><span data-stu-id="25dc5-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="25dc5-115">Elemento ListItem (Format)</span><span class="sxs-lookup"><span data-stu-id="25dc5-115">ListItem Element (Format)</span></span>](./listitem-element-for-listitems-for-listcontrol-format.md)|<span data-ttu-id="25dc5-116">Definisce la proprietà o lo script il cui valore viene visualizzato in una riga della visualizzazione elenco.</span><span class="sxs-lookup"><span data-stu-id="25dc5-116">Defines the property or script whose value is displayed in a row of the list view.</span></span>|

## <a name="text-value"></a><span data-ttu-id="25dc5-117">Valore di testo</span><span class="sxs-lookup"><span data-stu-id="25dc5-117">Text Value</span></span>

<span data-ttu-id="25dc5-118">Specificare il modello usato per formattare i dati.</span><span class="sxs-lookup"><span data-stu-id="25dc5-118">Specify the pattern that is used to format the data.</span></span> <span data-ttu-id="25dc5-119">Ad esempio, è possibile usare questo modello per formattare il valore di qualsiasi proprietà di tipo [System. TimeSpan](/dotnet/api/System.TimeSpan): {0: mmm} {0: dd} {0: HH}: {0: mm}.</span><span class="sxs-lookup"><span data-stu-id="25dc5-119">For example, you can use this pattern to format the value of any property that is of type [System.Timespan](/dotnet/api/System.TimeSpan): {0:MMM}{0:dd}{0:HH}:{0:mm}.</span></span>

## <a name="remarks"></a><span data-ttu-id="25dc5-120">Osservazioni</span><span class="sxs-lookup"><span data-stu-id="25dc5-120">Remarks</span></span>

<span data-ttu-id="25dc5-121">Le stringhe di formato possono essere utilizzate durante la creazione di visualizzazioni di tabella, visualizzazioni di elenchi, visualizzazioni estese o visualizzazioni personalizzate.</span><span class="sxs-lookup"><span data-stu-id="25dc5-121">Format strings can be used when creating table views, list views, wide views, or custom views.</span></span> <span data-ttu-id="25dc5-122">Per ulteriori informazioni sulla formattazione di un valore visualizzato in una visualizzazione, vedere [formattazione dei dati visualizzati](./formatting-displayed-data.md).</span><span class="sxs-lookup"><span data-stu-id="25dc5-122">For more information about formatting a value displayed in a view, see [Formatting Displayed Data](./formatting-displayed-data.md).</span></span>

<span data-ttu-id="25dc5-123">Per ulteriori informazioni sull'utilizzo di stringhe di formato nelle visualizzazioni elenco, vedere Creazione di una [visualizzazione elenco](./creating-a-list-view.md).</span><span class="sxs-lookup"><span data-stu-id="25dc5-123">For more information about using format strings in list views, see [Creating List View](./creating-a-list-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="25dc5-124">Esempio</span><span class="sxs-lookup"><span data-stu-id="25dc5-124">Example</span></span>

<span data-ttu-id="25dc5-125">Nell'esempio seguente viene illustrato come definire una stringa di formattazione per il valore della proprietà `StartTime`.</span><span class="sxs-lookup"><span data-stu-id="25dc5-125">The following example shows how to define a formatting string for the value of the `StartTime` property.</span></span>

```xml
<ListItem>
  <PropertyName>StartTime</PropertyName>
  <FormatString>{0:MMM} (0:DD) (0:HH):(0:MM)</FormatString>
</ListItem>
```

## <a name="see-also"></a><span data-ttu-id="25dc5-126">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="25dc5-126">See Also</span></span>

[<span data-ttu-id="25dc5-127">Creazione di una visualizzazione elenco</span><span class="sxs-lookup"><span data-stu-id="25dc5-127">Creating a List View</span></span>](./creating-a-list-view.md)

[<span data-ttu-id="25dc5-128">Elemento ListItem (Format)</span><span class="sxs-lookup"><span data-stu-id="25dc5-128">ListItem Element (Format)</span></span>](./listitem-element-for-listitems-for-listcontrol-format.md)

[<span data-ttu-id="25dc5-129">Scrittura di un file di formattazione e di tipi di Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="25dc5-129">Writing a Windows PowerShell Formatting and Types File</span></span>](./writing-a-powershell-formatting-file.md)
