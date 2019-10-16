---
title: Visualizzazione elenco (etichette) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 53442bb1-74a3-49f9-9150-3bc3081a7565
caps.latest.revision: 6
ms.openlocfilehash: 27de41c88e224f7610c10a764e51524016ecc8cb
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/15/2019
ms.locfileid: "72362790"
---
# <a name="list-view-labels"></a><span data-ttu-id="dbeee-102">Visualizzazione elenco (etichette)</span><span class="sxs-lookup"><span data-stu-id="dbeee-102">List View (Labels)</span></span>

<span data-ttu-id="dbeee-103">In questo esempio viene illustrato come implementare una visualizzazione elenco che visualizza un'etichetta personalizzata per ogni riga dell'elenco.</span><span class="sxs-lookup"><span data-stu-id="dbeee-103">This example shows how to implement a list view that displays a custom label for each row of the list.</span></span> <span data-ttu-id="dbeee-104">In questa visualizzazione elenco sono elencate le proprietà di [System. ServiceProcess. ServiceController? DisplayProperty = oggetto FullName](/dotnet/api/System.ServiceProcess.ServiceController) restituito dal cmdlet [Get-Service](/powershell/module/Microsoft.PowerShell.Management/Get-Service) .</span><span class="sxs-lookup"><span data-stu-id="dbeee-104">This list view displays the properties of the [System.Serviceprocess.Servicecontroller?Displayproperty=Fullname](/dotnet/api/System.ServiceProcess.ServiceController) object that is returned by the [Get-Service](/powershell/module/Microsoft.PowerShell.Management/Get-Service) cmdlet.</span></span> <span data-ttu-id="dbeee-105">Per ulteriori informazioni sui componenti di una visualizzazione elenco, vedere [creazione di una visualizzazione elenco](./creating-a-list-view.md).</span><span class="sxs-lookup"><span data-stu-id="dbeee-105">For more information about the components of a list view, see [Creating a List View](./creating-a-list-view.md).</span></span>

### <a name="to-load-this-formatting-file"></a><span data-ttu-id="dbeee-106">Per caricare il file di formattazione</span><span class="sxs-lookup"><span data-stu-id="dbeee-106">To load this formatting file</span></span>

1. <span data-ttu-id="dbeee-107">Copiare il codice XML dalla sezione esempio di questo argomento in un file di testo.</span><span class="sxs-lookup"><span data-stu-id="dbeee-107">Copy the XML from the Example section of this topic into a text file.</span></span>

2. <span data-ttu-id="dbeee-108">Salvare il file di testo.</span><span class="sxs-lookup"><span data-stu-id="dbeee-108">Save the text file.</span></span> <span data-ttu-id="dbeee-109">Assicurarsi di aggiungere l'estensione `format.ps1xml` al file per identificarla come un file di formattazione.</span><span class="sxs-lookup"><span data-stu-id="dbeee-109">Be sure to add the `format.ps1xml` extension to the file to identify it as a formatting file.</span></span>

3. <span data-ttu-id="dbeee-110">Aprire Windows PowerShell ed eseguire il comando seguente per caricare il file di formattazione nella sessione corrente: `Update-formatdata -prependpath PathToFormattingFile`.</span><span class="sxs-lookup"><span data-stu-id="dbeee-110">Open Windows PowerShell, and run the following command to load the formatting file into the current session: `Update-formatdata -prependpath PathToFormattingFile`.</span></span>

   > [!WARNING]
   > <span data-ttu-id="dbeee-111">Questo file di formattazione definisce la visualizzazione di un oggetto già definito da un file di formattazione di Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="dbeee-111">This formatting file defines the display of an object that is already defined by a Windows PowerShell formatting file.</span></span> <span data-ttu-id="dbeee-112">Quando si esegue il cmdlet, è necessario utilizzare il parametro `prependPath` e non è possibile caricare il file di formattazione come modulo.</span><span class="sxs-lookup"><span data-stu-id="dbeee-112">You must use the `prependPath` parameter when you run the cmdlet, and you cannot load this formatting file as a module.</span></span>

## <a name="demonstrates"></a><span data-ttu-id="dbeee-113">Dimostra</span><span class="sxs-lookup"><span data-stu-id="dbeee-113">Demonstrates</span></span>

<span data-ttu-id="dbeee-114">In questo file di formattazione vengono illustrati gli elementi XML seguenti:</span><span class="sxs-lookup"><span data-stu-id="dbeee-114">This formatting file demonstrates the following XML elements:</span></span>

