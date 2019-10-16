---
title: Elemento TypeName per EntrySelectedBy per GroupBy (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: b8b6739b-770c-432a-95ab-551c7507c51f
caps.latest.revision: 6
ms.openlocfilehash: 3b5ce60d3a0d76988af48f49445a5478a415d498
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/15/2019
ms.locfileid: "72361670"
---
# <a name="typename-element-for-entryselectedby-for-groupby-format"></a><span data-ttu-id="cf6fc-102">Elemento TypeName per EntrySelectedBy per GroupBy (formato)</span><span class="sxs-lookup"><span data-stu-id="cf6fc-102">TypeName Element for EntrySelectedBy for GroupBy (Format)</span></span>

<span data-ttu-id="cf6fc-103">Specifica un tipo .NET che usa questa definizione del controllo personalizzato.</span><span class="sxs-lookup"><span data-stu-id="cf6fc-103">Specifies a .NET type that uses this definition of the custom control.</span></span> <span data-ttu-id="cf6fc-104">Questo elemento viene utilizzato quando si definisce la modalità di visualizzazione di un nuovo gruppo di oggetti.</span><span class="sxs-lookup"><span data-stu-id="cf6fc-104">This element is used when defining how a new group of objects is displayed.</span></span>

<span data-ttu-id="cf6fc-105">Elemento Configuration (Format) elemento ViewDefinitions (Format) elemento View (Format) elemento GroupBy per View (Format) elemento CustomControl per l'elemento GroupBy (Format) CustomEntries per CustomControl per l'elemento GroupBy (Format) CustomEntry per CustomControl per l'elemento EntrySelectedBy di GroupBy (Format) per CustomEntry per l'elemento di GroupBy (Format) TypeName per EntrySelectedBy per GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="cf6fc-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) GroupBy Element for View (Format) CustomControl Element for GroupBy (Format) CustomEntries Element for CustomControl for GroupBy (Format) CustomEntry Element for CustomControl for GroupBy (Format) EntrySelectedBy Element for CustomEntry for GroupBy (Format) TypeName Element for EntrySelectedBy for GroupBy (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="cf6fc-106">Sintassi</span><span class="sxs-lookup"><span data-stu-id="cf6fc-106">Syntax</span></span>

```xml
<TypeName>Nameof.NetType</TypeName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="cf6fc-107">Attributi ed elementi</span><span class="sxs-lookup"><span data-stu-id="cf6fc-107">Attributes and Elements</span></span>

<span data-ttu-id="cf6fc-108">Nelle sezioni seguenti vengono descritti gli attributi, gli elementi figlio e l'elemento padre dell'elemento `TypeName`.</span><span class="sxs-lookup"><span data-stu-id="cf6fc-108">The following sections describe attributes, child elements, and the parent element of the `TypeName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="cf6fc-109">Attributi</span><span class="sxs-lookup"><span data-stu-id="cf6fc-109">Attributes</span></span>

<span data-ttu-id="cf6fc-110">Nessuna.</span><span class="sxs-lookup"><span data-stu-id="cf6fc-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="cf6fc-111">Elementi figlio</span><span class="sxs-lookup"><span data-stu-id="cf6fc-111">Child Elements</span></span>

<span data-ttu-id="cf6fc-112">Nessuna.</span><span class="sxs-lookup"><span data-stu-id="cf6fc-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="cf6fc-113">Elementi padre</span><span class="sxs-lookup"><span data-stu-id="cf6fc-113">Parent Elements</span></span>

|<span data-ttu-id="cf6fc-114">Elemento</span><span class="sxs-lookup"><span data-stu-id="cf6fc-114">Element</span></span>|<span data-ttu-id="cf6fc-115">Description</span><span class="sxs-lookup"><span data-stu-id="cf6fc-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="cf6fc-116">Elemento EntrySelectedBy per CustomEntry per GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="cf6fc-116">EntrySelectedBy Element for CustomEntry for GroupBy (Format)</span></span>](./entryselectedby-element-for-customentry-for-groupby-format.md)|<span data-ttu-id="cf6fc-117">Definisce i tipi .NET che utilizzano questa definizione di controllo o la condizione che deve esistere affinché questa definizione venga utilizzata.</span><span class="sxs-lookup"><span data-stu-id="cf6fc-117">Defines the .NET types that use this control definition or the condition that must exist for this definition to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="cf6fc-118">Valore di testo</span><span class="sxs-lookup"><span data-stu-id="cf6fc-118">Text Value</span></span>

<span data-ttu-id="cf6fc-119">Specificare il nome completo del tipo .NET, ad esempio `System.IO.DirectoryInfo`.</span><span class="sxs-lookup"><span data-stu-id="cf6fc-119">Specify the fully qualified name of the .NET type, such as `System.IO.DirectoryInfo`.</span></span>

## <a name="remarks"></a><span data-ttu-id="cf6fc-120">Osservazioni</span><span class="sxs-lookup"><span data-stu-id="cf6fc-120">Remarks</span></span>

<span data-ttu-id="cf6fc-121">Per ogni definizione di controllo deve essere definito almeno un nome di tipo, un set di selezione o una condizione di selezione.</span><span class="sxs-lookup"><span data-stu-id="cf6fc-121">Each control definition must have at least one type name, selection set, or selection condition defined.</span></span>

<span data-ttu-id="cf6fc-122">Per ulteriori informazioni sui componenti di una visualizzazione controlli personalizzata, vedere [creazione di controlli personalizzati](./creating-custom-controls.md).</span><span class="sxs-lookup"><span data-stu-id="cf6fc-122">For more information about the components of a custom control view, see [Creating Custom Controls](./creating-custom-controls.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="cf6fc-123">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="cf6fc-123">See Also</span></span>

[<span data-ttu-id="cf6fc-124">Creazione di controlli personalizzati</span><span class="sxs-lookup"><span data-stu-id="cf6fc-124">Creating Custom Controls</span></span>](./creating-custom-controls.md)

[<span data-ttu-id="cf6fc-125">Elemento EntrySelectedBy per CustomEntry per GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="cf6fc-125">EntrySelectedBy Element for CustomEntry for GroupBy (Format)</span></span>](./entryselectedby-element-for-customentry-for-groupby-format.md)

[<span data-ttu-id="cf6fc-126">Scrittura di un file di formattazione di PowerShell</span><span class="sxs-lookup"><span data-stu-id="cf6fc-126">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
