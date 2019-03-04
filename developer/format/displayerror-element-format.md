---
title: Elemento DisplayError (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 45c45800-a87d-456e-b07c-12d4d8c27c67
caps.latest.revision: 8
ms.openlocfilehash: 431e5d8407b9f689a5224b329d8c7b52802e19e1
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/03/2019
ms.locfileid: "56854917"
---
# <a name="displayerror-element-format"></a><span data-ttu-id="8aa0d-102">Elemento DisplayError (formato)</span><span class="sxs-lookup"><span data-stu-id="8aa0d-102">DisplayError Element (Format)</span></span>

<span data-ttu-id="8aa0d-103">Specifica che la stringa #ERR viene visualizzata quando si verifica un errore la visualizzazione di una porzione di dati.</span><span class="sxs-lookup"><span data-stu-id="8aa0d-103">Specifies that the string #ERR is displayed when an error occurs displaying a piece of data.</span></span>

<span data-ttu-id="8aa0d-104">Configurazione (formato) elemento DefaultSettings (formato) DisplayError elemento (Frmat)</span><span class="sxs-lookup"><span data-stu-id="8aa0d-104">Configuration Element (Format) DefaultSettings Element (Format) DisplayError Element (Frmat)</span></span>

## <a name="syntax"></a><span data-ttu-id="8aa0d-105">Sintassi</span><span class="sxs-lookup"><span data-stu-id="8aa0d-105">Syntax</span></span>

```xml
<DisplayError/>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="8aa0d-106">Attributi ed elementi</span><span class="sxs-lookup"><span data-stu-id="8aa0d-106">Attributes and Elements</span></span>

<span data-ttu-id="8aa0d-107">Le sezioni seguenti descrivono gli attributi e gli elementi figlio dell'elemento padre del `DisplayError` elemento.</span><span class="sxs-lookup"><span data-stu-id="8aa0d-107">The following sections describe attributes, child elements, and the parent element of the `DisplayError` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="8aa0d-108">Attributes</span><span class="sxs-lookup"><span data-stu-id="8aa0d-108">Attributes</span></span>

<span data-ttu-id="8aa0d-109">Nessuna.</span><span class="sxs-lookup"><span data-stu-id="8aa0d-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="8aa0d-110">Elementi figlio</span><span class="sxs-lookup"><span data-stu-id="8aa0d-110">Child Elements</span></span>

<span data-ttu-id="8aa0d-111">Nessuna.</span><span class="sxs-lookup"><span data-stu-id="8aa0d-111">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="8aa0d-112">Elementi padre</span><span class="sxs-lookup"><span data-stu-id="8aa0d-112">Parent Elements</span></span>

|<span data-ttu-id="8aa0d-113">Elemento</span><span class="sxs-lookup"><span data-stu-id="8aa0d-113">Element</span></span>|<span data-ttu-id="8aa0d-114">Description</span><span class="sxs-lookup"><span data-stu-id="8aa0d-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="8aa0d-115">Elemento DefaultSettings (formato)</span><span class="sxs-lookup"><span data-stu-id="8aa0d-115">DefaultSettings Element (Format)</span></span>](./defaultsettings-element-format.md)|<span data-ttu-id="8aa0d-116">Definisce le impostazioni comuni che si applicano a tutte le visualizzazioni del file di formattazione.</span><span class="sxs-lookup"><span data-stu-id="8aa0d-116">Defines common settings that apply to all the views of the formatting file.</span></span>|

## <a name="remarks"></a><span data-ttu-id="8aa0d-117">Osservazioni</span><span class="sxs-lookup"><span data-stu-id="8aa0d-117">Remarks</span></span>

<span data-ttu-id="8aa0d-118">Per impostazione predefinita, quando si verifica un errore durante il tentativo di visualizzare una porzione di dati, è possibile che il percorso dei dati viene lasciato vuoto.</span><span class="sxs-lookup"><span data-stu-id="8aa0d-118">By default, when an error occurs while trying to display a piece of data, the location of the data is left blank.</span></span> <span data-ttu-id="8aa0d-119">Quando questo elemento è impostato su true, la stringa #ERR verrà visualizzato.</span><span class="sxs-lookup"><span data-stu-id="8aa0d-119">When this element is set to true, the #ERR string will be displayed.</span></span>

## <a name="see-also"></a><span data-ttu-id="8aa0d-120">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="8aa0d-120">See Also</span></span>

[<span data-ttu-id="8aa0d-121">Elemento DefaultSettings (formato)</span><span class="sxs-lookup"><span data-stu-id="8aa0d-121">DefaultSettings Element (Format)</span></span>](./defaultsettings-element-format.md)

[<span data-ttu-id="8aa0d-122">La scrittura di un File di formattazione di PowerShell</span><span class="sxs-lookup"><span data-stu-id="8aa0d-122">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
