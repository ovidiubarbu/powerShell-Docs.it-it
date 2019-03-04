---
title: Visualizzazione (etichette punteggio) elenco | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 53442bb1-74a3-49f9-9150-3bc3081a7565
caps.latest.revision: 6
ms.openlocfilehash: 2bb62ab3e4fa1db9b3af8c82eb9035aa4f3e31c0
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/03/2019
ms.locfileid: "56860127"
---
# <a name="list-view-labels"></a><span data-ttu-id="1ea34-102">Visualizzazione elenco (etichette)</span><span class="sxs-lookup"><span data-stu-id="1ea34-102">List View (Labels)</span></span>

<span data-ttu-id="1ea34-103">In questo esempio viene illustrato come implementare una visualizzazione elenco che consente di visualizzare un'etichetta personalizzata per ogni riga dell'elenco.</span><span class="sxs-lookup"><span data-stu-id="1ea34-103">This example shows how to implement a list view that displays a custom label for each row of the list.</span></span> <span data-ttu-id="1ea34-104">Questa vista elenco vengono visualizzate le proprietà del [System.Serviceprocess.Servicecontroller? Displayproperty = Fullname](/dotnet/api/System.ServiceProcess.ServiceController) oggetto restituito dal [Get-Service](/powershell/module/microsoft.powershell.management/get-service) cmdlet.</span><span class="sxs-lookup"><span data-stu-id="1ea34-104">This list view displays the properties of the [System.Serviceprocess.Servicecontroller?Displayproperty=Fullname](/dotnet/api/System.ServiceProcess.ServiceController) object that is returned by the [Get-Service](/powershell/module/microsoft.powershell.management/get-service) cmdlet.</span></span> <span data-ttu-id="1ea34-105">Per altre informazioni sui componenti di una visualizzazione elenco, vedere [creazione di una visualizzazione elenco](./creating-a-list-view.md).</span><span class="sxs-lookup"><span data-stu-id="1ea34-105">For more information about the components of a list view, see [Creating a List View](./creating-a-list-view.md).</span></span>
<span data-ttu-id="1ea34-106">In questo esempio viene illustrato come implementare una visualizzazione elenco che consente di visualizzare un'etichetta personalizzata per ogni riga dell'elenco.</span><span class="sxs-lookup"><span data-stu-id="1ea34-106">This example shows how to implement a list view that displays a custom label for each row of the list.</span></span> <span data-ttu-id="1ea34-107">Questa vista elenco vengono visualizzate le proprietà del [System.Serviceprocess.Servicecontroller? Displayproperty = Fullname](/dotnet/api/System.ServiceProcess.ServiceController) oggetto restituito dal [Get-Service](/powershell/module/Microsoft.PowerShell.Management/Get-Service) cmdlet.</span><span class="sxs-lookup"><span data-stu-id="1ea34-107">This list view displays the properties of the [System.Serviceprocess.Servicecontroller?Displayproperty=Fullname](/dotnet/api/System.ServiceProcess.ServiceController) object that is returned by the [Get-Service](/powershell/module/Microsoft.PowerShell.Management/Get-Service) cmdlet.</span></span> <span data-ttu-id="1ea34-108">Per altre informazioni sui componenti di una visualizzazione elenco, vedere [creazione di una visualizzazione elenco](./creating-a-list-view.md).</span><span class="sxs-lookup"><span data-stu-id="1ea34-108">For more information about the components of a list view, see [Creating a List View](./creating-a-list-view.md).</span></span>

### <a name="to-load-this-formatting-file"></a><span data-ttu-id="1ea34-109">Per caricare questo file di formattazione</span><span class="sxs-lookup"><span data-stu-id="1ea34-109">To load this formatting file</span></span>

1. <span data-ttu-id="1ea34-110">Copiare il codice XML della sezione di questo argomento in un file di testo.</span><span class="sxs-lookup"><span data-stu-id="1ea34-110">Copy the XML from the Example section of this topic into a text file.</span></span>

