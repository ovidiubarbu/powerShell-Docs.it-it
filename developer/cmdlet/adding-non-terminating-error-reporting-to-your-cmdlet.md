---
title: Aggiunta di segnalazione errori al Cmdlet di Non definitive | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f2a1531a-a92a-4606-9d54-c5df80d34f33
caps.latest.revision: 8
ms.openlocfilehash: 3741982f81efa04d8fe7ab448fba5f2fdf4b0c01
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62068865"
---
# <a name="adding-non-terminating-error-reporting-to-your-cmdlet"></a><span data-ttu-id="ab0b4-102">Aggiunta di segnalazioni di errori non irreversibili al cmdlet</span><span class="sxs-lookup"><span data-stu-id="ab0b4-102">Adding Non-Terminating Error Reporting to Your Cmdlet</span></span>

<span data-ttu-id="ab0b4-103">I cmdlet possono segnalare gli errori non fatali chiamando il [System.Management.Automation.Cmdlet.WriteError][] (metodo) e comunque continuare a operare sull'oggetto di input corrente o in entrata ulteriormente gli oggetti di pipeline.</span><span class="sxs-lookup"><span data-stu-id="ab0b4-103">Cmdlets can report nonterminating errors by calling the [System.Management.Automation.Cmdlet.WriteError][] method and still continue to operate on the current input object or on further incoming pipeline objects.</span></span>
<span data-ttu-id="ab0b4-104">Questa sezione viene illustrato come creare un cmdlet che segnala gli errori non fatali dai relativi metodi di elaborazione dell'input.</span><span class="sxs-lookup"><span data-stu-id="ab0b4-104">This section explains how to create a cmdlet that reports nonterminating errors from its input processing methods.</span></span>

<span data-ttu-id="ab0b4-105">Per gli errori non fatali (così come gli errori irreversibili), il cmdlet è necessario passare un [System.Management.Automation.ErrorRecord][] oggetto che identifica l'errore.</span><span class="sxs-lookup"><span data-stu-id="ab0b4-105">For nonterminating errors (as well as terminating errors), the cmdlet must pass an [System.Management.Automation.ErrorRecord][] object identifying the error.</span></span>
<span data-ttu-id="ab0b4-106">Ogni record error è identificato da una stringa univoca, chiamata "identificatore dell'errore".</span><span class="sxs-lookup"><span data-stu-id="ab0b4-106">Each error record is identified by a unique string called the "error identifier".</span></span>
<span data-ttu-id="ab0b4-107">Oltre all'identificatore, la categoria di ogni errore è specificata dalle costanti definite da un [System.Management.Automation.ErrorCategory][] enumerazione.</span><span class="sxs-lookup"><span data-stu-id="ab0b4-107">In addition to the identifier, the category of each error is specified by constants defined by a [System.Management.Automation.ErrorCategory][] enumeration.</span></span>
<span data-ttu-id="ab0b4-108">L'utente può visualizzare gli errori in base alla categoria basati impostando il `$ErrorView` variabile "CategoryView".</span><span class="sxs-lookup"><span data-stu-id="ab0b4-108">The user can view errors based on their category by setting the `$ErrorView` variable to "CategoryView".</span></span>

<span data-ttu-id="ab0b4-109">Per altre informazioni sui record di errore, vedere [record di errore di Windows PowerShell](./windows-powershell-error-records.md).</span><span class="sxs-lookup"><span data-stu-id="ab0b4-109">For more information about error records, see [Windows PowerShell Error Records](./windows-powershell-error-records.md).</span></span>

## <a name="defining-the-cmdlet"></a><span data-ttu-id="ab0b4-110">Che definisce il Cmdlet</span><span class="sxs-lookup"><span data-stu-id="ab0b4-110">Defining the Cmdlet</span></span>

