---
title: Runspace02 (C#) esempio di codice | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 59a7b8b9-f72e-43fd-9a10-77404441a3f2
caps.latest.revision: 6
ms.openlocfilehash: 0a8fc05db74529e2bfb88820b9cfd988245e0aeb
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/03/2019
ms.locfileid: "56854617"
---
# <a name="runspace02-c-code-sample"></a>Codice di esempio di Runspace02 (C#)

Di seguito è riportato il C# codice sorgente per l'esempio Runspace02. Questo esempio Usa la [System.Management.Automation.Runspaceinvoke](/dotnet/api/System.Management.Automation.RunspaceInvoke) classe per eseguire il `Get-Process` cmdlet in modo sincrono. Windows Form e il data binding vengono quindi utilizzati per visualizzare i risultati in un controllo DataGridView

## <a name="code-sample"></a>Esempio di codice

[!code-csharp[Runspace02.cs](../../powershell-sdk-samples/SDK-2.0/csharp/Runspace02/Runspace02.cs#L11-L82 "Runspace02.cs")]

## <a name="see-also"></a>Vedere anche

[Windows PowerShell SDK](../windows-powershell-reference.md)