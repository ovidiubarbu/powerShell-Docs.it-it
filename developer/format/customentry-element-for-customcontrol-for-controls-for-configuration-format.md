---
title: Elemento CustomEntry per CustomControl per i controlli per la configurazione (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 9dfba86f-29b2-473c-9e98-9d679176acce
caps.latest.revision: 11
ms.openlocfilehash: 497485a388d1cdc834ecc1d1079b0714a7d7f9db
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62066473"
---
# <a name="customentry-element-for-customcontrol-for-controls-for-configuration-format"></a><span data-ttu-id="c695c-102">Elemento CustomEntry per CustomControl per Controls per Configuration (formato)</span><span class="sxs-lookup"><span data-stu-id="c695c-102">CustomEntry Element for CustomControl for Controls for Configuration (Format)</span></span>

<span data-ttu-id="c695c-103">Fornisce una definizione del controllo comune.</span><span class="sxs-lookup"><span data-stu-id="c695c-103">Provides a definition of the common control.</span></span> <span data-ttu-id="c695c-104">Questo elemento viene usato quando si definisce un controllo comune che può essere usato da tutte le visualizzazioni nel file di formattazione.</span><span class="sxs-lookup"><span data-stu-id="c695c-104">This element is used when defining a common control that can be used by all the views in the formatting file.</span></span>

<span data-ttu-id="c695c-105">Configurazione (formato) i controlli elemento di configurazione (formato) elemento di controllo per i controlli di configurazione (formato) CustomControl elemento per il controllo per elemento di configurazione (formato) CustomEntries per CustomControl per Configuration ( Elemento CustomEntry Format) per CustomControl per i controlli per la configurazione (formato)</span><span class="sxs-lookup"><span data-stu-id="c695c-105">Configuration Element (Format) Controls Element of Configuration (Format) Control Element for Controls for Configuration (Format) CustomControl Element for Control for Configuration (Format) CustomEntries Element for CustomControl for Configuration (Format) CustomEntry Element for CustomControl for Controls for Configuration (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="c695c-106">Sintassi</span><span class="sxs-lookup"><span data-stu-id="c695c-106">Syntax</span></span>

```xml
<CustomEntry>
  <EntrySelectedBy>...</EntrySelectedBy>
  <CustomItem>...</CustomItem>
</CustomEntry>

```

## <a name="attributes-and-elements"></a><span data-ttu-id="c695c-107">Elementi e attributi</span><span class="sxs-lookup"><span data-stu-id="c695c-107">Attributes and Elements</span></span>

<span data-ttu-id="c695c-108">Le sezioni seguenti descrivono gli attributi e gli elementi figlio dell'elemento padre del `CustomEntry` elemento.</span><span class="sxs-lookup"><span data-stu-id="c695c-108">The following sections describe attributes, child elements, and the parent element of the `CustomEntry` element.</span></span> <span data-ttu-id="c695c-109">È necessario specificare gli elementi visualizzati dalla definizione.</span><span class="sxs-lookup"><span data-stu-id="c695c-109">You must specify the items displayed by the definition.</span></span>

### <a name="attributes"></a><span data-ttu-id="c695c-110">Attributes</span><span class="sxs-lookup"><span data-stu-id="c695c-110">Attributes</span></span>

<span data-ttu-id="c695c-111">Nessuna.</span><span class="sxs-lookup"><span data-stu-id="c695c-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="c695c-112">Elementi figlio</span><span class="sxs-lookup"><span data-stu-id="c695c-112">Child Elements</span></span>

|<span data-ttu-id="c695c-113">Elemento</span><span class="sxs-lookup"><span data-stu-id="c695c-113">Element</span></span>|<span data-ttu-id="c695c-114">Description</span><span class="sxs-lookup"><span data-stu-id="c695c-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="c695c-115">Elemento EntrySelectedBy per CustomEntry per i controlli per la configurazione (formato)</span><span class="sxs-lookup"><span data-stu-id="c695c-115">EntrySelectedBy Element for CustomEntry for Controls for Configuration (Format)</span></span>](./entryselectedby-element-for-customentry-for-controls-for-configuration-format.md)|<span data-ttu-id="c695c-116">Elemento facoltativo.</span><span class="sxs-lookup"><span data-stu-id="c695c-116">Optional element.</span></span><br /><br /> <span data-ttu-id="c695c-117">Definisce i tipi .NET che usano la definizione di controllo comune o la condizione che deve essere presente per questo controllo da utilizzare.</span><span class="sxs-lookup"><span data-stu-id="c695c-117">Defines the .NET types that use the definition of the common control or the condition that must exist for this control to be used.</span></span>|
|[<span data-ttu-id="c695c-118">Elemento CustomItem per CustomEntry per i controlli per la configurazione</span><span class="sxs-lookup"><span data-stu-id="c695c-118">CustomItem Element for CustomEntry for Controls for Configuration</span></span>](./customitem-element-for-customentry-for-controls-for-configuration-format.md)|<span data-ttu-id="c695c-119">Elemento obbligatorio.</span><span class="sxs-lookup"><span data-stu-id="c695c-119">Required element.</span></span><br /><br /> <span data-ttu-id="c695c-120">Definisce i dati che vengano visualizzati dal controllo e la modalità di visualizzazione.</span><span class="sxs-lookup"><span data-stu-id="c695c-120">Defines what data is displayed by the control and how it is displayed.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="c695c-121">Elementi padre</span><span class="sxs-lookup"><span data-stu-id="c695c-121">Parent Elements</span></span>

|<span data-ttu-id="c695c-122">Elemento</span><span class="sxs-lookup"><span data-stu-id="c695c-122">Element</span></span>|<span data-ttu-id="c695c-123">Description</span><span class="sxs-lookup"><span data-stu-id="c695c-123">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="c695c-124">Elemento CustomEntries per CustomControl per la configurazione (formato)</span><span class="sxs-lookup"><span data-stu-id="c695c-124">CustomEntries Element for CustomControl for Configuration (Format)</span></span>](./customentries-element-for-customcontrol-for-controls-for-configuration-format.md)|<span data-ttu-id="c695c-125">Fornisce le definizioni del controllo comune.</span><span class="sxs-lookup"><span data-stu-id="c695c-125">Provides the definitions of the common control.</span></span>|

## <a name="remarks"></a><span data-ttu-id="c695c-126">Osservazioni</span><span class="sxs-lookup"><span data-stu-id="c695c-126">Remarks</span></span>

<span data-ttu-id="c695c-127">Nella maggior parte dei casi, è necessaria per ogni controllo personalizzato comune una sola definizione, ma è possibile avere più definizioni, se si desidera utilizzare lo stesso controllo per visualizzare diversi oggetti .NET.</span><span class="sxs-lookup"><span data-stu-id="c695c-127">In most cases, only one definition is required for each common custom control, but it is possible to have multiple definitions if you want to use the same control to display different .NET objects.</span></span> <span data-ttu-id="c695c-128">In questi casi, è possibile fornire una definizione separata per ogni oggetto o un set di oggetti.</span><span class="sxs-lookup"><span data-stu-id="c695c-128">In those cases, you can provide a separate definition for each object or set of objects.</span></span>

## <a name="see-also"></a><span data-ttu-id="c695c-129">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="c695c-129">See Also</span></span>

[<span data-ttu-id="c695c-130">Elemento CustomEntries per CustomControl per la configurazione (formato)</span><span class="sxs-lookup"><span data-stu-id="c695c-130">CustomEntries Element for CustomControl for Configuration (Format)</span></span>](./customentries-element-for-customcontrol-for-controls-for-configuration-format.md)

[<span data-ttu-id="c695c-131">Elemento CustomItem per CustomEntry per i controlli per la configurazione</span><span class="sxs-lookup"><span data-stu-id="c695c-131">CustomItem Element for CustomEntry for Controls for Configuration</span></span>](./customitem-element-for-customentry-for-controls-for-configuration-format.md)

[<span data-ttu-id="c695c-132">La scrittura di un File di formattazione di PowerShell</span><span class="sxs-lookup"><span data-stu-id="c695c-132">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
