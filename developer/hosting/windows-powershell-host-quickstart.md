---
title: Guida introduttiva di Windows PowerShell Host | Microsoft Docs
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 5a134b81-bd0c-4e1c-a2f0-9acbe852745a
caps.latest.revision: 9
ms.openlocfilehash: 9a080b6db7416ae6bf65a1b0353e9f17a56cc6c5
ms.sourcegitcommit: 00cf9a99972ce40db7c25b9a3fc6152dec6bddb6
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/28/2019
ms.locfileid: "64530614"
---
# <a name="windows-powershell-host-quickstart"></a><span data-ttu-id="8a2ed-102">Guida introduttiva dell'host di Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="8a2ed-102">Windows PowerShell Host Quickstart</span></span>

<span data-ttu-id="8a2ed-103">Per ospitare Windows PowerShell nell'applicazione, si utilizza il [System.Management.Automation.PowerShell](/dotnet/api/System.Management.Automation.PowerShell) classe.</span><span class="sxs-lookup"><span data-stu-id="8a2ed-103">To host Windows PowerShell in your application, you use the [System.Management.Automation.PowerShell](/dotnet/api/System.Management.Automation.PowerShell) class.</span></span>
<span data-ttu-id="8a2ed-104">Questa classe fornisce metodi che creano una pipeline di comandi e quindi eseguire questi comandi in uno spazio di esecuzione.</span><span class="sxs-lookup"><span data-stu-id="8a2ed-104">This class provides methods that create a pipeline of commands and then execute those commands in a runspace.</span></span>
<span data-ttu-id="8a2ed-105">Il modo più semplice per creare un'applicazione host è usare lo spazio di esecuzione predefinito.</span><span class="sxs-lookup"><span data-stu-id="8a2ed-105">The simplest way to create a host application is to use the default runspace.</span></span>
<span data-ttu-id="8a2ed-106">Lo spazio di esecuzione predefinito contiene tutti i comandi di Windows PowerShell core.</span><span class="sxs-lookup"><span data-stu-id="8a2ed-106">The default runspace contains all of the core Windows PowerShell commands.</span></span>
<span data-ttu-id="8a2ed-107">Se si desidera che l'applicazione da esporre solo un subset dei comandi di Windows PowerShell, è necessario creare uno spazio di esecuzione personalizzata.</span><span class="sxs-lookup"><span data-stu-id="8a2ed-107">If you want your application to expose only a subset of the Windows PowerShell commands, you must create a custom runspace.</span></span>

## <a name="using-the-default-runspace"></a><span data-ttu-id="8a2ed-108">Utilizzo spazio di esecuzione predefinito</span><span class="sxs-lookup"><span data-stu-id="8a2ed-108">Using the default runspace</span></span>

<span data-ttu-id="8a2ed-109">Per iniziare, si sarà usare lo spazio di esecuzione predefinito e usare i metodi del [System.Management.Automation.PowerShell](/dotnet/api/System.Management.Automation.PowerShell) classe da aggiungere a una pipeline di comandi, parametri, istruzioni e script.</span><span class="sxs-lookup"><span data-stu-id="8a2ed-109">To start, we'll use the default runspace, and use the methods of the [System.Management.Automation.PowerShell](/dotnet/api/System.Management.Automation.PowerShell) class to add commands, parameters, statements, and scripts to a pipeline.</span></span>

### <a name="addcommand"></a><span data-ttu-id="8a2ed-110">AddCommand</span><span class="sxs-lookup"><span data-stu-id="8a2ed-110">AddCommand</span></span>

<span data-ttu-id="8a2ed-111">Si utilizza il [System.Management.Automation.Powershell.AddCommand](/dotnet/api/System.Management.Automation.PowerShell.AddCommand) metodo per aggiungere comandi alla pipeline.</span><span class="sxs-lookup"><span data-stu-id="8a2ed-111">You use the [System.Management.Automation.Powershell.AddCommand](/dotnet/api/System.Management.Automation.PowerShell.AddCommand) method to add commands to the pipeline.</span></span>
<span data-ttu-id="8a2ed-112">Si supponga, ad esempio ottenere l'elenco dei processi in esecuzione nel computer.</span><span class="sxs-lookup"><span data-stu-id="8a2ed-112">For example, suppose you want to get the list of running processes on the machine.</span></span>
<span data-ttu-id="8a2ed-113">Il modo per eseguire questo comando è come indicato di seguito.</span><span class="sxs-lookup"><span data-stu-id="8a2ed-113">The way to run this command is as follows.</span></span>

