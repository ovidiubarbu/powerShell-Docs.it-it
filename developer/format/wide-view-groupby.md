---
title: Visualizzazione più ampia (GroupBy) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 39388197-4ff9-4889-aa32-526011afa1f6
caps.latest.revision: 6
ms.openlocfilehash: e95ec550a7815a76a8bd7f9526dfa405a9644360
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62083655"
---
# <a name="wide-view-groupby"></a><span data-ttu-id="59dff-102">Visualizzazione più ampia (GroupBy)</span><span class="sxs-lookup"><span data-stu-id="59dff-102">Wide View (GroupBy)</span></span>

<span data-ttu-id="59dff-103">In questo esempio viene illustrato come implementare una visualizzazione più ampia che consente di visualizzare gruppi di [System.Serviceprocess.Servicecontroller? Displayproperty = Fullname](/dotnet/api/System.ServiceProcess.ServiceController) gli oggetti restituiti dai `Get-Service` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="59dff-103">This example shows how to implement a wide view that displays groups of [System.Serviceprocess.Servicecontroller?Displayproperty=Fullname](/dotnet/api/System.ServiceProcess.ServiceController) objects returned by the `Get-Service` cmdlet.</span></span> <span data-ttu-id="59dff-104">Per altre informazioni sui componenti di una visualizzazione più ampia, vedere [creazione di una visualizzazione più ampia](./creating-a-wide-view.md).</span><span class="sxs-lookup"><span data-stu-id="59dff-104">For more information about the components of a wide view, see [Creating a Wide View](./creating-a-wide-view.md).</span></span>

### <a name="to-load-this-formatting-file"></a><span data-ttu-id="59dff-105">Per caricare questo file di formattazione</span><span class="sxs-lookup"><span data-stu-id="59dff-105">To load this formatting file</span></span>

1. <span data-ttu-id="59dff-106">Copiare il codice XML della sezione di questo argomento in un file di testo.</span><span class="sxs-lookup"><span data-stu-id="59dff-106">Copy the XML from the Example section of this topic into a text file.</span></span>

2. <span data-ttu-id="59dff-107">Salvare il file di testo.</span><span class="sxs-lookup"><span data-stu-id="59dff-107">Save the text file.</span></span> <span data-ttu-id="59dff-108">Assicurarsi di aggiungere il `format.ps1xml` estensione del file per identificarla come un file di formattazione.</span><span class="sxs-lookup"><span data-stu-id="59dff-108">Be sure to add the `format.ps1xml` extension to the file to identify it as a formatting file.</span></span>

3. <span data-ttu-id="59dff-109">Aprire Windows PowerShell ed eseguire il comando seguente per caricare il file di formattazione nella sessione corrente: `Update-formatdata -prependpath PathToFormattingFile`.</span><span class="sxs-lookup"><span data-stu-id="59dff-109">Open Windows PowerShell, and run the following command to load the formatting file into the current session: `Update-formatdata -prependpath PathToFormattingFile`.</span></span>

   > [!WARNING]
   > <span data-ttu-id="59dff-110">Questo file di formattazione definita la visualizzazione di un oggetto che è già definita da un file di formattazione di Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="59dff-110">This formatting file defines the display of an object that is already defined by a Windows PowerShell formatting files.</span></span> <span data-ttu-id="59dff-111">È necessario usare il `prependPath` parametro quando si esegue il cmdlet, e non è possibile caricare questo tipo di formattazione del file come modulo.</span><span class="sxs-lookup"><span data-stu-id="59dff-111">You must use the `prependPath` parameter when you run the cmdlet, and you cannot load this formatting file as a module.</span></span>

## <a name="demonstrates"></a><span data-ttu-id="59dff-112">Di seguito viene illustrato</span><span class="sxs-lookup"><span data-stu-id="59dff-112">Demonstrates</span></span>

<span data-ttu-id="59dff-113">Questo file di formattazione illustra gli elementi XML seguenti:</span><span class="sxs-lookup"><span data-stu-id="59dff-113">This formatting file demonstrates the following XML elements:</span></span>

- <span data-ttu-id="59dff-114">Il [nome](./name-element-for-view-format.md) (elemento) per la visualizzazione.</span><span class="sxs-lookup"><span data-stu-id="59dff-114">The [Name](./name-element-for-view-format.md) element for the view.</span></span>

