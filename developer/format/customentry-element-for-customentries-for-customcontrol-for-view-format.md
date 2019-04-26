---
title: Elemento CustomEntry per CustomEntries per CustomControl per visualizzazione (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ac3c0a25-f2ca-4e28-b3dc-9cb06a76d92a
caps.latest.revision: 11
ms.openlocfilehash: 7804155bffeb1f0df8339f797bf59f8def56a3fc
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62066448"
---
# <a name="customentry-element-for-customentries-for-customcontrol-for-view-format"></a><span data-ttu-id="dd212-102">Elemento CustomEntry per CustomEntries per CustomControl per View (formato)</span><span class="sxs-lookup"><span data-stu-id="dd212-102">CustomEntry Element for CustomEntries for CustomControl for View (Format)</span></span>

<span data-ttu-id="dd212-103">Fornisce una definizione della vista del controllo personalizzato.</span><span class="sxs-lookup"><span data-stu-id="dd212-103">Provides a definition of the custom control view.</span></span>

<span data-ttu-id="dd212-104">Elemento (formato) elemento ViewDefinitions (formato) visualizzazione elemento (formato) elemento CustomControl (formato) CustomEntries elemento di configurazione per CustomControl elemento di visualizzazione (formato) CustomEntry per CustomEntries per visualizzazione (formato)</span><span class="sxs-lookup"><span data-stu-id="dd212-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) CustomControl Element (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="dd212-105">Sintassi</span><span class="sxs-lookup"><span data-stu-id="dd212-105">Syntax</span></span>

```xml
<CustomEntry>
  <EntrySelectedBy>...</EntrySelectedBy>
  <CustomItem>...</CustomItem>
</CustomEntry>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="dd212-106">Elementi e attributi</span><span class="sxs-lookup"><span data-stu-id="dd212-106">Attributes and Elements</span></span>

<span data-ttu-id="dd212-107">Le sezioni seguenti descrivono gli attributi e gli elementi figlio dell'elemento padre del `CustomEntry` elemento.</span><span class="sxs-lookup"><span data-stu-id="dd212-107">The following sections describe attributes, child elements, and the parent element of the `CustomEntry` element.</span></span> <span data-ttu-id="dd212-108">È necessario specificare gli elementi visualizzati dalla definizione.</span><span class="sxs-lookup"><span data-stu-id="dd212-108">You must specify the items displayed by the definition.</span></span>

### <a name="attributes"></a><span data-ttu-id="dd212-109">Attributes</span><span class="sxs-lookup"><span data-stu-id="dd212-109">Attributes</span></span>

<span data-ttu-id="dd212-110">Nessuna.</span><span class="sxs-lookup"><span data-stu-id="dd212-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="dd212-111">Elementi figlio</span><span class="sxs-lookup"><span data-stu-id="dd212-111">Child Elements</span></span>

|<span data-ttu-id="dd212-112">Elemento</span><span class="sxs-lookup"><span data-stu-id="dd212-112">Element</span></span>|<span data-ttu-id="dd212-113">Description</span><span class="sxs-lookup"><span data-stu-id="dd212-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="dd212-114">Elemento EntrySelectedBy per CustomEntry per visualizzazione (formato)</span><span class="sxs-lookup"><span data-stu-id="dd212-114">EntrySelectedBy Element for CustomEntry for View (Format)</span></span>](./entryselectedby-element-for-customentry-for-customcontrol-for-view-format.md)|<span data-ttu-id="dd212-115">Elemento facoltativo.</span><span class="sxs-lookup"><span data-stu-id="dd212-115">Optional element.</span></span><br /><br /> <span data-ttu-id="dd212-116">Definisce i tipi .NET che usano la definizione della vista del controllo personalizzato oppure la condizione che deve essere presente per questa definizione da usare.</span><span class="sxs-lookup"><span data-stu-id="dd212-116">Defines the .NET types that use the definition of the custom control view or the condition that must exist for this definition to be used.</span></span>|
|[<span data-ttu-id="dd212-117">Elemento CustomItem per CustomEntry per visualizzazione (formato)</span><span class="sxs-lookup"><span data-stu-id="dd212-117">CustomItem Element for CustomEntry for View (Format)</span></span>](./customitem-element-for-customentry-for-customcontrol-for-view-format.md)|<span data-ttu-id="dd212-118">Definisce un controllo per la definizione del controllo personalizzato.</span><span class="sxs-lookup"><span data-stu-id="dd212-118">Defines a control for the custom control definition.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="dd212-119">Elementi padre</span><span class="sxs-lookup"><span data-stu-id="dd212-119">Parent Elements</span></span>

|<span data-ttu-id="dd212-120">Elemento</span><span class="sxs-lookup"><span data-stu-id="dd212-120">Element</span></span>|<span data-ttu-id="dd212-121">Description</span><span class="sxs-lookup"><span data-stu-id="dd212-121">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="dd212-122">Elemento CustomEntries per CustomControl per visualizzazione (formato)</span><span class="sxs-lookup"><span data-stu-id="dd212-122">CustomEntries Element for CustomControl for View (Format)</span></span>](./customentries-element-for-customcontrol-for-view-format.md)|<span data-ttu-id="dd212-123">Fornisce le definizioni della vista del controllo personalizzato.</span><span class="sxs-lookup"><span data-stu-id="dd212-123">Provides the definitions of the custom control view.</span></span> <span data-ttu-id="dd212-124">La visualizzazione controlli personalizzati è necessario specificare una o più definizioni.</span><span class="sxs-lookup"><span data-stu-id="dd212-124">The custom control view must specify one or more definitions.</span></span>|

## <a name="remarks"></a><span data-ttu-id="dd212-125">Osservazioni</span><span class="sxs-lookup"><span data-stu-id="dd212-125">Remarks</span></span>

<span data-ttu-id="dd212-126">Nella maggior parte dei casi, una sola definizione è obbligatorio per ogni visualizzazione del controllo personalizzato, ma è possibile avere più definizioni, se si desidera utilizzare la stessa vista per visualizzare diversi oggetti .NET.</span><span class="sxs-lookup"><span data-stu-id="dd212-126">In most cases, only one definition is required for each custom control view, but it is possible to have multiple definitions if you want to use the same view to display different .NET objects.</span></span> <span data-ttu-id="dd212-127">In questi casi, è possibile fornire una definizione separata per ogni oggetto o un set di oggetti.</span><span class="sxs-lookup"><span data-stu-id="dd212-127">In those cases, you can provide a separate definition for each object or set of objects.</span></span>

## <a name="see-also"></a><span data-ttu-id="dd212-128">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="dd212-128">See Also</span></span>

[<span data-ttu-id="dd212-129">Elemento CustomControl per visualizzazione (formato)</span><span class="sxs-lookup"><span data-stu-id="dd212-129">CustomControl Element for View (Format)</span></span>](./customcontrol-element-for-view-format.md)

[<span data-ttu-id="dd212-130">Elemento CustomItem per CustomEntry per visualizzazione (formato)</span><span class="sxs-lookup"><span data-stu-id="dd212-130">CustomItem Element for CustomEntry for View (Format)</span></span>](./customitem-element-for-customentry-for-customcontrol-for-view-format.md)

[<span data-ttu-id="dd212-131">Elemento EntrySelectedBy per CustomEntry per visualizzazione (formato)</span><span class="sxs-lookup"><span data-stu-id="dd212-131">EntrySelectedBy Element for CustomEntry for View (Format)</span></span>](./entryselectedby-element-for-customentry-for-customcontrol-for-view-format.md)

[<span data-ttu-id="dd212-132">La scrittura di un File di formattazione di PowerShell</span><span class="sxs-lookup"><span data-stu-id="dd212-132">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
