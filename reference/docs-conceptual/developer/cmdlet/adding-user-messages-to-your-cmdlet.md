---
title: Aggiunta di messaggi utente al cmdlet | Microsoft Docs
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
ms.openlocfilehash: 9079f40e75dae86c22fd8b4f8a45d501c6125498
ms.sourcegitcommit: d43f66071f1f33b350d34fa1f46f3a35910c5d24
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/23/2019
ms.locfileid: "74416034"
---
# <a name="adding-user-messages-to-your-cmdlet"></a><span data-ttu-id="1cfb1-102">Aggiunta di messaggi utente al cmdlet</span><span class="sxs-lookup"><span data-stu-id="1cfb1-102">Adding User Messages to Your Cmdlet</span></span>

<span data-ttu-id="1cfb1-103">I cmdlet possono scrivere diversi tipi di messaggi che possono essere visualizzati dall'utente dal runtime di Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="1cfb1-103">Cmdlets can write several kinds of messages that can be displayed to the user by the Windows PowerShell runtime.</span></span> <span data-ttu-id="1cfb1-104">Questi messaggi includono i tipi seguenti:</span><span class="sxs-lookup"><span data-stu-id="1cfb1-104">These messages include the following types:</span></span>

- <span data-ttu-id="1cfb1-105">Messaggi dettagliati contenenti informazioni generali sugli utenti.</span><span class="sxs-lookup"><span data-stu-id="1cfb1-105">Verbose messages that contain general user information.</span></span>

- <span data-ttu-id="1cfb1-106">Messaggi di debug che contengono informazioni sulla risoluzione dei problemi.</span><span class="sxs-lookup"><span data-stu-id="1cfb1-106">Debug messages that contain troubleshooting information.</span></span>

- <span data-ttu-id="1cfb1-107">Messaggi di avviso che contengono una notifica che il cmdlet sta per eseguire un'operazione che può avere risultati imprevisti.</span><span class="sxs-lookup"><span data-stu-id="1cfb1-107">Warning messages that contain a notification that the cmdlet is about to perform an operation that can have unexpected results.</span></span>

- <span data-ttu-id="1cfb1-108">Messaggi di report di stato che contengono informazioni sulla quantità di lavoro completata dal cmdlet durante l'esecuzione di un'operazione che richiede molto tempo.</span><span class="sxs-lookup"><span data-stu-id="1cfb1-108">Progress report messages that contain information about how much work the cmdlet has completed when performing an operation that takes a long time.</span></span>

<span data-ttu-id="1cfb1-109">Non sono previsti limiti per il numero di messaggi che possono essere scritti dal cmdlet o il tipo di messaggi scritti dal cmdlet.</span><span class="sxs-lookup"><span data-stu-id="1cfb1-109">There are no limits to the number of messages that your cmdlet can write or the type of messages that your cmdlet writes.</span></span> <span data-ttu-id="1cfb1-110">Ogni messaggio viene scritto effettuando una chiamata specifica dall'interno del metodo di elaborazione dell'input del cmdlet.</span><span class="sxs-lookup"><span data-stu-id="1cfb1-110">Each message is written by making a specific call from within the input processing method of your cmdlet.</span></span>

## <a name="defining-the-cmdlet"></a><span data-ttu-id="1cfb1-111">Definizione del cmdlet</span><span class="sxs-lookup"><span data-stu-id="1cfb1-111">Defining the Cmdlet</span></span>

<span data-ttu-id="1cfb1-112">Il primo passaggio nella creazione di cmdlet è sempre il nome del cmdlet e la dichiarazione della classe .NET che implementa il cmdlet.</span><span class="sxs-lookup"><span data-stu-id="1cfb1-112">The first step in cmdlet creation is always naming the cmdlet and declaring the .NET class that implements the cmdlet.</span></span> <span data-ttu-id="1cfb1-113">Qualsiasi tipo di cmdlet può scrivere notifiche utente dai metodi di elaborazione dell'input; Pertanto, in generale, è possibile assegnare un nome a questo cmdlet utilizzando un verbo che indica le modifiche del sistema eseguite dal cmdlet.</span><span class="sxs-lookup"><span data-stu-id="1cfb1-113">Any sort of cmdlet can write user notifications from its input processing methods; so, in general, you can name this cmdlet using any verb that indicates what system modifications the cmdlet performs.</span></span> <span data-ttu-id="1cfb1-114">Per altre informazioni sui verbi di cmdlet approvati, vedere [nomi dei verbi di cmdlet](./approved-verbs-for-windows-powershell-commands.md).</span><span class="sxs-lookup"><span data-stu-id="1cfb1-114">For more information about approved cmdlet verbs, see [Cmdlet Verb Names](./approved-verbs-for-windows-powershell-commands.md).</span></span>

