---
title: Creazione di un Cmdlet che modifichi il sistema | Microsoft Docs
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
ms.openlocfilehash: d93cc4a05a6625d073791c067d1e9b6662c3a565
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/03/2019
ms.locfileid: "56856337"
---
# <a name="creating-a-cmdlet-that-modifies-the-system"></a><span data-ttu-id="0bddd-102">Creazione di un cmdlet che modifica il sistema</span><span class="sxs-lookup"><span data-stu-id="0bddd-102">Creating a Cmdlet that Modifies the System</span></span>

<span data-ttu-id="0bddd-103">In alcuni casi un cmdlet è necessario modificare lo stato del sistema, non solo lo stato del runtime di Windows PowerShell in esecuzione.</span><span class="sxs-lookup"><span data-stu-id="0bddd-103">Sometimes a cmdlet must modify the running state of the system, not just the state of the Windows PowerShell runtime.</span></span> <span data-ttu-id="0bddd-104">In questi casi, il cmdlet deve consentire all'utente la possibilità di confermare se apportare la modifica o meno.</span><span class="sxs-lookup"><span data-stu-id="0bddd-104">In these cases, the cmdlet should allow the user a chance to confirm whether or not to make the change.</span></span>

<span data-ttu-id="0bddd-105">Per supportare la conferma un cmdlet deve fare due cose.</span><span class="sxs-lookup"><span data-stu-id="0bddd-105">To support confirmation a cmdlet must do two things.</span></span>

- <span data-ttu-id="0bddd-106">Dichiarare che il cmdlet supporta conferma quando si specifica la [System.Management.Automation.Cmdletattribute](/dotnet/api/System.Management.Automation.CmdletAttribute) attributo impostando la parola chiave SupportsShouldProcess su `true`.</span><span class="sxs-lookup"><span data-stu-id="0bddd-106">Declare that the cmdlet supports confirmation when you specify the [System.Management.Automation.Cmdletattribute](/dotnet/api/System.Management.Automation.CmdletAttribute) attribute by setting the SupportsShouldProcess keyword to `true`.</span></span>

- <span data-ttu-id="0bddd-107">Chiamare [System.Management.Automation.Cmdlet.Shouldprocess\*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) durante l'esecuzione del cmdlet (come illustrato nell'esempio seguente).</span><span class="sxs-lookup"><span data-stu-id="0bddd-107">Call [System.Management.Automation.Cmdlet.Shouldprocess\*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) during the execution of the cmdlet (as shown in the following example).</span></span>

<span data-ttu-id="0bddd-108">Grazie al supporto di conferma, espone un cmdlet di `Confirm` e `WhatIf` parametri che vengono forniti da Windows PowerShell e anche soddisfano le linee guida sullo sviluppo per i cmdlet (per altre informazioni sulle linee guida sullo sviluppo di cmdlet, vedere [ Linee guida sullo sviluppo di cmdlet](./cmdlet-development-guidelines.md).).</span><span class="sxs-lookup"><span data-stu-id="0bddd-108">By supporting confirmation, a cmdlet exposes the `Confirm` and `WhatIf` parameters that are provided by Windows PowerShell, and also meets the development guidelines for cmdlets (For more information about cmdlet development guidelines, see [Cmdlet Development Guidelines](./cmdlet-development-guidelines.md).).</span></span>

## <a name="changing-the-system"></a><span data-ttu-id="0bddd-109">La modifica del sistema</span><span class="sxs-lookup"><span data-stu-id="0bddd-109">Changing the System</span></span>

<span data-ttu-id="0bddd-110">L'atto di "modifica il sistema" si riferisce a tutti i cmdlet che potenzialmente modifica lo stato del sistema di fuori di Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="0bddd-110">The act of "changing the system" refers to any cmdlet that potentially changes the state of the system outside Windows PowerShell.</span></span> <span data-ttu-id="0bddd-111">Ad esempio, l'arresto di un processo, Abilita o disabilita un account utente o aggiunta di una riga a una tabella di database sono tutte le modifiche apportate al sistema che deve essere confermata.</span><span class="sxs-lookup"><span data-stu-id="0bddd-111">For example, stopping a process, enabling or disabling a user account, or adding a row to a database table are all changes to the system that should be confirmed.</span></span> <span data-ttu-id="0bddd-112">Operazioni di lettura dei dati o stabiliscono le connessioni temporanee, invece, non modificare il sistema e in genere non necessitano di una conferma.</span><span class="sxs-lookup"><span data-stu-id="0bddd-112">In contrast, operations that read data or establish transient connections do not change the system and generally do not require confirmation.</span></span> <span data-ttu-id="0bddd-113">Conferma non serve anche per le azioni il cui effetto è limitata all'interno del runtime di Windows PowerShell, ad esempio `set-variable`.</span><span class="sxs-lookup"><span data-stu-id="0bddd-113">Confirmation is also not needed for actions whose effect is limited to inside the Windows PowerShell runtime, such as `set-variable`.</span></span> <span data-ttu-id="0bddd-114">I cmdlet che possono o non potrebbero apportare una modifica permanente devono dichiarare `SupportsShouldProcess` e chiamare [System.Management.Automation.Cmdlet.Shouldprocess\*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) solo se si sta tentando di apportare una modifica permanente.</span><span class="sxs-lookup"><span data-stu-id="0bddd-114">Cmdlets that might or might not make a persistent change should declare `SupportsShouldProcess` and call [System.Management.Automation.Cmdlet.Shouldprocess\*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) only if they are about to make a persistent change.</span></span>

