---
title: Aggiunta di segnalazione errori non fatale al cmdlet | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f2a1531a-a92a-4606-9d54-c5df80d34f33
caps.latest.revision: 8
ms.openlocfilehash: ec29d1cffa083e4cce667d3e1efbd4eeecbffb51
ms.sourcegitcommit: d97b200e7a49315ce6608cd619e3e2fd99193edd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/10/2020
ms.locfileid: "75870116"
---
# <a name="adding-non-terminating-error-reporting-to-your-cmdlet"></a><span data-ttu-id="d88ee-102">Aggiunta di segnalazioni di errori non irreversibili al cmdlet</span><span class="sxs-lookup"><span data-stu-id="d88ee-102">Adding Non-Terminating Error Reporting to Your Cmdlet</span></span>

<span data-ttu-id="d88ee-103">I cmdlet possono segnalare errori non fatali chiamando il metodo [System. Management. Automation. cmdlet. WriteError][] e continuano comunque a funzionare sull'oggetto di input corrente o su altri oggetti pipeline in ingresso.</span><span class="sxs-lookup"><span data-stu-id="d88ee-103">Cmdlets can report nonterminating errors by calling the [System.Management.Automation.Cmdlet.WriteError][] method and still continue to operate on the current input object or on further incoming pipeline objects.</span></span> <span data-ttu-id="d88ee-104">In questa sezione viene illustrato come creare un cmdlet per la segnalazione di errori non fatali dei relativi metodi di elaborazione dell'input.</span><span class="sxs-lookup"><span data-stu-id="d88ee-104">This section explains how to create a cmdlet that reports nonterminating errors from its input processing methods.</span></span>

<span data-ttu-id="d88ee-105">Per gli errori non fatali (nonché per la terminazione degli errori), il cmdlet deve passare un oggetto [System. Management. Automation. ErrorRecord][] che identifica l'errore.</span><span class="sxs-lookup"><span data-stu-id="d88ee-105">For nonterminating errors (as well as terminating errors), the cmdlet must pass an [System.Management.Automation.ErrorRecord][] object identifying the error.</span></span> <span data-ttu-id="d88ee-106">Ogni record di errore è identificato da una stringa univoca denominata "identificatore errore".</span><span class="sxs-lookup"><span data-stu-id="d88ee-106">Each error record is identified by a unique string called the "error identifier".</span></span> <span data-ttu-id="d88ee-107">Oltre all'identificatore, la categoria di ogni errore viene specificata dalle costanti definite da un'enumerazione [System. Management. Automation. ErrorCategory][] .</span><span class="sxs-lookup"><span data-stu-id="d88ee-107">In addition to the identifier, the category of each error is specified by constants defined by a [System.Management.Automation.ErrorCategory][] enumeration.</span></span> <span data-ttu-id="d88ee-108">L'utente può visualizzare gli errori in base alla relativa categoria impostando la variabile `$ErrorView` su "CategoryView".</span><span class="sxs-lookup"><span data-stu-id="d88ee-108">The user can view errors based on their category by setting the `$ErrorView` variable to "CategoryView".</span></span>

<span data-ttu-id="d88ee-109">Per ulteriori informazioni sui record degli errori, vedere la pagina relativa ai [record degli errori di Windows PowerShell](./windows-powershell-error-records.md).</span><span class="sxs-lookup"><span data-stu-id="d88ee-109">For more information about error records, see [Windows PowerShell Error Records](./windows-powershell-error-records.md).</span></span>

## <a name="defining-the-cmdlet"></a><span data-ttu-id="d88ee-110">Definizione del cmdlet</span><span class="sxs-lookup"><span data-stu-id="d88ee-110">Defining the Cmdlet</span></span>

