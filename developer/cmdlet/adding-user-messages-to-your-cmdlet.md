---
title: Aggiunta di messaggi dell'utente al Cmdlet | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- WriteWarning
- notifications, writing
- progress notification
- WriteVerbose
- Stop-Proc
- WriteProgress
- WriteDebug
- notifications, debug
- ProgressRecord
- samples, Stop-Proc cmdlet
- notifications, progress
- notifications, warning
- WriteObject
- WriteError
- verbose notification
- ProcessRecord
- notifications, verbose
- debug notification
- cmdlet, writing notifications
- warning
- code sample, user notifications
- user notifications
ms.assetid: 14c13acb-f0b7-4613-bc7d-c361d14da1a2
caps.latest.revision: 8
ms.openlocfilehash: 138c6a43937e72fffaa2a09243e500e9822e6111
ms.sourcegitcommit: 01b81317029b28dd9b61d167045fd31f1ec7bc06
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/17/2019
ms.locfileid: "65854929"
---
# <a name="adding-user-messages-to-your-cmdlet"></a><span data-ttu-id="ddaea-102">Aggiunta di messaggi utente al cmdlet</span><span class="sxs-lookup"><span data-stu-id="ddaea-102">Adding User Messages to Your Cmdlet</span></span>

<span data-ttu-id="ddaea-103">I cmdlet possono scrivere diversi tipi di messaggi che possono essere visualizzati all'utente dal runtime di Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="ddaea-103">Cmdlets can write several kinds of messages that can be displayed to the user by the Windows PowerShell runtime.</span></span> <span data-ttu-id="ddaea-104">Questi messaggi includono i tipi seguenti:</span><span class="sxs-lookup"><span data-stu-id="ddaea-104">These messages include the following types:</span></span>

- <span data-ttu-id="ddaea-105">Messaggi dettagliati contenenti informazioni utente generali.</span><span class="sxs-lookup"><span data-stu-id="ddaea-105">Verbose messages that contain general user information.</span></span>

- <span data-ttu-id="ddaea-106">I messaggi che contengono informazioni sulla risoluzione dei problemi di debug.</span><span class="sxs-lookup"><span data-stu-id="ddaea-106">Debug messages that contain troubleshooting information.</span></span>

- <span data-ttu-id="ddaea-107">I messaggi di avviso che contengono una notifica che il cmdlet deve eseguire un'operazione che può avere risultati imprevisti.</span><span class="sxs-lookup"><span data-stu-id="ddaea-107">Warning messages that contain a notification that the cmdlet is about to perform an operation that can have unexpected results.</span></span>

- <span data-ttu-id="ddaea-108">Report stato di avanzamento dei messaggi che contengono informazioni sulla quantità di lavoro il cmdlet è stata completata durante l'esecuzione di un'operazione che richiede molto tempo.</span><span class="sxs-lookup"><span data-stu-id="ddaea-108">Progress report messages that contain information about how much work the cmdlet has completed when performing an operation that takes a long time.</span></span>

<span data-ttu-id="ddaea-109">Non sono previsti limiti al numero di messaggi che può scrivere cmdlet o il tipo di messaggi che il cmdlet scrive.</span><span class="sxs-lookup"><span data-stu-id="ddaea-109">There are no limits to the number of messages that your cmdlet can write or the type of messages that your cmdlet writes.</span></span> <span data-ttu-id="ddaea-110">Ogni messaggio viene scritto eseguendo una chiamata specifica da entro il metodo del cmdlet di elaborazione dell'input.</span><span class="sxs-lookup"><span data-stu-id="ddaea-110">Each message is written by making a specific call from within the input processing method of your cmdlet.</span></span>

## <a name="defining-the-cmdlet"></a><span data-ttu-id="ddaea-111">Che definisce il Cmdlet</span><span class="sxs-lookup"><span data-stu-id="ddaea-111">Defining the Cmdlet</span></span>

