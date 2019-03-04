---
title: Elemento CustomControlName per ExpressionBinding per i controlli per la visualizzazione (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 4b6ee11e-9086-41d2-afd3-42fb9f24da69
caps.latest.revision: 7
ms.openlocfilehash: bf1d57447f9018f1535af14466427aaeabc048f3
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/03/2019
ms.locfileid: "56855597"
---
# <a name="customcontrolname-element-for-expressionbinding-for-controls-for-view-format"></a><span data-ttu-id="69267-102">Elemento CustomControlName per ExpressionBinding per Controls per View (formato)</span><span class="sxs-lookup"><span data-stu-id="69267-102">CustomControlName Element for ExpressionBinding for Controls for View (Format)</span></span>

<span data-ttu-id="69267-103">Specifica il nome di un controllo comune o un controllo di visualizzazione.</span><span class="sxs-lookup"><span data-stu-id="69267-103">Specifies the name of a common control or a view control.</span></span> <span data-ttu-id="69267-104">Questo elemento viene usato quando si definiscono i controlli che possono essere usati da una vista.</span><span class="sxs-lookup"><span data-stu-id="69267-104">This element is used when defining controls that can be used by a view.</span></span>

<span data-ttu-id="69267-105">Elemento (formato) elemento ViewDefinitions (formato) visualizzazione elemento (formato) i controlli elemento (formato) controllo elemento di configurazione per i controlli elemento di visualizzazione (formato) CustomControl per il controllo per i controlli elemento di visualizzazione (formato) CustomEntries per Elemento di visualizzazione (formato) CustomEntry per CustomEntries per i controlli elemento di visualizzazione (formato) CustomItem per CustomEntry per i controlli elemento di visualizzazione (formato) ExpressionBinding per CustomItem per i controlli per la visualizzazione (formato) CustomControlName CustomControl Elemento per ExpressionBindine per i controlli per la visualizzazione (formato)</span><span class="sxs-lookup"><span data-stu-id="69267-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) Controls Element (Format) Control Element for Controls for View (Format) CustomControl Element for Control for Controls for View (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for Controls for View (Format) CustomItem Element for CustomEntry for Controls for View (Format) ExpressionBinding Element for CustomItem for Controls for View (Format) CustomControlName Element for ExpressionBindine for Controls for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="69267-106">Sintassi</span><span class="sxs-lookup"><span data-stu-id="69267-106">Syntax</span></span>

```xml
<CustomControlName>NameofCustomControl</CustomControlName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="69267-107">Attributi ed elementi</span><span class="sxs-lookup"><span data-stu-id="69267-107">Attributes and Elements</span></span>

<span data-ttu-id="69267-108">Le sezioni seguenti descrivono gli attributi e gli elementi figlio dell'elemento padre del `CustomControlName` elemento.</span><span class="sxs-lookup"><span data-stu-id="69267-108">The following sections describe attributes, child elements, and the parent element of the `CustomControlName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="69267-109">Attributes</span><span class="sxs-lookup"><span data-stu-id="69267-109">Attributes</span></span>

<span data-ttu-id="69267-110">Nessuna.</span><span class="sxs-lookup"><span data-stu-id="69267-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="69267-111">Elementi figlio</span><span class="sxs-lookup"><span data-stu-id="69267-111">Child Elements</span></span>

<span data-ttu-id="69267-112">Nessuna.</span><span class="sxs-lookup"><span data-stu-id="69267-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="69267-113">Elementi padre</span><span class="sxs-lookup"><span data-stu-id="69267-113">Parent Elements</span></span>

|<span data-ttu-id="69267-114">Elemento</span><span class="sxs-lookup"><span data-stu-id="69267-114">Element</span></span>|<span data-ttu-id="69267-115">Description</span><span class="sxs-lookup"><span data-stu-id="69267-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="69267-116">Elemento ExpressionBinding per CustomItem per i controlli per la visualizzazione (formato)</span><span class="sxs-lookup"><span data-stu-id="69267-116">ExpressionBinding Element for CustomItem for Controls for View (Format)</span></span>](./expressionbinding-element-for-customitem-for-controls-for-view-format.md)|<span data-ttu-id="69267-117">Definisce i dati che vengano visualizzati dal controllo.</span><span class="sxs-lookup"><span data-stu-id="69267-117">Defines the data that is displayed by the control.</span></span>|

## <a name="text-value"></a><span data-ttu-id="69267-118">Valore di testo</span><span class="sxs-lookup"><span data-stu-id="69267-118">Text Value</span></span>

<span data-ttu-id="69267-119">Specificare il nome del controllo.</span><span class="sxs-lookup"><span data-stu-id="69267-119">Specify the name of the control.</span></span>

## <a name="remarks"></a><span data-ttu-id="69267-120">Osservazioni</span><span class="sxs-lookup"><span data-stu-id="69267-120">Remarks</span></span>

<span data-ttu-id="69267-121">È possibile creare controlli comuni che possono essere usati da tutte le visualizzazioni di un file di formattazione ed è possibile creare controlli di visualizzazione che possono essere usati da una visualizzazione specifica.</span><span class="sxs-lookup"><span data-stu-id="69267-121">You can create common controls that can be used by all the views of a formatting file, and you can create view controls that can be used by a specific view.</span></span> <span data-ttu-id="69267-122">Gli elementi seguenti specificano i nomi di questi controlli:</span><span class="sxs-lookup"><span data-stu-id="69267-122">The following elements specify the names of these controls:</span></span>

- [<span data-ttu-id="69267-123">Elemento Name per il controllo per i controlli per la configurazione (formato)</span><span class="sxs-lookup"><span data-stu-id="69267-123">Name Element for Control for Controls for Configuration (Format)</span></span>](./name-element-for-control-for-controls-for-configuration-format.md)

- [<span data-ttu-id="69267-124">Elemento Name per il controllo per i controlli per la visualizzazione (formato)</span><span class="sxs-lookup"><span data-stu-id="69267-124">Name Element for Control for Controls for View (Format)</span></span>](./name-element-for-control-for-controls-for-view-format.md)

## <a name="see-also"></a><span data-ttu-id="69267-125">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="69267-125">See Also</span></span>

[<span data-ttu-id="69267-126">Elemento Name per il controllo per i controlli per la configurazione (formato)</span><span class="sxs-lookup"><span data-stu-id="69267-126">Name Element for Control for Controls for Configuration (Format)</span></span>](./name-element-for-control-for-controls-for-configuration-format.md)

[<span data-ttu-id="69267-127">Elemento Name per il controllo per i controlli per la visualizzazione (formato)</span><span class="sxs-lookup"><span data-stu-id="69267-127">Name Element for Control for Controls for View (Format)</span></span>](./name-element-for-control-for-controls-for-view-format.md)

[<span data-ttu-id="69267-128">Elemento ExpressionBinding per CustomItem per i controlli per la visualizzazione (formato)</span><span class="sxs-lookup"><span data-stu-id="69267-128">ExpressionBinding Element for CustomItem for Controls for View (Format)</span></span>](./expressionbinding-element-for-customitem-for-controls-for-view-format.md)

[<span data-ttu-id="69267-129">La scrittura di un File di formattazione di PowerShell</span><span class="sxs-lookup"><span data-stu-id="69267-129">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
