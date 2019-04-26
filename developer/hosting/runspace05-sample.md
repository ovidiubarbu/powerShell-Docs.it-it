---
title: Esempio Runspace05 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 1685cfc4-b32c-4bed-b221-e0c4482db955
caps.latest.revision: 9
ms.openlocfilehash: eb227b5fa5e91f59b6fc99981ff5affca1cf63fd
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62082703"
---
# <a name="runspace05-sample"></a><span data-ttu-id="fbdd2-102">Esempio di Runspace05</span><span class="sxs-lookup"><span data-stu-id="fbdd2-102">Runspace05 Sample</span></span>

<span data-ttu-id="fbdd2-103">Questo esempio viene illustrato come aggiungere uno snap-in per un [System.Management.Automation.Runspaces.Initialsessionstate](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) dell'oggetto in modo che il cmdlet dello snap-in è disponibile quando viene aperto lo spazio di esecuzione.</span><span class="sxs-lookup"><span data-stu-id="fbdd2-103">This sample shows how to add a snap-in to an [System.Management.Automation.Runspaces.Initialsessionstate](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) object so that the cmdlet of the snap-in is available when the runspace is opened.</span></span> <span data-ttu-id="fbdd2-104">Lo snap-in include un cmdlet Get-Proc (definito dal [esempio GetProcessSample01](../cmdlet/getprocesssample01-sample.md)) che viene eseguito in modo sincrono tramite un [System.Management.Automation.Powershell](/dotnet/api/system.management.automation.powershell) oggetto.</span><span class="sxs-lookup"><span data-stu-id="fbdd2-104">The snap-in provides a Get-Proc cmdlet (defined by the [GetProcessSample01 Sample](../cmdlet/getprocesssample01-sample.md)) that is run synchronously by using a [System.Management.Automation.Powershell](/dotnet/api/system.management.automation.powershell) object.</span></span>

## <a name="requirements"></a><span data-ttu-id="fbdd2-105">Requisiti</span><span class="sxs-lookup"><span data-stu-id="fbdd2-105">Requirements</span></span>

<span data-ttu-id="fbdd2-106">Questo esempio richiede Windows PowerShell 2.0.</span><span class="sxs-lookup"><span data-stu-id="fbdd2-106">This sample requires Windows PowerShell 2.0.</span></span>

## <a name="demonstrates"></a><span data-ttu-id="fbdd2-107">Di seguito viene illustrato</span><span class="sxs-lookup"><span data-stu-id="fbdd2-107">Demonstrates</span></span>

<span data-ttu-id="fbdd2-108">In questo esempio viene illustrato quanto segue.</span><span class="sxs-lookup"><span data-stu-id="fbdd2-108">This sample demonstrates the following.</span></span>

- <span data-ttu-id="fbdd2-109">Creazione di un' [System.Management.Automation.Runspaces.Initialsessionstate](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) oggetto.</span><span class="sxs-lookup"><span data-stu-id="fbdd2-109">Creating an [System.Management.Automation.Runspaces.Initialsessionstate](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) object.</span></span>

- <span data-ttu-id="fbdd2-110">Aggiunta dello snap-in per il [System.Management.Automation.Runspaces.Initialsessionstate](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) oggetto.</span><span class="sxs-lookup"><span data-stu-id="fbdd2-110">Adding the snap-in to the [System.Management.Automation.Runspaces.Initialsessionstate](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) object.</span></span>

- <span data-ttu-id="fbdd2-111">Creazione di un [System.Management.Automation.Runspaces.Runspace](/dotnet/api/System.Management.Automation.Runspaces.Runspace) oggetto che usa le [System.Management.Automation.Runspaces.Initialsessionstate](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) oggetto.</span><span class="sxs-lookup"><span data-stu-id="fbdd2-111">Creating a [System.Management.Automation.Runspaces.Runspace](/dotnet/api/System.Management.Automation.Runspaces.Runspace) object that uses the [System.Management.Automation.Runspaces.Initialsessionstate](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) object.</span></span>

- <span data-ttu-id="fbdd2-112">Creazione di un [System.Management.Automation.Powershell](/dotnet/api/system.management.automation.powershell) oggetto che usa lo spazio di esecuzione.</span><span class="sxs-lookup"><span data-stu-id="fbdd2-112">Creating a [System.Management.Automation.Powershell](/dotnet/api/system.management.automation.powershell) object that uses the runspace.</span></span>

- <span data-ttu-id="fbdd2-113">Aggiungere cmdlet get-proc dello snap-in alla pipeline del [System.Management.Automation.Powershell](/dotnet/api/system.management.automation.powershell) oggetto.</span><span class="sxs-lookup"><span data-stu-id="fbdd2-113">Adding the snap-in's get-proc cmdlet to the pipeline of the [System.Management.Automation.Powershell](/dotnet/api/system.management.automation.powershell) object.</span></span>

