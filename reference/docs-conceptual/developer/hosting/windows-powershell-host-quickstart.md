---
title: Guida introduttiva a Windows PowerShell Host | Microsoft Docs
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 5a134b81-bd0c-4e1c-a2f0-9acbe852745a
caps.latest.revision: 9
ms.openlocfilehash: 390eb2d0153c65967d8c0711c852aa6e13fe4660
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/05/2019
ms.locfileid: "72360820"
---
# <a name="windows-powershell-host-quickstart"></a><span data-ttu-id="fd0f4-102">Guida introduttiva dell'host di Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="fd0f4-102">Windows PowerShell Host Quickstart</span></span>

<span data-ttu-id="fd0f4-103">Per ospitare Windows PowerShell nell'applicazione, usare la classe [System. Management. Automation. PowerShell](/dotnet/api/System.Management.Automation.PowerShell) .</span><span class="sxs-lookup"><span data-stu-id="fd0f4-103">To host Windows PowerShell in your application, you use the [System.Management.Automation.PowerShell](/dotnet/api/System.Management.Automation.PowerShell) class.</span></span>
<span data-ttu-id="fd0f4-104">Questa classe fornisce metodi per la creazione di una pipeline di comandi, quindi l'esecuzione di tali comandi in un spazio.</span><span class="sxs-lookup"><span data-stu-id="fd0f4-104">This class provides methods that create a pipeline of commands and then execute those commands in a runspace.</span></span>
<span data-ttu-id="fd0f4-105">Il modo più semplice per creare un'applicazione host consiste nell'usare il valore predefinito spazio.</span><span class="sxs-lookup"><span data-stu-id="fd0f4-105">The simplest way to create a host application is to use the default runspace.</span></span>
<span data-ttu-id="fd0f4-106">Il valore predefinito di spazio contiene tutti i comandi di base di Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="fd0f4-106">The default runspace contains all of the core Windows PowerShell commands.</span></span>
<span data-ttu-id="fd0f4-107">Se si vuole che l'applicazione esponga solo un subset dei comandi di Windows PowerShell, è necessario creare un spazio personalizzato.</span><span class="sxs-lookup"><span data-stu-id="fd0f4-107">If you want your application to expose only a subset of the Windows PowerShell commands, you must create a custom runspace.</span></span>

## <a name="using-the-default-runspace"></a><span data-ttu-id="fd0f4-108">Uso del spazio predefinito</span><span class="sxs-lookup"><span data-stu-id="fd0f4-108">Using the default runspace</span></span>

<span data-ttu-id="fd0f4-109">Per iniziare, si userà il valore predefinito spazio e si useranno i metodi della classe [System. Management. Automation. PowerShell](/dotnet/api/System.Management.Automation.PowerShell) per aggiungere comandi, parametri, istruzioni e script a una pipeline.</span><span class="sxs-lookup"><span data-stu-id="fd0f4-109">To start, we'll use the default runspace, and use the methods of the [System.Management.Automation.PowerShell](/dotnet/api/System.Management.Automation.PowerShell) class to add commands, parameters, statements, and scripts to a pipeline.</span></span>

### <a name="addcommand"></a><span data-ttu-id="fd0f4-110">AddCommand</span><span class="sxs-lookup"><span data-stu-id="fd0f4-110">AddCommand</span></span>

<span data-ttu-id="fd0f4-111">Usare il metodo [System. Management. Automation. PowerShell. AddCommand](/dotnet/api/System.Management.Automation.PowerShell.AddCommand) per aggiungere comandi alla pipeline.</span><span class="sxs-lookup"><span data-stu-id="fd0f4-111">You use the [System.Management.Automation.Powershell.AddCommand](/dotnet/api/System.Management.Automation.PowerShell.AddCommand) method to add commands to the pipeline.</span></span>
<span data-ttu-id="fd0f4-112">Si supponga, ad esempio, di voler ottenere l'elenco dei processi in esecuzione nel computer.</span><span class="sxs-lookup"><span data-stu-id="fd0f4-112">For example, suppose you want to get the list of running processes on the machine.</span></span>
<span data-ttu-id="fd0f4-113">La modalità di esecuzione di questo comando è la seguente:</span><span class="sxs-lookup"><span data-stu-id="fd0f4-113">The way to run this command is as follows.</span></span>