1. <span data-ttu-id="8a2ed-114">Creare un [System.Management.Automation.PowerShell](/dotnet/api/System.Management.Automation.PowerShell) oggetto.</span><span class="sxs-lookup"><span data-stu-id="8a2ed-114">Create a [System.Management.Automation.PowerShell](/dotnet/api/System.Management.Automation.PowerShell) object.</span></span>

   ```csharp
   PowerShell ps = PowerShell.Create();
   ```

2. <span data-ttu-id="8a2ed-115">Aggiungere il comando che si desidera eseguire.</span><span class="sxs-lookup"><span data-stu-id="8a2ed-115">Add the command that you want to execute.</span></span>

   ```csharp
   ps.AddCommand("Get-Process");
   ```

3. <span data-ttu-id="8a2ed-116">Richiamare il comando.</span><span class="sxs-lookup"><span data-stu-id="8a2ed-116">Invoke the command.</span></span>

   ```csharp
   ps.Invoke();
   ```

<span data-ttu-id="8a2ed-117">Se si chiama il metodo AddCommand più volte prima di chiamare il [System.Management.Automation.Powershell.Invoke](/dotnet/api/System.Management.Automation.PowerShell.Invoke) metodo, il risultato del primo comando viene reindirizzato al secondo e così via.</span><span class="sxs-lookup"><span data-stu-id="8a2ed-117">If you call the AddCommand method more than once before you call the [System.Management.Automation.Powershell.Invoke](/dotnet/api/System.Management.Automation.PowerShell.Invoke) method, the result of the first command is piped to the second, and so on.</span></span>
<span data-ttu-id="8a2ed-118">Se non si desidera inviare tramite pipe il risultato di un comando precedente a un comando, aggiungerlo chiamando il [System.Management.Automation.Powershell.AddStatement](/dotnet/api/System.Management.Automation.PowerShell.AddStatement) invece.</span><span class="sxs-lookup"><span data-stu-id="8a2ed-118">If you do not want to pipe the result of a previous command to a command, add it by calling the [System.Management.Automation.Powershell.AddStatement](/dotnet/api/System.Management.Automation.PowerShell.AddStatement) instead.</span></span>

### <a name="addparameter"></a><span data-ttu-id="8a2ed-119">AddParameter</span><span class="sxs-lookup"><span data-stu-id="8a2ed-119">AddParameter</span></span>

<span data-ttu-id="8a2ed-120">Nell'esempio precedente esegue un comando singolo senza parametri.</span><span class="sxs-lookup"><span data-stu-id="8a2ed-120">The previous example executes a single command without any parameters.</span></span>
<span data-ttu-id="8a2ed-121">È possibile aggiungere parametri al comando utilizzando il [System.Management.Automation.PSCommand.AddParameter](/dotnet/api/System.Management.Automation.PSCommand.AddParameter) (metodo).</span><span class="sxs-lookup"><span data-stu-id="8a2ed-121">You can add parameters to the command by using the [System.Management.Automation.PSCommand.AddParameter](/dotnet/api/System.Management.Automation.PSCommand.AddParameter) method.</span></span>
<span data-ttu-id="8a2ed-122">Ad esempio, il codice seguente ottiene un elenco di tutti i processi denominati `PowerShell` in esecuzione nel computer.</span><span class="sxs-lookup"><span data-stu-id="8a2ed-122">For example, the following code gets a list of all of the processes that are named `PowerShell` running on the machine.</span></span>

```csharp
PowerShell.Create().AddCommand("Get-Process")
                   .AddParameter("Name", "PowerShell")
                   .Invoke();
```

<span data-ttu-id="8a2ed-123">È possibile aggiungere parametri aggiuntivi chiamando il metodo AddParameter ripetutamente.</span><span class="sxs-lookup"><span data-stu-id="8a2ed-123">You can add additional parameters by calling the AddParameter method repeatedly.</span></span>

```csharp
PowerShell.Create().AddCommand("Get-Process")
                   .AddParameter("Name", "PowerShell")
                   .AddParameter("Id", "12768")
                   .Invoke();
```

<span data-ttu-id="8a2ed-124">È anche possibile aggiungere un dizionario di nomi dei parametri e valori chiamando il [System.Management.Automation.PowerShell.AddParameters](/dotnet/api/System.Management.Automation.PowerShell.AddParameters) (metodo).</span><span class="sxs-lookup"><span data-stu-id="8a2ed-124">You can also add a dictionary of parameter names and values by calling the [System.Management.Automation.PowerShell.AddParameters](/dotnet/api/System.Management.Automation.PowerShell.AddParameters) method.</span></span>

