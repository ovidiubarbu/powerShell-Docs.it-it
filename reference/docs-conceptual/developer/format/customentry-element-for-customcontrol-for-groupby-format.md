---
title: Elemento CustomEntry per CustomControl per GroupBy (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 2987cb45-f646-45d4-b81b-7871e77af36f
caps.latest.revision: 5
ms.openlocfilehash: dcf4f8b2bbd422067ffdf9b3b4972e279e91edf9
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/15/2019
ms.locfileid: "72364060"
---
# <a name="customentry-element-for-customcontrol-for-groupby-format"></a><span data-ttu-id="3f3e6-102">Elemento CustomEntry per CustomControl per GroupBy (formato)</span><span class="sxs-lookup"><span data-stu-id="3f3e6-102">CustomEntry Element for CustomControl for GroupBy (Format)</span></span>

<span data-ttu-id="3f3e6-103">Fornisce una definizione del controllo.</span><span class="sxs-lookup"><span data-stu-id="3f3e6-103">Provides a definition of the control.</span></span> <span data-ttu-id="3f3e6-104">Questo elemento viene utilizzato quando si definisce la modalità di visualizzazione di un nuovo gruppo di oggetti.</span><span class="sxs-lookup"><span data-stu-id="3f3e6-104">This element is used when defining how a new group of objects is displayed.</span></span>

<span data-ttu-id="3f3e6-105">Elemento Configuration (Format) elemento ViewDefinitions (Format) elemento View (Format) elemento GroupBy per View (Format) elemento CustomControl per l'elemento GroupBy (Format) CustomEntries per CustomControl per l'elemento GroupBy (Format) CustomEntry per CustomControl per GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="3f3e6-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) GroupBy Element for View (Format) CustomControl Element for GroupBy (Format) CustomEntries Element for CustomControl for GroupBy (Format) CustomEntry Element for CustomControl for GroupBy (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="3f3e6-106">Sintassi</span><span class="sxs-lookup"><span data-stu-id="3f3e6-106">Syntax</span></span>

```xml
<CustomEntry>
  <EntrySelectedBy>...</EntrySelectedBy>
  <CustomItem>...</CustomItem>
</CustomEntry>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="3f3e6-107">Attributi ed elementi</span><span class="sxs-lookup"><span data-stu-id="3f3e6-107">Attributes and Elements</span></span>

<span data-ttu-id="3f3e6-108">Nelle sezioni seguenti vengono descritti gli attributi, gli elementi figlio e gli elementi padre dell'elemento `CustomEntry`.</span><span class="sxs-lookup"><span data-stu-id="3f3e6-108">The following sections describe attributes, child elements, and the parent elements of the `CustomEntry` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="3f3e6-109">Attributi</span><span class="sxs-lookup"><span data-stu-id="3f3e6-109">Attributes</span></span>

<span data-ttu-id="3f3e6-110">Nessuna.</span><span class="sxs-lookup"><span data-stu-id="3f3e6-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="3f3e6-111">Elementi figlio</span><span class="sxs-lookup"><span data-stu-id="3f3e6-111">Child Elements</span></span>

|<span data-ttu-id="3f3e6-112">Elemento</span><span class="sxs-lookup"><span data-stu-id="3f3e6-112">Element</span></span>|<span data-ttu-id="3f3e6-113">Description</span><span class="sxs-lookup"><span data-stu-id="3f3e6-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="3f3e6-114">Elemento EntrySelectedBy per CustomEntry per GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="3f3e6-114">EntrySelectedBy Element for CustomEntry for GroupBy (Format)</span></span>](./entryselectedby-element-for-customentry-for-groupby-format.md)|<span data-ttu-id="3f3e6-115">Elemento facoltativo.</span><span class="sxs-lookup"><span data-stu-id="3f3e6-115">Optional element.</span></span><br /><br /> <span data-ttu-id="3f3e6-116">Definisce i tipi .NET che utilizzano questa definizione di controllo o la condizione che deve esistere affinché questa definizione venga utilizzata.</span><span class="sxs-lookup"><span data-stu-id="3f3e6-116">Defines the .NET types that use this control definition or the condition that must exist for this definition to be used.</span></span>|
|[<span data-ttu-id="3f3e6-117">Elemento CustomItem per CustomEntry per GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="3f3e6-117">CustomItem Element for CustomEntry for GroupBy (Format)</span></span>](./customitem-element-for-customentry-for-groupby-format.md)|<span data-ttu-id="3f3e6-118">Elemento obbligatorio.</span><span class="sxs-lookup"><span data-stu-id="3f3e6-118">Required element.</span></span><br /><br /> <span data-ttu-id="3f3e6-119">Definisce la modalità di visualizzazione dei dati da parte del controllo.</span><span class="sxs-lookup"><span data-stu-id="3f3e6-119">Defines how the control displays the data.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="3f3e6-120">Elementi padre</span><span class="sxs-lookup"><span data-stu-id="3f3e6-120">Parent Elements</span></span>

|<span data-ttu-id="3f3e6-121">Elemento</span><span class="sxs-lookup"><span data-stu-id="3f3e6-121">Element</span></span>|<span data-ttu-id="3f3e6-122">Description</span><span class="sxs-lookup"><span data-stu-id="3f3e6-122">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="3f3e6-123">Elemento CustomEntries per CustomControl per GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="3f3e6-123">CustomEntries Element for CustomControl for GroupBy (Format)</span></span>](./customentries-element-for-customcontrol-for-groupby-format.md)|<span data-ttu-id="3f3e6-124">Fornisce le definizioni per il controllo.</span><span class="sxs-lookup"><span data-stu-id="3f3e6-124">Provides the definitions for the control.</span></span>|

## <a name="remarks"></a><span data-ttu-id="3f3e6-125">Osservazioni</span><span class="sxs-lookup"><span data-stu-id="3f3e6-125">Remarks</span></span>

## <a name="see-also"></a><span data-ttu-id="3f3e6-126">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="3f3e6-126">See Also</span></span>

[<span data-ttu-id="3f3e6-127">Elemento EntrySelectedBy per CustomEntry per GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="3f3e6-127">EntrySelectedBy Element for CustomEntry for GroupBy (Format)</span></span>](./entryselectedby-element-for-customentry-for-groupby-format.md)

[<span data-ttu-id="3f3e6-128">Elemento CustomItem per CustomEntry per GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="3f3e6-128">CustomItem Element for CustomEntry for GroupBy (Format)</span></span>](./customitem-element-for-customentry-for-groupby-format.md)

[<span data-ttu-id="3f3e6-129">Elemento CustomEntries per CustomControl per GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="3f3e6-129">CustomEntries Element for CustomControl for GroupBy (Format)</span></span>](./customentries-element-for-customcontrol-for-groupby-format.md)

[<span data-ttu-id="3f3e6-130">Scrittura di un file di formattazione di PowerShell</span><span class="sxs-lookup"><span data-stu-id="3f3e6-130">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
