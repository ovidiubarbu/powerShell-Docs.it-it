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
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/05/2019
ms.locfileid: "72361670"
---
# <a name="typename-element-for-entryselectedby-for-groupby-format"></a><span data-ttu-id="0628b-102">Elemento TypeName per EntrySelectedBy per GroupBy (formato)</span><span class="sxs-lookup"><span data-stu-id="0628b-102">TypeName Element for EntrySelectedBy for GroupBy (Format)</span></span>

<span data-ttu-id="0628b-103">Specifica un tipo .NET che usa questa definizione del controllo personalizzato.</span><span class="sxs-lookup"><span data-stu-id="0628b-103">Specifies a .NET type that uses this definition of the custom control.</span></span> <span data-ttu-id="0628b-104">Questo elemento viene utilizzato quando si definisce la modalità di visualizzazione di un nuovo gruppo di oggetti.</span><span class="sxs-lookup"><span data-stu-id="0628b-104">This element is used when defining how a new group of objects is displayed.</span></span>

<span data-ttu-id="0628b-105">Elemento Configuration (Format) elemento ViewDefinitions (Format) elemento View (Format) elemento GroupBy per View (Format) elemento CustomControl per l'elemento GroupBy (Format) CustomEntries per CustomControl per l'elemento GroupBy (Format) CustomEntry per CustomControl per l'elemento EntrySelectedBy di GroupBy (Format) per CustomEntry per l'elemento di GroupBy (Format) TypeName per EntrySelectedBy per GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="0628b-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) GroupBy Element for View (Format) CustomControl Element for GroupBy (Format) CustomEntries Element for CustomControl for GroupBy (Format) CustomEntry Element for CustomControl for GroupBy (Format) EntrySelectedBy Element for CustomEntry for GroupBy (Format) TypeName Element for EntrySelectedBy for GroupBy (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="0628b-106">Sintassi</span><span class="sxs-lookup"><span data-stu-id="0628b-106">Syntax</span></span>

```xml
<TypeName>Nameof.NetType</TypeName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="0628b-107">Attributi ed elementi</span><span class="sxs-lookup"><span data-stu-id="0628b-107">Attributes and Elements</span></span>

<span data-ttu-id="0628b-108">Nelle sezioni seguenti vengono descritti gli attributi, gli elementi figlio e l'elemento padre dell'elemento `TypeName`.</span><span class="sxs-lookup"><span data-stu-id="0628b-108">The following sections describe attributes, child elements, and the parent element of the `TypeName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="0628b-109">Attributi</span><span class="sxs-lookup"><span data-stu-id="0628b-109">Attributes</span></span>

<span data-ttu-id="0628b-110">Nessuna.</span><span class="sxs-lookup"><span data-stu-id="0628b-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="0628b-111">Elementi figlio</span><span class="sxs-lookup"><span data-stu-id="0628b-111">Child Elements</span></span>

<span data-ttu-id="0628b-112">Nessuna.</span><span class="sxs-lookup"><span data-stu-id="0628b-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="0628b-113">Elementi padre</span><span class="sxs-lookup"><span data-stu-id="0628b-113">Parent Elements</span></span>

|<span data-ttu-id="0628b-114">Elemento</span><span class="sxs-lookup"><span data-stu-id="0628b-114">Element</span></span>|<span data-ttu-id="0628b-115">Description</span><span class="sxs-lookup"><span data-stu-id="0628b-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="0628b-116">Elemento EntrySelectedBy per CustomEntry per GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="0628b-116">EntrySelectedBy Element for CustomEntry for GroupBy (Format)</span></span>](./entryselectedby-element-for-customentry-for-groupby-format.md)|<span data-ttu-id="0628b-117">Definisce i tipi .NET che utilizzano questa definizione di controllo o la condizione che deve esistere affinché questa definizione venga utilizzata.</span><span class="sxs-lookup"><span data-stu-id="0628b-117">Defines the .NET types that use this control definition or the condition that must exist for this definition to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="0628b-118">Valore testo</span><span class="sxs-lookup"><span data-stu-id="0628b-118">Text Value</span></span>

<span data-ttu-id="0628b-119">Specificare il nome completo del tipo .NET, ad esempio `System.IO.DirectoryInfo`.</span><span class="sxs-lookup"><span data-stu-id="0628b-119">Specify the fully qualified name of the .NET type, such as `System.IO.DirectoryInfo`.</span></span>

## <a name="remarks"></a><span data-ttu-id="0628b-120">Osservazioni</span><span class="sxs-lookup"><span data-stu-id="0628b-120">Remarks</span></span>

<span data-ttu-id="0628b-121">Per ogni definizione di controllo deve essere definito almeno un nome di tipo, un set di selezione o una condizione di selezione.</span><span class="sxs-lookup"><span data-stu-id="0628b-121">Each control definition must have at least one type name, selection set, or selection condition defined.</span></span>

<span data-ttu-id="0628b-122">Per ulteriori informazioni sui componenti di una visualizzazione controlli personalizzata, vedere [creazione di controlli personalizzati](./creating-custom-controls.md).</span><span class="sxs-lookup"><span data-stu-id="0628b-122">For more information about the components of a custom control view, see [Creating Custom Controls](./creating-custom-controls.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="0628b-123">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="0628b-123">See Also</span></span>

[<span data-ttu-id="0628b-124">Creazione di controlli personalizzati</span><span class="sxs-lookup"><span data-stu-id="0628b-124">Creating Custom Controls</span></span>](./creating-custom-controls.md)

[<span data-ttu-id="0628b-125">Elemento EntrySelectedBy per CustomEntry per GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="0628b-125">EntrySelectedBy Element for CustomEntry for GroupBy (Format)</span></span>](./entryselectedby-element-for-customentry-for-groupby-format.md)

[<span data-ttu-id="0628b-126">Scrittura di un file di formattazione di PowerShell</span><span class="sxs-lookup"><span data-stu-id="0628b-126">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
