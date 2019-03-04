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
ms.openlocfilehash: 41a6aaa24e5850bd390c8e3b6505cc88fc80b7b5
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/03/2019
ms.locfileid: "56856207"
---
# <a name="scriptblock-element-for-groupby-format"></a><span data-ttu-id="ec2cd-102">Elemento ScriptBlock per GroupBy (formato)</span><span class="sxs-lookup"><span data-stu-id="ec2cd-102">ScriptBlock Element for GroupBy (Format)</span></span>

<span data-ttu-id="ec2cd-103">Specifica lo script che avvia un nuovo gruppo ogni volta che cambia il relativo valore.</span><span class="sxs-lookup"><span data-stu-id="ec2cd-103">Specifies the script that starts a new group whenever its value changes.</span></span>

<span data-ttu-id="ec2cd-104">Elemento di GroupBy elemento (formato) per la visualizzazione elemento ViewDefinitions (formato) configurazione elemento (formato) elemento di visualizzazione (formato) ScriptBlock per GroupBy (formato)</span><span class="sxs-lookup"><span data-stu-id="ec2cd-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) GroupBy Element for View (Format) ScriptBlock Element for GroupBy (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="ec2cd-105">Sintassi</span><span class="sxs-lookup"><span data-stu-id="ec2cd-105">Syntax</span></span>

```xml
<ScriptBolck>ScriptToEvaluate</ScriptBlock>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="ec2cd-106">Attributi ed elementi</span><span class="sxs-lookup"><span data-stu-id="ec2cd-106">Attributes and Elements</span></span>

<span data-ttu-id="ec2cd-107">Le sezioni seguenti descrivono gli attributi e gli elementi figlio dell'elemento padre del `ScriptBlock` elemento.</span><span class="sxs-lookup"><span data-stu-id="ec2cd-107">The following sections describe attributes, child elements, and the parent element of the `ScriptBlock` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="ec2cd-108">Attributes</span><span class="sxs-lookup"><span data-stu-id="ec2cd-108">Attributes</span></span>

<span data-ttu-id="ec2cd-109">Nessuna.</span><span class="sxs-lookup"><span data-stu-id="ec2cd-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="ec2cd-110">Elementi figlio</span><span class="sxs-lookup"><span data-stu-id="ec2cd-110">Child Elements</span></span>

<span data-ttu-id="ec2cd-111">Nessuna.</span><span class="sxs-lookup"><span data-stu-id="ec2cd-111">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="ec2cd-112">Elementi padre</span><span class="sxs-lookup"><span data-stu-id="ec2cd-112">Parent Elements</span></span>

|<span data-ttu-id="ec2cd-113">Elemento</span><span class="sxs-lookup"><span data-stu-id="ec2cd-113">Element</span></span>|<span data-ttu-id="ec2cd-114">Description</span><span class="sxs-lookup"><span data-stu-id="ec2cd-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="ec2cd-115">Elemento GroupBy per visualizzazione (formato)</span><span class="sxs-lookup"><span data-stu-id="ec2cd-115">GroupBy Element for View (Format)</span></span>](./groupby-element-for-view-format.md)|<span data-ttu-id="ec2cd-116">Definisce la modalità di visualizzazione di un gruppo di oggetti .NET.</span><span class="sxs-lookup"><span data-stu-id="ec2cd-116">Defines how a group of .NET objects is displayed.</span></span>|

## <a name="text-value"></a><span data-ttu-id="ec2cd-117">Valore di testo</span><span class="sxs-lookup"><span data-stu-id="ec2cd-117">Text Value</span></span>

<span data-ttu-id="ec2cd-118">Specificare lo script che viene valutato.</span><span class="sxs-lookup"><span data-stu-id="ec2cd-118">Specify the script that is evaluated.</span></span>

## <a name="remarks"></a><span data-ttu-id="ec2cd-119">Osservazioni</span><span class="sxs-lookup"><span data-stu-id="ec2cd-119">Remarks</span></span>

<span data-ttu-id="ec2cd-120">Windows PowerShell avvia un nuovo gruppo ogni volta che cambia il valore di questo script.</span><span class="sxs-lookup"><span data-stu-id="ec2cd-120">Windows PowerShell starts a new group whenever the value of this script changes.</span></span>

<span data-ttu-id="ec2cd-121">Quando questo elemento viene specificato, non è possibile specificare il [PropertyName](http://msdn.microsoft.com/en-us/396dede0-039a-4a87-a5ef-3ecabb729676) elemento per avviare un nuovo gruppo.</span><span class="sxs-lookup"><span data-stu-id="ec2cd-121">When this element is specified, you cannot specify the [PropertyName](http://msdn.microsoft.com/en-us/396dede0-039a-4a87-a5ef-3ecabb729676) element to start a new group.</span></span>

## <a name="see-also"></a><span data-ttu-id="ec2cd-122">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="ec2cd-122">See Also</span></span>

[<span data-ttu-id="ec2cd-123">Elemento PropertyName per GroupBy (formato)</span><span class="sxs-lookup"><span data-stu-id="ec2cd-123">PropertyName Element for GroupBy (Format)</span></span>](./propertyname-element-for-groupby-format.md)

[<span data-ttu-id="ec2cd-124">Elemento GroupBy per visualizzazione (formato)</span><span class="sxs-lookup"><span data-stu-id="ec2cd-124">GroupBy Element for View (Format)</span></span>](./groupby-element-for-view-format.md)

[<span data-ttu-id="ec2cd-125">La scrittura di un File di formattazione di PowerShell</span><span class="sxs-lookup"><span data-stu-id="ec2cd-125">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
