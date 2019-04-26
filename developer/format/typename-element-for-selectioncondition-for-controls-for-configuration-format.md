---
title: Elemento TypeName per SelectionCondition per i controlli per la configurazione (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 477c8711-fffc-4f92-af45-6d4f80990474
caps.latest.revision: 7
ms.openlocfilehash: 60f02f3240c5574e1b1f9027b060bd9af89a11d2
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62083944"
---
# <a name="typename-element-for-selectioncondition-for-controls-for-configuration-format"></a><span data-ttu-id="0921a-102">Elemento TypeName per SelectionCondition per Controls per Configuration (formato)</span><span class="sxs-lookup"><span data-stu-id="0921a-102">TypeName Element for SelectionCondition for Controls for Configuration (Format)</span></span>

<span data-ttu-id="0921a-103">Specifica un tipo .NET che attiva la condizione.</span><span class="sxs-lookup"><span data-stu-id="0921a-103">Specifies a .NET type that triggers the condition.</span></span> <span data-ttu-id="0921a-104">Questo elemento viene usato quando si definisce un controllo comune che può essere usato da tutte le visualizzazioni nel file di formattazione.</span><span class="sxs-lookup"><span data-stu-id="0921a-104">This element is used when defining a common control that can be used by all the views in the formatting file.</span></span>

<span data-ttu-id="0921a-105">Configurazione (formato) i controlli elemento dell'elemento di controllo di configurazione (formato) per i controlli per Configuration (formato) CustomControl elemento per elemento Configuration (formato) CustomEntries CustomControl dei controlli per il controllo Elemento CustomEntry di configurazione (formato) per CustomControl per i controlli per elemento di configurazione (formato) EntrySelectedBy per CustomEntry per i controlli per elemento di configurazione (formato) SelectionCondition per EntrySelectedBy per CustomEntry per Elemento TypeName di configurazione (formato) per SelectionCondition per i controlli per la configurazione (formato)</span><span class="sxs-lookup"><span data-stu-id="0921a-105">Configuration Element (Format) Controls Element of Configuration (Format) Control Element for Controls for Configuration (Format) CustomControl Element for Control for Configuration (Format) CustomEntries Element for CustomControl for Controls for Configuration (Format) CustomEntry Element for CustomControl for Controls for Configuration (Format) EntrySelectedBy Element for CustomEntry for Controls for Configuration (Format) SelectionCondition Element for EntrySelectedBy for CustomEntry for Configuration (Format) TypeName Element for SelectionCondition for Controls for Configuration (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="0921a-106">Sintassi</span><span class="sxs-lookup"><span data-stu-id="0921a-106">Syntax</span></span>

```xml
<TypeName>Nameof.NetType</TypeName>

```

## <a name="attributes-and-elements"></a><span data-ttu-id="0921a-107">Elementi e attributi</span><span class="sxs-lookup"><span data-stu-id="0921a-107">Attributes and Elements</span></span>

<span data-ttu-id="0921a-108">Le sezioni seguenti descrivono gli attributi e gli elementi figlio dell'elemento padre del `TypeName` elemento.</span><span class="sxs-lookup"><span data-stu-id="0921a-108">The following sections describe attributes, child elements, and the parent element of the `TypeName` Element.</span></span>

### <a name="attributes"></a><span data-ttu-id="0921a-109">Attributes</span><span class="sxs-lookup"><span data-stu-id="0921a-109">Attributes</span></span>

<span data-ttu-id="0921a-110">Nessuna.</span><span class="sxs-lookup"><span data-stu-id="0921a-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="0921a-111">Elementi figlio</span><span class="sxs-lookup"><span data-stu-id="0921a-111">Child Elements</span></span>

<span data-ttu-id="0921a-112">Nessuna.</span><span class="sxs-lookup"><span data-stu-id="0921a-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="0921a-113">Elementi padre</span><span class="sxs-lookup"><span data-stu-id="0921a-113">Parent Elements</span></span>

|<span data-ttu-id="0921a-114">Elemento</span><span class="sxs-lookup"><span data-stu-id="0921a-114">Element</span></span>|<span data-ttu-id="0921a-115">Description</span><span class="sxs-lookup"><span data-stu-id="0921a-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="0921a-116">Elemento SelectionCondition per EntrySelectedBy per CustomEntry per la configurazione (formato)</span><span class="sxs-lookup"><span data-stu-id="0921a-116">SelectionCondition Element for EntrySelectedBy for CustomEntry for Configuration (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-controls-for-configuration-format.md)|<span data-ttu-id="0921a-117">Definisce una condizione che deve essere presente per la definizione di controllo da utilizzare.</span><span class="sxs-lookup"><span data-stu-id="0921a-117">Defines a condition that must exist for the control definition to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="0921a-118">Valore di testo</span><span class="sxs-lookup"><span data-stu-id="0921a-118">Text Value</span></span>

<span data-ttu-id="0921a-119">Specificare il nome completo del tipo .NET, ad esempio `System.IO.DirectoryInfo`.</span><span class="sxs-lookup"><span data-stu-id="0921a-119">Specify the fully qualified name of the .NET type, such as `System.IO.DirectoryInfo`.</span></span>

## <a name="remarks"></a><span data-ttu-id="0921a-120">Osservazioni</span><span class="sxs-lookup"><span data-stu-id="0921a-120">Remarks</span></span>

## <a name="see-also"></a><span data-ttu-id="0921a-121">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="0921a-121">See Also</span></span>

[<span data-ttu-id="0921a-122">Elemento SelectionCondition per EntrySelectedBy per CustomEntry per la configurazione (formato)</span><span class="sxs-lookup"><span data-stu-id="0921a-122">SelectionCondition Element for EntrySelectedBy for CustomEntry for Configuration (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-controls-for-configuration-format.md)

[<span data-ttu-id="0921a-123">La scrittura di un File di formattazione di PowerShell</span><span class="sxs-lookup"><span data-stu-id="0921a-123">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
