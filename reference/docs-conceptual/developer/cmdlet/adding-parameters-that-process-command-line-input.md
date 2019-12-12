---
title: Aggiunta di parametri che elaborano l'input della riga di comando | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- cmdlets [PowerShell Programmer's Guide], parameters
- Get-Proc cmdlet [PowerShell Programmer's Guide]
- cmdlets [PowerShell Programmer's Guide], command line input
- command line input [PowerShell Programmer's Guide]
- parameters [PowerShell Programmer's Guide]
- cmdlets [PowerShell Programmer's Guide], creating
ms.assetid: da0b32f8-7b51-440e-a061-3177b5759e0e
caps.latest.revision: 9
ms.openlocfilehash: 7db93af33717dc4802ed915793f6cd570cfb48f6
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/05/2019
ms.locfileid: "72364630"
---
# <a name="adding-parameters-that-process-command-line-input"></a><span data-ttu-id="ea1ea-102">Aggiunta di parametri che elaborano gli input della riga di comando</span><span class="sxs-lookup"><span data-stu-id="ea1ea-102">Adding Parameters That Process Command-Line Input</span></span>

<span data-ttu-id="ea1ea-103">Un'origine di input per un cmdlet è la riga di comando.</span><span class="sxs-lookup"><span data-stu-id="ea1ea-103">One source of input for a cmdlet is the command line.</span></span> <span data-ttu-id="ea1ea-104">Questo argomento descrive come aggiungere un parametro al cmdlet **Get-proc** , descritto in [creazione del primo cmdlet](./creating-a-cmdlet-without-parameters.md), in modo che il cmdlet possa elaborare l'input dal computer locale in base agli oggetti espliciti passati al cmdlet.</span><span class="sxs-lookup"><span data-stu-id="ea1ea-104">This topic describes how to add a parameter to the **Get-Proc** cmdlet (which is described in [Creating Your First Cmdlet](./creating-a-cmdlet-without-parameters.md)) so that the cmdlet can process input from the local computer based on explicit objects passed to the cmdlet.</span></span> <span data-ttu-id="ea1ea-105">Il cmdlet **Get-proc** descritto di seguito recupera i processi in base ai relativi nomi e quindi Visualizza le informazioni sui processi al prompt dei comandi.</span><span class="sxs-lookup"><span data-stu-id="ea1ea-105">The **Get-Proc** cmdlet described here retrieves processes based on their names, and then displays information about the processes at a command prompt.</span></span>

## <a name="defining-the-cmdlet-class"></a><span data-ttu-id="ea1ea-106">Definizione della classe cmdlet</span><span class="sxs-lookup"><span data-stu-id="ea1ea-106">Defining the Cmdlet Class</span></span>

<span data-ttu-id="ea1ea-107">Il primo passaggio nella creazione di cmdlet è la denominazione dei cmdlet e la dichiarazione della classe .NET Framework che implementa il cmdlet.</span><span class="sxs-lookup"><span data-stu-id="ea1ea-107">The first step in cmdlet creation is cmdlet naming and the declaration of the .NET Framework class that implements the cmdlet.</span></span> <span data-ttu-id="ea1ea-108">Questo cmdlet recupera le informazioni sul processo, quindi il nome del verbo scelto qui è "Get".</span><span class="sxs-lookup"><span data-stu-id="ea1ea-108">This cmdlet retrieves process information, so the verb name chosen here is "Get."</span></span> <span data-ttu-id="ea1ea-109">(Quasi tutti i tipi di cmdlet in grado di recuperare informazioni possono elaborare l'input della riga di comando). Per altre informazioni sui verbi di cmdlet approvati, vedere [nomi dei verbi di cmdlet](./approved-verbs-for-windows-powershell-commands.md).</span><span class="sxs-lookup"><span data-stu-id="ea1ea-109">(Almost any sort of cmdlet that is capable of retrieving information can process command-line input.) For more information about approved cmdlet verbs, see [Cmdlet Verb Names](./approved-verbs-for-windows-powershell-commands.md).</span></span>

<span data-ttu-id="ea1ea-110">Di seguito è illustrata la dichiarazione di classe per il cmdlet **Get-proc** .</span><span class="sxs-lookup"><span data-stu-id="ea1ea-110">Here's the class declaration for the **Get-Proc** cmdlet.</span></span> <span data-ttu-id="ea1ea-111">Informazioni dettagliate su questa definizione sono disponibili nella pagina relativa alla [creazione del primo cmdlet](./creating-a-cmdlet-without-parameters.md).</span><span class="sxs-lookup"><span data-stu-id="ea1ea-111">Details about this definition are provided in [Creating Your First Cmdlet](./creating-a-cmdlet-without-parameters.md).</span></span>

```csharp
[Cmdlet(VerbsCommon.Get, "proc")]
public class GetProcCommand: Cmdlet
```

```vb
<Cmdlet(VerbsCommon.Get, "Proc")> _
Public Class GetProcCommand
    Inherits Cmdlet
```

## <a name="declaring-parameters"></a><span data-ttu-id="ea1ea-112">Dichiarazione di parametri</span><span class="sxs-lookup"><span data-stu-id="ea1ea-112">Declaring Parameters</span></span>

<span data-ttu-id="ea1ea-113">Un parametro del cmdlet consente all'utente di fornire input al cmdlet.</span><span class="sxs-lookup"><span data-stu-id="ea1ea-113">A cmdlet parameter enables the user to provide input to the cmdlet.</span></span> <span data-ttu-id="ea1ea-114">Nell'esempio seguente **Get-proc** e `Get-Member` sono i nomi dei cmdlet Pipelined e `MemberType` è un parametro per il `Get-Member` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="ea1ea-114">In the following example, **Get-Proc** and `Get-Member` are the names of pipelined cmdlets, and `MemberType` is a parameter for the `Get-Member` cmdlet.</span></span> <span data-ttu-id="ea1ea-115">Il parametro ha l'argomento "Property".</span><span class="sxs-lookup"><span data-stu-id="ea1ea-115">The parameter has the argument "property."</span></span>

<span data-ttu-id="ea1ea-116">**PS > Get-proc; Proprietà `get-member`-MemberType**</span><span class="sxs-lookup"><span data-stu-id="ea1ea-116">**PS> get-proc ; `get-member` -membertype property**</span></span>

<span data-ttu-id="ea1ea-117">Per dichiarare i parametri per un cmdlet, è necessario definire prima le proprietà che rappresentano i parametri.</span><span class="sxs-lookup"><span data-stu-id="ea1ea-117">To declare parameters for a cmdlet, you must first define the properties that represent the parameters.</span></span> <span data-ttu-id="ea1ea-118">Nel cmdlet **Get-proc** , l'unico parametro è `Name`, che in questo caso rappresenta il nome dell'oggetto processo .NET Framework da recuperare.</span><span class="sxs-lookup"><span data-stu-id="ea1ea-118">In the **Get-Proc** cmdlet, the only parameter is `Name`, which in this case represents the name of the .NET Framework process object to retrieve.</span></span> <span data-ttu-id="ea1ea-119">Pertanto, la classe cmdlet definisce una proprietà di tipo stringa per accettare una matrice di nomi.</span><span class="sxs-lookup"><span data-stu-id="ea1ea-119">Therefore, the cmdlet class defines a property of type string to accept an array of names.</span></span>

<span data-ttu-id="ea1ea-120">Di seguito è illustrata la dichiarazione di parametro per il parametro `Name` del cmdlet **Get-proc** .</span><span class="sxs-lookup"><span data-stu-id="ea1ea-120">Here's the parameter declaration for the `Name` parameter of the **Get-Proc** cmdlet.</span></span>

```csharp
/// <summary>
/// Specify the cmdlet Name parameter.
/// </summary>
  [Parameter(Position = 0)]
  [ValidateNotNullOrEmpty]
  public string[] Name
  {
    get { return processNames; }
    set { processNames = value; }
  }
  private string[] processNames;

  #endregion Parameters
```

```vb
<Parameter(Position:=0), ValidateNotNullOrEmpty()> _
Public Property Name() As String()
    Get
        Return processNames
    End Get

    Set(ByVal value As String())
        processNames = value
    End Set

End Property
```

<span data-ttu-id="ea1ea-121">Per informare il runtime di Windows PowerShell che questa proprietà è il parametro `Name`, viene aggiunto un attributo [System. Management. Automation. ParameterAttribute](/dotnet/api/System.Management.Automation.ParameterAttribute) alla definizione della proprietà.</span><span class="sxs-lookup"><span data-stu-id="ea1ea-121">To inform the Windows PowerShell runtime that this property is the `Name` parameter, a [System.Management.Automation.Parameterattribute](/dotnet/api/System.Management.Automation.ParameterAttribute) attribute is added to the property definition.</span></span> <span data-ttu-id="ea1ea-122">La sintassi di base per la dichiarazione di questo attributo è `[Parameter()]`.</span><span class="sxs-lookup"><span data-stu-id="ea1ea-122">The basic syntax for declaring this attribute is `[Parameter()]`.</span></span>

> [!NOTE]
> <span data-ttu-id="ea1ea-123">Un parametro deve essere contrassegnato in modo esplicito come Public.</span><span class="sxs-lookup"><span data-stu-id="ea1ea-123">A parameter must be explicitly marked as public.</span></span> <span data-ttu-id="ea1ea-124">Parametri non contrassegnati come Public default come Internal e non vengono trovati dal runtime di Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="ea1ea-124">Parameters that are not marked as public default to internal and are not found by the Windows PowerShell runtime.</span></span>

<span data-ttu-id="ea1ea-125">Questo cmdlet usa una matrice di stringhe per il parametro `Name`.</span><span class="sxs-lookup"><span data-stu-id="ea1ea-125">This cmdlet uses an array of strings for the `Name` parameter.</span></span> <span data-ttu-id="ea1ea-126">Se possibile, il cmdlet deve anche definire un parametro come matrice, perché consente al cmdlet di accettare più di un elemento.</span><span class="sxs-lookup"><span data-stu-id="ea1ea-126">If possible, your cmdlet should also define a parameter as an array, because this allows the cmdlet to accept more than one item.</span></span>

#### <a name="things-to-remember-about-parameter-definitions"></a><span data-ttu-id="ea1ea-127">Aspetti da ricordare sulle definizioni dei parametri</span><span class="sxs-lookup"><span data-stu-id="ea1ea-127">Things to Remember About Parameter Definitions</span></span>

- <span data-ttu-id="ea1ea-128">I nomi di parametro e i tipi di dati predefiniti di Windows PowerShell devono essere riutilizzati il più possibile per garantire la compatibilità del cmdlet con i cmdlet di Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="ea1ea-128">Predefined Windows PowerShell parameter names and data types should be reused as much as possible to ensure that your cmdlet is compatible with Windows PowerShell cmdlets.</span></span> <span data-ttu-id="ea1ea-129">Se, ad esempio, tutti i cmdlet usano il nome del parametro `Id` predefinito per identificare una risorsa, l'utente potrà facilmente comprendere il significato del parametro, indipendentemente dal cmdlet usato.</span><span class="sxs-lookup"><span data-stu-id="ea1ea-129">For example, if all cmdlets use the predefined `Id` parameter name to identify a resource, user will easily understand the meaning of the parameter, regardless of what cmdlet they are using.</span></span> <span data-ttu-id="ea1ea-130">Fondamentalmente, i nomi di parametro seguono le stesse regole usate per i nomi delle variabili nella Common Language Runtime (CLR).</span><span class="sxs-lookup"><span data-stu-id="ea1ea-130">Basically, parameter names follow the same rules as those used for variable names in the common language runtime (CLR).</span></span> <span data-ttu-id="ea1ea-131">Per ulteriori informazioni sulla denominazione dei parametri, vedere [cmdlet parameter names](https://msdn.microsoft.com/en-us/c4500737-0a05-4d01-911b-394424c65bfb).</span><span class="sxs-lookup"><span data-stu-id="ea1ea-131">For more information about parameter naming, see [Cmdlet Parameter Names](https://msdn.microsoft.com/en-us/c4500737-0a05-4d01-911b-394424c65bfb).</span></span>

- <span data-ttu-id="ea1ea-132">Windows PowerShell riserva alcuni nomi di parametro per offrire un'esperienza utente coerente.</span><span class="sxs-lookup"><span data-stu-id="ea1ea-132">Windows PowerShell reserves a few parameter names to provide a consistent user experience.</span></span> <span data-ttu-id="ea1ea-133">Non usare questi nomi di parametro: `WhatIf`, `Confirm`, `Verbose`, `Debug`, `Warn`, `ErrorAction`, `ErrorVariable`, `OutVariable`e `OutBuffer`.</span><span class="sxs-lookup"><span data-stu-id="ea1ea-133">Do not use these parameter names: `WhatIf`, `Confirm`, `Verbose`, `Debug`, `Warn`, `ErrorAction`, `ErrorVariable`, `OutVariable`, and `OutBuffer`.</span></span> <span data-ttu-id="ea1ea-134">Sono inoltre riservati gli alias seguenti per i nomi dei parametri: `vb`, `db`, `ea`, `ev`, `ov`e `ob`.</span><span class="sxs-lookup"><span data-stu-id="ea1ea-134">Additionally, the following aliases for these parameter names are reserved: `vb`, `db`, `ea`, `ev`, `ov`, and `ob`.</span></span>

- <span data-ttu-id="ea1ea-135">`Name` è un nome di parametro semplice e comune, consigliato per l'uso nei cmdlet.</span><span class="sxs-lookup"><span data-stu-id="ea1ea-135">`Name` is a simple and common parameter name, recommended for use in your cmdlets.</span></span> <span data-ttu-id="ea1ea-136">È preferibile scegliere un nome di parametro simile a quello di un nome complesso univoco per un cmdlet specifico e difficile da ricordare.</span><span class="sxs-lookup"><span data-stu-id="ea1ea-136">It is better to choose a parameter name like this than a complex name that is unique to a specific cmdlet and hard to remember.</span></span>

- <span data-ttu-id="ea1ea-137">I parametri non fanno distinzione tra maiuscole e minuscole in Windows PowerShell, anche se per impostazione predefinita la shell conserva il caso.</span><span class="sxs-lookup"><span data-stu-id="ea1ea-137">Parameters are case-insensitive in Windows PowerShell, although by default the shell preserves case.</span></span> <span data-ttu-id="ea1ea-138">La distinzione tra maiuscole e minuscole degli argomenti dipende dall'operazione del cmdlet.</span><span class="sxs-lookup"><span data-stu-id="ea1ea-138">Case-sensitivity of the arguments depends on the operation of the cmdlet.</span></span> <span data-ttu-id="ea1ea-139">Gli argomenti vengono passati a un parametro come specificato nella riga di comando.</span><span class="sxs-lookup"><span data-stu-id="ea1ea-139">Arguments are passed to a parameter as specified at the command line.</span></span>

- <span data-ttu-id="ea1ea-140">Per esempi di altre dichiarazioni di parametro, vedere [parametri dei cmdlet](./cmdlet-parameters.md).</span><span class="sxs-lookup"><span data-stu-id="ea1ea-140">For examples of other parameter declarations, see [Cmdlet Parameters](./cmdlet-parameters.md).</span></span>

## <a name="declaring-parameters-as-positional-or-named"></a><span data-ttu-id="ea1ea-141">Dichiarazione di parametri come posizionale o con nome</span><span class="sxs-lookup"><span data-stu-id="ea1ea-141">Declaring Parameters as Positional or Named</span></span>

<span data-ttu-id="ea1ea-142">Un cmdlet deve impostare ogni parametro come parametro posizionale o denominato.</span><span class="sxs-lookup"><span data-stu-id="ea1ea-142">A cmdlet must set each parameter as either a positional or named parameter.</span></span> <span data-ttu-id="ea1ea-143">Entrambi i tipi di parametri accettano argomenti singoli, più argomenti separati da virgole e impostazioni booleane.</span><span class="sxs-lookup"><span data-stu-id="ea1ea-143">Both kinds of parameters accept single arguments, multiple arguments separated by commas, and Boolean settings.</span></span> <span data-ttu-id="ea1ea-144">Un parametro booleano, detto anche *opzione*, gestisce solo le impostazioni booleane.</span><span class="sxs-lookup"><span data-stu-id="ea1ea-144">A Boolean parameter, also called a *switch*, handles only Boolean settings.</span></span> <span data-ttu-id="ea1ea-145">L'opzione viene usata per determinare la presenza del parametro.</span><span class="sxs-lookup"><span data-stu-id="ea1ea-145">The switch is used to determine the presence of the parameter.</span></span> <span data-ttu-id="ea1ea-146">Il valore predefinito consigliato è `false`.</span><span class="sxs-lookup"><span data-stu-id="ea1ea-146">The recommended default is `false`.</span></span>

<span data-ttu-id="ea1ea-147">Il cmdlet **Get-proc** di esempio definisce il parametro `Name` come parametro posizionale con la posizione 0.</span><span class="sxs-lookup"><span data-stu-id="ea1ea-147">The sample **Get-Proc** cmdlet defines the `Name` parameter as a positional parameter with position 0.</span></span> <span data-ttu-id="ea1ea-148">Questo significa che il primo argomento immesso dall'utente nella riga di comando viene inserito automaticamente per questo parametro.</span><span class="sxs-lookup"><span data-stu-id="ea1ea-148">This means that the first argument the user enters on the command line is automatically inserted for this parameter.</span></span> <span data-ttu-id="ea1ea-149">Se si vuole definire un parametro denominato, per il quale l'utente deve specificare il nome del parametro dalla riga di comando, lasciare la parola chiave `Position` fuori dalla dichiarazione dell'attributo.</span><span class="sxs-lookup"><span data-stu-id="ea1ea-149">If you want to define a named parameter, for which the user must specify the parameter name from the command line, leave the `Position` keyword out of the attribute declaration.</span></span>

> [!NOTE]
> <span data-ttu-id="ea1ea-150">A meno che non sia necessario denominare i parametri, è consigliabile rendere posizionali i parametri più usati in modo che gli utenti non debbano digitare il nome del parametro.</span><span class="sxs-lookup"><span data-stu-id="ea1ea-150">Unless parameters must be named, we recommend that you make the most-used parameters positional so that users will not have to type the parameter name.</span></span>

## <a name="declaring-parameters-as-mandatory-or-optional"></a><span data-ttu-id="ea1ea-151">Dichiarazione dei parametri come obbligatoria o facoltativa</span><span class="sxs-lookup"><span data-stu-id="ea1ea-151">Declaring Parameters as Mandatory or Optional</span></span>

<span data-ttu-id="ea1ea-152">Un cmdlet deve impostare ogni parametro come parametro facoltativo o obbligatorio.</span><span class="sxs-lookup"><span data-stu-id="ea1ea-152">A cmdlet must set each parameter as either an optional or a mandatory parameter.</span></span> <span data-ttu-id="ea1ea-153">Nel cmdlet **Get-proc** di esempio, il parametro `Name` viene definito come facoltativo perché la parola chiave `Mandatory` non è impostata nella dichiarazione dell'attributo.</span><span class="sxs-lookup"><span data-stu-id="ea1ea-153">In the sample **Get-Proc** cmdlet, the `Name` parameter is defined as optional because the `Mandatory` keyword is not set in the attribute declaration.</span></span>

## <a name="supporting-parameter-validation"></a><span data-ttu-id="ea1ea-154">Supporto della convalida di parametri</span><span class="sxs-lookup"><span data-stu-id="ea1ea-154">Supporting Parameter Validation</span></span>

<span data-ttu-id="ea1ea-155">Il cmdlet **Get-proc** di esempio aggiunge un attributo di convalida di input, [System. Management. Automation. Validatenotnulloremptyattribute](/dotnet/api/System.Management.Automation.ValidateNotNullOrEmptyAttribute), al parametro `Name` per abilitare la convalida che l'input non sia `null` né vuoto.</span><span class="sxs-lookup"><span data-stu-id="ea1ea-155">The sample **Get-Proc** cmdlet adds an input validation attribute, [System.Management.Automation.Validatenotnulloremptyattribute](/dotnet/api/System.Management.Automation.ValidateNotNullOrEmptyAttribute), to the `Name` parameter to enable validation that the input is neither `null` nor empty.</span></span> <span data-ttu-id="ea1ea-156">Questo attributo è uno dei diversi attributi di convalida forniti da Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="ea1ea-156">This attribute is one of several validation attributes provided by Windows PowerShell.</span></span> <span data-ttu-id="ea1ea-157">Per esempi di altri attributi di convalida, vedere [convalida dell'input dei parametri](./validating-parameter-input.md).</span><span class="sxs-lookup"><span data-stu-id="ea1ea-157">For examples of other validation attributes, see [Validating Parameter Input](./validating-parameter-input.md).</span></span>

```
[Parameter(Position = 0)]
[ValidateNotNullOrEmpty]
public string[] Name
```

## <a name="overriding-an-input-processing-method"></a><span data-ttu-id="ea1ea-158">Override di un metodo di elaborazione dell'input</span><span class="sxs-lookup"><span data-stu-id="ea1ea-158">Overriding an Input Processing Method</span></span>

<span data-ttu-id="ea1ea-159">Se il cmdlet prevede di gestire l'input della riga di comando, deve eseguire l'override dei metodi di elaborazione dell'input appropriati.</span><span class="sxs-lookup"><span data-stu-id="ea1ea-159">If your cmdlet is to handle command-line input, it must override the appropriate input processing methods.</span></span> <span data-ttu-id="ea1ea-160">I metodi di elaborazione dell'input di base sono introdotti nella [creazione del primo cmdlet](./creating-a-cmdlet-without-parameters.md).</span><span class="sxs-lookup"><span data-stu-id="ea1ea-160">The basic input processing methods are introduced in [Creating Your First Cmdlet](./creating-a-cmdlet-without-parameters.md).</span></span>

<span data-ttu-id="ea1ea-161">Il cmdlet **Get-proc** esegue l'override del metodo [System. Management. Automation. cmdlet. ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) per gestire l'input del parametro `Name` fornito dall'utente o da uno script.</span><span class="sxs-lookup"><span data-stu-id="ea1ea-161">The **Get-Proc** cmdlet overrides the [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) method to handle the `Name` parameter input provided by the user or a script.</span></span> <span data-ttu-id="ea1ea-162">Questo metodo ottiene i processi per ogni nome di processo richiesto oppure tutti per i processi se non viene specificato alcun nome.</span><span class="sxs-lookup"><span data-stu-id="ea1ea-162">This method gets the processes for each requested process name, or all for processes if no name is provided.</span></span> <span data-ttu-id="ea1ea-163">Si noti che in [System. Management. Automation. cmdlet. ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord)la chiamata a [System. Management. Automation. cmdlet. WriteObject% 28System. Object% 2CSystem. Boolean %29](/dotnet/api/system.management.automation.cmdlet.writeobject?view=powershellsdk-1.1.0#System_Management_Automation_Cmdlet_WriteObject_System_Object_System_Boolean_) è il meccanismo di output per l'invio di oggetti di output alla pipeline.</span><span class="sxs-lookup"><span data-stu-id="ea1ea-163">Notice that in [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord), the call to [System.Management.Automation.Cmdlet.WriteObject%28System.Object%2CSystem.Boolean%29](/dotnet/api/system.management.automation.cmdlet.writeobject?view=powershellsdk-1.1.0#System_Management_Automation_Cmdlet_WriteObject_System_Object_System_Boolean_) is the output mechanism for sending output objects to the pipeline.</span></span> <span data-ttu-id="ea1ea-164">Il secondo parametro di questa chiamata, `enumerateCollection`, viene impostato su `true` per informare il runtime di Windows PowerShell di enumerare la matrice di output degli oggetti processo e scrivere un processo alla volta nella riga di comando.</span><span class="sxs-lookup"><span data-stu-id="ea1ea-164">The second parameter of this call, `enumerateCollection`, is set to `true` to inform the Windows PowerShell runtime to enumerate the output array of process objects and write one process at a time to the command line.</span></span>

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
    }
  }
}
```

```vb
Protected Overrides Sub ProcessRecord()

    '/ If no process names are passed to the cmdlet, get all processes.
    If processNames Is Nothing Then
        Dim processes As Process()
        processes = Process.GetProcesses()
    End If

    '/ If process names are specified, write the processes to the
    '/ pipeline to display them or make them available to the next cmdlet.

    For Each name As String In processNames
        '/ The second parameter of this call tells PowerShell to enumerate the
        '/ array, and send one process at a time to the pipeline.
        WriteObject(Process.GetProcessesByName(name), True)
    Next

End Sub 'ProcessRecord
```

## <a name="code-sample"></a><span data-ttu-id="ea1ea-165">Codice di esempio</span><span class="sxs-lookup"><span data-stu-id="ea1ea-165">Code Sample</span></span>

<span data-ttu-id="ea1ea-166">Per il codice C# di esempio completo, vedere l' [esempio GetProcessSample02](./getprocesssample02-sample.md).</span><span class="sxs-lookup"><span data-stu-id="ea1ea-166">For the complete C# sample code, see [GetProcessSample02 Sample](./getprocesssample02-sample.md).</span></span>

## <a name="defining-object-types-and-formatting"></a><span data-ttu-id="ea1ea-167">Definizione di tipi di oggetti e formattazione</span><span class="sxs-lookup"><span data-stu-id="ea1ea-167">Defining Object Types and Formatting</span></span>

<span data-ttu-id="ea1ea-168">Windows PowerShell passa informazioni tra i cmdlet usando oggetti .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="ea1ea-168">Windows PowerShell passes information between cmdlets by using .NET Framework objects.</span></span> <span data-ttu-id="ea1ea-169">Di conseguenza, un cmdlet potrebbe avere la necessità di definire un proprio tipo oppure un cmdlet potrebbe dover estendere un tipo esistente fornito da un altro cmdlet.</span><span class="sxs-lookup"><span data-stu-id="ea1ea-169">Consequently, a cmdlet might need to define its own type, or a cmdlet might need to extend an existing type provided by another cmdlet.</span></span> <span data-ttu-id="ea1ea-170">Per ulteriori informazioni sulla definizione di nuovi tipi o sull'estensione di tipi esistenti, vedere [estensione di tipi di oggetti e formattazione](https://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351).</span><span class="sxs-lookup"><span data-stu-id="ea1ea-170">For more information about defining new types or extending existing types, see [Extending Object Types and Formatting](https://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351).</span></span>

## <a name="building-the-cmdlet"></a><span data-ttu-id="ea1ea-171">Compilazione del cmdlet</span><span class="sxs-lookup"><span data-stu-id="ea1ea-171">Building the Cmdlet</span></span>

<span data-ttu-id="ea1ea-172">Dopo aver implementato un cmdlet, è necessario registrarlo con Windows PowerShell tramite uno snap-in di Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="ea1ea-172">After you implement a cmdlet, you must register it with Windows PowerShell by using a Windows PowerShell snap-in.</span></span> <span data-ttu-id="ea1ea-173">Per ulteriori informazioni sulla registrazione dei cmdlet, vedere [come registrare i cmdlet, i provider e le applicazioni host](https://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c).</span><span class="sxs-lookup"><span data-stu-id="ea1ea-173">For more information about registering cmdlets, see [How to Register Cmdlets, Providers, and Host Applications](https://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c).</span></span>

## <a name="testing-the-cmdlet"></a><span data-ttu-id="ea1ea-174">Test del cmdlet</span><span class="sxs-lookup"><span data-stu-id="ea1ea-174">Testing the Cmdlet</span></span>

<span data-ttu-id="ea1ea-175">Quando il cmdlet viene registrato con Windows PowerShell, è possibile testarlo eseguendolo nella riga di comando.</span><span class="sxs-lookup"><span data-stu-id="ea1ea-175">When your cmdlet is registered with Windows PowerShell, you can test it by running it on the command line.</span></span> <span data-ttu-id="ea1ea-176">Ecco due modi per testare il codice per il cmdlet di esempio.</span><span class="sxs-lookup"><span data-stu-id="ea1ea-176">Here are two ways to test the code for the sample cmdlet.</span></span> <span data-ttu-id="ea1ea-177">Per ulteriori informazioni sull'utilizzo dei cmdlet dalla riga di comando, vedere [Introduzione con Windows PowerShell](/powershell/scripting/getting-started/getting-started-with-windows-powershell).</span><span class="sxs-lookup"><span data-stu-id="ea1ea-177">For more information about using cmdlets from the command line, see [Getting Started with Windows PowerShell](/powershell/scripting/getting-started/getting-started-with-windows-powershell).</span></span>

- <span data-ttu-id="ea1ea-178">Al prompt di Windows PowerShell usare il comando seguente per elencare il processo di Internet Explorer, denominato "IEXPLORE".</span><span class="sxs-lookup"><span data-stu-id="ea1ea-178">At the Windows PowerShell prompt, use the following command to list the Internet Explorer process, which is named "IEXPLORE."</span></span>

    ```powershell
    PS> get-proc -name iexplore
    ```

<span data-ttu-id="ea1ea-179">Viene visualizzato l'output seguente:</span><span class="sxs-lookup"><span data-stu-id="ea1ea-179">The following output appears.</span></span>

    ```
    Handles  NPM(K)  PM(K)   WS(K)  VS(M)  CPU(s)   Id   ProcessName
    -------  ------  -----   -----  -----   ------ --   -----------
        354      11  10036   18992    85   0.67   3284   iexplore
    ```

- <span data-ttu-id="ea1ea-180">Per elencare i processi di Internet Explorer, Outlook e Notepad denominati "IEXPLORE", "OUTLOOK" e "NOTEPAD", utilizzare il comando seguente.</span><span class="sxs-lookup"><span data-stu-id="ea1ea-180">To list the Internet Explorer, Outlook, and Notepad processes named "IEXPLORE," "OUTLOOK," and "NOTEPAD," use the following command.</span></span> <span data-ttu-id="ea1ea-181">Se sono presenti più processi, vengono visualizzati tutti.</span><span class="sxs-lookup"><span data-stu-id="ea1ea-181">If there are multiple processes, all of them are displayed.</span></span>

    ```powershell
    PS> get-proc -name iexplore, outlook, notepad
    ```

<span data-ttu-id="ea1ea-182">Viene visualizzato l'output seguente:</span><span class="sxs-lookup"><span data-stu-id="ea1ea-182">The following output appears.</span></span>

    ```
    Handles  NPM(K)  PM(K)   WS(K)  VS(M)  CPU(s)   Id   ProcessName
    -------  ------  -----   -----  -----  ------   --    -----------
        732      21  24696    5000    138   2.25  2288   iexplore
        715      19  20556   14116    136   1.78  3860   iexplore
       3917      62  74096   58112    468 191.56  1848   OUTLOOK
         39       2   1024    3280     30   0.09  1444   notepad
         39       2   1024     356     30   0.08  3396   notepad
    ```

## <a name="see-also"></a><span data-ttu-id="ea1ea-183">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="ea1ea-183">See Also</span></span>

[<span data-ttu-id="ea1ea-184">Aggiunta di parametri che elaborano l'input della pipeline</span><span class="sxs-lookup"><span data-stu-id="ea1ea-184">Adding Parameters that Process Pipeline Input</span></span>](./adding-parameters-that-process-pipeline-input.md)

[<span data-ttu-id="ea1ea-185">Creazione del primo cmdlet</span><span class="sxs-lookup"><span data-stu-id="ea1ea-185">Creating Your First Cmdlet</span></span>](./creating-a-cmdlet-without-parameters.md)

[<span data-ttu-id="ea1ea-186">Estensione di tipi di oggetti e formattazione</span><span class="sxs-lookup"><span data-stu-id="ea1ea-186">Extending Object Types and Formatting</span></span>](https://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351)

[<span data-ttu-id="ea1ea-187">Come registrare cmdlet, provider e applicazioni host</span><span class="sxs-lookup"><span data-stu-id="ea1ea-187">How to Register Cmdlets, Providers, and Host Applications</span></span>](https://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c)

<span data-ttu-id="ea1ea-188">[Windows PowerShell Reference](../windows-powershell-reference.md) (Guida di riferimento di PowerShell)</span><span class="sxs-lookup"><span data-stu-id="ea1ea-188">[Windows PowerShell Reference](../windows-powershell-reference.md)</span></span>

[<span data-ttu-id="ea1ea-189">Esempi di cmdlet</span><span class="sxs-lookup"><span data-stu-id="ea1ea-189">Cmdlet Samples</span></span>](./cmdlet-samples.md)
