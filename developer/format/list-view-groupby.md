---
title: Visualizzazione (GroupBy) elenco | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: a2e66c86-83a7-4148-8575-c28d6d429d4f
caps.latest.revision: 6
ms.openlocfilehash: c178c4a48f9595001bcc249d5f55886fa54bb9f2
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62065292"
---
# <a name="list-view-groupby"></a><span data-ttu-id="c0db0-102">Visualizzazione elenco (GroupBy)</span><span class="sxs-lookup"><span data-stu-id="c0db0-102">List View (GroupBy)</span></span>

<span data-ttu-id="c0db0-103">In questo esempio viene illustrato come implementare una visualizzazione elenco che separa le righe dell'elenco in gruppi.</span><span class="sxs-lookup"><span data-stu-id="c0db0-103">This example shows how to implement a list view that separates the rows of the list into groups.</span></span> <span data-ttu-id="c0db0-104">Questa vista elenco vengono visualizzate le proprietà del [System.Serviceprocess.Servicecontroller? Displayproperty = Fullname](/dotnet/api/System.ServiceProcess.ServiceController) gli oggetti restituiti dai [Get-Service](/powershell/module/Microsoft.PowerShell.Management/Get-Service) cmdlet.</span><span class="sxs-lookup"><span data-stu-id="c0db0-104">This list view displays the properties of the [System.Serviceprocess.Servicecontroller?Displayproperty=Fullname](/dotnet/api/System.ServiceProcess.ServiceController) objects returned by the [Get-Service](/powershell/module/Microsoft.PowerShell.Management/Get-Service) cmdlet.</span></span> <span data-ttu-id="c0db0-105">Per altre informazioni sui componenti di una visualizzazione elenco, vedere [creazione di una visualizzazione elenco](./creating-a-list-view.md).</span><span class="sxs-lookup"><span data-stu-id="c0db0-105">For more information about the components of a list view, see [Creating a List View](./creating-a-list-view.md).</span></span>

### <a name="to-load-this-formatting-file"></a><span data-ttu-id="c0db0-106">Per caricare questo file di formattazione</span><span class="sxs-lookup"><span data-stu-id="c0db0-106">To load this formatting file</span></span>

1. <span data-ttu-id="c0db0-107">Copiare il codice XML della sezione di questo argomento in un file di testo.</span><span class="sxs-lookup"><span data-stu-id="c0db0-107">Copy the XML from the Example section of this topic into a text file.</span></span>

2. <span data-ttu-id="c0db0-108">Salvare il file di testo.</span><span class="sxs-lookup"><span data-stu-id="c0db0-108">Save the text file.</span></span> <span data-ttu-id="c0db0-109">Assicurarsi di aggiungere il `format.ps1xml` estensione del file per identificarla come un file di formattazione.</span><span class="sxs-lookup"><span data-stu-id="c0db0-109">Be sure to add the `format.ps1xml` extension to the file to identify it as a formatting file.</span></span>

3. <span data-ttu-id="c0db0-110">Aprire Windows PowerShell ed eseguire il comando seguente per caricare il file di formattazione nella sessione corrente: `Update-formatdata -prependpath PathToFormattingFile`.</span><span class="sxs-lookup"><span data-stu-id="c0db0-110">Open Windows PowerShell, and run the following command to load the formatting file into the current session: `Update-formatdata -prependpath PathToFormattingFile`.</span></span>

   > [!WARNING]
   > <span data-ttu-id="c0db0-111">Questo file di formattazione definita la visualizzazione di un oggetto che è già definita da un file di formattazione di Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="c0db0-111">This formatting file defines the display of an object that is already defined by a Windows PowerShell formatting file.</span></span> <span data-ttu-id="c0db0-112">È necessario usare il `prependPath` parametro quando si esegue il cmdlet, e non è possibile caricare questo tipo di formattazione del file come modulo.</span><span class="sxs-lookup"><span data-stu-id="c0db0-112">You must use the `prependPath` parameter when you run the cmdlet, and you cannot load this formatting file as a module.</span></span>

## <a name="demonstrates"></a><span data-ttu-id="c0db0-113">Di seguito viene illustrato</span><span class="sxs-lookup"><span data-stu-id="c0db0-113">Demonstrates</span></span>

<span data-ttu-id="c0db0-114">Questo file di formattazione illustra gli elementi XML seguenti:</span><span class="sxs-lookup"><span data-stu-id="c0db0-114">This formatting file demonstrates the following XML elements:</span></span>

- <span data-ttu-id="c0db0-115">Il [nome](./name-element-for-view-format.md) (elemento) per la visualizzazione.</span><span class="sxs-lookup"><span data-stu-id="c0db0-115">The [Name](./name-element-for-view-format.md) element for the view.</span></span>

- <span data-ttu-id="c0db0-116">Il [ViewSelectedBy](./viewselectedby-element-format.md) elemento che definisce quali oggetti vengono visualizzati nella visualizzazione.</span><span class="sxs-lookup"><span data-stu-id="c0db0-116">The [ViewSelectedBy](./viewselectedby-element-format.md) element that defines what objects are displayed by the view.</span></span>

- <span data-ttu-id="c0db0-117">Il [GroupBy](./viewselectedby-element-format.md) elemento che definisce come viene visualizzato un nuovo gruppo di oggetti.</span><span class="sxs-lookup"><span data-stu-id="c0db0-117">The [GroupBy](./viewselectedby-element-format.md) element that defines how a new group of objects is displayed.</span></span>

