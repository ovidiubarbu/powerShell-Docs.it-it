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
# <a name="creating-an-initialsessionstate"></a>Creazione di un InitialSessionState

I comandi di PowerShell vengono eseguiti in un spazio.
Per ospitare PowerShell nell'applicazione, è necessario creare un oggetto [System. Management. Automation. Runspaces. spazio](/dotnet/api/System.Management.Automation.Runspaces.Runspace) .
Ogni spazio dispone di un oggetto [System. Management. Automation. Runspaces. InitialSessionState](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) associato.
InitialSessionState specifica le caratteristiche di spazio, ad esempio i comandi, le variabili e i moduli disponibili per tale spazio.

## <a name="create-a-default-initialsessionstate"></a>Creare un InitialSessionState predefinito

Per creare un oggetto **InitialSessionState** , è possibile usare i metodi [CreateDefault](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState.CreateDefault) e [CreateDefault2](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState.CreateDefault2) della classe **InitialSessionState** .
Il metodo **CreateDefault** crea un **InitialSessionState** con tutti i comandi incorporati caricati, mentre il metodo **CreateDefault2** carica solo i comandi necessari per ospitare PowerShell (i comandi del modulo Microsoft. PowerShell. Core).

Se si desidera limitare ulteriormente i comandi disponibili nell'applicazione host, è necessario creare un spazio vincolato.
Per informazioni, vedere [creazione di un spazio vincolato](creating-a-constrained-runspace.md).

Il codice seguente illustra come creare un **InitialSessionState**, assegnarlo a un spazio, aggiungere comandi alla pipeline in tale spazio e richiamare i comandi.
Per ulteriori informazioni sull'aggiunta e la chiamata di comandi, vedere [aggiunta e richiamo di comandi](adding-and-invoking-commands.md).

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

## <a name="see-also"></a>Vedere anche

[Creazione di un spazio vincolato](creating-a-constrained-runspace.md)

[Aggiunta e richiamo di comandi](adding-and-invoking-commands.md)
