---
title: Aggiunta del parametro imposta a un Cmdlet | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- parameter sets [PowerShell Programmer's Guide]
ms.assetid: a6131db4-fd6e-45f1-bd47-17e7174afd56
caps.latest.revision: 8
ms.openlocfilehash: 6a3b592c5f85c1f065ad4b5b0290cf44dcef484e
ms.sourcegitcommit: 01b81317029b28dd9b61d167045fd31f1ec7bc06
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/17/2019
ms.locfileid: "65854889"
---
# <a name="adding-parameter-sets-to-a-cmdlet"></a><span data-ttu-id="4170b-102">Aggiunta dei set di parametri a un cmdlet</span><span class="sxs-lookup"><span data-stu-id="4170b-102">Adding Parameter Sets to a Cmdlet</span></span>

## <a name="things-to-know-about-parameter-sets"></a><span data-ttu-id="4170b-103">Informazioni utili sul set di parametri</span><span class="sxs-lookup"><span data-stu-id="4170b-103">Things to Know About Parameter Sets</span></span>

<span data-ttu-id="4170b-104">Windows PowerShell consente di definire un set di parametri di un gruppo di parametri che vengono usati insieme.</span><span class="sxs-lookup"><span data-stu-id="4170b-104">Windows PowerShell defines a parameter set as a group of parameters that operate together.</span></span> <span data-ttu-id="4170b-105">Raggruppando i parametri di un cmdlet, è possibile creare un singolo cmdlet che possono cambiare le funzionalità di base a quale gruppo di parametri specifica l'utente.</span><span class="sxs-lookup"><span data-stu-id="4170b-105">By grouping the parameters of a cmdlet, you can create a single cmdlet that can change its functionality based on what group of parameters the user specifies.</span></span>

<span data-ttu-id="4170b-106">È un esempio di un cmdlet che usa due set di parametri per definire diverse funzionalità di `Get-EventLog` cmdlet fornito da Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="4170b-106">An example of a cmdlet that uses two parameter sets to define different functionalities is the `Get-EventLog` cmdlet that is provided by Windows PowerShell.</span></span> <span data-ttu-id="4170b-107">Questo cmdlet restituisce informazioni diverse, quando l'utente specifica i `List` o `LogName` parametro.</span><span class="sxs-lookup"><span data-stu-id="4170b-107">This cmdlet returns different information when the user specifies the `List` or `LogName` parameter.</span></span> <span data-ttu-id="4170b-108">Se il `LogName` parametro viene specificato, il cmdlet restituisce informazioni sugli eventi in un determinato registro eventi.</span><span class="sxs-lookup"><span data-stu-id="4170b-108">If the `LogName` parameter is specified, the cmdlet returns information about the events in a given event log.</span></span> <span data-ttu-id="4170b-109">Se il `List` parametro viene specificato, il cmdlet restituisce informazioni sul log di file (non le informazioni sull'evento contengono).</span><span class="sxs-lookup"><span data-stu-id="4170b-109">If the `List` parameter is specified, the cmdlet returns information about the log files themselves (not the event information they contain).</span></span> <span data-ttu-id="4170b-110">In questo caso, il `List` e `LogName` parametro identificano due set di parametri separato.</span><span class="sxs-lookup"><span data-stu-id="4170b-110">In this case, the `List` and `LogName` parameters identify two separate parameter sets.</span></span>

<span data-ttu-id="4170b-111">Due aspetti importanti da ricordare riguardo a set di parametri è che il runtime di Windows PowerShell Usa un solo set di parametri per un input specifico e che ogni set di parametri deve contenere almeno un parametro che è univoco per il set di parametri.</span><span class="sxs-lookup"><span data-stu-id="4170b-111">Two important things to remember about parameter sets is that the Windows PowerShell runtime uses only one parameter set for a particular input, and that each parameter set must have at least one parameter that is unique for that parameter set.</span></span>

