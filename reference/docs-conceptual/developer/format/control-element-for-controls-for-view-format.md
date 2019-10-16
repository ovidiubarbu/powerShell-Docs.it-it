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
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/15/2019
ms.locfileid: "72363470"
---
# <a name="control-element-for-controls-for-view--format"></a><span data-ttu-id="4669a-102">Elemento Control per Controls per View (formato)</span><span class="sxs-lookup"><span data-stu-id="4669a-102">Control Element for Controls for View  (Format)</span></span>

<span data-ttu-id="4669a-103">Definisce un controllo che può essere utilizzato dalla visualizzazione e dal nome utilizzato per fare riferimento al controllo.</span><span class="sxs-lookup"><span data-stu-id="4669a-103">Defines a control that can be used by the view and the name that is used to reference the control.</span></span>

<span data-ttu-id="4669a-104">Elemento di configurazione (Format) elemento ViewDefinitions (Format) elemento di visualizzazione (Format) controlli elemento (Format) elemento di controllo per i controlli per la visualizzazione (formato)</span><span class="sxs-lookup"><span data-stu-id="4669a-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) Controls Element (Format) Control Element for Controls for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="4669a-105">Sintassi</span><span class="sxs-lookup"><span data-stu-id="4669a-105">Syntax</span></span>

