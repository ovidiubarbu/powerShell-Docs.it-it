---
title: Elemento FirstLineHanging per il frame per i controlli per la visualizzazione (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 53694f08-57f7-4185-b443-1636a0918afc
caps.latest.revision: 8
ms.openlocfilehash: 387340cd9b0aae2ad0419b187d96ab4fee183d5a
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/15/2019
ms.locfileid: "72363790"
---
# <a name="firstlinehanging-element-for-frame-for-controls-for-view-format"></a><span data-ttu-id="47cb0-102">Elemento FirstLineHanging per Frame per Controls per View (formato)</span><span class="sxs-lookup"><span data-stu-id="47cb0-102">FirstLineHanging Element for Frame for Controls for View (Format)</span></span>

<span data-ttu-id="47cb0-103">Specifica il numero di caratteri che la prima riga di dati viene spostata a sinistra.</span><span class="sxs-lookup"><span data-stu-id="47cb0-103">Specifies how many characters the first line of data is shifted to the left.</span></span> <span data-ttu-id="47cb0-104">Questo elemento viene utilizzato per la definizione di controlli che possono essere utilizzati da una visualizzazione.</span><span class="sxs-lookup"><span data-stu-id="47cb0-104">This element is used when defining controls that can be used by a view.</span></span>

<span data-ttu-id="47cb0-105">Elemento di configurazione (Format) elemento ViewDefinitions (Format) elemento di visualizzazione (Format) controlli elemento (Format) elemento di controllo per i controlli per la visualizzazione (formato) elemento CustomControl per il controllo per i controlli per la visualizzazione (formato) elemento CustomEntries per CustomControl per la visualizzazione (Format) elemento CustomEntry per CustomEntries per i controlli per la visualizzazione (formato) CustomItem elemento per CustomEntry per i controlli per la visualizzazione (formato) elemento del frame per CustomItem per i controlli per la visualizzazione (formato) FirstLineHanging elemento di Frame di controlli della visualizzazione (formato)</span><span class="sxs-lookup"><span data-stu-id="47cb0-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) Controls Element (Format) Control Element for Controls for View (Format) CustomControl Element for Control for Controls for View (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for Controls for View (Format) CustomItem Element for CustomEntry for Controls for View (Format) Frame Element for CustomItem for Controls for View (Format) FirstLineHanging Element of Frame of Controls of View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="47cb0-106">Sintassi</span><span class="sxs-lookup"><span data-stu-id="47cb0-106">Syntax</span></span>

```xml
<FirstLineHanging>NumberOfCharactersToShift</FirstLineHanging>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="47cb0-107">Attributi ed elementi</span><span class="sxs-lookup"><span data-stu-id="47cb0-107">Attributes and Elements</span></span>

<span data-ttu-id="47cb0-108">Nelle sezioni seguenti vengono descritti gli attributi, gli elementi figlio e l'elemento padre dell'elemento `FirstLineHanging`.</span><span class="sxs-lookup"><span data-stu-id="47cb0-108">The following sections describe attributes, child elements, and parent element of the `FirstLineHanging` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="47cb0-109">Attributi</span><span class="sxs-lookup"><span data-stu-id="47cb0-109">Attributes</span></span>

<span data-ttu-id="47cb0-110">Nessuna.</span><span class="sxs-lookup"><span data-stu-id="47cb0-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="47cb0-111">Elementi figlio</span><span class="sxs-lookup"><span data-stu-id="47cb0-111">Child Elements</span></span>

<span data-ttu-id="47cb0-112">Nessuna.</span><span class="sxs-lookup"><span data-stu-id="47cb0-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="47cb0-113">Elementi padre</span><span class="sxs-lookup"><span data-stu-id="47cb0-113">Parent Elements</span></span>

|<span data-ttu-id="47cb0-114">Elemento</span><span class="sxs-lookup"><span data-stu-id="47cb0-114">Element</span></span>|<span data-ttu-id="47cb0-115">Description</span><span class="sxs-lookup"><span data-stu-id="47cb0-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="47cb0-116">Elemento frame per CustomItem per i controlli per la visualizzazione (Format)</span><span class="sxs-lookup"><span data-stu-id="47cb0-116">Frame Element for CustomItem for Controls for View (Format)</span></span>](./frame-element-for-customitem-for-controls-for-view-format.md)|<span data-ttu-id="47cb0-117">Definisce la modalità di visualizzazione dei dati, ad esempio lo spostamento dei dati verso sinistra o verso destra.</span><span class="sxs-lookup"><span data-stu-id="47cb0-117">Defines how the data is displayed, such as shifting the data to the left or right.</span></span>|

## <a name="text-value"></a><span data-ttu-id="47cb0-118">Valore di testo</span><span class="sxs-lookup"><span data-stu-id="47cb0-118">Text Value</span></span>

<span data-ttu-id="47cb0-119">Consente di specificare il numero di caratteri che si desidera spostare nella prima riga dei dati.</span><span class="sxs-lookup"><span data-stu-id="47cb0-119">Specify the number of characters that you want to shift the first line of the data.</span></span>

## <a name="remarks"></a><span data-ttu-id="47cb0-120">Osservazioni</span><span class="sxs-lookup"><span data-stu-id="47cb0-120">Remarks</span></span>

<span data-ttu-id="47cb0-121">Se questo elemento è specificato, non è possibile specificare l'elemento [FirstLineIndent](./firstlineindent-element-for-frame-for-controls-for-view-format.md) .</span><span class="sxs-lookup"><span data-stu-id="47cb0-121">If this element is specified, you cannot specify the [FirstLineIndent](./firstlineindent-element-for-frame-for-controls-for-view-format.md) element.</span></span>

## <a name="see-also"></a><span data-ttu-id="47cb0-122">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="47cb0-122">See Also</span></span>

[<span data-ttu-id="47cb0-123">Elemento FirstLineIndent per il frame per i controlli per la visualizzazione (Format)</span><span class="sxs-lookup"><span data-stu-id="47cb0-123">FirstLineIndent Element for Frame for Controls for View (Format)</span></span>](./firstlineindent-element-for-frame-for-controls-for-view-format.md)

[<span data-ttu-id="47cb0-124">Elemento frame per CustomItem per i controlli per la visualizzazione (Format)</span><span class="sxs-lookup"><span data-stu-id="47cb0-124">Frame Element for CustomItem for Controls for View (Format)</span></span>](./frame-element-for-customitem-for-controls-for-view-format.md)

[<span data-ttu-id="47cb0-125">Scrittura di un file di formattazione di PowerShell</span><span class="sxs-lookup"><span data-stu-id="47cb0-125">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