<span data-ttu-id="4170b-112">Per illustrare questo ultimo punto, questo cmdlet Stop-Process Usa tre set di parametri: `ProcessName`, `ProcessId`, e `InputObject`.</span><span class="sxs-lookup"><span data-stu-id="4170b-112">To illustrate that last point, this Stop-Proc cmdlet uses three parameter sets: `ProcessName`, `ProcessId`, and `InputObject`.</span></span> <span data-ttu-id="4170b-113">Ognuno di questi set di parametri contiene un parametro che non sia in altri set di parametri.</span><span class="sxs-lookup"><span data-stu-id="4170b-113">Each of these parameter sets has one parameter that is not in the other parameter sets.</span></span> <span data-ttu-id="4170b-114">I set di parametri è stato possibile condividere gli altri parametri, ma il cmdlet Usa i parametri univoci `ProcessName`, `ProcessId`, e `InputObject` per identificare quale set di parametri che deve usare il runtime di Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="4170b-114">The parameter sets could share other parameters, but the cmdlet uses the unique parameters `ProcessName`, `ProcessId`, and `InputObject` to identify which set of parameters that the Windows PowerShell runtime should use.</span></span>

## <a name="declaring-the-cmdlet-class"></a><span data-ttu-id="4170b-115">La dichiarazione di classe del Cmdlet</span><span class="sxs-lookup"><span data-stu-id="4170b-115">Declaring the Cmdlet Class</span></span>

<span data-ttu-id="4170b-116">Il primo passaggio nella creazione di cmdlet è sempre il cmdlet di denominazione e la dichiarazione di classe .NET che implementa il cmdlet.</span><span class="sxs-lookup"><span data-stu-id="4170b-116">The first step in cmdlet creation is always naming the cmdlet and declaring the .NET class that implements the cmdlet.</span></span> <span data-ttu-id="4170b-117">Per questo cmdlet, viene utilizzato il verbo di ciclo di vita "Stop", perché il cmdlet arresta i processi di sistema.</span><span class="sxs-lookup"><span data-stu-id="4170b-117">For this cmdlet, the life-cycle verb "Stop" is used because the cmdlet stops system processes.</span></span> <span data-ttu-id="4170b-118">Il nome del sostantivo "Proc" viene usato perché il cmdlet può essere eseguita sui processi.</span><span class="sxs-lookup"><span data-stu-id="4170b-118">The noun name "Proc" is used because the cmdlet works on processes.</span></span> <span data-ttu-id="4170b-119">Nella dichiarazione seguente, si noti che il nome del verbo e sostantivo cmdlet vengono riflesse nel nome di classe del cmdlet.</span><span class="sxs-lookup"><span data-stu-id="4170b-119">In the declaration below, note that the cmdlet verb and noun name are reflected in the name of the cmdlet class.</span></span>

> [!NOTE]
> <span data-ttu-id="4170b-120">Per altre informazioni sui nomi dei verbi approvati di cmdlet, vedere [nomi dei verbi di Cmdlet](./approved-verbs-for-windows-powershell-commands.md).</span><span class="sxs-lookup"><span data-stu-id="4170b-120">For more information about approved cmdlet verb names, see [Cmdlet Verb Names](./approved-verbs-for-windows-powershell-commands.md).</span></span>

<span data-ttu-id="4170b-121">Il codice seguente è la definizione di classe per questo cmdlet Stop-Process.</span><span class="sxs-lookup"><span data-stu-id="4170b-121">The following code is the class definition for this Stop-Proc cmdlet.</span></span>

```csharp
[Cmdlet(VerbsLifecycle.Stop, "Proc",
        DefaultParameterSetName = "ProcessId",
        SupportsShouldProcess = true)]
public class StopProcCommand : PSCmdlet
```

```vb
<Cmdlet(VerbsLifecycle.Stop, "Proc", DefaultParameterSetName:="ProcessId", _
SupportsShouldProcess:=True)> _
Public Class StopProcCommand
    Inherits PSCmdlet
```

## <a name="declaring-the-parameters-of-the-cmdlet"></a><span data-ttu-id="4170b-122">Dichiarando i parametri del Cmdlet</span><span class="sxs-lookup"><span data-stu-id="4170b-122">Declaring the Parameters of the Cmdlet</span></span>

