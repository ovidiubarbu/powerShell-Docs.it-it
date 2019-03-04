---
title: Aggiunta e la chiamata dei comandi | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 62be8432-28c1-4ca2-bcdb-d0350163fa8c
caps.latest.revision: 5
ms.openlocfilehash: 31371797ee57f07075da3436e0b42b2ca01aaffd
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/03/2019
ms.locfileid: "56857347"
---
# <a name="adding-and-invoking-commands"></a><span data-ttu-id="502ca-102">Aggiunta e richiamo dei comandi</span><span class="sxs-lookup"><span data-stu-id="502ca-102">Adding and invoking commands</span></span>

<span data-ttu-id="502ca-103">Dopo aver creato uno spazio di esecuzione, è possibile aggiungere script e PowerShellcommands Windows a una pipeline e quindi richiama la pipeline in modo sincrono o asincrono.</span><span class="sxs-lookup"><span data-stu-id="502ca-103">After creating a runspace, you can add Windows PowerShellcommands and scripts to a pipeline, and then invoke the pipeline synchronously or asynchronously.</span></span>

## <a name="creating-a-pipeline"></a><span data-ttu-id="502ca-104">Creazione di una pipeline</span><span class="sxs-lookup"><span data-stu-id="502ca-104">Creating a pipeline</span></span>

 <span data-ttu-id="502ca-105">Il [System.Management.Automation.Powershell](/dotnet/api/system.management.automation.powershell) classe fornisce diversi metodi per aggiungere comandi e parametri di script alla pipeline.</span><span class="sxs-lookup"><span data-stu-id="502ca-105">The [System.Management.Automation.Powershell](/dotnet/api/system.management.automation.powershell) class provides several methods to add commands, parameters, and scripts to the pipeline.</span></span> <span data-ttu-id="502ca-106">È possibile richiamare la pipeline in modo sincrono chiamando un overload del [System.Management.Automation.Powershell.Invoke\*](/dotnet/api/System.Management.Automation.PowerShell.Invoke) metodo, o in modo asincrono chiamando un overload del [ System.Management.Automation.Powershell.Begininvoke\*](/dotnet/api/System.Management.Automation.PowerShell.BeginInvoke) e quindi il [System.Management.Automation.Powershell.Endinvoke\*](/dotnet/api/System.Management.Automation.PowerShell.EndInvoke) (metodo).</span><span class="sxs-lookup"><span data-stu-id="502ca-106">You can invoke the pipeline synchronously by calling an overload of the [System.Management.Automation.Powershell.Invoke\*](/dotnet/api/System.Management.Automation.PowerShell.Invoke) method, or asynchronously by calling an overload of the [System.Management.Automation.Powershell.Begininvoke\*](/dotnet/api/System.Management.Automation.PowerShell.BeginInvoke) and then the [System.Management.Automation.Powershell.Endinvoke\*](/dotnet/api/System.Management.Automation.PowerShell.EndInvoke) method.</span></span>

### <a name="addcommand"></a><span data-ttu-id="502ca-107">AddCommand</span><span class="sxs-lookup"><span data-stu-id="502ca-107">AddCommand</span></span>

1. <span data-ttu-id="502ca-108">Creare un [System.Management.Automation.Powershell](/dotnet/api/system.management.automation.powershell) oggetto.</span><span class="sxs-lookup"><span data-stu-id="502ca-108">Create a [System.Management.Automation.Powershell](/dotnet/api/system.management.automation.powershell) object.</span></span>

   ```csharp
   PowerShell ps = PowerShell.Create();
   ```

2. <span data-ttu-id="502ca-109">Aggiungere il comando che si desidera eseguire.</span><span class="sxs-lookup"><span data-stu-id="502ca-109">Add the command that you want to execute.</span></span>

   ```csharp
   ps.AddCommand("Get-Process");
   ```

