---
title: Elemento TypeName per SelectionCondition per GroupBy (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 290d38e3-b9bd-4382-9671-2e28b32b7260
caps.latest.revision: 6
ms.openlocfilehash: a4036b1e9de85da7e0029e02cca9e0eaed462f70
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/05/2019
ms.locfileid: "72361480"
---
# <a name="typename-element-for-selectioncondition-for-groupby-format"></a><span data-ttu-id="7b7e4-102">Elemento TypeName per SelectionCondition per GroupBy (formato)</span><span class="sxs-lookup"><span data-stu-id="7b7e4-102">TypeName Element for SelectionCondition for GroupBy (Format)</span></span>

<span data-ttu-id="7b7e4-103">Specifica un tipo .NET che attiva la condizione.</span><span class="sxs-lookup"><span data-stu-id="7b7e4-103">Specifies a .NET type that triggers the condition.</span></span> <span data-ttu-id="7b7e4-104">Questo elemento viene utilizzato quando si definisce la modalità di visualizzazione di un nuovo gruppo di oggetti.</span><span class="sxs-lookup"><span data-stu-id="7b7e4-104">This element is used when defining how a new group of objects is displayed.</span></span>

<span data-ttu-id="7b7e4-105">Elemento Configuration (Format) elemento ViewDefinitions (Format) elemento View (Format) elemento GroupBy per View (Format) elemento CustomControl per l'elemento GroupBy (Format) CustomEntries per CustomControl per l'elemento GroupBy (Format) CustomEntry per CustomControl per l'elemento EntrySelectedBy di GroupBy (Format) per CustomEntry per l'elemento SelectionCondition di GroupBy (Format) per EntrySelectedBy per la SelectionCondition per l'elemento TypeName (Format) TypeName per per GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="7b7e4-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) GroupBy Element for View (Format) CustomControl Element for GroupBy (Format) CustomEntries Element for CustomControl for GroupBy (Format) CustomEntry Element for CustomControl for GroupBy (Format) EntrySelectedBy Element for CustomEntry for GroupBy (Format) SelectionCondition Element for EntrySelectedBy for GroupBy (Format) TypeName Element for SelectionCondition for GroupBy  (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="7b7e4-106">Sintassi</span><span class="sxs-lookup"><span data-stu-id="7b7e4-106">Syntax</span></span>

```xml
<TypeName>Nameof.NetType</TypeName>

```

## <a name="attributes-and-elements"></a><span data-ttu-id="7b7e4-107">Attributi ed elementi</span><span class="sxs-lookup"><span data-stu-id="7b7e4-107">Attributes and Elements</span></span>

<span data-ttu-id="7b7e4-108">Nelle sezioni seguenti vengono descritti gli attributi, gli elementi figlio e l'elemento padre dell'elemento `TypeName`.</span><span class="sxs-lookup"><span data-stu-id="7b7e4-108">The following sections describe attributes, child elements, and the parent element of the `TypeName` Element.</span></span>

### <a name="attributes"></a><span data-ttu-id="7b7e4-109">Attributi</span><span class="sxs-lookup"><span data-stu-id="7b7e4-109">Attributes</span></span>

<span data-ttu-id="7b7e4-110">Nessuna.</span><span class="sxs-lookup"><span data-stu-id="7b7e4-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="7b7e4-111">Elementi figlio</span><span class="sxs-lookup"><span data-stu-id="7b7e4-111">Child Elements</span></span>

<span data-ttu-id="7b7e4-112">Nessuna.</span><span class="sxs-lookup"><span data-stu-id="7b7e4-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="7b7e4-113">Elementi padre</span><span class="sxs-lookup"><span data-stu-id="7b7e4-113">Parent Elements</span></span>

|<span data-ttu-id="7b7e4-114">Elemento</span><span class="sxs-lookup"><span data-stu-id="7b7e4-114">Element</span></span>|<span data-ttu-id="7b7e4-115">Description</span><span class="sxs-lookup"><span data-stu-id="7b7e4-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="7b7e4-116">Elemento SelectionCondition per EntrySelectedBy per GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="7b7e4-116">SelectionCondition Element for EntrySelectedBy for GroupBy (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-groupby-format.md)|<span data-ttu-id="7b7e4-117">Definisce una condizione che deve esistere per la definizione del controllo da utilizzare.</span><span class="sxs-lookup"><span data-stu-id="7b7e4-117">Defines a condition that must exist for the control definition to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="7b7e4-118">Valore testo</span><span class="sxs-lookup"><span data-stu-id="7b7e4-118">Text Value</span></span>

<span data-ttu-id="7b7e4-119">Specificare il nome completo del tipo .NET, ad esempio `System.IO.DirectoryInfo`.</span><span class="sxs-lookup"><span data-stu-id="7b7e4-119">Specify the fully qualified name of the .NET type, such as `System.IO.DirectoryInfo`.</span></span>

## <a name="remarks"></a><span data-ttu-id="7b7e4-120">Osservazioni</span><span class="sxs-lookup"><span data-stu-id="7b7e4-120">Remarks</span></span>

<span data-ttu-id="7b7e4-121">Quando si specifica questo elemento, non è possibile specificare l'elemento `SelectionSetName`.</span><span class="sxs-lookup"><span data-stu-id="7b7e4-121">When this element is specified, you cannot specify the `SelectionSetName` element.</span></span> <span data-ttu-id="7b7e4-122">Per ulteriori informazioni sulla definizione delle condizioni di selezione, vedere [definizione delle condizioni per la visualizzazione dei dati](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="7b7e4-122">For more information about defining selection conditions, see [Defining Conditions for Displaying Data](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="7b7e4-123">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="7b7e4-123">See Also</span></span>

[<span data-ttu-id="7b7e4-124">Elemento SelectionCondition per EntrySelectedBy per GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="7b7e4-124">SelectionCondition Element for EntrySelectedBy for GroupBy (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-groupby-format.md)

[<span data-ttu-id="7b7e4-125">Scrittura di un file di formattazione di PowerShell</span><span class="sxs-lookup"><span data-stu-id="7b7e4-125">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
