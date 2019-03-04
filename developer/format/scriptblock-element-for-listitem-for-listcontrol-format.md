---
title: Elemento ScriptBlock per ListItem per ListControl (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 74e30938-00ef-46fd-84e5-f0a83706a50e
caps.latest.revision: 11
ms.openlocfilehash: 76b600256af3f957f7fe0578f9fef810262aa5d5
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/03/2019
ms.locfileid: "56855557"
---
# <a name="scriptblock-element-for-listitem-for-listcontrol-format"></a><span data-ttu-id="71653-102">Elemento ScriptBlock per ListItem per ListControl (formato)</span><span class="sxs-lookup"><span data-stu-id="71653-102">ScriptBlock Element for ListItem for ListControl (Format)</span></span>

<span data-ttu-id="71653-103">Specifica lo script il cui valore viene visualizzato nella riga.</span><span class="sxs-lookup"><span data-stu-id="71653-103">Specifies the script whose value is displayed in the row.</span></span>

<span data-ttu-id="71653-104">Elemento (formato) elemento ViewDefinitions (formato) visualizzazione elemento (formato) elemento dell'oggetto ListControl (formato) ListEntries elemento di configurazione per elemento dell'oggetto ListControl (formato) ListEntry ListEntries per elemento ListItems dell'oggetto ListControl (formato) per ListEntry elemento ListItem ListControl (formato) per ListItems per elemento dell'oggetto ListControl (formato) ScriptBlock ListItem per ListControl (formato)</span><span class="sxs-lookup"><span data-stu-id="71653-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) ListControl Element (Format) ListEntries Element for ListControl (Format) ListEntry Element for ListEntries for ListControl (Format) ListItems Element for ListEntry for ListControl (Format) ListItem Element for ListItems for ListControl (Format) ScriptBlock Element for ListItem for ListControl (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="71653-105">Sintassi</span><span class="sxs-lookup"><span data-stu-id="71653-105">Syntax</span></span>

```xml
<ScriptBlock>ScriptToEvaluate</ScriptBlock>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="71653-106">Attributi ed elementi</span><span class="sxs-lookup"><span data-stu-id="71653-106">Attributes and Elements</span></span>

<span data-ttu-id="71653-107">Le sezioni seguenti descrivono gli attributi e gli elementi figlio dell'elemento padre del `ScriptBlock` elemento.</span><span class="sxs-lookup"><span data-stu-id="71653-107">The following sections describe the attributes, child elements, and the parent element of the `ScriptBlock` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="71653-108">Attributes</span><span class="sxs-lookup"><span data-stu-id="71653-108">Attributes</span></span>

<span data-ttu-id="71653-109">Nessuna.</span><span class="sxs-lookup"><span data-stu-id="71653-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="71653-110">Elementi figlio</span><span class="sxs-lookup"><span data-stu-id="71653-110">Child Elements</span></span>

<span data-ttu-id="71653-111">Nessuna.</span><span class="sxs-lookup"><span data-stu-id="71653-111">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="71653-112">Elementi padre</span><span class="sxs-lookup"><span data-stu-id="71653-112">Parent Elements</span></span>

|<span data-ttu-id="71653-113">Elemento</span><span class="sxs-lookup"><span data-stu-id="71653-113">Element</span></span>|<span data-ttu-id="71653-114">Description</span><span class="sxs-lookup"><span data-stu-id="71653-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="71653-115">Elemento ListItem (formato)</span><span class="sxs-lookup"><span data-stu-id="71653-115">ListItem Element (Format)</span></span>](./listitem-element-for-listitems-for-listcontrol-format.md)|<span data-ttu-id="71653-116">Definisce proprietà o script il cui valore viene visualizzato in una riga della visualizzazione elenco.</span><span class="sxs-lookup"><span data-stu-id="71653-116">Defines the property or script whose value is displayed in a row of the list view.</span></span>|

## <a name="text-value"></a><span data-ttu-id="71653-117">Valore di testo</span><span class="sxs-lookup"><span data-stu-id="71653-117">Text Value</span></span>

<span data-ttu-id="71653-118">Specificare lo script il cui valore viene visualizzato nella riga.</span><span class="sxs-lookup"><span data-stu-id="71653-118">Specify the script whose value is displayed in the row.</span></span>

## <a name="remarks"></a><span data-ttu-id="71653-119">Osservazioni</span><span class="sxs-lookup"><span data-stu-id="71653-119">Remarks</span></span>

<span data-ttu-id="71653-120">Quando questo elemento viene specificato, non è possibile specificare il [PropertyName](./propertyname-element-for-listitem-for-listcontrol-format.md) elemento.</span><span class="sxs-lookup"><span data-stu-id="71653-120">When this element is specified, you cannot specify the [PropertyName](./propertyname-element-for-listitem-for-listcontrol-format.md) element.</span></span>

<span data-ttu-id="71653-121">Per altre informazioni su come specificare gli script in una visualizzazione elenco, vedere [visualizzazione elenco](./creating-a-list-view.md).</span><span class="sxs-lookup"><span data-stu-id="71653-121">For more information about specifying scripts in a list view, see [List View](./creating-a-list-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="71653-122">Esempio</span><span class="sxs-lookup"><span data-stu-id="71653-122">Example</span></span>

<span data-ttu-id="71653-123">Nell'esempio seguente viene illustrato come specificare la proprietà il cui valore viene visualizzato.</span><span class="sxs-lookup"><span data-stu-id="71653-123">The following example shows how to specify the property whose value is displayed.</span></span>

```xml
<ListItem>
  <ScriptBlock>$_.ProcessName + ":" $_.Id</ScriptBlock>
</ListItem>

```

## <a name="see-also"></a><span data-ttu-id="71653-124">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="71653-124">See Also</span></span>

[<span data-ttu-id="71653-125">Elemento PropertyName per ListItem per ListControl (formato)</span><span class="sxs-lookup"><span data-stu-id="71653-125">PropertyName Element for ListItem for ListControl (Format)</span></span>](./propertyname-element-for-listitem-for-listcontrol-format.md)

[<span data-ttu-id="71653-126">Creazione di una visualizzazione elenco</span><span class="sxs-lookup"><span data-stu-id="71653-126">Creating a List View</span></span>](./creating-a-list-view.md)

[<span data-ttu-id="71653-127">Elemento ListItem per ListItems per ListControl (formato)</span><span class="sxs-lookup"><span data-stu-id="71653-127">ListItem Element for ListItems for ListControl (Format)</span></span>](./listitem-element-for-listitems-for-listcontrol-format.md)

[<span data-ttu-id="71653-128">La scrittura di un File di formattazione di PowerShell</span><span class="sxs-lookup"><span data-stu-id="71653-128">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
