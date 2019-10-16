---
title: Elemento FirstLineIndent per il frame per i controlli per la configurazione (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 2f489720-11f6-4019-940e-07f423d4278d
caps.latest.revision: 6
ms.openlocfilehash: c5b2d971fe1590116f96b024ae8769334768acf2
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/15/2019
ms.locfileid: "72363120"
---
# <a name="firstlineindent-element-for-frame-for-controls-for-configuration-format"></a><span data-ttu-id="53c9d-102">Elemento FirstLineIndent per Frame per Controls per Configuration (formato)</span><span class="sxs-lookup"><span data-stu-id="53c9d-102">FirstLineIndent Element for Frame for Controls for Configuration (Format)</span></span>

<span data-ttu-id="53c9d-103">Specifica il numero di caratteri che la prima riga di dati viene spostata a destra.</span><span class="sxs-lookup"><span data-stu-id="53c9d-103">Specifies how many characters the first line of data is shifted to the right.</span></span> <span data-ttu-id="53c9d-104">Questo elemento viene usato quando si definisce un controllo comune che può essere usato da tutte le visualizzazioni nel file di formattazione.</span><span class="sxs-lookup"><span data-stu-id="53c9d-104">This element is used when defining a common control that can be used by all the views in the formatting file.</span></span>

<span data-ttu-id="53c9d-105">Elemento di configurazione (Format) controlla l'elemento dell'elemento di controllo Configuration (Format) per i controlli per la configurazione (Format) elemento CustomControl per il controllo per la configurazione (Format) elemento CustomEntries per CustomControl per la configurazione ( Format) elemento CustomEntry per CustomControl per i controlli per la configurazione (Format) elemento CustomItem per CustomEntry per i controlli per l'elemento del frame di configurazione per CustomItem per i controlli per la configurazione (Format) elemento FirstLineIndent per frame per i controlli per la configurazione (Format)</span><span class="sxs-lookup"><span data-stu-id="53c9d-105">Configuration Element (Format) Controls Element of Configuration (Format) Control Element for Controls for Configuration (Format) CustomControl Element for Control for Configuration (Format) CustomEntries Element for CustomControl for Configuration (Format) CustomEntry Element for CustomControl for Controls for Configuration (Format) CustomItem Element for CustomEntry for Controls for Configuration Frame Element for CustomItem for Controls for Configuration (Format) FirstLineIndent Element for Frame for Controls for Configuration (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="53c9d-106">Sintassi</span><span class="sxs-lookup"><span data-stu-id="53c9d-106">Syntax</span></span>

```xml
<FirstLineIndent>NumberOfCharactersToShift</FirstLineIndent>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="53c9d-107">Attributi ed elementi</span><span class="sxs-lookup"><span data-stu-id="53c9d-107">Attributes and Elements</span></span>

<span data-ttu-id="53c9d-108">Nelle sezioni seguenti vengono descritti gli attributi, gli elementi figlio e l'elemento padre dell'elemento `FirstLineIndent`.</span><span class="sxs-lookup"><span data-stu-id="53c9d-108">The following sections describe attributes, child elements, and parent element of the `FirstLineIndent` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="53c9d-109">Attributi</span><span class="sxs-lookup"><span data-stu-id="53c9d-109">Attributes</span></span>

<span data-ttu-id="53c9d-110">Nessuna.</span><span class="sxs-lookup"><span data-stu-id="53c9d-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="53c9d-111">Elementi figlio</span><span class="sxs-lookup"><span data-stu-id="53c9d-111">Child Elements</span></span>

<span data-ttu-id="53c9d-112">Nessuna.</span><span class="sxs-lookup"><span data-stu-id="53c9d-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="53c9d-113">Elementi padre</span><span class="sxs-lookup"><span data-stu-id="53c9d-113">Parent Elements</span></span>

|<span data-ttu-id="53c9d-114">Elemento</span><span class="sxs-lookup"><span data-stu-id="53c9d-114">Element</span></span>|<span data-ttu-id="53c9d-115">Description</span><span class="sxs-lookup"><span data-stu-id="53c9d-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="53c9d-116">Elemento frame per CustomItem per i controlli per la configurazione (Format)</span><span class="sxs-lookup"><span data-stu-id="53c9d-116">Frame Element for CustomItem for Controls for Configuration (Format)</span></span>](./frame-element-for-customitem-for-controls-for-configuration-format.md)|<span data-ttu-id="53c9d-117">Definisce la modalità di visualizzazione dei dati, ad esempio lo spostamento dei dati verso sinistra o verso destra.</span><span class="sxs-lookup"><span data-stu-id="53c9d-117">Defines how the data is displayed, such as shifting the data to the left or right.</span></span>|

## <a name="text-value"></a><span data-ttu-id="53c9d-118">Valore di testo</span><span class="sxs-lookup"><span data-stu-id="53c9d-118">Text Value</span></span>

<span data-ttu-id="53c9d-119">Consente di specificare il numero di caratteri che si desidera spostare nella prima riga dei dati.</span><span class="sxs-lookup"><span data-stu-id="53c9d-119">Specify the number of characters that you want to shift the first line of the data.</span></span>

## <a name="remarks"></a><span data-ttu-id="53c9d-120">Osservazioni</span><span class="sxs-lookup"><span data-stu-id="53c9d-120">Remarks</span></span>

<span data-ttu-id="53c9d-121">Se questo elemento è specificato, non è possibile specificare l'elemento [FirstLineHanging](./firstlinehanging-element-for-frame-for-controls-for-configuration-format.md) .</span><span class="sxs-lookup"><span data-stu-id="53c9d-121">If this element is specified, you cannot specify the [FirstLineHanging](./firstlinehanging-element-for-frame-for-controls-for-configuration-format.md) element.</span></span>

## <a name="see-also"></a><span data-ttu-id="53c9d-122">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="53c9d-122">See Also</span></span>

[<span data-ttu-id="53c9d-123">Elemento FirstLineHanging per il frame per i controlli per la configurazione (Format)</span><span class="sxs-lookup"><span data-stu-id="53c9d-123">FirstLineHanging Element for Frame for Controls for Configuration (Format)</span></span>](./firstlinehanging-element-for-frame-for-controls-for-configuration-format.md)

[<span data-ttu-id="53c9d-124">Elemento frame per CustomItem per i controlli per la configurazione (Format)</span><span class="sxs-lookup"><span data-stu-id="53c9d-124">Frame Element for CustomItem for Controls for Configuration (Format)</span></span>](./frame-element-for-customitem-for-controls-for-configuration-format.md)

[<span data-ttu-id="53c9d-125">Scrittura di un file di formattazione di PowerShell</span><span class="sxs-lookup"><span data-stu-id="53c9d-125">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
