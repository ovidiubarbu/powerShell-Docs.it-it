---
title: Elemento ListEntries per ListControl (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: b62e81cc-4175-40fa-829f-634245b09f86
caps.latest.revision: 12
ms.openlocfilehash: aaf16702e485135b5299ccb43a2b62db2d9f5762
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62065394"
---
# <a name="listentries-element-for-listcontrol-format"></a><span data-ttu-id="38bbc-102">Elemento ListEntries per ListControl (formato)</span><span class="sxs-lookup"><span data-stu-id="38bbc-102">ListEntries Element for ListControl (Format)</span></span>

<span data-ttu-id="38bbc-103">Fornisce le definizioni della visualizzazione elenco.</span><span class="sxs-lookup"><span data-stu-id="38bbc-103">Provides the definitions of the list view.</span></span> <span data-ttu-id="38bbc-104">La visualizzazione elenco è necessario specificare una o più definizioni.</span><span class="sxs-lookup"><span data-stu-id="38bbc-104">The list view must specify one or more definitions.</span></span>

<span data-ttu-id="38bbc-105">Elemento (formato) elemento ViewDefinitions (formato) visualizzazione elemento (formato) dell'oggetto ListControl elemento (formato) ListEntries elemento di configurazione (formato)</span><span class="sxs-lookup"><span data-stu-id="38bbc-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) ListControl Element (Format) ListEntries Element (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="38bbc-106">Sintassi</span><span class="sxs-lookup"><span data-stu-id="38bbc-106">Syntax</span></span>

```xml
<ListEntries>
  <ListEntry>...</ListEntry>
</ListEntries>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="38bbc-107">Elementi e attributi</span><span class="sxs-lookup"><span data-stu-id="38bbc-107">Attributes and Elements</span></span>

<span data-ttu-id="38bbc-108">Le sezioni seguenti descrivono gli attributi e gli elementi figlio dell'elemento padre del `ListEntries` elemento.</span><span class="sxs-lookup"><span data-stu-id="38bbc-108">The following sections describe the attributes, child elements, and the parent element of the `ListEntries` element.</span></span> <span data-ttu-id="38bbc-109">È necessario specificare almeno un elemento figlio.</span><span class="sxs-lookup"><span data-stu-id="38bbc-109">At least one child element must be specified.</span></span>

### <a name="attributes"></a><span data-ttu-id="38bbc-110">Attributes</span><span class="sxs-lookup"><span data-stu-id="38bbc-110">Attributes</span></span>

<span data-ttu-id="38bbc-111">Nessuna.</span><span class="sxs-lookup"><span data-stu-id="38bbc-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="38bbc-112">Elementi figlio</span><span class="sxs-lookup"><span data-stu-id="38bbc-112">Child Elements</span></span>

|<span data-ttu-id="38bbc-113">Elemento</span><span class="sxs-lookup"><span data-stu-id="38bbc-113">Element</span></span>|<span data-ttu-id="38bbc-114">Description</span><span class="sxs-lookup"><span data-stu-id="38bbc-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="38bbc-115">Elemento ListEntry (formato)</span><span class="sxs-lookup"><span data-stu-id="38bbc-115">ListEntry Element (Format)</span></span>](./listentry-element-for-listcontrol-format.md)|<span data-ttu-id="38bbc-116">Fornisce una definizione della visualizzazione elenco.</span><span class="sxs-lookup"><span data-stu-id="38bbc-116">Provides a definition of the list view.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="38bbc-117">Elementi padre</span><span class="sxs-lookup"><span data-stu-id="38bbc-117">Parent Elements</span></span>

|<span data-ttu-id="38bbc-118">Elemento</span><span class="sxs-lookup"><span data-stu-id="38bbc-118">Element</span></span>|<span data-ttu-id="38bbc-119">Description</span><span class="sxs-lookup"><span data-stu-id="38bbc-119">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="38bbc-120">Elemento dell'oggetto ListControl (formato)</span><span class="sxs-lookup"><span data-stu-id="38bbc-120">ListControl Element (Format)</span></span>](./listcontrol-element-format.md)|<span data-ttu-id="38bbc-121">Definisce un formato di elenco per la visualizzazione.</span><span class="sxs-lookup"><span data-stu-id="38bbc-121">Defines a list format for the view.</span></span>|

## <a name="remarks"></a><span data-ttu-id="38bbc-122">Osservazioni</span><span class="sxs-lookup"><span data-stu-id="38bbc-122">Remarks</span></span>

<span data-ttu-id="38bbc-123">Per altre informazioni sulle visualizzazioni di elenco, vedere [visualizzazione elenco](./creating-a-list-view.md).</span><span class="sxs-lookup"><span data-stu-id="38bbc-123">For more information about list views, see [List View](./creating-a-list-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="38bbc-124">Esempio</span><span class="sxs-lookup"><span data-stu-id="38bbc-124">Example</span></span>

<span data-ttu-id="38bbc-125">Questo esempio illustra gli elementi XML che definiscono la visualizzazione elenco per il [System.Serviceprocess.Servicecontroller](/dotnet/api/System.ServiceProcess.ServiceController) oggetto.</span><span class="sxs-lookup"><span data-stu-id="38bbc-125">This example shows the XML elements that define the list view for the [System.Serviceprocess.Servicecontroller](/dotnet/api/System.ServiceProcess.ServiceController) object.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="38bbc-126">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="38bbc-126">See Also</span></span>

[<span data-ttu-id="38bbc-127">Elemento dell'oggetto ListControl (formato)</span><span class="sxs-lookup"><span data-stu-id="38bbc-127">ListControl Element (Format)</span></span>](./listcontrol-element-format.md)

[<span data-ttu-id="38bbc-128">Elemento ListEntry (formato)</span><span class="sxs-lookup"><span data-stu-id="38bbc-128">ListEntry Element (Format)</span></span>](./listentry-element-for-listcontrol-format.md)

[<span data-ttu-id="38bbc-129">Visualizzazione elenco</span><span class="sxs-lookup"><span data-stu-id="38bbc-129">List View</span></span>](./creating-a-list-view.md)

[<span data-ttu-id="38bbc-130">La scrittura di un metodo di formattazione di Windows PowerShell e i tipi di File</span><span class="sxs-lookup"><span data-stu-id="38bbc-130">Writing a Windows PowerShell Formatting and Types File</span></span>](./writing-a-powershell-formatting-file.md)
