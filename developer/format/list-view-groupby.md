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
ms.openlocfilehash: ad7ea457fe0f67bfa41f6bf81f36d4b2e4a76cb3
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/03/2019
ms.locfileid: "56860147"
---
# <a name="list-view-groupby"></a><span data-ttu-id="c3e6c-102">Visualizzazione elenco (GroupBy)</span><span class="sxs-lookup"><span data-stu-id="c3e6c-102">List View (GroupBy)</span></span>

<span data-ttu-id="c3e6c-103">In questo esempio viene illustrato come implementare una visualizzazione elenco che separa le righe dell'elenco in gruppi.</span><span class="sxs-lookup"><span data-stu-id="c3e6c-103">This example shows how to implement a list view that separates the rows of the list into groups.</span></span> <span data-ttu-id="c3e6c-104">Questa vista elenco vengono visualizzate le proprietà del [System.Serviceprocess.Servicecontroller? Displayproperty = Fullname](/dotnet/api/System.ServiceProcess.ServiceController) gli oggetti restituiti dai [Get-Service](/powershell/module/microsoft.powershell.management/get-service) cmdlet.</span><span class="sxs-lookup"><span data-stu-id="c3e6c-104">This list view displays the properties of the [System.Serviceprocess.Servicecontroller?Displayproperty=Fullname](/dotnet/api/System.ServiceProcess.ServiceController) objects returned by the [Get-Service](/powershell/module/microsoft.powershell.management/get-service) cmdlet.</span></span> <span data-ttu-id="c3e6c-105">Per altre informazioni sui componenti di una visualizzazione elenco, vedere [creazione di una visualizzazione elenco](./creating-a-list-view.md).</span><span class="sxs-lookup"><span data-stu-id="c3e6c-105">For more information about the components of a list view, see [Creating a List View](./creating-a-list-view.md).</span></span>
<span data-ttu-id="c3e6c-106">In questo esempio viene illustrato come implementare una visualizzazione elenco che separa le righe dell'elenco in gruppi.</span><span class="sxs-lookup"><span data-stu-id="c3e6c-106">This example shows how to implement a list view that separates the rows of the list into groups.</span></span> <span data-ttu-id="c3e6c-107">Questa vista elenco vengono visualizzate le proprietà del [System.Serviceprocess.Servicecontroller? Displayproperty = Fullname](/dotnet/api/System.ServiceProcess.ServiceController) gli oggetti restituiti dai [Get-Service](/powershell/module/Microsoft.PowerShell.Management/Get-Service) cmdlet.</span><span class="sxs-lookup"><span data-stu-id="c3e6c-107">This list view displays the properties of the [System.Serviceprocess.Servicecontroller?Displayproperty=Fullname](/dotnet/api/System.ServiceProcess.ServiceController) objects returned by the [Get-Service](/powershell/module/Microsoft.PowerShell.Management/Get-Service) cmdlet.</span></span> <span data-ttu-id="c3e6c-108">Per altre informazioni sui componenti di una visualizzazione elenco, vedere [creazione di una visualizzazione elenco](./creating-a-list-view.md).</span><span class="sxs-lookup"><span data-stu-id="c3e6c-108">For more information about the components of a list view, see [Creating a List View](./creating-a-list-view.md).</span></span>

### <a name="to-load-this-formatting-file"></a><span data-ttu-id="c3e6c-109">Per caricare questo file di formattazione</span><span class="sxs-lookup"><span data-stu-id="c3e6c-109">To load this formatting file</span></span>

1. <span data-ttu-id="c3e6c-110">Copiare il codice XML della sezione di questo argomento in un file di testo.</span><span class="sxs-lookup"><span data-stu-id="c3e6c-110">Copy the XML from the Example section of this topic into a text file.</span></span>

2. <span data-ttu-id="c3e6c-111">Salvare il file di testo.</span><span class="sxs-lookup"><span data-stu-id="c3e6c-111">Save the text file.</span></span> <span data-ttu-id="c3e6c-112">Assicurarsi di aggiungere il `format.ps1xml` estensione del file per identificarla come un file di formattazione.</span><span class="sxs-lookup"><span data-stu-id="c3e6c-112">Be sure to add the `format.ps1xml` extension to the file to identify it as a formatting file.</span></span>

3. <span data-ttu-id="c3e6c-113">Aprire Windows PowerShell ed eseguire il comando seguente per caricare il file di formattazione nella sessione corrente: `Update-formatdata -prependpath PathToFormattingFile`.</span><span class="sxs-lookup"><span data-stu-id="c3e6c-113">Open Windows PowerShell, and run the following command to load the formatting file into the current session: `Update-formatdata -prependpath PathToFormattingFile`.</span></span>

   > [!WARNING]
   > <span data-ttu-id="c3e6c-114">Questo file di formattazione definita la visualizzazione di un oggetto che è già definita da un file di formattazione di Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="c3e6c-114">This formatting file defines the display of an object that is already defined by a Windows PowerShell formatting file.</span></span> <span data-ttu-id="c3e6c-115">È necessario usare il `prependPath` parametro quando si esegue il cmdlet, e non è possibile caricare questo tipo di formattazione del file come modulo.</span><span class="sxs-lookup"><span data-stu-id="c3e6c-115">You must use the `prependPath` parameter when you run the cmdlet, and you cannot load this formatting file as a module.</span></span>

