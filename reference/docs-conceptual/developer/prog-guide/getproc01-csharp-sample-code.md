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
ms.openlocfilehash: 06a24266eb8fda6e4f138f1f77ae702f7454e525
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/15/2019
ms.locfileid: "72366800"
---
# <a name="getproc01-c-sample-code"></a>Codice di esempio di GetProc01 (C#)

Nel codice seguente viene illustrata l'implementazione del cmdlet di esempio GetProc01. Si noti che il cmdlet è semplificato lasciando il lavoro effettivo del recupero del processo al metodo [System. Diagnostics. Process. GetProcesses *](/dotnet/api/System.Diagnostics.Process.GetProcesses) .

> [!NOTE]
> È possibile scaricare il C# file di origine (getproc01.cs) per questo cmdlet Get-proc utilizzando Microsoft Windows Software Development Kit per i componenti di runtime di Windows Vista e .NET Framework 3,0. Per istruzioni sul download, vedere [come installare Windows PowerShell e scaricare Windows PowerShell SDK](/powershell/developer/installing-the-windows-powershell-sdk).
>
> I file di origine scaricati sono disponibili nella directory degli **esempi \<PowerShell >** .

## <a name="code-sample"></a>Esempio di codice

[!code-csharp[GetProcessSample01.cs](../../../../powershell-sdk-samples/SDK-2.0/csharp/GetProcessSample01/GetProcessSample01.cs#L11-L126 "GetProcessSample01.cs")]

## <a name="see-also"></a>Vedere anche

[Guida per programmatori di Windows PowerShell](./windows-powershell-programmer-s-guide.md)

[Windows PowerShell SDK](../windows-powershell-reference.md)
