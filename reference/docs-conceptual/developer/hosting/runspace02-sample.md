---
title: Esempio Runspace02 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 7630bb63-ef39-4abd-b795-8000f984c1e5
caps.latest.revision: 9
ms.openlocfilehash: 6352169cffbb8a8bf59a42f79979f5003c150fa4
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/05/2019
ms.locfileid: "72360980"
---
# <a name="runspace02-sample"></a>Esempio di Runspace02

Questo esempio illustra come usare la classe [System. Management. Automation. PowerShell](/dotnet/api/system.management.automation.powershell) per eseguire in modo sincrono i cmdlet [Get-Process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) e [Sort-Object](/powershell/module/Microsoft.PowerShell.Utility/Sort-Object) . Il cmdlet [Get-Process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) restituisce gli oggetti [System. Diagnostics. Process](/dotnet/api/System.Diagnostics.Process) per ogni processo in esecuzione nel computer locale e il `Sort-Object` Ordina gli oggetti in base alla relativa proprietà [System.Diagnostics.Process.ID *](/dotnet/api/System.Diagnostics.Process.Id) . I risultati di questi comandi vengono visualizzati usando un controllo [System. Windows. Forms. DataGridView](/dotnet/api/System.Windows.Forms.DataGridView) .

## <a name="requirements"></a>Requisiti

Questo esempio richiede Windows PowerShell 2,0.

## <a name="demonstrates"></a>Illustra

In questo esempio vengono illustrate le operazioni seguenti.

- Creazione di un oggetto [System. Management. Automation. PowerShell](/dotnet/api/system.management.automation.powershell) per eseguire i comandi.

- Aggiunta di comandi alla pipeline dell'oggetto [System. Management. Automation. PowerShell](/dotnet/api/system.management.automation.powershell) .

- Esecuzione dei comandi in modo sincrono.

- Uso di un controllo [System. Windows. Forms. DataGridView](/dotnet/api/System.Windows.Forms.DataGridView) per visualizzare l'output dei comandi in un Windows Forms Application.

## <a name="example"></a>Esempio

Questo esempio esegue in modo sincrono i cmdlet [Get-Process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) e [Sort-Object](/powershell/module/Microsoft.PowerShell.Utility/Sort-Object) nei spazio predefiniti forniti da Windows PowerShell. L'output viene visualizzato in un form usando un controllo [System. Windows. Forms. DataGridView](/dotnet/api/System.Windows.Forms.DataGridView) .

```csharp
namespace Microsoft.Samples.PowerShell.Runspaces
{
  using System;
  using System.Collections;
  using System.Collections.ObjectModel;
  using System.Management.Automation;
  using System.Management.Automation.Runspaces;
  using System.Windows.Forms;
  using PowerShell = System.Management.Automation.PowerShell;

  /// <summary>
  /// This class contains the Main entry point for this host application.
  /// </summary>
  internal class Runspace02
  {
    /// <summary>
    /// This method creates the form where the output is displayed.
    /// </summary>
    private static void CreateForm()
    {
      Form form = new Form();
      DataGridView grid = new DataGridView();
      form.Controls.Add(grid);
      grid.Dock = DockStyle.Fill;

      // Create a PowerShell object. Creating this object takes care of
      // building all of the other data structures needed to run the command.
      using (PowerShell powershell = PowerShell.Create())
      {
        powershell.AddCommand("get-process").AddCommand("sort-object").AddArgument("ID");
        if (Runspace.DefaultRunspace == null)
        {
          Runspace.DefaultRunspace = powershell.Runspace;
        }

        Collection<PSObject> results = powershell.Invoke();

        // The generic collection needs to be re-wrapped in an ArrayList
        // for data-binding to work.
        ArrayList objects = new ArrayList();
        objects.AddRange(results);

        // The DataGridView will use the PSObjectTypeDescriptor type
        // to retrieve the properties.
        grid.DataSource = objects;
      }

      form.ShowDialog();
    }

    /// <summary>
    /// This sample uses a PowerShell object to run the Get-Process
    /// and Sort-Object cmdlets synchronously. Windows Forms and
    /// data binding are then used to display the results in a
    /// DataGridView control.
    /// </summary>
    /// <param name="args">The parameter is not used.</param>
    /// <remarks>
    /// This sample demonstrates the following:
    /// 1. Creating a PowerShell object.
    /// 2. Adding commands and arguments to the pipeline of
    ///    the PowerShell object.
    /// 3. Running the commands synchronously.
    /// 4. Using a DataGridView control to display the output
    ///    of the commands in a Windows Forms application.
    /// </remarks>
    private static void Main(string[] args)
    {
      Runspace02.CreateForm();
    }
  }
}
```

## <a name="see-also"></a>Vedere anche

[Scrittura di un'applicazione host di Windows PowerShell](./writing-a-windows-powershell-host-application.md)