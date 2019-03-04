---
title: Elemento TypeName per SelectionCondition per GroupBy (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 290d38e3-b9bd-4382-9671-2e28b32b7260
caps.latest.revision: 6
ms.openlocfilehash: a4036b1e9de85da7e0029e02cca9e0eaed462f70
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/03/2019
ms.locfileid: "56858807"
---
# <a name="typename-element-for-selectioncondition-for-groupby-format"></a><span data-ttu-id="31840-102">Elemento TypeName per SelectionCondition per GroupBy (formato)</span><span class="sxs-lookup"><span data-stu-id="31840-102">TypeName Element for SelectionCondition for GroupBy (Format)</span></span>

<span data-ttu-id="31840-103">Specifica un tipo .NET che attiva la condizione.</span><span class="sxs-lookup"><span data-stu-id="31840-103">Specifies a .NET type that triggers the condition.</span></span> <span data-ttu-id="31840-104">Questo elemento viene usato quando si definisce come viene visualizzato un nuovo gruppo di oggetti.</span><span class="sxs-lookup"><span data-stu-id="31840-104">This element is used when defining how a new group of objects is displayed.</span></span>

<span data-ttu-id="31840-105">Elemento di GroupBy elemento (formato) per la visualizzazione elemento ViewDefinitions (formato) configurazione elemento (formato) per visualizzazione (formato) CustomControl elemento per elemento CustomEntries GroupBy (formato) per CustomControl per elemento CustomEntry GroupBy (formato) CustomControl per elemento EntrySelectedBy GroupBy (formato) per CustomEntry per elemento SelectionCondition GroupBy (formato) per EntrySelectedBy per elemento TypeName GroupBy (formato) per SelectionCondition per GroupBy (formato)</span><span class="sxs-lookup"><span data-stu-id="31840-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) GroupBy Element for View (Format) CustomControl Element for GroupBy (Format) CustomEntries Element for CustomControl for GroupBy (Format) CustomEntry Element for CustomControl for GroupBy (Format) EntrySelectedBy Element for CustomEntry for GroupBy (Format) SelectionCondition Element for EntrySelectedBy for GroupBy (Format) TypeName Element for SelectionCondition for GroupBy  (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="31840-106">Sintassi</span><span class="sxs-lookup"><span data-stu-id="31840-106">Syntax</span></span>

```xml
<TypeName>Nameof.NetType</TypeName>

```

## <a name="attributes-and-elements"></a><span data-ttu-id="31840-107">Attributi ed elementi</span><span class="sxs-lookup"><span data-stu-id="31840-107">Attributes and Elements</span></span>

<span data-ttu-id="31840-108">Le sezioni seguenti descrivono gli attributi e gli elementi figlio dell'elemento padre del `TypeName` elemento.</span><span class="sxs-lookup"><span data-stu-id="31840-108">The following sections describe attributes, child elements, and the parent element of the `TypeName` Element.</span></span>

### <a name="attributes"></a><span data-ttu-id="31840-109">Attributes</span><span class="sxs-lookup"><span data-stu-id="31840-109">Attributes</span></span>

<span data-ttu-id="31840-110">Nessuna.</span><span class="sxs-lookup"><span data-stu-id="31840-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="31840-111">Elementi figlio</span><span class="sxs-lookup"><span data-stu-id="31840-111">Child Elements</span></span>

<span data-ttu-id="31840-112">Nessuna.</span><span class="sxs-lookup"><span data-stu-id="31840-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="31840-113">Elementi padre</span><span class="sxs-lookup"><span data-stu-id="31840-113">Parent Elements</span></span>

|<span data-ttu-id="31840-114">Elemento</span><span class="sxs-lookup"><span data-stu-id="31840-114">Element</span></span>|<span data-ttu-id="31840-115">Description</span><span class="sxs-lookup"><span data-stu-id="31840-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="31840-116">Elemento SelectionCondition per EntrySelectedBy per GroupBy (formato)</span><span class="sxs-lookup"><span data-stu-id="31840-116">SelectionCondition Element for EntrySelectedBy for GroupBy (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-groupby-format.md)|<span data-ttu-id="31840-117">Definisce una condizione che deve essere presente per la definizione di controllo da utilizzare.</span><span class="sxs-lookup"><span data-stu-id="31840-117">Defines a condition that must exist for the control definition to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="31840-118">Valore di testo</span><span class="sxs-lookup"><span data-stu-id="31840-118">Text Value</span></span>

<span data-ttu-id="31840-119">Specificare il nome completo del tipo .NET, ad esempio `System.IO.DirectoryInfo`.</span><span class="sxs-lookup"><span data-stu-id="31840-119">Specify the fully qualified name of the .NET type, such as `System.IO.DirectoryInfo`.</span></span>

## <a name="remarks"></a><span data-ttu-id="31840-120">Osservazioni</span><span class="sxs-lookup"><span data-stu-id="31840-120">Remarks</span></span>

<span data-ttu-id="31840-121">Quando questo elemento viene specificato, non è possibile specificare il `SelectionSetName` elemento.</span><span class="sxs-lookup"><span data-stu-id="31840-121">When this element is specified, you cannot specify the `SelectionSetName` element.</span></span> <span data-ttu-id="31840-122">Per altre informazioni sulla definizione di condizioni di selezione, vedere [che definisce le condizioni per la visualizzazione dei dati](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="31840-122">For more information about defining selection conditions, see [Defining Conditions for Displaying Data](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="31840-123">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="31840-123">See Also</span></span>

[<span data-ttu-id="31840-124">Elemento SelectionCondition per EntrySelectedBy per GroupBy (formato)</span><span class="sxs-lookup"><span data-stu-id="31840-124">SelectionCondition Element for EntrySelectedBy for GroupBy (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-groupby-format.md)

[<span data-ttu-id="31840-125">La scrittura di un File di formattazione di PowerShell</span><span class="sxs-lookup"><span data-stu-id="31840-125">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
