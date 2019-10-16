---
title: Elemento PropertyName per TableColumnItem per Table ((Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: fb26d72c-2f77-4801-badf-0537ccc55e31
caps.latest.revision: 10
ms.openlocfilehash: 6e86b6a0874b385703121802bc8108a0410442cd
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/15/2019
ms.locfileid: "72362250"
---
# <a name="propertyname-element-for-tablecolumnitem-for-tablecontrol-format"></a><span data-ttu-id="2cb23-102">Elemento PropertyName per TableColumnItem per TableControl (formato)</span><span class="sxs-lookup"><span data-stu-id="2cb23-102">PropertyName Element for TableColumnItem for TableControl (Format)</span></span>

<span data-ttu-id="2cb23-103">Specifica la proprietà il cui valore viene visualizzato nella colonna della riga.</span><span class="sxs-lookup"><span data-stu-id="2cb23-103">Specifies the property whose value is displayed in the column of the row.</span></span>

<span data-ttu-id="2cb23-104">Elemento Configuration (Format) elemento ViewDefinitions (Format) elemento View (Format) elemento Table ((Format) elemento TableRowEntries (Format) elemento TableRowEntry (Format) elemento TableColumnItems (Format) elemento TableColumnItem (Format) Elemento PropertyName per TableColumnItem (Format)</span><span class="sxs-lookup"><span data-stu-id="2cb23-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) TableControl Element (Format) TableRowEntries Element (Format) TableRowEntry Element (Format) TableColumnItems Element (Format) TableColumnItem Element (Format) PropertyName Element for TableColumnItem (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="2cb23-105">Sintassi</span><span class="sxs-lookup"><span data-stu-id="2cb23-105">Syntax</span></span>

```xml
<PropertyName>.NetTypeProperty</PropertyName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="2cb23-106">Attributi ed elementi</span><span class="sxs-lookup"><span data-stu-id="2cb23-106">Attributes and Elements</span></span>

<span data-ttu-id="2cb23-107">Nelle sezioni seguenti vengono descritti gli attributi, gli elementi figlio e l'elemento padre dell'elemento `PropertyName`.</span><span class="sxs-lookup"><span data-stu-id="2cb23-107">The following sections describe attributes, child elements, and parent element of the `PropertyName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="2cb23-108">Attributi</span><span class="sxs-lookup"><span data-stu-id="2cb23-108">Attributes</span></span>

<span data-ttu-id="2cb23-109">Nessuna.</span><span class="sxs-lookup"><span data-stu-id="2cb23-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="2cb23-110">Elementi figlio</span><span class="sxs-lookup"><span data-stu-id="2cb23-110">Child Elements</span></span>

<span data-ttu-id="2cb23-111">Nessuna.</span><span class="sxs-lookup"><span data-stu-id="2cb23-111">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="2cb23-112">Elementi padre</span><span class="sxs-lookup"><span data-stu-id="2cb23-112">Parent Elements</span></span>

|<span data-ttu-id="2cb23-113">Elemento</span><span class="sxs-lookup"><span data-stu-id="2cb23-113">Element</span></span>|<span data-ttu-id="2cb23-114">Description</span><span class="sxs-lookup"><span data-stu-id="2cb23-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="2cb23-115">Elemento TableColumnItem (Format)</span><span class="sxs-lookup"><span data-stu-id="2cb23-115">TableColumnItem Element (Format)</span></span>](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md)|<span data-ttu-id="2cb23-116">Definisce la proprietà o lo script il cui valore viene visualizzato nella colonna della riga.</span><span class="sxs-lookup"><span data-stu-id="2cb23-116">Defines the property or script whose value is displayed in the column of the row.</span></span>|

## <a name="text-value"></a><span data-ttu-id="2cb23-117">Valore di testo</span><span class="sxs-lookup"><span data-stu-id="2cb23-117">Text Value</span></span>

<span data-ttu-id="2cb23-118">Consente di specificare il nome della proprietà di cui viene visualizzato il valore.</span><span class="sxs-lookup"><span data-stu-id="2cb23-118">Specify the name of the property whose value is displayed.</span></span>

## <a name="remarks"></a><span data-ttu-id="2cb23-119">Osservazioni</span><span class="sxs-lookup"><span data-stu-id="2cb23-119">Remarks</span></span>

<span data-ttu-id="2cb23-120">Per ulteriori informazioni sui componenti di una vista tabella, vedere [creazione di una vista tabella](./creating-a-table-view.md).</span><span class="sxs-lookup"><span data-stu-id="2cb23-120">For more information about the components of a table view, see [Creating a Table View](./creating-a-table-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="2cb23-121">Esempio</span><span class="sxs-lookup"><span data-stu-id="2cb23-121">Example</span></span>

<span data-ttu-id="2cb23-122">Questo esempio mostra un elemento `TableColumnItem` che specifica la proprietà `Status` dell'oggetto [System. Diagnostics. Process](/dotnet/api/System.Diagnostics.Process) .</span><span class="sxs-lookup"><span data-stu-id="2cb23-122">This example shows a `TableColumnItem` element that specifies the `Status` property of the [System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process) object.</span></span>

```xml
<TableColumnItem>
   <Alignment>Centered</Alignment>
  <PropertyName>Status</PropertyName>
</TableColumnItem>

```

## <a name="see-also"></a><span data-ttu-id="2cb23-123">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="2cb23-123">See Also</span></span>

[<span data-ttu-id="2cb23-124">Creazione di una vista tabella</span><span class="sxs-lookup"><span data-stu-id="2cb23-124">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="2cb23-125">Elemento TableColumnItem (Format)</span><span class="sxs-lookup"><span data-stu-id="2cb23-125">TableColumnItem Element (Format)</span></span>](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md)

[<span data-ttu-id="2cb23-126">Scrittura di un file di formattazione di PowerShell</span><span class="sxs-lookup"><span data-stu-id="2cb23-126">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
