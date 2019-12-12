---
title: Codice diC#esempio GetProc01 () | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 65094bb7-1972-44b3-b8b0-5f639860b58c
caps.latest.revision: 5
ms.openlocfilehash: 499a688ce5e8daa78baff58c454ad237836bbe48
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/05/2019
ms.locfileid: "74416166"
---
# <a name="getproc01-c-sample-code"></a>Codice di esempio di GetProc01 (C#)

Nel codice seguente viene illustrata l'implementazione del cmdlet di esempio GetProc01. Si noti che il cmdlet è semplificato lasciando il lavoro effettivo del recupero del processo al metodo [System. Diagnostics. Process. GetProcesses *](/dotnet/api/System.Diagnostics.Process.GetProcesses) .

> [!NOTE]
> È possibile scaricare il C# file di origine (getproc01.cs) per questo cmdlet Get-proc utilizzando Microsoft Windows Software Development Kit per i componenti di runtime di Windows Vista e .NET Framework 3,0. Per istruzioni sul download, vedere [come installare Windows PowerShell e scaricare Windows PowerShell SDK](/powershell/scripting/developer/installing-the-windows-powershell-sdk).
>
> I file di origine scaricati sono disponibili nella directory **\<PowerShell samples >** .

## <a name="code-sample"></a>Codice di esempio

[!code-csharp[GetProcessSample01.cs](../../../../powershell-sdk-samples/SDK-2.0/csharp/GetProcessSample01/GetProcessSample01.cs#L11-L126 "GetProcessSample01.cs")]

## <a name="see-also"></a>Vedere anche

[Guida per programmatori di Windows PowerShell](./windows-powershell-programmer-s-guide.md)

[Windows PowerShell SDK](../windows-powershell-reference.md)
