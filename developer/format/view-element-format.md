---
title: Visualizzare l'elemento (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d837d5d4-ed2e-4d84-a306-0b5d2ad2d0bf
caps.latest.revision: 24
ms.openlocfilehash: 2361c1117757569bef0815018c75764430a9e7a8
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/03/2019
ms.locfileid: "56856147"
---
# <a name="view-element-format"></a><span data-ttu-id="1c7a8-102">Elemento View (formato)</span><span class="sxs-lookup"><span data-stu-id="1c7a8-102">View Element (Format)</span></span>

<span data-ttu-id="1c7a8-103">Definisce una vista contenente uno o più oggetti .NET.</span><span class="sxs-lookup"><span data-stu-id="1c7a8-103">Defines a view that displays one or more .NET objects.</span></span> <span data-ttu-id="1c7a8-104">Non sono previsti limiti al numero di visualizzazioni che possono essere definite in un file di formattazione.</span><span class="sxs-lookup"><span data-stu-id="1c7a8-104">There is no limit to the number of views that can be defined in a formatting file.</span></span>

<span data-ttu-id="1c7a8-105">Elemento di visualizzazione configurazione elemento (formato) elemento ViewDefinitions (formato) (formato)</span><span class="sxs-lookup"><span data-stu-id="1c7a8-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="1c7a8-106">Sintassi</span><span class="sxs-lookup"><span data-stu-id="1c7a8-106">Syntax</span></span>

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

## <a name="attributes-and-elements"></a><span data-ttu-id="1c7a8-107">Attributi ed elementi</span><span class="sxs-lookup"><span data-stu-id="1c7a8-107">Attributes and Elements</span></span>

<span data-ttu-id="1c7a8-108">Le sezioni seguenti descrivono gli attributi e gli elementi figlio dell'elemento padre del `View` elemento.</span><span class="sxs-lookup"><span data-stu-id="1c7a8-108">The following sections describe the attributes, child elements, and the parent element of the `View` element.</span></span> <span data-ttu-id="1c7a8-109">È necessario specificare uno e uno solo gli elementi figlio del controllo e specificare il nome della visualizzazione e gli oggetti che utilizzano la vista.</span><span class="sxs-lookup"><span data-stu-id="1c7a8-109">You must specify one and only one of the control child elements, and you must specify the name of the view and the objects that use the view.</span></span> <span data-ttu-id="1c7a8-110">Definisce i controlli personalizzati, come raggruppare gli oggetti e che specifica se la vista è out-of-band sono facoltativi.</span><span class="sxs-lookup"><span data-stu-id="1c7a8-110">Defining custom controls, how to group objects, and specifying if the view is out-of-band are optional.</span></span>

### <a name="attributes"></a><span data-ttu-id="1c7a8-111">Attributes</span><span class="sxs-lookup"><span data-stu-id="1c7a8-111">Attributes</span></span>

<span data-ttu-id="1c7a8-112">Nessuna.</span><span class="sxs-lookup"><span data-stu-id="1c7a8-112">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="1c7a8-113">Elementi figlio</span><span class="sxs-lookup"><span data-stu-id="1c7a8-113">Child Elements</span></span>

