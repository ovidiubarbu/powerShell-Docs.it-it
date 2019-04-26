---
title: Elemento Control per i controlli per la configurazione (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: bddf7ffa-04d3-4354-90b9-5e714e096260
caps.latest.revision: 13
ms.openlocfilehash: 26fe417c9ca60dda22bdc23d9d339d40135a0c9b
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62066794"
---
# <a name="control-element-for-controls-for-configuration-format"></a><span data-ttu-id="18973-102">Elemento Control per Controls per Configuration (formato)</span><span class="sxs-lookup"><span data-stu-id="18973-102">Control Element for Controls for Configuration (Format)</span></span>

<span data-ttu-id="18973-103">Definisce un controllo comune che può essere usato da tutte le visualizzazioni del file di formattazione e il nome utilizzato per fare riferimento al controllo.</span><span class="sxs-lookup"><span data-stu-id="18973-103">Defines a common control that can be used by all the views of the formatting file and the name that is used to reference the control.</span></span>

<span data-ttu-id="18973-104">Configurazione (formato) i controlli elemento di configurazione (formato) elemento di controllo per i controlli per la configurazione (formato)</span><span class="sxs-lookup"><span data-stu-id="18973-104">Configuration Element (Format) Controls Element of Configuration (Format) Control Element for Controls for Configuration (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="18973-105">Sintassi</span><span class="sxs-lookup"><span data-stu-id="18973-105">Syntax</span></span>

```xml
<Control>
  <Name>NameOfControl</Name>
  <CustomControl>...</CustomControl>
</Control>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="18973-106">Elementi e attributi</span><span class="sxs-lookup"><span data-stu-id="18973-106">Attributes and Elements</span></span>

<span data-ttu-id="18973-107">Le sezioni seguenti descrivono gli attributi, elementi figlio e l'elemento padre per il `Control` elemento.</span><span class="sxs-lookup"><span data-stu-id="18973-107">The following sections describe the attributes, child elements, and the parent element for the `Control` element.</span></span> <span data-ttu-id="18973-108">È necessario specificare solo uno di ogni elemento figlio.</span><span class="sxs-lookup"><span data-stu-id="18973-108">You must specify only one of each child element.</span></span>

### <a name="attributes"></a><span data-ttu-id="18973-109">Attributes</span><span class="sxs-lookup"><span data-stu-id="18973-109">Attributes</span></span>

<span data-ttu-id="18973-110">Nessuna.</span><span class="sxs-lookup"><span data-stu-id="18973-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="18973-111">Elementi figlio</span><span class="sxs-lookup"><span data-stu-id="18973-111">Child Elements</span></span>

|<span data-ttu-id="18973-112">Elemento</span><span class="sxs-lookup"><span data-stu-id="18973-112">Element</span></span>|<span data-ttu-id="18973-113">Description</span><span class="sxs-lookup"><span data-stu-id="18973-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="18973-114">Elemento CustomControl per il controllo per i controlli per la configurazione (formato)</span><span class="sxs-lookup"><span data-stu-id="18973-114">CustomControl Element for Control for Controls for Configuration (Format)</span></span>](./customcontrol-element-for-control-for-controls-for-configuration-format.md)|<span data-ttu-id="18973-115">Elemento obbligatorio.</span><span class="sxs-lookup"><span data-stu-id="18973-115">Required element.</span></span><br /><br /> <span data-ttu-id="18973-116">Definisce il controllo.</span><span class="sxs-lookup"><span data-stu-id="18973-116">Defines the control.</span></span>|
|[<span data-ttu-id="18973-117">Elemento Name per il controllo per la configurazione (formato)</span><span class="sxs-lookup"><span data-stu-id="18973-117">Name Element for Control for Configuration (Format)</span></span>](./name-element-for-control-for-controls-for-configuration-format.md)|<span data-ttu-id="18973-118">Elemento obbligatorio.</span><span class="sxs-lookup"><span data-stu-id="18973-118">Required element.</span></span><br /><br /> <span data-ttu-id="18973-119">Specifica il nome usato per fare riferimento al controllo.</span><span class="sxs-lookup"><span data-stu-id="18973-119">Specifies the name used to reference the control.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="18973-120">Elementi padre</span><span class="sxs-lookup"><span data-stu-id="18973-120">Parent Elements</span></span>

|<span data-ttu-id="18973-121">Elemento</span><span class="sxs-lookup"><span data-stu-id="18973-121">Element</span></span>|<span data-ttu-id="18973-122">Description</span><span class="sxs-lookup"><span data-stu-id="18973-122">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="18973-123">I controlli elemento di configurazione (formato)</span><span class="sxs-lookup"><span data-stu-id="18973-123">Controls Element of Configuration (Format)</span></span>](./controls-element-for-configuration-format.md)|<span data-ttu-id="18973-124">Definisce i controlli comuni che possono essere utilizzati da tutte le visualizzazioni del file di formattazione o da altri controlli.</span><span class="sxs-lookup"><span data-stu-id="18973-124">Defines the common controls that can be used by all views of the formatting file or by other controls.</span></span>|

## <a name="remarks"></a><span data-ttu-id="18973-125">Osservazioni</span><span class="sxs-lookup"><span data-stu-id="18973-125">Remarks</span></span>

<span data-ttu-id="18973-126">Il nome assegnato a questo controllo può farvi riferimento negli elementi seguenti:</span><span class="sxs-lookup"><span data-stu-id="18973-126">The name given to this control can be referenced in the following elements:</span></span>

- [<span data-ttu-id="18973-127">Elemento ExpressionBinding per CustomItem (formato)</span><span class="sxs-lookup"><span data-stu-id="18973-127">ExpressionBinding Element for CustomItem (Format)</span></span>](./expressionbinding-element-for-customitem-for-controls-for-configuration-format.md)

- [<span data-ttu-id="18973-128">Elemento GroupBy per View(Format)</span><span class="sxs-lookup"><span data-stu-id="18973-128">GroupBy Element for View(Format)</span></span>](./groupby-element-for-view-format.md)

## <a name="see-also"></a><span data-ttu-id="18973-129">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="18973-129">See Also</span></span>

[<span data-ttu-id="18973-130">I controlli elemento di configurazione (formato)</span><span class="sxs-lookup"><span data-stu-id="18973-130">Controls Element of Configuration (Format)</span></span>](./controls-element-for-configuration-format.md)

[<span data-ttu-id="18973-131">Elemento CustomControl per il controllo per la configurazione (formato)</span><span class="sxs-lookup"><span data-stu-id="18973-131">CustomControl element for Control for Configuration (Format)</span></span>](./customcontrol-element-for-control-for-controls-for-configuration-format.md)

[<span data-ttu-id="18973-132">Elemento ExpressionBinding per CustomItem (formato)</span><span class="sxs-lookup"><span data-stu-id="18973-132">ExpressionBinding Element for CustomItem (Format)</span></span>](./expressionbinding-element-for-customitem-for-controls-for-configuration-format.md)

[<span data-ttu-id="18973-133">Elemento GroupBy per View(Format)</span><span class="sxs-lookup"><span data-stu-id="18973-133">GroupBy Element for View(Format)</span></span>](./groupby-element-for-view-format.md)

[<span data-ttu-id="18973-134">Elemento Name per il controllo per i controlli per la configurazione (formato)</span><span class="sxs-lookup"><span data-stu-id="18973-134">Name Element for Control for Controls for Configuration (Format)</span></span>](./name-element-for-control-for-controls-for-configuration-format.md)

[<span data-ttu-id="18973-135">La scrittura di un File di formattazione di PowerShell</span><span class="sxs-lookup"><span data-stu-id="18973-135">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
