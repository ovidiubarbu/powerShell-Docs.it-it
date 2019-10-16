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
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/15/2019
ms.locfileid: "72365550"
---
# <a name="how-to-invoke-a-cmdlet-from-within-a-cmdlet"></a><span data-ttu-id="20bfc-102">Come richiamare un cmdlet da un altro cmdlet</span><span class="sxs-lookup"><span data-stu-id="20bfc-102">How to Invoke a Cmdlet from Within a Cmdlet</span></span>

<span data-ttu-id="20bfc-103">In questo esempio viene illustrato come richiamare un cmdlet da un altro cmdlet, che consente di aggiungere la funzionalità del cmdlet richiamato al cmdlet che si sta sviluppando.</span><span class="sxs-lookup"><span data-stu-id="20bfc-103">This example shows how to invoke a cmdlet from within another cmdlet, which allows you to add the functionality of the invoked cmdlet to the cmdlet you are developing.</span></span> <span data-ttu-id="20bfc-104">In questo esempio viene richiamato il cmdlet `Get-Process` per ottenere i processi in esecuzione nel computer locale.</span><span class="sxs-lookup"><span data-stu-id="20bfc-104">In this example, the `Get-Process` cmdlet is invoked to get the processes that are running on the local computer.</span></span> <span data-ttu-id="20bfc-105">La chiamata al cmdlet `Get-Process` equivale al comando seguente.</span><span class="sxs-lookup"><span data-stu-id="20bfc-105">The call to the `Get-Process` cmdlet is equivalent to the following command.</span></span> <span data-ttu-id="20bfc-106">Questo comando recupera tutti i processi i cui nomi iniziano con i caratteri "a" e "t".</span><span class="sxs-lookup"><span data-stu-id="20bfc-106">This command retrieves all the processes whose names start with the characters "a" through "t".</span></span>

```powershell
Get-Process -name [a-t]
```

> [!IMPORTANT]
> <span data-ttu-id="20bfc-107">È possibile richiamare solo i cmdlet che derivano direttamente dalla classe [System. Management. Automation. cmdlet](/dotnet/api/System.Management.Automation.Cmdlet) .</span><span class="sxs-lookup"><span data-stu-id="20bfc-107">You can invoke only those cmdlets that derive directly from the [System.Management.Automation.Cmdlet](/dotnet/api/System.Management.Automation.Cmdlet) class.</span></span> <span data-ttu-id="20bfc-108">Non è possibile richiamare un cmdlet che deriva dalla classe [System. Management. Automation. PSCmdlet](/dotnet/api/System.Management.Automation.PSCmdlet) .</span><span class="sxs-lookup"><span data-stu-id="20bfc-108">You cannot invoke a cmdlet that derives from the [System.Management.Automation.PSCmdlet](/dotnet/api/System.Management.Automation.PSCmdlet) class.</span></span>

## <a name="to-invoke-a-cmdlet-from-within-a-cmdlet"></a><span data-ttu-id="20bfc-109">Per richiamare un cmdlet all'interno di un cmdlet</span><span class="sxs-lookup"><span data-stu-id="20bfc-109">To invoke a cmdlet from within a cmdlet</span></span>

1. <span data-ttu-id="20bfc-110">Verificare che venga fatto riferimento all'assembly che definisce il cmdlet da richiamare e che venga aggiunta l'istruzione `using` appropriata.</span><span class="sxs-lookup"><span data-stu-id="20bfc-110">Ensure that the assembly that defines the cmdlet to be invoked is referenced and that the appropriate `using` statement is added.</span></span> <span data-ttu-id="20bfc-111">In questo esempio vengono aggiunti gli spazi dei nomi seguenti.</span><span class="sxs-lookup"><span data-stu-id="20bfc-111">In this example, the following namespaces are added.</span></span>

    ```csharp
    using System.Diagnostics;
    using System.Management.Automation;   // Windows PowerShell assembly.
    using Microsoft.PowerShell.Commands;  // Windows PowerShell assembly.
    ```

2. <span data-ttu-id="20bfc-112">Nel metodo di elaborazione dell'input del cmdlet creare una nuova istanza del cmdlet da richiamare.</span><span class="sxs-lookup"><span data-stu-id="20bfc-112">In the input processing method of the cmdlet, create a new instance of the cmdlet to be invoked.</span></span> <span data-ttu-id="20bfc-113">In questo esempio viene creato un oggetto di tipo [Microsoft. PowerShell. Commands. Getprocesscommand](/dotnet/api/Microsoft.PowerShell.Commands.GetProcessCommand) insieme alla stringa che contiene gli argomenti utilizzati quando viene richiamato il cmdlet.</span><span class="sxs-lookup"><span data-stu-id="20bfc-113">In this example, an object of type [Microsoft.PowerShell.Commands.Getprocesscommand](/dotnet/api/Microsoft.PowerShell.Commands.GetProcessCommand) is created along with the string that contains the arguments that are used when the cmdlet is invoked.</span></span>

    ```csharp
    GetProcessCommand gp = new GetProcessCommand();
    gp.Name = new string[] { "[a-t]*" };
    ```

3. <span data-ttu-id="20bfc-114">Chiamare il metodo [System. Management. Automation. cmdlet. Invoke \*](/dotnet/api/System.Management.Automation.Cmdlet.Invoke) per richiamare il cmdlet `Get-Process`.</span><span class="sxs-lookup"><span data-stu-id="20bfc-114">Call the [System.Management.Automation.Cmdlet.Invoke\*](/dotnet/api/System.Management.Automation.Cmdlet.Invoke) method to invoke the `Get-Process` cmdlet.</span></span>

    ```csharp
      foreach (Process p in gp.Invoke<Process>())
      {
        Console.WriteLine(p.ToString());
      }
    }
    ```

## <a name="example"></a><span data-ttu-id="20bfc-115">Esempio</span><span class="sxs-lookup"><span data-stu-id="20bfc-115">Example</span></span>

<span data-ttu-id="20bfc-116">In questo esempio, il cmdlet `Get-Process` viene richiamato dall'interno del metodo [System. Management. Automation. cmdlet. BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) di un cmdlet.</span><span class="sxs-lookup"><span data-stu-id="20bfc-116">In this example, the `Get-Process` cmdlet is invoked from within the [System.Management.Automation.Cmdlet.BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) method of a cmdlet.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="20bfc-117">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="20bfc-117">See Also</span></span>

[<span data-ttu-id="20bfc-118">Scrittura di un cmdlet di Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="20bfc-118">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
