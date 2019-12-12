---
title: Messaggi di conferma | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: a886a26d-7730-4586-aeac-fd3f0bc60b88
caps.latest.revision: 8
ms.openlocfilehash: 229725b5b9f1f0082592dcebe11564fd2f630ce1
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/05/2019
ms.locfileid: "72365730"
---
# <a name="confirmation-messages"></a><span data-ttu-id="faa4f-102">Messaggi di conferma</span><span class="sxs-lookup"><span data-stu-id="faa4f-102">Confirmation Messages</span></span>

<span data-ttu-id="faa4f-103">Ecco diversi messaggi di conferma che possono essere visualizzati a seconda delle varianti dei metodi [System. Management. Automation. cmdlet. ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) e [System. Management. Automation. cmdlet. ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) chiamati.</span><span class="sxs-lookup"><span data-stu-id="faa4f-103">Here are different confirmation messages that can be displayed depending on the variants of the [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) and [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) methods that are called.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="faa4f-104">Per il codice di esempio che illustra come richiedere le conferme, vedere [come richiedere le conferme](./how-to-request-confirmations.md).</span><span class="sxs-lookup"><span data-stu-id="faa4f-104">For sample code that shows how to request confirmations, see [How to Request Confirmations](./how-to-request-confirmations.md).</span></span>

## <a name="specifying-the-resource"></a><span data-ttu-id="faa4f-105">Specifica della risorsa</span><span class="sxs-lookup"><span data-stu-id="faa4f-105">Specifying the Resource</span></span>

<span data-ttu-id="faa4f-106">È possibile specificare la risorsa che sta per essere modificata chiamando [System. Management. Automation. cmdlet. ShouldProcess% 2a? DisplayProperty = metodo FullName](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess?view=powershellsdk-1.1.0) .</span><span class="sxs-lookup"><span data-stu-id="faa4f-106">You can specify the resource that is about to be changed by calling the [System.Management.Automation.Cmdlet.Shouldprocess%2A?Displayproperty=Fullname](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess?view=powershellsdk-1.1.0) method.</span></span> <span data-ttu-id="faa4f-107">In questo caso, è necessario specificare la risorsa usando il parametro `target` del metodo e l'operazione viene aggiunta da Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="faa4f-107">In this case, you supply the resource by using the `target` parameter of the method, and the operation is added by Windows PowerShell.</span></span> <span data-ttu-id="faa4f-108">Nel messaggio seguente, il testo "risorse" è la risorsa su cui si è agito e l'operazione è il nome del comando che effettua la chiamata.</span><span class="sxs-lookup"><span data-stu-id="faa4f-108">In the following message, the text "MyResource" is the resource acted on and the operation is the name of the command that makes the call.</span></span>

```output
Confirm
Are you sure you want to perform this action?
Performing operation "Test-RequestConfirmationTemplate1" on Target "MyResource".
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"):
```

<span data-ttu-id="faa4f-109">Se l'utente seleziona **Sì** o **Sì per tutte** le richieste di conferma, come illustrato nell'esempio seguente, viene eseguita una chiamata al metodo [System. Management. Automation. cmdlet. ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) , che causa la visualizzazione di un secondo messaggio di conferma.</span><span class="sxs-lookup"><span data-stu-id="faa4f-109">If the user selects **Yes** or **Yes to All** to the confirmation request (as shown in the following example), a call to the [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) method is made, which causes a second confirmation message to be displayed.</span></span>

```output
Confirm
Are you sure you want to perform this action?
Performing operation "Test-RequestConfirmationTemplate1" on Target "MyResource".
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"): y

Confirm
Continue with this operation?
[Y] Yes  [N] No  [S] Suspend  [?] Help (default is "Y"):
```

## <a name="specifying-the-operation-and-resource"></a><span data-ttu-id="faa4f-110">Specifica dell'operazione e della risorsa</span><span class="sxs-lookup"><span data-stu-id="faa4f-110">Specifying the Operation and Resource</span></span>

<span data-ttu-id="faa4f-111">È possibile specificare la risorsa che sta per essere modificata e l'operazione che il comando sta per eseguire chiamando [System. Management. Automation. cmdlet. ShouldProcess% 2a? DisplayProperty = metodo FullName](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess?view=powershellsdk-1.1.0) .</span><span class="sxs-lookup"><span data-stu-id="faa4f-111">You can specify the resource that is about to be changed and the operation that the command is about to perform by calling the [System.Management.Automation.Cmdlet.Shouldprocess%2A?Displayproperty=Fullname](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess?view=powershellsdk-1.1.0) method.</span></span> <span data-ttu-id="faa4f-112">In questo caso, è necessario specificare la risorsa utilizzando il parametro `target` e l'operazione utilizzando il parametro `target`.</span><span class="sxs-lookup"><span data-stu-id="faa4f-112">In this case, you supply the resource by using the `target` parameter and the operation by using the `target` parameter.</span></span> <span data-ttu-id="faa4f-113">Nel messaggio seguente, il testo "risorse" è la risorsa su cui si è eseguita e "azione" è l'operazione da eseguire.</span><span class="sxs-lookup"><span data-stu-id="faa4f-113">In the following message, the text "MyResource" is the resource acted on and "MyAction" is the operation to be performed.</span></span>

```output
Confirm
Are you sure you want to perform this action?
Performing operation "MyAction" on Target "MyResource".
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"):
```

<span data-ttu-id="faa4f-114">Se l'utente seleziona **Sì** o **Sì** con il messaggio precedente, viene eseguita una chiamata al metodo [System. Management. Automation. cmdlet. ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) , che causa la visualizzazione di un secondo messaggio di conferma.</span><span class="sxs-lookup"><span data-stu-id="faa4f-114">If the user selects **Yes** or **Yes to All** to the previous message, a call to the [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) method is made, which causes a second confirmation message to be displayed.</span></span>

```output
Confirm
Are you sure you want to perform this action?
Performing operation "MyAction" on Target "MyResource".
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"): y

Confirm
Continue with this operation?
[Y] Yes  [N] No  [S] Suspend  [?] Help (default is "Y"):
```

## <a name="see-also"></a><span data-ttu-id="faa4f-115">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="faa4f-115">See Also</span></span>

[<span data-ttu-id="faa4f-116">Scrittura di un cmdlet di Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="faa4f-116">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
