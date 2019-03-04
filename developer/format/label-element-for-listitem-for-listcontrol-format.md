---
title: L'etichetta di elemento per elemento ListItem per ListControl (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: c693ff46-d1ad-4dc7-93ac-41ff2fc6c103
caps.latest.revision: 9
ms.openlocfilehash: c1293d5a1f942704ac01388c66bd9009fd340e82
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/03/2019
ms.locfileid: "56854777"
---
# <a name="label-element-for-listitem-for-listcontrol-format"></a><span data-ttu-id="53cc1-102">Elemento Label per ListItem per ListControl (formato)</span><span class="sxs-lookup"><span data-stu-id="53cc1-102">Label Element for ListItem for ListControl (Format)</span></span>

<span data-ttu-id="53cc1-103">Specifica l'etichetta che viene visualizzato a sinistra del valore della proprietà o script della riga.</span><span class="sxs-lookup"><span data-stu-id="53cc1-103">Specifies the label that is displayed to the left of the property or script value in the row.</span></span>

<span data-ttu-id="53cc1-104">Elemento (formato) elemento ViewDefinitions (formato) visualizzazione elemento (formato) elemento dell'oggetto ListControl (formato) ListEntries elemento di configurazione per ListControl (formato) ListEntry elemento ListItems dell'oggetto ListControl (formato) per ListEntry per elemento dell'oggetto ListControl ( Elemento ListItem Format) per ListItems per elemento etichetta dell'oggetto ListControl (formato) per ListItem per ListControl (formato)</span><span class="sxs-lookup"><span data-stu-id="53cc1-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) ListControl Element (Format) ListEntries Element for ListControl (Format) ListEntry Element for ListControl (Format) ListItems for ListEntry for ListControl Element (Format) ListItem Element for ListItems for ListControl (Format) Label Element for ListItem for ListControl (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="53cc1-105">Sintassi</span><span class="sxs-lookup"><span data-stu-id="53cc1-105">Syntax</span></span>

```xml
<Label>Label for displayed value</Label>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="53cc1-106">Attributi ed elementi</span><span class="sxs-lookup"><span data-stu-id="53cc1-106">Attributes and Elements</span></span>

<span data-ttu-id="53cc1-107">Le sezioni seguenti descrivono gli attributi e gli elementi figlio dell'elemento padre del `Label` elemento.</span><span class="sxs-lookup"><span data-stu-id="53cc1-107">The following sections describe the attributes, child elements, and the parent element of the `Label` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="53cc1-108">Attributes</span><span class="sxs-lookup"><span data-stu-id="53cc1-108">Attributes</span></span>

<span data-ttu-id="53cc1-109">Nessuna.</span><span class="sxs-lookup"><span data-stu-id="53cc1-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="53cc1-110">Elementi figlio</span><span class="sxs-lookup"><span data-stu-id="53cc1-110">Child Elements</span></span>

<span data-ttu-id="53cc1-111">Nessuna.</span><span class="sxs-lookup"><span data-stu-id="53cc1-111">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="53cc1-112">Elementi padre</span><span class="sxs-lookup"><span data-stu-id="53cc1-112">Parent Elements</span></span>

|<span data-ttu-id="53cc1-113">Elemento</span><span class="sxs-lookup"><span data-stu-id="53cc1-113">Element</span></span>|<span data-ttu-id="53cc1-114">Description</span><span class="sxs-lookup"><span data-stu-id="53cc1-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="53cc1-115">Elemento ListItem per ListItems per ListControl (formato)</span><span class="sxs-lookup"><span data-stu-id="53cc1-115">ListItem Element for ListItems for ListControl (Format)</span></span>](./listitem-element-for-listitems-for-listcontrol-format.md)|<span data-ttu-id="53cc1-116">Definisce proprietà o script il cui valore viene visualizzato in una riga della visualizzazione elenco.</span><span class="sxs-lookup"><span data-stu-id="53cc1-116">Defines the property or script whose value is displayed in a row of the list view.</span></span>|

## <a name="text-value"></a><span data-ttu-id="53cc1-117">Valore di testo</span><span class="sxs-lookup"><span data-stu-id="53cc1-117">Text Value</span></span>

<span data-ttu-id="53cc1-118">Specificare l'etichetta per essere visualizzato a sinistra del valore della proprietà o dello script.</span><span class="sxs-lookup"><span data-stu-id="53cc1-118">Specify the label to be display to the left of the property or script value.</span></span>

## <a name="remarks"></a><span data-ttu-id="53cc1-119">Osservazioni</span><span class="sxs-lookup"><span data-stu-id="53cc1-119">Remarks</span></span>

<span data-ttu-id="53cc1-120">Se non viene specificata un'etichetta, viene visualizzato il nome della proprietà o lo script.</span><span class="sxs-lookup"><span data-stu-id="53cc1-120">If a label is not specified, the name of the property or the script is displayed.</span></span> <span data-ttu-id="53cc1-121">Per altre informazioni sull'utilizzo di etichette in una visualizzazione elenco, vedere [creazione di una visualizzazione elenco](./creating-a-list-view.md).</span><span class="sxs-lookup"><span data-stu-id="53cc1-121">For more information about using labels in a list view, see [Creating a List View](./creating-a-list-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="53cc1-122">Esempio</span><span class="sxs-lookup"><span data-stu-id="53cc1-122">Example</span></span>

<span data-ttu-id="53cc1-123">Nell'esempio seguente viene illustrato come aggiungere un'etichetta a una riga.</span><span class="sxs-lookup"><span data-stu-id="53cc1-123">The following example shows how to add a label to a row.</span></span>

```xml
<ListItem>
  <Label>Property1: </Label>
  <PropertyName>DotNetProperty1</PropertyName>
</ListItem>

```

## <a name="see-also"></a><span data-ttu-id="53cc1-124">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="53cc1-124">See Also</span></span>

[<span data-ttu-id="53cc1-125">Creazione di una visualizzazione elenco</span><span class="sxs-lookup"><span data-stu-id="53cc1-125">Creating a List View</span></span>](./creating-a-list-view.md)

[<span data-ttu-id="53cc1-126">Elemento ListItem (formato)</span><span class="sxs-lookup"><span data-stu-id="53cc1-126">ListItem Element (Format)</span></span>](./listitem-element-for-listitems-for-listcontrol-format.md)

[<span data-ttu-id="53cc1-127">La scrittura di un File di formattazione di PowerShell</span><span class="sxs-lookup"><span data-stu-id="53cc1-127">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
