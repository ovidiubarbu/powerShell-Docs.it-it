---
title: Come richiedere le conferme | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f24f77d5-e224-4b62-b128-535e045d333e
caps.latest.revision: 9
ms.openlocfilehash: 19e96b612a8778d82cdbafb528a7ffeb01f15f99
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/05/2019
ms.locfileid: "72369680"
---
# <a name="how-to-request-confirmations"></a><span data-ttu-id="dd377-102">Come richiedere conferme</span><span class="sxs-lookup"><span data-stu-id="dd377-102">How to Request Confirmations</span></span>

<span data-ttu-id="dd377-103">Questo esempio illustra come chiamare i metodi [System. Management. Automation. cmdlet. ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) e [System. Management. Automation. cmdlet. ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) per richiedere le conferme dell'utente prima che venga eseguita un'azione.</span><span class="sxs-lookup"><span data-stu-id="dd377-103">This example shows how to call the [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) and [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) methods to request confirmations from the user before an action is taken.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="dd377-104">Per ulteriori informazioni sul modo in cui Windows PowerShell gestisce queste richieste, vedere [richiesta di conferma](./requesting-confirmation-from-cmdlets.md).</span><span class="sxs-lookup"><span data-stu-id="dd377-104">For more information about how Windows PowerShell handles these requests, see [Requesting Confirmation](./requesting-confirmation-from-cmdlets.md).</span></span>

## <a name="to-request-confirmation"></a><span data-ttu-id="dd377-105">Per richiedere la conferma</span><span class="sxs-lookup"><span data-stu-id="dd377-105">To request confirmation</span></span>

1. <span data-ttu-id="dd377-106">Verificare che il parametro `SupportsShouldProcess` dell'attributo cmdlet sia impostato su `true`.</span><span class="sxs-lookup"><span data-stu-id="dd377-106">Ensure that the `SupportsShouldProcess` parameter of the Cmdlet attribute is set to `true`.</span></span> <span data-ttu-id="dd377-107">(Per le funzioni si tratta di un parametro dell'attributo di cmdlet.)</span><span class="sxs-lookup"><span data-stu-id="dd377-107">(For functions this is a parameter of the CmdletBinding attribute.)</span></span>

    ```csharp
    [Cmdlet(VerbsDiagnostic.Test, "RequestConfirmationTemplate1",
            SupportsShouldProcess = true)]
    ```

2. <span data-ttu-id="dd377-108">Aggiungere un parametro `Force` al cmdlet in modo che l'utente possa eseguire l'override di una richiesta di conferma.</span><span class="sxs-lookup"><span data-stu-id="dd377-108">Add a `Force` parameter to your cmdlet so that the user can override a confirmation request.</span></span>

    ```csharp
    [Parameter()]
    public SwitchParameter Force
    {
      get { return force; }
      set { force = value; }
    }
    private bool force;
    ```

3. <span data-ttu-id="dd377-109">Aggiungere un'istruzione `if` che usa il valore restituito del metodo [System. Management. Automation. cmdlet. ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) per determinare se viene chiamato il metodo [System. Management. Automation. cmdlet. ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) .</span><span class="sxs-lookup"><span data-stu-id="dd377-109">Add an `if` statement that uses the return value of the [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) method to determine if the [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) method is called.</span></span>

4. <span data-ttu-id="dd377-110">Aggiungere una seconda istruzione `if` che usa il valore restituito del metodo [System. Management. Automation. cmdlet. ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) e il valore del parametro `Force` per determinare se l'operazione deve essere eseguita.</span><span class="sxs-lookup"><span data-stu-id="dd377-110">Add a second `if` statement that uses the return value of the [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) method and the value of the `Force` parameter to determine whether the operation should be performed.</span></span>

## <a name="example"></a><span data-ttu-id="dd377-111">Esempio</span><span class="sxs-lookup"><span data-stu-id="dd377-111">Example</span></span>

<span data-ttu-id="dd377-112">Nell'esempio di codice seguente, i metodi [System. Management. Automation. cmdlet. ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) e [System. Management. Automation. cmdlet. ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) vengono chiamati dall'interno dell'override del metodo [System. Management. Automation. cmdlet. ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) .</span><span class="sxs-lookup"><span data-stu-id="dd377-112">In the following code example, the [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) and [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) methods are called from within the override of the [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) method.</span></span> <span data-ttu-id="dd377-113">È tuttavia possibile chiamare questi metodi anche dagli altri metodi di elaborazione degli input.</span><span class="sxs-lookup"><span data-stu-id="dd377-113">However, you can also call these methods from the other input processing methods.</span></span>

```csharp
protected override void ProcessRecord()
{
  if (ShouldProcess("ShouldProcess target"))
  {
    if (Force || ShouldContinue("", ""))
    {
      // Add code that performs the operation.
    }
  }
}
```

## <a name="see-also"></a><span data-ttu-id="dd377-114">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="dd377-114">See Also</span></span>

[<span data-ttu-id="dd377-115">Scrittura di un cmdlet di Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="dd377-115">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
