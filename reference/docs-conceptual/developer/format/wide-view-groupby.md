---
title: Visualizzazione estesa (GroupBy) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 39388197-4ff9-4889-aa32-526011afa1f6
caps.latest.revision: 6
ms.openlocfilehash: e95ec550a7815a76a8bd7f9526dfa405a9644360
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/05/2019
ms.locfileid: "72367950"
---
# <a name="wide-view-groupby"></a><span data-ttu-id="2f268-102">Visualizzazione più ampia (GroupBy)</span><span class="sxs-lookup"><span data-stu-id="2f268-102">Wide View (GroupBy)</span></span>

<span data-ttu-id="2f268-103">Questo esempio illustra come implementare una visualizzazione estesa che Visualizza i gruppi di [System. ServiceProcess. ServiceController? DisplayProperty = oggetti FullName](/dotnet/api/System.ServiceProcess.ServiceController) restituiti dal cmdlet `Get-Service`.</span><span class="sxs-lookup"><span data-stu-id="2f268-103">This example shows how to implement a wide view that displays groups of [System.Serviceprocess.Servicecontroller?Displayproperty=Fullname](/dotnet/api/System.ServiceProcess.ServiceController) objects returned by the `Get-Service` cmdlet.</span></span> <span data-ttu-id="2f268-104">Per ulteriori informazioni sui componenti di una visualizzazione estesa, vedere [creazione di un'ampia visualizzazione](./creating-a-wide-view.md).</span><span class="sxs-lookup"><span data-stu-id="2f268-104">For more information about the components of a wide view, see [Creating a Wide View](./creating-a-wide-view.md).</span></span>

### <a name="to-load-this-formatting-file"></a><span data-ttu-id="2f268-105">Per caricare il file di formattazione</span><span class="sxs-lookup"><span data-stu-id="2f268-105">To load this formatting file</span></span>

1. <span data-ttu-id="2f268-106">Copiare il codice XML dalla sezione esempio di questo argomento in un file di testo.</span><span class="sxs-lookup"><span data-stu-id="2f268-106">Copy the XML from the Example section of this topic into a text file.</span></span>

2. <span data-ttu-id="2f268-107">Salvare il file di testo.</span><span class="sxs-lookup"><span data-stu-id="2f268-107">Save the text file.</span></span> <span data-ttu-id="2f268-108">Assicurarsi di aggiungere l'estensione `format.ps1xml` al file per identificarla come un file di formattazione.</span><span class="sxs-lookup"><span data-stu-id="2f268-108">Be sure to add the `format.ps1xml` extension to the file to identify it as a formatting file.</span></span>

3. <span data-ttu-id="2f268-109">Aprire Windows PowerShell ed eseguire il comando seguente per caricare il file di formattazione nella sessione corrente: `Update-formatdata -prependpath PathToFormattingFile`.</span><span class="sxs-lookup"><span data-stu-id="2f268-109">Open Windows PowerShell, and run the following command to load the formatting file into the current session: `Update-formatdata -prependpath PathToFormattingFile`.</span></span>

   > [!WARNING]
   > <span data-ttu-id="2f268-110">Questo file di formattazione definisce la visualizzazione di un oggetto già definito da un file di formattazione di Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="2f268-110">This formatting file defines the display of an object that is already defined by a Windows PowerShell formatting files.</span></span> <span data-ttu-id="2f268-111">Quando si esegue il cmdlet, è necessario utilizzare il parametro `prependPath` e non è possibile caricare il file di formattazione come modulo.</span><span class="sxs-lookup"><span data-stu-id="2f268-111">You must use the `prependPath` parameter when you run the cmdlet, and you cannot load this formatting file as a module.</span></span>

## <a name="demonstrates"></a><span data-ttu-id="2f268-112">Illustra</span><span class="sxs-lookup"><span data-stu-id="2f268-112">Demonstrates</span></span>

<span data-ttu-id="2f268-113">In questo file di formattazione vengono illustrati gli elementi XML seguenti:</span><span class="sxs-lookup"><span data-stu-id="2f268-113">This formatting file demonstrates the following XML elements:</span></span>

- <span data-ttu-id="2f268-114">Elemento del [nome](./name-element-for-view-format.md) per la visualizzazione.</span><span class="sxs-lookup"><span data-stu-id="2f268-114">The [Name](./name-element-for-view-format.md) element for the view.</span></span>

- <span data-ttu-id="2f268-115">Elemento [ViewSelectedBy](./viewselectedby-element-format.md) che definisce quali oggetti vengono visualizzati dalla visualizzazione.</span><span class="sxs-lookup"><span data-stu-id="2f268-115">The [ViewSelectedBy](./viewselectedby-element-format.md) element that defines what objects are displayed by the view.</span></span>

- <span data-ttu-id="2f268-116">Elemento [GroupBy](./groupby-element-for-view-format.md) che definisce quando viene visualizzato un nuovo gruppo.</span><span class="sxs-lookup"><span data-stu-id="2f268-116">The [GroupBy](./groupby-element-for-view-format.md) element that defines when a new group is displayed.</span></span>

- <span data-ttu-id="2f268-117">Elemento [WideItem](./wideitem-element-for-widecontrol-format.md) che definisce la proprietà visualizzata dalla visualizzazione.</span><span class="sxs-lookup"><span data-stu-id="2f268-117">The [WideItem](./wideitem-element-for-widecontrol-format.md) element that defines what property is displayed by the view.</span></span>

## <a name="example"></a><span data-ttu-id="2f268-118">Esempio</span><span class="sxs-lookup"><span data-stu-id="2f268-118">Example</span></span>

<span data-ttu-id="2f268-119">Nel codice XML seguente viene definita un'ampia visualizzazione che consente di visualizzare gruppi di oggetti.</span><span class="sxs-lookup"><span data-stu-id="2f268-119">The following XML defines a wide view that displays groups of objects.</span></span> <span data-ttu-id="2f268-120">Ogni nuovo gruppo viene avviato quando viene modificato il valore della proprietà [System. ServiceProcess. ServiceController. ServiceType](/dotnet/api/System.ServiceProcess.ServiceController.ServiceType) .</span><span class="sxs-lookup"><span data-stu-id="2f268-120">Each new group is started when the value of the [System.Serviceprocess.Servicecontroller.Servicetype](/dotnet/api/System.ServiceProcess.ServiceController.ServiceType) property changes.</span></span>

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

<span data-ttu-id="2f268-121">Nell'esempio seguente viene illustrato come Windows PowerShell visualizzi [System. ServiceProcess. ServiceController? DisplayProperty = oggetti FullName](/dotnet/api/System.ServiceProcess.ServiceController) dopo il caricamento del file di formato.</span><span class="sxs-lookup"><span data-stu-id="2f268-121">The following example shows how Windows PowerShell displays the [System.Serviceprocess.Servicecontroller?Displayproperty=Fullname](/dotnet/api/System.ServiceProcess.ServiceController) objects after this format file is loaded.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="2f268-122">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="2f268-122">See Also</span></span>

[<span data-ttu-id="2f268-123">Esempi di file di formattazione</span><span class="sxs-lookup"><span data-stu-id="2f268-123">Examples of Formatting Files</span></span>](./examples-of-formatting-files.md)

[<span data-ttu-id="2f268-124">Scrittura di un file di formattazione di PowerShell</span><span class="sxs-lookup"><span data-stu-id="2f268-124">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
