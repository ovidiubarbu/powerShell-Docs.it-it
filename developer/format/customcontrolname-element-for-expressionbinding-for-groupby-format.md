---
title: Elemento CustomControlName per ExpressionBinding per GroupBy (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 9e11da8f-1e75-4d3d-b4c8-b500dec3028e
caps.latest.revision: 6
ms.openlocfilehash: 32f8a71e9818c8c1a052f3b96f442f169c1bda4a
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62066569"
---
# <a name="customcontrolname-element-for-expressionbinding-for-groupby-format"></a><span data-ttu-id="1c3f1-102">Elemento CustomControlName per ExpressionBinding per GroupBy (formato)</span><span class="sxs-lookup"><span data-stu-id="1c3f1-102">CustomControlName Element for ExpressionBinding for GroupBy (Format)</span></span>

<span data-ttu-id="1c3f1-103">Specifica il nome di un controllo comune o un controllo di visualizzazione.</span><span class="sxs-lookup"><span data-stu-id="1c3f1-103">Specifies the name of a common control or a view control.</span></span> <span data-ttu-id="1c3f1-104">Questo elemento viene usato quando si definisce come viene visualizzato un nuovo gruppo di oggetti.</span><span class="sxs-lookup"><span data-stu-id="1c3f1-104">This element is used when defining how a new group of objects is displayed.</span></span>

<span data-ttu-id="1c3f1-105">Elemento di GroupBy elemento (formato) per la visualizzazione elemento ViewDefinitions (formato) configurazione elemento (formato) per visualizzazione (formato) CustomControl elemento per elemento CustomEntries GroupBy (formato) per CustomControl per elemento CustomEntry GroupBy (formato) CustomControl per elemento CustomItem GroupBy (formato) per CustomEntry per elemento ExpressionBinding GroupBy (formato) per CustomItem per elemento CustomControlName GroupBy (formato) per ExpressionBinding per GroupBy (formato)</span><span class="sxs-lookup"><span data-stu-id="1c3f1-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) GroupBy Element for View (Format) CustomControl Element for GroupBy (Format) CustomEntries Element for CustomControl for GroupBy (Format) CustomEntry Element for CustomControl for GroupBy (Format) CustomItem Element for CustomEntry for GroupBy (Format) ExpressionBinding Element for CustomItem for GroupBy (Format) CustomControlName Element for ExpressionBinding for GroupBy (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="1c3f1-106">Sintassi</span><span class="sxs-lookup"><span data-stu-id="1c3f1-106">Syntax</span></span>

```xml
<CustomControlName>NameofCustomControl</CustomControlName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="1c3f1-107">Elementi e attributi</span><span class="sxs-lookup"><span data-stu-id="1c3f1-107">Attributes and Elements</span></span>

<span data-ttu-id="1c3f1-108">Le sezioni seguenti descrivono gli attributi e gli elementi figlio dell'elemento padre del `CustomControlName` elemento.</span><span class="sxs-lookup"><span data-stu-id="1c3f1-108">The following sections describe attributes, child elements, and the parent element of the `CustomControlName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="1c3f1-109">Attributes</span><span class="sxs-lookup"><span data-stu-id="1c3f1-109">Attributes</span></span>

<span data-ttu-id="1c3f1-110">Nessuna.</span><span class="sxs-lookup"><span data-stu-id="1c3f1-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="1c3f1-111">Elementi figlio</span><span class="sxs-lookup"><span data-stu-id="1c3f1-111">Child Elements</span></span>

<span data-ttu-id="1c3f1-112">Nessuna.</span><span class="sxs-lookup"><span data-stu-id="1c3f1-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="1c3f1-113">Elementi padre</span><span class="sxs-lookup"><span data-stu-id="1c3f1-113">Parent Elements</span></span>

|<span data-ttu-id="1c3f1-114">Elemento</span><span class="sxs-lookup"><span data-stu-id="1c3f1-114">Element</span></span>|<span data-ttu-id="1c3f1-115">Description</span><span class="sxs-lookup"><span data-stu-id="1c3f1-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="1c3f1-116">Elemento ExpressionBinding per CustomItem per GroupBy (formato)</span><span class="sxs-lookup"><span data-stu-id="1c3f1-116">ExpressionBinding Element for CustomItem for GroupBy (Format)</span></span>](./expressionbinding-element-for-customitem-for-groupby-format.md)|<span data-ttu-id="1c3f1-117">Definisce i dati che vengano visualizzati dal controllo.</span><span class="sxs-lookup"><span data-stu-id="1c3f1-117">Defines the data that is displayed by the control.</span></span>|

## <a name="text-value"></a><span data-ttu-id="1c3f1-118">Valore di testo</span><span class="sxs-lookup"><span data-stu-id="1c3f1-118">Text Value</span></span>

<span data-ttu-id="1c3f1-119">Specificare il nome del controllo.</span><span class="sxs-lookup"><span data-stu-id="1c3f1-119">Specify the name of the control.</span></span>

## <a name="remarks"></a><span data-ttu-id="1c3f1-120">Osservazioni</span><span class="sxs-lookup"><span data-stu-id="1c3f1-120">Remarks</span></span>

<span data-ttu-id="1c3f1-121">È possibile creare controlli comuni che possono essere usati da tutte le visualizzazioni di un file di formattazione ed è possibile creare controlli di visualizzazione che possono essere usati da una visualizzazione specifica.</span><span class="sxs-lookup"><span data-stu-id="1c3f1-121">You can create common controls that can be used by all the views of a formatting file, and you can create view controls that can be used by a specific view.</span></span> <span data-ttu-id="1c3f1-122">Gli elementi seguenti specificano i nomi di questi controlli:</span><span class="sxs-lookup"><span data-stu-id="1c3f1-122">The following elements specify the names of these controls:</span></span>

- [<span data-ttu-id="1c3f1-123">Elemento Name per il controllo per i controlli per la configurazione (formato)</span><span class="sxs-lookup"><span data-stu-id="1c3f1-123">Name Element for Control for Controls for Configuration (Format)</span></span>](./name-element-for-control-for-controls-for-configuration-format.md)

- [<span data-ttu-id="1c3f1-124">Elemento Name per il controllo per i controlli per la visualizzazione (formato)</span><span class="sxs-lookup"><span data-stu-id="1c3f1-124">Name Element for Control for Controls for View (Format)</span></span>](./name-element-for-control-for-controls-for-view-format.md)

## <a name="see-also"></a><span data-ttu-id="1c3f1-125">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="1c3f1-125">See Also</span></span>

[<span data-ttu-id="1c3f1-126">Elemento Name per il controllo per i controlli per la configurazione (formato)</span><span class="sxs-lookup"><span data-stu-id="1c3f1-126">Name Element for Control for Controls for Configuration (Format)</span></span>](./name-element-for-control-for-controls-for-configuration-format.md)

[<span data-ttu-id="1c3f1-127">Elemento Name per il controllo per i controlli per la visualizzazione (formato)</span><span class="sxs-lookup"><span data-stu-id="1c3f1-127">Name Element for Control for Controls for View (Format)</span></span>](./name-element-for-control-for-controls-for-view-format.md)

[<span data-ttu-id="1c3f1-128">Elemento ExpressionBinding per CustomItem per GroupBy (formato)</span><span class="sxs-lookup"><span data-stu-id="1c3f1-128">ExpressionBinding Element for CustomItem for GroupBy (Format)</span></span>](./expressionbinding-element-for-customitem-for-groupby-format.md)

[<span data-ttu-id="1c3f1-129">La scrittura di un File di formattazione di PowerShell</span><span class="sxs-lookup"><span data-stu-id="1c3f1-129">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