3. <span data-ttu-id="502ca-110">Richiamare il comando.</span><span class="sxs-lookup"><span data-stu-id="502ca-110">Invoke the command.</span></span>

   ```csharp
   ps.Invoke();
   ```

 <span data-ttu-id="502ca-111">Se si chiama il [System.Management.Automation.Powershell.Addcommand\*](/dotnet/api/System.Management.Automation.PowerShell.AddCommand) metodo più volte prima di chiamare le [System.Management.Automation.Powershell.Invoke\*](/dotnet/api/System.Management.Automation.PowerShell.Invoke) (metodo), il risultato del primo comando viene reindirizzato al secondo e così via.</span><span class="sxs-lookup"><span data-stu-id="502ca-111">If you call the [System.Management.Automation.Powershell.Addcommand\*](/dotnet/api/System.Management.Automation.PowerShell.AddCommand) method more than once before you call the [System.Management.Automation.Powershell.Invoke\*](/dotnet/api/System.Management.Automation.PowerShell.Invoke) method, the result of the first command is piped to the second, and so on.</span></span> <span data-ttu-id="502ca-112">Se non si desidera inviare tramite pipe il risultato di un comando precedente a un comando, aggiungerlo chiamando il [System.Management.Automation.Powershell.Addstatement\*](/dotnet/api/System.Management.Automation.PowerShell.AddStatement) invece.</span><span class="sxs-lookup"><span data-stu-id="502ca-112">If you do not want to pipe the result of a previous command to a command, add it by calling the [System.Management.Automation.Powershell.Addstatement\*](/dotnet/api/System.Management.Automation.PowerShell.AddStatement) instead.</span></span>

### <a name="addparameter"></a><span data-ttu-id="502ca-113">AddParameter</span><span class="sxs-lookup"><span data-stu-id="502ca-113">AddParameter</span></span>

 <span data-ttu-id="502ca-114">Nell'esempio precedente esegue un comando singolo senza parametri.</span><span class="sxs-lookup"><span data-stu-id="502ca-114">The previous example executes a single command without any parameters.</span></span> <span data-ttu-id="502ca-115">È possibile aggiungere parametri al comando utilizzando il [System.Management.Automation.Pscommand.Addparameter\*](/dotnet/api/System.Management.Automation.PSCommand.AddParameter) metodo, ad esempio, il codice seguente ottiene un elenco di tutti i processi denominati `PowerShell` in esecuzione sul macchina.</span><span class="sxs-lookup"><span data-stu-id="502ca-115">You can add parameters to the command by using the [System.Management.Automation.Pscommand.Addparameter\*](/dotnet/api/System.Management.Automation.PSCommand.AddParameter) method For example, the following code gets a list of all of the processes that are named `PowerShell` running on the machine.</span></span>

```csharp
PowerShell.Create().AddCommand("Get-Process")
                   .AddParameter("Name", "PowerShell")
                   .Invoke();
```

 <span data-ttu-id="502ca-116">È possibile aggiungere ulteriori parametri chiamando [System.Management.Automation.Pscommand.Addparameter\*](/dotnet/api/System.Management.Automation.PSCommand.AddParameter) ripetutamente.</span><span class="sxs-lookup"><span data-stu-id="502ca-116">You can add additional parameters by calling [System.Management.Automation.Pscommand.Addparameter\*](/dotnet/api/System.Management.Automation.PSCommand.AddParameter) repeatedly.</span></span>

```csharp
PowerShell.Create().AddCommand("Get-Process")
                   .AddParameter("Name", "PowerShell")
                   .AddParameter("Id", "12768")
                   .Invoke();
```

 <span data-ttu-id="502ca-117">È anche possibile aggiungere un dizionario di nomi dei parametri e valori chiamando il [System.Management.Automation.Powershell.Addparameters\*](/dotnet/api/System.Management.Automation.PowerShell.AddParameters) (metodo).</span><span class="sxs-lookup"><span data-stu-id="502ca-117">You can also add a dictionary of parameter names and values by calling the [System.Management.Automation.Powershell.Addparameters\*](/dotnet/api/System.Management.Automation.PowerShell.AddParameters) method.</span></span>

```csharp
IDictionary parameters = new Dictionary<String, String>();
parameters.Add("Name", "PowerShell");

parameters.Add("Id", "12768");
PowerShell.Create().AddCommand("Get-Process")
   .AddParameters(parameters)
      .Invoke()

```

