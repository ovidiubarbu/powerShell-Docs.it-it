---
title: RunSpace03 (C#) esempio di codice | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 9ac8ab99-1856-4d6f-b30d-c0a18b8dd1fc
caps.latest.revision: 6
ms.openlocfilehash: 0e80f4d850a7c6dc044526a56b92f16eea4040b5
ms.sourcegitcommit: 69abc5ad16e5dd29ddfb1853e266a4bfd1d59d59
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/05/2019
ms.locfileid: "57429908"
---
# <a name="runspace03-c-code-sample"></a>Codice di esempio di Runspace03 (C#)

Di seguito è riportato il C# codice sorgente per l'applicazione console descritto in [creazione di un'applicazione Console che avvia uno Script specificato](http://msdn.microsoft.com/en-us/a93e6006-36db-4bcc-b9da-c5bebf4ffd68). Questo esempio Usa la [System.Management.Automation.Runspaceinvoke](/dotnet/api/System.Management.Automation.RunspaceInvoke) classe per eseguire uno script che recupera elabora le informazioni usando l'elenco di nomi di processo, passata allo script. Mostra come passare oggetti di input a uno script e come recuperare gli oggetti di errore, nonché gli oggetti di output.

> [!NOTE]
> È possibile scaricare il C# file di origine (runspace03.cs) per questo esempio di uso di Microsoft Windows Software Development Kit per Windows Vista e i componenti di Runtime di Microsoft .NET Framework 3.0. Per istruzioni sul download, vedere [come installare Windows PowerShell e il Download di Windows PowerShell SDK](/powershell/developer/installing-the-windows-powershell-sdk).
>
> Sono disponibili in file di origine scaricato il  **\<esempi di PowerShell >** directory.

## <a name="code-sample"></a>Esempio di codice

[!code-csharp[Runspace03.cs](../../powershell-sdk-samples/SDK-2.0/csharp/Runspace03/Runspace03.cs#L11-L88 "Runspace03.cs")]

## <a name="see-also"></a>Vedere anche

[Guida per programmatori di Windows PowerShell](./windows-powershell-programmer-s-guide.md)

[Windows PowerShell SDK](../windows-powershell-reference.md)