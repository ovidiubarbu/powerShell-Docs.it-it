---
title: Elemento Name per View (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 3a31010d-1db9-44ae-a7f3-6ed32cb641cb
caps.latest.revision: 16
ms.openlocfilehash: 097d20cb6a04635124d1f96823248df6095ca1af
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/15/2019
ms.locfileid: "72362640"
---
# <a name="name-element-for-view-format"></a><span data-ttu-id="2702a-102">Elemento Name per View (formato)</span><span class="sxs-lookup"><span data-stu-id="2702a-102">Name Element for View (Format)</span></span>

<span data-ttu-id="2702a-103">Specifica il nome utilizzato per identificare la visualizzazione.</span><span class="sxs-lookup"><span data-stu-id="2702a-103">Specifies the name that is used to identify the view.</span></span>

<span data-ttu-id="2702a-104">Elemento Configuration (Format) elemento ViewDefinitions (Format) elemento di visualizzazione (Format) elemento Name (Format)</span><span class="sxs-lookup"><span data-stu-id="2702a-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) Name Element (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="2702a-105">Sintassi</span><span class="sxs-lookup"><span data-stu-id="2702a-105">Syntax</span></span>

```xml
<Name>ViewName</Name>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="2702a-106">Attributi ed elementi</span><span class="sxs-lookup"><span data-stu-id="2702a-106">Attributes and Elements</span></span>

<span data-ttu-id="2702a-107">Nelle sezioni seguenti vengono descritti gli attributi, gli elementi figlio e l'elemento padre dell'elemento `Name`.</span><span class="sxs-lookup"><span data-stu-id="2702a-107">The following sections describe attributes, child elements, and the parent element of the `Name` element.</span></span> <span data-ttu-id="2702a-108">Per ogni visualizzazione è consentito un solo elemento `Name`.</span><span class="sxs-lookup"><span data-stu-id="2702a-108">Only one `Name` element is allowed for each view.</span></span>

### <a name="attributes"></a><span data-ttu-id="2702a-109">Attributi</span><span class="sxs-lookup"><span data-stu-id="2702a-109">Attributes</span></span>

<span data-ttu-id="2702a-110">Nessuna.</span><span class="sxs-lookup"><span data-stu-id="2702a-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="2702a-111">Elementi figlio</span><span class="sxs-lookup"><span data-stu-id="2702a-111">Child Elements</span></span>

<span data-ttu-id="2702a-112">Nessuna.</span><span class="sxs-lookup"><span data-stu-id="2702a-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="2702a-113">Elementi padre</span><span class="sxs-lookup"><span data-stu-id="2702a-113">Parent Elements</span></span>

|<span data-ttu-id="2702a-114">Elemento</span><span class="sxs-lookup"><span data-stu-id="2702a-114">Element</span></span>|<span data-ttu-id="2702a-115">Description</span><span class="sxs-lookup"><span data-stu-id="2702a-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="2702a-116">Elemento View (Format)</span><span class="sxs-lookup"><span data-stu-id="2702a-116">View Element (Format)</span></span>](./view-element-format.md)|<span data-ttu-id="2702a-117">Definisce una vista utilizzata per visualizzare i membri di uno o più oggetti .NET.</span><span class="sxs-lookup"><span data-stu-id="2702a-117">Defines a view that is used to display the members of one or more .NET objects.</span></span>|

## <a name="text-value"></a><span data-ttu-id="2702a-118">Valore di testo</span><span class="sxs-lookup"><span data-stu-id="2702a-118">Text Value</span></span>

<span data-ttu-id="2702a-119">Specificare un nome descrittivo univoco per la visualizzazione.</span><span class="sxs-lookup"><span data-stu-id="2702a-119">Specify a unique friendly name for the view.</span></span> <span data-ttu-id="2702a-120">Questo nome può includere un riferimento al tipo di visualizzazione, ad esempio una vista tabella o una visualizzazione elenco, che l'oggetto o il set di oggetti utilizza la vista, il comando che restituisce gli oggetti o una combinazione di questi.</span><span class="sxs-lookup"><span data-stu-id="2702a-120">This name can include a reference to the type of the view (such as a table view or list view), which object or set of objects use the view, what command returns the objects, or a combination of these.</span></span>

## <a name="remarks"></a><span data-ttu-id="2702a-121">Osservazioni</span><span class="sxs-lookup"><span data-stu-id="2702a-121">Remarks</span></span>

<span data-ttu-id="2702a-122">Per ulteriori informazioni sui diversi tipi di viste, vedere gli argomenti seguenti: [vista tabella](./creating-a-table-view.md), [visualizzazione elenco](./creating-a-list-view.md), [visualizzazione estesa](./creating-a-wide-view.md)e [visualizzazione personalizzata](./creating-custom-controls.md).</span><span class="sxs-lookup"><span data-stu-id="2702a-122">For more information about the different types of views, see the following topics: [Table View](./creating-a-table-view.md), [List View](./creating-a-list-view.md), [Wide View](./creating-a-wide-view.md), and [Custom View](./creating-custom-controls.md).</span></span>

## <a name="example"></a><span data-ttu-id="2702a-123">Esempio</span><span class="sxs-lookup"><span data-stu-id="2702a-123">Example</span></span>

<span data-ttu-id="2702a-124">Nell'esempio seguente viene illustrato un elemento `View` che definisce una vista tabella per l'oggetto [System. ServiceProcess. ServiceController](/dotnet/api/System.ServiceProcess.ServiceController) .</span><span class="sxs-lookup"><span data-stu-id="2702a-124">The following example shows a `View` element that defines a table view for the [System.Serviceprocess.Servicecontroller](/dotnet/api/System.ServiceProcess.ServiceController) object.</span></span> <span data-ttu-id="2702a-125">Il nome della vista è "Service".</span><span class="sxs-lookup"><span data-stu-id="2702a-125">The name of the view is "service".</span></span>

```xml
<View>
  <Name>service</Name>
  <ViewSelectedBy>
    <TypeName>System.ServiceProcess.ServiceController</TypeName>
  </ViewSelectedBy>
  <TableControl>...</TableControl>
</View>

```

## <a name="see-also"></a><span data-ttu-id="2702a-126">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="2702a-126">See Also</span></span>

[<span data-ttu-id="2702a-127">Creazione di una visualizzazione elenco</span><span class="sxs-lookup"><span data-stu-id="2702a-127">Creating a List View</span></span>](./creating-a-list-view.md)

[<span data-ttu-id="2702a-128">Creazione di una vista tabella</span><span class="sxs-lookup"><span data-stu-id="2702a-128">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="2702a-129">Creazione di una visualizzazione estesa</span><span class="sxs-lookup"><span data-stu-id="2702a-129">Creating a Wide View</span></span>](./creating-a-wide-view.md)

[<span data-ttu-id="2702a-130">Creazione di controlli personalizzati</span><span class="sxs-lookup"><span data-stu-id="2702a-130">Creating Custom Controls</span></span>](./creating-custom-controls.md)

[<span data-ttu-id="2702a-131">Elemento View (Format)</span><span class="sxs-lookup"><span data-stu-id="2702a-131">View Element (Format)</span></span>](./view-element-format.md)

[<span data-ttu-id="2702a-132">Scrittura di un file di formattazione di PowerShell</span><span class="sxs-lookup"><span data-stu-id="2702a-132">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