### <a name="addstatement"></a><span data-ttu-id="502ca-118">AddStatement</span><span class="sxs-lookup"><span data-stu-id="502ca-118">AddStatement</span></span>

 <span data-ttu-id="502ca-119">È possibile simulare l'invio in batch usando il [System.Management.Automation.Powershell.Addstatement\*](/dotnet/api/System.Management.Automation.PowerShell.AddStatement) metodo, che aggiunge un'ulteriore istruzione alla fine della pipeline il codice seguente ottiene un elenco di processi in esecuzione con il nome `PowerShell`e quindi Ottiene l'elenco dei servizi in esecuzione.</span><span class="sxs-lookup"><span data-stu-id="502ca-119">You can simulate batching by using the [System.Management.Automation.Powershell.Addstatement\*](/dotnet/api/System.Management.Automation.PowerShell.AddStatement) method, which adds an additional statement to the end of the pipeline The following code gets a list of running processes with the name `PowerShell`, and then gets the list of running services.</span></span>

```csharp
PowerShell ps = PowerShell.Create();
ps.AddCommand("Get-Process").AddParameter("Name", "PowerShell");
ps.AddStatement().AddCommand("Get-Service");
ps.Invoke();
```

### <a name="addscript"></a><span data-ttu-id="502ca-120">AddScript</span><span class="sxs-lookup"><span data-stu-id="502ca-120">AddScript</span></span>

 <span data-ttu-id="502ca-121">È possibile eseguire uno script esistente chiamando il [System.Management.Automation.Powershell.Addscript\*](/dotnet/api/System.Management.Automation.PowerShell.AddScript) (metodo).</span><span class="sxs-lookup"><span data-stu-id="502ca-121">You can run an existing script by calling the [System.Management.Automation.Powershell.Addscript\*](/dotnet/api/System.Management.Automation.PowerShell.AddScript) method.</span></span> <span data-ttu-id="502ca-122">Nell'esempio seguente aggiunge uno script alla pipeline e lo esegue.</span><span class="sxs-lookup"><span data-stu-id="502ca-122">The following example adds a script to the pipeline and runs it.</span></span> <span data-ttu-id="502ca-123">In questo esempio si presuppone che è già presente uno script denominato `MyScript.ps1` in una cartella denominata `D:\PSScripts`.</span><span class="sxs-lookup"><span data-stu-id="502ca-123">This example assumes there is already a script named `MyScript.ps1` in a folder named `D:\PSScripts`.</span></span>

```csharp
PowerShell ps = PowerShell.Create();
ps.AddScript("D:\PSScripts\MyScript.ps1").Invoke();
```

 <span data-ttu-id="502ca-124">È inoltre disponibile una versione del [System.Management.Automation.Powershell.Addscript\*](/dotnet/api/System.Management.Automation.PowerShell.AddScript) metodo che accetta un parametro booleano denominato `useLocalScope`.</span><span class="sxs-lookup"><span data-stu-id="502ca-124">There is also a version of the [System.Management.Automation.Powershell.Addscript\*](/dotnet/api/System.Management.Automation.PowerShell.AddScript) method that takes a boolean parameter named `useLocalScope`.</span></span> <span data-ttu-id="502ca-125">Se questo parametro è impostato su `true`, quindi lo script viene eseguito nell'ambito locale.</span><span class="sxs-lookup"><span data-stu-id="502ca-125">If this parameter is set to `true`, then the script is run in the local scope.</span></span> <span data-ttu-id="502ca-126">Il codice seguente verrà eseguito lo script nell'ambito locale.</span><span class="sxs-lookup"><span data-stu-id="502ca-126">The following code will run the script in the local scope.</span></span>

```csharp
PowerShell ps = PowerShell.Create();
ps.AddScript(@"D:\PSScripts\MyScript.ps1", true).Invoke();
```

### <a name="invoking-a-pipeline-synchronously"></a><span data-ttu-id="502ca-127">Chiamata in modo sincrono una pipeline</span><span class="sxs-lookup"><span data-stu-id="502ca-127">Invoking a pipeline synchronously</span></span>

 <span data-ttu-id="502ca-128">Dopo aver aggiunto gli elementi alla pipeline, si richiamarlo.</span><span class="sxs-lookup"><span data-stu-id="502ca-128">After you add elements to the pipeline, you invoke it.</span></span> <span data-ttu-id="502ca-129">Per richiamare la pipeline in modo sincrono, chiamare un overload del [System.Management.Automation.Powershell.Invoke\*](/dotnet/api/System.Management.Automation.PowerShell.Invoke) (metodo).</span><span class="sxs-lookup"><span data-stu-id="502ca-129">To invoke the pipeline synchronously, you call an overload of the [System.Management.Automation.Powershell.Invoke\*](/dotnet/api/System.Management.Automation.PowerShell.Invoke) method.</span></span> <span data-ttu-id="502ca-130">Nell'esempio seguente viene illustrato come richiamare in modo sincrono una pipeline.</span><span class="sxs-lookup"><span data-stu-id="502ca-130">The following example shows how to synchronously invoke a pipeline.</span></span>

