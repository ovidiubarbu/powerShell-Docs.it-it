---
title: Elemento FirstLineHanging per Frame per CustomControl per visualizzazione (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: c6ac3d86-0529-4b93-9bc7-ee94fcef9618
caps.latest.revision: 8
ms.openlocfilehash: ea43e025f5f653ff000e1d7591b535e73da5c9e5
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62065972"
---
# <a name="firstlinehanging-element-for-frame-for-customcontrol-for-view-format"></a><span data-ttu-id="ccd23-102">Elemento FirstLineHanging per Frame per CustomControl per View (formato)</span><span class="sxs-lookup"><span data-stu-id="ccd23-102">FirstLineHanging Element for Frame for CustomControl for View (Format)</span></span>

<span data-ttu-id="ccd23-103">Specifica il numero di caratteri la prima riga di dati verrà spostata a sinistra.</span><span class="sxs-lookup"><span data-stu-id="ccd23-103">Specifies how many characters the first line of data is shifted to the left.</span></span> <span data-ttu-id="ccd23-104">Questo elemento viene usato quando si definisce una vista di controllo personalizzato.</span><span class="sxs-lookup"><span data-stu-id="ccd23-104">This element is used when defining a custom control view.</span></span>

<span data-ttu-id="ccd23-105">Elemento (formato) elemento ViewDefinitions (formato) visualizzazione elemento (formato) elemento CustomControl (formato) CustomEntries elemento di configurazione per CustomControl elemento di visualizzazione (formato) CustomEntry per CustomEntries per elemento CustomItem visualizzazione (formato) CustomEntry per elemento Frame CustomControlView (formato) per CustomItem per CustomControl elemento di visualizzazione (formato) FirstLineHanging per Frame per CustomControl per visualizzazione (formato)</span><span class="sxs-lookup"><span data-stu-id="ccd23-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) CustomControl Element (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for View (Format) CustomItem Element for CustomEntry for CustomControlView (Format) Frame Element for CustomItem for CustomControl for View (Format) FirstLineHanging Element for Frame for CustomControl for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="ccd23-106">Sintassi</span><span class="sxs-lookup"><span data-stu-id="ccd23-106">Syntax</span></span>

```xml
<FirstLineHanging>NumberOfCharactersToShift</FirstLineHanging>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="ccd23-107">Elementi e attributi</span><span class="sxs-lookup"><span data-stu-id="ccd23-107">Attributes and Elements</span></span>

<span data-ttu-id="ccd23-108">Le sezioni seguenti descrivono l'elemento padre di attributi e gli elementi figlio di `FirstLineHanging` elemento.</span><span class="sxs-lookup"><span data-stu-id="ccd23-108">The following sections describe attributes, child elements, and parent element of the `FirstLineHanging` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="ccd23-109">Attributes</span><span class="sxs-lookup"><span data-stu-id="ccd23-109">Attributes</span></span>

<span data-ttu-id="ccd23-110">Nessuna.</span><span class="sxs-lookup"><span data-stu-id="ccd23-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="ccd23-111">Elementi figlio</span><span class="sxs-lookup"><span data-stu-id="ccd23-111">Child Elements</span></span>

<span data-ttu-id="ccd23-112">Nessuna.</span><span class="sxs-lookup"><span data-stu-id="ccd23-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="ccd23-113">Elementi padre</span><span class="sxs-lookup"><span data-stu-id="ccd23-113">Parent Elements</span></span>

|<span data-ttu-id="ccd23-114">Elemento</span><span class="sxs-lookup"><span data-stu-id="ccd23-114">Element</span></span>|<span data-ttu-id="ccd23-115">Description</span><span class="sxs-lookup"><span data-stu-id="ccd23-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="ccd23-116">Elemento frame per CustomItem per CustomControl per visualizzazione (formato)</span><span class="sxs-lookup"><span data-stu-id="ccd23-116">Frame Element for CustomItem for CustomControl for View (Format)</span></span>](./frame-element-for-customitem-for-customcontrol-for-view-format.md)|<span data-ttu-id="ccd23-117">Definisce come verranno visualizzati i dati, ad esempio lo spostamento di dati a sinistra o destra.</span><span class="sxs-lookup"><span data-stu-id="ccd23-117">Defines how the data is displayed, such as shifting the data to the left or right.</span></span>|

## <a name="text-value"></a><span data-ttu-id="ccd23-118">Valore di testo</span><span class="sxs-lookup"><span data-stu-id="ccd23-118">Text Value</span></span>

<span data-ttu-id="ccd23-119">Specificare il numero di caratteri che si desidera spostare la prima riga dei dati.</span><span class="sxs-lookup"><span data-stu-id="ccd23-119">Specify the number of characters that you want to shift the first line of the data.</span></span>

## <a name="remarks"></a><span data-ttu-id="ccd23-120">Osservazioni</span><span class="sxs-lookup"><span data-stu-id="ccd23-120">Remarks</span></span>

<span data-ttu-id="ccd23-121">Se questo elemento viene specificato, non è possibile specificare il [FirstLineIndent](./firstlineindent-element-for-frame-for-customcontrol-for-view-format.md) elemento.</span><span class="sxs-lookup"><span data-stu-id="ccd23-121">If this element is specified, you cannot specify the [FirstLineIndent](./firstlineindent-element-for-frame-for-customcontrol-for-view-format.md) element.</span></span>

## <a name="see-also"></a><span data-ttu-id="ccd23-122">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="ccd23-122">See Also</span></span>

[<span data-ttu-id="ccd23-123">Elemento FirstLineIndent per Frame per CustomControl per visualizzazione (formato)</span><span class="sxs-lookup"><span data-stu-id="ccd23-123">FirstLineIndent Element for Frame for CustomControl for View (Format)</span></span>](./firstlineindent-element-for-frame-for-customcontrol-for-view-format.md)

[<span data-ttu-id="ccd23-124">Elemento frame per CustomItem per CustomControl per visualizzazione (formato)</span><span class="sxs-lookup"><span data-stu-id="ccd23-124">Frame Element for CustomItem for CustomControl for View (Format)</span></span>](./frame-element-for-customitem-for-customcontrol-for-view-format.md)

[<span data-ttu-id="ccd23-125">La scrittura di un File di formattazione di PowerShell</span><span class="sxs-lookup"><span data-stu-id="ccd23-125">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