<span data-ttu-id="4170b-123">Questo cmdlet definisce tre parametri necessari come input al cmdlet (questi parametri anche definiscono i set di parametri), nonché una `Force` parametro che gestisce il cmdlet non e un `PassThru` parametro che determina se il cmdlet invia un oggetto di output tramite la pipeline.</span><span class="sxs-lookup"><span data-stu-id="4170b-123">This cmdlet defines three parameters needed as input to the cmdlet (these parameters also define the parameter sets), as well as a `Force` parameter that manages what the cmdlet does and a `PassThru` parameter that determines whether the cmdlet sends an output object through the pipeline.</span></span> <span data-ttu-id="4170b-124">Per impostazione predefinita, questo cmdlet non passare un oggetto tramite la pipeline.</span><span class="sxs-lookup"><span data-stu-id="4170b-124">By default, this cmdlet does not pass an object through the pipeline.</span></span> <span data-ttu-id="4170b-125">Per altre informazioni su questi ultimi due parametri, vedere [creazione di un Cmdlet che modifichi il sistema](./creating-a-cmdlet-that-modifies-the-system.md).</span><span class="sxs-lookup"><span data-stu-id="4170b-125">For more information about these last two parameters, see [Creating a Cmdlet that Modifies the System](./creating-a-cmdlet-that-modifies-the-system.md).</span></span>

### <a name="declaring-the-name-parameter"></a><span data-ttu-id="4170b-126">Dichiarare il parametro Name</span><span class="sxs-lookup"><span data-stu-id="4170b-126">Declaring the Name Parameter</span></span>

<span data-ttu-id="4170b-127">Questo parametro input consente all'utente di specificare i nomi dei processi da arrestare.</span><span class="sxs-lookup"><span data-stu-id="4170b-127">This input parameter allows the user to specify the names of the processes to be stopped.</span></span> <span data-ttu-id="4170b-128">Si noti che il `ParameterSetName` parola chiave dell'attributo di [System.Management.Automation.Parameterattribute](/dotnet/api/System.Management.Automation.ParameterAttribute) attributo specifica il `ProcessName` di impostazione parametro per questo parametro.</span><span class="sxs-lookup"><span data-stu-id="4170b-128">Note that the `ParameterSetName` attribute keyword of the [System.Management.Automation.Parameterattribute](/dotnet/api/System.Management.Automation.ParameterAttribute) attribute specifies the `ProcessName` parameter set for this parameter.</span></span>