<span data-ttu-id="ddaea-112">Il primo passaggio nella creazione di cmdlet è sempre il cmdlet di denominazione e la dichiarazione di classe .NET che implementa il cmdlet.</span><span class="sxs-lookup"><span data-stu-id="ddaea-112">The first step in cmdlet creation is always naming the cmdlet and declaring the .NET class that implements the cmdlet.</span></span> <span data-ttu-id="ddaea-113">Una sorta di cmdlet è possibile scrivere le notifiche utente dal proprio input; i metodi di elaborazione Pertanto, in generale, è possibile denominare questo cmdlet tramite qualsiasi verbo che indica quali modifiche di sistema esegue il cmdlet.</span><span class="sxs-lookup"><span data-stu-id="ddaea-113">Any sort of cmdlet can write user notifications from its input processing methods; so, in general, you can name this cmdlet using any verb that indicates what system modifications the cmdlet performs.</span></span> <span data-ttu-id="ddaea-114">Per altre informazioni sui verbi approvati di cmdlet, vedere [nomi dei verbi di Cmdlet](./approved-verbs-for-windows-powershell-commands.md).</span><span class="sxs-lookup"><span data-stu-id="ddaea-114">For more information about approved cmdlet verbs, see [Cmdlet Verb Names](./approved-verbs-for-windows-powershell-commands.md).</span></span>

<span data-ttu-id="ddaea-115">Il cmdlet Stop-Process è progettato per modificare il sistema. Pertanto, il [System.Management.Automation.CmdletAttribute](/dotnet/api/System.Management.Automation.CmdletAttribute) dichiarazione della classe .NET deve includere il `SupportsShouldProcess` parola chiave dell'attributo e impostato su `true`.</span><span class="sxs-lookup"><span data-stu-id="ddaea-115">The Stop-Proc cmdlet is designed to modify the system; therefore, the [System.Management.Automation.CmdletAttribute](/dotnet/api/System.Management.Automation.CmdletAttribute) declaration for the .NET class must include the `SupportsShouldProcess` attribute keyword and be set to `true`.</span></span>

<span data-ttu-id="ddaea-116">Il codice seguente è la definizione per questa classe cmdlet Stop-Process.</span><span class="sxs-lookup"><span data-stu-id="ddaea-116">The following code is the definition for this Stop-Proc cmdlet class.</span></span> <span data-ttu-id="ddaea-117">Per altre informazioni su questa definizione, vedere [creazione di un Cmdlet che modifichi il sistema](./creating-a-cmdlet-that-modifies-the-system.md).</span><span class="sxs-lookup"><span data-stu-id="ddaea-117">For more information about this definition, see [Creating a Cmdlet that Modifies the System](./creating-a-cmdlet-that-modifies-the-system.md).</span></span>

```csharp
[Cmdlet(VerbsLifecycle.Stop, "proc",
        SupportsShouldProcess = true)]
public class StopProcCommand : Cmdlet
```

## <a name="defining-parameters-for-system-modification"></a><span data-ttu-id="ddaea-118">Definizione dei parametri per la modifica di sistema</span><span class="sxs-lookup"><span data-stu-id="ddaea-118">Defining Parameters for System Modification</span></span>

<span data-ttu-id="ddaea-119">Il cmdlet Stop-Process definisce tre parametri: `Name`, `Force`, e `PassThru`.</span><span class="sxs-lookup"><span data-stu-id="ddaea-119">The Stop-Proc cmdlet defines three parameters: `Name`, `Force`, and `PassThru`.</span></span> <span data-ttu-id="ddaea-120">Per altre informazioni sulla definizione di questi parametri, vedere [creazione di un Cmdlet che modifichi il sistema](./creating-a-cmdlet-that-modifies-the-system.md).</span><span class="sxs-lookup"><span data-stu-id="ddaea-120">For more information about defining these parameters, see [Creating a Cmdlet that Modifies the System](./creating-a-cmdlet-that-modifies-the-system.md).</span></span>

<span data-ttu-id="ddaea-121">Ecco la dichiarazione di parametro per il cmdlet Stop-Process.</span><span class="sxs-lookup"><span data-stu-id="ddaea-121">Here is the parameter declaration for the Stop-Proc cmdlet.</span></span>

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

