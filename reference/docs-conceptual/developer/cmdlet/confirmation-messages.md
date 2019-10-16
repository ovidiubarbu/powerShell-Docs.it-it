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
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/15/2019
ms.locfileid: "72365730"
---
# <a name="confirmation-messages"></a>Messaggi di conferma

Ecco diversi messaggi di conferma che possono essere visualizzati a seconda delle varianti dei metodi [System. Management. Automation. cmdlet. ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) e [System. Management. Automation. cmdlet. ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) chiamati.

> [!IMPORTANT]
> Per il codice di esempio che illustra come richiedere le conferme, vedere [come richiedere le conferme](./how-to-request-confirmations.md).

## <a name="specifying-the-resource"></a>Specifica della risorsa

È possibile specificare la risorsa che sta per essere modificata chiamando [System. Management. Automation. cmdlet. ShouldProcess% 2a? DisplayProperty = metodo FullName](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess?view=powershellsdk-1.1.0) . In questo caso, è necessario specificare la risorsa usando il parametro `target` del metodo e l'operazione viene aggiunta da Windows PowerShell. Nel messaggio seguente, il testo "risorse" è la risorsa su cui si è agito e l'operazione è il nome del comando che effettua la chiamata.

```output
Confirm
Are you sure you want to perform this action?
Performing operation "Test-RequestConfirmationTemplate1" on Target "MyResource".
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"):
```

Se l'utente seleziona **Sì** o **Sì per tutte** le richieste di conferma (come illustrato nell'esempio seguente), viene eseguita una chiamata al metodo [System. Management. Automation. cmdlet. ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) , che fa sì che un secondo messaggio di conferma sia visualizzato.

```output
Confirm
Are you sure you want to perform this action?
Performing operation "Test-RequestConfirmationTemplate1" on Target "MyResource".
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"): y

Confirm
Continue with this operation?
[Y] Yes  [N] No  [S] Suspend  [?] Help (default is "Y"):
```

## <a name="specifying-the-operation-and-resource"></a>Specifica dell'operazione e della risorsa

È possibile specificare la risorsa che sta per essere modificata e l'operazione che il comando sta per eseguire chiamando [System. Management. Automation. cmdlet. ShouldProcess% 2a? DisplayProperty = metodo FullName](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess?view=powershellsdk-1.1.0) . In questo caso, è necessario specificare la risorsa utilizzando il parametro `target` e l'operazione utilizzando il parametro `target`. Nel messaggio seguente, il testo "risorse" è la risorsa su cui si è eseguita e "azione" è l'operazione da eseguire.

```output
Confirm
Are you sure you want to perform this action?
Performing operation "MyAction" on Target "MyResource".
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"):
```

Se l'utente seleziona **Sì** o **Sì** con il messaggio precedente, viene eseguita una chiamata al metodo [System. Management. Automation. cmdlet. ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) , che causa la visualizzazione di un secondo messaggio di conferma.

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