<span data-ttu-id="ab0b4-111">Il primo passaggio nella creazione di cmdlet è sempre il cmdlet di denominazione e la dichiarazione di classe .NET che implementa il cmdlet.</span><span class="sxs-lookup"><span data-stu-id="ab0b4-111">The first step in cmdlet creation is always naming the cmdlet and declaring the .NET class that implements the cmdlet.</span></span>
<span data-ttu-id="ab0b4-112">Questo cmdlet recupera le informazioni sul processo, in modo che il nome del verbo selezionato qui è "Get".</span><span class="sxs-lookup"><span data-stu-id="ab0b4-112">This cmdlet retrieves process information, so the verb name chosen here is "Get".</span></span>
<span data-ttu-id="ab0b4-113">(Quasi una sorta di cmdlet che è in grado di recuperare le informazioni può elaborare input della riga di comando). Per altre informazioni sui verbi approvati di cmdlet, vedere [nomi dei verbi di Cmdlet](approved-verbs-for-windows-powershell-commands.md).</span><span class="sxs-lookup"><span data-stu-id="ab0b4-113">(Almost any sort of cmdlet that is capable of retrieving information can process command-line input.) For more information about approved cmdlet verbs, see [Cmdlet Verb Names](approved-verbs-for-windows-powershell-commands.md).</span></span>

<span data-ttu-id="ab0b4-114">Di seguito è la definizione per il cmdlet Get-Process.</span><span class="sxs-lookup"><span data-stu-id="ab0b4-114">The following is the definition for this Get-Proc cmdlet.</span></span>
<span data-ttu-id="ab0b4-115">Dettagli di questa definizione sono disponibili nella [la creazione del primo Cmdlet](creating-a-cmdlet-without-parameters.md).</span><span class="sxs-lookup"><span data-stu-id="ab0b4-115">Details of this definition are given in [Creating Your First Cmdlet](creating-a-cmdlet-without-parameters.md).</span></span>

```csharp
[Cmdlet(VerbsCommon.Get, "proc")]
public class GetProcCommand: Cmdlet
```

```vb
<Cmdlet(VerbsCommon.Get, "Proc")> _
Public Class GetProcCommand
    Inherits Cmdlet
```

## <a name="defining-parameters"></a><span data-ttu-id="ab0b4-116">Definizione dei parametri</span><span class="sxs-lookup"><span data-stu-id="ab0b4-116">Defining Parameters</span></span>

<span data-ttu-id="ab0b4-117">Se necessario, il cmdlet necessario definire i parametri per l'elaborazione dell'input.</span><span class="sxs-lookup"><span data-stu-id="ab0b4-117">If necessary, your cmdlet must define parameters for processing input.</span></span>
<span data-ttu-id="ab0b4-118">Questo cmdlet Get-Proc definisce un **Name** parametro, come descritto in [aggiunta di parametri di Input della riga di comando processo](adding-parameters-that-process-command-line-input.md).</span><span class="sxs-lookup"><span data-stu-id="ab0b4-118">This Get-Proc cmdlet defines a **Name** parameter as described in [Adding Parameters that Process Command-Line Input](adding-parameters-that-process-command-line-input.md).</span></span>

<span data-ttu-id="ab0b4-119">Di seguito è riportata la dichiarazione di parametro per il **nome** parametro del cmdlet Get-Process.</span><span class="sxs-lookup"><span data-stu-id="ab0b4-119">Here is the parameter declaration for the **Name** parameter of this Get-Proc cmdlet.</span></span>

```csharp
[Parameter(
           Position = 0,
           ValueFromPipeline = true,
           ValueFromPipelineByPropertyName = true
)]
[ValidateNotNullOrEmpty]
public string[] Name
{
  get { return processNames; }
  set { processNames = value; }
}
private string[] processNames;
```

```vb
<Parameter(Position:=0, ValueFromPipeline:=True, _
ValueFromPipelineByPropertyName:=True), ValidateNotNullOrEmpty()> _
Public Property Name() As String()
    Get
        Return processNames
    End Get

    Set(ByVal value As String())
        processNames = value
    End Set

End Property
```

## <a name="overriding-input-processing-methods"></a><span data-ttu-id="ab0b4-120">Si esegue l'override di metodi di elaborazione dell'Input</span><span class="sxs-lookup"><span data-stu-id="ab0b4-120">Overriding Input Processing Methods</span></span>

<span data-ttu-id="ab0b4-121">Tutti i cmdlet devono eseguire l'override di almeno uno dei metodi forniti dall'elaborazione dell'input di [System.Management.Automation.Cmdlet][] classe.</span><span class="sxs-lookup"><span data-stu-id="ab0b4-121">All cmdlets must override at least one of the input processing methods provided by the [System.Management.Automation.Cmdlet][] class.</span></span>
<span data-ttu-id="ab0b4-122">Questi metodi sono descritti in [la creazione del primo Cmdlet](creating-a-cmdlet-without-parameters.md).</span><span class="sxs-lookup"><span data-stu-id="ab0b4-122">These methods are discussed in [Creating Your First Cmdlet](creating-a-cmdlet-without-parameters.md).</span></span>

