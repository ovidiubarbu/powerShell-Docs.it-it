---
title: Gli utenti che richiedono conferma | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 6f337498-c534-40ed-968a-09d4d9ca3849
caps.latest.revision: 8
ms.openlocfilehash: ed9ff9fc1668a89e1ac0ceac8f0800a15b349226
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62067219"
---
# <a name="users-requesting-confirmation"></a><span data-ttu-id="230a0-102">Richiesta di conferma da parte degli utenti</span><span class="sxs-lookup"><span data-stu-id="230a0-102">Users Requesting Confirmation</span></span>

<span data-ttu-id="230a0-103">Quando si specifica un valore `true` per il `SupportsShouldProcess` parametro della dichiarazione di attributo Cmdlet, gli utenti possono specificare la `Confirm` parametro al prompt dei comandi.</span><span class="sxs-lookup"><span data-stu-id="230a0-103">When you specify a value of `true` for the `SupportsShouldProcess` parameter of the Cmdlet attribute declaration, users can specify the `Confirm` parameter at the command prompt.</span></span>

<span data-ttu-id="230a0-104">Nell'ambiente predefinito, gli utenti possono specificare la `Confirm` parametro oppure `"-Confirm:$true` in modo che la conferma è richiesta quando le [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) viene chiamato il metodo.</span><span class="sxs-lookup"><span data-stu-id="230a0-104">In the default environment, users can specify the `Confirm` parameter or `"-Confirm:$true` so that confirmation is requested when the [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) method is called.</span></span> <span data-ttu-id="230a0-105">Ciò consente di ignorare [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) le richieste di conferma, anche per le operazioni a impatto elevato.</span><span class="sxs-lookup"><span data-stu-id="230a0-105">This bypasses [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) confirmation requests, even for high-impact operations.</span></span>

<span data-ttu-id="230a0-106">Se `Confirm` non viene specificato, il [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) chiamata richiede una conferma se la `$ConfirmPreference` variabile di preferenza è maggiore o uguale al `ConfirmImpact` l'impostazione del cmdlet o provider.</span><span class="sxs-lookup"><span data-stu-id="230a0-106">If `Confirm` is not specified, the [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) call requests confirmation if the `$ConfirmPreference` preference variable is equal to or greater than the `ConfirmImpact` setting of the cmdlet or provider.</span></span> <span data-ttu-id="230a0-107">L'impostazione predefinita di `$ConfirmPreference` è elevata.</span><span class="sxs-lookup"><span data-stu-id="230a0-107">The default setting of `$ConfirmPreference` is High.</span></span> <span data-ttu-id="230a0-108">Pertanto, nell'ambiente predefinito, solo i cmdlet e provider che specifica un'azione a impatto elevato richiedere conferma.</span><span class="sxs-lookup"><span data-stu-id="230a0-108">Therefore, in the default environment, only cmdlets and providers that specify a high-impact action request confirmation.</span></span>

<span data-ttu-id="230a0-109">Se `Confirm` è false o se `"-Confirm:$false` è specificato, il [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) chiamata richiede una conferma da parte dell'utente e il `$ConfirmPreference` variabile della shell viene ignorato.</span><span class="sxs-lookup"><span data-stu-id="230a0-109">If `Confirm` is false or if `"-Confirm:$false` is specified, the [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) call requests confirmation from the user, and the `$ConfirmPreference` shell variable is ignored.</span></span>

## <a name="remarks"></a><span data-ttu-id="230a0-110">Osservazioni</span><span class="sxs-lookup"><span data-stu-id="230a0-110">Remarks</span></span>

- <span data-ttu-id="230a0-111">Per i cmdlet e provider che specificano `SupportsShouldProcess`, ma non `ConfirmImpact`, tali operazioni vengono gestite come azioni di "impatto medio", e non verrà più richiesto per impostazione predefinita.</span><span class="sxs-lookup"><span data-stu-id="230a0-111">For cmdlets and providers that specify `SupportsShouldProcess`, but not `ConfirmImpact`, those actions are handled as "medium impact" actions, and they will not prompt by default.</span></span> <span data-ttu-id="230a0-112">Il livello di impatto è minore dell'impostazione predefinita il `$ConfirmPreference` variabile di preferenza.</span><span class="sxs-lookup"><span data-stu-id="230a0-112">Their impact level is less than the default setting of the `$ConfirmPreference` preference variable.</span></span>

- <span data-ttu-id="230a0-113">Se l'utente specifica il `Verbose` parametro, si riceverà una notifica dell'operazione anche se non è richiesta la conferma.</span><span class="sxs-lookup"><span data-stu-id="230a0-113">If the user specifies the `Verbose` parameter, they will be notified of the operation even if they are not prompted for confirmation.</span></span>

## <a name="see-also"></a><span data-ttu-id="230a0-114">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="230a0-114">See Also</span></span>

[<span data-ttu-id="230a0-115">Scrittura di un cmdlet di Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="230a0-115">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
