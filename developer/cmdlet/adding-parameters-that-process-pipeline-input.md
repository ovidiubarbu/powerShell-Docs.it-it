---
title: Aggiunta di parametri che elaborano Pipeline Input | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- cmdlets [PowerShell Programmer's Guide], pipeline input
- parameters [PowerShell Programmer's Guide], pipeline input
ms.assetid: 09bf70a9-7c76-4ffe-b3f0-a1d5f10a0931
caps.latest.revision: 8
ms.openlocfilehash: 34643d20c16f8cc45e7fb20dc2a87d78b18bbf10
ms.sourcegitcommit: f60fa420bdc81db174e6168d3aeb11371e483162
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/20/2019
ms.locfileid: "67298635"
---
# <a name="adding-parameters-that-process-pipeline-input"></a><span data-ttu-id="20991-102">Aggiunta di parametri che elaborano gli input della pipeline</span><span class="sxs-lookup"><span data-stu-id="20991-102">Adding Parameters that Process Pipeline Input</span></span>

<span data-ttu-id="20991-103">Un'origine di input per un cmdlet è un oggetto nella pipeline proveniente da un cmdlet a monte.</span><span class="sxs-lookup"><span data-stu-id="20991-103">One source of input for a cmdlet is an object on the pipeline that originates from an upstream cmdlet.</span></span> <span data-ttu-id="20991-104">In questa sezione viene descritto come aggiungere un parametro al cmdlet Get-Proc (descritto nella [la creazione del primo Cmdlet](./creating-a-cmdlet-without-parameters.md)) in modo che il cmdlet può elaborare gli oggetti pipeline.</span><span class="sxs-lookup"><span data-stu-id="20991-104">This section describes how to add a parameter to the Get-Proc cmdlet (described in [Creating Your First Cmdlet](./creating-a-cmdlet-without-parameters.md)) so that the cmdlet can process pipeline objects.</span></span>

<span data-ttu-id="20991-105">Questo cmdlet Get-Process Usa un `Name` parametro che accetta l'input da un oggetto della pipeline, recupera le informazioni sul processo dal computer locale in base ai nomi specificati e quindi Visualizza le informazioni sui processi nella riga di comando.</span><span class="sxs-lookup"><span data-stu-id="20991-105">This Get-Proc cmdlet uses a `Name` parameter that accepts input from a pipeline object, retrieves process information from the local computer based on the supplied names, and then displays information about the processes at the command line.</span></span>

## <a name="defining-the-cmdlet-class"></a><span data-ttu-id="20991-106">La definizione di classe del Cmdlet</span><span class="sxs-lookup"><span data-stu-id="20991-106">Defining the Cmdlet Class</span></span>

<span data-ttu-id="20991-107">Il primo passaggio nella creazione di cmdlet è sempre il cmdlet di denominazione e la dichiarazione di classe .NET che implementa il cmdlet.</span><span class="sxs-lookup"><span data-stu-id="20991-107">The first step in cmdlet creation is always naming the cmdlet and declaring the .NET class that implements the cmdlet.</span></span> <span data-ttu-id="20991-108">Questo cmdlet recupera le informazioni sul processo, in modo che il nome del verbo selezionato qui è "Get".</span><span class="sxs-lookup"><span data-stu-id="20991-108">This cmdlet retrieves process information, so the verb name chosen here is "Get".</span></span> <span data-ttu-id="20991-109">(Quasi una sorta di cmdlet che è in grado di recuperare le informazioni può elaborare input della riga di comando). Per altre informazioni sui verbi approvati di cmdlet, vedere [nomi dei verbi di Cmdlet](./approved-verbs-for-windows-powershell-commands.md).</span><span class="sxs-lookup"><span data-stu-id="20991-109">(Almost any sort of cmdlet that is capable of retrieving information can process command-line input.) For more information about approved cmdlet verbs, see [Cmdlet Verb Names](./approved-verbs-for-windows-powershell-commands.md).</span></span>

<span data-ttu-id="20991-110">Di seguito è la definizione per il cmdlet Get-Process.</span><span class="sxs-lookup"><span data-stu-id="20991-110">The following is the definition for this Get-Proc cmdlet.</span></span> <span data-ttu-id="20991-111">Dettagli di questa definizione sono disponibili nella [la creazione del primo Cmdlet](./creating-a-cmdlet-without-parameters.md).</span><span class="sxs-lookup"><span data-stu-id="20991-111">Details of this definition are given in [Creating Your First Cmdlet](./creating-a-cmdlet-without-parameters.md).</span></span>

```csharp
[Cmdlet(VerbsCommon.Get, "proc")]
public class GetProcCommand : Cmdlet
```

```vb
<Cmdlet(VerbsCommon.Get, "Proc")> _
Public Class GetProcCommand
    Inherits Cmdlet
```

## <a name="defining-input-from-the-pipeline"></a><span data-ttu-id="20991-112">La definizione di Input dalla Pipeline</span><span class="sxs-lookup"><span data-stu-id="20991-112">Defining Input from the Pipeline</span></span>

<span data-ttu-id="20991-113">In questa sezione viene descritto come definire l'input dalla pipeline per un cmdlet.</span><span class="sxs-lookup"><span data-stu-id="20991-113">This section describes how to define input from the pipeline for a cmdlet.</span></span> <span data-ttu-id="20991-114">Questo cmdlet Get-Proc definisce una proprietà che rappresenta il `Name` parametro, come descritto in [aggiunta di parametri di Input della riga di comando processo](./adding-parameters-that-process-command-line-input.md).</span><span class="sxs-lookup"><span data-stu-id="20991-114">This Get-Proc cmdlet defines a property that represents the `Name` parameter as described in [Adding Parameters that Process Command Line Input](./adding-parameters-that-process-command-line-input.md).</span></span> <span data-ttu-id="20991-115">(Vedere l'argomento per informazioni generali sulla dichiarazione di parametri).</span><span class="sxs-lookup"><span data-stu-id="20991-115">(See that topic for general information about declaring parameters.)</span></span>

<span data-ttu-id="20991-116">Tuttavia, quando un cmdlet deve elaborare l'input della pipeline, deve avere i parametri associati a valori di input dal runtime di Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="20991-116">However, when a cmdlet needs to process pipeline input, it must have its parameters bound to input values by the Windows PowerShell runtime.</span></span> <span data-ttu-id="20991-117">A tale scopo, è necessario aggiungere il `ValueFromPipeline` parola chiave o aggiungere il `ValueFromPipelineByProperty` parola chiave per il [System.Management.Automation.Parameterattribute](/dotnet/api/System.Management.Automation.ParameterAttribute) dichiarazione dell'attributo.</span><span class="sxs-lookup"><span data-stu-id="20991-117">To do this, you must add the `ValueFromPipeline` keyword or add the `ValueFromPipelineByProperty` keyword to the [System.Management.Automation.Parameterattribute](/dotnet/api/System.Management.Automation.ParameterAttribute) attribute declaration.</span></span> <span data-ttu-id="20991-118">Specificare il `ValueFromPipeline` parola chiave se il cmdlet accede all'oggetto di input completo.</span><span class="sxs-lookup"><span data-stu-id="20991-118">Specify the `ValueFromPipeline` keyword if the cmdlet accesses the complete input object.</span></span> <span data-ttu-id="20991-119">Specificare il `ValueFromPipelineByProperty` se il cmdlet accede solo una proprietà dell'oggetto.</span><span class="sxs-lookup"><span data-stu-id="20991-119">Specify the `ValueFromPipelineByProperty` if the cmdlet accesses only a property of the object.</span></span>

<span data-ttu-id="20991-120">Di seguito è riportata la dichiarazione di parametro per il `Name` parametro del cmdlet Get-Process che accetta l'input della pipeline.</span><span class="sxs-lookup"><span data-stu-id="20991-120">Here is the parameter declaration for the `Name` parameter of this Get-Proc cmdlet that accepts pipeline input.</span></span>

[!code-csharp[GetProcessSample03.cs](../../powershell-sdk-samples/SDK-2.0/csharp/GetProcessSample03/GetProcessSample03.cs#L35-L44 "GetProcessSample03.cs")]

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

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplesgetproc03#GetProc03VBNameParameter](Msh_samplesgetproc03#GetProc03VBNameParameter)]  -->

<span data-ttu-id="20991-121">I set di dichiarazione precedente di `ValueFromPipeline` parola chiave da `true` in modo che il runtime di Windows PowerShell verrà associato il parametro all'oggetto in ingresso se l'oggetto è dello stesso tipo di parametro o se può essere assegnato lo stesso tipo.</span><span class="sxs-lookup"><span data-stu-id="20991-121">The previous declaration sets the `ValueFromPipeline` keyword to `true` so that the Windows PowerShell runtime will bind the parameter to the incoming object if the object is the same type as the parameter, or if it can be coerced to the same type.</span></span> <span data-ttu-id="20991-122">Il `ValueFromPipelineByPropertyName` parola chiave viene impostata su `true` in modo che il runtime di Windows PowerShell controllerà l'oggetto in ingresso per un `Name` proprietà.</span><span class="sxs-lookup"><span data-stu-id="20991-122">The `ValueFromPipelineByPropertyName` keyword is also set to `true` so that the Windows PowerShell runtime will check the incoming object for a `Name` property.</span></span> <span data-ttu-id="20991-123">Se l'oggetto in ingresso ha una proprietà di questo tipo, il runtime verrà associato il `Name` parametro per il `Name` proprietà dell'oggetto in ingresso.</span><span class="sxs-lookup"><span data-stu-id="20991-123">If the incoming object has such a property, the runtime will bind the `Name` parameter to the `Name` property of the incoming object.</span></span>

> [!NOTE]
> <span data-ttu-id="20991-124">L'impostazione delle `ValueFromPipeline` parola chiave dell'attributo di un parametro ha la precedenza sull'impostazione del `ValueFromPipelineByPropertyName` (parola chiave).</span><span class="sxs-lookup"><span data-stu-id="20991-124">The setting of the `ValueFromPipeline` attribute keyword for a parameter takes precedence over the setting for the `ValueFromPipelineByPropertyName` keyword.</span></span>

## <a name="overriding-an-input-processing-method"></a><span data-ttu-id="20991-125">Si esegue l'override di un metodo di elaborazione dell'Input</span><span class="sxs-lookup"><span data-stu-id="20991-125">Overriding an Input Processing Method</span></span>

<span data-ttu-id="20991-126">Se il cmdlet deve gestire l'input della pipeline, è necessario eseguire l'override di metodi di elaborazione dell'input appropriati.</span><span class="sxs-lookup"><span data-stu-id="20991-126">If your cmdlet is to handle pipeline input, it needs to override the appropriate input processing methods.</span></span> <span data-ttu-id="20991-127">In cui sono stati introdotti i metodi di elaborazione dell'input di base [la creazione del primo Cmdlet](./creating-a-cmdlet-without-parameters.md).</span><span class="sxs-lookup"><span data-stu-id="20991-127">The basic input processing methods are introduced in [Creating Your First Cmdlet](./creating-a-cmdlet-without-parameters.md).</span></span>

<span data-ttu-id="20991-128">Esegue l'override di questo cmdlet Get-Proc il [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) metodo per gestire il `Name` input del parametro fornito dall'utente o uno script.</span><span class="sxs-lookup"><span data-stu-id="20991-128">This Get-Proc cmdlet overrides the [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) method to handle the `Name` parameter input provided by the user or a script.</span></span> <span data-ttu-id="20991-129">Questo metodo otterranno i processi per ogni nome di processo richiesto o tutti i processi se viene fornito alcun nome.</span><span class="sxs-lookup"><span data-stu-id="20991-129">This method will get the processes for each requested process name or all processes if no name is provided.</span></span> <span data-ttu-id="20991-130">Si noti che nel [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord), la chiamata a [WriteObject(System.Object,System.Boolean)](/dotnet/api/system.management.automation.cmdlet.writeobject?view=pscore-6.2.0#System_Management_Automation_Cmdlet_WriteObject_System_Object_System_Boolean_) è il meccanismo di output per l'invio di oggetti di output per il pipeline.</span><span class="sxs-lookup"><span data-stu-id="20991-130">Notice that within [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord), the call to [WriteObject(System.Object,System.Boolean)](/dotnet/api/system.management.automation.cmdlet.writeobject?view=pscore-6.2.0#System_Management_Automation_Cmdlet_WriteObject_System_Object_System_Boolean_) is the output mechanism for sending output objects to the pipeline.</span></span> <span data-ttu-id="20991-131">Il secondo parametro di questa chiamata `enumerateCollection`, è impostato su `true` indicare al runtime di Windows PowerShell per enumerare la matrice di oggetti processo e scrivere un solo processo alla volta nella riga di comando.</span><span class="sxs-lookup"><span data-stu-id="20991-131">The second parameter of this call, `enumerateCollection`, is set to `true` to tell the Windows PowerShell runtime to enumerate the array of process objects, and write one process at a time to the command line.</span></span>

```csharp
protected override void ProcessRecord()
{
  // If no process names are passed to the cmdlet, get all processes.
  if (processNames == null)
  {
      // Write the processes to the pipeline making them available
      // to the next cmdlet. The second argument of this call tells
      // PowerShell to enumerate the array, and send one process at a
      // time to the pipeline.
      WriteObject(Process.GetProcesses(), true);
  }
  else
  {
    // If process names are passed to the cmdlet, get and write
    // the associated processes.
    foreach (string name in processNames)
    {
      WriteObject(Process.GetProcessesByName(name), true);
    } // End foreach (string name...).
  }
}
```

```vb
Protected Overrides Sub ProcessRecord()
    Dim processes As Process()

    '/ If no process names are passed to the cmdlet, get all processes.
    If processNames Is Nothing Then
        processes = Process.GetProcesses()
    Else

        '/ If process names are specified, write the processes to the
        '/ pipeline to display them or make them available to the next cmdlet.
        For Each name As String In processNames
            '/ The second parameter of this call tells PowerShell to enumerate the
            '/ array, and send one process at a time to the pipeline.
            WriteObject(Process.GetProcessesByName(name), True)
        Next
    End If

End Sub 'ProcessRecord
```

## <a name="code-sample"></a><span data-ttu-id="20991-132">Esempio di codice</span><span class="sxs-lookup"><span data-stu-id="20991-132">Code Sample</span></span>

<span data-ttu-id="20991-133">Per l'intero C# esempi di codice, vedere [esempio GetProcessSample03](./getprocesssample03-sample.md).</span><span class="sxs-lookup"><span data-stu-id="20991-133">For the complete C# sample code, see [GetProcessSample03 Sample](./getprocesssample03-sample.md).</span></span>

## <a name="defining-object-types-and-formatting"></a><span data-ttu-id="20991-134">Definizione di tipi di oggetto e formattazione</span><span class="sxs-lookup"><span data-stu-id="20991-134">Defining Object Types and Formatting</span></span>

<span data-ttu-id="20991-135">Windows PowerShell passa informazioni tra i cmdlet con gli oggetti .net.</span><span class="sxs-lookup"><span data-stu-id="20991-135">Windows PowerShell passes information between cmdlets using .Net objects.</span></span> <span data-ttu-id="20991-136">Di conseguenza, potrebbe essere necessario definire un proprio tipo di un cmdlet o il cmdlet potrebbe essere necessario estendere un tipo esistente fornito da un altro cmdlet.</span><span class="sxs-lookup"><span data-stu-id="20991-136">Consequently, a cmdlet may need to define its own type, or the cmdlet may need to extend an existing type provided by another cmdlet.</span></span> <span data-ttu-id="20991-137">Per altre informazioni sulla definizione di nuovi tipi o estendere i tipi esistenti, vedere [estendendo i tipi di oggetto e formattazione](/previous-versions//ms714665(v=vs.85)).</span><span class="sxs-lookup"><span data-stu-id="20991-137">For more information about defining new types or extending existing types, see [Extending Object Types and Formatting](/previous-versions//ms714665(v=vs.85)).</span></span>

## <a name="building-the-cmdlet"></a><span data-ttu-id="20991-138">Creazione di Cmdlet</span><span class="sxs-lookup"><span data-stu-id="20991-138">Building the Cmdlet</span></span>

<span data-ttu-id="20991-139">Dopo l'implementazione di un cmdlet è necessario registrarlo con Windows PowerShell tramite uno snap-in Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="20991-139">After implementing a cmdlet it must be registered with Windows PowerShell through a Windows PowerShell snap-in.</span></span> <span data-ttu-id="20991-140">Per altre informazioni sulla registrazione dei cmdlet, vedere [come registrare i cmdlet, provider e applicazioni Host](/previous-versions//ms714644(v=vs.85)).</span><span class="sxs-lookup"><span data-stu-id="20991-140">For more information about registering cmdlets, see [How to Register Cmdlets, Providers, and Host Applications](/previous-versions//ms714644(v=vs.85)).</span></span>

## <a name="testing-the-cmdlet"></a><span data-ttu-id="20991-141">Il Cmdlet di test</span><span class="sxs-lookup"><span data-stu-id="20991-141">Testing the Cmdlet</span></span>

<span data-ttu-id="20991-142">Quando il cmdlet è stato registrato con Windows PowerShell, è possibile testarlo eseguendolo dalla riga di comando.</span><span class="sxs-lookup"><span data-stu-id="20991-142">When your cmdlet has been registered with Windows PowerShell, test it by running it on the command line.</span></span> <span data-ttu-id="20991-143">Ad esempio, testare il codice per il cmdlet di esempio.</span><span class="sxs-lookup"><span data-stu-id="20991-143">For example, test the code for the sample cmdlet.</span></span> <span data-ttu-id="20991-144">Per altre informazioni sull'utilizzo dei cmdlet dalla riga di comando, vedere la [Introduzione a Windows PowerShell](/powershell/scripting/getting-started/getting-started-with-windows-powershell).</span><span class="sxs-lookup"><span data-stu-id="20991-144">For more information about using cmdlets from the command line, see the [Getting Started with Windows PowerShell](/powershell/scripting/getting-started/getting-started-with-windows-powershell).</span></span>

- <span data-ttu-id="20991-145">Al prompt di Windows PowerShell, immettere i comandi seguenti per recuperare i nomi dei processi tramite la pipeline.</span><span class="sxs-lookup"><span data-stu-id="20991-145">At the Windows PowerShell prompt, enter the following commands to retrieve the process names through the pipeline.</span></span>

    ```powershell
    PS> type ProcessNames | get-proc
    ```

<span data-ttu-id="20991-146">Viene visualizzato l'output seguente.</span><span class="sxs-lookup"><span data-stu-id="20991-146">The following output appears.</span></span>

    ```
    Handles  NPM(K)  PM(K)   WS(K)  VS(M)  CPU(s)    Id  ProcessName
    -------  ------  -----   ----- -----   ------    --  -----------
        809      21  40856    4448    147    9.50  2288  iexplore
        737      21  26036   16348    144   22.03  3860  iexplore
         39       2   1024     388     30    0.08  3396  notepad
       3927      62  71836   26984    467  195.19  1848  OUTLOOK
    ```

- <span data-ttu-id="20991-147">Immettere le righe seguenti per ottenere gli oggetti processo che hanno un `Name` proprietà dai processi denominata "IEXPLORE".</span><span class="sxs-lookup"><span data-stu-id="20991-147">Enter the following lines to get the process objects that have a `Name` property from the processes called "IEXPLORE".</span></span> <span data-ttu-id="20991-148">Questo esempio viene usato il `Get-Process` cmdlet (fornito da Windows PowerShell) come un comando per recuperare i processi "IEXPLORE" upstream.</span><span class="sxs-lookup"><span data-stu-id="20991-148">This example uses the `Get-Process` cmdlet (provided by Windows PowerShell) as an upstream command to retrieve the "IEXPLORE" processes.</span></span>

    ```powershell
    PS> get-process iexplore | get-proc
    ```

<span data-ttu-id="20991-149">Viene visualizzato l'output seguente.</span><span class="sxs-lookup"><span data-stu-id="20991-149">The following output appears.</span></span>

    ```
    Handles  NPM(K)  PM(K)   WS(K)  VS(M)  CPU(s)    Id  ProcessName
    -------  ------  -----      ----- -----   ------     -- -----------
        801      21  40720    6544    142    9.52  2288  iexplore
        726      21  25872   16652    138   22.09  3860  iexplore
        801      21  40720    6544    142    9.52  2288  iexplore
        726      21  25872   16652    138   22.09  3860  iexplore
    ```

## <a name="see-also"></a><span data-ttu-id="20991-150">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="20991-150">See Also</span></span>

[<span data-ttu-id="20991-151">Aggiunta di parametri che elaborano gli Input della riga di comando</span><span class="sxs-lookup"><span data-stu-id="20991-151">Adding Parameters that Process Command Line Input</span></span>](./adding-parameters-that-process-command-line-input.md)

[<span data-ttu-id="20991-152">Creazione del primo Cmdlet</span><span class="sxs-lookup"><span data-stu-id="20991-152">Creating Your First Cmdlet</span></span>](./creating-a-cmdlet-without-parameters.md)

<span data-ttu-id="20991-153">[Estensione di tipi di oggetto e la formattazione](/previous-versions//ms714665(v=vs.85))</span><span class="sxs-lookup"><span data-stu-id="20991-153">[Extending Object Types and Formatting](/previous-versions//ms714665(v=vs.85))</span></span>

<span data-ttu-id="20991-154">[Come registrare i cmdlet, provider e applicazioni Host](/previous-versions//ms714644(v=vs.85))</span><span class="sxs-lookup"><span data-stu-id="20991-154">[How to Register Cmdlets, Providers, and Host Applications](/previous-versions//ms714644(v=vs.85))</span></span>

<span data-ttu-id="20991-155">[Windows PowerShell Reference](../windows-powershell-reference.md) (Guida di riferimento di PowerShell)</span><span class="sxs-lookup"><span data-stu-id="20991-155">[Windows PowerShell Reference](../windows-powershell-reference.md)</span></span>

[<span data-ttu-id="20991-156">Esempi di cmdlet</span><span class="sxs-lookup"><span data-stu-id="20991-156">Cmdlet Samples</span></span>](./cmdlet-samples.md)