1. <span data-ttu-id="fd0f4-114">Creare un oggetto [System. Management. Automation. PowerShell](/dotnet/api/System.Management.Automation.PowerShell) .</span><span class="sxs-lookup"><span data-stu-id="fd0f4-114">Create a [System.Management.Automation.PowerShell](/dotnet/api/System.Management.Automation.PowerShell) object.</span></span>

   ```csharp
   PowerShell ps = PowerShell.Create();
   ```

2. <span data-ttu-id="fd0f4-115">Aggiungere il comando che si desidera eseguire.</span><span class="sxs-lookup"><span data-stu-id="fd0f4-115">Add the command that you want to execute.</span></span>

   ```csharp
   ps.AddCommand("Get-Process");
   ```

3. <span data-ttu-id="fd0f4-116">Richiamare il comando.</span><span class="sxs-lookup"><span data-stu-id="fd0f4-116">Invoke the command.</span></span>

   ```csharp
   ps.Invoke();
   ```

<span data-ttu-id="fd0f4-117">Se si chiama il metodo AddCommand più di una volta prima di chiamare il metodo [System. Management. Automation. PowerShell. Invoke](/dotnet/api/System.Management.Automation.PowerShell.Invoke) , il risultato del primo comando viene reindirizzato al secondo e così via.</span><span class="sxs-lookup"><span data-stu-id="fd0f4-117">If you call the AddCommand method more than once before you call the [System.Management.Automation.Powershell.Invoke](/dotnet/api/System.Management.Automation.PowerShell.Invoke) method, the result of the first command is piped to the second, and so on.</span></span>
<span data-ttu-id="fd0f4-118">Se non si vuole inviare tramite pipe il risultato di un comando precedente a un comando, aggiungerlo chiamando [System. Management. Automation. PowerShell. AddStatement](/dotnet/api/System.Management.Automation.PowerShell.AddStatement) .</span><span class="sxs-lookup"><span data-stu-id="fd0f4-118">If you do not want to pipe the result of a previous command to a command, add it by calling the [System.Management.Automation.Powershell.AddStatement](/dotnet/api/System.Management.Automation.PowerShell.AddStatement) instead.</span></span>

### <a name="addparameter"></a><span data-ttu-id="fd0f4-119">AddParameter</span><span class="sxs-lookup"><span data-stu-id="fd0f4-119">AddParameter</span></span>

<span data-ttu-id="fd0f4-120">Nell'esempio precedente viene eseguito un unico comando senza parametri.</span><span class="sxs-lookup"><span data-stu-id="fd0f4-120">The previous example executes a single command without any parameters.</span></span>
<span data-ttu-id="fd0f4-121">È possibile aggiungere parametri al comando usando il metodo [System. Management. Automation. PSCommand. AddParameter](/dotnet/api/System.Management.Automation.PSCommand.AddParameter) .</span><span class="sxs-lookup"><span data-stu-id="fd0f4-121">You can add parameters to the command by using the [System.Management.Automation.PSCommand.AddParameter](/dotnet/api/System.Management.Automation.PSCommand.AddParameter) method.</span></span>
<span data-ttu-id="fd0f4-122">Il codice seguente, ad esempio, ottiene un elenco di tutti i processi denominati `PowerShell` in esecuzione nel computer.</span><span class="sxs-lookup"><span data-stu-id="fd0f4-122">For example, the following code gets a list of all of the processes that are named `PowerShell` running on the machine.</span></span>

```csharp
PowerShell.Create().AddCommand("Get-Process")
                   .AddParameter("Name", "PowerShell")
                   .Invoke();
```

<span data-ttu-id="fd0f4-123">È possibile aggiungere altri parametri chiamando ripetutamente il Metodo AddParameter.</span><span class="sxs-lookup"><span data-stu-id="fd0f4-123">You can add additional parameters by calling the AddParameter method repeatedly.</span></span>

```csharp                   
PowerShell.Create().AddCommand("Get-ChildItem")
                   .AddParameter("Path", @"c:\Windows")
                   .AddParameter("Filter", "*.exe")
                   .Invoke();
```

<span data-ttu-id="fd0f4-124">È anche possibile aggiungere un dizionario di nomi e valori di parametro chiamando il metodo [System. Management. Automation. PowerShell. AddParameters](/dotnet/api/System.Management.Automation.PowerShell.AddParameters) .</span><span class="sxs-lookup"><span data-stu-id="fd0f4-124">You can also add a dictionary of parameter names and values by calling the [System.Management.Automation.PowerShell.AddParameters](/dotnet/api/System.Management.Automation.PowerShell.AddParameters) method.</span></span>