- <span data-ttu-id="fbdd2-114">Esecuzione del comando in modo sincrono.</span><span class="sxs-lookup"><span data-stu-id="fbdd2-114">Running the command synchronously.</span></span>

- <span data-ttu-id="fbdd2-115">Estrazione di proprietà dal [System.Management.Automation.PSObject](/dotnet/api/System.Management.Automation.PSObject) gli oggetti restituiti dal comando.</span><span class="sxs-lookup"><span data-stu-id="fbdd2-115">Extracting properties from the [System.Management.Automation.PSObject](/dotnet/api/System.Management.Automation.PSObject) objects returned by the command.</span></span>

## <a name="example"></a><span data-ttu-id="fbdd2-116">Esempio</span><span class="sxs-lookup"><span data-stu-id="fbdd2-116">Example</span></span>

<span data-ttu-id="fbdd2-117">Questo esempio viene creato uno spazio di esecuzione che usa un' [System.Management.Automation.Runspaces.Initialsessionstate](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) oggetto per definire gli elementi che sono disponibili quando viene aperto lo spazio di esecuzione.</span><span class="sxs-lookup"><span data-stu-id="fbdd2-117">This sample creates a runspace that uses an [System.Management.Automation.Runspaces.Initialsessionstate](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) object to define the elements that are available when the runspace is opened.</span></span> <span data-ttu-id="fbdd2-118">In questo esempio, uno snap-in che definisce un cmdlet Get-Process viene aggiunto allo stato sessione iniziale.</span><span class="sxs-lookup"><span data-stu-id="fbdd2-118">In this sample, a snap-in that defines a Get-Proc cmdlet is added to the initial session state.</span></span>

```csharp
namespace Microsoft.Samples.PowerShell.Runspaces
{
  using System;
  using System.Collections.ObjectModel;
  using System.Management.Automation;
  using System.Management.Automation.Runspaces;
  using PowerShell = System.Management.Automation.PowerShell;

  /// <summary>
  /// This class contains the Main entry point for this host application.
  /// </summary>
  internal class Runspace05
  {
    /// <summary>
    /// This sample shows how to define an initial session state that is
    /// used when creating a runspace. The sample invokes a command from
    /// a Windows PowerShell snap-in that is present in the console file.
    /// </summary>
    /// <param name="args">The parameter is not used.</param>
    /// <remarks>
    /// This sample assumes that user has coppied the GetProcessSample01.dll
    /// that is produced by the GetProcessSample01 sample to the current
    /// directory.
    /// This sample demonstrates the following:
    /// 1. Creating a default initial session state.
    /// 2. Adding a snap-in to the initial session state.
    /// 3. Creating a runspace that uses the initial session state.
    /// 4. Creating a PowerShell object that uses the runspace.
    /// 5. Adding the snap-in's get-proc cmdlet to the PowerShell object.
    /// 6. Using PSObject objects to extract and display properties from
    ///    the objects returned by the cmdlet.
    /// </remarks>
    private static void Main(string[] args)
    {
      // Create the default initial session state. The default initial
      // session state contains all the elements provided by Windows
      // PowerShell.
      InitialSessionState iss = InitialSessionState.CreateDefault();
      PSSnapInException warning;
      iss.ImportPSSnapIn("GetProcPSSnapIn01", out warning);

      // Create a runspace. Notice that no PSHost object is supplied to the
      // CreateRunspace method so the default host is used. See the Host
      // samples for more information on creating your own custom host.
      using (Runspace myRunSpace = RunspaceFactory.CreateRunspace(iss))
      {
        myRunSpace.Open();

        // Create a PowerShell object.
        using (PowerShell powershell = PowerShell.Create())
        {
          // Add the snap-in cmdlet and specify the runspace.
          powershell.AddCommand("GetProcPSSnapIn01\\get-proc");
          powershell.Runspace = myRunSpace;

          // Run the cmdlet synchronously.
          Collection<PSObject> results = powershell.Invoke();

          Console.WriteLine("Process              HandleCount");
          Console.WriteLine("--------------------------------");

          // Display the results.
          foreach (PSObject result in results)
          {
            Console.WriteLine(
                              "{0,-20} {1}",
                              result.Members["ProcessName"].Value,
                              result.Members["HandleCount"].Value);
          }
        }

        // Close the runspace to release any resources.
        myRunSpace.Close();
      }
      System.Console.WriteLine("Hit any key to exit...");
      System.Console.ReadKey();
    }
  }
}
```

## <a name="see-also"></a><span data-ttu-id="fbdd2-119">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="fbdd2-119">See Also</span></span>

[<span data-ttu-id="fbdd2-120">Scrittura di un'applicazione Host di PowerShell di Windows</span><span class="sxs-lookup"><span data-stu-id="fbdd2-120">Writing a Windows PowerShell Host Application</span></span>](./writing-a-windows-powershell-host-application.md)