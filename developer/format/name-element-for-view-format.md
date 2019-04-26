---
title: Nome elemento di visualizzazione (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 3a31010d-1db9-44ae-a7f3-6ed32cb641cb
caps.latest.revision: 16
ms.openlocfilehash: 097d20cb6a04635124d1f96823248df6095ca1af
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62065071"
---
# <a name="name-element-for-view-format"></a><span data-ttu-id="224c6-102">Elemento Name per View (formato)</span><span class="sxs-lookup"><span data-stu-id="224c6-102">Name Element for View (Format)</span></span>

<span data-ttu-id="224c6-103">Specifica il nome utilizzato per identificare la vista.</span><span class="sxs-lookup"><span data-stu-id="224c6-103">Specifies the name that is used to identify the view.</span></span>

<span data-ttu-id="224c6-104">Configurazione elemento (formato) elemento ViewDefinitions (formato) visualizzazione elemento (formato) elemento Name (formato)</span><span class="sxs-lookup"><span data-stu-id="224c6-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) Name Element (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="224c6-105">Sintassi</span><span class="sxs-lookup"><span data-stu-id="224c6-105">Syntax</span></span>

```xml
<Name>ViewName</Name>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="224c6-106">Elementi e attributi</span><span class="sxs-lookup"><span data-stu-id="224c6-106">Attributes and Elements</span></span>

<span data-ttu-id="224c6-107">Le sezioni seguenti descrivono gli attributi e gli elementi figlio dell'elemento padre del `Name` elemento.</span><span class="sxs-lookup"><span data-stu-id="224c6-107">The following sections describe attributes, child elements, and the parent element of the `Name` element.</span></span> <span data-ttu-id="224c6-108">Un solo `Name` l'elemento è consentito per ogni visualizzazione.</span><span class="sxs-lookup"><span data-stu-id="224c6-108">Only one `Name` element is allowed for each view.</span></span>

### <a name="attributes"></a><span data-ttu-id="224c6-109">Attributes</span><span class="sxs-lookup"><span data-stu-id="224c6-109">Attributes</span></span>

<span data-ttu-id="224c6-110">Nessuna.</span><span class="sxs-lookup"><span data-stu-id="224c6-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="224c6-111">Elementi figlio</span><span class="sxs-lookup"><span data-stu-id="224c6-111">Child Elements</span></span>

<span data-ttu-id="224c6-112">Nessuna.</span><span class="sxs-lookup"><span data-stu-id="224c6-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="224c6-113">Elementi padre</span><span class="sxs-lookup"><span data-stu-id="224c6-113">Parent Elements</span></span>

|<span data-ttu-id="224c6-114">Elemento</span><span class="sxs-lookup"><span data-stu-id="224c6-114">Element</span></span>|<span data-ttu-id="224c6-115">Description</span><span class="sxs-lookup"><span data-stu-id="224c6-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="224c6-116">Elemento di visualizzazione (formato)</span><span class="sxs-lookup"><span data-stu-id="224c6-116">View Element (Format)</span></span>](./view-element-format.md)|<span data-ttu-id="224c6-117">Definisce una vista che consente di visualizzare i membri di uno o più oggetti .NET.</span><span class="sxs-lookup"><span data-stu-id="224c6-117">Defines a view that is used to display the members of one or more .NET objects.</span></span>|

## <a name="text-value"></a><span data-ttu-id="224c6-118">Valore di testo</span><span class="sxs-lookup"><span data-stu-id="224c6-118">Text Value</span></span>

<span data-ttu-id="224c6-119">Specificare un nome descrittivo univoco per la visualizzazione.</span><span class="sxs-lookup"><span data-stu-id="224c6-119">Specify a unique friendly name for the view.</span></span> <span data-ttu-id="224c6-120">Questo nome può includere un riferimento al tipo della visualizzazione (ad esempio una tabella o una vista elenco), quale oggetto o un set di oggetti di usare la vista, il comando restituisce gli oggetti o una combinazione di questi.</span><span class="sxs-lookup"><span data-stu-id="224c6-120">This name can include a reference to the type of the view (such as a table view or list view), which object or set of objects use the view, what command returns the objects, or a combination of these.</span></span>

## <a name="remarks"></a><span data-ttu-id="224c6-121">Osservazioni</span><span class="sxs-lookup"><span data-stu-id="224c6-121">Remarks</span></span>

<span data-ttu-id="224c6-122">Per altre informazioni sui diversi tipi di visualizzazioni, vedere gli argomenti seguenti: [Visualizzazione di una tabella](./creating-a-table-view.md), [visualizzazione elenco](./creating-a-list-view.md), [visualizzazione estesa](./creating-a-wide-view.md), e [visualizzazione personalizzata](./creating-custom-controls.md).</span><span class="sxs-lookup"><span data-stu-id="224c6-122">For more information about the different types of views, see the following topics: [Table View](./creating-a-table-view.md), [List View](./creating-a-list-view.md), [Wide View](./creating-a-wide-view.md), and [Custom View](./creating-custom-controls.md).</span></span>

## <a name="example"></a><span data-ttu-id="224c6-123">Esempio</span><span class="sxs-lookup"><span data-stu-id="224c6-123">Example</span></span>

<span data-ttu-id="224c6-124">L'esempio seguente mostra una `View` elemento che definisce una visualizzazione tabella per il [System.Serviceprocess.Servicecontroller](/dotnet/api/System.ServiceProcess.ServiceController) oggetto.</span><span class="sxs-lookup"><span data-stu-id="224c6-124">The following example shows a `View` element that defines a table view for the [System.Serviceprocess.Servicecontroller](/dotnet/api/System.ServiceProcess.ServiceController) object.</span></span> <span data-ttu-id="224c6-125">Il nome della visualizzazione è "servizio".</span><span class="sxs-lookup"><span data-stu-id="224c6-125">The name of the view is "service".</span></span>

```xml
<View>
  <Name>service</Name>
  <ViewSelectedBy>
    <TypeName>System.ServiceProcess.ServiceController</TypeName>
  </ViewSelectedBy>
  <TableControl>...</TableControl>
</View>

```

## <a name="see-also"></a><span data-ttu-id="224c6-126">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="224c6-126">See Also</span></span>

[<span data-ttu-id="224c6-127">Creazione di una visualizzazione elenco</span><span class="sxs-lookup"><span data-stu-id="224c6-127">Creating a List View</span></span>](./creating-a-list-view.md)

[<span data-ttu-id="224c6-128">Creazione di una visualizzazione tabella</span><span class="sxs-lookup"><span data-stu-id="224c6-128">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="224c6-129">Creazione di una visualizzazione più ampia</span><span class="sxs-lookup"><span data-stu-id="224c6-129">Creating a Wide View</span></span>](./creating-a-wide-view.md)

[<span data-ttu-id="224c6-130">Creazione di controlli personalizzati</span><span class="sxs-lookup"><span data-stu-id="224c6-130">Creating Custom Controls</span></span>](./creating-custom-controls.md)

[<span data-ttu-id="224c6-131">Elemento di visualizzazione (formato)</span><span class="sxs-lookup"><span data-stu-id="224c6-131">View Element (Format)</span></span>](./view-element-format.md)

[<span data-ttu-id="224c6-132">La scrittura di un File di formattazione di PowerShell</span><span class="sxs-lookup"><span data-stu-id="224c6-132">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
