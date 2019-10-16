---
title: Aggiunta e richiamo di comandi | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 62be8432-28c1-4ca2-bcdb-d0350163fa8c
caps.latest.revision: 5
ms.openlocfilehash: f776f13fe743a3f5f67de0d94883e3f754040ffc
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/15/2019
ms.locfileid: "72367640"
---
# <a name="adding-and-invoking-commands"></a><span data-ttu-id="e7a51-102">Aggiunta e richiamo dei comandi</span><span class="sxs-lookup"><span data-stu-id="e7a51-102">Adding and invoking commands</span></span>

<span data-ttu-id="e7a51-103">Dopo aver creato un spazio, è possibile aggiungere PowerShellcommands e script di Windows a una pipeline, quindi richiamare la pipeline in modo sincrono o asincrono.</span><span class="sxs-lookup"><span data-stu-id="e7a51-103">After creating a runspace, you can add Windows PowerShellcommands and scripts to a pipeline, and then invoke the pipeline synchronously or asynchronously.</span></span>

## <a name="creating-a-pipeline"></a><span data-ttu-id="e7a51-104">Creazione di una pipeline</span><span class="sxs-lookup"><span data-stu-id="e7a51-104">Creating a pipeline</span></span>

 <span data-ttu-id="e7a51-105">La classe [System. Management. Automation. PowerShell](/dotnet/api/system.management.automation.powershell) fornisce diversi metodi per aggiungere comandi, parametri e script alla pipeline.</span><span class="sxs-lookup"><span data-stu-id="e7a51-105">The [System.Management.Automation.Powershell](/dotnet/api/system.management.automation.powershell) class provides several methods to add commands, parameters, and scripts to the pipeline.</span></span> <span data-ttu-id="e7a51-106">È possibile richiamare la pipeline in modo sincrono chiamando un overload del metodo [System. Management. Automation. PowerShell. Invoke \*](/dotnet/api/System.Management.Automation.PowerShell.Invoke) o in modo asincrono chiamando un overload di [System. Management. Automation. PowerShell. BeginInvoke \*](/dotnet/api/System.Management.Automation.PowerShell.BeginInvoke) e quindi il metodo [System. Management. Automation. PowerShell. EndInvoke \*](/dotnet/api/System.Management.Automation.PowerShell.EndInvoke) .</span><span class="sxs-lookup"><span data-stu-id="e7a51-106">You can invoke the pipeline synchronously by calling an overload of the [System.Management.Automation.Powershell.Invoke\*](/dotnet/api/System.Management.Automation.PowerShell.Invoke) method, or asynchronously by calling an overload of the [System.Management.Automation.Powershell.Begininvoke\*](/dotnet/api/System.Management.Automation.PowerShell.BeginInvoke) and then the [System.Management.Automation.Powershell.Endinvoke\*](/dotnet/api/System.Management.Automation.PowerShell.EndInvoke) method.</span></span>

### <a name="addcommand"></a><span data-ttu-id="e7a51-107">AddCommand</span><span class="sxs-lookup"><span data-stu-id="e7a51-107">AddCommand</span></span>

1. <span data-ttu-id="e7a51-108">Creare un oggetto [System. Management. Automation. PowerShell](/dotnet/api/system.management.automation.powershell) .</span><span class="sxs-lookup"><span data-stu-id="e7a51-108">Create a [System.Management.Automation.Powershell](/dotnet/api/system.management.automation.powershell) object.</span></span>

   ```csharp
   PowerShell ps = PowerShell.Create();
   ```

2. <span data-ttu-id="e7a51-109">Aggiungere il comando che si desidera eseguire.</span><span class="sxs-lookup"><span data-stu-id="e7a51-109">Add the command that you want to execute.</span></span>

   ```csharp
   ps.AddCommand("Get-Process");
   ```

