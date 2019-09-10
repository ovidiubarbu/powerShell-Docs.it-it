---
title: Esempio diC#codice RunSpace03 () | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 9ac8ab99-1856-4d6f-b30d-c0a18b8dd1fc
caps.latest.revision: 6
ms.openlocfilehash: 9afdb97b8ae2919f091ca5bacccedbe37c2e1584
ms.sourcegitcommit: 00083f07b13c73b86936e7d7307397df27c63c04
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/10/2019
ms.locfileid: "70848035"
---
# <a name="runspace03-c-code-sample"></a>Codice di esempio di Runspace03 (C#)

Ecco il C# codice sorgente per l'applicazione console descritta in "creazione di un'applicazione console che esegue uno script specificato". Questo esempio usa la classe [System. Management. Automation. Runspaceinvoke](/dotnet/api/System.Management.Automation.RunspaceInvoke) per eseguire uno script che recupera le informazioni sul processo usando l'elenco dei nomi di processo passati allo script. Viene illustrato come passare gli oggetti di input a uno script e come recuperare gli oggetti Error, nonché gli oggetti di output.

> [!NOTE]
> È possibile scaricare il C# file di origine (runspace03.cs) per questo esempio utilizzando Microsoft Windows Software Development Kit per i componenti di runtime di Windows Vista e Microsoft .NET Framework 3,0. Per istruzioni sul download, vedere [come installare Windows PowerShell e scaricare Windows PowerShell SDK](/powershell/developer/installing-the-windows-powershell-sdk).
> I file di origine scaricati sono disponibili nell'  **\<>** directory degli esempi di PowerShell.

## <a name="code-sample"></a>Esempio di codice

[!code-csharp[Runspace03.cs](../../powershell-sdk-samples/SDK-2.0/csharp/Runspace03/Runspace03.cs#L11-L88 "Runspace03.cs")]

## <a name="see-also"></a>Vedere anche

[Guida per programmatori di Windows PowerShell](./windows-powershell-programmer-s-guide.md)

[Windows PowerShell SDK](../windows-powershell-reference.md)