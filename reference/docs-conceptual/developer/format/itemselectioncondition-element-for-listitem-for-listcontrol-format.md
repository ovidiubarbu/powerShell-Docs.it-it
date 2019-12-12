---
title: Elemento ItemSelectionCondition per ListItem per ListControl (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d2668aea-37e9-4753-a4e9-7980ae5ec2eb
caps.latest.revision: 10
ms.openlocfilehash: 6bc0ccbcc5bd62429f63ed220da66dc66f44f7ca
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/05/2019
ms.locfileid: "72365190"
---
# <a name="itemselectioncondition-element-for-listitem-for-listcontrol-format"></a><span data-ttu-id="a025b-102">Elemento ItemSelectionCondition per ListItem per ListControl (formato)</span><span class="sxs-lookup"><span data-stu-id="a025b-102">ItemSelectionCondition Element for ListItem for ListControl (Format)</span></span>

<span data-ttu-id="a025b-103">Definisce la condizione che deve esistere per l'uso di questo elemento elenco.</span><span class="sxs-lookup"><span data-stu-id="a025b-103">Defines the condition that must exist for this list item to be used.</span></span>

<span data-ttu-id="a025b-104">Elemento Configuration (Format) elemento ViewDefinitions (Format) elemento View (Format) elemento ListControl (Format) elemento ListEntries per l'elemento ListControl (Format) ListEntry per ListEntries per l'elemento ListItem (Format) ListItems per ListEntry per l'elemento ListItem (Format) ListItem per ListItems per l'elemento ListControl (Format) ItemSelectionCondition per ListItem per ListControl (Format)</span><span class="sxs-lookup"><span data-stu-id="a025b-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) ListControl Element (Format) ListEntries Element for ListControl (Format) ListEntry Element for ListEntries for ListControl (Format) ListItems Element for ListEntry for ListControl (Format) ListItem Element for ListItems for ListControl (Format) ItemSelectionCondition Element for ListItem for ListControl (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="a025b-105">Sintassi</span><span class="sxs-lookup"><span data-stu-id="a025b-105">Syntax</span></span>

```xml
<ItemSelectionCondition>
  <PropertyName>.NetTypeProperty</PropertyName>
  <ScriptBlock>ScriptToEvaluate</ScriptBlock>
</ItemSelectionCondition>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="a025b-106">Attributi ed elementi</span><span class="sxs-lookup"><span data-stu-id="a025b-106">Attributes and Elements</span></span>

<span data-ttu-id="a025b-107">Nelle sezioni seguenti vengono descritti gli attributi, gli elementi figlio e l'elemento padre dell'elemento `ItemSelectionCondition`.</span><span class="sxs-lookup"><span data-stu-id="a025b-107">The following sections describe attributes, child elements, and the parent element of the `ItemSelectionCondition` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="a025b-108">Attributi</span><span class="sxs-lookup"><span data-stu-id="a025b-108">Attributes</span></span>

<span data-ttu-id="a025b-109">Nessuna.</span><span class="sxs-lookup"><span data-stu-id="a025b-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="a025b-110">Elementi figlio</span><span class="sxs-lookup"><span data-stu-id="a025b-110">Child Elements</span></span>

|<span data-ttu-id="a025b-111">Elemento</span><span class="sxs-lookup"><span data-stu-id="a025b-111">Element</span></span>|<span data-ttu-id="a025b-112">Description</span><span class="sxs-lookup"><span data-stu-id="a025b-112">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="a025b-113">Elemento PropertyName per ItemSelectionCondition per ListControl (Format)</span><span class="sxs-lookup"><span data-stu-id="a025b-113">PropertyName Element for ItemSelectionCondition for ListControl (Format)</span></span>](./propertyname-element-for-itemselectioncondition-for-listcontrol-format.md)|<span data-ttu-id="a025b-114">Elemento facoltativo.</span><span class="sxs-lookup"><span data-stu-id="a025b-114">Optional element.</span></span><br /><br /> <span data-ttu-id="a025b-115">Specifica la proprietà .NET che attiva la condizione.</span><span class="sxs-lookup"><span data-stu-id="a025b-115">Specifies the .NET property that triggers the condition.</span></span>|
|[<span data-ttu-id="a025b-116">Elemento ScriptBlock per ItemSelectionCondition per ListControl (Format)</span><span class="sxs-lookup"><span data-stu-id="a025b-116">ScriptBlock Element for ItemSelectionCondition for ListControl (Format)</span></span>](./scriptblock-element-for-itemselectioncondition-for-listcontrol-format.md)|<span data-ttu-id="a025b-117">Elemento facoltativo.</span><span class="sxs-lookup"><span data-stu-id="a025b-117">Optional element.</span></span><br /><br /> <span data-ttu-id="a025b-118">Specifica lo script che attiva la condizione.</span><span class="sxs-lookup"><span data-stu-id="a025b-118">Specifies the script that triggers the condition.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="a025b-119">Elementi padre</span><span class="sxs-lookup"><span data-stu-id="a025b-119">Parent Elements</span></span>

|<span data-ttu-id="a025b-120">Elemento</span><span class="sxs-lookup"><span data-stu-id="a025b-120">Element</span></span>|<span data-ttu-id="a025b-121">Description</span><span class="sxs-lookup"><span data-stu-id="a025b-121">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="a025b-122">Elemento ListItem per ListItems per ListControl (Format)</span><span class="sxs-lookup"><span data-stu-id="a025b-122">ListItem Element for ListItems for ListControl (Format)</span></span>](./listitem-element-for-listitems-for-listcontrol-format.md)|<span data-ttu-id="a025b-123">Definisce la proprietà o lo script il cui valore viene visualizzato in una riga della visualizzazione elenco.</span><span class="sxs-lookup"><span data-stu-id="a025b-123">Defines the property or script whose value is displayed in a row of the list view.</span></span>|

## <a name="remarks"></a><span data-ttu-id="a025b-124">Osservazioni</span><span class="sxs-lookup"><span data-stu-id="a025b-124">Remarks</span></span>

<span data-ttu-id="a025b-125">È possibile specificare un nome di proprietà o uno script per questa condizione, ma non è possibile specificarli entrambi.</span><span class="sxs-lookup"><span data-stu-id="a025b-125">You can specify one property name or a script for this condition but cannot specify both.</span></span>

## <a name="see-also"></a><span data-ttu-id="a025b-126">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="a025b-126">See Also</span></span>

[<span data-ttu-id="a025b-127">Elemento ListItem per ListItems per ListControl (Format)</span><span class="sxs-lookup"><span data-stu-id="a025b-127">ListItem Element for ListItems for ListControl (Format)</span></span>](./listitem-element-for-listitems-for-listcontrol-format.md)

[<span data-ttu-id="a025b-128">Elemento PropertyName per ItemSelectionCondition per ListControl (Format)</span><span class="sxs-lookup"><span data-stu-id="a025b-128">PropertyName Element for ItemSelectionCondition for ListControl (Format)</span></span>](./propertyname-element-for-itemselectioncondition-for-listcontrol-format.md)

[<span data-ttu-id="a025b-129">Elemento ScriptBlock per ItemSelectionCondition per ListControl (Format)</span><span class="sxs-lookup"><span data-stu-id="a025b-129">ScriptBlock Element for ItemSelectionCondition for ListControl (Format)</span></span>](./scriptblock-element-for-itemselectioncondition-for-listcontrol-format.md)

[<span data-ttu-id="a025b-130">Scrittura di un file di formattazione di PowerShell</span><span class="sxs-lookup"><span data-stu-id="a025b-130">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
