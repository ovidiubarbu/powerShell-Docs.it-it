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
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/16/2019
ms.locfileid: "58054426"
---
# <a name="scriptblock-element-for-groupby-format"></a><span data-ttu-id="75ac6-102">Elemento ScriptBlock per GroupBy (formato)</span><span class="sxs-lookup"><span data-stu-id="75ac6-102">ScriptBlock Element for GroupBy (Format)</span></span>

<span data-ttu-id="75ac6-103">Specifica lo script che avvia un nuovo gruppo ogni volta che cambia il relativo valore.</span><span class="sxs-lookup"><span data-stu-id="75ac6-103">Specifies the script that starts a new group whenever its value changes.</span></span>

<span data-ttu-id="75ac6-104">Elemento di GroupBy elemento (formato) per la visualizzazione elemento ViewDefinitions (formato) configurazione elemento (formato) elemento di visualizzazione (formato) ScriptBlock per GroupBy (formato)</span><span class="sxs-lookup"><span data-stu-id="75ac6-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) GroupBy Element for View (Format) ScriptBlock Element for GroupBy (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="75ac6-105">Sintassi</span><span class="sxs-lookup"><span data-stu-id="75ac6-105">Syntax</span></span>

```xml
<ScriptBlock>ScriptToEvaluate</ScriptBlock>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="75ac6-106">Attributi ed elementi</span><span class="sxs-lookup"><span data-stu-id="75ac6-106">Attributes and Elements</span></span>

<span data-ttu-id="75ac6-107">Le sezioni seguenti descrivono gli attributi e gli elementi figlio dell'elemento padre del `ScriptBlock` elemento.</span><span class="sxs-lookup"><span data-stu-id="75ac6-107">The following sections describe attributes, child elements, and the parent element of the `ScriptBlock` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="75ac6-108">Attributes</span><span class="sxs-lookup"><span data-stu-id="75ac6-108">Attributes</span></span>

<span data-ttu-id="75ac6-109">Nessuna.</span><span class="sxs-lookup"><span data-stu-id="75ac6-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="75ac6-110">Elementi figlio</span><span class="sxs-lookup"><span data-stu-id="75ac6-110">Child Elements</span></span>

<span data-ttu-id="75ac6-111">Nessuna.</span><span class="sxs-lookup"><span data-stu-id="75ac6-111">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="75ac6-112">Elementi padre</span><span class="sxs-lookup"><span data-stu-id="75ac6-112">Parent Elements</span></span>

|<span data-ttu-id="75ac6-113">Elemento</span><span class="sxs-lookup"><span data-stu-id="75ac6-113">Element</span></span>|<span data-ttu-id="75ac6-114">Description</span><span class="sxs-lookup"><span data-stu-id="75ac6-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="75ac6-115">Elemento GroupBy per visualizzazione (formato)</span><span class="sxs-lookup"><span data-stu-id="75ac6-115">GroupBy Element for View (Format)</span></span>](./groupby-element-for-view-format.md)|<span data-ttu-id="75ac6-116">Definisce la modalità di visualizzazione di un gruppo di oggetti .NET.</span><span class="sxs-lookup"><span data-stu-id="75ac6-116">Defines how a group of .NET objects is displayed.</span></span>|

## <a name="text-value"></a><span data-ttu-id="75ac6-117">Valore di testo</span><span class="sxs-lookup"><span data-stu-id="75ac6-117">Text Value</span></span>

<span data-ttu-id="75ac6-118">Specificare lo script che viene valutato.</span><span class="sxs-lookup"><span data-stu-id="75ac6-118">Specify the script that is evaluated.</span></span>

## <a name="remarks"></a><span data-ttu-id="75ac6-119">Osservazioni</span><span class="sxs-lookup"><span data-stu-id="75ac6-119">Remarks</span></span>

<span data-ttu-id="75ac6-120">Windows PowerShell avvia un nuovo gruppo ogni volta che cambia il valore di questo script.</span><span class="sxs-lookup"><span data-stu-id="75ac6-120">Windows PowerShell starts a new group whenever the value of this script changes.</span></span>

<span data-ttu-id="75ac6-121">Quando questo elemento viene specificato, non è possibile specificare il [PropertyName](http://msdn.microsoft.com/en-us/396dede0-039a-4a87-a5ef-3ecabb729676) elemento per avviare un nuovo gruppo.</span><span class="sxs-lookup"><span data-stu-id="75ac6-121">When this element is specified, you cannot specify the [PropertyName](http://msdn.microsoft.com/en-us/396dede0-039a-4a87-a5ef-3ecabb729676) element to start a new group.</span></span>

## <a name="see-also"></a><span data-ttu-id="75ac6-122">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="75ac6-122">See Also</span></span>

[<span data-ttu-id="75ac6-123">Elemento PropertyName per GroupBy (formato)</span><span class="sxs-lookup"><span data-stu-id="75ac6-123">PropertyName Element for GroupBy (Format)</span></span>](./propertyname-element-for-groupby-format.md)

[<span data-ttu-id="75ac6-124">Elemento GroupBy per visualizzazione (formato)</span><span class="sxs-lookup"><span data-stu-id="75ac6-124">GroupBy Element for View (Format)</span></span>](./groupby-element-for-view-format.md)

[<span data-ttu-id="75ac6-125">La scrittura di un File di formattazione di PowerShell</span><span class="sxs-lookup"><span data-stu-id="75ac6-125">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
