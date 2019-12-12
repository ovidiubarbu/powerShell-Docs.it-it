---
title: Elemento CustomEntries per CustomControl per i controlli per la configurazione (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 80fc4de2-208f-4506-9a6a-c2675bb83be4
caps.latest.revision: 11
ms.openlocfilehash: abef6c91500f665c2366f221496d4cfd6444f5c9
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/05/2019
ms.locfileid: "72368820"
---
# <a name="customentries-element-for-customcontrol-for-controls-for-configuration-format"></a><span data-ttu-id="56a6e-102">Elemento CustomEntries per CustomControl per Controls per Configuration (formato)</span><span class="sxs-lookup"><span data-stu-id="56a6e-102">CustomEntries Element for CustomControl for Controls for Configuration (Format)</span></span>

<span data-ttu-id="56a6e-103">Fornisce le definizioni di un controllo comune.</span><span class="sxs-lookup"><span data-stu-id="56a6e-103">Provides the definitions of a common control.</span></span> <span data-ttu-id="56a6e-104">Questo elemento viene usato quando si definisce un controllo comune che può essere usato da tutte le visualizzazioni nel file di formattazione.</span><span class="sxs-lookup"><span data-stu-id="56a6e-104">This element is used when defining a common control that can be used by all the views in the formatting file.</span></span>

<span data-ttu-id="56a6e-105">Elemento di configurazione (Format) controlla l'elemento dell'elemento di controllo Configuration (Format) per i controlli per la configurazione (Format) elemento CustomControl per il controllo per la configurazione (Format) elemento CustomEntries per CustomControl per la configurazione ( Formato</span><span class="sxs-lookup"><span data-stu-id="56a6e-105">Configuration Element (Format) Controls Element of Configuration (Format) Control Element for Controls for Configuration (Format) CustomControl Element for Control for Configuration (Format) CustomEntries Element for CustomControl for Configuration (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="56a6e-106">Sintassi</span><span class="sxs-lookup"><span data-stu-id="56a6e-106">Syntax</span></span>

```xml
<CustomEntries>
  <CustomEntry>...</CustomEntry>
</CustomEntries>

```

## <a name="attributes-and-elements"></a><span data-ttu-id="56a6e-107">Attributi ed elementi</span><span class="sxs-lookup"><span data-stu-id="56a6e-107">Attributes and Elements</span></span>

<span data-ttu-id="56a6e-108">Nelle sezioni seguenti vengono descritti gli attributi, gli elementi figlio e l'elemento padre dell'elemento `CustomEntries`.</span><span class="sxs-lookup"><span data-stu-id="56a6e-108">The following sections describe attributes, child elements, and the parent element of the `CustomEntries` element.</span></span> <span data-ttu-id="56a6e-109">È necessario specificare uno o più elementi figlio.</span><span class="sxs-lookup"><span data-stu-id="56a6e-109">You must specify one or more child elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="56a6e-110">Attributi</span><span class="sxs-lookup"><span data-stu-id="56a6e-110">Attributes</span></span>

<span data-ttu-id="56a6e-111">Nessuna.</span><span class="sxs-lookup"><span data-stu-id="56a6e-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="56a6e-112">Elementi figlio</span><span class="sxs-lookup"><span data-stu-id="56a6e-112">Child Elements</span></span>

|<span data-ttu-id="56a6e-113">Elemento</span><span class="sxs-lookup"><span data-stu-id="56a6e-113">Element</span></span>|<span data-ttu-id="56a6e-114">Description</span><span class="sxs-lookup"><span data-stu-id="56a6e-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="56a6e-115">Elemento CustomEntry per CustomControl per i controlli per la configurazione (Format)</span><span class="sxs-lookup"><span data-stu-id="56a6e-115">CustomEntry Element for CustomControl for Controls for Configuration (Format)</span></span>](./customentry-element-for-customcontrol-for-controls-for-configuration-format.md)|<span data-ttu-id="56a6e-116">Fornisce una definizione del controllo comune.</span><span class="sxs-lookup"><span data-stu-id="56a6e-116">Provides a definition of the common control.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="56a6e-117">Elementi padre</span><span class="sxs-lookup"><span data-stu-id="56a6e-117">Parent Elements</span></span>

|<span data-ttu-id="56a6e-118">Elemento</span><span class="sxs-lookup"><span data-stu-id="56a6e-118">Element</span></span>|<span data-ttu-id="56a6e-119">Description</span><span class="sxs-lookup"><span data-stu-id="56a6e-119">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="56a6e-120">Elemento CustomControl per Control per Configuration (Format)</span><span class="sxs-lookup"><span data-stu-id="56a6e-120">CustomControl Element for Control for Configuration (Format)</span></span>](./customcontrol-element-for-control-for-controls-for-configuration-format.md)|<span data-ttu-id="56a6e-121">Definisce un controllo comune.</span><span class="sxs-lookup"><span data-stu-id="56a6e-121">Defines a common control.</span></span>|

## <a name="remarks"></a><span data-ttu-id="56a6e-122">Osservazioni</span><span class="sxs-lookup"><span data-stu-id="56a6e-122">Remarks</span></span>

<span data-ttu-id="56a6e-123">Nella maggior parte dei casi, un controllo ha una sola definizione, definita in un singolo elemento `CustomEntry`.</span><span class="sxs-lookup"><span data-stu-id="56a6e-123">In most cases, a control has only one definition, which is defined in a single `CustomEntry` element.</span></span> <span data-ttu-id="56a6e-124">Tuttavia, se si desidera utilizzare lo stesso controllo per visualizzare oggetti .NET diversi, è possibile disporre di più definizioni.</span><span class="sxs-lookup"><span data-stu-id="56a6e-124">However it is possible to have multiple definitions if you want to use the same control to display different .NET objects.</span></span> <span data-ttu-id="56a6e-125">In questi casi, è possibile definire un elemento `CustomEntry` per ogni oggetto o set di oggetti.</span><span class="sxs-lookup"><span data-stu-id="56a6e-125">In those cases, you can define a `CustomEntry` element for each object or set of objects.</span></span>

## <a name="see-also"></a><span data-ttu-id="56a6e-126">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="56a6e-126">See Also</span></span>

[<span data-ttu-id="56a6e-127">Elemento CustomControl per Control per Configuration (Format)</span><span class="sxs-lookup"><span data-stu-id="56a6e-127">CustomControl Element for Control for Configuration (Format)</span></span>](./customcontrol-element-for-control-for-controls-for-configuration-format.md)

[<span data-ttu-id="56a6e-128">Elemento CustomEntry per CustomControl per i controlli per la configurazione (Format)</span><span class="sxs-lookup"><span data-stu-id="56a6e-128">CustomEntry Element for CustomControl for Controls for Configuration (Format)</span></span>](./customentry-element-for-customcontrol-for-controls-for-configuration-format.md)

[<span data-ttu-id="56a6e-129">Scrittura di un file di formattazione di PowerShell</span><span class="sxs-lookup"><span data-stu-id="56a6e-129">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
