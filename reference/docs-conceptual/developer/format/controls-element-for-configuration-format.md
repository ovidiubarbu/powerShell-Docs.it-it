---
title: Elemento Controls per Configuration (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 4d4ef63d-5866-4319-ba00-7ed96de26821
caps.latest.revision: 18
ms.openlocfilehash: ac9f7ff08f6e87ef83b5a2fe23fc58ee2651566d
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/05/2019
ms.locfileid: "72369000"
---
# <a name="controls-element-for-configuration-format"></a><span data-ttu-id="e5f31-102">Elemento Controls per Configuration (formato)</span><span class="sxs-lookup"><span data-stu-id="e5f31-102">Controls Element for Configuration (Format)</span></span>

<span data-ttu-id="e5f31-103">Definisce i controlli comuni che possono essere utilizzati da tutte le visualizzazioni del file di formattazione.</span><span class="sxs-lookup"><span data-stu-id="e5f31-103">Defines the common controls that can be used by all views of the formatting file.</span></span>

<span data-ttu-id="e5f31-104">Elemento Configuration (Format) controlla l'elemento di configurazione (Format)</span><span class="sxs-lookup"><span data-stu-id="e5f31-104">Configuration Element (Format) Controls Element of Configuration (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="e5f31-105">Sintassi</span><span class="sxs-lookup"><span data-stu-id="e5f31-105">Syntax</span></span>

```xml
<Controls>
  <Control>...</Control>
</Controls>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="e5f31-106">Attributi ed elementi</span><span class="sxs-lookup"><span data-stu-id="e5f31-106">Attributes and Elements</span></span>

<span data-ttu-id="e5f31-107">Nelle sezioni seguenti vengono descritti gli attributi, gli elementi figlio e l'elemento padre dell'elemento `Controls`.</span><span class="sxs-lookup"><span data-stu-id="e5f31-107">The following sections describe the attributes, child elements, and the parent element of the `Controls` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="e5f31-108">Attributi</span><span class="sxs-lookup"><span data-stu-id="e5f31-108">Attributes</span></span>

<span data-ttu-id="e5f31-109">Nessuna.</span><span class="sxs-lookup"><span data-stu-id="e5f31-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="e5f31-110">Elementi figlio</span><span class="sxs-lookup"><span data-stu-id="e5f31-110">Child Elements</span></span>

|<span data-ttu-id="e5f31-111">Elemento</span><span class="sxs-lookup"><span data-stu-id="e5f31-111">Element</span></span>|<span data-ttu-id="e5f31-112">Description</span><span class="sxs-lookup"><span data-stu-id="e5f31-112">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="e5f31-113">Elemento Control per Controls per Configuration (Format)</span><span class="sxs-lookup"><span data-stu-id="e5f31-113">Control Element for Controls for Configuration (Format)</span></span>](./control-element-for-controls-for-configuration-format.md)|<span data-ttu-id="e5f31-114">Elemento obbligatorio.</span><span class="sxs-lookup"><span data-stu-id="e5f31-114">Required element.</span></span><br /><br /> <span data-ttu-id="e5f31-115">Definisce un controllo comune che può essere usato da tutte le visualizzazioni del file di formattazione.</span><span class="sxs-lookup"><span data-stu-id="e5f31-115">Defines a common control that can be used by all views of the formatting file.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="e5f31-116">Elementi padre</span><span class="sxs-lookup"><span data-stu-id="e5f31-116">Parent Elements</span></span>

|<span data-ttu-id="e5f31-117">Elemento</span><span class="sxs-lookup"><span data-stu-id="e5f31-117">Element</span></span>|<span data-ttu-id="e5f31-118">Description</span><span class="sxs-lookup"><span data-stu-id="e5f31-118">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="e5f31-119">Elemento Configuration (Format)</span><span class="sxs-lookup"><span data-stu-id="e5f31-119">Configuration Element (Format)</span></span>](./configuration-element-format.md)|<span data-ttu-id="e5f31-120">Rappresenta l'elemento di primo livello di un file di formattazione.</span><span class="sxs-lookup"><span data-stu-id="e5f31-120">Represents the top-level element of a formatting file.</span></span>|

## <a name="remarks"></a><span data-ttu-id="e5f31-121">Osservazioni</span><span class="sxs-lookup"><span data-stu-id="e5f31-121">Remarks</span></span>

<span data-ttu-id="e5f31-122">È possibile creare un numero qualsiasi di controlli comuni.</span><span class="sxs-lookup"><span data-stu-id="e5f31-122">You can create any number of common controls.</span></span> <span data-ttu-id="e5f31-123">Per ogni controllo è necessario specificare il nome usato per fare riferimento al controllo e ai componenti del controllo.</span><span class="sxs-lookup"><span data-stu-id="e5f31-123">For each control, you must specify the name that is used to reference the control and the components of the control.</span></span>

## <a name="see-also"></a><span data-ttu-id="e5f31-124">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="e5f31-124">See Also</span></span>

[<span data-ttu-id="e5f31-125">Elemento Configuration (Format)</span><span class="sxs-lookup"><span data-stu-id="e5f31-125">Configuration Element (Format)</span></span>](./configuration-element-format.md)

[<span data-ttu-id="e5f31-126">Elemento Control per Controls per Configuration (Format)</span><span class="sxs-lookup"><span data-stu-id="e5f31-126">Control Element for Controls for Configuration (Format)</span></span>](./control-element-for-controls-for-configuration-format.md)

[<span data-ttu-id="e5f31-127">Scrittura di un file di formattazione di PowerShell</span><span class="sxs-lookup"><span data-stu-id="e5f31-127">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
