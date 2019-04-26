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
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62066669"
---
# <a name="customcontrol-element-for-view-format"></a><span data-ttu-id="87a5c-102">Elemento CustomControl per View (formato)</span><span class="sxs-lookup"><span data-stu-id="87a5c-102">CustomControl Element for View (Format)</span></span>

<span data-ttu-id="87a5c-103">Definisce un formato di controllo personalizzato per la visualizzazione.</span><span class="sxs-lookup"><span data-stu-id="87a5c-103">Defines a custom control format for the view.</span></span>

<span data-ttu-id="87a5c-104">Configurazione (formato) elemento ViewDefinitions (formato) visualizzazione elemento (formato) CustomControl elemento (formato)</span><span class="sxs-lookup"><span data-stu-id="87a5c-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) CustomControl Element (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="87a5c-105">Sintassi</span><span class="sxs-lookup"><span data-stu-id="87a5c-105">Syntax</span></span>

```xml
<CustomControl>
  <CustomEntries>...</CustomEntries>
</CustomControl>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="87a5c-106">Elementi e attributi</span><span class="sxs-lookup"><span data-stu-id="87a5c-106">Attributes and Elements</span></span>

<span data-ttu-id="87a5c-107">Le sezioni seguenti descrivono gli attributi e gli elementi figlio dell'elemento padre del `CustomControl` elemento.</span><span class="sxs-lookup"><span data-stu-id="87a5c-107">The following sections describe attributes, child elements, and the parent element of the `CustomControl` element.</span></span> <span data-ttu-id="87a5c-108">È necessario specificare un elemento figlio.</span><span class="sxs-lookup"><span data-stu-id="87a5c-108">You must specify one child element.</span></span>

### <a name="attributes"></a><span data-ttu-id="87a5c-109">Attributes</span><span class="sxs-lookup"><span data-stu-id="87a5c-109">Attributes</span></span>

<span data-ttu-id="87a5c-110">Nessuna.</span><span class="sxs-lookup"><span data-stu-id="87a5c-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="87a5c-111">Elementi figlio</span><span class="sxs-lookup"><span data-stu-id="87a5c-111">Child Elements</span></span>

|<span data-ttu-id="87a5c-112">Elemento</span><span class="sxs-lookup"><span data-stu-id="87a5c-112">Element</span></span>|<span data-ttu-id="87a5c-113">Description</span><span class="sxs-lookup"><span data-stu-id="87a5c-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="87a5c-114">Elemento CustomEntries per CustomControl per visualizzazione (formato)</span><span class="sxs-lookup"><span data-stu-id="87a5c-114">CustomEntries Element for CustomControl for View (Format)</span></span>](./customentries-element-for-customcontrol-for-view-format.md)|<span data-ttu-id="87a5c-115">Elemento obbligatorio.</span><span class="sxs-lookup"><span data-stu-id="87a5c-115">Required element.</span></span><br /><br /> <span data-ttu-id="87a5c-116">Fornisce le definizioni della vista del controllo personalizzato.</span><span class="sxs-lookup"><span data-stu-id="87a5c-116">Provides the definitions of the custom control view.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="87a5c-117">Elementi padre</span><span class="sxs-lookup"><span data-stu-id="87a5c-117">Parent Elements</span></span>

|<span data-ttu-id="87a5c-118">Elemento</span><span class="sxs-lookup"><span data-stu-id="87a5c-118">Element</span></span>|<span data-ttu-id="87a5c-119">Description</span><span class="sxs-lookup"><span data-stu-id="87a5c-119">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="87a5c-120">Elemento di visualizzazione (formato)</span><span class="sxs-lookup"><span data-stu-id="87a5c-120">View Element (Format)</span></span>](./view-element-format.md)|<span data-ttu-id="87a5c-121">Definisce una vista che consente di visualizzare uno o più oggetti .NET.</span><span class="sxs-lookup"><span data-stu-id="87a5c-121">Defines a view that is used to display one or more .NET objects.</span></span>|

## <a name="remarks"></a><span data-ttu-id="87a5c-122">Osservazioni</span><span class="sxs-lookup"><span data-stu-id="87a5c-122">Remarks</span></span>

<span data-ttu-id="87a5c-123">Nella maggior parte dei casi, una sola definizione è obbligatorio per ogni visualizzazione del controllo, ma è possibile fornire più definizioni, se si desidera utilizzare la stessa vista per visualizzare diversi oggetti .NET.</span><span class="sxs-lookup"><span data-stu-id="87a5c-123">In most cases, only one definition is required for each control view, but it is possible to provide multiple definitions if you want to use the same view to display different .NET objects.</span></span> <span data-ttu-id="87a5c-124">In questi casi, è possibile fornire una definizione separata per ogni oggetto o un set di oggetti.</span><span class="sxs-lookup"><span data-stu-id="87a5c-124">In those cases, you can provide a separate definition for each object or set of objects.</span></span>

## <a name="see-also"></a><span data-ttu-id="87a5c-125">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="87a5c-125">See Also</span></span>

[<span data-ttu-id="87a5c-126">Elemento CustomEntries per CustomControl per visualizzazione (formato)</span><span class="sxs-lookup"><span data-stu-id="87a5c-126">CustomEntries Element for CustomControl for View (Format)</span></span>](./customentries-element-for-customcontrol-for-view-format.md)

[<span data-ttu-id="87a5c-127">Elemento di visualizzazione (formato)</span><span class="sxs-lookup"><span data-stu-id="87a5c-127">View Element (Format)</span></span>](./view-element-format.md)

[<span data-ttu-id="87a5c-128">La scrittura di un File di formattazione di PowerShell</span><span class="sxs-lookup"><span data-stu-id="87a5c-128">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
