---
title: Elemento FirstLineHanging per Frame per GroupBy (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 1cdcf66e-96a5-47b5-9269-b4330bde29f2
caps.latest.revision: 6
ms.openlocfilehash: 08db1f2d89c3fe6c1e9a5a522de3071425042c3f
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62065833"
---
# <a name="firstlinehanging-element-for-frame-for-groupby-format"></a><span data-ttu-id="04f08-102">Elemento FirstLineHanging per Frame per GroupBy (formato)</span><span class="sxs-lookup"><span data-stu-id="04f08-102">FirstLineHanging Element for Frame for GroupBy (Format)</span></span>

<span data-ttu-id="04f08-103">Specifica il numero di caratteri la prima riga di dati verrà spostata a sinistra.</span><span class="sxs-lookup"><span data-stu-id="04f08-103">Specifies how many characters the first line of data is shifted to the left.</span></span> <span data-ttu-id="04f08-104">Questo elemento viene usato quando si definisce come viene visualizzato un nuovo gruppo di oggetti.</span><span class="sxs-lookup"><span data-stu-id="04f08-104">This element is used when defining how a new group of objects is displayed.</span></span>

<span data-ttu-id="04f08-105">Elemento di GroupBy elemento (formato) per la visualizzazione elemento ViewDefinitions (formato) configurazione elemento (formato) per visualizzazione (formato) CustomControl elemento per elemento CustomEntries GroupBy (formato) per CustomControl per elemento CustomEntry GroupBy (formato) CustomControl per elemento CustomItem GroupBy (formato) per CustomEntry per elemento Frame GroupBy (formato) per CustomItem per elemento FirstLineHanging GroupBy (formato) per il Frame per GroupBy (formato)</span><span class="sxs-lookup"><span data-stu-id="04f08-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) GroupBy Element for View (Format) CustomControl Element for GroupBy (Format) CustomEntries Element for CustomControl for GroupBy (Format) CustomEntry Element for CustomControl for GroupBy (Format) CustomItem Element for CustomEntry for GroupBy (Format) Frame Element for CustomItem for GroupBy (Format) FirstLineHanging Element for Frame for GroupBy (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="04f08-106">Sintassi</span><span class="sxs-lookup"><span data-stu-id="04f08-106">Syntax</span></span>

```xml
<FirstLineHanging>NumberOfCharactersToShift</FirstLineHanging>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="04f08-107">Elementi e attributi</span><span class="sxs-lookup"><span data-stu-id="04f08-107">Attributes and Elements</span></span>

<span data-ttu-id="04f08-108">Le sezioni seguenti descrivono l'elemento padre di attributi e gli elementi figlio di `FirstLineHanging` elemento.</span><span class="sxs-lookup"><span data-stu-id="04f08-108">The following sections describe attributes, child elements, and parent element of the `FirstLineHanging` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="04f08-109">Attributes</span><span class="sxs-lookup"><span data-stu-id="04f08-109">Attributes</span></span>

<span data-ttu-id="04f08-110">Nessuna.</span><span class="sxs-lookup"><span data-stu-id="04f08-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="04f08-111">Elementi figlio</span><span class="sxs-lookup"><span data-stu-id="04f08-111">Child Elements</span></span>

<span data-ttu-id="04f08-112">Nessuna.</span><span class="sxs-lookup"><span data-stu-id="04f08-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="04f08-113">Elementi padre</span><span class="sxs-lookup"><span data-stu-id="04f08-113">Parent Elements</span></span>

|<span data-ttu-id="04f08-114">Elemento</span><span class="sxs-lookup"><span data-stu-id="04f08-114">Element</span></span>|<span data-ttu-id="04f08-115">Description</span><span class="sxs-lookup"><span data-stu-id="04f08-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="04f08-116">Elemento frame per CustomItem per GroupBy (formato)</span><span class="sxs-lookup"><span data-stu-id="04f08-116">Frame Element for CustomItem for GroupBy (Format)</span></span>](./frame-element-for-customitem-for-groupby-format.md)|<span data-ttu-id="04f08-117">Definisce come verranno visualizzati i dati, ad esempio lo spostamento di dati a sinistra o destra.</span><span class="sxs-lookup"><span data-stu-id="04f08-117">Defines how the data is displayed, such as shifting the data to the left or right.</span></span>|

## <a name="text-value"></a><span data-ttu-id="04f08-118">Valore di testo</span><span class="sxs-lookup"><span data-stu-id="04f08-118">Text Value</span></span>

<span data-ttu-id="04f08-119">Specificare il numero di caratteri che si desidera spostare la prima riga dei dati.</span><span class="sxs-lookup"><span data-stu-id="04f08-119">Specify the number of characters that you want to shift the first line of the data.</span></span>

## <a name="remarks"></a><span data-ttu-id="04f08-120">Osservazioni</span><span class="sxs-lookup"><span data-stu-id="04f08-120">Remarks</span></span>

<span data-ttu-id="04f08-121">Se questo elemento viene specificato, non è possibile specificare il [FirstLineIndent](./firstlineindent-element-for-frame-for-groupby-format.md) elemento.</span><span class="sxs-lookup"><span data-stu-id="04f08-121">If this element is specified, you cannot specify the [FirstLineIndent](./firstlineindent-element-for-frame-for-groupby-format.md) element.</span></span>

## <a name="see-also"></a><span data-ttu-id="04f08-122">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="04f08-122">See Also</span></span>

[<span data-ttu-id="04f08-123">Elemento FirstLineIndent per Frame per GroupBy (formato)</span><span class="sxs-lookup"><span data-stu-id="04f08-123">FirstLineIndent Element for Frame for GroupBy (Format)</span></span>](./firstlineindent-element-for-frame-for-groupby-format.md)

[<span data-ttu-id="04f08-124">Elemento frame per CustomItem per GroupBy (formato)</span><span class="sxs-lookup"><span data-stu-id="04f08-124">Frame Element for CustomItem for GroupBy (Format)</span></span>](./frame-element-for-customitem-for-groupby-format.md)

[<span data-ttu-id="04f08-125">La scrittura di un File di formattazione di PowerShell</span><span class="sxs-lookup"><span data-stu-id="04f08-125">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
