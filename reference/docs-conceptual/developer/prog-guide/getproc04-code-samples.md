---
title: Esempi di codice GetProc04 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: c00afd46-758a-4aec-b865-2c9d8f6a17ad
caps.latest.revision: 5
ms.openlocfilehash: 67081528ebe14fbb082091c1b9500de82069b48f
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/15/2019
ms.locfileid: "72360320"
---
# <a name="getproc04-code-samples"></a>Codici di esempio di GetProc04

Ecco gli esempi di codice per il cmdlet di esempio GetProc04. Questo è l'esempio di cmdlet `Get-Process` descritto in [aggiunta della segnalazione errori non fatale al cmdlet](../cmdlet/adding-non-terminating-error-reporting-to-your-cmdlet.md). Questo cmdlet `Get-Process` chiama il metodo [System. Management. Automation. cmdlet. WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) ogni volta che viene generata un'eccezione di operazione non valida durante il recupero delle informazioni sul processo.

> [!NOTE]
> È possibile scaricare il C# file di origine (getprov04.cs) per questo cmdlet Get-proc utilizzando Microsoft Windows Software Development Kit per i componenti di runtime di Windows Vista e .NET Framework 3,0. Per istruzioni sul download, vedere [come installare Windows PowerShell e scaricare Windows PowerShell SDK](/powershell/developer/installing-the-windows-powershell-sdk).
>
> I file di origine scaricati sono disponibili nella directory degli **esempi \<PowerShell >** .

Per il codice di esempio completo, vedere gli argomenti seguenti.

|Linguaggio|Argomento|
|--------------|-----------|
|C#|[Codice diC#esempio GetProc04 ()](./getproc04-csharp-sample-code.md)|
|VB.NET|[Codice di esempio GetProc04 (VB.NET)](./getproc04-vb-net-sample-code.md)|

## <a name="see-also"></a>Vedere anche

[Guida per programmatori di Windows PowerShell](./windows-powershell-programmer-s-guide.md)

[Windows PowerShell SDK](../windows-powershell-reference.md)