2. <span data-ttu-id="1ea34-111">Salvare il file di testo.</span><span class="sxs-lookup"><span data-stu-id="1ea34-111">Save the text file.</span></span> <span data-ttu-id="1ea34-112">Assicurarsi di aggiungere il `format.ps1xml` estensione del file per identificarla come un file di formattazione.</span><span class="sxs-lookup"><span data-stu-id="1ea34-112">Be sure to add the `format.ps1xml` extension to the file to identify it as a formatting file.</span></span>

3. <span data-ttu-id="1ea34-113">Aprire Windows PowerShell ed eseguire il comando seguente per caricare il file di formattazione nella sessione corrente: `Update-formatdata -prependpath PathToFormattingFile`.</span><span class="sxs-lookup"><span data-stu-id="1ea34-113">Open Windows PowerShell, and run the following command to load the formatting file into the current session: `Update-formatdata -prependpath PathToFormattingFile`.</span></span>

   > [!WARNING]
   > <span data-ttu-id="1ea34-114">Questo file di formattazione definita la visualizzazione di un oggetto che è già definita da un file di formattazione di Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="1ea34-114">This formatting file defines the display of an object that is already defined by a Windows PowerShell formatting file.</span></span> <span data-ttu-id="1ea34-115">È necessario usare il `prependPath` parametro quando si esegue il cmdlet, e non è possibile caricare questo tipo di formattazione del file come modulo.</span><span class="sxs-lookup"><span data-stu-id="1ea34-115">You must use the `prependPath` parameter when you run the cmdlet, and you cannot load this formatting file as a module.</span></span>

## <a name="demonstrates"></a><span data-ttu-id="1ea34-116">Illustra</span><span class="sxs-lookup"><span data-stu-id="1ea34-116">Demonstrates</span></span>

<span data-ttu-id="1ea34-117">Questo file di formattazione illustra gli elementi XML seguenti:</span><span class="sxs-lookup"><span data-stu-id="1ea34-117">This formatting file demonstrates the following XML elements:</span></span>

- <span data-ttu-id="1ea34-118">Il [nome](./name-element-for-view-format.md) (elemento) per la visualizzazione.</span><span class="sxs-lookup"><span data-stu-id="1ea34-118">The [Name](./name-element-for-view-format.md) element for the view.</span></span>

- <span data-ttu-id="1ea34-119">Il [ViewSelectedBy](./viewselectedby-element-format.md) elemento che definisce quali oggetti vengono visualizzati nella visualizzazione.</span><span class="sxs-lookup"><span data-stu-id="1ea34-119">The [ViewSelectedBy](./viewselectedby-element-format.md) element that defines what objects are displayed by the view.</span></span>

