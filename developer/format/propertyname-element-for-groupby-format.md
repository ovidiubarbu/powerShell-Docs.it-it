---
title: Elemento PropertyName per GroupBy (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ddcecc46-ac75-43fa-b03a-802a68524ec3
caps.latest.revision: 10
ms.openlocfilehash: da6ac5abe7acbbee8f57b3e81529664f81800b86
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/03/2019
ms.locfileid: "56863267"
---
# <a name="propertyname-element-for-groupby-format"></a><span data-ttu-id="7fe5f-102">Elemento PropertyName per GroupBy (formato)</span><span class="sxs-lookup"><span data-stu-id="7fe5f-102">PropertyName Element for GroupBy (Format)</span></span>

<span data-ttu-id="7fe5f-103">Specifica la proprietà .NET che avvia un nuovo gruppo ogni volta che cambia il relativo valore.</span><span class="sxs-lookup"><span data-stu-id="7fe5f-103">Specifies the .NET property that starts a new group whenever its value changes.</span></span>

<span data-ttu-id="7fe5f-104">Elemento di GroupBy elemento (formato) per la visualizzazione elemento ViewDefinitions (formato) configurazione elemento (formato) elemento di visualizzazione (formato) PropertyName per GroupBy (formato)</span><span class="sxs-lookup"><span data-stu-id="7fe5f-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) GroupBy Element for View (Format) PropertyName Element for GroupBy (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="7fe5f-105">Sintassi</span><span class="sxs-lookup"><span data-stu-id="7fe5f-105">Syntax</span></span>

```xml
<PropertyName>.NetTypeProperty</PropertyName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="7fe5f-106">Attributi ed elementi</span><span class="sxs-lookup"><span data-stu-id="7fe5f-106">Attributes and Elements</span></span>

<span data-ttu-id="7fe5f-107">Le sezioni seguenti descrivono gli attributi e gli elementi figlio dell'elemento padre del `PropertyName` elemento.</span><span class="sxs-lookup"><span data-stu-id="7fe5f-107">The following sections describe attributes, child elements, and the parent element of the `PropertyName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="7fe5f-108">Attributes</span><span class="sxs-lookup"><span data-stu-id="7fe5f-108">Attributes</span></span>

<span data-ttu-id="7fe5f-109">Nessuna.</span><span class="sxs-lookup"><span data-stu-id="7fe5f-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="7fe5f-110">Elementi figlio</span><span class="sxs-lookup"><span data-stu-id="7fe5f-110">Child Elements</span></span>

<span data-ttu-id="7fe5f-111">Nessuna.</span><span class="sxs-lookup"><span data-stu-id="7fe5f-111">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="7fe5f-112">Elementi padre</span><span class="sxs-lookup"><span data-stu-id="7fe5f-112">Parent Elements</span></span>

|<span data-ttu-id="7fe5f-113">Elemento</span><span class="sxs-lookup"><span data-stu-id="7fe5f-113">Element</span></span>|<span data-ttu-id="7fe5f-114">Description</span><span class="sxs-lookup"><span data-stu-id="7fe5f-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="7fe5f-115">Elemento GroupBy per visualizzazione (formato)</span><span class="sxs-lookup"><span data-stu-id="7fe5f-115">GroupBy Element for View (Format)</span></span>](./groupby-element-for-view-format.md)|<span data-ttu-id="7fe5f-116">Definisce la modalità di visualizzazione di un gruppo di oggetti .NET.</span><span class="sxs-lookup"><span data-stu-id="7fe5f-116">Defines how a group of .NET objects is displayed.</span></span>|

## <a name="text-value"></a><span data-ttu-id="7fe5f-117">Valore di testo</span><span class="sxs-lookup"><span data-stu-id="7fe5f-117">Text Value</span></span>

<span data-ttu-id="7fe5f-118">Specificare il nome della proprietà .NET.</span><span class="sxs-lookup"><span data-stu-id="7fe5f-118">Specify the .NET property name.</span></span>

## <a name="remarks"></a><span data-ttu-id="7fe5f-119">Osservazioni</span><span class="sxs-lookup"><span data-stu-id="7fe5f-119">Remarks</span></span>

<span data-ttu-id="7fe5f-120">Windows PowerShell avvia un nuovo gruppo ogni volta che il valore di questa proprietà viene modificato.</span><span class="sxs-lookup"><span data-stu-id="7fe5f-120">Windows PowerShell starts a new group whenever the value of this property changes.</span></span>

<span data-ttu-id="7fe5f-121">Quando questo elemento viene specificato, non è possibile specificare il [ScriptBlock](./scriptblock-element-for-groupby-format.md) elemento per avviare un nuovo gruppo.</span><span class="sxs-lookup"><span data-stu-id="7fe5f-121">When this element is specified, you cannot specify the [ScriptBlock](./scriptblock-element-for-groupby-format.md) element to start a new group.</span></span>

## <a name="example"></a><span data-ttu-id="7fe5f-122">Esempio</span><span class="sxs-lookup"><span data-stu-id="7fe5f-122">Example</span></span>

<span data-ttu-id="7fe5f-123">Nell'esempio seguente viene illustrato come avviare un nuovo gruppo quando cambia il valore di una proprietà.</span><span class="sxs-lookup"><span data-stu-id="7fe5f-123">The following example shows how to start a new group when the value of a property changes.</span></span>

```xml
<GroupBy>
  <Label>Service Type</Label>
  <PropertyName>ServiceType</PropertyName>
</GroupBy>

```

<span data-ttu-id="7fe5f-124">Per un esempio di un file di formattazione completato che include questo elemento, vedere [visualizzazione più ampia (GroupBy)](./wide-view-groupby.md).</span><span class="sxs-lookup"><span data-stu-id="7fe5f-124">For an example of a complete formatting file that includes this element, see [Wide View (GroupBy)](./wide-view-groupby.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="7fe5f-125">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="7fe5f-125">See Also</span></span>

[<span data-ttu-id="7fe5f-126">Elemento GroupBy per visualizzazione (formato)</span><span class="sxs-lookup"><span data-stu-id="7fe5f-126">GroupBy Element for View (Format)</span></span>](./groupby-element-for-view-format.md)

[<span data-ttu-id="7fe5f-127">Elemento ScriptBlock per GroupBy (formato)</span><span class="sxs-lookup"><span data-stu-id="7fe5f-127">ScriptBlock Element for GroupBy (Format)</span></span>](./scriptblock-element-for-groupby-format.md)

[<span data-ttu-id="7fe5f-128">La scrittura di un File di formattazione di PowerShell</span><span class="sxs-lookup"><span data-stu-id="7fe5f-128">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
