---
title: Elemento FirstLineIndent per Frame per i controlli per la configurazione (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 2f489720-11f6-4019-940e-07f423d4278d
caps.latest.revision: 6
ms.openlocfilehash: c5b2d971fe1590116f96b024ae8769334768acf2
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62065989"
---
# <a name="firstlineindent-element-for-frame-for-controls-for-configuration-format"></a><span data-ttu-id="57605-102">Elemento FirstLineIndent per Frame per Controls per Configuration (formato)</span><span class="sxs-lookup"><span data-stu-id="57605-102">FirstLineIndent Element for Frame for Controls for Configuration (Format)</span></span>

<span data-ttu-id="57605-103">Specifica il numero di caratteri la prima riga di dati verrà spostata a destra.</span><span class="sxs-lookup"><span data-stu-id="57605-103">Specifies how many characters the first line of data is shifted to the right.</span></span> <span data-ttu-id="57605-104">Questo elemento viene usato quando si definisce un controllo comune che può essere usato da tutte le visualizzazioni nel file di formattazione.</span><span class="sxs-lookup"><span data-stu-id="57605-104">This element is used when defining a common control that can be used by all the views in the formatting file.</span></span>

<span data-ttu-id="57605-105">Configurazione (formato) i controlli elemento di configurazione (formato) elemento di controllo per i controlli di configurazione (formato) CustomControl elemento per il controllo per elemento di configurazione (formato) CustomEntries per CustomControl per Configuration ( Elemento CustomEntry Format) per CustomControl per i controlli per elemento di configurazione (formato) CustomItem per CustomEntry per i controlli per la configurazione elemento Frame per CustomItem per i controlli per elemento di configurazione (formato) FirstLineIndent per Frame per i controlli per la configurazione (formato)</span><span class="sxs-lookup"><span data-stu-id="57605-105">Configuration Element (Format) Controls Element of Configuration (Format) Control Element for Controls for Configuration (Format) CustomControl Element for Control for Configuration (Format) CustomEntries Element for CustomControl for Configuration (Format) CustomEntry Element for CustomControl for Controls for Configuration (Format) CustomItem Element for CustomEntry for Controls for Configuration Frame Element for CustomItem for Controls for Configuration (Format) FirstLineIndent Element for Frame for Controls for Configuration (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="57605-106">Sintassi</span><span class="sxs-lookup"><span data-stu-id="57605-106">Syntax</span></span>

```xml
<FirstLineIndent>NumberOfCharactersToShift</FirstLineIndent>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="57605-107">Elementi e attributi</span><span class="sxs-lookup"><span data-stu-id="57605-107">Attributes and Elements</span></span>

<span data-ttu-id="57605-108">Le sezioni seguenti descrivono l'elemento padre di attributi e gli elementi figlio di `FirstLineIndent` elemento.</span><span class="sxs-lookup"><span data-stu-id="57605-108">The following sections describe attributes, child elements, and parent element of the `FirstLineIndent` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="57605-109">Attributes</span><span class="sxs-lookup"><span data-stu-id="57605-109">Attributes</span></span>

<span data-ttu-id="57605-110">Nessuna.</span><span class="sxs-lookup"><span data-stu-id="57605-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="57605-111">Elementi figlio</span><span class="sxs-lookup"><span data-stu-id="57605-111">Child Elements</span></span>

<span data-ttu-id="57605-112">Nessuna.</span><span class="sxs-lookup"><span data-stu-id="57605-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="57605-113">Elementi padre</span><span class="sxs-lookup"><span data-stu-id="57605-113">Parent Elements</span></span>

|<span data-ttu-id="57605-114">Elemento</span><span class="sxs-lookup"><span data-stu-id="57605-114">Element</span></span>|<span data-ttu-id="57605-115">Description</span><span class="sxs-lookup"><span data-stu-id="57605-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="57605-116">Elemento frame per CustomItem per i controlli per la configurazione (formato)</span><span class="sxs-lookup"><span data-stu-id="57605-116">Frame Element for CustomItem for Controls for Configuration (Format)</span></span>](./frame-element-for-customitem-for-controls-for-configuration-format.md)|<span data-ttu-id="57605-117">Definisce come verranno visualizzati i dati, ad esempio lo spostamento di dati a sinistra o destra.</span><span class="sxs-lookup"><span data-stu-id="57605-117">Defines how the data is displayed, such as shifting the data to the left or right.</span></span>|

## <a name="text-value"></a><span data-ttu-id="57605-118">Valore di testo</span><span class="sxs-lookup"><span data-stu-id="57605-118">Text Value</span></span>

<span data-ttu-id="57605-119">Specificare il numero di caratteri che si desidera spostare la prima riga dei dati.</span><span class="sxs-lookup"><span data-stu-id="57605-119">Specify the number of characters that you want to shift the first line of the data.</span></span>

## <a name="remarks"></a><span data-ttu-id="57605-120">Osservazioni</span><span class="sxs-lookup"><span data-stu-id="57605-120">Remarks</span></span>

<span data-ttu-id="57605-121">Se questo elemento viene specificato, non è possibile specificare il [FirstLineHanging](./firstlinehanging-element-for-frame-for-controls-for-configuration-format.md) elemento.</span><span class="sxs-lookup"><span data-stu-id="57605-121">If this element is specified, you cannot specify the [FirstLineHanging](./firstlinehanging-element-for-frame-for-controls-for-configuration-format.md) element.</span></span>

## <a name="see-also"></a><span data-ttu-id="57605-122">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="57605-122">See Also</span></span>

[<span data-ttu-id="57605-123">Elemento FirstLineHanging per Frame per i controlli per la configurazione (formato)</span><span class="sxs-lookup"><span data-stu-id="57605-123">FirstLineHanging Element for Frame for Controls for Configuration (Format)</span></span>](./firstlinehanging-element-for-frame-for-controls-for-configuration-format.md)

[<span data-ttu-id="57605-124">Elemento frame per CustomItem per i controlli per la configurazione (formato)</span><span class="sxs-lookup"><span data-stu-id="57605-124">Frame Element for CustomItem for Controls for Configuration (Format)</span></span>](./frame-element-for-customitem-for-controls-for-configuration-format.md)

[<span data-ttu-id="57605-125">La scrittura di un File di formattazione di PowerShell</span><span class="sxs-lookup"><span data-stu-id="57605-125">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
