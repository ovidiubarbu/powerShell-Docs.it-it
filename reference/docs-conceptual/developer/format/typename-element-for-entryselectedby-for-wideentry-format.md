---
title: Elemento TypeName per EntrySelectedBy per WideEntry (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 81a91c74-6229-4b64-aa2b-9123e8b7e9e5
caps.latest.revision: 11
ms.openlocfilehash: be35f6e9e2ad0b2d9a21a91c053aa0f70cafaf9c
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/15/2019
ms.locfileid: "72361620"
---
# <a name="typename-element-for-entryselectedby-for-wideentry-format"></a><span data-ttu-id="056ec-102">Elemento TypeName per EntrySelectedBy per WideEntry (formato)</span><span class="sxs-lookup"><span data-stu-id="056ec-102">TypeName Element for EntrySelectedBy for WideEntry (Format)</span></span>

<span data-ttu-id="056ec-103">Specifica un tipo .NET per la definizione.</span><span class="sxs-lookup"><span data-stu-id="056ec-103">Specifies a .NET type for the definition.</span></span> <span data-ttu-id="056ec-104">La definizione viene utilizzata ogni volta che l'oggetto viene visualizzato.</span><span class="sxs-lookup"><span data-stu-id="056ec-104">The definition is used whenever this object is displayed.</span></span>

<span data-ttu-id="056ec-105">Elemento Configuration (Format) elemento ViewDefinitions (Format) elemento View (Format) elemento WideControl (Format) elemento WideEntries (Format) elemento WideEntry (Format) EntrySelectedBy elemento per WideEntry (Format) TypeName elemento per WideEntry ( Formato</span><span class="sxs-lookup"><span data-stu-id="056ec-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) WideControl Element (Format) WideEntries Element (Format) WideEntry Element (Format) EntrySelectedBy Element for WideEntry (Format) TypeName Element for WideEntry (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="056ec-106">Sintassi</span><span class="sxs-lookup"><span data-stu-id="056ec-106">Syntax</span></span>

```xml
<TypeName>Nameof.NetType</TypeName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="056ec-107">Attributi ed elementi</span><span class="sxs-lookup"><span data-stu-id="056ec-107">Attributes and Elements</span></span>

<span data-ttu-id="056ec-108">Nelle sezioni seguenti vengono descritti gli attributi, gli elementi figlio e l'elemento padre dell'elemento `TypeName`.</span><span class="sxs-lookup"><span data-stu-id="056ec-108">The following sections describe the attributes, child elements, and the parent element of the `TypeName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="056ec-109">Attributi</span><span class="sxs-lookup"><span data-stu-id="056ec-109">Attributes</span></span>

<span data-ttu-id="056ec-110">Nessuna.</span><span class="sxs-lookup"><span data-stu-id="056ec-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="056ec-111">Elementi figlio</span><span class="sxs-lookup"><span data-stu-id="056ec-111">Child Elements</span></span>

<span data-ttu-id="056ec-112">Nessuna.</span><span class="sxs-lookup"><span data-stu-id="056ec-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="056ec-113">Elementi padre</span><span class="sxs-lookup"><span data-stu-id="056ec-113">Parent Elements</span></span>

|<span data-ttu-id="056ec-114">Elemento</span><span class="sxs-lookup"><span data-stu-id="056ec-114">Element</span></span>|<span data-ttu-id="056ec-115">Description</span><span class="sxs-lookup"><span data-stu-id="056ec-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="056ec-116">Elemento EntrySelectedBy per WideEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="056ec-116">EntrySelectedBy Element for WideEntry (Format)</span></span>](./entryselectedby-element-for-wideentry-format.md)|<span data-ttu-id="056ec-117">Definisce i tipi .NET che utilizzano questa voce estesa o la condizione che deve esistere affinché questa voce venga utilizzata.</span><span class="sxs-lookup"><span data-stu-id="056ec-117">Defines the .NET types that use this wide entry or the condition that must exist for this entry to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="056ec-118">Valore di testo</span><span class="sxs-lookup"><span data-stu-id="056ec-118">Text Value</span></span>

<span data-ttu-id="056ec-119">Specificare il nome completo del tipo .NET, ad esempio `System.IO.DirectoryInfo`.</span><span class="sxs-lookup"><span data-stu-id="056ec-119">Specify the fully qualified name of the .NET type, such as `System.IO.DirectoryInfo`.</span></span>

## <a name="remarks"></a><span data-ttu-id="056ec-120">Osservazioni</span><span class="sxs-lookup"><span data-stu-id="056ec-120">Remarks</span></span>

<span data-ttu-id="056ec-121">Ogni voce estesa deve specificare uno o più tipi .NET, un set di selezione o la condizione di selezione che deve esistere per la definizione da usare.</span><span class="sxs-lookup"><span data-stu-id="056ec-121">Each wide entry must specify one or more .NET types, a selection set, or the selection condition that must exist for the definition to be used.</span></span>

<span data-ttu-id="056ec-122">Per ulteriori informazioni su altri componenti di una visualizzazione estesa, vedere [creazione di un'ampia visualizzazione](./creating-a-wide-view.md).</span><span class="sxs-lookup"><span data-stu-id="056ec-122">For more information about other components of a wide view, see [Creating a Wide View](./creating-a-wide-view.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="056ec-123">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="056ec-123">See Also</span></span>

[<span data-ttu-id="056ec-124">Creazione di una visualizzazione estesa</span><span class="sxs-lookup"><span data-stu-id="056ec-124">Creating a Wide View</span></span>](./creating-a-wide-view.md)

[<span data-ttu-id="056ec-125">Elemento EntrySelectedBy per WideEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="056ec-125">EntrySelectedBy Element for WideEntry (Format)</span></span>](./entryselectedby-element-for-wideentry-format.md)

[<span data-ttu-id="056ec-126">Scrittura di un file di formattazione di PowerShell</span><span class="sxs-lookup"><span data-stu-id="056ec-126">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
