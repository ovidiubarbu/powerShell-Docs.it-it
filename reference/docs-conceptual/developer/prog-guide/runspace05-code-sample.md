---
title: Esempio di codice RunSpace05 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 9688cd69-07ea-4ea0-8822-0a4850bcf86c
caps.latest.revision: 7
ms.openlocfilehash: 979403376c5e694b686aaf77a2cb787d765cb883
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/05/2019
ms.locfileid: "74417937"
---
# <a name="runspace05-code-sample"></a>Codice di esempio di Runspace05

Ecco il codice sorgente per l'esempio Runspace05 descritto in [configurazione di un spazio con RunspaceConfiguration](https://msdn.microsoft.com/en-us/42681d19-2d05-4975-befd-afb1990e79b2). Questo esempio illustra come creare le informazioni di configurazione di spazio, creare un spazio, creare una pipeline con un unico comando e quindi eseguire la pipeline. Il comando eseguito è il cmdlet `Get-Process`.

> [!NOTE]
> È possibile scaricare il C# file di origine (runspace05.cs) utilizzando Microsoft Windows Software Development Kit per i componenti di runtime di Windows Vista e Microsoft .NET Framework 3,0. Per istruzioni sul download, vedere [come installare Windows PowerShell e scaricare Windows PowerShell SDK](/powershell/scripting/developer/installing-the-windows-powershell-sdk).
>
> I file di origine scaricati sono disponibili nella directory **\<PowerShell samples >** .

## <a name="code-sample"></a>Codice di esempio

[!code-csharp[Runspace05.cs](../../../../powershell-sdk-samples/SDK-2.0/csharp/Runspace05/Runspace05.cs#L11-L86 "Runspace05.cs")]

## <a name="see-also"></a>Vedere anche

[Guida per programmatori di Windows PowerShell](./windows-powershell-programmer-s-guide.md)

[Windows PowerShell SDK](../windows-powershell-reference.md)
