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
ms.openlocfilehash: bd52dc8aee7975d0899083a5c2f595b17690dc33
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/16/2019
ms.locfileid: "58054757"
---
# <a name="adding-parameters-that-process-pipeline-input"></a><span data-ttu-id="151ec-102">Aggiunta di parametri che elaborano gli input della pipeline</span><span class="sxs-lookup"><span data-stu-id="151ec-102">Adding Parameters that Process Pipeline Input</span></span>

<span data-ttu-id="151ec-103">Un'origine di input per un cmdlet è un oggetto nella pipeline proveniente da un cmdlet a monte.</span><span class="sxs-lookup"><span data-stu-id="151ec-103">One source of input for a cmdlet is an object on the pipeline that originates from an upstream cmdlet.</span></span> <span data-ttu-id="151ec-104">In questa sezione viene descritto come aggiungere un parametro al cmdlet Get-Proc (descritto nella [la creazione del primo Cmdlet](./creating-a-cmdlet-without-parameters.md)) in modo che il cmdlet può elaborare gli oggetti pipeline.</span><span class="sxs-lookup"><span data-stu-id="151ec-104">This section describes how to add a parameter to the Get-Proc cmdlet (described in [Creating Your First Cmdlet](./creating-a-cmdlet-without-parameters.md)) so that the cmdlet can process pipeline objects.</span></span>

<span data-ttu-id="151ec-105">Questo cmdlet Get-Process Usa un `Name` parametro che accetta l'input da un oggetto della pipeline, recupera le informazioni sul processo dal computer locale in base ai nomi specificati e quindi Visualizza le informazioni sui processi nella riga di comando.</span><span class="sxs-lookup"><span data-stu-id="151ec-105">This Get-Proc cmdlet uses a `Name` parameter that accepts input from a pipeline object, retrieves process information from the local computer based on the supplied names, and then displays information about the processes at the command line.</span></span>

<span data-ttu-id="151ec-106">Gli argomenti in questa sezione includono quanto segue:</span><span class="sxs-lookup"><span data-stu-id="151ec-106">Topics in this section include the following:</span></span>