- <span data-ttu-id="1ea34-120">Il [dell'oggetto ListControl](./listcontrol-element-format.md) elemento che definisce quale proprietà viene visualizzata nella visualizzazione.</span><span class="sxs-lookup"><span data-stu-id="1ea34-120">The [ListControl](./listcontrol-element-format.md) element that defines what property is displayed by the view.</span></span>

- <span data-ttu-id="1ea34-121">Il [ListItem](./listitem-element-for-listitems-for-listcontrol-format.md) elemento che definisce ciò che viene visualizzato in una riga della visualizzazione elenco.</span><span class="sxs-lookup"><span data-stu-id="1ea34-121">The [ListItem](./listitem-element-for-listitems-for-listcontrol-format.md) element that defines what is displayed in a row of the list view.</span></span>

- <span data-ttu-id="1ea34-122">Il [etichetta](./label-element-for-listitem-for-listcontrol-format.md) elemento che definisce ciò che viene visualizzato in una riga della visualizzazione elenco.</span><span class="sxs-lookup"><span data-stu-id="1ea34-122">The [Label](./label-element-for-listitem-for-listcontrol-format.md) element that defines what is displayed in a row of the list view.</span></span>

- <span data-ttu-id="1ea34-123">Il [PropertyName](./propertyname-element-for-listitem-for-listcontrol-format.md) elemento che definisce la proprietà da visualizzare.</span><span class="sxs-lookup"><span data-stu-id="1ea34-123">The [PropertyName](./propertyname-element-for-listitem-for-listcontrol-format.md) element that defines which property is displayed.</span></span>

## <a name="example"></a><span data-ttu-id="1ea34-124">Esempio</span><span class="sxs-lookup"><span data-stu-id="1ea34-124">Example</span></span>

<span data-ttu-id="1ea34-125">Il codice XML seguente definisce una visualizzazione elenco che consente di visualizzare un'etichetta personalizzata in ogni riga.</span><span class="sxs-lookup"><span data-stu-id="1ea34-125">The following XML defines a list view that displays a custom label in each row.</span></span> <span data-ttu-id="1ea34-126">In questo caso, l'etichetta include il nome della proprietà con ogni lettera maiuscola e la parola "proprietà".</span><span class="sxs-lookup"><span data-stu-id="1ea34-126">In this case, the label includes the property name with each letter capitalized and the word "property".</span></span> <span data-ttu-id="1ea34-127">In ogni riga, il nome della proprietà viene visualizzato seguito dal valore della proprietà.</span><span class="sxs-lookup"><span data-stu-id="1ea34-127">In each row, the name of the property is displayed followed by the value of the property.</span></span>

```xml
<Configuration>
  <ViewDefinitions>
    <View>
  <Name>System.ServiceProcess.ServiceController</Name>
  <ViewSelectedBy>
    <TypeName>System.ServiceProcess.ServiceController</TypeName>
  </ViewSelectedBy>
  <ListControl>
    <ListEntries>
      <ListEntry>
        <ListItems>
          <ListItem>
            <Label>NAME property</Label>
            <PropertyName>Name</PropertyName>
          </ListItem>
          <ListItem>
            <Label>DISPLAYNAME property</Label>
            <PropertyName>DisplayName</PropertyName>
          </ListItem>
          <ListItem>
            <Label>STATUS property</Label>
            <PropertyName>Status</PropertyName>
          </ListItem>
          <ListItem>
            <Label>SERVICETYPE property</Label>
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

<span data-ttu-id="1ea34-128">Nell'esempio seguente viene illustrato come Windows PowerShell Visualizza il [System.Serviceprocess.Servicecontroller? Displayproperty = Fullname](/dotnet/api/System.ServiceProcess.ServiceController) oggetti dopo il caricamento di questo file di formato.</span><span class="sxs-lookup"><span data-stu-id="1ea34-128">The following example shows how Windows PowerShell displays the [System.Serviceprocess.Servicecontroller?Displayproperty=Fullname](/dotnet/api/System.ServiceProcess.ServiceController) objects after this format file is loaded.</span></span>

```powershell
Get-Service f*
```

```output
NAME property        : Fax
DISPLAYNAME property : Fax
STATUS property      : Stopped
SERVICETYPE property : Win32OwnProcess

NAME property        : FCSAM
DISPLAYNAME property : Microsoft Antimalware Service
STATUS property      : Running
SERVICETYPE property : Win32OwnProcess

NAME property        : fdPHost
DISPLAYNAME property : Function Discovery Provider Host
STATUS property      : Stopped
SERVICETYPE property : Win32ShareProcess

NAME property        : FDResPub
DISPLAYNAME property : Function Discovery Resource Publication
STATUS property      : Running
SERVICETYPE property : Win32ShareProcess

NAME property        : FontCache
DISPLAYNAME property : Windows Font Cache Service
STATUS property      : Running
SERVICETYPE property : Win32ShareProcess

NAME property        : FontCache3.0.0.0
DISPLAYNAME property : Windows Presentation Foundation Font Cache 3.0.0.0
STATUS property      : Stopped
SERVICETYPE property : Win32OwnProcess

NAME property        : FSysAgent
DISPLAYNAME property : Microsoft Forefront System Agent
STATUS property      : Running
SERVICETYPE property : Win32OwnProcess

NAME property        : FwcAgent
DISPLAYNAME property : Firewall Client Agent
STATUS property      : Running
SERVICETYPE property : Win32OwnProcess
```

## <a name="see-also"></a><span data-ttu-id="1ea34-129">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="1ea34-129">See Also</span></span>

[<span data-ttu-id="1ea34-130">Esempi di file di formattazione</span><span class="sxs-lookup"><span data-stu-id="1ea34-130">Examples of Formatting Files</span></span>](./examples-of-formatting-files.md)

[<span data-ttu-id="1ea34-131">La scrittura di un File di formattazione di PowerShell</span><span class="sxs-lookup"><span data-stu-id="1ea34-131">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
