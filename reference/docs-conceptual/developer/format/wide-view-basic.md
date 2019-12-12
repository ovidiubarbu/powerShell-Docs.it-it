---
title: Visualizzazione estesa (di base) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 9abb63b8-6d02-4e24-9c0e-2d15a04e9051
caps.latest.revision: 8
ms.openlocfilehash: 7a36f548a3eccdf2c9cad04a8bfe28bf4e8d6dfd
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/05/2019
ms.locfileid: "72367940"
---
# <a name="wide-view-basic"></a><span data-ttu-id="a8306-102">Visualizzazione più ampia (base)</span><span class="sxs-lookup"><span data-stu-id="a8306-102">Wide View (Basic)</span></span>

<span data-ttu-id="a8306-103">In questo esempio viene illustrato come implementare una visualizzazione di base estesa che visualizza [System. ServiceProcess. ServiceController? DisplayProperty = oggetti FullName](/dotnet/api/System.ServiceProcess.ServiceController) restituiti dal cmdlet `Get-Service`.</span><span class="sxs-lookup"><span data-stu-id="a8306-103">This example shows how to implement a basic wide view that displays the [System.Serviceprocess.Servicecontroller?Displayproperty=Fullname](/dotnet/api/System.ServiceProcess.ServiceController) objects returned by the `Get-Service` cmdlet.</span></span> <span data-ttu-id="a8306-104">Per ulteriori informazioni sui componenti di una visualizzazione estesa, vedere [creazione di un'ampia visualizzazione](./creating-a-wide-view.md).</span><span class="sxs-lookup"><span data-stu-id="a8306-104">For more information about the components of a wide view, see [Creating a Wide View](./creating-a-wide-view.md).</span></span>

### <a name="to-load-this-formatting-file"></a><span data-ttu-id="a8306-105">Per caricare il file di formattazione</span><span class="sxs-lookup"><span data-stu-id="a8306-105">To load this formatting file</span></span>

1. <span data-ttu-id="a8306-106">Copiare il codice XML dalla sezione esempio di questo argomento in un file di testo.</span><span class="sxs-lookup"><span data-stu-id="a8306-106">Copy the XML from the Example section of this topic into a text file.</span></span>

2. <span data-ttu-id="a8306-107">Salvare il file di testo.</span><span class="sxs-lookup"><span data-stu-id="a8306-107">Save the text file.</span></span> <span data-ttu-id="a8306-108">Assicurarsi di aggiungere l'estensione `format.ps1xml` al file per identificarla come un file di formattazione.</span><span class="sxs-lookup"><span data-stu-id="a8306-108">Be sure to add the `format.ps1xml` extension to the file to identify it as a formatting file.</span></span>

3. <span data-ttu-id="a8306-109">Aprire Windows PowerShell ed eseguire il comando seguente per caricare il file di formattazione nella sessione corrente: `Update-formatdata -prependpath PathToFormattingFile`.</span><span class="sxs-lookup"><span data-stu-id="a8306-109">Open Windows PowerShell, and run the following command to load the formatting file into the current session: `Update-formatdata -prependpath PathToFormattingFile`.</span></span>

   > [!WARNING]
   > <span data-ttu-id="a8306-110">Questo file di formattazione definisce la visualizzazione di un oggetto già definito da un file di formattazione di Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="a8306-110">This formatting file defines the display of an object that is already defined by a Windows PowerShell formatting file.</span></span> <span data-ttu-id="a8306-111">Quando si esegue il cmdlet, è necessario utilizzare il parametro `prependPath` e non è possibile caricare il file di formattazione come modulo.</span><span class="sxs-lookup"><span data-stu-id="a8306-111">You must use the `prependPath` parameter when you run the cmdlet, and you cannot load this formatting file as a module.</span></span>

## <a name="demonstrates"></a><span data-ttu-id="a8306-112">Illustra</span><span class="sxs-lookup"><span data-stu-id="a8306-112">Demonstrates</span></span>

<span data-ttu-id="a8306-113">In questo file di formattazione vengono illustrati gli elementi XML seguenti:</span><span class="sxs-lookup"><span data-stu-id="a8306-113">This formatting file demonstrates the following XML elements:</span></span>

- <span data-ttu-id="a8306-114">Elemento del [nome](./name-element-for-view-format.md) per la visualizzazione.</span><span class="sxs-lookup"><span data-stu-id="a8306-114">The [Name](./name-element-for-view-format.md) element for the view.</span></span>

- <span data-ttu-id="a8306-115">Elemento [ViewSelectedBy](./viewselectedby-element-format.md) che definisce quali oggetti vengono visualizzati dalla visualizzazione.</span><span class="sxs-lookup"><span data-stu-id="a8306-115">The [ViewSelectedBy](./viewselectedby-element-format.md) element that defines what objects are displayed by the view.</span></span>

- <span data-ttu-id="a8306-116">Elemento [WideItem](./wideitem-element-for-widecontrol-format.md) che definisce la proprietà visualizzata dalla visualizzazione.</span><span class="sxs-lookup"><span data-stu-id="a8306-116">The [WideItem](./wideitem-element-for-widecontrol-format.md) element that defines what property is displayed by the view.</span></span>

## <a name="example"></a><span data-ttu-id="a8306-117">Esempio</span><span class="sxs-lookup"><span data-stu-id="a8306-117">Example</span></span>

<span data-ttu-id="a8306-118">Il codice XML seguente definisce una visualizzazione estesa che Visualizza il valore della proprietà [System. ServiceProcess. ServiceController. ServiceName](/dotnet/api/System.ServiceProcess.ServiceController.ServiceName) .</span><span class="sxs-lookup"><span data-stu-id="a8306-118">The following XML defines a wide view that displays the value of the [System.Serviceprocess.Servicecontroller.Servicename](/dotnet/api/System.ServiceProcess.ServiceController.ServiceName) property.</span></span>

```xml
<?xml version="1.0" encoding="utf-8" ?>

<Configuration>
  <ViewDefinitions>
    <View>
      <Name>ServiceWideView</Name>
      <ViewSelectedBy>
        <TypeName>System.ServiceProcess.ServiceController</TypeName>
      </ViewSelectedBy>
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

<span data-ttu-id="a8306-119">Nell'esempio seguente viene illustrato come Windows PowerShell visualizzi [System. ServiceProcess. ServiceController? DisplayProperty = oggetti FullName](/dotnet/api/System.ServiceProcess.ServiceController) dopo il caricamento del file di formato.</span><span class="sxs-lookup"><span data-stu-id="a8306-119">The following example shows how Windows PowerShell displays the [System.Serviceprocess.Servicecontroller?Displayproperty=Fullname](/dotnet/api/System.ServiceProcess.ServiceController) objects after this format file is loaded.</span></span>

```powershell
Get-Service f*
```

```output
Fax                      FCSAM
fdPHost                  FDResPub
FontCache                FontCache3.0.0.0
FSysAgent                FwcAgent
```

## <a name="see-also"></a><span data-ttu-id="a8306-120">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="a8306-120">See Also</span></span>

[<span data-ttu-id="a8306-121">Esempi di file di formattazione</span><span class="sxs-lookup"><span data-stu-id="a8306-121">Examples of Formatting Files</span></span>](./examples-of-formatting-files.md)

[<span data-ttu-id="a8306-122">Scrittura di un file di formattazione di PowerShell</span><span class="sxs-lookup"><span data-stu-id="a8306-122">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
