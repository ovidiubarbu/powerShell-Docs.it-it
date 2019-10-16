---
title: Elemento SelectionSetName per ViewSelectedBy (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 8ab0f033-df09-4435-a8bd-76ec2d01f13b
caps.latest.revision: 13
ms.openlocfilehash: d1de2b30860bac80bf17508f40eec33c2794c4b2
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/15/2019
ms.locfileid: "72368260"
---
# <a name="selectionsetname-element-for-viewselectedby-format"></a><span data-ttu-id="f1f60-102">Elemento SelectionSetName per ViewSelectedBy (formato)</span><span class="sxs-lookup"><span data-stu-id="f1f60-102">SelectionSetName Element for ViewSelectedBy (Format)</span></span>

<span data-ttu-id="f1f60-103">Specifica un set di oggetti .NET visualizzati dalla visualizzazione.</span><span class="sxs-lookup"><span data-stu-id="f1f60-103">Specifies a set of .NET objects that are displayed by the view.</span></span>

<span data-ttu-id="f1f60-104">Elemento Configuration (Format) elemento ViewDefinitions (Format) elemento View (Format) elemento ViewSelectedBy (Format) elemento SelectionSetName per ViewSelectedBy (Format)</span><span class="sxs-lookup"><span data-stu-id="f1f60-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) ViewSelectedBy Element (Format) SelectionSetName Element for ViewSelectedBy (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="f1f60-105">Sintassi</span><span class="sxs-lookup"><span data-stu-id="f1f60-105">Syntax</span></span>

```xml
<SelectionSetName>Name of selection set<SelectionSetName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="f1f60-106">Attributi ed elementi</span><span class="sxs-lookup"><span data-stu-id="f1f60-106">Attributes and Elements</span></span>

<span data-ttu-id="f1f60-107">Nelle sezioni seguenti vengono descritti gli attributi, gli elementi figlio e l'elemento padre dell'elemento `SelectionSetName`.</span><span class="sxs-lookup"><span data-stu-id="f1f60-107">The following sections describe the attributes, child elements, and the parent element of the `SelectionSetName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="f1f60-108">Attributi</span><span class="sxs-lookup"><span data-stu-id="f1f60-108">Attributes</span></span>

<span data-ttu-id="f1f60-109">Nessuna.</span><span class="sxs-lookup"><span data-stu-id="f1f60-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="f1f60-110">Elementi figlio</span><span class="sxs-lookup"><span data-stu-id="f1f60-110">Child Elements</span></span>

<span data-ttu-id="f1f60-111">Nessuna.</span><span class="sxs-lookup"><span data-stu-id="f1f60-111">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="f1f60-112">Elementi padre</span><span class="sxs-lookup"><span data-stu-id="f1f60-112">Parent Elements</span></span>

|<span data-ttu-id="f1f60-113">Elemento</span><span class="sxs-lookup"><span data-stu-id="f1f60-113">Element</span></span>|<span data-ttu-id="f1f60-114">Description</span><span class="sxs-lookup"><span data-stu-id="f1f60-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="f1f60-115">Elemento ViewSelectedBy (Format)</span><span class="sxs-lookup"><span data-stu-id="f1f60-115">ViewSelectedBy Element (Format)</span></span>](./viewselectedby-element-format.md)|<span data-ttu-id="f1f60-116">Definisce gli oggetti .NET visualizzati dalla visualizzazione.</span><span class="sxs-lookup"><span data-stu-id="f1f60-116">Defines the .NET objects that are displayed by the view.</span></span>|

## <a name="text-value"></a><span data-ttu-id="f1f60-117">Valore di testo</span><span class="sxs-lookup"><span data-stu-id="f1f60-117">Text Value</span></span>

<span data-ttu-id="f1f60-118">Consente di specificare il nome del set di selezione definito dall'elemento `Name` per il set di selezione.</span><span class="sxs-lookup"><span data-stu-id="f1f60-118">Specify the name of the selection set that is defined by the `Name` element for the selection set.</span></span>

## <a name="remarks"></a><span data-ttu-id="f1f60-119">Osservazioni</span><span class="sxs-lookup"><span data-stu-id="f1f60-119">Remarks</span></span>

<span data-ttu-id="f1f60-120">È possibile utilizzare i set di selezione quando si dispone di un set di oggetti correlati a cui si desidera fare riferimento utilizzando un solo nome, ad esempio un set di oggetti correlati tramite ereditarietà.</span><span class="sxs-lookup"><span data-stu-id="f1f60-120">You can use selection sets when you have a set of related objects that you want to reference by using a single name, such as a set of objects that are related through inheritance.</span></span> <span data-ttu-id="f1f60-121">Per ulteriori informazioni sulla definizione e il riferimento a set di selezione, vedere [definizione di set di oggetti](./defining-selection-sets.md).</span><span class="sxs-lookup"><span data-stu-id="f1f60-121">For more information about defining and referencing selection sets, see [Defining Sets of Objects](./defining-selection-sets.md).</span></span>

## <a name="example"></a><span data-ttu-id="f1f60-122">Esempio</span><span class="sxs-lookup"><span data-stu-id="f1f60-122">Example</span></span>

<span data-ttu-id="f1f60-123">Nell'esempio seguente viene illustrato come specificare un set di selezione per una visualizzazione elenco.</span><span class="sxs-lookup"><span data-stu-id="f1f60-123">The following example shows how to specify a selection set for a list view.</span></span> <span data-ttu-id="f1f60-124">Lo stesso schema viene utilizzato per le visualizzazioni tabella, Wide e Custom.</span><span class="sxs-lookup"><span data-stu-id="f1f60-124">The same schema is used for table, wide, and custom views.</span></span>

```xml
<View>
  <Name>Name of View</Name>
  <ViewSelectedBy>
    <SelectionSetName>NameofSelectionSet</SelectionSetName>>
  </ViewSelectedBy>
  <ListControl>...</ListControl>
</View>
```

## <a name="see-also"></a><span data-ttu-id="f1f60-125">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="f1f60-125">See Also</span></span>

[<span data-ttu-id="f1f60-126">Definizione di set di selezione</span><span class="sxs-lookup"><span data-stu-id="f1f60-126">Defining Selection Sets</span></span>](./defining-selection-sets.md)

[<span data-ttu-id="f1f60-127">Elemento ViewSelectedBy (Format)</span><span class="sxs-lookup"><span data-stu-id="f1f60-127">ViewSelectedBy Element (Format)</span></span>](./viewselectedby-element-format.md)

[<span data-ttu-id="f1f60-128">Scrittura di un file di formattazione di PowerShell</span><span class="sxs-lookup"><span data-stu-id="f1f60-128">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
