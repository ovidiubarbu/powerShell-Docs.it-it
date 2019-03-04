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
# <a name="confirmation-messages"></a>Messaggi di conferma

Ecco i messaggi di conferma diversi che possono essere visualizzati in base alle varianti del [System.Management.Automation.Cmdlet.Shouldprocess*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) e [ System.Management.Automation.Cmdlet.Shouldcontinue*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) metodi chiamati.

> [!IMPORTANT]
> Per codice di esempio che illustra come richiedere conferme, visitare [come richiesta conferme](./how-to-request-confirmations.md).

## <a name="specifying-the-resource"></a>Definizione di risorsa

È possibile specificare la risorsa che sta per essere modificato chiamando il [System.Management.Automation.Cmdlet.Shouldprocess%2A? Displayproperty = Fullname](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess?view=powershellsdk-1.1.0) (metodo). In questo caso, è fornire la risorsa usando il `target` parametro del metodo e l'operazione viene aggiunto da Windows PowerShell. Il messaggio seguente, il testo "MyResource" è la risorsa azione e l'operazione è il nome del comando che effettua la chiamata.

```output
Confirm
Are you sure you want to perform this action?
Performing operation "Test-RequestConfirmationTemplate1" on Target "MyResource".
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"):
```

Se l'utente seleziona **Yes** oppure **Sì a tutto** per la conferma della richiesta (come illustrato nell'esempio seguente), una chiamata al [System.Management.Automation.Cmdlet.Shouldcontinue*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) metodo viene eseguito, in modo che un secondo messaggio di conferma da visualizzare.

```output
Confirm
Are you sure you want to perform this action?
Performing operation "Test-RequestConfirmationTemplate1" on Target "MyResource".
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"): y

Confirm
Continue with this operation?
[Y] Yes  [N] No  [S] Suspend  [?] Help (default is "Y"):
```

## <a name="specifying-the-operation-and-resource"></a>Specifica l'operazione e risorse

È possibile specificare la risorsa che sta per essere modificato e l'operazione che il comando deve eseguire chiamando il [System.Management.Automation.Cmdlet.Shouldprocess%2A? Displayproperty = Fullname](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess?view=powershellsdk-1.1.0) (metodo). In questo caso, è fornire la risorsa usando il `target` parametro e l'operazione usando il `target` parametro. Il messaggio seguente, il testo "MyResource" è la risorsa risolverlo e "MyAction" è l'operazione da eseguire.

```output
Confirm
Are you sure you want to perform this action?
Performing operation "MyAction" on Target "MyResource".
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"):
```

Se l'utente seleziona **Yes** o **Sì a tutto** al messaggio precedente, una chiamata al [System.Management.Automation.Cmdlet.Shouldcontinue*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) metodo è costituito, determinando in tal modo un secondo messaggio di conferma da visualizzare.

```output
Confirm
Are you sure you want to perform this action?
Performing operation "MyAction" on Target "MyResource".
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"): y

Confirm
Continue with this operation?
[Y] Yes  [N] No  [S] Suspend  [?] Help (default is "Y"):
```

## <a name="see-also"></a>Vedere anche

[Scrittura di un cmdlet di Windows PowerShell](./writing-a-windows-powershell-cmdlet.md)
