---
title: Elemento EntrySelectedBy per CustomEntry per i controlli per la configurazione (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 30abae8f-c7f7-479d-ad85-19e07ddef204
caps.latest.revision: 10
ms.openlocfilehash: 81eca4f66f0057074612f2d60482b45adc36357b
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62066295"
---
# <a name="entryselectedby-element-for-customentry-for-controls-for-configuration-format"></a><span data-ttu-id="b2102-102">Elemento EntrySelectedBy per CustomEntry per Controls per Configuration (formato)</span><span class="sxs-lookup"><span data-stu-id="b2102-102">EntrySelectedBy Element for CustomEntry for Controls for Configuration (Format)</span></span>

<span data-ttu-id="b2102-103">Definisce i tipi .NET che usano la definizione di controllo comune o la condizione che deve essere presente per questo controllo da utilizzare.</span><span class="sxs-lookup"><span data-stu-id="b2102-103">Defines the .NET types that use the definition of the common control or the condition that must exist for this control to be used.</span></span> <span data-ttu-id="b2102-104">Questo elemento viene usato quando si definisce un controllo comune che può essere usato da tutte le visualizzazioni nel file di formattazione.</span><span class="sxs-lookup"><span data-stu-id="b2102-104">This element is used when defining a common control that can be used by all the views in the formatting file.</span></span>

<span data-ttu-id="b2102-105">Configurazione (formato) i controlli elemento di configurazione (formato) elemento di controllo per i controlli di configurazione (formato) CustomControl elemento per il controllo per elemento di configurazione (formato) CustomEntries per CustomControl per Configuration ( Elemento CustomEntry Format) per CustomControl per i controlli per elemento di configurazione (formato) EntrySelectedBy per CustomEntry per i controlli per la configurazione (formato)</span><span class="sxs-lookup"><span data-stu-id="b2102-105">Configuration Element (Format) Controls Element of Configuration (Format) Control Element for Controls for Configuration (Format) CustomControl Element for Control for Configuration (Format) CustomEntries Element for CustomControl for Configuration (Format) CustomEntry Element for CustomControl for Controls for Configuration (Format) EntrySelectedBy Element for CustomEntry for Controls for Configuration (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="b2102-106">Sintassi</span><span class="sxs-lookup"><span data-stu-id="b2102-106">Syntax</span></span>

```xml
<EntrySelectedBy>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>SelectionSet</SelectionSetName>
  <SelectionCondition>...</SelectionCondition>
</EntrySelectedBy>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="b2102-107">Elementi e attributi</span><span class="sxs-lookup"><span data-stu-id="b2102-107">Attributes and Elements</span></span>

<span data-ttu-id="b2102-108">Le sezioni seguenti descrivono gli attributi e gli elementi figlio dell'elemento padre del `EntrySelectedBy` elemento.</span><span class="sxs-lookup"><span data-stu-id="b2102-108">The following sections describe attributes, child elements, and the parent element of the `EntrySelectedBy` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="b2102-109">Attributes</span><span class="sxs-lookup"><span data-stu-id="b2102-109">Attributes</span></span>

<span data-ttu-id="b2102-110">Nessuna.</span><span class="sxs-lookup"><span data-stu-id="b2102-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="b2102-111">Elementi figlio</span><span class="sxs-lookup"><span data-stu-id="b2102-111">Child Elements</span></span>

|<span data-ttu-id="b2102-112">Elemento</span><span class="sxs-lookup"><span data-stu-id="b2102-112">Element</span></span>|<span data-ttu-id="b2102-113">Description</span><span class="sxs-lookup"><span data-stu-id="b2102-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="b2102-114">Elemento SelectionCondition per EntrySelectedBy per i controlli per la configurazione (formato)</span><span class="sxs-lookup"><span data-stu-id="b2102-114">SelectionCondition Element for EntrySelectedBy for Controls for Configuration (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-controls-for-configuration-format.md)|<span data-ttu-id="b2102-115">Elemento facoltativo.</span><span class="sxs-lookup"><span data-stu-id="b2102-115">Optional element.</span></span><br /><br /> <span data-ttu-id="b2102-116">Definisce la condizione che deve essere presente per la definizione di controllo comuni da usare.</span><span class="sxs-lookup"><span data-stu-id="b2102-116">Defines the condition that must exist for the common control definition to be used.</span></span>|
|[<span data-ttu-id="b2102-117">Elemento SelectionSetName per EntrySelectedBy per i controlli per la configurazione (formato)</span><span class="sxs-lookup"><span data-stu-id="b2102-117">SelectionSetName Element for EntrySelectedBy for Controls for Configuration (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-controls-for-configuration-format.md)|<span data-ttu-id="b2102-118">Elemento facoltativo.</span><span class="sxs-lookup"><span data-stu-id="b2102-118">Optional element.</span></span><br /><br /> <span data-ttu-id="b2102-119">Specifica un set di tipi .NET che usano questa definizione del controllo comune.</span><span class="sxs-lookup"><span data-stu-id="b2102-119">Specifies a set of .NET types that use this definition of the common control.</span></span>|
|[<span data-ttu-id="b2102-120">Elemento TypeName per EntrySelectedBy per i controlli per la configurazione (formato)</span><span class="sxs-lookup"><span data-stu-id="b2102-120">TypeName Element for EntrySelectedBy for Controls for Configuration (Format)</span></span>](./typename-element-for-entryselectedby-for-controls-for-configuration-format.md)|<span data-ttu-id="b2102-121">Elemento facoltativo.</span><span class="sxs-lookup"><span data-stu-id="b2102-121">Optional element.</span></span><br /><br /> <span data-ttu-id="b2102-122">Specifica un tipo .NET che usa questa definizione del controllo comune.</span><span class="sxs-lookup"><span data-stu-id="b2102-122">Specifies a .NET type that uses this definition of the common control.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="b2102-123">Elementi padre</span><span class="sxs-lookup"><span data-stu-id="b2102-123">Parent Elements</span></span>

|<span data-ttu-id="b2102-124">Elemento</span><span class="sxs-lookup"><span data-stu-id="b2102-124">Element</span></span>|<span data-ttu-id="b2102-125">Description</span><span class="sxs-lookup"><span data-stu-id="b2102-125">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="b2102-126">Elemento CustomEntry per CustomControl per i controlli per la configurazione (formato)</span><span class="sxs-lookup"><span data-stu-id="b2102-126">CustomEntry Element for CustomControl for Controls for Configuration (Format)</span></span>](./customentry-element-for-customcontrol-for-controls-for-configuration-format.md)|<span data-ttu-id="b2102-127">Fornisce una definizione del controllo comune.</span><span class="sxs-lookup"><span data-stu-id="b2102-127">Provides a definition of the common control.</span></span>|

## <a name="remarks"></a><span data-ttu-id="b2102-128">Osservazioni</span><span class="sxs-lookup"><span data-stu-id="b2102-128">Remarks</span></span>

<span data-ttu-id="b2102-129">Come minimo, ogni definizione deve avere almeno un tipo, set di selezione o condizione di selezione specificata .NET.</span><span class="sxs-lookup"><span data-stu-id="b2102-129">At a minimum, each definition must have at least one .NET type, selection set, or selection condition specified.</span></span> <span data-ttu-id="b2102-130">Non è definito alcun limite massimo al numero di tipi, set di selezione o condizioni di selezione che è possibile specificare.</span><span class="sxs-lookup"><span data-stu-id="b2102-130">There is no maximum limit to the number of types, selection sets, or selection conditions that you can specify.</span></span>

## <a name="see-also"></a><span data-ttu-id="b2102-131">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="b2102-131">See Also</span></span>

[<span data-ttu-id="b2102-132">Elemento SelectionCondition per EntrySelectedBy per i controlli per la configurazione (formato)</span><span class="sxs-lookup"><span data-stu-id="b2102-132">SelectionCondition Element for EntrySelectedBy for Controls for Configuration (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-controls-for-configuration-format.md)

[<span data-ttu-id="b2102-133">Elemento SelectionSetName per EntrySelectedBy per i controlli per la configurazione (formato)</span><span class="sxs-lookup"><span data-stu-id="b2102-133">SelectionSetName Element for EntrySelectedBy for Controls for Configuration (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-controls-for-configuration-format.md)

[<span data-ttu-id="b2102-134">Elemento CustomEntry per CustomControl per i controlli per la configurazione (formato)</span><span class="sxs-lookup"><span data-stu-id="b2102-134">CustomEntry Element for CustomControl for Controls for Configuration (Format)</span></span>](./customentry-element-for-customcontrol-for-controls-for-configuration-format.md)

[<span data-ttu-id="b2102-135">Elemento TypeName per EntrySelectedBy per i controlli per la configurazione (formato)</span><span class="sxs-lookup"><span data-stu-id="b2102-135">TypeName Element for EntrySelectedBy for Controls for Configuration (Format)</span></span>](./typename-element-for-selectioncondition-for-controls-for-configuration-format.md)

[<span data-ttu-id="b2102-136">La scrittura di un File di formattazione di PowerShell</span><span class="sxs-lookup"><span data-stu-id="b2102-136">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
