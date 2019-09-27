---
title: Aggiunta e richiamo di comandi | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 62be8432-28c1-4ca2-bcdb-d0350163fa8c
caps.latest.revision: 5
ms.openlocfilehash: f776f13fe743a3f5f67de0d94883e3f754040ffc
ms.sourcegitcommit: 4a2cf30351620a58ba95ff5d76b247e601907589
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/27/2019
ms.locfileid: "71323490"
---
# <a name="adding-and-invoking-commands"></a>Aggiunta e richiamo dei comandi

Dopo aver creato un spazio, è possibile aggiungere PowerShellcommands e script di Windows a una pipeline, quindi richiamare la pipeline in modo sincrono o asincrono.

## <a name="creating-a-pipeline"></a>Creazione di una pipeline

 La classe [System. Management. Automation. PowerShell](/dotnet/api/system.management.automation.powershell) fornisce diversi metodi per aggiungere comandi, parametri e script alla pipeline. È possibile richiamare la pipeline in modo sincrono chiamando un overload del metodo [System. Management. Automation. PowerShell. Invoke *](/dotnet/api/System.Management.Automation.PowerShell.Invoke) o in modo asincrono chiamando un overload di [System. Management. Automation. PowerShell. BeginInvoke *](/dotnet/api/System.Management.Automation.PowerShell.BeginInvoke) e quindi il metodo [System. Management. Automation. PowerShell. EndInvoke *](/dotnet/api/System.Management.Automation.PowerShell.EndInvoke) .

### <a name="addcommand"></a>AddCommand

1. Creare un oggetto [System. Management. Automation. PowerShell](/dotnet/api/system.management.automation.powershell) .

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

 Se si chiama il metodo [System. Management. Automation. PowerShell. AddCommand *](/dotnet/api/System.Management.Automation.PowerShell.AddCommand) più di una volta prima di chiamare il metodo [System. Management. Automation. PowerShell. Invoke *](/dotnet/api/System.Management.Automation.PowerShell.Invoke) , il risultato del primo comando viene reindirizzato al secondo e così via. Se non si vuole inviare tramite pipe il risultato di un comando precedente a un comando, aggiungerlo chiamando [System. Management. Automation. PowerShell. AddStatement *](/dotnet/api/System.Management.Automation.PowerShell.AddStatement) .

### <a name="addparameter"></a>AddParameter

 Nell'esempio precedente viene eseguito un unico comando senza parametri. È possibile aggiungere parametri al comando usando il metodo [System. Management. Automation. PSCommand. AddParameter *](/dotnet/api/System.Management.Automation.PSCommand.AddParameter) , ad esempio, il codice seguente ottiene un elenco di tutti i processi denominati `PowerShell` in esecuzione nel computer.

```csharp
PowerShell.Create().AddCommand("Get-Process")
                   .AddParameter("Name", "PowerShell")
                   .Invoke();
```

 È possibile aggiungere altri parametri chiamando [System. Management. Automation. PSCommand. AddParameter *](/dotnet/api/System.Management.Automation.PSCommand.AddParameter) ripetutamente.

```csharp
PowerShell.Create().AddCommand("Get-Process")
                   .AddParameter("Name", "PowerShell")
                   .AddParameter("Id", "12768")
                   .Invoke();
```

 È anche possibile aggiungere un dizionario di nomi e valori di parametro chiamando il metodo [System. Management. Automation. PowerShell. AddParameters *](/dotnet/api/System.Management.Automation.PowerShell.AddParameters) .

```csharp
IDictionary parameters = new Dictionary<String, String>();
parameters.Add("Name", "PowerShell");

parameters.Add("Id", "12768");
PowerShell.Create().AddCommand("Get-Process")
   .AddParameters(parameters)
      .Invoke()

```

### <a name="addstatement"></a>AddStatement

 È possibile simulare la suddivisione in batch usando il metodo [System. Management. Automation. PowerShell. AddStatement *](/dotnet/api/System.Management.Automation.PowerShell.AddStatement) , che aggiunge un'altra istruzione alla fine della pipeline. il codice seguente ottiene un elenco di processi in esecuzione con il `PowerShell`nome e Ottiene quindi l'elenco dei servizi in esecuzione.

```csharp
PowerShell ps = PowerShell.Create();
ps.AddCommand("Get-Process").AddParameter("Name", "PowerShell");
ps.AddStatement().AddCommand("Get-Service");
ps.Invoke();
```

### <a name="addscript"></a>AddScript

 È possibile eseguire uno script esistente chiamando il metodo [System. Management. Automation. PowerShell. AddScript *](/dotnet/api/System.Management.Automation.PowerShell.AddScript) . Nell'esempio seguente viene aggiunto uno script alla pipeline ed eseguito. In questo esempio si presuppone che esista già uno `MyScript.ps1` script denominato in una `D:\PSScripts`cartella denominata.

```csharp
PowerShell ps = PowerShell.Create();
ps.AddScript("D:\PSScripts\MyScript.ps1").Invoke();
```

 Esiste anche una versione del metodo [System. Management. Automation. PowerShell. AddScript *](/dotnet/api/System.Management.Automation.PowerShell.AddScript) che accetta un parametro booleano denominato `useLocalScope`. Se questo parametro è impostato su `true`, lo script viene eseguito nell'ambito locale. Nel codice seguente viene eseguito lo script nell'ambito locale.

```csharp
PowerShell ps = PowerShell.Create();
ps.AddScript(@"D:\PSScripts\MyScript.ps1", true).Invoke();
```

### <a name="invoking-a-pipeline-synchronously"></a>Richiamo di una pipeline in modo sincrono

 Quando si aggiungono elementi alla pipeline, questo viene richiamato. Per richiamare la pipeline in modo sincrono, chiamare un overload del metodo [System. Management. Automation. PowerShell. Invoke *](/dotnet/api/System.Management.Automation.PowerShell.Invoke) . Nell'esempio seguente viene illustrato come richiamare in modo sincrono una pipeline.

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

### <a name="invoking-a-pipeline-asynchronously"></a>Richiamo di una pipeline in modo asincrono

 Si richiama una pipeline in modo asincrono chiamando un overload di [System. Management. Automation. PowerShell. BeginInvoke *](/dotnet/api/System.Management.Automation.PowerShell.BeginInvoke) per creare un oggetto [IAsyncResult](https://msdn.microsoft.com/library/system.iasyncresult\(v=vs.110\).aspx) e quindi chiamando [System. Management. Automation. PowerShell. EndInvoke *](/dotnet/api/System.Management.Automation.PowerShell.EndInvoke) metodo.

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

 [Creazione di un spazio vincolato](./creating-a-constrained-runspace.md)
