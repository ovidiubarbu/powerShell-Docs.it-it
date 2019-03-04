---
title: Elemento ViewDefinitions (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 29840c10-2b30-4bb1-a8a0-ddf84d19c2d0
caps.latest.revision: 18
ms.openlocfilehash: c5ec80350c7707ccd41112ab5e1952e5dc198cca
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/03/2019
ms.locfileid: "56862087"
---
# <a name="viewdefinitions-element-format"></a><span data-ttu-id="5c49d-102">Elemento ViewDefinitions (formato)</span><span class="sxs-lookup"><span data-stu-id="5c49d-102">ViewDefinitions Element (Format)</span></span>

<span data-ttu-id="5c49d-103">Definisce le viste consente di visualizzare gli oggetti .NET.</span><span class="sxs-lookup"><span data-stu-id="5c49d-103">Defines the views used to display .NET objects.</span></span> <span data-ttu-id="5c49d-104">Tali viste è possono visualizzare le proprietà e valori di script di un oggetto in un formato di tabella, formato di elenco, formato esteso e personalizzato di controllo del formato.</span><span class="sxs-lookup"><span data-stu-id="5c49d-104">These views can display the properties and script values of an object  in a table format, list format, wide format, and custom control format.</span></span>

<span data-ttu-id="5c49d-105">Elemento di configurazione elemento (formato) ViewDefinitions (formato XML)</span><span class="sxs-lookup"><span data-stu-id="5c49d-105">Configuration Element (Format) ViewDefinitions (Format XML) Element</span></span>

## <a name="syntax"></a><span data-ttu-id="5c49d-106">Sintassi</span><span class="sxs-lookup"><span data-stu-id="5c49d-106">Syntax</span></span>

```xml

<ViewDefinitions>
  <View>...</View>
</ViewDefinitions>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="5c49d-107">Attributi ed elementi</span><span class="sxs-lookup"><span data-stu-id="5c49d-107">Attributes and Elements</span></span>

<span data-ttu-id="5c49d-108">Le sezioni seguenti descrivono gli attributi, elementi figlio ed elemento padre dell'elemento di `ViewDefinitions` elemento.</span><span class="sxs-lookup"><span data-stu-id="5c49d-108">The following sections describe the attributes, child elements, and parent element of the `ViewDefinitions` element.</span></span> <span data-ttu-id="5c49d-109">Non sono previsti limiti al numero di visualizzazioni che possono essere definite in un file di formattazione e possono essere aggiunti in qualsiasi ordine.</span><span class="sxs-lookup"><span data-stu-id="5c49d-109">There is no limit to the number of views that can be defined in a formatting file, and they can be added in any order.</span></span>

### <a name="attributes"></a><span data-ttu-id="5c49d-110">Attributes</span><span class="sxs-lookup"><span data-stu-id="5c49d-110">Attributes</span></span>

<span data-ttu-id="5c49d-111">Nessuna.</span><span class="sxs-lookup"><span data-stu-id="5c49d-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="5c49d-112">Elementi figlio</span><span class="sxs-lookup"><span data-stu-id="5c49d-112">Child Elements</span></span>

|<span data-ttu-id="5c49d-113">Elemento</span><span class="sxs-lookup"><span data-stu-id="5c49d-113">Element</span></span>|<span data-ttu-id="5c49d-114">Description</span><span class="sxs-lookup"><span data-stu-id="5c49d-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="5c49d-115">Elemento di visualizzazione (formato)</span><span class="sxs-lookup"><span data-stu-id="5c49d-115">View Element (Format)</span></span>](./view-element-format.md)|<span data-ttu-id="5c49d-116">Definisce una vista che consente di visualizzare uno o più oggetti .NET.</span><span class="sxs-lookup"><span data-stu-id="5c49d-116">Defines a view that is used to display one or more .NET objects.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="5c49d-117">Elementi padre</span><span class="sxs-lookup"><span data-stu-id="5c49d-117">Parent Elements</span></span>

|<span data-ttu-id="5c49d-118">Elemento</span><span class="sxs-lookup"><span data-stu-id="5c49d-118">Element</span></span>|<span data-ttu-id="5c49d-119">Description</span><span class="sxs-lookup"><span data-stu-id="5c49d-119">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="5c49d-120">Elemento di configurazione (formato)</span><span class="sxs-lookup"><span data-stu-id="5c49d-120">Configuration Element (Format)</span></span>](./configuration-element-format.md)|<span data-ttu-id="5c49d-121">Rappresenta l'elemento di livello superiore di un file di formattazione.</span><span class="sxs-lookup"><span data-stu-id="5c49d-121">Represents the top-level element of a formatting file.</span></span>|

## <a name="remarks"></a><span data-ttu-id="5c49d-122">Osservazioni</span><span class="sxs-lookup"><span data-stu-id="5c49d-122">Remarks</span></span>

<span data-ttu-id="5c49d-123">Per altre informazioni sui componenti dei diversi tipi di visualizzazioni, vedere gli argomenti seguenti:</span><span class="sxs-lookup"><span data-stu-id="5c49d-123">For more information about the components of the different types of views, see the following topics:</span></span>

- [<span data-ttu-id="5c49d-124">Creazione di una visualizzazione tabella</span><span class="sxs-lookup"><span data-stu-id="5c49d-124">Creating a Table View</span></span>](./creating-a-table-view.md)

- [<span data-ttu-id="5c49d-125">Creazione di una visualizzazione elenco</span><span class="sxs-lookup"><span data-stu-id="5c49d-125">Creating a List View</span></span>](./creating-a-list-view.md)

- [<span data-ttu-id="5c49d-126">Creazione di una visualizzazione più ampia</span><span class="sxs-lookup"><span data-stu-id="5c49d-126">Creating a Wide View</span></span>](./creating-a-wide-view.md)

- [<span data-ttu-id="5c49d-127">Controlli personalizzati</span><span class="sxs-lookup"><span data-stu-id="5c49d-127">Custom Controls</span></span>](./creating-custom-controls.md)

## <a name="example"></a><span data-ttu-id="5c49d-128">Esempio</span><span class="sxs-lookup"><span data-stu-id="5c49d-128">Example</span></span>

<span data-ttu-id="5c49d-129">Questo esempio viene illustrato un `ViewDefinitions` elemento che contiene gli elementi padre per la visualizzazione di una tabella e una visualizzazione elenco.</span><span class="sxs-lookup"><span data-stu-id="5c49d-129">This example shows a `ViewDefinitions` element that contains the parent elements for a table view and a list view.</span></span>

```xml
<Configuration>
  <ViewDefinitions>
    <View>
      <TableControl>...</TableControl>
    </View>
    <View>
      <ListControl>...</ListControl>
    </View>
  </ViewDefinitions>
</Configuration>
```

## <a name="see-also"></a><span data-ttu-id="5c49d-130">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="5c49d-130">See Also</span></span>

[<span data-ttu-id="5c49d-131">Elemento di configurazione (formato)</span><span class="sxs-lookup"><span data-stu-id="5c49d-131">Configuration Element (Format)</span></span>](./configuration-element-format.md)

[<span data-ttu-id="5c49d-132">Elemento di visualizzazione (formato)</span><span class="sxs-lookup"><span data-stu-id="5c49d-132">View Element (Format)</span></span>](./view-element-format.md)

[<span data-ttu-id="5c49d-133">Creazione di una visualizzazione tabella</span><span class="sxs-lookup"><span data-stu-id="5c49d-133">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="5c49d-134">Creazione di una visualizzazione elenco</span><span class="sxs-lookup"><span data-stu-id="5c49d-134">Creating a List View</span></span>](./creating-a-list-view.md)

[<span data-ttu-id="5c49d-135">Creazione di una visualizzazione più ampia</span><span class="sxs-lookup"><span data-stu-id="5c49d-135">Creating a Wide View</span></span>](./creating-a-wide-view.md)

[<span data-ttu-id="5c49d-136">Controlli personalizzati</span><span class="sxs-lookup"><span data-stu-id="5c49d-136">Custom Controls</span></span>](./creating-custom-controls.md)

[<span data-ttu-id="5c49d-137">La scrittura di un File di formattazione di PowerShell</span><span class="sxs-lookup"><span data-stu-id="5c49d-137">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