<span data-ttu-id="1cfb1-115">Il cmdlet Stop-proc è stato progettato per modificare il sistema; la Dichiarazione [System. Management. Automation. CmdletAttribute](/dotnet/api/System.Management.Automation.CmdletAttribute) per la classe .NET deve pertanto includere la parola chiave `SupportsShouldProcess` Attribute e essere impostata su `true`.</span><span class="sxs-lookup"><span data-stu-id="1cfb1-115">The Stop-Proc cmdlet is designed to modify the system; therefore, the [System.Management.Automation.CmdletAttribute](/dotnet/api/System.Management.Automation.CmdletAttribute) declaration for the .NET class must include the `SupportsShouldProcess` attribute keyword and be set to `true`.</span></span>

<span data-ttu-id="1cfb1-116">Il codice seguente è la definizione per questa classe di cmdlet Stop-proc.</span><span class="sxs-lookup"><span data-stu-id="1cfb1-116">The following code is the definition for this Stop-Proc cmdlet class.</span></span> <span data-ttu-id="1cfb1-117">Per ulteriori informazioni su questa definizione, vedere [creazione di un cmdlet che modifichi il sistema](./creating-a-cmdlet-that-modifies-the-system.md).</span><span class="sxs-lookup"><span data-stu-id="1cfb1-117">For more information about this definition, see [Creating a Cmdlet that Modifies the System](./creating-a-cmdlet-that-modifies-the-system.md).</span></span>

```csharp
[Cmdlet(VerbsLifecycle.Stop, "proc",
        SupportsShouldProcess = true)]
public class StopProcCommand : Cmdlet
```

## <a name="defining-parameters-for-system-modification"></a><span data-ttu-id="1cfb1-118">Definizione dei parametri per la modifica del sistema</span><span class="sxs-lookup"><span data-stu-id="1cfb1-118">Defining Parameters for System Modification</span></span>

<span data-ttu-id="1cfb1-119">Il cmdlet Stop-proc definisce tre parametri: `Name`, `Force`e `PassThru`.</span><span class="sxs-lookup"><span data-stu-id="1cfb1-119">The Stop-Proc cmdlet defines three parameters: `Name`, `Force`, and `PassThru`.</span></span> <span data-ttu-id="1cfb1-120">Per ulteriori informazioni sulla definizione di questi parametri, vedere [creazione di un cmdlet che modifichi il sistema](./creating-a-cmdlet-that-modifies-the-system.md).</span><span class="sxs-lookup"><span data-stu-id="1cfb1-120">For more information about defining these parameters, see [Creating a Cmdlet that Modifies the System](./creating-a-cmdlet-that-modifies-the-system.md).</span></span>

<span data-ttu-id="1cfb1-121">Di seguito è illustrata la dichiarazione di parametro per il cmdlet Stop-proc.</span><span class="sxs-lookup"><span data-stu-id="1cfb1-121">Here is the parameter declaration for the Stop-Proc cmdlet.</span></span>

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

## <a name="overriding-an-input-processing-method"></a><span data-ttu-id="1cfb1-122">Override di un metodo di elaborazione dell'input</span><span class="sxs-lookup"><span data-stu-id="1cfb1-122">Overriding an Input Processing Method</span></span>

