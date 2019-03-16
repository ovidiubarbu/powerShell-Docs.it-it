---
title: Come richiedere conferme | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f24f77d5-e224-4b62-b128-535e045d333e
caps.latest.revision: 9
ms.openlocfilehash: 19e96b612a8778d82cdbafb528a7ffeb01f15f99
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/16/2019
ms.locfileid: "58058820"
---
# <a name="how-to-request-confirmations"></a><span data-ttu-id="5cc53-102">Come richiedere conferme</span><span class="sxs-lookup"><span data-stu-id="5cc53-102">How to Request Confirmations</span></span>

<span data-ttu-id="5cc53-103">In questo esempio viene illustrato come chiamare le [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) e [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) metodi per richiedere conferme dal prima di eseguire un'azione dell'utente.</span><span class="sxs-lookup"><span data-stu-id="5cc53-103">This example shows how to call the [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) and [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) methods to request confirmations from the user before an action is taken.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="5cc53-104">Per altre informazioni su come Windows PowerShell gestisce queste richieste, vedere [richiesta di conferma](./requesting-confirmation-from-cmdlets.md).</span><span class="sxs-lookup"><span data-stu-id="5cc53-104">For more information about how Windows PowerShell handles these requests, see [Requesting Confirmation](./requesting-confirmation-from-cmdlets.md).</span></span>

## <a name="to-request-confirmation"></a><span data-ttu-id="5cc53-105">Per richiedere conferma</span><span class="sxs-lookup"><span data-stu-id="5cc53-105">To request confirmation</span></span>

1. <span data-ttu-id="5cc53-106">Verificare che il `SupportsShouldProcess` parametro dell'attributo Cmdlet è impostata su `true`.</span><span class="sxs-lookup"><span data-stu-id="5cc53-106">Ensure that the `SupportsShouldProcess` parameter of the Cmdlet attribute is set to `true`.</span></span> <span data-ttu-id="5cc53-107">(Per le funzioni di questo è un parametro dell'attributo CmdletBinding.)</span><span class="sxs-lookup"><span data-stu-id="5cc53-107">(For functions this is a parameter of the CmdletBinding attribute.)</span></span>

    ```csharp
    [Cmdlet(VerbsDiagnostic.Test, "RequestConfirmationTemplate1",
            SupportsShouldProcess = true)]
    ```

2. <span data-ttu-id="5cc53-108">Aggiungere un `Force` parametro al cmdlet in modo che l'utente può eseguire l'override di una richiesta di conferma.</span><span class="sxs-lookup"><span data-stu-id="5cc53-108">Add a `Force` parameter to your cmdlet so that the user can override a confirmation request.</span></span>

    ```csharp
    [Parameter()]
    public SwitchParameter Force
    {
      get { return force; }
      set { force = value; }
    }
    private bool force;
    ```

3. <span data-ttu-id="5cc53-109">Aggiungere un `if` istruzione che usa il valore restituito del [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) metodo per determinare se il [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) viene chiamato il metodo.</span><span class="sxs-lookup"><span data-stu-id="5cc53-109">Add an `if` statement that uses the return value of the [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) method to determine if the [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) method is called.</span></span>

4. <span data-ttu-id="5cc53-110">Aggiungere una seconda `if` istruzione che usa il valore restituito del [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) metodo e il valore della `Force` parametro per determinare se l'operazione deve essere eseguita.</span><span class="sxs-lookup"><span data-stu-id="5cc53-110">Add a second `if` statement that uses the return value of the [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) method and the value of the `Force` parameter to determine whether the operation should be performed.</span></span>

## <a name="example"></a><span data-ttu-id="5cc53-111">Esempio</span><span class="sxs-lookup"><span data-stu-id="5cc53-111">Example</span></span>

<span data-ttu-id="5cc53-112">Nell'esempio di codice seguente, il [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) e [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) metodi vengono chiamati all'interno dell'override del [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) (metodo).</span><span class="sxs-lookup"><span data-stu-id="5cc53-112">In the following code example, the [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) and [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) methods are called from within the override of the [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) method.</span></span> <span data-ttu-id="5cc53-113">Tuttavia, è anche possibile chiamare questi metodi dall'input altri metodi di elaborazione.</span><span class="sxs-lookup"><span data-stu-id="5cc53-113">However, you can also call these methods from the other input processing methods.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="5cc53-114">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="5cc53-114">See Also</span></span>

[<span data-ttu-id="5cc53-115">Scrittura di un cmdlet di Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="5cc53-115">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