```csharp
IDictionary parameters = new Dictionary<String, String>();
parameters.Add("Path", @"c:\Windows");
parameters.Add("Filter", "*.exe");

PowerShell.Create().AddCommand("Get-Process")
   .AddParameters(parameters)
      .Invoke()

```

### <a name="addstatement"></a><span data-ttu-id="fd0f4-125">AddStatement</span><span class="sxs-lookup"><span data-stu-id="fd0f4-125">AddStatement</span></span>

<span data-ttu-id="fd0f4-126">È possibile simulare la suddivisione in batch usando il metodo [System. Management. Automation. PowerShell. AddStatement](/dotnet/api/System.Management.Automation.PowerShell.AddStatement) , che aggiunge un'altra istruzione alla fine della pipeline.</span><span class="sxs-lookup"><span data-stu-id="fd0f4-126">You can simulate batching by using the [System.Management.Automation.PowerShell.AddStatement](/dotnet/api/System.Management.Automation.PowerShell.AddStatement) method, which adds an additional statement to the end of the pipeline.</span></span>
<span data-ttu-id="fd0f4-127">Il codice seguente ottiene un elenco di processi in esecuzione con il nome `PowerShell`e quindi ottiene l'elenco dei servizi in esecuzione.</span><span class="sxs-lookup"><span data-stu-id="fd0f4-127">The following code gets a list of running processes with the name `PowerShell`, and then gets the list of running services.</span></span>

```csharp
PowerShell ps = PowerShell.Create();
ps.AddCommand("Get-Process").AddParameter("Name", "PowerShell");
ps.AddStatement().AddCommand("Get-Service");
ps.Invoke();
```

### <a name="addscript"></a><span data-ttu-id="fd0f4-128">AddScript</span><span class="sxs-lookup"><span data-stu-id="fd0f4-128">AddScript</span></span>

<span data-ttu-id="fd0f4-129">È possibile eseguire uno script esistente chiamando il metodo [System. Management. Automation. PowerShell. AddScript](/dotnet/api/System.Management.Automation.PowerShell.AddScript) .</span><span class="sxs-lookup"><span data-stu-id="fd0f4-129">You can run an existing script by calling the [System.Management.Automation.PowerShell.AddScript](/dotnet/api/System.Management.Automation.PowerShell.AddScript) method.</span></span>
<span data-ttu-id="fd0f4-130">Nell'esempio seguente viene aggiunto uno script alla pipeline ed eseguito.</span><span class="sxs-lookup"><span data-stu-id="fd0f4-130">The following example adds a script to the pipeline and runs it.</span></span>
<span data-ttu-id="fd0f4-131">In questo esempio si presuppone che esista già uno script denominato `MyScript.ps1` in una cartella denominata `D:\PSScripts`.</span><span class="sxs-lookup"><span data-stu-id="fd0f4-131">This example assumes there is already a script named `MyScript.ps1` in a folder named `D:\PSScripts`.</span></span>

```csharp
PowerShell ps = PowerShell.Create();
ps.AddScript("D:\PSScripts\MyScript.ps1").Invoke();
```

<span data-ttu-id="fd0f4-132">Esiste anche una versione del metodo AddScript che accetta un parametro booleano denominato `useLocalScope`.</span><span class="sxs-lookup"><span data-stu-id="fd0f4-132">There is also a version of the AddScript method that takes a boolean parameter named `useLocalScope`.</span></span>
<span data-ttu-id="fd0f4-133">Se questo parametro è impostato su `true`, lo script viene eseguito nell'ambito locale.</span><span class="sxs-lookup"><span data-stu-id="fd0f4-133">If this parameter is set to `true`, then the script is run in the local scope.</span></span>
<span data-ttu-id="fd0f4-134">Nel codice seguente viene eseguito lo script nell'ambito locale.</span><span class="sxs-lookup"><span data-stu-id="fd0f4-134">The following code will run the script in the local scope.</span></span>

```csharp
PowerShell ps = PowerShell.Create();
ps.AddScript(@"D:\PSScripts\MyScript.ps1", true).Invoke();
```

## <a name="creating-a-custom-runspace"></a><span data-ttu-id="fd0f4-135">Creazione di un spazio personalizzato</span><span class="sxs-lookup"><span data-stu-id="fd0f4-135">Creating a custom runspace</span></span>