3. <span data-ttu-id="e7a51-110">Richiamare il comando.</span><span class="sxs-lookup"><span data-stu-id="e7a51-110">Invoke the command.</span></span>

   ```csharp
   ps.Invoke();
   ```

 <span data-ttu-id="e7a51-111">Se si chiama il metodo [System. Management. Automation. PowerShell. AddCommand \*](/dotnet/api/System.Management.Automation.PowerShell.AddCommand) più di una volta prima di chiamare il metodo [System. Management. Automation. PowerShell. Invoke \*](/dotnet/api/System.Management.Automation.PowerShell.Invoke) , il risultato del primo comando viene reindirizzato al secondo e così via.</span><span class="sxs-lookup"><span data-stu-id="e7a51-111">If you call the [System.Management.Automation.Powershell.Addcommand\*](/dotnet/api/System.Management.Automation.PowerShell.AddCommand) method more than once before you call the [System.Management.Automation.Powershell.Invoke\*](/dotnet/api/System.Management.Automation.PowerShell.Invoke) method, the result of the first command is piped to the second, and so on.</span></span> <span data-ttu-id="e7a51-112">Se non si vuole inviare tramite pipe il risultato di un comando precedente a un comando, aggiungerlo chiamando [System. Management. Automation. PowerShell. AddStatement \*](/dotnet/api/System.Management.Automation.PowerShell.AddStatement) .</span><span class="sxs-lookup"><span data-stu-id="e7a51-112">If you do not want to pipe the result of a previous command to a command, add it by calling the [System.Management.Automation.Powershell.Addstatement\*](/dotnet/api/System.Management.Automation.PowerShell.AddStatement) instead.</span></span>

### <a name="addparameter"></a><span data-ttu-id="e7a51-113">AddParameter</span><span class="sxs-lookup"><span data-stu-id="e7a51-113">AddParameter</span></span>

 <span data-ttu-id="e7a51-114">Nell'esempio precedente viene eseguito un unico comando senza parametri.</span><span class="sxs-lookup"><span data-stu-id="e7a51-114">The previous example executes a single command without any parameters.</span></span> <span data-ttu-id="e7a51-115">È possibile aggiungere parametri al comando usando il metodo [System. Management. Automation. PSCommand. AddParameter \*](/dotnet/api/System.Management.Automation.PSCommand.AddParameter) , ad esempio, il codice seguente ottiene un elenco di tutti i processi denominati `PowerShell` in esecuzione nel computer.</span><span class="sxs-lookup"><span data-stu-id="e7a51-115">You can add parameters to the command by using the [System.Management.Automation.Pscommand.Addparameter\*](/dotnet/api/System.Management.Automation.PSCommand.AddParameter) method For example, the following code gets a list of all of the processes that are named `PowerShell` running on the machine.</span></span>

```csharp
PowerShell.Create().AddCommand("Get-Process")
                   .AddParameter("Name", "PowerShell")
                   .Invoke();
```

 <span data-ttu-id="e7a51-116">È possibile aggiungere altri parametri chiamando [System. Management. Automation. PSCommand. AddParameter \*](/dotnet/api/System.Management.Automation.PSCommand.AddParameter) ripetutamente.</span><span class="sxs-lookup"><span data-stu-id="e7a51-116">You can add additional parameters by calling [System.Management.Automation.Pscommand.Addparameter\*](/dotnet/api/System.Management.Automation.PSCommand.AddParameter) repeatedly.</span></span>

```csharp
PowerShell.Create().AddCommand("Get-Process")
                   .AddParameter("Name", "PowerShell")
                   .AddParameter("Id", "12768")
                   .Invoke();
```

 <span data-ttu-id="e7a51-117">È anche possibile aggiungere un dizionario di nomi e valori di parametro chiamando il metodo [System. Management. Automation. PowerShell. AddParameters \*](/dotnet/api/System.Management.Automation.PowerShell.AddParameters) .</span><span class="sxs-lookup"><span data-stu-id="e7a51-117">You can also add a dictionary of parameter names and values by calling the [System.Management.Automation.Powershell.Addparameters\*](/dotnet/api/System.Management.Automation.PowerShell.AddParameters) method.</span></span>

