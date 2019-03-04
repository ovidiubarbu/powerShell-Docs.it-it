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
ms.openlocfilehash: 9aff23647e55e8c9c41c54e5b62cedc15fb28a2d
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/03/2019
ms.locfileid: "56857167"
---
# <a name="background-jobs"></a><span data-ttu-id="368ad-102">Processi in background</span><span class="sxs-lookup"><span data-stu-id="368ad-102">Background Jobs</span></span>

<span data-ttu-id="368ad-103">I cmdlet possono eseguire l'azione internamente o come un Windows PowerShell*processo in background*.</span><span class="sxs-lookup"><span data-stu-id="368ad-103">Cmdlets can perform their action internally or as a Windows PowerShell*background job*.</span></span> <span data-ttu-id="368ad-104">Quando un cmdlet viene eseguito come processo in background, il lavoro viene eseguito in modo asincrono nel proprio thread separato dal thread della pipeline che usa il cmdlet.</span><span class="sxs-lookup"><span data-stu-id="368ad-104">When a cmdlet runs as a background job, the work is done asynchronously in its own thread separate from the pipeline thread that the cmdlet is using.</span></span> <span data-ttu-id="368ad-105">Dalla prospettiva dell'utente, quando un cmdlet viene eseguito come processo in background, il prompt dei comandi restituisce immediatamente anche se il processo richiede una certa quantità di tempo per il completamento e l'utente può continuare senza interruzioni durante l'esecuzione del processo.</span><span class="sxs-lookup"><span data-stu-id="368ad-105">From the user perspective, when a cmdlet runs as a background job, the command prompt returns immediately even if the job takes an extended amount of time to complete, and the user can continue without interruption while the job runs.</span></span>

## <a name="background-jobs-child-jobs-and-the-job-repository"></a><span data-ttu-id="368ad-106">I processi in background, i processi figlio e l'archivio di processi</span><span class="sxs-lookup"><span data-stu-id="368ad-106">Background Jobs, Child Jobs, and the Job Repository</span></span>

<span data-ttu-id="368ad-107">L'oggetto processo restituito dai cmdlet che supportano i processi in background definisce il processo.</span><span class="sxs-lookup"><span data-stu-id="368ad-107">The job object that is returned by the cmdlets that support background jobs defines the job.</span></span> <span data-ttu-id="368ad-108">(Il [Start-Job](/powershell/module/Microsoft.PowerShell.Core/Start-Job) cmdlet restituisce anche un oggetto processo.) Il nome del processo, un identificatore che consente di specificare il processo, le informazioni sullo stato e i processi figlio sono inclusi in questa definizione.</span><span class="sxs-lookup"><span data-stu-id="368ad-108">(The [Start-Job](/powershell/module/Microsoft.PowerShell.Core/Start-Job) cmdlet also returns a job object.) The name of the job, an identifier that is used to specify the job, the state information, and the child jobs are included in this definition.</span></span> <span data-ttu-id="368ad-109">Il processo non esegue nessuna delle operazioni.</span><span class="sxs-lookup"><span data-stu-id="368ad-109">The job does not perform any of the work.</span></span> <span data-ttu-id="368ad-110">Ogni processo in background ha almeno un processo figlio perché il processo figlio esegue il lavoro effettivo.</span><span class="sxs-lookup"><span data-stu-id="368ad-110">Each background job has at least one child job because the child job performs the actual work.</span></span> <span data-ttu-id="368ad-111">Quando si esegue un cmdlet in modo che il lavoro viene eseguito come processo in background, il cmdlet necessario aggiungere il processo e i processi figlio a un repository comune, definito come il *archivio di processi*.</span><span class="sxs-lookup"><span data-stu-id="368ad-111">When you run a cmdlet so that the work is performed as a background job, the cmdlet must add the job and the child jobs to a common repository, referred to as the *job repository*.</span></span>
<span data-ttu-id="368ad-112">L'oggetto processo restituito dai cmdlet che supportano i processi in background definisce il processo.</span><span class="sxs-lookup"><span data-stu-id="368ad-112">The job object that is returned by the cmdlets that support background jobs defines the job.</span></span> <span data-ttu-id="368ad-113">(Il [Start-Job](/powershell/module/Microsoft.PowerShell.Core/Start-Job) cmdlet restituisce anche un oggetto processo.) Il nome del processo, un identificatore che consente di specificare il processo, le informazioni sullo stato e i processi figlio sono inclusi in questa definizione.</span><span class="sxs-lookup"><span data-stu-id="368ad-113">(The [Start-Job](/powershell/module/Microsoft.PowerShell.Core/Start-Job) cmdlet also returns a job object.) The name of the job, an identifier that is used to specify the job, the state information, and the child jobs are included in this definition.</span></span> <span data-ttu-id="368ad-114">Il processo non esegue nessuna delle operazioni.</span><span class="sxs-lookup"><span data-stu-id="368ad-114">The job does not perform any of the work.</span></span> <span data-ttu-id="368ad-115">Ogni processo in background ha almeno un processo figlio perché il processo figlio esegue il lavoro effettivo.</span><span class="sxs-lookup"><span data-stu-id="368ad-115">Each background job has at least one child job because the child job performs the actual work.</span></span> <span data-ttu-id="368ad-116">Quando si esegue un cmdlet in modo che il lavoro viene eseguito come processo in background, il cmdlet necessario aggiungere il processo e i processi figlio a un repository comune, definito come il *archivio di processi*.</span><span class="sxs-lookup"><span data-stu-id="368ad-116">When you run a cmdlet so that the work is performed as a background job, the cmdlet must add the job and the child jobs to a common repository, referred to as the *job repository*.</span></span>

