---
title: Elemento ListItems per ListEntry per ListControl (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d2c1da6d-acc7-4fe8-9e7d-6dcddc2787cd
caps.latest.revision: 9
ms.openlocfilehash: c25f18489d9c7abd8889758499dbbacd6ee29304
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/15/2019
ms.locfileid: "72362740"
---
# <a name="listitems-element-for-listentry-for-listcontrol-format"></a><span data-ttu-id="64104-102">Elemento ListItems per ListEntry per ListControl (formato)</span><span class="sxs-lookup"><span data-stu-id="64104-102">ListItems Element for ListEntry for ListControl (Format)</span></span>

<span data-ttu-id="64104-103">Definisce le proprietà e gli script i cui valori vengono visualizzati nelle righe della visualizzazione elenco.</span><span class="sxs-lookup"><span data-stu-id="64104-103">Defines the properties and scripts whose values are displayed in the rows of the list view.</span></span>

<span data-ttu-id="64104-104">Elemento Configuration (Format) elemento ViewDefinitions (Format) elemento View (Format) elemento ListControl (Format) elemento ListEntries per il controllo List (Format) elemento ListEntry per l'elemento ListControl (Format) ListItems per ListControl (Format)</span><span class="sxs-lookup"><span data-stu-id="64104-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) ListControl Element (Format) ListEntries Element for List Control (Format) ListEntry Element for ListControl (Format) ListItems Element for ListControl (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="64104-105">Sintassi</span><span class="sxs-lookup"><span data-stu-id="64104-105">Syntax</span></span>

```xml
<ListItems>
  <ListItem>...</ListItem>
</ListItems>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="64104-106">Attributi ed elementi</span><span class="sxs-lookup"><span data-stu-id="64104-106">Attributes and Elements</span></span>

<span data-ttu-id="64104-107">Nelle sezioni seguenti vengono descritti gli attributi, gli elementi figlio e l'elemento padre dell'elemento `ListItems`.</span><span class="sxs-lookup"><span data-stu-id="64104-107">The following sections describe the attributes, child elements, and parent element of the `ListItems` element.</span></span> <span data-ttu-id="64104-108">Non esiste alcun limite al numero di elementi figlio che è possibile specificare.</span><span class="sxs-lookup"><span data-stu-id="64104-108">There is no limit to the number of child elements that can be specified.</span></span> <span data-ttu-id="64104-109">L'ordine degli elementi figlio definisce l'ordine in cui i valori vengono visualizzati nella visualizzazione elenco.</span><span class="sxs-lookup"><span data-stu-id="64104-109">The order of the child elements defines the order that values are displayed in the list view.</span></span>

### <a name="attributes"></a><span data-ttu-id="64104-110">Attributi</span><span class="sxs-lookup"><span data-stu-id="64104-110">Attributes</span></span>

<span data-ttu-id="64104-111">Nessuna.</span><span class="sxs-lookup"><span data-stu-id="64104-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="64104-112">Elementi figlio</span><span class="sxs-lookup"><span data-stu-id="64104-112">Child Elements</span></span>

|<span data-ttu-id="64104-113">Elemento</span><span class="sxs-lookup"><span data-stu-id="64104-113">Element</span></span>|<span data-ttu-id="64104-114">Description</span><span class="sxs-lookup"><span data-stu-id="64104-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="64104-115">Elemento ListItem per ListControl (Format)</span><span class="sxs-lookup"><span data-stu-id="64104-115">ListItem Element for ListControl (Format)</span></span>](./listitem-element-for-listitems-for-listcontrol-format.md)|<span data-ttu-id="64104-116">Elemento obbligatorio.</span><span class="sxs-lookup"><span data-stu-id="64104-116">Required element.</span></span><br /><br /> <span data-ttu-id="64104-117">Definisce la proprietà o lo script il cui valore viene visualizzato dalla visualizzazione elenco.</span><span class="sxs-lookup"><span data-stu-id="64104-117">Defines the property or script whose value is displayed by the list view.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="64104-118">Elementi padre</span><span class="sxs-lookup"><span data-stu-id="64104-118">Parent Elements</span></span>

|<span data-ttu-id="64104-119">Elemento</span><span class="sxs-lookup"><span data-stu-id="64104-119">Element</span></span>|<span data-ttu-id="64104-120">Description</span><span class="sxs-lookup"><span data-stu-id="64104-120">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="64104-121">Elemento ListEntry per ListControl (Format)</span><span class="sxs-lookup"><span data-stu-id="64104-121">ListEntry Element for ListControl (Format)</span></span>](./listentry-element-for-listcontrol-format.md)|<span data-ttu-id="64104-122">Fornisce una definizione della visualizzazione elenco.</span><span class="sxs-lookup"><span data-stu-id="64104-122">Provides a definition of the list view.</span></span>|

## <a name="remarks"></a><span data-ttu-id="64104-123">Osservazioni</span><span class="sxs-lookup"><span data-stu-id="64104-123">Remarks</span></span>

<span data-ttu-id="64104-124">Per ulteriori informazioni su questo tipo di visualizzazione, vedere [creazione di una visualizzazione elenco](./creating-a-list-view.md).</span><span class="sxs-lookup"><span data-stu-id="64104-124">For more information about this type of view, see [Creating a List View](./creating-a-list-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="64104-125">Esempio</span><span class="sxs-lookup"><span data-stu-id="64104-125">Example</span></span>

<span data-ttu-id="64104-126">In questo esempio vengono illustrati gli elementi XML che definiscono tre righe della visualizzazione elenco.</span><span class="sxs-lookup"><span data-stu-id="64104-126">This example shows the XML elements that define three rows of the list view.</span></span>

```xml
<ListEntry>
    <ListItems>
      <ListItem>
        <Label>Property1: </Label>
        <PropertyName>.NetTypeProperty1</PropertyName>
      </ListItem>
      <ListItem>
        <PropertyName>.NetTypeProperty2</PropertyName>
      </ListItem>
      <ListItem>
        <ScriptBlock>$_.ProcessName + ":" $_.Id</ScriptBlock>
      </ListItem>
  </ListEntry>
```

## <a name="see-also"></a><span data-ttu-id="64104-127">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="64104-127">See Also</span></span>

[<span data-ttu-id="64104-128">Elemento ListEntry per ListControl (Format)</span><span class="sxs-lookup"><span data-stu-id="64104-128">ListEntry Element for ListControl (Format)</span></span>](./listentry-element-for-listcontrol-format.md)

[<span data-ttu-id="64104-129">Elemento ListItem per ListControl (Format)</span><span class="sxs-lookup"><span data-stu-id="64104-129">ListItem Element for ListControl (Format)</span></span>](./listitem-element-for-listitems-for-listcontrol-format.md)

[<span data-ttu-id="64104-130">Creazione di una visualizzazione elenco</span><span class="sxs-lookup"><span data-stu-id="64104-130">Creating a List View</span></span>](./creating-a-list-view.md)

[<span data-ttu-id="64104-131">Scrittura di un file di formattazione di PowerShell</span><span class="sxs-lookup"><span data-stu-id="64104-131">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
