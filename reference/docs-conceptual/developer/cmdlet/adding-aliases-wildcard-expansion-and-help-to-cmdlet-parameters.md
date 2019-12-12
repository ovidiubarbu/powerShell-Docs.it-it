---
title: Aggiunta di alias, espansione con caratteri jolly e guida ai parametri dei cmdlet | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 931ccace-c565-4a98-8dcc-df00f86394b1
caps.latest.revision: 8
ms.openlocfilehash: d210a852a90d94df2ab360dd86f0b83a396330e3
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/05/2019
ms.locfileid: "74415650"
---
# <a name="adding-aliases-wildcard-expansion-and-help-to-cmdlet-parameters"></a><span data-ttu-id="29c35-102">Aggiunta di alias, espansione di caratteri jolly e guida per i parametri del cmdlet</span><span class="sxs-lookup"><span data-stu-id="29c35-102">Adding Aliases, Wildcard Expansion, and Help to Cmdlet Parameters</span></span>

<span data-ttu-id="29c35-103">In questa sezione viene descritto come aggiungere alias, espansione con caratteri jolly e messaggi della Guida ai parametri del cmdlet Stop-proc (descritto in [creazione di un cmdlet che modifica il sistema](./creating-a-cmdlet-that-modifies-the-system.md)).</span><span class="sxs-lookup"><span data-stu-id="29c35-103">This section describes how to add aliases, wildcard expansion, and Help messages to the parameters of the Stop-Proc cmdlet (described in [Creating a Cmdlet that Modifies the System](./creating-a-cmdlet-that-modifies-the-system.md)).</span></span>

<span data-ttu-id="29c35-104">Questo cmdlet Stop-proc tenta di arrestare i processi recuperati tramite il cmdlet Get-proc, descritto in [creazione del primo cmdlet](./creating-a-cmdlet-without-parameters.md).</span><span class="sxs-lookup"><span data-stu-id="29c35-104">This Stop-Proc cmdlet attempts to stop processes that are retrieved using the Get-Proc cmdlet (described in [Creating Your First Cmdlet](./creating-a-cmdlet-without-parameters.md)).</span></span>

## <a name="defining-the-cmdlet"></a><span data-ttu-id="29c35-105">Definizione del cmdlet</span><span class="sxs-lookup"><span data-stu-id="29c35-105">Defining the Cmdlet</span></span>

<span data-ttu-id="29c35-106">Il primo passaggio nella creazione di cmdlet è sempre il nome del cmdlet e la dichiarazione della classe .NET che implementa il cmdlet.</span><span class="sxs-lookup"><span data-stu-id="29c35-106">The first step in cmdlet creation is always naming the cmdlet and declaring the .NET class that implements the cmdlet.</span></span> <span data-ttu-id="29c35-107">Poiché si sta scrivendo un cmdlet per modificare il sistema, è necessario denominarlo di conseguenza.</span><span class="sxs-lookup"><span data-stu-id="29c35-107">Because you are writing a cmdlet to change the system, it should be named accordingly.</span></span> <span data-ttu-id="29c35-108">Poiché questo cmdlet interrompe i processi di sistema, usa il verbo "Stop", definito dalla classe [System. Management. Automation. Verbslifecycle](/dotnet/api/System.Management.Automation.VerbsLifeCycle) , con il sostantivo "proc" per indicare il processo.</span><span class="sxs-lookup"><span data-stu-id="29c35-108">Because this cmdlet stops system processes, it uses the verb "Stop", defined by the [System.Management.Automation.Verbslifecycle](/dotnet/api/System.Management.Automation.VerbsLifeCycle) class, with the noun "Proc" to indicate process.</span></span> <span data-ttu-id="29c35-109">Per altre informazioni sui verbi di cmdlet approvati, vedere [nomi dei verbi di cmdlet](./approved-verbs-for-windows-powershell-commands.md).</span><span class="sxs-lookup"><span data-stu-id="29c35-109">For more information about approved cmdlet verbs, see [Cmdlet Verb Names](./approved-verbs-for-windows-powershell-commands.md).</span></span>

