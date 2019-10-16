---
title: Elemento FirstLineIndent per frame per GroupBy (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 33be3b9e-53c8-433f-8c11-c65b0d46744c
caps.latest.revision: 6
ms.openlocfilehash: 9ba6fc1b9924a4b0d5b56ee15290a2293217403c
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/15/2019
ms.locfileid: "72363080"
---
# <a name="firstlineindent-element-for-frame-for-groupby-format"></a><span data-ttu-id="c0b61-102">Elemento FirstLineIndent per Frame per GroupBy (formato)</span><span class="sxs-lookup"><span data-stu-id="c0b61-102">FirstLineIndent Element for Frame for GroupBy (Format)</span></span>

<span data-ttu-id="c0b61-103">Specifica il numero di caratteri che la prima riga di dati viene spostata a destra.</span><span class="sxs-lookup"><span data-stu-id="c0b61-103">Specifies how many characters the first line of data is shifted to the right.</span></span> <span data-ttu-id="c0b61-104">Questo elemento viene utilizzato quando si definisce la modalità di visualizzazione di un nuovo gruppo di oggetti.</span><span class="sxs-lookup"><span data-stu-id="c0b61-104">This element is used when defining how a new group of objects is displayed.</span></span>

<span data-ttu-id="c0b61-105">Elemento Configuration (Format) elemento ViewDefinitions (Format) elemento View (Format) elemento GroupBy per View (Format) elemento CustomControl per l'elemento GroupBy (Format) CustomEntries per CustomControl per l'elemento GroupBy (Format) CustomEntry per CustomControl per GroupBy (Format) elemento CustomItem per CustomEntry per l'elemento frame GroupBy (Format) per CustomItem per l'elemento GroupBy (Format) FirstLineIndent per frame per GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="c0b61-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) GroupBy Element for View (Format) CustomControl Element for GroupBy (Format) CustomEntries Element for CustomControl for GroupBy (Format) CustomEntry Element for CustomControl for GroupBy (Format) CustomItem Element for CustomEntry for GroupBy (Format) Frame Element for CustomItem for GroupBy (Format) FirstLineIndent Element for Frame for GroupBy (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="c0b61-106">Sintassi</span><span class="sxs-lookup"><span data-stu-id="c0b61-106">Syntax</span></span>

```xml
<FirstLineIndent>NumberOfCharactersToShift</FirstLineIndent>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="c0b61-107">Attributi ed elementi</span><span class="sxs-lookup"><span data-stu-id="c0b61-107">Attributes and Elements</span></span>

<span data-ttu-id="c0b61-108">Nelle sezioni seguenti vengono descritti gli attributi, gli elementi figlio e l'elemento padre dell'elemento `FirstLineIndent`.</span><span class="sxs-lookup"><span data-stu-id="c0b61-108">The following sections describe attributes, child elements, and parent element of the `FirstLineIndent` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="c0b61-109">Attributi</span><span class="sxs-lookup"><span data-stu-id="c0b61-109">Attributes</span></span>

<span data-ttu-id="c0b61-110">Nessuna.</span><span class="sxs-lookup"><span data-stu-id="c0b61-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="c0b61-111">Elementi figlio</span><span class="sxs-lookup"><span data-stu-id="c0b61-111">Child Elements</span></span>

<span data-ttu-id="c0b61-112">Nessuna.</span><span class="sxs-lookup"><span data-stu-id="c0b61-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="c0b61-113">Elementi padre</span><span class="sxs-lookup"><span data-stu-id="c0b61-113">Parent Elements</span></span>

|<span data-ttu-id="c0b61-114">Elemento</span><span class="sxs-lookup"><span data-stu-id="c0b61-114">Element</span></span>|<span data-ttu-id="c0b61-115">Description</span><span class="sxs-lookup"><span data-stu-id="c0b61-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="c0b61-116">Elemento frame per CustomItem per GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="c0b61-116">Frame Element for CustomItem for GroupBy (Format)</span></span>](./frame-element-for-customitem-for-groupby-format.md)|<span data-ttu-id="c0b61-117">Definisce la modalità di visualizzazione dei dati, ad esempio lo spostamento dei dati verso sinistra o verso destra.</span><span class="sxs-lookup"><span data-stu-id="c0b61-117">Defines how the data is displayed, such as shifting the data to the left or right.</span></span>|

## <a name="text-value"></a><span data-ttu-id="c0b61-118">Valore di testo</span><span class="sxs-lookup"><span data-stu-id="c0b61-118">Text Value</span></span>

<span data-ttu-id="c0b61-119">Consente di specificare il numero di caratteri che si desidera spostare nella prima riga dei dati.</span><span class="sxs-lookup"><span data-stu-id="c0b61-119">Specify the number of characters that you want to shift the first line of the data.</span></span>

## <a name="remarks"></a><span data-ttu-id="c0b61-120">Osservazioni</span><span class="sxs-lookup"><span data-stu-id="c0b61-120">Remarks</span></span>

<span data-ttu-id="c0b61-121">Se questo elemento è specificato, non è possibile specificare l'elemento [FirstLineHanging](./firstlinehanging-element-for-frame-for-groupby-format.md) .</span><span class="sxs-lookup"><span data-stu-id="c0b61-121">If this element is specified, you cannot specify the [FirstLineHanging](./firstlinehanging-element-for-frame-for-groupby-format.md) element.</span></span>

## <a name="see-also"></a><span data-ttu-id="c0b61-122">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="c0b61-122">See Also</span></span>

[<span data-ttu-id="c0b61-123">Elemento FirstLineHanging per frame per GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="c0b61-123">FirstLineHanging Element for Frame for GroupBy (Format)</span></span>](./firstlinehanging-element-for-frame-for-groupby-format.md)

[<span data-ttu-id="c0b61-124">Elemento frame per CustomItem per GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="c0b61-124">Frame Element for CustomItem for GroupBy (Format)</span></span>](./frame-element-for-customitem-for-groupby-format.md)

[<span data-ttu-id="c0b61-125">Scrittura di un file di formattazione di PowerShell</span><span class="sxs-lookup"><span data-stu-id="c0b61-125">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
