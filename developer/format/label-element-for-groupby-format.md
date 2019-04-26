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
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62065411"
---
# <a name="label-element-for-groupby-format"></a><span data-ttu-id="e1967-102">Elemento Label per GroupBy (formato)</span><span class="sxs-lookup"><span data-stu-id="e1967-102">Label Element for GroupBy (Format)</span></span>

<span data-ttu-id="e1967-103">Specifica un'etichetta che viene visualizzata quando viene rilevato un nuovo gruppo.</span><span class="sxs-lookup"><span data-stu-id="e1967-103">Specifies a label that is displayed when a new group is encountered.</span></span>

<span data-ttu-id="e1967-104">Elemento di GroupBy elemento (formato) per la visualizzazione elemento ViewDefinitions (formato) configurazione elemento (formato) elemento di visualizzazione (formato) etichetta per GroupBy (formato)</span><span class="sxs-lookup"><span data-stu-id="e1967-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) GroupBy Element for View (Format) Label Element for GroupBy (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="e1967-105">Sintassi</span><span class="sxs-lookup"><span data-stu-id="e1967-105">Syntax</span></span>

```xml
<Label>DisplayedLabel</Label>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="e1967-106">Elementi e attributi</span><span class="sxs-lookup"><span data-stu-id="e1967-106">Attributes and Elements</span></span>

<span data-ttu-id="e1967-107">Le sezioni seguenti descrivono gli attributi, elementi figlio ed elemento padre dell'elemento di `Label` elemento.</span><span class="sxs-lookup"><span data-stu-id="e1967-107">The following sections describe the attributes, child elements, and parent element of the `Label` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="e1967-108">Attributes</span><span class="sxs-lookup"><span data-stu-id="e1967-108">Attributes</span></span>

<span data-ttu-id="e1967-109">Nessuna.</span><span class="sxs-lookup"><span data-stu-id="e1967-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="e1967-110">Elementi figlio</span><span class="sxs-lookup"><span data-stu-id="e1967-110">Child Elements</span></span>

<span data-ttu-id="e1967-111">Nessuna.</span><span class="sxs-lookup"><span data-stu-id="e1967-111">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="e1967-112">Elementi padre</span><span class="sxs-lookup"><span data-stu-id="e1967-112">Parent Elements</span></span>

|<span data-ttu-id="e1967-113">Elemento</span><span class="sxs-lookup"><span data-stu-id="e1967-113">Element</span></span>|<span data-ttu-id="e1967-114">Description</span><span class="sxs-lookup"><span data-stu-id="e1967-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="e1967-115">Elemento GroupBy per visualizzazione (formato)</span><span class="sxs-lookup"><span data-stu-id="e1967-115">GroupBy Element for View (Format)</span></span>](./groupby-element-for-view-format.md)|<span data-ttu-id="e1967-116">Definisce come viene visualizzato un nuovo gruppo di oggetti.</span><span class="sxs-lookup"><span data-stu-id="e1967-116">Defines how a new group of objects is displayed.</span></span>|

## <a name="text-value"></a><span data-ttu-id="e1967-117">Valore di testo</span><span class="sxs-lookup"><span data-stu-id="e1967-117">Text Value</span></span>

<span data-ttu-id="e1967-118">Specificare il testo che viene visualizzato ogni volta che Windows PowerShell rileva una nuova proprietà o un valore di script.</span><span class="sxs-lookup"><span data-stu-id="e1967-118">Specify the text that is displayed whenever Windows PowerShell encounters a new property or script value.</span></span>

## <a name="remarks"></a><span data-ttu-id="e1967-119">Osservazioni</span><span class="sxs-lookup"><span data-stu-id="e1967-119">Remarks</span></span>

<span data-ttu-id="e1967-120">Oltre al testo specificato da questo elemento, Windows PowerShell consente di visualizzare il nuovo valore che si avvia il gruppo e aggiunge una riga vuota prima e dopo il gruppo.</span><span class="sxs-lookup"><span data-stu-id="e1967-120">In addition to the text specified by this element, Windows PowerShell displays the new value that starts the group, and adds a blank line before and after the group.</span></span>

## <a name="example"></a><span data-ttu-id="e1967-121">Esempio</span><span class="sxs-lookup"><span data-stu-id="e1967-121">Example</span></span>

<span data-ttu-id="e1967-122">Nell'esempio seguente mostra l'etichetta per un nuovo gruppo.</span><span class="sxs-lookup"><span data-stu-id="e1967-122">The following example shows the label for a new group.</span></span> <span data-ttu-id="e1967-123">Etichetta visualizzata sarà simile al seguente: `Service Type: NewValueofProperty`</span><span class="sxs-lookup"><span data-stu-id="e1967-123">The displayed label would look similar to this: `Service Type: NewValueofProperty`</span></span>

```xml
<GroupBy>
  <Label>Service Type</Label>
  <PropertyName>ServiceType</PropertyName>
</GroupBy>

```

<span data-ttu-id="e1967-124">Per un esempio di un file di formattazione completato che include questo elemento, vedere [visualizzazione più ampia (GroupBy)](./wide-view-groupby.md).</span><span class="sxs-lookup"><span data-stu-id="e1967-124">For an example of a complete formatting file that includes this element, see [Wide View (GroupBy)](./wide-view-groupby.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="e1967-125">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="e1967-125">See Also</span></span>

[<span data-ttu-id="e1967-126">Elemento GroupBy per visualizzazione (formato)</span><span class="sxs-lookup"><span data-stu-id="e1967-126">GroupBy Element for View (Format)</span></span>](./groupby-element-for-view-format.md)

[<span data-ttu-id="e1967-127">La scrittura di un File di formattazione di PowerShell</span><span class="sxs-lookup"><span data-stu-id="e1967-127">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
