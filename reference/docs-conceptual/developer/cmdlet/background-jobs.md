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
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/15/2019
ms.locfileid: "72363560"
---
# <a name="background-jobs"></a><span data-ttu-id="0ceba-102">Processi in background</span><span class="sxs-lookup"><span data-stu-id="0ceba-102">Background Jobs</span></span>

<span data-ttu-id="0ceba-103">I cmdlet possono eseguire l'azione internamente o come processo in*background*di Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="0ceba-103">Cmdlets can perform their action internally or as a Windows PowerShell*background job*.</span></span> <span data-ttu-id="0ceba-104">Quando un cmdlet viene eseguito come processo in background, il lavoro viene eseguito in modo asincrono in un thread separato dal thread della pipeline utilizzato dal cmdlet.</span><span class="sxs-lookup"><span data-stu-id="0ceba-104">When a cmdlet runs as a background job, the work is done asynchronously in its own thread separate from the pipeline thread that the cmdlet is using.</span></span> <span data-ttu-id="0ceba-105">Dal punto di vista dell'utente, quando un cmdlet viene eseguito come processo in background, il prompt dei comandi viene restituito immediatamente anche se il completamento del processo richiede una quantità di tempo prolungata e l'utente può continuare senza interruzioni durante l'esecuzione del processo.</span><span class="sxs-lookup"><span data-stu-id="0ceba-105">From the user perspective, when a cmdlet runs as a background job, the command prompt returns immediately even if the job takes an extended amount of time to complete, and the user can continue without interruption while the job runs.</span></span>

## <a name="background-jobs-child-jobs-and-the-job-repository"></a><span data-ttu-id="0ceba-106">Processi in background, processi figlio e repository di processi</span><span class="sxs-lookup"><span data-stu-id="0ceba-106">Background Jobs, Child Jobs, and the Job Repository</span></span>

<span data-ttu-id="0ceba-107">L'oggetto processo restituito dai cmdlet che supportano i processi in background definisce il processo.</span><span class="sxs-lookup"><span data-stu-id="0ceba-107">The job object that is returned by the cmdlets that support background jobs defines the job.</span></span> <span data-ttu-id="0ceba-108">Il cmdlet [Start-Job](/powershell/module/Microsoft.PowerShell.Core/Start-Job) restituisce anche un oggetto processo. Il nome del processo, un identificatore usato per specificare il processo, le informazioni sullo stato e i processi figlio sono inclusi in questa definizione.</span><span class="sxs-lookup"><span data-stu-id="0ceba-108">(The [Start-Job](/powershell/module/Microsoft.PowerShell.Core/Start-Job) cmdlet also returns a job object.) The name of the job, an identifier that is used to specify the job, the state information, and the child jobs are included in this definition.</span></span> <span data-ttu-id="0ceba-109">Il processo non esegue alcun lavoro.</span><span class="sxs-lookup"><span data-stu-id="0ceba-109">The job does not perform any of the work.</span></span> <span data-ttu-id="0ceba-110">Ogni processo in background ha almeno un processo figlio perché il processo figlio esegue il lavoro effettivo.</span><span class="sxs-lookup"><span data-stu-id="0ceba-110">Each background job has at least one child job because the child job performs the actual work.</span></span> <span data-ttu-id="0ceba-111">Quando si esegue un cmdlet in modo che il lavoro venga eseguito come processo in background, il cmdlet deve aggiungere il processo e i processi figlio a un repository comune, denominato repository dei *processi*.</span><span class="sxs-lookup"><span data-stu-id="0ceba-111">When you run a cmdlet so that the work is performed as a background job, the cmdlet must add the job and the child jobs to a common repository, referred to as the *job repository*.</span></span>

<span data-ttu-id="0ceba-112">Per ulteriori informazioni sul modo in cui i processi in background vengono gestiti dalla riga di comando, vedere gli argomenti seguenti:</span><span class="sxs-lookup"><span data-stu-id="0ceba-112">For more information about how background jobs are handled at the command line, see the following:</span></span>

- [<span data-ttu-id="0ceba-113">about_Jobs</span><span class="sxs-lookup"><span data-stu-id="0ceba-113">about_Jobs</span></span>](/powershell/module/microsoft.powershell.core/about/about_jobs)

- [<span data-ttu-id="0ceba-114">about_Job_Details</span><span class="sxs-lookup"><span data-stu-id="0ceba-114">about_Job_Details</span></span>](/powershell/module/microsoft.powershell.core/about/about_job_details)

- [<span data-ttu-id="0ceba-115">about_Remote_Jobs</span><span class="sxs-lookup"><span data-stu-id="0ceba-115">about_Remote_Jobs</span></span>](/powershell/module/microsoft.powershell.core/about/about_remote_jobs)

