---
title: Aggiunta di set di parametri a un cmdlet | Microsoft Docs
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
ms.openlocfilehash: 59db96cf03ff7086e8c89fb45bc96fd805078ac8
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/15/2019
ms.locfileid: "72364590"
---
# <a name="adding-parameter-sets-to-a-cmdlet"></a><span data-ttu-id="b3611-102">Aggiunta dei set di parametri a un cmdlet</span><span class="sxs-lookup"><span data-stu-id="b3611-102">Adding Parameter Sets to a Cmdlet</span></span>

## <a name="things-to-know-about-parameter-sets"></a><span data-ttu-id="b3611-103">Informazioni importanti sui set di parametri</span><span class="sxs-lookup"><span data-stu-id="b3611-103">Things to Know About Parameter Sets</span></span>

<span data-ttu-id="b3611-104">Windows PowerShell definisce un set di parametri come gruppo di parametri che operano insieme.</span><span class="sxs-lookup"><span data-stu-id="b3611-104">Windows PowerShell defines a parameter set as a group of parameters that operate together.</span></span> <span data-ttu-id="b3611-105">Raggruppando i parametri di un cmdlet, è possibile creare un singolo cmdlet in grado di modificarne le funzionalità in base al gruppo di parametri specificato dall'utente.</span><span class="sxs-lookup"><span data-stu-id="b3611-105">By grouping the parameters of a cmdlet, you can create a single cmdlet that can change its functionality based on what group of parameters the user specifies.</span></span>

<span data-ttu-id="b3611-106">Un esempio di cmdlet che usa due set di parametri per definire funzionalità diverse è il cmdlet `Get-EventLog` fornito da Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="b3611-106">An example of a cmdlet that uses two parameter sets to define different functionalities is the `Get-EventLog` cmdlet that is provided by Windows PowerShell.</span></span> <span data-ttu-id="b3611-107">Questo cmdlet restituisce informazioni diverse quando l'utente specifica il parametro `List` o `LogName`.</span><span class="sxs-lookup"><span data-stu-id="b3611-107">This cmdlet returns different information when the user specifies the `List` or `LogName` parameter.</span></span> <span data-ttu-id="b3611-108">Se viene specificato il parametro `LogName`, il cmdlet restituisce informazioni sugli eventi in un determinato registro eventi.</span><span class="sxs-lookup"><span data-stu-id="b3611-108">If the `LogName` parameter is specified, the cmdlet returns information about the events in a given event log.</span></span> <span data-ttu-id="b3611-109">Se viene specificato il parametro `List`, il cmdlet restituisce le informazioni sui file di log stessi (non le informazioni sull'evento che contengono).</span><span class="sxs-lookup"><span data-stu-id="b3611-109">If the `List` parameter is specified, the cmdlet returns information about the log files themselves (not the event information they contain).</span></span> <span data-ttu-id="b3611-110">In questo caso, i parametri `List` e `LogName` identificano due set di parametri distinti.</span><span class="sxs-lookup"><span data-stu-id="b3611-110">In this case, the `List` and `LogName` parameters identify two separate parameter sets.</span></span>

<span data-ttu-id="b3611-111">Due aspetti importanti da ricordare per i set di parametri sono che il runtime di Windows PowerShell usa un solo set di parametri per un input specifico e che ogni set di parametri deve avere almeno un parametro univoco per il set di parametri.</span><span class="sxs-lookup"><span data-stu-id="b3611-111">Two important things to remember about parameter sets is that the Windows PowerShell runtime uses only one parameter set for a particular input, and that each parameter set must have at least one parameter that is unique for that parameter set.</span></span>

<span data-ttu-id="b3611-112">Per illustrare l'ultimo punto, questo cmdlet Stop-proc usa tre set di parametri: `ProcessName`, `ProcessId` e `InputObject`.</span><span class="sxs-lookup"><span data-stu-id="b3611-112">To illustrate that last point, this Stop-Proc cmdlet uses three parameter sets: `ProcessName`, `ProcessId`, and `InputObject`.</span></span> <span data-ttu-id="b3611-113">Ognuno di questi set di parametri ha un parametro che non si trova negli altri set di parametri.</span><span class="sxs-lookup"><span data-stu-id="b3611-113">Each of these parameter sets has one parameter that is not in the other parameter sets.</span></span> <span data-ttu-id="b3611-114">I set di parametri possono condividere altri parametri, ma il cmdlet usa i parametri univoci `ProcessName`, `ProcessId` e `InputObject` per identificare il set di parametri che deve essere usato dal runtime di Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="b3611-114">The parameter sets could share other parameters, but the cmdlet uses the unique parameters `ProcessName`, `ProcessId`, and `InputObject` to identify which set of parameters that the Windows PowerShell runtime should use.</span></span>

