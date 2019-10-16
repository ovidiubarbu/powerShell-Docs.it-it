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
# <a name="how-to-write-a-cmdlet"></a><span data-ttu-id="058b8-102">Come scrivere un cmdlet</span><span class="sxs-lookup"><span data-stu-id="058b8-102">How to write a cmdlet</span></span>

<span data-ttu-id="058b8-103">Questo articolo illustra come scrivere un cmdlet.</span><span class="sxs-lookup"><span data-stu-id="058b8-103">This article shows how to write a cmdlet.</span></span> <span data-ttu-id="058b8-104">Il cmdlet `Send-Greeting` accetta un solo nome utente come input e quindi scrive un messaggio di saluto per tale utente.</span><span class="sxs-lookup"><span data-stu-id="058b8-104">The `Send-Greeting` cmdlet takes a single user name as input and then writes a greeting to that user.</span></span> <span data-ttu-id="058b8-105">Sebbene il cmdlet non esegua molte operazioni, in questo esempio vengono illustrate le sezioni principali di un cmdlet.</span><span class="sxs-lookup"><span data-stu-id="058b8-105">Although the cmdlet does not do much work, this example demonstrates the major sections of a cmdlet.</span></span>

## <a name="steps-to-write-a-cmdlet"></a><span data-ttu-id="058b8-106">Passaggi per scrivere un cmdlet</span><span class="sxs-lookup"><span data-stu-id="058b8-106">Steps to write a cmdlet</span></span>

1. <span data-ttu-id="058b8-107">Per dichiarare la classe come cmdlet, usare l'attributo **cmdlet** .</span><span class="sxs-lookup"><span data-stu-id="058b8-107">To declare the class as a cmdlet, use the **Cmdlet** attribute.</span></span> <span data-ttu-id="058b8-108">L'attributo **cmdlet** specifica il verbo e il sostantivo per il nome del cmdlet.</span><span class="sxs-lookup"><span data-stu-id="058b8-108">The **Cmdlet** attribute specifies the verb and the noun for the cmdlet name.</span></span>

   <span data-ttu-id="058b8-109">Per ulteriori informazioni sull'attributo **cmdlet** , vedere [dichiarazione CmdletAttribute](cmdlet-attribute-declaration.md).</span><span class="sxs-lookup"><span data-stu-id="058b8-109">For more information about the **Cmdlet** attribute, see [CmdletAttribute Declaration](cmdlet-attribute-declaration.md).</span></span>

2. <span data-ttu-id="058b8-110">Specificare il nome della classe.</span><span class="sxs-lookup"><span data-stu-id="058b8-110">Specify the name of the class.</span></span>

3. <span data-ttu-id="058b8-111">Specifica che il cmdlet deriva da una delle classi seguenti:</span><span class="sxs-lookup"><span data-stu-id="058b8-111">Specify that the cmdlet derives from either of the following classes:</span></span>

   * [<span data-ttu-id="058b8-112">System. Management. Automation. cmdlet</span><span class="sxs-lookup"><span data-stu-id="058b8-112">System.Management.Automation.Cmdlet</span></span>](/dotnet/api/System.Management.Automation.Cmdlet)
   * [<span data-ttu-id="058b8-113">System. Management. Automation. PSCmdlet</span><span class="sxs-lookup"><span data-stu-id="058b8-113">System.Management.Automation.PSCmdlet</span></span>](/dotnet/api/System.Management.Automation.PSCmdlet)

4. <span data-ttu-id="058b8-114">Per definire i parametri per il cmdlet, usare l'attributo **Parameter** .</span><span class="sxs-lookup"><span data-stu-id="058b8-114">To define the parameters for the cmdlet, use the **Parameter** attribute.</span></span> <span data-ttu-id="058b8-115">In questo caso, viene specificato un solo parametro obbligatorio.</span><span class="sxs-lookup"><span data-stu-id="058b8-115">In this case, only one required parameter is specified.</span></span>

   <span data-ttu-id="058b8-116">Per ulteriori informazioni sull'attributo **Parameter** , vedere [dichiarazione ParameterAttribute](parameter-attribute-declaration.md).</span><span class="sxs-lookup"><span data-stu-id="058b8-116">For more information about the **Parameter** attribute, see [ParameterAttribute Declaration](parameter-attribute-declaration.md).</span></span>

5. <span data-ttu-id="058b8-117">Eseguire l'override del metodo di elaborazione dell'input che elabora l'input.</span><span class="sxs-lookup"><span data-stu-id="058b8-117">Override the input processing method that processes the input.</span></span> <span data-ttu-id="058b8-118">In questo caso, viene eseguito l'override del metodo [System. Management. Automation. cmdlet. ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) .</span><span class="sxs-lookup"><span data-stu-id="058b8-118">In this case, the [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) method is overridden.</span></span>

6. <span data-ttu-id="058b8-119">Per scrivere il messaggio introduttivo, usare il metodo [System. Management. Automation. cmdlet. WriteObject](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject).</span><span class="sxs-lookup"><span data-stu-id="058b8-119">To write the greeting, use the method [System.Management.Automation.Cmdlet.WriteObject](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject).</span></span>
   <span data-ttu-id="058b8-120">Il saluto viene visualizzato nel formato seguente:</span><span class="sxs-lookup"><span data-stu-id="058b8-120">The greeting is displayed in the following format:</span></span>

   ```Output
   Hello <UserName>!
   ```

## <a name="example"></a><span data-ttu-id="058b8-121">Esempio</span><span class="sxs-lookup"><span data-stu-id="058b8-121">Example</span></span>

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

## <a name="see-also"></a><span data-ttu-id="058b8-122">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="058b8-122">See also</span></span>

[<span data-ttu-id="058b8-123">System. Management. Automation. cmdlet</span><span class="sxs-lookup"><span data-stu-id="058b8-123">System.Management.Automation.Cmdlet</span></span>](/dotnet/api/System.Management.Automation.Cmdlet)

[<span data-ttu-id="058b8-124">System. Management. Automation. PSCmdlet</span><span class="sxs-lookup"><span data-stu-id="058b8-124">System.Management.Automation.PSCmdlet</span></span>](/dotnet/api/System.Management.Automation.PSCmdlet)

[<span data-ttu-id="058b8-125">System. Management. Automation. cmdlet. ProcessRecord</span><span class="sxs-lookup"><span data-stu-id="058b8-125">System.Management.Automation.Cmdlet.ProcessRecord</span></span>](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord)

[<span data-ttu-id="058b8-126">System. Management. Automation. cmdlet. WriteObject</span><span class="sxs-lookup"><span data-stu-id="058b8-126">System.Management.Automation.Cmdlet.WriteObject</span></span>](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject)

[<span data-ttu-id="058b8-127">Dichiarazione CmdletAttribute</span><span class="sxs-lookup"><span data-stu-id="058b8-127">CmdletAttribute Declaration</span></span>](cmdlet-attribute-declaration.md)

[<span data-ttu-id="058b8-128">Dichiarazione ParameterAttribute</span><span class="sxs-lookup"><span data-stu-id="058b8-128">ParameterAttribute Declaration</span></span>](parameter-attribute-declaration.md)

[<span data-ttu-id="058b8-129">Scrittura di un cmdlet di Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="058b8-129">Writing a Windows PowerShell Cmdlet</span></span>](writing-a-windows-powershell-cmdlet.md)