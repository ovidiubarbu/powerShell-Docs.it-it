---
title: Elemento CustomControlName per GroupBy (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 473d9b56-521b-479a-8010-67fe9f040063
caps.latest.revision: 8
ms.openlocfilehash: 3a386eff95044eae573c255a451c5c8b8f16714d
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/03/2019
ms.locfileid: "56860307"
---
# <a name="customcontrolname-element-for-groupby-format"></a><span data-ttu-id="5de31-102">Elemento CustomControlName per GroupBy (formato)</span><span class="sxs-lookup"><span data-stu-id="5de31-102">CustomControlName Element for GroupBy (Format)</span></span>

<span data-ttu-id="5de31-103">Specifica il nome di un controllo personalizzato che consente di visualizzare il nuovo gruppo.</span><span class="sxs-lookup"><span data-stu-id="5de31-103">Specifies the name of a custom control that is used to display the new group.</span></span> <span data-ttu-id="5de31-104">Questo elemento viene usato quando si definisce una tabella, elenco, visualizzazione controllo wide o personalizzato.</span><span class="sxs-lookup"><span data-stu-id="5de31-104">This element is used when defining a table, list, wide or custom control view.</span></span>

<span data-ttu-id="5de31-105">Elemento di GroupBy elemento (formato) per la visualizzazione elemento ViewDefinitions (formato) configurazione elemento (formato) elemento di visualizzazione (formato) CustomControlName di GroupBy (formato)</span><span class="sxs-lookup"><span data-stu-id="5de31-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) GroupBy Element for View (Format) CustomControlName Element of GroupBy (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="5de31-106">Sintassi</span><span class="sxs-lookup"><span data-stu-id="5de31-106">Syntax</span></span>

```xml
<CustomControlName>ControlName</CustomControlName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="5de31-107">Attributi ed elementi</span><span class="sxs-lookup"><span data-stu-id="5de31-107">Attributes and Elements</span></span>

<span data-ttu-id="5de31-108">Le sezioni seguenti descrivono gli attributi, elementi figlio e gli elementi padre del `CustomControlName` elemento.</span><span class="sxs-lookup"><span data-stu-id="5de31-108">The following sections describe the attributes, child elements, and parent elements of the `CustomControlName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="5de31-109">Attributes</span><span class="sxs-lookup"><span data-stu-id="5de31-109">Attributes</span></span>

<span data-ttu-id="5de31-110">Nessuna.</span><span class="sxs-lookup"><span data-stu-id="5de31-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="5de31-111">Elementi figlio</span><span class="sxs-lookup"><span data-stu-id="5de31-111">Child Elements</span></span>

<span data-ttu-id="5de31-112">Nessuna.</span><span class="sxs-lookup"><span data-stu-id="5de31-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="5de31-113">Elementi padre</span><span class="sxs-lookup"><span data-stu-id="5de31-113">Parent Elements</span></span>

|<span data-ttu-id="5de31-114">Elemento</span><span class="sxs-lookup"><span data-stu-id="5de31-114">Element</span></span>|<span data-ttu-id="5de31-115">Description</span><span class="sxs-lookup"><span data-stu-id="5de31-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="5de31-116">Elemento GroupBy per visualizzazione (formato)</span><span class="sxs-lookup"><span data-stu-id="5de31-116">GroupBy Element for View (Format)</span></span>](./groupby-element-for-view-format.md)|<span data-ttu-id="5de31-117">Definisce la modalità di visualizzazione di un nuovo gruppo di oggetti Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="5de31-117">Defines how Windows PowerShell displays a new group of objects.</span></span>|

## <a name="text-value"></a><span data-ttu-id="5de31-118">Valore di testo</span><span class="sxs-lookup"><span data-stu-id="5de31-118">Text Value</span></span>

<span data-ttu-id="5de31-119">Specificare il nome del controllo personalizzato che consente di visualizzare un nuovo gruppo.</span><span class="sxs-lookup"><span data-stu-id="5de31-119">Specify the name of the custom control that is used to display a new group.</span></span>

## <a name="remarks"></a><span data-ttu-id="5de31-120">Osservazioni</span><span class="sxs-lookup"><span data-stu-id="5de31-120">Remarks</span></span>

<span data-ttu-id="5de31-121">È possibile creare controlli comuni che possono essere usati da tutte le visualizzazioni di un file di formattazione ed è possibile creare controlli di visualizzazione che possono essere usati da una visualizzazione specifica.</span><span class="sxs-lookup"><span data-stu-id="5de31-121">You can create common controls that can be used by all the views of a formatting file, and you can create view controls that can be used by a specific view.</span></span> <span data-ttu-id="5de31-122">Gli elementi seguenti specificano i nomi di questi controlli personalizzati:</span><span class="sxs-lookup"><span data-stu-id="5de31-122">The following elements specify the names of these custom controls:</span></span>

- [<span data-ttu-id="5de31-123">Elemento Name per il controllo per i controlli per la configurazione (formato)</span><span class="sxs-lookup"><span data-stu-id="5de31-123">Name Element for Control for Controls for Configuration (Format)</span></span>](./name-element-for-control-for-controls-for-configuration-format.md)

- [<span data-ttu-id="5de31-124">Elemento Name per il controllo per i controlli per la visualizzazione (formato)</span><span class="sxs-lookup"><span data-stu-id="5de31-124">Name Element for Control for Controls for View (Format)</span></span>](./name-element-for-control-for-controls-for-view-format.md)

## <a name="see-also"></a><span data-ttu-id="5de31-125">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="5de31-125">See Also</span></span>

[<span data-ttu-id="5de31-126">Elemento GroupBy per visualizzazione (formato)</span><span class="sxs-lookup"><span data-stu-id="5de31-126">GroupBy Element for View (Format)</span></span>](./groupby-element-for-view-format.md)

[<span data-ttu-id="5de31-127">Elemento Name per il controllo per i controlli per la configurazione (formato)</span><span class="sxs-lookup"><span data-stu-id="5de31-127">Name Element for Control for Controls for Configuration (Format)</span></span>](./name-element-for-control-for-controls-for-configuration-format.md)

[<span data-ttu-id="5de31-128">Elemento Name per il controllo per i controlli per la visualizzazione (formato)</span><span class="sxs-lookup"><span data-stu-id="5de31-128">Name Element for Control for Controls for View (Format)</span></span>](./name-element-for-control-for-controls-for-view-format.md)

[<span data-ttu-id="5de31-129">La scrittura di un File di formattazione di PowerShell</span><span class="sxs-lookup"><span data-stu-id="5de31-129">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