```csharp
IDictionary parameters = new Dictionary<String, String>();
parameters.Add("Name", "PowerShell");

parameters.Add("Id", "12768");
PowerShell.Create().AddCommand("Get-Process")
   .AddParameters(parameters)
      .Invoke()

```

### <a name="addstatement"></a><span data-ttu-id="8a2ed-125">AddStatement</span><span class="sxs-lookup"><span data-stu-id="8a2ed-125">AddStatement</span></span>

<span data-ttu-id="8a2ed-126">È possibile simulare l'invio in batch usando il [System.Management.Automation.PowerShell.AddStatement](/dotnet/api/System.Management.Automation.PowerShell.AddStatement) metodo, che aggiunge un'ulteriore istruzione alla fine della pipeline.</span><span class="sxs-lookup"><span data-stu-id="8a2ed-126">You can simulate batching by using the [System.Management.Automation.PowerShell.AddStatement](/dotnet/api/System.Management.Automation.PowerShell.AddStatement) method, which adds an additional statement to the end of the pipeline.</span></span>
<span data-ttu-id="8a2ed-127">Il codice seguente ottiene un elenco di processi in esecuzione con il nome `PowerShell`e quindi Ottiene l'elenco dei servizi in esecuzione.</span><span class="sxs-lookup"><span data-stu-id="8a2ed-127">The following code gets a list of running processes with the name `PowerShell`, and then gets the list of running services.</span></span>

```csharp
PowerShell ps = PowerShell.Create();
ps.AddCommand("Get-Process").AddParameter("Name", "PowerShell");
ps.AddStatement().AddCommand("Get-Service");
ps.Invoke();
```

### <a name="addscript"></a><span data-ttu-id="8a2ed-128">AddScript</span><span class="sxs-lookup"><span data-stu-id="8a2ed-128">AddScript</span></span>

<span data-ttu-id="8a2ed-129">È possibile eseguire uno script esistente chiamando il [System.Management.Automation.PowerShell.AddScript](/dotnet/api/System.Management.Automation.PowerShell.AddScript) (metodo).</span><span class="sxs-lookup"><span data-stu-id="8a2ed-129">You can run an existing script by calling the [System.Management.Automation.PowerShell.AddScript](/dotnet/api/System.Management.Automation.PowerShell.AddScript) method.</span></span>
<span data-ttu-id="8a2ed-130">Nell'esempio seguente aggiunge uno script alla pipeline e lo esegue.</span><span class="sxs-lookup"><span data-stu-id="8a2ed-130">The following example adds a script to the pipeline and runs it.</span></span>
<span data-ttu-id="8a2ed-131">In questo esempio si presuppone che è già presente uno script denominato `MyScript.ps1` in una cartella denominata `D:\PSScripts`.</span><span class="sxs-lookup"><span data-stu-id="8a2ed-131">This example assumes there is already a script named `MyScript.ps1` in a folder named `D:\PSScripts`.</span></span>

```csharp
PowerShell ps = PowerShell.Create();
ps.AddScript("D:\PSScripts\MyScript.ps1").Invoke();
```

<span data-ttu-id="8a2ed-132">È inoltre disponibile una versione del metodo che accetta un parametro booleano denominato AddScript `useLocalScope`.</span><span class="sxs-lookup"><span data-stu-id="8a2ed-132">There is also a version of the AddScript method that takes a boolean parameter named `useLocalScope`.</span></span>
<span data-ttu-id="8a2ed-133">Se questo parametro è impostato su `true`, quindi lo script viene eseguito nell'ambito locale.</span><span class="sxs-lookup"><span data-stu-id="8a2ed-133">If this parameter is set to `true`, then the script is run in the local scope.</span></span>
<span data-ttu-id="8a2ed-134">Il codice seguente verrà eseguito lo script nell'ambito locale.</span><span class="sxs-lookup"><span data-stu-id="8a2ed-134">The following code will run the script in the local scope.</span></span>

```csharp
PowerShell ps = PowerShell.Create();
ps.AddScript(@"D:\PSScripts\MyScript.ps1", true).Invoke();
```

## <a name="creating-a-custom-runspace"></a><span data-ttu-id="8a2ed-135">Creazione di uno spazio di esecuzione personalizzata</span><span class="sxs-lookup"><span data-stu-id="8a2ed-135">Creating a custom runspace</span></span>