## <a name="overriding-an-input-processing-method"></a><span data-ttu-id="ddaea-122">Si esegue l'override di un metodo di elaborazione dell'Input</span><span class="sxs-lookup"><span data-stu-id="ddaea-122">Overriding an Input Processing Method</span></span>

<span data-ttu-id="ddaea-123">Il cmdlet deve eseguire l'override di un metodo di elaborazione dell'input, in genere si tratterà [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord).</span><span class="sxs-lookup"><span data-stu-id="ddaea-123">Your cmdlet must override an input processing method, most often it will be [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord).</span></span> <span data-ttu-id="ddaea-124">Esegue l'override di questo cmdlet Stop-Process il [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) metodo di elaborazione di input.</span><span class="sxs-lookup"><span data-stu-id="ddaea-124">This Stop-Proc cmdlet overrides the [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) input processing method.</span></span> <span data-ttu-id="ddaea-125">In questa implementazione del cmdlet Stop-Process, eseguono chiamate a scrivere i messaggi dettagliati, messaggi di debug e i messaggi di avviso.</span><span class="sxs-lookup"><span data-stu-id="ddaea-125">In this implementation of the Stop-Proc cmdlet, calls are made to write verbose messages, debug messages, and warning messages.</span></span>

> [!NOTE]
> <span data-ttu-id="ddaea-126">Per altre informazioni sul modo in cui questo metodo chiama il [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) e [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) metodi, vedere [Creazione di un Cmdlet che modifichi il sistema](./creating-a-cmdlet-that-modifies-the-system.md).</span><span class="sxs-lookup"><span data-stu-id="ddaea-126">For more information about how this method calls the [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) and [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) methods, see [Creating a Cmdlet that Modifies the System](./creating-a-cmdlet-that-modifies-the-system.md).</span></span>

## <a name="writing-a-verbose-message"></a><span data-ttu-id="ddaea-127">La scrittura di un messaggio dettagliato</span><span class="sxs-lookup"><span data-stu-id="ddaea-127">Writing a Verbose Message</span></span>

<span data-ttu-id="ddaea-128">Il [System.Management.Automation.Cmdlet.WriteVerbose](/dotnet/api/System.Management.Automation.Cmdlet.WriteVerbose) metodo viene utilizzato per scrivere le informazioni utente a livello generale non sono correlate alle condizioni di errore specifico.</span><span class="sxs-lookup"><span data-stu-id="ddaea-128">The [System.Management.Automation.Cmdlet.WriteVerbose](/dotnet/api/System.Management.Automation.Cmdlet.WriteVerbose) method is used to write general user-level information that is unrelated to specific error conditions.</span></span> <span data-ttu-id="ddaea-129">L'amministratore di sistema può quindi usare tali informazioni per continuare a elaborare altri comandi.</span><span class="sxs-lookup"><span data-stu-id="ddaea-129">The system administrator can then use that information to continue processing other commands.</span></span> <span data-ttu-id="ddaea-130">Inoltre, eventuali informazioni scritte utilizzando questo metodo devono essere localizzate in base alle esigenze.</span><span class="sxs-lookup"><span data-stu-id="ddaea-130">In addition, any information written using this method should be localized as needed.</span></span>

<span data-ttu-id="ddaea-131">Il codice seguente da questo cmdlet Stop-Process Mostra due chiamate al [System.Management.Automation.Cmdlet.WriteVerbose](/dotnet/api/System.Management.Automation.Cmdlet.WriteVerbose) l'override del metodo di [System.Management.Automation.Cmdlet.ProcessRecord ](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) (metodo).</span><span class="sxs-lookup"><span data-stu-id="ddaea-131">The following code from this Stop-Proc cmdlet shows two calls to the [System.Management.Automation.Cmdlet.WriteVerbose](/dotnet/api/System.Management.Automation.Cmdlet.WriteVerbose) method from the override of the [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) method.</span></span>

```csharp
message = String.Format("Attempting to stop process \"{0}\".", name);
WriteVerbose(message);
```

```csharp
message = String.Format("Stopped process \"{0}\", pid {1}.",
                        processName, process.Id);

WriteVerbose(message);
```

