---
title: Elemento FirstLineIndent per Frame per i controlli per la visualizzazione (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ec63f4f9-8858-4529-8646-ffbbc278f83e
caps.latest.revision: 7
ms.openlocfilehash: 694c5baaa5e90a772257276ba139d90acf7ec0e3
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/03/2019
ms.locfileid: "56854317"
---
# <a name="firstlineindent-element-for-frame-for-controls-for-view-format"></a><span data-ttu-id="c9b44-102">Elemento FirstLineIndent per Frame per Controls per View (formato)</span><span class="sxs-lookup"><span data-stu-id="c9b44-102">FirstLineIndent Element for Frame for Controls for View (Format)</span></span>

<span data-ttu-id="c9b44-103">Specifica il numero di caratteri la prima riga di dati verrà spostata a destra.</span><span class="sxs-lookup"><span data-stu-id="c9b44-103">Specifies how many characters the first line of data is shifted to the right.</span></span> <span data-ttu-id="c9b44-104">Questo elemento viene usato quando si definiscono i controlli che possono essere usati da una vista.</span><span class="sxs-lookup"><span data-stu-id="c9b44-104">This element is used when defining controls that can be used by a view.</span></span>

<span data-ttu-id="c9b44-105">Elemento (formato) elemento ViewDefinitions (formato) visualizzazione elemento (formato) i controlli elemento (formato) controllo elemento di configurazione per i controlli elemento di visualizzazione (formato) CustomControl per il controllo per i controlli elemento di visualizzazione (formato) CustomEntries per CustomControl elemento di visualizzazione (formato) CustomEntry per CustomEntries per i controlli elemento di visualizzazione (formato) CustomItem per CustomEntry per i controlli elemento di visualizzazione (formato) Frame per CustomItem per i controlli elemento di visualizzazione (formato) FirstLineIndent del Frame controlli della visualizzazione (formato)</span><span class="sxs-lookup"><span data-stu-id="c9b44-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) Controls Element (Format) Control Element for Controls for View (Format) CustomControl Element for Control for Controls for View (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for Controls for View (Format) CustomItem Element for CustomEntry for Controls for View (Format) Frame Element for CustomItem for Controls for View (Format) FirstLineIndent Element of Frame of Controls of View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="c9b44-106">Sintassi</span><span class="sxs-lookup"><span data-stu-id="c9b44-106">Syntax</span></span>

```xml
<FirstLineIndent>NumberOfCharactersToShift</FirstLineIndent>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="c9b44-107">Attributi ed elementi</span><span class="sxs-lookup"><span data-stu-id="c9b44-107">Attributes and Elements</span></span>

<span data-ttu-id="c9b44-108">Le sezioni seguenti descrivono l'elemento padre di attributi e gli elementi figlio di `FirstLineIndent` elemento.</span><span class="sxs-lookup"><span data-stu-id="c9b44-108">The following sections describe attributes, child elements, and parent element of the `FirstLineIndent` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="c9b44-109">Attributes</span><span class="sxs-lookup"><span data-stu-id="c9b44-109">Attributes</span></span>

<span data-ttu-id="c9b44-110">Nessuna.</span><span class="sxs-lookup"><span data-stu-id="c9b44-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="c9b44-111">Elementi figlio</span><span class="sxs-lookup"><span data-stu-id="c9b44-111">Child Elements</span></span>

<span data-ttu-id="c9b44-112">Nessuna.</span><span class="sxs-lookup"><span data-stu-id="c9b44-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="c9b44-113">Elementi padre</span><span class="sxs-lookup"><span data-stu-id="c9b44-113">Parent Elements</span></span>

|<span data-ttu-id="c9b44-114">Elemento</span><span class="sxs-lookup"><span data-stu-id="c9b44-114">Element</span></span>|<span data-ttu-id="c9b44-115">Description</span><span class="sxs-lookup"><span data-stu-id="c9b44-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="c9b44-116">Elemento frame per CustomItem per i controlli per la visualizzazione (formato)</span><span class="sxs-lookup"><span data-stu-id="c9b44-116">Frame Element for CustomItem for Controls for View (Format)</span></span>](./frame-element-for-customitem-for-controls-for-view-format.md)|<span data-ttu-id="c9b44-117">Definisce come verranno visualizzati i dati, ad esempio lo spostamento di dati a sinistra o destra.</span><span class="sxs-lookup"><span data-stu-id="c9b44-117">Defines how the data is displayed, such as shifting the data to the left or right.</span></span>|

## <a name="text-value"></a><span data-ttu-id="c9b44-118">Valore di testo</span><span class="sxs-lookup"><span data-stu-id="c9b44-118">Text Value</span></span>

<span data-ttu-id="c9b44-119">Specificare il numero di caratteri che si desidera spostare la prima riga dei dati.</span><span class="sxs-lookup"><span data-stu-id="c9b44-119">Specify the number of characters that you want to shift the first line of the data.</span></span>

## <a name="remarks"></a><span data-ttu-id="c9b44-120">Osservazioni</span><span class="sxs-lookup"><span data-stu-id="c9b44-120">Remarks</span></span>

<span data-ttu-id="c9b44-121">Se questo elemento viene specificato, non è possibile specificare il [FirstLineHanging](./firstlinehanging-element-for-frame-for-controls-for-view-format.md) elemento.</span><span class="sxs-lookup"><span data-stu-id="c9b44-121">If this element is specified, you cannot specify the [FirstLineHanging](./firstlinehanging-element-for-frame-for-controls-for-view-format.md) element.</span></span>

## <a name="see-also"></a><span data-ttu-id="c9b44-122">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="c9b44-122">See Also</span></span>

[<span data-ttu-id="c9b44-123">Elemento FirstLineHanging per Frame per i controlli per la visualizzazione (formato)</span><span class="sxs-lookup"><span data-stu-id="c9b44-123">FirstLineHanging Element for Frame for Controls for View (Format)</span></span>](./firstlinehanging-element-for-frame-for-controls-for-view-format.md)

[<span data-ttu-id="c9b44-124">Elemento frame per CustomItem per i controlli per la visualizzazione (formato)</span><span class="sxs-lookup"><span data-stu-id="c9b44-124">Frame Element for CustomItem for Controls for View (Format)</span></span>](./frame-element-for-customitem-for-controls-for-view-format.md)

[<span data-ttu-id="c9b44-125">La scrittura di un File di formattazione di PowerShell</span><span class="sxs-lookup"><span data-stu-id="c9b44-125">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
