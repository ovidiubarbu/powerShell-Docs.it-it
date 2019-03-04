---
title: Aggiunta di alias di espansione di caratteri jolly e consentono di parametri del Cmdlet | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 931ccace-c565-4a98-8dcc-df00f86394b1
caps.latest.revision: 8
ms.openlocfilehash: 0f025213087e6f308adf8e597fc01c1320251f76
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/03/2019
ms.locfileid: "56859327"
---
# <a name="adding-aliases-wildcard-expansion-and-help-to-cmdlet-parameters"></a><span data-ttu-id="476ab-102">Aggiunta di alias, espansione di caratteri jolly e guida per i parametri del cmdlet</span><span class="sxs-lookup"><span data-stu-id="476ab-102">Adding Aliases, Wildcard Expansion, and Help to Cmdlet Parameters</span></span>

<span data-ttu-id="476ab-103">In questa sezione viene descritto come aggiungere gli alias, espansione di caratteri jolly, e i messaggi della Guida per i parametri del cmdlet Stop-Process (descritto nella [creazione di un Cmdlet che modifichi il sistema](./creating-a-cmdlet-that-modifies-the-system.md)).</span><span class="sxs-lookup"><span data-stu-id="476ab-103">This section describes how to add aliases, wildcard expansion, and Help messages to the parameters of the Stop-Proc cmdlet (described in [Creating a Cmdlet that Modifies the System](./creating-a-cmdlet-that-modifies-the-system.md)).</span></span>

<span data-ttu-id="476ab-104">Questo cmdlet Stop-Process tenta di arrestare i processi che vengono recuperati usando il cmdlet Get-Proc (descritto nella [la creazione del primo Cmdlet](./creating-a-cmdlet-without-parameters.md)).</span><span class="sxs-lookup"><span data-stu-id="476ab-104">This Stop-Proc cmdlet attempts to stop processes that are retrieved using the Get-Proc cmdlet (described in [Creating Your First Cmdlet](./creating-a-cmdlet-without-parameters.md)).</span></span>

<span data-ttu-id="476ab-105">Gli argomenti in questa sezione includono quanto segue:</span><span class="sxs-lookup"><span data-stu-id="476ab-105">Topics in this section include the following:</span></span>