<span data-ttu-id="29c35-110">Il codice seguente è la definizione di classe per questo cmdlet Stop-proc.</span><span class="sxs-lookup"><span data-stu-id="29c35-110">The following code is the class definition for this Stop-Proc cmdlet.</span></span>

```csharp
[Cmdlet(VerbsLifecycle.Stop, "proc",
        SupportsShouldProcess = true)]
public class StopProcCommand : Cmdlet
```

## <a name="defining-parameters-for-system-modification"></a><span data-ttu-id="29c35-111">Definizione dei parametri per la modifica del sistema</span><span class="sxs-lookup"><span data-stu-id="29c35-111">Defining Parameters for System Modification</span></span>

<span data-ttu-id="29c35-112">Il cmdlet deve definire i parametri che supportano le modifiche del sistema e il feedback dell'utente.</span><span class="sxs-lookup"><span data-stu-id="29c35-112">Your cmdlet needs to define parameters that support system modifications and user feedback.</span></span> <span data-ttu-id="29c35-113">Il cmdlet deve definire un parametro di `Name` o un valore equivalente, in modo che il cmdlet possa modificare il sistema con un tipo di identificatore.</span><span class="sxs-lookup"><span data-stu-id="29c35-113">The cmdlet should define a `Name` parameter or equivalent so that the cmdlet will be able to modify the system by some sort of identifier.</span></span> <span data-ttu-id="29c35-114">Inoltre, il cmdlet deve definire i parametri `Force` e `PassThru`.</span><span class="sxs-lookup"><span data-stu-id="29c35-114">In addition, the cmdlet should define the `Force` and `PassThru` parameters.</span></span> <span data-ttu-id="29c35-115">Per ulteriori informazioni su questi parametri, vedere [creazione di un cmdlet che modifichi il sistema](./creating-a-cmdlet-that-modifies-the-system.md).</span><span class="sxs-lookup"><span data-stu-id="29c35-115">For more information about these parameters, see [Creating a Cmdlet that Modifies the System](./creating-a-cmdlet-that-modifies-the-system.md).</span></span>

## <a name="defining-a-parameter-alias"></a><span data-ttu-id="29c35-116">Definizione di un alias di parametro</span><span class="sxs-lookup"><span data-stu-id="29c35-116">Defining a Parameter Alias</span></span>

<span data-ttu-id="29c35-117">Un alias di parametro può essere un nome alternativo o un nome breve con una lettera o un nome breve di due lettere per un parametro del cmdlet.</span><span class="sxs-lookup"><span data-stu-id="29c35-117">A parameter alias can be an alternate name or a well-defined 1-letter or 2-letter short name for a cmdlet parameter.</span></span> <span data-ttu-id="29c35-118">In entrambi i casi, l'obiettivo dell'utilizzo degli alias consiste nel semplificare la voce utente dalla riga di comando.</span><span class="sxs-lookup"><span data-stu-id="29c35-118">In both cases, the goal of using aliases is to simplify user entry from the command line.</span></span> <span data-ttu-id="29c35-119">Windows PowerShell supporta gli alias di parametro tramite l'attributo [System. Management. Automation. AliasAttribute](/dotnet/api/System.Management.Automation.AliasAttribute) , che usa la sintassi di dichiarazione [alias ()].</span><span class="sxs-lookup"><span data-stu-id="29c35-119">Windows PowerShell supports parameter aliases through the [System.Management.Automation.Aliasattribute](/dotnet/api/System.Management.Automation.AliasAttribute) attribute, which uses the declaration syntax [Alias()].</span></span>

<span data-ttu-id="29c35-120">Nel codice seguente viene illustrato come aggiungere un alias al parametro `Name`.</span><span class="sxs-lookup"><span data-stu-id="29c35-120">The following code shows how an alias is added to the `Name` parameter.</span></span>