|<span data-ttu-id="1c7a8-114">Elemento</span><span class="sxs-lookup"><span data-stu-id="1c7a8-114">Element</span></span>|<span data-ttu-id="1c7a8-115">Description</span><span class="sxs-lookup"><span data-stu-id="1c7a8-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="1c7a8-116">Elemento Controls per visualizzazione (formato)</span><span class="sxs-lookup"><span data-stu-id="1c7a8-116">Controls Element for View (Format)</span></span>](./controls-element-for-view-format.md)|<span data-ttu-id="1c7a8-117">Elemento facoltativo.</span><span class="sxs-lookup"><span data-stu-id="1c7a8-117">Optional element.</span></span><br /><br /> <span data-ttu-id="1c7a8-118">Definisce un set di controlli che possono fare riferimento al nome all'interno della visualizzazione.</span><span class="sxs-lookup"><span data-stu-id="1c7a8-118">Defines a set of controls that can be referenced by their name from within the view.</span></span>|
|[<span data-ttu-id="1c7a8-119">Elemento CustomControl (formato)</span><span class="sxs-lookup"><span data-stu-id="1c7a8-119">CustomControl Element (Format)</span></span>](./customcontrol-element-for-groupby-format.md)|<span data-ttu-id="1c7a8-120">Elemento facoltativo.</span><span class="sxs-lookup"><span data-stu-id="1c7a8-120">Optional element.</span></span><br /><br /> <span data-ttu-id="1c7a8-121">Definisce un formato di controllo personalizzato per la visualizzazione.</span><span class="sxs-lookup"><span data-stu-id="1c7a8-121">Defines a custom control format for the view.</span></span>|
|[<span data-ttu-id="1c7a8-122">Elemento GroupBy per visualizzazione (formato)</span><span class="sxs-lookup"><span data-stu-id="1c7a8-122">GroupBy Element for View (Format)</span></span>](./groupby-element-for-view-format.md)|<span data-ttu-id="1c7a8-123">Elemento facoltativo.</span><span class="sxs-lookup"><span data-stu-id="1c7a8-123">Optional element.</span></span><br /><br /> <span data-ttu-id="1c7a8-124">Definisce la modalità di raggruppamento dei membri degli oggetti .NET.</span><span class="sxs-lookup"><span data-stu-id="1c7a8-124">Defines how the members of the .NET objects are grouped.</span></span>|
|[<span data-ttu-id="1c7a8-125">Elemento dell'oggetto ListControl (formato)</span><span class="sxs-lookup"><span data-stu-id="1c7a8-125">ListControl Element (Format)</span></span>](./listcontrol-element-format.md)|<span data-ttu-id="1c7a8-126">Elemento facoltativo.</span><span class="sxs-lookup"><span data-stu-id="1c7a8-126">Optional element.</span></span><br /><br /> <span data-ttu-id="1c7a8-127">Definisce un formato di elenco per la visualizzazione.</span><span class="sxs-lookup"><span data-stu-id="1c7a8-127">Defines a list format for the view.</span></span>|
|[<span data-ttu-id="1c7a8-128">Elemento Name per visualizzazione (formato)</span><span class="sxs-lookup"><span data-stu-id="1c7a8-128">Name Element for View (Format)</span></span>](./name-element-for-view-format.md)|<span data-ttu-id="1c7a8-129">Elemento obbligatorio.</span><span class="sxs-lookup"><span data-stu-id="1c7a8-129">Required element.</span></span><br /><br /> <span data-ttu-id="1c7a8-130">Specifica il nome utilizzato per fare riferimento la vista.</span><span class="sxs-lookup"><span data-stu-id="1c7a8-130">Specifies the name used to reference the view.</span></span>|
|[<span data-ttu-id="1c7a8-131">Elemento Table (formato)</span><span class="sxs-lookup"><span data-stu-id="1c7a8-131">TableControl Element (Format)</span></span>](./tablecontrol-element-format.md)|<span data-ttu-id="1c7a8-132">Elemento facoltativo.</span><span class="sxs-lookup"><span data-stu-id="1c7a8-132">Optional element.</span></span><br /><br /> <span data-ttu-id="1c7a8-133">Definisce un formato di tabella per la visualizzazione.</span><span class="sxs-lookup"><span data-stu-id="1c7a8-133">Defines a table format for the view.</span></span>|
|[<span data-ttu-id="1c7a8-134">Elemento ViewSelectedBy per visualizzazione (formato)</span><span class="sxs-lookup"><span data-stu-id="1c7a8-134">ViewSelectedBy Element for View (Format)</span></span>](./viewselectedby-element-format.md)|<span data-ttu-id="1c7a8-135">Elemento obbligatorio.</span><span class="sxs-lookup"><span data-stu-id="1c7a8-135">Required element.</span></span><br /><br /> <span data-ttu-id="1c7a8-136">Definisce gli oggetti .NET che consente di visualizzare.</span><span class="sxs-lookup"><span data-stu-id="1c7a8-136">Defines the .NET objects that this view displays.</span></span>|
|[<span data-ttu-id="1c7a8-137">Elemento WideControl (formato)</span><span class="sxs-lookup"><span data-stu-id="1c7a8-137">WideControl Element (Format)</span></span>](./widecontrol-element-format.md)|<span data-ttu-id="1c7a8-138">Elemento facoltativo.</span><span class="sxs-lookup"><span data-stu-id="1c7a8-138">Optional element.</span></span><br /><br /> <span data-ttu-id="1c7a8-139">Definisce un'ampia (valore singolo) formato di elenco per la visualizzazione.</span><span class="sxs-lookup"><span data-stu-id="1c7a8-139">Defines a wide (single value) list format for the view.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="1c7a8-140">Elementi padre</span><span class="sxs-lookup"><span data-stu-id="1c7a8-140">Parent Elements</span></span>

|<span data-ttu-id="1c7a8-141">Elemento</span><span class="sxs-lookup"><span data-stu-id="1c7a8-141">Element</span></span>|<span data-ttu-id="1c7a8-142">Description</span><span class="sxs-lookup"><span data-stu-id="1c7a8-142">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="1c7a8-143">Elemento ViewDefinitions (formato)</span><span class="sxs-lookup"><span data-stu-id="1c7a8-143">ViewDefinitions Element (Format)</span></span>](./viewdefinitions-element-format.md)|<span data-ttu-id="1c7a8-144">Definisce le viste utilizzate per visualizzare gli oggetti.</span><span class="sxs-lookup"><span data-stu-id="1c7a8-144">Defines the views used to display objects.</span></span>|