<span data-ttu-id="8a2ed-136">Mentre lo spazio di esecuzione predefinito usato negli esempi precedenti carica tutti i comandi di Windows PowerShell core, è possibile creare uno spazio di esecuzione personalizzata che consente di caricare solo un subset specificato di tutti i comandi.</span><span class="sxs-lookup"><span data-stu-id="8a2ed-136">While the default runspace used in the previous examples loads all of the core Windows PowerShell commands, you can create a custom runspace that loads only a specified subset of all commands.</span></span>
<span data-ttu-id="8a2ed-137">Si potrebbe voler eseguire questa operazione per migliorare le prestazioni, il caricamento di un numero maggiore di comandi è una riduzione delle prestazioni, o limitare la capacità dell'utente per eseguire operazioni.</span><span class="sxs-lookup"><span data-stu-id="8a2ed-137">You might want to do this to improve performance (loading a larger number of commands is a performance hit), or to restrict the capability of the user to perform operations.</span></span>
<span data-ttu-id="8a2ed-138">Uno spazio di esecuzione che espone solo un numero limitato di comandi viene chiamato un spazio di esecuzione vincolato.</span><span class="sxs-lookup"><span data-stu-id="8a2ed-138">A runspace that exposes only a limited number of commands is called a constrained runspace.</span></span>
<span data-ttu-id="8a2ed-139">Per creare uno spazio di esecuzione vincolato, usare il [System.Management.Automation.Runspaces.Runspace](/dotnet/api/System.Management.Automation.Runspaces.Runspace) e [System.Management.Automation.Runspaces.InitialSessionState](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) classi.</span><span class="sxs-lookup"><span data-stu-id="8a2ed-139">To create a constrained runspace, you use the [System.Management.Automation.Runspaces.Runspace](/dotnet/api/System.Management.Automation.Runspaces.Runspace) and [System.Management.Automation.Runspaces.InitialSessionState](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) classes.</span></span>

### <a name="creating-an-initialsessionstate-object"></a><span data-ttu-id="8a2ed-140">Creazione di un oggetto InitialSessionState</span><span class="sxs-lookup"><span data-stu-id="8a2ed-140">Creating an InitialSessionState object</span></span>

<span data-ttu-id="8a2ed-141">Per creare uno spazio di esecuzione personalizzata, è innanzitutto necessario creare un [System.Management.Automation.Runspaces.InitialSessionState](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) oggetto.</span><span class="sxs-lookup"><span data-stu-id="8a2ed-141">To create a custom runspace, you must first create an [System.Management.Automation.Runspaces.InitialSessionState](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) object.</span></span>
<span data-ttu-id="8a2ed-142">Nell'esempio seguente, usiamo il [System.Management.Automation.Runspaces.RunspaceFactory](/dotnet/api/System.Management.Automation.Runspaces.RunspaceFactory) per creare uno spazio di esecuzione dopo la creazione di un oggetto InitialSessionState predefinito.</span><span class="sxs-lookup"><span data-stu-id="8a2ed-142">In the following example, we use the [System.Management.Automation.Runspaces.RunspaceFactory](/dotnet/api/System.Management.Automation.Runspaces.RunspaceFactory) to create a runspace after creating a default InitialSessionState object.</span></span>

```csharp
InitialSessionState iss = InitialSessionState.CreateDefault();
Runspace rs = RunspaceFactory.CreateRunspace(iss);
rs.Open();
PowerShell ps = PowerShell.Create();
ps.Runspace = rs;
ps.AddCommand("Get-Command");
ps.Invoke();
```

### <a name="constraining-the-runspace"></a><span data-ttu-id="8a2ed-143">Vincolare lo spazio di esecuzione</span><span class="sxs-lookup"><span data-stu-id="8a2ed-143">Constraining the runspace</span></span>