- <span data-ttu-id="dbeee-115">Elemento del [nome](./name-element-for-view-format.md) per la visualizzazione.</span><span class="sxs-lookup"><span data-stu-id="dbeee-115">The [Name](./name-element-for-view-format.md) element for the view.</span></span>

- <span data-ttu-id="dbeee-116">Elemento [ViewSelectedBy](./viewselectedby-element-format.md) che definisce quali oggetti vengono visualizzati dalla visualizzazione.</span><span class="sxs-lookup"><span data-stu-id="dbeee-116">The [ViewSelectedBy](./viewselectedby-element-format.md) element that defines what objects are displayed by the view.</span></span>

- <span data-ttu-id="dbeee-117">Elemento [ListControl](./listcontrol-element-format.md) che definisce la proprietà visualizzata dalla visualizzazione.</span><span class="sxs-lookup"><span data-stu-id="dbeee-117">The [ListControl](./listcontrol-element-format.md) element that defines what property is displayed by the view.</span></span>

- <span data-ttu-id="dbeee-118">Elemento [ListItem](./listitem-element-for-listitems-for-listcontrol-format.md) che definisce ciò che viene visualizzato in una riga della visualizzazione elenco.</span><span class="sxs-lookup"><span data-stu-id="dbeee-118">The [ListItem](./listitem-element-for-listitems-for-listcontrol-format.md) element that defines what is displayed in a row of the list view.</span></span>

- <span data-ttu-id="dbeee-119">Elemento [Label](./label-element-for-listitem-for-listcontrol-format.md) che definisce ciò che viene visualizzato in una riga della visualizzazione elenco.</span><span class="sxs-lookup"><span data-stu-id="dbeee-119">The [Label](./label-element-for-listitem-for-listcontrol-format.md) element that defines what is displayed in a row of the list view.</span></span>

- <span data-ttu-id="dbeee-120">Elemento [PropertyName](./propertyname-element-for-listitem-for-listcontrol-format.md) che definisce la proprietà che viene visualizzata.</span><span class="sxs-lookup"><span data-stu-id="dbeee-120">The [PropertyName](./propertyname-element-for-listitem-for-listcontrol-format.md) element that defines which property is displayed.</span></span>

## <a name="example"></a><span data-ttu-id="dbeee-121">Esempio</span><span class="sxs-lookup"><span data-stu-id="dbeee-121">Example</span></span>

<span data-ttu-id="dbeee-122">Il codice XML seguente definisce una visualizzazione elenco che consente di visualizzare un'etichetta personalizzata in ogni riga.</span><span class="sxs-lookup"><span data-stu-id="dbeee-122">The following XML defines a list view that displays a custom label in each row.</span></span> <span data-ttu-id="dbeee-123">In questo caso, l'etichetta include il nome della proprietà con ogni lettera maiuscola e la parola "Property".</span><span class="sxs-lookup"><span data-stu-id="dbeee-123">In this case, the label includes the property name with each letter capitalized and the word "property".</span></span> <span data-ttu-id="dbeee-124">In ogni riga il nome della proprietà viene visualizzato seguito dal valore della proprietà.</span><span class="sxs-lookup"><span data-stu-id="dbeee-124">In each row, the name of the property is displayed followed by the value of the property.</span></span>

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

<span data-ttu-id="dbeee-125">Nell'esempio seguente viene illustrato come Windows PowerShell visualizzi [System. ServiceProcess. ServiceController? DisplayProperty = oggetti FullName](/dotnet/api/System.ServiceProcess.ServiceController) dopo il caricamento del file di formato.</span><span class="sxs-lookup"><span data-stu-id="dbeee-125">The following example shows how Windows PowerShell displays the [System.Serviceprocess.Servicecontroller?Displayproperty=Fullname](/dotnet/api/System.ServiceProcess.ServiceController) objects after this format file is loaded.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="dbeee-126">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="dbeee-126">See Also</span></span>

[<span data-ttu-id="dbeee-127">Esempi di file di formattazione</span><span class="sxs-lookup"><span data-stu-id="dbeee-127">Examples of Formatting Files</span></span>](./examples-of-formatting-files.md)

[<span data-ttu-id="dbeee-128">Scrittura di un file di formattazione di PowerShell</span><span class="sxs-lookup"><span data-stu-id="dbeee-128">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