<span data-ttu-id="1cfb1-123">Il cmdlet deve eseguire l'override di un metodo di elaborazione dell'input, più spesso sarà [System. Management. Automation. cmdlet. ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord).</span><span class="sxs-lookup"><span data-stu-id="1cfb1-123">Your cmdlet must override an input processing method, most often it will be [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord).</span></span> <span data-ttu-id="1cfb1-124">Questo cmdlet Stop-proc esegue l'override del metodo di elaborazione dell'input [System. Management. Automation. cmdlet. ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) .</span><span class="sxs-lookup"><span data-stu-id="1cfb1-124">This Stop-Proc cmdlet overrides the [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) input processing method.</span></span> <span data-ttu-id="1cfb1-125">In questa implementazione del cmdlet Stop-proc vengono effettuate chiamate per scrivere messaggi dettagliati, messaggi di debug e messaggi di avviso.</span><span class="sxs-lookup"><span data-stu-id="1cfb1-125">In this implementation of the Stop-Proc cmdlet, calls are made to write verbose messages, debug messages, and warning messages.</span></span>

> [!NOTE]
> <span data-ttu-id="1cfb1-126">Per ulteriori informazioni sul modo in cui questo metodo chiama i metodi [System. Management. Automation. cmdlet. ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) e [System. Management. Automation. cmdlet. ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) , vedere [creazione di un cmdlet che modifica il sistema](./creating-a-cmdlet-that-modifies-the-system.md).</span><span class="sxs-lookup"><span data-stu-id="1cfb1-126">For more information about how this method calls the [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) and [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) methods, see [Creating a Cmdlet that Modifies the System](./creating-a-cmdlet-that-modifies-the-system.md).</span></span>

## <a name="writing-a-verbose-message"></a><span data-ttu-id="1cfb1-127">Scrittura di un messaggio dettagliato</span><span class="sxs-lookup"><span data-stu-id="1cfb1-127">Writing a Verbose Message</span></span>

<span data-ttu-id="1cfb1-128">Il metodo [System. Management. Automation. cmdlet. WriteVerbose](/dotnet/api/System.Management.Automation.Cmdlet.WriteVerbose) viene usato per scrivere informazioni generali a livello di utente che non sono correlate a condizioni di errore specifiche.</span><span class="sxs-lookup"><span data-stu-id="1cfb1-128">The [System.Management.Automation.Cmdlet.WriteVerbose](/dotnet/api/System.Management.Automation.Cmdlet.WriteVerbose) method is used to write general user-level information that is unrelated to specific error conditions.</span></span> <span data-ttu-id="1cfb1-129">L'amministratore di sistema può quindi utilizzare tali informazioni per continuare l'elaborazione di altri comandi.</span><span class="sxs-lookup"><span data-stu-id="1cfb1-129">The system administrator can then use that information to continue processing other commands.</span></span> <span data-ttu-id="1cfb1-130">Inoltre, tutte le informazioni scritte utilizzando questo metodo devono essere localizzate in base alle esigenze.</span><span class="sxs-lookup"><span data-stu-id="1cfb1-130">In addition, any information written using this method should be localized as needed.</span></span>

<span data-ttu-id="1cfb1-131">Il codice seguente di questo cmdlet Stop-proc Mostra due chiamate al metodo [System. Management. Automation. cmdlet. WriteVerbose](/dotnet/api/System.Management.Automation.Cmdlet.WriteVerbose) dall'override del metodo [System. Management. Automation. cmdlet. ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) .</span><span class="sxs-lookup"><span data-stu-id="1cfb1-131">The following code from this Stop-Proc cmdlet shows two calls to the [System.Management.Automation.Cmdlet.WriteVerbose](/dotnet/api/System.Management.Automation.Cmdlet.WriteVerbose) method from the override of the [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) method.</span></span>

```csharp
message = String.Format("Attempting to stop process \"{0}\".", name);
WriteVerbose(message);
```

```csharp
message = String.Format("Stopped process \"{0}\", pid {1}.",
                        processName, process.Id);

WriteVerbose(message);
```

## <a name="writing-a-debug-message"></a><span data-ttu-id="1cfb1-132">Scrittura di un messaggio di debug</span><span class="sxs-lookup"><span data-stu-id="1cfb1-132">Writing a Debug Message</span></span>

