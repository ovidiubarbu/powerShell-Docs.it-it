---
title: Codice di esempio di PowerShell di Windows | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 1106829a-8ddc-454e-bbdd-ade15d4bffb4
caps.latest.revision: 7
ms.openlocfilehash: 4154aeb22b5dde7806f3af133559d471e82bb981
ms.sourcegitcommit: 46bebe692689ebedfe65ff2c828fe666b443198d
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/10/2019
ms.locfileid: "67733770"
---
# <a name="windows-powershell-sample-code"></a>Codice di esempio di Windows PowerShell

Windows PowerShell® esempi sono disponibili tramite il SDK di Windows. In questa sezione contiene il codice di esempio contenuta negli esempi del SDK di Windows.

> [!NOTE]
> Quando viene installato il SDK di Windows, un **esempi** viene creata una directory in cui vengono resi disponibili tutti gli esempi di Windows PowerShell. È una directory di installazione tipiche **C:\Program Files\Microsoft SDKs\Windows\v6.0**. Avviare Windows PowerShell e digitare **"cd Samples\SysMgmt\PowerShell"** per individuare la directory di esempi di Windows PowerShell. In questo documento, la directory degli esempi PowerShell di Windows è detto  **\<esempi di PowerShell >** .

## <a name="sample-code-listing"></a>Listato di codice di esempio

