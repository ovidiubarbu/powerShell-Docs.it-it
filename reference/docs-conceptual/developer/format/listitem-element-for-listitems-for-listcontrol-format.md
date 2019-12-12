---
title: Elemento ListItem per ListItems per ListControl (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 0f96f4f5-8bd5-43ed-95e7-a7358115999a
caps.latest.revision: 11
ms.openlocfilehash: 1e0a1b2d20853650328b8cfd1513a08f7e167cd6
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/05/2019
ms.locfileid: "72365130"
---
# <a name="listitem-element-for-listitems-for-listcontrol-format"></a><span data-ttu-id="b055a-102">Elemento ListItem per ListItems per ListControl (formato)</span><span class="sxs-lookup"><span data-stu-id="b055a-102">ListItem Element for ListItems for ListControl (Format)</span></span>

<span data-ttu-id="b055a-103">Definisce la proprietà o lo script il cui valore viene visualizzato in una riga della visualizzazione elenco.</span><span class="sxs-lookup"><span data-stu-id="b055a-103">Defines the property or script whose value is displayed in a row of the list view.</span></span>

<span data-ttu-id="b055a-104">Elemento Configuration (Format) elemento ViewDefinitions (Format) elemento View (Format) elemento ListControl (Format) elemento ListEntries per ListControl (Format) elemento ListEntry per ListControl (Format) elemento ListItems per ListControl (Format) ListItem per l'elemento ListControl (Format)</span><span class="sxs-lookup"><span data-stu-id="b055a-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) ListControl Element (Format) ListEntries Element for ListControl (Format) ListEntry Element for ListControl (Format) ListItems Element for ListControl (Format) ListItem for ListControl Element (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="b055a-105">Sintassi</span><span class="sxs-lookup"><span data-stu-id="b055a-105">Syntax</span></span>

```xml
<ListItem>
  <PropertyName>PropertyToDisplay</PropertyName>
  <ScriptBlock>ScriptToExecute</ScriptBlock>
  <Label>LabelToDisplay</Label>
  <FormatString>FormatPattern</FormatString>
  <ItemSelectionCondition>...</ItemSelectionCondition>
</ListItem>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="b055a-106">Attributi ed elementi</span><span class="sxs-lookup"><span data-stu-id="b055a-106">Attributes and Elements</span></span>

<span data-ttu-id="b055a-107">Nelle sezioni seguenti vengono descritti gli attributi, gli elementi figlio e l'elemento padre dell'elemento `ListItem`.</span><span class="sxs-lookup"><span data-stu-id="b055a-107">The following sections describe the attributes, child elements, and parent element of the `ListItem` element.</span></span> <span data-ttu-id="b055a-108">È possibile specificare solo una proprietà o uno script.</span><span class="sxs-lookup"><span data-stu-id="b055a-108">Only one property or script can be specified.</span></span>

### <a name="attributes"></a><span data-ttu-id="b055a-109">Attributi</span><span class="sxs-lookup"><span data-stu-id="b055a-109">Attributes</span></span>

<span data-ttu-id="b055a-110">Nessuno</span><span class="sxs-lookup"><span data-stu-id="b055a-110">None</span></span>

### <a name="child-elements"></a><span data-ttu-id="b055a-111">Elementi figlio</span><span class="sxs-lookup"><span data-stu-id="b055a-111">Child Elements</span></span>

|<span data-ttu-id="b055a-112">Elemento</span><span class="sxs-lookup"><span data-stu-id="b055a-112">Element</span></span>|<span data-ttu-id="b055a-113">Description</span><span class="sxs-lookup"><span data-stu-id="b055a-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="b055a-114">Elemento FormatString per ListItem per ListControl (Format)</span><span class="sxs-lookup"><span data-stu-id="b055a-114">FormatString Element for ListItem for ListControl (Format)</span></span>](./formatstring-element-for-listitem-for-listcontrol-format.md)|<span data-ttu-id="b055a-115">Elemento facoltativo.</span><span class="sxs-lookup"><span data-stu-id="b055a-115">Optional element.</span></span><br /><br /> <span data-ttu-id="b055a-116">Specifica una stringa di formato che definisce come viene visualizzato il valore della proprietà o dello script.</span><span class="sxs-lookup"><span data-stu-id="b055a-116">Specifies a format string that defines how the property or script value is displayed.</span></span>|
|[<span data-ttu-id="b055a-117">Elemento ItemSelectionCondition per ListItem per ListControl (Format)</span><span class="sxs-lookup"><span data-stu-id="b055a-117">ItemSelectionCondition Element for ListItem for ListControl (Format)</span></span>](./itemselectioncondition-element-for-listitem-for-listcontrol-format.md)|<span data-ttu-id="b055a-118">Elemento facoltativo.</span><span class="sxs-lookup"><span data-stu-id="b055a-118">Optional element.</span></span><br /><br /> <span data-ttu-id="b055a-119">Definisce la condizione che deve esistere per l'uso di questo elemento elenco.</span><span class="sxs-lookup"><span data-stu-id="b055a-119">Defines the condition that must exist for this list item to be used.</span></span>|
|[<span data-ttu-id="b055a-120">Elemento label per ListItem per ListControl (Format)</span><span class="sxs-lookup"><span data-stu-id="b055a-120">Label Element for ListItem for ListControl (Format)</span></span>](./label-element-for-listitem-for-listcontrol-format.md)|<span data-ttu-id="b055a-121">Elemento facoltativo</span><span class="sxs-lookup"><span data-stu-id="b055a-121">Optional element</span></span><br /><br /> <span data-ttu-id="b055a-122">Specifica l'etichetta visualizzata a sinistra della proprietà o del valore dello script nella riga.</span><span class="sxs-lookup"><span data-stu-id="b055a-122">Specifies the label that is displayed to the left of the property or script value in the row.</span></span>|
|[<span data-ttu-id="b055a-123">Elemento PropertyName per ListItem per ListControl (Format)</span><span class="sxs-lookup"><span data-stu-id="b055a-123">PropertyName Element for ListItem for ListControl (Format)</span></span>](./propertyname-element-for-listitem-for-listcontrol-format.md)|<span data-ttu-id="b055a-124">Elemento facoltativo.</span><span class="sxs-lookup"><span data-stu-id="b055a-124">Optional element.</span></span><br /><br /> <span data-ttu-id="b055a-125">Specifica la proprietà .NET il cui valore viene visualizzato nella riga.</span><span class="sxs-lookup"><span data-stu-id="b055a-125">Specifies the .NET property whose value is displayed in the row.</span></span>|
|[<span data-ttu-id="b055a-126">Elemento ScriptBlock per ListItem per ListControl (Format)</span><span class="sxs-lookup"><span data-stu-id="b055a-126">ScriptBlock Element for ListItem for ListControl (Format)</span></span>](./scriptblock-element-for-listitem-for-listcontrol-format.md)|<span data-ttu-id="b055a-127">Elemento facoltativo.</span><span class="sxs-lookup"><span data-stu-id="b055a-127">Optional element.</span></span><br /><br /> <span data-ttu-id="b055a-128">Specifica lo script il cui valore viene visualizzato nella riga.</span><span class="sxs-lookup"><span data-stu-id="b055a-128">Specifies the script whose value is displayed in the row.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="b055a-129">Elementi padre</span><span class="sxs-lookup"><span data-stu-id="b055a-129">Parent Elements</span></span>

|<span data-ttu-id="b055a-130">Elemento</span><span class="sxs-lookup"><span data-stu-id="b055a-130">Element</span></span>|<span data-ttu-id="b055a-131">Description</span><span class="sxs-lookup"><span data-stu-id="b055a-131">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="b055a-132">Elemento ListItems per il controllo List (Format)</span><span class="sxs-lookup"><span data-stu-id="b055a-132">ListItems Element for List Control (Format)</span></span>](./listitems-element-for-listentry-for-listcontrol-format.md)|<span data-ttu-id="b055a-133">Definisce le proprietà e gli script i cui valori vengono visualizzati nella visualizzazione elenco.</span><span class="sxs-lookup"><span data-stu-id="b055a-133">Defines the properties and scripts whose values are displayed in the list view.</span></span>|

## <a name="remarks"></a><span data-ttu-id="b055a-134">Osservazioni</span><span class="sxs-lookup"><span data-stu-id="b055a-134">Remarks</span></span>

<span data-ttu-id="b055a-135">Per ulteriori informazioni sui componenti di una visualizzazione elenco, vedere [creazione di una visualizzazione elenco](./creating-a-list-view.md).</span><span class="sxs-lookup"><span data-stu-id="b055a-135">For more information about the components of a list view, see [Creating a List View](./creating-a-list-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="b055a-136">Esempio</span><span class="sxs-lookup"><span data-stu-id="b055a-136">Example</span></span>

<span data-ttu-id="b055a-137">In questo esempio vengono illustrati gli elementi XML che definiscono tre righe della visualizzazione elenco.</span><span class="sxs-lookup"><span data-stu-id="b055a-137">This example shows the XML elements that define three rows of the list view.</span></span> <span data-ttu-id="b055a-138">Nelle prime due righe viene visualizzato il valore di una proprietà .NET e nell'ultima riga viene visualizzato un valore generato da uno script.</span><span class="sxs-lookup"><span data-stu-id="b055a-138">The first two rows display the value of a .NET property, and the last row displays a value generated by a script.</span></span>

```xml
<ListEntry>
    <ListItems>
      <ListItem>
        <Label>Property1: </Label>
        <PropertyName>DotNetProperty1</PropertyName>
      </ListItem>
      <ListItem>
        <PropertyName>DotNetProperty2</PropertyName>
      </ListItem>
      <ListItem>
        <ScriptBlock>$_.ProcessName + ":" $_.Id</ScriptBlock>
      </ListItem>
    </ListItems>
</ListEntry>

```

## <a name="see-also"></a><span data-ttu-id="b055a-139">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="b055a-139">See Also</span></span>

[<span data-ttu-id="b055a-140">Elemento ListItems (Format)</span><span class="sxs-lookup"><span data-stu-id="b055a-140">ListItems Element (Format)</span></span>](./listitems-element-for-listentry-for-listcontrol-format.md)

[<span data-ttu-id="b055a-141">Elemento FormatString per ListItem (Format)</span><span class="sxs-lookup"><span data-stu-id="b055a-141">FormatString Element for ListItem (Format)</span></span>](./formatstring-element-for-listitem-for-listcontrol-format.md)

[<span data-ttu-id="b055a-142">Elemento label per ListItem (Format)</span><span class="sxs-lookup"><span data-stu-id="b055a-142">Label Element for ListItem (Format)</span></span>](./label-element-for-listitem-for-listcontrol-format.md)

[<span data-ttu-id="b055a-143">Elemento PropertyName per ListItem (Format)</span><span class="sxs-lookup"><span data-stu-id="b055a-143">PropertyName Element for ListItem (Format)</span></span>](./propertyname-element-for-listitem-for-listcontrol-format.md)

[<span data-ttu-id="b055a-144">Elemento ScriptBlock per ListItem (Format)</span><span class="sxs-lookup"><span data-stu-id="b055a-144">ScriptBlock Element for ListItem (Format)</span></span>](./scriptblock-element-for-listitem-for-listcontrol-format.md)

[<span data-ttu-id="b055a-145">Creazione di una visualizzazione elenco</span><span class="sxs-lookup"><span data-stu-id="b055a-145">Creating a List View</span></span>](./creating-a-list-view.md)

[<span data-ttu-id="b055a-146">Scrittura di un file di formattazione e di tipi di Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="b055a-146">Writing a Windows PowerShell Formatting and Types File</span></span>](./writing-a-powershell-formatting-file.md)
