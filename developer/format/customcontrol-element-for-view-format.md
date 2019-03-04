---
title: Elemento CustomControl per visualizzazione (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 2edac16c-0b30-4985-ac84-0821aa9a9f6d
caps.latest.revision: 12
ms.openlocfilehash: bd0f7ca4de8dede97d1553cd62884ea45876e0c7
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/03/2019
ms.locfileid: "56861257"
---
# <a name="customcontrol-element-for-view-format"></a><span data-ttu-id="ef0ba-102">Elemento CustomControl per View (formato)</span><span class="sxs-lookup"><span data-stu-id="ef0ba-102">CustomControl Element for View (Format)</span></span>

<span data-ttu-id="ef0ba-103">Definisce un formato di controllo personalizzato per la visualizzazione.</span><span class="sxs-lookup"><span data-stu-id="ef0ba-103">Defines a custom control format for the view.</span></span>

<span data-ttu-id="ef0ba-104">Configurazione (formato) elemento ViewDefinitions (formato) visualizzazione elemento (formato) CustomControl elemento (formato)</span><span class="sxs-lookup"><span data-stu-id="ef0ba-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) CustomControl Element (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="ef0ba-105">Sintassi</span><span class="sxs-lookup"><span data-stu-id="ef0ba-105">Syntax</span></span>

```xml
<CustomControl>
  <CustomEntries>...</CustomEntries>
</CustomControl>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="ef0ba-106">Attributi ed elementi</span><span class="sxs-lookup"><span data-stu-id="ef0ba-106">Attributes and Elements</span></span>

<span data-ttu-id="ef0ba-107">Le sezioni seguenti descrivono gli attributi e gli elementi figlio dell'elemento padre del `CustomControl` elemento.</span><span class="sxs-lookup"><span data-stu-id="ef0ba-107">The following sections describe attributes, child elements, and the parent element of the `CustomControl` element.</span></span> <span data-ttu-id="ef0ba-108">È necessario specificare un elemento figlio.</span><span class="sxs-lookup"><span data-stu-id="ef0ba-108">You must specify one child element.</span></span>

### <a name="attributes"></a><span data-ttu-id="ef0ba-109">Attributes</span><span class="sxs-lookup"><span data-stu-id="ef0ba-109">Attributes</span></span>

<span data-ttu-id="ef0ba-110">Nessuna.</span><span class="sxs-lookup"><span data-stu-id="ef0ba-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="ef0ba-111">Elementi figlio</span><span class="sxs-lookup"><span data-stu-id="ef0ba-111">Child Elements</span></span>

|<span data-ttu-id="ef0ba-112">Elemento</span><span class="sxs-lookup"><span data-stu-id="ef0ba-112">Element</span></span>|<span data-ttu-id="ef0ba-113">Description</span><span class="sxs-lookup"><span data-stu-id="ef0ba-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="ef0ba-114">Elemento CustomEntries per CustomControl per visualizzazione (formato)</span><span class="sxs-lookup"><span data-stu-id="ef0ba-114">CustomEntries Element for CustomControl for View (Format)</span></span>](./customentries-element-for-customcontrol-for-view-format.md)|<span data-ttu-id="ef0ba-115">Elemento obbligatorio.</span><span class="sxs-lookup"><span data-stu-id="ef0ba-115">Required element.</span></span><br /><br /> <span data-ttu-id="ef0ba-116">Fornisce le definizioni della vista del controllo personalizzato.</span><span class="sxs-lookup"><span data-stu-id="ef0ba-116">Provides the definitions of the custom control view.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="ef0ba-117">Elementi padre</span><span class="sxs-lookup"><span data-stu-id="ef0ba-117">Parent Elements</span></span>

|<span data-ttu-id="ef0ba-118">Elemento</span><span class="sxs-lookup"><span data-stu-id="ef0ba-118">Element</span></span>|<span data-ttu-id="ef0ba-119">Description</span><span class="sxs-lookup"><span data-stu-id="ef0ba-119">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="ef0ba-120">Elemento di visualizzazione (formato)</span><span class="sxs-lookup"><span data-stu-id="ef0ba-120">View Element (Format)</span></span>](./view-element-format.md)|<span data-ttu-id="ef0ba-121">Definisce una vista che consente di visualizzare uno o più oggetti .NET.</span><span class="sxs-lookup"><span data-stu-id="ef0ba-121">Defines a view that is used to display one or more .NET objects.</span></span>|

## <a name="remarks"></a><span data-ttu-id="ef0ba-122">Osservazioni</span><span class="sxs-lookup"><span data-stu-id="ef0ba-122">Remarks</span></span>

<span data-ttu-id="ef0ba-123">Nella maggior parte dei casi, una sola definizione è obbligatorio per ogni visualizzazione del controllo, ma è possibile fornire più definizioni, se si desidera utilizzare la stessa vista per visualizzare diversi oggetti .NET.</span><span class="sxs-lookup"><span data-stu-id="ef0ba-123">In most cases, only one definition is required for each control view, but it is possible to provide multiple definitions if you want to use the same view to display different .NET objects.</span></span> <span data-ttu-id="ef0ba-124">In questi casi, è possibile fornire una definizione separata per ogni oggetto o un set di oggetti.</span><span class="sxs-lookup"><span data-stu-id="ef0ba-124">In those cases, you can provide a separate definition for each object or set of objects.</span></span>

## <a name="see-also"></a><span data-ttu-id="ef0ba-125">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="ef0ba-125">See Also</span></span>

[<span data-ttu-id="ef0ba-126">Elemento CustomEntries per CustomControl per visualizzazione (formato)</span><span class="sxs-lookup"><span data-stu-id="ef0ba-126">CustomEntries Element for CustomControl for View (Format)</span></span>](./customentries-element-for-customcontrol-for-view-format.md)

[<span data-ttu-id="ef0ba-127">Elemento di visualizzazione (formato)</span><span class="sxs-lookup"><span data-stu-id="ef0ba-127">View Element (Format)</span></span>](./view-element-format.md)

[<span data-ttu-id="ef0ba-128">La scrittura di un File di formattazione di PowerShell</span><span class="sxs-lookup"><span data-stu-id="ef0ba-128">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
