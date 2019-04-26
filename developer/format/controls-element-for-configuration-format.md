---
title: Controlla l'elemento di configurazione (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 4d4ef63d-5866-4319-ba00-7ed96de26821
caps.latest.revision: 18
ms.openlocfilehash: ac9f7ff08f6e87ef83b5a2fe23fc58ee2651566d
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62066873"
---
# <a name="controls-element-for-configuration-format"></a><span data-ttu-id="68d6d-102">Elemento Controls per Configuration (formato)</span><span class="sxs-lookup"><span data-stu-id="68d6d-102">Controls Element for Configuration (Format)</span></span>

<span data-ttu-id="68d6d-103">Definisce i controlli comuni che possono essere usati da tutte le visualizzazioni del file di formattazione.</span><span class="sxs-lookup"><span data-stu-id="68d6d-103">Defines the common controls that can be used by all views of the formatting file.</span></span>

<span data-ttu-id="68d6d-104">Configurazione (formato) i controlli elemento di configurazione (formato)</span><span class="sxs-lookup"><span data-stu-id="68d6d-104">Configuration Element (Format) Controls Element of Configuration (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="68d6d-105">Sintassi</span><span class="sxs-lookup"><span data-stu-id="68d6d-105">Syntax</span></span>

```xml
<Controls>
  <Control>...</Control>
</Controls>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="68d6d-106">Elementi e attributi</span><span class="sxs-lookup"><span data-stu-id="68d6d-106">Attributes and Elements</span></span>

<span data-ttu-id="68d6d-107">Le sezioni seguenti descrivono gli attributi e gli elementi figlio dell'elemento padre del `Controls` elemento.</span><span class="sxs-lookup"><span data-stu-id="68d6d-107">The following sections describe the attributes, child elements, and the parent element of the `Controls` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="68d6d-108">Attributes</span><span class="sxs-lookup"><span data-stu-id="68d6d-108">Attributes</span></span>

<span data-ttu-id="68d6d-109">Nessuna.</span><span class="sxs-lookup"><span data-stu-id="68d6d-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="68d6d-110">Elementi figlio</span><span class="sxs-lookup"><span data-stu-id="68d6d-110">Child Elements</span></span>

|<span data-ttu-id="68d6d-111">Elemento</span><span class="sxs-lookup"><span data-stu-id="68d6d-111">Element</span></span>|<span data-ttu-id="68d6d-112">Description</span><span class="sxs-lookup"><span data-stu-id="68d6d-112">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="68d6d-113">Elemento di controllo per i controlli per la configurazione (formato)</span><span class="sxs-lookup"><span data-stu-id="68d6d-113">Control Element for Controls for Configuration (Format)</span></span>](./control-element-for-controls-for-configuration-format.md)|<span data-ttu-id="68d6d-114">Elemento obbligatorio.</span><span class="sxs-lookup"><span data-stu-id="68d6d-114">Required element.</span></span><br /><br /> <span data-ttu-id="68d6d-115">Definisce un controllo comune che può essere usato da tutte le visualizzazioni del file di formattazione.</span><span class="sxs-lookup"><span data-stu-id="68d6d-115">Defines a common control that can be used by all views of the formatting file.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="68d6d-116">Elementi padre</span><span class="sxs-lookup"><span data-stu-id="68d6d-116">Parent Elements</span></span>

|<span data-ttu-id="68d6d-117">Elemento</span><span class="sxs-lookup"><span data-stu-id="68d6d-117">Element</span></span>|<span data-ttu-id="68d6d-118">Description</span><span class="sxs-lookup"><span data-stu-id="68d6d-118">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="68d6d-119">Elemento di configurazione (formato)</span><span class="sxs-lookup"><span data-stu-id="68d6d-119">Configuration Element (Format)</span></span>](./configuration-element-format.md)|<span data-ttu-id="68d6d-120">Rappresenta l'elemento di livello superiore di un file di formattazione.</span><span class="sxs-lookup"><span data-stu-id="68d6d-120">Represents the top-level element of a formatting file.</span></span>|

## <a name="remarks"></a><span data-ttu-id="68d6d-121">Osservazioni</span><span class="sxs-lookup"><span data-stu-id="68d6d-121">Remarks</span></span>

<span data-ttu-id="68d6d-122">È possibile creare qualsiasi numero di controlli comuni.</span><span class="sxs-lookup"><span data-stu-id="68d6d-122">You can create any number of common controls.</span></span> <span data-ttu-id="68d6d-123">Per ogni controllo, è necessario specificare il nome utilizzato per fare riferimento al controllo e i componenti del controllo.</span><span class="sxs-lookup"><span data-stu-id="68d6d-123">For each control, you must specify the name that is used to reference the control and the components of the control.</span></span>

## <a name="see-also"></a><span data-ttu-id="68d6d-124">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="68d6d-124">See Also</span></span>

[<span data-ttu-id="68d6d-125">Elemento di configurazione (formato)</span><span class="sxs-lookup"><span data-stu-id="68d6d-125">Configuration Element (Format)</span></span>](./configuration-element-format.md)

[<span data-ttu-id="68d6d-126">Elemento di controllo per i controlli per la configurazione (formato)</span><span class="sxs-lookup"><span data-stu-id="68d6d-126">Control Element for Controls for Configuration (Format)</span></span>](./control-element-for-controls-for-configuration-format.md)

[<span data-ttu-id="68d6d-127">La scrittura di un File di formattazione di PowerShell</span><span class="sxs-lookup"><span data-stu-id="68d6d-127">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
