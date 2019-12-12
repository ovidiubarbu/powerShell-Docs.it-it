---
title: Elemento FirstLineIndent per il frame per i controlli per la visualizzazione (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ec63f4f9-8858-4529-8646-ffbbc278f83e
caps.latest.revision: 7
ms.openlocfilehash: 694c5baaa5e90a772257276ba139d90acf7ec0e3
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/05/2019
ms.locfileid: "72363090"
---
# <a name="firstlineindent-element-for-frame-for-controls-for-view-format"></a><span data-ttu-id="a4f3c-102">Elemento FirstLineIndent per Frame per Controls per View (formato)</span><span class="sxs-lookup"><span data-stu-id="a4f3c-102">FirstLineIndent Element for Frame for Controls for View (Format)</span></span>

<span data-ttu-id="a4f3c-103">Specifica il numero di caratteri che la prima riga di dati viene spostata a destra.</span><span class="sxs-lookup"><span data-stu-id="a4f3c-103">Specifies how many characters the first line of data is shifted to the right.</span></span> <span data-ttu-id="a4f3c-104">Questo elemento viene utilizzato per la definizione di controlli che possono essere utilizzati da una visualizzazione.</span><span class="sxs-lookup"><span data-stu-id="a4f3c-104">This element is used when defining controls that can be used by a view.</span></span>

<span data-ttu-id="a4f3c-105">Elemento di configurazione (Format) elemento ViewDefinitions (Format) elemento di visualizzazione (Format) controlli elemento (Format) elemento di controllo per i controlli per la visualizzazione (formato) elemento CustomControl per il controllo per i controlli per la visualizzazione (formato) elemento CustomEntries per CustomControl per la visualizzazione (Format) elemento CustomEntry per CustomEntries per i controlli per la visualizzazione (formato) CustomItem elemento per CustomEntry per i controlli per la visualizzazione (formato) elemento del frame per CustomItem per i controlli per la visualizzazione (formato) FirstLineIndent elemento del frame dei controlli di visualizzazione (formato)</span><span class="sxs-lookup"><span data-stu-id="a4f3c-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) Controls Element (Format) Control Element for Controls for View (Format) CustomControl Element for Control for Controls for View (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for Controls for View (Format) CustomItem Element for CustomEntry for Controls for View (Format) Frame Element for CustomItem for Controls for View (Format) FirstLineIndent Element of Frame of Controls of View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="a4f3c-106">Sintassi</span><span class="sxs-lookup"><span data-stu-id="a4f3c-106">Syntax</span></span>

```xml
<FirstLineIndent>NumberOfCharactersToShift</FirstLineIndent>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="a4f3c-107">Attributi ed elementi</span><span class="sxs-lookup"><span data-stu-id="a4f3c-107">Attributes and Elements</span></span>

<span data-ttu-id="a4f3c-108">Nelle sezioni seguenti vengono descritti gli attributi, gli elementi figlio e l'elemento padre dell'elemento `FirstLineIndent`.</span><span class="sxs-lookup"><span data-stu-id="a4f3c-108">The following sections describe attributes, child elements, and parent element of the `FirstLineIndent` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="a4f3c-109">Attributi</span><span class="sxs-lookup"><span data-stu-id="a4f3c-109">Attributes</span></span>

<span data-ttu-id="a4f3c-110">Nessuna.</span><span class="sxs-lookup"><span data-stu-id="a4f3c-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="a4f3c-111">Elementi figlio</span><span class="sxs-lookup"><span data-stu-id="a4f3c-111">Child Elements</span></span>

<span data-ttu-id="a4f3c-112">Nessuna.</span><span class="sxs-lookup"><span data-stu-id="a4f3c-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="a4f3c-113">Elementi padre</span><span class="sxs-lookup"><span data-stu-id="a4f3c-113">Parent Elements</span></span>

|<span data-ttu-id="a4f3c-114">Elemento</span><span class="sxs-lookup"><span data-stu-id="a4f3c-114">Element</span></span>|<span data-ttu-id="a4f3c-115">Description</span><span class="sxs-lookup"><span data-stu-id="a4f3c-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="a4f3c-116">Elemento frame per CustomItem per i controlli per la visualizzazione (Format)</span><span class="sxs-lookup"><span data-stu-id="a4f3c-116">Frame Element for CustomItem for Controls for View (Format)</span></span>](./frame-element-for-customitem-for-controls-for-view-format.md)|<span data-ttu-id="a4f3c-117">Definisce la modalità di visualizzazione dei dati, ad esempio lo spostamento dei dati verso sinistra o verso destra.</span><span class="sxs-lookup"><span data-stu-id="a4f3c-117">Defines how the data is displayed, such as shifting the data to the left or right.</span></span>|

## <a name="text-value"></a><span data-ttu-id="a4f3c-118">Valore testo</span><span class="sxs-lookup"><span data-stu-id="a4f3c-118">Text Value</span></span>

<span data-ttu-id="a4f3c-119">Consente di specificare il numero di caratteri che si desidera spostare nella prima riga dei dati.</span><span class="sxs-lookup"><span data-stu-id="a4f3c-119">Specify the number of characters that you want to shift the first line of the data.</span></span>

## <a name="remarks"></a><span data-ttu-id="a4f3c-120">Osservazioni</span><span class="sxs-lookup"><span data-stu-id="a4f3c-120">Remarks</span></span>

<span data-ttu-id="a4f3c-121">Se questo elemento è specificato, non è possibile specificare l'elemento [FirstLineHanging](./firstlinehanging-element-for-frame-for-controls-for-view-format.md) .</span><span class="sxs-lookup"><span data-stu-id="a4f3c-121">If this element is specified, you cannot specify the [FirstLineHanging](./firstlinehanging-element-for-frame-for-controls-for-view-format.md) element.</span></span>

## <a name="see-also"></a><span data-ttu-id="a4f3c-122">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="a4f3c-122">See Also</span></span>

[<span data-ttu-id="a4f3c-123">Elemento FirstLineHanging per il frame per i controlli per la visualizzazione (Format)</span><span class="sxs-lookup"><span data-stu-id="a4f3c-123">FirstLineHanging Element for Frame for Controls for View (Format)</span></span>](./firstlinehanging-element-for-frame-for-controls-for-view-format.md)

[<span data-ttu-id="a4f3c-124">Elemento frame per CustomItem per i controlli per la visualizzazione (Format)</span><span class="sxs-lookup"><span data-stu-id="a4f3c-124">Frame Element for CustomItem for Controls for View (Format)</span></span>](./frame-element-for-customitem-for-controls-for-view-format.md)

[<span data-ttu-id="a4f3c-125">Scrittura di un file di formattazione di PowerShell</span><span class="sxs-lookup"><span data-stu-id="a4f3c-125">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
