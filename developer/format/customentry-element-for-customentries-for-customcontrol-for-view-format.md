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
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/03/2019
ms.locfileid: "56861817"
---
# <a name="customentry-element-for-customentries-for-customcontrol-for-view-format"></a><span data-ttu-id="1195c-102">Elemento CustomEntry per CustomEntries per CustomControl per View (formato)</span><span class="sxs-lookup"><span data-stu-id="1195c-102">CustomEntry Element for CustomEntries for CustomControl for View (Format)</span></span>

<span data-ttu-id="1195c-103">Fornisce una definizione della vista del controllo personalizzato.</span><span class="sxs-lookup"><span data-stu-id="1195c-103">Provides a definition of the custom control view.</span></span>

<span data-ttu-id="1195c-104">Elemento (formato) elemento ViewDefinitions (formato) visualizzazione elemento (formato) elemento CustomControl (formato) CustomEntries elemento di configurazione per CustomControl elemento di visualizzazione (formato) CustomEntry per CustomEntries per visualizzazione (formato)</span><span class="sxs-lookup"><span data-stu-id="1195c-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) CustomControl Element (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="1195c-105">Sintassi</span><span class="sxs-lookup"><span data-stu-id="1195c-105">Syntax</span></span>

```xml
<CustomEntry>
  <EntrySelectedBy>...</EntrySelectedBy>
  <CustomItem>...</CustomItem>
</CustomEntry>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="1195c-106">Attributi ed elementi</span><span class="sxs-lookup"><span data-stu-id="1195c-106">Attributes and Elements</span></span>

<span data-ttu-id="1195c-107">Le sezioni seguenti descrivono gli attributi e gli elementi figlio dell'elemento padre del `CustomEntry` elemento.</span><span class="sxs-lookup"><span data-stu-id="1195c-107">The following sections describe attributes, child elements, and the parent element of the `CustomEntry` element.</span></span> <span data-ttu-id="1195c-108">È necessario specificare gli elementi visualizzati dalla definizione.</span><span class="sxs-lookup"><span data-stu-id="1195c-108">You must specify the items displayed by the definition.</span></span>

### <a name="attributes"></a><span data-ttu-id="1195c-109">Attributes</span><span class="sxs-lookup"><span data-stu-id="1195c-109">Attributes</span></span>

<span data-ttu-id="1195c-110">Nessuna.</span><span class="sxs-lookup"><span data-stu-id="1195c-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="1195c-111">Elementi figlio</span><span class="sxs-lookup"><span data-stu-id="1195c-111">Child Elements</span></span>

|<span data-ttu-id="1195c-112">Elemento</span><span class="sxs-lookup"><span data-stu-id="1195c-112">Element</span></span>|<span data-ttu-id="1195c-113">Description</span><span class="sxs-lookup"><span data-stu-id="1195c-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="1195c-114">Elemento EntrySelectedBy per CustomEntry per visualizzazione (formato)</span><span class="sxs-lookup"><span data-stu-id="1195c-114">EntrySelectedBy Element for CustomEntry for View (Format)</span></span>](./entryselectedby-element-for-customentry-for-customcontrol-for-view-format.md)|<span data-ttu-id="1195c-115">Elemento facoltativo.</span><span class="sxs-lookup"><span data-stu-id="1195c-115">Optional element.</span></span><br /><br /> <span data-ttu-id="1195c-116">Definisce i tipi .NET che usano la definizione della vista del controllo personalizzato oppure la condizione che deve essere presente per questa definizione da usare.</span><span class="sxs-lookup"><span data-stu-id="1195c-116">Defines the .NET types that use the definition of the custom control view or the condition that must exist for this definition to be used.</span></span>|
|[<span data-ttu-id="1195c-117">Elemento CustomItem per CustomEntry per visualizzazione (formato)</span><span class="sxs-lookup"><span data-stu-id="1195c-117">CustomItem Element for CustomEntry for View (Format)</span></span>](./customitem-element-for-customentry-for-customcontrol-for-view-format.md)|<span data-ttu-id="1195c-118">Definisce un controllo per la definizione del controllo personalizzato.</span><span class="sxs-lookup"><span data-stu-id="1195c-118">Defines a control for the custom control definition.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="1195c-119">Elementi padre</span><span class="sxs-lookup"><span data-stu-id="1195c-119">Parent Elements</span></span>

|<span data-ttu-id="1195c-120">Elemento</span><span class="sxs-lookup"><span data-stu-id="1195c-120">Element</span></span>|<span data-ttu-id="1195c-121">Description</span><span class="sxs-lookup"><span data-stu-id="1195c-121">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="1195c-122">Elemento CustomEntries per CustomControl per visualizzazione (formato)</span><span class="sxs-lookup"><span data-stu-id="1195c-122">CustomEntries Element for CustomControl for View (Format)</span></span>](./customentries-element-for-customcontrol-for-view-format.md)|<span data-ttu-id="1195c-123">Fornisce le definizioni della vista del controllo personalizzato.</span><span class="sxs-lookup"><span data-stu-id="1195c-123">Provides the definitions of the custom control view.</span></span> <span data-ttu-id="1195c-124">La visualizzazione controlli personalizzati è necessario specificare una o più definizioni.</span><span class="sxs-lookup"><span data-stu-id="1195c-124">The custom control view must specify one or more definitions.</span></span>|

## <a name="remarks"></a><span data-ttu-id="1195c-125">Osservazioni</span><span class="sxs-lookup"><span data-stu-id="1195c-125">Remarks</span></span>

<span data-ttu-id="1195c-126">Nella maggior parte dei casi, una sola definizione è obbligatorio per ogni visualizzazione del controllo personalizzato, ma è possibile avere più definizioni, se si desidera utilizzare la stessa vista per visualizzare diversi oggetti .NET.</span><span class="sxs-lookup"><span data-stu-id="1195c-126">In most cases, only one definition is required for each custom control view, but it is possible to have multiple definitions if you want to use the same view to display different .NET objects.</span></span> <span data-ttu-id="1195c-127">In questi casi, è possibile fornire una definizione separata per ogni oggetto o un set di oggetti.</span><span class="sxs-lookup"><span data-stu-id="1195c-127">In those cases, you can provide a separate definition for each object or set of objects.</span></span>

## <a name="see-also"></a><span data-ttu-id="1195c-128">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="1195c-128">See Also</span></span>

[<span data-ttu-id="1195c-129">Elemento CustomControl per visualizzazione (formato)</span><span class="sxs-lookup"><span data-stu-id="1195c-129">CustomControl Element for View (Format)</span></span>](./customcontrol-element-for-view-format.md)

[<span data-ttu-id="1195c-130">Elemento CustomItem per CustomEntry per visualizzazione (formato)</span><span class="sxs-lookup"><span data-stu-id="1195c-130">CustomItem Element for CustomEntry for View (Format)</span></span>](./customitem-element-for-customentry-for-customcontrol-for-view-format.md)

[<span data-ttu-id="1195c-131">Elemento EntrySelectedBy per CustomEntry per visualizzazione (formato)</span><span class="sxs-lookup"><span data-stu-id="1195c-131">EntrySelectedBy Element for CustomEntry for View (Format)</span></span>](./entryselectedby-element-for-customentry-for-customcontrol-for-view-format.md)

[<span data-ttu-id="1195c-132">La scrittura di un File di formattazione di PowerShell</span><span class="sxs-lookup"><span data-stu-id="1195c-132">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
