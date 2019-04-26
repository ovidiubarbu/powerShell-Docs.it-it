---
title: Elemento CustomEntries per CustomControl per i controlli per la configurazione (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 80fc4de2-208f-4506-9a6a-c2675bb83be4
caps.latest.revision: 11
ms.openlocfilehash: abef6c91500f665c2366f221496d4cfd6444f5c9
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62066601"
---
# <a name="customentries-element-for-customcontrol-for-controls-for-configuration-format"></a><span data-ttu-id="10505-102">Elemento CustomEntries per CustomControl per Controls per Configuration (formato)</span><span class="sxs-lookup"><span data-stu-id="10505-102">CustomEntries Element for CustomControl for Controls for Configuration (Format)</span></span>

<span data-ttu-id="10505-103">Fornisce le definizioni di un controllo comune.</span><span class="sxs-lookup"><span data-stu-id="10505-103">Provides the definitions of a common control.</span></span> <span data-ttu-id="10505-104">Questo elemento viene usato quando si definisce un controllo comune che può essere usato da tutte le visualizzazioni nel file di formattazione.</span><span class="sxs-lookup"><span data-stu-id="10505-104">This element is used when defining a common control that can be used by all the views in the formatting file.</span></span>

<span data-ttu-id="10505-105">Configurazione (formato) i controlli elemento di configurazione (formato) elemento di controllo per i controlli di configurazione (formato) CustomControl elemento per il controllo per elemento di configurazione (formato) CustomEntries per CustomControl per Configuration ( Formato)</span><span class="sxs-lookup"><span data-stu-id="10505-105">Configuration Element (Format) Controls Element of Configuration (Format) Control Element for Controls for Configuration (Format) CustomControl Element for Control for Configuration (Format) CustomEntries Element for CustomControl for Configuration (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="10505-106">Sintassi</span><span class="sxs-lookup"><span data-stu-id="10505-106">Syntax</span></span>

```xml
<CustomEntries>
  <CustomEntry>...</CustomEntry>
</CustomEntries>

```

## <a name="attributes-and-elements"></a><span data-ttu-id="10505-107">Elementi e attributi</span><span class="sxs-lookup"><span data-stu-id="10505-107">Attributes and Elements</span></span>

<span data-ttu-id="10505-108">Le sezioni seguenti descrivono gli attributi e gli elementi figlio dell'elemento padre del `CustomEntries` elemento.</span><span class="sxs-lookup"><span data-stu-id="10505-108">The following sections describe attributes, child elements, and the parent element of the `CustomEntries` element.</span></span> <span data-ttu-id="10505-109">È necessario specificare uno o più elementi figlio.</span><span class="sxs-lookup"><span data-stu-id="10505-109">You must specify one or more child elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="10505-110">Attributes</span><span class="sxs-lookup"><span data-stu-id="10505-110">Attributes</span></span>

<span data-ttu-id="10505-111">Nessuna.</span><span class="sxs-lookup"><span data-stu-id="10505-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="10505-112">Elementi figlio</span><span class="sxs-lookup"><span data-stu-id="10505-112">Child Elements</span></span>

|<span data-ttu-id="10505-113">Elemento</span><span class="sxs-lookup"><span data-stu-id="10505-113">Element</span></span>|<span data-ttu-id="10505-114">Description</span><span class="sxs-lookup"><span data-stu-id="10505-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="10505-115">Elemento CustomEntry per CustomControl per i controlli per la configurazione (formato)</span><span class="sxs-lookup"><span data-stu-id="10505-115">CustomEntry Element for CustomControl for Controls for Configuration (Format)</span></span>](./customentry-element-for-customcontrol-for-controls-for-configuration-format.md)|<span data-ttu-id="10505-116">Fornisce una definizione del controllo comune.</span><span class="sxs-lookup"><span data-stu-id="10505-116">Provides a definition of the common control.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="10505-117">Elementi padre</span><span class="sxs-lookup"><span data-stu-id="10505-117">Parent Elements</span></span>

|<span data-ttu-id="10505-118">Elemento</span><span class="sxs-lookup"><span data-stu-id="10505-118">Element</span></span>|<span data-ttu-id="10505-119">Description</span><span class="sxs-lookup"><span data-stu-id="10505-119">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="10505-120">Elemento CustomControl per il controllo per la configurazione (formato)</span><span class="sxs-lookup"><span data-stu-id="10505-120">CustomControl Element for Control for Configuration (Format)</span></span>](./customcontrol-element-for-control-for-controls-for-configuration-format.md)|<span data-ttu-id="10505-121">Definisce un controllo comune.</span><span class="sxs-lookup"><span data-stu-id="10505-121">Defines a common control.</span></span>|

## <a name="remarks"></a><span data-ttu-id="10505-122">Osservazioni</span><span class="sxs-lookup"><span data-stu-id="10505-122">Remarks</span></span>

<span data-ttu-id="10505-123">Nella maggior parte dei casi, un controllo ha una sola definizione, di cui è definita in una singola `CustomEntry` elemento.</span><span class="sxs-lookup"><span data-stu-id="10505-123">In most cases, a control has only one definition, which is defined in a single `CustomEntry` element.</span></span> <span data-ttu-id="10505-124">Tuttavia è possibile avere più definizioni, se si desidera utilizzare lo stesso controllo per visualizzare diversi oggetti .NET.</span><span class="sxs-lookup"><span data-stu-id="10505-124">However it is possible to have multiple definitions if you want to use the same control to display different .NET objects.</span></span> <span data-ttu-id="10505-125">In questi casi, è possibile definire un `CustomEntry` (elemento) per ogni oggetto o un set di oggetti.</span><span class="sxs-lookup"><span data-stu-id="10505-125">In those cases, you can define a `CustomEntry` element for each object or set of objects.</span></span>

## <a name="see-also"></a><span data-ttu-id="10505-126">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="10505-126">See Also</span></span>

[<span data-ttu-id="10505-127">Elemento CustomControl per il controllo per la configurazione (formato)</span><span class="sxs-lookup"><span data-stu-id="10505-127">CustomControl Element for Control for Configuration (Format)</span></span>](./customcontrol-element-for-control-for-controls-for-configuration-format.md)

[<span data-ttu-id="10505-128">Elemento CustomEntry per CustomControl per i controlli per la configurazione (formato)</span><span class="sxs-lookup"><span data-stu-id="10505-128">CustomEntry Element for CustomControl for Controls for Configuration (Format)</span></span>](./customentry-element-for-customcontrol-for-controls-for-configuration-format.md)

[<span data-ttu-id="10505-129">La scrittura di un File di formattazione di PowerShell</span><span class="sxs-lookup"><span data-stu-id="10505-129">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
