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
ms.openlocfilehash: f0197e6ca3535b72f843ba52e97381c0f2531598
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/15/2019
ms.locfileid: "72366490"
---
# <a name="runspace06-code-sample"></a>Codice di esempio di Runspace06

Ecco il codice sorgente per l'esempio Runspace06 descritto in [configurazione di un spazio mediante uno snap-in di Windows PowerShell](https://msdn.microsoft.com/en-us/a7289ee8-9732-49ee-91c7-d533e9538b83). Questa applicazione di esempio crea un spazio basato su uno snap-in di Windows PowerShell, che viene quindi usato per eseguire una pipeline con un unico comando. A tale scopo, l'applicazione crea le informazioni di configurazione spazio, crea una spazio, crea una pipeline con un unico comando, quindi esegue la pipeline.

> [!NOTE]
> È possibile scaricare il C# file di origine (runspace06.cs) utilizzando Windows Software Development Kit per i componenti di runtime di Windows Vista e Microsoft .NET Framework 3,0. Per istruzioni sul download, vedere [come installare Windows PowerShell e scaricare Windows PowerShell SDK](/powershell/developer/installing-the-windows-powershell-sdk).
>
> I file di origine scaricati sono disponibili nella directory degli **esempi \<PowerShell >** .

## <a name="code-sample"></a>Esempio di codice

[!code-csharp[Runspace06.cs](../../../../powershell-sdk-samples/SDK-2.0/csharp/Runspace06/Runspace06.cs#L11-L85 "Runspace06.cs")]

## <a name="see-also"></a>Vedere anche

[Guida per programmatori di Windows PowerShell](./windows-powershell-programmer-s-guide.md)

[Windows PowerShell SDK](../windows-powershell-reference.md)