- [<span data-ttu-id="476ab-106">Che definisce il Cmdlet</span><span class="sxs-lookup"><span data-stu-id="476ab-106">Defining the Cmdlet</span></span>](#Defining-the-Cmdlet)

- [<span data-ttu-id="476ab-107">Definizione dei parametri per la modifica di sistema</span><span class="sxs-lookup"><span data-stu-id="476ab-107">Defining Parameters for System Modification</span></span>](#Defining-Parameters-for-System-Modification)

- [<span data-ttu-id="476ab-108">La definizione di un Alias del parametro</span><span class="sxs-lookup"><span data-stu-id="476ab-108">Defining a Parameter Alias</span></span>](#Defining-a-Parameter-Alias)

- [<span data-ttu-id="476ab-109">Creazione di una Guida per i parametri</span><span class="sxs-lookup"><span data-stu-id="476ab-109">Creating Help for Parameters</span></span>](#Creating-Help-for-Parameters)

- [<span data-ttu-id="476ab-110">Si esegue l'override di un metodo di elaborazione dell'Input</span><span class="sxs-lookup"><span data-stu-id="476ab-110">Overriding an Input Processing Method</span></span>](#Overriding-an-Input-Processing-Method)

- [<span data-ttu-id="476ab-111">Supporto di espansione di caratteri jolly</span><span class="sxs-lookup"><span data-stu-id="476ab-111">Supporting Wildcard Expansion</span></span>](#Supporting-Wildcard-Expansion)

- [<span data-ttu-id="476ab-112">Esempio di codice</span><span class="sxs-lookup"><span data-stu-id="476ab-112">Code Sample</span></span>](#Defining-a-Parameter-Alias)

- [<span data-ttu-id="476ab-113">Definizione di tipi di oggetto e formattazione</span><span class="sxs-lookup"><span data-stu-id="476ab-113">Defining Object Types and Formatting</span></span>](#Define-Object-Types-and-Formatting)

- [<span data-ttu-id="476ab-114">Creazione di Cmdlet</span><span class="sxs-lookup"><span data-stu-id="476ab-114">Building the Cmdlet</span></span>](#Building-the-Cmdlet)

- [<span data-ttu-id="476ab-115">Il Cmdlet di test</span><span class="sxs-lookup"><span data-stu-id="476ab-115">Testing the Cmdlet</span></span>](#Testing-the-Cmdlet)

## <a name="defining-the-cmdlet"></a><span data-ttu-id="476ab-116">Che definisce il Cmdlet</span><span class="sxs-lookup"><span data-stu-id="476ab-116">Defining the Cmdlet</span></span>

<span data-ttu-id="476ab-117">Il primo passaggio nella creazione di cmdlet è sempre il cmdlet di denominazione e la dichiarazione di classe .NET che implementa il cmdlet.</span><span class="sxs-lookup"><span data-stu-id="476ab-117">The first step in cmdlet creation is always naming the cmdlet and declaring the .NET class that implements the cmdlet.</span></span> <span data-ttu-id="476ab-118">Poiché si sta scrivendo un cmdlet per modificare il sistema, devono essere denominato di conseguenza.</span><span class="sxs-lookup"><span data-stu-id="476ab-118">Because you are writing a cmdlet to change the system, it should be named accordingly.</span></span> <span data-ttu-id="476ab-119">Poiché questo cmdlet arresta i processi di sistema, utilizza il verbo "Stop", definito dal [System.Management.Automation.Verbslifecycle](/dotnet/api/System.Management.Automation.VerbsLifeCycle) (classe), con il sostantivo "Proc" per indicare di processo.</span><span class="sxs-lookup"><span data-stu-id="476ab-119">Because this cmdlet stops system processes, it uses the verb "Stop", defined by the [System.Management.Automation.Verbslifecycle](/dotnet/api/System.Management.Automation.VerbsLifeCycle) class, with the noun "Proc" to indicate process.</span></span> <span data-ttu-id="476ab-120">Per altre informazioni sui verbi approvati di cmdlet, vedere [nomi dei verbi di Cmdlet](./approved-verbs-for-windows-powershell-commands.md).</span><span class="sxs-lookup"><span data-stu-id="476ab-120">For more information about approved cmdlet verbs, see [Cmdlet Verb Names](./approved-verbs-for-windows-powershell-commands.md).</span></span>

<span data-ttu-id="476ab-121">Il codice seguente è la definizione di classe per questo cmdlet Stop-Process.</span><span class="sxs-lookup"><span data-stu-id="476ab-121">The following code is the class definition for this Stop-Proc cmdlet.</span></span>

```csharp
[Cmdlet(VerbsLifecycle.Stop, "proc",
        SupportsShouldProcess = true)]
public class StopProcCommand : Cmdlet
```

## <a name="defining-parameters-for-system-modification"></a><span data-ttu-id="476ab-122">Definizione dei parametri per la modifica di sistema</span><span class="sxs-lookup"><span data-stu-id="476ab-122">Defining Parameters for System Modification</span></span>

<span data-ttu-id="476ab-123">Il cmdlet deve definire i parametri che le modifiche di sistema di supporto e commenti degli utenti.</span><span class="sxs-lookup"><span data-stu-id="476ab-123">Your cmdlet needs to define parameters that support system modifications and user feedback.</span></span> <span data-ttu-id="476ab-124">Il cmdlet deve definire un `Name` parametro o equivalente in modo che il cmdlet sarà in grado di modificare il sistema da una forma di identificatore.</span><span class="sxs-lookup"><span data-stu-id="476ab-124">The cmdlet should define a `Name` parameter or equivalent so that the cmdlet will be able to modify the system by some sort of identifier.</span></span> <span data-ttu-id="476ab-125">Inoltre, è necessario definire il cmdlet di `Force` e `PassThru` parametri.</span><span class="sxs-lookup"><span data-stu-id="476ab-125">In addition, the cmdlet should define the `Force` and `PassThru` parameters.</span></span> <span data-ttu-id="476ab-126">Per altre informazioni su questi parametri, vedere [creazione di un Cmdlet che modifichi il sistema](./creating-a-cmdlet-that-modifies-the-system.md).</span><span class="sxs-lookup"><span data-stu-id="476ab-126">For more information about these parameters, see [Creating a Cmdlet that Modifies the System](./creating-a-cmdlet-that-modifies-the-system.md).</span></span>

## <a name="defining-a-parameter-alias"></a><span data-ttu-id="476ab-127">La definizione di un Alias del parametro</span><span class="sxs-lookup"><span data-stu-id="476ab-127">Defining a Parameter Alias</span></span>

<span data-ttu-id="476ab-128">Un alias del parametro può essere un nome alternativo o un nome breve di-1 o 2 lettere ben definito per un parametro del cmdlet.</span><span class="sxs-lookup"><span data-stu-id="476ab-128">A parameter alias can be an alternate name or a well-defined 1-letter or 2-letter short name for a cmdlet parameter.</span></span> <span data-ttu-id="476ab-129">In entrambi i casi, l'obiettivo di utilizzo degli alias è per semplificare l'immissione di utente dalla riga di comando.</span><span class="sxs-lookup"><span data-stu-id="476ab-129">In both cases, the goal of using aliases is to simplify user entry from the command line.</span></span> <span data-ttu-id="476ab-130">Windows PowerShell supporta gli alias di parametro tramite il [System.Management.Automation.Aliasattribute](/dotnet/api/System.Management.Automation.AliasAttribute) attribute, che utilizza la sintassi di dichiarazione [Alias()].</span><span class="sxs-lookup"><span data-stu-id="476ab-130">Windows PowerShell supports parameter aliases through the [System.Management.Automation.Aliasattribute](/dotnet/api/System.Management.Automation.AliasAttribute) attribute, which uses the declaration syntax [Alias()].</span></span>

<span data-ttu-id="476ab-131">Il codice seguente illustra come aggiungere un alias per il `Name` parametro.</span><span class="sxs-lookup"><span data-stu-id="476ab-131">The following code shows how an alias is added to the `Name` parameter.</span></span>

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

<span data-ttu-id="476ab-132">Oltre a usare il [System.Management.Automation.Aliasattribute](/dotnet/api/System.Management.Automation.AliasAttribute) attributo, il runtime di Windows PowerShell esegue la corrispondenza nome parziale, anche se non viene specificato alcun alias.</span><span class="sxs-lookup"><span data-stu-id="476ab-132">In addition to using the [System.Management.Automation.Aliasattribute](/dotnet/api/System.Management.Automation.AliasAttribute) attribute, the Windows PowerShell runtime performs partial name matching, even if no aliases are specified.</span></span> <span data-ttu-id="476ab-133">Se, ad esempio, il cmdlet dispone di un `FileName` parametro e che è l'unico parametro che inizia con `F`, l'utente potrebbe immettere `Filename`, `Filenam`, `File`, `Fi`, o `F` e riconosce ancora la voce come il `FileName` parametro.</span><span class="sxs-lookup"><span data-stu-id="476ab-133">For example, if your cmdlet has a `FileName` parameter and that is the only parameter that starts with `F`, the user could enter `Filename`, `Filenam`, `File`, `Fi`, or `F` and still recognize the entry as the `FileName` parameter.</span></span>

## <a name="creating-help-for-parameters"></a><span data-ttu-id="476ab-134">Creazione di una Guida per i parametri</span><span class="sxs-lookup"><span data-stu-id="476ab-134">Creating Help for Parameters</span></span>

<span data-ttu-id="476ab-135">Windows PowerShell consente di creare la Guida per i parametri del cmdlet.</span><span class="sxs-lookup"><span data-stu-id="476ab-135">Windows PowerShell allows you to create Help for cmdlet parameters.</span></span> <span data-ttu-id="476ab-136">Eseguire questa operazione per qualsiasi parametro usato per il feedback utente e la modifica di sistema.</span><span class="sxs-lookup"><span data-stu-id="476ab-136">Do this for any parameter used for system modification and user feedback.</span></span> <span data-ttu-id="476ab-137">Per ogni parametro per il supporto della Guida, è possibile impostare il `HelpMessage` parola chiave nell'attributo le [System.Management.Automation.Parameterattribute](/dotnet/api/System.Management.Automation.ParameterAttribute) dichiarazione dell'attributo.</span><span class="sxs-lookup"><span data-stu-id="476ab-137">For each parameter to support Help, you can set the `HelpMessage` attribute keyword in the [System.Management.Automation.Parameterattribute](/dotnet/api/System.Management.Automation.ParameterAttribute) attribute declaration.</span></span> <span data-ttu-id="476ab-138">Questa parola chiave definisce il testo da visualizzare all'utente per ottenere assistenza tramite il parametro.</span><span class="sxs-lookup"><span data-stu-id="476ab-138">This keyword defines the text to display to the user for assistance in using the parameter.</span></span> <span data-ttu-id="476ab-139">È anche possibile impostare il `HelpMessageBaseName` parola chiave per identificare il nome di base di una risorsa da usare per il messaggio.</span><span class="sxs-lookup"><span data-stu-id="476ab-139">You can also set the `HelpMessageBaseName` keyword to identify the base name of a resource to use for the message.</span></span> <span data-ttu-id="476ab-140">Se si imposta questa parola chiave, è necessario impostare anche la `HelpMessageResourceId` (parola chiave) per specificare l'identificatore della risorsa.</span><span class="sxs-lookup"><span data-stu-id="476ab-140">If you set this keyword, you must also set the `HelpMessageResourceId` keyword to specify the resource identifier.</span></span>

<span data-ttu-id="476ab-141">Il codice seguente da questo cmdlet Stop-Process definisce il `HelpMessage` attributo la parola chiave per il `Name` parametro.</span><span class="sxs-lookup"><span data-stu-id="476ab-141">The following code from this Stop-Proc cmdlet defines the `HelpMessage` attribute keyword for the `Name` parameter.</span></span>

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

## <a name="overriding-an-input-processing-method"></a><span data-ttu-id="476ab-142">Si esegue l'override di un metodo di elaborazione dell'Input</span><span class="sxs-lookup"><span data-stu-id="476ab-142">Overriding an Input Processing Method</span></span>

<span data-ttu-id="476ab-143">Il cmdlet deve eseguire l'override di un metodo di elaborazione dell'input, in genere si tratterà [System.Management.Automation.Cmdlet.Processrecord\*](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord).</span><span class="sxs-lookup"><span data-stu-id="476ab-143">Your cmdlet must override an input processing method, most often this will be [System.Management.Automation.Cmdlet.Processrecord\*](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord).</span></span> <span data-ttu-id="476ab-144">Quando si modifica il sistema, è necessario chiamare il cmdlet di [System.Management.Automation.Cmdlet.Shouldprocess\*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) e [System.Management.Automation.Cmdlet.Shouldcontinue\*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) metodi per consentire il utente di fornire commenti e suggerimenti prima viene apportata una modifica.</span><span class="sxs-lookup"><span data-stu-id="476ab-144">When modifying the system, the cmdlet should call the [System.Management.Automation.Cmdlet.Shouldprocess\*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) and [System.Management.Automation.Cmdlet.Shouldcontinue\*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) methods to allow the user to provide feedback before a change is made.</span></span> <span data-ttu-id="476ab-145">Per altre informazioni su questi metodi, vedere [creazione di un Cmdlet che modifichi il sistema](./creating-a-cmdlet-that-modifies-the-system.md).</span><span class="sxs-lookup"><span data-stu-id="476ab-145">For more information about these methods, see [Creating a Cmdlet that Modifies the System](./creating-a-cmdlet-that-modifies-the-system.md).</span></span>

## <a name="supporting-wildcard-expansion"></a><span data-ttu-id="476ab-146">Supporto di espansione di caratteri jolly</span><span class="sxs-lookup"><span data-stu-id="476ab-146">Supporting Wildcard Expansion</span></span>

<span data-ttu-id="476ab-147">Per consentire la selezione di più oggetti, è possibile usare i cmdlet di [System.Management.Automation.Wildcardpattern](/dotnet/api/System.Management.Automation.WildcardPattern) e [System.Management.Automation.Wildcardoptions](/dotnet/api/System.Management.Automation.WildcardOptions) alle classi di fornire supporto di espansione con caratteri jolly per il parametro di input.</span><span class="sxs-lookup"><span data-stu-id="476ab-147">To allow the selection of multiple objects, your cmdlet can use the [System.Management.Automation.Wildcardpattern](/dotnet/api/System.Management.Automation.WildcardPattern) and [System.Management.Automation.Wildcardoptions](/dotnet/api/System.Management.Automation.WildcardOptions) classes to provide wildcard expansion support for parameter input.</span></span> <span data-ttu-id="476ab-148">Esempi di modelli con caratteri jolly sono lsa \* \*file con estensione txt e [a-c]\*.</span><span class="sxs-lookup"><span data-stu-id="476ab-148">Examples of wildcard patterns are lsa\*, \*.txt, and [a-c]\*.</span></span> <span data-ttu-id="476ab-149">Quando il modello contiene un carattere che deve essere utilizzato in modo letterale, utilizzare il carattere virgoletta inversa (') come carattere di escape.</span><span class="sxs-lookup"><span data-stu-id="476ab-149">Use the back-quote character (\`) as an escape character when the pattern contains a character that should be used literally.</span></span>

<span data-ttu-id="476ab-150">Le espansioni con caratteri jolly di nomi di file e percorso sono esempi di scenari comuni in cui il cmdlet potrebbe essere necessario consentire il supporto per gli input di percorso quando è richiesta la selezione di più oggetti.</span><span class="sxs-lookup"><span data-stu-id="476ab-150">Wildcard expansions of file and path names are examples of common scenarios where the cmdlet may want to allow support for path inputs when the selection of multiple objects is required.</span></span> <span data-ttu-id="476ab-151">Un caso comune è nel file system, in cui un utente desidera vedere tutti i file che si trovano nella cartella corrente.</span><span class="sxs-lookup"><span data-stu-id="476ab-151">A common case is in the file system, where a user wants to see all files residing in the current folder.</span></span>

<span data-ttu-id="476ab-152">È necessario solo raramente un'implementazione corrispondente del modello con caratteri jolly personalizzati.</span><span class="sxs-lookup"><span data-stu-id="476ab-152">You should need a customized wildcard pattern matching implementation only rarely.</span></span> <span data-ttu-id="476ab-153">In questo caso, il cmdlet deve supportare la completa 1003.2 POSIX, 3,13 specifica per l'espansione di caratteri jolly o il subset semplificato seguente:</span><span class="sxs-lookup"><span data-stu-id="476ab-153">In this case, your cmdlet should support either the full POSIX 1003.2, 3.13 specification for wildcard expansion or the following simplified subset:</span></span>

- <span data-ttu-id="476ab-154">**Punto interrogativo (?).**</span><span class="sxs-lookup"><span data-stu-id="476ab-154">**Question mark (?).**</span></span> <span data-ttu-id="476ab-155">Corrisponde a qualsiasi carattere nella posizione specificata.</span><span class="sxs-lookup"><span data-stu-id="476ab-155">Matches any character at the specified location.</span></span>

- <span data-ttu-id="476ab-156">**Asterisco (\*).**</span><span class="sxs-lookup"><span data-stu-id="476ab-156">**Asterisk (\*).**</span></span> <span data-ttu-id="476ab-157">Corrisponde a zero o più caratteri a partire dalla posizione specificata.</span><span class="sxs-lookup"><span data-stu-id="476ab-157">Matches zero or more characters starting at the specified location.</span></span>

- <span data-ttu-id="476ab-158">**Parentesi quadra aperta ([]).**</span><span class="sxs-lookup"><span data-stu-id="476ab-158">**Open bracket ([).**</span></span> <span data-ttu-id="476ab-159">Introduce un'espressione tra parentesi quadre che può contenere caratteri o un intervallo di caratteri.</span><span class="sxs-lookup"><span data-stu-id="476ab-159">Introduces a pattern bracket expression that can contain characters or a range of characters.</span></span> <span data-ttu-id="476ab-160">Se è necessario un intervallo di valori, un trattino (-) viene utilizzato per indicare l'intervallo.</span><span class="sxs-lookup"><span data-stu-id="476ab-160">If a range is required, a hyphen (-) is used to indicate the range.</span></span>

- <span data-ttu-id="476ab-161">**Parentesi quadra chiusa (]).**</span><span class="sxs-lookup"><span data-stu-id="476ab-161">**Close bracket (]).**</span></span> <span data-ttu-id="476ab-162">Termina un'espressione tra parentesi quadre.</span><span class="sxs-lookup"><span data-stu-id="476ab-162">Ends a pattern bracket expression.</span></span>

- <span data-ttu-id="476ab-163">**Virgoletta carattere di escape (').**</span><span class="sxs-lookup"><span data-stu-id="476ab-163">**Back-quote escape character (\`).**</span></span> <span data-ttu-id="476ab-164">Indica che il carattere successivo deve essere considerato letteralmente.</span><span class="sxs-lookup"><span data-stu-id="476ab-164">Indicates that the next character should be taken literally.</span></span> <span data-ttu-id="476ab-165">Tenere presente che quando si specifica il carattere di virgoletta dalla riga di comando (invece di specificare a livello di codice), il carattere di escape virgoletta deve essere specificato due volte.</span><span class="sxs-lookup"><span data-stu-id="476ab-165">Be aware that when specifying the back-quote character from the command line (as opposed to specifying it programmatically), the back-quote escape character must be specified twice.</span></span>

> [!NOTE]
> <span data-ttu-id="476ab-166">Per altre informazioni sui modelli con caratteri jolly, vedere [che supportano i caratteri jolly in parametri del Cmdlet](./supporting-wildcard-characters-in-cmdlet-parameters.md).</span><span class="sxs-lookup"><span data-stu-id="476ab-166">For more information about wildcard patterns, see [Supporting Wildcards in Cmdlet Parameters](./supporting-wildcard-characters-in-cmdlet-parameters.md).</span></span>

<span data-ttu-id="476ab-167">Il codice seguente viene illustrato come impostare le opzioni con caratteri jolly e definire il modello carattere jolly usato per risolvere il `Name` parametro per questo cmdlet.</span><span class="sxs-lookup"><span data-stu-id="476ab-167">The following code shows how to set wildcard options and define the wildcard pattern used for resolving the `Name` parameter for this cmdlet.</span></span>

```csharp
WildcardOptions options = WildcardOptions.IgnoreCase |
                          WildcardOptions.Compiled;
WildcardPattern wildcard = new WildcardPattern(name,options);
```

<span data-ttu-id="476ab-168">Il codice seguente viene illustrato come testare se il nome di processo corrisponde al modello definito con caratteri jolly.</span><span class="sxs-lookup"><span data-stu-id="476ab-168">The following code shows how to test whether the process name matches the defined wildcard pattern.</span></span> <span data-ttu-id="476ab-169">Si noti che, in questo caso, se il nome del processo non corrisponde al modello, il cmdlet continua nel ottenere il nome del processo successivo.</span><span class="sxs-lookup"><span data-stu-id="476ab-169">Notice that, in this case, if the process name does not match the pattern, the cmdlet continues on to get the next process name.</span></span>

```csharp
if (!wildcard.IsMatch(processName))
{
  continue;
}
```

## <a name="code-sample"></a><span data-ttu-id="476ab-170">Esempio di codice</span><span class="sxs-lookup"><span data-stu-id="476ab-170">Code Sample</span></span>

<span data-ttu-id="476ab-171">Per l'intero C# esempi di codice, vedere [esempio StopProcessSample03](./stopprocesssample03-sample.md).</span><span class="sxs-lookup"><span data-stu-id="476ab-171">For the complete C# sample code, see [StopProcessSample03 Sample](./stopprocesssample03-sample.md).</span></span>

## <a name="define-object-types-and-formatting"></a><span data-ttu-id="476ab-172">Definire i tipi di oggetto e la formattazione</span><span class="sxs-lookup"><span data-stu-id="476ab-172">Define Object Types and Formatting</span></span>

<span data-ttu-id="476ab-173">Windows PowerShell passa informazioni tra i cmdlet con gli oggetti .net.</span><span class="sxs-lookup"><span data-stu-id="476ab-173">Windows PowerShell passes information between cmdlets using .Net objects.</span></span> <span data-ttu-id="476ab-174">Di conseguenza, potrebbe essere necessario definire un proprio tipo di un cmdlet o il cmdlet potrebbe essere necessario estendere un tipo esistente fornito da un altro cmdlet.</span><span class="sxs-lookup"><span data-stu-id="476ab-174">Consequently, a cmdlet may need to define its own type, or the cmdlet may need to extend an existing type provided by another cmdlet.</span></span> <span data-ttu-id="476ab-175">Per altre informazioni sulla definizione di nuovi tipi o estendere i tipi esistenti, vedere [estendendo i tipi di oggetto e formattazione](https://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351).</span><span class="sxs-lookup"><span data-stu-id="476ab-175">For more information about defining new types or extending existing types, see [Extending Object Types and Formatting](https://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351).</span></span>

## <a name="building-the-cmdlet"></a><span data-ttu-id="476ab-176">Creazione di Cmdlet</span><span class="sxs-lookup"><span data-stu-id="476ab-176">Building the Cmdlet</span></span>

<span data-ttu-id="476ab-177">Dopo l'implementazione di un cmdlet, è necessario registrarlo con Windows PowerShell tramite uno snap-in Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="476ab-177">After implementing a cmdlet, it must be registered with Windows PowerShell through a Windows PowerShell snap-in.</span></span> <span data-ttu-id="476ab-178">Per altre informazioni sulla registrazione dei cmdlet, vedere [come registrare i cmdlet, provider e applicazioni Host](https://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c).</span><span class="sxs-lookup"><span data-stu-id="476ab-178">For more information about registering cmdlets, see [How to Register Cmdlets, Providers, and Host Applications](https://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c).</span></span>

## <a name="testing-the-cmdlet"></a><span data-ttu-id="476ab-179">Il Cmdlet di test</span><span class="sxs-lookup"><span data-stu-id="476ab-179">Testing the Cmdlet</span></span>

<span data-ttu-id="476ab-180">Quando il cmdlet è stato registrato con Windows PowerShell, è possibile testarlo eseguendolo dalla riga di comando.</span><span class="sxs-lookup"><span data-stu-id="476ab-180">When your cmdlet has been registered with Windows PowerShell, you can test it by running it on the command line.</span></span> <span data-ttu-id="476ab-181">È possibile testare il cmdlet Stop-Process di esempio.</span><span class="sxs-lookup"><span data-stu-id="476ab-181">Let's test the sample Stop-Proc cmdlet.</span></span> <span data-ttu-id="476ab-182">Per altre informazioni sull'utilizzo dei cmdlet dalla riga di comando, vedere la [Introduzione a Windows PowerShell](/powershell/scripting/getting-started/getting-started-with-windows-powershell).</span><span class="sxs-lookup"><span data-stu-id="476ab-182">For more information about using cmdlets from the command line, see the [Getting Started with Windows PowerShell](/powershell/scripting/getting-started/getting-started-with-windows-powershell).</span></span>

- <span data-ttu-id="476ab-183">Avviare Windows PowerShell e usare Stop-Process per arrestare un processo usando l'alias ProcessName di `Name` parametro.</span><span class="sxs-lookup"><span data-stu-id="476ab-183">Start Windows PowerShell and use Stop-Proc to stop a process using the ProcessName alias for the `Name` parameter.</span></span>

    ```powershell
    PS> stop-proc -ProcessName notepad
    ```

<span data-ttu-id="476ab-184">Viene visualizzato l'output seguente.</span><span class="sxs-lookup"><span data-stu-id="476ab-184">The following output appears.</span></span>

    ```
    Confirm
    Are you sure you want to perform this action?
    Performing operation "stop-proc" on Target "notepad (3496)".
    [Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"): Y
    ```

- <span data-ttu-id="476ab-185">Verificare la voce seguente nella riga di comando.</span><span class="sxs-lookup"><span data-stu-id="476ab-185">Make the following entry on the command line.</span></span> <span data-ttu-id="476ab-186">Poiché il parametro Name è obbligatorio, richiesto.</span><span class="sxs-lookup"><span data-stu-id="476ab-186">Because the Name parameter is mandatory, you are prompted for it.</span></span> <span data-ttu-id="476ab-187">Immettere "!?"</span><span class="sxs-lookup"><span data-stu-id="476ab-187">Entering "!?"</span></span> <span data-ttu-id="476ab-188">Visualizza il testo della Guida associato al parametro.</span><span class="sxs-lookup"><span data-stu-id="476ab-188">brings up the help text associated with the parameter.</span></span>

    ```powershell
    PS> stop-proc
    ```

<span data-ttu-id="476ab-189">Viene visualizzato l'output seguente.</span><span class="sxs-lookup"><span data-stu-id="476ab-189">The following output appears.</span></span>

    ```
    Cmdlet stop-proc at command pipeline position 1
    Supply values for the following parameters:
    (Type !? for Help.)
    Name[0]: !?
    The name of one or more processes to stop. Wildcards are permitted.
    Name[0]: notepad
    ```

- <span data-ttu-id="476ab-190">Ora apportare la voce seguente per arrestare tutti i processi che corrispondono al modello con caratteri jolly "\* Nota\*".</span><span class="sxs-lookup"><span data-stu-id="476ab-190">Now make the following entry to stop all processes that match the wildcard pattern "\*note\*".</span></span> <span data-ttu-id="476ab-191">Viene chiesto prima di arrestare ciascun processo che corrisponde al modello.</span><span class="sxs-lookup"><span data-stu-id="476ab-191">You are prompted before stopping each process that matches the pattern.</span></span>

    ```powershell
    PS> stop-proc -Name *note*
    ```

<span data-ttu-id="476ab-192">Viene visualizzato l'output seguente.</span><span class="sxs-lookup"><span data-stu-id="476ab-192">The following output appears.</span></span>

    ```
    Confirm
    Are you sure you want to perform this action?
    Performing operation "stop-proc" on Target "notepad (1112)".
    [Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"): Y
    ```

<span data-ttu-id="476ab-193">Viene visualizzato l'output seguente.</span><span class="sxs-lookup"><span data-stu-id="476ab-193">The following output appears.</span></span>

    ```
    Confirm
    Are you sure you want to perform this action?
    Performing operation "stop-proc" on Target "ONENOTEM (3712)".
    [Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"): N
    ```

<span data-ttu-id="476ab-194">Viene visualizzato l'output seguente.</span><span class="sxs-lookup"><span data-stu-id="476ab-194">The following output appears.</span></span>

    ```
    Confirm
    Are you sure you want to perform this action?
    Performing operation "stop-proc" on Target "ONENOTE (3592)".
    [Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"): N
    ```

## <a name="see-also"></a><span data-ttu-id="476ab-195">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="476ab-195">See Also</span></span>

[<span data-ttu-id="476ab-196">Creare un Cmdlet che modifichi il sistema</span><span class="sxs-lookup"><span data-stu-id="476ab-196">Create a Cmdlet that Modifies the System</span></span>](./creating-a-cmdlet-that-modifies-the-system.md)

[<span data-ttu-id="476ab-197">Come creare un Cmdlet di Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="476ab-197">How to Create a Windows PowerShell Cmdlet</span></span>](https://msdn.microsoft.com/en-us/0d721742-c849-4d0d-964f-78ddd9cd258c)

[<span data-ttu-id="476ab-198">Estensione di tipi di oggetto e la formattazione</span><span class="sxs-lookup"><span data-stu-id="476ab-198">Extending Object Types and Formatting</span></span>](https://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351)

[<span data-ttu-id="476ab-199">Come registrare i cmdlet, provider e applicazioni Host</span><span class="sxs-lookup"><span data-stu-id="476ab-199">How to Register Cmdlets, Providers, and Host Applications</span></span>](https://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c)

[<span data-ttu-id="476ab-200">Che supportano i caratteri jolly in parametri del Cmdlet</span><span class="sxs-lookup"><span data-stu-id="476ab-200">Supporting Wildcards in Cmdlet Parameters</span></span>](./supporting-wildcard-characters-in-cmdlet-parameters.md)

[<span data-ttu-id="476ab-201">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="476ab-201">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)