```csharp
/// <summary>
/// Specify the mandatory Name parameter used to identify the
/// processes to be stopped.
/// </summary>
[Parameter(
           Position = 0,
           Mandatory = true,
           ValueFromPipeline = true,
           ValueFromPipelineByPropertyName = true,
           HelpMessage = "The name of one or more processes to stop. Wildcards are permitted."
)]
[Alias("ProcessName")]
public string[] Name
{
  get { return processNames; }
  set { processNames = value; }
}
private string[] processNames;
```

<span data-ttu-id="29c35-121">Oltre a usare l'attributo [System. Management. Automation. AliasAttribute](/dotnet/api/System.Management.Automation.AliasAttribute) , il runtime di Windows PowerShell esegue la corrispondenza parziale dei nomi, anche se non è specificato alcun alias.</span><span class="sxs-lookup"><span data-stu-id="29c35-121">In addition to using the [System.Management.Automation.Aliasattribute](/dotnet/api/System.Management.Automation.AliasAttribute) attribute, the Windows PowerShell runtime performs partial name matching, even if no aliases are specified.</span></span> <span data-ttu-id="29c35-122">Se, ad esempio, il cmdlet dispone di un parametro `FileName` ed è l'unico parametro che inizia con `F`, l'utente può immettere `Filename`, `Filenam`, `File`, `Fi`o `F` e riconoscerne la voce come parametro di `FileName`.</span><span class="sxs-lookup"><span data-stu-id="29c35-122">For example, if your cmdlet has a `FileName` parameter and that is the only parameter that starts with `F`, the user could enter `Filename`, `Filenam`, `File`, `Fi`, or `F` and still recognize the entry as the `FileName` parameter.</span></span>

## <a name="creating-help-for-parameters"></a><span data-ttu-id="29c35-123">Creazione della Guida per i parametri</span><span class="sxs-lookup"><span data-stu-id="29c35-123">Creating Help for Parameters</span></span>

<span data-ttu-id="29c35-124">Windows PowerShell consente di creare una guida per i parametri dei cmdlet.</span><span class="sxs-lookup"><span data-stu-id="29c35-124">Windows PowerShell allows you to create Help for cmdlet parameters.</span></span> <span data-ttu-id="29c35-125">Eseguire questa operazione per qualsiasi parametro usato per la modifica del sistema e il feedback dell'utente.</span><span class="sxs-lookup"><span data-stu-id="29c35-125">Do this for any parameter used for system modification and user feedback.</span></span> <span data-ttu-id="29c35-126">Per ogni parametro per supportare la guida, è possibile impostare la parola chiave `HelpMessage` attribute nella dichiarazione di attributo [System. Management. Automation. ParameterAttribute](/dotnet/api/System.Management.Automation.ParameterAttribute) .</span><span class="sxs-lookup"><span data-stu-id="29c35-126">For each parameter to support Help, you can set the `HelpMessage` attribute keyword in the [System.Management.Automation.Parameterattribute](/dotnet/api/System.Management.Automation.ParameterAttribute) attribute declaration.</span></span> <span data-ttu-id="29c35-127">Questa parola chiave definisce il testo da visualizzare all'utente per ottenere assistenza nell'uso del parametro.</span><span class="sxs-lookup"><span data-stu-id="29c35-127">This keyword defines the text to display to the user for assistance in using the parameter.</span></span> <span data-ttu-id="29c35-128">È inoltre possibile impostare la parola chiave `HelpMessageBaseName` per identificare il nome di base di una risorsa da utilizzare per il messaggio.</span><span class="sxs-lookup"><span data-stu-id="29c35-128">You can also set the `HelpMessageBaseName` keyword to identify the base name of a resource to use for the message.</span></span> <span data-ttu-id="29c35-129">Se si imposta questa parola chiave, è necessario impostare anche la parola chiave `HelpMessageResourceId` per specificare l'identificatore della risorsa.</span><span class="sxs-lookup"><span data-stu-id="29c35-129">If you set this keyword, you must also set the `HelpMessageResourceId` keyword to specify the resource identifier.</span></span>

