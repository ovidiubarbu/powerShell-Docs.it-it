---
title: Elemento CustomEntry per CustomEntries per CustomControl per View (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ac3c0a25-f2ca-4e28-b3dc-9cb06a76d92a
caps.latest.revision: 11
ms.openlocfilehash: 7804155bffeb1f0df8339f797bf59f8def56a3fc
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/15/2019
ms.locfileid: "72364020"
---
# <a name="customentry-element-for-customentries-for-customcontrol-for-view-format"></a><span data-ttu-id="1be24-102">Elemento CustomEntry per CustomEntries per CustomControl per View (formato)</span><span class="sxs-lookup"><span data-stu-id="1be24-102">CustomEntry Element for CustomEntries for CustomControl for View (Format)</span></span>

<span data-ttu-id="1be24-103">Fornisce una definizione della visualizzazione controlli personalizzata.</span><span class="sxs-lookup"><span data-stu-id="1be24-103">Provides a definition of the custom control view.</span></span>

<span data-ttu-id="1be24-104">Elemento Configuration (Format) elemento ViewDefinitions (Format) elemento View (Format) elemento CustomControl (Format) elemento CustomEntries per CustomControl per l'elemento View (Format) CustomEntry per CustomEntries per View (Format)</span><span class="sxs-lookup"><span data-stu-id="1be24-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) CustomControl Element (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="1be24-105">Sintassi</span><span class="sxs-lookup"><span data-stu-id="1be24-105">Syntax</span></span>

```xml
<CustomEntry>
  <EntrySelectedBy>...</EntrySelectedBy>
  <CustomItem>...</CustomItem>
</CustomEntry>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="1be24-106">Attributi ed elementi</span><span class="sxs-lookup"><span data-stu-id="1be24-106">Attributes and Elements</span></span>

<span data-ttu-id="1be24-107">Nelle sezioni seguenti vengono descritti gli attributi, gli elementi figlio e l'elemento padre dell'elemento `CustomEntry`.</span><span class="sxs-lookup"><span data-stu-id="1be24-107">The following sections describe attributes, child elements, and the parent element of the `CustomEntry` element.</span></span> <span data-ttu-id="1be24-108">È necessario specificare gli elementi visualizzati dalla definizione.</span><span class="sxs-lookup"><span data-stu-id="1be24-108">You must specify the items displayed by the definition.</span></span>

### <a name="attributes"></a><span data-ttu-id="1be24-109">Attributi</span><span class="sxs-lookup"><span data-stu-id="1be24-109">Attributes</span></span>

<span data-ttu-id="1be24-110">Nessuna.</span><span class="sxs-lookup"><span data-stu-id="1be24-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="1be24-111">Elementi figlio</span><span class="sxs-lookup"><span data-stu-id="1be24-111">Child Elements</span></span>

|<span data-ttu-id="1be24-112">Elemento</span><span class="sxs-lookup"><span data-stu-id="1be24-112">Element</span></span>|<span data-ttu-id="1be24-113">Description</span><span class="sxs-lookup"><span data-stu-id="1be24-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="1be24-114">Elemento EntrySelectedBy per CustomEntry per View (Format)</span><span class="sxs-lookup"><span data-stu-id="1be24-114">EntrySelectedBy Element for CustomEntry for View (Format)</span></span>](./entryselectedby-element-for-customentry-for-customcontrol-for-view-format.md)|<span data-ttu-id="1be24-115">Elemento facoltativo.</span><span class="sxs-lookup"><span data-stu-id="1be24-115">Optional element.</span></span><br /><br /> <span data-ttu-id="1be24-116">Definisce i tipi .NET che utilizzano la definizione della visualizzazione controlli personalizzata o la condizione che deve esistere affinché questa definizione venga utilizzata.</span><span class="sxs-lookup"><span data-stu-id="1be24-116">Defines the .NET types that use the definition of the custom control view or the condition that must exist for this definition to be used.</span></span>|
|[<span data-ttu-id="1be24-117">Elemento CustomItem per CustomEntry per View (Format)</span><span class="sxs-lookup"><span data-stu-id="1be24-117">CustomItem Element for CustomEntry for View (Format)</span></span>](./customitem-element-for-customentry-for-customcontrol-for-view-format.md)|<span data-ttu-id="1be24-118">Definisce un controllo per la definizione del controllo personalizzato.</span><span class="sxs-lookup"><span data-stu-id="1be24-118">Defines a control for the custom control definition.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="1be24-119">Elementi padre</span><span class="sxs-lookup"><span data-stu-id="1be24-119">Parent Elements</span></span>

|<span data-ttu-id="1be24-120">Elemento</span><span class="sxs-lookup"><span data-stu-id="1be24-120">Element</span></span>|<span data-ttu-id="1be24-121">Description</span><span class="sxs-lookup"><span data-stu-id="1be24-121">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="1be24-122">Elemento CustomEntries per CustomControl per View (Format)</span><span class="sxs-lookup"><span data-stu-id="1be24-122">CustomEntries Element for CustomControl for View (Format)</span></span>](./customentries-element-for-customcontrol-for-view-format.md)|<span data-ttu-id="1be24-123">Fornisce le definizioni della visualizzazione controlli personalizzata.</span><span class="sxs-lookup"><span data-stu-id="1be24-123">Provides the definitions of the custom control view.</span></span> <span data-ttu-id="1be24-124">La visualizzazione controlli personalizzata deve specificare una o più definizioni.</span><span class="sxs-lookup"><span data-stu-id="1be24-124">The custom control view must specify one or more definitions.</span></span>|

## <a name="remarks"></a><span data-ttu-id="1be24-125">Osservazioni</span><span class="sxs-lookup"><span data-stu-id="1be24-125">Remarks</span></span>

<span data-ttu-id="1be24-126">Nella maggior parte dei casi, è necessaria una sola definizione per ogni visualizzazione controlli personalizzata, ma è possibile avere più definizioni se si vuole usare la stessa vista per visualizzare oggetti .NET diversi.</span><span class="sxs-lookup"><span data-stu-id="1be24-126">In most cases, only one definition is required for each custom control view, but it is possible to have multiple definitions if you want to use the same view to display different .NET objects.</span></span> <span data-ttu-id="1be24-127">In questi casi, è possibile specificare una definizione separata per ogni oggetto o set di oggetti.</span><span class="sxs-lookup"><span data-stu-id="1be24-127">In those cases, you can provide a separate definition for each object or set of objects.</span></span>

## <a name="see-also"></a><span data-ttu-id="1be24-128">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="1be24-128">See Also</span></span>

[<span data-ttu-id="1be24-129">Elemento CustomControl per View (Format)</span><span class="sxs-lookup"><span data-stu-id="1be24-129">CustomControl Element for View (Format)</span></span>](./customcontrol-element-for-view-format.md)

[<span data-ttu-id="1be24-130">Elemento CustomItem per CustomEntry per View (Format)</span><span class="sxs-lookup"><span data-stu-id="1be24-130">CustomItem Element for CustomEntry for View (Format)</span></span>](./customitem-element-for-customentry-for-customcontrol-for-view-format.md)

[<span data-ttu-id="1be24-131">Elemento EntrySelectedBy per CustomEntry per View (Format)</span><span class="sxs-lookup"><span data-stu-id="1be24-131">EntrySelectedBy Element for CustomEntry for View (Format)</span></span>](./entryselectedby-element-for-customentry-for-customcontrol-for-view-format.md)

[<span data-ttu-id="1be24-132">Scrittura di un file di formattazione di PowerShell</span><span class="sxs-lookup"><span data-stu-id="1be24-132">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
