---
title: Esempi di spazio di esecuzione | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: c92a6d3d-8d34-4a76-bdc3-dea923d9858e
caps.latest.revision: 17
ms.openlocfilehash: e24d40746da91f60aaf2af655ddcadc88ab6a4db
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/03/2019
ms.locfileid: "56857337"
---
# <a name="runspace-samples"></a>Esempi di spazi di esecuzione

In questa sezione include il codice di esempio che illustra come usare diversi tipi di spazi di esecuzione per eseguire comandi in modo sincrono e asincrono. È possibile utilizzare Microsoft Visual Studio per creare un'applicazione console e quindi copiare il codice dagli argomenti di questa sezione nell'applicazione host.

## <a name="in-this-section"></a>Contenuto della sezione

> [!NOTE]
> Per esempi di hosting di applicazioni che creano interfacce host personalizzato, vedere [esempi di Host personalizzato](./custom-host-samples.md).

 [Esempio Runspace01](./runspace01-sample.md) in questo esempio viene illustrato come utilizzare il [System.Management.Automation.Powershell](/dotnet/api/system.management.automation.powershell) classe per eseguire il [Get-Process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) cmdlet in modo sincrono e visualizzarne l'output in una console di finestra.

 [Esempio Runspace02](./runspace02-sample.md) in questo esempio viene illustrato come utilizzare il [System.Management.Automation.Powershell](/dotnet/api/system.management.automation.powershell) classe per eseguire il [Get-Process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) e [Sort-Object](/powershell/module/Microsoft.PowerShell.Utility/Sort-Object) i cmdlet in modo sincrono. I risultati di questi comandi vengono visualizzati utilizzando un [System.Windows.Forms.Datagridview](/dotnet/api/System.Windows.Forms.DataGridView) controllo.

 [Esempio Runspace03](./runspace03-sample.md) in questo esempio viene illustrato come utilizzare il [System.Management.Automation.Powershell](/dotnet/api/system.management.automation.powershell) classe per eseguire uno script in modo sincrono e come gestire gli errori non fatali. Lo script riceve un elenco di nomi di processo e quindi recupera tali processi. I risultati dello script, compresi gli errori non fatali che si sono generati durante l'esecuzione dello script, vengono visualizzati in una finestra della console.

 [Esempio Runspace04](./runspace04-sample.md) in questo esempio viene illustrato come utilizzare il [System.Management.Automation.Powershell](/dotnet/api/system.management.automation.powershell) classe per eseguire comandi e su come recuperare gli errori fatali generati durante l'esecuzione di comandi. Vengono eseguiti due comandi e all'ultimo viene passato un argomento di parametro non valido. Di conseguenza non restituisce alcun oggetto e viene generato un errore irreversibile.

 [Esempio Runspace05](./runspace05-sample.md) in questo esempio viene illustrato come aggiungere uno snap-in per un [System.Management.Automation.Runspaces.Initialsessionstate](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) dell'oggetto in modo che il cmdlet dello snap-in è disponibile quando viene aperto lo spazio di esecuzione. Lo snap-in include un cmdlet Get-Proc (definito dal [esempio GetProcessSample01](../cmdlet/getprocesssample01-sample.md)) che viene eseguito in modo sincrono tramite un [System.Management.Automation.Powershell](/dotnet/api/system.management.automation.powershell) oggetto.

 [Esempio Runspace06](./runspace06-sample.md) in questo esempio viene illustrato come aggiungere un modulo a un [System.Management.Automation.Runspaces.Initialsessionstate](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) dell'oggetto in modo che il modulo venga caricato quando viene aperto lo spazio di esecuzione. Il modulo include un cmdlet Get-Proc (definito dal [esempio GetProcessSample02](../cmdlet/getprocesssample02-sample.md)) che viene eseguito in modo sincrono tramite un [System.Management.Automation.Powershell](/dotnet/api/system.management.automation.powershell) oggetto.

 [Esempio Runspace07](./runspace07-sample.md) in questo esempio viene illustrato come creare uno spazio di esecuzione e quindi usare tale spazio di esecuzione per eseguire due cmdlet in modo sincrono tramite un [System.Management.Automation.Powershell](/dotnet/api/system.management.automation.powershell) oggetto.

 [Esempio Runspace08](./runspace08-sample.md) in questo esempio viene illustrato come aggiungere comandi e argomenti alla pipeline di un [System.Management.Automation.Powershell](/dotnet/api/system.management.automation.powershell) oggetto e come eseguire i comandi in modo sincrono.

 [Esempio Runspace09](./runspace09-sample.md) in questo esempio viene illustrato come aggiungere uno script alla pipeline di un [System.Management.Automation.Powershell](/dotnet/api/system.management.automation.powershell) oggetto e come eseguire lo script in modo asincrono. Gli eventi vengono usati per gestire l'output dello script.

 [Esempio Runspace10](./runspace10-sample.md) in questo esempio viene illustrato come creare uno stato sessione iniziale predefinito, come aggiungere un cmdlet per il [System.Management.Automation.Runspaces.Initialsessionstate](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState), come creare uno spazio di esecuzione che utilizza il stato sessione iniziale e come eseguire il comando utilizzando un [System.Management.Automation.Powershell](/dotnet/api/system.management.automation.powershell) oggetto.

 [Esempio Runspace11](./runspace11-sample.md) viene illustrato come usare il [System.Management.Automation.Proxycommand](/dotnet/api/System.Management.Automation.ProxyCommand) classe per creare un comando proxy che chiama un cmdlet esistente, ma limita il set di parametri disponibili. Il comando proxy viene quindi aggiunto a uno stato sessione iniziale usato per creare uno spazio di esecuzione vincolato. Ciò significa che l'utente può accedere alla funzionalità del cmdlet solo tramite il comando proxy.

## <a name="see-also"></a>Vedere anche