<span data-ttu-id="368ad-117">Per altre informazioni su come i processi in background vengono gestiti dalla riga di comando, vedere gli argomenti seguenti:</span><span class="sxs-lookup"><span data-stu-id="368ad-117">For more information about how background jobs are handled at the command line, see the following:</span></span>

- [<span data-ttu-id="368ad-118">about_Jobs</span><span class="sxs-lookup"><span data-stu-id="368ad-118">about_Jobs</span></span>](/powershell/module/microsoft.powershell.core/about/about_jobs)

- [<span data-ttu-id="368ad-119">about_Job_Details</span><span class="sxs-lookup"><span data-stu-id="368ad-119">about_Job_Details</span></span>](/powershell/module/microsoft.powershell.core/about/about_job_details)

- [<span data-ttu-id="368ad-120">about_Remote_Jobs</span><span class="sxs-lookup"><span data-stu-id="368ad-120">about_Remote_Jobs</span></span>](/powershell/module/microsoft.powershell.core/about/about_remote_jobs)

## <a name="writing-a-cmdlet-that-runs-as-a-background-job"></a><span data-ttu-id="368ad-121">Scrittura di un Cmdlet che viene eseguito come processo in Background</span><span class="sxs-lookup"><span data-stu-id="368ad-121">Writing a Cmdlet That Runs as a Background Job</span></span>

<span data-ttu-id="368ad-122">Per scrivere un cmdlet che può essere eseguito come processo in background, è necessario completare le attività seguenti:</span><span class="sxs-lookup"><span data-stu-id="368ad-122">To write a cmdlet that can be run as a background job, you must complete the following tasks:</span></span>

- <span data-ttu-id="368ad-123">Definire un `asJob` parametro opzionale in modo che l'utente può decidere se eseguire il cmdlet come processo in background.</span><span class="sxs-lookup"><span data-stu-id="368ad-123">Define an `asJob` switch parameter so that the user can decide whether to run the cmdlet as a background job.</span></span>

- <span data-ttu-id="368ad-124">Creare un oggetto da cui deriva il [System.Management.Automation.Job](/dotnet/api/System.Management.Automation.Job) classe.</span><span class="sxs-lookup"><span data-stu-id="368ad-124">Create an object that derives from the [System.Management.Automation.Job](/dotnet/api/System.Management.Automation.Job) class.</span></span> <span data-ttu-id="368ad-125">Questo oggetto può essere un oggetto processo personalizzato o un oggetto processo forniti da Windows PowerShell, ad esempio un [pseventjob](/dotnet/api/System.Management.Automation.PSEventJob) oggetto.</span><span class="sxs-lookup"><span data-stu-id="368ad-125">This object can be a custom job object or a job object provided by Windows PowerShell, such as a [System.Management.Automation.Pseventjob](/dotnet/api/System.Management.Automation.PSEventJob) object.</span></span>

