---
title: Elemento CustomEntries per CustomControl per i controlli per la visualizzazione (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 3485958a-ba87-4932-907c-a8f140c4abdb
caps.latest.revision: 8
ms.openlocfilehash: 4856aee930285781a101868bd6cb67824585bce1
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/15/2019
ms.locfileid: "72368810"
---
# <a name="customentries-element-for-customcontrol-for-controls-for-view-format"></a><span data-ttu-id="955be-102">Elemento CustomEntries per CustomControl per Controls per View (formato)</span><span class="sxs-lookup"><span data-stu-id="955be-102">CustomEntries Element for CustomControl for Controls for View (Format)</span></span>

<span data-ttu-id="955be-103">Fornisce le definizioni per il controllo.</span><span class="sxs-lookup"><span data-stu-id="955be-103">Provides the definitions for the control.</span></span> <span data-ttu-id="955be-104">Questo elemento viene utilizzato per la definizione di controlli che possono essere utilizzati da una visualizzazione.</span><span class="sxs-lookup"><span data-stu-id="955be-104">This element is used when defining controls that can be used by a view.</span></span>

<span data-ttu-id="955be-105">Elemento di configurazione (Format) elemento ViewDefinitions (Format) elemento di visualizzazione (Format) controlli elemento (Format) elemento di controllo per i controlli per la visualizzazione (formato) elemento CustomControl per il controllo per i controlli per la visualizzazione (formato) elemento CustomEntries per CustomControl per i controlli per la visualizzazione (formato)</span><span class="sxs-lookup"><span data-stu-id="955be-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) Controls Element (Format) Control Element for Controls for View (Format) CustomControl Element for Control for Controls for View (Format) CustomEntries Element for CustomControl for Controls for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="955be-106">Sintassi</span><span class="sxs-lookup"><span data-stu-id="955be-106">Syntax</span></span>

```xml
<CustomEntries>
  <CustomEntry>...</CustomEntry>
</CustomEntries>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="955be-107">Attributi ed elementi</span><span class="sxs-lookup"><span data-stu-id="955be-107">Attributes and Elements</span></span>

<span data-ttu-id="955be-108">Nelle sezioni seguenti vengono descritti gli attributi, gli elementi figlio e gli elementi padre dell'elemento `CustomEntries`.</span><span class="sxs-lookup"><span data-stu-id="955be-108">The following sections describe attributes, child elements, and parent elements of the `CustomEntries` element.</span></span> <span data-ttu-id="955be-109">Non esiste un limite massimo per il numero di elementi figlio che è possibile specificare.</span><span class="sxs-lookup"><span data-stu-id="955be-109">There is no maximum limit to the number of child elements that can be specified.</span></span>

### <a name="attributes"></a><span data-ttu-id="955be-110">Attributi</span><span class="sxs-lookup"><span data-stu-id="955be-110">Attributes</span></span>

<span data-ttu-id="955be-111">Nessuna.</span><span class="sxs-lookup"><span data-stu-id="955be-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="955be-112">Elementi figlio</span><span class="sxs-lookup"><span data-stu-id="955be-112">Child Elements</span></span>

|<span data-ttu-id="955be-113">Elemento</span><span class="sxs-lookup"><span data-stu-id="955be-113">Element</span></span>|<span data-ttu-id="955be-114">Description</span><span class="sxs-lookup"><span data-stu-id="955be-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="955be-115">Elemento CustomEntry per CustomEntries per i controlli per la visualizzazione (Format)</span><span class="sxs-lookup"><span data-stu-id="955be-115">CustomEntry Element for CustomEntries for Controls for View (Format)</span></span>](./customentry-element-for-customentries-for-controls-for-view-format.md)|<span data-ttu-id="955be-116">Elemento obbligatorio.</span><span class="sxs-lookup"><span data-stu-id="955be-116">Required element.</span></span><br /><br /> <span data-ttu-id="955be-117">Fornisce una definizione del controllo.</span><span class="sxs-lookup"><span data-stu-id="955be-117">Provides a definition of the control.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="955be-118">Elementi padre</span><span class="sxs-lookup"><span data-stu-id="955be-118">Parent Elements</span></span>

|<span data-ttu-id="955be-119">Elemento</span><span class="sxs-lookup"><span data-stu-id="955be-119">Element</span></span>|<span data-ttu-id="955be-120">Description</span><span class="sxs-lookup"><span data-stu-id="955be-120">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="955be-121">Elemento CustomControl per il controllo per i controlli per la visualizzazione (Format)</span><span class="sxs-lookup"><span data-stu-id="955be-121">CustomControl Element for Control for Controls for View (Format)</span></span>](./customcontrol-element-for-control-for-controls-for-view-format.md)|<span data-ttu-id="955be-122">Definisce il controllo utilizzato dalla visualizzazione.</span><span class="sxs-lookup"><span data-stu-id="955be-122">Defines the control used by the view.</span></span>|

## <a name="remarks"></a><span data-ttu-id="955be-123">Osservazioni</span><span class="sxs-lookup"><span data-stu-id="955be-123">Remarks</span></span>

<span data-ttu-id="955be-124">Nella maggior parte dei casi, un controllo ha una sola definizione, specificata in un singolo elemento `CustomEntry`.</span><span class="sxs-lookup"><span data-stu-id="955be-124">In most cases, a control has only one definition, which is specified in a single `CustomEntry` element.</span></span> <span data-ttu-id="955be-125">Tuttavia, se si desidera utilizzare lo stesso controllo per visualizzare oggetti .NET diversi, è possibile specificare più definizioni.</span><span class="sxs-lookup"><span data-stu-id="955be-125">However, it is possible to provide multiple definitions if you want to use the same control to display different .NET objects.</span></span> <span data-ttu-id="955be-126">In questi casi, è possibile definire un elemento `CustomEntry` per ogni oggetto o set di oggetti.</span><span class="sxs-lookup"><span data-stu-id="955be-126">In those cases, you can define a `CustomEntry` element for each object or set of objects.</span></span>

## <a name="see-also"></a><span data-ttu-id="955be-127">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="955be-127">See Also</span></span>

[<span data-ttu-id="955be-128">Elemento CustomEntry per CustomEntries per i controlli per la visualizzazione (Format)</span><span class="sxs-lookup"><span data-stu-id="955be-128">CustomEntry Element for CustomEntries for Controls for View (Format)</span></span>](./customentry-element-for-customentries-for-controls-for-view-format.md)

[<span data-ttu-id="955be-129">Elemento CustomControl per il controllo per i controlli per la visualizzazione (Format)</span><span class="sxs-lookup"><span data-stu-id="955be-129">CustomControl Element for Control for Controls for View (Format)</span></span>](./customcontrol-element-for-control-for-controls-for-view-format.md)

[<span data-ttu-id="955be-130">Scrittura di un file di formattazione di PowerShell</span><span class="sxs-lookup"><span data-stu-id="955be-130">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
