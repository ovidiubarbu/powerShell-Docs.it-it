---
title: Elemento FormatString per ListItem per ListControl (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: fd2cac66-88bb-449f-9d47-bd2cd4fe1801
caps.latest.revision: 13
ms.openlocfilehash: e6024ec4f7fc490c92408047c8c15c775e45bf9d
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62065621"
---
# <a name="formatstring-element-for-listitem-for-listcontrol--format"></a><span data-ttu-id="4f444-102">Elemento FormatString per ListItem per ListControl (formato)</span><span class="sxs-lookup"><span data-stu-id="4f444-102">FormatString Element for ListItem for ListControl  (Format)</span></span>

<span data-ttu-id="4f444-103">Specifica un modello di formato che definisce come viene visualizzato il valore della proprietà o dello script.</span><span class="sxs-lookup"><span data-stu-id="4f444-103">Specifies a format pattern that defines how the property or script value is displayed.</span></span>

<span data-ttu-id="4f444-104">Configurazione (formato) elemento ViewDefinitions (formato) visualizzazione elemento (formato) elemento dell'oggetto ListControl (formato) ListEntries elemento dell'elemento dell'oggetto ListControl (formato) ListEntry elemento per elemento ListItems dell'oggetto ListControl (formato) dell'oggetto ListControl (formato) Elemento ListItem per elemento FormatString dell'oggetto ListControl (formato) per ListItem per ListControl (formato)</span><span class="sxs-lookup"><span data-stu-id="4f444-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) ListControl Element (Format) ListEntries Element for ListControl (Format) ListEntry Element for ListControl (Format) ListItems Element for ListControl (Format) ListItem Element for ListControl (Format) FormatString Element for ListItem for ListControl (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="4f444-105">Sintassi</span><span class="sxs-lookup"><span data-stu-id="4f444-105">Syntax</span></span>

```xml
<FormatString>PropertyPattern</FormatString>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="4f444-106">Elementi e attributi</span><span class="sxs-lookup"><span data-stu-id="4f444-106">Attributes and Elements</span></span>

<span data-ttu-id="4f444-107">Le sezioni seguenti descrivono gli attributi e gli elementi figlio dell'elemento padre del `FormatString` elemento.</span><span class="sxs-lookup"><span data-stu-id="4f444-107">The following sections describe the attributes, child elements, and the parent element of the `FormatString` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="4f444-108">Attributes</span><span class="sxs-lookup"><span data-stu-id="4f444-108">Attributes</span></span>

<span data-ttu-id="4f444-109">Nessuna.</span><span class="sxs-lookup"><span data-stu-id="4f444-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="4f444-110">Elementi figlio</span><span class="sxs-lookup"><span data-stu-id="4f444-110">Child Elements</span></span>

<span data-ttu-id="4f444-111">Nessuna.</span><span class="sxs-lookup"><span data-stu-id="4f444-111">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="4f444-112">Elementi padre</span><span class="sxs-lookup"><span data-stu-id="4f444-112">Parent Elements</span></span>

|<span data-ttu-id="4f444-113">Elemento</span><span class="sxs-lookup"><span data-stu-id="4f444-113">Element</span></span>|<span data-ttu-id="4f444-114">Description</span><span class="sxs-lookup"><span data-stu-id="4f444-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="4f444-115">Elemento ListItem (formato)</span><span class="sxs-lookup"><span data-stu-id="4f444-115">ListItem Element (Format)</span></span>](./listitem-element-for-listitems-for-listcontrol-format.md)|<span data-ttu-id="4f444-116">Definisce proprietà o script il cui valore viene visualizzato in una riga della visualizzazione elenco.</span><span class="sxs-lookup"><span data-stu-id="4f444-116">Defines the property or script whose value is displayed in a row of the list view.</span></span>|

## <a name="text-value"></a><span data-ttu-id="4f444-117">Valore di testo</span><span class="sxs-lookup"><span data-stu-id="4f444-117">Text Value</span></span>

<span data-ttu-id="4f444-118">Specificare il modello utilizzato per formattare i dati.</span><span class="sxs-lookup"><span data-stu-id="4f444-118">Specify the pattern that is used to format the data.</span></span> <span data-ttu-id="4f444-119">Ad esempio, è possibile usare questo modello per formattare il valore di qualsiasi proprietà che è di tipo [System. TimeSpan](/dotnet/api/System.TimeSpan): {0: MMM} {0:dd} {{0:hh}: {0:mm}.</span><span class="sxs-lookup"><span data-stu-id="4f444-119">For example, you can use this pattern to format the value of any property that is of type [System.Timespan](/dotnet/api/System.TimeSpan): {0:MMM}{0:dd}{0:HH}:{0:mm}.</span></span>

## <a name="remarks"></a><span data-ttu-id="4f444-120">Osservazioni</span><span class="sxs-lookup"><span data-stu-id="4f444-120">Remarks</span></span>

<span data-ttu-id="4f444-121">Stringhe di formato possono essere usate durante la creazione di viste delle tabelle, elencare le visualizzazioni, visualizzazioni ampie o visualizzazioni personalizzate.</span><span class="sxs-lookup"><span data-stu-id="4f444-121">Format strings can be used when creating table views, list views, wide views, or custom views.</span></span> <span data-ttu-id="4f444-122">Per altre informazioni sulla formattazione di un valore visualizzato in una vista, vedere [formattazione dei dati visualizzati](./formatting-displayed-data.md).</span><span class="sxs-lookup"><span data-stu-id="4f444-122">For more information about formatting a value displayed in a view, see [Formatting Displayed Data](./formatting-displayed-data.md).</span></span>

<span data-ttu-id="4f444-123">Per altre informazioni sull'uso di stringhe di formato nelle visualizzazioni elenco, vedere [creazione di visualizzazione elenco](./creating-a-list-view.md).</span><span class="sxs-lookup"><span data-stu-id="4f444-123">For more information about using format strings in list views, see [Creating List View](./creating-a-list-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="4f444-124">Esempio</span><span class="sxs-lookup"><span data-stu-id="4f444-124">Example</span></span>

<span data-ttu-id="4f444-125">Nell'esempio seguente viene illustrato come definire una stringa di formattazione per il valore della `StartTime` proprietà.</span><span class="sxs-lookup"><span data-stu-id="4f444-125">The following example shows how to define a formatting string for the value of the `StartTime` property.</span></span>

```xml
<ListItem>
  <PropertyName>StartTime</PropertyName>
  <FormatString>{0:MMM} (0:DD) (0:HH):(0:MM)</FormatString>
</ListItem>
```

## <a name="see-also"></a><span data-ttu-id="4f444-126">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="4f444-126">See Also</span></span>

[<span data-ttu-id="4f444-127">Creazione di una visualizzazione elenco</span><span class="sxs-lookup"><span data-stu-id="4f444-127">Creating a List View</span></span>](./creating-a-list-view.md)

[<span data-ttu-id="4f444-128">Elemento ListItem (formato)</span><span class="sxs-lookup"><span data-stu-id="4f444-128">ListItem Element (Format)</span></span>](./listitem-element-for-listitems-for-listcontrol-format.md)

[<span data-ttu-id="4f444-129">La scrittura di un metodo di formattazione di Windows PowerShell e i tipi di File</span><span class="sxs-lookup"><span data-stu-id="4f444-129">Writing a Windows PowerShell Formatting and Types File</span></span>](./writing-a-powershell-formatting-file.md)
