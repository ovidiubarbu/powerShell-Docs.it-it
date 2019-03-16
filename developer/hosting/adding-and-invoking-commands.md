---
title: Aggiunta e la chiamata dei comandi | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 62be8432-28c1-4ca2-bcdb-d0350163fa8c
caps.latest.revision: 5
ms.openlocfilehash: 9a01f948c5b474b4f9068030907601543e13cc7e
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/16/2019
ms.locfileid: "58057655"
---
# <a name="adding-and-invoking-commands"></a>Aggiunta e richiamo dei comandi

Dopo aver creato uno spazio di esecuzione, è possibile aggiungere script e PowerShellcommands Windows a una pipeline e quindi richiama la pipeline in modo sincrono o asincrono.

## <a name="creating-a-pipeline"></a>Creazione di una pipeline

 Il [System.Management.Automation.Powershell](/dotnet/api/system.management.automation.powershell) classe fornisce diversi metodi per aggiungere comandi e parametri di script alla pipeline. È possibile richiamare la pipeline in modo sincrono chiamando un overload del [System.Management.Automation.Powershell.Invoke*](/dotnet/api/System.Management.Automation.PowerShell.Invoke) metodo, o in modo asincrono chiamando un overload del [ System.Management.Automation.Powershell.Begininvoke*](/dotnet/api/System.Management.Automation.PowerShell.BeginInvoke) e quindi il [System.Management.Automation.Powershell.Endinvoke*](/dotnet/api/System.Management.Automation.PowerShell.EndInvoke) (metodo).

### <a name="addcommand"></a>AddCommand

1. Creare un [System.Management.Automation.Powershell](/dotnet/api/system.management.automation.powershell) oggetto.

   ```csharp
   PowerShell ps = PowerShell.Create();
   ```

2. Aggiungere il comando che si desidera eseguire.

   ```csharp
   ps.AddCommand("Get-Process");
   ```

3. Richiamare il comando.

   ```csharp
   ps.Invoke();
   ```

 Se si chiama il [System.Management.Automation.Powershell.Addcommand*](/dotnet/api/System.Management.Automation.PowerShell.AddCommand) metodo più volte prima di chiamare le [System.Management.Automation.Powershell.Invoke*](/dotnet/api/System.Management.Automation.PowerShell.Invoke) (metodo), il risultato del primo comando viene reindirizzato al secondo e così via. Se non si desidera inviare tramite pipe il risultato di un comando precedente a un comando, aggiungerlo chiamando il [System.Management.Automation.Powershell.Addstatement*](/dotnet/api/System.Management.Automation.PowerShell.AddStatement) invece.

### <a name="addparameter"></a>AddParameter

 Nell'esempio precedente esegue un comando singolo senza parametri. È possibile aggiungere parametri al comando utilizzando il [System.Management.Automation.Pscommand.Addparameter*](/dotnet/api/System.Management.Automation.PSCommand.AddParameter) metodo, ad esempio, il codice seguente ottiene un elenco di tutti i processi denominati `PowerShell` in esecuzione sul macchina.

```csharp
PowerShell.Create().AddCommand("Get-Process")
                   .AddParameter("Name", "PowerShell")
                   .Invoke();
```

 È possibile aggiungere ulteriori parametri chiamando [System.Management.Automation.Pscommand.Addparameter*](/dotnet/api/System.Management.Automation.PSCommand.AddParameter) ripetutamente.

```csharp
PowerShell.Create().AddCommand("Get-Process")
                   .AddParameter("Name", "PowerShell")
                   .AddParameter("Id", "12768")
                   .Invoke();
```

 È anche possibile aggiungere un dizionario di nomi dei parametri e valori chiamando il [System.Management.Automation.Powershell.Addparameters*](/dotnet/api/System.Management.Automation.PowerShell.AddParameters) (metodo).

```csharp
IDictionary parameters = new Dictionary<String, String>();
parameters.Add("Name", "PowerShell");

parameters.Add("Id", "12768");
PowerShell.Create().AddCommand("Get-Process")
   .AddParameters(parameters)
      .Invoke()

```

### <a name="addstatement"></a>AddStatement

 È possibile simulare l'invio in batch usando il [System.Management.Automation.Powershell.Addstatement*](/dotnet/api/System.Management.Automation.PowerShell.AddStatement) metodo, che aggiunge un'ulteriore istruzione alla fine della pipeline il codice seguente ottiene un elenco di processi in esecuzione con il nome `PowerShell`e quindi Ottiene l'elenco dei servizi in esecuzione.

