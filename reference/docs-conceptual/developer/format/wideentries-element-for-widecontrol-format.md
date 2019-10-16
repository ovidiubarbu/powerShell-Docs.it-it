---
title: Elemento WideEntries per WideControl (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 0c4bff45-0960-4b3a-95e7-47f2cee03ac5
caps.latest.revision: 12
ms.openlocfilehash: 083f3c8df8136858e32778ed231943ef983e47aa
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/15/2019
ms.locfileid: "72361430"
---
# <a name="wideentries-element-for-widecontrol-format"></a><span data-ttu-id="3f0b0-102">Elemento WideEntries per WideControl (formato)</span><span class="sxs-lookup"><span data-stu-id="3f0b0-102">WideEntries Element for WideControl (Format)</span></span>

<span data-ttu-id="3f0b0-103">Fornisce le definizioni della visualizzazione estesa.</span><span class="sxs-lookup"><span data-stu-id="3f0b0-103">Provides the definitions of the wide view.</span></span> <span data-ttu-id="3f0b0-104">La visualizzazione estesa deve specificare una o più definizioni.</span><span class="sxs-lookup"><span data-stu-id="3f0b0-104">The wide view must specify one or more definitions.</span></span>

<span data-ttu-id="3f0b0-105">Elemento Configuration (Format) elemento ViewDefinitions (Format) elemento View (Format) elemento WideControl (Format) elemento WideEntries (Format)</span><span class="sxs-lookup"><span data-stu-id="3f0b0-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) WideControl Element (Format) WideEntries Element (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="3f0b0-106">Sintassi</span><span class="sxs-lookup"><span data-stu-id="3f0b0-106">Syntax</span></span>

```xml
<WideEntries>
  <WideEntry>...</WideEntry>
</WideEntries>

```

## <a name="attributes-and-elements"></a><span data-ttu-id="3f0b0-107">Attributi ed elementi</span><span class="sxs-lookup"><span data-stu-id="3f0b0-107">Attributes and Elements</span></span>

<span data-ttu-id="3f0b0-108">Nelle sezioni seguenti vengono descritti gli attributi, gli elementi figlio e l'elemento padre dell'elemento `WideEntries`.</span><span class="sxs-lookup"><span data-stu-id="3f0b0-108">The following sections describe the attributes, child elements, and parent element of the `WideEntries` element.</span></span> <span data-ttu-id="3f0b0-109">È necessario specificare almeno un elemento figlio.</span><span class="sxs-lookup"><span data-stu-id="3f0b0-109">At least one child element must be specified.</span></span>

### <a name="attributes"></a><span data-ttu-id="3f0b0-110">Attributi</span><span class="sxs-lookup"><span data-stu-id="3f0b0-110">Attributes</span></span>

<span data-ttu-id="3f0b0-111">Nessuna.</span><span class="sxs-lookup"><span data-stu-id="3f0b0-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="3f0b0-112">Elementi figlio</span><span class="sxs-lookup"><span data-stu-id="3f0b0-112">Child Elements</span></span>

|<span data-ttu-id="3f0b0-113">Elemento</span><span class="sxs-lookup"><span data-stu-id="3f0b0-113">Element</span></span>|<span data-ttu-id="3f0b0-114">Description</span><span class="sxs-lookup"><span data-stu-id="3f0b0-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="3f0b0-115">Elemento WideEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="3f0b0-115">WideEntry Element (Format)</span></span>](./wideentry-element-for-widecontrol-format.md)|<span data-ttu-id="3f0b0-116">Fornisce una definizione dell'ampia visualizzazione.</span><span class="sxs-lookup"><span data-stu-id="3f0b0-116">Provides a definition of the wide view.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="3f0b0-117">Elementi padre</span><span class="sxs-lookup"><span data-stu-id="3f0b0-117">Parent Elements</span></span>

|<span data-ttu-id="3f0b0-118">Elemento</span><span class="sxs-lookup"><span data-stu-id="3f0b0-118">Element</span></span>|<span data-ttu-id="3f0b0-119">Description</span><span class="sxs-lookup"><span data-stu-id="3f0b0-119">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="3f0b0-120">Elemento WideControl (Format)</span><span class="sxs-lookup"><span data-stu-id="3f0b0-120">WideControl Element (Format)</span></span>](./widecontrol-element-format.md)|<span data-ttu-id="3f0b0-121">Definisce un formato di elenco Wide (valore singolo) per la visualizzazione.</span><span class="sxs-lookup"><span data-stu-id="3f0b0-121">Defines a wide (single value) list format for the view.</span></span>|

## <a name="remarks"></a><span data-ttu-id="3f0b0-122">Osservazioni</span><span class="sxs-lookup"><span data-stu-id="3f0b0-122">Remarks</span></span>

<span data-ttu-id="3f0b0-123">Una visualizzazione estesa è un formato di elenco che consente di visualizzare un singolo valore di proprietà o un valore di script per ogni oggetto.</span><span class="sxs-lookup"><span data-stu-id="3f0b0-123">A wide view is a list format that displays a single property value or script value for each object.</span></span> <span data-ttu-id="3f0b0-124">Per ulteriori informazioni sui componenti di una visualizzazione estesa, vedere [componenti di visualizzazione ampia](./creating-a-wide-view.md).</span><span class="sxs-lookup"><span data-stu-id="3f0b0-124">For more information about the components of a wide view, see [Wide View Components](./creating-a-wide-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="3f0b0-125">Esempio</span><span class="sxs-lookup"><span data-stu-id="3f0b0-125">Example</span></span>

<span data-ttu-id="3f0b0-126">Nell'esempio seguente viene illustrato un elemento `WideEntries` che definisce un singolo elemento `WideEntry`.</span><span class="sxs-lookup"><span data-stu-id="3f0b0-126">The following example shows a `WideEntries` element that defines a single `WideEntry` element.</span></span> <span data-ttu-id="3f0b0-127">L'elemento `WideEntry` contiene un singolo elemento `WideItem` che definisce la proprietà o il valore dello script visualizzato nella visualizzazione.</span><span class="sxs-lookup"><span data-stu-id="3f0b0-127">The `WideEntry` element contains a single `WideItem` element that defines what property or script value is displayed in the view.</span></span>

```xml
<WideControl>
  <WideEntries>
    <WideEntry>
      <WideItem>...</WideItem>
    <WideEntry>
  </WideEntries>
</WideControl>
```

<span data-ttu-id="3f0b0-128">Per un esempio completo di una visualizzazione estesa, vedere [Wide View (Basic)](./wide-view-basic.md).</span><span class="sxs-lookup"><span data-stu-id="3f0b0-128">For a complete example of a wide view, see [Wide View (Basic)](./wide-view-basic.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="3f0b0-129">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="3f0b0-129">See Also</span></span>

[<span data-ttu-id="3f0b0-130">Creazione di una visualizzazione estesa</span><span class="sxs-lookup"><span data-stu-id="3f0b0-130">Creating a Wide View</span></span>](./creating-a-wide-view.md)

[<span data-ttu-id="3f0b0-131">Elemento WideControl (Format)</span><span class="sxs-lookup"><span data-stu-id="3f0b0-131">WideControl Element (Format)</span></span>](./widecontrol-element-format.md)

[<span data-ttu-id="3f0b0-132">Elemento WideEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="3f0b0-132">WideEntry Element (Format)</span></span>](./wideentry-element-for-widecontrol-format.md)

[<span data-ttu-id="3f0b0-133">Scrittura di un file di formattazione di PowerShell</span><span class="sxs-lookup"><span data-stu-id="3f0b0-133">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
