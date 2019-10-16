---
title: Codice di esempio di Windows PowerShell | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 1106829a-8ddc-454e-bbdd-ade15d4bffb4
caps.latest.revision: 7
ms.openlocfilehash: e9df44b17453e9f73f6eb388d9cbc8a69fce4ba2
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/15/2019
ms.locfileid: "72366420"
---
# <a name="windows-powershell-sample-code"></a>Codice di esempio di Windows PowerShell

Gli esempi di® di Windows PowerShell sono disponibili tramite l'Windows SDK. Questa sezione contiene il codice di esempio contenuto nell'Windows SDK esempi.

> [!NOTE]
> Quando viene installata la Windows SDK, viene creata una directory degli **esempi** in cui vengono resi disponibili tutti gli esempi di Windows PowerShell. Una directory di installazione tipica è **C:\Programmi\Microsoft SDKs\Windows\v6.0**.
> Avviare Windows PowerShell e digitare **"CD Samples\SysMgmt\PowerShell"** per individuare la directory degli esempi di Windows PowerShell. In questo documento la directory degli esempi di Windows PowerShell viene definita **\<PowerShell samples >** .

## <a name="sample-code-listing"></a>Listato di codice di esempio

|Codice di esempio|Description|
|-----------------|-----------------|
|[Esempio di codice AccessDbProviderSample01](./accessdbprovidersample01-code-sample.md)|Si tratta del provider descritto in [creazione di un provider di Windows PowerShell di base](./creating-a-basic-windows-powershell-provider.md).|
|[Esempio di codice AccessDbProviderSample02](./accessdbprovidersample02-code-sample.md)|Si tratta del provider descritto in [creazione di un provider di unità di Windows PowerShell](./creating-a-windows-powershell-drive-provider.md).|
|[Esempio di codice AccessDbProviderSample03](./accessdbprovidersample03-code-sample.md)|Si tratta del provider descritto in [creazione di un provider di elementi di Windows PowerShell](./creating-a-windows-powershell-item-provider.md).|
|[Esempio di codice AccessDbProviderSample04](./accessdbprovidersample04-code-sample.md)|Si tratta del provider descritto in [creazione di un provider di contenitori di Windows PowerShell](./creating-a-windows-powershell-container-provider.md).|
|[Esempio di codice AccessDbProviderSample05](./accessdbprovidersample05-code-sample.md)|Si tratta del provider descritto in [creazione di un provider di navigazione di Windows PowerShell](./creating-a-windows-powershell-navigation-provider.md).|
|[Esempio di codice AccessDbProviderSample06](./accessdbprovidersample06-code-sample.md)|Si tratta del provider descritto in [creazione di un provider di contenuti Windows PowerShell](./creating-a-windows-powershell-content-provider.md).|
|[Esempi di codice GetProc01](./getproc01-code-samples.md)|Questo è l'esempio di cmdlet `Get-Process` di base descritto in [creazione del primo cmdlet](../cmdlet/creating-a-cmdlet-without-parameters.md).|
|[Esempi di codice GetProc02](./getproc02-code-samples.md)|Questo è l'esempio di cmdlet `Get-Process` descritto in [aggiunta di parametri che elaborano l'input della riga di comando](../cmdlet/adding-parameters-that-process-command-line-input.md).|
|[Esempi di codice GetProc03](./getproc03-code-samples.md)|Questo è l'esempio di cmdlet `Get-Process` descritto in [aggiunta di parametri che elaborano l'input della pipeline](../cmdlet/adding-parameters-that-process-pipeline-input.md).|
|[Esempi di codice GetProc04](./getproc04-code-samples.md)|Questo è l'esempio di cmdlet `Get-Process` descritto in [aggiunta della segnalazione errori non fatale al cmdlet](../cmdlet/adding-non-terminating-error-reporting-to-your-cmdlet.md).|
|[Esempi di codice GetProc05](./getproc05-code-samples.md)|Questo cmdlet `Get-Process` è simile al cmdlet descritto in [aggiunta della segnalazione errori non fatale al cmdlet](../cmdlet/adding-non-terminating-error-reporting-to-your-cmdlet.md).|
|[Esempi di codice StopProc01](./stopproc01-code-samples.md)|Questo è l'esempio di cmdlet `Stop-Process` descritto in [creazione di un cmdlet che modifica il sistema](../cmdlet/creating-a-cmdlet-that-modifies-the-system.md).|
|[Esempi di codice StopProcessSample04](./stopprocesssample04-code-samples.md)|Questo è l'esempio di cmdlet `Stop-Process` descritto in [aggiunta di set di parametri a un cmdlet](../cmdlet/adding-parameter-sets-to-a-cmdlet.md).|
|[Esempi di codice Runspace01](./runspace01-code-samples.md)|Questi sono gli esempi di codice per spazio descritto in [creazione di un'applicazione console che esegue un comando specificato](/dotnet/csharp/programming-guide/inside-a-program/hello-world-your-first-program).|
|[Esempi di codice Runspace02](./runspace02-code-samples.md)|Questo esempio usa la classe [System. Management. Automation. Runspaceinvoke](/dotnet/api/System.Management.Automation.RunspaceInvoke) per eseguire il cmdlet `Get-Process` in modo sincrono.|
|[Esempi di codice RunSpace03](./runspace03-code-samples.md)|Questi sono gli esempi di codice per spazio descritti in "creazione di un'applicazione console che esegue uno script specificato".|
|[Esempi di codice RunSpace04](./runspace04-code-samples.md)|Questo è un esempio di codice per un spazio che usa la classe [System. Management. Automation. Runspaceinvoke](/dotnet/api/System.Management.Automation.RunspaceInvoke) per eseguire uno script che genera un errore di terminazione.|
|[Esempio di codice RunSpace05](./runspace05-code-sample.md)|Questo è il codice sorgente per l'esempio Runspace05 descritto in [configurazione di un spazio con RunspaceConfiguration](https://msdn.microsoft.com/en-us/42681d19-2d05-4975-befd-afb1990e79b2).|
|[Esempio di codice RunSpace06](./runspace06-code-sample.md)|Questo è il codice sorgente per l'esempio Runspace06 descritto in [configurazione di un spazio mediante uno snap-in di Windows PowerShell](https://msdn.microsoft.com/en-us/a7289ee8-9732-49ee-91c7-d533e9538b83).|
|[Esempio di codice RunSpace07](./runspace07-code-sample.md)|Questo è il codice sorgente per l'esempio Runspace07 descritto in [creazione di un'applicazione console che aggiunge comandi a una pipeline](https://msdn.microsoft.com/en-us/01eb7808-e97b-4905-80be-9e2fa38c262e).|
|[Esempio di codice RunSpace08](./runspace08-code-sample.md)|Questo è il codice sorgente per l'esempio Runspace08 descritto in [creazione di un'applicazione console che aggiunge parametri a un comando](https://msdn.microsoft.com/en-us/848b2b46-60f1-4a86-b448-cfc7c0cccfba).|
|[Esempio di codice RunSpace09](./runspace09-code-sample.md)|Questo è il codice sorgente per l'esempio Runspace09 descritto in [creazione di un'applicazione console che richiama una pipeline in modo asincrono](https://msdn.microsoft.com/en-us/198c1c94-2a06-457e-93ce-c0d910618e47).|
|[Esempio di codice RunSpace10](./runspace10-code-sample.md)|Questo è il codice sorgente per l'esempio Runspace10, che aggiunge un cmdlet a [System. Management. Automation. Runspaces. RunspaceConfiguration](/dotnet/api/System.Management.Automation.Runspaces.RunspaceConfiguration) e quindi usa le informazioni di configurazione modificate per creare il spazio.|

## <a name="see-also"></a>Vedere anche

[Guida per programmatori di Windows PowerShell](./windows-powershell-programmer-s-guide.md)

[Windows PowerShell SDK](../windows-powershell-reference.md)