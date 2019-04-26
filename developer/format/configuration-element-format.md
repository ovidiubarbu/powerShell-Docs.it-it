---
title: Elemento di configurazione (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d46df0cb-50b7-4b81-82ba-37186a7b7a7f
caps.latest.revision: 28
ms.openlocfilehash: 296c63d0c774a0bf56e90dbaa32f2c221d4c3dbd
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62066822"
---
# <a name="configuration-element-format"></a><span data-ttu-id="bf147-102">Elemento Configuration (formato)</span><span class="sxs-lookup"><span data-stu-id="bf147-102">Configuration Element (Format)</span></span>

<span data-ttu-id="bf147-103">Rappresenta l'elemento di livello superiore di un file di formattazione.</span><span class="sxs-lookup"><span data-stu-id="bf147-103">Represents the top-level element of a formatting file.</span></span>

<span data-ttu-id="bf147-104">Elemento di configurazione</span><span class="sxs-lookup"><span data-stu-id="bf147-104">Configuration Element</span></span>

## <a name="syntax"></a><span data-ttu-id="bf147-105">Sintassi</span><span class="sxs-lookup"><span data-stu-id="bf147-105">Syntax</span></span>

```xml
<Configuration>
  <DefaultSettings>...</DefaultSettings>
  <SelectionSets>...</SelectionSets>
  <Controls>...</Controls>
  <ViewDefinitions>...</ViewDefinitions>
</Configuration>

```

## <a name="attributes-and-elements"></a><span data-ttu-id="bf147-106">Elementi e attributi</span><span class="sxs-lookup"><span data-stu-id="bf147-106">Attributes and Elements</span></span>

<span data-ttu-id="bf147-107">Le sezioni seguenti descrivono gli attributi e gli elementi figlio dell'elemento padre del `Configuration` elemento.</span><span class="sxs-lookup"><span data-stu-id="bf147-107">The following sections describe the attributes, child elements, and the parent element of the `Configuration` element.</span></span> <span data-ttu-id="bf147-108">Questo elemento deve essere l'elemento radice per ogni file di formattazione e questo elemento deve contenere almeno un elemento figlio.</span><span class="sxs-lookup"><span data-stu-id="bf147-108">This element must be the root element for each formatting file, and this element must contain at least one child element.</span></span>

### <a name="attributes"></a><span data-ttu-id="bf147-109">Attributes</span><span class="sxs-lookup"><span data-stu-id="bf147-109">Attributes</span></span>

<span data-ttu-id="bf147-110">Nessuna.</span><span class="sxs-lookup"><span data-stu-id="bf147-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="bf147-111">Elementi figlio</span><span class="sxs-lookup"><span data-stu-id="bf147-111">Child Elements</span></span>

|<span data-ttu-id="bf147-112">Elemento</span><span class="sxs-lookup"><span data-stu-id="bf147-112">Element</span></span>|<span data-ttu-id="bf147-113">Description</span><span class="sxs-lookup"><span data-stu-id="bf147-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="bf147-114">I controlli elemento di configurazione (formato)</span><span class="sxs-lookup"><span data-stu-id="bf147-114">Controls Element for Configuration (Format)</span></span>](./controls-element-for-configuration-format.md)|<span data-ttu-id="bf147-115">Elemento facoltativo.</span><span class="sxs-lookup"><span data-stu-id="bf147-115">Optional element.</span></span><br /><br /> <span data-ttu-id="bf147-116">Definisce i controlli comuni che possono essere usati da tutte le visualizzazioni del file di formattazione.</span><span class="sxs-lookup"><span data-stu-id="bf147-116">Defines the common controls that can be used by all views of the formatting file.</span></span>|
|[<span data-ttu-id="bf147-117">Elemento DefaultSettings (formato)</span><span class="sxs-lookup"><span data-stu-id="bf147-117">DefaultSettings Element (Format)</span></span>](./defaultsettings-element-format.md)|<span data-ttu-id="bf147-118">Elemento facoltativo.</span><span class="sxs-lookup"><span data-stu-id="bf147-118">Optional element.</span></span><br /><br /> <span data-ttu-id="bf147-119">Definisce le impostazioni comuni che si applicano a tutte le visualizzazioni del file di formattazione.</span><span class="sxs-lookup"><span data-stu-id="bf147-119">Defines common settings that apply to all the views of the formatting file.</span></span>|
|[<span data-ttu-id="bf147-120">Formato elemento SelectionSets</span><span class="sxs-lookup"><span data-stu-id="bf147-120">SelectionSets Element Format</span></span>](./selectionsets-element-format.md)|<span data-ttu-id="bf147-121">Elemento facoltativo.</span><span class="sxs-lookup"><span data-stu-id="bf147-121">Optional element.</span></span><br /><br /> <span data-ttu-id="bf147-122">Definisce il set di oggetti .NET che possono essere usati da tutte le visualizzazioni del file di formattazione comuni.</span><span class="sxs-lookup"><span data-stu-id="bf147-122">Defines the common sets of .NET objects that can be used by all views of the formatting file.</span></span>|
|[<span data-ttu-id="bf147-123">Elemento ViewDefinitions (formato)</span><span class="sxs-lookup"><span data-stu-id="bf147-123">ViewDefinitions Element (Format)</span></span>](./viewdefinitions-element-format.md)|<span data-ttu-id="bf147-124">Elemento facoltativo.</span><span class="sxs-lookup"><span data-stu-id="bf147-124">Optional element.</span></span><br /><br /> <span data-ttu-id="bf147-125">Definisce le viste utilizzate per visualizzare gli oggetti.</span><span class="sxs-lookup"><span data-stu-id="bf147-125">Defines the views used to display objects.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="bf147-126">Elementi padre</span><span class="sxs-lookup"><span data-stu-id="bf147-126">Parent Elements</span></span>

<span data-ttu-id="bf147-127">Nessuna.</span><span class="sxs-lookup"><span data-stu-id="bf147-127">None.</span></span>

## <a name="remarks"></a><span data-ttu-id="bf147-128">Osservazioni</span><span class="sxs-lookup"><span data-stu-id="bf147-128">Remarks</span></span>

<span data-ttu-id="bf147-129">File di formattazione definiscono come gli oggetti vengono visualizzati.</span><span class="sxs-lookup"><span data-stu-id="bf147-129">Formatting files define how objects are displayed.</span></span> <span data-ttu-id="bf147-130">Nella maggior parte dei casi, questo elemento radice contiene un [ViewDefinitions](./viewdefinitions-element-format.md) elemento che definisce la tabella, elenco e visualizzazioni ampie del file di formattazione.</span><span class="sxs-lookup"><span data-stu-id="bf147-130">In most cases, this root element contains a [ViewDefinitions](./viewdefinitions-element-format.md) element that defines the table, list, and wide views of the formatting file.</span></span> <span data-ttu-id="bf147-131">Oltre alle definizioni delle viste, è possibile definire il file di formattazione comuni selezione set, impostazioni e i controlli che è possono utilizzare tali viste.</span><span class="sxs-lookup"><span data-stu-id="bf147-131">In addition to the view definitions, the formatting file can define common selection sets, settings, and controls that those views can use.</span></span>

## <a name="see-also"></a><span data-ttu-id="bf147-132">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="bf147-132">See Also</span></span>

[<span data-ttu-id="bf147-133">I controlli elemento di configurazione (formato)</span><span class="sxs-lookup"><span data-stu-id="bf147-133">Controls Element for Configuration (Format)</span></span>](./controls-element-for-configuration-format.md)

[<span data-ttu-id="bf147-134">Elemento DefaultSettings (formato)</span><span class="sxs-lookup"><span data-stu-id="bf147-134">DefaultSettings Element (Format)</span></span>](./defaultsettings-element-format.md)

[<span data-ttu-id="bf147-135">Elemento SelectionSets (formato)</span><span class="sxs-lookup"><span data-stu-id="bf147-135">SelectionSets Element (Format)</span></span>](./selectionsets-element-format.md)

[<span data-ttu-id="bf147-136">Elemento ViewDefinitions (formato)</span><span class="sxs-lookup"><span data-stu-id="bf147-136">ViewDefinitions Element (Format)</span></span>](./viewdefinitions-element-format.md)

[<span data-ttu-id="bf147-137">La scrittura di un File di formattazione di PowerShell</span><span class="sxs-lookup"><span data-stu-id="bf147-137">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
