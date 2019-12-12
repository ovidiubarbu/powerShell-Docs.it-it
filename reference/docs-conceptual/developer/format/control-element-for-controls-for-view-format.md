---
title: Elemento Control per Controls per View (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 1fd53f55-698d-4df5-bb9a-fe28dc3193e1
caps.latest.revision: 11
ms.openlocfilehash: df568ccb36a2646b983622cdf95718dd5cac62c3
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/05/2019
ms.locfileid: "72363470"
---
# <a name="control-element-for-controls-for-view--format"></a><span data-ttu-id="94000-102">Elemento Control per Controls per View (formato)</span><span class="sxs-lookup"><span data-stu-id="94000-102">Control Element for Controls for View  (Format)</span></span>

<span data-ttu-id="94000-103">Definisce un controllo che può essere utilizzato dalla visualizzazione e dal nome utilizzato per fare riferimento al controllo.</span><span class="sxs-lookup"><span data-stu-id="94000-103">Defines a control that can be used by the view and the name that is used to reference the control.</span></span>

<span data-ttu-id="94000-104">Elemento di configurazione (Format) elemento ViewDefinitions (Format) elemento di visualizzazione (Format) controlli elemento (Format) elemento di controllo per i controlli per la visualizzazione (formato)</span><span class="sxs-lookup"><span data-stu-id="94000-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) Controls Element (Format) Control Element for Controls for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="94000-105">Sintassi</span><span class="sxs-lookup"><span data-stu-id="94000-105">Syntax</span></span>

```xml
<Control>
  <Name>NameOfControl</Name>
  <CustomControl>...</CustomControl>
</Control>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="94000-106">Attributi ed elementi</span><span class="sxs-lookup"><span data-stu-id="94000-106">Attributes and Elements</span></span>

<span data-ttu-id="94000-107">Nelle sezioni seguenti vengono descritti gli attributi, gli elementi figlio e l'elemento padre dell'elemento `Control`.</span><span class="sxs-lookup"><span data-stu-id="94000-107">The following sections describe the attributes, child elements, and the parent element of the `Control` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="94000-108">Attributi</span><span class="sxs-lookup"><span data-stu-id="94000-108">Attributes</span></span>

<span data-ttu-id="94000-109">Nessuna.</span><span class="sxs-lookup"><span data-stu-id="94000-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="94000-110">Elementi figlio</span><span class="sxs-lookup"><span data-stu-id="94000-110">Child Elements</span></span>

|<span data-ttu-id="94000-111">Elemento</span><span class="sxs-lookup"><span data-stu-id="94000-111">Element</span></span>|<span data-ttu-id="94000-112">Description</span><span class="sxs-lookup"><span data-stu-id="94000-112">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="94000-113">Elemento Name per Control per View (Format)</span><span class="sxs-lookup"><span data-stu-id="94000-113">Name Element for Control for View (Format)</span></span>](./name-element-for-control-for-controls-for-view-format.md)|<span data-ttu-id="94000-114">Elemento obbligatorio.</span><span class="sxs-lookup"><span data-stu-id="94000-114">Required element.</span></span><br /><br /> <span data-ttu-id="94000-115">Specifica il nome del controllo.</span><span class="sxs-lookup"><span data-stu-id="94000-115">Specifies the name of the control.</span></span>|
|[<span data-ttu-id="94000-116">Elemento CustomControl per il controllo per i controlli per la visualizzazione (Format)</span><span class="sxs-lookup"><span data-stu-id="94000-116">CustomControl Element for Control for Controls for View (Format)</span></span>](./customcontrol-element-for-control-for-controls-for-view-format.md)|<span data-ttu-id="94000-117">Elemento obbligatorio.</span><span class="sxs-lookup"><span data-stu-id="94000-117">Required element.</span></span><br /><br /> <span data-ttu-id="94000-118">Definisce il controllo utilizzato da questa visualizzazione.</span><span class="sxs-lookup"><span data-stu-id="94000-118">Defines the control used by this view.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="94000-119">Elementi padre</span><span class="sxs-lookup"><span data-stu-id="94000-119">Parent Elements</span></span>

|<span data-ttu-id="94000-120">Elemento</span><span class="sxs-lookup"><span data-stu-id="94000-120">Element</span></span>|<span data-ttu-id="94000-121">Description</span><span class="sxs-lookup"><span data-stu-id="94000-121">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="94000-122">Elemento Controls (Format)</span><span class="sxs-lookup"><span data-stu-id="94000-122">Controls Element (Format)</span></span>](./controls-element-for-view-format.md)|<span data-ttu-id="94000-123">Definisce i controlli di visualizzazione che possono essere utilizzati da una visualizzazione specifica.</span><span class="sxs-lookup"><span data-stu-id="94000-123">Defines the view controls that can be used by a specific view.</span></span>|

## <a name="remarks"></a><span data-ttu-id="94000-124">Osservazioni</span><span class="sxs-lookup"><span data-stu-id="94000-124">Remarks</span></span>

<span data-ttu-id="94000-125">Questo controllo può essere specificato dagli elementi seguenti:</span><span class="sxs-lookup"><span data-stu-id="94000-125">This control can be specified by the following elements:</span></span>

- [<span data-ttu-id="94000-126">Elemento CustomControlName per Expressiongroup per i controlli per la visualizzazione (Format)</span><span class="sxs-lookup"><span data-stu-id="94000-126">CustomControlName Element for ExpressionBinding for Controls for View (Format)</span></span>](./customcontrolname-element-for-expressionbinding-for-controls-for-view-format.md)

- [<span data-ttu-id="94000-127">Elemento CustomControlName per Expression per CustomControl per View (Format)</span><span class="sxs-lookup"><span data-stu-id="94000-127">CustomControlName Element for ExpressionBinding for CustomControl for View (Format)</span></span>](./customcontrolname-element-for-expressionbinding-for-customcontrol-for-view-format.md)

- [<span data-ttu-id="94000-128">Elemento CustomControlName per Expressiongroup per GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="94000-128">CustomControlName Element for ExpressionBinding for GroupBy (Format)</span></span>](./customcontrolname-element-for-expressionbinding-for-groupby-format.md)

- [<span data-ttu-id="94000-129">Elemento CustomControlName per GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="94000-129">CustomControlName Element for GroupBy (Format)</span></span>](./customcontrolname-element-for-groupby-format.md)

## <a name="see-also"></a><span data-ttu-id="94000-130">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="94000-130">See Also</span></span>

[<span data-ttu-id="94000-131">Elemento CustomControl per il controllo per i controlli per la visualizzazione (Format)</span><span class="sxs-lookup"><span data-stu-id="94000-131">CustomControl Element for Control for Controls for View (Format)</span></span>](./customcontrol-element-for-control-for-controls-for-view-format.md)

[<span data-ttu-id="94000-132">Elemento CustomControlName per Expressiongroup per i controlli per la visualizzazione (Format)</span><span class="sxs-lookup"><span data-stu-id="94000-132">CustomControlName Element for ExpressionBinding for Controls for View (Format)</span></span>](./customcontrolname-element-for-expressionbinding-for-controls-for-view-format.md)

[<span data-ttu-id="94000-133">Elemento CustomControlName per Expression per CustomControl per View (Format)</span><span class="sxs-lookup"><span data-stu-id="94000-133">CustomControlName Element for ExpressionBinding for CustomControl for View (Format)</span></span>](./customcontrolname-element-for-expressionbinding-for-customcontrol-for-view-format.md)

[<span data-ttu-id="94000-134">Elemento CustomControlName per Expressiongroup per GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="94000-134">CustomControlName Element for ExpressionBinding for GroupBy (Format)</span></span>](./customcontrolname-element-for-expressionbinding-for-groupby-format.md)

[<span data-ttu-id="94000-135">Elemento CustomControlName per Expressiongroup per GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="94000-135">CustomControlName Element for ExpressionBinding for GroupBy (Format)</span></span>](./customcontrolname-element-for-expressionbinding-for-groupby-format.md)

[<span data-ttu-id="94000-136">Elemento Controls (Format)</span><span class="sxs-lookup"><span data-stu-id="94000-136">Controls Element (Format)</span></span>](./controls-element-for-view-format.md)

[<span data-ttu-id="94000-137">Elemento Name per il controllo per i controlli per la visualizzazione (Format)</span><span class="sxs-lookup"><span data-stu-id="94000-137">Name Element for Control for Controls for View (Format)</span></span>](./name-element-for-control-for-controls-for-view-format.md)

[<span data-ttu-id="94000-138">Scrittura di un file di formattazione di PowerShell</span><span class="sxs-lookup"><span data-stu-id="94000-138">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
