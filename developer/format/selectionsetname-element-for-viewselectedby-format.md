---
title: Elemento SelectionSetName per ViewSelectedBy (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 8ab0f033-df09-4435-a8bd-76ec2d01f13b
caps.latest.revision: 13
ms.openlocfilehash: d1de2b30860bac80bf17508f40eec33c2794c4b2
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/03/2019
ms.locfileid: "56858337"
---
# <a name="selectionsetname-element-for-viewselectedby-format"></a><span data-ttu-id="2748c-102">Elemento SelectionSetName per ViewSelectedBy (formato)</span><span class="sxs-lookup"><span data-stu-id="2748c-102">SelectionSetName Element for ViewSelectedBy (Format)</span></span>

<span data-ttu-id="2748c-103">Specifica un set di oggetti .NET che vengono visualizzati nella visualizzazione.</span><span class="sxs-lookup"><span data-stu-id="2748c-103">Specifies a set of .NET objects that are displayed by the view.</span></span>

<span data-ttu-id="2748c-104">Elemento (formato) elemento ViewDefinitions (formato) visualizzazione elemento (formato) elemento ViewSelectedBy (formato) SelectionSetName elemento di configurazione per ViewSelectedBy (formato)</span><span class="sxs-lookup"><span data-stu-id="2748c-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) ViewSelectedBy Element (Format) SelectionSetName Element for ViewSelectedBy (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="2748c-105">Sintassi</span><span class="sxs-lookup"><span data-stu-id="2748c-105">Syntax</span></span>

```xml
<SelectionSetName>Name of selection set<SelectionSetName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="2748c-106">Attributi ed elementi</span><span class="sxs-lookup"><span data-stu-id="2748c-106">Attributes and Elements</span></span>

<span data-ttu-id="2748c-107">Le sezioni seguenti descrivono gli attributi e gli elementi figlio dell'elemento padre del `SelectionSetName` elemento.</span><span class="sxs-lookup"><span data-stu-id="2748c-107">The following sections describe the attributes, child elements, and the parent element of the `SelectionSetName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="2748c-108">Attributes</span><span class="sxs-lookup"><span data-stu-id="2748c-108">Attributes</span></span>

<span data-ttu-id="2748c-109">Nessuna.</span><span class="sxs-lookup"><span data-stu-id="2748c-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="2748c-110">Elementi figlio</span><span class="sxs-lookup"><span data-stu-id="2748c-110">Child Elements</span></span>

<span data-ttu-id="2748c-111">Nessuna.</span><span class="sxs-lookup"><span data-stu-id="2748c-111">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="2748c-112">Elementi padre</span><span class="sxs-lookup"><span data-stu-id="2748c-112">Parent Elements</span></span>

|<span data-ttu-id="2748c-113">Elemento</span><span class="sxs-lookup"><span data-stu-id="2748c-113">Element</span></span>|<span data-ttu-id="2748c-114">Description</span><span class="sxs-lookup"><span data-stu-id="2748c-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="2748c-115">Elemento ViewSelectedBy (formato)</span><span class="sxs-lookup"><span data-stu-id="2748c-115">ViewSelectedBy Element (Format)</span></span>](./viewselectedby-element-format.md)|<span data-ttu-id="2748c-116">Definisce gli oggetti .NET che vengono visualizzati nella visualizzazione.</span><span class="sxs-lookup"><span data-stu-id="2748c-116">Defines the .NET objects that are displayed by the view.</span></span>|

## <a name="text-value"></a><span data-ttu-id="2748c-117">Valore di testo</span><span class="sxs-lookup"><span data-stu-id="2748c-117">Text Value</span></span>

<span data-ttu-id="2748c-118">Specificare il nome del set di selezione definito dal `Name` (elemento) per il set di selezione.</span><span class="sxs-lookup"><span data-stu-id="2748c-118">Specify the name of the selection set that is defined by the `Name` element for the selection set.</span></span>

## <a name="remarks"></a><span data-ttu-id="2748c-119">Osservazioni</span><span class="sxs-lookup"><span data-stu-id="2748c-119">Remarks</span></span>

<span data-ttu-id="2748c-120">Quando si dispone di un set di oggetti correlati che si desidera fare riferimento tramite un solo nome, ad esempio un set di oggetti che sono correlati tramite l'ereditarietà, è possibile usare set di selezione.</span><span class="sxs-lookup"><span data-stu-id="2748c-120">You can use selection sets when you have a set of related objects that you want to reference by using a single name, such as a set of objects that are related through inheritance.</span></span> <span data-ttu-id="2748c-121">Per altre informazioni sulla definizione e riferimento a set di selezione, vedere [definizione imposta di oggetti](./defining-selection-sets.md).</span><span class="sxs-lookup"><span data-stu-id="2748c-121">For more information about defining and referencing selection sets, see [Defining Sets of Objects](./defining-selection-sets.md).</span></span>

## <a name="example"></a><span data-ttu-id="2748c-122">Esempio</span><span class="sxs-lookup"><span data-stu-id="2748c-122">Example</span></span>

<span data-ttu-id="2748c-123">Nell'esempio seguente viene illustrato come specificare un insieme per una visualizzazione elenco di selezione.</span><span class="sxs-lookup"><span data-stu-id="2748c-123">The following example shows how to specify a selection set for a list view.</span></span> <span data-ttu-id="2748c-124">Lo stesso schema viene utilizzato per le visualizzazioni di tabella, ampia e personalizzati.</span><span class="sxs-lookup"><span data-stu-id="2748c-124">The same schema is used for table, wide, and custom views.</span></span>

```xml
<View>
  <Name>Name of View</Name>
  <ViewSelectedBy>
    <SelectionSetName>NameofSelectionSet</SelectionSetName>>
  </ViewSelectedBy>
  <ListControl>...</ListControl>
</View>
```

## <a name="see-also"></a><span data-ttu-id="2748c-125">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="2748c-125">See Also</span></span>

[<span data-ttu-id="2748c-126">La definizione di set di selezione</span><span class="sxs-lookup"><span data-stu-id="2748c-126">Defining Selection Sets</span></span>](./defining-selection-sets.md)

[<span data-ttu-id="2748c-127">Elemento ViewSelectedBy (formato)</span><span class="sxs-lookup"><span data-stu-id="2748c-127">ViewSelectedBy Element (Format)</span></span>](./viewselectedby-element-format.md)

[<span data-ttu-id="2748c-128">La scrittura di un File di formattazione di PowerShell</span><span class="sxs-lookup"><span data-stu-id="2748c-128">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
