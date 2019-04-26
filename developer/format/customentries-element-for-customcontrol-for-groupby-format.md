---
title: Elemento CustomEntries per CustomControl per GroupBy (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: af83c0f6-7fdd-4aa0-af12-efc62f632974
caps.latest.revision: 7
ms.openlocfilehash: f073142bf836ae892f161cf8c36ed16c35e311f5
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62066541"
---
# <a name="customentries-element-for-customcontrol-for-groupby-format"></a><span data-ttu-id="21676-102">Elemento CustomEntries per CustomControl per GroupBy (formato)</span><span class="sxs-lookup"><span data-stu-id="21676-102">CustomEntries Element for CustomControl for GroupBy (Format)</span></span>

<span data-ttu-id="21676-103">Fornisce le definizioni per il controllo.</span><span class="sxs-lookup"><span data-stu-id="21676-103">Provides the definitions for the control.</span></span> <span data-ttu-id="21676-104">Questo elemento viene usato quando si definisce come viene visualizzato un nuovo gruppo di oggetti.</span><span class="sxs-lookup"><span data-stu-id="21676-104">This element is used when defining how a new group of objects is displayed.</span></span>

<span data-ttu-id="21676-105">Elemento di GroupBy elemento (formato) per la visualizzazione elemento ViewDefinitions (formato) configurazione elemento (formato) per la visualizzazione (formato) CustomControl elemento per elemento CustomEntries GroupBy (formato) per CustomControl per GroupBy (formato)</span><span class="sxs-lookup"><span data-stu-id="21676-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) GroupBy Element for View (Format) CustomControl Element for GroupBy (Format) CustomEntries Element for CustomControl for GroupBy (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="21676-106">Sintassi</span><span class="sxs-lookup"><span data-stu-id="21676-106">Syntax</span></span>

```xml
<CustomEntries>
  <CustomEntry>...</CustomEntry>
</CustomEntries>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="21676-107">Elementi e attributi</span><span class="sxs-lookup"><span data-stu-id="21676-107">Attributes and Elements</span></span>

<span data-ttu-id="21676-108">Le sezioni seguenti descrivono gli attributi, elementi figlio e gli elementi padre del `CustomEntries` elemento.</span><span class="sxs-lookup"><span data-stu-id="21676-108">The following sections describe attributes, child elements, and parent elements of the `CustomEntries` element.</span></span> <span data-ttu-id="21676-109">Non è definito alcun limite massimo al numero di elementi figlio che possono essere specificati.</span><span class="sxs-lookup"><span data-stu-id="21676-109">There is no maximum limit to the number of child elements that can be specified.</span></span>

### <a name="attributes"></a><span data-ttu-id="21676-110">Attributes</span><span class="sxs-lookup"><span data-stu-id="21676-110">Attributes</span></span>

<span data-ttu-id="21676-111">Nessuna.</span><span class="sxs-lookup"><span data-stu-id="21676-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="21676-112">Elementi figlio</span><span class="sxs-lookup"><span data-stu-id="21676-112">Child Elements</span></span>

|<span data-ttu-id="21676-113">Elemento</span><span class="sxs-lookup"><span data-stu-id="21676-113">Element</span></span>|<span data-ttu-id="21676-114">Description</span><span class="sxs-lookup"><span data-stu-id="21676-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="21676-115">Elemento CustomEntry per CustomControl per GroupBy (formato)</span><span class="sxs-lookup"><span data-stu-id="21676-115">CustomEntry Element for CustomControl for GroupBy (Format)</span></span>](./customentry-element-for-customcontrol-for-groupby-format.md)|<span data-ttu-id="21676-116">Elemento obbligatorio.</span><span class="sxs-lookup"><span data-stu-id="21676-116">Required element.</span></span><br /><br /> <span data-ttu-id="21676-117">Fornisce una definizione del controllo.</span><span class="sxs-lookup"><span data-stu-id="21676-117">Provides a definition of the control.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="21676-118">Elementi padre</span><span class="sxs-lookup"><span data-stu-id="21676-118">Parent Elements</span></span>

|<span data-ttu-id="21676-119">Elemento</span><span class="sxs-lookup"><span data-stu-id="21676-119">Element</span></span>|<span data-ttu-id="21676-120">Description</span><span class="sxs-lookup"><span data-stu-id="21676-120">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="21676-121">Elemento CustomControl per GroupBy (formato)</span><span class="sxs-lookup"><span data-stu-id="21676-121">CustomControl Element for GroupBy (Format)</span></span>](./customcontrol-element-for-groupby-format.md)|<span data-ttu-id="21676-122">Definisce il controllo personalizzato che consente di visualizzare il nuovo gruppo.</span><span class="sxs-lookup"><span data-stu-id="21676-122">Defines the custom control that displays the new group.</span></span>|

## <a name="remarks"></a><span data-ttu-id="21676-123">Osservazioni</span><span class="sxs-lookup"><span data-stu-id="21676-123">Remarks</span></span>

<span data-ttu-id="21676-124">Nella maggior parte dei casi, un controllo ha una sola definizione, di cui è specificata in un singolo `CustomEntry` elemento.</span><span class="sxs-lookup"><span data-stu-id="21676-124">In most cases, a control has only one definition, which is specified in a single `CustomEntry` element.</span></span> <span data-ttu-id="21676-125">Tuttavia, è possibile fornire più definizioni, se si desidera utilizzare lo stesso controllo per visualizzare gruppi diversi.</span><span class="sxs-lookup"><span data-stu-id="21676-125">However, it is possible to provide multiple definitions if you want to use the same control to display different groups.</span></span> <span data-ttu-id="21676-126">In questi casi, è possibile definire un `CustomEntry` (elemento) per un gruppo.</span><span class="sxs-lookup"><span data-stu-id="21676-126">In those cases, you can define a `CustomEntry` element for a group.</span></span>

## <a name="see-also"></a><span data-ttu-id="21676-127">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="21676-127">See Also</span></span>

[<span data-ttu-id="21676-128">Elemento CustomEntry per CustomEntries per i controlli per la visualizzazione (formato)</span><span class="sxs-lookup"><span data-stu-id="21676-128">CustomEntry Element for CustomEntries for Controls for View (Format)</span></span>](./customentry-element-for-customentries-for-controls-for-view-format.md)

[<span data-ttu-id="21676-129">Elemento CustomControl per GroupBy (formato)</span><span class="sxs-lookup"><span data-stu-id="21676-129">CustomControl Element for GroupBy (Format)</span></span>](./customcontrol-element-for-groupby-format.md)

[<span data-ttu-id="21676-130">La scrittura di un File di formattazione di PowerShell</span><span class="sxs-lookup"><span data-stu-id="21676-130">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
