---
title: Elemento ItemSelectionCondition per ListItem per ListControl (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d2668aea-37e9-4753-a4e9-7980ae5ec2eb
caps.latest.revision: 10
ms.openlocfilehash: 6bc0ccbcc5bd62429f63ed220da66dc66f44f7ca
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62065445"
---
# <a name="itemselectioncondition-element-for-listitem-for-listcontrol-format"></a><span data-ttu-id="83c57-102">Elemento ItemSelectionCondition per ListItem per ListControl (formato)</span><span class="sxs-lookup"><span data-stu-id="83c57-102">ItemSelectionCondition Element for ListItem for ListControl (Format)</span></span>

<span data-ttu-id="83c57-103">Definisce la condizione che deve essere presente per questo elemento di elenco da utilizzare.</span><span class="sxs-lookup"><span data-stu-id="83c57-103">Defines the condition that must exist for this list item to be used.</span></span>

<span data-ttu-id="83c57-104">Elemento (formato) elemento ViewDefinitions (formato) visualizzazione elemento (formato) elemento dell'oggetto ListControl (formato) ListEntries elemento di configurazione per elemento dell'oggetto ListControl (formato) ListEntry ListEntries per elemento ListItems dell'oggetto ListControl (formato) per ListEntry elemento ListItem ListControl (formato) per ListItems per elemento dell'oggetto ListControl (formato) ItemSelectionCondition ListItem per ListControl (formato)</span><span class="sxs-lookup"><span data-stu-id="83c57-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) ListControl Element (Format) ListEntries Element for ListControl (Format) ListEntry Element for ListEntries for ListControl (Format) ListItems Element for ListEntry for ListControl (Format) ListItem Element for ListItems for ListControl (Format) ItemSelectionCondition Element for ListItem for ListControl (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="83c57-105">Sintassi</span><span class="sxs-lookup"><span data-stu-id="83c57-105">Syntax</span></span>

```xml
<ItemSelectionCondition>
  <PropertyName>.NetTypeProperty</PropertyName>
  <ScriptBlock>ScriptToEvaluate</ScriptBlock>
</ItemSelectionCondition>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="83c57-106">Elementi e attributi</span><span class="sxs-lookup"><span data-stu-id="83c57-106">Attributes and Elements</span></span>

<span data-ttu-id="83c57-107">Le sezioni seguenti descrivono gli attributi e gli elementi figlio dell'elemento padre del `ItemSelectionCondition` elemento.</span><span class="sxs-lookup"><span data-stu-id="83c57-107">The following sections describe attributes, child elements, and the parent element of the `ItemSelectionCondition` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="83c57-108">Attributes</span><span class="sxs-lookup"><span data-stu-id="83c57-108">Attributes</span></span>

<span data-ttu-id="83c57-109">Nessuna.</span><span class="sxs-lookup"><span data-stu-id="83c57-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="83c57-110">Elementi figlio</span><span class="sxs-lookup"><span data-stu-id="83c57-110">Child Elements</span></span>

|<span data-ttu-id="83c57-111">Elemento</span><span class="sxs-lookup"><span data-stu-id="83c57-111">Element</span></span>|<span data-ttu-id="83c57-112">Description</span><span class="sxs-lookup"><span data-stu-id="83c57-112">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="83c57-113">Elemento PropertyName per ItemSelectionCondition per ListControl (formato)</span><span class="sxs-lookup"><span data-stu-id="83c57-113">PropertyName Element for ItemSelectionCondition for ListControl (Format)</span></span>](./propertyname-element-for-itemselectioncondition-for-listcontrol-format.md)|<span data-ttu-id="83c57-114">Elemento facoltativo.</span><span class="sxs-lookup"><span data-stu-id="83c57-114">Optional element.</span></span><br /><br /> <span data-ttu-id="83c57-115">Specifica la proprietà .NET che attiva la condizione.</span><span class="sxs-lookup"><span data-stu-id="83c57-115">Specifies the .NET property that triggers the condition.</span></span>|
|[<span data-ttu-id="83c57-116">Elemento ScriptBlock per ItemSelectionCondition per ListControl (formato)</span><span class="sxs-lookup"><span data-stu-id="83c57-116">ScriptBlock Element for ItemSelectionCondition for ListControl (Format)</span></span>](./scriptblock-element-for-itemselectioncondition-for-listcontrol-format.md)|<span data-ttu-id="83c57-117">Elemento facoltativo.</span><span class="sxs-lookup"><span data-stu-id="83c57-117">Optional element.</span></span><br /><br /> <span data-ttu-id="83c57-118">Specifica lo script che genera la condizione.</span><span class="sxs-lookup"><span data-stu-id="83c57-118">Specifies the script that triggers the condition.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="83c57-119">Elementi padre</span><span class="sxs-lookup"><span data-stu-id="83c57-119">Parent Elements</span></span>

|<span data-ttu-id="83c57-120">Elemento</span><span class="sxs-lookup"><span data-stu-id="83c57-120">Element</span></span>|<span data-ttu-id="83c57-121">Description</span><span class="sxs-lookup"><span data-stu-id="83c57-121">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="83c57-122">Elemento ListItem per ListItems per ListControl (formato)</span><span class="sxs-lookup"><span data-stu-id="83c57-122">ListItem Element for ListItems for ListControl (Format)</span></span>](./listitem-element-for-listitems-for-listcontrol-format.md)|<span data-ttu-id="83c57-123">Definisce proprietà o script il cui valore viene visualizzato in una riga della visualizzazione elenco.</span><span class="sxs-lookup"><span data-stu-id="83c57-123">Defines the property or script whose value is displayed in a row of the list view.</span></span>|

## <a name="remarks"></a><span data-ttu-id="83c57-124">Osservazioni</span><span class="sxs-lookup"><span data-stu-id="83c57-124">Remarks</span></span>

<span data-ttu-id="83c57-125">È possibile specificare un nome di proprietà o uno script per questa condizione, ma non è possibile specificare entrambi.</span><span class="sxs-lookup"><span data-stu-id="83c57-125">You can specify one property name or a script for this condition but cannot specify both.</span></span>

## <a name="see-also"></a><span data-ttu-id="83c57-126">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="83c57-126">See Also</span></span>

[<span data-ttu-id="83c57-127">Elemento ListItem per ListItems per ListControl (formato)</span><span class="sxs-lookup"><span data-stu-id="83c57-127">ListItem Element for ListItems for ListControl (Format)</span></span>](./listitem-element-for-listitems-for-listcontrol-format.md)

[<span data-ttu-id="83c57-128">Elemento PropertyName per ItemSelectionCondition per ListControl (formato)</span><span class="sxs-lookup"><span data-stu-id="83c57-128">PropertyName Element for ItemSelectionCondition for ListControl (Format)</span></span>](./propertyname-element-for-itemselectioncondition-for-listcontrol-format.md)

[<span data-ttu-id="83c57-129">Elemento ScriptBlock per ItemSelectionCondition per ListControl (formato)</span><span class="sxs-lookup"><span data-stu-id="83c57-129">ScriptBlock Element for ItemSelectionCondition for ListControl (Format)</span></span>](./scriptblock-element-for-itemselectioncondition-for-listcontrol-format.md)

[<span data-ttu-id="83c57-130">La scrittura di un File di formattazione di PowerShell</span><span class="sxs-lookup"><span data-stu-id="83c57-130">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
