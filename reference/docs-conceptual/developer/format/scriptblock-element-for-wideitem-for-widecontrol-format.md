---
title: Elemento ScriptBlock per WideItem per WideControl (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e00e8f36-76f2-49a0-9b02-3a2a7fceb2dd
caps.latest.revision: 8
ms.openlocfilehash: 6534e9dbfbe0dedf60dadd6467cff9ad9b447ba4
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/05/2019
ms.locfileid: "72362030"
---
# <a name="scriptblock-element-for-wideitem-for-widecontrol-format"></a><span data-ttu-id="c6b89-102">Elemento ScriptBlock per WideItem per WideControl (formato)</span><span class="sxs-lookup"><span data-stu-id="c6b89-102">ScriptBlock Element for WideItem for WideControl (Format)</span></span>

<span data-ttu-id="c6b89-103">Specifica lo script il cui valore viene visualizzato nella visualizzazione estesa.</span><span class="sxs-lookup"><span data-stu-id="c6b89-103">Specifies the script whose value is displayed in the wide view.</span></span>

<span data-ttu-id="c6b89-104">Elemento Configuration (Format) elemento ViewDefinitions (Format) elemento View (Format) elemento WideControl (Format) elemento WideEntries (Format) elemento WideEntry (Format) elemento WideItem (Format) elemento ScriptBlock per WideItem (Format)</span><span class="sxs-lookup"><span data-stu-id="c6b89-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) WideControl Element (Format) WideEntries Element (Format) WideEntry Element (Format) WideItem Element (Format) ScriptBlock Element for WideItem (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="c6b89-105">Sintassi</span><span class="sxs-lookup"><span data-stu-id="c6b89-105">Syntax</span></span>

```xml
<ScriptBlock>ScriptToExecute</ScriptBlock>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="c6b89-106">Attributi ed elementi</span><span class="sxs-lookup"><span data-stu-id="c6b89-106">Attributes and Elements</span></span>

<span data-ttu-id="c6b89-107">Nelle sezioni seguenti vengono descritti gli attributi, gli elementi figlio e l'elemento padre dell'elemento `ScriptBlock`.</span><span class="sxs-lookup"><span data-stu-id="c6b89-107">The following sections describe the attributes, child elements, and parent element of the `ScriptBlock` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="c6b89-108">Attributi</span><span class="sxs-lookup"><span data-stu-id="c6b89-108">Attributes</span></span>

<span data-ttu-id="c6b89-109">Nessuna.</span><span class="sxs-lookup"><span data-stu-id="c6b89-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="c6b89-110">Elementi figlio</span><span class="sxs-lookup"><span data-stu-id="c6b89-110">Child Elements</span></span>

<span data-ttu-id="c6b89-111">Nessuna.</span><span class="sxs-lookup"><span data-stu-id="c6b89-111">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="c6b89-112">Elementi padre</span><span class="sxs-lookup"><span data-stu-id="c6b89-112">Parent Elements</span></span>

|<span data-ttu-id="c6b89-113">Elemento</span><span class="sxs-lookup"><span data-stu-id="c6b89-113">Element</span></span>|<span data-ttu-id="c6b89-114">Description</span><span class="sxs-lookup"><span data-stu-id="c6b89-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="c6b89-115">Elemento WideItem (Format)</span><span class="sxs-lookup"><span data-stu-id="c6b89-115">WideItem Element (Format)</span></span>](./wideitem-element-for-widecontrol-format.md)|<span data-ttu-id="c6b89-116">Definisce la proprietà o il blocco di script il cui valore viene visualizzato nella visualizzazione estesa.</span><span class="sxs-lookup"><span data-stu-id="c6b89-116">Defines the property or script block whose value is displayed in the wide view.</span></span>|

## <a name="text-value"></a><span data-ttu-id="c6b89-117">Valore testo</span><span class="sxs-lookup"><span data-stu-id="c6b89-117">Text Value</span></span>

<span data-ttu-id="c6b89-118">Specificare lo script di cui viene visualizzato il valore.</span><span class="sxs-lookup"><span data-stu-id="c6b89-118">Specify the script whose value is displayed.</span></span>

## <a name="remarks"></a><span data-ttu-id="c6b89-119">Osservazioni</span><span class="sxs-lookup"><span data-stu-id="c6b89-119">Remarks</span></span>

<span data-ttu-id="c6b89-120">Per ulteriori informazioni sui componenti di una visualizzazione estesa, vedere [creazione di un'ampia visualizzazione](./creating-a-wide-view.md).</span><span class="sxs-lookup"><span data-stu-id="c6b89-120">For more information about the components of a wide view, see [Creating a Wide View](./creating-a-wide-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="c6b89-121">Esempio</span><span class="sxs-lookup"><span data-stu-id="c6b89-121">Example</span></span>

<span data-ttu-id="c6b89-122">In questo esempio viene illustrato un elemento `WideItem` che definisce uno script il cui valore viene visualizzato nella vista.</span><span class="sxs-lookup"><span data-stu-id="c6b89-122">This example shows a `WideItem` element that defines a script whose value is displayed in the view.</span></span>

```xml
<WideItem>
  <ScriptBlock>ScriptToExecute</ScriptBlock>
</WideItem>
```

## <a name="see-also"></a><span data-ttu-id="c6b89-123">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="c6b89-123">See Also</span></span>

[<span data-ttu-id="c6b89-124">Elemento WideItem (Format)</span><span class="sxs-lookup"><span data-stu-id="c6b89-124">WideItem Element (Format)</span></span>](./wideitem-element-for-widecontrol-format.md)

[<span data-ttu-id="c6b89-125">Creazione di una visualizzazione estesa</span><span class="sxs-lookup"><span data-stu-id="c6b89-125">Creating a Wide View</span></span>](./creating-a-wide-view.md)

[<span data-ttu-id="c6b89-126">Scrittura di un file di formattazione di PowerShell</span><span class="sxs-lookup"><span data-stu-id="c6b89-126">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
