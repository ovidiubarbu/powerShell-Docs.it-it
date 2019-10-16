---
title: Elemento PropertyName per ListItem per ListControl (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 01ae8cbe-acdc-4043-bd6e-1118a5691a55
caps.latest.revision: 12
ms.openlocfilehash: 405184f7bdbf1955f1df7766bf2723c244dcc27f
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/15/2019
ms.locfileid: "72362380"
---
# <a name="propertyname-element-for-listitem-for-listcontrol-format"></a><span data-ttu-id="21077-102">Elemento PropertyName per ListItem per ListControl (formato)</span><span class="sxs-lookup"><span data-stu-id="21077-102">PropertyName Element for ListItem for ListControl (Format)</span></span>

<span data-ttu-id="21077-103">Specifica la proprietà .NET il cui valore viene visualizzato nell'elenco.</span><span class="sxs-lookup"><span data-stu-id="21077-103">Specifies the .NET property whose value is displayed in the list.</span></span>

<span data-ttu-id="21077-104">Elemento Configuration (Format) elemento ViewDefinitions (Format) elemento View (Format) elemento ListControl (Format) elemento ListEntries (Format) elemento ListEntry (Format) elemento ListItem (Format) elemento ListItem (Format) PropertyName elemento per ListItem (formato)</span><span class="sxs-lookup"><span data-stu-id="21077-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) ListControl Element (Format) ListEntries Element (Format) ListEntry Element (Format) ListItems Element (Format) ListItem Element (Format) PropertyName Element for ListItem (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="21077-105">Sintassi</span><span class="sxs-lookup"><span data-stu-id="21077-105">Syntax</span></span>

```xml
<PropertyName>.NetTypeProperty</PropertyName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="21077-106">Attributi ed elementi</span><span class="sxs-lookup"><span data-stu-id="21077-106">Attributes and Elements</span></span>

<span data-ttu-id="21077-107">Nelle sezioni seguenti vengono descritti gli attributi, gli elementi figlio e l'elemento padre dell'elemento `PropertyName`.</span><span class="sxs-lookup"><span data-stu-id="21077-107">The following sections describe the attributes, child elements, and the parent element of the `PropertyName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="21077-108">Attributi</span><span class="sxs-lookup"><span data-stu-id="21077-108">Attributes</span></span>

<span data-ttu-id="21077-109">Nessuna.</span><span class="sxs-lookup"><span data-stu-id="21077-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="21077-110">Elementi figlio</span><span class="sxs-lookup"><span data-stu-id="21077-110">Child Elements</span></span>

<span data-ttu-id="21077-111">Nessuna.</span><span class="sxs-lookup"><span data-stu-id="21077-111">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="21077-112">Elementi padre</span><span class="sxs-lookup"><span data-stu-id="21077-112">Parent Elements</span></span>

|<span data-ttu-id="21077-113">Elemento</span><span class="sxs-lookup"><span data-stu-id="21077-113">Element</span></span>|<span data-ttu-id="21077-114">Description</span><span class="sxs-lookup"><span data-stu-id="21077-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="21077-115">Elemento ListItem (Format)</span><span class="sxs-lookup"><span data-stu-id="21077-115">ListItem Element (Format)</span></span>](./listitem-element-for-listitems-for-listcontrol-format.md)|<span data-ttu-id="21077-116">Definisce la proprietà o lo script il cui valore viene visualizzato nella riga della visualizzazione elenco.</span><span class="sxs-lookup"><span data-stu-id="21077-116">Defines the property or script whose value is displayed in the row of the list view.</span></span>|

## <a name="text-value"></a><span data-ttu-id="21077-117">Valore di testo</span><span class="sxs-lookup"><span data-stu-id="21077-117">Text Value</span></span>

<span data-ttu-id="21077-118">Consente di specificare il nome della proprietà di cui viene visualizzato il valore.</span><span class="sxs-lookup"><span data-stu-id="21077-118">Specify the name of the property whose value is displayed.</span></span>

## <a name="remarks"></a><span data-ttu-id="21077-119">Osservazioni</span><span class="sxs-lookup"><span data-stu-id="21077-119">Remarks</span></span>

<span data-ttu-id="21077-120">Quando questo elemento viene specificato, non è possibile specificare l'elemento [scriptblock](./scriptblock-element-for-listitem-for-listcontrol-format.md) .</span><span class="sxs-lookup"><span data-stu-id="21077-120">When this element is specified, you cannot specify the [ScriptBlock](./scriptblock-element-for-listitem-for-listcontrol-format.md) element.</span></span>

<span data-ttu-id="21077-121">Oltre a visualizzare il valore della proprietà, è anche possibile specificare un'etichetta per il valore o una stringa di formato che può essere utilizzata per modificare la visualizzazione del valore.</span><span class="sxs-lookup"><span data-stu-id="21077-121">In addition to displaying the property value, you can also specify a label for the value or a format string that can be used to change the display of the value.</span></span> <span data-ttu-id="21077-122">Per ulteriori informazioni su come specificare i dati in una visualizzazione elenco, vedere [creazione di una visualizzazione elenco](./creating-a-list-view.md).</span><span class="sxs-lookup"><span data-stu-id="21077-122">For more information about specifying data in a list view, see [Creating a List View](./creating-a-list-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="21077-123">Esempio</span><span class="sxs-lookup"><span data-stu-id="21077-123">Example</span></span>

<span data-ttu-id="21077-124">Nell'esempio seguente viene illustrato come specificare l'etichetta e la proprietà di cui viene visualizzato il valore.</span><span class="sxs-lookup"><span data-stu-id="21077-124">The following example shows how to specify the label and property whose value is displayed.</span></span>

```xml
ListItem>
  <Label>NameOfProperty</Label>
  <PropertyName>.NetTypeProperty</PropertyName>
</ListItem>

```

## <a name="see-also"></a><span data-ttu-id="21077-125">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="21077-125">See Also</span></span>

[<span data-ttu-id="21077-126">Elemento ScriptBlock per ListItem per ListControl (Format)</span><span class="sxs-lookup"><span data-stu-id="21077-126">ScriptBlock Element for ListItem for ListControl (Format)</span></span>](./scriptblock-element-for-listitem-for-listcontrol-format.md)

[<span data-ttu-id="21077-127">Creazione di una visualizzazione elenco</span><span class="sxs-lookup"><span data-stu-id="21077-127">Creating a List View</span></span>](./creating-a-list-view.md)

[<span data-ttu-id="21077-128">Elemento ListItem per ListControl (Format)</span><span class="sxs-lookup"><span data-stu-id="21077-128">ListItem Element for ListControl(Format)</span></span>](./listitem-element-for-listitems-for-listcontrol-format.md)

[<span data-ttu-id="21077-129">Scrittura di un file di formattazione di PowerShell</span><span class="sxs-lookup"><span data-stu-id="21077-129">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
