---
title: Elemento CustomEntries per CustomControl per visualizzazione (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: cb412831-94f7-4054-b19e-32c1b14c66dd
caps.latest.revision: 11
ms.openlocfilehash: 827baacd22ef258dd9b0c8a383a23fce7d975f7f
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62066516"
---
# <a name="customentries-element-for-customcontrol-for-view-format"></a><span data-ttu-id="75fac-102">Elemento CustomEntries per CustomControl per View (formato)</span><span class="sxs-lookup"><span data-stu-id="75fac-102">CustomEntries Element for CustomControl for View (Format)</span></span>

<span data-ttu-id="75fac-103">Fornisce le definizioni della vista del controllo personalizzato.</span><span class="sxs-lookup"><span data-stu-id="75fac-103">Provides the definitions of the custom control view.</span></span> <span data-ttu-id="75fac-104">La visualizzazione controlli personalizzati è necessario specificare una o più definizioni.</span><span class="sxs-lookup"><span data-stu-id="75fac-104">The custom control view must specify one or more definitions.</span></span>

<span data-ttu-id="75fac-105">Elemento (formato) elemento ViewDefinitions (formato) visualizzazione elemento (formato) elemento CustomControl (formato) CustomEntries elemento di configurazione per CustomControl per visualizzazione (formato)</span><span class="sxs-lookup"><span data-stu-id="75fac-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) CustomControl Element (Format) CustomEntries Element for CustomControl for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="75fac-106">Sintassi</span><span class="sxs-lookup"><span data-stu-id="75fac-106">Syntax</span></span>

```xml
<CustomEntries>
  <CustomEntry>...</CustomEntry>
</CustomEntries>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="75fac-107">Elementi e attributi</span><span class="sxs-lookup"><span data-stu-id="75fac-107">Attributes and Elements</span></span>

<span data-ttu-id="75fac-108">Le sezioni seguenti descrivono gli attributi e gli elementi figlio dell'elemento padre del `CustomControlEntries` elemento.</span><span class="sxs-lookup"><span data-stu-id="75fac-108">The following sections describe attributes, child elements, and the parent element of the `CustomControlEntries` element.</span></span> <span data-ttu-id="75fac-109">È necessario specificare uno o più elementi figlio.</span><span class="sxs-lookup"><span data-stu-id="75fac-109">You must specify one or more child elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="75fac-110">Attributes</span><span class="sxs-lookup"><span data-stu-id="75fac-110">Attributes</span></span>

<span data-ttu-id="75fac-111">Nessuna.</span><span class="sxs-lookup"><span data-stu-id="75fac-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="75fac-112">Elementi figlio</span><span class="sxs-lookup"><span data-stu-id="75fac-112">Child Elements</span></span>

|<span data-ttu-id="75fac-113">Elemento</span><span class="sxs-lookup"><span data-stu-id="75fac-113">Element</span></span>|<span data-ttu-id="75fac-114">Description</span><span class="sxs-lookup"><span data-stu-id="75fac-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="75fac-115">Elemento CustomEntry per CustomEntries per visualizzazione (formato)</span><span class="sxs-lookup"><span data-stu-id="75fac-115">CustomEntry Element for CustomEntries for View (Format)</span></span>](./customentry-element-for-customentries-for-customcontrol-for-view-format.md)|<span data-ttu-id="75fac-116">Elemento obbligatorio.</span><span class="sxs-lookup"><span data-stu-id="75fac-116">Required element.</span></span><br /><br /> <span data-ttu-id="75fac-117">Fornisce una definizione della vista del controllo personalizzato.</span><span class="sxs-lookup"><span data-stu-id="75fac-117">Provides a definition of the custom control view.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="75fac-118">Elementi padre</span><span class="sxs-lookup"><span data-stu-id="75fac-118">Parent Elements</span></span>

|<span data-ttu-id="75fac-119">Elemento</span><span class="sxs-lookup"><span data-stu-id="75fac-119">Element</span></span>|<span data-ttu-id="75fac-120">Description</span><span class="sxs-lookup"><span data-stu-id="75fac-120">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="75fac-121">Elemento CustomControl per visualizzazione (formato)</span><span class="sxs-lookup"><span data-stu-id="75fac-121">CustomControl Element for View (Format)</span></span>](./customcontrol-element-for-view-format.md)|<span data-ttu-id="75fac-122">Elemento obbligatorio.</span><span class="sxs-lookup"><span data-stu-id="75fac-122">Required element.</span></span><br /><br /> <span data-ttu-id="75fac-123">Definisce un formato di controllo personalizzato per la visualizzazione.</span><span class="sxs-lookup"><span data-stu-id="75fac-123">Defines a custom control format for the view.</span></span>|

## <a name="remarks"></a><span data-ttu-id="75fac-124">Osservazioni</span><span class="sxs-lookup"><span data-stu-id="75fac-124">Remarks</span></span>

<span data-ttu-id="75fac-125">Nella maggior parte dei casi, un controllo ha una sola definizione, di cui è definita in una singola `CustomEntry` elemento.</span><span class="sxs-lookup"><span data-stu-id="75fac-125">In most cases, a control has only one definition, which is defined in a single `CustomEntry` element.</span></span> <span data-ttu-id="75fac-126">Tuttavia è possibile avere più definizioni, se si desidera utilizzare lo stesso controllo per visualizzare diversi oggetti .NET.</span><span class="sxs-lookup"><span data-stu-id="75fac-126">However it is possible to have multiple definitions if you want to use the same control to display different .NET objects.</span></span> <span data-ttu-id="75fac-127">In questi casi, è possibile definire un `CustomEntry` (elemento) per ogni oggetto o un set di oggetti.</span><span class="sxs-lookup"><span data-stu-id="75fac-127">In those cases, you can define a `CustomEntry` element for each object or set of objects.</span></span>

## <a name="see-also"></a><span data-ttu-id="75fac-128">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="75fac-128">See Also</span></span>

[<span data-ttu-id="75fac-129">Elemento CustomControl per visualizzazione (formato)</span><span class="sxs-lookup"><span data-stu-id="75fac-129">CustomControl Element for View (Format)</span></span>](./customcontrol-element-for-view-format.md)

[<span data-ttu-id="75fac-130">Elemento CustomEntry per CustomEntries per visualizzazione (formato)</span><span class="sxs-lookup"><span data-stu-id="75fac-130">CustomEntry Element for CustomEntries for View (Format)</span></span>](./customentry-element-for-customentries-for-customcontrol-for-view-format.md)

[<span data-ttu-id="75fac-131">La scrittura di un File di formattazione di PowerShell</span><span class="sxs-lookup"><span data-stu-id="75fac-131">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