```xml
<Control>
  <Name>NameOfControl</Name>
  <CustomControl>...</CustomControl>
</Control>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="4669a-106">Attributi ed elementi</span><span class="sxs-lookup"><span data-stu-id="4669a-106">Attributes and Elements</span></span>

<span data-ttu-id="4669a-107">Nelle sezioni seguenti vengono descritti gli attributi, gli elementi figlio e l'elemento padre dell'elemento `Control`.</span><span class="sxs-lookup"><span data-stu-id="4669a-107">The following sections describe the attributes, child elements, and the parent element of the `Control` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="4669a-108">Attributi</span><span class="sxs-lookup"><span data-stu-id="4669a-108">Attributes</span></span>

<span data-ttu-id="4669a-109">Nessuna.</span><span class="sxs-lookup"><span data-stu-id="4669a-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="4669a-110">Elementi figlio</span><span class="sxs-lookup"><span data-stu-id="4669a-110">Child Elements</span></span>

|<span data-ttu-id="4669a-111">Elemento</span><span class="sxs-lookup"><span data-stu-id="4669a-111">Element</span></span>|<span data-ttu-id="4669a-112">Description</span><span class="sxs-lookup"><span data-stu-id="4669a-112">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="4669a-113">Elemento Name per Control per View (Format)</span><span class="sxs-lookup"><span data-stu-id="4669a-113">Name Element for Control for View (Format)</span></span>](./name-element-for-control-for-controls-for-view-format.md)|<span data-ttu-id="4669a-114">Elemento obbligatorio.</span><span class="sxs-lookup"><span data-stu-id="4669a-114">Required element.</span></span><br /><br /> <span data-ttu-id="4669a-115">Specifica il nome del controllo.</span><span class="sxs-lookup"><span data-stu-id="4669a-115">Specifies the name of the control.</span></span>|
|[<span data-ttu-id="4669a-116">Elemento CustomControl per il controllo per i controlli per la visualizzazione (Format)</span><span class="sxs-lookup"><span data-stu-id="4669a-116">CustomControl Element for Control for Controls for View (Format)</span></span>](./customcontrol-element-for-control-for-controls-for-view-format.md)|<span data-ttu-id="4669a-117">Elemento obbligatorio.</span><span class="sxs-lookup"><span data-stu-id="4669a-117">Required element.</span></span><br /><br /> <span data-ttu-id="4669a-118">Definisce il controllo utilizzato da questa visualizzazione.</span><span class="sxs-lookup"><span data-stu-id="4669a-118">Defines the control used by this view.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="4669a-119">Elementi padre</span><span class="sxs-lookup"><span data-stu-id="4669a-119">Parent Elements</span></span>

|<span data-ttu-id="4669a-120">Elemento</span><span class="sxs-lookup"><span data-stu-id="4669a-120">Element</span></span>|<span data-ttu-id="4669a-121">Description</span><span class="sxs-lookup"><span data-stu-id="4669a-121">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="4669a-122">Elemento Controls (Format)</span><span class="sxs-lookup"><span data-stu-id="4669a-122">Controls Element (Format)</span></span>](./controls-element-for-view-format.md)|<span data-ttu-id="4669a-123">Definisce i controlli di visualizzazione che possono essere utilizzati da una visualizzazione specifica.</span><span class="sxs-lookup"><span data-stu-id="4669a-123">Defines the view controls that can be used by a specific view.</span></span>|

## <a name="remarks"></a><span data-ttu-id="4669a-124">Osservazioni</span><span class="sxs-lookup"><span data-stu-id="4669a-124">Remarks</span></span>

<span data-ttu-id="4669a-125">Questo controllo può essere specificato dagli elementi seguenti:</span><span class="sxs-lookup"><span data-stu-id="4669a-125">This control can be specified by the following elements:</span></span>

- [<span data-ttu-id="4669a-126">Elemento CustomControlName per Expressiongroup per i controlli per la visualizzazione (Format)</span><span class="sxs-lookup"><span data-stu-id="4669a-126">CustomControlName Element for ExpressionBinding for Controls for View (Format)</span></span>](./customcontrolname-element-for-expressionbinding-for-controls-for-view-format.md)

- [<span data-ttu-id="4669a-127">Elemento CustomControlName per Expression per CustomControl per View (Format)</span><span class="sxs-lookup"><span data-stu-id="4669a-127">CustomControlName Element for ExpressionBinding for CustomControl for View (Format)</span></span>](./customcontrolname-element-for-expressionbinding-for-customcontrol-for-view-format.md)

- [<span data-ttu-id="4669a-128">Elemento CustomControlName per Expressiongroup per GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="4669a-128">CustomControlName Element for ExpressionBinding for GroupBy (Format)</span></span>](./customcontrolname-element-for-expressionbinding-for-groupby-format.md)

- [<span data-ttu-id="4669a-129">Elemento CustomControlName per GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="4669a-129">CustomControlName Element for GroupBy (Format)</span></span>](./customcontrolname-element-for-groupby-format.md)

## <a name="see-also"></a><span data-ttu-id="4669a-130">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="4669a-130">See Also</span></span>

[<span data-ttu-id="4669a-131">Elemento CustomControl per il controllo per i controlli per la visualizzazione (Format)</span><span class="sxs-lookup"><span data-stu-id="4669a-131">CustomControl Element for Control for Controls for View (Format)</span></span>](./customcontrol-element-for-control-for-controls-for-view-format.md)

[<span data-ttu-id="4669a-132">Elemento CustomControlName per Expressiongroup per i controlli per la visualizzazione (Format)</span><span class="sxs-lookup"><span data-stu-id="4669a-132">CustomControlName Element for ExpressionBinding for Controls for View (Format)</span></span>](./customcontrolname-element-for-expressionbinding-for-controls-for-view-format.md)

[<span data-ttu-id="4669a-133">Elemento CustomControlName per Expression per CustomControl per View (Format)</span><span class="sxs-lookup"><span data-stu-id="4669a-133">CustomControlName Element for ExpressionBinding for CustomControl for View (Format)</span></span>](./customcontrolname-element-for-expressionbinding-for-customcontrol-for-view-format.md)

[<span data-ttu-id="4669a-134">Elemento CustomControlName per Expressiongroup per GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="4669a-134">CustomControlName Element for ExpressionBinding for GroupBy (Format)</span></span>](./customcontrolname-element-for-expressionbinding-for-groupby-format.md)

[<span data-ttu-id="4669a-135">Elemento CustomControlName per Expressiongroup per GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="4669a-135">CustomControlName Element for ExpressionBinding for GroupBy (Format)</span></span>](./customcontrolname-element-for-expressionbinding-for-groupby-format.md)

[<span data-ttu-id="4669a-136">Elemento Controls (Format)</span><span class="sxs-lookup"><span data-stu-id="4669a-136">Controls Element (Format)</span></span>](./controls-element-for-view-format.md)

[<span data-ttu-id="4669a-137">Elemento Name per il controllo per i controlli per la visualizzazione (Format)</span><span class="sxs-lookup"><span data-stu-id="4669a-137">Name Element for Control for Controls for View (Format)</span></span>](./name-element-for-control-for-controls-for-view-format.md)

[<span data-ttu-id="4669a-138">Scrittura di un file di formattazione di PowerShell</span><span class="sxs-lookup"><span data-stu-id="4669a-138">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