- <span data-ttu-id="368ad-126">In un metodo di elaborazione record, aggiungere un `if` informativa in grado di rilevare se il cmdlet deve essere eseguito come processo in background.</span><span class="sxs-lookup"><span data-stu-id="368ad-126">In a record processing method, add an `if` statement that detects whether the cmdlet should run as a background job.</span></span>

- <span data-ttu-id="368ad-127">Per gli oggetti di processo personalizzato, implementare la classe di processo.</span><span class="sxs-lookup"><span data-stu-id="368ad-127">For custom job objects, implement the job class.</span></span>

- <span data-ttu-id="368ad-128">Restituisce gli oggetti appropriati, a seconda del fatto che il cmdlet viene eseguito come processo in background.</span><span class="sxs-lookup"><span data-stu-id="368ad-128">Return the appropriate objects, depending on whether the cmdlet is run as a background job.</span></span>

<span data-ttu-id="368ad-129">Per un esempio di codice, vedere [come i processi di supporto](./how-to-support-jobs.md).</span><span class="sxs-lookup"><span data-stu-id="368ad-129">For a code example, see [How to Support Jobs](./how-to-support-jobs.md).</span></span>

## <a name="background-job-related-apis"></a><span data-ttu-id="368ad-130">API correlata al processo in background</span><span class="sxs-lookup"><span data-stu-id="368ad-130">Background Job-Related APIs</span></span>

<span data-ttu-id="368ad-131">Le API seguenti sono fornite da Windows PowerShell per gestire i processi in background.</span><span class="sxs-lookup"><span data-stu-id="368ad-131">The following APIs are provided by Windows PowerShell to manage background jobs.</span></span>

<span data-ttu-id="368ad-132">[System.Management.Automation.Job](/dotnet/api/System.Management.Automation.Job) deriva gli oggetti di processo personalizzato.</span><span class="sxs-lookup"><span data-stu-id="368ad-132">[System.Management.Automation.Job](/dotnet/api/System.Management.Automation.Job) Derives custom job objects.</span></span> <span data-ttu-id="368ad-133">Si tratta di una classe astratta.</span><span class="sxs-lookup"><span data-stu-id="368ad-133">This is an abstract class.</span></span>

<span data-ttu-id="368ad-134">[System.Management.Automation.Jobrepository](/dotnet/api/System.Management.Automation.JobRepository) gestisce e fornisce informazioni sui processi in background attivo corrente.</span><span class="sxs-lookup"><span data-stu-id="368ad-134">[System.Management.Automation.Jobrepository](/dotnet/api/System.Management.Automation.JobRepository) Manages and provides information about the current active background jobs.</span></span>

<span data-ttu-id="368ad-135">[System.Management.Automation.Jobstate](/dotnet/api/System.Management.Automation.JobState) definisce lo stato del processo in background.</span><span class="sxs-lookup"><span data-stu-id="368ad-135">[System.Management.Automation.Jobstate](/dotnet/api/System.Management.Automation.JobState) Defines the state of the background job.</span></span> <span data-ttu-id="368ad-136">Stati includono Started, in esecuzione e arrestato.</span><span class="sxs-lookup"><span data-stu-id="368ad-136">States include Started, Running, and Stopped.</span></span>

<span data-ttu-id="368ad-137">[System.Management.Automation.Jobstateinfo](/dotnet/api/System.Management.Automation.JobStateInfo) fornisce informazioni sullo stato del processo in background e, se l'ultimo stato di modifica è stato causato da un errore, il motivo per il processo è passato allo stato corrente.</span><span class="sxs-lookup"><span data-stu-id="368ad-137">[System.Management.Automation.Jobstateinfo](/dotnet/api/System.Management.Automation.JobStateInfo) Provides information about the state of a background job and, if the last state change was caused by an error, the reason the job entered its current state.</span></span>

