---
title: Concetti di segnalazione degli errori | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- non-terminating errors [PowerShell SDK]
- errors [PowerShell SDK], described
- terminating errors [PowerShell SDK]
- errors [PowerShell SDK]
ms.assetid: 0dce97c0-bd9a-4691-8ca3-e8d5dea902c5
caps.latest.revision: 11
ms.openlocfilehash: aac6b7b6ac8a0fad15194b6d3f92c434524fabdb
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/03/2019
ms.locfileid: "56855077"
---
# <a name="error-reporting-concepts"></a>Concetti relativi alla segnalazione di errori

Windows PowerShell fornisce due meccanismi per la segnalazione degli errori: un meccanismo per la *irreversibili* e un altro meccanismo per *errori non fatali*. È importante per i cmdlet per segnalare gli errori correttamente in modo che l'applicazione host che esegue il cmdlet può rispondere in modo appropriato.

Il cmdlet deve chiamare il [System.Management.Automation.Cmdlet.Throwterminatingerror*](/dotnet/api/System.Management.Automation.Cmdlet.ThrowTerminatingError) metodo quando si verifica un errore che non esiste o non deve consentire al cmdlet di continuare a elaborare gli oggetti di input. Il cmdlet deve chiamare il [System.Management.Automation.Cmdlet.Writeerror*](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) metodo per segnalare errori non fatali quando il cmdlet può continuare a elaborare gli oggetti di input. Entrambi i metodi forniscono un record di errore che l'applicazione host può utilizzare per ricercare la causa dell'errore.

Usare le linee guida seguenti per determinare se un errore è un tipo di terminazione o errore non fatale.

- Un errore è un errore irreversibile se evita che i cmdlet di continuare a elaborare l'oggetto corrente o dall'elaborazione degli oggetti di un'ulteriore input, indipendentemente dal loro contenuto.

- Un errore è un errore se non vuoi cmdlet continuare l'elaborazione degli oggetti di un'ulteriore input, indipendentemente dal loro contenuto o l'oggetto corrente.

- Un errore è un errore se si verifica in un cmdlet che non accettano o restituiscono un oggetto o se si verifica in un cmdlet che accetta o restituisce un solo oggetto.

- Se si desidera che i cmdlet per continuare a elaborare l'oggetto corrente e degli oggetti di un'ulteriore input, un errore è un errore non fatale.

- Se è collegato a un oggetto di input specifico o un subset di oggetti di input, un errore è un errore non fatale.

## <a name="see-also"></a>Vedere anche

[System.Management.Automation.Cmdlet.Throwterminatingerror*](/dotnet/api/System.Management.Automation.Cmdlet.ThrowTerminatingError)

[System.Management.Automation.Cmdlet.Writeerror*](/dotnet/api/System.Management.Automation.Cmdlet.WriteError)

[Record degli errori di PowerShell di Windows](./windows-powershell-error-records.md)

[Scrittura di un cmdlet di Windows PowerShell](./writing-a-windows-powershell-cmdlet.md)
