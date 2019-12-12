---
title: Elemento CustomControlName per Expressiongroup per i controlli per la visualizzazione (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 4b6ee11e-9086-41d2-afd3-42fb9f24da69
caps.latest.revision: 7
ms.openlocfilehash: bf1d57447f9018f1535af14466427aaeabc048f3
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/05/2019
ms.locfileid: "72369150"
---
# <a name="customcontrolname-element-for-expressionbinding-for-controls-for-view-format"></a><span data-ttu-id="ab478-102">Elemento CustomControlName per ExpressionBinding per Controls per View (formato)</span><span class="sxs-lookup"><span data-stu-id="ab478-102">CustomControlName Element for ExpressionBinding for Controls for View (Format)</span></span>

<span data-ttu-id="ab478-103">Specifica il nome di un controllo comune o di un controllo di visualizzazione.</span><span class="sxs-lookup"><span data-stu-id="ab478-103">Specifies the name of a common control or a view control.</span></span> <span data-ttu-id="ab478-104">Questo elemento viene utilizzato per la definizione di controlli che possono essere utilizzati da una visualizzazione.</span><span class="sxs-lookup"><span data-stu-id="ab478-104">This element is used when defining controls that can be used by a view.</span></span>

<span data-ttu-id="ab478-105">Elemento di configurazione (Format) elemento ViewDefinitions (Format) elemento di visualizzazione (Format) controlli elemento (Format) elemento di controllo per i controlli per la visualizzazione (formato) elemento CustomControl per il controllo per i controlli per la visualizzazione (formato) elemento CustomEntries per CustomControl per la visualizzazione (Format) elemento CustomEntry per CustomEntries per i controlli per la visualizzazione (formato) elemento CustomItem per CustomEntry per i controlli per la visualizzazione (formato) elemento Expressiongroup per CustomItem per i controlli per la visualizzazione (Format) CustomControlName Elemento per ExpressionBindine per i controlli per la visualizzazione (Format)</span><span class="sxs-lookup"><span data-stu-id="ab478-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) Controls Element (Format) Control Element for Controls for View (Format) CustomControl Element for Control for Controls for View (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for Controls for View (Format) CustomItem Element for CustomEntry for Controls for View (Format) ExpressionBinding Element for CustomItem for Controls for View (Format) CustomControlName Element for ExpressionBindine for Controls for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="ab478-106">Sintassi</span><span class="sxs-lookup"><span data-stu-id="ab478-106">Syntax</span></span>

```xml
<CustomControlName>NameofCustomControl</CustomControlName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="ab478-107">Attributi ed elementi</span><span class="sxs-lookup"><span data-stu-id="ab478-107">Attributes and Elements</span></span>

<span data-ttu-id="ab478-108">Nelle sezioni seguenti vengono descritti gli attributi, gli elementi figlio e l'elemento padre dell'elemento `CustomControlName`.</span><span class="sxs-lookup"><span data-stu-id="ab478-108">The following sections describe attributes, child elements, and the parent element of the `CustomControlName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="ab478-109">Attributi</span><span class="sxs-lookup"><span data-stu-id="ab478-109">Attributes</span></span>

<span data-ttu-id="ab478-110">Nessuna.</span><span class="sxs-lookup"><span data-stu-id="ab478-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="ab478-111">Elementi figlio</span><span class="sxs-lookup"><span data-stu-id="ab478-111">Child Elements</span></span>

<span data-ttu-id="ab478-112">Nessuna.</span><span class="sxs-lookup"><span data-stu-id="ab478-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="ab478-113">Elementi padre</span><span class="sxs-lookup"><span data-stu-id="ab478-113">Parent Elements</span></span>

|<span data-ttu-id="ab478-114">Elemento</span><span class="sxs-lookup"><span data-stu-id="ab478-114">Element</span></span>|<span data-ttu-id="ab478-115">Description</span><span class="sxs-lookup"><span data-stu-id="ab478-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="ab478-116">Elemento expressiongroup per CustomItem per i controlli per la visualizzazione (Format)</span><span class="sxs-lookup"><span data-stu-id="ab478-116">ExpressionBinding Element for CustomItem for Controls for View (Format)</span></span>](./expressionbinding-element-for-customitem-for-controls-for-view-format.md)|<span data-ttu-id="ab478-117">Definisce i dati visualizzati dal controllo.</span><span class="sxs-lookup"><span data-stu-id="ab478-117">Defines the data that is displayed by the control.</span></span>|

## <a name="text-value"></a><span data-ttu-id="ab478-118">Valore testo</span><span class="sxs-lookup"><span data-stu-id="ab478-118">Text Value</span></span>

<span data-ttu-id="ab478-119">Specificare il nome del controllo.</span><span class="sxs-lookup"><span data-stu-id="ab478-119">Specify the name of the control.</span></span>

## <a name="remarks"></a><span data-ttu-id="ab478-120">Osservazioni</span><span class="sxs-lookup"><span data-stu-id="ab478-120">Remarks</span></span>

<span data-ttu-id="ab478-121">È possibile creare controlli comuni che possono essere utilizzati da tutte le visualizzazioni di un file di formattazione ed è possibile creare controlli di visualizzazione che possono essere utilizzati da una visualizzazione specifica.</span><span class="sxs-lookup"><span data-stu-id="ab478-121">You can create common controls that can be used by all the views of a formatting file, and you can create view controls that can be used by a specific view.</span></span> <span data-ttu-id="ab478-122">Gli elementi seguenti specificano i nomi di questi controlli:</span><span class="sxs-lookup"><span data-stu-id="ab478-122">The following elements specify the names of these controls:</span></span>

- [<span data-ttu-id="ab478-123">Elemento Name per il controllo per i controlli per la configurazione (Format)</span><span class="sxs-lookup"><span data-stu-id="ab478-123">Name Element for Control for Controls for Configuration (Format)</span></span>](./name-element-for-control-for-controls-for-configuration-format.md)

- [<span data-ttu-id="ab478-124">Elemento Name per il controllo per i controlli per la visualizzazione (Format)</span><span class="sxs-lookup"><span data-stu-id="ab478-124">Name Element for Control for Controls for View (Format)</span></span>](./name-element-for-control-for-controls-for-view-format.md)

## <a name="see-also"></a><span data-ttu-id="ab478-125">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="ab478-125">See Also</span></span>

[<span data-ttu-id="ab478-126">Elemento Name per il controllo per i controlli per la configurazione (Format)</span><span class="sxs-lookup"><span data-stu-id="ab478-126">Name Element for Control for Controls for Configuration (Format)</span></span>](./name-element-for-control-for-controls-for-configuration-format.md)

[<span data-ttu-id="ab478-127">Elemento Name per il controllo per i controlli per la visualizzazione (Format)</span><span class="sxs-lookup"><span data-stu-id="ab478-127">Name Element for Control for Controls for View (Format)</span></span>](./name-element-for-control-for-controls-for-view-format.md)

[<span data-ttu-id="ab478-128">Elemento expressiongroup per CustomItem per i controlli per la visualizzazione (Format)</span><span class="sxs-lookup"><span data-stu-id="ab478-128">ExpressionBinding Element for CustomItem for Controls for View (Format)</span></span>](./expressionbinding-element-for-customitem-for-controls-for-view-format.md)

[<span data-ttu-id="ab478-129">Scrittura di un file di formattazione di PowerShell</span><span class="sxs-lookup"><span data-stu-id="ab478-129">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
