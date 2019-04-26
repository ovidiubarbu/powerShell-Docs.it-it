---
title: Elemento dell'oggetto ListControl (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 37beeb0b-7a81-4747-becb-e309e17278fb
caps.latest.revision: 12
ms.openlocfilehash: 7a117c25b0d117dc846ba8e060e31e838b5edd52
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62065258"
---
# <a name="listcontrol-element-format"></a><span data-ttu-id="6bab0-102">Elemento ListControl (formato)</span><span class="sxs-lookup"><span data-stu-id="6bab0-102">ListControl Element (Format)</span></span>

<span data-ttu-id="6bab0-103">Definisce un formato di elenco per la visualizzazione.</span><span class="sxs-lookup"><span data-stu-id="6bab0-103">Defines a list format for the view.</span></span>

<span data-ttu-id="6bab0-104">Configurazione (formato) elemento ViewDefinitions (formato) visualizzazione elemento (formato) dell'oggetto ListControl elemento (formato)</span><span class="sxs-lookup"><span data-stu-id="6bab0-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) ListControl Element (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="6bab0-105">Sintassi</span><span class="sxs-lookup"><span data-stu-id="6bab0-105">Syntax</span></span>

```xml
<ListControl>
  <ListEntries>...</ListEntries>
</ListControl>

```

## <a name="attributes-and-elements"></a><span data-ttu-id="6bab0-106">Elementi e attributi</span><span class="sxs-lookup"><span data-stu-id="6bab0-106">Attributes and Elements</span></span>

<span data-ttu-id="6bab0-107">Le sezioni seguenti descrivono gli attributi e gli elementi figlio dell'elemento padre del `ListControl` elemento.</span><span class="sxs-lookup"><span data-stu-id="6bab0-107">The following sections describe the attributes, child elements, and the parent element of the `ListControl` element.</span></span> <span data-ttu-id="6bab0-108">Questo elemento deve contenere solo un singolo elemento figlio.</span><span class="sxs-lookup"><span data-stu-id="6bab0-108">This element must contain only a single child element.</span></span>

### <a name="attributes"></a><span data-ttu-id="6bab0-109">Attributes</span><span class="sxs-lookup"><span data-stu-id="6bab0-109">Attributes</span></span>

<span data-ttu-id="6bab0-110">Nessuna.</span><span class="sxs-lookup"><span data-stu-id="6bab0-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="6bab0-111">Elementi figlio</span><span class="sxs-lookup"><span data-stu-id="6bab0-111">Child Elements</span></span>

|<span data-ttu-id="6bab0-112">Elemento</span><span class="sxs-lookup"><span data-stu-id="6bab0-112">Element</span></span>|<span data-ttu-id="6bab0-113">Description</span><span class="sxs-lookup"><span data-stu-id="6bab0-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="6bab0-114">Elemento ListEntries (formato)</span><span class="sxs-lookup"><span data-stu-id="6bab0-114">ListEntries Element (Format)</span></span>](./listentries-element-for-listcontrol-format.md)|<span data-ttu-id="6bab0-115">Elemento obbligatorio.</span><span class="sxs-lookup"><span data-stu-id="6bab0-115">Required element.</span></span><br /><br /> <span data-ttu-id="6bab0-116">Fornisce le definizioni della visualizzazione elenco.</span><span class="sxs-lookup"><span data-stu-id="6bab0-116">Provides the definitions of the list view.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="6bab0-117">Elementi padre</span><span class="sxs-lookup"><span data-stu-id="6bab0-117">Parent Elements</span></span>

|<span data-ttu-id="6bab0-118">Elemento</span><span class="sxs-lookup"><span data-stu-id="6bab0-118">Element</span></span>|<span data-ttu-id="6bab0-119">Description</span><span class="sxs-lookup"><span data-stu-id="6bab0-119">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="6bab0-120">Elemento di visualizzazione (formato)</span><span class="sxs-lookup"><span data-stu-id="6bab0-120">View Element (Format)</span></span>](./view-element-format.md)|<span data-ttu-id="6bab0-121">Definisce una vista che consente di visualizzare i membri di uno o più oggetti.</span><span class="sxs-lookup"><span data-stu-id="6bab0-121">Defines a view that is used to display the members of one or more objects.</span></span>|

## <a name="remarks"></a><span data-ttu-id="6bab0-122">Osservazioni</span><span class="sxs-lookup"><span data-stu-id="6bab0-122">Remarks</span></span>

<span data-ttu-id="6bab0-123">Per altre informazioni sulla creazione di una visualizzazione elenco, vedere [creazione di una visualizzazione elenco](./creating-a-list-view.md).</span><span class="sxs-lookup"><span data-stu-id="6bab0-123">For more information about creating a list view, see [Creating a List View](./creating-a-list-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="6bab0-124">Esempio</span><span class="sxs-lookup"><span data-stu-id="6bab0-124">Example</span></span>

<span data-ttu-id="6bab0-125">Questo esempio mostra una visualizzazione elenco per il [System.Serviceprocess.Servicecontroller](/dotnet/api/System.ServiceProcess.ServiceController) oggetto.</span><span class="sxs-lookup"><span data-stu-id="6bab0-125">This example shows a list view for the [System.Serviceprocess.Servicecontroller](/dotnet/api/System.ServiceProcess.ServiceController) object.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="6bab0-126">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="6bab0-126">See Also</span></span>

[<span data-ttu-id="6bab0-127">Elemento di visualizzazione (formato)</span><span class="sxs-lookup"><span data-stu-id="6bab0-127">View Element (Format)</span></span>](./view-element-format.md)

[<span data-ttu-id="6bab0-128">Elemento ListEntries (formato)</span><span class="sxs-lookup"><span data-stu-id="6bab0-128">ListEntries Element (Format)</span></span>](./listentries-element-for-listcontrol-format.md)

[<span data-ttu-id="6bab0-129">Creazione di una visualizzazione elenco</span><span class="sxs-lookup"><span data-stu-id="6bab0-129">Creating a List View</span></span>](./creating-a-list-view.md)

[<span data-ttu-id="6bab0-130">La scrittura di un metodo di formattazione di Windows PowerShell e i tipi di File</span><span class="sxs-lookup"><span data-stu-id="6bab0-130">Writing a Windows PowerShell Formatting and Types File</span></span>](./writing-a-powershell-formatting-file.md)
