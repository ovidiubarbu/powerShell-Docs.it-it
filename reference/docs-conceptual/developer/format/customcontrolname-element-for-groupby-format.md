---
title: Elemento CustomControlName per GroupBy (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 473d9b56-521b-479a-8010-67fe9f040063
caps.latest.revision: 8
ms.openlocfilehash: 3a386eff95044eae573c255a451c5c8b8f16714d
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/05/2019
ms.locfileid: "72368880"
---
# <a name="customcontrolname-element-for-groupby-format"></a><span data-ttu-id="391f3-102">Elemento CustomControlName per GroupBy (formato)</span><span class="sxs-lookup"><span data-stu-id="391f3-102">CustomControlName Element for GroupBy (Format)</span></span>

<span data-ttu-id="391f3-103">Specifica il nome di un controllo personalizzato usato per visualizzare il nuovo gruppo.</span><span class="sxs-lookup"><span data-stu-id="391f3-103">Specifies the name of a custom control that is used to display the new group.</span></span> <span data-ttu-id="391f3-104">Questo elemento viene utilizzato quando si definisce una tabella, un elenco, una visualizzazione di controlli Wide o Custom.</span><span class="sxs-lookup"><span data-stu-id="391f3-104">This element is used when defining a table, list, wide or custom control view.</span></span>

<span data-ttu-id="391f3-105">Elemento Configuration (Format) elemento ViewDefinitions (Format) elemento View (Format) elemento GroupBy per View (Format) elemento CustomControlName di GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="391f3-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) GroupBy Element for View (Format) CustomControlName Element of GroupBy (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="391f3-106">Sintassi</span><span class="sxs-lookup"><span data-stu-id="391f3-106">Syntax</span></span>

```xml
<CustomControlName>ControlName</CustomControlName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="391f3-107">Attributi ed elementi</span><span class="sxs-lookup"><span data-stu-id="391f3-107">Attributes and Elements</span></span>

<span data-ttu-id="391f3-108">Nelle sezioni seguenti vengono descritti gli attributi, gli elementi figlio e gli elementi padre dell'elemento `CustomControlName`.</span><span class="sxs-lookup"><span data-stu-id="391f3-108">The following sections describe the attributes, child elements, and parent elements of the `CustomControlName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="391f3-109">Attributi</span><span class="sxs-lookup"><span data-stu-id="391f3-109">Attributes</span></span>

<span data-ttu-id="391f3-110">Nessuna.</span><span class="sxs-lookup"><span data-stu-id="391f3-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="391f3-111">Elementi figlio</span><span class="sxs-lookup"><span data-stu-id="391f3-111">Child Elements</span></span>

<span data-ttu-id="391f3-112">Nessuna.</span><span class="sxs-lookup"><span data-stu-id="391f3-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="391f3-113">Elementi padre</span><span class="sxs-lookup"><span data-stu-id="391f3-113">Parent Elements</span></span>

|<span data-ttu-id="391f3-114">Elemento</span><span class="sxs-lookup"><span data-stu-id="391f3-114">Element</span></span>|<span data-ttu-id="391f3-115">Description</span><span class="sxs-lookup"><span data-stu-id="391f3-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="391f3-116">Elemento GroupBy per View (Format)</span><span class="sxs-lookup"><span data-stu-id="391f3-116">GroupBy Element for View (Format)</span></span>](./groupby-element-for-view-format.md)|<span data-ttu-id="391f3-117">Definisce la modalità di visualizzazione di un nuovo gruppo di oggetti in Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="391f3-117">Defines how Windows PowerShell displays a new group of objects.</span></span>|

## <a name="text-value"></a><span data-ttu-id="391f3-118">Valore testo</span><span class="sxs-lookup"><span data-stu-id="391f3-118">Text Value</span></span>

<span data-ttu-id="391f3-119">Specificare il nome del controllo personalizzato usato per visualizzare un nuovo gruppo.</span><span class="sxs-lookup"><span data-stu-id="391f3-119">Specify the name of the custom control that is used to display a new group.</span></span>

## <a name="remarks"></a><span data-ttu-id="391f3-120">Osservazioni</span><span class="sxs-lookup"><span data-stu-id="391f3-120">Remarks</span></span>

<span data-ttu-id="391f3-121">È possibile creare controlli comuni che possono essere utilizzati da tutte le visualizzazioni di un file di formattazione ed è possibile creare controlli di visualizzazione che possono essere utilizzati da una visualizzazione specifica.</span><span class="sxs-lookup"><span data-stu-id="391f3-121">You can create common controls that can be used by all the views of a formatting file, and you can create view controls that can be used by a specific view.</span></span> <span data-ttu-id="391f3-122">Gli elementi seguenti specificano i nomi di questi controlli personalizzati:</span><span class="sxs-lookup"><span data-stu-id="391f3-122">The following elements specify the names of these custom controls:</span></span>

- [<span data-ttu-id="391f3-123">Elemento Name per il controllo per i controlli per la configurazione (Format)</span><span class="sxs-lookup"><span data-stu-id="391f3-123">Name Element for Control for Controls for Configuration (Format)</span></span>](./name-element-for-control-for-controls-for-configuration-format.md)

- [<span data-ttu-id="391f3-124">Elemento Name per il controllo per i controlli per la visualizzazione (Format)</span><span class="sxs-lookup"><span data-stu-id="391f3-124">Name Element for Control for Controls for View (Format)</span></span>](./name-element-for-control-for-controls-for-view-format.md)

## <a name="see-also"></a><span data-ttu-id="391f3-125">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="391f3-125">See Also</span></span>

[<span data-ttu-id="391f3-126">Elemento GroupBy per View (Format)</span><span class="sxs-lookup"><span data-stu-id="391f3-126">GroupBy Element for View (Format)</span></span>](./groupby-element-for-view-format.md)

[<span data-ttu-id="391f3-127">Elemento Name per il controllo per i controlli per la configurazione (Format)</span><span class="sxs-lookup"><span data-stu-id="391f3-127">Name Element for Control for Controls for Configuration (Format)</span></span>](./name-element-for-control-for-controls-for-configuration-format.md)

[<span data-ttu-id="391f3-128">Elemento Name per il controllo per i controlli per la visualizzazione (Format)</span><span class="sxs-lookup"><span data-stu-id="391f3-128">Name Element for Control for Controls for View (Format)</span></span>](./name-element-for-control-for-controls-for-view-format.md)

[<span data-ttu-id="391f3-129">Scrittura di un file di formattazione di PowerShell</span><span class="sxs-lookup"><span data-stu-id="391f3-129">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
