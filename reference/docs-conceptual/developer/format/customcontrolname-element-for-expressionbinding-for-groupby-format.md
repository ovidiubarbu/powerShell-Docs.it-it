---
title: Elemento CustomControlName per ExpressionName per GroupBy (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 9e11da8f-1e75-4d3d-b4c8-b500dec3028e
caps.latest.revision: 6
ms.openlocfilehash: 32f8a71e9818c8c1a052f3b96f442f169c1bda4a
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/05/2019
ms.locfileid: "72368910"
---
# <a name="customcontrolname-element-for-expressionbinding-for-groupby-format"></a><span data-ttu-id="263e9-102">Elemento CustomControlName per ExpressionBinding per GroupBy (formato)</span><span class="sxs-lookup"><span data-stu-id="263e9-102">CustomControlName Element for ExpressionBinding for GroupBy (Format)</span></span>

<span data-ttu-id="263e9-103">Specifica il nome di un controllo comune o di un controllo di visualizzazione.</span><span class="sxs-lookup"><span data-stu-id="263e9-103">Specifies the name of a common control or a view control.</span></span> <span data-ttu-id="263e9-104">Questo elemento viene utilizzato quando si definisce la modalità di visualizzazione di un nuovo gruppo di oggetti.</span><span class="sxs-lookup"><span data-stu-id="263e9-104">This element is used when defining how a new group of objects is displayed.</span></span>

<span data-ttu-id="263e9-105">Elemento Configuration (Format) elemento ViewDefinitions (Format) elemento View (Format) elemento GroupBy per View (Format) elemento CustomControl per l'elemento GroupBy (Format) CustomEntries per CustomControl per l'elemento GroupBy (Format) CustomEntry per CustomControl per GroupBy (Format) elemento CustomItem per CustomEntry per l'elemento di espressione GroupBy (Format) per CustomItem per l'elemento GroupBy (Format) CustomControlName per Expression per GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="263e9-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) GroupBy Element for View (Format) CustomControl Element for GroupBy (Format) CustomEntries Element for CustomControl for GroupBy (Format) CustomEntry Element for CustomControl for GroupBy (Format) CustomItem Element for CustomEntry for GroupBy (Format) ExpressionBinding Element for CustomItem for GroupBy (Format) CustomControlName Element for ExpressionBinding for GroupBy (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="263e9-106">Sintassi</span><span class="sxs-lookup"><span data-stu-id="263e9-106">Syntax</span></span>

```xml
<CustomControlName>NameofCustomControl</CustomControlName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="263e9-107">Attributi ed elementi</span><span class="sxs-lookup"><span data-stu-id="263e9-107">Attributes and Elements</span></span>

<span data-ttu-id="263e9-108">Nelle sezioni seguenti vengono descritti gli attributi, gli elementi figlio e l'elemento padre dell'elemento `CustomControlName`.</span><span class="sxs-lookup"><span data-stu-id="263e9-108">The following sections describe attributes, child elements, and the parent element of the `CustomControlName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="263e9-109">Attributi</span><span class="sxs-lookup"><span data-stu-id="263e9-109">Attributes</span></span>

<span data-ttu-id="263e9-110">Nessuna.</span><span class="sxs-lookup"><span data-stu-id="263e9-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="263e9-111">Elementi figlio</span><span class="sxs-lookup"><span data-stu-id="263e9-111">Child Elements</span></span>

<span data-ttu-id="263e9-112">Nessuna.</span><span class="sxs-lookup"><span data-stu-id="263e9-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="263e9-113">Elementi padre</span><span class="sxs-lookup"><span data-stu-id="263e9-113">Parent Elements</span></span>

|<span data-ttu-id="263e9-114">Elemento</span><span class="sxs-lookup"><span data-stu-id="263e9-114">Element</span></span>|<span data-ttu-id="263e9-115">Description</span><span class="sxs-lookup"><span data-stu-id="263e9-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="263e9-116">Elemento expressiongroup per CustomItem per GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="263e9-116">ExpressionBinding Element for CustomItem for GroupBy (Format)</span></span>](./expressionbinding-element-for-customitem-for-groupby-format.md)|<span data-ttu-id="263e9-117">Definisce i dati visualizzati dal controllo.</span><span class="sxs-lookup"><span data-stu-id="263e9-117">Defines the data that is displayed by the control.</span></span>|

## <a name="text-value"></a><span data-ttu-id="263e9-118">Valore testo</span><span class="sxs-lookup"><span data-stu-id="263e9-118">Text Value</span></span>

<span data-ttu-id="263e9-119">Specificare il nome del controllo.</span><span class="sxs-lookup"><span data-stu-id="263e9-119">Specify the name of the control.</span></span>

## <a name="remarks"></a><span data-ttu-id="263e9-120">Osservazioni</span><span class="sxs-lookup"><span data-stu-id="263e9-120">Remarks</span></span>

<span data-ttu-id="263e9-121">È possibile creare controlli comuni che possono essere utilizzati da tutte le visualizzazioni di un file di formattazione ed è possibile creare controlli di visualizzazione che possono essere utilizzati da una visualizzazione specifica.</span><span class="sxs-lookup"><span data-stu-id="263e9-121">You can create common controls that can be used by all the views of a formatting file, and you can create view controls that can be used by a specific view.</span></span> <span data-ttu-id="263e9-122">Gli elementi seguenti specificano i nomi di questi controlli:</span><span class="sxs-lookup"><span data-stu-id="263e9-122">The following elements specify the names of these controls:</span></span>

- [<span data-ttu-id="263e9-123">Elemento Name per il controllo per i controlli per la configurazione (Format)</span><span class="sxs-lookup"><span data-stu-id="263e9-123">Name Element for Control for Controls for Configuration (Format)</span></span>](./name-element-for-control-for-controls-for-configuration-format.md)

- [<span data-ttu-id="263e9-124">Elemento Name per il controllo per i controlli per la visualizzazione (Format)</span><span class="sxs-lookup"><span data-stu-id="263e9-124">Name Element for Control for Controls for View (Format)</span></span>](./name-element-for-control-for-controls-for-view-format.md)

## <a name="see-also"></a><span data-ttu-id="263e9-125">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="263e9-125">See Also</span></span>

[<span data-ttu-id="263e9-126">Elemento Name per il controllo per i controlli per la configurazione (Format)</span><span class="sxs-lookup"><span data-stu-id="263e9-126">Name Element for Control for Controls for Configuration (Format)</span></span>](./name-element-for-control-for-controls-for-configuration-format.md)

[<span data-ttu-id="263e9-127">Elemento Name per il controllo per i controlli per la visualizzazione (Format)</span><span class="sxs-lookup"><span data-stu-id="263e9-127">Name Element for Control for Controls for View (Format)</span></span>](./name-element-for-control-for-controls-for-view-format.md)

[<span data-ttu-id="263e9-128">Elemento expressiongroup per CustomItem per GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="263e9-128">ExpressionBinding Element for CustomItem for GroupBy (Format)</span></span>](./expressionbinding-element-for-customitem-for-groupby-format.md)

[<span data-ttu-id="263e9-129">Scrittura di un file di formattazione di PowerShell</span><span class="sxs-lookup"><span data-stu-id="263e9-129">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