<span data-ttu-id="d88ee-111">Il primo passaggio nella creazione di cmdlet è sempre il nome del cmdlet e la dichiarazione della classe .NET che implementa il cmdlet.</span><span class="sxs-lookup"><span data-stu-id="d88ee-111">The first step in cmdlet creation is always naming the cmdlet and declaring the .NET class that implements the cmdlet.</span></span> <span data-ttu-id="d88ee-112">Questo cmdlet recupera le informazioni sul processo, quindi il nome del verbo scelto qui è "Get".</span><span class="sxs-lookup"><span data-stu-id="d88ee-112">This cmdlet retrieves process information, so the verb name chosen here is "Get".</span></span> <span data-ttu-id="d88ee-113">(Quasi tutti i tipi di cmdlet in grado di recuperare informazioni possono elaborare l'input della riga di comando). Per altre informazioni sui verbi di cmdlet approvati, vedere [nomi dei verbi di cmdlet](approved-verbs-for-windows-powershell-commands.md).</span><span class="sxs-lookup"><span data-stu-id="d88ee-113">(Almost any sort of cmdlet that is capable of retrieving information can process command-line input.) For more information about approved cmdlet verbs, see [Cmdlet Verb Names](approved-verbs-for-windows-powershell-commands.md).</span></span>

<span data-ttu-id="d88ee-114">Di seguito è riportata la definizione di questo cmdlet `Get-Proc`.</span><span class="sxs-lookup"><span data-stu-id="d88ee-114">The following is the definition for this `Get-Proc` cmdlet.</span></span> <span data-ttu-id="d88ee-115">I dettagli di questa definizione sono forniti durante [la creazione del primo cmdlet](creating-a-cmdlet-without-parameters.md).</span><span class="sxs-lookup"><span data-stu-id="d88ee-115">Details of this definition are given in [Creating Your First Cmdlet](creating-a-cmdlet-without-parameters.md).</span></span>

```csharp
[Cmdlet(VerbsCommon.Get, "proc")]
public class GetProcCommand: Cmdlet
```

```vb
<Cmdlet(VerbsCommon.Get, "Proc")> _
Public Class GetProcCommand
    Inherits Cmdlet
```

## <a name="defining-parameters"></a><span data-ttu-id="d88ee-116">Definizione dei parametri</span><span class="sxs-lookup"><span data-stu-id="d88ee-116">Defining Parameters</span></span>

<span data-ttu-id="d88ee-117">Se necessario, il cmdlet deve definire i parametri per l'elaborazione dell'input.</span><span class="sxs-lookup"><span data-stu-id="d88ee-117">If necessary, your cmdlet must define parameters for processing input.</span></span> <span data-ttu-id="d88ee-118">Questo cmdlet Get-proc definisce un parametro del **nome** come descritto in [aggiunta di parametri che elaborano l'input della riga di comando](adding-parameters-that-process-command-line-input.md).</span><span class="sxs-lookup"><span data-stu-id="d88ee-118">This Get-Proc cmdlet defines a **Name** parameter as described in [Adding Parameters that Process Command-Line Input](adding-parameters-that-process-command-line-input.md).</span></span>

<span data-ttu-id="d88ee-119">Di seguito è illustrata la dichiarazione di parametro per il parametro **Name** del cmdlet Get-proc.</span><span class="sxs-lookup"><span data-stu-id="d88ee-119">Here is the parameter declaration for the **Name** parameter of this Get-Proc cmdlet.</span></span>

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

## <a name="overriding-input-processing-methods"></a><span data-ttu-id="d88ee-120">Override dei metodi di elaborazione degli input</span><span class="sxs-lookup"><span data-stu-id="d88ee-120">Overriding Input Processing Methods</span></span>

<span data-ttu-id="d88ee-121">Tutti i cmdlet devono eseguire l'override di almeno uno dei metodi di elaborazione dell'input forniti dalla classe [System. Management. Automation. cmdlet][] .</span><span class="sxs-lookup"><span data-stu-id="d88ee-121">All cmdlets must override at least one of the input processing methods provided by the [System.Management.Automation.Cmdlet][] class.</span></span> <span data-ttu-id="d88ee-122">Questi metodi vengono descritti in [creazione del primo cmdlet](creating-a-cmdlet-without-parameters.md).</span><span class="sxs-lookup"><span data-stu-id="d88ee-122">These methods are discussed in [Creating Your First Cmdlet](creating-a-cmdlet-without-parameters.md).</span></span>

> [!NOTE]
> <span data-ttu-id="d88ee-123">Il cmdlet deve gestire ogni record nel modo più indipendente possibile.</span><span class="sxs-lookup"><span data-stu-id="d88ee-123">Your cmdlet should handle each record as independently as possible.</span></span>

<span data-ttu-id="d88ee-124">Questo cmdlet Get-proc esegue l'override del metodo [System. Management. Automation. cmdlet. ProcessRecord][] per gestire il parametro **Name** per l'input fornito dall'utente o da uno script.</span><span class="sxs-lookup"><span data-stu-id="d88ee-124">This Get-Proc cmdlet overrides the [System.Management.Automation.Cmdlet.ProcessRecord][] method to handle the **Name** parameter for input provided by the user or a script.</span></span> <span data-ttu-id="d88ee-125">Questo metodo otterrà i processi per ogni nome di processo richiesto o per tutti i processi se non viene specificato alcun nome.</span><span class="sxs-lookup"><span data-stu-id="d88ee-125">This method will get the processes for each requested process name or all processes if no name is provided.</span></span> <span data-ttu-id="d88ee-126">I dettagli di questa sostituzione sono forniti in [creazione del primo cmdlet](creating-a-cmdlet-without-parameters.md).</span><span class="sxs-lookup"><span data-stu-id="d88ee-126">Details of this override are given in [Creating Your First Cmdlet](creating-a-cmdlet-without-parameters.md).</span></span>

### <a name="things-to-remember-when-reporting-errors"></a><span data-ttu-id="d88ee-127">Aspetti da ricordare quando si segnalano errori</span><span class="sxs-lookup"><span data-stu-id="d88ee-127">Things to Remember When Reporting Errors</span></span>

<span data-ttu-id="d88ee-128">L'oggetto [System. Management. Automation. ErrorRecord][] passato dal cmdlet quando si scrive un errore richiede un'eccezione al suo interno.</span><span class="sxs-lookup"><span data-stu-id="d88ee-128">The [System.Management.Automation.ErrorRecord][] object that the cmdlet passes when writing an error requires an exception at its core.</span></span> <span data-ttu-id="d88ee-129">Per determinare l'eccezione da usare, seguire le linee guida di .NET.</span><span class="sxs-lookup"><span data-stu-id="d88ee-129">Follow the .NET guidelines when determining the exception to use.</span></span>
<span data-ttu-id="d88ee-130">In sostanza, se l'errore è semanticamente uguale a un'eccezione esistente, il cmdlet deve usare o derivare da tale eccezione.</span><span class="sxs-lookup"><span data-stu-id="d88ee-130">Basically, if the error is semantically the same as an existing exception, the cmdlet should use or derive from that exception.</span></span> <span data-ttu-id="d88ee-131">In caso contrario, deve derivare una nuova eccezione o una nuova gerarchia di eccezioni direttamente dalla classe [System. Exception][] .</span><span class="sxs-lookup"><span data-stu-id="d88ee-131">Otherwise, it should derive a new exception or exception hierarchy directly from the [System.Exception][] class.</span></span>

<span data-ttu-id="d88ee-132">Quando si creano identificatori di errore (a cui si accede tramite la proprietà FullyQualifiedErrorId della classe ErrorRecord), tenere presente quanto segue.</span><span class="sxs-lookup"><span data-stu-id="d88ee-132">When creating error identifiers (accessed through the FullyQualifiedErrorId property of the ErrorRecord class) keep the following in mind.</span></span>

- <span data-ttu-id="d88ee-133">Usare le stringhe destinate a scopi diagnostici in modo che, quando si esamina l'identificatore completo, sia possibile determinare l'errore e il punto in cui è stato generato l'errore.</span><span class="sxs-lookup"><span data-stu-id="d88ee-133">Use strings that are targeted for diagnostic purposes so that when inspecting the fully qualified identifier you can determine what the error is and where the error came from.</span></span>

- <span data-ttu-id="d88ee-134">Un identificatore di errore completo ben formato potrebbe essere il seguente.</span><span class="sxs-lookup"><span data-stu-id="d88ee-134">A well formed fully qualified error identifier might be as follows.</span></span>

  `CommandNotFoundException,Microsoft.PowerShell.Commands.GetCommandCommand`

<span data-ttu-id="d88ee-135">Si noti che nell'esempio precedente, l'identificatore di errore (il primo token) designa l'errore e la parte rimanente indica da dove proviene l'errore.</span><span class="sxs-lookup"><span data-stu-id="d88ee-135">Notice that in the previous example, the error identifier (the first token) designates what the error is and the remaining part indicates where the error came from.</span></span>

- <span data-ttu-id="d88ee-136">Per scenari più complessi, l'identificatore di errore può essere un token separato da punti che può essere analizzato durante l'ispezione.</span><span class="sxs-lookup"><span data-stu-id="d88ee-136">For more complex scenarios, the error identifier can be a dot separated token that can be parsed on inspection.</span></span> <span data-ttu-id="d88ee-137">In questo modo è possibile creare rami anche per le parti dell'identificatore di errore, nonché l'identificatore e la categoria di errore.</span><span class="sxs-lookup"><span data-stu-id="d88ee-137">This allows you too branch on the parts of the error identifier as well as the error identifier and error category.</span></span>

<span data-ttu-id="d88ee-138">Il cmdlet deve assegnare identificatori di errore specifici a percorsi di codice diversi.</span><span class="sxs-lookup"><span data-stu-id="d88ee-138">The cmdlet should assign specific error identifiers to different code paths.</span></span> <span data-ttu-id="d88ee-139">Per l'assegnazione degli identificatori di errore, tenere presenti le seguenti informazioni:</span><span class="sxs-lookup"><span data-stu-id="d88ee-139">Keep the following information in mind for assignment of error identifiers:</span></span>

- <span data-ttu-id="d88ee-140">Un identificatore di errore deve rimanere costante durante tutto il ciclo di vita del cmdlet.</span><span class="sxs-lookup"><span data-stu-id="d88ee-140">An error identifier should remain constant throughout the cmdlet life cycle.</span></span> <span data-ttu-id="d88ee-141">Non modificare la semantica di un identificatore errore tra le versioni dei cmdlet.</span><span class="sxs-lookup"><span data-stu-id="d88ee-141">Do not change the semantics of an error identifier between cmdlet versions.</span></span>
- <span data-ttu-id="d88ee-142">Usare il testo per un identificatore di errore che laconicamente corrisponde all'errore segnalato.</span><span class="sxs-lookup"><span data-stu-id="d88ee-142">Use text for an error identifier that tersely corresponds to the error being reported.</span></span> <span data-ttu-id="d88ee-143">Non usare spazi vuoti o segni di punteggiatura.</span><span class="sxs-lookup"><span data-stu-id="d88ee-143">Do not use white space or punctuation.</span></span>
- <span data-ttu-id="d88ee-144">Se il cmdlet genera solo identificatori di errore riproducibili.</span><span class="sxs-lookup"><span data-stu-id="d88ee-144">Have your cmdlet generate only error identifiers that are reproducible.</span></span> <span data-ttu-id="d88ee-145">Ad esempio, non deve generare un identificatore che include un identificatore di processo.</span><span class="sxs-lookup"><span data-stu-id="d88ee-145">For example, it should not generate an identifier that includes a process identifier.</span></span> <span data-ttu-id="d88ee-146">Gli identificatori di errore sono utili per un utente solo quando corrispondono agli identificatori visualizzati da altri utenti che hanno riscontrato lo stesso problema.</span><span class="sxs-lookup"><span data-stu-id="d88ee-146">Error identifiers are useful to a user only when they correspond to identifiers that are seen by other users experiencing the same problem.</span></span>

<span data-ttu-id="d88ee-147">Le eccezioni non gestite non vengono rilevate da PowerShell nelle condizioni seguenti:</span><span class="sxs-lookup"><span data-stu-id="d88ee-147">Unhandled exceptions are not caught by PowerShell in the following conditions:</span></span>

- <span data-ttu-id="d88ee-148">Se un cmdlet crea un nuovo thread e il codice in esecuzione nel thread genera un'eccezione non gestita, PowerShell non rileva l'errore e termina il processo.</span><span class="sxs-lookup"><span data-stu-id="d88ee-148">If a cmdlet creates a new thread and code running in that thread throws an unhandled exception, PowerShell will not catch the error and will terminate the process.</span></span>
- <span data-ttu-id="d88ee-149">Se un oggetto dispone di codice nel relativo distruttore o di metodi Dispose che causa un'eccezione non gestita, PowerShell non rileva l'errore e termina il processo.</span><span class="sxs-lookup"><span data-stu-id="d88ee-149">If an object has code in its destructor or Dispose methods that causes an unhandled exception, PowerShell will not catch the error and will terminate the process.</span></span>

## <a name="reporting-nonterminating-errors"></a><span data-ttu-id="d88ee-150">Segnalazione di errori non fatali</span><span class="sxs-lookup"><span data-stu-id="d88ee-150">Reporting Nonterminating Errors</span></span>

<span data-ttu-id="d88ee-151">Uno dei metodi di elaborazione dell'input può segnalare un errore non fatale al flusso di output usando il metodo [System. Management. Automation. cmdlet. WriteError][] .</span><span class="sxs-lookup"><span data-stu-id="d88ee-151">Any one of the input processing methods can report a nonterminating error to the output stream using the [System.Management.Automation.Cmdlet.WriteError][] method.</span></span>

<span data-ttu-id="d88ee-152">Di seguito è riportato un esempio di codice di questo cmdlet Get-proc che illustra la chiamata a [System. Management. Automation. cmdlet. WriteError][] dall'interno dell'override del metodo [System. Management. Automation. cmdlet. ProcessRecord][] .</span><span class="sxs-lookup"><span data-stu-id="d88ee-152">Here is a code example from this Get-Proc cmdlet that illustrates the call to [System.Management.Automation.Cmdlet.WriteError][] from within the override of the [System.Management.Automation.Cmdlet.ProcessRecord][] method.</span></span> <span data-ttu-id="d88ee-153">In questo caso, la chiamata viene eseguita se il cmdlet non riesce a trovare un processo per un identificatore di processo specificato.</span><span class="sxs-lookup"><span data-stu-id="d88ee-153">In this case, the call is made if the cmdlet cannot find a process for a specified process identifier.</span></span>

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

### <a name="things-to-remember-about-writing-nonterminating-errors"></a><span data-ttu-id="d88ee-154">Aspetti da ricordare per la scrittura di errori non fatali</span><span class="sxs-lookup"><span data-stu-id="d88ee-154">Things to Remember About Writing Nonterminating Errors</span></span>

<span data-ttu-id="d88ee-155">Per un errore non fatale, il cmdlet deve generare un identificatore di errore specifico per ogni oggetto di input specifico.</span><span class="sxs-lookup"><span data-stu-id="d88ee-155">For a nonterminating error, the cmdlet must generate a specific error identifier for each specific input object.</span></span>

<span data-ttu-id="d88ee-156">Un cmdlet deve spesso modificare l'azione di PowerShell generata da un errore non fatale.</span><span class="sxs-lookup"><span data-stu-id="d88ee-156">A cmdlet frequently needs to modify the PowerShell action produced by a nonterminating error.</span></span> <span data-ttu-id="d88ee-157">Questa operazione può essere eseguita definendo i parametri `ErrorAction` e `ErrorVariable`.</span><span class="sxs-lookup"><span data-stu-id="d88ee-157">It can do this by defining the `ErrorAction` and `ErrorVariable` parameters.</span></span> <span data-ttu-id="d88ee-158">Se si definisce il parametro `ErrorAction`, il cmdlet presenta le opzioni utente [System. Management. Automation. preferenzaazione][], è anche possibile influenzare direttamente l'azione impostando la variabile `$ErrorActionPreference`.</span><span class="sxs-lookup"><span data-stu-id="d88ee-158">If defining the `ErrorAction` parameter, the cmdlet presents the user options [System.Management.Automation.ActionPreference][], you can also directly influence the action by setting the `$ErrorActionPreference` variable.</span></span>

<span data-ttu-id="d88ee-159">Il cmdlet consente di salvare errori non fatali in una variabile utilizzando il parametro `ErrorVariable`, che non è influenzato dall'impostazione di `ErrorAction`.</span><span class="sxs-lookup"><span data-stu-id="d88ee-159">The cmdlet can save nonterminating errors to a variable using the `ErrorVariable` parameter, which is not affected by the setting of `ErrorAction`.</span></span> <span data-ttu-id="d88ee-160">Gli errori possono essere aggiunti a una variabile di errore esistente aggiungendo un segno più (+) all'inizio del nome della variabile.</span><span class="sxs-lookup"><span data-stu-id="d88ee-160">Failures can be appended to an existing error variable by adding a plus sign (+) to the front of the variable name.</span></span>

## <a name="code-sample"></a><span data-ttu-id="d88ee-161">Codice di esempio</span><span class="sxs-lookup"><span data-stu-id="d88ee-161">Code Sample</span></span>

<span data-ttu-id="d88ee-162">Per il codice C# di esempio completo, vedere l' [esempio GetProcessSample04](./getprocesssample04-sample.md).</span><span class="sxs-lookup"><span data-stu-id="d88ee-162">For the complete C# sample code, see [GetProcessSample04 Sample](./getprocesssample04-sample.md).</span></span>

## <a name="define-object-types-and-formatting"></a><span data-ttu-id="d88ee-163">Definire i tipi di oggetto e la formattazione</span><span class="sxs-lookup"><span data-stu-id="d88ee-163">Define Object Types and Formatting</span></span>

<span data-ttu-id="d88ee-164">PowerShell passa informazioni tra i cmdlet usando oggetti .NET.</span><span class="sxs-lookup"><span data-stu-id="d88ee-164">PowerShell passes information between cmdlets using .NET objects.</span></span> <span data-ttu-id="d88ee-165">Di conseguenza, un cmdlet potrebbe dover definire il proprio tipo oppure il cmdlet deve estendere un tipo esistente fornito da un altro cmdlet.</span><span class="sxs-lookup"><span data-stu-id="d88ee-165">Consequently, a cmdlet might need to define its own type, or the cmdlet might need to extend an existing type provided by another cmdlet.</span></span> <span data-ttu-id="d88ee-166">Per ulteriori informazioni sulla definizione di nuovi tipi o sull'estensione di tipi esistenti, vedere [estensione di tipi di oggetti e formattazione](/previous-versions/ms714665(v=vs.85)).</span><span class="sxs-lookup"><span data-stu-id="d88ee-166">For more information about defining new types or extending existing types, see [Extending Object Types and Formatting](/previous-versions/ms714665(v=vs.85)).</span></span>

## <a name="building-the-cmdlet"></a><span data-ttu-id="d88ee-167">Compilazione del cmdlet</span><span class="sxs-lookup"><span data-stu-id="d88ee-167">Building the Cmdlet</span></span>

<span data-ttu-id="d88ee-168">Dopo l'implementazione di un cmdlet, è necessario registrarlo con Windows PowerShell tramite uno snap-in di Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="d88ee-168">After implementing a cmdlet, you must register it with Windows PowerShell through a Windows PowerShell snap-in.</span></span> <span data-ttu-id="d88ee-169">Per ulteriori informazioni sulla registrazione dei cmdlet, vedere [come registrare i cmdlet, i provider e le applicazioni host](/previous-versions//ms714644(v=vs.85)).</span><span class="sxs-lookup"><span data-stu-id="d88ee-169">For more information about registering cmdlets, see [How to Register Cmdlets, Providers, and Host Applications](/previous-versions//ms714644(v=vs.85)).</span></span>

## <a name="testing-the-cmdlet"></a><span data-ttu-id="d88ee-170">Test del cmdlet</span><span class="sxs-lookup"><span data-stu-id="d88ee-170">Testing the Cmdlet</span></span>

<span data-ttu-id="d88ee-171">Quando il cmdlet è stato registrato con PowerShell, è possibile testarlo eseguendolo nella riga di comando.</span><span class="sxs-lookup"><span data-stu-id="d88ee-171">When your cmdlet has been registered with PowerShell, you can test it by running it on the command line.</span></span> <span data-ttu-id="d88ee-172">Testiamo il cmdlet Get-proc di esempio per verificare se viene segnalato un errore:</span><span class="sxs-lookup"><span data-stu-id="d88ee-172">Let's test the sample Get-Proc cmdlet to see whether it reports an error:</span></span>

- <span data-ttu-id="d88ee-173">Avviare PowerShell e usare il cmdlet Get-proc per recuperare i processi denominati "TEST".</span><span class="sxs-lookup"><span data-stu-id="d88ee-173">Start PowerShell, and use the Get-Proc cmdlet to retrieve the processes named "TEST".</span></span>

  ```powershell
  get-proc -name test
  ```

  <span data-ttu-id="d88ee-174">Viene visualizzato l'output seguente.</span><span class="sxs-lookup"><span data-stu-id="d88ee-174">The following output appears.</span></span>

  ```
  get-proc : Operation is not valid due to the current state of the object.
  At line:1 char:9
  + get-proc  <<<< -name test
  ```

## <a name="see-also"></a><span data-ttu-id="d88ee-175">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="d88ee-175">See Also</span></span>

[<span data-ttu-id="d88ee-176">Aggiunta di parametri che elaborano l'input della pipeline</span><span class="sxs-lookup"><span data-stu-id="d88ee-176">Adding Parameters that Process Pipeline Input</span></span>](./adding-parameters-that-process-pipeline-input.md)

[<span data-ttu-id="d88ee-177">Aggiunta di parametri che elaborano l'input della riga di comando</span><span class="sxs-lookup"><span data-stu-id="d88ee-177">Adding Parameters that Process Command-Line Input</span></span>](./adding-parameters-that-process-command-line-input.md)

[<span data-ttu-id="d88ee-178">Creazione del primo cmdlet</span><span class="sxs-lookup"><span data-stu-id="d88ee-178">Creating Your First Cmdlet</span></span>](./creating-a-cmdlet-without-parameters.md)

<span data-ttu-id="d88ee-179">[Estensione di tipi di oggetti e formattazione](/previous-versions/ms714665(v=vs.85))</span><span class="sxs-lookup"><span data-stu-id="d88ee-179">[Extending Object Types and Formatting](/previous-versions/ms714665(v=vs.85))</span></span>

<span data-ttu-id="d88ee-180">[Come registrare cmdlet, provider e applicazioni host](/previous-versions/ms714644(v=vs.85))</span><span class="sxs-lookup"><span data-stu-id="d88ee-180">[How to Register Cmdlets, Providers, and Host Applications](/previous-versions/ms714644(v=vs.85))</span></span>

[<span data-ttu-id="d88ee-181">Riferimenti Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="d88ee-181">Windows PowerShell Reference</span></span>](../windows-powershell-reference.md)

[<span data-ttu-id="d88ee-182">Esempi di cmdlet</span><span class="sxs-lookup"><span data-stu-id="d88ee-182">Cmdlet Samples</span></span>](./cmdlet-samples.md)

[System. Exception]: /dotnet/api/System.Exception
[System.Exception]: /dotnet/api/System.Exception
[System. Management. Automation. Preferenzaazione]: /dotnet/api/System.Management.Automation.ActionPreference
[System.Management.Automation.ActionPreference]: /dotnet/api/System.Management.Automation.ActionPreference
[System. Management. Automation. cmdlet. ProcessRecord]: /dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord
[System.Management.Automation.Cmdlet.ProcessRecord]: /dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord
[System. Management. Automation. cmdlet. WriteError]: /dotnet/api/System.Management.Automation.Cmdlet.WriteError
[System.Management.Automation.Cmdlet.WriteError]: /dotnet/api/System.Management.Automation.Cmdlet.WriteError
[System. Management. Automation. cmdlet]: /dotnet/api/System.Management.Automation.Cmdlet
[System.Management.Automation.Cmdlet]: /dotnet/api/System.Management.Automation.Cmdlet
[System. Management. Automation. ErrorCategory]: /dotnet/api/System.Management.Automation.ErrorCategory
[System.Management.Automation.ErrorCategory]: /dotnet/api/System.Management.Automation.ErrorCategory
[System. Management. Automation. ErrorRecord]: /dotnet/api/System.Management.Automation.ErrorRecord
[System.Management.Automation.ErrorRecord]: /dotnet/api/System.Management.Automation.ErrorRecord
