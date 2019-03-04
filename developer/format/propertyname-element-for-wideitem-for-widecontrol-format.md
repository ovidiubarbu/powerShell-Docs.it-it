---
title: Elemento PropertyName per WideItem per WideControl (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 3d91d0e6-bf18-4587-b651-db66849e5df5
caps.latest.revision: 6
ms.openlocfilehash: 326880834cd82ab826aadc409cd7a8f21cd36824
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/03/2019
ms.locfileid: "56860957"
---
# <a name="propertyname-element-for-wideitem-for-widecontrol-format"></a><span data-ttu-id="77c13-102">Elemento PropertyName per WideItem per WideControl (formato)</span><span class="sxs-lookup"><span data-stu-id="77c13-102">PropertyName Element for WideItem for WideControl (Format)</span></span>

<span data-ttu-id="77c13-103">Specifica la proprietà dell'oggetto il cui valore viene visualizzato in visualizzazione estesa.</span><span class="sxs-lookup"><span data-stu-id="77c13-103">Specifies the property of the object whose value is displayed in the wide view.</span></span>

<span data-ttu-id="77c13-104">Elemento (formato) elemento ViewDefinitions (formato) visualizzazione elemento (formato) elemento WideControl (formato) elemento WideEntries (formato) elemento WideEntry (formato) elemento WideItem (formato) PropertyName elemento di configurazione per WideItem (formato)</span><span class="sxs-lookup"><span data-stu-id="77c13-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) WideControl Element (Format) WideEntries Element (Format) WideEntry Element (Format) WideItem Element (Format) PropertyName Element for WideItem (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="77c13-105">Sintassi</span><span class="sxs-lookup"><span data-stu-id="77c13-105">Syntax</span></span>

```xml
<PropertyName>.NetTypeProperty</PropertyName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="77c13-106">Attributi ed elementi</span><span class="sxs-lookup"><span data-stu-id="77c13-106">Attributes and Elements</span></span>

<span data-ttu-id="77c13-107">Le sezioni seguenti descrivono gli attributi, elementi figlio ed elemento padre dell'elemento di `PropertyName` elemento.</span><span class="sxs-lookup"><span data-stu-id="77c13-107">The following sections describe the attributes, child elements, and parent element of the `PropertyName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="77c13-108">Attributes</span><span class="sxs-lookup"><span data-stu-id="77c13-108">Attributes</span></span>

<span data-ttu-id="77c13-109">Nessuna.</span><span class="sxs-lookup"><span data-stu-id="77c13-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="77c13-110">Elementi figlio</span><span class="sxs-lookup"><span data-stu-id="77c13-110">Child Elements</span></span>

<span data-ttu-id="77c13-111">Nessuna.</span><span class="sxs-lookup"><span data-stu-id="77c13-111">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="77c13-112">Elementi padre</span><span class="sxs-lookup"><span data-stu-id="77c13-112">Parent Elements</span></span>

|<span data-ttu-id="77c13-113">Elemento</span><span class="sxs-lookup"><span data-stu-id="77c13-113">Element</span></span>|<span data-ttu-id="77c13-114">Description</span><span class="sxs-lookup"><span data-stu-id="77c13-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="77c13-115">Elemento WideItem (formato)</span><span class="sxs-lookup"><span data-stu-id="77c13-115">WideItem Element (Format)</span></span>](./wideitem-element-for-widecontrol-format.md)|<span data-ttu-id="77c13-116">Definisce le proprietà il cui valore viene visualizzato nella vista a livello di script.</span><span class="sxs-lookup"><span data-stu-id="77c13-116">Defines the property or script whose value is displayed in the wide view.</span></span>|

## <a name="text-value"></a><span data-ttu-id="77c13-117">Valore di testo</span><span class="sxs-lookup"><span data-stu-id="77c13-117">Text Value</span></span>

<span data-ttu-id="77c13-118">Specificare il nome della proprietà il cui valore viene visualizzato.</span><span class="sxs-lookup"><span data-stu-id="77c13-118">Specify the name of the property whose value is displayed.</span></span>

## <a name="remarks"></a><span data-ttu-id="77c13-119">Osservazioni</span><span class="sxs-lookup"><span data-stu-id="77c13-119">Remarks</span></span>

<span data-ttu-id="77c13-120">Per altre informazioni sui componenti di una visualizzazione più ampia, vedere [creazione di una visualizzazione più ampia](./creating-a-wide-view.md).</span><span class="sxs-lookup"><span data-stu-id="77c13-120">For more information about the components of a wide view, see [Creating a Wide View](./creating-a-wide-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="77c13-121">Esempio</span><span class="sxs-lookup"><span data-stu-id="77c13-121">Example</span></span>

<span data-ttu-id="77c13-122">In questo esempio mostra una visualizzazione più ampia che visualizza il valore della proprietà ProcessName del [Diagnostics](/dotnet/api/System.Diagnostics.Process) oggetto.</span><span class="sxs-lookup"><span data-stu-id="77c13-122">This example shows a wide view that displays the value of the ProcessName property of the [System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process) object.</span></span>

```xml
View>
  <Name>process</Name>
  <ViewSelectedBy>
    <TypeName>System.Diagnostics.Process</TypeName>
  </ViewSelectedBy>
  <WideControl>
    <WideEntries>
      <WideEntry>
        <WideItem>
          <PropertyName>ProcessName</PropertyName>
        </WideItem>
      </WideEntry>
    </WideEntries>
  </WideControl>
</View>

```

## <a name="see-also"></a><span data-ttu-id="77c13-123">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="77c13-123">See Also</span></span>

[<span data-ttu-id="77c13-124">Elemento WideItem (formato)</span><span class="sxs-lookup"><span data-stu-id="77c13-124">WideItem Element (Format)</span></span>](./wideitem-element-for-widecontrol-format.md)

[<span data-ttu-id="77c13-125">Creazione di una visualizzazione più ampia</span><span class="sxs-lookup"><span data-stu-id="77c13-125">Creating a Wide View</span></span>](./creating-a-wide-view.md)

[<span data-ttu-id="77c13-126">La scrittura di un File di formattazione di PowerShell</span><span class="sxs-lookup"><span data-stu-id="77c13-126">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
