---
title: Elemento CustomControl per View (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 2edac16c-0b30-4985-ac84-0821aa9a9f6d
caps.latest.revision: 12
ms.openlocfilehash: bd0f7ca4de8dede97d1553cd62884ea45876e0c7
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/05/2019
ms.locfileid: "72363360"
---
# <a name="customcontrol-element-for-view-format"></a><span data-ttu-id="c33fc-102">Elemento CustomControl per View (formato)</span><span class="sxs-lookup"><span data-stu-id="c33fc-102">CustomControl Element for View (Format)</span></span>

<span data-ttu-id="c33fc-103">Definisce un formato di controllo personalizzato per la visualizzazione.</span><span class="sxs-lookup"><span data-stu-id="c33fc-103">Defines a custom control format for the view.</span></span>

<span data-ttu-id="c33fc-104">Elemento Configuration (Format) elemento ViewDefinitions (Format) elemento View (Format) elemento CustomControl (Format)</span><span class="sxs-lookup"><span data-stu-id="c33fc-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) CustomControl Element (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="c33fc-105">Sintassi</span><span class="sxs-lookup"><span data-stu-id="c33fc-105">Syntax</span></span>

```xml
<CustomControl>
  <CustomEntries>...</CustomEntries>
</CustomControl>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="c33fc-106">Attributi ed elementi</span><span class="sxs-lookup"><span data-stu-id="c33fc-106">Attributes and Elements</span></span>

<span data-ttu-id="c33fc-107">Nelle sezioni seguenti vengono descritti gli attributi, gli elementi figlio e l'elemento padre dell'elemento `CustomControl`.</span><span class="sxs-lookup"><span data-stu-id="c33fc-107">The following sections describe attributes, child elements, and the parent element of the `CustomControl` element.</span></span> <span data-ttu-id="c33fc-108">È necessario specificare un elemento figlio.</span><span class="sxs-lookup"><span data-stu-id="c33fc-108">You must specify one child element.</span></span>

### <a name="attributes"></a><span data-ttu-id="c33fc-109">Attributi</span><span class="sxs-lookup"><span data-stu-id="c33fc-109">Attributes</span></span>

<span data-ttu-id="c33fc-110">Nessuna.</span><span class="sxs-lookup"><span data-stu-id="c33fc-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="c33fc-111">Elementi figlio</span><span class="sxs-lookup"><span data-stu-id="c33fc-111">Child Elements</span></span>

|<span data-ttu-id="c33fc-112">Elemento</span><span class="sxs-lookup"><span data-stu-id="c33fc-112">Element</span></span>|<span data-ttu-id="c33fc-113">Description</span><span class="sxs-lookup"><span data-stu-id="c33fc-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="c33fc-114">Elemento CustomEntries per CustomControl per View (Format)</span><span class="sxs-lookup"><span data-stu-id="c33fc-114">CustomEntries Element for CustomControl for View (Format)</span></span>](./customentries-element-for-customcontrol-for-view-format.md)|<span data-ttu-id="c33fc-115">Elemento obbligatorio.</span><span class="sxs-lookup"><span data-stu-id="c33fc-115">Required element.</span></span><br /><br /> <span data-ttu-id="c33fc-116">Fornisce le definizioni della visualizzazione controlli personalizzata.</span><span class="sxs-lookup"><span data-stu-id="c33fc-116">Provides the definitions of the custom control view.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="c33fc-117">Elementi padre</span><span class="sxs-lookup"><span data-stu-id="c33fc-117">Parent Elements</span></span>

|<span data-ttu-id="c33fc-118">Elemento</span><span class="sxs-lookup"><span data-stu-id="c33fc-118">Element</span></span>|<span data-ttu-id="c33fc-119">Description</span><span class="sxs-lookup"><span data-stu-id="c33fc-119">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="c33fc-120">Elemento View (Format)</span><span class="sxs-lookup"><span data-stu-id="c33fc-120">View Element (Format)</span></span>](./view-element-format.md)|<span data-ttu-id="c33fc-121">Definisce una vista utilizzata per visualizzare uno o più oggetti .NET.</span><span class="sxs-lookup"><span data-stu-id="c33fc-121">Defines a view that is used to display one or more .NET objects.</span></span>|

## <a name="remarks"></a><span data-ttu-id="c33fc-122">Osservazioni</span><span class="sxs-lookup"><span data-stu-id="c33fc-122">Remarks</span></span>

<span data-ttu-id="c33fc-123">Nella maggior parte dei casi, è necessaria una sola definizione per ogni visualizzazione controlli, ma è possibile specificare più definizioni se si desidera utilizzare la stessa visualizzazione per visualizzare oggetti .NET diversi.</span><span class="sxs-lookup"><span data-stu-id="c33fc-123">In most cases, only one definition is required for each control view, but it is possible to provide multiple definitions if you want to use the same view to display different .NET objects.</span></span> <span data-ttu-id="c33fc-124">In questi casi, è possibile specificare una definizione separata per ogni oggetto o set di oggetti.</span><span class="sxs-lookup"><span data-stu-id="c33fc-124">In those cases, you can provide a separate definition for each object or set of objects.</span></span>

## <a name="see-also"></a><span data-ttu-id="c33fc-125">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="c33fc-125">See Also</span></span>

[<span data-ttu-id="c33fc-126">Elemento CustomEntries per CustomControl per View (Format)</span><span class="sxs-lookup"><span data-stu-id="c33fc-126">CustomEntries Element for CustomControl for View (Format)</span></span>](./customentries-element-for-customcontrol-for-view-format.md)

[<span data-ttu-id="c33fc-127">Elemento View (Format)</span><span class="sxs-lookup"><span data-stu-id="c33fc-127">View Element (Format)</span></span>](./view-element-format.md)

[<span data-ttu-id="c33fc-128">Scrittura di un file di formattazione di PowerShell</span><span class="sxs-lookup"><span data-stu-id="c33fc-128">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
