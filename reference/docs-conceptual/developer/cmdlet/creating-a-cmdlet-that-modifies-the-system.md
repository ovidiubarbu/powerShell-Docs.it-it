---
title: Creazione di un cmdlet che modifica il sistema | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- should process [PowerShell Programmer's Guide]
- should continue [PowerShell Programmer's Guide]
- user feedback [PowerShell Programmer's Guide]
- confirm impact [PowerShell Programmer's Guide]
ms.assetid: 59be4120-1700-4d92-a308-ef4a32ccf11a
caps.latest.revision: 8
ms.openlocfilehash: 8a65915b88a04e36e773853b903528a65fe11e99
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/15/2019
ms.locfileid: "72365760"
---
# <a name="creating-a-cmdlet-that-modifies-the-system"></a><span data-ttu-id="dbf57-102">Creazione di un cmdlet che modifica il sistema</span><span class="sxs-lookup"><span data-stu-id="dbf57-102">Creating a Cmdlet that Modifies the System</span></span>

<span data-ttu-id="dbf57-103">A volte un cmdlet deve modificare lo stato di esecuzione del sistema, non solo lo stato del runtime di Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="dbf57-103">Sometimes a cmdlet must modify the running state of the system, not just the state of the Windows PowerShell runtime.</span></span> <span data-ttu-id="dbf57-104">In questi casi, il cmdlet deve consentire all'utente di confermare se apportare o meno la modifica.</span><span class="sxs-lookup"><span data-stu-id="dbf57-104">In these cases, the cmdlet should allow the user a chance to confirm whether or not to make the change.</span></span>

<span data-ttu-id="dbf57-105">Per supportare la conferma, un cmdlet deve eseguire due operazioni.</span><span class="sxs-lookup"><span data-stu-id="dbf57-105">To support confirmation a cmdlet must do two things.</span></span>

- <span data-ttu-id="dbf57-106">Dichiarare che il cmdlet supporta la conferma quando si specifica l'attributo [System. Management. Automation. CmdletAttribute](/dotnet/api/System.Management.Automation.CmdletAttribute) impostando la parola chiave SupportsShouldProcess su `true`.</span><span class="sxs-lookup"><span data-stu-id="dbf57-106">Declare that the cmdlet supports confirmation when you specify the [System.Management.Automation.CmdletAttribute](/dotnet/api/System.Management.Automation.CmdletAttribute) attribute by setting the SupportsShouldProcess keyword to `true`.</span></span>

- <span data-ttu-id="dbf57-107">Chiamare [System. Management. Automation. cmdlet. ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) durante l'esecuzione del cmdlet (come illustrato nell'esempio seguente).</span><span class="sxs-lookup"><span data-stu-id="dbf57-107">Call [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) during the execution of the cmdlet (as shown in the following example).</span></span>

<span data-ttu-id="dbf57-108">Grazie al supporto della conferma, un cmdlet espone i parametri `Confirm` e `WhatIf` forniti da Windows PowerShell e soddisfa anche le linee guida di sviluppo per i cmdlet. per ulteriori informazioni sulle linee guida per lo sviluppo di cmdlet, vedere [linee guida per lo](./cmdlet-development-guidelines.md)sviluppo di cmdlet.</span><span class="sxs-lookup"><span data-stu-id="dbf57-108">By supporting confirmation, a cmdlet exposes the `Confirm` and `WhatIf` parameters that are provided by Windows PowerShell, and also meets the development guidelines for cmdlets (For more information about cmdlet development guidelines, see [Cmdlet Development Guidelines](./cmdlet-development-guidelines.md).).</span></span>

## <a name="changing-the-system"></a><span data-ttu-id="dbf57-109">Modifica del sistema</span><span class="sxs-lookup"><span data-stu-id="dbf57-109">Changing the System</span></span>

<span data-ttu-id="dbf57-110">L'azione di "modifica del sistema" si riferisce a qualsiasi cmdlet che potenzialmente modifica lo stato del sistema al di fuori di Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="dbf57-110">The act of "changing the system" refers to any cmdlet that potentially changes the state of the system outside Windows PowerShell.</span></span> <span data-ttu-id="dbf57-111">Ad esempio, l'arresto di un processo, l'abilitazione o la disabilitazione di un account utente o l'aggiunta di una riga a una tabella di database sono tutte modifiche al sistema che devono essere confermate.</span><span class="sxs-lookup"><span data-stu-id="dbf57-111">For example, stopping a process, enabling or disabling a user account, or adding a row to a database table are all changes to the system that should be confirmed.</span></span> <span data-ttu-id="dbf57-112">Al contrario, le operazioni di lettura dei dati o di stabilire connessioni temporanee non cambiano il sistema e in genere non richiedono la conferma.</span><span class="sxs-lookup"><span data-stu-id="dbf57-112">In contrast, operations that read data or establish transient connections do not change the system and generally do not require confirmation.</span></span> <span data-ttu-id="dbf57-113">Non è inoltre necessaria una conferma per le azioni il cui effetto è limitato all'interno del runtime di Windows PowerShell, ad esempio `set-variable`.</span><span class="sxs-lookup"><span data-stu-id="dbf57-113">Confirmation is also not needed for actions whose effect is limited to inside the Windows PowerShell runtime, such as `set-variable`.</span></span> <span data-ttu-id="dbf57-114">I cmdlet che potrebbero o meno apportare una modifica permanente devono dichiarare `SupportsShouldProcess` e chiamare [System. Management. Automation. cmdlet. ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) solo se stanno per apportare una modifica permanente.</span><span class="sxs-lookup"><span data-stu-id="dbf57-114">Cmdlets that might or might not make a persistent change should declare `SupportsShouldProcess` and call [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) only if they are about to make a persistent change.</span></span>

> [!NOTE]
> <span data-ttu-id="dbf57-115">La conferma ShouldProcess si applica solo ai cmdlet.</span><span class="sxs-lookup"><span data-stu-id="dbf57-115">ShouldProcess confirmation applies only to cmdlets.</span></span> <span data-ttu-id="dbf57-116">Se un comando o uno script modifica lo stato di esecuzione di un sistema chiamando direttamente i metodi o le proprietà .NET oppure chiamando le applicazioni all'esterno di Windows PowerShell, questo tipo di conferma non sarà disponibile.</span><span class="sxs-lookup"><span data-stu-id="dbf57-116">If a command or script modifies the running state of a system by directly calling .NET methods or properties, or by calling applications outside of Windows PowerShell, this form of confirmation will not be available.</span></span>

## <a name="the-stopproc-cmdlet"></a><span data-ttu-id="dbf57-117">Cmdlet StopProc</span><span class="sxs-lookup"><span data-stu-id="dbf57-117">The StopProc Cmdlet</span></span>

<span data-ttu-id="dbf57-118">Questo argomento descrive un cmdlet Stop-proc che tenta di arrestare i processi recuperati usando il cmdlet Get-proc, descritto in [creazione del primo cmdlet](./creating-a-cmdlet-without-parameters.md).</span><span class="sxs-lookup"><span data-stu-id="dbf57-118">This topic describes a Stop-Proc cmdlet that attempts to stop processes that are retrieved using the Get-Proc cmdlet (described in [Creating Your First Cmdlet](./creating-a-cmdlet-without-parameters.md)).</span></span>

## <a name="defining-the-cmdlet"></a><span data-ttu-id="dbf57-119">Definizione del cmdlet</span><span class="sxs-lookup"><span data-stu-id="dbf57-119">Defining the Cmdlet</span></span>

<span data-ttu-id="dbf57-120">Il primo passaggio nella creazione di cmdlet è sempre il nome del cmdlet e la dichiarazione della classe .NET che implementa il cmdlet.</span><span class="sxs-lookup"><span data-stu-id="dbf57-120">The first step in cmdlet creation is always naming the cmdlet and declaring the .NET class that implements the cmdlet.</span></span> <span data-ttu-id="dbf57-121">Poiché si sta scrivendo un cmdlet per modificare il sistema, è necessario denominarlo di conseguenza.</span><span class="sxs-lookup"><span data-stu-id="dbf57-121">Because you are writing a cmdlet to change the system, it should be named accordingly.</span></span> <span data-ttu-id="dbf57-122">Questo cmdlet interrompe i processi di sistema, quindi il nome del verbo scelto qui è "Stop", definito dalla classe [System. Management. Automation. Verbslifecycle](/dotnet/api/System.Management.Automation.VerbsLifeCycle) , con il sostantivo "proc" per indicare che il cmdlet interrompe i processi.</span><span class="sxs-lookup"><span data-stu-id="dbf57-122">This cmdlet stops system processes, so the verb name chosen here is "Stop", defined by the [System.Management.Automation.Verbslifecycle](/dotnet/api/System.Management.Automation.VerbsLifeCycle) class, with the noun "Proc" to indicate that the cmdlet stops processes.</span></span> <span data-ttu-id="dbf57-123">Per altre informazioni sui verbi di cmdlet approvati, vedere [nomi dei verbi di cmdlet](./approved-verbs-for-windows-powershell-commands.md).</span><span class="sxs-lookup"><span data-stu-id="dbf57-123">For more information about approved cmdlet verbs, see [Cmdlet Verb Names](./approved-verbs-for-windows-powershell-commands.md).</span></span>

<span data-ttu-id="dbf57-124">Di seguito è riportata la definizione della classe per il cmdlet Stop-proc.</span><span class="sxs-lookup"><span data-stu-id="dbf57-124">The following is the class definition for this Stop-Proc cmdlet.</span></span>

```csharp
[Cmdlet(VerbsLifecycle.Stop, "Proc",
        SupportsShouldProcess = true)]
public class StopProcCommand : Cmdlet
```

<span data-ttu-id="dbf57-125">Tenere presente che nella Dichiarazione [System. Management. Automation. CmdletAttribute](/dotnet/api/System.Management.Automation.CmdletAttribute) la parola chiave `SupportsShouldProcess` attribute è impostata su `true` per consentire al cmdlet di effettuare chiamate a [System. Management. Automation. cmdlet. ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) e [System. Management. Automation. cmdlet. ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue).</span><span class="sxs-lookup"><span data-stu-id="dbf57-125">Be aware that in the [System.Management.Automation.CmdletAttribute](/dotnet/api/System.Management.Automation.CmdletAttribute) declaration, the `SupportsShouldProcess` attribute keyword is set to `true` to enable the cmdlet to make calls to [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) and [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue).</span></span> <span data-ttu-id="dbf57-126">Senza questa parola chiave impostata, i parametri `Confirm` e `WhatIf` non saranno disponibili per l'utente.</span><span class="sxs-lookup"><span data-stu-id="dbf57-126">Without this keyword set, the `Confirm` and `WhatIf` parameters will not be available to the user.</span></span>

### <a name="extremely-destructive-actions"></a><span data-ttu-id="dbf57-127">Azioni estremamente distruttive</span><span class="sxs-lookup"><span data-stu-id="dbf57-127">Extremely Destructive Actions</span></span>

<span data-ttu-id="dbf57-128">Alcune operazioni sono estremamente distruttive, ad esempio la riformattazione di una partizione del disco rigido attiva.</span><span class="sxs-lookup"><span data-stu-id="dbf57-128">Some operations are extremely destructive, such as reformatting an active hard disk partition.</span></span> <span data-ttu-id="dbf57-129">In questi casi, il cmdlet deve impostare `ConfirmImpact` = `ConfirmImpact.High` quando dichiara l'attributo [System. Management. Automation. CmdletAttribute](/dotnet/api/System.Management.Automation.CmdletAttribute) .</span><span class="sxs-lookup"><span data-stu-id="dbf57-129">In these cases, the cmdlet should set `ConfirmImpact` = `ConfirmImpact.High` when declaring the [System.Management.Automation.CmdletAttribute](/dotnet/api/System.Management.Automation.CmdletAttribute) attribute.</span></span> <span data-ttu-id="dbf57-130">Questa impostazione impone al cmdlet di richiedere la conferma dell'utente anche quando l'utente non ha specificato il parametro `Confirm`.</span><span class="sxs-lookup"><span data-stu-id="dbf57-130">This setting forces the cmdlet to request user confirmation even when the user has not specified the `Confirm` parameter.</span></span> <span data-ttu-id="dbf57-131">Tuttavia, gli sviluppatori di cmdlet devono evitare di usare `ConfirmImpact` per operazioni potenzialmente distruttive, ad esempio l'eliminazione di un account utente.</span><span class="sxs-lookup"><span data-stu-id="dbf57-131">However, cmdlet developers should avoid overusing `ConfirmImpact` for operations that are just potentially destructive, such as deleting a user account.</span></span> <span data-ttu-id="dbf57-132">Tenere presente che se `ConfirmImpact` è impostato su [System. Management. Automation. ConfirmImpact](/dotnet/api/System.Management.Automation.ConfirmImpact) **High**.</span><span class="sxs-lookup"><span data-stu-id="dbf57-132">Remember that if `ConfirmImpact` is set to [System.Management.Automation.ConfirmImpact](/dotnet/api/System.Management.Automation.ConfirmImpact) **High**.</span></span>

<span data-ttu-id="dbf57-133">Analogamente, è improbabile che alcune operazioni siano distruttive, sebbene in teoria modifichino lo stato di esecuzione di un sistema al di fuori di Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="dbf57-133">Similarly, some operations are unlikely to be destructive, although they do in theory modify the running state of a system outside Windows PowerShell.</span></span> <span data-ttu-id="dbf57-134">Questi cmdlet possono impostare `ConfirmImpact` su [System. Management. Automation. ConfirmImpact. Low](/dotnet/api/system.management.automation.confirmimpact?view=powershellsdk-1.1.0).</span><span class="sxs-lookup"><span data-stu-id="dbf57-134">Such cmdlets can set `ConfirmImpact` to [System.Management.Automation.Confirmimpact.Low](/dotnet/api/system.management.automation.confirmimpact?view=powershellsdk-1.1.0).</span></span> <span data-ttu-id="dbf57-135">Questa operazione consente di ignorare le richieste di conferma in cui l'utente ha richiesto di confermare solo le operazioni a medio e a elevato utilizzo.</span><span class="sxs-lookup"><span data-stu-id="dbf57-135">This will bypass confirmation requests where the user has asked to confirm only medium-impact and high-impact operations.</span></span>

## <a name="defining-parameters-for-system-modification"></a><span data-ttu-id="dbf57-136">Definizione dei parametri per la modifica del sistema</span><span class="sxs-lookup"><span data-stu-id="dbf57-136">Defining Parameters for System Modification</span></span>

<span data-ttu-id="dbf57-137">In questa sezione viene descritto come definire i parametri del cmdlet, inclusi quelli necessari per supportare la modifica del sistema.</span><span class="sxs-lookup"><span data-stu-id="dbf57-137">This section describes how to define the cmdlet parameters, including those that are needed to support system modification.</span></span> <span data-ttu-id="dbf57-138">Per informazioni generali sulla definizione dei parametri, vedere [aggiunta di parametri che elaborano l'input della riga](./adding-parameters-that-process-command-line-input.md) di comando.</span><span class="sxs-lookup"><span data-stu-id="dbf57-138">See [Adding Parameters that Process CommandLine Input](./adding-parameters-that-process-command-line-input.md) if you need general information about defining parameters.</span></span>

<span data-ttu-id="dbf57-139">Il cmdlet Stop-proc definisce tre parametri: `Name`, `Force`e `PassThru`.</span><span class="sxs-lookup"><span data-stu-id="dbf57-139">The Stop-Proc cmdlet defines three parameters: `Name`, `Force`, and `PassThru`.</span></span>

<span data-ttu-id="dbf57-140">Il parametro `Name` corrisponde alla proprietà `Name` dell'oggetto di input del processo.</span><span class="sxs-lookup"><span data-stu-id="dbf57-140">The `Name` parameter corresponds to the `Name` property of the process input object.</span></span> <span data-ttu-id="dbf57-141">Tenere presente che il parametro `Name` in questo esempio è obbligatorio, in quanto il cmdlet avrà esito negativo se non è presente un processo denominato da arrestare.</span><span class="sxs-lookup"><span data-stu-id="dbf57-141">Be aware that the `Name` parameter in this sample is mandatory, as the cmdlet will fail if it does not have a named process to stop.</span></span>

<span data-ttu-id="dbf57-142">Il parametro `Force` consente all'utente di eseguire l'override delle chiamate a [System. Management. Automation. cmdlet. ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue).</span><span class="sxs-lookup"><span data-stu-id="dbf57-142">The `Force` parameter allows the user to override calls to [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue).</span></span> <span data-ttu-id="dbf57-143">In realtà, qualsiasi cmdlet che chiama [System. Management. Automation. cmdlet. ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) deve avere un parametro `Force` in modo che, quando viene specificato `Force`, il cmdlet ignora la chiamata a [System. Management. Automation. cmdlet. ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) e procede con l'operazione.</span><span class="sxs-lookup"><span data-stu-id="dbf57-143">In fact, any cmdlet that calls [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) should have a `Force` parameter so that when `Force` is specified, the cmdlet skips the call to [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) and proceeds with the operation.</span></span> <span data-ttu-id="dbf57-144">Tenere presente che questa operazione non influisce sulle chiamate a [System. Management. Automation. cmdlet. ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess).</span><span class="sxs-lookup"><span data-stu-id="dbf57-144">Be aware that this does not affect calls to [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess).</span></span>

<span data-ttu-id="dbf57-145">Il `PassThru` parametro consente all'utente di indicare se il cmdlet passa un oggetto di output attraverso la pipeline, in questo caso, dopo l'arresto di un processo.</span><span class="sxs-lookup"><span data-stu-id="dbf57-145">The `PassThru` parameter allows the user to indicate whether the cmdlet passes an output object through the pipeline, in this case, after a process is stopped.</span></span> <span data-ttu-id="dbf57-146">Tenere presente che questo parametro è associato al cmdlet stesso anziché a una proprietà dell'oggetto di input.</span><span class="sxs-lookup"><span data-stu-id="dbf57-146">Be aware that this parameter is tied to the cmdlet itself instead of to a property of the input object.</span></span>

<span data-ttu-id="dbf57-147">Di seguito è illustrata la dichiarazione di parametro per il cmdlet Stop-proc.</span><span class="sxs-lookup"><span data-stu-id="dbf57-147">Here is the parameter declaration for the Stop-Proc cmdlet.</span></span>

```csharp
[Parameter(
           Position = 0,
           Mandatory = true,
           ValueFromPipeline = true,
           ValueFromPipelineByPropertyName = true
)]
public string[] Name
{
  get { return processNames; }
  set { processNames = value; }
}
private string[] processNames;

/// <summary>
/// Specify the Force parameter that allows the user to override
/// the ShouldContinue call to force the stop operation. This
/// parameter should always be used with caution.
/// </summary>
[Parameter]
public SwitchParameter Force
{
  get { return force; }
  set { force = value; }
}
private bool force;

/// <summary>
/// Specify the PassThru parameter that allows the user to specify
/// that the cmdlet should pass the process object down the pipeline
/// after the process has been stopped.
/// </summary>
[Parameter]
public SwitchParameter PassThru
{
  get { return passThru; }
  set { passThru = value; }
}
private bool passThru;
```

## <a name="overriding-an-input-processing-method"></a><span data-ttu-id="dbf57-148">Override di un metodo di elaborazione dell'input</span><span class="sxs-lookup"><span data-stu-id="dbf57-148">Overriding an Input Processing Method</span></span>

<span data-ttu-id="dbf57-149">Il cmdlet deve eseguire l'override di un metodo di elaborazione dell'input.</span><span class="sxs-lookup"><span data-stu-id="dbf57-149">The cmdlet must override an input processing method.</span></span> <span data-ttu-id="dbf57-150">Il codice seguente illustra l'override di [System. Management. Automation. cmdlet. ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) usato nel cmdlet Stop-proc di esempio.</span><span class="sxs-lookup"><span data-stu-id="dbf57-150">The following code illustrates the [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) override used in the sample Stop-Proc cmdlet.</span></span> <span data-ttu-id="dbf57-151">Per ogni nome di processo richiesto, questo metodo garantisce che il processo non sia un processo speciale, tenta di arrestare il processo e quindi Invia un oggetto di output se viene specificato il parametro `PassThru`.</span><span class="sxs-lookup"><span data-stu-id="dbf57-151">For each requested process name, this method ensures that the process is not a special process, tries to stop the process, and then sends an output object if the `PassThru` parameter is specified.</span></span>

```csharp
protected override void ProcessRecord()
{
  foreach (string name in processNames)
  {
    // For every process name passed to the cmdlet, get the associated
    // process(es). For failures, write a non-terminating error
    Process[] processes;

    try
    {
      processes = Process.GetProcessesByName(name);
    }
    catch (InvalidOperationException ioe)
    {
      WriteError(new ErrorRecord(ioe,"Unable to access the target process by name",
                 ErrorCategory.InvalidOperation, name));
      continue;
    }

    // Try to stop the process(es) that have been retrieved for a name
    foreach (Process process in processes)
    {
      string processName;

      try
      {
        processName = process.ProcessName;
      }

      catch (Win32Exception e)
        {
          WriteError(new ErrorRecord(e, "ProcessNameNotFound",
                     ErrorCategory.ReadError, process));
          continue;
        }

        // Call Should Process to confirm the operation first.
        // This is always false if WhatIf is set.
        if (!ShouldProcess(string.Format("{0} ({1})", processName,
                           process.Id)))
        {
          continue;
        }
        // Call ShouldContinue to make sure the user really does want
        // to stop a critical process that could possibly stop the computer.
        bool criticalProcess =
             criticalProcessNames.Contains(processName.ToLower());

        if (criticalProcess &&!force)
        {
          string message = String.Format
                ("The process \"{0}\" is a critical process and should not be stopped. Are you sure you wish to stop the process?",
                processName);

          // It is possible that ProcessRecord is called multiple times
          // when the Name parameter receives objects as input from the
          // pipeline. So to retain YesToAll and NoToAll input that the
          // user may enter across multiple calls to ProcessRecord, this
          // information is stored as private members of the cmdlet.
          if (!ShouldContinue(message, "Warning!",
                              ref yesToAll,
                              ref noToAll))
          {
            continue;
          }
        } // if (criticalProcess...
        // Stop the named process.
        try
        {
          process.Kill();
        }
        catch (Exception e)
        {
          if ((e is Win32Exception) || (e is SystemException) ||
              (e is InvalidOperationException))
          {
            // This process could not be stopped so write
            // a non-terminating error.
            string message = String.Format("{0} {1} {2}",
                             "Could not stop process \"", processName,
                             "\".");
            WriteError(new ErrorRecord(e, message,
                       ErrorCategory.CloseError, process));
                       continue;
          } // if ((e is...
          else throw;
        } // catch

        // If the PassThru parameter argument is
        // True, pass the terminated process on.
        if (passThru)
        {
          WriteObject(process);
        }
    } // foreach (Process...
  } // foreach (string...
} // ProcessRecord
```

## <a name="calling-the-shouldprocess-method"></a><span data-ttu-id="dbf57-152">Chiamata al metodo ShouldProcess</span><span class="sxs-lookup"><span data-stu-id="dbf57-152">Calling the ShouldProcess Method</span></span>

<span data-ttu-id="dbf57-153">Il metodo di elaborazione dell'input del cmdlet deve chiamare il metodo [System. Management. Automation. cmdlet. ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) per confermare l'esecuzione di un'operazione prima che venga apportata una modifica, ad esempio l'eliminazione di file, allo stato di esecuzione del sistema.</span><span class="sxs-lookup"><span data-stu-id="dbf57-153">The input processing method of your cmdlet should call the [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) method to confirm execution of an operation before a change (for example, deleting files) is made to the running state of the system.</span></span> <span data-ttu-id="dbf57-154">Ciò consente al runtime di Windows PowerShell di fornire il comportamento corretto "WhatIf" e "Confirm" all'interno della shell.</span><span class="sxs-lookup"><span data-stu-id="dbf57-154">This allows the Windows PowerShell runtime to supply the correct "WhatIf" and "Confirm" behavior within the shell.</span></span>

> [!NOTE]
> <span data-ttu-id="dbf57-155">Se un cmdlet dichiara che supporta deve elaborare e non riesce a eseguire la chiamata [System. Management. Automation. cmdlet. ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) , l'utente potrebbe modificare il sistema in modo imprevisto.</span><span class="sxs-lookup"><span data-stu-id="dbf57-155">If a cmdlet states that it supports should process and fails to make the [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) call, the user might modify the system unexpectedly.</span></span>

<span data-ttu-id="dbf57-156">La chiamata a [System. Management. Automation. cmdlet. ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) invia il nome della risorsa da modificare all'utente, con il runtime di Windows PowerShell che prende in considerazione le impostazioni della riga di comando o le variabili di preferenza per determinare gli elementi da visualizzare all'utente.</span><span class="sxs-lookup"><span data-stu-id="dbf57-156">The call to [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) sends the name of the resource to be changed to the user, with the Windows PowerShell runtime taking into account any command-line settings or preference variables in determining what should be displayed to the user.</span></span>

<span data-ttu-id="dbf57-157">Nell'esempio seguente viene illustrata la chiamata a [System. Management. Automation. cmdlet. ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) dall'override del metodo [System. Management. Automation. cmdlet. ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) nel cmdlet Stop-proc di esempio.</span><span class="sxs-lookup"><span data-stu-id="dbf57-157">The following example shows the call to [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) from the override of the [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) method in the sample Stop-Proc cmdlet.</span></span>

```csharp
if (!ShouldProcess(string.Format("{0} ({1})", processName,
                   process.Id)))
{
  continue;
}
```

## <a name="calling-the-shouldcontinue-method"></a><span data-ttu-id="dbf57-158">Chiamata al metodo ShouldContinue</span><span class="sxs-lookup"><span data-stu-id="dbf57-158">Calling the ShouldContinue Method</span></span>

<span data-ttu-id="dbf57-159">La chiamata al metodo [System. Management. Automation. cmdlet. ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) Invia un messaggio secondario all'utente.</span><span class="sxs-lookup"><span data-stu-id="dbf57-159">The call to the [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) method sends a secondary message to the user.</span></span> <span data-ttu-id="dbf57-160">Questa chiamata viene eseguita dopo che la chiamata a [System. Management. Automation. cmdlet. ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) restituisce `true` e se il parametro `Force` non è stato impostato su `true`.</span><span class="sxs-lookup"><span data-stu-id="dbf57-160">This call is made after the call to [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) returns `true` and if the `Force` parameter was not set to `true`.</span></span> <span data-ttu-id="dbf57-161">L'utente può quindi inviare commenti e suggerimenti per indicare se l'operazione deve essere continuata.</span><span class="sxs-lookup"><span data-stu-id="dbf57-161">The user can then provide feedback to say whether the operation should be continued.</span></span> <span data-ttu-id="dbf57-162">Il cmdlet chiama [System. Management. Automation. cmdlet. ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) come controllo aggiuntivo per le modifiche di sistema potenzialmente pericolose o quando si desidera fornire all'utente opzioni Sì-a-tutti e no-to-all.</span><span class="sxs-lookup"><span data-stu-id="dbf57-162">Your cmdlet calls [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) as an additional check for potentially dangerous system modifications or when you want to provide yes-to-all and no-to-all options to the user.</span></span>

<span data-ttu-id="dbf57-163">Nell'esempio seguente viene illustrata la chiamata a [System. Management. Automation. cmdlet. ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) dall'override del metodo [System. Management. Automation. cmdlet. ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) nel cmdlet Stop-proc di esempio.</span><span class="sxs-lookup"><span data-stu-id="dbf57-163">The following example shows the call to [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) from the override of the [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) method in the sample Stop-Proc cmdlet.</span></span>

```csharp
if (criticalProcess &&!force)
{
  string message = String.Format
        ("The process \"{0}\" is a critical process and should not be stopped. Are you sure you wish to stop the process?",
        processName);

  // It is possible that ProcessRecord is called multiple times
  // when the Name parameter receives objects as input from the
  // pipeline. So to retain YesToAll and NoToAll input that the
  // user may enter across multiple calls to ProcessRecord, this
  // information is stored as private members of the cmdlet.
  if (!ShouldContinue(message, "Warning!",
                      ref yesToAll,
                      ref noToAll))
  {
    continue;
  }
} // if (criticalProcess...
```

## <a name="stopping-input-processing"></a><span data-ttu-id="dbf57-164">Arresto dell'elaborazione dell'input</span><span class="sxs-lookup"><span data-stu-id="dbf57-164">Stopping Input Processing</span></span>

<span data-ttu-id="dbf57-165">Il metodo di elaborazione dell'input di un cmdlet che apporta modifiche al sistema deve fornire un modo per arrestare l'elaborazione dell'input.</span><span class="sxs-lookup"><span data-stu-id="dbf57-165">The input processing method of a cmdlet that makes system modifications must provide a way of stopping the processing of input.</span></span> <span data-ttu-id="dbf57-166">Nel caso di questo cmdlet Stop-proc, viene eseguita una chiamata dal metodo [System. Management. Automation. cmdlet. ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) al metodo [System. Diagnostics. Process. Kill \*](/dotnet/api/System.Diagnostics.Process.Kill) .</span><span class="sxs-lookup"><span data-stu-id="dbf57-166">In the case of this Stop-Proc cmdlet, a call is made from the [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) method to the [System.Diagnostics.Process.Kill\*](/dotnet/api/System.Diagnostics.Process.Kill) method.</span></span> <span data-ttu-id="dbf57-167">Poiché il parametro `PassThru` è impostato su `true`, [System. Management. Automation. cmdlet. ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) chiama anche [System. Management. Automation. cmdlet. WriteObject](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject) per inviare l'oggetto processo alla pipeline.</span><span class="sxs-lookup"><span data-stu-id="dbf57-167">Because the `PassThru` parameter is set to `true`, [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) also calls [System.Management.Automation.Cmdlet.WriteObject](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject) to send the process object to the pipeline.</span></span>

## <a name="code-sample"></a><span data-ttu-id="dbf57-168">Esempio di codice</span><span class="sxs-lookup"><span data-stu-id="dbf57-168">Code Sample</span></span>

<span data-ttu-id="dbf57-169">Per il codice C# di esempio completo, vedere l' [esempio StopProcessSample01](./stopprocesssample01-sample.md).</span><span class="sxs-lookup"><span data-stu-id="dbf57-169">For the complete C# sample code, see [StopProcessSample01 Sample](./stopprocesssample01-sample.md).</span></span>

## <a name="defining-object-types-and-formatting"></a><span data-ttu-id="dbf57-170">Definizione di tipi di oggetti e formattazione</span><span class="sxs-lookup"><span data-stu-id="dbf57-170">Defining Object Types and Formatting</span></span>

<span data-ttu-id="dbf57-171">Windows PowerShell passa le informazioni tra i cmdlet usando gli oggetti .NET.</span><span class="sxs-lookup"><span data-stu-id="dbf57-171">Windows PowerShell passes information between cmdlets using .Net objects.</span></span> <span data-ttu-id="dbf57-172">Di conseguenza, un cmdlet può avere la necessità di definire un proprio tipo oppure il cmdlet deve estendere un tipo esistente fornito da un altro cmdlet.</span><span class="sxs-lookup"><span data-stu-id="dbf57-172">Consequently, a cmdlet may need to define its own type, or the cmdlet may need to extend an existing type provided by another cmdlet.</span></span> <span data-ttu-id="dbf57-173">Per ulteriori informazioni sulla definizione di nuovi tipi o sull'estensione di tipi esistenti, vedere [estensione di tipi di oggetti e formattazione](/previous-versions//ms714665(v=vs.85)).</span><span class="sxs-lookup"><span data-stu-id="dbf57-173">For more information about defining new types or extending existing types, see [Extending Object Types and Formatting](/previous-versions//ms714665(v=vs.85)).</span></span>

## <a name="building-the-cmdlet"></a><span data-ttu-id="dbf57-174">Compilazione del cmdlet</span><span class="sxs-lookup"><span data-stu-id="dbf57-174">Building the Cmdlet</span></span>

<span data-ttu-id="dbf57-175">Dopo l'implementazione di un cmdlet, è necessario registrarlo con Windows PowerShell tramite uno snap-in di Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="dbf57-175">After implementing a cmdlet, it must be registered with Windows PowerShell through a Windows PowerShell snap-in.</span></span> <span data-ttu-id="dbf57-176">Per ulteriori informazioni sulla registrazione dei cmdlet, vedere [come registrare i cmdlet, i provider e le applicazioni host](/previous-versions//ms714644(v=vs.85)).</span><span class="sxs-lookup"><span data-stu-id="dbf57-176">For more information about registering cmdlets, see [How to Register Cmdlets, Providers, and Host Applications](/previous-versions//ms714644(v=vs.85)).</span></span>

## <a name="testing-the-cmdlet"></a><span data-ttu-id="dbf57-177">Test del cmdlet</span><span class="sxs-lookup"><span data-stu-id="dbf57-177">Testing the Cmdlet</span></span>

<span data-ttu-id="dbf57-178">Quando il cmdlet è stato registrato con Windows PowerShell, è possibile testarlo eseguendolo nella riga di comando.</span><span class="sxs-lookup"><span data-stu-id="dbf57-178">When your cmdlet has been registered with Windows PowerShell, you can test it by running it on the command line.</span></span> <span data-ttu-id="dbf57-179">Di seguito sono riportati diversi test che testano il cmdlet Stop-proc.</span><span class="sxs-lookup"><span data-stu-id="dbf57-179">Here are several tests that test the Stop-Proc cmdlet.</span></span> <span data-ttu-id="dbf57-180">Per ulteriori informazioni sull'utilizzo dei cmdlet dalla riga di comando, vedere la [Introduzione con Windows PowerShell](/powershell/scripting/getting-started/getting-started-with-windows-powershell).</span><span class="sxs-lookup"><span data-stu-id="dbf57-180">For more information about using cmdlets from the command line, see the [Getting Started with Windows PowerShell](/powershell/scripting/getting-started/getting-started-with-windows-powershell).</span></span>

- <span data-ttu-id="dbf57-181">Avviare Windows PowerShell e usare il cmdlet Stop-proc per arrestare l'elaborazione, come illustrato di seguito.</span><span class="sxs-lookup"><span data-stu-id="dbf57-181">Start Windows PowerShell and use the Stop-Proc cmdlet to stop processing as shown below.</span></span> <span data-ttu-id="dbf57-182">Poiché il cmdlet specifica il parametro `Name` come obbligatorio, il cmdlet esegue una query per il parametro.</span><span class="sxs-lookup"><span data-stu-id="dbf57-182">Because the cmdlet specifies the `Name` parameter as mandatory, the cmdlet queries for the parameter.</span></span>

    ```powershell
    PS> stop-proc
    ```

<span data-ttu-id="dbf57-183">Viene visualizzato l'output seguente.</span><span class="sxs-lookup"><span data-stu-id="dbf57-183">The following output appears.</span></span>

    ```
    Cmdlet stop-proc at command pipeline position 1
    Supply values for the following parameters:
    Name[0]:
    ```

- <span data-ttu-id="dbf57-184">A questo punto è possibile usare il cmdlet per arrestare il processo denominato "blocco note".</span><span class="sxs-lookup"><span data-stu-id="dbf57-184">Now let's use the cmdlet to stop the process named "NOTEPAD".</span></span> <span data-ttu-id="dbf57-185">Il cmdlet richiede di confermare l'azione.</span><span class="sxs-lookup"><span data-stu-id="dbf57-185">The cmdlet asks you to confirm the action.</span></span>

    ```powershell
    PS> stop-proc -Name notepad
    ```

<span data-ttu-id="dbf57-186">Viene visualizzato l'output seguente.</span><span class="sxs-lookup"><span data-stu-id="dbf57-186">The following output appears.</span></span>

    ```
    Confirm
    Are you sure you want to perform this action?
    Performing operation "stop-proc" on Target "notepad (4996)".
    [Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"): Y
    ```

- <span data-ttu-id="dbf57-187">Usare stop-proc come illustrato per arrestare il processo critico denominato "WINLOGON".</span><span class="sxs-lookup"><span data-stu-id="dbf57-187">Use Stop-Proc as shown to stop the critical process named "WINLOGON".</span></span> <span data-ttu-id="dbf57-188">Viene richiesto e visualizzato un avviso relativo all'esecuzione di questa azione perché il sistema operativo verrà riavviato.</span><span class="sxs-lookup"><span data-stu-id="dbf57-188">You are prompted and warned about performing this action because it will cause the operating system to reboot.</span></span>

    ```powershell
    PS> stop-proc -Name Winlogon
    ```

<span data-ttu-id="dbf57-189">Viene visualizzato l'output seguente.</span><span class="sxs-lookup"><span data-stu-id="dbf57-189">The following output appears.</span></span>

    ```output
    Confirm
    Are you sure you want to perform this action?
    Performing operation "stop-proc" on Target "winlogon (656)".
    [Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"): Y
    Warning!
    The process " winlogon " is a critical process and should not be stopped. Are you sure you wish to stop the process?
    [Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"): N
    ```

- <span data-ttu-id="dbf57-190">A questo punto, provare ad arrestare il processo WINLOGON senza ricevere un avviso.</span><span class="sxs-lookup"><span data-stu-id="dbf57-190">Let's now try to stop the WINLOGON process without receiving a warning.</span></span> <span data-ttu-id="dbf57-191">Tenere presente che questa voce di comando usa il parametro `Force` per eseguire l'override dell'avviso.</span><span class="sxs-lookup"><span data-stu-id="dbf57-191">Be aware that this command entry uses the `Force` parameter to override the warning.</span></span>

    ```powershell
    PS> stop-proc -Name winlogon -Force
    ```

<span data-ttu-id="dbf57-192">Viene visualizzato l'output seguente.</span><span class="sxs-lookup"><span data-stu-id="dbf57-192">The following output appears.</span></span>

    ```output
    Confirm
    Are you sure you want to perform this action?
    Performing operation "stop-proc" on Target "winlogon (656)".
    [Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"): N
    ```

## <a name="see-also"></a><span data-ttu-id="dbf57-193">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="dbf57-193">See Also</span></span>

[<span data-ttu-id="dbf57-194">Aggiunta di parametri che elaborano l'input della riga di comando</span><span class="sxs-lookup"><span data-stu-id="dbf57-194">Adding Parameters that Process Command-Line Input</span></span>](./adding-parameters-that-process-command-line-input.md)

<span data-ttu-id="dbf57-195">[Estensione di tipi di oggetti e formattazione](/previous-versions//ms714665(v=vs.85))</span><span class="sxs-lookup"><span data-stu-id="dbf57-195">[Extending Object Types and Formatting](/previous-versions//ms714665(v=vs.85))</span></span>

<span data-ttu-id="dbf57-196">[Come registrare cmdlet, provider e applicazioni host](/previous-versions//ms714644(v=vs.85))</span><span class="sxs-lookup"><span data-stu-id="dbf57-196">[How to Register Cmdlets, Providers, and Host Applications](/previous-versions//ms714644(v=vs.85))</span></span>

[<span data-ttu-id="dbf57-197">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="dbf57-197">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)

[<span data-ttu-id="dbf57-198">Esempi di cmdlet</span><span class="sxs-lookup"><span data-stu-id="dbf57-198">Cmdlet Samples</span></span>](./cmdlet-samples.md)