## <a name="declaring-the-cmdlet-class"></a><span data-ttu-id="b3611-115">Dichiarazione della classe cmdlet</span><span class="sxs-lookup"><span data-stu-id="b3611-115">Declaring the Cmdlet Class</span></span>

<span data-ttu-id="b3611-116">Il primo passaggio nella creazione di cmdlet è sempre il nome del cmdlet e la dichiarazione della classe .NET che implementa il cmdlet.</span><span class="sxs-lookup"><span data-stu-id="b3611-116">The first step in cmdlet creation is always naming the cmdlet and declaring the .NET class that implements the cmdlet.</span></span> <span data-ttu-id="b3611-117">Per questo cmdlet viene usato il verbo "Stop" del ciclo di vita perché il cmdlet interrompe i processi di sistema.</span><span class="sxs-lookup"><span data-stu-id="b3611-117">For this cmdlet, the life-cycle verb "Stop" is used because the cmdlet stops system processes.</span></span> <span data-ttu-id="b3611-118">Il nome del sostantivo "proc" viene usato perché il cmdlet funziona nei processi.</span><span class="sxs-lookup"><span data-stu-id="b3611-118">The noun name "Proc" is used because the cmdlet works on processes.</span></span> <span data-ttu-id="b3611-119">Nella dichiarazione seguente si noti che il verbo del cmdlet e il nome del sostantivo sono riflessi nel nome della classe cmdlet.</span><span class="sxs-lookup"><span data-stu-id="b3611-119">In the declaration below, note that the cmdlet verb and noun name are reflected in the name of the cmdlet class.</span></span>

> [!NOTE]
> <span data-ttu-id="b3611-120">Per ulteriori informazioni sui nomi dei verbi di cmdlet approvati, vedere [nomi dei verbi di cmdlet](./approved-verbs-for-windows-powershell-commands.md).</span><span class="sxs-lookup"><span data-stu-id="b3611-120">For more information about approved cmdlet verb names, see [Cmdlet Verb Names](./approved-verbs-for-windows-powershell-commands.md).</span></span>

<span data-ttu-id="b3611-121">Il codice seguente è la definizione di classe per questo cmdlet Stop-proc.</span><span class="sxs-lookup"><span data-stu-id="b3611-121">The following code is the class definition for this Stop-Proc cmdlet.</span></span>

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

## <a name="declaring-the-parameters-of-the-cmdlet"></a><span data-ttu-id="b3611-122">Dichiarazione dei parametri del cmdlet</span><span class="sxs-lookup"><span data-stu-id="b3611-122">Declaring the Parameters of the Cmdlet</span></span>

<span data-ttu-id="b3611-123">Questo cmdlet definisce tre parametri necessari come input per il cmdlet (questi parametri definiscono anche i set di parametri), oltre a un parametro `Force` che gestisce le operazioni del cmdlet e un parametro `PassThru` che determina se il cmdlet invia un oggetto di output tramite la pipeline.</span><span class="sxs-lookup"><span data-stu-id="b3611-123">This cmdlet defines three parameters needed as input to the cmdlet (these parameters also define the parameter sets), as well as a `Force` parameter that manages what the cmdlet does and a `PassThru` parameter that determines whether the cmdlet sends an output object through the pipeline.</span></span> <span data-ttu-id="b3611-124">Per impostazione predefinita, questo cmdlet non passa un oggetto tramite la pipeline.</span><span class="sxs-lookup"><span data-stu-id="b3611-124">By default, this cmdlet does not pass an object through the pipeline.</span></span> <span data-ttu-id="b3611-125">Per ulteriori informazioni su questi ultimi due parametri, vedere [creazione di un cmdlet che modifichi il sistema](./creating-a-cmdlet-that-modifies-the-system.md).</span><span class="sxs-lookup"><span data-stu-id="b3611-125">For more information about these last two parameters, see [Creating a Cmdlet that Modifies the System](./creating-a-cmdlet-that-modifies-the-system.md).</span></span>

### <a name="declaring-the-name-parameter"></a><span data-ttu-id="b3611-126">Dichiarazione del parametro Name</span><span class="sxs-lookup"><span data-stu-id="b3611-126">Declaring the Name Parameter</span></span>