<span data-ttu-id="1cfb1-133">Il metodo [System. Management. Automation. cmdlet. WriteDebug](/dotnet/api/System.Management.Automation.Cmdlet.WriteDebug) viene usato per scrivere messaggi di debug che possono essere usati per risolvere i problemi relativi all'operazione del cmdlet.</span><span class="sxs-lookup"><span data-stu-id="1cfb1-133">The [System.Management.Automation.Cmdlet.WriteDebug](/dotnet/api/System.Management.Automation.Cmdlet.WriteDebug) method is used to write debug messages that can be used to troubleshoot the operation of the cmdlet.</span></span> <span data-ttu-id="1cfb1-134">La chiamata viene eseguita da un metodo di elaborazione dell'input.</span><span class="sxs-lookup"><span data-stu-id="1cfb1-134">The call is made from an input processing method.</span></span>

> [!NOTE]
> <span data-ttu-id="1cfb1-135">Windows PowerShell definisce anche un parametro di `Debug` che presenta informazioni dettagliate e di debug.</span><span class="sxs-lookup"><span data-stu-id="1cfb1-135">Windows PowerShell also defines a `Debug` parameter that presents both verbose and debug information.</span></span> <span data-ttu-id="1cfb1-136">Se il cmdlet supporta questo parametro, non è necessario chiamare [System. Management. Automation. cmdlet. WriteDebug](/dotnet/api/System.Management.Automation.Cmdlet.WriteDebug) nello stesso codice che chiama [System. Management. Automation. cmdlet. WriteVerbose](/dotnet/api/System.Management.Automation.Cmdlet.WriteVerbose).</span><span class="sxs-lookup"><span data-stu-id="1cfb1-136">If your cmdlet supports this parameter, it does not need to call [System.Management.Automation.Cmdlet.WriteDebug](/dotnet/api/System.Management.Automation.Cmdlet.WriteDebug) in the same code that calls [System.Management.Automation.Cmdlet.WriteVerbose](/dotnet/api/System.Management.Automation.Cmdlet.WriteVerbose).</span></span>

<span data-ttu-id="1cfb1-137">Nelle due sezioni seguenti del codice del cmdlet di esempio Stop-proc vengono visualizzate le chiamate al metodo [System. Management. Automation. cmdlet. WriteDebug](/dotnet/api/System.Management.Automation.Cmdlet.WriteDebug) dall'override del metodo [System. Management. Automation. cmdlet. ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) .</span><span class="sxs-lookup"><span data-stu-id="1cfb1-137">The following two sections of code from the sample Stop-Proc cmdlet show calls to the [System.Management.Automation.Cmdlet.WriteDebug](/dotnet/api/System.Management.Automation.Cmdlet.WriteDebug) method from the override of the [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) method.</span></span>

<span data-ttu-id="1cfb1-138">Questo messaggio di debug viene scritto immediatamente prima della chiamata a [System. Management. Automation. cmdlet. ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) .</span><span class="sxs-lookup"><span data-stu-id="1cfb1-138">This debug message is written immediately before [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) is called.</span></span>

```csharp
message =
          String.Format("Acquired name for pid {0} : \"{1}\"",
                       process.Id, processName);
WriteDebug(message);
```

<span data-ttu-id="1cfb1-139">Questo messaggio di debug viene scritto immediatamente prima della chiamata a [System. Management. Automation. cmdlet. WriteObject](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject) .</span><span class="sxs-lookup"><span data-stu-id="1cfb1-139">This debug message is written immediately before [System.Management.Automation.Cmdlet.WriteObject](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject) is called.</span></span>

```csharp
message =
         String.Format("Writing process \"{0}\" to pipeline",
         processName);
WriteDebug(message);
WriteObject(process);
```

