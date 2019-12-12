---
title: Elemento PropertyName per WideItem per WideControl (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 3d91d0e6-bf18-4587-b651-db66849e5df5
caps.latest.revision: 6
ms.openlocfilehash: 326880834cd82ab826aadc409cd7a8f21cd36824
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/05/2019
ms.locfileid: "72364940"
---
# <a name="propertyname-element-for-wideitem-for-widecontrol-format"></a><span data-ttu-id="08b0e-102">Elemento PropertyName per WideItem per WideControl (formato)</span><span class="sxs-lookup"><span data-stu-id="08b0e-102">PropertyName Element for WideItem for WideControl (Format)</span></span>

<span data-ttu-id="08b0e-103">Specifica la proprietà dell'oggetto il cui valore viene visualizzato nella visualizzazione estesa.</span><span class="sxs-lookup"><span data-stu-id="08b0e-103">Specifies the property of the object whose value is displayed in the wide view.</span></span>

<span data-ttu-id="08b0e-104">Elemento Configuration (Format) elemento ViewDefinitions (Format) elemento View (Format) elemento WideControl (Format) elemento WideEntries (Format) elemento WideEntry (Format) elemento WideItem (Format) PropertyName per WideItem (Format)</span><span class="sxs-lookup"><span data-stu-id="08b0e-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) WideControl Element (Format) WideEntries Element (Format) WideEntry Element (Format) WideItem Element (Format) PropertyName Element for WideItem (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="08b0e-105">Sintassi</span><span class="sxs-lookup"><span data-stu-id="08b0e-105">Syntax</span></span>

```xml
<PropertyName>.NetTypeProperty</PropertyName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="08b0e-106">Attributi ed elementi</span><span class="sxs-lookup"><span data-stu-id="08b0e-106">Attributes and Elements</span></span>

<span data-ttu-id="08b0e-107">Nelle sezioni seguenti vengono descritti gli attributi, gli elementi figlio e l'elemento padre dell'elemento `PropertyName`.</span><span class="sxs-lookup"><span data-stu-id="08b0e-107">The following sections describe the attributes, child elements, and parent element of the `PropertyName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="08b0e-108">Attributi</span><span class="sxs-lookup"><span data-stu-id="08b0e-108">Attributes</span></span>

<span data-ttu-id="08b0e-109">Nessuna.</span><span class="sxs-lookup"><span data-stu-id="08b0e-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="08b0e-110">Elementi figlio</span><span class="sxs-lookup"><span data-stu-id="08b0e-110">Child Elements</span></span>

<span data-ttu-id="08b0e-111">Nessuna.</span><span class="sxs-lookup"><span data-stu-id="08b0e-111">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="08b0e-112">Elementi padre</span><span class="sxs-lookup"><span data-stu-id="08b0e-112">Parent Elements</span></span>

|<span data-ttu-id="08b0e-113">Elemento</span><span class="sxs-lookup"><span data-stu-id="08b0e-113">Element</span></span>|<span data-ttu-id="08b0e-114">Description</span><span class="sxs-lookup"><span data-stu-id="08b0e-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="08b0e-115">Elemento WideItem (Format)</span><span class="sxs-lookup"><span data-stu-id="08b0e-115">WideItem Element (Format)</span></span>](./wideitem-element-for-widecontrol-format.md)|<span data-ttu-id="08b0e-116">Definisce la proprietà o lo script il cui valore viene visualizzato nella visualizzazione estesa.</span><span class="sxs-lookup"><span data-stu-id="08b0e-116">Defines the property or script whose value is displayed in the wide view.</span></span>|

## <a name="text-value"></a><span data-ttu-id="08b0e-117">Valore testo</span><span class="sxs-lookup"><span data-stu-id="08b0e-117">Text Value</span></span>

<span data-ttu-id="08b0e-118">Consente di specificare il nome della proprietà di cui viene visualizzato il valore.</span><span class="sxs-lookup"><span data-stu-id="08b0e-118">Specify the name of the property whose value is displayed.</span></span>

## <a name="remarks"></a><span data-ttu-id="08b0e-119">Osservazioni</span><span class="sxs-lookup"><span data-stu-id="08b0e-119">Remarks</span></span>

<span data-ttu-id="08b0e-120">Per ulteriori informazioni sui componenti di una visualizzazione estesa, vedere [creazione di un'ampia visualizzazione](./creating-a-wide-view.md).</span><span class="sxs-lookup"><span data-stu-id="08b0e-120">For more information about the components of a wide view, see [Creating a Wide View](./creating-a-wide-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="08b0e-121">Esempio</span><span class="sxs-lookup"><span data-stu-id="08b0e-121">Example</span></span>

<span data-ttu-id="08b0e-122">Questo esempio mostra una visualizzazione estesa che Visualizza il valore della proprietà ProcessName dell'oggetto [System. Diagnostics. Process](/dotnet/api/System.Diagnostics.Process) .</span><span class="sxs-lookup"><span data-stu-id="08b0e-122">This example shows a wide view that displays the value of the ProcessName property of the [System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process) object.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="08b0e-123">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="08b0e-123">See Also</span></span>

[<span data-ttu-id="08b0e-124">Elemento WideItem (Format)</span><span class="sxs-lookup"><span data-stu-id="08b0e-124">WideItem Element (Format)</span></span>](./wideitem-element-for-widecontrol-format.md)

[<span data-ttu-id="08b0e-125">Creazione di una visualizzazione estesa</span><span class="sxs-lookup"><span data-stu-id="08b0e-125">Creating a Wide View</span></span>](./creating-a-wide-view.md)

[<span data-ttu-id="08b0e-126">Scrittura di un file di formattazione di PowerShell</span><span class="sxs-lookup"><span data-stu-id="08b0e-126">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