<span data-ttu-id="fd0f4-136">Mentre il spazio predefinito usato negli esempi precedenti carica tutti i comandi di Windows PowerShell di base, è possibile creare un spazio personalizzato che carica solo un subset specificato di tutti i comandi.</span><span class="sxs-lookup"><span data-stu-id="fd0f4-136">While the default runspace used in the previous examples loads all of the core Windows PowerShell commands, you can create a custom runspace that loads only a specified subset of all commands.</span></span>
<span data-ttu-id="fd0f4-137">Questa operazione può essere utile per migliorare le prestazioni (il caricamento di un numero maggiore di comandi è un riscontro delle prestazioni) o per limitare la capacità dell'utente di eseguire operazioni.</span><span class="sxs-lookup"><span data-stu-id="fd0f4-137">You might want to do this to improve performance (loading a larger number of commands is a performance hit), or to restrict the capability of the user to perform operations.</span></span>
<span data-ttu-id="fd0f4-138">Un spazio che espone solo un numero limitato di comandi è denominato spazio vincolato.</span><span class="sxs-lookup"><span data-stu-id="fd0f4-138">A runspace that exposes only a limited number of commands is called a constrained runspace.</span></span>
<span data-ttu-id="fd0f4-139">Per creare un spazio vincolato, usare le classi [System. Management. Automation. Runspaces. spazio](/dotnet/api/System.Management.Automation.Runspaces.Runspace) e [System. Management. Automation. Runspaces. InitialSessionState](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) .</span><span class="sxs-lookup"><span data-stu-id="fd0f4-139">To create a constrained runspace, you use the [System.Management.Automation.Runspaces.Runspace](/dotnet/api/System.Management.Automation.Runspaces.Runspace) and [System.Management.Automation.Runspaces.InitialSessionState](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) classes.</span></span>

### <a name="creating-an-initialsessionstate-object"></a><span data-ttu-id="fd0f4-140">Creazione di un oggetto InitialSessionState</span><span class="sxs-lookup"><span data-stu-id="fd0f4-140">Creating an InitialSessionState object</span></span>

<span data-ttu-id="fd0f4-141">Per creare un spazio personalizzato, è prima necessario creare un oggetto [System. Management. Automation. Runspaces. InitialSessionState](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) .</span><span class="sxs-lookup"><span data-stu-id="fd0f4-141">To create a custom runspace, you must first create an [System.Management.Automation.Runspaces.InitialSessionState](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) object.</span></span>
<span data-ttu-id="fd0f4-142">Nell'esempio seguente viene usato [System. Management. Automation. Runspaces. RunspaceFactory](/dotnet/api/System.Management.Automation.Runspaces.RunspaceFactory) per creare un spazio dopo la creazione di un oggetto InitialSessionState predefinito.</span><span class="sxs-lookup"><span data-stu-id="fd0f4-142">In the following example, we use the [System.Management.Automation.Runspaces.RunspaceFactory](/dotnet/api/System.Management.Automation.Runspaces.RunspaceFactory) to create a runspace after creating a default InitialSessionState object.</span></span>

```csharp
InitialSessionState iss = InitialSessionState.CreateDefault();
Runspace rs = RunspaceFactory.CreateRunspace(iss);
rs.Open();
PowerShell ps = PowerShell.Create();
ps.Runspace = rs;
ps.AddCommand("Get-Command");
ps.Invoke();
```

### <a name="constraining-the-runspace"></a><span data-ttu-id="fd0f4-143">Limitazione del spazio</span><span class="sxs-lookup"><span data-stu-id="fd0f4-143">Constraining the runspace</span></span>

<span data-ttu-id="fd0f4-144">Nell'esempio precedente è stato creato un oggetto [System. Management. Automation. Runspaces. InitialSessionState](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) predefinito che carica tutte le funzionalità di base di Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="fd0f4-144">In the previous example, we created a default [System.Management.Automation.Runspaces.InitialSessionState](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) object that loads all of the built-in core Windows PowerShell.</span></span>
<span data-ttu-id="fd0f4-145">Avremmo anche chiamato il metodo [System. Management. Automation. Runspaces. InitialSessionState. CreateDefault2](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState.CreateDefault2) per creare un oggetto InitialSessionState che caricherà solo i comandi nello snap-in Microsoft. PowerShell. Core.</span><span class="sxs-lookup"><span data-stu-id="fd0f4-145">We could also have called the [System.Management.Automation.Runspaces.InitialSessionState.CreateDefault2](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState.CreateDefault2) method to create an InitialSessionState object that would load only the commands in the Microsoft.PowerShell.Core snapin.</span></span>
<span data-ttu-id="fd0f4-146">Per creare un spazio più vincolato, è necessario creare un oggetto InitialSessionState vuoto chiamando il metodo [System. Management. Automation. Runspaces. InitialSessionState. Create](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState.Create) , quindi aggiungere i comandi a InitialSessionState.</span><span class="sxs-lookup"><span data-stu-id="fd0f4-146">To create a more constrained runspace, you must create an empty InitialSessionState object by calling the [System.Management.Automation.Runspaces.InitialSessionState.Create](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState.Create) method, and then add commands to the InitialSessionState.</span></span>

