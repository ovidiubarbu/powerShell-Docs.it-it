---
title: Elemento CustomEntry per CustomControl per GroupBy (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 2987cb45-f646-45d4-b81b-7871e77af36f
caps.latest.revision: 5
ms.openlocfilehash: dcf4f8b2bbd422067ffdf9b3b4972e279e91edf9
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62066485"
---
# <a name="customentry-element-for-customcontrol-for-groupby-format"></a><span data-ttu-id="76d3b-102">Elemento CustomEntry per CustomControl per GroupBy (formato)</span><span class="sxs-lookup"><span data-stu-id="76d3b-102">CustomEntry Element for CustomControl for GroupBy (Format)</span></span>

<span data-ttu-id="76d3b-103">Fornisce una definizione del controllo.</span><span class="sxs-lookup"><span data-stu-id="76d3b-103">Provides a definition of the control.</span></span> <span data-ttu-id="76d3b-104">Questo elemento viene usato quando si definisce come viene visualizzato un nuovo gruppo di oggetti.</span><span class="sxs-lookup"><span data-stu-id="76d3b-104">This element is used when defining how a new group of objects is displayed.</span></span>

<span data-ttu-id="76d3b-105">Elemento di GroupBy elemento (formato) per la visualizzazione elemento ViewDefinitions (formato) configurazione elemento (formato) per visualizzazione (formato) CustomControl elemento per elemento CustomEntries GroupBy (formato) per CustomControl per elemento CustomEntry GroupBy (formato) CustomControl per GroupBy (formato)</span><span class="sxs-lookup"><span data-stu-id="76d3b-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) GroupBy Element for View (Format) CustomControl Element for GroupBy (Format) CustomEntries Element for CustomControl for GroupBy (Format) CustomEntry Element for CustomControl for GroupBy (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="76d3b-106">Sintassi</span><span class="sxs-lookup"><span data-stu-id="76d3b-106">Syntax</span></span>

```xml
<CustomEntry>
  <EntrySelectedBy>...</EntrySelectedBy>
  <CustomItem>...</CustomItem>
</CustomEntry>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="76d3b-107">Elementi e attributi</span><span class="sxs-lookup"><span data-stu-id="76d3b-107">Attributes and Elements</span></span>

<span data-ttu-id="76d3b-108">Le sezioni seguenti descrivono gli attributi, elementi figlio e gli elementi padre del `CustomEntry` elemento.</span><span class="sxs-lookup"><span data-stu-id="76d3b-108">The following sections describe attributes, child elements, and the parent elements of the `CustomEntry` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="76d3b-109">Attributes</span><span class="sxs-lookup"><span data-stu-id="76d3b-109">Attributes</span></span>

<span data-ttu-id="76d3b-110">Nessuna.</span><span class="sxs-lookup"><span data-stu-id="76d3b-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="76d3b-111">Elementi figlio</span><span class="sxs-lookup"><span data-stu-id="76d3b-111">Child Elements</span></span>

|<span data-ttu-id="76d3b-112">Elemento</span><span class="sxs-lookup"><span data-stu-id="76d3b-112">Element</span></span>|<span data-ttu-id="76d3b-113">Description</span><span class="sxs-lookup"><span data-stu-id="76d3b-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="76d3b-114">Elemento EntrySelectedBy per CustomEntry per GroupBy (formato)</span><span class="sxs-lookup"><span data-stu-id="76d3b-114">EntrySelectedBy Element for CustomEntry for GroupBy (Format)</span></span>](./entryselectedby-element-for-customentry-for-groupby-format.md)|<span data-ttu-id="76d3b-115">Elemento facoltativo.</span><span class="sxs-lookup"><span data-stu-id="76d3b-115">Optional element.</span></span><br /><br /> <span data-ttu-id="76d3b-116">Definisce i tipi .NET che usano questa definizione di controllo o la condizione che deve essere presente per questa definizione da usare.</span><span class="sxs-lookup"><span data-stu-id="76d3b-116">Defines the .NET types that use this control definition or the condition that must exist for this definition to be used.</span></span>|
|[<span data-ttu-id="76d3b-117">Elemento CustomItem per CustomEntry per GroupBy (formato)</span><span class="sxs-lookup"><span data-stu-id="76d3b-117">CustomItem Element for CustomEntry for GroupBy (Format)</span></span>](./customitem-element-for-customentry-for-groupby-format.md)|<span data-ttu-id="76d3b-118">Elemento obbligatorio.</span><span class="sxs-lookup"><span data-stu-id="76d3b-118">Required element.</span></span><br /><br /> <span data-ttu-id="76d3b-119">Definisce come il controllo Visualizza i dati.</span><span class="sxs-lookup"><span data-stu-id="76d3b-119">Defines how the control displays the data.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="76d3b-120">Elementi padre</span><span class="sxs-lookup"><span data-stu-id="76d3b-120">Parent Elements</span></span>

|<span data-ttu-id="76d3b-121">Elemento</span><span class="sxs-lookup"><span data-stu-id="76d3b-121">Element</span></span>|<span data-ttu-id="76d3b-122">Description</span><span class="sxs-lookup"><span data-stu-id="76d3b-122">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="76d3b-123">Elemento CustomEntries per CustomControl per GroupBy (formato)</span><span class="sxs-lookup"><span data-stu-id="76d3b-123">CustomEntries Element for CustomControl for GroupBy (Format)</span></span>](./customentries-element-for-customcontrol-for-groupby-format.md)|<span data-ttu-id="76d3b-124">Fornisce le definizioni per il controllo.</span><span class="sxs-lookup"><span data-stu-id="76d3b-124">Provides the definitions for the control.</span></span>|

## <a name="remarks"></a><span data-ttu-id="76d3b-125">Osservazioni</span><span class="sxs-lookup"><span data-stu-id="76d3b-125">Remarks</span></span>

## <a name="see-also"></a><span data-ttu-id="76d3b-126">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="76d3b-126">See Also</span></span>

[<span data-ttu-id="76d3b-127">Elemento EntrySelectedBy per CustomEntry per GroupBy (formato)</span><span class="sxs-lookup"><span data-stu-id="76d3b-127">EntrySelectedBy Element for CustomEntry for GroupBy (Format)</span></span>](./entryselectedby-element-for-customentry-for-groupby-format.md)

[<span data-ttu-id="76d3b-128">Elemento CustomItem per CustomEntry per GroupBy (formato)</span><span class="sxs-lookup"><span data-stu-id="76d3b-128">CustomItem Element for CustomEntry for GroupBy (Format)</span></span>](./customitem-element-for-customentry-for-groupby-format.md)

[<span data-ttu-id="76d3b-129">Elemento CustomEntries per CustomControl per GroupBy (formato)</span><span class="sxs-lookup"><span data-stu-id="76d3b-129">CustomEntries Element for CustomControl for GroupBy (Format)</span></span>](./customentries-element-for-customcontrol-for-groupby-format.md)

[<span data-ttu-id="76d3b-130">La scrittura di un File di formattazione di PowerShell</span><span class="sxs-lookup"><span data-stu-id="76d3b-130">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
