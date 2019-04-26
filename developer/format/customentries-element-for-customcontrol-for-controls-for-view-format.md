---
title: Elemento CustomEntries per CustomControl per i controlli per la visualizzazione (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 3485958a-ba87-4932-907c-a8f140c4abdb
caps.latest.revision: 8
ms.openlocfilehash: 4856aee930285781a101868bd6cb67824585bce1
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62066584"
---
# <a name="customentries-element-for-customcontrol-for-controls-for-view-format"></a><span data-ttu-id="a1905-102">Elemento CustomEntries per CustomControl per Controls per View (formato)</span><span class="sxs-lookup"><span data-stu-id="a1905-102">CustomEntries Element for CustomControl for Controls for View (Format)</span></span>

<span data-ttu-id="a1905-103">Fornisce le definizioni per il controllo.</span><span class="sxs-lookup"><span data-stu-id="a1905-103">Provides the definitions for the control.</span></span> <span data-ttu-id="a1905-104">Questo elemento viene usato quando si definiscono i controlli che possono essere usati da una vista.</span><span class="sxs-lookup"><span data-stu-id="a1905-104">This element is used when defining controls that can be used by a view.</span></span>

<span data-ttu-id="a1905-105">Elemento (formato) elemento ViewDefinitions (formato) visualizzazione elemento (formato) i controlli elemento (formato) controllo elemento di configurazione per i controlli elemento di visualizzazione (formato) CustomControl per il controllo per i controlli elemento di visualizzazione (formato) CustomEntries per CustomControl per i controlli per la visualizzazione (formato)</span><span class="sxs-lookup"><span data-stu-id="a1905-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) Controls Element (Format) Control Element for Controls for View (Format) CustomControl Element for Control for Controls for View (Format) CustomEntries Element for CustomControl for Controls for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="a1905-106">Sintassi</span><span class="sxs-lookup"><span data-stu-id="a1905-106">Syntax</span></span>

```xml
<CustomEntries>
  <CustomEntry>...</CustomEntry>
</CustomEntries>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="a1905-107">Elementi e attributi</span><span class="sxs-lookup"><span data-stu-id="a1905-107">Attributes and Elements</span></span>

<span data-ttu-id="a1905-108">Le sezioni seguenti descrivono gli attributi, elementi figlio e gli elementi padre del `CustomEntries` elemento.</span><span class="sxs-lookup"><span data-stu-id="a1905-108">The following sections describe attributes, child elements, and parent elements of the `CustomEntries` element.</span></span> <span data-ttu-id="a1905-109">Non è definito alcun limite massimo al numero di elementi figlio che possono essere specificati.</span><span class="sxs-lookup"><span data-stu-id="a1905-109">There is no maximum limit to the number of child elements that can be specified.</span></span>

### <a name="attributes"></a><span data-ttu-id="a1905-110">Attributes</span><span class="sxs-lookup"><span data-stu-id="a1905-110">Attributes</span></span>

<span data-ttu-id="a1905-111">Nessuna.</span><span class="sxs-lookup"><span data-stu-id="a1905-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="a1905-112">Elementi figlio</span><span class="sxs-lookup"><span data-stu-id="a1905-112">Child Elements</span></span>

|<span data-ttu-id="a1905-113">Elemento</span><span class="sxs-lookup"><span data-stu-id="a1905-113">Element</span></span>|<span data-ttu-id="a1905-114">Description</span><span class="sxs-lookup"><span data-stu-id="a1905-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="a1905-115">Elemento CustomEntry per CustomEntries per i controlli per la visualizzazione (formato)</span><span class="sxs-lookup"><span data-stu-id="a1905-115">CustomEntry Element for CustomEntries for Controls for View (Format)</span></span>](./customentry-element-for-customentries-for-controls-for-view-format.md)|<span data-ttu-id="a1905-116">Elemento obbligatorio.</span><span class="sxs-lookup"><span data-stu-id="a1905-116">Required element.</span></span><br /><br /> <span data-ttu-id="a1905-117">Fornisce una definizione del controllo.</span><span class="sxs-lookup"><span data-stu-id="a1905-117">Provides a definition of the control.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="a1905-118">Elementi padre</span><span class="sxs-lookup"><span data-stu-id="a1905-118">Parent Elements</span></span>

|<span data-ttu-id="a1905-119">Elemento</span><span class="sxs-lookup"><span data-stu-id="a1905-119">Element</span></span>|<span data-ttu-id="a1905-120">Description</span><span class="sxs-lookup"><span data-stu-id="a1905-120">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="a1905-121">Elemento CustomControl per il controllo per i controlli per la visualizzazione (formato)</span><span class="sxs-lookup"><span data-stu-id="a1905-121">CustomControl Element for Control for Controls for View (Format)</span></span>](./customcontrol-element-for-control-for-controls-for-view-format.md)|<span data-ttu-id="a1905-122">Definisce il controllo utilizzato dalla visualizzazione.</span><span class="sxs-lookup"><span data-stu-id="a1905-122">Defines the control used by the view.</span></span>|

## <a name="remarks"></a><span data-ttu-id="a1905-123">Osservazioni</span><span class="sxs-lookup"><span data-stu-id="a1905-123">Remarks</span></span>

<span data-ttu-id="a1905-124">Nella maggior parte dei casi, un controllo ha una sola definizione, di cui è specificata in un singolo `CustomEntry` elemento.</span><span class="sxs-lookup"><span data-stu-id="a1905-124">In most cases, a control has only one definition, which is specified in a single `CustomEntry` element.</span></span> <span data-ttu-id="a1905-125">Tuttavia, è possibile fornire più definizioni, se si desidera utilizzare lo stesso controllo per visualizzare diversi oggetti .NET.</span><span class="sxs-lookup"><span data-stu-id="a1905-125">However, it is possible to provide multiple definitions if you want to use the same control to display different .NET objects.</span></span> <span data-ttu-id="a1905-126">In questi casi, è possibile definire un `CustomEntry` (elemento) per ogni oggetto o un set di oggetti.</span><span class="sxs-lookup"><span data-stu-id="a1905-126">In those cases, you can define a `CustomEntry` element for each object or set of objects.</span></span>

## <a name="see-also"></a><span data-ttu-id="a1905-127">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="a1905-127">See Also</span></span>

[<span data-ttu-id="a1905-128">Elemento CustomEntry per CustomEntries per i controlli per la visualizzazione (formato)</span><span class="sxs-lookup"><span data-stu-id="a1905-128">CustomEntry Element for CustomEntries for Controls for View (Format)</span></span>](./customentry-element-for-customentries-for-controls-for-view-format.md)

[<span data-ttu-id="a1905-129">Elemento CustomControl per il controllo per i controlli per la visualizzazione (formato)</span><span class="sxs-lookup"><span data-stu-id="a1905-129">CustomControl Element for Control for Controls for View (Format)</span></span>](./customcontrol-element-for-control-for-controls-for-view-format.md)

[<span data-ttu-id="a1905-130">La scrittura di un File di formattazione di PowerShell</span><span class="sxs-lookup"><span data-stu-id="a1905-130">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
