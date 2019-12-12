---
title: Creazione di più Runspaces | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 42c40c7f-1ee7-4021-950c-2e013c8f2a4a
caps.latest.revision: 4
ms.openlocfilehash: 606a2ee4e70d303bf1b1d69b7523eb8649f9be0c
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/05/2019
ms.locfileid: "72367610"
---
# <a name="creating-multiple-runspaces"></a><span data-ttu-id="8cb48-102">Creazione di più spazi di esecuzione</span><span class="sxs-lookup"><span data-stu-id="8cb48-102">Creating multiple runspaces</span></span>

<span data-ttu-id="8cb48-103">Se si crea un numero elevato di Runspaces, è possibile prendere in considerazione la creazione di un pool spazio.</span><span class="sxs-lookup"><span data-stu-id="8cb48-103">If you create a large number of runspaces, you might consider creating a runspace pool.</span></span> <span data-ttu-id="8cb48-104">L'uso di un oggetto [System. Management. Automation. Runspaces. Runspacepool](/dotnet/api/System.Management.Automation.Runspaces.RunspacePool) , anziché creare un numero elevato di singoli Runspaces con le stesse caratteristiche, può migliorare le prestazioni.</span><span class="sxs-lookup"><span data-stu-id="8cb48-104">Using a [System.Management.Automation.Runspaces.Runspacepool](/dotnet/api/System.Management.Automation.Runspaces.RunspacePool) object, rather than creating a large number of individual runspaces with the same characteristics, can improve performance.</span></span>

## <a name="creating-and-using-a-runspace-pool"></a><span data-ttu-id="8cb48-105">Creazione e utilizzo di un pool spazio.</span><span class="sxs-lookup"><span data-stu-id="8cb48-105">Creating and using a runspace pool.</span></span>

 <span data-ttu-id="8cb48-106">Nell'esempio seguente viene illustrato come creare un pool spazio e come eseguire un comando in modo asincrono in un spazio del pool.</span><span class="sxs-lookup"><span data-stu-id="8cb48-106">The following example shows how to create a runspace pool and how to run a command asynchronously in a runspace of the pool.</span></span>

```csharp
namespace HostRunspacePool
{
  using System;
  using System.Collections.ObjectModel;
  using System.Management.Automation;
  using System.Management.Automation.Runspaces;

  /// <summary>
  /// This class provides the Main entry point for the Host application.
  /// </summary>
  internal class HostRunspacePool
  {
    /// <summary>
    /// This sample demonstrates the following.
    /// 1. Creating and opening a runspace pool.
    /// 2. Creating a PowerShell object.
    /// 3. Adding commands and arguments to the PowerShell object.
    /// 4. Running the commands asynchronously using the runspace
    ///    of the runspace pool.
    /// </summary>
    /// <param name="args">Parameter is not used.</param>
    private static void Main(string[] args)
    {
      // Create a pool of runspaces.
      using (RunspacePool rsp = RunspaceFactory.CreateRunspacePool())
      {
        rsp.Open();

        // Create a PowerShell object to run the following command.
        //  get-process wmi*
        PowerShell gpc = PowerShell.Create();
        // Specify the runspace to use and add commands.
        gpc.RunspacePool = rsp;
        gpc.AddCommand("Get-Process").AddArgument("wmi*");

        // Invoke the command asynchronously.
        IAsyncResult gpcAsyncResult = gpc.BeginInvoke();
        // Get the results of running the command.
        PSDataCollection<PSObject> gpcOutput = gpc.EndInvoke(gpcAsyncResult);

        // Process the output.
        Console.WriteLine("The output from running the command: get-process wmi*");
        for (int i= 0; i < gpcOutput.Count; i++)
        {
         Console.WriteLine(
                           "Process Name: {0} Process Id: {1}",
                           gpcOutput[i].Properties["ProcessName"].Value,
                           gpcOutput[i].Properties["Id"].Value);
        }
      } // End using.
    } // End Main entry point.
  } // End HostPs5 class.
}
```

## <a name="see-also"></a><span data-ttu-id="8cb48-107">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="8cb48-107">See Also</span></span>

 [<span data-ttu-id="8cb48-108">Creazione di un InitialSessionState</span><span class="sxs-lookup"><span data-stu-id="8cb48-108">Creating an InitialSessionState</span></span>](./creating-an-initialsessionstate.md)
