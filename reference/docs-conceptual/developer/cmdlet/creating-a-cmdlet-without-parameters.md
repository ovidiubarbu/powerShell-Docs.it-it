---
title: Creazione di un cmdlet senza parametri | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- cmdlets [PowerShell Programmers Guide], creating
- cmdlets [PowerShell Programmers Guide], basic cmdlet
ms.assetid: 54236ef3-82db-45f8-9114-1ecb7ff65d3e
caps.latest.revision: 8
ms.openlocfilehash: af41c2c9855310d047404114a07b27180a7aa8fc
ms.sourcegitcommit: d43f66071f1f33b350d34fa1f46f3a35910c5d24
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/23/2019
ms.locfileid: "74415663"
---
# <a name="creating-a-cmdlet-without-parameters"></a><span data-ttu-id="3c6a8-102">Creazione di un cmdlet senza parametri</span><span class="sxs-lookup"><span data-stu-id="3c6a8-102">Creating a Cmdlet without Parameters</span></span>

<span data-ttu-id="3c6a8-103">In questa sezione viene descritto come creare un cmdlet che recupera le informazioni dal computer locale senza l'utilizzo di parametri e quindi scrive le informazioni nella pipeline.</span><span class="sxs-lookup"><span data-stu-id="3c6a8-103">This section describes how to create a cmdlet that retrieves information from the local computer without the use of parameters, and then writes the information to the pipeline.</span></span> <span data-ttu-id="3c6a8-104">Il cmdlet descritto di seguito è un cmdlet Get-proc che recupera le informazioni sui processi del computer locale e quindi visualizza tali informazioni nella riga di comando.</span><span class="sxs-lookup"><span data-stu-id="3c6a8-104">The cmdlet described here is a Get-Proc cmdlet that retrieves information about the processes of the local computer, and then displays that information at the command line.</span></span>

> [!NOTE]
> <span data-ttu-id="3c6a8-105">Tenere presente che quando si scrivono i cmdlet, gli assembly di riferimento® di Windows PowerShell vengono scaricati su disco (per impostazione predefinita, in C:\Program Files\Reference Assemblies\Microsoft\WindowsPowerShell\v1.0).</span><span class="sxs-lookup"><span data-stu-id="3c6a8-105">Be aware that when writing cmdlets, the Windows PowerShell® reference assemblies are downloaded onto disk (by default at C:\Program Files\Reference Assemblies\Microsoft\WindowsPowerShell\v1.0).</span></span> <span data-ttu-id="3c6a8-106">Non sono installati nella global assembly cache (GAC).</span><span class="sxs-lookup"><span data-stu-id="3c6a8-106">They are not installed in the Global Assembly Cache (GAC).</span></span>

## <a name="naming-the-cmdlet"></a><span data-ttu-id="3c6a8-107">Assegnazione di un nome al cmdlet</span><span class="sxs-lookup"><span data-stu-id="3c6a8-107">Naming the Cmdlet</span></span>

<span data-ttu-id="3c6a8-108">Il nome di un cmdlet è costituito da un verbo che indica l'azione eseguita dal cmdlet e da un sostantivo che indica gli elementi su cui agisce il cmdlet.</span><span class="sxs-lookup"><span data-stu-id="3c6a8-108">A cmdlet name consists of a verb that indicates the action the cmdlet takes and a noun that indicates the items that the cmdlet acts upon.</span></span> <span data-ttu-id="3c6a8-109">Poiché questo cmdlet Get-proc di esempio recupera gli oggetti processo, usa il verbo "Get", definito dall'enumerazione [System. Management. Automation. Verbscommon](/dotnet/api/System.Management.Automation.VerbsCommon) e il sostantivo "proc" per indicare che il cmdlet funziona sugli elementi del processo.</span><span class="sxs-lookup"><span data-stu-id="3c6a8-109">Because this sample Get-Proc cmdlet retrieves process objects, it uses the verb "Get", defined by the [System.Management.Automation.Verbscommon](/dotnet/api/System.Management.Automation.VerbsCommon) enumeration, and the noun "Proc" to indicate that the cmdlet works on process items.</span></span>

<span data-ttu-id="3c6a8-110">Quando si assegnano nomi ai cmdlet, non usare i caratteri seguenti: #, () {} [] &-/\ $; : "' < > &#124; ?</span><span class="sxs-lookup"><span data-stu-id="3c6a8-110">When naming cmdlets, do not use any of the following characters: # , () {} [] & - /\ $ ; : " '<> &#124; ?</span></span> <span data-ttu-id="3c6a8-111">@ \` .</span><span class="sxs-lookup"><span data-stu-id="3c6a8-111">@ \` .</span></span>

