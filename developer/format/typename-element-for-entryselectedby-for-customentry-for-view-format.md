---
title: Elemento TypeName per EntrySelectedBy per CustomEntry per visualizzazione (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 76548af7-05bd-4d12-bf71-6fb69c434ef2
caps.latest.revision: 10
ms.openlocfilehash: c3dd761cd9b6c468d4833ea35b897ba5d425f598
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62083978"
---
# <a name="typename-element-for-entryselectedby-for-customentry-for-view-format"></a><span data-ttu-id="c4337-102">Elemento TypeName per EntrySelectedBy per CustomEntry per View (formato)</span><span class="sxs-lookup"><span data-stu-id="c4337-102">TypeName Element for EntrySelectedBy for CustomEntry for View (Format)</span></span>

<span data-ttu-id="c4337-103">Specifica un tipo .NET che usa questa definizione della vista del controllo personalizzato.</span><span class="sxs-lookup"><span data-stu-id="c4337-103">Specifies a .NET type that uses this definition of the custom control view.</span></span> <span data-ttu-id="c4337-104">Non sono previsti limiti al numero di tipi che possono essere specificati per una definizione.</span><span class="sxs-lookup"><span data-stu-id="c4337-104">There is no limit to the number of types that can be specified for a definition.</span></span>

<span data-ttu-id="c4337-105">Elemento (formato) elemento ViewDefinitions (formato) visualizzazione elemento (formato) elemento CustomControl (formato) CustomEntries elemento di configurazione per CustomControl elemento di visualizzazione (formato) CustomEntry per CustomEntries per EntrySelectedBy visualizzazione (formato) Elemento per CustomEntry elemento di visualizzazione (formato) TypeName per EntrySelectedBy per CustomEntry per visualizzazione (formato)</span><span class="sxs-lookup"><span data-stu-id="c4337-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) CustomControl Element (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for View (Format) EntrySelectedBy Element for CustomEntry for View (Format) TypeName Element for EntrySelectedBy for CustomEntry for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="c4337-106">Sintassi</span><span class="sxs-lookup"><span data-stu-id="c4337-106">Syntax</span></span>

```xml
<TypeName>Nameof.NetType</TypeName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="c4337-107">Elementi e attributi</span><span class="sxs-lookup"><span data-stu-id="c4337-107">Attributes and Elements</span></span>

<span data-ttu-id="c4337-108">Le sezioni seguenti descrivono gli attributi e gli elementi figlio dell'elemento padre del `TypeName` elemento.</span><span class="sxs-lookup"><span data-stu-id="c4337-108">The following sections describe attributes, child elements, and the parent element of the `TypeName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="c4337-109">Attributes</span><span class="sxs-lookup"><span data-stu-id="c4337-109">Attributes</span></span>

<span data-ttu-id="c4337-110">Nessuna.</span><span class="sxs-lookup"><span data-stu-id="c4337-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="c4337-111">Elementi figlio</span><span class="sxs-lookup"><span data-stu-id="c4337-111">Child Elements</span></span>

<span data-ttu-id="c4337-112">Nessuna.</span><span class="sxs-lookup"><span data-stu-id="c4337-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="c4337-113">Elementi padre</span><span class="sxs-lookup"><span data-stu-id="c4337-113">Parent Elements</span></span>

|<span data-ttu-id="c4337-114">Elemento</span><span class="sxs-lookup"><span data-stu-id="c4337-114">Element</span></span>|<span data-ttu-id="c4337-115">Description</span><span class="sxs-lookup"><span data-stu-id="c4337-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="c4337-116">Elemento EntrySelectedBy per CustomEntry per visualizzazione (formato)</span><span class="sxs-lookup"><span data-stu-id="c4337-116">EntrySelectedBy Element for CustomEntry for View (Format)</span></span>](./entryselectedby-element-for-customentry-for-customcontrol-for-view-format.md)|<span data-ttu-id="c4337-117">Definisce i tipi .NET che usano questa definizione di vista del controllo personalizzato o la condizione che deve essere presente per questa definizione da usare.</span><span class="sxs-lookup"><span data-stu-id="c4337-117">Defines the .NET types that use this custom control view definition or the condition that must exist for this definition to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="c4337-118">Valore di testo</span><span class="sxs-lookup"><span data-stu-id="c4337-118">Text Value</span></span>

<span data-ttu-id="c4337-119">Specificare il nome completo del tipo .NET, ad esempio `System.IO.DirectoryInfo`.</span><span class="sxs-lookup"><span data-stu-id="c4337-119">Specify the fully qualified name of the .NET type, such as `System.IO.DirectoryInfo`.</span></span>

## <a name="remarks"></a><span data-ttu-id="c4337-120">Osservazioni</span><span class="sxs-lookup"><span data-stu-id="c4337-120">Remarks</span></span>

<span data-ttu-id="c4337-121">Ogni definizione di vista di controllo personalizzato deve avere almeno un nome di tipo, il set di selezione o condizione di selezione definiti.</span><span class="sxs-lookup"><span data-stu-id="c4337-121">Each custom control view definition must have at least one type name, selection set, or selection condition defined.</span></span>

<span data-ttu-id="c4337-122">Per altre informazioni sui componenti di una vista di controllo personalizzato, vedere [Creating Custom Controls](./creating-custom-controls.md).</span><span class="sxs-lookup"><span data-stu-id="c4337-122">For more information about the components of a custom control view, see [Creating Custom Controls](./creating-custom-controls.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="c4337-123">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="c4337-123">See Also</span></span>

[<span data-ttu-id="c4337-124">Creazione di controlli personalizzati</span><span class="sxs-lookup"><span data-stu-id="c4337-124">Creating Custom Controls</span></span>](./creating-custom-controls.md)

[<span data-ttu-id="c4337-125">Elemento EntrySelectedBy per CustomEntry per visualizzazione (formato)</span><span class="sxs-lookup"><span data-stu-id="c4337-125">EntrySelectedBy Element for CustomEntry for View (Format)</span></span>](./entryselectedby-element-for-customentry-for-customcontrol-for-view-format.md)

[<span data-ttu-id="c4337-126">La scrittura di un File di formattazione di PowerShell</span><span class="sxs-lookup"><span data-stu-id="c4337-126">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
