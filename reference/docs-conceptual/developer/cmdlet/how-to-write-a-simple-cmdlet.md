---
title: Come scrivere un semplice cmdlet | Microsoft Docs
ms.custom: ''
ms.date: 01/15/2019
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 137543d8-0012-4cba-bcd6-98b25aac83bb
caps.latest.revision: 9
ms.openlocfilehash: 8271512d06047f3ff5e45f81d971ffe2c1f6afd7
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/15/2019
ms.locfileid: "72365470"
---
# <a name="how-to-write-a-cmdlet"></a>Come scrivere un cmdlet

Questo articolo illustra come scrivere un cmdlet. Il cmdlet `Send-Greeting` accetta un solo nome utente come input e quindi scrive un messaggio di saluto per tale utente. Sebbene il cmdlet non esegua molte operazioni, in questo esempio vengono illustrate le sezioni principali di un cmdlet.

## <a name="steps-to-write-a-cmdlet"></a>Passaggi per scrivere un cmdlet

1. Per dichiarare la classe come cmdlet, usare l'attributo **cmdlet** . L'attributo **cmdlet** specifica il verbo e il sostantivo per il nome del cmdlet.

   Per ulteriori informazioni sull'attributo **cmdlet** , vedere [dichiarazione CmdletAttribute](cmdlet-attribute-declaration.md).

2. Specificare il nome della classe.

3. Specifica che il cmdlet deriva da una delle classi seguenti:

   * [System. Management. Automation. cmdlet](/dotnet/api/System.Management.Automation.Cmdlet)
   * [System. Management. Automation. PSCmdlet](/dotnet/api/System.Management.Automation.PSCmdlet)

4. Per definire i parametri per il cmdlet, usare l'attributo **Parameter** . In questo caso, viene specificato un solo parametro obbligatorio.

   Per ulteriori informazioni sull'attributo **Parameter** , vedere [dichiarazione ParameterAttribute](parameter-attribute-declaration.md).

5. Eseguire l'override del metodo di elaborazione dell'input che elabora l'input. In questo caso, viene eseguito l'override del metodo [System. Management. Automation. cmdlet. ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) .

6. Per scrivere il messaggio introduttivo, usare il metodo [System. Management. Automation. cmdlet. WriteObject](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject).
   Il saluto viene visualizzato nel formato seguente:

   ```Output
   Hello <UserName>!
   ```

## <a name="example"></a>Esempio

```csharp
using System.Management.Automation;  // Windows PowerShell assembly.

namespace SendGreeting
{
  // Declare the class as a cmdlet and specify the
  // appropriate verb and noun for the cmdlet name.
  [Cmdlet(VerbsCommunications.Send, "Greeting")]
  public class SendGreetingCommand : Cmdlet
  {
    // Declare the parameters for the cmdlet.
    [Parameter(Mandatory=true)]
    public string Name
    {
      get { return name; }
      set { name = value; }
    }
    private string name;

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

[System. Management. Automation. cmdlet](/dotnet/api/System.Management.Automation.Cmdlet)

[System. Management. Automation. PSCmdlet](/dotnet/api/System.Management.Automation.PSCmdlet)

[System. Management. Automation. cmdlet. ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord)

[System. Management. Automation. cmdlet. WriteObject](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject)

[Dichiarazione CmdletAttribute](cmdlet-attribute-declaration.md)

[Dichiarazione ParameterAttribute](parameter-attribute-declaration.md)

[Scrittura di un cmdlet di Windows PowerShell](writing-a-windows-powershell-cmdlet.md)