## <a name="writing-a-cmdlet-that-runs-as-a-background-job"></a><span data-ttu-id="0ceba-116">Scrittura di un cmdlet eseguito come processo in background</span><span class="sxs-lookup"><span data-stu-id="0ceba-116">Writing a Cmdlet That Runs as a Background Job</span></span>

<span data-ttu-id="0ceba-117">Per scrivere un cmdlet che può essere eseguito come processo in background, è necessario completare le attività seguenti:</span><span class="sxs-lookup"><span data-stu-id="0ceba-117">To write a cmdlet that can be run as a background job, you must complete the following tasks:</span></span>

- <span data-ttu-id="0ceba-118">Definire un parametro di opzione `asJob` in modo che l'utente possa decidere se eseguire il cmdlet come processo in background.</span><span class="sxs-lookup"><span data-stu-id="0ceba-118">Define an `asJob` switch parameter so that the user can decide whether to run the cmdlet as a background job.</span></span>

- <span data-ttu-id="0ceba-119">Creare un oggetto che deriva dalla classe [System. Management. Automation. job](/dotnet/api/System.Management.Automation.Job) .</span><span class="sxs-lookup"><span data-stu-id="0ceba-119">Create an object that derives from the [System.Management.Automation.Job](/dotnet/api/System.Management.Automation.Job) class.</span></span> <span data-ttu-id="0ceba-120">Questo oggetto può essere un oggetto processo personalizzato o un oggetto processo fornito da Windows PowerShell, ad esempio un oggetto [System. Management. Automation. PSEventJob](/dotnet/api/System.Management.Automation.PSEventJob) .</span><span class="sxs-lookup"><span data-stu-id="0ceba-120">This object can be a custom job object or a job object provided by Windows PowerShell, such as a [System.Management.Automation.Pseventjob](/dotnet/api/System.Management.Automation.PSEventJob) object.</span></span>

- <span data-ttu-id="0ceba-121">In un metodo di elaborazione dei record aggiungere un'istruzione `if` che rilevi se il cmdlet deve essere eseguito come processo in background.</span><span class="sxs-lookup"><span data-stu-id="0ceba-121">In a record processing method, add an `if` statement that detects whether the cmdlet should run as a background job.</span></span>

- <span data-ttu-id="0ceba-122">Per gli oggetti processo personalizzati, implementare la classe Job.</span><span class="sxs-lookup"><span data-stu-id="0ceba-122">For custom job objects, implement the job class.</span></span>

- <span data-ttu-id="0ceba-123">Restituisce gli oggetti appropriati, a seconda che il cmdlet venga eseguito come processo in background.</span><span class="sxs-lookup"><span data-stu-id="0ceba-123">Return the appropriate objects, depending on whether the cmdlet is run as a background job.</span></span>

<span data-ttu-id="0ceba-124">Per un esempio di codice, vedere [come supportare i processi](./how-to-support-jobs.md).</span><span class="sxs-lookup"><span data-stu-id="0ceba-124">For a code example, see [How to Support Jobs](./how-to-support-jobs.md).</span></span>

## <a name="background-job-related-apis"></a><span data-ttu-id="0ceba-125">API correlate ai processi in background</span><span class="sxs-lookup"><span data-stu-id="0ceba-125">Background Job-Related APIs</span></span>

<span data-ttu-id="0ceba-126">Le API seguenti sono fornite da Windows PowerShell per gestire i processi in background.</span><span class="sxs-lookup"><span data-stu-id="0ceba-126">The following APIs are provided by Windows PowerShell to manage background jobs.</span></span>

<span data-ttu-id="0ceba-127">[System. Management. Automation. job](/dotnet/api/System.Management.Automation.Job) deriva oggetti processo personalizzati.</span><span class="sxs-lookup"><span data-stu-id="0ceba-127">[System.Management.Automation.Job](/dotnet/api/System.Management.Automation.Job) Derives custom job objects.</span></span> <span data-ttu-id="0ceba-128">Si tratta di una classe astratta.</span><span class="sxs-lookup"><span data-stu-id="0ceba-128">This is an abstract class.</span></span>

<span data-ttu-id="0ceba-129">[System. Management. Automation. Jobrepository](/dotnet/api/System.Management.Automation.JobRepository) gestisce e fornisce informazioni sui processi in background attivi correnti.</span><span class="sxs-lookup"><span data-stu-id="0ceba-129">[System.Management.Automation.Jobrepository](/dotnet/api/System.Management.Automation.JobRepository) Manages and provides information about the current active background jobs.</span></span>

<span data-ttu-id="0ceba-130">[System. Management. Automation. JobState](/dotnet/api/System.Management.Automation.JobState) definisce lo stato del processo in background.</span><span class="sxs-lookup"><span data-stu-id="0ceba-130">[System.Management.Automation.Jobstate](/dotnet/api/System.Management.Automation.JobState) Defines the state of the background job.</span></span> <span data-ttu-id="0ceba-131">Gli Stati sono Started, running e Stopped.</span><span class="sxs-lookup"><span data-stu-id="0ceba-131">States include Started, Running, and Stopped.</span></span>

