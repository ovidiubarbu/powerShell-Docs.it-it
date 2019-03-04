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
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/03/2019
ms.locfileid: "56861697"
---
# <a name="customentries-element-for-customcontrol-for-view-format"></a><span data-ttu-id="f6f45-102">Elemento CustomEntries per CustomControl per View (formato)</span><span class="sxs-lookup"><span data-stu-id="f6f45-102">CustomEntries Element for CustomControl for View (Format)</span></span>

<span data-ttu-id="f6f45-103">Fornisce le definizioni della vista del controllo personalizzato.</span><span class="sxs-lookup"><span data-stu-id="f6f45-103">Provides the definitions of the custom control view.</span></span> <span data-ttu-id="f6f45-104">La visualizzazione controlli personalizzati è necessario specificare una o più definizioni.</span><span class="sxs-lookup"><span data-stu-id="f6f45-104">The custom control view must specify one or more definitions.</span></span>

<span data-ttu-id="f6f45-105">Elemento (formato) elemento ViewDefinitions (formato) visualizzazione elemento (formato) elemento CustomControl (formato) CustomEntries elemento di configurazione per CustomControl per visualizzazione (formato)</span><span class="sxs-lookup"><span data-stu-id="f6f45-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) CustomControl Element (Format) CustomEntries Element for CustomControl for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="f6f45-106">Sintassi</span><span class="sxs-lookup"><span data-stu-id="f6f45-106">Syntax</span></span>

```xml
<CustomEntries>
  <CustomEntry>...</CustomEntry>
</CustomEntries>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="f6f45-107">Attributi ed elementi</span><span class="sxs-lookup"><span data-stu-id="f6f45-107">Attributes and Elements</span></span>

<span data-ttu-id="f6f45-108">Le sezioni seguenti descrivono gli attributi e gli elementi figlio dell'elemento padre del `CustomControlEntries` elemento.</span><span class="sxs-lookup"><span data-stu-id="f6f45-108">The following sections describe attributes, child elements, and the parent element of the `CustomControlEntries` element.</span></span> <span data-ttu-id="f6f45-109">È necessario specificare uno o più elementi figlio.</span><span class="sxs-lookup"><span data-stu-id="f6f45-109">You must specify one or more child elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="f6f45-110">Attributes</span><span class="sxs-lookup"><span data-stu-id="f6f45-110">Attributes</span></span>

<span data-ttu-id="f6f45-111">Nessuna.</span><span class="sxs-lookup"><span data-stu-id="f6f45-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="f6f45-112">Elementi figlio</span><span class="sxs-lookup"><span data-stu-id="f6f45-112">Child Elements</span></span>

|<span data-ttu-id="f6f45-113">Elemento</span><span class="sxs-lookup"><span data-stu-id="f6f45-113">Element</span></span>|<span data-ttu-id="f6f45-114">Description</span><span class="sxs-lookup"><span data-stu-id="f6f45-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="f6f45-115">Elemento CustomEntry per CustomEntries per visualizzazione (formato)</span><span class="sxs-lookup"><span data-stu-id="f6f45-115">CustomEntry Element for CustomEntries for View (Format)</span></span>](./customentry-element-for-customentries-for-customcontrol-for-view-format.md)|<span data-ttu-id="f6f45-116">Elemento obbligatorio.</span><span class="sxs-lookup"><span data-stu-id="f6f45-116">Required element.</span></span><br /><br /> <span data-ttu-id="f6f45-117">Fornisce una definizione della vista del controllo personalizzato.</span><span class="sxs-lookup"><span data-stu-id="f6f45-117">Provides a definition of the custom control view.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="f6f45-118">Elementi padre</span><span class="sxs-lookup"><span data-stu-id="f6f45-118">Parent Elements</span></span>

|<span data-ttu-id="f6f45-119">Elemento</span><span class="sxs-lookup"><span data-stu-id="f6f45-119">Element</span></span>|<span data-ttu-id="f6f45-120">Description</span><span class="sxs-lookup"><span data-stu-id="f6f45-120">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="f6f45-121">Elemento CustomControl per visualizzazione (formato)</span><span class="sxs-lookup"><span data-stu-id="f6f45-121">CustomControl Element for View (Format)</span></span>](./customcontrol-element-for-view-format.md)|<span data-ttu-id="f6f45-122">Elemento obbligatorio.</span><span class="sxs-lookup"><span data-stu-id="f6f45-122">Required element.</span></span><br /><br /> <span data-ttu-id="f6f45-123">Definisce un formato di controllo personalizzato per la visualizzazione.</span><span class="sxs-lookup"><span data-stu-id="f6f45-123">Defines a custom control format for the view.</span></span>|

## <a name="remarks"></a><span data-ttu-id="f6f45-124">Osservazioni</span><span class="sxs-lookup"><span data-stu-id="f6f45-124">Remarks</span></span>

<span data-ttu-id="f6f45-125">Nella maggior parte dei casi, un controllo ha una sola definizione, di cui è definita in una singola `CustomEntry` elemento.</span><span class="sxs-lookup"><span data-stu-id="f6f45-125">In most cases, a control has only one definition, which is defined in a single `CustomEntry` element.</span></span> <span data-ttu-id="f6f45-126">Tuttavia è possibile avere più definizioni, se si desidera utilizzare lo stesso controllo per visualizzare diversi oggetti .NET.</span><span class="sxs-lookup"><span data-stu-id="f6f45-126">However it is possible to have multiple definitions if you want to use the same control to display different .NET objects.</span></span> <span data-ttu-id="f6f45-127">In questi casi, è possibile definire un `CustomEntry` (elemento) per ogni oggetto o un set di oggetti.</span><span class="sxs-lookup"><span data-stu-id="f6f45-127">In those cases, you can define a `CustomEntry` element for each object or set of objects.</span></span>

## <a name="see-also"></a><span data-ttu-id="f6f45-128">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="f6f45-128">See Also</span></span>

[<span data-ttu-id="f6f45-129">Elemento CustomControl per visualizzazione (formato)</span><span class="sxs-lookup"><span data-stu-id="f6f45-129">CustomControl Element for View (Format)</span></span>](./customcontrol-element-for-view-format.md)

[<span data-ttu-id="f6f45-130">Elemento CustomEntry per CustomEntries per visualizzazione (formato)</span><span class="sxs-lookup"><span data-stu-id="f6f45-130">CustomEntry Element for CustomEntries for View (Format)</span></span>](./customentry-element-for-customentries-for-customcontrol-for-view-format.md)

[<span data-ttu-id="f6f45-131">La scrittura di un File di formattazione di PowerShell</span><span class="sxs-lookup"><span data-stu-id="f6f45-131">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
