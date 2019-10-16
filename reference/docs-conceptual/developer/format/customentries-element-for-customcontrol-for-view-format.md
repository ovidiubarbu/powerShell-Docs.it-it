---
title: Elemento CustomEntries per CustomControl per View (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: cb412831-94f7-4054-b19e-32c1b14c66dd
caps.latest.revision: 11
ms.openlocfilehash: 827baacd22ef258dd9b0c8a383a23fce7d975f7f
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/15/2019
ms.locfileid: "72364080"
---
# <a name="customentries-element-for-customcontrol-for-view-format"></a><span data-ttu-id="4d405-102">Elemento CustomEntries per CustomControl per View (formato)</span><span class="sxs-lookup"><span data-stu-id="4d405-102">CustomEntries Element for CustomControl for View (Format)</span></span>

<span data-ttu-id="4d405-103">Fornisce le definizioni della visualizzazione controlli personalizzata.</span><span class="sxs-lookup"><span data-stu-id="4d405-103">Provides the definitions of the custom control view.</span></span> <span data-ttu-id="4d405-104">La visualizzazione controlli personalizzata deve specificare una o più definizioni.</span><span class="sxs-lookup"><span data-stu-id="4d405-104">The custom control view must specify one or more definitions.</span></span>

<span data-ttu-id="4d405-105">Elemento Configuration (Format) elemento ViewDefinitions (Format) elemento View (Format) elemento CustomControl (Format) elemento CustomEntries per CustomControl per View (Format)</span><span class="sxs-lookup"><span data-stu-id="4d405-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) CustomControl Element (Format) CustomEntries Element for CustomControl for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="4d405-106">Sintassi</span><span class="sxs-lookup"><span data-stu-id="4d405-106">Syntax</span></span>

```xml
<CustomEntries>
  <CustomEntry>...</CustomEntry>
</CustomEntries>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="4d405-107">Attributi ed elementi</span><span class="sxs-lookup"><span data-stu-id="4d405-107">Attributes and Elements</span></span>

<span data-ttu-id="4d405-108">Nelle sezioni seguenti vengono descritti gli attributi, gli elementi figlio e l'elemento padre dell'elemento `CustomControlEntries`.</span><span class="sxs-lookup"><span data-stu-id="4d405-108">The following sections describe attributes, child elements, and the parent element of the `CustomControlEntries` element.</span></span> <span data-ttu-id="4d405-109">È necessario specificare uno o più elementi figlio.</span><span class="sxs-lookup"><span data-stu-id="4d405-109">You must specify one or more child elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="4d405-110">Attributi</span><span class="sxs-lookup"><span data-stu-id="4d405-110">Attributes</span></span>

<span data-ttu-id="4d405-111">Nessuna.</span><span class="sxs-lookup"><span data-stu-id="4d405-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="4d405-112">Elementi figlio</span><span class="sxs-lookup"><span data-stu-id="4d405-112">Child Elements</span></span>

|<span data-ttu-id="4d405-113">Elemento</span><span class="sxs-lookup"><span data-stu-id="4d405-113">Element</span></span>|<span data-ttu-id="4d405-114">Description</span><span class="sxs-lookup"><span data-stu-id="4d405-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="4d405-115">Elemento CustomEntry per CustomEntries per View (Format)</span><span class="sxs-lookup"><span data-stu-id="4d405-115">CustomEntry Element for CustomEntries for View (Format)</span></span>](./customentry-element-for-customentries-for-customcontrol-for-view-format.md)|<span data-ttu-id="4d405-116">Elemento obbligatorio.</span><span class="sxs-lookup"><span data-stu-id="4d405-116">Required element.</span></span><br /><br /> <span data-ttu-id="4d405-117">Fornisce una definizione della visualizzazione controlli personalizzata.</span><span class="sxs-lookup"><span data-stu-id="4d405-117">Provides a definition of the custom control view.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="4d405-118">Elementi padre</span><span class="sxs-lookup"><span data-stu-id="4d405-118">Parent Elements</span></span>

|<span data-ttu-id="4d405-119">Elemento</span><span class="sxs-lookup"><span data-stu-id="4d405-119">Element</span></span>|<span data-ttu-id="4d405-120">Description</span><span class="sxs-lookup"><span data-stu-id="4d405-120">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="4d405-121">Elemento CustomControl per View (Format)</span><span class="sxs-lookup"><span data-stu-id="4d405-121">CustomControl Element for View (Format)</span></span>](./customcontrol-element-for-view-format.md)|<span data-ttu-id="4d405-122">Elemento obbligatorio.</span><span class="sxs-lookup"><span data-stu-id="4d405-122">Required element.</span></span><br /><br /> <span data-ttu-id="4d405-123">Definisce un formato di controllo personalizzato per la visualizzazione.</span><span class="sxs-lookup"><span data-stu-id="4d405-123">Defines a custom control format for the view.</span></span>|

## <a name="remarks"></a><span data-ttu-id="4d405-124">Osservazioni</span><span class="sxs-lookup"><span data-stu-id="4d405-124">Remarks</span></span>

<span data-ttu-id="4d405-125">Nella maggior parte dei casi, un controllo ha una sola definizione, definita in un singolo elemento `CustomEntry`.</span><span class="sxs-lookup"><span data-stu-id="4d405-125">In most cases, a control has only one definition, which is defined in a single `CustomEntry` element.</span></span> <span data-ttu-id="4d405-126">Tuttavia, se si desidera utilizzare lo stesso controllo per visualizzare oggetti .NET diversi, è possibile disporre di più definizioni.</span><span class="sxs-lookup"><span data-stu-id="4d405-126">However it is possible to have multiple definitions if you want to use the same control to display different .NET objects.</span></span> <span data-ttu-id="4d405-127">In questi casi, è possibile definire un elemento `CustomEntry` per ogni oggetto o set di oggetti.</span><span class="sxs-lookup"><span data-stu-id="4d405-127">In those cases, you can define a `CustomEntry` element for each object or set of objects.</span></span>

## <a name="see-also"></a><span data-ttu-id="4d405-128">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="4d405-128">See Also</span></span>

[<span data-ttu-id="4d405-129">Elemento CustomControl per View (Format)</span><span class="sxs-lookup"><span data-stu-id="4d405-129">CustomControl Element for View (Format)</span></span>](./customcontrol-element-for-view-format.md)

[<span data-ttu-id="4d405-130">Elemento CustomEntry per CustomEntries per View (Format)</span><span class="sxs-lookup"><span data-stu-id="4d405-130">CustomEntry Element for CustomEntries for View (Format)</span></span>](./customentry-element-for-customentries-for-customcontrol-for-view-format.md)

[<span data-ttu-id="4d405-131">Scrittura di un file di formattazione di PowerShell</span><span class="sxs-lookup"><span data-stu-id="4d405-131">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