<span data-ttu-id="1cfb1-140">Windows PowerShell instrada automaticamente le chiamate [System. Management. Automation. cmdlet. WriteDebug](/dotnet/api/System.Management.Automation.Cmdlet.WriteDebug) all'infrastruttura di traccia e ai cmdlet.</span><span class="sxs-lookup"><span data-stu-id="1cfb1-140">Windows PowerShell automatically routes any [System.Management.Automation.Cmdlet.WriteDebug](/dotnet/api/System.Management.Automation.Cmdlet.WriteDebug) calls to the tracing infrastructure and cmdlets.</span></span> <span data-ttu-id="1cfb1-141">In questo modo è possibile tracciare le chiamate al metodo nell'applicazione host, in un file o in un debugger senza dover eseguire ulteriori operazioni di sviluppo all'interno del cmdlet.</span><span class="sxs-lookup"><span data-stu-id="1cfb1-141">This allows the method calls to be traced to the hosting application, a file, or a debugger without your having to do any extra development work within the cmdlet.</span></span> <span data-ttu-id="1cfb1-142">La seguente voce della riga di comando implementa un'operazione di traccia.</span><span class="sxs-lookup"><span data-stu-id="1cfb1-142">The following command-line entry implements a tracing operation.</span></span>

<span data-ttu-id="1cfb1-143">**PS > Trace-Expression stop-proc-file proc. log-command stop-proc blocco note**</span><span class="sxs-lookup"><span data-stu-id="1cfb1-143">**PS> trace-expression stop-proc -file proc.log -command stop-proc notepad**</span></span>

## <a name="writing-a-warning-message"></a><span data-ttu-id="1cfb1-144">Scrittura di un messaggio di avviso</span><span class="sxs-lookup"><span data-stu-id="1cfb1-144">Writing a Warning Message</span></span>

<span data-ttu-id="1cfb1-145">Il metodo [System. Management. Automation. cmdlet. WriteWarning](/dotnet/api/System.Management.Automation.Cmdlet.WriteWarning) viene usato per scrivere un avviso quando il cmdlet sta per eseguire un'operazione che potrebbe avere un risultato imprevisto, ad esempio, sovrascrivendo un file di sola lettura.</span><span class="sxs-lookup"><span data-stu-id="1cfb1-145">The [System.Management.Automation.Cmdlet.WriteWarning](/dotnet/api/System.Management.Automation.Cmdlet.WriteWarning) method is used to write a warning when the cmdlet is about to perform an operation that might have an unexpected result, for example, overwriting a read-only file.</span></span>

<span data-ttu-id="1cfb1-146">Il codice seguente dal cmdlet Stop-proc di esempio mostra la chiamata al metodo [System. Management. Automation. cmdlet. WriteWarning](/dotnet/api/System.Management.Automation.Cmdlet.WriteWarning) dall'override del metodo [System. Management. Automation. cmdlet. ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) .</span><span class="sxs-lookup"><span data-stu-id="1cfb1-146">The following code from the sample Stop-Proc cmdlet shows the call to the [System.Management.Automation.Cmdlet.WriteWarning](/dotnet/api/System.Management.Automation.Cmdlet.WriteWarning) method from the override of the [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) method.</span></span>

```csharp
 if (criticalProcess)
 {
   message =
             String.Format("Stopping the critical process \"{0}\".",
                           processName);
   WriteWarning(message);
} // if (criticalProcess...
```

## <a name="writing-a-progress-message"></a><span data-ttu-id="1cfb1-147">Scrittura di un messaggio di stato</span><span class="sxs-lookup"><span data-stu-id="1cfb1-147">Writing a Progress Message</span></span>

<span data-ttu-id="1cfb1-148">[System. Management. Automation. cmdlet. WriteProgress](/dotnet/api/System.Management.Automation.Cmdlet.WriteProgress) viene utilizzato per scrivere i messaggi di stato quando le operazioni del cmdlet impiegano un periodo di tempo prolungato per il completamento.</span><span class="sxs-lookup"><span data-stu-id="1cfb1-148">The [System.Management.Automation.Cmdlet.WriteProgress](/dotnet/api/System.Management.Automation.Cmdlet.WriteProgress) is used to write progress messages when cmdlet operations take an extended amount of time to complete.</span></span> <span data-ttu-id="1cfb1-149">Una chiamata a [System. Management. Automation. cmdlet. WriteProgress](/dotnet/api/System.Management.Automation.Cmdlet.WriteProgress) passa un oggetto [System. Management. Automation. ProgressRecord](/dotnet/api/System.Management.Automation.ProgressRecord) che viene inviato all'applicazione host per il rendering all'utente.</span><span class="sxs-lookup"><span data-stu-id="1cfb1-149">A call to [System.Management.Automation.Cmdlet.WriteProgress](/dotnet/api/System.Management.Automation.Cmdlet.WriteProgress) passes a [System.Management.Automation.Progressrecord](/dotnet/api/System.Management.Automation.ProgressRecord) object that is sent to the hosting application for rendering to the user.</span></span>

