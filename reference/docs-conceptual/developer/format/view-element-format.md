---
title: Elemento View (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d837d5d4-ed2e-4d84-a306-0b5d2ad2d0bf
caps.latest.revision: 24
ms.openlocfilehash: 2361c1117757569bef0815018c75764430a9e7a8
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/05/2019
ms.locfileid: "72361460"
---
# <a name="view-element-format"></a><span data-ttu-id="3989b-102">Elemento View (formato)</span><span class="sxs-lookup"><span data-stu-id="3989b-102">View Element (Format)</span></span>

<span data-ttu-id="3989b-103">Definisce una vista che visualizza uno o più oggetti .NET.</span><span class="sxs-lookup"><span data-stu-id="3989b-103">Defines a view that displays one or more .NET objects.</span></span> <span data-ttu-id="3989b-104">Non esiste alcun limite al numero di visualizzazioni che è possibile definire in un file di formattazione.</span><span class="sxs-lookup"><span data-stu-id="3989b-104">There is no limit to the number of views that can be defined in a formatting file.</span></span>

<span data-ttu-id="3989b-105">Elemento Configuration (Format) elemento ViewDefinitions (Format) elemento View (Format)</span><span class="sxs-lookup"><span data-stu-id="3989b-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="3989b-106">Sintassi</span><span class="sxs-lookup"><span data-stu-id="3989b-106">Syntax</span></span>

```xml
<View>
  <Name>Friendly name of view.</Name>
  <ViewSelectedBy>...</ViewSelectedBy>
  <Controls>...</Controls>
  <GroupBy>...</GroupBy>
  <TableControl>...</TableControl>
  <ListControl>...</ListControl>
  <WideControl>...</WideControl>
  <CustomControl>...</CustomControl>
</View>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="3989b-107">Attributi ed elementi</span><span class="sxs-lookup"><span data-stu-id="3989b-107">Attributes and Elements</span></span>

<span data-ttu-id="3989b-108">Nelle sezioni seguenti vengono descritti gli attributi, gli elementi figlio e l'elemento padre dell'elemento `View`.</span><span class="sxs-lookup"><span data-stu-id="3989b-108">The following sections describe the attributes, child elements, and the parent element of the `View` element.</span></span> <span data-ttu-id="3989b-109">È necessario specificare uno solo degli elementi figlio del controllo ed è necessario specificare il nome della visualizzazione e gli oggetti che utilizzano la visualizzazione.</span><span class="sxs-lookup"><span data-stu-id="3989b-109">You must specify one and only one of the control child elements, and you must specify the name of the view and the objects that use the view.</span></span> <span data-ttu-id="3989b-110">La definizione di controlli personalizzati, la procedura per raggruppare gli oggetti e la specifica se la vista è fuori banda è facoltativa.</span><span class="sxs-lookup"><span data-stu-id="3989b-110">Defining custom controls, how to group objects, and specifying if the view is out-of-band are optional.</span></span>

### <a name="attributes"></a><span data-ttu-id="3989b-111">Attributi</span><span class="sxs-lookup"><span data-stu-id="3989b-111">Attributes</span></span>

<span data-ttu-id="3989b-112">Nessuna.</span><span class="sxs-lookup"><span data-stu-id="3989b-112">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="3989b-113">Elementi figlio</span><span class="sxs-lookup"><span data-stu-id="3989b-113">Child Elements</span></span>

|<span data-ttu-id="3989b-114">Elemento</span><span class="sxs-lookup"><span data-stu-id="3989b-114">Element</span></span>|<span data-ttu-id="3989b-115">Description</span><span class="sxs-lookup"><span data-stu-id="3989b-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="3989b-116">Elemento Controls per View (Format)</span><span class="sxs-lookup"><span data-stu-id="3989b-116">Controls Element for View (Format)</span></span>](./controls-element-for-view-format.md)|<span data-ttu-id="3989b-117">Elemento facoltativo.</span><span class="sxs-lookup"><span data-stu-id="3989b-117">Optional element.</span></span><br /><br /> <span data-ttu-id="3989b-118">Definisce un set di controlli a cui è possibile fare riferimento tramite il nome dall'interno della vista.</span><span class="sxs-lookup"><span data-stu-id="3989b-118">Defines a set of controls that can be referenced by their name from within the view.</span></span>|
|[<span data-ttu-id="3989b-119">Elemento CustomControl (Format)</span><span class="sxs-lookup"><span data-stu-id="3989b-119">CustomControl Element (Format)</span></span>](./customcontrol-element-for-groupby-format.md)|<span data-ttu-id="3989b-120">Elemento facoltativo.</span><span class="sxs-lookup"><span data-stu-id="3989b-120">Optional element.</span></span><br /><br /> <span data-ttu-id="3989b-121">Definisce un formato di controllo personalizzato per la visualizzazione.</span><span class="sxs-lookup"><span data-stu-id="3989b-121">Defines a custom control format for the view.</span></span>|
|[<span data-ttu-id="3989b-122">Elemento GroupBy per View (Format)</span><span class="sxs-lookup"><span data-stu-id="3989b-122">GroupBy Element for View (Format)</span></span>](./groupby-element-for-view-format.md)|<span data-ttu-id="3989b-123">Elemento facoltativo.</span><span class="sxs-lookup"><span data-stu-id="3989b-123">Optional element.</span></span><br /><br /> <span data-ttu-id="3989b-124">Definisce la modalità di raggruppamento dei membri degli oggetti .NET.</span><span class="sxs-lookup"><span data-stu-id="3989b-124">Defines how the members of the .NET objects are grouped.</span></span>|
|[<span data-ttu-id="3989b-125">Elemento ListControl (Format)</span><span class="sxs-lookup"><span data-stu-id="3989b-125">ListControl Element (Format)</span></span>](./listcontrol-element-format.md)|<span data-ttu-id="3989b-126">Elemento facoltativo.</span><span class="sxs-lookup"><span data-stu-id="3989b-126">Optional element.</span></span><br /><br /> <span data-ttu-id="3989b-127">Definisce un formato di elenco per la visualizzazione.</span><span class="sxs-lookup"><span data-stu-id="3989b-127">Defines a list format for the view.</span></span>|
|[<span data-ttu-id="3989b-128">Elemento Name per View (Format)</span><span class="sxs-lookup"><span data-stu-id="3989b-128">Name Element for View (Format)</span></span>](./name-element-for-view-format.md)|<span data-ttu-id="3989b-129">Elemento obbligatorio.</span><span class="sxs-lookup"><span data-stu-id="3989b-129">Required element.</span></span><br /><br /> <span data-ttu-id="3989b-130">Specifica il nome utilizzato per fare riferimento alla vista.</span><span class="sxs-lookup"><span data-stu-id="3989b-130">Specifies the name used to reference the view.</span></span>|
|[<span data-ttu-id="3989b-131">Elemento Table ((Format)</span><span class="sxs-lookup"><span data-stu-id="3989b-131">TableControl Element (Format)</span></span>](./tablecontrol-element-format.md)|<span data-ttu-id="3989b-132">Elemento facoltativo.</span><span class="sxs-lookup"><span data-stu-id="3989b-132">Optional element.</span></span><br /><br /> <span data-ttu-id="3989b-133">Definisce un formato di tabella per la visualizzazione.</span><span class="sxs-lookup"><span data-stu-id="3989b-133">Defines a table format for the view.</span></span>|
|[<span data-ttu-id="3989b-134">Elemento ViewSelectedBy per View (Format)</span><span class="sxs-lookup"><span data-stu-id="3989b-134">ViewSelectedBy Element for View (Format)</span></span>](./viewselectedby-element-format.md)|<span data-ttu-id="3989b-135">Elemento obbligatorio.</span><span class="sxs-lookup"><span data-stu-id="3989b-135">Required element.</span></span><br /><br /> <span data-ttu-id="3989b-136">Definisce gli oggetti .NET visualizzati da questa visualizzazione.</span><span class="sxs-lookup"><span data-stu-id="3989b-136">Defines the .NET objects that this view displays.</span></span>|
|[<span data-ttu-id="3989b-137">Elemento WideControl (Format)</span><span class="sxs-lookup"><span data-stu-id="3989b-137">WideControl Element (Format)</span></span>](./widecontrol-element-format.md)|<span data-ttu-id="3989b-138">Elemento facoltativo.</span><span class="sxs-lookup"><span data-stu-id="3989b-138">Optional element.</span></span><br /><br /> <span data-ttu-id="3989b-139">Definisce un formato di elenco Wide (valore singolo) per la visualizzazione.</span><span class="sxs-lookup"><span data-stu-id="3989b-139">Defines a wide (single value) list format for the view.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="3989b-140">Elementi padre</span><span class="sxs-lookup"><span data-stu-id="3989b-140">Parent Elements</span></span>

|<span data-ttu-id="3989b-141">Elemento</span><span class="sxs-lookup"><span data-stu-id="3989b-141">Element</span></span>|<span data-ttu-id="3989b-142">Description</span><span class="sxs-lookup"><span data-stu-id="3989b-142">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="3989b-143">Elemento ViewDefinitions (Format)</span><span class="sxs-lookup"><span data-stu-id="3989b-143">ViewDefinitions Element (Format)</span></span>](./viewdefinitions-element-format.md)|<span data-ttu-id="3989b-144">Definisce le visualizzazioni utilizzate per visualizzare gli oggetti.</span><span class="sxs-lookup"><span data-stu-id="3989b-144">Defines the views used to display objects.</span></span>|

## <a name="remarks"></a><span data-ttu-id="3989b-145">Osservazioni</span><span class="sxs-lookup"><span data-stu-id="3989b-145">Remarks</span></span>

<span data-ttu-id="3989b-146">Per ulteriori informazioni sui componenti di visualizzazioni e controlli personalizzati diversi, vedere gli argomenti seguenti:</span><span class="sxs-lookup"><span data-stu-id="3989b-146">For more information about the components of different views and custom controls, see the following topics:</span></span>

- [<span data-ttu-id="3989b-147">Componenti di visualizzazione tabella</span><span class="sxs-lookup"><span data-stu-id="3989b-147">Table View Components</span></span>](./creating-a-table-view.md)

- [<span data-ttu-id="3989b-148">Componenti visualizzazione elenco</span><span class="sxs-lookup"><span data-stu-id="3989b-148">List View Components</span></span>](./creating-a-list-view.md)

- [<span data-ttu-id="3989b-149">Componenti di visualizzazione estesa</span><span class="sxs-lookup"><span data-stu-id="3989b-149">Wide View Components</span></span>](./creating-a-wide-view.md)

- [<span data-ttu-id="3989b-150">Controlli personalizzati</span><span class="sxs-lookup"><span data-stu-id="3989b-150">Custom Controls</span></span>](./creating-custom-controls.md)

## <a name="example"></a><span data-ttu-id="3989b-151">Esempio</span><span class="sxs-lookup"><span data-stu-id="3989b-151">Example</span></span>

<span data-ttu-id="3989b-152">Questo esempio illustra un elemento `View` che definisce una visualizzazione tabella per l'oggetto [System. ServiceProcess. ServiceController](/dotnet/api/System.ServiceProcess.ServiceController) .</span><span class="sxs-lookup"><span data-stu-id="3989b-152">This example shows a `View` element that defines a table view for the [System.Serviceprocess.Servicecontroller](/dotnet/api/System.ServiceProcess.ServiceController) object.</span></span>

```xml
<ViewDefinitions>
  <View>
    <Name>service</Name>
    <ViewSelectedBy>
      <TypeName>System.ServiceProcess.ServiceController</TypeName>
    </ViewSelectedBy>
    <TableControl>...</TableControl>
  </View>
</ViewDefinitions>

```

## <a name="see-also"></a><span data-ttu-id="3989b-153">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="3989b-153">See Also</span></span>

[<span data-ttu-id="3989b-154">Elemento ViewDefinitions (Format)</span><span class="sxs-lookup"><span data-stu-id="3989b-154">ViewDefinitions Element (Format)</span></span>](./viewdefinitions-element-format.md)

[<span data-ttu-id="3989b-155">Elemento Name per View (Format)</span><span class="sxs-lookup"><span data-stu-id="3989b-155">Name Element for View (Format)</span></span>](./name-element-for-view-format.md)

[<span data-ttu-id="3989b-156">Elemento ViewSelectedBy (Format)</span><span class="sxs-lookup"><span data-stu-id="3989b-156">ViewSelectedBy Element (Format)</span></span>](./viewselectedby-element-format.md)

[<span data-ttu-id="3989b-157">Elemento Controls per View (Format)</span><span class="sxs-lookup"><span data-stu-id="3989b-157">Controls Element for View (Format)</span></span>](./controls-element-for-view-format.md)

[<span data-ttu-id="3989b-158">Elemento GroupBy per View (Format)</span><span class="sxs-lookup"><span data-stu-id="3989b-158">GroupBy Element for View (Format)</span></span>](./groupby-element-for-view-format.md)

[<span data-ttu-id="3989b-159">Elemento Table ((Format)</span><span class="sxs-lookup"><span data-stu-id="3989b-159">TableControl Element (Format)</span></span>](./tablecontrol-element-format.md)

[<span data-ttu-id="3989b-160">Elemento ListControl (Format)</span><span class="sxs-lookup"><span data-stu-id="3989b-160">ListControl Element (Format)</span></span>](./listcontrol-element-format.md)

[<span data-ttu-id="3989b-161">Elemento WideControl (Format)</span><span class="sxs-lookup"><span data-stu-id="3989b-161">WideControl Element (Format)</span></span>](./widecontrol-element-format.md)

[<span data-ttu-id="3989b-162">Elemento CustomControl (Format)</span><span class="sxs-lookup"><span data-stu-id="3989b-162">CustomControl Element (Format)</span></span>](./customcontrol-element-for-groupby-format.md)

[<span data-ttu-id="3989b-163">Scrittura di un file di formattazione di PowerShell</span><span class="sxs-lookup"><span data-stu-id="3989b-163">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
