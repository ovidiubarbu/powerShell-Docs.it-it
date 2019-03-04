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
ms.openlocfilehash: 8cfbcacf93733667ffba63a252c86518c0919b57
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/03/2019
ms.locfileid: "56863407"
---
# <a name="how-to-request-confirmations"></a>Come richiedere conferme

In questo esempio viene illustrato come chiamare le [System.Management.Automation.Cmdlet.Shouldprocess*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) e [System.Management.Automation.Cmdlet.Shouldcontinue*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) metodi per richiedere conferme dal prima di eseguire un'azione dell'utente.

> [!IMPORTANT]
> Per altre informazioni su come Windows PowerShell gestisce queste richieste, vedere [richiesta di conferma](./requesting-confirmation-from-cmdlets.md).

## <a name="to-request-confirmation"></a>Per richiedere conferma

1. Verificare che il `SupportsShouldProcess` parametro dell'attributo Cmdlet è impostata su `true`. (Per le funzioni di questo è un parametro dell'attributo CmdletBinding.)

    ```csharp
    [Cmdlet(VerbsDiagnostic.Test, "RequestConfirmationTemplate1",
            SupportsShouldProcess = true)]
    ```

2. Aggiungere un `Force` parametro al cmdlet in modo che l'utente può eseguire l'override di una richiesta di conferma.

    ```csharp
    [Parameter()]
    public SwitchParameter Force
    {
      get { return force; }
      set { force = value; }
    }
    private bool force;
    ```

3. Aggiungere un `if` istruzione che usa il valore restituito del [System.Management.Automation.Cmdlet.Shouldprocess*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) metodo per determinare se il [System.Management.Automation.Cmdlet.Shouldcontinue*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) viene chiamato il metodo.

4. Aggiungere una seconda `if` istruzione che usa il valore restituito del [System.Management.Automation.Cmdlet.Shouldcontinue*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) metodo e il valore della `Force` parametro per determinare se l'operazione deve essere eseguita.

## <a name="example"></a>Esempio

Nell'esempio di codice seguente, il [System.Management.Automation.Cmdlet.Shouldprocess*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) e [System.Management.Automation.Cmdlet.Shouldcontinue*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) metodi vengono chiamati dall'interno di eseguire l'override del [System.Management.Automation.Cmdlet.Processrecord*](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) (metodo). Tuttavia, è anche possibile chiamare questi metodi dall'input altri metodi di elaborazione.

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

## <a name="see-also"></a>Vedere anche

[Scrittura di un cmdlet di Windows PowerShell](./writing-a-windows-powershell-cmdlet.md)