### <a name="choosing-a-noun"></a><span data-ttu-id="3c6a8-112">Scelta di un sostantivo</span><span class="sxs-lookup"><span data-stu-id="3c6a8-112">Choosing a Noun</span></span>

<span data-ttu-id="3c6a8-113">È necessario scegliere un sostantivo specifico.</span><span class="sxs-lookup"><span data-stu-id="3c6a8-113">You should choose a noun that is specific.</span></span> <span data-ttu-id="3c6a8-114">È preferibile usare un sostantivo singolare preceduto da una versione abbreviata del nome del prodotto.</span><span class="sxs-lookup"><span data-stu-id="3c6a8-114">It is best to use a singular noun prefixed with a shortened version of the product name.</span></span> <span data-ttu-id="3c6a8-115">Un esempio di nome di cmdlet di questo tipo è "`Get-SQLServer`".</span><span class="sxs-lookup"><span data-stu-id="3c6a8-115">An example cmdlet name of this type is "`Get-SQLServer`".</span></span>

### <a name="choosing-a-verb"></a><span data-ttu-id="3c6a8-116">Scelta di un verbo</span><span class="sxs-lookup"><span data-stu-id="3c6a8-116">Choosing a Verb</span></span>

<span data-ttu-id="3c6a8-117">È necessario usare un verbo dal set di nomi di verbi di cmdlet approvati.</span><span class="sxs-lookup"><span data-stu-id="3c6a8-117">You should use a verb from the set of approved cmdlet verb names.</span></span> <span data-ttu-id="3c6a8-118">Per ulteriori informazioni sui verbi dei cmdlet approvati, vedere [nomi dei verbi dei cmdlet](./approved-verbs-for-windows-powershell-commands.md).</span><span class="sxs-lookup"><span data-stu-id="3c6a8-118">For more information about the approved cmdlet verbs, see [Cmdlet Verb Names](./approved-verbs-for-windows-powershell-commands.md).</span></span>

## <a name="defining-the-cmdlet-class"></a><span data-ttu-id="3c6a8-119">Definizione della classe cmdlet</span><span class="sxs-lookup"><span data-stu-id="3c6a8-119">Defining the Cmdlet Class</span></span>

<span data-ttu-id="3c6a8-120">Una volta scelto il nome di un cmdlet, definire una classe .NET per implementare il cmdlet.</span><span class="sxs-lookup"><span data-stu-id="3c6a8-120">Once you have chosen a cmdlet name, define a .NET class to implement the cmdlet.</span></span> <span data-ttu-id="3c6a8-121">Di seguito è illustrata la definizione di classe per questo cmdlet Get-proc di esempio:</span><span class="sxs-lookup"><span data-stu-id="3c6a8-121">Here is the class definition for this sample Get-Proc cmdlet:</span></span>

```csharp
[Cmdlet(VerbsCommon.Get, "Proc")]
  public class GetProcCommand : Cmdlet
```

```vb
<Cmdlet(VerbsCommon.Get, "Proc")> _
Public Class GetProcCommand
    Inherits Cmdlet
```

<span data-ttu-id="3c6a8-122">Si noti che precedente alla definizione della classe, l'attributo [System. Management. Automation. CmdletAttribute](/dotnet/api/System.Management.Automation.CmdletAttribute) , con la sintassi `[Cmdlet(verb, noun, ...)]`, viene usato per identificare questa classe come un cmdlet.</span><span class="sxs-lookup"><span data-stu-id="3c6a8-122">Notice that previous to the class definition, the [System.Management.Automation.CmdletAttribute](/dotnet/api/System.Management.Automation.CmdletAttribute) attribute, with the syntax `[Cmdlet(verb, noun, ...)]`, is used to identify this class as a cmdlet.</span></span> <span data-ttu-id="3c6a8-123">Questo è l'unico attributo obbligatorio per tutti i cmdlet e consente al runtime di Windows PowerShell di chiamarli correttamente.</span><span class="sxs-lookup"><span data-stu-id="3c6a8-123">This is the only required attribute for all cmdlets, and it allows the Windows PowerShell runtime to call them correctly.</span></span> <span data-ttu-id="3c6a8-124">È possibile impostare le parole chiave degli attributi per dichiarare ulteriormente la classe se necessario.</span><span class="sxs-lookup"><span data-stu-id="3c6a8-124">You can set attribute keywords to further declare the class if necessary.</span></span> <span data-ttu-id="3c6a8-125">Tenere presente che la dichiarazione di attributo per la classe GetProcCommand di esempio dichiara solo i nomi dei sostantivi e dei verbi per il cmdlet Get-proc.</span><span class="sxs-lookup"><span data-stu-id="3c6a8-125">Be aware that the attribute declaration for our sample GetProcCommand class declares only the noun and verb names for the Get-Proc cmdlet.</span></span>