## <a name="writing-a-debug-message"></a><span data-ttu-id="ddaea-132">La scrittura di un messaggio di Debug</span><span class="sxs-lookup"><span data-stu-id="ddaea-132">Writing a Debug Message</span></span>

<span data-ttu-id="ddaea-133">Il [System.Management.Automation.Cmdlet.WriteDebug](/dotnet/api/System.Management.Automation.Cmdlet.WriteDebug) metodo viene utilizzato per scrivere i messaggi di debug che possono essere utilizzati per risolvere i problemi di funzionamento del cmdlet.</span><span class="sxs-lookup"><span data-stu-id="ddaea-133">The [System.Management.Automation.Cmdlet.WriteDebug](/dotnet/api/System.Management.Automation.Cmdlet.WriteDebug) method is used to write debug messages that can be used to troubleshoot the operation of the cmdlet.</span></span> <span data-ttu-id="ddaea-134">La chiamata viene effettuata da un metodo di elaborazione dell'input.</span><span class="sxs-lookup"><span data-stu-id="ddaea-134">The call is made from an input processing method.</span></span>

> [!NOTE]
> <span data-ttu-id="ddaea-135">Windows PowerShell definisce anche un `Debug` parametro presenta sia dettagliato e informazioni di debug.</span><span class="sxs-lookup"><span data-stu-id="ddaea-135">Windows PowerShell also defines a `Debug` parameter that presents both verbose and debug information.</span></span> <span data-ttu-id="ddaea-136">Se il cmdlet supporta questo parametro, non dovrà chiamare [System.Management.Automation.Cmdlet.WriteDebug](/dotnet/api/System.Management.Automation.Cmdlet.WriteDebug) nello stesso codice che chiama [System.Management.Automation.Cmdlet.WriteVerbose](/dotnet/api/System.Management.Automation.Cmdlet.WriteVerbose) .</span><span class="sxs-lookup"><span data-stu-id="ddaea-136">If your cmdlet supports this parameter, it does not need to call [System.Management.Automation.Cmdlet.WriteDebug](/dotnet/api/System.Management.Automation.Cmdlet.WriteDebug) in the same code that calls [System.Management.Automation.Cmdlet.WriteVerbose](/dotnet/api/System.Management.Automation.Cmdlet.WriteVerbose).</span></span>

<span data-ttu-id="ddaea-137">Le due sezioni di codice tramite il cmdlet Stop-Process di esempio seguente mostrano le chiamate per il [System.Management.Automation.Cmdlet.WriteDebug](/dotnet/api/System.Management.Automation.Cmdlet.WriteDebug) l'override del metodo il [ System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) (metodo).</span><span class="sxs-lookup"><span data-stu-id="ddaea-137">The following two sections of code from the sample Stop-Proc cmdlet show calls to the [System.Management.Automation.Cmdlet.WriteDebug](/dotnet/api/System.Management.Automation.Cmdlet.WriteDebug) method from the override of the [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) method.</span></span>

<span data-ttu-id="ddaea-138">Questo messaggio di debug viene scritto immediatamente prima [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) viene chiamato.</span><span class="sxs-lookup"><span data-stu-id="ddaea-138">This debug message is written immediately before [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) is called.</span></span>

```csharp
message =
          String.Format("Acquired name for pid {0} : \"{1}\"",
                       process.Id, processName);
WriteDebug(message);
```

<span data-ttu-id="ddaea-139">Questo messaggio di debug viene scritto immediatamente prima [System.Management.Automation.Cmdlet.WriteObject](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject) viene chiamato.</span><span class="sxs-lookup"><span data-stu-id="ddaea-139">This debug message is written immediately before [System.Management.Automation.Cmdlet.WriteObject](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject) is called.</span></span>

```csharp
message =
         String.Format("Writing process \"{0}\" to pipeline",
         processName);
WriteDebug(message);
WriteObject(process);
```

