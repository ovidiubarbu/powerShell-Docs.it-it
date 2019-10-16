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
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/15/2019
ms.locfileid: "72369250"
---
# <a name="users-requesting-confirmation"></a>Richiesta di conferma da parte degli utenti

Quando si specifica il valore `true` per il parametro `SupportsShouldProcess` della dichiarazione dell'attributo del cmdlet, gli utenti possono specificare il parametro `Confirm` al prompt dei comandi.

Nell'ambiente predefinito gli utenti possono specificare il parametro `Confirm` o `"-Confirm:$true` in modo che venga richiesta la conferma quando viene chiamato il metodo [System. Management. Automation. cmdlet. ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) . Questo ignora le richieste di conferma [System. Management. Automation. cmdlet. ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) , anche per le operazioni a elevato effetto.

Se non si specifica `Confirm`, la chiamata [System. Management. Automation. cmdlet. ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) richiede la conferma se la variabile di preferenza `$ConfirmPreference` è uguale o maggiore dell'impostazione `ConfirmImpact` del cmdlet o del provider. L'impostazione predefinita di `$ConfirmPreference` è alta. Pertanto, nell'ambiente predefinito, solo i cmdlet e i provider che specificano una conferma di richiesta di azione ad alto impatto.

Se `Confirm` è false o se viene specificato `"-Confirm:$false`, la chiamata [System. Management. Automation. cmdlet. ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) richiede la conferma dell'utente e la variabile della shell `$ConfirmPreference` viene ignorata.

## <a name="remarks"></a>Osservazioni

- Per i cmdlet e i provider che specificano `SupportsShouldProcess`, ma non `ConfirmImpact`, tali azioni vengono gestite come azioni di "Media Impact" e non verranno visualizzate per impostazione predefinita. Il livello di influenza è inferiore rispetto all'impostazione predefinita della variabile di preferenza `$ConfirmPreference`.

- Se l'utente specifica il parametro `Verbose`, riceverà una notifica dell'operazione anche se non viene richiesta la conferma.

## <a name="see-also"></a>Vedere anche

[Scrittura di un cmdlet di Windows PowerShell](./writing-a-windows-powershell-cmdlet.md)