- <span data-ttu-id="59dff-115">Il [ViewSelectedBy](./viewselectedby-element-format.md) elemento che definisce quali oggetti vengono visualizzati nella visualizzazione.</span><span class="sxs-lookup"><span data-stu-id="59dff-115">The [ViewSelectedBy](./viewselectedby-element-format.md) element that defines what objects are displayed by the view.</span></span>

- <span data-ttu-id="59dff-116">Il [GroupBy](./groupby-element-for-view-format.md) elemento che definisce quando viene visualizzato un nuovo gruppo.</span><span class="sxs-lookup"><span data-stu-id="59dff-116">The [GroupBy](./groupby-element-for-view-format.md) element that defines when a new group is displayed.</span></span>

- <span data-ttu-id="59dff-117">Il [WideItem](./wideitem-element-for-widecontrol-format.md) elemento che definisce quale proprietà viene visualizzata nella visualizzazione.</span><span class="sxs-lookup"><span data-stu-id="59dff-117">The [WideItem](./wideitem-element-for-widecontrol-format.md) element that defines what property is displayed by the view.</span></span>

## <a name="example"></a><span data-ttu-id="59dff-118">Esempio</span><span class="sxs-lookup"><span data-stu-id="59dff-118">Example</span></span>

<span data-ttu-id="59dff-119">Il codice XML seguente definisce una visualizzazione più ampia che consente di visualizzare gruppi di oggetti.</span><span class="sxs-lookup"><span data-stu-id="59dff-119">The following XML defines a wide view that displays groups of objects.</span></span> <span data-ttu-id="59dff-120">Ogni nuovo gruppo viene avviato quando il valore della [System.Serviceprocess.Servicecontroller.Servicetype](/dotnet/api/System.ServiceProcess.ServiceController.ServiceType) le modifiche alle proprietà.</span><span class="sxs-lookup"><span data-stu-id="59dff-120">Each new group is started when the value of the [System.Serviceprocess.Servicecontroller.Servicetype](/dotnet/api/System.ServiceProcess.ServiceController.ServiceType) property changes.</span></span>

```xml
<?xml version="1.0" encoding="utf-8" ?>

<Configuration>
  <ViewDefinitions>
    <View>
      <Name>ServiceWideView</Name>
      <ViewSelectedBy>
        <TypeName>System.ServiceProcess.ServiceController</TypeName>
      </ViewSelectedBy>
      <GroupBy>
        <Label>Service Type</Label>
        <PropertyName>ServiceType</PropertyName>
      </GroupBy>
      <WideControl>
        <WideEntries>
          <WideEntry>
            <WideItem>
              <PropertyName>ServiceName</PropertyName>
            </WideItem>
          </WideEntry>
        </WideEntries>
      </WideControl>
    </View>
  </ViewDefinitions>
</Configuration>
```

<span data-ttu-id="59dff-121">Nell'esempio seguente viene illustrato come Windows PowerShell Visualizza il [System.Serviceprocess.Servicecontroller? Displayproperty = Fullname](/dotnet/api/System.ServiceProcess.ServiceController) oggetti dopo il caricamento di questo file di formato.</span><span class="sxs-lookup"><span data-stu-id="59dff-121">The following example shows how Windows PowerShell displays the [System.Serviceprocess.Servicecontroller?Displayproperty=Fullname](/dotnet/api/System.ServiceProcess.ServiceController) objects after this format file is loaded.</span></span>

```powershell
Get-Service f*
```

```output
   Service Type: Win32OwnProcess

Fax                             FCSAM

   Service Type: Win32ShareProcess

fdPHost                         FDResPub
FontCache

   Service Type: Win32OwnProcess

FontCache3.0.0.0                FSysAgent
FwcAgent
```

## <a name="see-also"></a><span data-ttu-id="59dff-122">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="59dff-122">See Also</span></span>

[<span data-ttu-id="59dff-123">Esempi di file di formattazione</span><span class="sxs-lookup"><span data-stu-id="59dff-123">Examples of Formatting Files</span></span>](./examples-of-formatting-files.md)

[<span data-ttu-id="59dff-124">La scrittura di un File di formattazione di PowerShell</span><span class="sxs-lookup"><span data-stu-id="59dff-124">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
