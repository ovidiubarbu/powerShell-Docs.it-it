---
title: Creazione di un InitialSessionState | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 5ae707db-52e0-408c-87fa-b35c42eaaab1
caps.latest.revision: 5
ms.openlocfilehash: 3a7c47487b632d00643fce0aa082e0dc9a9bb626
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/16/2019
ms.locfileid: "58057995"
---
# <a name="creating-an-initialsessionstate"></a><span data-ttu-id="a64de-102">Creazione di un InitialSessionState</span><span class="sxs-lookup"><span data-stu-id="a64de-102">Creating an InitialSessionState</span></span>

<span data-ttu-id="a64de-103">I comandi di Windows PowerShell eseguiti in uno spazio di esecuzione.</span><span class="sxs-lookup"><span data-stu-id="a64de-103">Windows PowerShell commands run in a runspace.</span></span> <span data-ttu-id="a64de-104">Per ospitare Windows PowerShell nell'applicazione, è necessario creare un [System.Management.Automation.Runspaces.Runspace](/dotnet/api/System.Management.Automation.Runspaces.Runspace) oggetto.</span><span class="sxs-lookup"><span data-stu-id="a64de-104">To host Windows PowerShell in your application, you must create a [System.Management.Automation.Runspaces.Runspace](/dotnet/api/System.Management.Automation.Runspaces.Runspace) object.</span></span> <span data-ttu-id="a64de-105">Ogni spazio di esecuzione ha un [System.Management.Automation.Runspaces.Initialsessionstate](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) oggetto associato.</span><span class="sxs-lookup"><span data-stu-id="a64de-105">Every runspace has an [System.Management.Automation.Runspaces.Initialsessionstate](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) object associated with it.</span></span> <span data-ttu-id="a64de-106">Il [System.Management.Automation.Runspaces.Initialsessionstate](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) specifica le caratteristiche di spazio di esecuzione, ad esempio quali moduli, variabili e comandi sono disponibili per tale spazio di esecuzione.</span><span class="sxs-lookup"><span data-stu-id="a64de-106">The [System.Management.Automation.Runspaces.Initialsessionstate](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) specifies characteristics of the runspace, such as which commands, variables, and modules are available for that runspace.</span></span>

## <a name="create-a-default-initialsessionstate"></a><span data-ttu-id="a64de-107">Creare un valore predefinito InitialSessionState</span><span class="sxs-lookup"><span data-stu-id="a64de-107">Create a default InitialSessionState</span></span>

 <span data-ttu-id="a64de-108">Il [System.Management.Automation.Runspaces.Initialsessionstate.Createdefault\*](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState.CreateDefault)e [System.Management.Automation.Runspaces.Initialsessionstate.Createdefault2\*](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState.CreateDefault2) metodi possono essere usati Per creare [System.Management.Automation.Runspaces.Initialsessionstate](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) oggetti.</span><span class="sxs-lookup"><span data-stu-id="a64de-108">The [System.Management.Automation.Runspaces.Initialsessionstate.Createdefault\*](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState.CreateDefault)and [System.Management.Automation.Runspaces.Initialsessionstate.Createdefault2\*](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState.CreateDefault2) methods can be used to create [System.Management.Automation.Runspaces.Initialsessionstate](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) objects.</span></span> <span data-ttu-id="a64de-109">[System.Management.Automation.Runspaces.Initialsessionstate.Createdefault\*](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState.CreateDefault) crea un InitialSessionState con tutti i comandi predefiniti caricato, mentre [ System.Management.Automation.Runspaces.Initialsessionstate.Createdefault2\*](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState.CreateDefault2) carica solo i comandi necessari all'host di Windows PowerShell (i comandi dal modulo Microsoft.PowerShell.Core.</span><span class="sxs-lookup"><span data-stu-id="a64de-109">[System.Management.Automation.Runspaces.Initialsessionstate.Createdefault\*](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState.CreateDefault) creates an InitialSessionState with all of the built-in commands loaded, while [System.Management.Automation.Runspaces.Initialsessionstate.Createdefault2\*](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState.CreateDefault2) loads only the commands required to host Windows PowerShell (the commands from the Microsoft.PowerShell.Core module.</span></span>

 <span data-ttu-id="a64de-110">Se si desidera limitare ulteriormente i comandi disponibili nell'applicazione host è necessario creare uno spazio di esecuzione vincolato.</span><span class="sxs-lookup"><span data-stu-id="a64de-110">If you want to further limit the commands available in your host application you need to create a constrained runspace.</span></span> <span data-ttu-id="a64de-111">Per informazioni, vedere Creazione di uno spazio di esecuzione vincolato.</span><span class="sxs-lookup"><span data-stu-id="a64de-111">For information, see Creating a constrained runspace.</span></span>

 <span data-ttu-id="a64de-112">Il codice seguente viene illustrato come creare un InitialSessionState, assegnarla a uno spazio di esecuzione, aggiungere comandi alla pipeline in tale spazio di esecuzione e richiamare i comandi.</span><span class="sxs-lookup"><span data-stu-id="a64de-112">The following code shows how to create an InitialSessionState, assign it to a runspace, add commands to the pipeline in that runspace, and invoke the commands.</span></span> <span data-ttu-id="a64de-113">Per altre informazioni sull'aggiunta e la chiamata dei comandi, vedere Aggiunta e la chiamata di comandi.</span><span class="sxs-lookup"><span data-stu-id="a64de-113">For more information about adding and invoking commands, see Adding and invoking commands.</span></span>

```csharp

namespace SampleHost
{
  using System;
  using System.Management.Automation;
  using System.Management.Automation.Runspaces;

  class HostP4b
  {
    static void Main(string[] args)
    {
      // Call the InitialSessionState.CreateDefault method to create
      // an empty InitialSessionState object, and then add the
      // elements that will be available when the runspace is opened.
      InitialSessionState iss = InitialSessionState.CreateDefault();
      SessionStateVariableEntry var1 = new
          SessionStateVariableEntry("test1",
                                    "MyVar1",
                                    "Initial session state MyVar1 test");
      iss.Variables.Add(var1);

      SessionStateVariableEntry var2 = new
          SessionStateVariableEntry("test2",
                                    "MyVar2",
                                    "Initial session state MyVar2 test");
      iss.Variables.Add(var2);

      // Call the RunspaceFactory.CreateRunspace(InitialSessionState)
      // method to create the runspace where the pipeline is run.
      Runspace rs = RunspaceFactory.CreateRunspace(iss);
      rs.Open();

      // Call the PowerShell.Create() method to create the PowerShell
      // object,and then specify the runspace and commands to the pipeline.
      // and  create the command pipeline.
      PowerShell ps = PowerShell.Create();
      ps.Runspace = rs;
      ps.AddCommand("Get-Variable");
      ps.AddArgument("test*");

      Console.WriteLine("Variable             Value");
      Console.WriteLine("--------------------------");

      // Call the PowerShell.Invoke() method to run
      // the pipeline synchronously.
        foreach (PSObject result in ps.Invoke())
        {
          Console.WriteLine("{0,-20}{1}",
                  result.Members["Name"].Value,
                  result.Members["Value"].Value);
        } // End foreach.

        // Close the runspace to free resources.
        rs.Close();

    } // End Main.
  } // End SampleHost.
}
```

## <a name="see-also"></a><span data-ttu-id="a64de-114">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="a64de-114">See Also</span></span>

 [<span data-ttu-id="a64de-115">Creazione di uno spazio di esecuzione vincolata</span><span class="sxs-lookup"><span data-stu-id="a64de-115">Creating a constrained runspace</span></span>](./creating-a-constrained-runspace.md)
