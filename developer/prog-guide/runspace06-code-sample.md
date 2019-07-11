---
title: Esempio di codice RunSpace06 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d71f86d5-eb62-4b16-aa95-5fd3f314ffd3
caps.latest.revision: 6
ms.openlocfilehash: b6fdad90f7339e941d77646936b1b5952cd65500
ms.sourcegitcommit: 46bebe692689ebedfe65ff2c828fe666b443198d
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/10/2019
ms.locfileid: "67734939"
---
# <a name="runspace06-code-sample"></a>Codice di esempio di Runspace06

Ecco il codice sorgente per l'esempio Runspace06 descritto in [configurazione di uno spazio di esecuzione tramite uno Snap-in PowerShell di Windows](https://msdn.microsoft.com/en-us/a7289ee8-9732-49ee-91c7-d533e9538b83). Questa applicazione di esempio crea uno spazio di esecuzione in base uno snap-in Windows PowerShell, che viene quindi usato per eseguire una pipeline con un unico comando. A tale scopo, l'applicazione crea le informazioni di configurazione dello spazio di esecuzione, crea uno spazio di esecuzione, viene creata una pipeline con un singolo comando e quindi esegue la pipeline.

> [!NOTE]
> È possibile scaricare il C# file di origine (runspace06.cs) utilizzando il Windows Software Development Kit per Windows Vista e i componenti di Runtime di Microsoft .NET Framework 3.0. Per istruzioni sul download, vedere [come installare Windows PowerShell e il Download di Windows PowerShell SDK](/powershell/developer/installing-the-windows-powershell-sdk).
>
> Sono disponibili in file di origine scaricato il  **\<esempi di PowerShell >** directory.

## <a name="code-sample"></a>Esempio di codice

[!code-csharp[Runspace06.cs](../../powershell-sdk-samples/SDK-2.0/csharp/Runspace06/Runspace06.cs#L11-L85 "Runspace06.cs")]

## <a name="see-also"></a>Vedere anche

[Guida per programmatori di Windows PowerShell](./windows-powershell-programmer-s-guide.md)

[Windows PowerShell SDK](../windows-powershell-reference.md)