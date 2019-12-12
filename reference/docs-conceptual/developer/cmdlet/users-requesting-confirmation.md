---
title: Utenti che richiedono la conferma | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 6f337498-c534-40ed-968a-09d4d9ca3849
caps.latest.revision: 8
ms.openlocfilehash: ed9ff9fc1668a89e1ac0ceac8f0800a15b349226
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/05/2019
ms.locfileid: "72369250"
---
# <a name="users-requesting-confirmation"></a><span data-ttu-id="79913-102">Richiesta di conferma da parte degli utenti</span><span class="sxs-lookup"><span data-stu-id="79913-102">Users Requesting Confirmation</span></span>

<span data-ttu-id="79913-103">Quando si specifica il valore `true` per il parametro `SupportsShouldProcess` della dichiarazione dell'attributo del cmdlet, gli utenti possono specificare il parametro `Confirm` al prompt dei comandi.</span><span class="sxs-lookup"><span data-stu-id="79913-103">When you specify a value of `true` for the `SupportsShouldProcess` parameter of the Cmdlet attribute declaration, users can specify the `Confirm` parameter at the command prompt.</span></span>

<span data-ttu-id="79913-104">Nell'ambiente predefinito gli utenti possono specificare il `Confirm` parametro o `"-Confirm:$true`, in modo che venga richiesta la conferma quando viene chiamato il metodo [System. Management. Automation. cmdlet. ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) .</span><span class="sxs-lookup"><span data-stu-id="79913-104">In the default environment, users can specify the `Confirm` parameter or `"-Confirm:$true` so that confirmation is requested when the [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) method is called.</span></span> <span data-ttu-id="79913-105">Questo ignora le richieste di conferma [System. Management. Automation. cmdlet. ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) , anche per le operazioni a elevato effetto.</span><span class="sxs-lookup"><span data-stu-id="79913-105">This bypasses [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) confirmation requests, even for high-impact operations.</span></span>

<span data-ttu-id="79913-106">Se `Confirm` viene omesso, la chiamata [System. Management. Automation. cmdlet. ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) richiede la conferma se la variabile `$ConfirmPreference` preferenza è uguale o maggiore dell'impostazione `ConfirmImpact` del cmdlet o del provider.</span><span class="sxs-lookup"><span data-stu-id="79913-106">If `Confirm` is not specified, the [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) call requests confirmation if the `$ConfirmPreference` preference variable is equal to or greater than the `ConfirmImpact` setting of the cmdlet or provider.</span></span> <span data-ttu-id="79913-107">L'impostazione predefinita di `$ConfirmPreference` è alta.</span><span class="sxs-lookup"><span data-stu-id="79913-107">The default setting of `$ConfirmPreference` is High.</span></span> <span data-ttu-id="79913-108">Pertanto, nell'ambiente predefinito, solo i cmdlet e i provider che specificano una conferma di richiesta di azione ad alto impatto.</span><span class="sxs-lookup"><span data-stu-id="79913-108">Therefore, in the default environment, only cmdlets and providers that specify a high-impact action request confirmation.</span></span>

<span data-ttu-id="79913-109">Se `Confirm` è false o se viene specificato `"-Confirm:$false`, la chiamata [System. Management. Automation. cmdlet. ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) richiede la conferma dell'utente e la variabile `$ConfirmPreference` Shell viene ignorata.</span><span class="sxs-lookup"><span data-stu-id="79913-109">If `Confirm` is false or if `"-Confirm:$false` is specified, the [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) call requests confirmation from the user, and the `$ConfirmPreference` shell variable is ignored.</span></span>

## <a name="remarks"></a><span data-ttu-id="79913-110">Osservazioni</span><span class="sxs-lookup"><span data-stu-id="79913-110">Remarks</span></span>

- <span data-ttu-id="79913-111">Per i cmdlet e i provider che specificano `SupportsShouldProcess`, ma non `ConfirmImpact`, tali azioni vengono gestite come azioni di "Media Impact" e non verranno visualizzate per impostazione predefinita.</span><span class="sxs-lookup"><span data-stu-id="79913-111">For cmdlets and providers that specify `SupportsShouldProcess`, but not `ConfirmImpact`, those actions are handled as "medium impact" actions, and they will not prompt by default.</span></span> <span data-ttu-id="79913-112">Il livello di influenza è inferiore rispetto all'impostazione predefinita della variabile di preferenza `$ConfirmPreference`.</span><span class="sxs-lookup"><span data-stu-id="79913-112">Their impact level is less than the default setting of the `$ConfirmPreference` preference variable.</span></span>

- <span data-ttu-id="79913-113">Se l'utente specifica il parametro `Verbose`, riceverà una notifica dell'operazione anche se non viene richiesta la conferma.</span><span class="sxs-lookup"><span data-stu-id="79913-113">If the user specifies the `Verbose` parameter, they will be notified of the operation even if they are not prompted for confirmation.</span></span>

## <a name="see-also"></a><span data-ttu-id="79913-114">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="79913-114">See Also</span></span>

[<span data-ttu-id="79913-115">Scrittura di un cmdlet di Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="79913-115">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
