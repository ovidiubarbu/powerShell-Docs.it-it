---
title: Elemento GroupBy per visualizzazione (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 67a2b061-2a4a-4ad1-84f9-cdbefb64aaab
caps.latest.revision: 8
ms.openlocfilehash: abb8b91626128b3deaa2db24a9fd8b34a6563410
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62065544"
---
# <a name="groupby-element-for-view-format"></a><span data-ttu-id="48533-102">Elemento GroupBy per View (formato)</span><span class="sxs-lookup"><span data-stu-id="48533-102">GroupBy Element for View (Format)</span></span>

<span data-ttu-id="48533-103">Definisce come viene visualizzato un nuovo gruppo di oggetti.</span><span class="sxs-lookup"><span data-stu-id="48533-103">Defines how a new group of objects is displayed.</span></span> <span data-ttu-id="48533-104">Questo elemento viene usato quando si definisce una tabella, elenco, visualizzazione controllo wide o personalizzato.</span><span class="sxs-lookup"><span data-stu-id="48533-104">This element is used when defining a table, list, wide, or custom control view.</span></span>

<span data-ttu-id="48533-105">Elemento di GroupBy elemento (formato) per la visualizzazione elemento ViewDefinitions (formato) configurazione elemento (formato) per la visualizzazione (formato)</span><span class="sxs-lookup"><span data-stu-id="48533-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) GroupBy Element for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="48533-106">Sintassi</span><span class="sxs-lookup"><span data-stu-id="48533-106">Syntax</span></span>

```xml
<GroupBy>
  <PropertyName>.NetTypeProperty</PropertyName>
  <ScriptBlock>ScriptToEvaluate</ScriptBlock>
  <Label>TextToDisplay</Label>
  <CustomControl>...</CustomControl>
  <CustomControlName>NameOfControl</CustomControlName>
</GroupBy>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="48533-107">Elementi e attributi</span><span class="sxs-lookup"><span data-stu-id="48533-107">Attributes and Elements</span></span>

<span data-ttu-id="48533-108">Le sezioni seguenti descrivono gli attributi, elementi figlio e gli elementi padre.</span><span class="sxs-lookup"><span data-stu-id="48533-108">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="48533-109">Attributes</span><span class="sxs-lookup"><span data-stu-id="48533-109">Attributes</span></span>

<span data-ttu-id="48533-110">Nessuna.</span><span class="sxs-lookup"><span data-stu-id="48533-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="48533-111">Elementi figlio</span><span class="sxs-lookup"><span data-stu-id="48533-111">Child Elements</span></span>

|<span data-ttu-id="48533-112">Elemento</span><span class="sxs-lookup"><span data-stu-id="48533-112">Element</span></span>|<span data-ttu-id="48533-113">Description</span><span class="sxs-lookup"><span data-stu-id="48533-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="48533-114">Elemento CustomControl per GroupBy (formato)</span><span class="sxs-lookup"><span data-stu-id="48533-114">CustomControl Element for GroupBy (Format)</span></span>](./customcontrol-element-for-groupby-format.md)|<span data-ttu-id="48533-115">Elemento facoltativo.</span><span class="sxs-lookup"><span data-stu-id="48533-115">Optional element.</span></span><br /><br /> <span data-ttu-id="48533-116">Definisce il controllo personalizzato che consentono di visualizzare i nuovi gruppi.</span><span class="sxs-lookup"><span data-stu-id="48533-116">Defines the custom control that display new groups.</span></span>|
|[<span data-ttu-id="48533-117">Elemento CustomControlName per GroupBy (formato)</span><span class="sxs-lookup"><span data-stu-id="48533-117">CustomControlName Element for GroupBy (Format)</span></span>](./customcontrolname-element-for-groupby-format.md)|<span data-ttu-id="48533-118">Elemento facoltativo.</span><span class="sxs-lookup"><span data-stu-id="48533-118">Optional element.</span></span><br /><br /> <span data-ttu-id="48533-119">Specifica il nome di un controllo che consente di visualizzare il nuovo gruppo.</span><span class="sxs-lookup"><span data-stu-id="48533-119">Specifies the name of a control that is used to display the new group.</span></span>|
|[<span data-ttu-id="48533-120">Elemento Label per GroupBy (formato)</span><span class="sxs-lookup"><span data-stu-id="48533-120">Label Element for GroupBy (Format)</span></span>](./label-element-for-groupby-format.md)|<span data-ttu-id="48533-121">Elemento facoltativo.</span><span class="sxs-lookup"><span data-stu-id="48533-121">Optional element.</span></span><br /><br /> <span data-ttu-id="48533-122">Specifica un'etichetta che viene visualizzata quando viene rilevato un nuovo gruppo.</span><span class="sxs-lookup"><span data-stu-id="48533-122">Specifies a label that is displayed when a new group is encountered.</span></span>|
|[<span data-ttu-id="48533-123">Elemento PropertyName per GroupBy (formato)</span><span class="sxs-lookup"><span data-stu-id="48533-123">PropertyName Element for GroupBy (Format)</span></span>](./propertyname-element-for-groupby-format.md)|<span data-ttu-id="48533-124">Elemento facoltativo.</span><span class="sxs-lookup"><span data-stu-id="48533-124">Optional element.</span></span><br /><br /> <span data-ttu-id="48533-125">Specifica la proprietà .NET inizia un nuovo gruppo ogni volta che cambia il relativo valore.</span><span class="sxs-lookup"><span data-stu-id="48533-125">Specifies the .NET property the starts a new group whenever its value changes.</span></span>|
|[<span data-ttu-id="48533-126">Elemento ScriptBlock per GroupBy (formato)</span><span class="sxs-lookup"><span data-stu-id="48533-126">ScriptBlock Element for GroupBy (Format)</span></span>](./scriptblock-element-for-groupby-format.md)|<span data-ttu-id="48533-127">Elemento facoltativo.</span><span class="sxs-lookup"><span data-stu-id="48533-127">Optional element.</span></span><br /><br /> <span data-ttu-id="48533-128">Specifica lo script che avvia un nuovo gruppo ogni volta che cambia il relativo valore.</span><span class="sxs-lookup"><span data-stu-id="48533-128">Specifies the script that starts a new group whenever its value changes.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="48533-129">Elementi padre</span><span class="sxs-lookup"><span data-stu-id="48533-129">Parent Elements</span></span>

|<span data-ttu-id="48533-130">Elemento</span><span class="sxs-lookup"><span data-stu-id="48533-130">Element</span></span>|<span data-ttu-id="48533-131">Description</span><span class="sxs-lookup"><span data-stu-id="48533-131">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="48533-132">Elemento di visualizzazione (formato)</span><span class="sxs-lookup"><span data-stu-id="48533-132">View Element (Format)</span></span>](./view-element-format.md)|<span data-ttu-id="48533-133">Definisce una vista contenente uno o più oggetti .NET.</span><span class="sxs-lookup"><span data-stu-id="48533-133">Defines a view that displays one or more .NET objects.</span></span>|

## <a name="remarks"></a><span data-ttu-id="48533-134">Osservazioni</span><span class="sxs-lookup"><span data-stu-id="48533-134">Remarks</span></span>

<span data-ttu-id="48533-135">Quando si definisce come viene visualizzato un nuovo gruppo di oggetti, è necessario specificare la proprietà o script che avvierà il nuovo gruppo; Tuttavia, è possibile specificare entrambi.</span><span class="sxs-lookup"><span data-stu-id="48533-135">When defining how a new group of objects is displayed, you must specify the property or script that will start the new group; however, you cannot specify both.</span></span>

## <a name="see-also"></a><span data-ttu-id="48533-136">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="48533-136">See Also</span></span>

[<span data-ttu-id="48533-137">Elemento CustomControlName per GroupBy (formato)</span><span class="sxs-lookup"><span data-stu-id="48533-137">CustomControlName Element for GroupBy (Format)</span></span>](./customcontrolname-element-for-groupby-format.md)

[<span data-ttu-id="48533-138">Elemento Label per GroupBy (formato)</span><span class="sxs-lookup"><span data-stu-id="48533-138">Label Element for GroupBy (Format)</span></span>](./label-element-for-groupby-format.md)

[<span data-ttu-id="48533-139">Elemento PropertyName per GroupBy (formato)</span><span class="sxs-lookup"><span data-stu-id="48533-139">PropertyName Element for GroupBy (Format)</span></span>](./propertyname-element-for-groupby-format.md)

[<span data-ttu-id="48533-140">Elemento ScriptBlock per GroupBy (formato)</span><span class="sxs-lookup"><span data-stu-id="48533-140">ScriptBlock Element for GroupBy (Format)</span></span>](./scriptblock-element-for-groupby-format.md)

[<span data-ttu-id="48533-141">Elemento di visualizzazione (formato)</span><span class="sxs-lookup"><span data-stu-id="48533-141">View Element (Format)</span></span>](./view-element-format.md)

[<span data-ttu-id="48533-142">La scrittura di un File di formattazione di PowerShell</span><span class="sxs-lookup"><span data-stu-id="48533-142">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
