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
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/03/2019
ms.locfileid: "56856787"
---
# <a name="listentries-element-for-listcontrol-format"></a><span data-ttu-id="f97b2-102">Elemento ListEntries per ListControl (formato)</span><span class="sxs-lookup"><span data-stu-id="f97b2-102">ListEntries Element for ListControl (Format)</span></span>

<span data-ttu-id="f97b2-103">Fornisce le definizioni della visualizzazione elenco.</span><span class="sxs-lookup"><span data-stu-id="f97b2-103">Provides the definitions of the list view.</span></span> <span data-ttu-id="f97b2-104">La visualizzazione elenco è necessario specificare una o più definizioni.</span><span class="sxs-lookup"><span data-stu-id="f97b2-104">The list view must specify one or more definitions.</span></span>

<span data-ttu-id="f97b2-105">Elemento (formato) elemento ViewDefinitions (formato) visualizzazione elemento (formato) dell'oggetto ListControl elemento (formato) ListEntries elemento di configurazione (formato)</span><span class="sxs-lookup"><span data-stu-id="f97b2-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) ListControl Element (Format) ListEntries Element (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="f97b2-106">Sintassi</span><span class="sxs-lookup"><span data-stu-id="f97b2-106">Syntax</span></span>

```xml
<ListEntries>
  <ListEntry>...</ListEntry>
</ListEntries>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="f97b2-107">Attributi ed elementi</span><span class="sxs-lookup"><span data-stu-id="f97b2-107">Attributes and Elements</span></span>

<span data-ttu-id="f97b2-108">Le sezioni seguenti descrivono gli attributi e gli elementi figlio dell'elemento padre del `ListEntries` elemento.</span><span class="sxs-lookup"><span data-stu-id="f97b2-108">The following sections describe the attributes, child elements, and the parent element of the `ListEntries` element.</span></span> <span data-ttu-id="f97b2-109">È necessario specificare almeno un elemento figlio.</span><span class="sxs-lookup"><span data-stu-id="f97b2-109">At least one child element must be specified.</span></span>

### <a name="attributes"></a><span data-ttu-id="f97b2-110">Attributes</span><span class="sxs-lookup"><span data-stu-id="f97b2-110">Attributes</span></span>

<span data-ttu-id="f97b2-111">Nessuna.</span><span class="sxs-lookup"><span data-stu-id="f97b2-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="f97b2-112">Elementi figlio</span><span class="sxs-lookup"><span data-stu-id="f97b2-112">Child Elements</span></span>

|<span data-ttu-id="f97b2-113">Elemento</span><span class="sxs-lookup"><span data-stu-id="f97b2-113">Element</span></span>|<span data-ttu-id="f97b2-114">Description</span><span class="sxs-lookup"><span data-stu-id="f97b2-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="f97b2-115">Elemento ListEntry (formato)</span><span class="sxs-lookup"><span data-stu-id="f97b2-115">ListEntry Element (Format)</span></span>](./listentry-element-for-listcontrol-format.md)|<span data-ttu-id="f97b2-116">Fornisce una definizione della visualizzazione elenco.</span><span class="sxs-lookup"><span data-stu-id="f97b2-116">Provides a definition of the list view.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="f97b2-117">Elementi padre</span><span class="sxs-lookup"><span data-stu-id="f97b2-117">Parent Elements</span></span>

|<span data-ttu-id="f97b2-118">Elemento</span><span class="sxs-lookup"><span data-stu-id="f97b2-118">Element</span></span>|<span data-ttu-id="f97b2-119">Description</span><span class="sxs-lookup"><span data-stu-id="f97b2-119">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="f97b2-120">Elemento dell'oggetto ListControl (formato)</span><span class="sxs-lookup"><span data-stu-id="f97b2-120">ListControl Element (Format)</span></span>](./listcontrol-element-format.md)|<span data-ttu-id="f97b2-121">Definisce un formato di elenco per la visualizzazione.</span><span class="sxs-lookup"><span data-stu-id="f97b2-121">Defines a list format for the view.</span></span>|

## <a name="remarks"></a><span data-ttu-id="f97b2-122">Osservazioni</span><span class="sxs-lookup"><span data-stu-id="f97b2-122">Remarks</span></span>

<span data-ttu-id="f97b2-123">Per altre informazioni sulle visualizzazioni di elenco, vedere [visualizzazione elenco](./creating-a-list-view.md).</span><span class="sxs-lookup"><span data-stu-id="f97b2-123">For more information about list views, see [List View](./creating-a-list-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="f97b2-124">Esempio</span><span class="sxs-lookup"><span data-stu-id="f97b2-124">Example</span></span>

<span data-ttu-id="f97b2-125">Questo esempio illustra gli elementi XML che definiscono la visualizzazione elenco per il [System.Serviceprocess.Servicecontroller](/dotnet/api/System.ServiceProcess.ServiceController) oggetto.</span><span class="sxs-lookup"><span data-stu-id="f97b2-125">This example shows the XML elements that define the list view for the [System.Serviceprocess.Servicecontroller](/dotnet/api/System.ServiceProcess.ServiceController) object.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="f97b2-126">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="f97b2-126">See Also</span></span>

[<span data-ttu-id="f97b2-127">Elemento dell'oggetto ListControl (formato)</span><span class="sxs-lookup"><span data-stu-id="f97b2-127">ListControl Element (Format)</span></span>](./listcontrol-element-format.md)

[<span data-ttu-id="f97b2-128">Elemento ListEntry (formato)</span><span class="sxs-lookup"><span data-stu-id="f97b2-128">ListEntry Element (Format)</span></span>](./listentry-element-for-listcontrol-format.md)

[<span data-ttu-id="f97b2-129">Visualizzazione elenco</span><span class="sxs-lookup"><span data-stu-id="f97b2-129">List View</span></span>](./creating-a-list-view.md)

[<span data-ttu-id="f97b2-130">La scrittura di un metodo di formattazione di Windows PowerShell e i tipi di File</span><span class="sxs-lookup"><span data-stu-id="f97b2-130">Writing a Windows PowerShell Formatting and Types File</span></span>](./writing-a-powershell-formatting-file.md)