> [!NOTE]
> <span data-ttu-id="ab0b4-123">Il cmdlet consente di gestire ogni record più indipendente possibile.</span><span class="sxs-lookup"><span data-stu-id="ab0b4-123">Your cmdlet should handle each record as independently as possible.</span></span>

<span data-ttu-id="ab0b4-124">Esegue l'override di questo cmdlet Get-Proc il [System.Management.Automation.Cmdlet.ProcessRecord][] metodo per gestire le **nome** parametro per l'input fornito dall'utente o uno script.</span><span class="sxs-lookup"><span data-stu-id="ab0b4-124">This Get-Proc cmdlet overrides the [System.Management.Automation.Cmdlet.ProcessRecord][] method to handle the **Name** parameter for input provided by the user or a script.</span></span>
<span data-ttu-id="ab0b4-125">Questo metodo otterranno i processi per ogni nome di processo richiesto o tutti i processi se viene fornito alcun nome.</span><span class="sxs-lookup"><span data-stu-id="ab0b4-125">This method will get the processes for each requested process name or all processes if no name is provided.</span></span>
<span data-ttu-id="ab0b4-126">Dettagli di questa sostituzione sono disponibili nella [la creazione del primo Cmdlet](creating-a-cmdlet-without-parameters.md).</span><span class="sxs-lookup"><span data-stu-id="ab0b4-126">Details of this override are given in [Creating Your First Cmdlet](creating-a-cmdlet-without-parameters.md).</span></span>

### <a name="things-to-remember-when-reporting-errors"></a><span data-ttu-id="ab0b4-127">Aspetti da ricordare quando si segnalano gli errori</span><span class="sxs-lookup"><span data-stu-id="ab0b4-127">Things to Remember When Reporting Errors</span></span>

<span data-ttu-id="ab0b4-128">Il [System.Management.Automation.ErrorRecord][] che il cmdlet ha esito positivo quando la scrittura di un errore richiede un'eccezione alla base dell'oggetto.</span><span class="sxs-lookup"><span data-stu-id="ab0b4-128">The [System.Management.Automation.ErrorRecord][] object that the cmdlet passes when writing an error requires an exception at its core.</span></span>
<span data-ttu-id="ab0b4-129">Seguire le linee guida di .NET durante la determinazione di eccezione da usare.</span><span class="sxs-lookup"><span data-stu-id="ab0b4-129">Follow the .NET guidelines when determining the exception to use.</span></span>
<span data-ttu-id="ab0b4-130">In sostanza, se l'errore è semanticamente identico un'eccezione esistente, il cmdlet deve usare o derivare da tale eccezione.</span><span class="sxs-lookup"><span data-stu-id="ab0b4-130">Basically, if the error is semantically the same as an existing exception, the cmdlet should use or derive from that exception.</span></span>
<span data-ttu-id="ab0b4-131">In caso contrario, consigliabile derivare una nuova eccezione o una gerarchia di eccezione direttamente dai [System.Exception][] classe.</span><span class="sxs-lookup"><span data-stu-id="ab0b4-131">Otherwise, it should derive a new exception or exception hierarchy directly from the [System.Exception][] class.</span></span>

<span data-ttu-id="ab0b4-132">Durante la creazione di identificatori di errore, accessibili tramite la proprietà FullyQualifiedErrorId della classe ErrorRecord, tenere presente quanto segue.</span><span class="sxs-lookup"><span data-stu-id="ab0b4-132">When creating error identifiers (accessed through the FullyQualifiedErrorId property of the ErrorRecord class) keep the following in mind.</span></span>

- <span data-ttu-id="ab0b4-133">Stringhe di utilizzo assegnati per scopi diagnostici in modo che quando si esamina l'identificatore completo è possibile determinare la causa del problema è e in cui l'errore proviene dal.</span><span class="sxs-lookup"><span data-stu-id="ab0b4-133">Use strings that are targeted for diagnostic purposes so that when inspecting the fully qualified identifier you can determine what the error is and where the error came from.</span></span>