<span data-ttu-id="ddaea-140">Windows PowerShell instrada automaticamente uno [System.Management.Automation.Cmdlet.WriteDebug](/dotnet/api/System.Management.Automation.Cmdlet.WriteDebug) chiamate per l'infrastruttura di traccia e i cmdlet.</span><span class="sxs-lookup"><span data-stu-id="ddaea-140">Windows PowerShell automatically routes any [System.Management.Automation.Cmdlet.WriteDebug](/dotnet/api/System.Management.Automation.Cmdlet.WriteDebug) calls to the tracing infrastructure and cmdlets.</span></span> <span data-ttu-id="ddaea-141">In questo modo le chiamate al metodo da tracciare senza che sia necessario eseguire alcuna operazione aggiuntiva sviluppo entro il cmdlet per l'applicazione host, un file o un debugger.</span><span class="sxs-lookup"><span data-stu-id="ddaea-141">This allows the method calls to be traced to the hosting application, a file, or a debugger without your having to do any extra development work within the cmdlet.</span></span> <span data-ttu-id="ddaea-142">La voce della riga di comando seguente implementa un'operazione di traccia.</span><span class="sxs-lookup"><span data-stu-id="ddaea-142">The following command-line entry implements a tracing operation.</span></span>

<span data-ttu-id="ddaea-143">**PS > espressione di traccia stop-Process-file proc.log-notepad stop-Process di comando**</span><span class="sxs-lookup"><span data-stu-id="ddaea-143">**PS> trace-expression stop-proc -file proc.log -command stop-proc notepad**</span></span>

## <a name="writing-a-warning-message"></a><span data-ttu-id="ddaea-144">La scrittura di un messaggio di avviso</span><span class="sxs-lookup"><span data-stu-id="ddaea-144">Writing a Warning Message</span></span>

<span data-ttu-id="ddaea-145">Il [System.Management.Automation.Cmdlet.WriteWarning](/dotnet/api/System.Management.Automation.Cmdlet.WriteWarning) metodo viene utilizzato per scrivere un messaggio di avviso quando il cmdlet sta per eseguire un'operazione che potrebbe avere un risultato di imprevisto, ad esempio, sovrascrivere un file di sola lettura.</span><span class="sxs-lookup"><span data-stu-id="ddaea-145">The [System.Management.Automation.Cmdlet.WriteWarning](/dotnet/api/System.Management.Automation.Cmdlet.WriteWarning) method is used to write a warning when the cmdlet is about to perform an operation that might have an unexpected result, for example, overwriting a read-only file.</span></span>

<span data-ttu-id="ddaea-146">Il codice seguente tramite il cmdlet Stop-Process di esempio illustra la chiamata ai [System.Management.Automation.Cmdlet.WriteWarning](/dotnet/api/System.Management.Automation.Cmdlet.WriteWarning) l'override del metodo di [ System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) (metodo).</span><span class="sxs-lookup"><span data-stu-id="ddaea-146">The following code from the sample Stop-Proc cmdlet shows the call to the [System.Management.Automation.Cmdlet.WriteWarning](/dotnet/api/System.Management.Automation.Cmdlet.WriteWarning) method from the override of the [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) method.</span></span>

```csharp
 if (criticalProcess)
 {
   message =
             String.Format("Stopping the critical process \"{0}\".",
                           processName);
   WriteWarning(message);
} // if (criticalProcess...
```

## <a name="writing-a-progress-message"></a><span data-ttu-id="ddaea-147">Scrittura di un messaggio di stato di avanzamento</span><span class="sxs-lookup"><span data-stu-id="ddaea-147">Writing a Progress Message</span></span>

<span data-ttu-id="ddaea-148">Il [System.Management.Automation.Cmdlet.WriteProgress](/dotnet/api/System.Management.Automation.Cmdlet.WriteProgress) viene usato per scrivere i messaggi di stato di avanzamento durante operazioni del cmdlet richiedono una certa quantità di tempo.</span><span class="sxs-lookup"><span data-stu-id="ddaea-148">The [System.Management.Automation.Cmdlet.WriteProgress](/dotnet/api/System.Management.Automation.Cmdlet.WriteProgress) is used to write progress messages when cmdlet operations take an extended amount of time to complete.</span></span> <span data-ttu-id="ddaea-149">Una chiamata a [System.Management.Automation.Cmdlet.WriteProgress](/dotnet/api/System.Management.Automation.Cmdlet.WriteProgress) passa una [progressrecord](/dotnet/api/System.Management.Automation.ProgressRecord) oggetto che viene inviato all'applicazione host per il rendering all'utente.</span><span class="sxs-lookup"><span data-stu-id="ddaea-149">A call to [System.Management.Automation.Cmdlet.WriteProgress](/dotnet/api/System.Management.Automation.Cmdlet.WriteProgress) passes a [System.Management.Automation.Progressrecord](/dotnet/api/System.Management.Automation.ProgressRecord) object that is sent to the hosting application for rendering to the user.</span></span>

