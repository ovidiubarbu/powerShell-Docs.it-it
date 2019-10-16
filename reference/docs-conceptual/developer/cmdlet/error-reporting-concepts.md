---
title: Concetti relativi alla segnalazione degli errori | Microsoft Docs
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
ms.openlocfilehash: 2f185e415e3effc2cf09a282ca1167e3bcfb7d6a
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/15/2019
ms.locfileid: "72364620"
---
# <a name="error-reporting-concepts"></a>Concetti relativi alla segnalazione di errori

Windows PowerShell fornisce due meccanismi per la segnalazione degli errori: un meccanismo per *terminare gli errori* e un altro meccanismo per gli *errori non fatali*. È importante che il cmdlet segnali correttamente gli errori, in modo che l'applicazione host che esegue i cmdlet possa reagire in modo appropriato.

Il cmdlet deve chiamare il metodo [System. Management. Automation. cmdlet. ThrowTerminatingError *](/dotnet/api/System.Management.Automation.Cmdlet.ThrowTerminatingError) quando si verifica un errore che non consente al cmdlet di continuare a elaborare gli oggetti di input. Il cmdlet deve chiamare il metodo [System. Management. Automation. cmdlet. WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) per segnalare errori non fatali quando il cmdlet può continuare a elaborare gli oggetti di input. Entrambi i metodi forniscono un record di errore che può essere utilizzato dall'applicazione host per analizzare la provocazione dell'errore.

Usare le linee guida seguenti per determinare se un errore è un errore di terminazione o non fatale.

- Un errore è un errore di terminazione se impedisce al cmdlet di continuare a elaborare l'oggetto corrente o di elaborare correttamente eventuali altri oggetti di input, indipendentemente dal contenuto.

- Se non si desidera che il cmdlet continui a elaborare l'oggetto corrente o altri oggetti di input, indipendentemente dal relativo contenuto, si verifica un errore di terminazione.

- Un errore è un errore di terminazione se si verifica in un cmdlet che non accetta o restituisce un oggetto o se si trova in un cmdlet che accetta o restituisce un solo oggetto.

- Un errore è un errore non fatale se si desidera che il cmdlet continui a elaborare l'oggetto corrente e altri oggetti di input.

- Un errore è un errore non fatale se è correlato a un oggetto di input specifico o a un subset di oggetti di input.

## <a name="see-also"></a>Vedere anche

[System. Management. Automation. cmdlet. ThrowTerminatingError *](/dotnet/api/System.Management.Automation.Cmdlet.ThrowTerminatingError)

[System. Management. Automation. cmdlet. WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError)

[Record degli errori di Windows PowerShell](./windows-powershell-error-records.md)

[Scrittura di un cmdlet di Windows PowerShell](./writing-a-windows-powershell-cmdlet.md)
