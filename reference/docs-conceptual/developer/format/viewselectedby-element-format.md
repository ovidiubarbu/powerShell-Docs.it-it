---
title: Elemento ViewSelectedBy (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: acdeef4d-3554-4f39-a7e6-a684e3848fd7
caps.latest.revision: 19
ms.openlocfilehash: efc1c5d1338889ecd0be7150b7733842ce78979e
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/15/2019
ms.locfileid: "72367970"
---
# <a name="viewselectedby-element-format"></a><span data-ttu-id="1f39c-102">Elemento ViewSelectedBy (formato)</span><span class="sxs-lookup"><span data-stu-id="1f39c-102">ViewSelectedBy Element (Format)</span></span>

<span data-ttu-id="1f39c-103">Definisce gli oggetti .NET visualizzati dalla visualizzazione.</span><span class="sxs-lookup"><span data-stu-id="1f39c-103">Defines the .NET objects that are displayed by the view.</span></span> <span data-ttu-id="1f39c-104">Ogni visualizzazione deve specificare almeno un oggetto .NET.</span><span class="sxs-lookup"><span data-stu-id="1f39c-104">Each view must specify at least one .NET object.</span></span>

<span data-ttu-id="1f39c-105">Elemento ViewDefinitions (Format) elemento View (Format) elemento ViewSelectedBy (Format)</span><span class="sxs-lookup"><span data-stu-id="1f39c-105">ViewDefinitions Element (Format) View Element (Format) ViewSelectedBy Element (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="1f39c-106">Sintassi</span><span class="sxs-lookup"><span data-stu-id="1f39c-106">Syntax</span></span>

```xml
<ViewSelectedBy>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>SelectionSet</SelectionSetName>
</ViewSelectedBy>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="1f39c-107">Attributi ed elementi</span><span class="sxs-lookup"><span data-stu-id="1f39c-107">Attributes and Elements</span></span>

<span data-ttu-id="1f39c-108">Nelle sezioni seguenti vengono descritti gli attributi, gli elementi figlio e l'elemento padre dell'elemento `ViewSelectedBy`.</span><span class="sxs-lookup"><span data-stu-id="1f39c-108">The following sections describe the attributes, child elements, and parent element of the `ViewSelectedBy` element.</span></span> <span data-ttu-id="1f39c-109">Questo elemento deve contenere almeno un elemento figlio `TypeName` o `SelectionSetName`.</span><span class="sxs-lookup"><span data-stu-id="1f39c-109">This element must contain at least one `TypeName` or `SelectionSetName` child element.</span></span> <span data-ttu-id="1f39c-110">Non esiste alcun limite al numero di elementi figlio che è possibile specificare, né l'ordine è significativo.</span><span class="sxs-lookup"><span data-stu-id="1f39c-110">There is no limit to the number of child elements that can be specified nor is their order significant.</span></span>

### <a name="attributes"></a><span data-ttu-id="1f39c-111">Attributi</span><span class="sxs-lookup"><span data-stu-id="1f39c-111">Attributes</span></span>

<span data-ttu-id="1f39c-112">Nessuna.</span><span class="sxs-lookup"><span data-stu-id="1f39c-112">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="1f39c-113">Elementi figlio</span><span class="sxs-lookup"><span data-stu-id="1f39c-113">Child Elements</span></span>

|<span data-ttu-id="1f39c-114">Elemento</span><span class="sxs-lookup"><span data-stu-id="1f39c-114">Element</span></span>|<span data-ttu-id="1f39c-115">Description</span><span class="sxs-lookup"><span data-stu-id="1f39c-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="1f39c-116">Elemento TypeName per ViewSelectedBy (Format)</span><span class="sxs-lookup"><span data-stu-id="1f39c-116">TypeName Element for ViewSelectedBy (Format)</span></span>](./typename-element-for-viewselectedby-format.md)|<span data-ttu-id="1f39c-117">Elemento facoltativo.</span><span class="sxs-lookup"><span data-stu-id="1f39c-117">Optional element.</span></span><br /><br /> <span data-ttu-id="1f39c-118">Specifica un oggetto .NET visualizzato dalla visualizzazione.</span><span class="sxs-lookup"><span data-stu-id="1f39c-118">Specifies a .NET object that is displayed by the view.</span></span>|
|[<span data-ttu-id="1f39c-119">Elemento SelectionSetName per ViewSelectedBy (Format)</span><span class="sxs-lookup"><span data-stu-id="1f39c-119">SelectionSetName Element for ViewSelectedBy (Format)</span></span>](./selectionsetname-element-for-viewselectedby-format.md)|<span data-ttu-id="1f39c-120">Elemento facoltativo.</span><span class="sxs-lookup"><span data-stu-id="1f39c-120">Optional element.</span></span><br /><br /> <span data-ttu-id="1f39c-121">Specifica un set di oggetti .NET visualizzati dalla visualizzazione.</span><span class="sxs-lookup"><span data-stu-id="1f39c-121">Specifies a set of .NET objects that are displayed by the view.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="1f39c-122">Elementi padre</span><span class="sxs-lookup"><span data-stu-id="1f39c-122">Parent Elements</span></span>

|<span data-ttu-id="1f39c-123">Elemento</span><span class="sxs-lookup"><span data-stu-id="1f39c-123">Element</span></span>|<span data-ttu-id="1f39c-124">Description</span><span class="sxs-lookup"><span data-stu-id="1f39c-124">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="1f39c-125">Elemento View (Format)</span><span class="sxs-lookup"><span data-stu-id="1f39c-125">View Element (Format)</span></span>](./view-element-format.md)|<span data-ttu-id="1f39c-126">Definisce una vista che visualizza uno o più oggetti .NET.</span><span class="sxs-lookup"><span data-stu-id="1f39c-126">Defines a view that displays one or more .NET objects.</span></span>|

## <a name="remarks"></a><span data-ttu-id="1f39c-127">Osservazioni</span><span class="sxs-lookup"><span data-stu-id="1f39c-127">Remarks</span></span>

<span data-ttu-id="1f39c-128">Per ulteriori informazioni sull'utilizzo di questo elemento in visualizzazioni diverse, vedere [componenti di visualizzazione tabella](./creating-a-table-view.md), [componenti di visualizzazione elenco](./creating-a-list-view.md), [componenti di visualizzazione ampia](./creating-a-wide-view.md)e [componenti di controllo personalizzati](./creating-custom-controls.md).</span><span class="sxs-lookup"><span data-stu-id="1f39c-128">For more information about how this element is used in different views, see [Table View Components](./creating-a-table-view.md), [List View Components](./creating-a-list-view.md), [Wide View Components](./creating-a-wide-view.md), and [Custom Control Components](./creating-custom-controls.md).</span></span>

<span data-ttu-id="1f39c-129">L'elemento `SelectionSetName` viene utilizzato quando il file di formattazione definisce un set di oggetti visualizzati da più visualizzazioni.</span><span class="sxs-lookup"><span data-stu-id="1f39c-129">The `SelectionSetName` element is used when the formatting file defines a set of objects that are displayed by multiple views.</span></span> <span data-ttu-id="1f39c-130">Per ulteriori informazioni su come definire e fare riferimento ai set di selezione, vedere [definizione di set di oggetti](./defining-selection-sets.md).</span><span class="sxs-lookup"><span data-stu-id="1f39c-130">For more information about how selection sets are defined and referenced, see [Defining Sets of Objects](./defining-selection-sets.md).</span></span>

## <a name="example"></a><span data-ttu-id="1f39c-131">Esempio</span><span class="sxs-lookup"><span data-stu-id="1f39c-131">Example</span></span>

<span data-ttu-id="1f39c-132">Nell'esempio seguente viene illustrato come specificare l'oggetto [System. ServiceProcess. ServiceController](/dotnet/api/System.ServiceProcess.ServiceController) per una visualizzazione elenco.</span><span class="sxs-lookup"><span data-stu-id="1f39c-132">The following example shows how to specify the [System.Serviceprocess.Servicecontroller](/dotnet/api/System.ServiceProcess.ServiceController) object for a list view.</span></span> <span data-ttu-id="1f39c-133">Lo stesso schema viene utilizzato per le visualizzazioni tabella, Wide e Custom.</span><span class="sxs-lookup"><span data-stu-id="1f39c-133">The same schema is used for table, wide, and custom views.</span></span>

```xml
<View>
  <Name>System.ServiceProcess.ServiceController</Name>
  <ViewSelectedBy>
    <TypeName>System.ServiceProcess.ServiceController</TypeName>
  </ViewSelectedBy>
  <ListControl>...</ListControl>
</View>
```

## <a name="see-also"></a><span data-ttu-id="1f39c-134">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="1f39c-134">See Also</span></span>

[<span data-ttu-id="1f39c-135">Creazione di una visualizzazione elenco</span><span class="sxs-lookup"><span data-stu-id="1f39c-135">Creating a List View</span></span>](./creating-a-list-view.md)

[<span data-ttu-id="1f39c-136">Creazione di una vista tabella</span><span class="sxs-lookup"><span data-stu-id="1f39c-136">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="1f39c-137">Creazione di una visualizzazione estesa</span><span class="sxs-lookup"><span data-stu-id="1f39c-137">Creating a Wide View</span></span>](./creating-a-wide-view.md)

[<span data-ttu-id="1f39c-138">Creazione di controlli personalizzati</span><span class="sxs-lookup"><span data-stu-id="1f39c-138">Creating Custom Controls</span></span>](./creating-custom-controls.md)

[<span data-ttu-id="1f39c-139">Definizione di set di selezione</span><span class="sxs-lookup"><span data-stu-id="1f39c-139">Defining Selection Sets</span></span>](./defining-selection-sets.md)

[<span data-ttu-id="1f39c-140">Elemento SelectionSetName per ViewSelectedBy (Format)</span><span class="sxs-lookup"><span data-stu-id="1f39c-140">SelectionSetName Element for ViewSelectedBy (Format)</span></span>](./selectionsetname-element-for-viewselectedby-format.md)

[<span data-ttu-id="1f39c-141">Elemento TypeName (Format)</span><span class="sxs-lookup"><span data-stu-id="1f39c-141">TypeName Element (Format)</span></span>](./typename-element-for-viewselectedby-format.md)

[<span data-ttu-id="1f39c-142">Scrittura di un file di formattazione di PowerShell</span><span class="sxs-lookup"><span data-stu-id="1f39c-142">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