<span data-ttu-id="8a2ed-144">Nell'esempio precedente è stato creato un valore predefinito [System.Management.Automation.Runspaces.InitialSessionState](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) oggetto che consente di caricare tutti i core predefinito Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="8a2ed-144">In the previous example, we created a default [System.Management.Automation.Runspaces.InitialSessionState](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) object that loads all of the built-in core Windows PowerShell.</span></span>
<span data-ttu-id="8a2ed-145">È possibile inoltre hanno chiamato la [System.Management.Automation.Runspaces.InitialSessionState.CreateDefault2](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState.CreateDefault2) metodo per creare un oggetto InitialSessionState che carica solo i comandi nel Microsoft.PowerShell.Core snap-in.</span><span class="sxs-lookup"><span data-stu-id="8a2ed-145">We could also have called the [System.Management.Automation.Runspaces.InitialSessionState.CreateDefault2](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState.CreateDefault2) method to create an InitialSessionState object that would load only the commands in the Microsoft.PowerShell.Core snapin.</span></span>
<span data-ttu-id="8a2ed-146">Per creare uno spazio di esecuzione più limitato, è necessario creare un oggetto vuoto InitialSessionState chiamando il [System.Management.Automation.Runspaces.InitialSessionState.Create](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState.Create) (metodo), quindi aggiungere i comandi per il InitialSessionState.</span><span class="sxs-lookup"><span data-stu-id="8a2ed-146">To create a more constrained runspace, you must create an empty InitialSessionState object by calling the [System.Management.Automation.Runspaces.InitialSessionState.Create](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState.Create) method, and then add commands to the InitialSessionState.</span></span>

<span data-ttu-id="8a2ed-147">Con uno spazio di esecuzione che carica solo i comandi che specificano offre prestazioni notevolmente migliorate.</span><span class="sxs-lookup"><span data-stu-id="8a2ed-147">Using a runspace that loads only the commands that you specify provides significantly improved performance.</span></span>

<span data-ttu-id="8a2ed-148">Usare i metodi del [System.Management.Automation.Runspaces.SessionStateCmdletEntry](/dotnet/api/System.Management.Automation.Runspaces.SessionStateCmdletEntry) classe per definire i cmdlet per lo stato sessione iniziale.</span><span class="sxs-lookup"><span data-stu-id="8a2ed-148">You use the methods of the [System.Management.Automation.Runspaces.SessionStateCmdletEntry](/dotnet/api/System.Management.Automation.Runspaces.SessionStateCmdletEntry) class to define cmdlets for the initial session state.</span></span>
<span data-ttu-id="8a2ed-149">Nell'esempio seguente crea uno stato sessione iniziale vuota, quindi definisce e aggiunge il `Get-Command` e `Import-Module` comandi per lo stato sessione iniziale.</span><span class="sxs-lookup"><span data-stu-id="8a2ed-149">The following example creates an empty initial session state, then defines and adds the `Get-Command` and `Import-Module` commands to the initial session state.</span></span>
<span data-ttu-id="8a2ed-150">Abbiamo quindi creare uno spazio di esecuzione vincolato dallo stato sessione iniziale ed eseguire i comandi in tale spazio di esecuzione.</span><span class="sxs-lookup"><span data-stu-id="8a2ed-150">We then create a runspace constrained by that initial session state, and execute the commands in that runspace.</span></span>

<span data-ttu-id="8a2ed-151">Creare lo stato sessione iniziale.</span><span class="sxs-lookup"><span data-stu-id="8a2ed-151">Create the initial session state.</span></span>

```csharp
InitialSessionState iss = InitialSessionState.Create();
```

<span data-ttu-id="8a2ed-152">Definire e aggiungere i comandi per lo stato sessione iniziale.</span><span class="sxs-lookup"><span data-stu-id="8a2ed-152">Define and add commands to the initial session state.</span></span>

```csharp
SessionStateCmdletEntry getCommand = new SessionStateCmdletEntry(
        "Get-Command", typeof(Microsoft.PowerShell.Commands.GetCommandCommand), "");
SessionStateCmdletEntry importModule = new SessionStateCmdletEntry(
        "Import-Module", typeof(Microsoft.PowerShell.Commands.ImportModuleCommand), "");
iss.Commands.Add(getCommand);
iss.Commands.Add(importModule);
```

<span data-ttu-id="8a2ed-153">Creare e aprire lo spazio di esecuzione.</span><span class="sxs-lookup"><span data-stu-id="8a2ed-153">Create and open the runspace.</span></span>

```csharp
Runspace rs = RunspaceFactory.CreateRunspace(iss);
rs.Open();
```

<span data-ttu-id="8a2ed-154">Eseguire un comando e visualizza il risultato.</span><span class="sxs-lookup"><span data-stu-id="8a2ed-154">Execute a command and show the result.</span></span>

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

<span data-ttu-id="8a2ed-155">Quando eseguito, l'output di questo codice avrà un aspetto come indicato di seguito.</span><span class="sxs-lookup"><span data-stu-id="8a2ed-155">When run, the output of this code will look as follows.</span></span>

```powershell
Get-Command
Import-Module
```