<span data-ttu-id="fd0f4-147">L'uso di un spazio che carica solo i comandi specificati fornisce prestazioni significativamente migliorate.</span><span class="sxs-lookup"><span data-stu-id="fd0f4-147">Using a runspace that loads only the commands that you specify provides significantly improved performance.</span></span>

<span data-ttu-id="fd0f4-148">Usare i metodi della classe [System. Management. Automation. Runspaces. SessionStateCmdletEntry](/dotnet/api/System.Management.Automation.Runspaces.SessionStateCmdletEntry) per definire i cmdlet per lo stato della sessione iniziale.</span><span class="sxs-lookup"><span data-stu-id="fd0f4-148">You use the methods of the [System.Management.Automation.Runspaces.SessionStateCmdletEntry](/dotnet/api/System.Management.Automation.Runspaces.SessionStateCmdletEntry) class to define cmdlets for the initial session state.</span></span>
<span data-ttu-id="fd0f4-149">Nell'esempio seguente viene creato uno stato sessione iniziale vuoto, quindi vengono definiti e aggiunti i comandi `Get-Command` e `Import-Module` allo stato sessione iniziale.</span><span class="sxs-lookup"><span data-stu-id="fd0f4-149">The following example creates an empty initial session state, then defines and adds the `Get-Command` and `Import-Module` commands to the initial session state.</span></span>
<span data-ttu-id="fd0f4-150">Viene quindi creato un spazio vincolato da tale stato della sessione iniziale ed eseguito i comandi in tale spazio.</span><span class="sxs-lookup"><span data-stu-id="fd0f4-150">We then create a runspace constrained by that initial session state, and execute the commands in that runspace.</span></span>

<span data-ttu-id="fd0f4-151">Creare lo stato della sessione iniziale.</span><span class="sxs-lookup"><span data-stu-id="fd0f4-151">Create the initial session state.</span></span>

```csharp
InitialSessionState iss = InitialSessionState.Create();
```

<span data-ttu-id="fd0f4-152">Definire e aggiungere comandi allo stato della sessione iniziale.</span><span class="sxs-lookup"><span data-stu-id="fd0f4-152">Define and add commands to the initial session state.</span></span>

```csharp
SessionStateCmdletEntry getCommand = new SessionStateCmdletEntry(
        "Get-Command", typeof(Microsoft.PowerShell.Commands.GetCommandCommand), "");
SessionStateCmdletEntry importModule = new SessionStateCmdletEntry(
        "Import-Module", typeof(Microsoft.PowerShell.Commands.ImportModuleCommand), "");
iss.Commands.Add(getCommand);
iss.Commands.Add(importModule);
```

<span data-ttu-id="fd0f4-153">Creare e aprire spazio.</span><span class="sxs-lookup"><span data-stu-id="fd0f4-153">Create and open the runspace.</span></span>

```csharp
Runspace rs = RunspaceFactory.CreateRunspace(iss);
rs.Open();
```

<span data-ttu-id="fd0f4-154">Eseguire un comando e visualizzare il risultato.</span><span class="sxs-lookup"><span data-stu-id="fd0f4-154">Execute a command and show the result.</span></span>

```csharp
PowerShell ps = PowerShell.Create();
ps.Runspace = rs;
ps.AddCommand("Get-Command");
Collection<CommandInfo> result = ps.Invoke<CommandInfo>();
foreach (var entry in result)
{
       Console.WriteLine(entry.Name);
}
```

<span data-ttu-id="fd0f4-155">Quando viene eseguito, l'output di questo codice sarà simile al seguente.</span><span class="sxs-lookup"><span data-stu-id="fd0f4-155">When run, the output of this code will look as follows.</span></span>

```powershell
Get-Command
Import-Module
```
