---
title: Esempio Runspace01 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 42c1c59c-6da5-4cda-9562-e8059177fee1
caps.latest.revision: 11
ms.openlocfilehash: eec9c616fc6d5240db185f764a3ea2c8f9575d03
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/15/2019
ms.locfileid: "72367420"
---
# <a name="runspace01-sample"></a><span data-ttu-id="f86aa-102">Esempio di Runspace01</span><span class="sxs-lookup"><span data-stu-id="f86aa-102">Runspace01 Sample</span></span>

<span data-ttu-id="f86aa-103">Questo esempio illustra come usare la classe [System. Management. Automation. PowerShell](/dotnet/api/system.management.automation.powershell) per eseguire il cmdlet [Get-Process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) in modo sincrono.</span><span class="sxs-lookup"><span data-stu-id="f86aa-103">This sample shows how to use the [System.Management.Automation.Powershell](/dotnet/api/system.management.automation.powershell) class to run the [Get-Process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) cmdlet synchronously.</span></span> <span data-ttu-id="f86aa-104">Il cmdlet [Get-Process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) restituisce gli oggetti [System. Diagnostics. Process](/dotnet/api/System.Diagnostics.Process) per ogni processo in esecuzione nel computer locale.</span><span class="sxs-lookup"><span data-stu-id="f86aa-104">The [Get-Process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) cmdlet returns [System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process) objects for each process running on the local computer.</span></span> <span data-ttu-id="f86aa-105">I valori delle proprietà [System. Diagnostics. Process. ProcessName \*](/dotnet/api/System.Diagnostics.Process.ProcessName) e [System. Diagnostics. Process. HandleCount \*](/dotnet/api/System.Diagnostics.Process.Handlecount) vengono quindi estratti dagli oggetti restituiti e visualizzati in una finestra della console.</span><span class="sxs-lookup"><span data-stu-id="f86aa-105">The values of the [System.Diagnostics.Process.Processname\*](/dotnet/api/System.Diagnostics.Process.ProcessName) and [System.Diagnostics.Process.Handlecount\*](/dotnet/api/System.Diagnostics.Process.Handlecount) properties are then extracted from the returned objects and displayed in a console window.</span></span>

## <a name="requirements"></a><span data-ttu-id="f86aa-106">Requisiti</span><span class="sxs-lookup"><span data-stu-id="f86aa-106">Requirements</span></span>

 <span data-ttu-id="f86aa-107">Questo esempio richiede Windows PowerShell 2,0.</span><span class="sxs-lookup"><span data-stu-id="f86aa-107">This sample requires Windows PowerShell 2.0.</span></span>

## <a name="demonstrates"></a><span data-ttu-id="f86aa-108">Dimostra</span><span class="sxs-lookup"><span data-stu-id="f86aa-108">Demonstrates</span></span>

- <span data-ttu-id="f86aa-109">Creazione di un oggetto [System. Management. Automation. PowerShell](/dotnet/api/system.management.automation.powershell) per eseguire un comando.</span><span class="sxs-lookup"><span data-stu-id="f86aa-109">Creating a [System.Management.Automation.Powershell](/dotnet/api/system.management.automation.powershell) object to run a command.</span></span>

- <span data-ttu-id="f86aa-110">Aggiunta di un comando alla pipeline dell'oggetto [System. Management. Automation. PowerShell](/dotnet/api/system.management.automation.powershell) .</span><span class="sxs-lookup"><span data-stu-id="f86aa-110">Adding a command to the pipeline of the [System.Management.Automation.Powershell](/dotnet/api/system.management.automation.powershell) object.</span></span>

- <span data-ttu-id="f86aa-111">Esecuzione del comando in modo sincrono.</span><span class="sxs-lookup"><span data-stu-id="f86aa-111">Running the command synchronously.</span></span>

- <span data-ttu-id="f86aa-112">Uso di oggetti [System. Management. Automation. PSObject](/dotnet/api/System.Management.Automation.PSObject) per estrarre le proprietà dagli oggetti restituiti dal comando.</span><span class="sxs-lookup"><span data-stu-id="f86aa-112">Using [System.Management.Automation.PSObject](/dotnet/api/System.Management.Automation.PSObject) objects to extract properties from the objects returned by the command.</span></span>

## <a name="example"></a><span data-ttu-id="f86aa-113">Esempio</span><span class="sxs-lookup"><span data-stu-id="f86aa-113">Example</span></span>

 <span data-ttu-id="f86aa-114">Questo esempio esegue il cmdlet [Get-Process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) in modo sincrono nei spazio predefiniti forniti da Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="f86aa-114">This sample runs the [Get-Process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) cmdlet synchronously in the default runspace provided by Windows PowerShell.</span></span>

```csharp
namespace Microsoft.Samples.PowerShell.Runspaces
{
  using System;
  using System.Management.Automation;
  using PowerShell = System.Management.Automation.PowerShell;

  /// <summary>
  /// This class contains the Main entry point for this host application.
  /// </summary>
  internal class Runspace01
  {
    /// <summary>
    /// This sample uses the PowerShell class to execute
    /// the get-process cmdlet synchronously. The name and
    /// handlecount are then extracted from the PSObjects
    /// returned and displayed.
    /// </summary>
    /// <param name="args">Parameter not used.</param>
    /// <remarks>
    /// This sample demonstrates the following:
    /// 1. Creating a PowerShell object to run a command.
    /// 2. Adding a command to the pipeline of the PowerShell object.
    /// 3. Running the command synchronously.
    /// 4. Using PSObject objects to extract properties from the objects
    ///    returned by the command.
    /// </remarks>
    private static void Main(string[] args)
    {
      // Create a PowerShell object. Creating this object takes care of
      // building all of the other data structures needed to run the command.
      using (PowerShell powershell = PowerShell.Create().AddCommand("get-process"))
      {
        Console.WriteLine("Process              HandleCount");
        Console.WriteLine("--------------------------------");

        // Invoke the command synchronously and display the
        // ProcessName and HandleCount properties of the
        // objects that are returned.
        foreach (PSObject result in powershell.Invoke())
        {
          Console.WriteLine(
                      "{0,-20} {1}",
                      result.Members["ProcessName"].Value,
                      result.Members["HandleCount"].Value);
        }
      }

      System.Console.WriteLine("Hit any key to exit...");
      System.Console.ReadKey();
    }
  }
}
```

## <a name="see-also"></a><span data-ttu-id="f86aa-115">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="f86aa-115">See Also</span></span>