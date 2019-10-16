---
title: Esempio Runspace03 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 31df99d7-6954-4fdc-b6f5-06ecba094f43
caps.latest.revision: 8
ms.openlocfilehash: 39495f7813aecf5d0210866fc11f94557fdb0cd9
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/15/2019
ms.locfileid: "72360920"
---
# <a name="runspace03-sample"></a>Esempio di Runspace03

Questo esempio illustra come usare la classe [System. Management. Automation. PowerShell](/dotnet/api/system.management.automation.powershell) per eseguire uno script in modo sincrono e come gestire errori non fatali. Lo script riceve un elenco di nomi di processo e quindi recupera tali processi. I risultati dello script, compresi gli errori non fatali che si sono generati durante l'esecuzione dello script, vengono visualizzati in una finestra della console.

## <a name="requirements"></a>Requisiti

Questo esempio richiede Windows PowerShell 2,0.

## <a name="demonstrates"></a>Dimostra

In questo esempio vengono illustrate le operazioni seguenti.

- Creazione di un oggetto [System. Management. Automation. PowerShell](/dotnet/api/system.management.automation.powershell) per eseguire uno script.

- Aggiunta di uno script alla pipeline dell'oggetto [System. Management. Automation. PowerShell](/dotnet/api/system.management.automation.powershell) .

- Passaggio di oggetti di input allo script dal programma chiamante.

- Esecuzione dello script in modo sincrono.

- Uso di oggetti [System. Management. Automation. PSObject](/dotnet/api/System.Management.Automation.PSObject) per estrarre e visualizzare le proprietà dagli oggetti restituiti dallo script.

- Recupero e visualizzazione dei record di errore generati durante l'esecuzione dello script.

## <a name="example"></a>Esempio

Questo esempio esegue uno script in modo sincrono nei spazio predefiniti forniti da Windows PowerShell. L'output dello script e gli eventuali errori non fatali generati vengono visualizzati in una finestra della console.

```csharp
namespace Microsoft.Samples.PowerShell.Runspaces
{
  using System;
  using System.Collections;
  using System.Management.Automation;
  using System.Management.Automation.Runspaces;
  using PowerShell = System.Management.Automation.PowerShell;

  /// <summary>
  /// This class contains the Main entry point for this host application.
  /// </summary>
  internal class Runspace03
  {
    /// <summary>
    /// This sample shows how to use the PowerShell class to run a
    /// script that retrieves process information for the list of
    /// process names passed to the script. It shows how to pass input
    /// objects to a script and how to retrieve error objects as well
    /// as the output objects.
    /// </summary>
    /// <param name="args">Parameter not used.</param>
    /// <remarks>
    /// This sample demonstrates the following:
    /// 1. Creating a PowerSHell object to run a script.
    /// 2. Adding a script to the pipeline of the PowerShell object.
    /// 3. Passing input objects to the script from the calling program.
    /// 4. Running the script synchronously.
    /// 5. Using PSObject objects to extract and display properties from
    ///    the objects returned by the script.
    /// 6. Retrieving and displaying error records that were generated
    ///    when the script was run.
    /// </remarks>
    private static void Main(string[] args)
    {
      // Define a list of processes to look for.
      string[] processNames = new string[]
      {
        "lsass", "nosuchprocess", "services", "nosuchprocess2"
      };

      // The script to run to get these processes. Input passed
      // to the script will be available in the $input variable.
      string script = "$input | get-process -name {$_}";

      // Create a PowerShell object. Creating this object takes care of
      // building all of the other data structures needed to run the script.
      using (PowerShell powershell = PowerShell.Create())
      {
        powershell.AddScript(script);

        Console.WriteLine("Process              HandleCount");
        Console.WriteLine("--------------------------------");

        // Invoke the script synchronously and display the
        // ProcessName and HandleCount properties of the
        // objects that are returned.
        foreach (PSObject result in powershell.Invoke(processNames))
        {
          Console.WriteLine(
                            "{0,-20} {1}",
                            result.Members["ProcessName"].Value,
                            result.Members["HandleCount"].Value);
        }

        // Process any error records that were generated while running
        //  the script.
        Console.WriteLine("\nThe following non-terminating errors occurred:\n");
        PSDataCollection<ErrorRecord> errors = powershell.Streams.Error;
        if (errors != null && errors.Count > 0)
        {
          foreach (ErrorRecord err in errors)
          {
            System.Console.WriteLine("    error: {0}", err.ToString());
          }
        }
      }

      System.Console.WriteLine("\nHit any key to exit...");
      System.Console.ReadKey();
    }
  }
}
```

## <a name="see-also"></a>Vedere anche

[Scrittura di un'applicazione host di Windows PowerShell](./writing-a-windows-powershell-host-application.md)