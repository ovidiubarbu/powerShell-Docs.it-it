---
title: Elemento CustomEntries per CustomControl per GroupBy (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: af83c0f6-7fdd-4aa0-af12-efc62f632974
caps.latest.revision: 7
ms.openlocfilehash: f073142bf836ae892f161cf8c36ed16c35e311f5
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/05/2019
ms.locfileid: "72364090"
---
# <a name="customentries-element-for-customcontrol-for-groupby-format"></a><span data-ttu-id="7b890-102">Elemento CustomEntries per CustomControl per GroupBy (formato)</span><span class="sxs-lookup"><span data-stu-id="7b890-102">CustomEntries Element for CustomControl for GroupBy (Format)</span></span>

<span data-ttu-id="7b890-103">Fornisce le definizioni per il controllo.</span><span class="sxs-lookup"><span data-stu-id="7b890-103">Provides the definitions for the control.</span></span> <span data-ttu-id="7b890-104">Questo elemento viene utilizzato quando si definisce la modalità di visualizzazione di un nuovo gruppo di oggetti.</span><span class="sxs-lookup"><span data-stu-id="7b890-104">This element is used when defining how a new group of objects is displayed.</span></span>

<span data-ttu-id="7b890-105">Elemento Configuration (Format) elemento ViewDefinitions (Format) elemento View (Format) elemento GroupBy per View (Format) elemento CustomControl per GroupBy (Format) elemento CustomEntries per CustomControl per GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="7b890-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) GroupBy Element for View (Format) CustomControl Element for GroupBy (Format) CustomEntries Element for CustomControl for GroupBy (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="7b890-106">Sintassi</span><span class="sxs-lookup"><span data-stu-id="7b890-106">Syntax</span></span>

```xml
<CustomEntries>
  <CustomEntry>...</CustomEntry>
</CustomEntries>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="7b890-107">Attributi ed elementi</span><span class="sxs-lookup"><span data-stu-id="7b890-107">Attributes and Elements</span></span>

<span data-ttu-id="7b890-108">Nelle sezioni seguenti vengono descritti gli attributi, gli elementi figlio e gli elementi padre dell'elemento `CustomEntries`.</span><span class="sxs-lookup"><span data-stu-id="7b890-108">The following sections describe attributes, child elements, and parent elements of the `CustomEntries` element.</span></span> <span data-ttu-id="7b890-109">Non esiste un limite massimo per il numero di elementi figlio che è possibile specificare.</span><span class="sxs-lookup"><span data-stu-id="7b890-109">There is no maximum limit to the number of child elements that can be specified.</span></span>

### <a name="attributes"></a><span data-ttu-id="7b890-110">Attributi</span><span class="sxs-lookup"><span data-stu-id="7b890-110">Attributes</span></span>

<span data-ttu-id="7b890-111">Nessuna.</span><span class="sxs-lookup"><span data-stu-id="7b890-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="7b890-112">Elementi figlio</span><span class="sxs-lookup"><span data-stu-id="7b890-112">Child Elements</span></span>

|<span data-ttu-id="7b890-113">Elemento</span><span class="sxs-lookup"><span data-stu-id="7b890-113">Element</span></span>|<span data-ttu-id="7b890-114">Description</span><span class="sxs-lookup"><span data-stu-id="7b890-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="7b890-115">Elemento CustomEntry per CustomControl per GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="7b890-115">CustomEntry Element for CustomControl for GroupBy (Format)</span></span>](./customentry-element-for-customcontrol-for-groupby-format.md)|<span data-ttu-id="7b890-116">Elemento obbligatorio.</span><span class="sxs-lookup"><span data-stu-id="7b890-116">Required element.</span></span><br /><br /> <span data-ttu-id="7b890-117">Fornisce una definizione del controllo.</span><span class="sxs-lookup"><span data-stu-id="7b890-117">Provides a definition of the control.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="7b890-118">Elementi padre</span><span class="sxs-lookup"><span data-stu-id="7b890-118">Parent Elements</span></span>

|<span data-ttu-id="7b890-119">Elemento</span><span class="sxs-lookup"><span data-stu-id="7b890-119">Element</span></span>|<span data-ttu-id="7b890-120">Description</span><span class="sxs-lookup"><span data-stu-id="7b890-120">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="7b890-121">Elemento CustomControl per GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="7b890-121">CustomControl Element for GroupBy (Format)</span></span>](./customcontrol-element-for-groupby-format.md)|<span data-ttu-id="7b890-122">Definisce il controllo personalizzato che Visualizza il nuovo gruppo.</span><span class="sxs-lookup"><span data-stu-id="7b890-122">Defines the custom control that displays the new group.</span></span>|

## <a name="remarks"></a><span data-ttu-id="7b890-123">Osservazioni</span><span class="sxs-lookup"><span data-stu-id="7b890-123">Remarks</span></span>

<span data-ttu-id="7b890-124">Nella maggior parte dei casi, un controllo ha una sola definizione, specificata in un singolo elemento `CustomEntry`.</span><span class="sxs-lookup"><span data-stu-id="7b890-124">In most cases, a control has only one definition, which is specified in a single `CustomEntry` element.</span></span> <span data-ttu-id="7b890-125">Tuttavia, se si desidera utilizzare lo stesso controllo per visualizzare gruppi diversi, è possibile specificare più definizioni.</span><span class="sxs-lookup"><span data-stu-id="7b890-125">However, it is possible to provide multiple definitions if you want to use the same control to display different groups.</span></span> <span data-ttu-id="7b890-126">In questi casi, è possibile definire un elemento `CustomEntry` per un gruppo.</span><span class="sxs-lookup"><span data-stu-id="7b890-126">In those cases, you can define a `CustomEntry` element for a group.</span></span>

## <a name="see-also"></a><span data-ttu-id="7b890-127">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="7b890-127">See Also</span></span>

[<span data-ttu-id="7b890-128">Elemento CustomEntry per CustomEntries per i controlli per la visualizzazione (Format)</span><span class="sxs-lookup"><span data-stu-id="7b890-128">CustomEntry Element for CustomEntries for Controls for View (Format)</span></span>](./customentry-element-for-customentries-for-controls-for-view-format.md)

[<span data-ttu-id="7b890-129">Elemento CustomControl per GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="7b890-129">CustomControl Element for GroupBy (Format)</span></span>](./customcontrol-element-for-groupby-format.md)

[<span data-ttu-id="7b890-130">Scrittura di un file di formattazione di PowerShell</span><span class="sxs-lookup"><span data-stu-id="7b890-130">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