> [!NOTE]
> <span data-ttu-id="ddaea-150">Questo cmdlet Stop-Process non include una chiamata per il [System.Management.Automation.Cmdlet.WriteProgress](/dotnet/api/System.Management.Automation.Cmdlet.WriteProgress) (metodo).</span><span class="sxs-lookup"><span data-stu-id="ddaea-150">This Stop-Proc cmdlet does not include a call to the [System.Management.Automation.Cmdlet.WriteProgress](/dotnet/api/System.Management.Automation.Cmdlet.WriteProgress) method.</span></span>

<span data-ttu-id="ddaea-151">Il codice riportato di seguito è riportato un esempio di un messaggio di stato scritto da un cmdlet che sta tentando di copiare un elemento.</span><span class="sxs-lookup"><span data-stu-id="ddaea-151">The following code is an example of a progress message written by a cmdlet that is attempting to copy an item.</span></span>

```csharp
int myId = 0;
string myActivity = "Copy-item: Copying *.* to c:\abc";
string myStatus = "Copying file bar.txt";
ProgressRecord pr = new ProgressRecord(myId, myActivity, myStatus);
WriteProgress(pr);

pr.RecordType = ProgressRecordType.Completed;
WriteProgress(pr);
```

## <a name="code-sample"></a><span data-ttu-id="ddaea-152">Esempio di codice</span><span class="sxs-lookup"><span data-stu-id="ddaea-152">Code Sample</span></span>

<span data-ttu-id="ddaea-153">Per l'intero C# esempi di codice, vedere [StopProcessSample02 campione](./stopprocesssample02-sample.md).</span><span class="sxs-lookup"><span data-stu-id="ddaea-153">For the complete C# sample code, see [StopProcessSample02 Sample](./stopprocesssample02-sample.md).</span></span>

## <a name="define-object-types-and-formatting"></a><span data-ttu-id="ddaea-154">Definire i tipi di oggetto e la formattazione</span><span class="sxs-lookup"><span data-stu-id="ddaea-154">Define Object Types and Formatting</span></span>

