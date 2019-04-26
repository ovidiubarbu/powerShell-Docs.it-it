---
title: Elemento larghezza per TableColumnHeader per Table (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 94eb0535-8002-4f17-9a2b-4be75ec20e5c
caps.latest.revision: 18
ms.openlocfilehash: 4a25c9d81df670dc10955065bfb66766cdb1bd33
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62083621"
---
# <a name="width-element-for-tablecolumnheader-for-tablecontrol-format"></a><span data-ttu-id="82cff-102">Elemento Width per TableColumnHeader per TableControl (formato)</span><span class="sxs-lookup"><span data-stu-id="82cff-102">Width Element for TableColumnHeader for TableControl (Format)</span></span>

<span data-ttu-id="82cff-103">Definisce la larghezza (in caratteri) di una colonna.</span><span class="sxs-lookup"><span data-stu-id="82cff-103">Defines the width (in characters) of a column.</span></span>

<span data-ttu-id="82cff-104">Elemento (formato) elemento ViewDefinitions (formato) visualizzazione elemento (formato) elemento Table (formato) TableHeaders elemento di configurazione per Table (formato) TableHeaders TableColumnHeader elemento per elemento larghezza Table (formato) TableColumnHeader per Table (formato)</span><span class="sxs-lookup"><span data-stu-id="82cff-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) TableControl Element (Format) TableHeaders Element for TableControl (Format) TableColumnHeader Element TableHeaders for TableControl (Format) Width Element for TableColumnHeader for TableControl (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="82cff-105">Sintassi</span><span class="sxs-lookup"><span data-stu-id="82cff-105">Syntax</span></span>

```xml
<Width>NumberOfCharacters</Width>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="82cff-106">Elementi e attributi</span><span class="sxs-lookup"><span data-stu-id="82cff-106">Attributes and Elements</span></span>

<span data-ttu-id="82cff-107">Le sezioni seguenti descrivono gli attributi, elementi figlio ed elemento padre dell'elemento di `Width` elemento utilizzato quando si definiscono le intestazioni di colonna.</span><span class="sxs-lookup"><span data-stu-id="82cff-107">The following sections describe the attributes, child elements, and parent element of the `Width` element used when defining column headers.</span></span>

### <a name="attributes"></a><span data-ttu-id="82cff-108">Attributes</span><span class="sxs-lookup"><span data-stu-id="82cff-108">Attributes</span></span>

<span data-ttu-id="82cff-109">Nessuna.</span><span class="sxs-lookup"><span data-stu-id="82cff-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="82cff-110">Elementi figlio</span><span class="sxs-lookup"><span data-stu-id="82cff-110">Child Elements</span></span>

<span data-ttu-id="82cff-111">Nessuna.</span><span class="sxs-lookup"><span data-stu-id="82cff-111">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="82cff-112">Elementi padre</span><span class="sxs-lookup"><span data-stu-id="82cff-112">Parent Elements</span></span>

|<span data-ttu-id="82cff-113">Elemento</span><span class="sxs-lookup"><span data-stu-id="82cff-113">Element</span></span>|<span data-ttu-id="82cff-114">Description</span><span class="sxs-lookup"><span data-stu-id="82cff-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="82cff-115">Elemento TableColumnHeader per TableHeaders per Table (formato)</span><span class="sxs-lookup"><span data-stu-id="82cff-115">TableColumnHeader Element for TableHeaders for TableControl (Format)</span></span>](./tablecolumnheader-element-format.md)|<span data-ttu-id="82cff-116">Definisce un'etichetta, larghezza e l'allineamento dei dati per una colonna della tabella.</span><span class="sxs-lookup"><span data-stu-id="82cff-116">Defines a label, width, and alignment of the data for a column of the table.</span></span>|

## <a name="text-value"></a><span data-ttu-id="82cff-117">Valore di testo</span><span class="sxs-lookup"><span data-stu-id="82cff-117">Text Value</span></span>

<span data-ttu-id="82cff-118">Quando si trova in tutte le possibili, specificare una larghezza (in caratteri) che è maggiore della lunghezza dei valori di proprietà visualizzata.</span><span class="sxs-lookup"><span data-stu-id="82cff-118">When at all possible, specify a width (in characters) that is greater than the length of the displayed property values.</span></span>

## <a name="remarks"></a><span data-ttu-id="82cff-119">Osservazioni</span><span class="sxs-lookup"><span data-stu-id="82cff-119">Remarks</span></span>

<span data-ttu-id="82cff-120">Per altre informazioni sui componenti di visualizzazione di una tabella, vedere [creazione di una visualizzazione tabella](./creating-a-table-view.md).</span><span class="sxs-lookup"><span data-stu-id="82cff-120">For more information about the components of a table view, see [Creating a Table View](./creating-a-table-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="82cff-121">Esempio</span><span class="sxs-lookup"><span data-stu-id="82cff-121">Example</span></span>

<span data-ttu-id="82cff-122">L'esempio seguente mostra un `TableColumnHeader` elemento la cui larghezza è 16 caratteri.</span><span class="sxs-lookup"><span data-stu-id="82cff-122">The following example shows a `TableColumnHeader` element whose width is 16 characters.</span></span>

```xml
<TableColumnHeader>
  <Label>Column 1</Label)
  <Width>16</Width>
  <Alignment>Left</Alignment>
</TableColumnHeader>
```

## <a name="see-also"></a><span data-ttu-id="82cff-123">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="82cff-123">See Also</span></span>

[<span data-ttu-id="82cff-124">Creazione di una visualizzazione tabella</span><span class="sxs-lookup"><span data-stu-id="82cff-124">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="82cff-125">Elemento TableColumnHeader per TableHeader per Table (formato)</span><span class="sxs-lookup"><span data-stu-id="82cff-125">TableColumnHeader Element for TableHeader for TableControl (Format)</span></span>](./tablecolumnheader-element-format.md)

[<span data-ttu-id="82cff-126">La scrittura di un File di formattazione di PowerShell</span><span class="sxs-lookup"><span data-stu-id="82cff-126">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
