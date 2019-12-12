---
title: Elemento FirstLineHanging per frame per GroupBy (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 1cdcf66e-96a5-47b5-9269-b4330bde29f2
caps.latest.revision: 6
ms.openlocfilehash: 08db1f2d89c3fe6c1e9a5a522de3071425042c3f
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/05/2019
ms.locfileid: "72363820"
---
# <a name="firstlinehanging-element-for-frame-for-groupby-format"></a><span data-ttu-id="cf4e6-102">Elemento FirstLineHanging per Frame per GroupBy (formato)</span><span class="sxs-lookup"><span data-stu-id="cf4e6-102">FirstLineHanging Element for Frame for GroupBy (Format)</span></span>

<span data-ttu-id="cf4e6-103">Specifica il numero di caratteri che la prima riga di dati viene spostata a sinistra.</span><span class="sxs-lookup"><span data-stu-id="cf4e6-103">Specifies how many characters the first line of data is shifted to the left.</span></span> <span data-ttu-id="cf4e6-104">Questo elemento viene utilizzato quando si definisce la modalità di visualizzazione di un nuovo gruppo di oggetti.</span><span class="sxs-lookup"><span data-stu-id="cf4e6-104">This element is used when defining how a new group of objects is displayed.</span></span>

<span data-ttu-id="cf4e6-105">Elemento Configuration (Format) elemento ViewDefinitions (Format) elemento View (Format) elemento GroupBy per View (Format) elemento CustomControl per l'elemento GroupBy (Format) CustomEntries per CustomControl per l'elemento GroupBy (Format) CustomEntry per CustomControl per GroupBy (Format) elemento CustomItem per CustomEntry per l'elemento frame GroupBy (Format) per CustomItem per l'elemento GroupBy (Format) FirstLineHanging per frame per GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="cf4e6-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) GroupBy Element for View (Format) CustomControl Element for GroupBy (Format) CustomEntries Element for CustomControl for GroupBy (Format) CustomEntry Element for CustomControl for GroupBy (Format) CustomItem Element for CustomEntry for GroupBy (Format) Frame Element for CustomItem for GroupBy (Format) FirstLineHanging Element for Frame for GroupBy (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="cf4e6-106">Sintassi</span><span class="sxs-lookup"><span data-stu-id="cf4e6-106">Syntax</span></span>

```xml
<FirstLineHanging>NumberOfCharactersToShift</FirstLineHanging>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="cf4e6-107">Attributi ed elementi</span><span class="sxs-lookup"><span data-stu-id="cf4e6-107">Attributes and Elements</span></span>

<span data-ttu-id="cf4e6-108">Nelle sezioni seguenti vengono descritti gli attributi, gli elementi figlio e l'elemento padre dell'elemento `FirstLineHanging`.</span><span class="sxs-lookup"><span data-stu-id="cf4e6-108">The following sections describe attributes, child elements, and parent element of the `FirstLineHanging` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="cf4e6-109">Attributi</span><span class="sxs-lookup"><span data-stu-id="cf4e6-109">Attributes</span></span>

<span data-ttu-id="cf4e6-110">Nessuna.</span><span class="sxs-lookup"><span data-stu-id="cf4e6-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="cf4e6-111">Elementi figlio</span><span class="sxs-lookup"><span data-stu-id="cf4e6-111">Child Elements</span></span>

<span data-ttu-id="cf4e6-112">Nessuna.</span><span class="sxs-lookup"><span data-stu-id="cf4e6-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="cf4e6-113">Elementi padre</span><span class="sxs-lookup"><span data-stu-id="cf4e6-113">Parent Elements</span></span>

|<span data-ttu-id="cf4e6-114">Elemento</span><span class="sxs-lookup"><span data-stu-id="cf4e6-114">Element</span></span>|<span data-ttu-id="cf4e6-115">Description</span><span class="sxs-lookup"><span data-stu-id="cf4e6-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="cf4e6-116">Elemento frame per CustomItem per GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="cf4e6-116">Frame Element for CustomItem for GroupBy (Format)</span></span>](./frame-element-for-customitem-for-groupby-format.md)|<span data-ttu-id="cf4e6-117">Definisce la modalità di visualizzazione dei dati, ad esempio lo spostamento dei dati verso sinistra o verso destra.</span><span class="sxs-lookup"><span data-stu-id="cf4e6-117">Defines how the data is displayed, such as shifting the data to the left or right.</span></span>|

## <a name="text-value"></a><span data-ttu-id="cf4e6-118">Valore testo</span><span class="sxs-lookup"><span data-stu-id="cf4e6-118">Text Value</span></span>

<span data-ttu-id="cf4e6-119">Consente di specificare il numero di caratteri che si desidera spostare nella prima riga dei dati.</span><span class="sxs-lookup"><span data-stu-id="cf4e6-119">Specify the number of characters that you want to shift the first line of the data.</span></span>

## <a name="remarks"></a><span data-ttu-id="cf4e6-120">Osservazioni</span><span class="sxs-lookup"><span data-stu-id="cf4e6-120">Remarks</span></span>

<span data-ttu-id="cf4e6-121">Se questo elemento è specificato, non è possibile specificare l'elemento [FirstLineIndent](./firstlineindent-element-for-frame-for-groupby-format.md) .</span><span class="sxs-lookup"><span data-stu-id="cf4e6-121">If this element is specified, you cannot specify the [FirstLineIndent](./firstlineindent-element-for-frame-for-groupby-format.md) element.</span></span>

## <a name="see-also"></a><span data-ttu-id="cf4e6-122">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="cf4e6-122">See Also</span></span>

[<span data-ttu-id="cf4e6-123">Elemento FirstLineIndent per frame per GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="cf4e6-123">FirstLineIndent Element for Frame for GroupBy (Format)</span></span>](./firstlineindent-element-for-frame-for-groupby-format.md)

[<span data-ttu-id="cf4e6-124">Elemento frame per CustomItem per GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="cf4e6-124">Frame Element for CustomItem for GroupBy (Format)</span></span>](./frame-element-for-customitem-for-groupby-format.md)

[<span data-ttu-id="cf4e6-125">Scrittura di un file di formattazione di PowerShell</span><span class="sxs-lookup"><span data-stu-id="cf4e6-125">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