|Codice di esempio|Description|
|-----------------|-----------------|
|[AccessDbProviderSample01 Code Sample](./accessdbprovidersample01-code-sample.md)|Si tratta del provider descritte in [creazione di un PowerShell Provider di Windows base](./creating-a-basic-windows-powershell-provider.md).|
|[AccessDbProviderSample02 Code Sample](./accessdbprovidersample02-code-sample.md)|Si tratta del provider descritte in [creazione di un Provider di unità di Windows PowerShell](./creating-a-windows-powershell-drive-provider.md).|
|[AccessDbProviderSample03 Code Sample](./accessdbprovidersample03-code-sample.md)|Si tratta del provider descritte in [creazione di un Provider di Windows PowerShell](./creating-a-windows-powershell-item-provider.md).|
|[AccessDbProviderSample04 Code Sample](./accessdbprovidersample04-code-sample.md)|Si tratta del provider descritte in [creazione di un Provider di contenitore di Windows PowerShell](./creating-a-windows-powershell-container-provider.md).|
|[AccessDbProviderSample05 Code Sample](./accessdbprovidersample05-code-sample.md)|Si tratta del provider descritte in [creazione di un Provider di navigazione di Windows PowerShell](./creating-a-windows-powershell-navigation-provider.md).|
|[AccessDbProviderSample06 Code Sample](./accessdbprovidersample06-code-sample.md)|Si tratta del provider descritte in [creazione di un Provider di contenuti di Windows PowerShell](./creating-a-windows-powershell-content-provider.md).|
|[Esempi di codice GetProc01](./getproc01-code-samples.md)|Si tratta di basic `Get-Process` cmdlet esempio descritto in [creazione del primo Cmdlet](../cmdlet/creating-a-cmdlet-without-parameters.md).|
|[Esempi di codice GetProc02](./getproc02-code-samples.md)|Questo è il `Get-Process` cmdlet esempio descritto in [aggiunta di parametri di Input della riga di comando processo](../cmdlet/adding-parameters-that-process-command-line-input.md).|
|[Esempi di codice GetProc03](./getproc03-code-samples.md)|Questo è il `Get-Process` cmdlet esempio descritto in [aggiunta di parametri di Input della Pipeline di processo](../cmdlet/adding-parameters-that-process-pipeline-input.md).|
|[Esempi di codice GetProc04](./getproc04-code-samples.md)|Questo è il `Get-Process` cmdlet esempio descritto in [aggiunta non fatali di segnalazione errori per il Cmdlet](../cmdlet/adding-non-terminating-error-reporting-to-your-cmdlet.md).|
|[Esempi di codice GetProc05](./getproc05-code-samples.md)|Ciò `Get-Process` cmdlet è simile al cmdlet descritto in [aggiunta non fatali di segnalazione errori per il Cmdlet](../cmdlet/adding-non-terminating-error-reporting-to-your-cmdlet.md).|
|[Esempi di codice StopProc01](./stopproc01-code-samples.md)|Questo è il `Stop-Process` cmdlet esempio descritto in [creazione di un Cmdlet che modifichi il sistema](../cmdlet/creating-a-cmdlet-that-modifies-the-system.md).|
|[Esempi di codice StopProcessSample04](./stopprocesssample04-code-samples.md)|Questo è il `Stop-Process` cmdlet esempio descritto in [aggiunta di set di parametri a un Cmdlet](../cmdlet/adding-parameter-sets-to-a-cmdlet.md).|
|[Esempi di codice Runspace01](./runspace01-code-samples.md)|Questi sono esempi di codice per lo spazio di esecuzione descritto in [creazione di un'applicazione Console che avvia un comando specificato](/dotnet/csharp/programming-guide/inside-a-program/hello-world-your-first-program).|
|[Esempi di codice Runspace02](./runspace02-code-samples.md)|Questo esempio Usa la [System.Management.Automation.Runspaceinvoke](/dotnet/api/System.Management.Automation.RunspaceInvoke) classe per eseguire il `Get-Process` cmdlet in modo sincrono.|
|[Esempi di codice RunSpace03](./runspace03-code-samples.md)|Questi sono esempi di codice per lo spazio di esecuzione descritto in [creazione di un'applicazione Console che avvia uno Script specificato](fd).|
|[Esempi di codice RunSpace04](./runspace04-code-samples.md)|Questo è un esempio di codice per uno spazio di esecuzione che usa il [System.Management.Automation.Runspaceinvoke](/dotnet/api/System.Management.Automation.RunspaceInvoke) classe per eseguire uno script che genera un errore irreversibile.|
|[Esempio di codice RunSpace05](./runspace05-code-sample.md)|Si tratta del codice sorgente per l'esempio Runspace05 descritto nel [configurazione di un RunspaceConfiguration usando spazio di esecuzione](https://msdn.microsoft.com/en-us/42681d19-2d05-4975-befd-afb1990e79b2).|
|[Esempio di codice RunSpace06](./runspace06-code-sample.md)|Si tratta del codice sorgente per l'esempio Runspace06 descritto nel [configurazione di uno spazio di esecuzione tramite uno Snap-in PowerShell di Windows](https://msdn.microsoft.com/en-us/a7289ee8-9732-49ee-91c7-d533e9538b83).|
|[Esempio di codice RunSpace07](./runspace07-code-sample.md)|Si tratta del codice sorgente per l'esempio Runspace07 descritto nel [creazione di un'applicazione che aggiunge i comandi della Console a una Pipeline](https://msdn.microsoft.com/en-us/01eb7808-e97b-4905-80be-9e2fa38c262e).|
|[Esempio di codice RunSpace08](./runspace08-code-sample.md)|Si tratta del codice sorgente per l'esempio Runspace08 descritto nel [creazione di una Console che aggiunge i parametri dell'applicazione a un comando](https://msdn.microsoft.com/en-us/848b2b46-60f1-4a86-b448-cfc7c0cccfba).|
|[Esempio di codice RunSpace09](./runspace09-code-sample.md)|Si tratta del codice sorgente per l'esempio Runspace09 descritto nel [la creazione di una Console dell'applicazione che richiama una Pipeline in modo asincrono](https://msdn.microsoft.com/en-us/198c1c94-2a06-457e-93ce-c0d910618e47).|
|[Esempio di codice RunSpace10](./runspace10-code-sample.md)|Questo è il codice sorgente per l'esempio Runspace10, che viene aggiunto un cmdlet per [System.Management.Automation.Runspaces.Runspaceconfiguration](/dotnet/api/System.Management.Automation.Runspaces.RunspaceConfiguration) e quindi Usa le informazioni di configurazione modificato per creare lo spazio di esecuzione.|

## <a name="see-also"></a>Vedere anche

[Guida per programmatori di Windows PowerShell](./windows-powershell-programmer-s-guide.md)

[Windows PowerShell SDK](../windows-powershell-reference.md)