```csharp
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using System.Management.Automation;

namespace HostPS1e
{
  class HostPS1e
  {
    static void Main(string[] args)
    {
      // Using the PowerShell.Create and AddCommand
      // methods, create a command pipeline.
      PowerShell ps = PowerShell.Create().AddCommand ("Sort-Object");

      // Using the PowerShell.Invoke method, run the command
      // pipeline using the supplied input.
      foreach (PSObject result in ps.Invoke(new int[] { 3, 1, 6, 2, 5, 4 }))
      {
          Console.WriteLine("{0}", result);
      } // End foreach.
    } // End Main.
  } // End HostPS1e.
}
```

### <a name="invoking-a-pipeline-asynchronously"></a><span data-ttu-id="502ca-131">Chiamata di una pipeline in modo asincrono</span><span class="sxs-lookup"><span data-stu-id="502ca-131">Invoking a pipeline asynchronously</span></span>

 <span data-ttu-id="502ca-132">Si richiama una pipeline in modo asincrono chiamando un overload del [System.Management.Automation.Powershell.Begininvoke\*](/dotnet/api/System.Management.Automation.PowerShell.BeginInvoke) per creare un [IAsyncResult](http://msdn.microsoft.com/library/system.iasyncresult\(v=vs.110\).aspx) e quindi chiamando il [ System.Management.Automation.Powershell.Endinvoke\*](/dotnet/api/System.Management.Automation.PowerShell.EndInvoke) (metodo).</span><span class="sxs-lookup"><span data-stu-id="502ca-132">You invoke a pipeline asynchronously by calling an overload of the [System.Management.Automation.Powershell.Begininvoke\*](/dotnet/api/System.Management.Automation.PowerShell.BeginInvoke) to create an [IAsyncResult](http://msdn.microsoft.com/library/system.iasyncresult\(v=vs.110\).aspx) object, and then calling the [System.Management.Automation.Powershell.Endinvoke\*](/dotnet/api/System.Management.Automation.PowerShell.EndInvoke) method.</span></span>

 <span data-ttu-id="502ca-133">Nell'esempio seguente viene illustrato come richiamare un asynchronoulsy pipeline.</span><span class="sxs-lookup"><span data-stu-id="502ca-133">The following example shows how to invoke a pipeline asynchronoulsy.</span></span>

```csharp
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using System.Management.Automation;

namespace HostPS3
{
  class HostPS3
  {
    static void Main(string[] args)
    {
      // Use the PowerShell.Create and PowerShell.AddCommand
      // methods to create a command pipeline that includes
      // Get-Process cmdlet. Do not include spaces immediatly
      // before or after the cmdlet name as that will cause
      // the command to fail.
      PowerShell ps = PowerShell.Create().AddCommand("Get-Process");

      // Create an IAsyncResult object and call the
      // BeginInvoke method to start running the
      // command pipeline asynchronously.
      IAsyncResult async = ps.BeginInvoke();

      // Using the PowerShell.Invoke method, run the command
      // pipeline using the default runspace.
      foreach (PSObject result in ps.EndInvoke(async))
      {
        Console.WriteLine("{0,-20}{1}",
                result.Members["ProcessName"].Value,
                result.Members["Id"].Value);
      } // End foreach.
      System.Console.WriteLine("Hit any key to exit.");
      System.Console.ReadKey();
    } // End Main.
  } // End HostPS3.
}
```

## <a name="see-also"></a><span data-ttu-id="502ca-134">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="502ca-134">See Also</span></span>

 [<span data-ttu-id="502ca-135">Creazione di un InitialSessionState</span><span class="sxs-lookup"><span data-stu-id="502ca-135">Creating an InitialSessionState</span></span>](./creating-an-initialsessionstate.md)

 [<span data-ttu-id="502ca-136">Creazione di uno spazio di esecuzione vincolata</span><span class="sxs-lookup"><span data-stu-id="502ca-136">Creating a constrained runspace</span></span>](./creating-a-constrained-runspace.md)
