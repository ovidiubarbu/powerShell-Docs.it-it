---
title: Elemento ListEntries per ListControl (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: b62e81cc-4175-40fa-829f-634245b09f86
caps.latest.revision: 12
ms.openlocfilehash: aaf16702e485135b5299ccb43a2b62db2d9f5762
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/15/2019
ms.locfileid: "72362760"
---
# <a name="listentries-element-for-listcontrol-format"></a><span data-ttu-id="34ce5-102">Elemento ListEntries per ListControl (formato)</span><span class="sxs-lookup"><span data-stu-id="34ce5-102">ListEntries Element for ListControl (Format)</span></span>

<span data-ttu-id="34ce5-103">Fornisce le definizioni della visualizzazione elenco.</span><span class="sxs-lookup"><span data-stu-id="34ce5-103">Provides the definitions of the list view.</span></span> <span data-ttu-id="34ce5-104">Nella visualizzazione elenco è necessario specificare una o più definizioni.</span><span class="sxs-lookup"><span data-stu-id="34ce5-104">The list view must specify one or more definitions.</span></span>

<span data-ttu-id="34ce5-105">Elemento Configuration (Format) elemento ViewDefinitions (Format) elemento View (Format) elemento ListControl (Format) elemento ListEntries (Format)</span><span class="sxs-lookup"><span data-stu-id="34ce5-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) ListControl Element (Format) ListEntries Element (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="34ce5-106">Sintassi</span><span class="sxs-lookup"><span data-stu-id="34ce5-106">Syntax</span></span>

```xml
<ListEntries>
  <ListEntry>...</ListEntry>
</ListEntries>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="34ce5-107">Attributi ed elementi</span><span class="sxs-lookup"><span data-stu-id="34ce5-107">Attributes and Elements</span></span>

<span data-ttu-id="34ce5-108">Nelle sezioni seguenti vengono descritti gli attributi, gli elementi figlio e l'elemento padre dell'elemento `ListEntries`.</span><span class="sxs-lookup"><span data-stu-id="34ce5-108">The following sections describe the attributes, child elements, and the parent element of the `ListEntries` element.</span></span> <span data-ttu-id="34ce5-109">È necessario specificare almeno un elemento figlio.</span><span class="sxs-lookup"><span data-stu-id="34ce5-109">At least one child element must be specified.</span></span>

### <a name="attributes"></a><span data-ttu-id="34ce5-110">Attributi</span><span class="sxs-lookup"><span data-stu-id="34ce5-110">Attributes</span></span>

<span data-ttu-id="34ce5-111">Nessuna.</span><span class="sxs-lookup"><span data-stu-id="34ce5-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="34ce5-112">Elementi figlio</span><span class="sxs-lookup"><span data-stu-id="34ce5-112">Child Elements</span></span>

|<span data-ttu-id="34ce5-113">Elemento</span><span class="sxs-lookup"><span data-stu-id="34ce5-113">Element</span></span>|<span data-ttu-id="34ce5-114">Description</span><span class="sxs-lookup"><span data-stu-id="34ce5-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="34ce5-115">Elemento ListEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="34ce5-115">ListEntry Element (Format)</span></span>](./listentry-element-for-listcontrol-format.md)|<span data-ttu-id="34ce5-116">Fornisce una definizione della visualizzazione elenco.</span><span class="sxs-lookup"><span data-stu-id="34ce5-116">Provides a definition of the list view.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="34ce5-117">Elementi padre</span><span class="sxs-lookup"><span data-stu-id="34ce5-117">Parent Elements</span></span>

|<span data-ttu-id="34ce5-118">Elemento</span><span class="sxs-lookup"><span data-stu-id="34ce5-118">Element</span></span>|<span data-ttu-id="34ce5-119">Description</span><span class="sxs-lookup"><span data-stu-id="34ce5-119">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="34ce5-120">Elemento ListControl (Format)</span><span class="sxs-lookup"><span data-stu-id="34ce5-120">ListControl Element (Format)</span></span>](./listcontrol-element-format.md)|<span data-ttu-id="34ce5-121">Definisce un formato di elenco per la visualizzazione.</span><span class="sxs-lookup"><span data-stu-id="34ce5-121">Defines a list format for the view.</span></span>|

## <a name="remarks"></a><span data-ttu-id="34ce5-122">Osservazioni</span><span class="sxs-lookup"><span data-stu-id="34ce5-122">Remarks</span></span>

<span data-ttu-id="34ce5-123">Per ulteriori informazioni sulle visualizzazioni elenco, vedere [visualizzazione elenco](./creating-a-list-view.md).</span><span class="sxs-lookup"><span data-stu-id="34ce5-123">For more information about list views, see [List View](./creating-a-list-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="34ce5-124">Esempio</span><span class="sxs-lookup"><span data-stu-id="34ce5-124">Example</span></span>

<span data-ttu-id="34ce5-125">Questo esempio Mostra gli elementi XML che definiscono la visualizzazione elenco per l'oggetto [System. ServiceProcess. ServiceController](/dotnet/api/System.ServiceProcess.ServiceController) .</span><span class="sxs-lookup"><span data-stu-id="34ce5-125">This example shows the XML elements that define the list view for the [System.Serviceprocess.Servicecontroller](/dotnet/api/System.ServiceProcess.ServiceController) object.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="34ce5-126">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="34ce5-126">See Also</span></span>

[<span data-ttu-id="34ce5-127">Elemento ListControl (Format)</span><span class="sxs-lookup"><span data-stu-id="34ce5-127">ListControl Element (Format)</span></span>](./listcontrol-element-format.md)

[<span data-ttu-id="34ce5-128">Elemento ListEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="34ce5-128">ListEntry Element (Format)</span></span>](./listentry-element-for-listcontrol-format.md)

[<span data-ttu-id="34ce5-129">Visualizzazione elenco</span><span class="sxs-lookup"><span data-stu-id="34ce5-129">List View</span></span>](./creating-a-list-view.md)

[<span data-ttu-id="34ce5-130">Scrittura di un file di formattazione e di tipi di Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="34ce5-130">Writing a Windows PowerShell Formatting and Types File</span></span>](./writing-a-powershell-formatting-file.md)
