---
title: Come richiamare un cmdlet all'interno di un cmdlet | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: efa4dc9c-ddee-46a3-978a-9dbb61e9bb6f
caps.latest.revision: 12
ms.openlocfilehash: 57543a88d04eb66c9d109249a99ddd272b02ef9d
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/05/2019
ms.locfileid: "72365550"
---
# <a name="how-to-invoke-a-cmdlet-from-within-a-cmdlet"></a>Come richiamare un cmdlet da un altro cmdlet

In questo esempio viene illustrato come richiamare un cmdlet da un altro cmdlet, che consente di aggiungere la funzionalità del cmdlet richiamato al cmdlet che si sta sviluppando. In questo esempio viene richiamato il cmdlet `Get-Process` per ottenere i processi in esecuzione nel computer locale. La chiamata al cmdlet `Get-Process` è equivalente al comando seguente. Questo comando recupera tutti i processi i cui nomi iniziano con i caratteri "a" e "t".

```powershell
Get-Process -name [a-t]
```

> [!IMPORTANT]
> È possibile richiamare solo i cmdlet che derivano direttamente dalla classe [System. Management. Automation. cmdlet](/dotnet/api/System.Management.Automation.Cmdlet) . Non è possibile richiamare un cmdlet che deriva dalla classe [System. Management. Automation. PSCmdlet](/dotnet/api/System.Management.Automation.PSCmdlet) .

## <a name="to-invoke-a-cmdlet-from-within-a-cmdlet"></a>Per richiamare un cmdlet all'interno di un cmdlet

1. Verificare che venga fatto riferimento all'assembly che definisce il cmdlet da richiamare e che venga aggiunta l'istruzione `using` appropriata. In questo esempio vengono aggiunti gli spazi dei nomi seguenti.

    ```csharp
    using System.Diagnostics;
    using System.Management.Automation;   // Windows PowerShell assembly.
    using Microsoft.PowerShell.Commands;  // Windows PowerShell assembly.
    ```

2. Nel metodo di elaborazione dell'input del cmdlet creare una nuova istanza del cmdlet da richiamare. In questo esempio viene creato un oggetto di tipo [Microsoft. PowerShell. Commands. Getprocesscommand](/dotnet/api/Microsoft.PowerShell.Commands.GetProcessCommand) insieme alla stringa che contiene gli argomenti utilizzati quando viene richiamato il cmdlet.

    ```csharp
    GetProcessCommand gp = new GetProcessCommand();
    gp.Name = new string[] { "[a-t]*" };
    ```

3. Chiamare il metodo [System. Management. Automation. cmdlet. Invoke *](/dotnet/api/System.Management.Automation.Cmdlet.Invoke) per richiamare il cmdlet `Get-Process`.

    ```csharp
      foreach (Process p in gp.Invoke<Process>())
      {
        Console.WriteLine(p.ToString());
      }
    }
    ```

## <a name="example"></a>Esempio

In questo esempio il cmdlet `Get-Process` viene richiamato dall'interno del metodo [System. Management. Automation. cmdlet. BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) di un cmdlet.

```csharp
using System;
using System.Diagnostics;
using System.Management.Automation;   // Windows PowerShell assembly.
using Microsoft.PowerShell.Commands;  // Windows PowerShell assembly.

namespace SendGreeting
{
  // Declare the class as a cmdlet and specify an
  // appropriate verb and noun for the cmdlet name.
  [Cmdlet(VerbsCommunications.Send, "GreetingInvoke")]
  public class SendGreetingInvokeCommand : Cmdlet
  {
    // Declare the parameters for the cmdlet.
    [Parameter(Mandatory = true)]
    public string Name
    {
      get { return name; }
      set { name = value; }
    }
    private string name;

    // Override the BeginProcessing method to invoke
    // the Get-Process cmdlet.
    protected override void BeginProcessing()
    {
      GetProcessCommand gp = new GetProcessCommand();
      gp.Name = new string[] { "[a-t]*" };
      foreach (Process p in gp.Invoke<Process>())
      {
        Console.WriteLine(p.ToString());
      }
    }

    // Override the ProcessRecord method to process
    // the supplied user name and write out a
    // greeting to the user by calling the WriteObject
    // method.
    protected override void ProcessRecord()
    {
      WriteObject("Hello " + name + "!");
    }
  }
}
```

## <a name="see-also"></a>Vedere anche

[Scrittura di un cmdlet di Windows PowerShell](./writing-a-windows-powershell-cmdlet.md)
