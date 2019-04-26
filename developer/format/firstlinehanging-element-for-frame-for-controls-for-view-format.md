---
title: Elemento FirstLineHanging per Frame per i controlli per la visualizzazione (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 53694f08-57f7-4185-b443-1636a0918afc
caps.latest.revision: 8
ms.openlocfilehash: 387340cd9b0aae2ad0419b187d96ab4fee183d5a
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62065804"
---
# <a name="firstlinehanging-element-for-frame-for-controls-for-view-format"></a><span data-ttu-id="15ba7-102">Elemento FirstLineHanging per Frame per Controls per View (formato)</span><span class="sxs-lookup"><span data-stu-id="15ba7-102">FirstLineHanging Element for Frame for Controls for View (Format)</span></span>

<span data-ttu-id="15ba7-103">Specifica il numero di caratteri la prima riga di dati verrà spostata a sinistra.</span><span class="sxs-lookup"><span data-stu-id="15ba7-103">Specifies how many characters the first line of data is shifted to the left.</span></span> <span data-ttu-id="15ba7-104">Questo elemento viene usato quando si definiscono i controlli che possono essere usati da una vista.</span><span class="sxs-lookup"><span data-stu-id="15ba7-104">This element is used when defining controls that can be used by a view.</span></span>

<span data-ttu-id="15ba7-105">Elemento (formato) elemento ViewDefinitions (formato) visualizzazione elemento (formato) i controlli elemento (formato) controllo elemento di configurazione per i controlli elemento di visualizzazione (formato) CustomControl per il controllo per i controlli elemento di visualizzazione (formato) CustomEntries per Elemento di visualizzazione (formato) CustomEntry per CustomEntries per i controlli elemento di visualizzazione (formato) CustomItem per CustomEntry per i controlli elemento di visualizzazione (formato) Frame per CustomItem per i controlli elemento di visualizzazione (formato) FirstLineHanging di CustomControl Frame di controlli di visualizzazione (formato)</span><span class="sxs-lookup"><span data-stu-id="15ba7-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) Controls Element (Format) Control Element for Controls for View (Format) CustomControl Element for Control for Controls for View (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for Controls for View (Format) CustomItem Element for CustomEntry for Controls for View (Format) Frame Element for CustomItem for Controls for View (Format) FirstLineHanging Element of Frame of Controls of View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="15ba7-106">Sintassi</span><span class="sxs-lookup"><span data-stu-id="15ba7-106">Syntax</span></span>

```xml
<FirstLineHanging>NumberOfCharactersToShift</FirstLineHanging>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="15ba7-107">Elementi e attributi</span><span class="sxs-lookup"><span data-stu-id="15ba7-107">Attributes and Elements</span></span>

<span data-ttu-id="15ba7-108">Le sezioni seguenti descrivono l'elemento padre di attributi e gli elementi figlio di `FirstLineHanging` elemento.</span><span class="sxs-lookup"><span data-stu-id="15ba7-108">The following sections describe attributes, child elements, and parent element of the `FirstLineHanging` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="15ba7-109">Attributes</span><span class="sxs-lookup"><span data-stu-id="15ba7-109">Attributes</span></span>

<span data-ttu-id="15ba7-110">Nessuna.</span><span class="sxs-lookup"><span data-stu-id="15ba7-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="15ba7-111">Elementi figlio</span><span class="sxs-lookup"><span data-stu-id="15ba7-111">Child Elements</span></span>

<span data-ttu-id="15ba7-112">Nessuna.</span><span class="sxs-lookup"><span data-stu-id="15ba7-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="15ba7-113">Elementi padre</span><span class="sxs-lookup"><span data-stu-id="15ba7-113">Parent Elements</span></span>

|<span data-ttu-id="15ba7-114">Elemento</span><span class="sxs-lookup"><span data-stu-id="15ba7-114">Element</span></span>|<span data-ttu-id="15ba7-115">Description</span><span class="sxs-lookup"><span data-stu-id="15ba7-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="15ba7-116">Elemento frame per CustomItem per i controlli per la visualizzazione (formato)</span><span class="sxs-lookup"><span data-stu-id="15ba7-116">Frame Element for CustomItem for Controls for View (Format)</span></span>](./frame-element-for-customitem-for-controls-for-view-format.md)|<span data-ttu-id="15ba7-117">Definisce come verranno visualizzati i dati, ad esempio lo spostamento di dati a sinistra o destra.</span><span class="sxs-lookup"><span data-stu-id="15ba7-117">Defines how the data is displayed, such as shifting the data to the left or right.</span></span>|

## <a name="text-value"></a><span data-ttu-id="15ba7-118">Valore di testo</span><span class="sxs-lookup"><span data-stu-id="15ba7-118">Text Value</span></span>

<span data-ttu-id="15ba7-119">Specificare il numero di caratteri che si desidera spostare la prima riga dei dati.</span><span class="sxs-lookup"><span data-stu-id="15ba7-119">Specify the number of characters that you want to shift the first line of the data.</span></span>

## <a name="remarks"></a><span data-ttu-id="15ba7-120">Osservazioni</span><span class="sxs-lookup"><span data-stu-id="15ba7-120">Remarks</span></span>

<span data-ttu-id="15ba7-121">Se questo elemento viene specificato, non è possibile specificare il [FirstLineIndent](./firstlineindent-element-for-frame-for-controls-for-view-format.md) elemento.</span><span class="sxs-lookup"><span data-stu-id="15ba7-121">If this element is specified, you cannot specify the [FirstLineIndent](./firstlineindent-element-for-frame-for-controls-for-view-format.md) element.</span></span>

## <a name="see-also"></a><span data-ttu-id="15ba7-122">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="15ba7-122">See Also</span></span>

[<span data-ttu-id="15ba7-123">Elemento FirstLineIndent per Frame per i controlli per la visualizzazione (formato)</span><span class="sxs-lookup"><span data-stu-id="15ba7-123">FirstLineIndent Element for Frame for Controls for View (Format)</span></span>](./firstlineindent-element-for-frame-for-controls-for-view-format.md)

[<span data-ttu-id="15ba7-124">Elemento frame per CustomItem per i controlli per la visualizzazione (formato)</span><span class="sxs-lookup"><span data-stu-id="15ba7-124">Frame Element for CustomItem for Controls for View (Format)</span></span>](./frame-element-for-customitem-for-controls-for-view-format.md)

[<span data-ttu-id="15ba7-125">La scrittura di un File di formattazione di PowerShell</span><span class="sxs-lookup"><span data-stu-id="15ba7-125">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