- <span data-ttu-id="ab0b4-134">Un identificatore di errore completo valido potrebbe essere come segue.</span><span class="sxs-lookup"><span data-stu-id="ab0b4-134">A well formed fully qualified error identifier might be as follows.</span></span>

`CommandNotFoundException,Microsoft.PowerShell.Commands.GetCommandCommand`

<span data-ttu-id="ab0b4-135">Si noti che nell'esempio precedente, l'identificatore dell'errore (il primo token) definisce l'errore e la parte rimanente indica dove l'errore proviene.</span><span class="sxs-lookup"><span data-stu-id="ab0b4-135">Notice that in the previous example, the error identifier (the first token) designates what the error is and the remaining part indicates where the error came from.</span></span>

- <span data-ttu-id="ab0b4-136">Per scenari più complessi, l'identificatore dell'errore può essere un token separati da punto che può essere analizzato in ispezione.</span><span class="sxs-lookup"><span data-stu-id="ab0b4-136">For more complex scenarios, the error identifier can be a dot separated token that can be parsed on inspection.</span></span>
  <span data-ttu-id="ab0b4-137">In questo modo che si crea un ramo troppo sulle parti dell'identificatore dell'errore, nonché la categoria dell'errore identificatore ed errore.</span><span class="sxs-lookup"><span data-stu-id="ab0b4-137">This allows you too branch on the parts of the error identifier as well as the error identifier and error category.</span></span>

<span data-ttu-id="ab0b4-138">Il cmdlet deve assegnare identificatori di errore specifico ai percorsi del codice diversi.</span><span class="sxs-lookup"><span data-stu-id="ab0b4-138">The cmdlet should assign specific error identifiers to different code paths.</span></span>
<span data-ttu-id="ab0b4-139">Tenere presente per l'assegnazione di identificatori di errore le informazioni seguenti:</span><span class="sxs-lookup"><span data-stu-id="ab0b4-139">Keep the following information in mind for assignment of error identifiers:</span></span>

- <span data-ttu-id="ab0b4-140">Un identificatore di errore dovrebbe rimanere costante durante il ciclo di vita di cmdlet.</span><span class="sxs-lookup"><span data-stu-id="ab0b4-140">An error identifier should remain constant throughout the cmdlet life cycle.</span></span>
  <span data-ttu-id="ab0b4-141">Non modificare la semantica di un identificatore di errore tra le versioni di cmdlet.</span><span class="sxs-lookup"><span data-stu-id="ab0b4-141">Do not change the semantics of an error identifier between cmdlet versions.</span></span>

- <span data-ttu-id="ab0b4-142">Usare testo per un identificatore di errore che fornisce risposte superficiali corrispondente all'errore segnalato.</span><span class="sxs-lookup"><span data-stu-id="ab0b4-142">Use text for an error identifier that tersely corresponds to the error being reported.</span></span>
  <span data-ttu-id="ab0b4-143">Non usare spazi vuoti o punteggiatura.</span><span class="sxs-lookup"><span data-stu-id="ab0b4-143">Do not use white space or punctuation.</span></span>

- <span data-ttu-id="ab0b4-144">Generare solo gli identificatori degli errori che sono riproducibile con il cmdlet.</span><span class="sxs-lookup"><span data-stu-id="ab0b4-144">Have your cmdlet generate only error identifiers that are reproducible.</span></span>
  <span data-ttu-id="ab0b4-145">Ad esempio, non deve generare un identificatore che include un identificatore di processo.</span><span class="sxs-lookup"><span data-stu-id="ab0b4-145">For example, it should not generate an identifier that includes a process identifier.</span></span>
  <span data-ttu-id="ab0b4-146">Gli identificatori di errore sono utili per un utente solo se corrispondono agli identificatori visualizzate da altri utenti che rilevano lo stesso problema.</span><span class="sxs-lookup"><span data-stu-id="ab0b4-146">Error identifiers are useful to a user only when they correspond to identifiers that are seen by other users experiencing the same problem.</span></span>

<span data-ttu-id="ab0b4-147">Le eccezioni non gestite non vengono rilevate dal PowerShell nelle condizioni seguenti:</span><span class="sxs-lookup"><span data-stu-id="ab0b4-147">Unhandled exceptions are not caught by PowerShell in the following conditions:</span></span>

