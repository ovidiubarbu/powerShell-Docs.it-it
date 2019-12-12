---
title: Elemento FirstLineHanging per il frame per i controlli per la configurazione (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 679c8bcb-b49d-4bb4-91f5-ea1af6c217e3
caps.latest.revision: 8
ms.openlocfilehash: 4553f95e48a2b1440c00b4951bea56376b00628a
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/05/2019
ms.locfileid: "72363170"
---
# <a name="firstlinehanging-element-for-frame-for-controls-for-configuration-format"></a><span data-ttu-id="dedac-102">Elemento FirstLineHanging per Frame per Controls per Configuration (formato)</span><span class="sxs-lookup"><span data-stu-id="dedac-102">FirstLineHanging Element for Frame for Controls for Configuration (Format)</span></span>

<span data-ttu-id="dedac-103">Specifica il numero di caratteri che la prima riga di dati viene spostata a sinistra.</span><span class="sxs-lookup"><span data-stu-id="dedac-103">Specifies how many characters the first line of data is shifted to the left.</span></span> <span data-ttu-id="dedac-104">Questo elemento viene usato quando si definisce un controllo comune che può essere usato da tutte le visualizzazioni nel file di formattazione.</span><span class="sxs-lookup"><span data-stu-id="dedac-104">This element is used when defining a common control that can be used by all the views in the formatting file.</span></span>

<span data-ttu-id="dedac-105">Elemento di configurazione (Format) controlla l'elemento dell'elemento di controllo Configuration (Format) per i controlli per la configurazione (Format) elemento CustomControl per il controllo per la configurazione (Format) elemento CustomEntries per CustomControl per la configurazione ( Format) elemento CustomEntry per CustomControl per i controlli per la configurazione (Format) elemento CustomItem per CustomEntry per i controlli per l'elemento del frame di configurazione per CustomItem per i controlli per la configurazione (Format) elemento FirstLineHanging per frame per i controlli per la configurazione (Format)</span><span class="sxs-lookup"><span data-stu-id="dedac-105">Configuration Element (Format) Controls Element of Configuration (Format) Control Element for Controls for Configuration (Format) CustomControl Element for Control for Configuration (Format) CustomEntries Element for CustomControl for Configuration (Format) CustomEntry Element for CustomControl for Controls for Configuration (Format) CustomItem Element for CustomEntry for Controls for Configuration Frame Element for CustomItem for Controls for Configuration (Format) FirstLineHanging Element for Frame for Controls for Configuration (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="dedac-106">Sintassi</span><span class="sxs-lookup"><span data-stu-id="dedac-106">Syntax</span></span>

```xml
<FirstLineHanging>NumberOfCharactersToShift</FirstLineHanging>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="dedac-107">Attributi ed elementi</span><span class="sxs-lookup"><span data-stu-id="dedac-107">Attributes and Elements</span></span>

<span data-ttu-id="dedac-108">Nelle sezioni seguenti vengono descritti gli attributi, gli elementi figlio e l'elemento padre dell'elemento `FirstLineHanging`.</span><span class="sxs-lookup"><span data-stu-id="dedac-108">The following sections describe attributes, child elements, and parent element of the `FirstLineHanging` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="dedac-109">Attributi</span><span class="sxs-lookup"><span data-stu-id="dedac-109">Attributes</span></span>

<span data-ttu-id="dedac-110">Nessuna.</span><span class="sxs-lookup"><span data-stu-id="dedac-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="dedac-111">Elementi figlio</span><span class="sxs-lookup"><span data-stu-id="dedac-111">Child Elements</span></span>

<span data-ttu-id="dedac-112">Nessuna.</span><span class="sxs-lookup"><span data-stu-id="dedac-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="dedac-113">Elementi padre</span><span class="sxs-lookup"><span data-stu-id="dedac-113">Parent Elements</span></span>

|<span data-ttu-id="dedac-114">Elemento</span><span class="sxs-lookup"><span data-stu-id="dedac-114">Element</span></span>|<span data-ttu-id="dedac-115">Description</span><span class="sxs-lookup"><span data-stu-id="dedac-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="dedac-116">Elemento frame per CustomItem per i controlli per la configurazione (Format)</span><span class="sxs-lookup"><span data-stu-id="dedac-116">Frame Element for CustomItem for Controls for Configuration (Format)</span></span>](./frame-element-for-customitem-for-controls-for-configuration-format.md)|<span data-ttu-id="dedac-117">Definisce la modalità di visualizzazione dei dati, ad esempio lo spostamento dei dati verso sinistra o verso destra.</span><span class="sxs-lookup"><span data-stu-id="dedac-117">Defines how the data is displayed, such as shifting the data to the left or right.</span></span>|

## <a name="text-value"></a><span data-ttu-id="dedac-118">Valore testo</span><span class="sxs-lookup"><span data-stu-id="dedac-118">Text Value</span></span>

<span data-ttu-id="dedac-119">Consente di specificare il numero di caratteri che si desidera spostare nella prima riga dei dati.</span><span class="sxs-lookup"><span data-stu-id="dedac-119">Specify the number of characters that you want to shift the first line of the data.</span></span>

## <a name="remarks"></a><span data-ttu-id="dedac-120">Osservazioni</span><span class="sxs-lookup"><span data-stu-id="dedac-120">Remarks</span></span>

<span data-ttu-id="dedac-121">Se questo elemento è specificato, non è possibile specificare l'elemento `FirstLineIndent`.</span><span class="sxs-lookup"><span data-stu-id="dedac-121">If this element is specified, you cannot specify the `FirstLineIndent` element.</span></span>

## <a name="see-also"></a><span data-ttu-id="dedac-122">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="dedac-122">See Also</span></span>

[<span data-ttu-id="dedac-123">Elemento frame per CustomItem per i controlli per la configurazione (Format)</span><span class="sxs-lookup"><span data-stu-id="dedac-123">Frame Element for CustomItem for Controls for Configuration (Format)</span></span>](./frame-element-for-customitem-for-controls-for-configuration-format.md)

[<span data-ttu-id="dedac-124">Scrittura di un file di formattazione di PowerShell</span><span class="sxs-lookup"><span data-stu-id="dedac-124">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