> [!NOTE]
> <span data-ttu-id="3c6a8-126">Per tutte le classi di attributi di Windows PowerShell, le parole chiave che è possibile impostare corrispondono alle proprietà della classe Attribute.</span><span class="sxs-lookup"><span data-stu-id="3c6a8-126">For all Windows PowerShell attribute classes, the keywords that you can set correspond to properties of the attribute class.</span></span>

<span data-ttu-id="3c6a8-127">Quando si denomina la classe del cmdlet, è consigliabile riflettere il nome del cmdlet nel nome della classe.</span><span class="sxs-lookup"><span data-stu-id="3c6a8-127">When naming the class of the cmdlet, it is a good practice to reflect the cmdlet name in the class name.</span></span> <span data-ttu-id="3c6a8-128">A tale scopo, utilizzare il formato "VerbNounCommand" e sostituire "verb" e "noun" con il verbo e il sostantivo utilizzati nel nome del cmdlet.</span><span class="sxs-lookup"><span data-stu-id="3c6a8-128">To do this, use the form "VerbNounCommand" and replace "Verb" and "Noun" with the verb and noun used in the cmdlet name.</span></span> <span data-ttu-id="3c6a8-129">Come illustrato nella definizione di classe precedente, il cmdlet Get-proc di esempio definisce una classe denominata GetProcCommand, che deriva dalla classe di base [System. Management. Automation. cmdlet](/dotnet/api/System.Management.Automation.Cmdlet) .</span><span class="sxs-lookup"><span data-stu-id="3c6a8-129">As is shown in the previous class definition, the sample Get-Proc cmdlet defines a class called GetProcCommand, which derives from the [System.Management.Automation.Cmdlet](/dotnet/api/System.Management.Automation.Cmdlet) base class.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="3c6a8-130">Se si vuole definire un cmdlet che accede direttamente al runtime di Windows PowerShell, la classe .NET deve derivare dalla classe di base [System. Management. Automation. PSCmdlet](/dotnet/api/System.Management.Automation.PSCmdlet) .</span><span class="sxs-lookup"><span data-stu-id="3c6a8-130">If you want to define a cmdlet that accesses the Windows PowerShell runtime directly, your .NET class should derive from the [System.Management.Automation.PSCmdlet](/dotnet/api/System.Management.Automation.PSCmdlet) base class.</span></span> <span data-ttu-id="3c6a8-131">Per ulteriori informazioni su questa classe, vedere [creazione di un cmdlet che definisce i set di parametri](./adding-parameter-sets-to-a-cmdlet.md).</span><span class="sxs-lookup"><span data-stu-id="3c6a8-131">For more information about this class, see [Creating a Cmdlet that Defines Parameter Sets](./adding-parameter-sets-to-a-cmdlet.md).</span></span>

> [!NOTE]
> <span data-ttu-id="3c6a8-132">La classe per un cmdlet deve essere contrassegnata in modo esplicito come Public.</span><span class="sxs-lookup"><span data-stu-id="3c6a8-132">The class for a cmdlet must be explicitly marked as public.</span></span> <span data-ttu-id="3c6a8-133">Per impostazione predefinita, le classi non contrassegnate come pubbliche saranno interne e non verranno trovate dal runtime di Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="3c6a8-133">Classes that are not marked as public will default to internal and will not be found by the Windows PowerShell runtime.</span></span>

<span data-ttu-id="3c6a8-134">Windows PowerShell usa lo spazio dei nomi [Microsoft. PowerShell. Commands](/dotnet/api/Microsoft.PowerShell.Commands) per le classi di cmdlet.</span><span class="sxs-lookup"><span data-stu-id="3c6a8-134">Windows PowerShell uses the [Microsoft.PowerShell.Commands](/dotnet/api/Microsoft.PowerShell.Commands) namespace for its cmdlet classes.</span></span> <span data-ttu-id="3c6a8-135">Si consiglia di inserire le classi di cmdlet in uno spazio dei nomi Commands dello spazio dei nomi dell'API, ad esempio, xxx. PS. Commands.</span><span class="sxs-lookup"><span data-stu-id="3c6a8-135">It is recommended to place your cmdlet classes in a Commands namespace of your API namespace, for example, xxx.PS.Commands.</span></span>

## <a name="overriding-an-input-processing-method"></a><span data-ttu-id="3c6a8-136">Override di un metodo di elaborazione dell'input</span><span class="sxs-lookup"><span data-stu-id="3c6a8-136">Overriding an Input Processing Method</span></span>

