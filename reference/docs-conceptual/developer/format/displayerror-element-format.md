---
title: Elemento DisplayError (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 45c45800-a87d-456e-b07c-12d4d8c27c67
caps.latest.revision: 8
ms.openlocfilehash: 2c6a3d678ca68dc0d189f6ab981fdea5fef894cb
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/05/2019
ms.locfileid: "72363990"
---
# <a name="displayerror-element-format"></a><span data-ttu-id="b939f-102">Elemento DisplayError (formato)</span><span class="sxs-lookup"><span data-stu-id="b939f-102">DisplayError Element (Format)</span></span>

<span data-ttu-id="b939f-103">Specifica che la stringa #ERR viene visualizzata quando si verifica un errore durante la visualizzazione di una porzione di dati.</span><span class="sxs-lookup"><span data-stu-id="b939f-103">Specifies that the string #ERR is displayed when an error occurs displaying a piece of data.</span></span>

<span data-ttu-id="b939f-104">Elemento Configuration (Format) elemento DefaultSettings (Format) elemento DisplayError (Format)</span><span class="sxs-lookup"><span data-stu-id="b939f-104">Configuration Element (Format) DefaultSettings Element (Format) DisplayError Element (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="b939f-105">Sintassi</span><span class="sxs-lookup"><span data-stu-id="b939f-105">Syntax</span></span>

```xml
<DisplayError/>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="b939f-106">Attributi ed elementi</span><span class="sxs-lookup"><span data-stu-id="b939f-106">Attributes and Elements</span></span>

<span data-ttu-id="b939f-107">Nelle sezioni seguenti vengono descritti gli attributi, gli elementi figlio e l'elemento padre dell'elemento `DisplayError`.</span><span class="sxs-lookup"><span data-stu-id="b939f-107">The following sections describe attributes, child elements, and the parent element of the `DisplayError` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="b939f-108">Attributi</span><span class="sxs-lookup"><span data-stu-id="b939f-108">Attributes</span></span>

<span data-ttu-id="b939f-109">Nessuna.</span><span class="sxs-lookup"><span data-stu-id="b939f-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="b939f-110">Elementi figlio</span><span class="sxs-lookup"><span data-stu-id="b939f-110">Child Elements</span></span>

<span data-ttu-id="b939f-111">Nessuna.</span><span class="sxs-lookup"><span data-stu-id="b939f-111">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="b939f-112">Elementi padre</span><span class="sxs-lookup"><span data-stu-id="b939f-112">Parent Elements</span></span>

|<span data-ttu-id="b939f-113">Elemento</span><span class="sxs-lookup"><span data-stu-id="b939f-113">Element</span></span>|<span data-ttu-id="b939f-114">Description</span><span class="sxs-lookup"><span data-stu-id="b939f-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="b939f-115">Elemento DefaultSettings (Format)</span><span class="sxs-lookup"><span data-stu-id="b939f-115">DefaultSettings Element (Format)</span></span>](./defaultsettings-element-format.md)|<span data-ttu-id="b939f-116">Definisce le impostazioni comuni che si applicano a tutte le visualizzazioni del file di formattazione.</span><span class="sxs-lookup"><span data-stu-id="b939f-116">Defines common settings that apply to all the views of the formatting file.</span></span>|

## <a name="remarks"></a><span data-ttu-id="b939f-117">Osservazioni</span><span class="sxs-lookup"><span data-stu-id="b939f-117">Remarks</span></span>

<span data-ttu-id="b939f-118">Per impostazione predefinita, quando si verifica un errore durante il tentativo di visualizzare una porzione di dati, la posizione dei dati viene lasciata vuota.</span><span class="sxs-lookup"><span data-stu-id="b939f-118">By default, when an error occurs while trying to display a piece of data, the location of the data is left blank.</span></span> <span data-ttu-id="b939f-119">Quando questo elemento è impostato su true, viene visualizzata la stringa #ERR.</span><span class="sxs-lookup"><span data-stu-id="b939f-119">When this element is set to true, the #ERR string will be displayed.</span></span>

## <a name="see-also"></a><span data-ttu-id="b939f-120">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="b939f-120">See Also</span></span>

[<span data-ttu-id="b939f-121">Elemento DefaultSettings (Format)</span><span class="sxs-lookup"><span data-stu-id="b939f-121">DefaultSettings Element (Format)</span></span>](./defaultsettings-element-format.md)

[<span data-ttu-id="b939f-122">Scrittura di un file di formattazione di PowerShell</span><span class="sxs-lookup"><span data-stu-id="b939f-122">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
