---
title: Elemento PropertyName per TableColumnItem per Table (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: fb26d72c-2f77-4801-badf-0537ccc55e31
caps.latest.revision: 10
ms.openlocfilehash: 6e86b6a0874b385703121802bc8108a0410442cd
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/03/2019
ms.locfileid: "56859467"
---
# <a name="propertyname-element-for-tablecolumnitem-for-tablecontrol-format"></a><span data-ttu-id="a61af-102">Elemento PropertyName per TableColumnItem per TableControl (formato)</span><span class="sxs-lookup"><span data-stu-id="a61af-102">PropertyName Element for TableColumnItem for TableControl (Format)</span></span>

<span data-ttu-id="a61af-103">Specifica la proprietà il cui valore viene visualizzato nella colonna della riga.</span><span class="sxs-lookup"><span data-stu-id="a61af-103">Specifies the property whose value is displayed in the column of the row.</span></span>

<span data-ttu-id="a61af-104">Elemento (formato) elemento ViewDefinitions (formato) visualizzazione elemento (formato) elemento Table (formato) elemento TableRowEntries (formato) elemento TableRowEntry (formato) elemento TableColumnItems (formato) TableColumnItem elemento di configurazione (formato) Elemento PropertyName per TableColumnItem (formato)</span><span class="sxs-lookup"><span data-stu-id="a61af-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) TableControl Element (Format) TableRowEntries Element (Format) TableRowEntry Element (Format) TableColumnItems Element (Format) TableColumnItem Element (Format) PropertyName Element for TableColumnItem (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="a61af-105">Sintassi</span><span class="sxs-lookup"><span data-stu-id="a61af-105">Syntax</span></span>

```xml
<PropertyName>.NetTypeProperty</PropertyName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="a61af-106">Attributi ed elementi</span><span class="sxs-lookup"><span data-stu-id="a61af-106">Attributes and Elements</span></span>

<span data-ttu-id="a61af-107">Le sezioni seguenti descrivono l'elemento padre di attributi e gli elementi figlio di `PropertyName` elemento.</span><span class="sxs-lookup"><span data-stu-id="a61af-107">The following sections describe attributes, child elements, and parent element of the `PropertyName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="a61af-108">Attributes</span><span class="sxs-lookup"><span data-stu-id="a61af-108">Attributes</span></span>

<span data-ttu-id="a61af-109">Nessuna.</span><span class="sxs-lookup"><span data-stu-id="a61af-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="a61af-110">Elementi figlio</span><span class="sxs-lookup"><span data-stu-id="a61af-110">Child Elements</span></span>

<span data-ttu-id="a61af-111">Nessuna.</span><span class="sxs-lookup"><span data-stu-id="a61af-111">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="a61af-112">Elementi padre</span><span class="sxs-lookup"><span data-stu-id="a61af-112">Parent Elements</span></span>

|<span data-ttu-id="a61af-113">Elemento</span><span class="sxs-lookup"><span data-stu-id="a61af-113">Element</span></span>|<span data-ttu-id="a61af-114">Description</span><span class="sxs-lookup"><span data-stu-id="a61af-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="a61af-115">Elemento TableColumnItem (formato)</span><span class="sxs-lookup"><span data-stu-id="a61af-115">TableColumnItem Element (Format)</span></span>](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md)|<span data-ttu-id="a61af-116">Definisce le proprietà il cui valore viene visualizzato nella colonna della riga di script.</span><span class="sxs-lookup"><span data-stu-id="a61af-116">Defines the property or script whose value is displayed in the column of the row.</span></span>|

## <a name="text-value"></a><span data-ttu-id="a61af-117">Valore di testo</span><span class="sxs-lookup"><span data-stu-id="a61af-117">Text Value</span></span>

<span data-ttu-id="a61af-118">Specificare il nome della proprietà il cui valore viene visualizzato.</span><span class="sxs-lookup"><span data-stu-id="a61af-118">Specify the name of the property whose value is displayed.</span></span>

## <a name="remarks"></a><span data-ttu-id="a61af-119">Osservazioni</span><span class="sxs-lookup"><span data-stu-id="a61af-119">Remarks</span></span>

<span data-ttu-id="a61af-120">Per altre informazioni sui componenti di visualizzazione di una tabella, vedere [creazione di una visualizzazione tabella](./creating-a-table-view.md).</span><span class="sxs-lookup"><span data-stu-id="a61af-120">For more information about the components of a table view, see [Creating a Table View](./creating-a-table-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="a61af-121">Esempio</span><span class="sxs-lookup"><span data-stu-id="a61af-121">Example</span></span>

<span data-ttu-id="a61af-122">Questo esempio viene illustrato un `TableColumnItem` elemento che specifica il `Status` proprietà delle [Diagnostics](/dotnet/api/System.Diagnostics.Process) oggetto.</span><span class="sxs-lookup"><span data-stu-id="a61af-122">This example shows a `TableColumnItem` element that specifies the `Status` property of the [System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process) object.</span></span>

```xml
<TableColumnItem>
   <Alignment>Centered</Alignment>
  <PropertyName>Status</PropertyName>
</TableColumnItem>

```

## <a name="see-also"></a><span data-ttu-id="a61af-123">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="a61af-123">See Also</span></span>

[<span data-ttu-id="a61af-124">Creazione di una visualizzazione tabella</span><span class="sxs-lookup"><span data-stu-id="a61af-124">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="a61af-125">Elemento TableColumnItem (formato)</span><span class="sxs-lookup"><span data-stu-id="a61af-125">TableColumnItem Element (Format)</span></span>](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md)

[<span data-ttu-id="a61af-126">La scrittura di un File di formattazione di PowerShell</span><span class="sxs-lookup"><span data-stu-id="a61af-126">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