<span data-ttu-id="3c6a8-137">La classe [System. Management. Automation. cmdlet](/dotnet/api/System.Management.Automation.Cmdlet) fornisce tre metodi principali di elaborazione dell'input, almeno uno dei quali deve eseguire l'override del cmdlet.</span><span class="sxs-lookup"><span data-stu-id="3c6a8-137">The [System.Management.Automation.Cmdlet](/dotnet/api/System.Management.Automation.Cmdlet) class provides three main input processing methods, at least one of which your cmdlet must override.</span></span> <span data-ttu-id="3c6a8-138">Per ulteriori informazioni sul modo in cui Windows PowerShell elabora i record, vedere funzionamento di [Windows PowerShell](/previous-versions//ms714658(v=vs.85)).</span><span class="sxs-lookup"><span data-stu-id="3c6a8-138">For more information about how Windows PowerShell processes records, see [How Windows PowerShell Works](/previous-versions//ms714658(v=vs.85)).</span></span>

<span data-ttu-id="3c6a8-139">Per tutti i tipi di input, il runtime di Windows PowerShell chiama [System. Management. Automation. cmdlet. BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) per abilitare l'elaborazione.</span><span class="sxs-lookup"><span data-stu-id="3c6a8-139">For all types of input, the Windows PowerShell runtime calls [System.Management.Automation.Cmdlet.BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) to enable processing.</span></span> <span data-ttu-id="3c6a8-140">Se il cmdlet deve eseguire una pre-elaborazione o un programma di installazione, è possibile eseguire questa operazione eseguendo l'override di questo metodo.</span><span class="sxs-lookup"><span data-stu-id="3c6a8-140">If your cmdlet must perform some preprocessing or setup, it can do this by overriding this method.</span></span>

> [!NOTE]
> <span data-ttu-id="3c6a8-141">Windows PowerShell usa il termine "record" per descrivere il set di valori di parametro fornito quando viene chiamato un cmdlet.</span><span class="sxs-lookup"><span data-stu-id="3c6a8-141">Windows PowerShell uses the term "record" to describe the set of parameter values supplied when a cmdlet is called.</span></span>

<span data-ttu-id="3c6a8-142">Se il cmdlet accetta input della pipeline, deve eseguire l'override del metodo [System. Management. Automation. cmdlet. ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) e, facoltativamente, del metodo [System. Management. Automation. cmdlet. EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) .</span><span class="sxs-lookup"><span data-stu-id="3c6a8-142">If your cmdlet accepts pipeline input, it must override the [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) method, and optionally the [System.Management.Automation.Cmdlet.EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) method.</span></span> <span data-ttu-id="3c6a8-143">Ad esempio, un cmdlet potrebbe eseguire l'override di entrambi i metodi se raccoglie tutti gli input usando [System. Management. Automation. cmdlet. ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) e quindi opera sull'input nel suo complesso anziché su un elemento alla volta, come fa il cmdlet `Sort-Object`.</span><span class="sxs-lookup"><span data-stu-id="3c6a8-143">For example, a cmdlet might override both methods if it gathers all input using [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) and then operates on the input as a whole rather than one element at a time, as the `Sort-Object` cmdlet does.</span></span>

<span data-ttu-id="3c6a8-144">Se il cmdlet non accetta input della pipeline, deve eseguire l'override del metodo [System. Management. Automation. cmdlet. EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) .</span><span class="sxs-lookup"><span data-stu-id="3c6a8-144">If your cmdlet does not take pipeline input, it should override the [System.Management.Automation.Cmdlet.EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) method.</span></span> <span data-ttu-id="3c6a8-145">Tenere presente che questo metodo viene spesso usato al posto di [System. Management. Automation. cmdlet. BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) quando il cmdlet non può funzionare su un elemento alla volta, come nel caso di un cmdlet di ordinamento.</span><span class="sxs-lookup"><span data-stu-id="3c6a8-145">Be aware that this method is frequently used in place of [System.Management.Automation.Cmdlet.BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) when the cmdlet cannot operate on one element at a time, as is the case for a sorting cmdlet.</span></span>

<span data-ttu-id="3c6a8-146">Poiché questo cmdlet Get-proc di esempio deve ricevere input della pipeline, esegue l'override del metodo [System. Management. Automation. cmdlet. ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) e usa le implementazioni predefinite per [System. Management. Automation. cmdlet. BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) e [System. Management. Automation. cmdlet. EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing).</span><span class="sxs-lookup"><span data-stu-id="3c6a8-146">Because this sample Get-Proc cmdlet must receive pipeline input, it overrides the [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) method and uses the default implementations for [System.Management.Automation.Cmdlet.BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) and [System.Management.Automation.Cmdlet.EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing).</span></span> <span data-ttu-id="3c6a8-147">L'override di [System. Management. Automation. cmdlet. ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) recupera i processi e li scrive nella riga di comando usando il metodo [System. Management. Automation. cmdlet. WriteObject](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject) .</span><span class="sxs-lookup"><span data-stu-id="3c6a8-147">The [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) override retrieves processes and writes them to the command line using the [System.Management.Automation.Cmdlet.WriteObject](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject) method.</span></span>

```csharp
protected override void ProcessRecord()
{
  // Get the current processes
  Process[] processes = Process.GetProcesses();

  // Write the processes to the pipeline making them available
  // to the next cmdlet. The second parameter of this call tells
  // PowerShell to enumerate the array, and send one process at a
  // time to the pipeline.
  WriteObject(processes, true);
}
```

```vb
Protected Overrides Sub ProcessRecord()

    '/ Get the current processes.
    Dim processes As Process()
    processes = Process.GetProcesses()

    '/ Write the processes to the pipeline making them available
    '/ to the next cmdlet. The second parameter of this call tells
    '/ PowerShell to enumerate the array, and send one process at a
    '/ time to the pipeline.
    WriteObject(processes, True)

End Sub 'ProcessRecord
```

#### <a name="things-to-remember-about-input-processing"></a><span data-ttu-id="3c6a8-148">Aspetti da ricordare sull'elaborazione dell'input</span><span class="sxs-lookup"><span data-stu-id="3c6a8-148">Things to Remember About Input Processing</span></span>

- <span data-ttu-id="3c6a8-149">L'origine predefinita per l'input è un oggetto esplicito, ad esempio una stringa, fornito dall'utente nella riga di comando.</span><span class="sxs-lookup"><span data-stu-id="3c6a8-149">The default source for input is an explicit object (for example, a string) provided by the user on the command line.</span></span> <span data-ttu-id="3c6a8-150">Per ulteriori informazioni, vedere [creazione di un cmdlet per elaborare l'input della riga di comando](./adding-parameters-that-process-command-line-input.md).</span><span class="sxs-lookup"><span data-stu-id="3c6a8-150">For more information, see [Creating a Cmdlet to Process Command Line Input](./adding-parameters-that-process-command-line-input.md).</span></span>