- <span data-ttu-id="ab0b4-148">Se un cmdlet crea un nuovo thread e il codice in esecuzione in quanto thread genera un'eccezione non gestita, PowerShell non rileva l'errore e terminerà il processo.</span><span class="sxs-lookup"><span data-stu-id="ab0b4-148">If a cmdlet creates a new thread and code running in that thread throws an unhandled exception, PowerShell will not catch the error and will terminate the process.</span></span>

- <span data-ttu-id="ab0b4-149">Se un oggetto dispone di codice che genera un'eccezione non gestita nel relativo distruttore o i metodi Dispose, PowerShell non rileva l'errore e terminerà il processo.</span><span class="sxs-lookup"><span data-stu-id="ab0b4-149">If an object has code in its destructor or Dispose methods that causes an unhandled exception, PowerShell will not catch the error and will terminate the process.</span></span>

## <a name="reporting-nonterminating-errors"></a><span data-ttu-id="ab0b4-150">Segnalazione di errori non fatali</span><span class="sxs-lookup"><span data-stu-id="ab0b4-150">Reporting Nonterminating Errors</span></span>

<span data-ttu-id="ab0b4-151">Uno dei metodi di elaborazione dell'input può segnalare un errore non fatali per il flusso di output usando il [System.Management.Automation.Cmdlet.WriteError][] (metodo).</span><span class="sxs-lookup"><span data-stu-id="ab0b4-151">Any one of the input processing methods can report a nonterminating error to the output stream using the [System.Management.Automation.Cmdlet.WriteError][] method.</span></span>

<span data-ttu-id="ab0b4-152">Di seguito è riportato un esempio di codice da questo cmdlet Get-Process che illustra la chiamata a [System.Management.Automation.Cmdlet.WriteError][] all'interno dell'override del [System.Management.Automation.Cmdlet.ProcessRecord][] (metodo).</span><span class="sxs-lookup"><span data-stu-id="ab0b4-152">Here is a code example from this Get-Proc cmdlet that illustrates the call to [System.Management.Automation.Cmdlet.WriteError][] from within the override of the [System.Management.Automation.Cmdlet.ProcessRecord][] method.</span></span>
<span data-ttu-id="ab0b4-153">In questo caso, la chiamata viene eseguita se il cmdlet non è possibile trovare un processo per un identificatore di processo specificato.</span><span class="sxs-lookup"><span data-stu-id="ab0b4-153">In this case, the call is made if the cmdlet cannot find a process for a specified process identifier.</span></span>

```csharp
protected override void ProcessRecord()
{
  // If no name parameter passed to cmdlet, get all processes.
  if (processNames == null)
  {
    WriteObject(Process.GetProcesses(), true);
  }
    else
    {
      // If a name parameter is passed to cmdlet, get and write
      // the associated processes.
      // Write a nonterminating error for failure to retrieve
      // a process.
      foreach (string name in processNames)
      {
        Process[] processes;

        try
        {
          processes = Process.GetProcessesByName(name);
        }
        catch (InvalidOperationException ex)
        {
          WriteError(new ErrorRecord(
                     ex,
                     "NameNotFound",
                     ErrorCategory.InvalidOperation,
                     name));
          continue;
        }

        WriteObject(processes, true);
      } // foreach (...
    } // else
  }
```

### <a name="things-to-remember-about-writing-nonterminating-errors"></a><span data-ttu-id="ab0b4-154">Aspetti da ricordare sulla scrittura di errori non fatali</span><span class="sxs-lookup"><span data-stu-id="ab0b4-154">Things to Remember About Writing Nonterminating Errors</span></span>

<span data-ttu-id="ab0b4-155">Per un errore non fatali, il cmdlet necessario generare un identificatore di errore specifico per ogni oggetto di input specifico.</span><span class="sxs-lookup"><span data-stu-id="ab0b4-155">For a nonterminating error, the cmdlet must generate a specific error identifier for each specific input object.</span></span>

