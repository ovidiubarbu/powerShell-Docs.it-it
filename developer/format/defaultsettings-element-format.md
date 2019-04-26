---
title: Elemento DefaultSettings (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 41c56499-ee20-4821-830a-478fdcc33f83
caps.latest.revision: 11
ms.openlocfilehash: bc95c62222eb2806f92499257a397c2e4ec5dbab
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62066346"
---
# <a name="defaultsettings-element-format"></a><span data-ttu-id="5413d-102">Elemento DefaultSettings (formato)</span><span class="sxs-lookup"><span data-stu-id="5413d-102">DefaultSettings Element (Format)</span></span>

<span data-ttu-id="5413d-103">Definisce le impostazioni comuni che si applicano a tutte le visualizzazioni del file di formattazione.</span><span class="sxs-lookup"><span data-stu-id="5413d-103">Defines common settings that apply to all the views of the formatting file.</span></span> <span data-ttu-id="5413d-104">Impostazioni comuni includono la visualizzazione di errori, la disposizione del testo in tabelle, che definisce come vengono espanse le raccolte e così via.</span><span class="sxs-lookup"><span data-stu-id="5413d-104">Common settings include displaying errors, wrapping text in tables, defining how collections are expanded, and more.</span></span>

<span data-ttu-id="5413d-105">Elemento di configurazione elemento (formato) DefaultSettings (formato)</span><span class="sxs-lookup"><span data-stu-id="5413d-105">Configuration Element (Format) DefaultSettings Element (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="5413d-106">Sintassi</span><span class="sxs-lookup"><span data-stu-id="5413d-106">Syntax</span></span>

```xml
<DefaultSettings>
  <ShowError/>
  <DisplayError/>
 <PropertyCountForTable>NumberOfProperties</PropertyCountFortable>
  <WrapTables/>
  <EnumerableExpansions>...</EnumerableExpansions>
</DefaultSettings>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="5413d-107">Elementi e attributi</span><span class="sxs-lookup"><span data-stu-id="5413d-107">Attributes and Elements</span></span>

<span data-ttu-id="5413d-108">Le sezioni seguenti descrivono gli attributi e gli elementi figlio dell'elemento padre del `DefaultSettings` elemento.</span><span class="sxs-lookup"><span data-stu-id="5413d-108">The following sections describe attributes, child elements, and the parent element of the `DefaultSettings` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="5413d-109">Attributes</span><span class="sxs-lookup"><span data-stu-id="5413d-109">Attributes</span></span>

<span data-ttu-id="5413d-110">Nessuna.</span><span class="sxs-lookup"><span data-stu-id="5413d-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="5413d-111">Elementi figlio</span><span class="sxs-lookup"><span data-stu-id="5413d-111">Child Elements</span></span>

|<span data-ttu-id="5413d-112">Elemento</span><span class="sxs-lookup"><span data-stu-id="5413d-112">Element</span></span>|<span data-ttu-id="5413d-113">Description</span><span class="sxs-lookup"><span data-stu-id="5413d-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="5413d-114">Elemento DisplayError (formato)</span><span class="sxs-lookup"><span data-stu-id="5413d-114">DisplayError Element (Format)</span></span>](./displayerror-element-format.md)|<span data-ttu-id="5413d-115">Elemento facoltativo.</span><span class="sxs-lookup"><span data-stu-id="5413d-115">Optional element.</span></span><br /><br /> <span data-ttu-id="5413d-116">Specifica che la stringa #ERR viene visualizzata quando si verifica un errore durante la visualizzazione di una porzione di dati.</span><span class="sxs-lookup"><span data-stu-id="5413d-116">Specifies that the string #ERR is displayed when an error occurs while displaying a piece of data.</span></span>|
|[<span data-ttu-id="5413d-117">Elemento EnumerableExpansions (formato)</span><span class="sxs-lookup"><span data-stu-id="5413d-117">EnumerableExpansions Element (Format)</span></span>](./enumerableexpansions-element-format.md)|<span data-ttu-id="5413d-118">Elemento facoltativo.</span><span class="sxs-lookup"><span data-stu-id="5413d-118">Optional element.</span></span><br /><br /> <span data-ttu-id="5413d-119">Definisce i diversi modi in cui gli oggetti .NET vengono espanse quando vengono visualizzati in una vista.</span><span class="sxs-lookup"><span data-stu-id="5413d-119">Defines the different ways that .NET objects are expanded when they are displayed in a view.</span></span>|
|[<span data-ttu-id="5413d-120">PropertyCountForTable (formato)</span><span class="sxs-lookup"><span data-stu-id="5413d-120">PropertyCountForTable (Format)</span></span>](./propertycountfortable-element-format.md)|<span data-ttu-id="5413d-121">Elemento facoltativo.</span><span class="sxs-lookup"><span data-stu-id="5413d-121">Optional element.</span></span><br /><br /> <span data-ttu-id="5413d-122">Specifica il numero minimo di proprietà che deve avere un oggetto per visualizzare l'oggetto in una visualizzazione tabella.</span><span class="sxs-lookup"><span data-stu-id="5413d-122">Specifies the minimum number of properties that an object must have to display the object in a table view.</span></span>|
|[<span data-ttu-id="5413d-123">Elemento ShowError (formato)</span><span class="sxs-lookup"><span data-stu-id="5413d-123">ShowError Element (Format)</span></span>](./showerror-element-format.md)|<span data-ttu-id="5413d-124">Elemento facoltativo.</span><span class="sxs-lookup"><span data-stu-id="5413d-124">Optional element.</span></span><br /><br /> <span data-ttu-id="5413d-125">Specifica che il record di errore completo viene visualizzato quando si verifica un errore durante la visualizzazione di una porzione di dati.</span><span class="sxs-lookup"><span data-stu-id="5413d-125">Specifies that the full error record is displayed when an error occurs while displaying a piece of data.</span></span>|
|[<span data-ttu-id="5413d-126">Elemento WrapTables (formato)</span><span class="sxs-lookup"><span data-stu-id="5413d-126">WrapTables Element (Format)</span></span>](./wraptables-element-format.md)|<span data-ttu-id="5413d-127">Elemento facoltativo.</span><span class="sxs-lookup"><span data-stu-id="5413d-127">Optional element.</span></span><br /><br /> <span data-ttu-id="5413d-128">Specifica che i dati in una tabella vengano spostati alla riga successiva se non adattarsi alla larghezza della colonna.</span><span class="sxs-lookup"><span data-stu-id="5413d-128">Specifies that data in a table is moved to the next line if it does not fit into the width of the column.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="5413d-129">Elementi padre</span><span class="sxs-lookup"><span data-stu-id="5413d-129">Parent Elements</span></span>

|<span data-ttu-id="5413d-130">Elemento</span><span class="sxs-lookup"><span data-stu-id="5413d-130">Element</span></span>|<span data-ttu-id="5413d-131">Description</span><span class="sxs-lookup"><span data-stu-id="5413d-131">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="5413d-132">Elemento di configurazione</span><span class="sxs-lookup"><span data-stu-id="5413d-132">Configuration Element</span></span>](./configuration-element-format.md)|<span data-ttu-id="5413d-133">Rappresenta l'elemento di livello superiore di un file di formattazione.</span><span class="sxs-lookup"><span data-stu-id="5413d-133">Represents the top-level element of a formatting file.</span></span>|

## <a name="remarks"></a><span data-ttu-id="5413d-134">Osservazioni</span><span class="sxs-lookup"><span data-stu-id="5413d-134">Remarks</span></span>

## <a name="see-also"></a><span data-ttu-id="5413d-135">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="5413d-135">See Also</span></span>

[<span data-ttu-id="5413d-136">Elemento di configurazione</span><span class="sxs-lookup"><span data-stu-id="5413d-136">Configuration Element</span></span>](./configuration-element-format.md)

[<span data-ttu-id="5413d-137">Elemento DisplayError (formato)</span><span class="sxs-lookup"><span data-stu-id="5413d-137">DisplayError Element (Format)</span></span>](./displayerror-element-format.md)

[<span data-ttu-id="5413d-138">Elemento EnumerableExpansions (formato)</span><span class="sxs-lookup"><span data-stu-id="5413d-138">EnumerableExpansions Element (Format)</span></span>](./enumerableexpansions-element-format.md)

[<span data-ttu-id="5413d-139">PropertyCountForTable (formato)</span><span class="sxs-lookup"><span data-stu-id="5413d-139">PropertyCountForTable (Format)</span></span>](./propertycountfortable-element-format.md)

[<span data-ttu-id="5413d-140">Elemento ShowError (formato)</span><span class="sxs-lookup"><span data-stu-id="5413d-140">ShowError Element (Format)</span></span>](./showerror-element-format.md)

[<span data-ttu-id="5413d-141">Elemento WrapTables (formato)</span><span class="sxs-lookup"><span data-stu-id="5413d-141">WrapTables Element (Format)</span></span>](./wraptables-element-format.md)

[<span data-ttu-id="5413d-142">La scrittura di un File di formattazione di PowerShell</span><span class="sxs-lookup"><span data-stu-id="5413d-142">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
