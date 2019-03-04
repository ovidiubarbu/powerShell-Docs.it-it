---
title: Runspace01 (C#) esempio di codice | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d59f8b7c-e800-4633-aa5b-74d4c57e2706
caps.latest.revision: 6
ms.openlocfilehash: 2f1839d1ba578cdfe97f60c741c84b0a57f1d8f6
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/03/2019
ms.locfileid: "56854217"
---
# <a name="runspace01-c-code-sample"></a>Codice di esempio di Runspace01 (C#)

Ecco gli esempi di codice per lo spazio di esecuzione descritto in [creazione di un'applicazione Console che avvia un comando specificato](http://msdn.microsoft.com/en-us/793a6570-a072-4799-840b-172f28ce620e). A tale scopo, l'applicazione richiama uno spazio di esecuzione e quindi richiama un comando. Si noti che questa applicazione non specifica le informazioni di configurazione dello spazio di esecuzione, né e in modo esplicito crea una pipeline. Il comando che viene richiamato il `Get-Process` cmdlet.
Ecco gli esempi di codice per lo spazio di esecuzione descritto in [creazione di un'applicazione Console che avvia un comando specificato](http://msdn.microsoft.com/en-us/793a6570-a072-4799-840b-172f28ce620e). A tale scopo, l'applicazione richiama uno spazio di esecuzione e quindi richiama un comando. Si noti che questa applicazione non specifica le informazioni di configurazione dello spazio di esecuzione, né e in modo esplicito crea una pipeline. Il comando che viene richiamato il `Get-Process` cmdlet.

> [!NOTE]
> È possibile scaricare il C# file di origine (runspace01.cs) per questo spazio di esecuzione usando il Microsoft Windows Software Development Kit per Windows Vista e i componenti di Runtime di Microsoft .NET Framework 3.0. Per istruzioni sul download, vedere [come installare Windows PowerShell e il Download di Windows PowerShell SDK](/powershell/developer/installing-the-windows-powershell-sdk).
> È possibile scaricare il C# file di origine (runspace01.cs) per questo spazio di esecuzione usando il Microsoft Windows Software Development Kit per Windows Vista e i componenti di Runtime di Microsoft .NET Framework 3.0. Per istruzioni sul download, vedere [come installare Windows PowerShell e il Download di Windows PowerShell SDK](/powershell/developer/installing-the-windows-powershell-sdk).
>
> Sono disponibili in file di origine scaricato il  **\<esempi di PowerShell >** directory.

## <a name="code-sample"></a>Esempio di codice

[!code-csharp[Runspace01.cs](../../powershell-sdk-samples/SDK-2.0/csharp/Runspace01/Runspace01.cs#L11-L62 "Runspace01.cs")]

## <a name="see-also"></a>Vedere anche

[Guida per programmatori di Windows PowerShell](./windows-powershell-programmer-s-guide.md)

[Windows PowerShell SDK](../windows-powershell-reference.md)