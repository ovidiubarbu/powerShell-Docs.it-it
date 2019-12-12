---
title: Elemento DefaultSettings (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 41c56499-ee20-4821-830a-478fdcc33f83
caps.latest.revision: 11
ms.openlocfilehash: bc95c62222eb2806f92499257a397c2e4ec5dbab
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/05/2019
ms.locfileid: "72363870"
---
# <a name="defaultsettings-element-format"></a><span data-ttu-id="9aa8f-102">Elemento DefaultSettings (formato)</span><span class="sxs-lookup"><span data-stu-id="9aa8f-102">DefaultSettings Element (Format)</span></span>

<span data-ttu-id="9aa8f-103">Definisce le impostazioni comuni che si applicano a tutte le visualizzazioni del file di formattazione.</span><span class="sxs-lookup"><span data-stu-id="9aa8f-103">Defines common settings that apply to all the views of the formatting file.</span></span> <span data-ttu-id="9aa8f-104">Le impostazioni comuni includono la visualizzazione di errori, il wrapping del testo nelle tabelle, la definizione del modo in cui le raccolte vengono espanse e altro.</span><span class="sxs-lookup"><span data-stu-id="9aa8f-104">Common settings include displaying errors, wrapping text in tables, defining how collections are expanded, and more.</span></span>

<span data-ttu-id="9aa8f-105">Elemento Configuration (Format) elemento DefaultSettings (Format)</span><span class="sxs-lookup"><span data-stu-id="9aa8f-105">Configuration Element (Format) DefaultSettings Element (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="9aa8f-106">Sintassi</span><span class="sxs-lookup"><span data-stu-id="9aa8f-106">Syntax</span></span>

```xml
<DefaultSettings>
  <ShowError/>
  <DisplayError/>
 <PropertyCountForTable>NumberOfProperties</PropertyCountFortable>
  <WrapTables/>
  <EnumerableExpansions>...</EnumerableExpansions>
</DefaultSettings>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="9aa8f-107">Attributi ed elementi</span><span class="sxs-lookup"><span data-stu-id="9aa8f-107">Attributes and Elements</span></span>

<span data-ttu-id="9aa8f-108">Nelle sezioni seguenti vengono descritti gli attributi, gli elementi figlio e l'elemento padre dell'elemento `DefaultSettings`.</span><span class="sxs-lookup"><span data-stu-id="9aa8f-108">The following sections describe attributes, child elements, and the parent element of the `DefaultSettings` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="9aa8f-109">Attributi</span><span class="sxs-lookup"><span data-stu-id="9aa8f-109">Attributes</span></span>

<span data-ttu-id="9aa8f-110">Nessuna.</span><span class="sxs-lookup"><span data-stu-id="9aa8f-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="9aa8f-111">Elementi figlio</span><span class="sxs-lookup"><span data-stu-id="9aa8f-111">Child Elements</span></span>

|<span data-ttu-id="9aa8f-112">Elemento</span><span class="sxs-lookup"><span data-stu-id="9aa8f-112">Element</span></span>|<span data-ttu-id="9aa8f-113">Description</span><span class="sxs-lookup"><span data-stu-id="9aa8f-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="9aa8f-114">Elemento DisplayError (Format)</span><span class="sxs-lookup"><span data-stu-id="9aa8f-114">DisplayError Element (Format)</span></span>](./displayerror-element-format.md)|<span data-ttu-id="9aa8f-115">Elemento facoltativo.</span><span class="sxs-lookup"><span data-stu-id="9aa8f-115">Optional element.</span></span><br /><br /> <span data-ttu-id="9aa8f-116">Specifica che la stringa #ERR viene visualizzata quando si verifica un errore durante la visualizzazione di una porzione di dati.</span><span class="sxs-lookup"><span data-stu-id="9aa8f-116">Specifies that the string #ERR is displayed when an error occurs while displaying a piece of data.</span></span>|
|[<span data-ttu-id="9aa8f-117">Elemento EnumerableExpansions (Format)</span><span class="sxs-lookup"><span data-stu-id="9aa8f-117">EnumerableExpansions Element (Format)</span></span>](./enumerableexpansions-element-format.md)|<span data-ttu-id="9aa8f-118">Elemento facoltativo.</span><span class="sxs-lookup"><span data-stu-id="9aa8f-118">Optional element.</span></span><br /><br /> <span data-ttu-id="9aa8f-119">Definisce le diverse modalità di espansione degli oggetti .NET quando vengono visualizzati in una visualizzazione.</span><span class="sxs-lookup"><span data-stu-id="9aa8f-119">Defines the different ways that .NET objects are expanded when they are displayed in a view.</span></span>|
|[<span data-ttu-id="9aa8f-120">PropertyCountForTable (formato)</span><span class="sxs-lookup"><span data-stu-id="9aa8f-120">PropertyCountForTable (Format)</span></span>](./propertycountfortable-element-format.md)|<span data-ttu-id="9aa8f-121">Elemento facoltativo.</span><span class="sxs-lookup"><span data-stu-id="9aa8f-121">Optional element.</span></span><br /><br /> <span data-ttu-id="9aa8f-122">Specifica il numero minimo di proprietà che un oggetto deve avere per visualizzare l'oggetto in una visualizzazione tabella.</span><span class="sxs-lookup"><span data-stu-id="9aa8f-122">Specifies the minimum number of properties that an object must have to display the object in a table view.</span></span>|
|[<span data-ttu-id="9aa8f-123">Elemento ShowError (Format)</span><span class="sxs-lookup"><span data-stu-id="9aa8f-123">ShowError Element (Format)</span></span>](./showerror-element-format.md)|<span data-ttu-id="9aa8f-124">Elemento facoltativo.</span><span class="sxs-lookup"><span data-stu-id="9aa8f-124">Optional element.</span></span><br /><br /> <span data-ttu-id="9aa8f-125">Specifica che il record di errore completo viene visualizzato quando si verifica un errore durante la visualizzazione di una porzione di dati.</span><span class="sxs-lookup"><span data-stu-id="9aa8f-125">Specifies that the full error record is displayed when an error occurs while displaying a piece of data.</span></span>|
|[<span data-ttu-id="9aa8f-126">Elemento WrapTables (Format)</span><span class="sxs-lookup"><span data-stu-id="9aa8f-126">WrapTables Element (Format)</span></span>](./wraptables-element-format.md)|<span data-ttu-id="9aa8f-127">Elemento facoltativo.</span><span class="sxs-lookup"><span data-stu-id="9aa8f-127">Optional element.</span></span><br /><br /> <span data-ttu-id="9aa8f-128">Specifica che i dati di una tabella vengono spostati alla riga successiva se non rientra nella larghezza della colonna.</span><span class="sxs-lookup"><span data-stu-id="9aa8f-128">Specifies that data in a table is moved to the next line if it does not fit into the width of the column.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="9aa8f-129">Elementi padre</span><span class="sxs-lookup"><span data-stu-id="9aa8f-129">Parent Elements</span></span>

|<span data-ttu-id="9aa8f-130">Elemento</span><span class="sxs-lookup"><span data-stu-id="9aa8f-130">Element</span></span>|<span data-ttu-id="9aa8f-131">Description</span><span class="sxs-lookup"><span data-stu-id="9aa8f-131">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="9aa8f-132">Elemento Configuration</span><span class="sxs-lookup"><span data-stu-id="9aa8f-132">Configuration Element</span></span>](./configuration-element-format.md)|<span data-ttu-id="9aa8f-133">Rappresenta l'elemento di primo livello di un file di formattazione.</span><span class="sxs-lookup"><span data-stu-id="9aa8f-133">Represents the top-level element of a formatting file.</span></span>|

## <a name="remarks"></a><span data-ttu-id="9aa8f-134">Osservazioni</span><span class="sxs-lookup"><span data-stu-id="9aa8f-134">Remarks</span></span>

## <a name="see-also"></a><span data-ttu-id="9aa8f-135">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="9aa8f-135">See Also</span></span>

[<span data-ttu-id="9aa8f-136">Elemento Configuration</span><span class="sxs-lookup"><span data-stu-id="9aa8f-136">Configuration Element</span></span>](./configuration-element-format.md)

[<span data-ttu-id="9aa8f-137">Elemento DisplayError (Format)</span><span class="sxs-lookup"><span data-stu-id="9aa8f-137">DisplayError Element (Format)</span></span>](./displayerror-element-format.md)

[<span data-ttu-id="9aa8f-138">Elemento EnumerableExpansions (Format)</span><span class="sxs-lookup"><span data-stu-id="9aa8f-138">EnumerableExpansions Element (Format)</span></span>](./enumerableexpansions-element-format.md)

[<span data-ttu-id="9aa8f-139">PropertyCountForTable (formato)</span><span class="sxs-lookup"><span data-stu-id="9aa8f-139">PropertyCountForTable (Format)</span></span>](./propertycountfortable-element-format.md)

[<span data-ttu-id="9aa8f-140">Elemento ShowError (Format)</span><span class="sxs-lookup"><span data-stu-id="9aa8f-140">ShowError Element (Format)</span></span>](./showerror-element-format.md)

[<span data-ttu-id="9aa8f-141">Elemento WrapTables (Format)</span><span class="sxs-lookup"><span data-stu-id="9aa8f-141">WrapTables Element (Format)</span></span>](./wraptables-element-format.md)

[<span data-ttu-id="9aa8f-142">Scrittura di un file di formattazione di PowerShell</span><span class="sxs-lookup"><span data-stu-id="9aa8f-142">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
