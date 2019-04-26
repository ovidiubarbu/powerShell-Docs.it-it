---
title: Elemento TypeName per EntrySelectedBy per WideEntry (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 81a91c74-6229-4b64-aa2b-9123e8b7e9e5
caps.latest.revision: 11
ms.openlocfilehash: be35f6e9e2ad0b2d9a21a91c053aa0f70cafaf9c
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62083927"
---
# <a name="typename-element-for-entryselectedby-for-wideentry-format"></a><span data-ttu-id="8b7ab-102">Elemento TypeName per EntrySelectedBy per WideEntry (formato)</span><span class="sxs-lookup"><span data-stu-id="8b7ab-102">TypeName Element for EntrySelectedBy for WideEntry (Format)</span></span>

<span data-ttu-id="8b7ab-103">Specifica un tipo .NET per la definizione.</span><span class="sxs-lookup"><span data-stu-id="8b7ab-103">Specifies a .NET type for the definition.</span></span> <span data-ttu-id="8b7ab-104">La definizione viene utilizzata ogni volta che viene visualizzato questo oggetto.</span><span class="sxs-lookup"><span data-stu-id="8b7ab-104">The definition is used whenever this object is displayed.</span></span>

<span data-ttu-id="8b7ab-105">Elemento (formato) elemento ViewDefinitions (formato) visualizzazione elemento (formato) elemento WideControl (formato) elemento WideEntries (formato) elemento WideEntry (formato) EntrySelectedBy elemento di configurazione per TypeName WideEntry (formato) (elemento) per WideEntry ( Formato)</span><span class="sxs-lookup"><span data-stu-id="8b7ab-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) WideControl Element (Format) WideEntries Element (Format) WideEntry Element (Format) EntrySelectedBy Element for WideEntry (Format) TypeName Element for WideEntry (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="8b7ab-106">Sintassi</span><span class="sxs-lookup"><span data-stu-id="8b7ab-106">Syntax</span></span>

```xml
<TypeName>Nameof.NetType</TypeName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="8b7ab-107">Elementi e attributi</span><span class="sxs-lookup"><span data-stu-id="8b7ab-107">Attributes and Elements</span></span>

<span data-ttu-id="8b7ab-108">Le sezioni seguenti descrivono gli attributi e gli elementi figlio dell'elemento padre del `TypeName` elemento.</span><span class="sxs-lookup"><span data-stu-id="8b7ab-108">The following sections describe the attributes, child elements, and the parent element of the `TypeName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="8b7ab-109">Attributes</span><span class="sxs-lookup"><span data-stu-id="8b7ab-109">Attributes</span></span>

<span data-ttu-id="8b7ab-110">Nessuna.</span><span class="sxs-lookup"><span data-stu-id="8b7ab-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="8b7ab-111">Elementi figlio</span><span class="sxs-lookup"><span data-stu-id="8b7ab-111">Child Elements</span></span>

<span data-ttu-id="8b7ab-112">Nessuna.</span><span class="sxs-lookup"><span data-stu-id="8b7ab-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="8b7ab-113">Elementi padre</span><span class="sxs-lookup"><span data-stu-id="8b7ab-113">Parent Elements</span></span>

|<span data-ttu-id="8b7ab-114">Elemento</span><span class="sxs-lookup"><span data-stu-id="8b7ab-114">Element</span></span>|<span data-ttu-id="8b7ab-115">Description</span><span class="sxs-lookup"><span data-stu-id="8b7ab-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="8b7ab-116">Elemento EntrySelectedBy per WideEntry (formato)</span><span class="sxs-lookup"><span data-stu-id="8b7ab-116">EntrySelectedBy Element for WideEntry (Format)</span></span>](./entryselectedby-element-for-wideentry-format.md)|<span data-ttu-id="8b7ab-117">Definisce i tipi .NET che usano questa voce ampia o la condizione che deve essere presente per questa voce da usare.</span><span class="sxs-lookup"><span data-stu-id="8b7ab-117">Defines the .NET types that use this wide entry or the condition that must exist for this entry to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="8b7ab-118">Valore di testo</span><span class="sxs-lookup"><span data-stu-id="8b7ab-118">Text Value</span></span>

<span data-ttu-id="8b7ab-119">Specificare il nome completo del tipo .NET, ad esempio `System.IO.DirectoryInfo`.</span><span class="sxs-lookup"><span data-stu-id="8b7ab-119">Specify the fully qualified name of the .NET type, such as `System.IO.DirectoryInfo`.</span></span>

## <a name="remarks"></a><span data-ttu-id="8b7ab-120">Osservazioni</span><span class="sxs-lookup"><span data-stu-id="8b7ab-120">Remarks</span></span>

<span data-ttu-id="8b7ab-121">Ogni voce ampia è necessario specificare uno o più tipi di .NET, un set di selezione o la condizione di selezione che deve essere presente per la definizione da usare.</span><span class="sxs-lookup"><span data-stu-id="8b7ab-121">Each wide entry must specify one or more .NET types, a selection set, or the selection condition that must exist for the definition to be used.</span></span>

<span data-ttu-id="8b7ab-122">Per altre informazioni sugli altri componenti di una visualizzazione più ampia, vedere [creazione di una visualizzazione più ampia](./creating-a-wide-view.md).</span><span class="sxs-lookup"><span data-stu-id="8b7ab-122">For more information about other components of a wide view, see [Creating a Wide View](./creating-a-wide-view.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="8b7ab-123">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="8b7ab-123">See Also</span></span>

[<span data-ttu-id="8b7ab-124">Creazione di una visualizzazione più ampia</span><span class="sxs-lookup"><span data-stu-id="8b7ab-124">Creating a Wide View</span></span>](./creating-a-wide-view.md)

[<span data-ttu-id="8b7ab-125">Elemento EntrySelectedBy per WideEntry (formato)</span><span class="sxs-lookup"><span data-stu-id="8b7ab-125">EntrySelectedBy Element for WideEntry (Format)</span></span>](./entryselectedby-element-for-wideentry-format.md)

[<span data-ttu-id="8b7ab-126">La scrittura di un File di formattazione di PowerShell</span><span class="sxs-lookup"><span data-stu-id="8b7ab-126">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
