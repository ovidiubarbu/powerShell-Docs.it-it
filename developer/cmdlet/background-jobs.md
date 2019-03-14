---
title: I processi in background | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: a0ef5ac9-8254-4832-ace8-84b356c10f08
caps.latest.revision: 13
ms.openlocfilehash: ff4fe159eedc47fc69f4d783cd90d2b0e888c0d5
ms.sourcegitcommit: 5990f04b8042ef2d8e571bec6d5b051e64c9921c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/12/2019
ms.locfileid: "57794706"
---
# <a name="background-jobs"></a>Processi in background

I cmdlet possono eseguire l'azione internamente o come un Windows PowerShell*processo in background*. Quando un cmdlet viene eseguito come processo in background, il lavoro viene eseguito in modo asincrono nel proprio thread separato dal thread della pipeline che usa il cmdlet. Dalla prospettiva dell'utente, quando un cmdlet viene eseguito come processo in background, il prompt dei comandi restituisce immediatamente anche se il processo richiede una certa quantità di tempo per il completamento e l'utente può continuare senza interruzioni durante l'esecuzione del processo.

## <a name="background-jobs-child-jobs-and-the-job-repository"></a>I processi in background, i processi figlio e l'archivio di processi

L'oggetto processo restituito dai cmdlet che supportano i processi in background definisce il processo. (Il [Start-Job](/powershell/module/Microsoft.PowerShell.Core/Start-Job) cmdlet restituisce anche un oggetto processo.) Il nome del processo, un identificatore che consente di specificare il processo, le informazioni sullo stato e i processi figlio sono inclusi in questa definizione. Il processo non esegue nessuna delle operazioni. Ogni processo in background ha almeno un processo figlio perché il processo figlio esegue il lavoro effettivo. Quando si esegue un cmdlet in modo che il lavoro viene eseguito come processo in background, il cmdlet necessario aggiungere il processo e i processi figlio a un repository comune, definito come il *archivio di processi*.

Per altre informazioni su come i processi in background vengono gestiti dalla riga di comando, vedere gli argomenti seguenti:

- [about_Jobs](/powershell/module/microsoft.powershell.core/about/about_jobs)

- [about_Job_Details](/powershell/module/microsoft.powershell.core/about/about_job_details)

- [about_Remote_Jobs](/powershell/module/microsoft.powershell.core/about/about_remote_jobs)

## <a name="writing-a-cmdlet-that-runs-as-a-background-job"></a>Scrittura di un Cmdlet che viene eseguito come processo in Background

Per scrivere un cmdlet che può essere eseguito come processo in background, è necessario completare le attività seguenti:

- Definire un `asJob` parametro opzionale in modo che l'utente può decidere se eseguire il cmdlet come processo in background.

- Creare un oggetto da cui deriva il [System.Management.Automation.Job](/dotnet/api/System.Management.Automation.Job) classe. Questo oggetto può essere un oggetto processo personalizzato o un oggetto processo forniti da Windows PowerShell, ad esempio un [pseventjob](/dotnet/api/System.Management.Automation.PSEventJob) oggetto.

- In un metodo di elaborazione record, aggiungere un `if` informativa in grado di rilevare se il cmdlet deve essere eseguito come processo in background.

- Per gli oggetti di processo personalizzato, implementare la classe di processo.

- Restituisce gli oggetti appropriati, a seconda del fatto che il cmdlet viene eseguito come processo in background.

Per un esempio di codice, vedere [come i processi di supporto](./how-to-support-jobs.md).

## <a name="background-job-related-apis"></a>API correlata al processo in background

Le API seguenti sono fornite da Windows PowerShell per gestire i processi in background.

[System.Management.Automation.Job](/dotnet/api/System.Management.Automation.Job) deriva gli oggetti di processo personalizzato. Si tratta di una classe astratta.

[System.Management.Automation.Jobrepository](/dotnet/api/System.Management.Automation.JobRepository) gestisce e fornisce informazioni sui processi in background attivo corrente.

[System.Management.Automation.Jobstate](/dotnet/api/System.Management.Automation.JobState) definisce lo stato del processo in background. Stati includono Started, in esecuzione e arrestato.

[System.Management.Automation.Jobstateinfo](/dotnet/api/System.Management.Automation.JobStateInfo) fornisce informazioni sullo stato del processo in background e, se l'ultimo stato di modifica è stato causato da un errore, il motivo per il processo è passato allo stato corrente.

[System.Management.Automation.Jobstateeventargs](/dotnet/api/System.Management.Automation.JobStateEventArgs) fornisce gli argomenti per un evento generato quando lo stato viene modificato un processo in background.

## <a name="windows-powershell-job-cmdlets"></a>Cmdlet di PowerShell processo Windows

I cmdlet seguenti vengono forniti tramite Windows PowerShell per gestire i processi in background.

[Get-Job](/powershell/module/Microsoft.PowerShell.Core/Get-Job)

Ottiene i processi in background di Windows PowerShell in esecuzione nella sessione corrente.

[Receive-Job](/powershell/module/Microsoft.PowerShell.Core/Receive-Job)

Ottiene i risultati dei processi in background di Windows PowerShell nella sessione corrente.

[Remove-Job](/powershell/module/Microsoft.PowerShell.Core/Remove-Job)

Elimina un processo in background di Windows PowerShell.

[Start-Job](/powershell/module/Microsoft.PowerShell.Core/Start-Job)

Avvia un processo in background di Windows PowerShell.

[Stop-Job](/powershell/module/Microsoft.PowerShell.Core/Stop-Job)

Arresta un processo in background di Windows PowerShell.

[Wait-Job](/powershell/module/Microsoft.PowerShell.Core/Wait-Job)

Elimina il prompt dei comandi finché non vengono completati uno o tutti i processi in background di Windows PowerShell in esecuzione nella sessione.

## <a name="see-also"></a>Vedere anche

[Scrittura di un cmdlet di Windows PowerShell](./writing-a-windows-powershell-cmdlet.md)
