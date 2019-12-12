---
title: Elemento Control per Controls per Configuration (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: bddf7ffa-04d3-4354-90b9-5e714e096260
caps.latest.revision: 13
ms.openlocfilehash: 26fe417c9ca60dda22bdc23d9d339d40135a0c9b
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/05/2019
ms.locfileid: "72369010"
---
# <a name="control-element-for-controls-for-configuration-format"></a><span data-ttu-id="e651f-102">Elemento Control per Controls per Configuration (formato)</span><span class="sxs-lookup"><span data-stu-id="e651f-102">Control Element for Controls for Configuration (Format)</span></span>

<span data-ttu-id="e651f-103">Definisce un controllo comune che può essere utilizzato da tutte le visualizzazioni del file di formattazione e dal nome utilizzato per fare riferimento al controllo.</span><span class="sxs-lookup"><span data-stu-id="e651f-103">Defines a common control that can be used by all the views of the formatting file and the name that is used to reference the control.</span></span>

<span data-ttu-id="e651f-104">Elemento di configurazione (Format) controlla l'elemento dell'elemento di controllo Configuration (Format) per i controlli per la configurazione (Format)</span><span class="sxs-lookup"><span data-stu-id="e651f-104">Configuration Element (Format) Controls Element of Configuration (Format) Control Element for Controls for Configuration (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="e651f-105">Sintassi</span><span class="sxs-lookup"><span data-stu-id="e651f-105">Syntax</span></span>

```xml
<Control>
  <Name>NameOfControl</Name>
  <CustomControl>...</CustomControl>
</Control>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="e651f-106">Attributi ed elementi</span><span class="sxs-lookup"><span data-stu-id="e651f-106">Attributes and Elements</span></span>

<span data-ttu-id="e651f-107">Nelle sezioni seguenti vengono descritti gli attributi, gli elementi figlio e l'elemento padre per l'elemento `Control`.</span><span class="sxs-lookup"><span data-stu-id="e651f-107">The following sections describe the attributes, child elements, and the parent element for the `Control` element.</span></span> <span data-ttu-id="e651f-108">È necessario specificare un solo elemento figlio.</span><span class="sxs-lookup"><span data-stu-id="e651f-108">You must specify only one of each child element.</span></span>

### <a name="attributes"></a><span data-ttu-id="e651f-109">Attributi</span><span class="sxs-lookup"><span data-stu-id="e651f-109">Attributes</span></span>

<span data-ttu-id="e651f-110">Nessuna.</span><span class="sxs-lookup"><span data-stu-id="e651f-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="e651f-111">Elementi figlio</span><span class="sxs-lookup"><span data-stu-id="e651f-111">Child Elements</span></span>

|<span data-ttu-id="e651f-112">Elemento</span><span class="sxs-lookup"><span data-stu-id="e651f-112">Element</span></span>|<span data-ttu-id="e651f-113">Description</span><span class="sxs-lookup"><span data-stu-id="e651f-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="e651f-114">Elemento CustomControl per Control per Controls per Configuration (Format)</span><span class="sxs-lookup"><span data-stu-id="e651f-114">CustomControl Element for Control for Controls for Configuration (Format)</span></span>](./customcontrol-element-for-control-for-controls-for-configuration-format.md)|<span data-ttu-id="e651f-115">Elemento obbligatorio.</span><span class="sxs-lookup"><span data-stu-id="e651f-115">Required element.</span></span><br /><br /> <span data-ttu-id="e651f-116">Definisce il controllo.</span><span class="sxs-lookup"><span data-stu-id="e651f-116">Defines the control.</span></span>|
|[<span data-ttu-id="e651f-117">Elemento Name per Control per Configuration (Format)</span><span class="sxs-lookup"><span data-stu-id="e651f-117">Name Element for Control for Configuration (Format)</span></span>](./name-element-for-control-for-controls-for-configuration-format.md)|<span data-ttu-id="e651f-118">Elemento obbligatorio.</span><span class="sxs-lookup"><span data-stu-id="e651f-118">Required element.</span></span><br /><br /> <span data-ttu-id="e651f-119">Specifica il nome utilizzato per fare riferimento al controllo.</span><span class="sxs-lookup"><span data-stu-id="e651f-119">Specifies the name used to reference the control.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="e651f-120">Elementi padre</span><span class="sxs-lookup"><span data-stu-id="e651f-120">Parent Elements</span></span>

|<span data-ttu-id="e651f-121">Elemento</span><span class="sxs-lookup"><span data-stu-id="e651f-121">Element</span></span>|<span data-ttu-id="e651f-122">Description</span><span class="sxs-lookup"><span data-stu-id="e651f-122">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="e651f-123">Elemento Controls di Configuration (Format)</span><span class="sxs-lookup"><span data-stu-id="e651f-123">Controls Element of Configuration (Format)</span></span>](./controls-element-for-configuration-format.md)|<span data-ttu-id="e651f-124">Definisce i controlli comuni che possono essere utilizzati da tutte le visualizzazioni del file di formattazione o da altri controlli.</span><span class="sxs-lookup"><span data-stu-id="e651f-124">Defines the common controls that can be used by all views of the formatting file or by other controls.</span></span>|

## <a name="remarks"></a><span data-ttu-id="e651f-125">Osservazioni</span><span class="sxs-lookup"><span data-stu-id="e651f-125">Remarks</span></span>

<span data-ttu-id="e651f-126">È possibile fare riferimento al nome assegnato a questo controllo negli elementi seguenti:</span><span class="sxs-lookup"><span data-stu-id="e651f-126">The name given to this control can be referenced in the following elements:</span></span>

- [<span data-ttu-id="e651f-127">Elemento expressiongroup per CustomItem (Format)</span><span class="sxs-lookup"><span data-stu-id="e651f-127">ExpressionBinding Element for CustomItem (Format)</span></span>](./expressionbinding-element-for-customitem-for-controls-for-configuration-format.md)

- [<span data-ttu-id="e651f-128">Elemento GroupBy per View (Format)</span><span class="sxs-lookup"><span data-stu-id="e651f-128">GroupBy Element for View(Format)</span></span>](./groupby-element-for-view-format.md)

## <a name="see-also"></a><span data-ttu-id="e651f-129">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="e651f-129">See Also</span></span>

[<span data-ttu-id="e651f-130">Elemento Controls di Configuration (Format)</span><span class="sxs-lookup"><span data-stu-id="e651f-130">Controls Element of Configuration (Format)</span></span>](./controls-element-for-configuration-format.md)

[<span data-ttu-id="e651f-131">Elemento CustomControl per Control per Configuration (Format)</span><span class="sxs-lookup"><span data-stu-id="e651f-131">CustomControl element for Control for Configuration (Format)</span></span>](./customcontrol-element-for-control-for-controls-for-configuration-format.md)

[<span data-ttu-id="e651f-132">Elemento expressiongroup per CustomItem (Format)</span><span class="sxs-lookup"><span data-stu-id="e651f-132">ExpressionBinding Element for CustomItem (Format)</span></span>](./expressionbinding-element-for-customitem-for-controls-for-configuration-format.md)

[<span data-ttu-id="e651f-133">Elemento GroupBy per View (Format)</span><span class="sxs-lookup"><span data-stu-id="e651f-133">GroupBy Element for View(Format)</span></span>](./groupby-element-for-view-format.md)

[<span data-ttu-id="e651f-134">Elemento Name per il controllo per i controlli per la configurazione (Format)</span><span class="sxs-lookup"><span data-stu-id="e651f-134">Name Element for Control for Controls for Configuration (Format)</span></span>](./name-element-for-control-for-controls-for-configuration-format.md)

[<span data-ttu-id="e651f-135">Scrittura di un file di formattazione di PowerShell</span><span class="sxs-lookup"><span data-stu-id="e651f-135">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
