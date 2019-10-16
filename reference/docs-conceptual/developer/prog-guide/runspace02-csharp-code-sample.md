---
title: Esempio diC#codice Runspace02 () | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 59a7b8b9-f72e-43fd-9a10-77404441a3f2
caps.latest.revision: 6
ms.openlocfilehash: abf539bc29bd9ccac59bd5957397fbe68951f266
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/15/2019
ms.locfileid: "72366620"
---
# <a name="runspace02-c-code-sample"></a>Codice di esempio di Runspace02 (C#)

Ecco il C# codice sorgente per l'esempio Runspace02. Questo esempio usa la classe [System. Management. Automation. Runspaceinvoke](/dotnet/api/System.Management.Automation.RunspaceInvoke) per eseguire il cmdlet `Get-Process` in modo sincrono. Windows Forms e data binding vengono quindi utilizzati per visualizzare i risultati in un controllo DataGridView

## <a name="code-sample"></a>Esempio di codice

[!code-csharp[Runspace02.cs](../../../../powershell-sdk-samples/SDK-2.0/csharp/Runspace02/Runspace02.cs#L11-L82 "Runspace02.cs")]

## <a name="see-also"></a>Vedere anche

[Windows PowerShell SDK](../windows-powershell-reference.md)