<span data-ttu-id="ddaea-155">Windows PowerShell passa informazioni tra i cmdlet con gli oggetti .NET.</span><span class="sxs-lookup"><span data-stu-id="ddaea-155">Windows PowerShell passes information between cmdlets using .NET objects.</span></span> <span data-ttu-id="ddaea-156">Di conseguenza, potrebbe essere necessario definire un proprio tipo di un cmdlet o il cmdlet potrebbe essere necessario estendere un tipo esistente fornito da un altro cmdlet.</span><span class="sxs-lookup"><span data-stu-id="ddaea-156">Consequently, a cmdlet might need to define its own type, or the cmdlet might need to extend an existing type provided by another cmdlet.</span></span> <span data-ttu-id="ddaea-157">Per altre informazioni sulla definizione di nuovi tipi o estendere i tipi esistenti, vedere [estendendo i tipi di oggetto e formattazione](http://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351).</span><span class="sxs-lookup"><span data-stu-id="ddaea-157">For more information about defining new types or extending existing types, see [Extending Object Types and Formatting](http://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351).</span></span>

## <a name="building-the-cmdlet"></a><span data-ttu-id="ddaea-158">Creazione di Cmdlet</span><span class="sxs-lookup"><span data-stu-id="ddaea-158">Building the Cmdlet</span></span>

<span data-ttu-id="ddaea-159">Dopo l'implementazione di un cmdlet, è necessario registrarlo con Windows PowerShell tramite uno snap-in Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="ddaea-159">After implementing a cmdlet, it must be registered with Windows PowerShell through a Windows PowerShell snap-in.</span></span> <span data-ttu-id="ddaea-160">Per altre informazioni sulla registrazione dei cmdlet, vedere [come registrare i cmdlet, provider e applicazioni Host](http://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c).</span><span class="sxs-lookup"><span data-stu-id="ddaea-160">For more information about registering cmdlets, see [How to Register Cmdlets, Providers, and Host Applications](http://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c).</span></span>

## <a name="testing-the-cmdlet"></a><span data-ttu-id="ddaea-161">Il Cmdlet di test</span><span class="sxs-lookup"><span data-stu-id="ddaea-161">Testing the Cmdlet</span></span>

<span data-ttu-id="ddaea-162">Quando il cmdlet è stato registrato con Windows PowerShell, è possibile testarlo eseguendolo dalla riga di comando.</span><span class="sxs-lookup"><span data-stu-id="ddaea-162">When your cmdlet has been registered with Windows PowerShell, you can test it by running it on the command line.</span></span> <span data-ttu-id="ddaea-163">È possibile testare il cmdlet Stop-Process di esempio.</span><span class="sxs-lookup"><span data-stu-id="ddaea-163">Let's test the sample Stop-Proc cmdlet.</span></span> <span data-ttu-id="ddaea-164">Per altre informazioni sull'utilizzo dei cmdlet dalla riga di comando, vedere la [Introduzione a Windows PowerShell](/powershell/scripting/getting-started/getting-started-with-windows-powershell).</span><span class="sxs-lookup"><span data-stu-id="ddaea-164">For more information about using cmdlets from the command line, see the [Getting Started with Windows PowerShell](/powershell/scripting/getting-started/getting-started-with-windows-powershell).</span></span>

- <span data-ttu-id="ddaea-165">La voce della riga di comando seguente usa Stop-Process per arrestare il processo denominato "NOTEPAD", fornire notifiche dettagliate e stampare le informazioni di debug.</span><span class="sxs-lookup"><span data-stu-id="ddaea-165">The following command-line entry uses Stop-Proc to stop the process named "NOTEPAD", provide verbose notifications, and print debug information.</span></span>

    ```powershell
    PS> stop-proc -Name notepad -Verbose -Debug
    ```

<span data-ttu-id="ddaea-166">Viene visualizzato l'output seguente.</span><span class="sxs-lookup"><span data-stu-id="ddaea-166">The following output appears.</span></span>

    ```
    VERBOSE: Attempting to stop process " notepad ".
    DEBUG: Acquired name for pid 5584 : "notepad"

    Confirm
    Continue with this operation?
    [Y] Yes  [A] Yes to All  [H] Halt Command  [S] Suspend  [?] Help (default is "Y"): Y

    Confirm
    Are you sure you want to perform this action?
    Performing operation "stop-proc" on Target "notepad (5584)".
    [Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"): Y
    VERBOSE: Stopped process "notepad", pid 5584.
    ```

## <a name="see-also"></a><span data-ttu-id="ddaea-167">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="ddaea-167">See Also</span></span>

[<span data-ttu-id="ddaea-168">Creare un Cmdlet che modifichi il sistema</span><span class="sxs-lookup"><span data-stu-id="ddaea-168">Create a Cmdlet that Modifies the System</span></span>](./creating-a-cmdlet-that-modifies-the-system.md)

[<span data-ttu-id="ddaea-169">Come creare un Cmdlet di Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="ddaea-169">How to Create a Windows PowerShell Cmdlet</span></span>](http://msdn.microsoft.com/en-us/0d721742-c849-4d0d-964f-78ddd9cd258c)

[<span data-ttu-id="ddaea-170">Estensione di tipi di oggetto e la formattazione</span><span class="sxs-lookup"><span data-stu-id="ddaea-170">Extending Object Types and Formatting</span></span>](http://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351)

[<span data-ttu-id="ddaea-171">Come registrare i cmdlet, provider e applicazioni Host</span><span class="sxs-lookup"><span data-stu-id="ddaea-171">How to Register Cmdlets, Providers, and Host Applications</span></span>](http://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c)

[<span data-ttu-id="ddaea-172">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="ddaea-172">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)
