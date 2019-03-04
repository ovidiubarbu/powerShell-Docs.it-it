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
ms.openlocfilehash: e4abbb14b31406b845d9b6af6b6372338fb0d926
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/03/2019
ms.locfileid: "56856237"
---
# <a name="users-requesting-confirmation"></a>Richiesta di conferma da parte degli utenti

Quando si specifica un valore `true` per il `SupportsShouldProcess` parametro della dichiarazione di attributo Cmdlet, gli utenti possono specificare la `Confirm` parametro al prompt dei comandi.

Nell'ambiente predefinito, gli utenti possono specificare la `Confirm` parametro oppure `"-Confirm:$true` in modo che la conferma è richiesta quando le [System.Management.Automation.Cmdlet.Shouldprocess*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) viene chiamato il metodo. Ciò consente di ignorare [System.Management.Automation.Cmdlet.Shouldprocess*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) le richieste di conferma, anche per le operazioni a impatto elevato.

Se `Confirm` non viene specificato, il [System.Management.Automation.Cmdlet.Shouldprocess*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) chiamata richiede una conferma se la `$ConfirmPreference` variabile di preferenza è maggiore o uguale al `ConfirmImpact` l'impostazione del cmdlet o provider. L'impostazione predefinita di `$ConfirmPreference` è elevata. Pertanto, nell'ambiente predefinito, solo i cmdlet e provider che specifica un'azione a impatto elevato richiedere conferma.

Se `Confirm` è false o se `"-Confirm:$false` è specificato, il [System.Management.Automation.Cmdlet.Shouldprocess*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) chiamata richiede una conferma da parte dell'utente e il `$ConfirmPreference` variabile della shell viene ignorato.

## <a name="remarks"></a>Osservazioni

- Per i cmdlet e provider che specificano `SupportsShouldProcess`, ma non `ConfirmImpact`, tali operazioni vengono gestite come azioni di "impatto medio", e non verrà più richiesto per impostazione predefinita. Il livello di impatto è minore dell'impostazione predefinita il `$ConfirmPreference` variabile di preferenza.

- Se l'utente specifica il `Verbose` parametro, si riceverà una notifica dell'operazione anche se non è richiesta la conferma.

## <a name="see-also"></a>Vedere anche

[Scrittura di un cmdlet di Windows PowerShell](./writing-a-windows-powershell-cmdlet.md)