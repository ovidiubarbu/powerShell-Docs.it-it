---
title: Elemento WideEntries per WideControl (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 0c4bff45-0960-4b3a-95e7-47f2cee03ac5
caps.latest.revision: 12
ms.openlocfilehash: 083f3c8df8136858e32778ed231943ef983e47aa
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62083689"
---
# <a name="wideentries-element-for-widecontrol-format"></a><span data-ttu-id="f71fa-102">Elemento WideEntries per WideControl (formato)</span><span class="sxs-lookup"><span data-stu-id="f71fa-102">WideEntries Element for WideControl (Format)</span></span>

<span data-ttu-id="f71fa-103">Fornisce le definizioni di visualizzazione estesa.</span><span class="sxs-lookup"><span data-stu-id="f71fa-103">Provides the definitions of the wide view.</span></span> <span data-ttu-id="f71fa-104">La visualizzazione più ampia è necessario specificare una o più definizioni.</span><span class="sxs-lookup"><span data-stu-id="f71fa-104">The wide view must specify one or more definitions.</span></span>

<span data-ttu-id="f71fa-105">Elemento (formato) elemento ViewDefinitions (formato) visualizzazione elemento (formato) elemento WideControl (formato) WideEntries elemento di configurazione (formato)</span><span class="sxs-lookup"><span data-stu-id="f71fa-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) WideControl Element (Format) WideEntries Element (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="f71fa-106">Sintassi</span><span class="sxs-lookup"><span data-stu-id="f71fa-106">Syntax</span></span>

```xml
<WideEntries>
  <WideEntry>...</WideEntry>
</WideEntries>

```

## <a name="attributes-and-elements"></a><span data-ttu-id="f71fa-107">Elementi e attributi</span><span class="sxs-lookup"><span data-stu-id="f71fa-107">Attributes and Elements</span></span>

<span data-ttu-id="f71fa-108">Le sezioni seguenti descrivono gli attributi, elementi figlio ed elemento padre dell'elemento di `WideEntries` elemento.</span><span class="sxs-lookup"><span data-stu-id="f71fa-108">The following sections describe the attributes, child elements, and parent element of the `WideEntries` element.</span></span> <span data-ttu-id="f71fa-109">È necessario specificare almeno un elemento figlio.</span><span class="sxs-lookup"><span data-stu-id="f71fa-109">At least one child element must be specified.</span></span>

### <a name="attributes"></a><span data-ttu-id="f71fa-110">Attributes</span><span class="sxs-lookup"><span data-stu-id="f71fa-110">Attributes</span></span>

<span data-ttu-id="f71fa-111">Nessuna.</span><span class="sxs-lookup"><span data-stu-id="f71fa-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="f71fa-112">Elementi figlio</span><span class="sxs-lookup"><span data-stu-id="f71fa-112">Child Elements</span></span>

|<span data-ttu-id="f71fa-113">Elemento</span><span class="sxs-lookup"><span data-stu-id="f71fa-113">Element</span></span>|<span data-ttu-id="f71fa-114">Description</span><span class="sxs-lookup"><span data-stu-id="f71fa-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="f71fa-115">Elemento WideEntry (formato)</span><span class="sxs-lookup"><span data-stu-id="f71fa-115">WideEntry Element (Format)</span></span>](./wideentry-element-for-widecontrol-format.md)|<span data-ttu-id="f71fa-116">Fornisce una definizione della vista wide.</span><span class="sxs-lookup"><span data-stu-id="f71fa-116">Provides a definition of the wide view.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="f71fa-117">Elementi padre</span><span class="sxs-lookup"><span data-stu-id="f71fa-117">Parent Elements</span></span>

|<span data-ttu-id="f71fa-118">Elemento</span><span class="sxs-lookup"><span data-stu-id="f71fa-118">Element</span></span>|<span data-ttu-id="f71fa-119">Description</span><span class="sxs-lookup"><span data-stu-id="f71fa-119">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="f71fa-120">Elemento WideControl (formato)</span><span class="sxs-lookup"><span data-stu-id="f71fa-120">WideControl Element (Format)</span></span>](./widecontrol-element-format.md)|<span data-ttu-id="f71fa-121">Definisce un'ampia (valore singolo) formato di elenco per la visualizzazione.</span><span class="sxs-lookup"><span data-stu-id="f71fa-121">Defines a wide (single value) list format for the view.</span></span>|

## <a name="remarks"></a><span data-ttu-id="f71fa-122">Osservazioni</span><span class="sxs-lookup"><span data-stu-id="f71fa-122">Remarks</span></span>

<span data-ttu-id="f71fa-123">Una visualizzazione più ampia è un formato di elenco che viene visualizzato un singolo valore di proprietà o script per ogni oggetto.</span><span class="sxs-lookup"><span data-stu-id="f71fa-123">A wide view is a list format that displays a single property value or script value for each object.</span></span> <span data-ttu-id="f71fa-124">Per altre informazioni sui componenti di una visualizzazione più ampia, vedere [ampia i componenti di visualizzazione](./creating-a-wide-view.md).</span><span class="sxs-lookup"><span data-stu-id="f71fa-124">For more information about the components of a wide view, see [Wide View Components](./creating-a-wide-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="f71fa-125">Esempio</span><span class="sxs-lookup"><span data-stu-id="f71fa-125">Example</span></span>

<span data-ttu-id="f71fa-126">L'esempio seguente mostra una `WideEntries` che definisce un singolo elemento `WideEntry` elemento.</span><span class="sxs-lookup"><span data-stu-id="f71fa-126">The following example shows a `WideEntries` element that defines a single `WideEntry` element.</span></span> <span data-ttu-id="f71fa-127">Il `WideEntry` elemento contiene un singolo `WideItem` elemento che definisce il valore di proprietà o lo script viene visualizzato nella vista.</span><span class="sxs-lookup"><span data-stu-id="f71fa-127">The `WideEntry` element contains a single `WideItem` element that defines what property or script value is displayed in the view.</span></span>

```xml
<WideControl>
  <WideEntries>
    <WideEntry>
      <WideItem>...</WideItem>
    <WideEntry>
  </WideEntries>
</WideControl>
```

<span data-ttu-id="f71fa-128">Per un esempio completo di una visualizzazione più ampia, vedere [visualizzazione più ampia (Basic)](./wide-view-basic.md).</span><span class="sxs-lookup"><span data-stu-id="f71fa-128">For a complete example of a wide view, see [Wide View (Basic)](./wide-view-basic.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="f71fa-129">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="f71fa-129">See Also</span></span>

[<span data-ttu-id="f71fa-130">Creazione di una visualizzazione più ampia</span><span class="sxs-lookup"><span data-stu-id="f71fa-130">Creating a Wide View</span></span>](./creating-a-wide-view.md)

[<span data-ttu-id="f71fa-131">Elemento WideControl (formato)</span><span class="sxs-lookup"><span data-stu-id="f71fa-131">WideControl Element (Format)</span></span>](./widecontrol-element-format.md)

[<span data-ttu-id="f71fa-132">Elemento WideEntry (formato)</span><span class="sxs-lookup"><span data-stu-id="f71fa-132">WideEntry Element (Format)</span></span>](./wideentry-element-for-widecontrol-format.md)

[<span data-ttu-id="f71fa-133">La scrittura di un File di formattazione di PowerShell</span><span class="sxs-lookup"><span data-stu-id="f71fa-133">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