```csharp
PowerShell ps = PowerShell.Create();
ps.AddCommand("Get-Process").AddParameter("Name", "PowerShell");
ps.AddStatement().AddCommand("Get-Service");
ps.Invoke();
```

### <a name="addscript"></a>AddScript

 È possibile eseguire uno script esistente chiamando il [System.Management.Automation.Powershell.Addscript*](/dotnet/api/System.Management.Automation.PowerShell.AddScript) (metodo). Nell'esempio seguente aggiunge uno script alla pipeline e lo esegue. In questo esempio si presuppone che è già presente uno script denominato `MyScript.ps1` in una cartella denominata `D:\PSScripts`.

```csharp
PowerShell ps = PowerShell.Create();
ps.AddScript("D:\PSScripts\MyScript.ps1").Invoke();
```

 È inoltre disponibile una versione del [System.Management.Automation.Powershell.Addscript*](/dotnet/api/System.Management.Automation.PowerShell.AddScript) metodo che accetta un parametro booleano denominato `useLocalScope`. Se questo parametro è impostato su `true`, quindi lo script viene eseguito nell'ambito locale. Il codice seguente verrà eseguito lo script nell'ambito locale.

```csharp
PowerShell ps = PowerShell.Create();
ps.AddScript(@"D:\PSScripts\MyScript.ps1", true).Invoke();
```

### <a name="invoking-a-pipeline-synchronously"></a>Chiamata in modo sincrono una pipeline

 Dopo aver aggiunto gli elementi alla pipeline, si richiamarlo. Per richiamare la pipeline in modo sincrono, chiamare un overload del [System.Management.Automation.Powershell.Invoke*](/dotnet/api/System.Management.Automation.PowerShell.Invoke) (metodo). Nell'esempio seguente viene illustrato come richiamare in modo sincrono una pipeline.

```csharp
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using System.Management.Automation;

namespace HostPS1e
{
  class HostPS1e
  {
    static void Main(string[] args)
    {
      // Using the PowerShell.Create and AddCommand
      // methods, create a command pipeline.
      PowerShell ps = PowerShell.Create().AddCommand ("Sort-Object");

      // Using the PowerShell.Invoke method, run the command
      // pipeline using the supplied input.
      foreach (PSObject result in ps.Invoke(new int[] { 3, 1, 6, 2, 5, 4 }))
      {
          Console.WriteLine("{0}", result);
      } // End foreach.
    } // End Main.
  } // End HostPS1e.
}
```

### <a name="invoking-a-pipeline-asynchronously"></a>Chiamata di una pipeline in modo asincrono

 Si richiama una pipeline in modo asincrono chiamando un overload del [System.Management.Automation.Powershell.Begininvoke*](/dotnet/api/System.Management.Automation.PowerShell.BeginInvoke) per creare un [IAsyncResult](http://msdn.microsoft.com/library/system.iasyncresult\(v=vs.110\).aspx) e quindi chiamando il [ System.Management.Automation.Powershell.Endinvoke*](/dotnet/api/System.Management.Automation.PowerShell.EndInvoke) (metodo).

 Nell'esempio seguente viene illustrato come richiamare una pipeline in modo asincrono.

```csharp
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using System.Management.Automation;

namespace HostPS3
{
  class HostPS3
  {
    static void Main(string[] args)
    {
      // Use the PowerShell.Create and PowerShell.AddCommand
      // methods to create a command pipeline that includes
      // Get-Process cmdlet. Do not include spaces immediately
      // before or after the cmdlet name as that will cause
      // the command to fail.
      PowerShell ps = PowerShell.Create().AddCommand("Get-Process");

      // Create an IAsyncResult object and call the
      // BeginInvoke method to start running the
      // command pipeline asynchronously.
      IAsyncResult async = ps.BeginInvoke();

      // Using the PowerShell.Invoke method, run the command
      // pipeline using the default runspace.
      foreach (PSObject result in ps.EndInvoke(async))
      {
        Console.WriteLine("{0,-20}{1}",
                result.Members["ProcessName"].Value,
                result.Members["Id"].Value);
      } // End foreach.
      System.Console.WriteLine("Hit any key to exit.");
      System.Console.ReadKey();
    } // End Main.
  } // End HostPS3.
}
```

## <a name="see-also"></a>Vedere anche

 [Creazione di un InitialSessionState](./creating-an-initialsessionstate.md)

 [Creazione di uno spazio di esecuzione vincolata](./creating-a-constrained-runspace.md)
