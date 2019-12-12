---
title: Esempi di spazio | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: c92a6d3d-8d34-4a76-bdc3-dea923d9858e
caps.latest.revision: 17
ms.openlocfilehash: e24d40746da91f60aaf2af655ddcadc88ab6a4db
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/05/2019
ms.locfileid: "72361000"
---
# <a name="runspace-samples"></a>Esempi di spazi di esecuzione

Questa sezione include codice di esempio che illustra come usare tipi diversi di Runspaces per eseguire i comandi in modo sincrono e asincrono. È possibile utilizzare Microsoft Visual Studio per creare un'applicazione console e quindi copiare il codice dagli argomenti in questa sezione nell'applicazione host.

## <a name="in-this-section"></a>Contenuto della sezione

> [!NOTE]
> Per esempi di applicazioni host che creano interfacce host personalizzate, vedere [esempi di host personalizzati](./custom-host-samples.md).

 [Esempio Runspace01](./runspace01-sample.md) Questo esempio illustra come usare la classe [System. Management. Automation. PowerShell](/dotnet/api/system.management.automation.powershell) per eseguire il cmdlet [Get-Process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) in modo sincrono e visualizzarne l'output in una finestra della console.

 [Esempio Runspace02](./runspace02-sample.md) Questo esempio illustra come usare la classe [System. Management. Automation. PowerShell](/dotnet/api/system.management.automation.powershell) per eseguire in modo sincrono i cmdlet [Get-Process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) e [Sort-Object](/powershell/module/Microsoft.PowerShell.Utility/Sort-Object) . I risultati di questi comandi vengono visualizzati usando un controllo [System. Windows. Forms. DataGridView](/dotnet/api/System.Windows.Forms.DataGridView) .

 [Esempio Runspace03](./runspace03-sample.md) Questo esempio illustra come usare la classe [System. Management. Automation. PowerShell](/dotnet/api/system.management.automation.powershell) per eseguire uno script in modo sincrono e come gestire errori non fatali. Lo script riceve un elenco di nomi di processo e quindi recupera tali processi. I risultati dello script, compresi gli errori non fatali che si sono generati durante l'esecuzione dello script, vengono visualizzati in una finestra della console.

 [Esempio Runspace04](./runspace04-sample.md) Questo esempio illustra come usare la classe [System. Management. Automation. PowerShell](/dotnet/api/system.management.automation.powershell) per eseguire i comandi e come intercettare gli errori di terminazione che vengono generati quando si eseguono i comandi. Vengono eseguiti due comandi e all'ultimo viene passato un argomento di parametro non valido. Di conseguenza, non viene restituito alcun oggetto e viene generato un errore di terminazione.

 [Esempio Runspace05](./runspace05-sample.md) In questo esempio viene illustrato come aggiungere uno snap-in a un oggetto [System. Management. Automation. Runspaces. InitialSessionState](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) , in modo che il cmdlet dello snap-in sia disponibile quando viene aperto il spazio. Lo snap-in fornisce un cmdlet Get-proc (definito dall' [esempio GetProcessSample01](../cmdlet/getprocesssample01-sample.md)) che viene eseguito in modo sincrono tramite un oggetto [System. Management. Automation. PowerShell](/dotnet/api/system.management.automation.powershell) .

 [Esempio Runspace06](./runspace06-sample.md) Questo esempio illustra come aggiungere un modulo a un oggetto [System. Management. Automation. Runspaces. InitialSessionState](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) , in modo che il modulo venga caricato quando viene aperto il spazio. Il modulo fornisce un cmdlet Get-proc (definito dall' [esempio GetProcessSample02](../cmdlet/getprocesssample02-sample.md)) che viene eseguito in modo sincrono usando un oggetto [System. Management. Automation. PowerShell](/dotnet/api/system.management.automation.powershell) .

 [Esempio Runspace07](./runspace07-sample.md) Questo esempio illustra come creare un spazio e quindi usare tale spazio per eseguire due cmdlet in modo sincrono usando un oggetto [System. Management. Automation. PowerShell](/dotnet/api/system.management.automation.powershell) .

 [Esempio Runspace08](./runspace08-sample.md) Questo esempio illustra come aggiungere comandi e argomenti alla pipeline di un oggetto [System. Management. Automation. PowerShell](/dotnet/api/system.management.automation.powershell) e come eseguire i comandi in modo sincrono.

 [Esempio Runspace09](./runspace09-sample.md) Questo esempio illustra come aggiungere uno script alla pipeline di un oggetto [System. Management. Automation. PowerShell](/dotnet/api/system.management.automation.powershell) e come eseguire lo script in modo asincrono. Gli eventi vengono usati per gestire l'output dello script.

 [Esempio Runspace10](./runspace10-sample.md) Questo esempio illustra come creare uno stato di sessione iniziale predefinito, come aggiungere un cmdlet a [System. Management. Automation. Runspaces. InitialSessionState](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState), come creare un spazio che usa lo stato della sessione iniziale e come eseguire il comando usando un oggetto [System. Management. Automation. PowerShell](/dotnet/api/system.management.automation.powershell) .

 [Esempio Runspace11](./runspace11-sample.md) Viene illustrato come usare la classe [System. Management. Automation. ProxyCommand](/dotnet/api/System.Management.Automation.ProxyCommand) per creare un comando proxy che chiama un cmdlet esistente, ma limita il set di parametri disponibili. Il comando proxy viene quindi aggiunto a uno stato sessione iniziale usato per creare uno spazio di esecuzione vincolato. Ciò significa che l'utente può accedere alla funzionalità del cmdlet solo tramite il comando proxy.

## <a name="see-also"></a>Vedere anche
