---
title: Elemento Configuration (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d46df0cb-50b7-4b81-82ba-37186a7b7a7f
caps.latest.revision: 28
ms.openlocfilehash: 296c63d0c774a0bf56e90dbaa32f2c221d4c3dbd
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/05/2019
ms.locfileid: "72363500"
---
# <a name="configuration-element-format"></a><span data-ttu-id="5ff7b-102">Elemento Configuration (formato)</span><span class="sxs-lookup"><span data-stu-id="5ff7b-102">Configuration Element (Format)</span></span>

<span data-ttu-id="5ff7b-103">Rappresenta l'elemento di primo livello di un file di formattazione.</span><span class="sxs-lookup"><span data-stu-id="5ff7b-103">Represents the top-level element of a formatting file.</span></span>

<span data-ttu-id="5ff7b-104">Elemento di configurazione</span><span class="sxs-lookup"><span data-stu-id="5ff7b-104">Configuration Element</span></span>

## <a name="syntax"></a><span data-ttu-id="5ff7b-105">Sintassi</span><span class="sxs-lookup"><span data-stu-id="5ff7b-105">Syntax</span></span>

```xml
<Configuration>
  <DefaultSettings>...</DefaultSettings>
  <SelectionSets>...</SelectionSets>
  <Controls>...</Controls>
  <ViewDefinitions>...</ViewDefinitions>
</Configuration>

```

## <a name="attributes-and-elements"></a><span data-ttu-id="5ff7b-106">Attributi ed elementi</span><span class="sxs-lookup"><span data-stu-id="5ff7b-106">Attributes and Elements</span></span>

<span data-ttu-id="5ff7b-107">Nelle sezioni seguenti vengono descritti gli attributi, gli elementi figlio e l'elemento padre dell'elemento `Configuration`.</span><span class="sxs-lookup"><span data-stu-id="5ff7b-107">The following sections describe the attributes, child elements, and the parent element of the `Configuration` element.</span></span> <span data-ttu-id="5ff7b-108">Questo elemento deve essere l'elemento radice per ogni file di formattazione e questo elemento deve contenere almeno un elemento figlio.</span><span class="sxs-lookup"><span data-stu-id="5ff7b-108">This element must be the root element for each formatting file, and this element must contain at least one child element.</span></span>

### <a name="attributes"></a><span data-ttu-id="5ff7b-109">Attributi</span><span class="sxs-lookup"><span data-stu-id="5ff7b-109">Attributes</span></span>

<span data-ttu-id="5ff7b-110">Nessuna.</span><span class="sxs-lookup"><span data-stu-id="5ff7b-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="5ff7b-111">Elementi figlio</span><span class="sxs-lookup"><span data-stu-id="5ff7b-111">Child Elements</span></span>

|<span data-ttu-id="5ff7b-112">Elemento</span><span class="sxs-lookup"><span data-stu-id="5ff7b-112">Element</span></span>|<span data-ttu-id="5ff7b-113">Description</span><span class="sxs-lookup"><span data-stu-id="5ff7b-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="5ff7b-114">Elemento Controls per Configuration (Format)</span><span class="sxs-lookup"><span data-stu-id="5ff7b-114">Controls Element for Configuration (Format)</span></span>](./controls-element-for-configuration-format.md)|<span data-ttu-id="5ff7b-115">Elemento facoltativo.</span><span class="sxs-lookup"><span data-stu-id="5ff7b-115">Optional element.</span></span><br /><br /> <span data-ttu-id="5ff7b-116">Definisce i controlli comuni che possono essere utilizzati da tutte le visualizzazioni del file di formattazione.</span><span class="sxs-lookup"><span data-stu-id="5ff7b-116">Defines the common controls that can be used by all views of the formatting file.</span></span>|
|[<span data-ttu-id="5ff7b-117">Elemento DefaultSettings (Format)</span><span class="sxs-lookup"><span data-stu-id="5ff7b-117">DefaultSettings Element (Format)</span></span>](./defaultsettings-element-format.md)|<span data-ttu-id="5ff7b-118">Elemento facoltativo.</span><span class="sxs-lookup"><span data-stu-id="5ff7b-118">Optional element.</span></span><br /><br /> <span data-ttu-id="5ff7b-119">Definisce le impostazioni comuni che si applicano a tutte le visualizzazioni del file di formattazione.</span><span class="sxs-lookup"><span data-stu-id="5ff7b-119">Defines common settings that apply to all the views of the formatting file.</span></span>|
|[<span data-ttu-id="5ff7b-120">Formato elemento SelectionSets</span><span class="sxs-lookup"><span data-stu-id="5ff7b-120">SelectionSets Element Format</span></span>](./selectionsets-element-format.md)|<span data-ttu-id="5ff7b-121">Elemento facoltativo.</span><span class="sxs-lookup"><span data-stu-id="5ff7b-121">Optional element.</span></span><br /><br /> <span data-ttu-id="5ff7b-122">Definisce i set comuni di oggetti .NET che possono essere utilizzati da tutte le visualizzazioni del file di formattazione.</span><span class="sxs-lookup"><span data-stu-id="5ff7b-122">Defines the common sets of .NET objects that can be used by all views of the formatting file.</span></span>|
|[<span data-ttu-id="5ff7b-123">Elemento ViewDefinitions (Format)</span><span class="sxs-lookup"><span data-stu-id="5ff7b-123">ViewDefinitions Element (Format)</span></span>](./viewdefinitions-element-format.md)|<span data-ttu-id="5ff7b-124">Elemento facoltativo.</span><span class="sxs-lookup"><span data-stu-id="5ff7b-124">Optional element.</span></span><br /><br /> <span data-ttu-id="5ff7b-125">Definisce le visualizzazioni utilizzate per visualizzare gli oggetti.</span><span class="sxs-lookup"><span data-stu-id="5ff7b-125">Defines the views used to display objects.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="5ff7b-126">Elementi padre</span><span class="sxs-lookup"><span data-stu-id="5ff7b-126">Parent Elements</span></span>

<span data-ttu-id="5ff7b-127">Nessuna.</span><span class="sxs-lookup"><span data-stu-id="5ff7b-127">None.</span></span>

## <a name="remarks"></a><span data-ttu-id="5ff7b-128">Osservazioni</span><span class="sxs-lookup"><span data-stu-id="5ff7b-128">Remarks</span></span>

<span data-ttu-id="5ff7b-129">I file di formattazione definiscono la modalità di visualizzazione degli oggetti.</span><span class="sxs-lookup"><span data-stu-id="5ff7b-129">Formatting files define how objects are displayed.</span></span> <span data-ttu-id="5ff7b-130">Nella maggior parte dei casi, questo elemento radice contiene un elemento [ViewDefinitions](./viewdefinitions-element-format.md) che definisce la tabella, l'elenco e le visualizzazioni estese del file di formattazione.</span><span class="sxs-lookup"><span data-stu-id="5ff7b-130">In most cases, this root element contains a [ViewDefinitions](./viewdefinitions-element-format.md) element that defines the table, list, and wide views of the formatting file.</span></span> <span data-ttu-id="5ff7b-131">Oltre alle definizioni delle viste, il file di formattazione può definire set di selezione, impostazioni e controlli comuni che tali visualizzazioni possono usare.</span><span class="sxs-lookup"><span data-stu-id="5ff7b-131">In addition to the view definitions, the formatting file can define common selection sets, settings, and controls that those views can use.</span></span>

## <a name="see-also"></a><span data-ttu-id="5ff7b-132">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="5ff7b-132">See Also</span></span>

[<span data-ttu-id="5ff7b-133">Elemento Controls per Configuration (Format)</span><span class="sxs-lookup"><span data-stu-id="5ff7b-133">Controls Element for Configuration (Format)</span></span>](./controls-element-for-configuration-format.md)

[<span data-ttu-id="5ff7b-134">Elemento DefaultSettings (Format)</span><span class="sxs-lookup"><span data-stu-id="5ff7b-134">DefaultSettings Element (Format)</span></span>](./defaultsettings-element-format.md)

[<span data-ttu-id="5ff7b-135">Elemento SelectionSets (Format)</span><span class="sxs-lookup"><span data-stu-id="5ff7b-135">SelectionSets Element (Format)</span></span>](./selectionsets-element-format.md)

[<span data-ttu-id="5ff7b-136">Elemento ViewDefinitions (Format)</span><span class="sxs-lookup"><span data-stu-id="5ff7b-136">ViewDefinitions Element (Format)</span></span>](./viewdefinitions-element-format.md)

[<span data-ttu-id="5ff7b-137">Scrittura di un file di formattazione di PowerShell</span><span class="sxs-lookup"><span data-stu-id="5ff7b-137">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
