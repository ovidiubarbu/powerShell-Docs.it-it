---
title: L'etichetta di elemento per GroupBy (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 3351d237-e8c2-4ec5-9500-4eceadb407c2
caps.latest.revision: 11
ms.openlocfilehash: e7158711c60d13c745bbdfab9b1b9fc7d98b34e2
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/03/2019
ms.locfileid: "56862397"
---
# <a name="label-element-for-groupby-format"></a><span data-ttu-id="e90ce-102">Elemento Label per GroupBy (formato)</span><span class="sxs-lookup"><span data-stu-id="e90ce-102">Label Element for GroupBy (Format)</span></span>

<span data-ttu-id="e90ce-103">Specifica un'etichetta che viene visualizzata quando viene rilevato un nuovo gruppo.</span><span class="sxs-lookup"><span data-stu-id="e90ce-103">Specifies a label that is displayed when a new group is encountered.</span></span>

<span data-ttu-id="e90ce-104">Elemento di GroupBy elemento (formato) per la visualizzazione elemento ViewDefinitions (formato) configurazione elemento (formato) elemento di visualizzazione (formato) etichetta per GroupBy (formato)</span><span class="sxs-lookup"><span data-stu-id="e90ce-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) GroupBy Element for View (Format) Label Element for GroupBy (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="e90ce-105">Sintassi</span><span class="sxs-lookup"><span data-stu-id="e90ce-105">Syntax</span></span>

```xml
<Label>DisplayedLabel</Label>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="e90ce-106">Attributi ed elementi</span><span class="sxs-lookup"><span data-stu-id="e90ce-106">Attributes and Elements</span></span>

<span data-ttu-id="e90ce-107">Le sezioni seguenti descrivono gli attributi, elementi figlio ed elemento padre dell'elemento di `Label` elemento.</span><span class="sxs-lookup"><span data-stu-id="e90ce-107">The following sections describe the attributes, child elements, and parent element of the `Label` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="e90ce-108">Attributes</span><span class="sxs-lookup"><span data-stu-id="e90ce-108">Attributes</span></span>

<span data-ttu-id="e90ce-109">Nessuna.</span><span class="sxs-lookup"><span data-stu-id="e90ce-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="e90ce-110">Elementi figlio</span><span class="sxs-lookup"><span data-stu-id="e90ce-110">Child Elements</span></span>

<span data-ttu-id="e90ce-111">Nessuna.</span><span class="sxs-lookup"><span data-stu-id="e90ce-111">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="e90ce-112">Elementi padre</span><span class="sxs-lookup"><span data-stu-id="e90ce-112">Parent Elements</span></span>

|<span data-ttu-id="e90ce-113">Elemento</span><span class="sxs-lookup"><span data-stu-id="e90ce-113">Element</span></span>|<span data-ttu-id="e90ce-114">Description</span><span class="sxs-lookup"><span data-stu-id="e90ce-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="e90ce-115">Elemento GroupBy per visualizzazione (formato)</span><span class="sxs-lookup"><span data-stu-id="e90ce-115">GroupBy Element for View (Format)</span></span>](./groupby-element-for-view-format.md)|<span data-ttu-id="e90ce-116">Definisce come viene visualizzato un nuovo gruppo di oggetti.</span><span class="sxs-lookup"><span data-stu-id="e90ce-116">Defines how a new group of objects is displayed.</span></span>|

## <a name="text-value"></a><span data-ttu-id="e90ce-117">Valore di testo</span><span class="sxs-lookup"><span data-stu-id="e90ce-117">Text Value</span></span>

<span data-ttu-id="e90ce-118">Specificare il testo che viene visualizzato ogni volta che Windows PowerShell rileva una nuova proprietà o un valore di script.</span><span class="sxs-lookup"><span data-stu-id="e90ce-118">Specify the text that is displayed whenever Windows PowerShell encounters a new property or script value.</span></span>

## <a name="remarks"></a><span data-ttu-id="e90ce-119">Osservazioni</span><span class="sxs-lookup"><span data-stu-id="e90ce-119">Remarks</span></span>

<span data-ttu-id="e90ce-120">Oltre al testo specificato da questo elemento, Windows PowerShell consente di visualizzare il nuovo valore che si avvia il gruppo e aggiunge una riga vuota prima e dopo il gruppo.</span><span class="sxs-lookup"><span data-stu-id="e90ce-120">In addition to the text specified by this element, Windows PowerShell displays the new value that starts the group, and adds a blank line before and after the group.</span></span>

## <a name="example"></a><span data-ttu-id="e90ce-121">Esempio</span><span class="sxs-lookup"><span data-stu-id="e90ce-121">Example</span></span>

<span data-ttu-id="e90ce-122">Nell'esempio seguente mostra l'etichetta per un nuovo gruppo.</span><span class="sxs-lookup"><span data-stu-id="e90ce-122">The following example shows the label for a new group.</span></span> <span data-ttu-id="e90ce-123">Etichetta visualizzata sarà simile al seguente: `Service Type: NewValueofProperty`</span><span class="sxs-lookup"><span data-stu-id="e90ce-123">The displayed label would look similar to this: `Service Type: NewValueofProperty`</span></span>

```xml
<GroupBy>
  <Label>Service Type</Label>
  <PropertyName>ServiceType</PropertyName>
</GroupBy>

```

<span data-ttu-id="e90ce-124">Per un esempio di un file di formattazione completato che include questo elemento, vedere [visualizzazione più ampia (GroupBy)](./wide-view-groupby.md).</span><span class="sxs-lookup"><span data-stu-id="e90ce-124">For an example of a complete formatting file that includes this element, see [Wide View (GroupBy)](./wide-view-groupby.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="e90ce-125">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="e90ce-125">See Also</span></span>

[<span data-ttu-id="e90ce-126">Elemento GroupBy per visualizzazione (formato)</span><span class="sxs-lookup"><span data-stu-id="e90ce-126">GroupBy Element for View (Format)</span></span>](./groupby-element-for-view-format.md)

[<span data-ttu-id="e90ce-127">La scrittura di un File di formattazione di PowerShell</span><span class="sxs-lookup"><span data-stu-id="e90ce-127">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
