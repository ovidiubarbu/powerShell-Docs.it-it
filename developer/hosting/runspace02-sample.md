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
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62082720"
---
# <a name="runspace02-sample"></a><span data-ttu-id="c26c3-102">Esempio di Runspace02</span><span class="sxs-lookup"><span data-stu-id="c26c3-102">Runspace02 Sample</span></span>

<span data-ttu-id="c26c3-103">Questo esempio viene illustrato come usare il [System.Management.Automation.Powershell](/dotnet/api/system.management.automation.powershell) classe per eseguire il [Get-Process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) e [Sort-Object](/powershell/module/Microsoft.PowerShell.Utility/Sort-Object) cmdlet in modo sincrono.</span><span class="sxs-lookup"><span data-stu-id="c26c3-103">This sample shows how to use the [System.Management.Automation.Powershell](/dotnet/api/system.management.automation.powershell) class to run the [Get-Process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) and [Sort-Object](/powershell/module/Microsoft.PowerShell.Utility/Sort-Object) cmdlets synchronously.</span></span> <span data-ttu-id="c26c3-104">Il [Get-Process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) cmdlet restituisce [Diagnostics](/dotnet/api/System.Diagnostics.Process) oggetti per ogni processo in esecuzione nel computer locale e il `Sort-Object` Ordina gli oggetti in base alle loro [ System.Diagnostics.Process.Id\*](/dotnet/api/System.Diagnostics.Process.Id) proprietà.</span><span class="sxs-lookup"><span data-stu-id="c26c3-104">The [Get-Process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) cmdlet returns [System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process) objects for each process running on the local computer, and the `Sort-Object` sorts the objects based on their [System.Diagnostics.Process.Id\*](/dotnet/api/System.Diagnostics.Process.Id) property.</span></span> <span data-ttu-id="c26c3-105">I risultati di questi comandi vengono visualizzati utilizzando un [System.Windows.Forms.Datagridview](/dotnet/api/System.Windows.Forms.DataGridView) controllo.</span><span class="sxs-lookup"><span data-stu-id="c26c3-105">The results of these commands is displayed by using a [System.Windows.Forms.Datagridview](/dotnet/api/System.Windows.Forms.DataGridView) control.</span></span>

## <a name="requirements"></a><span data-ttu-id="c26c3-106">Requisiti</span><span class="sxs-lookup"><span data-stu-id="c26c3-106">Requirements</span></span>

<span data-ttu-id="c26c3-107">Questo esempio richiede Windows PowerShell 2.0.</span><span class="sxs-lookup"><span data-stu-id="c26c3-107">This sample requires Windows PowerShell 2.0.</span></span>

## <a name="demonstrates"></a><span data-ttu-id="c26c3-108">Di seguito viene illustrato</span><span class="sxs-lookup"><span data-stu-id="c26c3-108">Demonstrates</span></span>

<span data-ttu-id="c26c3-109">In questo esempio viene illustrato quanto segue.</span><span class="sxs-lookup"><span data-stu-id="c26c3-109">This sample demonstrates the following.</span></span>

- <span data-ttu-id="c26c3-110">Creazione di un [System.Management.Automation.Powershell](/dotnet/api/system.management.automation.powershell) oggetto per eseguire i comandi.</span><span class="sxs-lookup"><span data-stu-id="c26c3-110">Creating a [System.Management.Automation.Powershell](/dotnet/api/system.management.automation.powershell) object to run commands.</span></span>

- <span data-ttu-id="c26c3-111">Aggiunta di comandi per la pipeline della [System.Management.Automation.Powershell](/dotnet/api/system.management.automation.powershell) oggetto.</span><span class="sxs-lookup"><span data-stu-id="c26c3-111">Adding commands to the pipeline of [System.Management.Automation.Powershell](/dotnet/api/system.management.automation.powershell) object.</span></span>

- <span data-ttu-id="c26c3-112">Eseguire i comandi in modo sincrono.</span><span class="sxs-lookup"><span data-stu-id="c26c3-112">Running the commands synchronously.</span></span>

- <span data-ttu-id="c26c3-113">Usando un [System.Windows.Forms.Datagridview](/dotnet/api/System.Windows.Forms.DataGridView) controllo per visualizzare l'output dei comandi in un'applicazione Windows Form.</span><span class="sxs-lookup"><span data-stu-id="c26c3-113">Using a [System.Windows.Forms.Datagridview](/dotnet/api/System.Windows.Forms.DataGridView) control to display the output of the commands in a Windows Forms application.</span></span>

## <a name="example"></a><span data-ttu-id="c26c3-114">Esempio</span><span class="sxs-lookup"><span data-stu-id="c26c3-114">Example</span></span>

<span data-ttu-id="c26c3-115">In questo esempio viene eseguito il [Get-Process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) e [Sort-Object](/powershell/module/Microsoft.PowerShell.Utility/Sort-Object) cmdlet in modo sincrono nello spazio di esecuzione predefiniti fornito da Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="c26c3-115">This sample runs the [Get-Process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) and [Sort-Object](/powershell/module/Microsoft.PowerShell.Utility/Sort-Object) cmdlets synchronously in the default runspace provided by Windows PowerShell.</span></span> <span data-ttu-id="c26c3-116">L'output viene visualizzato in un form utilizzando un [System.Windows.Forms.Datagridview](/dotnet/api/System.Windows.Forms.DataGridView) controllo.</span><span class="sxs-lookup"><span data-stu-id="c26c3-116">The output is displayed in a form using a [System.Windows.Forms.Datagridview](/dotnet/api/System.Windows.Forms.DataGridView) control.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="c26c3-117">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="c26c3-117">See Also</span></span>

[<span data-ttu-id="c26c3-118">Scrittura di un'applicazione Host di PowerShell di Windows</span><span class="sxs-lookup"><span data-stu-id="c26c3-118">Writing a Windows PowerShell Host Application</span></span>](./writing-a-windows-powershell-host-application.md)