<span data-ttu-id="29c35-130">Il codice seguente di questo cmdlet Stop-proc definisce la parola chiave dell'attributo `HelpMessage` per il parametro `Name`.</span><span class="sxs-lookup"><span data-stu-id="29c35-130">The following code from this Stop-Proc cmdlet defines the `HelpMessage` attribute keyword for the `Name` parameter.</span></span>

```csharp
/// <summary>
/// Specify the mandatory Name parameter used to identify the
/// processes to be stopped.
/// </summary>
[Parameter(
           Position = 0,
           Mandatory = true,
           ValueFromPipeline = true,
           ValueFromPipelineByPropertyName = true,
           HelpMessage = "The name of one or more processes to stop. Wildcards are permitted."
)]
```

## <a name="overriding-an-input-processing-method"></a><span data-ttu-id="29c35-131">Override di un metodo di elaborazione dell'input</span><span class="sxs-lookup"><span data-stu-id="29c35-131">Overriding an Input Processing Method</span></span>

<span data-ttu-id="29c35-132">Il cmdlet deve eseguire l'override di un metodo di elaborazione dell'input, più spesso sarà [System. Management. Automation. cmdlet. ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord).</span><span class="sxs-lookup"><span data-stu-id="29c35-132">Your cmdlet must override an input processing method, most often this will be [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord).</span></span> <span data-ttu-id="29c35-133">Quando si modifica il sistema, il cmdlet deve chiamare i metodi [System. Management. Automation. cmdlet. ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) e [System. Management. Automation. cmdlet. ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) per consentire all'utente di fornire feedback prima che venga apportata una modifica.</span><span class="sxs-lookup"><span data-stu-id="29c35-133">When modifying the system, the cmdlet should call the [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) and [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) methods to allow the user to provide feedback before a change is made.</span></span> <span data-ttu-id="29c35-134">Per ulteriori informazioni su questi metodi, vedere [creazione di un cmdlet che modifichi il sistema](./creating-a-cmdlet-that-modifies-the-system.md).</span><span class="sxs-lookup"><span data-stu-id="29c35-134">For more information about these methods, see [Creating a Cmdlet that Modifies the System](./creating-a-cmdlet-that-modifies-the-system.md).</span></span>

## <a name="supporting-wildcard-expansion"></a><span data-ttu-id="29c35-135">Supporto dell'espansione con caratteri jolly</span><span class="sxs-lookup"><span data-stu-id="29c35-135">Supporting Wildcard Expansion</span></span>

