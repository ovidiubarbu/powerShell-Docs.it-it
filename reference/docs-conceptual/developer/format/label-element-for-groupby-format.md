---
title: Elemento label per GroupBy (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 3351d237-e8c2-4ec5-9500-4eceadb407c2
caps.latest.revision: 11
ms.openlocfilehash: e7158711c60d13c745bbdfab9b1b9fc7d98b34e2
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/15/2019
ms.locfileid: "72365200"
---
# <a name="label-element-for-groupby-format"></a><span data-ttu-id="1f615-102">Elemento Label per GroupBy (formato)</span><span class="sxs-lookup"><span data-stu-id="1f615-102">Label Element for GroupBy (Format)</span></span>

<span data-ttu-id="1f615-103">Specifica un'etichetta visualizzata quando viene rilevato un nuovo gruppo.</span><span class="sxs-lookup"><span data-stu-id="1f615-103">Specifies a label that is displayed when a new group is encountered.</span></span>

<span data-ttu-id="1f615-104">Elemento Configuration (Format) elemento ViewDefinitions (Format) elemento View (Format) elemento GroupBy per l'elemento label view (Format) per GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="1f615-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) GroupBy Element for View (Format) Label Element for GroupBy (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="1f615-105">Sintassi</span><span class="sxs-lookup"><span data-stu-id="1f615-105">Syntax</span></span>

```xml
<Label>DisplayedLabel</Label>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="1f615-106">Attributi ed elementi</span><span class="sxs-lookup"><span data-stu-id="1f615-106">Attributes and Elements</span></span>

<span data-ttu-id="1f615-107">Nelle sezioni seguenti vengono descritti gli attributi, gli elementi figlio e l'elemento padre dell'elemento `Label`.</span><span class="sxs-lookup"><span data-stu-id="1f615-107">The following sections describe the attributes, child elements, and parent element of the `Label` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="1f615-108">Attributi</span><span class="sxs-lookup"><span data-stu-id="1f615-108">Attributes</span></span>

<span data-ttu-id="1f615-109">Nessuna.</span><span class="sxs-lookup"><span data-stu-id="1f615-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="1f615-110">Elementi figlio</span><span class="sxs-lookup"><span data-stu-id="1f615-110">Child Elements</span></span>

<span data-ttu-id="1f615-111">Nessuna.</span><span class="sxs-lookup"><span data-stu-id="1f615-111">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="1f615-112">Elementi padre</span><span class="sxs-lookup"><span data-stu-id="1f615-112">Parent Elements</span></span>

|<span data-ttu-id="1f615-113">Elemento</span><span class="sxs-lookup"><span data-stu-id="1f615-113">Element</span></span>|<span data-ttu-id="1f615-114">Description</span><span class="sxs-lookup"><span data-stu-id="1f615-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="1f615-115">Elemento GroupBy per View (Format)</span><span class="sxs-lookup"><span data-stu-id="1f615-115">GroupBy Element for View (Format)</span></span>](./groupby-element-for-view-format.md)|<span data-ttu-id="1f615-116">Definisce la modalità di visualizzazione di un nuovo gruppo di oggetti.</span><span class="sxs-lookup"><span data-stu-id="1f615-116">Defines how a new group of objects is displayed.</span></span>|

## <a name="text-value"></a><span data-ttu-id="1f615-117">Valore di testo</span><span class="sxs-lookup"><span data-stu-id="1f615-117">Text Value</span></span>

<span data-ttu-id="1f615-118">Specificare il testo visualizzato ogni volta che Windows PowerShell incontra un nuovo valore di proprietà o script.</span><span class="sxs-lookup"><span data-stu-id="1f615-118">Specify the text that is displayed whenever Windows PowerShell encounters a new property or script value.</span></span>

## <a name="remarks"></a><span data-ttu-id="1f615-119">Osservazioni</span><span class="sxs-lookup"><span data-stu-id="1f615-119">Remarks</span></span>

<span data-ttu-id="1f615-120">Oltre al testo specificato da questo elemento, Windows PowerShell Visualizza il nuovo valore che avvia il gruppo e aggiunge una riga vuota prima e dopo il gruppo.</span><span class="sxs-lookup"><span data-stu-id="1f615-120">In addition to the text specified by this element, Windows PowerShell displays the new value that starts the group, and adds a blank line before and after the group.</span></span>

## <a name="example"></a><span data-ttu-id="1f615-121">Esempio</span><span class="sxs-lookup"><span data-stu-id="1f615-121">Example</span></span>

<span data-ttu-id="1f615-122">Nell'esempio seguente viene illustrata l'etichetta per un nuovo gruppo.</span><span class="sxs-lookup"><span data-stu-id="1f615-122">The following example shows the label for a new group.</span></span> <span data-ttu-id="1f615-123">L'etichetta visualizzata avrà un aspetto simile al seguente: `Service Type: NewValueofProperty`</span><span class="sxs-lookup"><span data-stu-id="1f615-123">The displayed label would look similar to this: `Service Type: NewValueofProperty`</span></span>

```xml
<GroupBy>
  <Label>Service Type</Label>
  <PropertyName>ServiceType</PropertyName>
</GroupBy>

```

<span data-ttu-id="1f615-124">Per un esempio di un file di formattazione completo che include questo elemento, vedere [visualizzazione estesa (GroupBy)](./wide-view-groupby.md).</span><span class="sxs-lookup"><span data-stu-id="1f615-124">For an example of a complete formatting file that includes this element, see [Wide View (GroupBy)](./wide-view-groupby.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="1f615-125">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="1f615-125">See Also</span></span>

[<span data-ttu-id="1f615-126">Elemento GroupBy per View (Format)</span><span class="sxs-lookup"><span data-stu-id="1f615-126">GroupBy Element for View (Format)</span></span>](./groupby-element-for-view-format.md)

[<span data-ttu-id="1f615-127">Scrittura di un file di formattazione di PowerShell</span><span class="sxs-lookup"><span data-stu-id="1f615-127">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)