[!code-csharp[StopProcessSample04.cs](../../powershell-sdk-samples/SDK-2.0/csharp/StopProcessSample04/StopProcessSample04.cs#L44-L58 "StopProcessSample04.cs")]

```vb
<Parameter(Position:=0, ParameterSetName:="ProcessName", _
Mandatory:=True, _
ValueFromPipeline:=True, ValueFromPipelineByPropertyName:=True, _
HelpMessage:="The name of one or more processes to stop. " & _
    "Wildcards are permitted."), [Alias]("ProcessName")> _
Public Property Name() As String()
    Get
        Return processNames
    End Get
    Set(ByVal value As String())
        processNames = value
    End Set
End Property

Private processNames() As String
```

<span data-ttu-id="4170b-129">Si noti anche che l'alias "ProcessName" viene assegnato a questo parametro.</span><span class="sxs-lookup"><span data-stu-id="4170b-129">Note also that the alias "ProcessName" is given to this parameter.</span></span>

### <a name="declaring-the-id-parameter"></a><span data-ttu-id="4170b-130">Dichiarare il parametro Id</span><span class="sxs-lookup"><span data-stu-id="4170b-130">Declaring the Id Parameter</span></span>

<span data-ttu-id="4170b-131">Questo parametro input consente all'utente di specificare gli identificatori dei processi da arrestare.</span><span class="sxs-lookup"><span data-stu-id="4170b-131">This input parameter allows the user to specify the identifiers of the processes to be stopped.</span></span> <span data-ttu-id="4170b-132">Si noti che il `ParameterSetName` parola chiave dell'attributo di [System.Management.Automation.Parameterattribute](/dotnet/api/System.Management.Automation.ParameterAttribute) attributo specifica il `ProcessId` set di parametri.</span><span class="sxs-lookup"><span data-stu-id="4170b-132">Note that the `ParameterSetName` attribute keyword of the [System.Management.Automation.Parameterattribute](/dotnet/api/System.Management.Automation.ParameterAttribute) attribute specifies the `ProcessId` parameter set.</span></span>

```csharp
[Parameter(
           ParameterSetName = "ProcessId",
           Mandatory = true,
           ValueFromPipelineByPropertyName = true,
           ValueFromPipeline = true
)]
[Alias("ProcessId")]
public int[] Id
{
  get { return processIds; }
  set { processIds = value; }
}
private int[] processIds;
```

```vb
<Parameter(ParameterSetName:="ProcessId", _
Mandatory:=True, _
ValueFromPipelineByPropertyName:=True, _
ValueFromPipeline:=True), [Alias]("ProcessId")> _
Public Property Id() As Integer()
    Get
        Return processIds
    End Get
    Set(ByVal value As Integer())
        processIds = value
    End Set
End Property
Private processIds() As Integer
```

<span data-ttu-id="4170b-133">Si noti anche che l'alias "ProcessId" viene assegnato a questo parametro.</span><span class="sxs-lookup"><span data-stu-id="4170b-133">Note also that the alias "ProcessId" is given to this parameter.</span></span>

### <a name="declaring-the-inputobject-parameter"></a><span data-ttu-id="4170b-134">Il parametro InputObject di dichiarazione</span><span class="sxs-lookup"><span data-stu-id="4170b-134">Declaring the InputObject Parameter</span></span>

<span data-ttu-id="4170b-135">Questo parametro input consente all'utente di specificare un oggetto di input che contiene informazioni sui processi da arrestare.</span><span class="sxs-lookup"><span data-stu-id="4170b-135">This input parameter allows the user to specify an input object that contains information about the processes to be stopped.</span></span> <span data-ttu-id="4170b-136">Si noti che il `ParameterSetName` parola chiave dell'attributo di [System.Management.Automation.Parameterattribute](/dotnet/api/System.Management.Automation.ParameterAttribute) attributo specifica il `InputObject` di impostazione parametro per questo parametro.</span><span class="sxs-lookup"><span data-stu-id="4170b-136">Note that the `ParameterSetName` attribute keyword of the [System.Management.Automation.Parameterattribute](/dotnet/api/System.Management.Automation.ParameterAttribute) attribute specifies the `InputObject` parameter set for this parameter.</span></span>

```csharp
[Parameter(
           ParameterSetName = "InputObject",
           Mandatory = true,
           ValueFromPipeline = true)]
public Process[] InputObject
{
  get { return inputObject; }
  set { inputObject = value; }
}
private Process[] inputObject;
```

```vb
<Parameter(ParameterSetName:="InputObject", _
Mandatory:=True, ValueFromPipeline:=True)> _
Public Property InputObject() As Process()
    Get
        Return myInputObject
    End Get
    Set(ByVal value As Process())
        myInputObject = value
    End Set
End Property
Private myInputObject() As Process
```

<span data-ttu-id="4170b-137">Si noti anche che questo parametro non ha alias.</span><span class="sxs-lookup"><span data-stu-id="4170b-137">Note also that this parameter has no alias.</span></span>

### <a name="declaring-parameters-in-multiple-parameter-sets"></a><span data-ttu-id="4170b-138">Dichiarazione dei parametri in più set di parametri</span><span class="sxs-lookup"><span data-stu-id="4170b-138">Declaring Parameters in Multiple Parameter Sets</span></span>

<span data-ttu-id="4170b-139">Anche se è necessario un parametro univoco per ogni set di parametri, i parametri possono appartenere a più di un set di parametri.</span><span class="sxs-lookup"><span data-stu-id="4170b-139">Although there must be a unique parameter for each parameter set, parameters can belong to more than one parameter set.</span></span> <span data-ttu-id="4170b-140">In questi casi, assegnare al parametro condiviso una [System.Management.Automation.Parameterattribute](/dotnet/api/System.Management.Automation.ParameterAttribute) dichiarazione di attributo per ogni set a cui il parametro appartiene.</span><span class="sxs-lookup"><span data-stu-id="4170b-140">In these cases, give the shared parameter a [System.Management.Automation.Parameterattribute](/dotnet/api/System.Management.Automation.ParameterAttribute) attribute declaration for each set to which that the parameter belongs.</span></span> <span data-ttu-id="4170b-141">Se un parametro in tutti i set di parametri, solo necessario dichiarare l'attributo parameter una sola volta e non è necessario specificare che il parametro del set di nome.</span><span class="sxs-lookup"><span data-stu-id="4170b-141">If a parameter is in all parameter sets, you only have to declare the parameter attribute once and do not need to specify the parameter set name.</span></span>

## <a name="overriding-an-input-processing-method"></a><span data-ttu-id="4170b-142">Si esegue l'override di un metodo di elaborazione dell'Input</span><span class="sxs-lookup"><span data-stu-id="4170b-142">Overriding an Input Processing Method</span></span>

<span data-ttu-id="4170b-143">Ogni cmdlet è necessario eseguire l'override di un metodo di elaborazione dell'input, in genere si tratterà il [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) (metodo).</span><span class="sxs-lookup"><span data-stu-id="4170b-143">Every cmdlet must override an input processing method, most often this will be the [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) method.</span></span> <span data-ttu-id="4170b-144">In questo cmdlet, il [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) è sottoposto a override in modo che il cmdlet può elaborare qualsiasi numero di processi.</span><span class="sxs-lookup"><span data-stu-id="4170b-144">In this cmdlet, the [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) method is overridden so that the cmdlet can process any number of processes.</span></span> <span data-ttu-id="4170b-145">Contiene un'istruzione Select che chiama un metodo diverso basato su quale set di parametri l'utente ha specificato.</span><span class="sxs-lookup"><span data-stu-id="4170b-145">It contains a Select statement that calls a different method based on which parameter set the user has specified.</span></span>

```csharp
protected override void ProcessRecord()
{
  switch (ParameterSetName)
  {
    case "ProcessName":
         ProcessByName();
         break;

    case "ProcessId":
         ProcessById();
         break;

    case "InputObject":
         foreach (Process process in inputObject)
         {
           SafeStopProcess(process);
         }
         break;

    default:
         throw new ArgumentException("Bad ParameterSet Name");
  } // switch (ParameterSetName...
} // ProcessRecord
```

```vb
Protected Overrides Sub ProcessRecord()
    Select Case ParameterSetName
        Case "ProcessName"
            ProcessByName()

        Case "ProcessId"
            ProcessById()

        Case "InputObject"
            Dim process As Process
            For Each process In myInputObject
                SafeStopProcess(process)
            Next process

        Case Else
            Throw New ArgumentException("Bad ParameterSet Name")
    End Select

End Sub 'ProcessRecord ' ProcessRecord
```

<span data-ttu-id="4170b-146">I metodi Helper chiamati dall'istruzione Select non sono descritti di seguito, ma è possibile visualizzare la relativa implementazione nell'esempio di codice completo nella sezione successiva.</span><span class="sxs-lookup"><span data-stu-id="4170b-146">The Helper methods called by the Select statement are not described here, but you can see their implementation in the complete code sample in the next section.</span></span>

## <a name="code-sample"></a><span data-ttu-id="4170b-147">Esempio di codice</span><span class="sxs-lookup"><span data-stu-id="4170b-147">Code Sample</span></span>

<span data-ttu-id="4170b-148">Per l'intero C# esempi di codice, vedere [esempio StopProcessSample04](./stopprocesssample04-sample.md).</span><span class="sxs-lookup"><span data-stu-id="4170b-148">For the complete C# sample code, see [StopProcessSample04 Sample](./stopprocesssample04-sample.md).</span></span>

## <a name="defining-object-types-and-formatting"></a><span data-ttu-id="4170b-149">Definizione di tipi di oggetto e formattazione</span><span class="sxs-lookup"><span data-stu-id="4170b-149">Defining Object Types and Formatting</span></span>

<span data-ttu-id="4170b-150">Windows PowerShell passa informazioni tra i cmdlet con gli oggetti .NET.</span><span class="sxs-lookup"><span data-stu-id="4170b-150">Windows PowerShell passes information between cmdlets using .NET objects.</span></span> <span data-ttu-id="4170b-151">Di conseguenza, potrebbe essere necessario definire un proprio tipo di un cmdlet o il cmdlet potrebbe essere necessario estendere un tipo esistente fornito da un altro cmdlet.</span><span class="sxs-lookup"><span data-stu-id="4170b-151">Consequently, a cmdlet might need to define its own type, or the cmdlet might need to extend an existing type provided by another cmdlet.</span></span> <span data-ttu-id="4170b-152">Per altre informazioni sulla definizione di nuovi tipi o estendere i tipi esistenti, vedere [estendendo i tipi di oggetto e formattazione](http://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351).</span><span class="sxs-lookup"><span data-stu-id="4170b-152">For more information about defining new types or extending existing types, see [Extending Object Types and Formatting](http://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351).</span></span>

## <a name="building-the-cmdlet"></a><span data-ttu-id="4170b-153">Creazione di Cmdlet</span><span class="sxs-lookup"><span data-stu-id="4170b-153">Building the Cmdlet</span></span>

<span data-ttu-id="4170b-154">Dopo l'implementazione di un cmdlet, è necessario registrarlo con Windows PowerShell tramite uno snap-in Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="4170b-154">After implementing a cmdlet, you must register it with Windows PowerShell through a Windows PowerShell snap-in.</span></span> <span data-ttu-id="4170b-155">Per altre informazioni sulla registrazione dei cmdlet, vedere [come registrare i cmdlet, provider e applicazioni Host](http://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c).</span><span class="sxs-lookup"><span data-stu-id="4170b-155">For more information about registering cmdlets, see [How to Register Cmdlets, Providers, and Host Applications](http://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c).</span></span>

## <a name="testing-the-cmdlet"></a><span data-ttu-id="4170b-156">Il Cmdlet di test</span><span class="sxs-lookup"><span data-stu-id="4170b-156">Testing the Cmdlet</span></span>

<span data-ttu-id="4170b-157">Quando il cmdlet è stato registrato con Windows PowerShell, è possibile testarlo eseguendolo dalla riga di comando.</span><span class="sxs-lookup"><span data-stu-id="4170b-157">When your cmdlet has been registered with Windows PowerShell, test it by running it on the command line.</span></span> <span data-ttu-id="4170b-158">Ecco alcuni test che illustrano come il `ProcessId` e `InputObject` parametri possono essere utilizzati per i set di parametri per arrestare un processo di test.</span><span class="sxs-lookup"><span data-stu-id="4170b-158">Here are some tests that show how the `ProcessId` and `InputObject` parameters can be used to test their parameter sets to stop a process.</span></span>

- <span data-ttu-id="4170b-159">Con Windows PowerShell avviata, eseguire il cmdlet Stop-Process con il `ProcessId` parametro impostato su arrestare un processo in base al relativo identificatore.</span><span class="sxs-lookup"><span data-stu-id="4170b-159">With Windows PowerShell started, run the Stop-Proc cmdlet with the `ProcessId` parameter set to stop a process based on its identifier.</span></span> <span data-ttu-id="4170b-160">In questo caso, Usa il cmdlet di `ProcessId` parametro impostato per arrestare il processo.</span><span class="sxs-lookup"><span data-stu-id="4170b-160">In this case, the cmdlet is using the `ProcessId` parameter set to stop the process.</span></span>

    ```
    PS> stop-proc -Id 444
    Confirm
    Are you sure you want to perform this action?
    Performing operation "stop-proc" on Target "notepad (444)".
    [Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"): Y
    ```

- <span data-ttu-id="4170b-161">Con Windows PowerShell avviata, eseguire il cmdlet Stop-Process con il `InputObject` parametro è impostato per arrestare i processi per l'oggetto di blocco note recuperato tramite il `Get-Process` comando.</span><span class="sxs-lookup"><span data-stu-id="4170b-161">With Windows PowerShell started, run the Stop-Proc cmdlet with the `InputObject` parameter set to stop processes on the Notepad object retrieved by the `Get-Process` command.</span></span>

    ```
    PS> get-process notepad | stop-proc
    Confirm
    Are you sure you want to perform this action?
    Performing operation "stop-proc" on Target "notepad (444)".
    [Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"): N
    ```

## <a name="see-also"></a><span data-ttu-id="4170b-162">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="4170b-162">See Also</span></span>

[<span data-ttu-id="4170b-163">Creazione di un Cmdlet che modifichi il sistema</span><span class="sxs-lookup"><span data-stu-id="4170b-163">Creating a Cmdlet that Modifies the System</span></span>](./creating-a-cmdlet-that-modifies-the-system.md)

[<span data-ttu-id="4170b-164">Come creare un Cmdlet di Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="4170b-164">How to Create a Windows PowerShell Cmdlet</span></span>](http://msdn.microsoft.com/en-us/0d721742-c849-4d0d-964f-78ddd9cd258c)

[<span data-ttu-id="4170b-165">Estensione di tipi di oggetto e la formattazione</span><span class="sxs-lookup"><span data-stu-id="4170b-165">Extending Object Types and Formatting</span></span>](http://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351)

[<span data-ttu-id="4170b-166">Come registrare i cmdlet, provider e applicazioni Host</span><span class="sxs-lookup"><span data-stu-id="4170b-166">How to Register Cmdlets, Providers, and Host Applications</span></span>](http://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c)

[<span data-ttu-id="4170b-167">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="4170b-167">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)