<span data-ttu-id="29c35-136">Per consentire la selezione di più oggetti, il cmdlet può usare le classi [System. Management. Automation. Wildcardpattern](/dotnet/api/System.Management.Automation.WildcardPattern) e [System. Management. Automation. Wildcardoptions](/dotnet/api/System.Management.Automation.WildcardOptions) per fornire supporto per l'espansione dei caratteri jolly per l'input dei parametri.</span><span class="sxs-lookup"><span data-stu-id="29c35-136">To allow the selection of multiple objects, your cmdlet can use the [System.Management.Automation.Wildcardpattern](/dotnet/api/System.Management.Automation.WildcardPattern) and [System.Management.Automation.Wildcardoptions](/dotnet/api/System.Management.Automation.WildcardOptions) classes to provide wildcard expansion support for parameter input.</span></span> <span data-ttu-id="29c35-137">Esempi di modelli con caratteri jolly sono LSA \*, \*. txt e [a-c]\*.</span><span class="sxs-lookup"><span data-stu-id="29c35-137">Examples of wildcard patterns are lsa\*, \*.txt, and [a-c]\*.</span></span> <span data-ttu-id="29c35-138">Usare il carattere virgoletta indietro (') come carattere di escape quando il pattern contiene un carattere che deve essere usato letteralmente.</span><span class="sxs-lookup"><span data-stu-id="29c35-138">Use the back-quote character (\`) as an escape character when the pattern contains a character that should be used literally.</span></span>

<span data-ttu-id="29c35-139">Le espansioni con caratteri jolly di nomi di file e percorsi sono esempi di scenari comuni in cui il cmdlet può volere supportare gli input di percorso quando è richiesta la selezione di più oggetti.</span><span class="sxs-lookup"><span data-stu-id="29c35-139">Wildcard expansions of file and path names are examples of common scenarios where the cmdlet may want to allow support for path inputs when the selection of multiple objects is required.</span></span> <span data-ttu-id="29c35-140">Un caso comune è nel file system, in cui un utente desidera visualizzare tutti i file che risiedono nella cartella corrente.</span><span class="sxs-lookup"><span data-stu-id="29c35-140">A common case is in the file system, where a user wants to see all files residing in the current folder.</span></span>

<span data-ttu-id="29c35-141">Dovrebbe essere necessaria un'implementazione di criteri di ricerca con caratteri jolly personalizzata solo raramente.</span><span class="sxs-lookup"><span data-stu-id="29c35-141">You should need a customized wildcard pattern matching implementation only rarely.</span></span> <span data-ttu-id="29c35-142">In questo caso, il cmdlet deve supportare la specifica POSIX 1003,2, 3,13 completa per l'espansione con caratteri jolly o il subset semplificato seguente:</span><span class="sxs-lookup"><span data-stu-id="29c35-142">In this case, your cmdlet should support either the full POSIX 1003.2, 3.13 specification for wildcard expansion or the following simplified subset:</span></span>

- <span data-ttu-id="29c35-143">**Punto interrogativo (?).**</span><span class="sxs-lookup"><span data-stu-id="29c35-143">**Question mark (?).**</span></span> <span data-ttu-id="29c35-144">Corrisponde a qualsiasi carattere nella posizione specificata.</span><span class="sxs-lookup"><span data-stu-id="29c35-144">Matches any character at the specified location.</span></span>

- <span data-ttu-id="29c35-145">**Asterisco (\*).**</span><span class="sxs-lookup"><span data-stu-id="29c35-145">**Asterisk (\*).**</span></span> <span data-ttu-id="29c35-146">Trova la corrispondenza di zero o più caratteri a partire dalla posizione specificata.</span><span class="sxs-lookup"><span data-stu-id="29c35-146">Matches zero or more characters starting at the specified location.</span></span>

- <span data-ttu-id="29c35-147">**Parentesi aperta ([).**</span><span class="sxs-lookup"><span data-stu-id="29c35-147">**Open bracket ([).**</span></span> <span data-ttu-id="29c35-148">Introduce un'espressione tra parentesi quadre che può contenere caratteri o un intervallo di caratteri.</span><span class="sxs-lookup"><span data-stu-id="29c35-148">Introduces a pattern bracket expression that can contain characters or a range of characters.</span></span> <span data-ttu-id="29c35-149">Se è necessario un intervallo, viene usato un segno meno (-) per indicare l'intervallo.</span><span class="sxs-lookup"><span data-stu-id="29c35-149">If a range is required, a hyphen (-) is used to indicate the range.</span></span>

- <span data-ttu-id="29c35-150">**Parentesi chiusa (]).**</span><span class="sxs-lookup"><span data-stu-id="29c35-150">**Close bracket (]).**</span></span> <span data-ttu-id="29c35-151">Termina un'espressione di parentesi quadre.</span><span class="sxs-lookup"><span data-stu-id="29c35-151">Ends a pattern bracket expression.</span></span>

- <span data-ttu-id="29c35-152">**Carattere di escape tra virgolette (').**</span><span class="sxs-lookup"><span data-stu-id="29c35-152">**Back-quote escape character (\`).**</span></span> <span data-ttu-id="29c35-153">Indica che il carattere successivo deve essere effettivamente utilizzato.</span><span class="sxs-lookup"><span data-stu-id="29c35-153">Indicates that the next character should be taken literally.</span></span> <span data-ttu-id="29c35-154">Tenere presente che quando si specifica il carattere di virgolette indietro dalla riga di comando, anziché specificarlo a livello di codice, il carattere di escape per virgolette doppie deve essere specificato due volte.</span><span class="sxs-lookup"><span data-stu-id="29c35-154">Be aware that when specifying the back-quote character from the command line (as opposed to specifying it programmatically), the back-quote escape character must be specified twice.</span></span>

> [!NOTE]
> <span data-ttu-id="29c35-155">Per ulteriori informazioni sui modelli con caratteri jolly, vedere [supporto dei caratteri jolly nei parametri del cmdlet](./supporting-wildcard-characters-in-cmdlet-parameters.md).</span><span class="sxs-lookup"><span data-stu-id="29c35-155">For more information about wildcard patterns, see [Supporting Wildcards in Cmdlet Parameters](./supporting-wildcard-characters-in-cmdlet-parameters.md).</span></span>

<span data-ttu-id="29c35-156">Nel codice seguente viene illustrato come impostare le opzioni con caratteri jolly e come definire il modello con caratteri jolly utilizzato per la risoluzione del parametro `Name` per questo cmdlet.</span><span class="sxs-lookup"><span data-stu-id="29c35-156">The following code shows how to set wildcard options and define the wildcard pattern used for resolving the `Name` parameter for this cmdlet.</span></span>

```csharp
WildcardOptions options = WildcardOptions.IgnoreCase |
                          WildcardOptions.Compiled;
WildcardPattern wildcard = new WildcardPattern(name,options);
```

<span data-ttu-id="29c35-157">Il codice seguente illustra come verificare se il nome del processo corrisponde al modello con caratteri jolly definito.</span><span class="sxs-lookup"><span data-stu-id="29c35-157">The following code shows how to test whether the process name matches the defined wildcard pattern.</span></span> <span data-ttu-id="29c35-158">Si noti che, in questo caso, se il nome del processo non corrisponde al modello, il cmdlet continua in per ottenere il nome del processo successivo.</span><span class="sxs-lookup"><span data-stu-id="29c35-158">Notice that, in this case, if the process name does not match the pattern, the cmdlet continues on to get the next process name.</span></span>

```csharp
if (!wildcard.IsMatch(processName))
{
  continue;
}
```

## <a name="code-sample"></a><span data-ttu-id="29c35-159">Codice di esempio</span><span class="sxs-lookup"><span data-stu-id="29c35-159">Code Sample</span></span>

<span data-ttu-id="29c35-160">Per il codice C# di esempio completo, vedere l' [esempio StopProcessSample03](./stopprocesssample03-sample.md).</span><span class="sxs-lookup"><span data-stu-id="29c35-160">For the complete C# sample code, see [StopProcessSample03 Sample](./stopprocesssample03-sample.md).</span></span>

## <a name="define-object-types-and-formatting"></a><span data-ttu-id="29c35-161">Definire i tipi di oggetto e la formattazione</span><span class="sxs-lookup"><span data-stu-id="29c35-161">Define Object Types and Formatting</span></span>

<span data-ttu-id="29c35-162">Windows PowerShell passa le informazioni tra i cmdlet usando gli oggetti .NET.</span><span class="sxs-lookup"><span data-stu-id="29c35-162">Windows PowerShell passes information between cmdlets using .Net objects.</span></span> <span data-ttu-id="29c35-163">Di conseguenza, un cmdlet può avere la necessità di definire un proprio tipo oppure il cmdlet deve estendere un tipo esistente fornito da un altro cmdlet.</span><span class="sxs-lookup"><span data-stu-id="29c35-163">Consequently, a cmdlet may need to define its own type, or the cmdlet may need to extend an existing type provided by another cmdlet.</span></span> <span data-ttu-id="29c35-164">Per ulteriori informazioni sulla definizione di nuovi tipi o sull'estensione di tipi esistenti, vedere [estensione di tipi di oggetti e formattazione](/previous-versions//ms714665(v=vs.85)).</span><span class="sxs-lookup"><span data-stu-id="29c35-164">For more information about defining new types or extending existing types, see [Extending Object Types and Formatting](/previous-versions//ms714665(v=vs.85)).</span></span>

## <a name="building-the-cmdlet"></a><span data-ttu-id="29c35-165">Compilazione del cmdlet</span><span class="sxs-lookup"><span data-stu-id="29c35-165">Building the Cmdlet</span></span>

<span data-ttu-id="29c35-166">Dopo l'implementazione di un cmdlet, è necessario registrarlo con Windows PowerShell tramite uno snap-in di Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="29c35-166">After implementing a cmdlet, it must be registered with Windows PowerShell through a Windows PowerShell snap-in.</span></span> <span data-ttu-id="29c35-167">Per ulteriori informazioni sulla registrazione dei cmdlet, vedere [come registrare i cmdlet, i provider e le applicazioni host](/previous-versions//ms714644(v=vs.85)).</span><span class="sxs-lookup"><span data-stu-id="29c35-167">For more information about registering cmdlets, see [How to Register Cmdlets, Providers, and Host Applications](/previous-versions//ms714644(v=vs.85)).</span></span>

## <a name="testing-the-cmdlet"></a><span data-ttu-id="29c35-168">Test del cmdlet</span><span class="sxs-lookup"><span data-stu-id="29c35-168">Testing the Cmdlet</span></span>

<span data-ttu-id="29c35-169">Quando il cmdlet è stato registrato con Windows PowerShell, è possibile testarlo eseguendolo nella riga di comando.</span><span class="sxs-lookup"><span data-stu-id="29c35-169">When your cmdlet has been registered with Windows PowerShell, you can test it by running it on the command line.</span></span> <span data-ttu-id="29c35-170">Testare il cmdlet di esempio Stop-proc.</span><span class="sxs-lookup"><span data-stu-id="29c35-170">Let's test the sample Stop-Proc cmdlet.</span></span> <span data-ttu-id="29c35-171">Per ulteriori informazioni sull'utilizzo dei cmdlet dalla riga di comando, vedere la [Introduzione con Windows PowerShell](/powershell/scripting/getting-started/getting-started-with-windows-powershell).</span><span class="sxs-lookup"><span data-stu-id="29c35-171">For more information about using cmdlets from the command line, see the [Getting Started with Windows PowerShell](/powershell/scripting/getting-started/getting-started-with-windows-powershell).</span></span>

- <span data-ttu-id="29c35-172">Avviare Windows PowerShell e usare stop-proc per arrestare un processo usando l'alias ProcessName per il parametro `Name`.</span><span class="sxs-lookup"><span data-stu-id="29c35-172">Start Windows PowerShell and use Stop-Proc to stop a process using the ProcessName alias for the `Name` parameter.</span></span>

    ```powershell
    PS> stop-proc -ProcessName notepad
    ```

<span data-ttu-id="29c35-173">Viene visualizzato l'output seguente:</span><span class="sxs-lookup"><span data-stu-id="29c35-173">The following output appears.</span></span>

    ```
    Confirm
    Are you sure you want to perform this action?
    Performing operation "stop-proc" on Target "notepad (3496)".
    [Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"): Y
    ```

- <span data-ttu-id="29c35-174">Eseguire la voce seguente nella riga di comando.</span><span class="sxs-lookup"><span data-stu-id="29c35-174">Make the following entry on the command line.</span></span> <span data-ttu-id="29c35-175">Poiché il parametro Name è obbligatorio, viene richiesto.</span><span class="sxs-lookup"><span data-stu-id="29c35-175">Because the Name parameter is mandatory, you are prompted for it.</span></span> <span data-ttu-id="29c35-176">Immissione di "!?"</span><span class="sxs-lookup"><span data-stu-id="29c35-176">Entering "!?"</span></span> <span data-ttu-id="29c35-177">Visualizza il testo della Guida associato al parametro.</span><span class="sxs-lookup"><span data-stu-id="29c35-177">brings up the help text associated with the parameter.</span></span>

    ```powershell
    PS> stop-proc
    ```

<span data-ttu-id="29c35-178">Viene visualizzato l'output seguente:</span><span class="sxs-lookup"><span data-stu-id="29c35-178">The following output appears.</span></span>

    ```
    Cmdlet stop-proc at command pipeline position 1
    Supply values for the following parameters:
    (Type !? for Help.)
    Name[0]: !?
    The name of one or more processes to stop. Wildcards are permitted.
    Name[0]: notepad
    ```

- <span data-ttu-id="29c35-179">A questo punto, effettuare la seguente voce per arrestare tutti i processi che corrispondono al modello con caratteri jolly "\* Nota\*".</span><span class="sxs-lookup"><span data-stu-id="29c35-179">Now make the following entry to stop all processes that match the wildcard pattern "\*note\*".</span></span> <span data-ttu-id="29c35-180">Viene richiesto prima di arrestare ogni processo che corrisponde al modello.</span><span class="sxs-lookup"><span data-stu-id="29c35-180">You are prompted before stopping each process that matches the pattern.</span></span>

    ```powershell
    PS> stop-proc -Name *note*
    ```

<span data-ttu-id="29c35-181">Viene visualizzato l'output seguente:</span><span class="sxs-lookup"><span data-stu-id="29c35-181">The following output appears.</span></span>

    ```
    Confirm
    Are you sure you want to perform this action?
    Performing operation "stop-proc" on Target "notepad (1112)".
    [Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"): Y
    ```

<span data-ttu-id="29c35-182">Viene visualizzato l'output seguente:</span><span class="sxs-lookup"><span data-stu-id="29c35-182">The following output appears.</span></span>

    ```
    Confirm
    Are you sure you want to perform this action?
    Performing operation "stop-proc" on Target "ONENOTEM (3712)".
    [Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"): N
    ```

<span data-ttu-id="29c35-183">Viene visualizzato l'output seguente:</span><span class="sxs-lookup"><span data-stu-id="29c35-183">The following output appears.</span></span>

    ```
    Confirm
    Are you sure you want to perform this action?
    Performing operation "stop-proc" on Target "ONENOTE (3592)".
    [Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"): N
    ```

## <a name="see-also"></a><span data-ttu-id="29c35-184">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="29c35-184">See Also</span></span>

[<span data-ttu-id="29c35-185">Creare un cmdlet che modifichi il sistema</span><span class="sxs-lookup"><span data-stu-id="29c35-185">Create a Cmdlet that Modifies the System</span></span>](./creating-a-cmdlet-that-modifies-the-system.md)

[<span data-ttu-id="29c35-186">Come creare un cmdlet di Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="29c35-186">How to Create a Windows PowerShell Cmdlet</span></span>](/powershell/scripting/developer/cmdlet/writing-a-windows-powershell-cmdlet)

<span data-ttu-id="29c35-187">[Estensione di tipi di oggetti e formattazione](/previous-versions//ms714665(v=vs.85))</span><span class="sxs-lookup"><span data-stu-id="29c35-187">[Extending Object Types and Formatting](/previous-versions//ms714665(v=vs.85))</span></span>

<span data-ttu-id="29c35-188">[Come registrare cmdlet, provider e applicazioni host](/previous-versions//ms714644(v=vs.85))</span><span class="sxs-lookup"><span data-stu-id="29c35-188">[How to Register Cmdlets, Providers, and Host Applications](/previous-versions//ms714644(v=vs.85))</span></span>

[<span data-ttu-id="29c35-189">Supporto dei caratteri jolly nei parametri dei cmdlet</span><span class="sxs-lookup"><span data-stu-id="29c35-189">Supporting Wildcards in Cmdlet Parameters</span></span>](./supporting-wildcard-characters-in-cmdlet-parameters.md)

[<span data-ttu-id="29c35-190">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="29c35-190">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)
