---
title: Elemento TypeName per SelectionCondition per i controlli per la configurazione (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 477c8711-fffc-4f92-af45-6d4f80990474
caps.latest.revision: 7
ms.openlocfilehash: 60f02f3240c5574e1b1f9027b060bd9af89a11d2
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/15/2019
ms.locfileid: "72361610"
---
# <a name="typename-element-for-selectioncondition-for-controls-for-configuration-format"></a><span data-ttu-id="a4bfe-102">Elemento TypeName per SelectionCondition per Controls per Configuration (formato)</span><span class="sxs-lookup"><span data-stu-id="a4bfe-102">TypeName Element for SelectionCondition for Controls for Configuration (Format)</span></span>

<span data-ttu-id="a4bfe-103">Specifica un tipo .NET che attiva la condizione.</span><span class="sxs-lookup"><span data-stu-id="a4bfe-103">Specifies a .NET type that triggers the condition.</span></span> <span data-ttu-id="a4bfe-104">Questo elemento viene usato quando si definisce un controllo comune che può essere usato da tutte le visualizzazioni nel file di formattazione.</span><span class="sxs-lookup"><span data-stu-id="a4bfe-104">This element is used when defining a common control that can be used by all the views in the formatting file.</span></span>

<span data-ttu-id="a4bfe-105">Elemento di configurazione (Format) controlla l'elemento dell'elemento di controllo Configuration (Format) per i controlli per la configurazione (Format) elemento CustomControl per il controllo per la configurazione (Format) elemento CustomEntries per CustomControl per i controlli per Configuration (Format) elemento CustomEntry per CustomControl per i controlli per la configurazione (Format) elemento EntrySelectedBy per CustomEntry per i controlli per la configurazione (Format) SelectionCondition elemento per EntrySelectedBy per CustomEntry per Configurazione (Format) elemento TypeName per SelectionCondition per i controlli per la configurazione (Format)</span><span class="sxs-lookup"><span data-stu-id="a4bfe-105">Configuration Element (Format) Controls Element of Configuration (Format) Control Element for Controls for Configuration (Format) CustomControl Element for Control for Configuration (Format) CustomEntries Element for CustomControl for Controls for Configuration (Format) CustomEntry Element for CustomControl for Controls for Configuration (Format) EntrySelectedBy Element for CustomEntry for Controls for Configuration (Format) SelectionCondition Element for EntrySelectedBy for CustomEntry for Configuration (Format) TypeName Element for SelectionCondition for Controls for Configuration (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="a4bfe-106">Sintassi</span><span class="sxs-lookup"><span data-stu-id="a4bfe-106">Syntax</span></span>

```xml
<TypeName>Nameof.NetType</TypeName>

```

## <a name="attributes-and-elements"></a><span data-ttu-id="a4bfe-107">Attributi ed elementi</span><span class="sxs-lookup"><span data-stu-id="a4bfe-107">Attributes and Elements</span></span>

<span data-ttu-id="a4bfe-108">Nelle sezioni seguenti vengono descritti gli attributi, gli elementi figlio e l'elemento padre dell'elemento `TypeName`.</span><span class="sxs-lookup"><span data-stu-id="a4bfe-108">The following sections describe attributes, child elements, and the parent element of the `TypeName` Element.</span></span>

### <a name="attributes"></a><span data-ttu-id="a4bfe-109">Attributi</span><span class="sxs-lookup"><span data-stu-id="a4bfe-109">Attributes</span></span>

<span data-ttu-id="a4bfe-110">Nessuna.</span><span class="sxs-lookup"><span data-stu-id="a4bfe-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="a4bfe-111">Elementi figlio</span><span class="sxs-lookup"><span data-stu-id="a4bfe-111">Child Elements</span></span>

<span data-ttu-id="a4bfe-112">Nessuna.</span><span class="sxs-lookup"><span data-stu-id="a4bfe-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="a4bfe-113">Elementi padre</span><span class="sxs-lookup"><span data-stu-id="a4bfe-113">Parent Elements</span></span>

|<span data-ttu-id="a4bfe-114">Elemento</span><span class="sxs-lookup"><span data-stu-id="a4bfe-114">Element</span></span>|<span data-ttu-id="a4bfe-115">Description</span><span class="sxs-lookup"><span data-stu-id="a4bfe-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="a4bfe-116">Elemento SelectionCondition per EntrySelectedBy per CustomEntry per Configuration (Format)</span><span class="sxs-lookup"><span data-stu-id="a4bfe-116">SelectionCondition Element for EntrySelectedBy for CustomEntry for Configuration (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-controls-for-configuration-format.md)|<span data-ttu-id="a4bfe-117">Definisce una condizione che deve esistere per la definizione del controllo da utilizzare.</span><span class="sxs-lookup"><span data-stu-id="a4bfe-117">Defines a condition that must exist for the control definition to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="a4bfe-118">Valore di testo</span><span class="sxs-lookup"><span data-stu-id="a4bfe-118">Text Value</span></span>

<span data-ttu-id="a4bfe-119">Specificare il nome completo del tipo .NET, ad esempio `System.IO.DirectoryInfo`.</span><span class="sxs-lookup"><span data-stu-id="a4bfe-119">Specify the fully qualified name of the .NET type, such as `System.IO.DirectoryInfo`.</span></span>

## <a name="remarks"></a><span data-ttu-id="a4bfe-120">Osservazioni</span><span class="sxs-lookup"><span data-stu-id="a4bfe-120">Remarks</span></span>

## <a name="see-also"></a><span data-ttu-id="a4bfe-121">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="a4bfe-121">See Also</span></span>

[<span data-ttu-id="a4bfe-122">Elemento SelectionCondition per EntrySelectedBy per CustomEntry per Configuration (Format)</span><span class="sxs-lookup"><span data-stu-id="a4bfe-122">SelectionCondition Element for EntrySelectedBy for CustomEntry for Configuration (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-controls-for-configuration-format.md)

[<span data-ttu-id="a4bfe-123">Scrittura di un file di formattazione di PowerShell</span><span class="sxs-lookup"><span data-stu-id="a4bfe-123">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