<span data-ttu-id="368ad-138">[System.Management.Automation.Jobstateeventargs](/dotnet/api/System.Management.Automation.JobStateEventArgs) fornisce gli argomenti per un evento generato quando lo stato viene modificato un processo in background.</span><span class="sxs-lookup"><span data-stu-id="368ad-138">[System.Management.Automation.Jobstateeventargs](/dotnet/api/System.Management.Automation.JobStateEventArgs) Provides the arguments for an event that is raised when a background job changes state.</span></span>

## <a name="windows-powershell-job-cmdlets"></a><span data-ttu-id="368ad-139">Cmdlet di PowerShell processo Windows</span><span class="sxs-lookup"><span data-stu-id="368ad-139">Windows PowerShell Job Cmdlets</span></span>

<span data-ttu-id="368ad-140">I cmdlet seguenti vengono forniti tramite Windows PowerShell per gestire i processi in background.</span><span class="sxs-lookup"><span data-stu-id="368ad-140">The following cmdlets are provided by Windows PowerShell to manage background jobs.</span></span>

[<span data-ttu-id="368ad-141">Get-Job</span><span class="sxs-lookup"><span data-stu-id="368ad-141">Get-Job</span></span>](/powershell/module/Microsoft.PowerShell.Core/Get-Job)

<span data-ttu-id="368ad-142">Ottiene i processi in background di Windows PowerShell in esecuzione nella sessione corrente.</span><span class="sxs-lookup"><span data-stu-id="368ad-142">Gets Windows PowerShell background jobs that are running in the current session.</span></span>

[<span data-ttu-id="368ad-143">Receive-Job</span><span class="sxs-lookup"><span data-stu-id="368ad-143">Receive-Job</span></span>](/powershell/module/Microsoft.PowerShell.Core/Receive-Job)

<span data-ttu-id="368ad-144">Ottiene i risultati dei processi in background di Windows PowerShell nella sessione corrente.</span><span class="sxs-lookup"><span data-stu-id="368ad-144">Gets the results of the Windows PowerShell background jobs in the current session.</span></span>

[<span data-ttu-id="368ad-145">Remove-Job</span><span class="sxs-lookup"><span data-stu-id="368ad-145">Remove-Job</span></span>](/powershell/module/Microsoft.PowerShell.Core/Remove-Job)

<span data-ttu-id="368ad-146">Elimina un processo in background di Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="368ad-146">Deletes a Windows PowerShell background job.</span></span>

[<span data-ttu-id="368ad-147">Start-Job</span><span class="sxs-lookup"><span data-stu-id="368ad-147">Start-Job</span></span>](/powershell/module/Microsoft.PowerShell.Core/Start-Job)

<span data-ttu-id="368ad-148">Avvia un processo in background di Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="368ad-148">Starts a Windows PowerShell background job.</span></span>

[<span data-ttu-id="368ad-149">Stop-Job</span><span class="sxs-lookup"><span data-stu-id="368ad-149">Stop-Job</span></span>](/powershell/module/Microsoft.PowerShell.Core/Stop-Job)

<span data-ttu-id="368ad-150">Arresta un processo in background di Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="368ad-150">Stops a Windows PowerShell background job.</span></span>

[<span data-ttu-id="368ad-151">Wait-Job</span><span class="sxs-lookup"><span data-stu-id="368ad-151">Wait-Job</span></span>](/powershell/module/Microsoft.PowerShell.Core/Wait-Job)

<span data-ttu-id="368ad-152">Elimina il prompt dei comandi finché non vengono completati uno o tutti i processi in background di Windows PowerShell in esecuzione nella sessione.</span><span class="sxs-lookup"><span data-stu-id="368ad-152">Suppresses the command prompt until one or all of the Windows PowerShell background jobs running in the session are complete.</span></span>

## <a name="see-also"></a><span data-ttu-id="368ad-153">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="368ad-153">See Also</span></span>

[<span data-ttu-id="368ad-154">Scrittura di un cmdlet di Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="368ad-154">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
