---
title: Elemento ViewDefinitions (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 29840c10-2b30-4bb1-a8a0-ddf84d19c2d0
caps.latest.revision: 18
ms.openlocfilehash: c5ec80350c7707ccd41112ab5e1952e5dc198cca
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/15/2019
ms.locfileid: "72361420"
---
# <a name="viewdefinitions-element-format"></a><span data-ttu-id="675fb-102">Elemento ViewDefinitions (formato)</span><span class="sxs-lookup"><span data-stu-id="675fb-102">ViewDefinitions Element (Format)</span></span>

<span data-ttu-id="675fb-103">Definisce le visualizzazioni utilizzate per visualizzare gli oggetti .NET.</span><span class="sxs-lookup"><span data-stu-id="675fb-103">Defines the views used to display .NET objects.</span></span> <span data-ttu-id="675fb-104">Queste visualizzazioni possono visualizzare le proprietà e i valori di script di un oggetto in formato tabella, formato elenco, formato esteso e formato controllo personalizzato.</span><span class="sxs-lookup"><span data-stu-id="675fb-104">These views can display the properties and script values of an object  in a table format, list format, wide format, and custom control format.</span></span>

<span data-ttu-id="675fb-105">Elemento Configuration (Format) ViewDefinitions (format XML)</span><span class="sxs-lookup"><span data-stu-id="675fb-105">Configuration Element (Format) ViewDefinitions (Format XML) Element</span></span>

## <a name="syntax"></a><span data-ttu-id="675fb-106">Sintassi</span><span class="sxs-lookup"><span data-stu-id="675fb-106">Syntax</span></span>

```xml

<ViewDefinitions>
  <View>...</View>
</ViewDefinitions>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="675fb-107">Attributi ed elementi</span><span class="sxs-lookup"><span data-stu-id="675fb-107">Attributes and Elements</span></span>

<span data-ttu-id="675fb-108">Nelle sezioni seguenti vengono descritti gli attributi, gli elementi figlio e l'elemento padre dell'elemento `ViewDefinitions`.</span><span class="sxs-lookup"><span data-stu-id="675fb-108">The following sections describe the attributes, child elements, and parent element of the `ViewDefinitions` element.</span></span> <span data-ttu-id="675fb-109">Non esiste alcun limite al numero di visualizzazioni che possono essere definite in un file di formattazione e possono essere aggiunte in qualsiasi ordine.</span><span class="sxs-lookup"><span data-stu-id="675fb-109">There is no limit to the number of views that can be defined in a formatting file, and they can be added in any order.</span></span>

### <a name="attributes"></a><span data-ttu-id="675fb-110">Attributi</span><span class="sxs-lookup"><span data-stu-id="675fb-110">Attributes</span></span>

<span data-ttu-id="675fb-111">Nessuna.</span><span class="sxs-lookup"><span data-stu-id="675fb-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="675fb-112">Elementi figlio</span><span class="sxs-lookup"><span data-stu-id="675fb-112">Child Elements</span></span>

|<span data-ttu-id="675fb-113">Elemento</span><span class="sxs-lookup"><span data-stu-id="675fb-113">Element</span></span>|<span data-ttu-id="675fb-114">Description</span><span class="sxs-lookup"><span data-stu-id="675fb-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="675fb-115">Elemento View (Format)</span><span class="sxs-lookup"><span data-stu-id="675fb-115">View Element (Format)</span></span>](./view-element-format.md)|<span data-ttu-id="675fb-116">Definisce una vista utilizzata per visualizzare uno o più oggetti .NET.</span><span class="sxs-lookup"><span data-stu-id="675fb-116">Defines a view that is used to display one or more .NET objects.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="675fb-117">Elementi padre</span><span class="sxs-lookup"><span data-stu-id="675fb-117">Parent Elements</span></span>

|<span data-ttu-id="675fb-118">Elemento</span><span class="sxs-lookup"><span data-stu-id="675fb-118">Element</span></span>|<span data-ttu-id="675fb-119">Description</span><span class="sxs-lookup"><span data-stu-id="675fb-119">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="675fb-120">Elemento Configuration (Format)</span><span class="sxs-lookup"><span data-stu-id="675fb-120">Configuration Element (Format)</span></span>](./configuration-element-format.md)|<span data-ttu-id="675fb-121">Rappresenta l'elemento di primo livello di un file di formattazione.</span><span class="sxs-lookup"><span data-stu-id="675fb-121">Represents the top-level element of a formatting file.</span></span>|

## <a name="remarks"></a><span data-ttu-id="675fb-122">Osservazioni</span><span class="sxs-lookup"><span data-stu-id="675fb-122">Remarks</span></span>

<span data-ttu-id="675fb-123">Per ulteriori informazioni sui componenti dei diversi tipi di viste, vedere gli argomenti seguenti:</span><span class="sxs-lookup"><span data-stu-id="675fb-123">For more information about the components of the different types of views, see the following topics:</span></span>

- [<span data-ttu-id="675fb-124">Creazione di una vista tabella</span><span class="sxs-lookup"><span data-stu-id="675fb-124">Creating a Table View</span></span>](./creating-a-table-view.md)

- [<span data-ttu-id="675fb-125">Creazione di una visualizzazione elenco</span><span class="sxs-lookup"><span data-stu-id="675fb-125">Creating a List View</span></span>](./creating-a-list-view.md)

- [<span data-ttu-id="675fb-126">Creazione di una visualizzazione estesa</span><span class="sxs-lookup"><span data-stu-id="675fb-126">Creating a Wide View</span></span>](./creating-a-wide-view.md)

- [<span data-ttu-id="675fb-127">Controlli personalizzati</span><span class="sxs-lookup"><span data-stu-id="675fb-127">Custom Controls</span></span>](./creating-custom-controls.md)

## <a name="example"></a><span data-ttu-id="675fb-128">Esempio</span><span class="sxs-lookup"><span data-stu-id="675fb-128">Example</span></span>

<span data-ttu-id="675fb-129">In questo esempio viene illustrato un elemento `ViewDefinitions` che contiene gli elementi padre per una visualizzazione tabella e una visualizzazione elenco.</span><span class="sxs-lookup"><span data-stu-id="675fb-129">This example shows a `ViewDefinitions` element that contains the parent elements for a table view and a list view.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="675fb-130">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="675fb-130">See Also</span></span>

[<span data-ttu-id="675fb-131">Elemento Configuration (Format)</span><span class="sxs-lookup"><span data-stu-id="675fb-131">Configuration Element (Format)</span></span>](./configuration-element-format.md)

[<span data-ttu-id="675fb-132">Elemento View (Format)</span><span class="sxs-lookup"><span data-stu-id="675fb-132">View Element (Format)</span></span>](./view-element-format.md)

[<span data-ttu-id="675fb-133">Creazione di una vista tabella</span><span class="sxs-lookup"><span data-stu-id="675fb-133">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="675fb-134">Creazione di una visualizzazione elenco</span><span class="sxs-lookup"><span data-stu-id="675fb-134">Creating a List View</span></span>](./creating-a-list-view.md)

[<span data-ttu-id="675fb-135">Creazione di una visualizzazione estesa</span><span class="sxs-lookup"><span data-stu-id="675fb-135">Creating a Wide View</span></span>](./creating-a-wide-view.md)

[<span data-ttu-id="675fb-136">Controlli personalizzati</span><span class="sxs-lookup"><span data-stu-id="675fb-136">Custom Controls</span></span>](./creating-custom-controls.md)

[<span data-ttu-id="675fb-137">Scrittura di un file di formattazione di PowerShell</span><span class="sxs-lookup"><span data-stu-id="675fb-137">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
