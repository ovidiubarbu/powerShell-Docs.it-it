---
title: Elemento TypeName per EntrySelectedBy per CustomEntry per View (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 76548af7-05bd-4d12-bf71-6fb69c434ef2
caps.latest.revision: 10
ms.openlocfilehash: c3dd761cd9b6c468d4833ea35b897ba5d425f598
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/05/2019
ms.locfileid: "72368070"
---
# <a name="typename-element-for-entryselectedby-for-customentry-for-view-format"></a><span data-ttu-id="cf647-102">Elemento TypeName per EntrySelectedBy per CustomEntry per View (formato)</span><span class="sxs-lookup"><span data-stu-id="cf647-102">TypeName Element for EntrySelectedBy for CustomEntry for View (Format)</span></span>

<span data-ttu-id="cf647-103">Specifica un tipo .NET che usa questa definizione della visualizzazione del controllo personalizzato.</span><span class="sxs-lookup"><span data-stu-id="cf647-103">Specifies a .NET type that uses this definition of the custom control view.</span></span> <span data-ttu-id="cf647-104">Non esiste alcun limite al numero di tipi che è possibile specificare per una definizione.</span><span class="sxs-lookup"><span data-stu-id="cf647-104">There is no limit to the number of types that can be specified for a definition.</span></span>

<span data-ttu-id="cf647-105">Elemento Configuration (Format) elemento ViewDefinitions (Format) elemento View (Format) elemento CustomControl (Format) elemento CustomEntries per CustomControl per l'elemento View (Format) CustomEntry per CustomEntries per View (Format) EntrySelectedBy Elemento per CustomEntry per la visualizzazione (formato) elemento TypeName per EntrySelectedBy per CustomEntry per View (Format)</span><span class="sxs-lookup"><span data-stu-id="cf647-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) CustomControl Element (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for View (Format) EntrySelectedBy Element for CustomEntry for View (Format) TypeName Element for EntrySelectedBy for CustomEntry for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="cf647-106">Sintassi</span><span class="sxs-lookup"><span data-stu-id="cf647-106">Syntax</span></span>

```xml
<TypeName>Nameof.NetType</TypeName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="cf647-107">Attributi ed elementi</span><span class="sxs-lookup"><span data-stu-id="cf647-107">Attributes and Elements</span></span>

<span data-ttu-id="cf647-108">Nelle sezioni seguenti vengono descritti gli attributi, gli elementi figlio e l'elemento padre dell'elemento `TypeName`.</span><span class="sxs-lookup"><span data-stu-id="cf647-108">The following sections describe attributes, child elements, and the parent element of the `TypeName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="cf647-109">Attributi</span><span class="sxs-lookup"><span data-stu-id="cf647-109">Attributes</span></span>

<span data-ttu-id="cf647-110">Nessuna.</span><span class="sxs-lookup"><span data-stu-id="cf647-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="cf647-111">Elementi figlio</span><span class="sxs-lookup"><span data-stu-id="cf647-111">Child Elements</span></span>

<span data-ttu-id="cf647-112">Nessuna.</span><span class="sxs-lookup"><span data-stu-id="cf647-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="cf647-113">Elementi padre</span><span class="sxs-lookup"><span data-stu-id="cf647-113">Parent Elements</span></span>

|<span data-ttu-id="cf647-114">Elemento</span><span class="sxs-lookup"><span data-stu-id="cf647-114">Element</span></span>|<span data-ttu-id="cf647-115">Description</span><span class="sxs-lookup"><span data-stu-id="cf647-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="cf647-116">Elemento EntrySelectedBy per CustomEntry per View (Format)</span><span class="sxs-lookup"><span data-stu-id="cf647-116">EntrySelectedBy Element for CustomEntry for View (Format)</span></span>](./entryselectedby-element-for-customentry-for-customcontrol-for-view-format.md)|<span data-ttu-id="cf647-117">Definisce i tipi .NET che utilizzano questa definizione della vista di controllo personalizzata o la condizione che deve esistere affinché questa definizione venga utilizzata.</span><span class="sxs-lookup"><span data-stu-id="cf647-117">Defines the .NET types that use this custom control view definition or the condition that must exist for this definition to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="cf647-118">Valore testo</span><span class="sxs-lookup"><span data-stu-id="cf647-118">Text Value</span></span>

<span data-ttu-id="cf647-119">Specificare il nome completo del tipo .NET, ad esempio `System.IO.DirectoryInfo`.</span><span class="sxs-lookup"><span data-stu-id="cf647-119">Specify the fully qualified name of the .NET type, such as `System.IO.DirectoryInfo`.</span></span>

## <a name="remarks"></a><span data-ttu-id="cf647-120">Osservazioni</span><span class="sxs-lookup"><span data-stu-id="cf647-120">Remarks</span></span>

<span data-ttu-id="cf647-121">Ogni definizione di visualizzazione controlli personalizzata deve avere almeno un nome di tipo, un set di selezione o una condizione di selezione definita.</span><span class="sxs-lookup"><span data-stu-id="cf647-121">Each custom control view definition must have at least one type name, selection set, or selection condition defined.</span></span>

<span data-ttu-id="cf647-122">Per ulteriori informazioni sui componenti di una visualizzazione controlli personalizzata, vedere [creazione di controlli personalizzati](./creating-custom-controls.md).</span><span class="sxs-lookup"><span data-stu-id="cf647-122">For more information about the components of a custom control view, see [Creating Custom Controls](./creating-custom-controls.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="cf647-123">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="cf647-123">See Also</span></span>

[<span data-ttu-id="cf647-124">Creazione di controlli personalizzati</span><span class="sxs-lookup"><span data-stu-id="cf647-124">Creating Custom Controls</span></span>](./creating-custom-controls.md)

[<span data-ttu-id="cf647-125">Elemento EntrySelectedBy per CustomEntry per View (Format)</span><span class="sxs-lookup"><span data-stu-id="cf647-125">EntrySelectedBy Element for CustomEntry for View (Format)</span></span>](./entryselectedby-element-for-customentry-for-customcontrol-for-view-format.md)

[<span data-ttu-id="cf647-126">Scrittura di un file di formattazione di PowerShell</span><span class="sxs-lookup"><span data-stu-id="cf647-126">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
