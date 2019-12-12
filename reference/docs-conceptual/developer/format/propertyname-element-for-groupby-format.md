---
title: Elemento PropertyName per GroupBy (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ddcecc46-ac75-43fa-b03a-802a68524ec3
caps.latest.revision: 10
ms.openlocfilehash: da6ac5abe7acbbee8f57b3e81529664f81800b86
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/05/2019
ms.locfileid: "72362520"
---
# <a name="propertyname-element-for-groupby-format"></a><span data-ttu-id="6293e-102">Elemento PropertyName per GroupBy (formato)</span><span class="sxs-lookup"><span data-stu-id="6293e-102">PropertyName Element for GroupBy (Format)</span></span>

<span data-ttu-id="6293e-103">Specifica la proprietà .NET che avvia un nuovo gruppo ogni volta che il relativo valore viene modificato.</span><span class="sxs-lookup"><span data-stu-id="6293e-103">Specifies the .NET property that starts a new group whenever its value changes.</span></span>

<span data-ttu-id="6293e-104">Elemento Configuration (Format) elemento ViewDefinitions (Format) elemento View (Format) elemento GroupBy per la visualizzazione (formato) elemento PropertyName per GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="6293e-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) GroupBy Element for View (Format) PropertyName Element for GroupBy (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="6293e-105">Sintassi</span><span class="sxs-lookup"><span data-stu-id="6293e-105">Syntax</span></span>

```xml
<PropertyName>.NetTypeProperty</PropertyName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="6293e-106">Attributi ed elementi</span><span class="sxs-lookup"><span data-stu-id="6293e-106">Attributes and Elements</span></span>

<span data-ttu-id="6293e-107">Nelle sezioni seguenti vengono descritti gli attributi, gli elementi figlio e l'elemento padre dell'elemento `PropertyName`.</span><span class="sxs-lookup"><span data-stu-id="6293e-107">The following sections describe attributes, child elements, and the parent element of the `PropertyName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="6293e-108">Attributi</span><span class="sxs-lookup"><span data-stu-id="6293e-108">Attributes</span></span>

<span data-ttu-id="6293e-109">Nessuna.</span><span class="sxs-lookup"><span data-stu-id="6293e-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="6293e-110">Elementi figlio</span><span class="sxs-lookup"><span data-stu-id="6293e-110">Child Elements</span></span>

<span data-ttu-id="6293e-111">Nessuna.</span><span class="sxs-lookup"><span data-stu-id="6293e-111">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="6293e-112">Elementi padre</span><span class="sxs-lookup"><span data-stu-id="6293e-112">Parent Elements</span></span>

|<span data-ttu-id="6293e-113">Elemento</span><span class="sxs-lookup"><span data-stu-id="6293e-113">Element</span></span>|<span data-ttu-id="6293e-114">Description</span><span class="sxs-lookup"><span data-stu-id="6293e-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="6293e-115">Elemento GroupBy per View (Format)</span><span class="sxs-lookup"><span data-stu-id="6293e-115">GroupBy Element for View (Format)</span></span>](./groupby-element-for-view-format.md)|<span data-ttu-id="6293e-116">Definisce la modalità di visualizzazione di un gruppo di oggetti .NET.</span><span class="sxs-lookup"><span data-stu-id="6293e-116">Defines how a group of .NET objects is displayed.</span></span>|

## <a name="text-value"></a><span data-ttu-id="6293e-117">Valore testo</span><span class="sxs-lookup"><span data-stu-id="6293e-117">Text Value</span></span>

<span data-ttu-id="6293e-118">Specificare il nome della proprietà .NET.</span><span class="sxs-lookup"><span data-stu-id="6293e-118">Specify the .NET property name.</span></span>

## <a name="remarks"></a><span data-ttu-id="6293e-119">Osservazioni</span><span class="sxs-lookup"><span data-stu-id="6293e-119">Remarks</span></span>

<span data-ttu-id="6293e-120">Windows PowerShell avvia un nuovo gruppo ogni volta che il valore di questa proprietà viene modificato.</span><span class="sxs-lookup"><span data-stu-id="6293e-120">Windows PowerShell starts a new group whenever the value of this property changes.</span></span>

<span data-ttu-id="6293e-121">Quando questo elemento viene specificato, non è possibile specificare l'elemento [scriptblock](./scriptblock-element-for-groupby-format.md) per avviare un nuovo gruppo.</span><span class="sxs-lookup"><span data-stu-id="6293e-121">When this element is specified, you cannot specify the [ScriptBlock](./scriptblock-element-for-groupby-format.md) element to start a new group.</span></span>

## <a name="example"></a><span data-ttu-id="6293e-122">Esempio</span><span class="sxs-lookup"><span data-stu-id="6293e-122">Example</span></span>

<span data-ttu-id="6293e-123">Nell'esempio seguente viene illustrato come avviare un nuovo gruppo quando viene modificato il valore di una proprietà.</span><span class="sxs-lookup"><span data-stu-id="6293e-123">The following example shows how to start a new group when the value of a property changes.</span></span>

```xml
<GroupBy>
  <Label>Service Type</Label>
  <PropertyName>ServiceType</PropertyName>
</GroupBy>

```

<span data-ttu-id="6293e-124">Per un esempio di un file di formattazione completo che include questo elemento, vedere [visualizzazione estesa (GroupBy)](./wide-view-groupby.md).</span><span class="sxs-lookup"><span data-stu-id="6293e-124">For an example of a complete formatting file that includes this element, see [Wide View (GroupBy)](./wide-view-groupby.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="6293e-125">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="6293e-125">See Also</span></span>

[<span data-ttu-id="6293e-126">Elemento GroupBy per View (Format)</span><span class="sxs-lookup"><span data-stu-id="6293e-126">GroupBy Element for View (Format)</span></span>](./groupby-element-for-view-format.md)

[<span data-ttu-id="6293e-127">Elemento ScriptBlock per GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="6293e-127">ScriptBlock Element for GroupBy (Format)</span></span>](./scriptblock-element-for-groupby-format.md)

[<span data-ttu-id="6293e-128">Scrittura di un file di formattazione di PowerShell</span><span class="sxs-lookup"><span data-stu-id="6293e-128">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