<span data-ttu-id="b3611-127">Questo parametro di input consente all'utente di specificare i nomi dei processi da arrestare.</span><span class="sxs-lookup"><span data-stu-id="b3611-127">This input parameter allows the user to specify the names of the processes to be stopped.</span></span> <span data-ttu-id="b3611-128">Si noti che la parola chiave dell'attributo `ParameterSetName` dell'attributo [System. Management. Automation. ParameterAttribute](/dotnet/api/System.Management.Automation.ParameterAttribute) specifica il set di parametri `ProcessName` per questo parametro.</span><span class="sxs-lookup"><span data-stu-id="b3611-128">Note that the `ParameterSetName` attribute keyword of the [System.Management.Automation.Parameterattribute](/dotnet/api/System.Management.Automation.ParameterAttribute) attribute specifies the `ProcessName` parameter set for this parameter.</span></span>

[!code-csharp[StopProcessSample04.cs](../../../../powershell-sdk-samples/SDK-2.0/csharp/StopProcessSample04/StopProcessSample04.cs#L44-L58 "StopProcessSample04.cs")]

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

<span data-ttu-id="b3611-129">Si noti anche che l'alias "ProcessName" è assegnato a questo parametro.</span><span class="sxs-lookup"><span data-stu-id="b3611-129">Note also that the alias "ProcessName" is given to this parameter.</span></span>

### <a name="declaring-the-id-parameter"></a><span data-ttu-id="b3611-130">Dichiarazione del parametro ID</span><span class="sxs-lookup"><span data-stu-id="b3611-130">Declaring the Id Parameter</span></span>

<span data-ttu-id="b3611-131">Questo parametro di input consente all'utente di specificare gli identificatori dei processi da arrestare.</span><span class="sxs-lookup"><span data-stu-id="b3611-131">This input parameter allows the user to specify the identifiers of the processes to be stopped.</span></span> <span data-ttu-id="b3611-132">Si noti che la parola chiave dell'attributo `ParameterSetName` dell'attributo [System. Management. Automation. ParameterAttribute](/dotnet/api/System.Management.Automation.ParameterAttribute) specifica il set di parametri `ProcessId`.</span><span class="sxs-lookup"><span data-stu-id="b3611-132">Note that the `ParameterSetName` attribute keyword of the [System.Management.Automation.Parameterattribute](/dotnet/api/System.Management.Automation.ParameterAttribute) attribute specifies the `ProcessId` parameter set.</span></span>

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

<span data-ttu-id="b3611-133">Si noti anche che l'alias "ProcessID" è assegnato a questo parametro.</span><span class="sxs-lookup"><span data-stu-id="b3611-133">Note also that the alias "ProcessId" is given to this parameter.</span></span>

### <a name="declaring-the-inputobject-parameter"></a><span data-ttu-id="b3611-134">Dichiarazione del parametro InputObject</span><span class="sxs-lookup"><span data-stu-id="b3611-134">Declaring the InputObject Parameter</span></span>

<span data-ttu-id="b3611-135">Questo parametro di input consente all'utente di specificare un oggetto di input che contiene informazioni sui processi da arrestare.</span><span class="sxs-lookup"><span data-stu-id="b3611-135">This input parameter allows the user to specify an input object that contains information about the processes to be stopped.</span></span> <span data-ttu-id="b3611-136">Si noti che la parola chiave dell'attributo `ParameterSetName` dell'attributo [System. Management. Automation. ParameterAttribute](/dotnet/api/System.Management.Automation.ParameterAttribute) specifica il set di parametri `InputObject` per questo parametro.</span><span class="sxs-lookup"><span data-stu-id="b3611-136">Note that the `ParameterSetName` attribute keyword of the [System.Management.Automation.Parameterattribute](/dotnet/api/System.Management.Automation.ParameterAttribute) attribute specifies the `InputObject` parameter set for this parameter.</span></span>

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

<span data-ttu-id="b3611-137">Si noti inoltre che questo parametro non ha alias.</span><span class="sxs-lookup"><span data-stu-id="b3611-137">Note also that this parameter has no alias.</span></span>

### <a name="declaring-parameters-in-multiple-parameter-sets"></a><span data-ttu-id="b3611-138">Dichiarazione di parametri in più set di parametri</span><span class="sxs-lookup"><span data-stu-id="b3611-138">Declaring Parameters in Multiple Parameter Sets</span></span>

<span data-ttu-id="b3611-139">Sebbene sia necessario un parametro univoco per ogni set di parametri, i parametri possono appartenere a più di un set di parametri.</span><span class="sxs-lookup"><span data-stu-id="b3611-139">Although there must be a unique parameter for each parameter set, parameters can belong to more than one parameter set.</span></span> <span data-ttu-id="b3611-140">In questi casi, assegnare al parametro Shared una dichiarazione di attributo [System. Management. Automation. ParameterAttribute](/dotnet/api/System.Management.Automation.ParameterAttribute) per ogni set a cui appartiene il parametro.</span><span class="sxs-lookup"><span data-stu-id="b3611-140">In these cases, give the shared parameter a [System.Management.Automation.Parameterattribute](/dotnet/api/System.Management.Automation.ParameterAttribute) attribute declaration for each set to which that the parameter belongs.</span></span> <span data-ttu-id="b3611-141">Se un parametro è presente in tutti i set di parametri, è necessario dichiarare l'attributo del parametro una sola volta e non è necessario specificare il nome del set di parametri.</span><span class="sxs-lookup"><span data-stu-id="b3611-141">If a parameter is in all parameter sets, you only have to declare the parameter attribute once and do not need to specify the parameter set name.</span></span>

## <a name="overriding-an-input-processing-method"></a><span data-ttu-id="b3611-142">Override di un metodo di elaborazione dell'input</span><span class="sxs-lookup"><span data-stu-id="b3611-142">Overriding an Input Processing Method</span></span>

<span data-ttu-id="b3611-143">Ogni cmdlet deve eseguire l'override di un metodo di elaborazione dell'input, più spesso questo sarà il metodo [System. Management. Automation. cmdlet. ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) .</span><span class="sxs-lookup"><span data-stu-id="b3611-143">Every cmdlet must override an input processing method, most often this will be the [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) method.</span></span> <span data-ttu-id="b3611-144">In questo cmdlet viene eseguito l'override del metodo [System. Management. Automation. cmdlet. ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) in modo che il cmdlet possa elaborare un numero qualsiasi di processi.</span><span class="sxs-lookup"><span data-stu-id="b3611-144">In this cmdlet, the [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) method is overridden so that the cmdlet can process any number of processes.</span></span> <span data-ttu-id="b3611-145">Contiene un'istruzione SELECT che chiama un metodo diverso in base al set di parametri specificato dall'utente.</span><span class="sxs-lookup"><span data-stu-id="b3611-145">It contains a Select statement that calls a different method based on which parameter set the user has specified.</span></span>

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

<span data-ttu-id="b3611-146">I metodi di supporto chiamati dall'istruzione SELECT non sono descritti qui, ma è possibile visualizzarne l'implementazione nell'esempio di codice completo nella sezione successiva.</span><span class="sxs-lookup"><span data-stu-id="b3611-146">The Helper methods called by the Select statement are not described here, but you can see their implementation in the complete code sample in the next section.</span></span>

## <a name="code-sample"></a><span data-ttu-id="b3611-147">Esempio di codice</span><span class="sxs-lookup"><span data-stu-id="b3611-147">Code Sample</span></span>

<span data-ttu-id="b3611-148">Per il codice C# di esempio completo, vedere l' [esempio StopProcessSample04](./stopprocesssample04-sample.md).</span><span class="sxs-lookup"><span data-stu-id="b3611-148">For the complete C# sample code, see [StopProcessSample04 Sample](./stopprocesssample04-sample.md).</span></span>

## <a name="defining-object-types-and-formatting"></a><span data-ttu-id="b3611-149">Definizione di tipi di oggetti e formattazione</span><span class="sxs-lookup"><span data-stu-id="b3611-149">Defining Object Types and Formatting</span></span>

<span data-ttu-id="b3611-150">Windows PowerShell passa le informazioni tra i cmdlet usando gli oggetti .NET.</span><span class="sxs-lookup"><span data-stu-id="b3611-150">Windows PowerShell passes information between cmdlets using .NET objects.</span></span> <span data-ttu-id="b3611-151">Di conseguenza, un cmdlet potrebbe dover definire il proprio tipo oppure il cmdlet deve estendere un tipo esistente fornito da un altro cmdlet.</span><span class="sxs-lookup"><span data-stu-id="b3611-151">Consequently, a cmdlet might need to define its own type, or the cmdlet might need to extend an existing type provided by another cmdlet.</span></span> <span data-ttu-id="b3611-152">Per ulteriori informazioni sulla definizione di nuovi tipi o sull'estensione di tipi esistenti, vedere [estensione di tipi di oggetti e formattazione](/previous-versions//ms714665(v=vs.85)).</span><span class="sxs-lookup"><span data-stu-id="b3611-152">For more information about defining new types or extending existing types, see [Extending Object Types and Formatting](/previous-versions//ms714665(v=vs.85)).</span></span>

## <a name="building-the-cmdlet"></a><span data-ttu-id="b3611-153">Compilazione del cmdlet</span><span class="sxs-lookup"><span data-stu-id="b3611-153">Building the Cmdlet</span></span>

<span data-ttu-id="b3611-154">Dopo l'implementazione di un cmdlet, è necessario registrarlo con Windows PowerShell tramite uno snap-in di Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="b3611-154">After implementing a cmdlet, you must register it with Windows PowerShell through a Windows PowerShell snap-in.</span></span> <span data-ttu-id="b3611-155">Per ulteriori informazioni sulla registrazione dei cmdlet, vedere [come registrare i cmdlet, i provider e le applicazioni host](/previous-versions//ms714644(v=vs.85)).</span><span class="sxs-lookup"><span data-stu-id="b3611-155">For more information about registering cmdlets, see [How to Register Cmdlets, Providers, and Host Applications](/previous-versions//ms714644(v=vs.85)).</span></span>

## <a name="testing-the-cmdlet"></a><span data-ttu-id="b3611-156">Test del cmdlet</span><span class="sxs-lookup"><span data-stu-id="b3611-156">Testing the Cmdlet</span></span>

<span data-ttu-id="b3611-157">Quando il cmdlet è stato registrato con Windows PowerShell, testarlo eseguendolo nella riga di comando.</span><span class="sxs-lookup"><span data-stu-id="b3611-157">When your cmdlet has been registered with Windows PowerShell, test it by running it on the command line.</span></span> <span data-ttu-id="b3611-158">Ecco alcuni test che illustrano come i parametri `ProcessId` e `InputObject` possono essere usati per testare i set di parametri per arrestare un processo.</span><span class="sxs-lookup"><span data-stu-id="b3611-158">Here are some tests that show how the `ProcessId` and `InputObject` parameters can be used to test their parameter sets to stop a process.</span></span>

- <span data-ttu-id="b3611-159">Con Windows PowerShell avviato, eseguire il cmdlet Stop-proc con il set di parametri `ProcessId` per arrestare un processo in base al relativo identificatore.</span><span class="sxs-lookup"><span data-stu-id="b3611-159">With Windows PowerShell started, run the Stop-Proc cmdlet with the `ProcessId` parameter set to stop a process based on its identifier.</span></span> <span data-ttu-id="b3611-160">In questo caso, il cmdlet usa il set di parametri `ProcessId` per arrestare il processo.</span><span class="sxs-lookup"><span data-stu-id="b3611-160">In this case, the cmdlet is using the `ProcessId` parameter set to stop the process.</span></span>

    ```
    PS> stop-proc -Id 444
    Confirm
    Are you sure you want to perform this action?
    Performing operation "stop-proc" on Target "notepad (444)".
    [Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"): Y
    ```

- <span data-ttu-id="b3611-161">Con Windows PowerShell avviato, eseguire il cmdlet Stop-proc con il set di parametri `InputObject` per arrestare i processi nell'oggetto blocco note recuperato dal comando `Get-Process`.</span><span class="sxs-lookup"><span data-stu-id="b3611-161">With Windows PowerShell started, run the Stop-Proc cmdlet with the `InputObject` parameter set to stop processes on the Notepad object retrieved by the `Get-Process` command.</span></span>

    ```
    PS> get-process notepad | stop-proc
    Confirm
    Are you sure you want to perform this action?
    Performing operation "stop-proc" on Target "notepad (444)".
    [Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"): N
    ```

## <a name="see-also"></a><span data-ttu-id="b3611-162">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="b3611-162">See Also</span></span>

[<span data-ttu-id="b3611-163">Creazione di un cmdlet che modifica il sistema</span><span class="sxs-lookup"><span data-stu-id="b3611-163">Creating a Cmdlet that Modifies the System</span></span>](./creating-a-cmdlet-that-modifies-the-system.md)

[<span data-ttu-id="b3611-164">Come creare un cmdlet di Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="b3611-164">How to Create a Windows PowerShell Cmdlet</span></span>](/powershell/developer/cmdlet/writing-a-windows-powershell-cmdlet)

<span data-ttu-id="b3611-165">[Estensione di tipi di oggetti e formattazione](/previous-versions//ms714665(v=vs.85))</span><span class="sxs-lookup"><span data-stu-id="b3611-165">[Extending Object Types and Formatting](/previous-versions//ms714665(v=vs.85))</span></span>

<span data-ttu-id="b3611-166">[Come registrare cmdlet, provider e applicazioni host](/previous-versions//ms714644(v=vs.85))</span><span class="sxs-lookup"><span data-stu-id="b3611-166">[How to Register Cmdlets, Providers, and Host Applications](/previous-versions//ms714644(v=vs.85))</span></span>

[<span data-ttu-id="b3611-167">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="b3611-167">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)
