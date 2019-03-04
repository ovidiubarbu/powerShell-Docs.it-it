---
title: Elemento TypeName per ViewSelectedBy (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 0ad807a9-d7d8-4e96-b799-9c6a7677cc2d
caps.latest.revision: 12
ms.openlocfilehash: e2028c479103cc414295dc24a0f9bb69190bfc66
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/03/2019
ms.locfileid: "56857897"
---
# <a name="typename-element-for-viewselectedby-format"></a><span data-ttu-id="7a164-102">Elemento TypeName per ViewSelectedBy (formato)</span><span class="sxs-lookup"><span data-stu-id="7a164-102">TypeName Element for ViewSelectedBy (Format)</span></span>

<span data-ttu-id="7a164-103">Specifica un oggetto .NET che viene visualizzato nella visualizzazione.</span><span class="sxs-lookup"><span data-stu-id="7a164-103">Specifies a .NET object that is displayed by the view.</span></span>

<span data-ttu-id="7a164-104">Elemento (formato) elemento ViewDefinitions (formato) visualizzazione elemento (formato) elemento ViewSelectedBy (formato) TypeName elemento di configurazione per ViewSelectedBy (formato)</span><span class="sxs-lookup"><span data-stu-id="7a164-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) ViewSelectedBy Element (Format) TypeName Element for ViewSelectedBy (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="7a164-105">Sintassi</span><span class="sxs-lookup"><span data-stu-id="7a164-105">Syntax</span></span>

```xml
<TypeName>FullyQualifiedTypeName</TypeName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="7a164-106">Attributi ed elementi</span><span class="sxs-lookup"><span data-stu-id="7a164-106">Attributes and Elements</span></span>

<span data-ttu-id="7a164-107">Le sezioni seguenti descrivono gli attributi, elementi figlio e gli elementi padre del `TypeName` elemento.</span><span class="sxs-lookup"><span data-stu-id="7a164-107">The following sections describe attributes, child elements, and the parent elements of the `TypeName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="7a164-108">Attributes</span><span class="sxs-lookup"><span data-stu-id="7a164-108">Attributes</span></span>

<span data-ttu-id="7a164-109">Nessuna.</span><span class="sxs-lookup"><span data-stu-id="7a164-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="7a164-110">Elementi figlio</span><span class="sxs-lookup"><span data-stu-id="7a164-110">Child Elements</span></span>

<span data-ttu-id="7a164-111">Nessuna.</span><span class="sxs-lookup"><span data-stu-id="7a164-111">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="7a164-112">Elementi padre</span><span class="sxs-lookup"><span data-stu-id="7a164-112">Parent Elements</span></span>

|<span data-ttu-id="7a164-113">Elemento</span><span class="sxs-lookup"><span data-stu-id="7a164-113">Element</span></span>|<span data-ttu-id="7a164-114">Description</span><span class="sxs-lookup"><span data-stu-id="7a164-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="7a164-115">Elemento ViewSelectedBy (formato)</span><span class="sxs-lookup"><span data-stu-id="7a164-115">ViewSelectedBy Element (Format)</span></span>](./viewselectedby-element-format.md)|<span data-ttu-id="7a164-116">Definisce gli oggetti .NET che vengono visualizzati nella visualizzazione.</span><span class="sxs-lookup"><span data-stu-id="7a164-116">Defines the .NET objects that are displayed by the view.</span></span>|

## <a name="text-value"></a><span data-ttu-id="7a164-117">Valore di testo</span><span class="sxs-lookup"><span data-stu-id="7a164-117">Text Value</span></span>

<span data-ttu-id="7a164-118">Specificare il nome completo del tipo .NET, ad esempio `System.IO.DirectoryInfo`.</span><span class="sxs-lookup"><span data-stu-id="7a164-118">Specify the fully qualified name of the .NET type, such as `System.IO.DirectoryInfo`.</span></span>

## <a name="remarks"></a><span data-ttu-id="7a164-119">Osservazioni</span><span class="sxs-lookup"><span data-stu-id="7a164-119">Remarks</span></span>

<span data-ttu-id="7a164-120">Per altre informazioni sul modo in cui questo elemento viene usato in diverse visualizzazioni, vedere [creazione di una visualizzazione tabella](./creating-a-table-view.md), [creazione di una visualizzazione elenco](./creating-a-list-view.md), [la creazione di una visualizzazione più ampia](./creating-a-wide-view.md), e [ I componenti di visualizzazione personalizzato](./creating-custom-controls.md).</span><span class="sxs-lookup"><span data-stu-id="7a164-120">For more information about how this element is used in different views, see [Creating a Table View](./creating-a-table-view.md), [Creating a List View](./creating-a-list-view.md), [Creating a Wide View](./creating-a-wide-view.md), and [Custom View Components](./creating-custom-controls.md).</span></span>

## <a name="example"></a><span data-ttu-id="7a164-121">Esempio</span><span class="sxs-lookup"><span data-stu-id="7a164-121">Example</span></span>

<span data-ttu-id="7a164-122">Nell'esempio seguente viene illustrato come specificare il [System.Serviceprocess.Servicecontroller](/dotnet/api/System.ServiceProcess.ServiceController) oggetto per una visualizzazione elenco.</span><span class="sxs-lookup"><span data-stu-id="7a164-122">The following example shows how to specify the [System.Serviceprocess.Servicecontroller](/dotnet/api/System.ServiceProcess.ServiceController) object for a list view.</span></span> <span data-ttu-id="7a164-123">Lo stesso schema viene utilizzato per le visualizzazioni di tabella, ampia e personalizzati.</span><span class="sxs-lookup"><span data-stu-id="7a164-123">The same schema is used for table, wide, and custom views.</span></span>

```xml
<View>
  <Name>System.ServiceProcess.ServiceController</Name>
  <ViewSelectedBy>
    <TypeName>System.ServiceProcess.ServiceController</TypeName>
  </ViewSelectedBy>
  <ListControl>...</ListControl>
</View>
```

## <a name="see-also"></a><span data-ttu-id="7a164-124">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="7a164-124">See Also</span></span>

[<span data-ttu-id="7a164-125">Creazione di una visualizzazione elenco</span><span class="sxs-lookup"><span data-stu-id="7a164-125">Creating a List View</span></span>](./creating-a-list-view.md)

[<span data-ttu-id="7a164-126">Creazione di una visualizzazione tabella</span><span class="sxs-lookup"><span data-stu-id="7a164-126">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="7a164-127">Creazione di una visualizzazione più ampia</span><span class="sxs-lookup"><span data-stu-id="7a164-127">Creating a Wide View</span></span>](./creating-a-wide-view.md)

[<span data-ttu-id="7a164-128">Creazione di controlli personalizzati</span><span class="sxs-lookup"><span data-stu-id="7a164-128">Creating Custom Controls</span></span>](./creating-custom-controls.md)

[<span data-ttu-id="7a164-129">Elemento ViewSelectedBy (formato)</span><span class="sxs-lookup"><span data-stu-id="7a164-129">ViewSelectedBy Element (Format)</span></span>](./viewselectedby-element-format.md)

[<span data-ttu-id="7a164-130">La scrittura di un File di formattazione di PowerShell</span><span class="sxs-lookup"><span data-stu-id="7a164-130">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