- [<span data-ttu-id="151ec-107">La definizione di classe del Cmdlet</span><span class="sxs-lookup"><span data-stu-id="151ec-107">Defining the Cmdlet Class</span></span>](#Defining-the-Cmdlet-Class)

- [<span data-ttu-id="151ec-108">La definizione di Input dalla Pipeline</span><span class="sxs-lookup"><span data-stu-id="151ec-108">Defining Input from the Pipeline</span></span>](#Defining-Input-from-the-Pipeline)

- [<span data-ttu-id="151ec-109">Si esegue l'override di un metodo di elaborazione dell'Input</span><span class="sxs-lookup"><span data-stu-id="151ec-109">Overriding an Input Processing Method</span></span>](#Overriding-an-Input-Processing-Method)

- [<span data-ttu-id="151ec-110">Esempio di codice</span><span class="sxs-lookup"><span data-stu-id="151ec-110">Code Sample</span></span>](#Code-Sample)

- [<span data-ttu-id="151ec-111">Definizione di tipi di oggetto e formattazione</span><span class="sxs-lookup"><span data-stu-id="151ec-111">Defining Object Types and Formatting</span></span>](#Defining-Object-Types-and-Formatting)

- [<span data-ttu-id="151ec-112">Creazione di Cmdlet</span><span class="sxs-lookup"><span data-stu-id="151ec-112">Building the Cmdlet</span></span>](#Building-the-Cmdlet)

- [<span data-ttu-id="151ec-113">Il Cmdlet di test</span><span class="sxs-lookup"><span data-stu-id="151ec-113">Testing the Cmdlet</span></span>](#Testing-the-Cmdlet)

## <a name="defining-the-cmdlet-class"></a><span data-ttu-id="151ec-114">La definizione di classe del Cmdlet</span><span class="sxs-lookup"><span data-stu-id="151ec-114">Defining the Cmdlet Class</span></span>

<span data-ttu-id="151ec-115">Il primo passaggio nella creazione di cmdlet è sempre il cmdlet di denominazione e la dichiarazione di classe .NET che implementa il cmdlet.</span><span class="sxs-lookup"><span data-stu-id="151ec-115">The first step in cmdlet creation is always naming the cmdlet and declaring the .NET class that implements the cmdlet.</span></span> <span data-ttu-id="151ec-116">Questo cmdlet recupera le informazioni sul processo, in modo che il nome del verbo selezionato qui è "Get".</span><span class="sxs-lookup"><span data-stu-id="151ec-116">This cmdlet retrieves process information, so the verb name chosen here is "Get".</span></span> <span data-ttu-id="151ec-117">(Quasi una sorta di cmdlet che è in grado di recuperare le informazioni può elaborare input della riga di comando). Per altre informazioni sui verbi approvati di cmdlet, vedere [nomi dei verbi di Cmdlet](./approved-verbs-for-windows-powershell-commands.md).</span><span class="sxs-lookup"><span data-stu-id="151ec-117">(Almost any sort of cmdlet that is capable of retrieving information can process command-line input.) For more information about approved cmdlet verbs, see [Cmdlet Verb Names](./approved-verbs-for-windows-powershell-commands.md).</span></span>

<span data-ttu-id="151ec-118">Di seguito è la definizione per il cmdlet Get-Process.</span><span class="sxs-lookup"><span data-stu-id="151ec-118">The following is the definition for this Get-Proc cmdlet.</span></span> <span data-ttu-id="151ec-119">Dettagli di questa definizione sono disponibili nella [la creazione del primo Cmdlet](./creating-a-cmdlet-without-parameters.md).</span><span class="sxs-lookup"><span data-stu-id="151ec-119">Details of this definition are given in [Creating Your First Cmdlet](./creating-a-cmdlet-without-parameters.md).</span></span>

```csharp
[Cmdlet(VerbsCommon.Get, "proc")]
public class GetProcCommand : Cmdlet
```

```vb
<Cmdlet(VerbsCommon.Get, "Proc")> _
Public Class GetProcCommand
    Inherits Cmdlet
```

## <a name="defining-input-from-the-pipeline"></a><span data-ttu-id="151ec-120">La definizione di Input dalla Pipeline</span><span class="sxs-lookup"><span data-stu-id="151ec-120">Defining Input from the Pipeline</span></span>

<span data-ttu-id="151ec-121">In questa sezione viene descritto come definire l'input dalla pipeline per un cmdlet.</span><span class="sxs-lookup"><span data-stu-id="151ec-121">This section describes how to define input from the pipeline for a cmdlet.</span></span> <span data-ttu-id="151ec-122">Questo cmdlet Get-Proc definisce una proprietà che rappresenta il `Name` parametro, come descritto in [aggiunta di parametri di Input della riga di comando processo](./adding-parameters-that-process-command-line-input.md).</span><span class="sxs-lookup"><span data-stu-id="151ec-122">This Get-Proc cmdlet defines a property that represents the `Name` parameter as described in [Adding Parameters that Process Command Line Input](./adding-parameters-that-process-command-line-input.md).</span></span> <span data-ttu-id="151ec-123">(Vedere l'argomento per informazioni generali sulla dichiarazione di parametri).</span><span class="sxs-lookup"><span data-stu-id="151ec-123">(See that topic for general information about declaring parameters.)</span></span>

<span data-ttu-id="151ec-124">Tuttavia, quando un cmdlet deve elaborare l'input della pipeline, deve avere i parametri associati a valori di input dal runtime di Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="151ec-124">However, when a cmdlet needs to process pipeline input, it must have its parameters bound to input values by the Windows PowerShell runtime.</span></span> <span data-ttu-id="151ec-125">A tale scopo, è necessario aggiungere il `ValueFromPipeline` parola chiave o aggiungere il `ValueFromPipelineByProperty` parola chiave per il [System.Management.Automation.Parameterattribute](/dotnet/api/System.Management.Automation.ParameterAttribute) dichiarazione dell'attributo.</span><span class="sxs-lookup"><span data-stu-id="151ec-125">To do this, you must add the `ValueFromPipeline` keyword or add the `ValueFromPipelineByProperty` keyword to the [System.Management.Automation.Parameterattribute](/dotnet/api/System.Management.Automation.ParameterAttribute) attribute declaration.</span></span> <span data-ttu-id="151ec-126">Specificare il `ValueFromPipeline` parola chiave se il cmdlet accede all'oggetto di input completo.</span><span class="sxs-lookup"><span data-stu-id="151ec-126">Specify the `ValueFromPipeline` keyword if the cmdlet accesses the complete input object.</span></span> <span data-ttu-id="151ec-127">Specificare il `ValueFromPipelineByProperty` se il cmdlet accede solo una proprietà dell'oggetto.</span><span class="sxs-lookup"><span data-stu-id="151ec-127">Specify the `ValueFromPipelineByProperty` if the cmdlet accesses only a property of the object.</span></span>

<span data-ttu-id="151ec-128">Di seguito è riportata la dichiarazione di parametro per il `Name` parametro del cmdlet Get-Process che accetta l'input della pipeline.</span><span class="sxs-lookup"><span data-stu-id="151ec-128">Here is the parameter declaration for the `Name` parameter of this Get-Proc cmdlet that accepts pipeline input.</span></span>

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

<span data-ttu-id="151ec-129">I set di dichiarazione precedente di `ValueFromPipeline` parola chiave da `true` in modo che il runtime di Windows PowerShell verrà associato il parametro all'oggetto in ingresso se l'oggetto è dello stesso tipo di parametro o se può essere assegnato lo stesso tipo.</span><span class="sxs-lookup"><span data-stu-id="151ec-129">The previous declaration sets the `ValueFromPipeline` keyword to `true` so that the Windows PowerShell runtime will bind the parameter to the incoming object if the object is the same type as the parameter, or if it can be coerced to the same type.</span></span> <span data-ttu-id="151ec-130">Il `ValueFromPipelineByPropertyName` parola chiave viene impostata su `true` in modo che il runtime di Windows PowerShell controllerà l'oggetto in ingresso per un `Name` proprietà.</span><span class="sxs-lookup"><span data-stu-id="151ec-130">The `ValueFromPipelineByPropertyName` keyword is also set to `true` so that the Windows PowerShell runtime will check the incoming object for a `Name` property.</span></span> <span data-ttu-id="151ec-131">Se l'oggetto in ingresso ha una proprietà di questo tipo, il runtime verrà associato il `Name` parametro per il `Name` proprietà dell'oggetto in ingresso.</span><span class="sxs-lookup"><span data-stu-id="151ec-131">If the incoming object has such a property, the runtime will bind the `Name` parameter to the `Name` property of the incoming object.</span></span>

> [!NOTE]
> <span data-ttu-id="151ec-132">L'impostazione delle `ValueFromPipeline` parola chiave dell'attributo di un parametro ha la precedenza sull'impostazione del `ValueFromPipelineByPropertyName` (parola chiave).</span><span class="sxs-lookup"><span data-stu-id="151ec-132">The setting of the `ValueFromPipeline` attribute keyword for a parameter takes precedence over the setting for the `ValueFromPipelineByPropertyName` keyword.</span></span>

## <a name="overriding-an-input-processing-method"></a><span data-ttu-id="151ec-133">Si esegue l'override di un metodo di elaborazione dell'Input</span><span class="sxs-lookup"><span data-stu-id="151ec-133">Overriding an Input Processing Method</span></span>

<span data-ttu-id="151ec-134">Se il cmdlet deve gestire l'input della pipeline, è necessario eseguire l'override di metodi di elaborazione dell'input appropriati.</span><span class="sxs-lookup"><span data-stu-id="151ec-134">If your cmdlet is to handle pipeline input, it needs to override the appropriate input processing methods.</span></span> <span data-ttu-id="151ec-135">In cui sono stati introdotti i metodi di elaborazione dell'input di base [la creazione del primo Cmdlet](./creating-a-cmdlet-without-parameters.md).</span><span class="sxs-lookup"><span data-stu-id="151ec-135">The basic input processing methods are introduced in [Creating Your First Cmdlet](./creating-a-cmdlet-without-parameters.md).</span></span>

<span data-ttu-id="151ec-136">Esegue l'override di questo cmdlet Get-Proc il [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) metodo per gestire il `Name` input del parametro fornito dall'utente o uno script.</span><span class="sxs-lookup"><span data-stu-id="151ec-136">This Get-Proc cmdlet overrides the [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) method to handle the `Name` parameter input provided by the user or a script.</span></span> <span data-ttu-id="151ec-137">Questo metodo otterranno i processi per ogni nome di processo richiesto o tutti i processi se viene fornito alcun nome.</span><span class="sxs-lookup"><span data-stu-id="151ec-137">This method will get the processes for each requested process name or all processes if no name is provided.</span></span> <span data-ttu-id="151ec-138">Si noti che nel [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord), la chiamata a [System.Management.Automation.Cmdlet.WriteObject%28System.Object%2CSystem.Boolean%29](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject%28System.Object%2CSystem.Boolean%29) è riportato l'output meccanismo per l'invio di output oggetti alla pipeline.</span><span class="sxs-lookup"><span data-stu-id="151ec-138">Notice that within [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord), the call to [System.Management.Automation.Cmdlet.WriteObject%28System.Object%2CSystem.Boolean%29](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject%28System.Object%2CSystem.Boolean%29) is the output mechanism for sending output objects to the pipeline.</span></span> <span data-ttu-id="151ec-139">Il secondo parametro di questa chiamata `enumerateCollection`, è impostato su `true` indicare al runtime di Windows PowerShell per enumerare la matrice di oggetti processo e scrivere un solo processo alla volta nella riga di comando.</span><span class="sxs-lookup"><span data-stu-id="151ec-139">The second parameter of this call, `enumerateCollection`, is set to `true` to tell the Windows PowerShell runtime to enumerate the array of process objects, and write one process at a time to the command line.</span></span>

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

## <a name="code-sample"></a><span data-ttu-id="151ec-140">Esempio di codice</span><span class="sxs-lookup"><span data-stu-id="151ec-140">Code Sample</span></span>

<span data-ttu-id="151ec-141">Per l'intero C# esempi di codice, vedere [esempio GetProcessSample03](./getprocesssample03-sample.md).</span><span class="sxs-lookup"><span data-stu-id="151ec-141">For the complete C# sample code, see [GetProcessSample03 Sample](./getprocesssample03-sample.md).</span></span>

## <a name="defining-object-types-and-formatting"></a><span data-ttu-id="151ec-142">Definizione di tipi di oggetto e formattazione</span><span class="sxs-lookup"><span data-stu-id="151ec-142">Defining Object Types and Formatting</span></span>

<span data-ttu-id="151ec-143">Windows PowerShell passa informazioni tra i cmdlet con gli oggetti .net.</span><span class="sxs-lookup"><span data-stu-id="151ec-143">Windows PowerShell passes information between cmdlets using .Net objects.</span></span> <span data-ttu-id="151ec-144">Di conseguenza, potrebbe essere necessario definire un proprio tipo di un cmdlet o il cmdlet potrebbe essere necessario estendere un tipo esistente fornito da un altro cmdlet.</span><span class="sxs-lookup"><span data-stu-id="151ec-144">Consequently, a cmdlet may need to define its own type, or the cmdlet may need to extend an existing type provided by another cmdlet.</span></span> <span data-ttu-id="151ec-145">Per altre informazioni sulla definizione di nuovi tipi o estendere i tipi esistenti, vedere [estendendo i tipi di oggetto e formattazione](http://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351).</span><span class="sxs-lookup"><span data-stu-id="151ec-145">For more information about defining new types or extending existing types, see [Extending Object Types and Formatting](http://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351).</span></span>

## <a name="building-the-cmdlet"></a><span data-ttu-id="151ec-146">Creazione di Cmdlet</span><span class="sxs-lookup"><span data-stu-id="151ec-146">Building the Cmdlet</span></span>

<span data-ttu-id="151ec-147">Dopo l'implementazione di un cmdlet è necessario registrarlo con Windows PowerShell tramite uno snap-in Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="151ec-147">After implementing a cmdlet it must be registered with Windows PowerShell through a Windows PowerShell snap-in.</span></span> <span data-ttu-id="151ec-148">Per altre informazioni sulla registrazione dei cmdlet, vedere [come registrare i cmdlet, provider e applicazioni Host](http://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c).</span><span class="sxs-lookup"><span data-stu-id="151ec-148">For more information about registering cmdlets, see [How to Register Cmdlets, Providers, and Host Applications](http://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c).</span></span>

## <a name="testing-the-cmdlet"></a><span data-ttu-id="151ec-149">Il Cmdlet di test</span><span class="sxs-lookup"><span data-stu-id="151ec-149">Testing the Cmdlet</span></span>

<span data-ttu-id="151ec-150">Quando il cmdlet è stato registrato con Windows PowerShell, è possibile testarlo eseguendolo dalla riga di comando.</span><span class="sxs-lookup"><span data-stu-id="151ec-150">When your cmdlet has been registered with Windows PowerShell, test it by running it on the command line.</span></span> <span data-ttu-id="151ec-151">Ad esempio, testare il codice per il cmdlet di esempio.</span><span class="sxs-lookup"><span data-stu-id="151ec-151">For example, test the code for the sample cmdlet.</span></span> <span data-ttu-id="151ec-152">Per altre informazioni sull'utilizzo dei cmdlet dalla riga di comando, vedere la [Introduzione a Windows PowerShell](/powershell/scripting/getting-started/getting-started-with-windows-powershell).</span><span class="sxs-lookup"><span data-stu-id="151ec-152">For more information about using cmdlets from the command line, see the [Getting Started with Windows PowerShell](/powershell/scripting/getting-started/getting-started-with-windows-powershell).</span></span>

- <span data-ttu-id="151ec-153">Al prompt di Windows PowerShell, immettere i comandi seguenti per recuperare i nomi dei processi tramite la pipeline.</span><span class="sxs-lookup"><span data-stu-id="151ec-153">At the Windows PowerShell prompt, enter the following commands to retrieve the process names through the pipeline.</span></span>

    ```powershell
    PS> type ProcessNames | get-proc
    ```

<span data-ttu-id="151ec-154">Viene visualizzato l'output seguente.</span><span class="sxs-lookup"><span data-stu-id="151ec-154">The following output appears.</span></span>

    ```
    Handles  NPM(K)  PM(K)   WS(K)  VS(M)  CPU(s)    Id  ProcessName
    -------  ------  -----   ----- -----   ------    --  -----------
        809      21  40856    4448    147    9.50  2288  iexplore
        737      21  26036   16348    144   22.03  3860  iexplore
         39       2   1024     388     30    0.08  3396  notepad
       3927      62  71836   26984    467  195.19  1848  OUTLOOK
    ```

- <span data-ttu-id="151ec-155">Immettere le righe seguenti per ottenere gli oggetti processo che hanno un `Name` proprietà dai processi denominata "IEXPLORE".</span><span class="sxs-lookup"><span data-stu-id="151ec-155">Enter the following lines to get the process objects that have a `Name` property from the processes called "IEXPLORE".</span></span> <span data-ttu-id="151ec-156">Questo esempio viene usato il `Get-Process` cmdlet (fornito da Windows PowerShell) come un comando per recuperare i processi "IEXPLORE" upstream.</span><span class="sxs-lookup"><span data-stu-id="151ec-156">This example uses the `Get-Process` cmdlet (provided by Windows PowerShell) as an upstream command to retrieve the "IEXPLORE" processes.</span></span>

    ```powershell
    PS> get-process iexplore | get-proc
    ```

<span data-ttu-id="151ec-157">Viene visualizzato l'output seguente.</span><span class="sxs-lookup"><span data-stu-id="151ec-157">The following output appears.</span></span>

    ```
    Handles  NPM(K)  PM(K)   WS(K)  VS(M)  CPU(s)    Id  ProcessName
    -------  ------  -----      ----- -----   ------     -- -----------
        801      21  40720    6544    142    9.52  2288  iexplore
        726      21  25872   16652    138   22.09  3860  iexplore
        801      21  40720    6544    142    9.52  2288  iexplore
        726      21  25872   16652    138   22.09  3860  iexplore
    ```

## <a name="see-also"></a><span data-ttu-id="151ec-158">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="151ec-158">See Also</span></span>

[<span data-ttu-id="151ec-159">Aggiunta di parametri che elaborano gli Input della riga di comando</span><span class="sxs-lookup"><span data-stu-id="151ec-159">Adding Parameters that Process Command Line Input</span></span>](./adding-parameters-that-process-command-line-input.md)

[<span data-ttu-id="151ec-160">Creazione del primo Cmdlet</span><span class="sxs-lookup"><span data-stu-id="151ec-160">Creating Your First Cmdlet</span></span>](./creating-a-cmdlet-without-parameters.md)

[<span data-ttu-id="151ec-161">Estensione di tipi di oggetto e la formattazione</span><span class="sxs-lookup"><span data-stu-id="151ec-161">Extending Object Types and Formatting</span></span>](http://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351)

[<span data-ttu-id="151ec-162">Come registrare i cmdlet, provider e applicazioni Host</span><span class="sxs-lookup"><span data-stu-id="151ec-162">How to Register Cmdlets, Providers, and Host Applications</span></span>](http://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c)

<span data-ttu-id="151ec-163">[Windows PowerShell Reference](../windows-powershell-reference.md) (Guida di riferimento di PowerShell)</span><span class="sxs-lookup"><span data-stu-id="151ec-163">[Windows PowerShell Reference](../windows-powershell-reference.md)</span></span>

[<span data-ttu-id="151ec-164">Esempi di cmdlet</span><span class="sxs-lookup"><span data-stu-id="151ec-164">Cmdlet Samples</span></span>](./cmdlet-samples.md)
