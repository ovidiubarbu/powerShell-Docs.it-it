---
title: Come scrivere un semplice Cmdlet | Microsoft Docs
ms.custom: ''
ms.date: 01/15/2019
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 137543d8-0012-4cba-bcd6-98b25aac83bb
caps.latest.revision: 9
ms.openlocfilehash: 8271512d06047f3ff5e45f81d971ffe2c1f6afd7
ms.sourcegitcommit: ce46e5098786e19d521b4bf948ff62d2b90bc53e
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/02/2019
ms.locfileid: "57251456"
---
# <a name="how-to-write-a-cmdlet"></a>Come scrivere un cmdlet

Questo articolo illustra come scrivere un cmdlet. Il `Send-Greeting` cmdlet accetta un unico nome utente come input e quindi scrive un messaggio di saluto all'utente. Anche se il cmdlet non esegue la quantità di lavoro, questo esempio illustra le sezioni principali di un cmdlet.

## <a name="steps-to-write-a-cmdlet"></a>Passaggi per scrivere un cmdlet

1. Per dichiarare la classe come un cmdlet, usare il **Cmdlet** attributo. Il **Cmdlet** attributo specifica il verbo e sostantivo per il nome del cmdlet.

   Per altre informazioni sul **Cmdlet** dell'attributo, vedere [dichiarazione CmdletAttribute](cmdlet-attribute-declaration.md).

2. Specificare il nome della classe.

3. Specificare che il cmdlet deriva da una delle classi seguenti:

   * [System.Management.Automation.Cmdlet](/dotnet/api/System.Management.Automation.Cmdlet)
   * [System.Management.Automation.PSCmdlet](/dotnet/api/System.Management.Automation.PSCmdlet)

4. Per definire i parametri del cmdlet, usare il **parametro** attributo. In questo caso, solo uno obbligatorio parametro è specificato.

   Per altre informazioni sul **parametri** dell'attributo, vedere [ParameterAttribute dichiarazione](parameter-attribute-declaration.md).

5. Eseguire l'override di metodo che elabora l'input di elaborazione dell'input. In questo caso, il [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) è sottoposto a override.

6. Per scrivere il messaggio di saluto, usare il metodo [System.Management.Automation.Cmdlet.WriteObject](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject).
   Viene visualizzato il messaggio di saluto nel formato seguente:

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

[System.Management.Automation.Cmdlet](/dotnet/api/System.Management.Automation.Cmdlet)

[System.Management.Automation.PSCmdlet](/dotnet/api/System.Management.Automation.PSCmdlet)

[System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord)

[System.Management.Automation.Cmdlet.WriteObject](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject)

[Dichiarazione CmdletAttribute](cmdlet-attribute-declaration.md)

[Dichiarazione ParameterAttribute](parameter-attribute-declaration.md)

[Scrittura di un cmdlet di Windows PowerShell](writing-a-windows-powershell-cmdlet.md)