```csharp
IDictionary parameters = new Dictionary<String, String>();
parameters.Add("Name", "PowerShell");

parameters.Add("Id", "12768");
PowerShell.Create().AddCommand("Get-Process")
   .AddParameters(parameters)
      .Invoke()

```

### <a name="addstatement"></a><span data-ttu-id="e7a51-118">AddStatement</span><span class="sxs-lookup"><span data-stu-id="e7a51-118">AddStatement</span></span>

 <span data-ttu-id="e7a51-119">È possibile simulare la suddivisione in batch usando il metodo [System. Management. Automation. PowerShell. AddStatement \*](/dotnet/api/System.Management.Automation.PowerShell.AddStatement) , che aggiunge un'altra istruzione alla fine della pipeline. il codice seguente ottiene un elenco di processi in esecuzione con il nome `PowerShell`, quindi Ottiene l'elenco dei servizi in esecuzione.</span><span class="sxs-lookup"><span data-stu-id="e7a51-119">You can simulate batching by using the [System.Management.Automation.Powershell.Addstatement\*](/dotnet/api/System.Management.Automation.PowerShell.AddStatement) method, which adds an additional statement to the end of the pipeline The following code gets a list of running processes with the name `PowerShell`, and then gets the list of running services.</span></span>

```csharp
PowerShell ps = PowerShell.Create();
ps.AddCommand("Get-Process").AddParameter("Name", "PowerShell");
ps.AddStatement().AddCommand("Get-Service");
ps.Invoke();
```

### <a name="addscript"></a><span data-ttu-id="e7a51-120">AddScript</span><span class="sxs-lookup"><span data-stu-id="e7a51-120">AddScript</span></span>

 <span data-ttu-id="e7a51-121">È possibile eseguire uno script esistente chiamando il metodo [System. Management. Automation. PowerShell. AddScript \*](/dotnet/api/System.Management.Automation.PowerShell.AddScript) .</span><span class="sxs-lookup"><span data-stu-id="e7a51-121">You can run an existing script by calling the [System.Management.Automation.Powershell.Addscript\*](/dotnet/api/System.Management.Automation.PowerShell.AddScript) method.</span></span> <span data-ttu-id="e7a51-122">Nell'esempio seguente viene aggiunto uno script alla pipeline ed eseguito.</span><span class="sxs-lookup"><span data-stu-id="e7a51-122">The following example adds a script to the pipeline and runs it.</span></span> <span data-ttu-id="e7a51-123">In questo esempio si presuppone che esista già uno script denominato `MyScript.ps1` in una cartella denominata `D:\PSScripts`.</span><span class="sxs-lookup"><span data-stu-id="e7a51-123">This example assumes there is already a script named `MyScript.ps1` in a folder named `D:\PSScripts`.</span></span>

```csharp
PowerShell ps = PowerShell.Create();
ps.AddScript("D:\PSScripts\MyScript.ps1").Invoke();
```

 <span data-ttu-id="e7a51-124">Esiste anche una versione del metodo [System. Management. Automation. PowerShell. AddScript \*](/dotnet/api/System.Management.Automation.PowerShell.AddScript) che accetta un parametro booleano denominato `useLocalScope`.</span><span class="sxs-lookup"><span data-stu-id="e7a51-124">There is also a version of the [System.Management.Automation.Powershell.Addscript\*](/dotnet/api/System.Management.Automation.PowerShell.AddScript) method that takes a boolean parameter named `useLocalScope`.</span></span> <span data-ttu-id="e7a51-125">Se questo parametro è impostato su `true`, lo script viene eseguito nell'ambito locale.</span><span class="sxs-lookup"><span data-stu-id="e7a51-125">If this parameter is set to `true`, then the script is run in the local scope.</span></span> <span data-ttu-id="e7a51-126">Nel codice seguente viene eseguito lo script nell'ambito locale.</span><span class="sxs-lookup"><span data-stu-id="e7a51-126">The following code will run the script in the local scope.</span></span>