## <a name="demonstrates"></a><span data-ttu-id="c3e6c-116">Illustra</span><span class="sxs-lookup"><span data-stu-id="c3e6c-116">Demonstrates</span></span>

<span data-ttu-id="c3e6c-117">Questo file di formattazione illustra gli elementi XML seguenti:</span><span class="sxs-lookup"><span data-stu-id="c3e6c-117">This formatting file demonstrates the following XML elements:</span></span>

- <span data-ttu-id="c3e6c-118">Il [nome](./name-element-for-view-format.md) (elemento) per la visualizzazione.</span><span class="sxs-lookup"><span data-stu-id="c3e6c-118">The [Name](./name-element-for-view-format.md) element for the view.</span></span>

- <span data-ttu-id="c3e6c-119">Il [ViewSelectedBy](./viewselectedby-element-format.md) elemento che definisce quali oggetti vengono visualizzati nella visualizzazione.</span><span class="sxs-lookup"><span data-stu-id="c3e6c-119">The [ViewSelectedBy](./viewselectedby-element-format.md) element that defines what objects are displayed by the view.</span></span>

- <span data-ttu-id="c3e6c-120">Il [GroupBy](./viewselectedby-element-format.md) elemento che definisce come viene visualizzato un nuovo gruppo di oggetti.</span><span class="sxs-lookup"><span data-stu-id="c3e6c-120">The [GroupBy](./viewselectedby-element-format.md) element that defines how a new group of objects is displayed.</span></span>

- <span data-ttu-id="c3e6c-121">Il [dell'oggetto ListControl](./listcontrol-element-format.md) elemento che definisce quale proprietà viene visualizzata nella visualizzazione.</span><span class="sxs-lookup"><span data-stu-id="c3e6c-121">The [ListControl](./listcontrol-element-format.md) element that defines what property is displayed by the view.</span></span>

- <span data-ttu-id="c3e6c-122">Il [ListItem](./listitem-element-for-listitems-for-listcontrol-format.md) elemento che definisce ciò che viene visualizzato in una riga della visualizzazione elenco.</span><span class="sxs-lookup"><span data-stu-id="c3e6c-122">The [ListItem](./listitem-element-for-listitems-for-listcontrol-format.md) element that defines what is displayed in a row of the list view.</span></span>

- <span data-ttu-id="c3e6c-123">Il [PropertyName](./propertyname-element-for-listitem-for-listcontrol-format.md) elemento che definisce la proprietà da visualizzare.</span><span class="sxs-lookup"><span data-stu-id="c3e6c-123">The [PropertyName](./propertyname-element-for-listitem-for-listcontrol-format.md) element that defines which property is displayed.</span></span>

## <a name="example"></a><span data-ttu-id="c3e6c-124">Esempio</span><span class="sxs-lookup"><span data-stu-id="c3e6c-124">Example</span></span>

<span data-ttu-id="c3e6c-125">Il codice XML seguente definisce una visualizzazione elenco che inizia un nuovo gruppo ogni volta che il valore della [System.Serviceprocess.Servicecontroller.Status](/dotnet/api/System.ServiceProcess.ServiceController.Status) le modifiche alle proprietà.</span><span class="sxs-lookup"><span data-stu-id="c3e6c-125">The following XML defines a list view that starts a new group whenever the value of the [System.Serviceprocess.Servicecontroller.Status](/dotnet/api/System.ServiceProcess.ServiceController.Status) property changes.</span></span> <span data-ttu-id="c3e6c-126">Quando viene avviata ogni gruppo, viene visualizzata un'etichetta personalizzata che include il nuovo valore della proprietà.</span><span class="sxs-lookup"><span data-stu-id="c3e6c-126">When each group is started, a custom label is displayed that includes the new value of the property.</span></span>

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

<span data-ttu-id="c3e6c-127">Nell'esempio seguente viene illustrato come Windows PowerShell Visualizza il [System.Serviceprocess.Servicecontroller? Displayproperty = Fullname](/dotnet/api/System.ServiceProcess.ServiceController) oggetti dopo il caricamento di questo file di formato.</span><span class="sxs-lookup"><span data-stu-id="c3e6c-127">The following example shows how Windows PowerShell displays the [System.Serviceprocess.Servicecontroller?Displayproperty=Fullname](/dotnet/api/System.ServiceProcess.ServiceController) objects after this format file is loaded.</span></span> <span data-ttu-id="c3e6c-128">Le righe vuote aggiunte prima e dopo l'etichetta di gruppo vengono aggiunti automaticamente da Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="c3e6c-128">The blank lines added before and after the group label are automatically added by Windows PowerShell.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="c3e6c-129">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="c3e6c-129">See Also</span></span>

[<span data-ttu-id="c3e6c-130">Esempi di file di formattazione</span><span class="sxs-lookup"><span data-stu-id="c3e6c-130">Examples of Formatting Files</span></span>](./examples-of-formatting-files.md)

[<span data-ttu-id="c3e6c-131">La scrittura di un File di formattazione di PowerShell</span><span class="sxs-lookup"><span data-stu-id="c3e6c-131">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
