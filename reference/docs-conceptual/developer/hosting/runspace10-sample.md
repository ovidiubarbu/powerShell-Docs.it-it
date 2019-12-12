---
title: Esempio Runspace10 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 7c265084-e072-46ca-9844-c3c0e275d6b0
caps.latest.revision: 7
ms.openlocfilehash: fdf0036c68b608d254ed928ae9ac58616a856200
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/05/2019
ms.locfileid: "72367340"
---
# <a name="runspace10-sample"></a>Esempio di Runspace10

Questo esempio illustra come creare uno stato di sessione iniziale predefinito, come aggiungere un cmdlet a [System. Management. Automation. Runspaces. InitialSessionState](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState), come creare un spazio che usa lo stato della sessione iniziale e come eseguire il comando usando un oggetto [System. Management. Automation. PowerShell](/dotnet/api/system.management.automation.powershell) .

## <a name="requirements"></a>Requisiti

Questo esempio richiede Windows PowerShell 2,0.

## <a name="demonstrates"></a>Illustra

In questo esempio vengono illustrate le operazioni seguenti.

- Creazione di un oggetto [System. Management. Automation. Runspaces. InitialSessionState](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) .

- Aggiunta di un cmdlet (definito dall'applicazione host) all'oggetto [System. Management. Automation. Runspaces. InitialSessionState](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) .

- Creazione di un oggetto [System. Management. Automation. Runspaces. spazio](/dotnet/api/System.Management.Automation.Runspaces.Runspace) che utilizza l'oggetto.

- Creazione di un oggetto [System. Management. Automation. PowerShell](/dotnet/api/system.management.automation.powershell) che usa l'oggetto [System. Management. Automation. Runspaces. spazio](/dotnet/api/System.Management.Automation.Runspaces.Runspace) .

- Aggiunta del comando alla pipeline dell'oggetto [System. Management. Automation. PowerShell](/dotnet/api/system.management.automation.powershell) .

- Estrazione delle proprietà dagli oggetti [System. Management. Automation. PSObject](/dotnet/api/System.Management.Automation.PSObject) restituiti dal comando.

## <a name="example"></a>Esempio

Questo esempio crea un spazio che usa un oggetto [System. Management. Automation. Runspaces. InitialSessionState](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) per definire gli elementi disponibili quando viene aperto il spazio. In questo esempio, il cmdlet Get-proc (definito dall'applicazione host) viene aggiunto allo stato della sessione iniziale e il cmdlet viene eseguito in modo sincrono tramite un oggetto [System. Management. Automation. PowerShell](/dotnet/api/system.management.automation.powershell) .

```csharp
namespace Microsoft.Samples.PowerShell.Runspaces
{
  using System;
  using System.Collections.Generic;
  using System.Collections.ObjectModel;
  using System.Diagnostics;
  using System.Management.Automation;
  using System.Management.Automation.Runspaces;
  using PowerShell = System.Management.Automation.PowerShell;

  #region GetProcCommand

  /// <summary>
  /// Class that implements the GetProcCommand.
  /// </summary>
  [Cmdlet(VerbsCommon.Get, "Proc")]
  public class GetProcCommand : Cmdlet
  {
    #region Cmdlet Overrides

    /// <summary>
    /// For each of the requested process names, retrieve and write
    /// the associated processes.
    /// </summary>
    protected override void ProcessRecord()
    {
      // Get the current processes.
      Process[] processes = Process.GetProcesses();

      // Write the processes to the pipeline making them available
      // to the next cmdlet. The second argument (true) tells the
      // system to enumerate the array, and send one process object
      // at a time to the pipeline.
      WriteObject(processes, true);
    }

    #endregion Overrides
  } // End GetProcCommand class.

  #endregion GetProcCommand

  /// <summary>
  /// This class contains the Main entry point for this host application.
  /// </summary>
  internal class Runspace10
  {
    /// <summary>
    /// This sample shows how to create a default initial session state, how to add
    /// add a cmdlet to the InitialSessionState object, and then how to create
    /// a Runspace object.
    /// </summary>
    /// <param name="args">Parameter is not used.</param>
    /// This sample demonstrates:
    /// 1. Creating an InitialSessionState object.
    /// 2. Adding a cmdlet to the InitialSessionState object.
    /// 3. Creating a runspace that uses the InitialSessionState object.
    /// 4. Creating a PowerShell object that uses the Runspace object.
    /// 5. Running the added command synchronously.
    /// 6. Working with PSObject objects to extract properties
    ///    from the objects returned by the pipeline.
    private static void Main(string[] args)
    {
      // Create a default InitialSessionState object. The default
      // InitialSessionState object contains all the elements provided
      // by Windows PowerShell.
      InitialSessionState iss = InitialSessionState.CreateDefault();

      // Add the get-proc cmdlet to the InitialSessionState object.
      SessionStateCmdletEntry ssce = new SessionStateCmdletEntry("get-proc", typeof(GetProcCommand), null);
      iss.Commands.Add(ssce);

      // Create a Runspace object that uses the InitialSessionState object.
      // Notice that no PSHost object is specified, so the default host is used.
      // See the Hosting samples for information on creating your own custom host.
      using (Runspace myRunSpace = RunspaceFactory.CreateRunspace(iss))
      {
        myRunSpace.Open();

        using (PowerShell powershell = PowerShell.Create())
        {
          powershell.Runspace = myRunSpace;

          // Add the get-proc cmdlet to the pipeline of the PowerShell object.
          powershell.AddCommand("get-proc");

          Collection<PSObject> results = powershell.Invoke();

          Console.WriteLine("Process              HandleCount");
          Console.WriteLine("--------------------------------");

          // Display the output of the pipeline.
          foreach (PSObject result in results)
          {
             Console.WriteLine(
                               "{0,-20} {1}",
                               result.Members["ProcessName"].Value,
                               result.Members["HandleCount"].Value);
          }
        }

        // Close the runspace to release resources.
        myRunSpace.Close();
      }

      System.Console.WriteLine("Hit any key to exit...");
      System.Console.ReadKey();
    }
  }
}
```

## <a name="see-also"></a>Vedere anche

[Scrittura di un'applicazione host di Windows PowerShell](./writing-a-windows-powershell-host-application.md)