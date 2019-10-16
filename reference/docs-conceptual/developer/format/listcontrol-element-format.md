---
title: Elemento ListControl (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 37beeb0b-7a81-4747-becb-e309e17278fb
caps.latest.revision: 12
ms.openlocfilehash: 7a117c25b0d117dc846ba8e060e31e838b5edd52
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/15/2019
ms.locfileid: "72362780"
---
# <a name="listcontrol-element-format"></a><span data-ttu-id="59c27-102">Elemento ListControl (formato)</span><span class="sxs-lookup"><span data-stu-id="59c27-102">ListControl Element (Format)</span></span>

<span data-ttu-id="59c27-103">Definisce un formato di elenco per la visualizzazione.</span><span class="sxs-lookup"><span data-stu-id="59c27-103">Defines a list format for the view.</span></span>

<span data-ttu-id="59c27-104">Elemento Configuration (Format) elemento ViewDefinitions (Format) elemento View (Format) elemento ListControl (Format)</span><span class="sxs-lookup"><span data-stu-id="59c27-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) ListControl Element (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="59c27-105">Sintassi</span><span class="sxs-lookup"><span data-stu-id="59c27-105">Syntax</span></span>

```xml
<ListControl>
  <ListEntries>...</ListEntries>
</ListControl>

```

## <a name="attributes-and-elements"></a><span data-ttu-id="59c27-106">Attributi ed elementi</span><span class="sxs-lookup"><span data-stu-id="59c27-106">Attributes and Elements</span></span>

<span data-ttu-id="59c27-107">Nelle sezioni seguenti vengono descritti gli attributi, gli elementi figlio e l'elemento padre dell'elemento `ListControl`.</span><span class="sxs-lookup"><span data-stu-id="59c27-107">The following sections describe the attributes, child elements, and the parent element of the `ListControl` element.</span></span> <span data-ttu-id="59c27-108">Questo elemento deve contenere solo un singolo elemento figlio.</span><span class="sxs-lookup"><span data-stu-id="59c27-108">This element must contain only a single child element.</span></span>

### <a name="attributes"></a><span data-ttu-id="59c27-109">Attributi</span><span class="sxs-lookup"><span data-stu-id="59c27-109">Attributes</span></span>

<span data-ttu-id="59c27-110">Nessuna.</span><span class="sxs-lookup"><span data-stu-id="59c27-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="59c27-111">Elementi figlio</span><span class="sxs-lookup"><span data-stu-id="59c27-111">Child Elements</span></span>

|<span data-ttu-id="59c27-112">Elemento</span><span class="sxs-lookup"><span data-stu-id="59c27-112">Element</span></span>|<span data-ttu-id="59c27-113">Description</span><span class="sxs-lookup"><span data-stu-id="59c27-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="59c27-114">Elemento ListEntries (Format)</span><span class="sxs-lookup"><span data-stu-id="59c27-114">ListEntries Element (Format)</span></span>](./listentries-element-for-listcontrol-format.md)|<span data-ttu-id="59c27-115">Elemento obbligatorio.</span><span class="sxs-lookup"><span data-stu-id="59c27-115">Required element.</span></span><br /><br /> <span data-ttu-id="59c27-116">Fornisce le definizioni della visualizzazione elenco.</span><span class="sxs-lookup"><span data-stu-id="59c27-116">Provides the definitions of the list view.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="59c27-117">Elementi padre</span><span class="sxs-lookup"><span data-stu-id="59c27-117">Parent Elements</span></span>

|<span data-ttu-id="59c27-118">Elemento</span><span class="sxs-lookup"><span data-stu-id="59c27-118">Element</span></span>|<span data-ttu-id="59c27-119">Description</span><span class="sxs-lookup"><span data-stu-id="59c27-119">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="59c27-120">Elemento View (Format)</span><span class="sxs-lookup"><span data-stu-id="59c27-120">View Element (Format)</span></span>](./view-element-format.md)|<span data-ttu-id="59c27-121">Definisce una vista utilizzata per visualizzare i membri di uno o più oggetti.</span><span class="sxs-lookup"><span data-stu-id="59c27-121">Defines a view that is used to display the members of one or more objects.</span></span>|

## <a name="remarks"></a><span data-ttu-id="59c27-122">Osservazioni</span><span class="sxs-lookup"><span data-stu-id="59c27-122">Remarks</span></span>

<span data-ttu-id="59c27-123">Per ulteriori informazioni sulla creazione di una visualizzazione elenco, vedere [creazione di una visualizzazione elenco](./creating-a-list-view.md).</span><span class="sxs-lookup"><span data-stu-id="59c27-123">For more information about creating a list view, see [Creating a List View](./creating-a-list-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="59c27-124">Esempio</span><span class="sxs-lookup"><span data-stu-id="59c27-124">Example</span></span>

<span data-ttu-id="59c27-125">Questo esempio mostra una visualizzazione elenco per l'oggetto [System. ServiceProcess. ServiceController](/dotnet/api/System.ServiceProcess.ServiceController) .</span><span class="sxs-lookup"><span data-stu-id="59c27-125">This example shows a list view for the [System.Serviceprocess.Servicecontroller](/dotnet/api/System.ServiceProcess.ServiceController) object.</span></span>

```
<View>
  <Name>System.ServiceProcess.ServiceController</Name>
  <ViewSelectedBy>
    <TypeName>System.ServiceProcess.ServiceController</TypeName>
  </ViewSelectedBy>
  <ListControl>
    <ListEntries>
      <ListEntry>...</ListEntry>
    </ListEntries>
  </ListControl>
</View>
```

## <a name="see-also"></a><span data-ttu-id="59c27-126">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="59c27-126">See Also</span></span>

[<span data-ttu-id="59c27-127">Elemento View (Format)</span><span class="sxs-lookup"><span data-stu-id="59c27-127">View Element (Format)</span></span>](./view-element-format.md)

[<span data-ttu-id="59c27-128">Elemento ListEntries (Format)</span><span class="sxs-lookup"><span data-stu-id="59c27-128">ListEntries Element (Format)</span></span>](./listentries-element-for-listcontrol-format.md)

[<span data-ttu-id="59c27-129">Creazione di una visualizzazione elenco</span><span class="sxs-lookup"><span data-stu-id="59c27-129">Creating a List View</span></span>](./creating-a-list-view.md)

[<span data-ttu-id="59c27-130">Scrittura di un file di formattazione e di tipi di Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="59c27-130">Writing a Windows PowerShell Formatting and Types File</span></span>](./writing-a-powershell-formatting-file.md)