> [!NOTE]
> <span data-ttu-id="1cfb1-150">Questo cmdlet Stop-proc non include una chiamata al metodo [System. Management. Automation. cmdlet. WriteProgress](/dotnet/api/System.Management.Automation.Cmdlet.WriteProgress) .</span><span class="sxs-lookup"><span data-stu-id="1cfb1-150">This Stop-Proc cmdlet does not include a call to the [System.Management.Automation.Cmdlet.WriteProgress](/dotnet/api/System.Management.Automation.Cmdlet.WriteProgress) method.</span></span>

<span data-ttu-id="1cfb1-151">Il codice seguente è un esempio di messaggio di stato scritto da un cmdlet che tenta di copiare un elemento.</span><span class="sxs-lookup"><span data-stu-id="1cfb1-151">The following code is an example of a progress message written by a cmdlet that is attempting to copy an item.</span></span>

```csharp
int myId = 0;
string myActivity = "Copy-item: Copying *.* to c:\abc";
string myStatus = "Copying file bar.txt";
ProgressRecord pr = new ProgressRecord(myId, myActivity, myStatus);
WriteProgress(pr);

pr.RecordType = ProgressRecordType.Completed;
WriteProgress(pr);
```

## <a name="code-sample"></a><span data-ttu-id="1cfb1-152">Esempio di codice</span><span class="sxs-lookup"><span data-stu-id="1cfb1-152">Code Sample</span></span>

<span data-ttu-id="1cfb1-153">Per il codice C# di esempio completo, vedere l' [esempio StopProcessSample02](./stopprocesssample02-sample.md).</span><span class="sxs-lookup"><span data-stu-id="1cfb1-153">For the complete C# sample code, see [StopProcessSample02 Sample](./stopprocesssample02-sample.md).</span></span>

## <a name="define-object-types-and-formatting"></a><span data-ttu-id="1cfb1-154">Definire i tipi di oggetto e la formattazione</span><span class="sxs-lookup"><span data-stu-id="1cfb1-154">Define Object Types and Formatting</span></span>

<span data-ttu-id="1cfb1-155">Windows PowerShell passa le informazioni tra i cmdlet usando gli oggetti .NET.</span><span class="sxs-lookup"><span data-stu-id="1cfb1-155">Windows PowerShell passes information between cmdlets using .NET objects.</span></span> <span data-ttu-id="1cfb1-156">Di conseguenza, un cmdlet potrebbe dover definire il proprio tipo oppure il cmdlet deve estendere un tipo esistente fornito da un altro cmdlet.</span><span class="sxs-lookup"><span data-stu-id="1cfb1-156">Consequently, a cmdlet might need to define its own type, or the cmdlet might need to extend an existing type provided by another cmdlet.</span></span> <span data-ttu-id="1cfb1-157">Per ulteriori informazioni sulla definizione di nuovi tipi o sull'estensione di tipi esistenti, vedere [estensione di tipi di oggetti e formattazione](/previous-versions//ms714665(v=vs.85)).</span><span class="sxs-lookup"><span data-stu-id="1cfb1-157">For more information about defining new types or extending existing types, see [Extending Object Types and Formatting](/previous-versions//ms714665(v=vs.85)).</span></span>

## <a name="building-the-cmdlet"></a><span data-ttu-id="1cfb1-158">Compilazione del cmdlet</span><span class="sxs-lookup"><span data-stu-id="1cfb1-158">Building the Cmdlet</span></span>

