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
ms.openlocfilehash: 37a297228eb33ff75daf94a12635d42b52c6cc9f
ms.sourcegitcommit: 58fb23c854f5a8b40ad1f952d3323aeeccac7a24
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/07/2019
ms.locfileid: "65229306"
---
# <a name="scriptblock-element-for-groupby-format"></a><span data-ttu-id="6be51-102">Elemento ScriptBlock per GroupBy (formato)</span><span class="sxs-lookup"><span data-stu-id="6be51-102">ScriptBlock Element for GroupBy (Format)</span></span>

<span data-ttu-id="6be51-103">Specifica lo script che avvia un nuovo gruppo ogni volta che cambia il relativo valore.</span><span class="sxs-lookup"><span data-stu-id="6be51-103">Specifies the script that starts a new group whenever its value changes.</span></span>

<span data-ttu-id="6be51-104">Elemento di GroupBy elemento (formato) per la visualizzazione elemento ViewDefinitions (formato) configurazione elemento (formato) elemento di visualizzazione (formato) ScriptBlock per GroupBy (formato)</span><span class="sxs-lookup"><span data-stu-id="6be51-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) GroupBy Element for View (Format) ScriptBlock Element for GroupBy (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="6be51-105">Sintassi</span><span class="sxs-lookup"><span data-stu-id="6be51-105">Syntax</span></span>

```xml
<ScriptBlock>ScriptToEvaluate</ScriptBlock>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="6be51-106">Attributi ed elementi</span><span class="sxs-lookup"><span data-stu-id="6be51-106">Attributes and Elements</span></span>

<span data-ttu-id="6be51-107">Le sezioni seguenti descrivono gli attributi e gli elementi figlio dell'elemento padre del `ScriptBlock` elemento.</span><span class="sxs-lookup"><span data-stu-id="6be51-107">The following sections describe attributes, child elements, and the parent element of the `ScriptBlock` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="6be51-108">Attributes</span><span class="sxs-lookup"><span data-stu-id="6be51-108">Attributes</span></span>

<span data-ttu-id="6be51-109">Nessuna.</span><span class="sxs-lookup"><span data-stu-id="6be51-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="6be51-110">Elementi figlio</span><span class="sxs-lookup"><span data-stu-id="6be51-110">Child Elements</span></span>

<span data-ttu-id="6be51-111">Nessuna.</span><span class="sxs-lookup"><span data-stu-id="6be51-111">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="6be51-112">Elementi padre</span><span class="sxs-lookup"><span data-stu-id="6be51-112">Parent Elements</span></span>

|<span data-ttu-id="6be51-113">Elemento</span><span class="sxs-lookup"><span data-stu-id="6be51-113">Element</span></span>|<span data-ttu-id="6be51-114">Description</span><span class="sxs-lookup"><span data-stu-id="6be51-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="6be51-115">Elemento GroupBy per visualizzazione (formato)</span><span class="sxs-lookup"><span data-stu-id="6be51-115">GroupBy Element for View (Format)</span></span>](./groupby-element-for-view-format.md)|<span data-ttu-id="6be51-116">Definisce la modalità di visualizzazione di un gruppo di oggetti .NET.</span><span class="sxs-lookup"><span data-stu-id="6be51-116">Defines how a group of .NET objects is displayed.</span></span>|

## <a name="text-value"></a><span data-ttu-id="6be51-117">Valore di testo</span><span class="sxs-lookup"><span data-stu-id="6be51-117">Text Value</span></span>

<span data-ttu-id="6be51-118">Specificare lo script che viene valutato.</span><span class="sxs-lookup"><span data-stu-id="6be51-118">Specify the script that is evaluated.</span></span>

## <a name="remarks"></a><span data-ttu-id="6be51-119">Osservazioni</span><span class="sxs-lookup"><span data-stu-id="6be51-119">Remarks</span></span>

<span data-ttu-id="6be51-120">Ogni volta che cambia il valore di questo script, PowerShell avvia un nuovo gruppo.</span><span class="sxs-lookup"><span data-stu-id="6be51-120">PowerShell starts a new group whenever the value of this script changes.</span></span>

<span data-ttu-id="6be51-121">Quando questo elemento viene specificato, non è possibile specificare il [PropertyName](propertyname-element-for-groupby-format.md) elemento per avviare un nuovo gruppo.</span><span class="sxs-lookup"><span data-stu-id="6be51-121">When this element is specified, you cannot specify the [PropertyName](propertyname-element-for-groupby-format.md) element to start a new group.</span></span>

## <a name="see-also"></a><span data-ttu-id="6be51-122">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="6be51-122">See Also</span></span>

[<span data-ttu-id="6be51-123">Elemento PropertyName per GroupBy (formato)</span><span class="sxs-lookup"><span data-stu-id="6be51-123">PropertyName Element for GroupBy (Format)</span></span>](propertyname-element-for-groupby-format.md)

[<span data-ttu-id="6be51-124">Elemento GroupBy per visualizzazione (formato)</span><span class="sxs-lookup"><span data-stu-id="6be51-124">GroupBy Element for View (Format)</span></span>](groupby-element-for-view-format.md)

[<span data-ttu-id="6be51-125">La scrittura di un File di formattazione di PowerShell</span><span class="sxs-lookup"><span data-stu-id="6be51-125">Writing a PowerShell Formatting File</span></span>](writing-a-powershell-formatting-file.md)
