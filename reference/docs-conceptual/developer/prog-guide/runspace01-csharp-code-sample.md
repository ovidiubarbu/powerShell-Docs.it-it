---
title: Esempio diC#codice Runspace01 () | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d59f8b7c-e800-4633-aa5b-74d4c57e2706
caps.latest.revision: 6
ms.openlocfilehash: 0978880a4294edb96fc6edb00f420cd0a9ad197b
ms.sourcegitcommit: 7f2479edd329dfdc55726afff7019d45e45f9156
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/08/2020
ms.locfileid: "80977982"
---
# <a name="runspace01-c-code-sample"></a>Codice di esempio di Runspace01 (C#)

Ecco gli esempi di codice per spazio descritto in [creazione di un'applicazione console che esegue un comando specificato](/dotnet/csharp/programming-guide/inside-a-program/hello-world-your-first-program).
A tale scopo, l'applicazione richiama un spazio e quindi richiama un comando. Si noti che questa applicazione non specifica le informazioni di configurazione spazio né crea in modo esplicito una pipeline. Il comando richiamato è il cmdlet `Get-Process`.

> [!NOTE]
> È possibile scaricare il C# file di origine (runspace01.cs) per questo spazio utilizzando Microsoft Windows Software Development Kit per i componenti di runtime di Windows Vista e Microsoft .NET Framework 3,0.
> Per istruzioni sul download, vedere [come installare Windows PowerShell e scaricare Windows PowerShell SDK](/powershell/scripting/developer/installing-the-windows-powershell-sdk).
> I file di origine scaricati sono disponibili nella directory **\<PowerShell samples >** .

## <a name="code-sample"></a>Codice di esempio

:::code language="csharp" source="~/../powershell-sdk-samples/SDK-2.0/csharp/Runspace01/Runspace01.cs" range="11-62":::

## <a name="see-also"></a>Vedere anche

[Guida per programmatori di Windows PowerShell](./windows-powershell-programmer-s-guide.md)

[Windows PowerShell SDK](../windows-powershell-reference.md)