<span data-ttu-id="1cfb1-159">Dopo l'implementazione di un cmdlet, è necessario registrarlo con Windows PowerShell tramite uno snap-in di Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="1cfb1-159">After implementing a cmdlet, it must be registered with Windows PowerShell through a Windows PowerShell snap-in.</span></span> <span data-ttu-id="1cfb1-160">Per ulteriori informazioni sulla registrazione dei cmdlet, vedere [come registrare i cmdlet, i provider e le applicazioni host](/previous-versions//ms714644(v=vs.85)).</span><span class="sxs-lookup"><span data-stu-id="1cfb1-160">For more information about registering cmdlets, see [How to Register Cmdlets, Providers, and Host Applications](/previous-versions//ms714644(v=vs.85)).</span></span>

## <a name="testing-the-cmdlet"></a><span data-ttu-id="1cfb1-161">Test del cmdlet</span><span class="sxs-lookup"><span data-stu-id="1cfb1-161">Testing the Cmdlet</span></span>

<span data-ttu-id="1cfb1-162">Quando il cmdlet è stato registrato con Windows PowerShell, è possibile testarlo eseguendolo nella riga di comando.</span><span class="sxs-lookup"><span data-stu-id="1cfb1-162">When your cmdlet has been registered with Windows PowerShell, you can test it by running it on the command line.</span></span> <span data-ttu-id="1cfb1-163">Testare il cmdlet di esempio Stop-proc.</span><span class="sxs-lookup"><span data-stu-id="1cfb1-163">Let's test the sample Stop-Proc cmdlet.</span></span> <span data-ttu-id="1cfb1-164">Per ulteriori informazioni sull'utilizzo dei cmdlet dalla riga di comando, vedere la [Introduzione con Windows PowerShell](/powershell/scripting/getting-started/getting-started-with-windows-powershell).</span><span class="sxs-lookup"><span data-stu-id="1cfb1-164">For more information about using cmdlets from the command line, see the [Getting Started with Windows PowerShell](/powershell/scripting/getting-started/getting-started-with-windows-powershell).</span></span>

- <span data-ttu-id="1cfb1-165">La voce della riga di comando seguente USA stop-proc per arrestare il processo denominato "blocco note", fornire notifiche dettagliate e stampare le informazioni di debug.</span><span class="sxs-lookup"><span data-stu-id="1cfb1-165">The following command-line entry uses Stop-Proc to stop the process named "NOTEPAD", provide verbose notifications, and print debug information.</span></span>

    ```powershell
    PS> stop-proc -Name notepad -Verbose -Debug
    ```

<span data-ttu-id="1cfb1-166">Viene visualizzato l'output seguente.</span><span class="sxs-lookup"><span data-stu-id="1cfb1-166">The following output appears.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="1cfb1-167">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="1cfb1-167">See Also</span></span>

[<span data-ttu-id="1cfb1-168">Creare un cmdlet che modifichi il sistema</span><span class="sxs-lookup"><span data-stu-id="1cfb1-168">Create a Cmdlet that Modifies the System</span></span>](./creating-a-cmdlet-that-modifies-the-system.md)

[<span data-ttu-id="1cfb1-169">Come creare un cmdlet di Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="1cfb1-169">How to Create a Windows PowerShell Cmdlet</span></span>](/powershell/scripting/developer/cmdlet/writing-a-windows-powershell-cmdlet)

<span data-ttu-id="1cfb1-170">[Estensione di tipi di oggetti e formattazione](/previous-versions//ms714665(v=vs.85))</span><span class="sxs-lookup"><span data-stu-id="1cfb1-170">[Extending Object Types and Formatting](/previous-versions//ms714665(v=vs.85))</span></span>

<span data-ttu-id="1cfb1-171">[Come registrare cmdlet, provider e applicazioni host](/previous-versions//ms714644(v=vs.85))</span><span class="sxs-lookup"><span data-stu-id="1cfb1-171">[How to Register Cmdlets, Providers, and Host Applications](/previous-versions//ms714644(v=vs.85))</span></span>

[<span data-ttu-id="1cfb1-172">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="1cfb1-172">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)
