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
ms.openlocfilehash: b16ee45383059c52ce3433699c6b8d2120992431
ms.sourcegitcommit: 69abc5ad16e5dd29ddfb1853e266a4bfd1d59d59
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/05/2019
ms.locfileid: "57429568"
---
# <a name="runspace05-code-sample"></a>Codice di esempio di Runspace05

Ecco il codice sorgente dell'esempio Runspace05 descritto nella [configurazione di un RunspaceConfiguration usando spazio di esecuzione](http://msdn.microsoft.com/en-us/42681d19-2d05-4975-befd-afb1990e79b2). In questo esempio viene illustrato come creare le informazioni di configurazione dello spazio di esecuzione, creare uno spazio di esecuzione, creare una pipeline con un singolo comando e quindi eseguire la pipeline. Il comando che viene eseguito è il `Get-Process` cmdlet.

> [!NOTE]
> È possibile scaricare il C# file di origine (runspace05.cs) tramite il Microsoft Windows Software Development Kit per Windows Vista e i componenti di Runtime di Microsoft .NET Framework 3.0. Per istruzioni sul download, vedere [come installare Windows PowerShell e il Download di Windows PowerShell SDK](/powershell/developer/installing-the-windows-powershell-sdk).
>
> Sono disponibili in file di origine scaricato il  **\<esempi di PowerShell >** directory.

## <a name="code-sample"></a>Esempio di codice

[!code-csharp[Runspace05.cs](../../powershell-sdk-samples/SDK-2.0/csharp/Runspace05/Runspace05.cs#L11-L86 "Runspace05.cs")]

## <a name="see-also"></a>Vedere anche

[Guida per programmatori di Windows PowerShell](./windows-powershell-programmer-s-guide.md)

[Windows PowerShell SDK](../windows-powershell-reference.md)