- <span data-ttu-id="3c6a8-151">Un metodo di elaborazione dell'input può anche ricevere input dall'oggetto di output di un cmdlet upstream sulla pipeline.</span><span class="sxs-lookup"><span data-stu-id="3c6a8-151">An input processing method can also receive input from the output object of an upstream cmdlet on the pipeline.</span></span> <span data-ttu-id="3c6a8-152">Per ulteriori informazioni, vedere [creazione di un cmdlet per elaborare l'input della pipeline](./adding-parameters-that-process-pipeline-input.md).</span><span class="sxs-lookup"><span data-stu-id="3c6a8-152">For more information, see [Creating a Cmdlet to Process Pipeline Input](./adding-parameters-that-process-pipeline-input.md).</span></span> <span data-ttu-id="3c6a8-153">Tenere presente che il cmdlet può ricevere input da una combinazione di origini della riga di comando e di pipeline.</span><span class="sxs-lookup"><span data-stu-id="3c6a8-153">Be aware that your cmdlet can receive input from a combination of command-line and pipeline sources.</span></span>

- <span data-ttu-id="3c6a8-154">È possibile che il cmdlet downstream non venga restituito per molto tempo.</span><span class="sxs-lookup"><span data-stu-id="3c6a8-154">The downstream cmdlet might not return for a long time, or not at all.</span></span> <span data-ttu-id="3c6a8-155">Per questo motivo, il metodo di elaborazione dell'input nel cmdlet non deve mantenere i blocchi durante le chiamate a [System. Management. Automation. cmdlet. WriteObject](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject), in particolare i blocchi per i quali l'ambito si estende oltre l'istanza del cmdlet.</span><span class="sxs-lookup"><span data-stu-id="3c6a8-155">For that reason, the input processing method in your cmdlet should not hold locks during calls to [System.Management.Automation.Cmdlet.WriteObject](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject), especially locks for which the scope extends beyond the cmdlet instance.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="3c6a8-156">I cmdlet non devono mai chiamare [System. Console. WriteLine \*](/dotnet/api/System.Console.WriteLine) o l'equivalente.</span><span class="sxs-lookup"><span data-stu-id="3c6a8-156">Cmdlets should never call [System.Console.Writeline\*](/dotnet/api/System.Console.WriteLine) or its equivalent.</span></span>

- <span data-ttu-id="3c6a8-157">Il cmdlet potrebbe avere variabili oggetto da pulire al termine dell'elaborazione, ad esempio se apre un handle di file nel metodo [System. Management. Automation. cmdlet. BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) e mantiene l'handle aperto per l'uso da parte di [System. Management. Automation. cmdlet. ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord)).</span><span class="sxs-lookup"><span data-stu-id="3c6a8-157">Your cmdlet might have object variables to clean up when it is finished processing (for example, if it opens a file handle in the [System.Management.Automation.Cmdlet.BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) method and keeps the handle open for use by [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord)).</span></span> <span data-ttu-id="3c6a8-158">È importante ricordare che il runtime di Windows PowerShell non chiama sempre il metodo [System. Management. Automation. cmdlet. EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) , che deve eseguire la pulizia degli oggetti.</span><span class="sxs-lookup"><span data-stu-id="3c6a8-158">It is important to remember that the Windows PowerShell runtime does not always call the [System.Management.Automation.Cmdlet.EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) method, which should perform object cleanup.</span></span>

<span data-ttu-id="3c6a8-159">Ad esempio, [System. Management. Automation. cmdlet. EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) potrebbe non essere chiamato se il cmdlet viene annullato a metà o se si verifica un errore di terminazione in qualsiasi parte del cmdlet.</span><span class="sxs-lookup"><span data-stu-id="3c6a8-159">For example, [System.Management.Automation.Cmdlet.EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) might not be called if the cmdlet is canceled midway or if a terminating error occurs in any part of the cmdlet.</span></span> <span data-ttu-id="3c6a8-160">Pertanto, un cmdlet che richiede la pulizia degli oggetti deve implementare il modello [System. IDisposable](/dotnet/api/System.IDisposable) completo, incluso il finalizzatore, in modo che il runtime possa chiamare sia [System. Management. Automation. cmdlet. EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) e [System. IDisposable. Dispose \*](/dotnet/api/System.IDisposable.Dispose) al termine dell'elaborazione.</span><span class="sxs-lookup"><span data-stu-id="3c6a8-160">Therefore, a cmdlet that requires object cleanup should implement the complete [System.IDisposable](/dotnet/api/System.IDisposable) pattern, including the finalizer, so that the runtime can call both [System.Management.Automation.Cmdlet.EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) and [System.IDisposable.Dispose\*](/dotnet/api/System.IDisposable.Dispose) at the end of processing.</span></span>

## <a name="code-sample"></a><span data-ttu-id="3c6a8-161">Esempio di codice</span><span class="sxs-lookup"><span data-stu-id="3c6a8-161">Code Sample</span></span>

<span data-ttu-id="3c6a8-162">Per il codice C# di esempio completo, vedere l' [esempio GetProcessSample01](./getprocesssample01-sample.md).</span><span class="sxs-lookup"><span data-stu-id="3c6a8-162">For the complete C# sample code, see [GetProcessSample01 Sample](./getprocesssample01-sample.md).</span></span>

## <a name="defining-object-types-and-formatting"></a><span data-ttu-id="3c6a8-163">Definizione di tipi di oggetti e formattazione</span><span class="sxs-lookup"><span data-stu-id="3c6a8-163">Defining Object Types and Formatting</span></span>

<span data-ttu-id="3c6a8-164">Windows PowerShell passa le informazioni tra i cmdlet usando gli oggetti .NET.</span><span class="sxs-lookup"><span data-stu-id="3c6a8-164">Windows PowerShell passes information between cmdlets using .NET objects.</span></span> <span data-ttu-id="3c6a8-165">Di conseguenza, un cmdlet potrebbe dover definire il proprio tipo oppure il cmdlet deve estendere un tipo esistente fornito da un altro cmdlet.</span><span class="sxs-lookup"><span data-stu-id="3c6a8-165">Consequently, a cmdlet might need to define its own type, or the cmdlet might need to extend an existing type provided by another cmdlet.</span></span> <span data-ttu-id="3c6a8-166">Per ulteriori informazioni sulla definizione di nuovi tipi o sull'estensione di tipi esistenti, vedere [estensione di tipi di oggetti e formattazione](/previous-versions//ms714665(v=vs.85)).</span><span class="sxs-lookup"><span data-stu-id="3c6a8-166">For more information about defining new types or extending existing types, see [Extending Object Types and Formatting](/previous-versions//ms714665(v=vs.85)).</span></span>

## <a name="building-the-cmdlet"></a><span data-ttu-id="3c6a8-167">Compilazione del cmdlet</span><span class="sxs-lookup"><span data-stu-id="3c6a8-167">Building the Cmdlet</span></span>

<span data-ttu-id="3c6a8-168">Dopo l'implementazione di un cmdlet, è necessario registrarlo con Windows PowerShell tramite uno snap-in di Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="3c6a8-168">After implementing a cmdlet, you must register it with Windows PowerShell through a Windows PowerShell snap-in.</span></span> <span data-ttu-id="3c6a8-169">Per ulteriori informazioni sulla registrazione dei cmdlet, vedere [come registrare i cmdlet, i provider e le applicazioni host](/previous-versions//ms714644(v=vs.85)).</span><span class="sxs-lookup"><span data-stu-id="3c6a8-169">For more information about registering cmdlets, see [How to Register Cmdlets, Providers, and Host Applications](/previous-versions//ms714644(v=vs.85)).</span></span>

## <a name="testing-the-cmdlet"></a><span data-ttu-id="3c6a8-170">Test del cmdlet</span><span class="sxs-lookup"><span data-stu-id="3c6a8-170">Testing the Cmdlet</span></span>

<span data-ttu-id="3c6a8-171">Quando il cmdlet è stato registrato con Windows PowerShell, è possibile testarlo eseguendolo nella riga di comando.</span><span class="sxs-lookup"><span data-stu-id="3c6a8-171">When your cmdlet has been registered with Windows PowerShell, you can test it by running it on the command line.</span></span> <span data-ttu-id="3c6a8-172">Il codice per il cmdlet Get-proc di esempio è di dimensioni ridotte, ma usa ancora il runtime di Windows PowerShell e un oggetto .NET esistente, che è sufficiente per renderlo utile.</span><span class="sxs-lookup"><span data-stu-id="3c6a8-172">The code for our sample Get-Proc cmdlet is small, but it still uses the Windows PowerShell runtime and an existing .NET object, which is enough to make it useful.</span></span> <span data-ttu-id="3c6a8-173">È possibile eseguirne il test per comprendere meglio cosa può fare Get-proc e come può essere usato l'output.</span><span class="sxs-lookup"><span data-stu-id="3c6a8-173">Let's test it to better understand what Get-Proc can do and how its output can be used.</span></span> <span data-ttu-id="3c6a8-174">Per ulteriori informazioni sull'utilizzo dei cmdlet dalla riga di comando, vedere la [Introduzione con Windows PowerShell](/powershell/scripting/getting-started/getting-started-with-windows-powershell).</span><span class="sxs-lookup"><span data-stu-id="3c6a8-174">For more information about using cmdlets from the command line, see the [Getting Started with Windows PowerShell](/powershell/scripting/getting-started/getting-started-with-windows-powershell).</span></span>

1. <span data-ttu-id="3c6a8-175">Avviare Windows PowerShell e ottenere i processi correnti in esecuzione nel computer.</span><span class="sxs-lookup"><span data-stu-id="3c6a8-175">Start Windows PowerShell, and get the current processes running on the computer.</span></span>

    ```powershell
    get-proc
    ```

    <span data-ttu-id="3c6a8-176">Viene visualizzato l'output seguente.</span><span class="sxs-lookup"><span data-stu-id="3c6a8-176">The following output appears.</span></span>

    ```output
    Handles  NPM(K)  PM(K)  WS(K)  VS(M)  CPU(s)  Id   ProcessName
    -------  ------  -----  -----  -----  ------  --   ----------
    254      7       7664   12048  66     173.75  1200  QCTRAY
    32       2       1372   2628   31       0.04  1860  DLG
    271      6       1216   3688   33       0.03  3816  lg
    27       2       560    1920   24       0.01  1768  TpScrex
    ...
    ```

2. <span data-ttu-id="3c6a8-177">Assegnare una variabile ai risultati del cmdlet per una manipolazione più semplice.</span><span class="sxs-lookup"><span data-stu-id="3c6a8-177">Assign a variable to the cmdlet results for easier manipulation.</span></span>

    ```powershell
    $p=get-proc
    ```

3. <span data-ttu-id="3c6a8-178">Ottenere il numero di processi.</span><span class="sxs-lookup"><span data-stu-id="3c6a8-178">Get the number of processes.</span></span>

    ```powershell
    $p.length
    ```

    <span data-ttu-id="3c6a8-179">Viene visualizzato l'output seguente.</span><span class="sxs-lookup"><span data-stu-id="3c6a8-179">The following output appears.</span></span>

    ```output
    63
    ```

4. <span data-ttu-id="3c6a8-180">Recuperare un processo specifico.</span><span class="sxs-lookup"><span data-stu-id="3c6a8-180">Retrieve a specific process.</span></span>

    ```powershell
    $p[6]
    ```

    <span data-ttu-id="3c6a8-181">Viene visualizzato l'output seguente.</span><span class="sxs-lookup"><span data-stu-id="3c6a8-181">The following output appears.</span></span>

    ```output
    Handles  NPM(K)  PM(K)  WS(K)  VS(M)  CPU(s)  Id    ProcessName
    -------  ------  -----  -----  -----  ------  --    -----------
    1033     3       2400   3336   35     0.53    1588  rundll32
    ```

5. <span data-ttu-id="3c6a8-182">Ottiene l'ora di inizio del processo.</span><span class="sxs-lookup"><span data-stu-id="3c6a8-182">Get the start time of this process.</span></span>

    ```powershell
    $p[6].starttime
    ```

    <span data-ttu-id="3c6a8-183">Viene visualizzato l'output seguente.</span><span class="sxs-lookup"><span data-stu-id="3c6a8-183">The following output appears.</span></span>

    ```output
    Tuesday, July 26, 2005 9:34:15 AM
    ```

    ```powershell
    $p[6].starttime.dayofyear
    ```

    ```output
    207
    ```

6. <span data-ttu-id="3c6a8-184">Ottenere i processi per i quali il numero di handle è maggiore di 500 e ordinare il risultato.</span><span class="sxs-lookup"><span data-stu-id="3c6a8-184">Get the processes for which the handle count is greater than 500, and sort the result.</span></span>

    ```powershell
    $p | Where-Object {$_.HandleCount -gt 500 } | Sort-Object HandleCount
    ```

    <span data-ttu-id="3c6a8-185">Viene visualizzato l'output seguente.</span><span class="sxs-lookup"><span data-stu-id="3c6a8-185">The following output appears.</span></span>

    ```output
    Handles  NPM(K)  PM(K)  WS(K)  VS(M)  CPU(s)  Id   ProcessName
    -------  ------  -----  -----  -----  ------  --   ----------
    568      14      2164   4972   39     5.55    824  svchost
    716       7      2080   5332   28    25.38    468  csrss
    761      21      33060  56608  440  393.56    3300 WINWORD
    791      71      7412   4540   59     3.31    492  winlogon
    ...
    ```

7. <span data-ttu-id="3c6a8-186">Usare il cmdlet `Get-Member` per elencare le proprietà disponibili per ogni processo.</span><span class="sxs-lookup"><span data-stu-id="3c6a8-186">Use the `Get-Member` cmdlet to list the properties available for each process.</span></span>

    ```powershell
    $p | Get-Member -MemberType property
    ```

    ```output
        TypeName: System.Diagnostics.Process
    ```

    <span data-ttu-id="3c6a8-187">Viene visualizzato l'output seguente.</span><span class="sxs-lookup"><span data-stu-id="3c6a8-187">The following output appears.</span></span>

    ```output
    Name                     MemberType Definition
    ----                     ---------- ----------
    BasePriority             Property   System.Int32 BasePriority {get;}
    Container                Property   System.ComponentModel.IContainer Conta...
    EnableRaisingEvents      Property   System.Boolean EnableRaisingEvents {ge...
    ...
    ```

## <a name="see-also"></a><span data-ttu-id="3c6a8-188">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="3c6a8-188">See Also</span></span>

[<span data-ttu-id="3c6a8-189">Creazione di un cmdlet per elaborare l'input della riga di comando</span><span class="sxs-lookup"><span data-stu-id="3c6a8-189">Creating a Cmdlet to Process Command Line Input</span></span>](./adding-parameters-that-process-command-line-input.md)

[<span data-ttu-id="3c6a8-190">Creazione di un cmdlet per elaborare l'input della pipeline</span><span class="sxs-lookup"><span data-stu-id="3c6a8-190">Creating a Cmdlet to Process Pipeline Input</span></span>](./adding-parameters-that-process-pipeline-input.md)

[<span data-ttu-id="3c6a8-191">Come creare un cmdlet di Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="3c6a8-191">How to Create a Windows PowerShell Cmdlet</span></span>](/powershell/scripting/developer/cmdlet/writing-a-windows-powershell-cmdlet)

<span data-ttu-id="3c6a8-192">[Estensione di tipi di oggetti e formattazione](/previous-versions//ms714665(v=vs.85))</span><span class="sxs-lookup"><span data-stu-id="3c6a8-192">[Extending Object Types and Formatting](/previous-versions//ms714665(v=vs.85))</span></span>

<span data-ttu-id="3c6a8-193">[Funzionamento di Windows PowerShell](/previous-versions//ms714658(v=vs.85))</span><span class="sxs-lookup"><span data-stu-id="3c6a8-193">[How Windows PowerShell Works](/previous-versions//ms714658(v=vs.85))</span></span>

<span data-ttu-id="3c6a8-194">[Come registrare cmdlet, provider e applicazioni host](/previous-versions//ms714644(v=vs.85))</span><span class="sxs-lookup"><span data-stu-id="3c6a8-194">[How to Register Cmdlets, Providers, and Host Applications](/previous-versions//ms714644(v=vs.85))</span></span>

<span data-ttu-id="3c6a8-195">[Windows PowerShell Reference](../windows-powershell-reference.md) (Guida di riferimento di PowerShell)</span><span class="sxs-lookup"><span data-stu-id="3c6a8-195">[Windows PowerShell Reference](../windows-powershell-reference.md)</span></span>

[<span data-ttu-id="3c6a8-196">Esempi di cmdlet</span><span class="sxs-lookup"><span data-stu-id="3c6a8-196">Cmdlet Samples</span></span>](./cmdlet-samples.md)
