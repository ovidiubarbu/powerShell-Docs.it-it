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
ms.openlocfilehash: 8326d1f47ce07698f09ade9ba97154ecc358465a
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/05/2019
ms.locfileid: "74417450"
---
# <a name="getproc04-code-samples"></a>Codici di esempio di GetProc04

Ecco gli esempi di codice per il cmdlet di esempio GetProc04. Questo è l'esempio di cmdlet `Get-Process` descritto in [aggiunta della segnalazione errori non fatale al cmdlet](../cmdlet/adding-non-terminating-error-reporting-to-your-cmdlet.md). Questo cmdlet `Get-Process` chiama il metodo [System. Management. Automation. cmdlet. WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) ogni volta che viene generata un'eccezione di operazione non valida durante il recupero delle informazioni sul processo.

> [!NOTE]
> È possibile scaricare il C# file di origine (getprov04.cs) per questo cmdlet Get-proc utilizzando Microsoft Windows Software Development Kit per i componenti di runtime di Windows Vista e .NET Framework 3,0. Per istruzioni sul download, vedere [come installare Windows PowerShell e scaricare Windows PowerShell SDK](/powershell/scripting/developer/installing-the-windows-powershell-sdk).
>
> I file di origine scaricati sono disponibili nella directory **\<PowerShell samples >** .

Per il codice di esempio completo, vedere gli argomenti seguenti.

|Linguaggio|Argomento|
|--------------|-----------|
|C#|[Codice diC#esempio GetProc04 ()](./getproc04-csharp-sample-code.md)|
|VB.NET|[Codice di esempio GetProc04 (VB.NET)](./getproc04-vb-net-sample-code.md)|

## <a name="see-also"></a>Vedere anche

[Guida per programmatori di Windows PowerShell](./windows-powershell-programmer-s-guide.md)

[Windows PowerShell SDK](../windows-powershell-reference.md)
