---
title: Elemento Name per il controllo per i controlli per la visualizzazione (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 26437467-d578-4e8d-8cdd-17dfe644957a
caps.latest.revision: 7
ms.openlocfilehash: 7e24aa60f7abae5768707d2527826c452b709002
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/05/2019
ms.locfileid: "72365100"
---
# <a name="name-element-for-control-for-controls-for-view-format"></a><span data-ttu-id="57562-102">Elemento Name per Control per Controls per View (formato)</span><span class="sxs-lookup"><span data-stu-id="57562-102">Name Element for Control for Controls for View (Format)</span></span>

<span data-ttu-id="57562-103">Specifica il nome del controllo.</span><span class="sxs-lookup"><span data-stu-id="57562-103">Specifies the name of the control.</span></span>

<span data-ttu-id="57562-104">Elemento di configurazione (Format) elemento ViewDefinitions (Format) elemento di visualizzazione (Format) controlli elemento (Format) elemento di controllo per i controlli per la visualizzazione (formato) elemento nome per il controllo per visualizzazione (formato)</span><span class="sxs-lookup"><span data-stu-id="57562-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) Controls Element (Format) Control Element for Controls for View (Format) Name Element for Control for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="57562-105">Sintassi</span><span class="sxs-lookup"><span data-stu-id="57562-105">Syntax</span></span>

```xml
<Name>ControlName</Name>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="57562-106">Attributi ed elementi</span><span class="sxs-lookup"><span data-stu-id="57562-106">Attributes and Elements</span></span>

<span data-ttu-id="57562-107">Nelle sezioni seguenti vengono descritti gli attributi, gli elementi figlio e l'elemento padre dell'elemento `Name`.</span><span class="sxs-lookup"><span data-stu-id="57562-107">The following sections describe attributes, child elements, and the parent element of the `Name` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="57562-108">Attributi</span><span class="sxs-lookup"><span data-stu-id="57562-108">Attributes</span></span>

<span data-ttu-id="57562-109">Nessuna.</span><span class="sxs-lookup"><span data-stu-id="57562-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="57562-110">Elementi figlio</span><span class="sxs-lookup"><span data-stu-id="57562-110">Child Elements</span></span>

<span data-ttu-id="57562-111">Nessuna.</span><span class="sxs-lookup"><span data-stu-id="57562-111">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="57562-112">Elementi padre</span><span class="sxs-lookup"><span data-stu-id="57562-112">Parent Elements</span></span>

|<span data-ttu-id="57562-113">Elemento</span><span class="sxs-lookup"><span data-stu-id="57562-113">Element</span></span>|<span data-ttu-id="57562-114">Description</span><span class="sxs-lookup"><span data-stu-id="57562-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="57562-115">Elemento Control per Controls per View (Format)</span><span class="sxs-lookup"><span data-stu-id="57562-115">Control Element for Controls for View (Format)</span></span>](./control-element-for-controls-for-view-format.md)|<span data-ttu-id="57562-116">Definisce un controllo che può essere utilizzato dalla visualizzazione e dal nome utilizzato per fare riferimento al controllo.</span><span class="sxs-lookup"><span data-stu-id="57562-116">Defines a control that can be used by the view and the name that is used to reference the control.</span></span>|

## <a name="text-value"></a><span data-ttu-id="57562-117">Valore testo</span><span class="sxs-lookup"><span data-stu-id="57562-117">Text Value</span></span>

<span data-ttu-id="57562-118">Specificare il nome utilizzato per fare riferimento al controllo.</span><span class="sxs-lookup"><span data-stu-id="57562-118">Specify the name that is used to reference the control.</span></span>

## <a name="remarks"></a><span data-ttu-id="57562-119">Osservazioni</span><span class="sxs-lookup"><span data-stu-id="57562-119">Remarks</span></span>

<span data-ttu-id="57562-120">Il nome specificato qui può essere usato negli elementi seguenti per fare riferimento a questo controllo.</span><span class="sxs-lookup"><span data-stu-id="57562-120">The name specified here can be used in the following elements to reference this control.</span></span>

- <span data-ttu-id="57562-121">Quando si crea una tabella, un elenco, una visualizzazione di controlli di tipo Wide o Custom, il controllo può essere specificato dall'elemento [GroupBy per View (Format)](./groupby-element-for-view-format.md) .</span><span class="sxs-lookup"><span data-stu-id="57562-121">When creating a table, list, wide or custom control view, the control can be specified by the following element: [GroupBy Element for View (Format)](./groupby-element-for-view-format.md)</span></span>

- <span data-ttu-id="57562-122">Quando si crea un altro controllo che può essere usato da una vista, questo controllo può essere specificato dal seguente elemento: [espressione di espressione per CustomItem per i controlli per la visualizzazione (formato)](./expressionbinding-element-for-customitem-for-controls-for-view-format.md)</span><span class="sxs-lookup"><span data-stu-id="57562-122">When creating another control that can be used by a view, this control can be specified by the following element: [ExpressionBinding Element for CustomItem for Controls for View (Format)](./expressionbinding-element-for-customitem-for-controls-for-view-format.md)</span></span>

## <a name="see-also"></a><span data-ttu-id="57562-123">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="57562-123">See Also</span></span>

[<span data-ttu-id="57562-124">Elemento GroupBy per View (Format)</span><span class="sxs-lookup"><span data-stu-id="57562-124">GroupBy Element for View (Format)</span></span>](./groupby-element-for-view-format.md)

[<span data-ttu-id="57562-125">Elemento expressiongroup per CustomItem per i controlli per la visualizzazione (Format)</span><span class="sxs-lookup"><span data-stu-id="57562-125">ExpressionBinding Element for CustomItem for Controls for View (Format)</span></span>](./expressionbinding-element-for-customitem-for-controls-for-view-format.md)

[<span data-ttu-id="57562-126">Elemento Control per Controls per View (Format)</span><span class="sxs-lookup"><span data-stu-id="57562-126">Control Element for Controls for View (Format)</span></span>](./control-element-for-controls-for-view-format.md)

[<span data-ttu-id="57562-127">Scrittura di un file di formattazione di PowerShell</span><span class="sxs-lookup"><span data-stu-id="57562-127">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
