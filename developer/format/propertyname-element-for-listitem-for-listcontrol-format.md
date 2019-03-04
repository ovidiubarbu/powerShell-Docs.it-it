---
title: Elemento PropertyName per ListItem per ListControl (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 01ae8cbe-acdc-4043-bd6e-1118a5691a55
caps.latest.revision: 12
ms.openlocfilehash: 405184f7bdbf1955f1df7766bf2723c244dcc27f
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/03/2019
ms.locfileid: "56855737"
---
# <a name="propertyname-element-for-listitem-for-listcontrol-format"></a><span data-ttu-id="afaf8-102">Elemento PropertyName per ListItem per ListControl (formato)</span><span class="sxs-lookup"><span data-stu-id="afaf8-102">PropertyName Element for ListItem for ListControl (Format)</span></span>

<span data-ttu-id="afaf8-103">Specifica la proprietà .NET il cui valore viene visualizzato nell'elenco.</span><span class="sxs-lookup"><span data-stu-id="afaf8-103">Specifies the .NET property whose value is displayed in the list.</span></span>

<span data-ttu-id="afaf8-104">Elemento (formato) elemento ViewDefinitions (formato) visualizzazione elemento (formato) dell'oggetto ListControl elemento (formato) elemento ListEntries (formato) elemento ListEntry (formato) elemento ListItems (formato) elemento ListItem (formato) PropertyName elemento di configurazione per ListItem (formato)</span><span class="sxs-lookup"><span data-stu-id="afaf8-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) ListControl Element (Format) ListEntries Element (Format) ListEntry Element (Format) ListItems Element (Format) ListItem Element (Format) PropertyName Element for ListItem (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="afaf8-105">Sintassi</span><span class="sxs-lookup"><span data-stu-id="afaf8-105">Syntax</span></span>

```xml
<PropertyName>.NetTypeProperty</PropertyName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="afaf8-106">Attributi ed elementi</span><span class="sxs-lookup"><span data-stu-id="afaf8-106">Attributes and Elements</span></span>

<span data-ttu-id="afaf8-107">Le sezioni seguenti descrivono gli attributi e gli elementi figlio dell'elemento padre del `PropertyName` elemento.</span><span class="sxs-lookup"><span data-stu-id="afaf8-107">The following sections describe the attributes, child elements, and the parent element of the `PropertyName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="afaf8-108">Attributes</span><span class="sxs-lookup"><span data-stu-id="afaf8-108">Attributes</span></span>

<span data-ttu-id="afaf8-109">Nessuna.</span><span class="sxs-lookup"><span data-stu-id="afaf8-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="afaf8-110">Elementi figlio</span><span class="sxs-lookup"><span data-stu-id="afaf8-110">Child Elements</span></span>

<span data-ttu-id="afaf8-111">Nessuna.</span><span class="sxs-lookup"><span data-stu-id="afaf8-111">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="afaf8-112">Elementi padre</span><span class="sxs-lookup"><span data-stu-id="afaf8-112">Parent Elements</span></span>

|<span data-ttu-id="afaf8-113">Elemento</span><span class="sxs-lookup"><span data-stu-id="afaf8-113">Element</span></span>|<span data-ttu-id="afaf8-114">Description</span><span class="sxs-lookup"><span data-stu-id="afaf8-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="afaf8-115">Elemento ListItem (formato)</span><span class="sxs-lookup"><span data-stu-id="afaf8-115">ListItem Element (Format)</span></span>](./listitem-element-for-listitems-for-listcontrol-format.md)|<span data-ttu-id="afaf8-116">Definisce le proprietà dello script il cui valore viene visualizzato nella riga della visualizzazione elenco.</span><span class="sxs-lookup"><span data-stu-id="afaf8-116">Defines the property or script whose value is displayed in the row of the list view.</span></span>|

## <a name="text-value"></a><span data-ttu-id="afaf8-117">Valore di testo</span><span class="sxs-lookup"><span data-stu-id="afaf8-117">Text Value</span></span>

<span data-ttu-id="afaf8-118">Specificare il nome della proprietà il cui valore viene visualizzato.</span><span class="sxs-lookup"><span data-stu-id="afaf8-118">Specify the name of the property whose value is displayed.</span></span>

## <a name="remarks"></a><span data-ttu-id="afaf8-119">Osservazioni</span><span class="sxs-lookup"><span data-stu-id="afaf8-119">Remarks</span></span>

<span data-ttu-id="afaf8-120">Quando questo elemento viene specificato, non è possibile specificare il [ScriptBlock](./scriptblock-element-for-listitem-for-listcontrol-format.md) elemento.</span><span class="sxs-lookup"><span data-stu-id="afaf8-120">When this element is specified, you cannot specify the [ScriptBlock](./scriptblock-element-for-listitem-for-listcontrol-format.md) element.</span></span>

<span data-ttu-id="afaf8-121">Oltre a visualizzare il valore della proprietà, è anche possibile specificare un'etichetta per il valore o una stringa di formato che può essere utilizzata per modificare la visualizzazione del valore.</span><span class="sxs-lookup"><span data-stu-id="afaf8-121">In addition to displaying the property value, you can also specify a label for the value or a format string that can be used to change the display of the value.</span></span> <span data-ttu-id="afaf8-122">Per altre informazioni su come specificare i dati in una visualizzazione elenco, vedere [creazione di una visualizzazione elenco](./creating-a-list-view.md).</span><span class="sxs-lookup"><span data-stu-id="afaf8-122">For more information about specifying data in a list view, see [Creating a List View](./creating-a-list-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="afaf8-123">Esempio</span><span class="sxs-lookup"><span data-stu-id="afaf8-123">Example</span></span>

<span data-ttu-id="afaf8-124">Nell'esempio seguente viene illustrato come specificare l'etichetta e la proprietà il cui valore viene visualizzato.</span><span class="sxs-lookup"><span data-stu-id="afaf8-124">The following example shows how to specify the label and property whose value is displayed.</span></span>

```xml
ListItem>
  <Label>NameOfProperty</Label>
  <PropertyName>.NetTypeProperty</PropertyName>
</ListItem>

```

## <a name="see-also"></a><span data-ttu-id="afaf8-125">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="afaf8-125">See Also</span></span>

[<span data-ttu-id="afaf8-126">Elemento ScriptBlock per ListItem per ListControl (formato)</span><span class="sxs-lookup"><span data-stu-id="afaf8-126">ScriptBlock Element for ListItem for ListControl (Format)</span></span>](./scriptblock-element-for-listitem-for-listcontrol-format.md)

[<span data-ttu-id="afaf8-127">Creazione di una visualizzazione elenco</span><span class="sxs-lookup"><span data-stu-id="afaf8-127">Creating a List View</span></span>](./creating-a-list-view.md)

[<span data-ttu-id="afaf8-128">Elemento ListItem per ListControl(Format)</span><span class="sxs-lookup"><span data-stu-id="afaf8-128">ListItem Element for ListControl(Format)</span></span>](./listitem-element-for-listitems-for-listcontrol-format.md)

[<span data-ttu-id="afaf8-129">La scrittura di un File di formattazione di PowerShell</span><span class="sxs-lookup"><span data-stu-id="afaf8-129">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
