---
title: Elemento ListEntry per ListControl (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 6d16bca8-d025-432d-aa84-8b607b8af3ae
caps.latest.revision: 12
ms.openlocfilehash: 1a3bafd4ca94aee70e869c699f7a4ef8befc5511
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62065224"
---
# <a name="listentry-element-for-listcontrol-format"></a><span data-ttu-id="25bee-102">Elemento ListEntry per ListControl (formato)</span><span class="sxs-lookup"><span data-stu-id="25bee-102">ListEntry Element for ListControl (Format)</span></span>

<span data-ttu-id="25bee-103">Fornisce una definizione della visualizzazione elenco.</span><span class="sxs-lookup"><span data-stu-id="25bee-103">Provides a definition of the list view.</span></span>

<span data-ttu-id="25bee-104">Elemento (formato) elemento ViewDefinitions (formato) visualizzazione elemento (formato) dell'oggetto ListControl elemento (formato) elemento ListEntries (formato) ListEntry elemento di configurazione (formato)</span><span class="sxs-lookup"><span data-stu-id="25bee-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) ListControl Element (Format) ListEntries Element (Format) ListEntry Element (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="25bee-105">Sintassi</span><span class="sxs-lookup"><span data-stu-id="25bee-105">Syntax</span></span>

```xml
<ListEntry>
  <EntrySelectedBy>...</EntrySelectedBy>
  <ListItems>...</ListItems>
</ListEntry>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="25bee-106">Elementi e attributi</span><span class="sxs-lookup"><span data-stu-id="25bee-106">Attributes and Elements</span></span>

<span data-ttu-id="25bee-107">Le sezioni seguenti descrivono gli attributi e gli elementi figlio dell'elemento padre del `ListEntry` elemento.</span><span class="sxs-lookup"><span data-stu-id="25bee-107">The following sections describe the attributes, child elements, and the parent element of the `ListEntry` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="25bee-108">Attributes</span><span class="sxs-lookup"><span data-stu-id="25bee-108">Attributes</span></span>

<span data-ttu-id="25bee-109">Nessuna.</span><span class="sxs-lookup"><span data-stu-id="25bee-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="25bee-110">Elementi figlio</span><span class="sxs-lookup"><span data-stu-id="25bee-110">Child Elements</span></span>

|<span data-ttu-id="25bee-111">Elemento</span><span class="sxs-lookup"><span data-stu-id="25bee-111">Element</span></span>|<span data-ttu-id="25bee-112">Description</span><span class="sxs-lookup"><span data-stu-id="25bee-112">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="25bee-113">Elemento EntrySelectedBy per ListEntry (formato)</span><span class="sxs-lookup"><span data-stu-id="25bee-113">EntrySelectedBy Element for ListEntry (Format)</span></span>](./entryselectedby-element-for-listentry-for-listcontrol-format.md)|<span data-ttu-id="25bee-114">Elemento facoltativo.</span><span class="sxs-lookup"><span data-stu-id="25bee-114">Optional element.</span></span><br /><br /> <span data-ttu-id="25bee-115">Definisce gli oggetti .NET che usano questa definizione di visualizzazione elenco o la condizione che deve essere presente per questa definizione da usare.</span><span class="sxs-lookup"><span data-stu-id="25bee-115">Defines the .NET objects that use this list view definition or the condition that must exist for this definition to be used.</span></span>|
|[<span data-ttu-id="25bee-116">Elemento ListItems (formato)</span><span class="sxs-lookup"><span data-stu-id="25bee-116">ListItems Element (Format)</span></span>](./listitems-element-for-listentry-for-listcontrol-format.md)|<span data-ttu-id="25bee-117">Elemento obbligatorio.</span><span class="sxs-lookup"><span data-stu-id="25bee-117">Required element.</span></span><br /><br /> <span data-ttu-id="25bee-118">Definisce le proprietà e gli script i cui valori vengono visualizzati nella visualizzazione elenco.</span><span class="sxs-lookup"><span data-stu-id="25bee-118">Defines the properties and scripts whose values are displayed by the list view.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="25bee-119">Elementi padre</span><span class="sxs-lookup"><span data-stu-id="25bee-119">Parent Elements</span></span>

|<span data-ttu-id="25bee-120">Elemento</span><span class="sxs-lookup"><span data-stu-id="25bee-120">Element</span></span>|<span data-ttu-id="25bee-121">Description</span><span class="sxs-lookup"><span data-stu-id="25bee-121">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="25bee-122">Elemento ListEntries (formato)</span><span class="sxs-lookup"><span data-stu-id="25bee-122">ListEntries Element (Format)</span></span>](./listentries-element-for-listcontrol-format.md)|<span data-ttu-id="25bee-123">Fornisce le definizioni della visualizzazione elenco.</span><span class="sxs-lookup"><span data-stu-id="25bee-123">Provides the definitions of the list view.</span></span>|

## <a name="remarks"></a><span data-ttu-id="25bee-124">Osservazioni</span><span class="sxs-lookup"><span data-stu-id="25bee-124">Remarks</span></span>

<span data-ttu-id="25bee-125">Una visualizzazione elenco è un formato di elenco che consente di visualizzare valori di proprietà o script per ogni oggetto.</span><span class="sxs-lookup"><span data-stu-id="25bee-125">A list view is a list format that displays property values or script values for each object.</span></span> <span data-ttu-id="25bee-126">Per altre informazioni sulle visualizzazioni di elenco, vedere [creazione di una visualizzazione elenco](./creating-a-list-view.md).</span><span class="sxs-lookup"><span data-stu-id="25bee-126">For more information about list views, see [Creating a List View](./creating-a-list-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="25bee-127">Esempio</span><span class="sxs-lookup"><span data-stu-id="25bee-127">Example</span></span>

<span data-ttu-id="25bee-128">Questo esempio illustra gli elementi XML che definiscono la visualizzazione elenco per il [System.Serviceprocess.Servicecontroller](/dotnet/api/System.ServiceProcess.ServiceController) oggetto.</span><span class="sxs-lookup"><span data-stu-id="25bee-128">This example shows the XML elements that define the list view for the [System.Serviceprocess.Servicecontroller](/dotnet/api/System.ServiceProcess.ServiceController) object.</span></span>

```xml
<View>
  <Name>System.ServiceProcess.ServiceController</Name>
  <ViewSelectedBy>
    <TypeName>System.ServiceProcess.ServiceController</TypeName>
  </ViewSelectedBy>
  <ListControl>
    <ListEntries>
      <ListEntry>
        <ListItems>...</ListItems>
      </ListEntry>
    </ListEntries>
  </ListControl>
</View>
```

## <a name="see-also"></a><span data-ttu-id="25bee-129">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="25bee-129">See Also</span></span>

[<span data-ttu-id="25bee-130">Creazione di una visualizzazione elenco</span><span class="sxs-lookup"><span data-stu-id="25bee-130">Creating a List View</span></span>](./creating-a-list-view.md)

[<span data-ttu-id="25bee-131">Elemento EntrySelectedBy per ListEntry (formato)</span><span class="sxs-lookup"><span data-stu-id="25bee-131">EntrySelectedBy Element for ListEntry (Format)</span></span>](./entryselectedby-element-for-listentry-for-listcontrol-format.md)

[<span data-ttu-id="25bee-132">Elemento ListEntries (formato)</span><span class="sxs-lookup"><span data-stu-id="25bee-132">ListEntries Element (Format)</span></span>](./listentries-element-for-listcontrol-format.md)

[<span data-ttu-id="25bee-133">Elemento ListItems (formato)</span><span class="sxs-lookup"><span data-stu-id="25bee-133">ListItems Element (Format)</span></span>](./listitems-element-for-listentry-for-listcontrol-format.md)

[<span data-ttu-id="25bee-134">La scrittura di un metodo di formattazione di Windows PowerShell e i tipi di File</span><span class="sxs-lookup"><span data-stu-id="25bee-134">Writing a Windows PowerShell Formatting and Types File</span></span>](./writing-a-powershell-formatting-file.md)