- <span data-ttu-id="c0db0-118">Il [dell'oggetto ListControl](./listcontrol-element-format.md) elemento che definisce quale proprietà viene visualizzata nella visualizzazione.</span><span class="sxs-lookup"><span data-stu-id="c0db0-118">The [ListControl](./listcontrol-element-format.md) element that defines what property is displayed by the view.</span></span>

- <span data-ttu-id="c0db0-119">Il [ListItem](./listitem-element-for-listitems-for-listcontrol-format.md) elemento che definisce ciò che viene visualizzato in una riga della visualizzazione elenco.</span><span class="sxs-lookup"><span data-stu-id="c0db0-119">The [ListItem](./listitem-element-for-listitems-for-listcontrol-format.md) element that defines what is displayed in a row of the list view.</span></span>

- <span data-ttu-id="c0db0-120">Il [PropertyName](./propertyname-element-for-listitem-for-listcontrol-format.md) elemento che definisce la proprietà da visualizzare.</span><span class="sxs-lookup"><span data-stu-id="c0db0-120">The [PropertyName](./propertyname-element-for-listitem-for-listcontrol-format.md) element that defines which property is displayed.</span></span>

## <a name="example"></a><span data-ttu-id="c0db0-121">Esempio</span><span class="sxs-lookup"><span data-stu-id="c0db0-121">Example</span></span>

<span data-ttu-id="c0db0-122">Il codice XML seguente definisce una visualizzazione elenco che inizia un nuovo gruppo ogni volta che il valore della [System.Serviceprocess.Servicecontroller.Status](/dotnet/api/System.ServiceProcess.ServiceController.Status) le modifiche alle proprietà.</span><span class="sxs-lookup"><span data-stu-id="c0db0-122">The following XML defines a list view that starts a new group whenever the value of the [System.Serviceprocess.Servicecontroller.Status](/dotnet/api/System.ServiceProcess.ServiceController.Status) property changes.</span></span> <span data-ttu-id="c0db0-123">Quando viene avviata ogni gruppo, viene visualizzata un'etichetta personalizzata che include il nuovo valore della proprietà.</span><span class="sxs-lookup"><span data-stu-id="c0db0-123">When each group is started, a custom label is displayed that includes the new value of the property.</span></span>

```xml
<Configuration>
  <ViewDefinitions>
    <View>
      <Name>System.ServiceProcess.ServiceController</Name>
      <ViewSelectedBy>
        <TypeName>System.ServiceProcess.ServiceController</TypeName>
      </ViewSelectedBy>
      <GroupBy>
        <PropertyName>Status</PropertyName>
        <Label>New Service Status</Label>
      </GroupBy>
      <ListControl>
        <ListEntries>
          <ListEntry>
            <ListItems>
              <ListItem>
                <PropertyName>Name</PropertyName>
              </ListItem>
              <ListItem>
                <PropertyName>DisplayName</PropertyName>
              </ListItem>
              <ListItem>
                <PropertyName>ServiceType</PropertyName>
              </ListItem>
            </ListItems>
          </ListEntry>
        </ListEntries>
      </ListControl>
    </View>
  </ViewDefinitions>
</Configuration>
```

<span data-ttu-id="c0db0-124">Nell'esempio seguente viene illustrato come Windows PowerShell Visualizza il [System.Serviceprocess.Servicecontroller? Displayproperty = Fullname](/dotnet/api/System.ServiceProcess.ServiceController) oggetti dopo il caricamento di questo file di formato.</span><span class="sxs-lookup"><span data-stu-id="c0db0-124">The following example shows how Windows PowerShell displays the [System.Serviceprocess.Servicecontroller?Displayproperty=Fullname](/dotnet/api/System.ServiceProcess.ServiceController) objects after this format file is loaded.</span></span> <span data-ttu-id="c0db0-125">Le righe vuote aggiunte prima e dopo l'etichetta di gruppo vengono aggiunti automaticamente da Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="c0db0-125">The blank lines added before and after the group label are automatically added by Windows PowerShell.</span></span>

```powershell
Get-Service f*
```

```output
   New Service Status: Stopped

Name        : Fax
DisplayName : Fax
ServiceType : Win32OwnProcess

   New Service Status: Running

Name        : FCSAM
DisplayName : Microsoft Antimalware Service
ServiceType : Win32OwnProcess

   New Service Status: Stopped

Name        : fdPHost
DisplayName : Function Discovery Provider Host
ServiceType : Win32ShareProcess

   New Service Status: Running

Name        : FDResPub
DisplayName : Function Discovery Resource Publication
ServiceType : Win32ShareProcess

Name        : FontCache
DisplayName : Windows Font Cache Service
ServiceType : Win32ShareProcess

   New Service Status: Stopped

Name        : FontCache3.0.0.0
DisplayName : Windows Presentation Foundation Font Cache 3.0.0.0
ServiceType : Win32OwnProcess

   New Service Status: Running

Name        : FSysAgent
DisplayName : Microsoft Forefront System Agent
ServiceType : Win32OwnProcess

Name        : FwcAgent
DisplayName : Firewall Client Agent
ServiceType : Win32OwnProcess
```

## <a name="see-also"></a><span data-ttu-id="c0db0-126">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="c0db0-126">See Also</span></span>

[<span data-ttu-id="c0db0-127">Esempi di file di formattazione</span><span class="sxs-lookup"><span data-stu-id="c0db0-127">Examples of Formatting Files</span></span>](./examples-of-formatting-files.md)

[<span data-ttu-id="c0db0-128">La scrittura di un File di formattazione di PowerShell</span><span class="sxs-lookup"><span data-stu-id="c0db0-128">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