<span data-ttu-id="0ceba-132">[System. Management. Automation. JobStateInfo](/dotnet/api/System.Management.Automation.JobStateInfo) fornisce informazioni sullo stato di un processo in background e, se l'ultima modifica dello stato è stata causata da un errore, il motivo per cui il processo è entrato nello stato corrente.</span><span class="sxs-lookup"><span data-stu-id="0ceba-132">[System.Management.Automation.Jobstateinfo](/dotnet/api/System.Management.Automation.JobStateInfo) Provides information about the state of a background job and, if the last state change was caused by an error, the reason the job entered its current state.</span></span>

<span data-ttu-id="0ceba-133">[System. Management. Automation. Jobstateeventargs](/dotnet/api/System.Management.Automation.JobStateEventArgs) fornisce gli argomenti per un evento generato quando viene modificato lo stato di un processo in background.</span><span class="sxs-lookup"><span data-stu-id="0ceba-133">[System.Management.Automation.Jobstateeventargs](/dotnet/api/System.Management.Automation.JobStateEventArgs) Provides the arguments for an event that is raised when a background job changes state.</span></span>

## <a name="windows-powershell-job-cmdlets"></a><span data-ttu-id="0ceba-134">Cmdlet per processi di Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="0ceba-134">Windows PowerShell Job Cmdlets</span></span>

<span data-ttu-id="0ceba-135">I cmdlet seguenti sono forniti da Windows PowerShell per gestire i processi in background.</span><span class="sxs-lookup"><span data-stu-id="0ceba-135">The following cmdlets are provided by Windows PowerShell to manage background jobs.</span></span>

[<span data-ttu-id="0ceba-136">Get-Job</span><span class="sxs-lookup"><span data-stu-id="0ceba-136">Get-Job</span></span>](/powershell/module/Microsoft.PowerShell.Core/Get-Job)

<span data-ttu-id="0ceba-137">Ottiene i processi in background di Windows PowerShell in esecuzione nella sessione corrente.</span><span class="sxs-lookup"><span data-stu-id="0ceba-137">Gets Windows PowerShell background jobs that are running in the current session.</span></span>

[<span data-ttu-id="0ceba-138">Receive-Job</span><span class="sxs-lookup"><span data-stu-id="0ceba-138">Receive-Job</span></span>](/powershell/module/Microsoft.PowerShell.Core/Receive-Job)

<span data-ttu-id="0ceba-139">Ottiene i risultati dei processi in background di Windows PowerShell nella sessione corrente.</span><span class="sxs-lookup"><span data-stu-id="0ceba-139">Gets the results of the Windows PowerShell background jobs in the current session.</span></span>

[<span data-ttu-id="0ceba-140">Remove-Job</span><span class="sxs-lookup"><span data-stu-id="0ceba-140">Remove-Job</span></span>](/powershell/module/Microsoft.PowerShell.Core/Remove-Job)

<span data-ttu-id="0ceba-141">Elimina un processo in background di Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="0ceba-141">Deletes a Windows PowerShell background job.</span></span>

[<span data-ttu-id="0ceba-142">Start-Job</span><span class="sxs-lookup"><span data-stu-id="0ceba-142">Start-Job</span></span>](/powershell/module/Microsoft.PowerShell.Core/Start-Job)

<span data-ttu-id="0ceba-143">Avvia un processo in background di Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="0ceba-143">Starts a Windows PowerShell background job.</span></span>

[<span data-ttu-id="0ceba-144">Stop-Job</span><span class="sxs-lookup"><span data-stu-id="0ceba-144">Stop-Job</span></span>](/powershell/module/Microsoft.PowerShell.Core/Stop-Job)

<span data-ttu-id="0ceba-145">Arresta un processo in background di Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="0ceba-145">Stops a Windows PowerShell background job.</span></span>

[<span data-ttu-id="0ceba-146">Wait-Job</span><span class="sxs-lookup"><span data-stu-id="0ceba-146">Wait-Job</span></span>](/powershell/module/Microsoft.PowerShell.Core/Wait-Job)

<span data-ttu-id="0ceba-147">Elimina il prompt dei comandi finché non vengono completati uno o tutti i processi in background di Windows PowerShell in esecuzione nella sessione.</span><span class="sxs-lookup"><span data-stu-id="0ceba-147">Suppresses the command prompt until one or all of the Windows PowerShell background jobs running in the session are complete.</span></span>

## <a name="see-also"></a><span data-ttu-id="0ceba-148">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="0ceba-148">See Also</span></span>

[<span data-ttu-id="0ceba-149">Scrittura di un cmdlet di Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="0ceba-149">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