<span data-ttu-id="ab0b4-156">Un cmdlet deve spesso modificare l'azione di PowerShell generato da un errore non fatali.</span><span class="sxs-lookup"><span data-stu-id="ab0b4-156">A cmdlet frequently needs to modify the PowerShell action produced by a nonterminating error.</span></span>
<span data-ttu-id="ab0b4-157">È possibile eseguire questa operazione definendo i `ErrorAction` e `ErrorVariable` parametri.</span><span class="sxs-lookup"><span data-stu-id="ab0b4-157">It can do this by defining the `ErrorAction` and `ErrorVariable` parameters.</span></span>
<span data-ttu-id="ab0b4-158">Se la definizione del `ErrorAction` parametro, il cmdlet Visualizza le opzioni utente [System.Management.Automation.ActionPreference][], è possibile influenzare anche direttamente l'azione impostando il `$ErrorActionPreference` variabile.</span><span class="sxs-lookup"><span data-stu-id="ab0b4-158">If defining the `ErrorAction` parameter, the cmdlet presents the user options [System.Management.Automation.ActionPreference][], you can also directly influence the action by setting the `$ErrorActionPreference` variable.</span></span>

<span data-ttu-id="ab0b4-159">Il cmdlet è possibile salvare gli errori non fatali in una variabile utilizzando la `ErrorVariable` parametro, che non è interessato dall'impostazione della `ErrorAction`.</span><span class="sxs-lookup"><span data-stu-id="ab0b4-159">The cmdlet can save nonterminating errors to a variable using the `ErrorVariable` parameter, which is not affected by the setting of `ErrorAction`.</span></span>
<span data-ttu-id="ab0b4-160">Errori possono essere aggiunta in una variabile di errore esistente aggiungendo un segno più (+) all'inizio del nome della variabile.</span><span class="sxs-lookup"><span data-stu-id="ab0b4-160">Failures can be appended to an existing error variable by adding a plus sign (+) to the front of the variable name.</span></span>

## <a name="code-sample"></a><span data-ttu-id="ab0b4-161">Esempio di codice</span><span class="sxs-lookup"><span data-stu-id="ab0b4-161">Code Sample</span></span>

<span data-ttu-id="ab0b4-162">Per l'intero C# esempi di codice, vedere [GetProcessSample04 campione](./getprocesssample04-sample.md).</span><span class="sxs-lookup"><span data-stu-id="ab0b4-162">For the complete C# sample code, see [GetProcessSample04 Sample](./getprocesssample04-sample.md).</span></span>

## <a name="define-object-types-and-formatting"></a><span data-ttu-id="ab0b4-163">Definire i tipi di oggetto e la formattazione</span><span class="sxs-lookup"><span data-stu-id="ab0b4-163">Define Object Types and Formatting</span></span>