## <a name="remarks"></a><span data-ttu-id="1c7a8-145">Osservazioni</span><span class="sxs-lookup"><span data-stu-id="1c7a8-145">Remarks</span></span>

<span data-ttu-id="1c7a8-146">Per altre informazioni sui componenti di diverse visualizzazioni e i controlli personalizzati, vedere gli argomenti seguenti:</span><span class="sxs-lookup"><span data-stu-id="1c7a8-146">For more information about the components of different views and custom controls, see the following topics:</span></span>

- [<span data-ttu-id="1c7a8-147">Componenti di visualizzazione tabella</span><span class="sxs-lookup"><span data-stu-id="1c7a8-147">Table View Components</span></span>](./creating-a-table-view.md)

- [<span data-ttu-id="1c7a8-148">Componenti di visualizzazione elenco</span><span class="sxs-lookup"><span data-stu-id="1c7a8-148">List View Components</span></span>](./creating-a-list-view.md)

- [<span data-ttu-id="1c7a8-149">Componenti di visualizzazione estesa</span><span class="sxs-lookup"><span data-stu-id="1c7a8-149">Wide View Components</span></span>](./creating-a-wide-view.md)

- [<span data-ttu-id="1c7a8-150">Controlli personalizzati</span><span class="sxs-lookup"><span data-stu-id="1c7a8-150">Custom Controls</span></span>](./creating-custom-controls.md)

## <a name="example"></a><span data-ttu-id="1c7a8-151">Esempio</span><span class="sxs-lookup"><span data-stu-id="1c7a8-151">Example</span></span>

<span data-ttu-id="1c7a8-152">Questo esempio viene illustrato un `View` elemento che definisce una visualizzazione tabella per il [System.Serviceprocess.Servicecontroller](/dotnet/api/System.ServiceProcess.ServiceController) oggetto.</span><span class="sxs-lookup"><span data-stu-id="1c7a8-152">This example shows a `View` element that defines a table view for the [System.Serviceprocess.Servicecontroller](/dotnet/api/System.ServiceProcess.ServiceController) object.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="1c7a8-153">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="1c7a8-153">See Also</span></span>

[<span data-ttu-id="1c7a8-154">Elemento ViewDefinitions (formato)</span><span class="sxs-lookup"><span data-stu-id="1c7a8-154">ViewDefinitions Element (Format)</span></span>](./viewdefinitions-element-format.md)

[<span data-ttu-id="1c7a8-155">Elemento Name per visualizzazione (formato)</span><span class="sxs-lookup"><span data-stu-id="1c7a8-155">Name Element for View (Format)</span></span>](./name-element-for-view-format.md)

[<span data-ttu-id="1c7a8-156">Elemento ViewSelectedBy (formato)</span><span class="sxs-lookup"><span data-stu-id="1c7a8-156">ViewSelectedBy Element (Format)</span></span>](./viewselectedby-element-format.md)

[<span data-ttu-id="1c7a8-157">Elemento Controls per visualizzazione (formato)</span><span class="sxs-lookup"><span data-stu-id="1c7a8-157">Controls Element for View (Format)</span></span>](./controls-element-for-view-format.md)

[<span data-ttu-id="1c7a8-158">Elemento GroupBy per visualizzazione (formato)</span><span class="sxs-lookup"><span data-stu-id="1c7a8-158">GroupBy Element for View (Format)</span></span>](./groupby-element-for-view-format.md)

[<span data-ttu-id="1c7a8-159">Elemento Table (formato)</span><span class="sxs-lookup"><span data-stu-id="1c7a8-159">TableControl Element (Format)</span></span>](./tablecontrol-element-format.md)

[<span data-ttu-id="1c7a8-160">Elemento dell'oggetto ListControl (formato)</span><span class="sxs-lookup"><span data-stu-id="1c7a8-160">ListControl Element (Format)</span></span>](./listcontrol-element-format.md)

[<span data-ttu-id="1c7a8-161">Elemento WideControl (formato)</span><span class="sxs-lookup"><span data-stu-id="1c7a8-161">WideControl Element (Format)</span></span>](./widecontrol-element-format.md)

[<span data-ttu-id="1c7a8-162">Elemento CustomControl (formato)</span><span class="sxs-lookup"><span data-stu-id="1c7a8-162">CustomControl Element (Format)</span></span>](./customcontrol-element-for-groupby-format.md)

[<span data-ttu-id="1c7a8-163">La scrittura di un File di formattazione di PowerShell</span><span class="sxs-lookup"><span data-stu-id="1c7a8-163">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
