---
title: I messaggi di conferma | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: a886a26d-7730-4586-aeac-fd3f0bc60b88
caps.latest.revision: 8
ms.openlocfilehash: 75214a3fe4bc019836f75db19fb873bd081f200f
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/03/2019
ms.locfileid: "56861417"
---
# <a name="confirmation-messages"></a><span data-ttu-id="9ea07-102">Messaggi di conferma</span><span class="sxs-lookup"><span data-stu-id="9ea07-102">Confirmation Messages</span></span>

<span data-ttu-id="9ea07-103">Ecco i messaggi di conferma diversi che possono essere visualizzati in base alle varianti del [System.Management.Automation.Cmdlet.Shouldprocess\*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) e [ System.Management.Automation.Cmdlet.Shouldcontinue\*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) metodi chiamati.</span><span class="sxs-lookup"><span data-stu-id="9ea07-103">Here are different confirmation messages that can be displayed depending on the variants of the [System.Management.Automation.Cmdlet.Shouldprocess\*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) and [System.Management.Automation.Cmdlet.Shouldcontinue\*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) methods that are called.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="9ea07-104">Per codice di esempio che illustra come richiedere conferme, visitare [come richiesta conferme](./how-to-request-confirmations.md).</span><span class="sxs-lookup"><span data-stu-id="9ea07-104">For sample code that shows how to request confirmations, see [How to Request Confirmations](./how-to-request-confirmations.md).</span></span>

## <a name="specifying-the-resource"></a><span data-ttu-id="9ea07-105">Definizione di risorsa</span><span class="sxs-lookup"><span data-stu-id="9ea07-105">Specifying the Resource</span></span>

<span data-ttu-id="9ea07-106">È possibile specificare la risorsa che sta per essere modificato chiamando il [System.Management.Automation.Cmdlet.Shouldprocess%2A? Displayproperty = Fullname](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess?view=powershellsdk-1.1.0) (metodo).</span><span class="sxs-lookup"><span data-stu-id="9ea07-106">You can specify the resource that is about to be changed by calling the [System.Management.Automation.Cmdlet.Shouldprocess%2A?Displayproperty=Fullname](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess?view=powershellsdk-1.1.0) method.</span></span> <span data-ttu-id="9ea07-107">In questo caso, è fornire la risorsa usando il `target` parametro del metodo e l'operazione viene aggiunto da Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="9ea07-107">In this case, you supply the resource by using the `target` parameter of the method, and the operation is added by Windows PowerShell.</span></span> <span data-ttu-id="9ea07-108">Il messaggio seguente, il testo "MyResource" è la risorsa azione e l'operazione è il nome del comando che effettua la chiamata.</span><span class="sxs-lookup"><span data-stu-id="9ea07-108">In the following message, the text "MyResource" is the resource acted on and the operation is the name of the command that makes the call.</span></span>

```output
Confirm
Are you sure you want to perform this action?
Performing operation "Test-RequestConfirmationTemplate1" on Target "MyResource".
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"):
```

<span data-ttu-id="9ea07-109">Se l'utente seleziona **Yes** oppure **Sì a tutto** per la conferma della richiesta (come illustrato nell'esempio seguente), una chiamata al [System.Management.Automation.Cmdlet.Shouldcontinue\*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) metodo viene eseguito, in modo che un secondo messaggio di conferma da visualizzare.</span><span class="sxs-lookup"><span data-stu-id="9ea07-109">If the user selects **Yes** or **Yes to All** to the confirmation request (as shown in the following example), a call to the [System.Management.Automation.Cmdlet.Shouldcontinue\*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) method is made, which causes a second confirmation message to be displayed.</span></span>

```output
Confirm
Are you sure you want to perform this action?
Performing operation "Test-RequestConfirmationTemplate1" on Target "MyResource".
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"): y

Confirm
Continue with this operation?
[Y] Yes  [N] No  [S] Suspend  [?] Help (default is "Y"):
```

## <a name="specifying-the-operation-and-resource"></a><span data-ttu-id="9ea07-110">Specifica l'operazione e risorse</span><span class="sxs-lookup"><span data-stu-id="9ea07-110">Specifying the Operation and Resource</span></span>

<span data-ttu-id="9ea07-111">È possibile specificare la risorsa che sta per essere modificato e l'operazione che il comando deve eseguire chiamando il [System.Management.Automation.Cmdlet.Shouldprocess%2A? Displayproperty = Fullname](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess?view=powershellsdk-1.1.0) (metodo).</span><span class="sxs-lookup"><span data-stu-id="9ea07-111">You can specify the resource that is about to be changed and the operation that the command is about to perform by calling the [System.Management.Automation.Cmdlet.Shouldprocess%2A?Displayproperty=Fullname](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess?view=powershellsdk-1.1.0) method.</span></span> <span data-ttu-id="9ea07-112">In questo caso, è fornire la risorsa usando il `target` parametro e l'operazione usando il `target` parametro.</span><span class="sxs-lookup"><span data-stu-id="9ea07-112">In this case, you supply the resource by using the `target` parameter and the operation by using the `target` parameter.</span></span> <span data-ttu-id="9ea07-113">Il messaggio seguente, il testo "MyResource" è la risorsa risolverlo e "MyAction" è l'operazione da eseguire.</span><span class="sxs-lookup"><span data-stu-id="9ea07-113">In the following message, the text "MyResource" is the resource acted on and "MyAction" is the operation to be performed.</span></span>

```output
Confirm
Are you sure you want to perform this action?
Performing operation "MyAction" on Target "MyResource".
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"):
```

<span data-ttu-id="9ea07-114">Se l'utente seleziona **Yes** o **Sì a tutto** al messaggio precedente, una chiamata al [System.Management.Automation.Cmdlet.Shouldcontinue\*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) metodo è costituito, determinando in tal modo un secondo messaggio di conferma da visualizzare.</span><span class="sxs-lookup"><span data-stu-id="9ea07-114">If the user selects **Yes** or **Yes to All** to the previous message, a call to the [System.Management.Automation.Cmdlet.Shouldcontinue\*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) method is made, which causes a second confirmation message to be displayed.</span></span>

```output
Confirm
Are you sure you want to perform this action?
Performing operation "MyAction" on Target "MyResource".
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"): y

Confirm
Continue with this operation?
[Y] Yes  [N] No  [S] Suspend  [?] Help (default is "Y"):
```

## <a name="see-also"></a><span data-ttu-id="9ea07-115">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="9ea07-115">See Also</span></span>

[<span data-ttu-id="9ea07-116">Scrittura di un cmdlet di Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="9ea07-116">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
