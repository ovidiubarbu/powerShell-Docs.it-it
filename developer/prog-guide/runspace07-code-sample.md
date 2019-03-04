---
title: Esempio di codice RunSpace07 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 8ad306d9-45c2-4d55-8e64-fdcba43402c5
caps.latest.revision: 6
ms.openlocfilehash: 3e016b0e98234797afc8f303a55919228eaf8829
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/03/2019
ms.locfileid: "56857927"
---
# <a name="runspace07-code-sample"></a>Codice di esempio di Runspace07

Ecco il codice sorgente per l'esempio Runspace07 descritto in [creazione di un'applicazione che aggiunge i comandi della Console a una Pipeline](http://msdn.microsoft.com/en-us/01eb7808-e97b-4905-80be-9e2fa38c262e). Questa applicazione di esempio crea uno spazio di esecuzione, viene creata una pipeline, aggiunge i due comandi alla pipeline e quindi esegue la pipeline. I comandi aggiunti alla pipeline sono le `Get-Process` e `Measure-Object` cmdlet.

> [!NOTE]
> È possibile scaricare il C# file di origine (runspace07.cs) usando il Microsoft Windows Software Development Kit per Windows Vista e i componenti di Microsoft .NET Framework 3.0 Runtime. Per istruzioni sul download, vedere [come installare Windows PowerShell e il Download di Windows PowerShell SDK](/powershell/developer/installing-the-windows-powershell-sdk).
> È possibile scaricare il C# file di origine (runspace07.cs) usando il Microsoft Windows Software Development Kit per Windows Vista e i componenti di Microsoft .NET Framework 3.0 Runtime. Per istruzioni sul download, vedere [come installare Windows PowerShell e il Download di Windows PowerShell SDK](/powershell/developer/installing-the-windows-powershell-sdk).
>
> Sono disponibili in file di origine scaricato il  **\<esempi di PowerShell >** directory.

## <a name="code-sample"></a>Esempio di codice

[!code-csharp[Runspace07.cs](../../powershell-sdk-samples/SDK-2.0/csharp/Runspace07/Runspace07.cs#L11-L108 "Runspace07.cs")]

## <a name="see-also"></a>Vedere anche

[Guida per programmatori di Windows PowerShell](./windows-powershell-programmer-s-guide.md)

[Windows PowerShell SDK](../windows-powershell-reference.md)