> [!NOTE]
> <span data-ttu-id="0bddd-115">Conferma ShouldProcess si applica solo ai cmdlet.</span><span class="sxs-lookup"><span data-stu-id="0bddd-115">ShouldProcess confirmation applies only to cmdlets.</span></span> <span data-ttu-id="0bddd-116">Se un comando o lo script modifica lo stato in esecuzione di un sistema chiamando direttamente i metodi .NET o proprietà o da applicazioni chiamanti all'esterno di Windows PowerShell, questa forma di conferma non saranno disponibile.</span><span class="sxs-lookup"><span data-stu-id="0bddd-116">If a command or script modifies the running state of a system by directly calling .NET methods or properties, or by calling applications outside of Windows PowerShell, this form of confirmation will not be available.</span></span>

## <a name="the-stopproc-cmdlet"></a><span data-ttu-id="0bddd-117">Il StopProc Cmdlet</span><span class="sxs-lookup"><span data-stu-id="0bddd-117">The StopProc Cmdlet</span></span>

<span data-ttu-id="0bddd-118">Questo argomento viene descritto un cmdlet Stop-Process che tenta di arrestare i processi che vengono recuperati usando il cmdlet Get-Proc (descritto nella [la creazione del primo Cmdlet](./creating-a-cmdlet-without-parameters.md)).</span><span class="sxs-lookup"><span data-stu-id="0bddd-118">This topic describes a Stop-Proc cmdlet that attempts to stop processes that are retrieved using the Get-Proc cmdlet (described in [Creating Your First Cmdlet](./creating-a-cmdlet-without-parameters.md)).</span></span>

<span data-ttu-id="0bddd-119">Gli argomenti in questa sezione includono quanto segue:</span><span class="sxs-lookup"><span data-stu-id="0bddd-119">Topics in this section include the following:</span></span>