<span data-ttu-id="ab0b4-164">PowerShell passa informazioni tra i cmdlet con gli oggetti .NET.</span><span class="sxs-lookup"><span data-stu-id="ab0b4-164">PowerShell passes information between cmdlets using .NET objects.</span></span>
<span data-ttu-id="ab0b4-165">Di conseguenza, potrebbe essere necessario definire un proprio tipo di un cmdlet o il cmdlet potrebbe essere necessario estendere un tipo esistente fornito da un altro cmdlet.</span><span class="sxs-lookup"><span data-stu-id="ab0b4-165">Consequently, a cmdlet might need to define its own type, or the cmdlet might need to extend an existing type provided by another cmdlet.</span></span>
<span data-ttu-id="ab0b4-166">Per altre informazioni sulla definizione di nuovi tipi o estendere i tipi esistenti, vedere [estendendo i tipi di oggetto e formattazione](http://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351).</span><span class="sxs-lookup"><span data-stu-id="ab0b4-166">For more information about defining new types or extending existing types, see [Extending Object Types and Formatting](http://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351).</span></span>

## <a name="building-the-cmdlet"></a><span data-ttu-id="ab0b4-167">Creazione di Cmdlet</span><span class="sxs-lookup"><span data-stu-id="ab0b4-167">Building the Cmdlet</span></span>

<span data-ttu-id="ab0b4-168">Dopo l'implementazione di un cmdlet, è necessario registrarlo con Windows PowerShell tramite uno snap-in Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="ab0b4-168">After implementing a cmdlet, you must register it with Windows PowerShell through a Windows PowerShell snap-in.</span></span>
<span data-ttu-id="ab0b4-169">Per altre informazioni sulla registrazione dei cmdlet, vedere [come registrare i cmdlet, provider e applicazioni Host](http://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c).</span><span class="sxs-lookup"><span data-stu-id="ab0b4-169">For more information about registering cmdlets, see [How to Register Cmdlets, Providers, and Host Applications](http://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c).</span></span>

## <a name="testing-the-cmdlet"></a><span data-ttu-id="ab0b4-170">Il Cmdlet di test</span><span class="sxs-lookup"><span data-stu-id="ab0b4-170">Testing the Cmdlet</span></span>

<span data-ttu-id="ab0b4-171">Quando il cmdlet è stato registrato con PowerShell, è possibile testarlo eseguendolo dalla riga di comando.</span><span class="sxs-lookup"><span data-stu-id="ab0b4-171">When your cmdlet has been registered with PowerShell, you can test it by running it on the command line.</span></span>
<span data-ttu-id="ab0b4-172">È possibile testare il cmdlet Get-Process di esempio per vedere se viene segnalato un errore:</span><span class="sxs-lookup"><span data-stu-id="ab0b4-172">Let's test the sample Get-Proc cmdlet to see whether it reports an error:</span></span>

- <span data-ttu-id="ab0b4-173">Avviare PowerShell e usare il cmdlet Get-Process per recuperare i processi denominati "TEST".</span><span class="sxs-lookup"><span data-stu-id="ab0b4-173">Start PowerShell, and use the Get-Proc cmdlet to retrieve the processes named "TEST".</span></span>

    ```powershell
    PS> get-proc -name test
    ```

<span data-ttu-id="ab0b4-174">Viene visualizzato l'output seguente.</span><span class="sxs-lookup"><span data-stu-id="ab0b4-174">The following output appears.</span></span>

    ```
    get-proc : Operation is not valid due to the current state of the object.
    At line:1 char:9
    + get-proc  <<<< -name test
    ```

## <a name="see-also"></a><span data-ttu-id="ab0b4-175">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="ab0b4-175">See Also</span></span>

[<span data-ttu-id="ab0b4-176">Aggiunta di parametri di Input della Pipeline di processo</span><span class="sxs-lookup"><span data-stu-id="ab0b4-176">Adding Parameters that Process Pipeline Input</span></span>](./adding-parameters-that-process-pipeline-input.md)

[<span data-ttu-id="ab0b4-177">Aggiunta di parametri che elaborano gli Input della riga di comando</span><span class="sxs-lookup"><span data-stu-id="ab0b4-177">Adding Parameters that Process Command-Line Input</span></span>](./adding-parameters-that-process-command-line-input.md)

[<span data-ttu-id="ab0b4-178">Creazione del primo Cmdlet</span><span class="sxs-lookup"><span data-stu-id="ab0b4-178">Creating Your First Cmdlet</span></span>](./creating-a-cmdlet-without-parameters.md)

[<span data-ttu-id="ab0b4-179">Estensione di tipi di oggetto e la formattazione</span><span class="sxs-lookup"><span data-stu-id="ab0b4-179">Extending Object Types and Formatting</span></span>](http://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351)

[<span data-ttu-id="ab0b4-180">Come registrare i cmdlet, provider e applicazioni Host</span><span class="sxs-lookup"><span data-stu-id="ab0b4-180">How to Register Cmdlets, Providers, and Host Applications</span></span>](http://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c)

<span data-ttu-id="ab0b4-181">[Windows PowerShell Reference](../windows-powershell-reference.md) (Guida di riferimento di PowerShell)</span><span class="sxs-lookup"><span data-stu-id="ab0b4-181">[Windows PowerShell Reference](../windows-powershell-reference.md)</span></span>

[<span data-ttu-id="ab0b4-182">Esempi di cmdlet</span><span class="sxs-lookup"><span data-stu-id="ab0b4-182">Cmdlet Samples</span></span>](./cmdlet-samples.md)

[System.Exception]: /dotnet/api/System.Exception
[System.Management.Automation.ActionPreference]: /dotnet/api/System.Management.Automation.ActionPreference
[System.Management.Automation.Cmdlet.ProcessRecord]: /dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord
[System.Management.Automation.Cmdlet.WriteError]: /dotnet/api/System.Management.Automation.Cmdlet.WriteError
[System.Management.Automation.Cmdlet]: /dotnet/api/System.Management.Automation.Cmdlet
[System.Management.Automation.ErrorCategory]: /dotnet/api/System.Management.Automation.ErrorCategory
[System.Management.Automation.ErrorRecord]: /dotnet/api/System.Management.Automation.ErrorRecord
