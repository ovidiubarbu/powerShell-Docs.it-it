---
title: Elemento ScriptBlock per GroupBy (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 30183927-6f0e-4717-b6f5-f07a6e134cfb
caps.latest.revision: 6
ms.openlocfilehash: f2f6b9af7740b1231881294c2f32bf97b5a1568b
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62064510"
---
# <a name="scriptblock-element-for-groupby-format"></a><span data-ttu-id="a70e2-102">Elemento ScriptBlock per GroupBy (formato)</span><span class="sxs-lookup"><span data-stu-id="a70e2-102">ScriptBlock Element for GroupBy (Format)</span></span>

<span data-ttu-id="a70e2-103">Specifica lo script che avvia un nuovo gruppo ogni volta che cambia il relativo valore.</span><span class="sxs-lookup"><span data-stu-id="a70e2-103">Specifies the script that starts a new group whenever its value changes.</span></span>

<span data-ttu-id="a70e2-104">Elemento di GroupBy elemento (formato) per la visualizzazione elemento ViewDefinitions (formato) configurazione elemento (formato) elemento di visualizzazione (formato) ScriptBlock per GroupBy (formato)</span><span class="sxs-lookup"><span data-stu-id="a70e2-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) GroupBy Element for View (Format) ScriptBlock Element for GroupBy (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="a70e2-105">Sintassi</span><span class="sxs-lookup"><span data-stu-id="a70e2-105">Syntax</span></span>

```xml
<ScriptBlock>ScriptToEvaluate</ScriptBlock>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="a70e2-106">Elementi e attributi</span><span class="sxs-lookup"><span data-stu-id="a70e2-106">Attributes and Elements</span></span>

<span data-ttu-id="a70e2-107">Le sezioni seguenti descrivono gli attributi e gli elementi figlio dell'elemento padre del `ScriptBlock` elemento.</span><span class="sxs-lookup"><span data-stu-id="a70e2-107">The following sections describe attributes, child elements, and the parent element of the `ScriptBlock` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="a70e2-108">Attributes</span><span class="sxs-lookup"><span data-stu-id="a70e2-108">Attributes</span></span>

<span data-ttu-id="a70e2-109">Nessuna.</span><span class="sxs-lookup"><span data-stu-id="a70e2-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="a70e2-110">Elementi figlio</span><span class="sxs-lookup"><span data-stu-id="a70e2-110">Child Elements</span></span>

<span data-ttu-id="a70e2-111">Nessuna.</span><span class="sxs-lookup"><span data-stu-id="a70e2-111">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="a70e2-112">Elementi padre</span><span class="sxs-lookup"><span data-stu-id="a70e2-112">Parent Elements</span></span>

|<span data-ttu-id="a70e2-113">Elemento</span><span class="sxs-lookup"><span data-stu-id="a70e2-113">Element</span></span>|<span data-ttu-id="a70e2-114">Description</span><span class="sxs-lookup"><span data-stu-id="a70e2-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="a70e2-115">Elemento GroupBy per visualizzazione (formato)</span><span class="sxs-lookup"><span data-stu-id="a70e2-115">GroupBy Element for View (Format)</span></span>](./groupby-element-for-view-format.md)|<span data-ttu-id="a70e2-116">Definisce la modalità di visualizzazione di un gruppo di oggetti .NET.</span><span class="sxs-lookup"><span data-stu-id="a70e2-116">Defines how a group of .NET objects is displayed.</span></span>|

## <a name="text-value"></a><span data-ttu-id="a70e2-117">Valore di testo</span><span class="sxs-lookup"><span data-stu-id="a70e2-117">Text Value</span></span>

<span data-ttu-id="a70e2-118">Specificare lo script che viene valutato.</span><span class="sxs-lookup"><span data-stu-id="a70e2-118">Specify the script that is evaluated.</span></span>

## <a name="remarks"></a><span data-ttu-id="a70e2-119">Osservazioni</span><span class="sxs-lookup"><span data-stu-id="a70e2-119">Remarks</span></span>

<span data-ttu-id="a70e2-120">Windows PowerShell avvia un nuovo gruppo ogni volta che cambia il valore di questo script.</span><span class="sxs-lookup"><span data-stu-id="a70e2-120">Windows PowerShell starts a new group whenever the value of this script changes.</span></span>

<span data-ttu-id="a70e2-121">Quando questo elemento viene specificato, non è possibile specificare il [PropertyName](http://msdn.microsoft.com/en-us/396dede0-039a-4a87-a5ef-3ecabb729676) elemento per avviare un nuovo gruppo.</span><span class="sxs-lookup"><span data-stu-id="a70e2-121">When this element is specified, you cannot specify the [PropertyName](http://msdn.microsoft.com/en-us/396dede0-039a-4a87-a5ef-3ecabb729676) element to start a new group.</span></span>

## <a name="see-also"></a><span data-ttu-id="a70e2-122">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="a70e2-122">See Also</span></span>

[<span data-ttu-id="a70e2-123">Elemento PropertyName per GroupBy (formato)</span><span class="sxs-lookup"><span data-stu-id="a70e2-123">PropertyName Element for GroupBy (Format)</span></span>](./propertyname-element-for-groupby-format.md)

[<span data-ttu-id="a70e2-124">Elemento GroupBy per visualizzazione (formato)</span><span class="sxs-lookup"><span data-stu-id="a70e2-124">GroupBy Element for View (Format)</span></span>](./groupby-element-for-view-format.md)

[<span data-ttu-id="a70e2-125">La scrittura di un File di formattazione di PowerShell</span><span class="sxs-lookup"><span data-stu-id="a70e2-125">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
