---
title: Elemento Control per i controlli per la visualizzazione (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 1fd53f55-698d-4df5-bb9a-fe28dc3193e1
caps.latest.revision: 11
ms.openlocfilehash: df568ccb36a2646b983622cdf95718dd5cac62c3
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62066771"
---
# <a name="control-element-for-controls-for-view--format"></a><span data-ttu-id="c57cd-102">Elemento Control per Controls per View (formato)</span><span class="sxs-lookup"><span data-stu-id="c57cd-102">Control Element for Controls for View  (Format)</span></span>

<span data-ttu-id="c57cd-103">Definisce un controllo che può essere utilizzato per la visualizzazione e il nome utilizzato per fare riferimento al controllo.</span><span class="sxs-lookup"><span data-stu-id="c57cd-103">Defines a control that can be used by the view and the name that is used to reference the control.</span></span>

<span data-ttu-id="c57cd-104">Elemento di visualizzazione configurazione elemento (formato) elemento ViewDefinitions (formato) (formato) controlla controllo elemento (formato) per i controlli per visualizzazione (formato)</span><span class="sxs-lookup"><span data-stu-id="c57cd-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) Controls Element (Format) Control Element for Controls for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="c57cd-105">Sintassi</span><span class="sxs-lookup"><span data-stu-id="c57cd-105">Syntax</span></span>

```xml
<Control>
  <Name>NameOfControl</Name>
  <CustomControl>...</CustomControl>
</Control>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="c57cd-106">Elementi e attributi</span><span class="sxs-lookup"><span data-stu-id="c57cd-106">Attributes and Elements</span></span>

<span data-ttu-id="c57cd-107">Le sezioni seguenti descrivono gli attributi e gli elementi figlio dell'elemento padre del `Control` elemento.</span><span class="sxs-lookup"><span data-stu-id="c57cd-107">The following sections describe the attributes, child elements, and the parent element of the `Control` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="c57cd-108">Attributes</span><span class="sxs-lookup"><span data-stu-id="c57cd-108">Attributes</span></span>

<span data-ttu-id="c57cd-109">Nessuna.</span><span class="sxs-lookup"><span data-stu-id="c57cd-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="c57cd-110">Elementi figlio</span><span class="sxs-lookup"><span data-stu-id="c57cd-110">Child Elements</span></span>

|<span data-ttu-id="c57cd-111">Elemento</span><span class="sxs-lookup"><span data-stu-id="c57cd-111">Element</span></span>|<span data-ttu-id="c57cd-112">Description</span><span class="sxs-lookup"><span data-stu-id="c57cd-112">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="c57cd-113">Elemento Name per il controllo di visualizzazione (formato)</span><span class="sxs-lookup"><span data-stu-id="c57cd-113">Name Element for Control for View (Format)</span></span>](./name-element-for-control-for-controls-for-view-format.md)|<span data-ttu-id="c57cd-114">Elemento obbligatorio.</span><span class="sxs-lookup"><span data-stu-id="c57cd-114">Required element.</span></span><br /><br /> <span data-ttu-id="c57cd-115">Specifica il nome del controllo.</span><span class="sxs-lookup"><span data-stu-id="c57cd-115">Specifies the name of the control.</span></span>|
|[<span data-ttu-id="c57cd-116">Elemento CustomControl per il controllo per i controlli per la visualizzazione (formato)</span><span class="sxs-lookup"><span data-stu-id="c57cd-116">CustomControl Element for Control for Controls for View (Format)</span></span>](./customcontrol-element-for-control-for-controls-for-view-format.md)|<span data-ttu-id="c57cd-117">Elemento obbligatorio.</span><span class="sxs-lookup"><span data-stu-id="c57cd-117">Required element.</span></span><br /><br /> <span data-ttu-id="c57cd-118">Definisce il controllo utilizzato da questa vista.</span><span class="sxs-lookup"><span data-stu-id="c57cd-118">Defines the control used by this view.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="c57cd-119">Elementi padre</span><span class="sxs-lookup"><span data-stu-id="c57cd-119">Parent Elements</span></span>

|<span data-ttu-id="c57cd-120">Elemento</span><span class="sxs-lookup"><span data-stu-id="c57cd-120">Element</span></span>|<span data-ttu-id="c57cd-121">Description</span><span class="sxs-lookup"><span data-stu-id="c57cd-121">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="c57cd-122">Elemento Controls (formato)</span><span class="sxs-lookup"><span data-stu-id="c57cd-122">Controls Element (Format)</span></span>](./controls-element-for-view-format.md)|<span data-ttu-id="c57cd-123">Definisce i controlli di visualizzazione che possono essere usati da una visualizzazione specifica.</span><span class="sxs-lookup"><span data-stu-id="c57cd-123">Defines the view controls that can be used by a specific view.</span></span>|

## <a name="remarks"></a><span data-ttu-id="c57cd-124">Osservazioni</span><span class="sxs-lookup"><span data-stu-id="c57cd-124">Remarks</span></span>

<span data-ttu-id="c57cd-125">Questo controllo può essere specificato dagli elementi seguenti:</span><span class="sxs-lookup"><span data-stu-id="c57cd-125">This control can be specified by the following elements:</span></span>

- [<span data-ttu-id="c57cd-126">Elemento CustomControlName per ExpressionBinding per i controlli per la visualizzazione (formato)</span><span class="sxs-lookup"><span data-stu-id="c57cd-126">CustomControlName Element for ExpressionBinding for Controls for View (Format)</span></span>](./customcontrolname-element-for-expressionbinding-for-controls-for-view-format.md)

- [<span data-ttu-id="c57cd-127">Elemento CustomControlName per ExpressionBinding per CustomControl per visualizzazione (formato)</span><span class="sxs-lookup"><span data-stu-id="c57cd-127">CustomControlName Element for ExpressionBinding for CustomControl for View (Format)</span></span>](./customcontrolname-element-for-expressionbinding-for-customcontrol-for-view-format.md)

- [<span data-ttu-id="c57cd-128">Elemento CustomControlName per ExpressionBinding per GroupBy (formato)</span><span class="sxs-lookup"><span data-stu-id="c57cd-128">CustomControlName Element for ExpressionBinding for GroupBy (Format)</span></span>](./customcontrolname-element-for-expressionbinding-for-groupby-format.md)

- [<span data-ttu-id="c57cd-129">Elemento CustomControlName per GroupBy (formato)</span><span class="sxs-lookup"><span data-stu-id="c57cd-129">CustomControlName Element for GroupBy (Format)</span></span>](./customcontrolname-element-for-groupby-format.md)

## <a name="see-also"></a><span data-ttu-id="c57cd-130">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="c57cd-130">See Also</span></span>

[<span data-ttu-id="c57cd-131">Elemento CustomControl per il controllo per i controlli per la visualizzazione (formato)</span><span class="sxs-lookup"><span data-stu-id="c57cd-131">CustomControl Element for Control for Controls for View (Format)</span></span>](./customcontrol-element-for-control-for-controls-for-view-format.md)

[<span data-ttu-id="c57cd-132">Elemento CustomControlName per ExpressionBinding per i controlli per la visualizzazione (formato)</span><span class="sxs-lookup"><span data-stu-id="c57cd-132">CustomControlName Element for ExpressionBinding for Controls for View (Format)</span></span>](./customcontrolname-element-for-expressionbinding-for-controls-for-view-format.md)

[<span data-ttu-id="c57cd-133">Elemento CustomControlName per ExpressionBinding per CustomControl per visualizzazione (formato)</span><span class="sxs-lookup"><span data-stu-id="c57cd-133">CustomControlName Element for ExpressionBinding for CustomControl for View (Format)</span></span>](./customcontrolname-element-for-expressionbinding-for-customcontrol-for-view-format.md)

[<span data-ttu-id="c57cd-134">Elemento CustomControlName per ExpressionBinding per GroupBy (formato)</span><span class="sxs-lookup"><span data-stu-id="c57cd-134">CustomControlName Element for ExpressionBinding for GroupBy (Format)</span></span>](./customcontrolname-element-for-expressionbinding-for-groupby-format.md)

[<span data-ttu-id="c57cd-135">Elemento CustomControlName per ExpressionBinding per GroupBy (formato)</span><span class="sxs-lookup"><span data-stu-id="c57cd-135">CustomControlName Element for ExpressionBinding for GroupBy (Format)</span></span>](./customcontrolname-element-for-expressionbinding-for-groupby-format.md)

[<span data-ttu-id="c57cd-136">Elemento Controls (formato)</span><span class="sxs-lookup"><span data-stu-id="c57cd-136">Controls Element (Format)</span></span>](./controls-element-for-view-format.md)

[<span data-ttu-id="c57cd-137">Elemento Name per il controllo per i controlli per la visualizzazione (formato)</span><span class="sxs-lookup"><span data-stu-id="c57cd-137">Name Element for Control for Controls for View (Format)</span></span>](./name-element-for-control-for-controls-for-view-format.md)

[<span data-ttu-id="c57cd-138">La scrittura di un File di formattazione di PowerShell</span><span class="sxs-lookup"><span data-stu-id="c57cd-138">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
