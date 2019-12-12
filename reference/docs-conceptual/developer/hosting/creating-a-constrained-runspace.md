---
title: Creazione di un spazio vincolato | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 59125e65-7030-40bb-9926-756120b2d952
caps.latest.revision: 5
ms.openlocfilehash: 20ac1e2af8e047b8b572d86a55439676aa8df25c
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/05/2019
ms.locfileid: "72367650"
---
# <a name="creating-a-constrained-runspace"></a>Creazione di uno spazio di esecuzione vincolato

Per motivi di prestazioni o sicurezza, potrebbe essere necessario limitare i comandi di Windows PowerShell disponibili per l'applicazione host. A tale scopo, creare un oggetto [System. Management. Automation. Runspaces. InitialSessionState](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) vuoto chiamando il metodo [System. Management. Automation. Runspaces. InitialSessionState. Create *](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState.Create) , quindi aggiungere solo i comandi che si desidera siano disponibili.

 L'uso di un spazio che carica solo i comandi specificati fornisce prestazioni significativamente migliorate.

 Usare i metodi della classe [System. Management. Automation. Runspaces. Sessionstatecmdletentry](/dotnet/api/System.Management.Automation.Runspaces.SessionStateCmdletEntry) per definire i cmdlet per lo stato della sessione iniziale.

 È anche possibile rendere privati i comandi. I comandi privati possono essere usati dall'applicazione host, ma non dagli utenti dell'applicazione.

## <a name="adding-commands-to-an-empty-runspace"></a>Aggiunta di comandi a un spazio vuoto

 Nell'esempio seguente viene illustrato come creare un InitialSessionState vuoto e aggiungervi comandi.

```csharp
namespace Microsoft.Samples.PowerShell.Runspaces
{
  using System;
  using System.Collections.ObjectModel;
  using System.Management.Automation;
  using System.Management.Automation.Runspaces;
  using Microsoft.PowerShell.Commands;
  using PowerShell = System.Management.Automation.PowerShell;

  /// <summary>
  /// This class contains the Main entry point for the application.
  /// </summary>
  internal class Runspace10b
  {
    /// <summary>
    /// This sample shows how to create an empty initial session state,
    /// how to add commands to the session state, and then how to create a
    /// runspace that has only those two commands. A PowerShell object
    /// is used to run the Get-Command cmdlet to show that only two commands
    /// are available.
    /// </summary>
    /// <param name="args">Parameter not used.</param>
    private static void Main(string[] args)
    {
      // Create an empty InitialSessionState and then add two commands.
      InitialSessionState iss = InitialSessionState.Create();

      // Add the Get-Process and Get-Command cmdlets to the session state.
      SessionStateCmdletEntry ssce1 = new SessionStateCmdletEntry(
                                                            "get-process",
                                                            typeof(GetProcessCommand),
                                                            null);
      iss.Commands.Add(ssce1);

      SessionStateCmdletEntry ssce2 = new SessionStateCmdletEntry(
                                                            "get-command",
                                                            typeof(GetCommandCommand),
                                                            null);
      iss.Commands.Add(ssce2);

      // Create a runspace.
      using (Runspace myRunSpace = RunspaceFactory.CreateRunspace(iss))
      {
        myRunSpace.Open();
        using (PowerShell powershell = PowerShell.Create())
        {
          powershell.Runspace = myRunSpace;

          // Create a pipeline with the Get-Command command.
          powershell.AddCommand("get-command");

          Collection<PSObject> results = powershell.Invoke();

          Console.WriteLine("Verb                 Noun");
          Console.WriteLine("----------------------------");

          // Display each result object.
          foreach (PSObject result in results)
          {
            Console.WriteLine(
                             "{0,-20} {1}",
                             result.Members["verb"].Value,
                             result.Members["Noun"].Value);
          }
        }

        // Close the runspace and release any resources.
        myRunSpace.Close();
      }

      System.Console.WriteLine("Hit any key to exit...");
      System.Console.ReadKey();
    }
  }
}
```

## <a name="making-commands-private"></a>Creazione di comandi privati

 È anche possibile impostare un comando come privato, impostando la proprietà [System. Management. Automation. CommandInfo. Visibility](/dotnet/api/System.Management.Automation.CommandInfo.Visibility) su [System. Management. Automation. SessionStateEntryVisibility](/dotnet/api/System.Management.Automation.SessionStateEntryVisibility) **private**. L'applicazione host e altri comandi possono chiamare tale comando, ma l'utente dell'applicazione non può. Nell'esempio seguente il comando [Get-ChildItem](/powershell/module/Microsoft.PowerShell.Management/Get-ChildItem) è privato.

```csharp
defaultSessionState = InitialSessionState.CreateDefault();
commandIndex = GetIndexOfEntry(defaultSessionState.Commands, "get-childitem");
defaultSessionState.Commands[commandIndex].Visibility = SessionStateEntryVisibility.Private;

this.runspace = RunspaceFactory.CreateRunspace(defaultSessionState);
this.runspace.Open();
```

## <a name="see-also"></a>Vedere anche

 [Creazione di un InitialSessionState](./creating-an-initialsessionstate.md)
