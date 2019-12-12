---
title: Processi in background | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: a0ef5ac9-8254-4832-ace8-84b356c10f08
caps.latest.revision: 13
ms.openlocfilehash: ff4fe159eedc47fc69f4d783cd90d2b0e888c0d5
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/05/2019
ms.locfileid: "72363560"
---
# <a name="background-jobs"></a>Processi in background

I cmdlet possono eseguire l'azione internamente o come processo in*background*di Windows PowerShell. Quando un cmdlet viene eseguito come processo in background, il lavoro viene eseguito in modo asincrono in un thread separato dal thread della pipeline utilizzato dal cmdlet. Dal punto di vista dell'utente, quando un cmdlet viene eseguito come processo in background, il prompt dei comandi viene restituito immediatamente anche se il completamento del processo richiede una quantità di tempo prolungata e l'utente può continuare senza interruzioni durante l'esecuzione del processo.

## <a name="background-jobs-child-jobs-and-the-job-repository"></a>Processi in background, processi figlio e repository di processi

L'oggetto processo restituito dai cmdlet che supportano i processi in background definisce il processo. Il cmdlet [Start-Job](/powershell/module/Microsoft.PowerShell.Core/Start-Job) restituisce anche un oggetto processo. Il nome del processo, un identificatore usato per specificare il processo, le informazioni sullo stato e i processi figlio sono inclusi in questa definizione. Il processo non esegue alcun lavoro. Ogni processo in background ha almeno un processo figlio perché il processo figlio esegue il lavoro effettivo. Quando si esegue un cmdlet in modo che il lavoro venga eseguito come processo in background, il cmdlet deve aggiungere il processo e i processi figlio a un repository comune, denominato repository dei *processi*.

Per ulteriori informazioni sul modo in cui i processi in background vengono gestiti dalla riga di comando, vedere gli argomenti seguenti:

- [about_Jobs](/powershell/module/microsoft.powershell.core/about/about_jobs)

- [about_Job_Details](/powershell/module/microsoft.powershell.core/about/about_job_details)

- [about_Remote_Jobs](/powershell/module/microsoft.powershell.core/about/about_remote_jobs)

## <a name="writing-a-cmdlet-that-runs-as-a-background-job"></a>Scrittura di un cmdlet eseguito come processo in background

Per scrivere un cmdlet che può essere eseguito come processo in background, è necessario completare le attività seguenti:

- Definire un parametro di opzione `asJob` in modo che l'utente possa decidere se eseguire il cmdlet come processo in background.

- Creare un oggetto che deriva dalla classe [System. Management. Automation. job](/dotnet/api/System.Management.Automation.Job) . Questo oggetto può essere un oggetto processo personalizzato o un oggetto processo fornito da Windows PowerShell, ad esempio un oggetto [System. Management. Automation. PSEventJob](/dotnet/api/System.Management.Automation.PSEventJob) .

- In un metodo di elaborazione dei record aggiungere un'istruzione `if` che rilevi se il cmdlet deve essere eseguito come processo in background.

- Per gli oggetti processo personalizzati, implementare la classe Job.

- Restituisce gli oggetti appropriati, a seconda che il cmdlet venga eseguito come processo in background.

Per un esempio di codice, vedere [come supportare i processi](./how-to-support-jobs.md).

## <a name="background-job-related-apis"></a>API correlate ai processi in background

Le API seguenti sono fornite da Windows PowerShell per gestire i processi in background.

[System. Management. Automation. job](/dotnet/api/System.Management.Automation.Job) deriva oggetti processo personalizzati. Questa è una classe astratta.

[System. Management. Automation. Jobrepository](/dotnet/api/System.Management.Automation.JobRepository) gestisce e fornisce informazioni sui processi in background attivi correnti.

[System. Management. Automation. JobState](/dotnet/api/System.Management.Automation.JobState) definisce lo stato del processo in background. Gli Stati sono Started, running e Stopped.

[System. Management. Automation. JobStateInfo](/dotnet/api/System.Management.Automation.JobStateInfo) fornisce informazioni sullo stato di un processo in background e, se l'ultima modifica dello stato è stata causata da un errore, il motivo per cui il processo è entrato nello stato corrente.

[System. Management. Automation. Jobstateeventargs](/dotnet/api/System.Management.Automation.JobStateEventArgs) fornisce gli argomenti per un evento generato quando viene modificato lo stato di un processo in background.

## <a name="windows-powershell-job-cmdlets"></a>Cmdlet per processi di Windows PowerShell

I cmdlet seguenti sono forniti da Windows PowerShell per gestire i processi in background.

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
