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
ms.openlocfilehash: 9140d03e046def2fbbcc2a842b9ea1b9e1fa2985
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/05/2019
ms.locfileid: "72367620"
---
# <a name="creating-an-initialsessionstate"></a><span data-ttu-id="847ef-102">Creazione di un InitialSessionState</span><span class="sxs-lookup"><span data-stu-id="847ef-102">Creating an InitialSessionState</span></span>

<span data-ttu-id="847ef-103">I comandi di PowerShell vengono eseguiti in un spazio.</span><span class="sxs-lookup"><span data-stu-id="847ef-103">PowerShell commands run in a runspace.</span></span>
<span data-ttu-id="847ef-104">Per ospitare PowerShell nell'applicazione, è necessario creare un oggetto [System. Management. Automation. Runspaces. spazio](/dotnet/api/System.Management.Automation.Runspaces.Runspace) .</span><span class="sxs-lookup"><span data-stu-id="847ef-104">To host PowerShell in your application, you must create a [System.Management.Automation.Runspaces.Runspace](/dotnet/api/System.Management.Automation.Runspaces.Runspace) object.</span></span>
<span data-ttu-id="847ef-105">Ogni spazio dispone di un oggetto [System. Management. Automation. Runspaces. InitialSessionState](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) associato.</span><span class="sxs-lookup"><span data-stu-id="847ef-105">Every runspace has an [System.Management.Automation.Runspaces.InitialSessionState](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) object associated with it.</span></span>
<span data-ttu-id="847ef-106">InitialSessionState specifica le caratteristiche di spazio, ad esempio i comandi, le variabili e i moduli disponibili per tale spazio.</span><span class="sxs-lookup"><span data-stu-id="847ef-106">The InitialSessionState specifies characteristics of the runspace, such as which commands, variables, and modules are available for that runspace.</span></span>

## <a name="create-a-default-initialsessionstate"></a><span data-ttu-id="847ef-107">Creare un InitialSessionState predefinito</span><span class="sxs-lookup"><span data-stu-id="847ef-107">Create a default InitialSessionState</span></span>

<span data-ttu-id="847ef-108">Per creare un oggetto **InitialSessionState** , è possibile usare i metodi [CreateDefault](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState.CreateDefault) e [CreateDefault2](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState.CreateDefault2) della classe **InitialSessionState** .</span><span class="sxs-lookup"><span data-stu-id="847ef-108">The [CreateDefault](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState.CreateDefault) and [CreateDefault2](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState.CreateDefault2) methods of the **InitialSessionState** class can be used to create an **InitialSessionState** object.</span></span>
<span data-ttu-id="847ef-109">Il metodo **CreateDefault** crea un **InitialSessionState** con tutti i comandi incorporati caricati, mentre il metodo **CreateDefault2** carica solo i comandi necessari per ospitare PowerShell (i comandi del modulo Microsoft. PowerShell. Core).</span><span class="sxs-lookup"><span data-stu-id="847ef-109">The **CreateDefault** method creates an **InitialSessionState** with all of the built-in commands loaded, while the **CreateDefault2** method loads only the commands required to host PowerShell (the commands from the Microsoft.PowerShell.Core module).</span></span>

<span data-ttu-id="847ef-110">Se si desidera limitare ulteriormente i comandi disponibili nell'applicazione host, è necessario creare un spazio vincolato.</span><span class="sxs-lookup"><span data-stu-id="847ef-110">If you want to further limit the commands available in your host application you need to create a constrained runspace.</span></span>
<span data-ttu-id="847ef-111">Per informazioni, vedere [creazione di un spazio vincolato](creating-a-constrained-runspace.md).</span><span class="sxs-lookup"><span data-stu-id="847ef-111">For information, see [Creating a constrained runspace](creating-a-constrained-runspace.md).</span></span>

<span data-ttu-id="847ef-112">Il codice seguente illustra come creare un **InitialSessionState**, assegnarlo a un spazio, aggiungere comandi alla pipeline in tale spazio e richiamare i comandi.</span><span class="sxs-lookup"><span data-stu-id="847ef-112">The following code shows how to create an **InitialSessionState**, assign it to a runspace, add commands to the pipeline in that runspace, and invoke the commands.</span></span>
<span data-ttu-id="847ef-113">Per ulteriori informazioni sull'aggiunta e la chiamata di comandi, vedere [aggiunta e richiamo di comandi](adding-and-invoking-commands.md).</span><span class="sxs-lookup"><span data-stu-id="847ef-113">For more information about adding and invoking commands, see [Adding and invoking commands](adding-and-invoking-commands.md).</span></span>

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

      // Call the PowerShell.Create() method to create the PowerShell object,
      // and then specify the runspace and commands to the pipeline.
      // and create the command pipeline.
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

## <a name="see-also"></a><span data-ttu-id="847ef-114">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="847ef-114">See Also</span></span>

[<span data-ttu-id="847ef-115">Creazione di un spazio vincolato</span><span class="sxs-lookup"><span data-stu-id="847ef-115">Creating a constrained runspace</span></span>](creating-a-constrained-runspace.md)

[<span data-ttu-id="847ef-116">Aggiunta e richiamo di comandi</span><span class="sxs-lookup"><span data-stu-id="847ef-116">Adding and invoking commands</span></span>](adding-and-invoking-commands.md)
