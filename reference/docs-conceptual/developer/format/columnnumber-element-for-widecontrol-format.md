---
title: Elemento ColumnNumber per WideControl (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: fe9eb5f9-a193-41a4-ad47-a96ba3f8d7e3
caps.latest.revision: 8
ms.openlocfilehash: 49f501538b8f72777984a5e575b999866abcdebf
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/05/2019
ms.locfileid: "72364220"
---
# <a name="columnnumber-element-for-widecontrol-format"></a><span data-ttu-id="9bf54-102">Elemento ColumnNumber per WideControl (formato)</span><span class="sxs-lookup"><span data-stu-id="9bf54-102">ColumnNumber Element for WideControl (Format)</span></span>

<span data-ttu-id="9bf54-103">Specifica il numero di colonne visualizzate nella visualizzazione estesa.</span><span class="sxs-lookup"><span data-stu-id="9bf54-103">Specifies the number of columns displayed in the wide view.</span></span>

<span data-ttu-id="9bf54-104">Elemento Configuration (Format) elemento ViewDefinitions (Format) elemento View (Format) elemento WideControl (Format) elemento ColumnNumber per WideControl (Format)</span><span class="sxs-lookup"><span data-stu-id="9bf54-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) WideControl Element (Format) ColumnNumber Element for WideControl (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="9bf54-105">Sintassi</span><span class="sxs-lookup"><span data-stu-id="9bf54-105">Syntax</span></span>

```xml
<ColumnNumber>PositiveInteger</ColumnNumber>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="9bf54-106">Attributi ed elementi</span><span class="sxs-lookup"><span data-stu-id="9bf54-106">Attributes and Elements</span></span>

<span data-ttu-id="9bf54-107">Nelle sezioni seguenti vengono descritti gli attributi, gli elementi figlio e l'elemento padre dell'elemento `ColumnNumber`.</span><span class="sxs-lookup"><span data-stu-id="9bf54-107">The following sections describe attributes, child elements, and the parent element of the `ColumnNumber` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="9bf54-108">Attributi</span><span class="sxs-lookup"><span data-stu-id="9bf54-108">Attributes</span></span>

<span data-ttu-id="9bf54-109">Nessuna.</span><span class="sxs-lookup"><span data-stu-id="9bf54-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="9bf54-110">Elementi figlio</span><span class="sxs-lookup"><span data-stu-id="9bf54-110">Child Elements</span></span>

<span data-ttu-id="9bf54-111">Nessuna.</span><span class="sxs-lookup"><span data-stu-id="9bf54-111">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="9bf54-112">Elementi padre</span><span class="sxs-lookup"><span data-stu-id="9bf54-112">Parent Elements</span></span>

|<span data-ttu-id="9bf54-113">Elemento</span><span class="sxs-lookup"><span data-stu-id="9bf54-113">Element</span></span>|<span data-ttu-id="9bf54-114">Description</span><span class="sxs-lookup"><span data-stu-id="9bf54-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="9bf54-115">Elemento WideControl (Format)</span><span class="sxs-lookup"><span data-stu-id="9bf54-115">WideControl Element (Format)</span></span>](./widecontrol-element-format.md)|<span data-ttu-id="9bf54-116">Definisce un formato di elenco Wide (valore singolo) per la visualizzazione.</span><span class="sxs-lookup"><span data-stu-id="9bf54-116">Defines a wide (single value) list format for the view.</span></span>|

## <a name="text-value"></a><span data-ttu-id="9bf54-117">Valore testo</span><span class="sxs-lookup"><span data-stu-id="9bf54-117">Text Value</span></span>

<span data-ttu-id="9bf54-118">Specificare un valore intero positivo.</span><span class="sxs-lookup"><span data-stu-id="9bf54-118">Specify a positive integer value.</span></span>

## <a name="remarks"></a><span data-ttu-id="9bf54-119">Osservazioni</span><span class="sxs-lookup"><span data-stu-id="9bf54-119">Remarks</span></span>

<span data-ttu-id="9bf54-120">Quando si definisce una visualizzazione estesa, è possibile aggiungere l'elemento `AutoSize` o l'elemento `ColumnNumber`, ma non è possibile aggiungere entrambi.</span><span class="sxs-lookup"><span data-stu-id="9bf54-120">When defining a wide view, you can add the `AutoSize` element or the `ColumnNumber` element, but you cannot add both.</span></span>

<span data-ttu-id="9bf54-121">Per ulteriori informazioni sui componenti di una visualizzazione estesa, vedere [creazione di un'ampia visualizzazione](./creating-a-wide-view.md).</span><span class="sxs-lookup"><span data-stu-id="9bf54-121">For more information about the components of a wide view, see [Creating a Wide View](./creating-a-wide-view.md).</span></span>

<span data-ttu-id="9bf54-122">Per un esempio di visualizzazione estesa, vedere [Wide View (Basic)](./wide-view-basic.md).</span><span class="sxs-lookup"><span data-stu-id="9bf54-122">For an example of a wide view, see [Wide View (Basic)](./wide-view-basic.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="9bf54-123">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="9bf54-123">See Also</span></span>

[<span data-ttu-id="9bf54-124">Elemento AutoSize per WideControl (Format)</span><span class="sxs-lookup"><span data-stu-id="9bf54-124">Autosize Element for WideControl (Format)</span></span>](./autosize-element-for-widecontrol-format.md)

[<span data-ttu-id="9bf54-125">Creazione di una visualizzazione estesa</span><span class="sxs-lookup"><span data-stu-id="9bf54-125">Creating a Wide View</span></span>](./creating-a-wide-view.md)

[<span data-ttu-id="9bf54-126">Visualizzazione estesa (di base)</span><span class="sxs-lookup"><span data-stu-id="9bf54-126">Wide View (Basic)</span></span>](./wide-view-basic.md)

[<span data-ttu-id="9bf54-127">Scrittura di un file di formattazione di PowerShell</span><span class="sxs-lookup"><span data-stu-id="9bf54-127">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