```csharp
PowerShell ps = PowerShell.Create();
ps.AddScript(@"D:\PSScripts\MyScript.ps1", true).Invoke();
```

### <a name="invoking-a-pipeline-synchronously"></a><span data-ttu-id="e7a51-127">Richiamo di una pipeline in modo sincrono</span><span class="sxs-lookup"><span data-stu-id="e7a51-127">Invoking a pipeline synchronously</span></span>

 <span data-ttu-id="e7a51-128">Quando si aggiungono elementi alla pipeline, questo viene richiamato.</span><span class="sxs-lookup"><span data-stu-id="e7a51-128">After you add elements to the pipeline, you invoke it.</span></span> <span data-ttu-id="e7a51-129">Per richiamare la pipeline in modo sincrono, chiamare un overload del metodo [System. Management. Automation. PowerShell. Invoke \*](/dotnet/api/System.Management.Automation.PowerShell.Invoke) .</span><span class="sxs-lookup"><span data-stu-id="e7a51-129">To invoke the pipeline synchronously, you call an overload of the [System.Management.Automation.Powershell.Invoke\*](/dotnet/api/System.Management.Automation.PowerShell.Invoke) method.</span></span> <span data-ttu-id="e7a51-130">Nell'esempio seguente viene illustrato come richiamare in modo sincrono una pipeline.</span><span class="sxs-lookup"><span data-stu-id="e7a51-130">The following example shows how to synchronously invoke a pipeline.</span></span>

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

### <a name="invoking-a-pipeline-asynchronously"></a><span data-ttu-id="e7a51-131">Richiamo di una pipeline in modo asincrono</span><span class="sxs-lookup"><span data-stu-id="e7a51-131">Invoking a pipeline asynchronously</span></span>

 <span data-ttu-id="e7a51-132">Si richiama una pipeline in modo asincrono chiamando un overload di [System. Management. Automation. PowerShell. BeginInvoke \*](/dotnet/api/System.Management.Automation.PowerShell.BeginInvoke) per creare un oggetto [IAsyncResult](https://msdn.microsoft.com/library/system.iasyncresult\(v=vs.110\).aspx) e quindi chiamando [System. Management. Automation. PowerShell. EndInvoke \*](/dotnet/api/System.Management.Automation.PowerShell.EndInvoke) metodo.</span><span class="sxs-lookup"><span data-stu-id="e7a51-132">You invoke a pipeline asynchronously by calling an overload of the [System.Management.Automation.Powershell.Begininvoke\*](/dotnet/api/System.Management.Automation.PowerShell.BeginInvoke) to create an [IAsyncResult](https://msdn.microsoft.com/library/system.iasyncresult\(v=vs.110\).aspx) object, and then calling the [System.Management.Automation.Powershell.Endinvoke\*](/dotnet/api/System.Management.Automation.PowerShell.EndInvoke) method.</span></span>

 <span data-ttu-id="e7a51-133">Nell'esempio seguente viene illustrato come richiamare una pipeline in modo asincrono.</span><span class="sxs-lookup"><span data-stu-id="e7a51-133">The following example shows how to invoke a pipeline asynchronously.</span></span>

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
      // Get-Process cmdlet. Do not include spaces immediately
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

## <a name="see-also"></a><span data-ttu-id="e7a51-134">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="e7a51-134">See Also</span></span>

 [<span data-ttu-id="e7a51-135">Creazione di un InitialSessionState</span><span class="sxs-lookup"><span data-stu-id="e7a51-135">Creating an InitialSessionState</span></span>](./creating-an-initialsessionstate.md)

 [<span data-ttu-id="e7a51-136">Creazione di un spazio vincolato</span><span class="sxs-lookup"><span data-stu-id="e7a51-136">Creating a constrained runspace</span></span>](./creating-a-constrained-runspace.md)
