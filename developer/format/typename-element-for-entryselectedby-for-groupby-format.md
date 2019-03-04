---
title: Elemento TypeName per EntrySelectedBy per GroupBy (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: b8b6739b-770c-432a-95ab-551c7507c51f
caps.latest.revision: 6
ms.openlocfilehash: 3b5ce60d3a0d76988af48f49445a5478a415d498
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/03/2019
ms.locfileid: "56861667"
---
# <a name="typename-element-for-entryselectedby-for-groupby-format"></a><span data-ttu-id="e8af5-102">Elemento TypeName per EntrySelectedBy per GroupBy (formato)</span><span class="sxs-lookup"><span data-stu-id="e8af5-102">TypeName Element for EntrySelectedBy for GroupBy (Format)</span></span>

<span data-ttu-id="e8af5-103">Specifica un tipo .NET che usa questa definizione del controllo personalizzato.</span><span class="sxs-lookup"><span data-stu-id="e8af5-103">Specifies a .NET type that uses this definition of the custom control.</span></span> <span data-ttu-id="e8af5-104">Questo elemento viene usato quando si definisce come viene visualizzato un nuovo gruppo di oggetti.</span><span class="sxs-lookup"><span data-stu-id="e8af5-104">This element is used when defining how a new group of objects is displayed.</span></span>

<span data-ttu-id="e8af5-105">Elemento di GroupBy elemento (formato) per la visualizzazione elemento ViewDefinitions (formato) configurazione elemento (formato) per visualizzazione (formato) CustomControl elemento per elemento CustomEntries GroupBy (formato) per CustomControl per elemento CustomEntry GroupBy (formato) CustomControl per elemento EntrySelectedBy GroupBy (formato) per CustomEntry per elemento TypeName GroupBy (formato) per EntrySelectedBy per GroupBy (formato)</span><span class="sxs-lookup"><span data-stu-id="e8af5-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) GroupBy Element for View (Format) CustomControl Element for GroupBy (Format) CustomEntries Element for CustomControl for GroupBy (Format) CustomEntry Element for CustomControl for GroupBy (Format) EntrySelectedBy Element for CustomEntry for GroupBy (Format) TypeName Element for EntrySelectedBy for GroupBy (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="e8af5-106">Sintassi</span><span class="sxs-lookup"><span data-stu-id="e8af5-106">Syntax</span></span>

```xml
<TypeName>Nameof.NetType</TypeName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="e8af5-107">Attributi ed elementi</span><span class="sxs-lookup"><span data-stu-id="e8af5-107">Attributes and Elements</span></span>

<span data-ttu-id="e8af5-108">Le sezioni seguenti descrivono gli attributi e gli elementi figlio dell'elemento padre del `TypeName` elemento.</span><span class="sxs-lookup"><span data-stu-id="e8af5-108">The following sections describe attributes, child elements, and the parent element of the `TypeName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="e8af5-109">Attributes</span><span class="sxs-lookup"><span data-stu-id="e8af5-109">Attributes</span></span>

<span data-ttu-id="e8af5-110">Nessuna.</span><span class="sxs-lookup"><span data-stu-id="e8af5-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="e8af5-111">Elementi figlio</span><span class="sxs-lookup"><span data-stu-id="e8af5-111">Child Elements</span></span>

<span data-ttu-id="e8af5-112">Nessuna.</span><span class="sxs-lookup"><span data-stu-id="e8af5-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="e8af5-113">Elementi padre</span><span class="sxs-lookup"><span data-stu-id="e8af5-113">Parent Elements</span></span>

|<span data-ttu-id="e8af5-114">Elemento</span><span class="sxs-lookup"><span data-stu-id="e8af5-114">Element</span></span>|<span data-ttu-id="e8af5-115">Description</span><span class="sxs-lookup"><span data-stu-id="e8af5-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="e8af5-116">Elemento EntrySelectedBy per CustomEntry per GroupBy (formato)</span><span class="sxs-lookup"><span data-stu-id="e8af5-116">EntrySelectedBy Element for CustomEntry for GroupBy (Format)</span></span>](./entryselectedby-element-for-customentry-for-groupby-format.md)|<span data-ttu-id="e8af5-117">Definisce i tipi .NET che usano questa definizione di controllo o la condizione che deve essere presente per questa definizione da usare.</span><span class="sxs-lookup"><span data-stu-id="e8af5-117">Defines the .NET types that use this control definition or the condition that must exist for this definition to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="e8af5-118">Valore di testo</span><span class="sxs-lookup"><span data-stu-id="e8af5-118">Text Value</span></span>

<span data-ttu-id="e8af5-119">Specificare il nome completo del tipo .NET, ad esempio `System.IO.DirectoryInfo`.</span><span class="sxs-lookup"><span data-stu-id="e8af5-119">Specify the fully qualified name of the .NET type, such as `System.IO.DirectoryInfo`.</span></span>

## <a name="remarks"></a><span data-ttu-id="e8af5-120">Osservazioni</span><span class="sxs-lookup"><span data-stu-id="e8af5-120">Remarks</span></span>

<span data-ttu-id="e8af5-121">Ogni definizione di controllo deve avere almeno un nome di tipo, il set di selezione o condizione di selezione definiti.</span><span class="sxs-lookup"><span data-stu-id="e8af5-121">Each control definition must have at least one type name, selection set, or selection condition defined.</span></span>

<span data-ttu-id="e8af5-122">Per altre informazioni sui componenti di una vista di controllo personalizzato, vedere [Creating Custom Controls](./creating-custom-controls.md).</span><span class="sxs-lookup"><span data-stu-id="e8af5-122">For more information about the components of a custom control view, see [Creating Custom Controls](./creating-custom-controls.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="e8af5-123">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="e8af5-123">See Also</span></span>

[<span data-ttu-id="e8af5-124">Creazione di controlli personalizzati</span><span class="sxs-lookup"><span data-stu-id="e8af5-124">Creating Custom Controls</span></span>](./creating-custom-controls.md)

[<span data-ttu-id="e8af5-125">Elemento EntrySelectedBy per CustomEntry per GroupBy (formato)</span><span class="sxs-lookup"><span data-stu-id="e8af5-125">EntrySelectedBy Element for CustomEntry for GroupBy (Format)</span></span>](./entryselectedby-element-for-customentry-for-groupby-format.md)

[<span data-ttu-id="e8af5-126">La scrittura di un File di formattazione di PowerShell</span><span class="sxs-lookup"><span data-stu-id="e8af5-126">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