- [<span data-ttu-id="0bddd-120">Che definisce il Cmdlet</span><span class="sxs-lookup"><span data-stu-id="0bddd-120">Defining the Cmdlet</span></span>](#Defining-the-Cmdlet)

- [<span data-ttu-id="0bddd-121">Definizione dei parametri per la modifica di sistema</span><span class="sxs-lookup"><span data-stu-id="0bddd-121">Defining Parameters for System Modification</span></span>](#Defining-Parameters-for-System-Modification)

- [<span data-ttu-id="0bddd-122">Si esegue l'override di un metodo di elaborazione dell'Input</span><span class="sxs-lookup"><span data-stu-id="0bddd-122">Overriding an Input Processing Method</span></span>](#Overriding-an-Input-Processing-Method)

- [<span data-ttu-id="0bddd-123">La chiamata al metodo ShouldProcess</span><span class="sxs-lookup"><span data-stu-id="0bddd-123">Calling the ShouldProcess Method</span></span>](#Calling-the-ShouldProcess-Method)

- [<span data-ttu-id="0bddd-124">La chiamata al metodo ShouldContinue</span><span class="sxs-lookup"><span data-stu-id="0bddd-124">Calling the ShouldContinue Method</span></span>](#Calling-the-ShouldContinue-Method)

- [<span data-ttu-id="0bddd-125">Arresto l'elaborazione dell'Input</span><span class="sxs-lookup"><span data-stu-id="0bddd-125">Stopping Input Processing</span></span>](#Stopping-Input-Processing)

- [<span data-ttu-id="0bddd-126">Esempio di codice</span><span class="sxs-lookup"><span data-stu-id="0bddd-126">Code Sample</span></span>](#Code-Sample)

- [<span data-ttu-id="0bddd-127">Definizione di tipi di oggetto e formattazione</span><span class="sxs-lookup"><span data-stu-id="0bddd-127">Defining Object Types and Formatting</span></span>](#Defining-Object-Types-and-Formatting)

- [<span data-ttu-id="0bddd-128">Creazione di Cmdlet</span><span class="sxs-lookup"><span data-stu-id="0bddd-128">Building the Cmdlet</span></span>](#Building-the-Cmdlet)

- [<span data-ttu-id="0bddd-129">Il Cmdlet di test</span><span class="sxs-lookup"><span data-stu-id="0bddd-129">Testing the Cmdlet</span></span>](#Testing-the-Cmdlet)

## <a name="defining-the-cmdlet"></a><span data-ttu-id="0bddd-130">Che definisce il Cmdlet</span><span class="sxs-lookup"><span data-stu-id="0bddd-130">Defining the Cmdlet</span></span>

<span data-ttu-id="0bddd-131">Il primo passaggio nella creazione di cmdlet è sempre il cmdlet di denominazione e la dichiarazione di classe .NET che implementa il cmdlet.</span><span class="sxs-lookup"><span data-stu-id="0bddd-131">The first step in cmdlet creation is always naming the cmdlet and declaring the .NET class that implements the cmdlet.</span></span> <span data-ttu-id="0bddd-132">Poiché si sta scrivendo un cmdlet per modificare il sistema, devono essere denominato di conseguenza.</span><span class="sxs-lookup"><span data-stu-id="0bddd-132">Because you are writing a cmdlet to change the system, it should be named accordingly.</span></span> <span data-ttu-id="0bddd-133">Questo cmdlet arresta i processi di sistema, in modo che il nome del verbo selezionato qui è "Stop", definiti per il [System.Management.Automation.Verbslifecycle](/dotnet/api/System.Management.Automation.VerbsLifeCycle) (classe), con il sostantivo "Proc" per indicare che il cmdlet arresta i processi.</span><span class="sxs-lookup"><span data-stu-id="0bddd-133">This cmdlet stops system processes, so the verb name chosen here is "Stop", defined by the [System.Management.Automation.Verbslifecycle](/dotnet/api/System.Management.Automation.VerbsLifeCycle) class, with the noun "Proc" to indicate that the cmdlet stops processes.</span></span> <span data-ttu-id="0bddd-134">Per altre informazioni sui verbi approvati di cmdlet, vedere [nomi dei verbi di Cmdlet](./approved-verbs-for-windows-powershell-commands.md).</span><span class="sxs-lookup"><span data-stu-id="0bddd-134">For more information about approved cmdlet verbs, see [Cmdlet Verb Names](./approved-verbs-for-windows-powershell-commands.md).</span></span>

<span data-ttu-id="0bddd-135">Di seguito è la definizione della classe per questo cmdlet Stop-Process.</span><span class="sxs-lookup"><span data-stu-id="0bddd-135">The following is the class definition for this Stop-Proc cmdlet.</span></span>

```csharp
[Cmdlet(VerbsLifecycle.Stop, "Proc",
        SupportsShouldProcess = true)]
public class StopProcCommand : Cmdlet
```

<span data-ttu-id="0bddd-136">Tenere presente che nel [System.Management.Automation.Cmdletattribute](/dotnet/api/System.Management.Automation.CmdletAttribute) dichiarazione, il `SupportsShouldProcess` parola chiave di attributo è impostato su `true` per abilitare il cmdlet di effettuare chiamate a [ System.Management.Automation.Cmdlet.Shouldprocess\*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) e [System.Management.Automation.Cmdlet.Shouldcontinue\*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue).</span><span class="sxs-lookup"><span data-stu-id="0bddd-136">Be aware that in the [System.Management.Automation.Cmdletattribute](/dotnet/api/System.Management.Automation.CmdletAttribute) declaration, the `SupportsShouldProcess` attribute keyword is set to `true` to enable the cmdlet to make calls to [System.Management.Automation.Cmdlet.Shouldprocess\*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) and [System.Management.Automation.Cmdlet.Shouldcontinue\*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue).</span></span> <span data-ttu-id="0bddd-137">Senza questo set di parole chiave, il `Confirm` e `WhatIf` parametri non sarà disponibili per l'utente.</span><span class="sxs-lookup"><span data-stu-id="0bddd-137">Without this keyword set, the `Confirm` and `WhatIf` parameters will not be available to the user.</span></span>

### <a name="extremely-destructive-actions"></a><span data-ttu-id="0bddd-138">Azioni distruttive</span><span class="sxs-lookup"><span data-stu-id="0bddd-138">Extremely Destructive Actions</span></span>

<span data-ttu-id="0bddd-139">Alcune operazioni sono estremamente distruttive, ad esempio la riformattazione di una partizione disco rigido attivo.</span><span class="sxs-lookup"><span data-stu-id="0bddd-139">Some operations are extremely destructive, such as reformatting an active hard disk partition.</span></span> <span data-ttu-id="0bddd-140">In questi casi, è necessario impostare il cmdlet `ConfirmImpact`  =  `ConfirmImpact.High` quando si dichiara il [System.Management.Automation.Cmdletattribute](/dotnet/api/System.Management.Automation.CmdletAttribute) attributo.</span><span class="sxs-lookup"><span data-stu-id="0bddd-140">In these cases, the cmdlet should set `ConfirmImpact` = `ConfirmImpact.High` when declaring the [System.Management.Automation.Cmdletattribute](/dotnet/api/System.Management.Automation.CmdletAttribute) attribute.</span></span> <span data-ttu-id="0bddd-141">Questa impostazione forza il cmdlet per richiesta conferma all'utente, anche quando l'utente non ha specificato il `Confirm` parametro.</span><span class="sxs-lookup"><span data-stu-id="0bddd-141">This setting forces the cmdlet to request user confirmation even when the user has not specified the `Confirm` parameter.</span></span> <span data-ttu-id="0bddd-142">Tuttavia, gli sviluppatori di cmdlet devono evitare un uso eccessivo `ConfirmImpact` per le operazioni che sono semplicemente potenzialmente distruttive, ad esempio l'eliminazione di un account utente.</span><span class="sxs-lookup"><span data-stu-id="0bddd-142">However, cmdlet developers should avoid overusing `ConfirmImpact` for operations that are just potentially destructive, such as deleting a user account.</span></span> <span data-ttu-id="0bddd-143">Tenere presente che, se `ConfirmImpact` è impostata su [System.Management.Automation.Confirmimpact.High](/dotnet/api/System.Management.Automation.ConfirmImpact.High).</span><span class="sxs-lookup"><span data-stu-id="0bddd-143">Remember that if `ConfirmImpact` is set to [System.Management.Automation.Confirmimpact.High](/dotnet/api/System.Management.Automation.ConfirmImpact.High).</span></span>

<span data-ttu-id="0bddd-144">In modo analogo, alcune operazioni sono probabilmente non distruttiva, sebbene in teoria modificano tuttavia lo stato di un sistema all'esterno di Windows PowerShell in esecuzione.</span><span class="sxs-lookup"><span data-stu-id="0bddd-144">Similarly, some operations are unlikely to be destructive, although they do in theory modify the running state of a system outside Windows PowerShell.</span></span> <span data-ttu-id="0bddd-145">Questi cmdlet è possono impostare `ConfirmImpact` al [System.Management.Automation.Confirmimpact.Low](/dotnet/api/system.management.automation.confirmimpact?view=powershellsdk-1.1.0).</span><span class="sxs-lookup"><span data-stu-id="0bddd-145">Such cmdlets can set `ConfirmImpact` to [System.Management.Automation.Confirmimpact.Low](/dotnet/api/system.management.automation.confirmimpact?view=powershellsdk-1.1.0).</span></span> <span data-ttu-id="0bddd-146">Si possono ignorare le richieste di conferma in cui l'utente ha richiesto di confermare le operazioni di solo supporto a impatto e a impatto elevato.</span><span class="sxs-lookup"><span data-stu-id="0bddd-146">This will bypass confirmation requests where the user has asked to confirm only medium-impact and high-impact operations.</span></span>

## <a name="defining-parameters-for-system-modification"></a><span data-ttu-id="0bddd-147">Definizione dei parametri per la modifica di sistema</span><span class="sxs-lookup"><span data-stu-id="0bddd-147">Defining Parameters for System Modification</span></span>

<span data-ttu-id="0bddd-148">Questa sezione descrive come definire i parametri del cmdlet, inclusi quelli che sono necessari per la modifica di sistema di supporto.</span><span class="sxs-lookup"><span data-stu-id="0bddd-148">This section describes how to define the cmdlet parameters, including those that are needed to support system modification.</span></span> <span data-ttu-id="0bddd-149">Visualizzare [aggiunta di parametri di Input della riga di comando processo](./adding-parameters-that-process-command-line-input.md) se sono necessarie informazioni generali sulla definizione dei parametri.</span><span class="sxs-lookup"><span data-stu-id="0bddd-149">See [Adding Parameters that Process CommandLine Input](./adding-parameters-that-process-command-line-input.md) if you need general information about defining parameters.</span></span>

<span data-ttu-id="0bddd-150">Il cmdlet Stop-Process definisce tre parametri: `Name`, `Force`, e `PassThru`.</span><span class="sxs-lookup"><span data-stu-id="0bddd-150">The Stop-Proc cmdlet defines three parameters: `Name`, `Force`, and `PassThru`.</span></span>

<span data-ttu-id="0bddd-151">Il `Name` parametro corrisponde al `Name` proprietà dell'oggetto di input di processo.</span><span class="sxs-lookup"><span data-stu-id="0bddd-151">The `Name` parameter corresponds to the `Name` property of the process input object.</span></span> <span data-ttu-id="0bddd-152">Tenere presente che il `Name` in questo esempio il parametro è obbligatorio, come il cmdlet avrà esito negativo se non dispone di un processo denominato arrestare.</span><span class="sxs-lookup"><span data-stu-id="0bddd-152">Be aware that the `Name` parameter in this sample is mandatory, as the cmdlet will fail if it does not have a named process to stop.</span></span>

<span data-ttu-id="0bddd-153">Il `Force` parametro consente all'utente di eseguire l'override di chiamate a [System.Management.Automation.Cmdlet.Shouldcontinue\*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue).</span><span class="sxs-lookup"><span data-stu-id="0bddd-153">The `Force` parameter allows the user to override calls to [System.Management.Automation.Cmdlet.Shouldcontinue\*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue).</span></span> <span data-ttu-id="0bddd-154">In effetti, tutti i cmdlet che chiama [System.Management.Automation.Cmdlet.Shouldcontinue\*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) deve avere una `Force` parametri in modo che quando `Force` viene specificato, il cmdlet ignora la chiamata a [ System.Management.Automation.Cmdlet.Shouldcontinue\*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) e procede con l'operazione.</span><span class="sxs-lookup"><span data-stu-id="0bddd-154">In fact, any cmdlet that calls [System.Management.Automation.Cmdlet.Shouldcontinue\*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) should have a `Force` parameter so that when `Force` is specified, the cmdlet skips the call to [System.Management.Automation.Cmdlet.Shouldcontinue\*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) and proceeds with the operation.</span></span> <span data-ttu-id="0bddd-155">Tenere presente che questa operazione non influenza le chiamate a [System.Management.Automation.Cmdlet.Shouldprocess\*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess).</span><span class="sxs-lookup"><span data-stu-id="0bddd-155">Be aware that this does not affect calls to [System.Management.Automation.Cmdlet.Shouldprocess\*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess).</span></span>

<span data-ttu-id="0bddd-156">Il `PassThru` parametro consente all'utente di indicare se il cmdlet passa un oggetto di output tramite la pipeline, in questo caso, dopo un processo viene arrestato.</span><span class="sxs-lookup"><span data-stu-id="0bddd-156">The `PassThru` parameter allows the user to indicate whether the cmdlet passes an output object through the pipeline, in this case, after a process is stopped.</span></span> <span data-ttu-id="0bddd-157">Tenere presente che questo parametro è correlato al cmdlet stesso anziché a una proprietà dell'oggetto di input.</span><span class="sxs-lookup"><span data-stu-id="0bddd-157">Be aware that this parameter is tied to the cmdlet itself instead of to a property of the input object.</span></span>

<span data-ttu-id="0bddd-158">Ecco la dichiarazione di parametro per il cmdlet Stop-Process.</span><span class="sxs-lookup"><span data-stu-id="0bddd-158">Here is the parameter declaration for the Stop-Proc cmdlet.</span></span>

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

## <a name="overriding-an-input-processing-method"></a><span data-ttu-id="0bddd-159">Si esegue l'override di un metodo di elaborazione dell'Input</span><span class="sxs-lookup"><span data-stu-id="0bddd-159">Overriding an Input Processing Method</span></span>

<span data-ttu-id="0bddd-160">Il cmdlet deve eseguire l'override di un metodo di elaborazione dell'input.</span><span class="sxs-lookup"><span data-stu-id="0bddd-160">The cmdlet must override an input processing method.</span></span> <span data-ttu-id="0bddd-161">Il codice seguente illustra il [System.Management.Automation.Cmdlet.Processrecord\*](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) sostituzione usata nel cmdlet Stop-Process esempio.</span><span class="sxs-lookup"><span data-stu-id="0bddd-161">The following code illustrates the [System.Management.Automation.Cmdlet.Processrecord\*](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) override used in the sample Stop-Proc cmdlet.</span></span> <span data-ttu-id="0bddd-162">Per ogni richiesta di nome di processo, questo metodo garantisce che il processo non è un processo speciale, tenta di arrestare il processo e quindi invia un oggetto di output se il `PassThru` parametro è specificato.</span><span class="sxs-lookup"><span data-stu-id="0bddd-162">For each requested process name, this method ensures that the process is not a special process, tries to stop the process, and then sends an output object if the `PassThru` parameter is specified.</span></span>

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
          // when the Name parameter reveives objects as input from the
          // pipeline. So to retain YesToAll and NoToAll input that the
          // user may enter across mutilple calls to ProcessRecord, this
          // information is stored as private members of the cmdlet.
          if (!ShouldContinue(message, "Warning!",
                              ref yesToAll,
                              ref noToAll))
          {
            continue;
          }
        } // if (cricicalProcess...
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

## <a name="calling-the-shouldprocess-method"></a><span data-ttu-id="0bddd-163">La chiamata al metodo ShouldProcess</span><span class="sxs-lookup"><span data-stu-id="0bddd-163">Calling the ShouldProcess Method</span></span>

<span data-ttu-id="0bddd-164">Deve chiamare il metodo del cmdlet di elaborazione dell'input di [System.Management.Automation.Cmdlet.Shouldprocess\*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) metodo per confermare l'esecuzione di un'operazione prima che all'esecuzione viene apportata una modifica (ad esempio, l'eliminazione di file) stato del sistema.</span><span class="sxs-lookup"><span data-stu-id="0bddd-164">The input processing method of your cmdlet should call the [System.Management.Automation.Cmdlet.Shouldprocess\*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) method to confirm execution of an operation before a change (for example, deleting files) is made to the running state of the system.</span></span> <span data-ttu-id="0bddd-165">In questo modo il runtime di Windows PowerShell fornire il comportamento corretto "WhatIf" e "Conferma" all'interno della shell.</span><span class="sxs-lookup"><span data-stu-id="0bddd-165">This allows the Windows PowerShell runtime to supply the correct "WhatIf" and "Confirm" behavior within the shell.</span></span>

> [!NOTE]
> <span data-ttu-id="0bddd-166">Se un cmdlet indica il supporto deve essere elaborato e non riesce a eseguire la [System.Management.Automation.Cmdlet.Shouldprocess\*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) chiamare, l'utente può modificare il sistema in modo imprevisto.</span><span class="sxs-lookup"><span data-stu-id="0bddd-166">If a cmdlet states that it supports should process and fails to make the [System.Management.Automation.Cmdlet.Shouldprocess\*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) call, the user might modify the system unexpectedly.</span></span>

<span data-ttu-id="0bddd-167">La chiamata a [System.Management.Automation.Cmdlet.Shouldprocess\*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) invia il nome della risorsa da modificare per l'utente, con il runtime di Windows PowerShell prendendo in considerazione tutte le impostazioni della riga di comando o variabili di preferenza determinare ciò che deve essere visualizzato all'utente.</span><span class="sxs-lookup"><span data-stu-id="0bddd-167">The call to [System.Management.Automation.Cmdlet.Shouldprocess\*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) sends the name of the resource to be changed to the user, with the Windows PowerShell runtime taking into account any command-line settings or preference variables in determining what should be displayed to the user.</span></span>

<span data-ttu-id="0bddd-168">L'esempio seguente illustra la chiamata a [System.Management.Automation.Cmdlet.Shouldprocess\*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) dall'override del [System.Management.Automation.Cmdlet.Processrecord\*](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) metodo di esempio di cmdlet Stop-Process.</span><span class="sxs-lookup"><span data-stu-id="0bddd-168">The following example shows the call to [System.Management.Automation.Cmdlet.Shouldprocess\*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) from the override of the [System.Management.Automation.Cmdlet.Processrecord\*](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) method in the sample Stop-Proc cmdlet.</span></span>

```csharp
if (!ShouldProcess(string.Format("{0} ({1})", processName,
                   process.Id)))
{
  continue;
}
```

## <a name="calling-the-shouldcontinue-method"></a><span data-ttu-id="0bddd-169">La chiamata al metodo ShouldContinue</span><span class="sxs-lookup"><span data-stu-id="0bddd-169">Calling the ShouldContinue Method</span></span>

<span data-ttu-id="0bddd-170">La chiamata per il [System.Management.Automation.Cmdlet.Shouldcontinue\*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) metodo invia un messaggio secondario all'utente.</span><span class="sxs-lookup"><span data-stu-id="0bddd-170">The call to the [System.Management.Automation.Cmdlet.Shouldcontinue\*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) method sends a secondary message to the user.</span></span> <span data-ttu-id="0bddd-171">Questa chiamata viene eseguita dopo la chiamata a [System.Management.Automation.Cmdlet.Shouldprocess\*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) restituisce `true` e, se il `Force` parametro non è stato impostato su `true`.</span><span class="sxs-lookup"><span data-stu-id="0bddd-171">This call is made after the call to [System.Management.Automation.Cmdlet.Shouldprocess\*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) returns `true` and if the `Force` parameter was not set to `true`.</span></span> <span data-ttu-id="0bddd-172">L'utente può quindi fornire commenti e suggerimenti, ad esempio, se l'operazione deve proseguire.</span><span class="sxs-lookup"><span data-stu-id="0bddd-172">The user can then provide feedback to say whether the operation should be continued.</span></span> <span data-ttu-id="0bddd-173">Chiama il cmdlet [System.Management.Automation.Cmdlet.Shouldcontinue\*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) come un controllo aggiuntivo per le modifiche del sistema potenzialmente pericolose o quando si desidera fornire all'utente, le opzioni yes to all e no-to-all.</span><span class="sxs-lookup"><span data-stu-id="0bddd-173">Your cmdlet calls [System.Management.Automation.Cmdlet.Shouldcontinue\*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) as an additional check for potentially dangerous system modifications or when you want to provide yes-to-all and no-to-all options to the user.</span></span>

<span data-ttu-id="0bddd-174">L'esempio seguente illustra la chiamata a [System.Management.Automation.Cmdlet.Shouldcontinue\*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) dall'override del [System.Management.Automation.Cmdlet.Processrecord\*](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) metodo di esempio di cmdlet Stop-Process.</span><span class="sxs-lookup"><span data-stu-id="0bddd-174">The following example shows the call to [System.Management.Automation.Cmdlet.Shouldcontinue\*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) from the override of the [System.Management.Automation.Cmdlet.Processrecord\*](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) method in the sample Stop-Proc cmdlet.</span></span>

```csharp
if (criticalProcess &&!force)
{
  string message = String.Format
        ("The process \"{0}\" is a critical process and should not be stopped. Are you sure you wish to stop the process?",
        processName);

  // It is possible that ProcessRecord is called multiple times
  // when the Name parameter reveives objects as input from the
  // pipeline. So to retain YesToAll and NoToAll input that the
  // user may enter across mutilple calls to ProcessRecord, this
  // information is stored as private members of the cmdlet.
  if (!ShouldContinue(message, "Warning!",
                      ref yesToAll,
                      ref noToAll))
  {
    continue;
  }
} // if (cricicalProcess...
```

## <a name="stopping-input-processing"></a><span data-ttu-id="0bddd-175">Arresto l'elaborazione dell'Input</span><span class="sxs-lookup"><span data-stu-id="0bddd-175">Stopping Input Processing</span></span>

<span data-ttu-id="0bddd-176">Il metodo di un cmdlet che rende le modifiche di sistema di elaborazione dell'input è necessario fornire un modo per arrestare l'elaborazione dell'input.</span><span class="sxs-lookup"><span data-stu-id="0bddd-176">The input processing method of a cmdlet that makes system modifications must provide a way of stopping the processing of input.</span></span> <span data-ttu-id="0bddd-177">Nel caso di questo cmdlet Stop-Process, viene eseguita una chiamata dal [System.Management.Automation.Cmdlet.Processrecord\*](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) metodo per il [System.Diagnostics.Process.Kill\*](/dotnet/api/System.Diagnostics.Process.Kill) (metodo).</span><span class="sxs-lookup"><span data-stu-id="0bddd-177">In the case of this Stop-Proc cmdlet, a call is made from the [System.Management.Automation.Cmdlet.Processrecord\*](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) method to the [System.Diagnostics.Process.Kill\*](/dotnet/api/System.Diagnostics.Process.Kill) method.</span></span> <span data-ttu-id="0bddd-178">Poiché il `PassThru` parametro è impostato su `true`, [System.Management.Automation.Cmdlet.Processrecord\*](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) chiama inoltre [System.Management.Automation.Cmdlet.Writeobject\*](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject) a inviare l'oggetto processo per la pipeline.</span><span class="sxs-lookup"><span data-stu-id="0bddd-178">Because the `PassThru` parameter is set to `true`, [System.Management.Automation.Cmdlet.Processrecord\*](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) also calls [System.Management.Automation.Cmdlet.Writeobject\*](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject) to send the process object to the pipeline.</span></span>

## <a name="code-sample"></a><span data-ttu-id="0bddd-179">Esempio di codice</span><span class="sxs-lookup"><span data-stu-id="0bddd-179">Code Sample</span></span>

<span data-ttu-id="0bddd-180">Per l'intero C# esempi di codice, vedere [esempio StopProcessSample01](./stopprocesssample01-sample.md).</span><span class="sxs-lookup"><span data-stu-id="0bddd-180">For the complete C# sample code, see [StopProcessSample01 Sample](./stopprocesssample01-sample.md).</span></span>

## <a name="defining-object-types-and-formatting"></a><span data-ttu-id="0bddd-181">Definizione di tipi di oggetto e formattazione</span><span class="sxs-lookup"><span data-stu-id="0bddd-181">Defining Object Types and Formatting</span></span>

<span data-ttu-id="0bddd-182">Windows PowerShell passa informazioni tra i cmdlet con gli oggetti .net.</span><span class="sxs-lookup"><span data-stu-id="0bddd-182">Windows PowerShell passes information between cmdlets using .Net objects.</span></span> <span data-ttu-id="0bddd-183">Di conseguenza, potrebbe essere necessario definire un proprio tipo di un cmdlet o il cmdlet potrebbe essere necessario estendere un tipo esistente fornito da un altro cmdlet.</span><span class="sxs-lookup"><span data-stu-id="0bddd-183">Consequently, a cmdlet may need to define its own type, or the cmdlet may need to extend an existing type provided by another cmdlet.</span></span> <span data-ttu-id="0bddd-184">Per altre informazioni sulla definizione di nuovi tipi o estendere i tipi esistenti, vedere [estendendo i tipi di oggetto e formattazione](https://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351).</span><span class="sxs-lookup"><span data-stu-id="0bddd-184">For more information about defining new types or extending existing types, see [Extending Object Types and Formatting](https://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351).</span></span>

## <a name="building-the-cmdlet"></a><span data-ttu-id="0bddd-185">Creazione di Cmdlet</span><span class="sxs-lookup"><span data-stu-id="0bddd-185">Building the Cmdlet</span></span>

<span data-ttu-id="0bddd-186">Dopo l'implementazione di un cmdlet, è necessario registrarlo con Windows PowerShell tramite uno snap-in Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="0bddd-186">After implementing a cmdlet, it must be registered with Windows PowerShell through a Windows PowerShell snap-in.</span></span> <span data-ttu-id="0bddd-187">Per altre informazioni sulla registrazione dei cmdlet, vedere [come registrare i cmdlet, provider e applicazioni Host](https://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c).</span><span class="sxs-lookup"><span data-stu-id="0bddd-187">For more information about registering cmdlets, see [How to Register Cmdlets, Providers, and Host Applications](https://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c).</span></span>

## <a name="testing-the-cmdlet"></a><span data-ttu-id="0bddd-188">Il Cmdlet di test</span><span class="sxs-lookup"><span data-stu-id="0bddd-188">Testing the Cmdlet</span></span>

<span data-ttu-id="0bddd-189">Quando il cmdlet è stato registrato con Windows PowerShell, è possibile testarlo eseguendolo dalla riga di comando.</span><span class="sxs-lookup"><span data-stu-id="0bddd-189">When your cmdlet has been registered with Windows PowerShell, you can test it by running it on the command line.</span></span> <span data-ttu-id="0bddd-190">Ecco alcuni test che verificano il cmdlet Stop-Process.</span><span class="sxs-lookup"><span data-stu-id="0bddd-190">Here are several tests that test the Stop-Proc cmdlet.</span></span> <span data-ttu-id="0bddd-191">Per altre informazioni sull'utilizzo dei cmdlet dalla riga di comando, vedere la [Introduzione a Windows PowerShell](/powershell/scripting/getting-started/getting-started-with-windows-powershell).</span><span class="sxs-lookup"><span data-stu-id="0bddd-191">For more information about using cmdlets from the command line, see the [Getting Started with Windows PowerShell](/powershell/scripting/getting-started/getting-started-with-windows-powershell).</span></span>

- <span data-ttu-id="0bddd-192">Avviare Windows PowerShell e usare il cmdlet Stop-Process per arrestare l'elaborazione come illustrato di seguito.</span><span class="sxs-lookup"><span data-stu-id="0bddd-192">Start Windows PowerShell and use the Stop-Proc cmdlet to stop processing as shown below.</span></span> <span data-ttu-id="0bddd-193">Poiché il cmdlet specifica la `Name` parametro come obbligatorio, la query dei cmdlet per il parametro.</span><span class="sxs-lookup"><span data-stu-id="0bddd-193">Because the cmdlet specifies the `Name` parameter as mandatory, the cmdlet queries for the parameter.</span></span>

    ```powershell
    PS> stop-proc
    ```

<span data-ttu-id="0bddd-194">Viene visualizzato l'output seguente.</span><span class="sxs-lookup"><span data-stu-id="0bddd-194">The following output appears.</span></span>

    ```
    Cmdlet stop-proc at command pipeline position 1
    Supply values for the following parameters:
    Name[0]:
    ```

- <span data-ttu-id="0bddd-195">A questo punto è possibile usare il cmdlet per arrestare il processo denominato "NOTEPAD".</span><span class="sxs-lookup"><span data-stu-id="0bddd-195">Now let's use the cmdlet to stop the process named "NOTEPAD".</span></span> <span data-ttu-id="0bddd-196">Il cmdlet chiede di confermare l'azione.</span><span class="sxs-lookup"><span data-stu-id="0bddd-196">The cmdlet asks you to confirm the action.</span></span>

    ```powershell
    PS> stop-proc -Name notepad
    ```

<span data-ttu-id="0bddd-197">Viene visualizzato l'output seguente.</span><span class="sxs-lookup"><span data-stu-id="0bddd-197">The following output appears.</span></span>

    ```
    Confirm
    Are you sure you want to perform this action?
    Performing operation "stop-proc" on Target "notepad (4996)".
    [Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"): Y
    ```

- <span data-ttu-id="0bddd-198">Come illustrato, usare Stop-Process per arrestare il processo critico denominato "WINLOGON".</span><span class="sxs-lookup"><span data-stu-id="0bddd-198">Use Stop-Proc as shown to stop the critical process named "WINLOGON".</span></span> <span data-ttu-id="0bddd-199">Si è richiesto e visualizzato un avviso su come eseguire questa azione perché si verificheranno di riavvio del sistema operativo.</span><span class="sxs-lookup"><span data-stu-id="0bddd-199">You are prompted and warned about performing this action because it will cause the operating system to reboot.</span></span>

    ```powershell
    PS> stop-proc -Name Winlogon
    ```

<span data-ttu-id="0bddd-200">Viene visualizzato l'output seguente.</span><span class="sxs-lookup"><span data-stu-id="0bddd-200">The following output appears.</span></span>

    ```output
    Confirm
    Are you sure you want to perform this action?
    Performing operation "stop-proc" on Target "winlogon (656)".
    [Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"): Y
    Warning!
    The process " winlogon " is a critical process and should not be stopped. Are you sure you wish to stop the process?
    [Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"): N
    ```

- <span data-ttu-id="0bddd-201">A questo punto Proviamo ad arrestare il processo WINLOGON senza ricevere un avviso.</span><span class="sxs-lookup"><span data-stu-id="0bddd-201">Let's now try to stop the WINLOGON process without receiving a warning.</span></span> <span data-ttu-id="0bddd-202">Tenere presente che questa voce comando Usa il `Force` parametro per ignorare l'avviso.</span><span class="sxs-lookup"><span data-stu-id="0bddd-202">Be aware that this command entry uses the `Force` parameter to override the warning.</span></span>

    ```powershell
    PS> stop-proc -Name winlogon -Force
    ```

<span data-ttu-id="0bddd-203">Viene visualizzato l'output seguente.</span><span class="sxs-lookup"><span data-stu-id="0bddd-203">The following output appears.</span></span>

    ```output
    Confirm
    Are you sure you want to perform this action?
    Performing operation "stop-proc" on Target "winlogon (656)".
    [Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"): N
    ```

## <a name="see-also"></a><span data-ttu-id="0bddd-204">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="0bddd-204">See Also</span></span>

[<span data-ttu-id="0bddd-205">Aggiunta di parametri che elaborano gli Input della riga di comando</span><span class="sxs-lookup"><span data-stu-id="0bddd-205">Adding Parameters that Process Command-Line Input</span></span>](./adding-parameters-that-process-command-line-input.md)

[<span data-ttu-id="0bddd-206">Estensione di tipi di oggetto e la formattazione</span><span class="sxs-lookup"><span data-stu-id="0bddd-206">Extending Object Types and Formatting</span></span>](https://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351)

[<span data-ttu-id="0bddd-207">Come registrare i cmdlet, provider e applicazioni Host</span><span class="sxs-lookup"><span data-stu-id="0bddd-207">How to Register Cmdlets, Providers, and Host Applications</span></span>](https://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c)

[<span data-ttu-id="0bddd-208">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="0bddd-208">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)

[<span data-ttu-id="0bddd-209">Esempi di cmdlet</span><span class="sxs-lookup"><span data-stu-id="0bddd-209">Cmdlet Samples</span></span>](./cmdlet-samples.md)