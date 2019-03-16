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
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/16/2019
ms.locfileid: "58059066"
---
# <a name="defaultsettings-element-format"></a><span data-ttu-id="935dd-102">Elemento DefaultSettings (formato)</span><span class="sxs-lookup"><span data-stu-id="935dd-102">DefaultSettings Element (Format)</span></span>

<span data-ttu-id="935dd-103">Definisce le impostazioni comuni che si applicano a tutte le visualizzazioni del file di formattazione.</span><span class="sxs-lookup"><span data-stu-id="935dd-103">Defines common settings that apply to all the views of the formatting file.</span></span> <span data-ttu-id="935dd-104">Impostazioni comuni includono la visualizzazione di errori, la disposizione del testo in tabelle, che definisce come vengono espanse le raccolte e così via.</span><span class="sxs-lookup"><span data-stu-id="935dd-104">Common settings include displaying errors, wrapping text in tables, defining how collections are expanded, and more.</span></span>

<span data-ttu-id="935dd-105">Elemento di configurazione elemento (formato) DefaultSettings (formato)</span><span class="sxs-lookup"><span data-stu-id="935dd-105">Configuration Element (Format) DefaultSettings Element (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="935dd-106">Sintassi</span><span class="sxs-lookup"><span data-stu-id="935dd-106">Syntax</span></span>

```xml
<DefaultSettings>
  <ShowError/>
  <DisplayError/>
 <PropertyCountForTable>NumberOfProperties</PropertyCountFortable>
  <WrapTables/>
  <EnumerableExpansions>...</EnumerableExpansions>
</DefaultSettings>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="935dd-107">Attributi ed elementi</span><span class="sxs-lookup"><span data-stu-id="935dd-107">Attributes and Elements</span></span>

<span data-ttu-id="935dd-108">Le sezioni seguenti descrivono gli attributi e gli elementi figlio dell'elemento padre del `DefaultSettings` elemento.</span><span class="sxs-lookup"><span data-stu-id="935dd-108">The following sections describe attributes, child elements, and the parent element of the `DefaultSettings` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="935dd-109">Attributes</span><span class="sxs-lookup"><span data-stu-id="935dd-109">Attributes</span></span>

<span data-ttu-id="935dd-110">Nessuna.</span><span class="sxs-lookup"><span data-stu-id="935dd-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="935dd-111">Elementi figlio</span><span class="sxs-lookup"><span data-stu-id="935dd-111">Child Elements</span></span>

|<span data-ttu-id="935dd-112">Elemento</span><span class="sxs-lookup"><span data-stu-id="935dd-112">Element</span></span>|<span data-ttu-id="935dd-113">Description</span><span class="sxs-lookup"><span data-stu-id="935dd-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="935dd-114">Elemento DisplayError (formato)</span><span class="sxs-lookup"><span data-stu-id="935dd-114">DisplayError Element (Format)</span></span>](./displayerror-element-format.md)|<span data-ttu-id="935dd-115">Elemento facoltativo.</span><span class="sxs-lookup"><span data-stu-id="935dd-115">Optional element.</span></span><br /><br /> <span data-ttu-id="935dd-116">Specifica che la stringa #ERR viene visualizzata quando si verifica un errore durante la visualizzazione di una porzione di dati.</span><span class="sxs-lookup"><span data-stu-id="935dd-116">Specifies that the string #ERR is displayed when an error occurs while displaying a piece of data.</span></span>|
|[<span data-ttu-id="935dd-117">Elemento EnumerableExpansions (formato)</span><span class="sxs-lookup"><span data-stu-id="935dd-117">EnumerableExpansions Element (Format)</span></span>](./enumerableexpansions-element-format.md)|<span data-ttu-id="935dd-118">Elemento facoltativo.</span><span class="sxs-lookup"><span data-stu-id="935dd-118">Optional element.</span></span><br /><br /> <span data-ttu-id="935dd-119">Definisce i diversi modi in cui gli oggetti .NET vengono espanse quando vengono visualizzati in una vista.</span><span class="sxs-lookup"><span data-stu-id="935dd-119">Defines the different ways that .NET objects are expanded when they are displayed in a view.</span></span>|
|[<span data-ttu-id="935dd-120">PropertyCountForTable (formato)</span><span class="sxs-lookup"><span data-stu-id="935dd-120">PropertyCountForTable (Format)</span></span>](./propertycountfortable-element-format.md)|<span data-ttu-id="935dd-121">Elemento facoltativo.</span><span class="sxs-lookup"><span data-stu-id="935dd-121">Optional element.</span></span><br /><br /> <span data-ttu-id="935dd-122">Specifica il numero minimo di proprietà che deve avere un oggetto per visualizzare l'oggetto in una visualizzazione tabella.</span><span class="sxs-lookup"><span data-stu-id="935dd-122">Specifies the minimum number of properties that an object must have to display the object in a table view.</span></span>|
|[<span data-ttu-id="935dd-123">Elemento ShowError (formato)</span><span class="sxs-lookup"><span data-stu-id="935dd-123">ShowError Element (Format)</span></span>](./showerror-element-format.md)|<span data-ttu-id="935dd-124">Elemento facoltativo.</span><span class="sxs-lookup"><span data-stu-id="935dd-124">Optional element.</span></span><br /><br /> <span data-ttu-id="935dd-125">Specifica che il record di errore completo viene visualizzato quando si verifica un errore durante la visualizzazione di una porzione di dati.</span><span class="sxs-lookup"><span data-stu-id="935dd-125">Specifies that the full error record is displayed when an error occurs while displaying a piece of data.</span></span>|
|[<span data-ttu-id="935dd-126">Elemento WrapTables (formato)</span><span class="sxs-lookup"><span data-stu-id="935dd-126">WrapTables Element (Format)</span></span>](./wraptables-element-format.md)|<span data-ttu-id="935dd-127">Elemento facoltativo.</span><span class="sxs-lookup"><span data-stu-id="935dd-127">Optional element.</span></span><br /><br /> <span data-ttu-id="935dd-128">Specifica che i dati in una tabella vengano spostati alla riga successiva se non adattarsi alla larghezza della colonna.</span><span class="sxs-lookup"><span data-stu-id="935dd-128">Specifies that data in a table is moved to the next line if it does not fit into the width of the column.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="935dd-129">Elementi padre</span><span class="sxs-lookup"><span data-stu-id="935dd-129">Parent Elements</span></span>

|<span data-ttu-id="935dd-130">Elemento</span><span class="sxs-lookup"><span data-stu-id="935dd-130">Element</span></span>|<span data-ttu-id="935dd-131">Description</span><span class="sxs-lookup"><span data-stu-id="935dd-131">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="935dd-132">Elemento di configurazione</span><span class="sxs-lookup"><span data-stu-id="935dd-132">Configuration Element</span></span>](./configuration-element-format.md)|<span data-ttu-id="935dd-133">Rappresenta l'elemento di livello superiore di un file di formattazione.</span><span class="sxs-lookup"><span data-stu-id="935dd-133">Represents the top-level element of a formatting file.</span></span>|

## <a name="remarks"></a><span data-ttu-id="935dd-134">Osservazioni</span><span class="sxs-lookup"><span data-stu-id="935dd-134">Remarks</span></span>

## <a name="see-also"></a><span data-ttu-id="935dd-135">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="935dd-135">See Also</span></span>

[<span data-ttu-id="935dd-136">Elemento di configurazione</span><span class="sxs-lookup"><span data-stu-id="935dd-136">Configuration Element</span></span>](./configuration-element-format.md)

[<span data-ttu-id="935dd-137">Elemento DisplayError (formato)</span><span class="sxs-lookup"><span data-stu-id="935dd-137">DisplayError Element (Format)</span></span>](./displayerror-element-format.md)

[<span data-ttu-id="935dd-138">Elemento EnumerableExpansions (formato)</span><span class="sxs-lookup"><span data-stu-id="935dd-138">EnumerableExpansions Element (Format)</span></span>](./enumerableexpansions-element-format.md)

[<span data-ttu-id="935dd-139">PropertyCountForTable (formato)</span><span class="sxs-lookup"><span data-stu-id="935dd-139">PropertyCountForTable (Format)</span></span>](./propertycountfortable-element-format.md)

[<span data-ttu-id="935dd-140">Elemento ShowError (formato)</span><span class="sxs-lookup"><span data-stu-id="935dd-140">ShowError Element (Format)</span></span>](./showerror-element-format.md)

[<span data-ttu-id="935dd-141">Elemento WrapTables (formato)</span><span class="sxs-lookup"><span data-stu-id="935dd-141">WrapTables Element (Format)</span></span>](./wraptables-element-format.md)

[<span data-ttu-id="935dd-142">La scrittura di un File di formattazione di PowerShell</span><span class="sxs-lookup"><span data-stu-id="935dd-142">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
