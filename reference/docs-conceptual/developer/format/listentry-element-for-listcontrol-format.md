---
title: Elemento ListEntry per ListControl (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 6d16bca8-d025-432d-aa84-8b607b8af3ae
caps.latest.revision: 12
ms.openlocfilehash: 1a3bafd4ca94aee70e869c699f7a4ef8befc5511
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/15/2019
ms.locfileid: "72362750"
---
# <a name="listentry-element-for-listcontrol-format"></a><span data-ttu-id="de7df-102">Elemento ListEntry per ListControl (formato)</span><span class="sxs-lookup"><span data-stu-id="de7df-102">ListEntry Element for ListControl (Format)</span></span>

<span data-ttu-id="de7df-103">Fornisce una definizione della visualizzazione elenco.</span><span class="sxs-lookup"><span data-stu-id="de7df-103">Provides a definition of the list view.</span></span>

<span data-ttu-id="de7df-104">Elemento Configuration (Format) elemento ViewDefinitions (Format) elemento View (Format) elemento ListControl (Format) elemento ListEntries (Format) elemento ListEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="de7df-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) ListControl Element (Format) ListEntries Element (Format) ListEntry Element (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="de7df-105">Sintassi</span><span class="sxs-lookup"><span data-stu-id="de7df-105">Syntax</span></span>

```xml
<ListEntry>
  <EntrySelectedBy>...</EntrySelectedBy>
  <ListItems>...</ListItems>
</ListEntry>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="de7df-106">Attributi ed elementi</span><span class="sxs-lookup"><span data-stu-id="de7df-106">Attributes and Elements</span></span>

<span data-ttu-id="de7df-107">Nelle sezioni seguenti vengono descritti gli attributi, gli elementi figlio e l'elemento padre dell'elemento `ListEntry`.</span><span class="sxs-lookup"><span data-stu-id="de7df-107">The following sections describe the attributes, child elements, and the parent element of the `ListEntry` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="de7df-108">Attributi</span><span class="sxs-lookup"><span data-stu-id="de7df-108">Attributes</span></span>

<span data-ttu-id="de7df-109">Nessuna.</span><span class="sxs-lookup"><span data-stu-id="de7df-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="de7df-110">Elementi figlio</span><span class="sxs-lookup"><span data-stu-id="de7df-110">Child Elements</span></span>

|<span data-ttu-id="de7df-111">Elemento</span><span class="sxs-lookup"><span data-stu-id="de7df-111">Element</span></span>|<span data-ttu-id="de7df-112">Description</span><span class="sxs-lookup"><span data-stu-id="de7df-112">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="de7df-113">Elemento EntrySelectedBy per ListEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="de7df-113">EntrySelectedBy Element for ListEntry (Format)</span></span>](./entryselectedby-element-for-listentry-for-listcontrol-format.md)|<span data-ttu-id="de7df-114">Elemento facoltativo.</span><span class="sxs-lookup"><span data-stu-id="de7df-114">Optional element.</span></span><br /><br /> <span data-ttu-id="de7df-115">Definisce gli oggetti .NET che utilizzano questa definizione di visualizzazione elenco o la condizione che deve esistere affinché questa definizione venga utilizzata.</span><span class="sxs-lookup"><span data-stu-id="de7df-115">Defines the .NET objects that use this list view definition or the condition that must exist for this definition to be used.</span></span>|
|[<span data-ttu-id="de7df-116">Elemento ListItems (Format)</span><span class="sxs-lookup"><span data-stu-id="de7df-116">ListItems Element (Format)</span></span>](./listitems-element-for-listentry-for-listcontrol-format.md)|<span data-ttu-id="de7df-117">Elemento obbligatorio.</span><span class="sxs-lookup"><span data-stu-id="de7df-117">Required element.</span></span><br /><br /> <span data-ttu-id="de7df-118">Definisce le proprietà e gli script i cui valori vengono visualizzati dalla visualizzazione elenco.</span><span class="sxs-lookup"><span data-stu-id="de7df-118">Defines the properties and scripts whose values are displayed by the list view.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="de7df-119">Elementi padre</span><span class="sxs-lookup"><span data-stu-id="de7df-119">Parent Elements</span></span>

|<span data-ttu-id="de7df-120">Elemento</span><span class="sxs-lookup"><span data-stu-id="de7df-120">Element</span></span>|<span data-ttu-id="de7df-121">Description</span><span class="sxs-lookup"><span data-stu-id="de7df-121">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="de7df-122">Elemento ListEntries (Format)</span><span class="sxs-lookup"><span data-stu-id="de7df-122">ListEntries Element (Format)</span></span>](./listentries-element-for-listcontrol-format.md)|<span data-ttu-id="de7df-123">Fornisce le definizioni della visualizzazione elenco.</span><span class="sxs-lookup"><span data-stu-id="de7df-123">Provides the definitions of the list view.</span></span>|

## <a name="remarks"></a><span data-ttu-id="de7df-124">Osservazioni</span><span class="sxs-lookup"><span data-stu-id="de7df-124">Remarks</span></span>

<span data-ttu-id="de7df-125">Una visualizzazione elenco è un formato di elenco che consente di visualizzare i valori delle proprietà o i valori di script per ogni oggetto.</span><span class="sxs-lookup"><span data-stu-id="de7df-125">A list view is a list format that displays property values or script values for each object.</span></span> <span data-ttu-id="de7df-126">Per ulteriori informazioni sulle visualizzazioni elenco, vedere [creazione di una visualizzazione elenco](./creating-a-list-view.md).</span><span class="sxs-lookup"><span data-stu-id="de7df-126">For more information about list views, see [Creating a List View](./creating-a-list-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="de7df-127">Esempio</span><span class="sxs-lookup"><span data-stu-id="de7df-127">Example</span></span>

<span data-ttu-id="de7df-128">Questo esempio Mostra gli elementi XML che definiscono la visualizzazione elenco per l'oggetto [System. ServiceProcess. ServiceController](/dotnet/api/System.ServiceProcess.ServiceController) .</span><span class="sxs-lookup"><span data-stu-id="de7df-128">This example shows the XML elements that define the list view for the [System.Serviceprocess.Servicecontroller](/dotnet/api/System.ServiceProcess.ServiceController) object.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="de7df-129">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="de7df-129">See Also</span></span>

[<span data-ttu-id="de7df-130">Creazione di una visualizzazione elenco</span><span class="sxs-lookup"><span data-stu-id="de7df-130">Creating a List View</span></span>](./creating-a-list-view.md)

[<span data-ttu-id="de7df-131">Elemento EntrySelectedBy per ListEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="de7df-131">EntrySelectedBy Element for ListEntry (Format)</span></span>](./entryselectedby-element-for-listentry-for-listcontrol-format.md)

[<span data-ttu-id="de7df-132">Elemento ListEntries (Format)</span><span class="sxs-lookup"><span data-stu-id="de7df-132">ListEntries Element (Format)</span></span>](./listentries-element-for-listcontrol-format.md)

[<span data-ttu-id="de7df-133">Elemento ListItems (Format)</span><span class="sxs-lookup"><span data-stu-id="de7df-133">ListItems Element (Format)</span></span>](./listitems-element-for-listentry-for-listcontrol-format.md)

[<span data-ttu-id="de7df-134">Scrittura di un file di formattazione e di tipi di Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="de7df-134">Writing a Windows PowerShell Formatting and Types File</span></span>](./writing-a-powershell-formatting-file.md)