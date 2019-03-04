---
title: Nome elemento per il controllo per i controlli per la visualizzazione (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 26437467-d578-4e8d-8cdd-17dfe644957a
caps.latest.revision: 7
ms.openlocfilehash: 7e24aa60f7abae5768707d2527826c452b709002
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/03/2019
ms.locfileid: "56862387"
---
# <a name="name-element-for-control-for-controls-for-view-format"></a><span data-ttu-id="eed50-102">Elemento Name per Control per Controls per View (formato)</span><span class="sxs-lookup"><span data-stu-id="eed50-102">Name Element for Control for Controls for View (Format)</span></span>

<span data-ttu-id="eed50-103">Specifica il nome del controllo.</span><span class="sxs-lookup"><span data-stu-id="eed50-103">Specifies the name of the control.</span></span>

<span data-ttu-id="eed50-104">Elemento (formato) elemento ViewDefinitions (formato) Visualizza elemento di configurazione (formato) controlla controllo elemento (formato) per i controlli elemento di visualizzazione (formato) nome per il controllo per la visualizzazione (formato)</span><span class="sxs-lookup"><span data-stu-id="eed50-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) Controls Element (Format) Control Element for Controls for View (Format) Name Element for Control for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="eed50-105">Sintassi</span><span class="sxs-lookup"><span data-stu-id="eed50-105">Syntax</span></span>

```xml
<Name>ControlName</Name>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="eed50-106">Attributi ed elementi</span><span class="sxs-lookup"><span data-stu-id="eed50-106">Attributes and Elements</span></span>

<span data-ttu-id="eed50-107">Le sezioni seguenti descrivono gli attributi e gli elementi figlio dell'elemento padre del `Name` elemento.</span><span class="sxs-lookup"><span data-stu-id="eed50-107">The following sections describe attributes, child elements, and the parent element of the `Name` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="eed50-108">Attributes</span><span class="sxs-lookup"><span data-stu-id="eed50-108">Attributes</span></span>

<span data-ttu-id="eed50-109">Nessuna.</span><span class="sxs-lookup"><span data-stu-id="eed50-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="eed50-110">Elementi figlio</span><span class="sxs-lookup"><span data-stu-id="eed50-110">Child Elements</span></span>

<span data-ttu-id="eed50-111">Nessuna.</span><span class="sxs-lookup"><span data-stu-id="eed50-111">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="eed50-112">Elementi padre</span><span class="sxs-lookup"><span data-stu-id="eed50-112">Parent Elements</span></span>

|<span data-ttu-id="eed50-113">Elemento</span><span class="sxs-lookup"><span data-stu-id="eed50-113">Element</span></span>|<span data-ttu-id="eed50-114">Description</span><span class="sxs-lookup"><span data-stu-id="eed50-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="eed50-115">Elemento di controllo per i controlli per la visualizzazione (formato)</span><span class="sxs-lookup"><span data-stu-id="eed50-115">Control Element for Controls for View (Format)</span></span>](./control-element-for-controls-for-view-format.md)|<span data-ttu-id="eed50-116">Definisce un controllo che può essere utilizzato per la visualizzazione e il nome utilizzato per fare riferimento al controllo.</span><span class="sxs-lookup"><span data-stu-id="eed50-116">Defines a control that can be used by the view and the name that is used to reference the control.</span></span>|

## <a name="text-value"></a><span data-ttu-id="eed50-117">Valore di testo</span><span class="sxs-lookup"><span data-stu-id="eed50-117">Text Value</span></span>

<span data-ttu-id="eed50-118">Specificare il nome utilizzato per fare riferimento al controllo.</span><span class="sxs-lookup"><span data-stu-id="eed50-118">Specify the name that is used to reference the control.</span></span>

## <a name="remarks"></a><span data-ttu-id="eed50-119">Osservazioni</span><span class="sxs-lookup"><span data-stu-id="eed50-119">Remarks</span></span>

<span data-ttu-id="eed50-120">Il nome specificato qui è utilizzabile negli elementi seguenti per fare riferimento a questo controllo.</span><span class="sxs-lookup"><span data-stu-id="eed50-120">The name specified here can be used in the following elements to reference this control.</span></span>

- <span data-ttu-id="eed50-121">Quando si crea una tabella, elenco, visualizzazione controllo wide o personalizzato, il controllo può essere specificato dal seguente elemento: [Elemento GroupBy per visualizzazione (formato)](./groupby-element-for-view-format.md)</span><span class="sxs-lookup"><span data-stu-id="eed50-121">When creating a table, list, wide or custom control view, the control can be specified by the following element: [GroupBy Element for View (Format)](./groupby-element-for-view-format.md)</span></span>

- <span data-ttu-id="eed50-122">Quando la creazione di un altro controllo che può essere usata da una vista, questo controllo può essere specificato per l'elemento seguente: [Elemento ExpressionBinding per CustomItem per i controlli per la visualizzazione (formato)](./expressionbinding-element-for-customitem-for-controls-for-view-format.md)</span><span class="sxs-lookup"><span data-stu-id="eed50-122">When creating another control that can be used by a view, this control can be specified by the following element: [ExpressionBinding Element for CustomItem for Controls for View (Format)](./expressionbinding-element-for-customitem-for-controls-for-view-format.md)</span></span>

## <a name="see-also"></a><span data-ttu-id="eed50-123">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="eed50-123">See Also</span></span>

[<span data-ttu-id="eed50-124">Elemento GroupBy per visualizzazione (formato)</span><span class="sxs-lookup"><span data-stu-id="eed50-124">GroupBy Element for View (Format)</span></span>](./groupby-element-for-view-format.md)

[<span data-ttu-id="eed50-125">Elemento ExpressionBinding per CustomItem per i controlli per la visualizzazione (formato)</span><span class="sxs-lookup"><span data-stu-id="eed50-125">ExpressionBinding Element for CustomItem for Controls for View (Format)</span></span>](./expressionbinding-element-for-customitem-for-controls-for-view-format.md)

[<span data-ttu-id="eed50-126">Elemento di controllo per i controlli per la visualizzazione (formato)</span><span class="sxs-lookup"><span data-stu-id="eed50-126">Control Element for Controls for View (Format)</span></span>](./control-element-for-controls-for-view-format.md)

[<span data-ttu-id="eed50-127">La scrittura di un File di formattazione di PowerShell</span><span class="sxs-lookup"><span data-stu-id="eed50-127">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
