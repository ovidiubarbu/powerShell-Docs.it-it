---
title: Creazione di un cmdlet per accedere a un archivio dati
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.openlocfilehash: 3096965ba9f99f70994f2fb5b180cc58691b04f8
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/05/2019
ms.locfileid: "74415707"
---
# <a name="creating-a-cmdlet-to-access-a-data-store"></a><span data-ttu-id="da1b8-102">Creazione di un cmdlet per accedere a un archivio dati</span><span class="sxs-lookup"><span data-stu-id="da1b8-102">Creating a Cmdlet to Access a Data Store</span></span>

<span data-ttu-id="da1b8-103">In questa sezione viene descritto come creare un cmdlet per accedere ai dati archiviati tramite un provider di Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="da1b8-103">This section describes how to create a cmdlet that accesses stored data by way of a Windows PowerShell provider.</span></span> <span data-ttu-id="da1b8-104">Questo tipo di cmdlet usa l'infrastruttura del provider di Windows PowerShell del runtime di Windows PowerShell e, di conseguenza, la classe cmdlet deve derivare dalla classe di base [System. Management. Automation. PSCmdlet](/dotnet/api/System.Management.Automation.PSCmdlet) .</span><span class="sxs-lookup"><span data-stu-id="da1b8-104">This type of cmdlet uses the Windows PowerShell provider infrastructure of the Windows PowerShell runtime and, therefore, the cmdlet class must derive from the [System.Management.Automation.PSCmdlet](/dotnet/api/System.Management.Automation.PSCmdlet) base class.</span></span>

<span data-ttu-id="da1b8-105">Il cmdlet Select-Str descritto qui può individuare e selezionare le stringhe in un file o in un oggetto.</span><span class="sxs-lookup"><span data-stu-id="da1b8-105">The Select-Str cmdlet described here can locate and select strings in a file or object.</span></span> <span data-ttu-id="da1b8-106">I modelli utilizzati per identificare la stringa possono essere specificati in modo esplicito tramite il parametro `Path` del cmdlet o in modo implicito tramite il parametro `Script`.</span><span class="sxs-lookup"><span data-stu-id="da1b8-106">The patterns used to identify the string can be specified explicitly through the `Path` parameter of the cmdlet or implicitly through the `Script` parameter.</span></span>

<span data-ttu-id="da1b8-107">Il cmdlet è progettato per usare qualsiasi provider di Windows PowerShell che deriva da [System. Management. Automation. provider. Icontentcmdletprovider](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider).</span><span class="sxs-lookup"><span data-stu-id="da1b8-107">The cmdlet is designed to use any Windows PowerShell provider that derives from [System.Management.Automation.Provider.Icontentcmdletprovider](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider).</span></span> <span data-ttu-id="da1b8-108">Ad esempio, il cmdlet può specificare il provider FileSystem o il provider di variabili fornito da Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="da1b8-108">For example, the cmdlet can specify the FileSystem provider or the Variable provider that is provided by Windows PowerShell.</span></span> <span data-ttu-id="da1b8-109">Per ulteriori informazioni sui provider aboutWindows PowerShell, vedere [progettazione del provider di Windows PowerShell](../prog-guide/designing-your-windows-powershell-provider.md).</span><span class="sxs-lookup"><span data-stu-id="da1b8-109">For more information aboutWindows PowerShell providers, see [Designing Your Windows PowerShell provider](../prog-guide/designing-your-windows-powershell-provider.md).</span></span>

## <a name="defining-the-cmdlet-class"></a><span data-ttu-id="da1b8-110">Definizione della classe cmdlet</span><span class="sxs-lookup"><span data-stu-id="da1b8-110">Defining the Cmdlet Class</span></span>

<span data-ttu-id="da1b8-111">Il primo passaggio nella creazione di cmdlet è sempre il nome del cmdlet e la dichiarazione della classe .NET che implementa il cmdlet.</span><span class="sxs-lookup"><span data-stu-id="da1b8-111">The first step in cmdlet creation is always naming the cmdlet and declaring the .NET class that implements the cmdlet.</span></span> <span data-ttu-id="da1b8-112">Questo cmdlet rileva determinate stringhe, quindi il nome del verbo scelto qui è "Select", definito dalla classe [System. Management. Automation. Verbscommon](/dotnet/api/System.Management.Automation.VerbsCommon) .</span><span class="sxs-lookup"><span data-stu-id="da1b8-112">This cmdlet detects certain strings, so the verb name chosen here is "Select", defined by the [System.Management.Automation.Verbscommon](/dotnet/api/System.Management.Automation.VerbsCommon) class.</span></span> <span data-ttu-id="da1b8-113">Il nome del sostantivo "Str" viene usato perché il cmdlet agisce sulle stringhe.</span><span class="sxs-lookup"><span data-stu-id="da1b8-113">The noun name "Str" is used because the cmdlet acts upon strings.</span></span> <span data-ttu-id="da1b8-114">Nella dichiarazione seguente si noti che il verbo del cmdlet e il nome del sostantivo sono riflessi nel nome della classe cmdlet.</span><span class="sxs-lookup"><span data-stu-id="da1b8-114">In the declaration below, note that the cmdlet verb and noun name are reflected in the name of the cmdlet class.</span></span> <span data-ttu-id="da1b8-115">Per altre informazioni sui verbi di cmdlet approvati, vedere [nomi dei verbi di cmdlet](./approved-verbs-for-windows-powershell-commands.md).</span><span class="sxs-lookup"><span data-stu-id="da1b8-115">For more information about approved cmdlet verbs, see [Cmdlet Verb Names](./approved-verbs-for-windows-powershell-commands.md).</span></span>

<span data-ttu-id="da1b8-116">La classe .NET per questo cmdlet deve derivare dalla classe di base [System. Management. Automation. PSCmdlet](/dotnet/api/System.Management.Automation.PSCmdlet) , perché fornisce il supporto necessario al runtime di Windows PowerShell per esporre l'infrastruttura del provider di Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="da1b8-116">The .NET class for this cmdlet must derive from the [System.Management.Automation.PSCmdlet](/dotnet/api/System.Management.Automation.PSCmdlet) base class, because it provides the support needed by the Windows PowerShell runtime to expose the Windows PowerShell provider infrastructure.</span></span> <span data-ttu-id="da1b8-117">Si noti che questo cmdlet usa anche le classi di espressioni regolari .NET Framework, ad esempio [System. Text. RegularExpressions. Regex](/dotnet/api/System.Text.RegularExpressions.Regex).</span><span class="sxs-lookup"><span data-stu-id="da1b8-117">Note that this cmdlet also makes use of the .NET Framework regular expressions classes, such as [System.Text.Regularexpressions.Regex](/dotnet/api/System.Text.RegularExpressions.Regex).</span></span>

<span data-ttu-id="da1b8-118">Il codice seguente è la definizione di classe per questo cmdlet Select-Str.</span><span class="sxs-lookup"><span data-stu-id="da1b8-118">The following code is the class definition for this Select-Str cmdlet.</span></span>

```csharp
[Cmdlet(VerbsCommon.Select, "Str", DefaultParameterSetName="PatternParameterSet")]
public class SelectStringCommand : PSCmdlet
```

<span data-ttu-id="da1b8-119">Questo cmdlet definisce un set di parametri predefinito aggiungendo la parola chiave `DefaultParameterSetName` attribute alla dichiarazione della classe.</span><span class="sxs-lookup"><span data-stu-id="da1b8-119">This cmdlet defines a default parameter set by adding the `DefaultParameterSetName` attribute keyword to the class declaration.</span></span> <span data-ttu-id="da1b8-120">Il set di parametri predefinito `PatternParameterSet` viene usato quando il parametro `Script` non è specificato.</span><span class="sxs-lookup"><span data-stu-id="da1b8-120">The default parameter set `PatternParameterSet` is used when the `Script` parameter is not specified.</span></span> <span data-ttu-id="da1b8-121">Per ulteriori informazioni su questo set di parametri, vedere il `Pattern` e `Script` discussione dei parametri nella sezione seguente.</span><span class="sxs-lookup"><span data-stu-id="da1b8-121">For more information about this parameter set, see the `Pattern` and `Script` parameter discussion in the following section.</span></span>

## <a name="defining-parameters-for-data-access"></a><span data-ttu-id="da1b8-122">Definizione di parametri per l'accesso ai dati</span><span class="sxs-lookup"><span data-stu-id="da1b8-122">Defining Parameters for Data Access</span></span>

<span data-ttu-id="da1b8-123">Questo cmdlet definisce diversi parametri che consentono all'utente di accedere ed esaminare i dati archiviati.</span><span class="sxs-lookup"><span data-stu-id="da1b8-123">This cmdlet defines several parameters that allow the user to access and examine stored data.</span></span> <span data-ttu-id="da1b8-124">Questi parametri includono un parametro di `Path` che indica il percorso dell'archivio dati, un parametro di `Pattern` che specifica il modello da utilizzare nella ricerca e diversi altri parametri che supportano la modalità di esecuzione della ricerca.</span><span class="sxs-lookup"><span data-stu-id="da1b8-124">These parameters include a `Path` parameter that indicates the location of the data store, a `Pattern` parameter that specifies the pattern to be used in the search, and several other parameters that support how the search is performed.</span></span>

> [!NOTE]
> <span data-ttu-id="da1b8-125">Per ulteriori informazioni sulle nozioni di base sulla definizione dei parametri, vedere [aggiunta di parametri che elaborano l'input della riga di comando](./adding-parameters-that-process-command-line-input.md).</span><span class="sxs-lookup"><span data-stu-id="da1b8-125">For more information about the basics of defining parameters, see [Adding Parameters that Process Command Line Input](./adding-parameters-that-process-command-line-input.md).</span></span>

### <a name="declaring-the-path-parameter"></a><span data-ttu-id="da1b8-126">Dichiarazione del parametro path</span><span class="sxs-lookup"><span data-stu-id="da1b8-126">Declaring the Path Parameter</span></span>

<span data-ttu-id="da1b8-127">Per individuare l'archivio dati, questo cmdlet deve usare un percorso di Windows PowerShell per identificare il provider di Windows PowerShell progettato per accedere all'archivio dati.</span><span class="sxs-lookup"><span data-stu-id="da1b8-127">To locate the data store, this cmdlet must use a Windows PowerShell path to identify the Windows PowerShell provider that is designed to access the data store.</span></span> <span data-ttu-id="da1b8-128">Viene pertanto definito un parametro `Path` di tipo matrice di stringhe per indicare la posizione del provider.</span><span class="sxs-lookup"><span data-stu-id="da1b8-128">Therefore, it defines a `Path` parameter of type string array to indicate the location of the provider.</span></span>

```csharp
[Parameter(
           Position = 0,
           ParameterSetName = "ScriptParameterSet",
           Mandatory = true)]
[Parameter(
           Position = 0,
           ParameterSetName = "PatternParameterSet",
           ValueFromPipeline = true,
           Mandatory = true)]
           [Alias("PSPath")]
public string[] Path
{
  get { return paths; }
  set { paths = value; }
}
private string[] paths;
```

<span data-ttu-id="da1b8-129">Si noti che questo parametro appartiene a due set di parametri diversi e che dispone di un alias.</span><span class="sxs-lookup"><span data-stu-id="da1b8-129">Note that this parameter belongs to two different parameter sets and that it has an alias.</span></span>

<span data-ttu-id="da1b8-130">Due attributi [System. Management. Automation. ParameterAttribute](/dotnet/api/System.Management.Automation.ParameterAttribute) dichiarano che il parametro `Path` appartiene al `ScriptParameterSet` e al `PatternParameterSet`.</span><span class="sxs-lookup"><span data-stu-id="da1b8-130">Two [System.Management.Automation.Parameterattribute](/dotnet/api/System.Management.Automation.ParameterAttribute) attributes declare that the `Path` parameter belongs to the `ScriptParameterSet` and the `PatternParameterSet`.</span></span> <span data-ttu-id="da1b8-131">Per ulteriori informazioni sui set di parametri, vedere [aggiunta di set di parametri a un cmdlet](./adding-parameter-sets-to-a-cmdlet.md).</span><span class="sxs-lookup"><span data-stu-id="da1b8-131">For more information about parameter sets, see [Adding Parameter Sets to a Cmdlet](./adding-parameter-sets-to-a-cmdlet.md).</span></span>

<span data-ttu-id="da1b8-132">L'attributo [System. Management. Automation. AliasAttribute](/dotnet/api/System.Management.Automation.AliasAttribute) dichiara un alias di `PSPath` per il parametro del `Path`.</span><span class="sxs-lookup"><span data-stu-id="da1b8-132">The [System.Management.Automation.Aliasattribute](/dotnet/api/System.Management.Automation.AliasAttribute) attribute declares a `PSPath` alias for the `Path` parameter.</span></span> <span data-ttu-id="da1b8-133">La dichiarazione di questo alias è fortemente consigliata per coerenza con gli altri cmdlet che accedono ai provider di Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="da1b8-133">Declaring this alias is strongly recommended for consistency with other cmdlets that access Windows PowerShell providers.</span></span> <span data-ttu-id="da1b8-134">Per ulteriori informazioni sui percorsi di PowerShell per aboutWindows, vedere "concetti relativi ai percorsi di PowerShell" nel funzionamento di [Windows PowerShell](/previous-versions//ms714658(v=vs.85)).</span><span class="sxs-lookup"><span data-stu-id="da1b8-134">For more information aboutWindows PowerShell paths, see "PowerShell Path Concepts" in [How Windows PowerShell Works](/previous-versions//ms714658(v=vs.85)).</span></span>

### <a name="declaring-the-pattern-parameter"></a><span data-ttu-id="da1b8-135">Dichiarazione del parametro pattern</span><span class="sxs-lookup"><span data-stu-id="da1b8-135">Declaring the Pattern Parameter</span></span>

<span data-ttu-id="da1b8-136">Per specificare i criteri di ricerca, questo cmdlet dichiara un `Pattern` parametro che è una matrice di stringhe.</span><span class="sxs-lookup"><span data-stu-id="da1b8-136">To specify the patterns to search for, this cmdlet declares a `Pattern` parameter that is an array of strings.</span></span> <span data-ttu-id="da1b8-137">Un risultato positivo viene restituito quando uno dei modelli viene trovato nell'archivio dati.</span><span class="sxs-lookup"><span data-stu-id="da1b8-137">A positive result is returned when any of the patterns are found in the data store.</span></span> <span data-ttu-id="da1b8-138">Si noti che questi modelli possono essere compilati in una matrice di espressioni regolari compilate o una matrice di modelli di caratteri jolly usati per le ricerche letterali.</span><span class="sxs-lookup"><span data-stu-id="da1b8-138">Note that these patterns can be compiled into an array of compiled regular expressions or an array of wildcard patterns used for literal searches.</span></span>

```csharp
[Parameter(
           Position = 1,
           ParameterSetName = "PatternParameterSet",
           Mandatory = true)]
public string[] Pattern
{
  get { return patterns; }
  set { patterns = value; }
}
private string[] patterns;
private Regex[] regexPattern;
private WildcardPattern[] wildcardPattern;
```

<span data-ttu-id="da1b8-139">Quando si specifica questo parametro, il cmdlet usa il set di parametri predefinito `PatternParameterSet`.</span><span class="sxs-lookup"><span data-stu-id="da1b8-139">When this parameter is specified, the cmdlet uses the default parameter set `PatternParameterSet`.</span></span> <span data-ttu-id="da1b8-140">In questo caso, il cmdlet usa i criteri specificati qui per selezionare le stringhe.</span><span class="sxs-lookup"><span data-stu-id="da1b8-140">In this case, the cmdlet uses the patterns specified here to select strings.</span></span> <span data-ttu-id="da1b8-141">Al contrario, il parametro `Script` può essere utilizzato anche per fornire uno script che contiene i modelli.</span><span class="sxs-lookup"><span data-stu-id="da1b8-141">In contrast, the `Script` parameter could also be used to provide a script that contains the patterns.</span></span> <span data-ttu-id="da1b8-142">I parametri `Script` e `Pattern` definiscono due set di parametri distinti, quindi si escludono a vicenda.</span><span class="sxs-lookup"><span data-stu-id="da1b8-142">The `Script` and `Pattern` parameters define two separate parameter sets, so they are mutually exclusive.</span></span>

### <a name="declaring-search-support-parameters"></a><span data-ttu-id="da1b8-143">Dichiarazione dei parametri di supporto per la ricerca</span><span class="sxs-lookup"><span data-stu-id="da1b8-143">Declaring Search Support Parameters</span></span>

<span data-ttu-id="da1b8-144">Questo cmdlet definisce i parametri di supporto seguenti che possono essere utilizzati per modificare le funzionalità di ricerca del cmdlet.</span><span class="sxs-lookup"><span data-stu-id="da1b8-144">This cmdlet defines the following support parameters that can be used to modify the search capabilities of the cmdlet.</span></span>

<span data-ttu-id="da1b8-145">Il parametro `Script` specifica un blocco di script che può essere utilizzato per fornire un meccanismo di ricerca alternativo per il cmdlet.</span><span class="sxs-lookup"><span data-stu-id="da1b8-145">The `Script` parameter specifies a script block that can be used to provide an alternate search mechanism for the cmdlet.</span></span> <span data-ttu-id="da1b8-146">Lo script deve contenere i modelli usati per la corrispondenza e restituire un oggetto [System. Management. Automation. PSObject](/dotnet/api/System.Management.Automation.PSObject) .</span><span class="sxs-lookup"><span data-stu-id="da1b8-146">The script must contain the patterns used for matching and return a [System.Management.Automation.PSObject](/dotnet/api/System.Management.Automation.PSObject) object.</span></span> <span data-ttu-id="da1b8-147">Si noti che questo parametro è anche il parametro univoco che identifica il set di parametri `ScriptParameterSet`.</span><span class="sxs-lookup"><span data-stu-id="da1b8-147">Note that this parameter is also the unique parameter that identifies the `ScriptParameterSet` parameter set.</span></span> <span data-ttu-id="da1b8-148">Quando il runtime di Windows PowerShell Visualizza questo parametro, vengono usati solo i parametri che appartengono al set di parametri `ScriptParameterSet`.</span><span class="sxs-lookup"><span data-stu-id="da1b8-148">When the Windows PowerShell runtime sees this parameter, it uses only parameters that belong to the `ScriptParameterSet` parameter set.</span></span>

```csharp
[Parameter(
           Position = 1,
           ParameterSetName = "ScriptParameterSet",
           Mandatory = true)]
public ScriptBlock Script
{
  set { script = value; }
  get { return script; }
}
ScriptBlock script;
```

<span data-ttu-id="da1b8-149">Il parametro `SimpleMatch` è un parametro switch che indica se il cmdlet deve corrispondere in modo esplicito ai criteri specificati.</span><span class="sxs-lookup"><span data-stu-id="da1b8-149">The `SimpleMatch` parameter is a switch parameter that indicates whether the cmdlet is to explicitly match the patterns as they are supplied.</span></span> <span data-ttu-id="da1b8-150">Quando l'utente specifica il parametro nella riga di comando (`true`), il cmdlet usa i modelli così come vengono specificati.</span><span class="sxs-lookup"><span data-stu-id="da1b8-150">When the user specifies the parameter at the command line (`true`), the cmdlet uses the patterns as they are supplied.</span></span> <span data-ttu-id="da1b8-151">Se il parametro non viene specificato (`false`), il cmdlet usa le espressioni regolari.</span><span class="sxs-lookup"><span data-stu-id="da1b8-151">If the parameter is not specified (`false`), the cmdlet uses regular expressions.</span></span> <span data-ttu-id="da1b8-152">Il valore predefinito per questo parametro è `false`.</span><span class="sxs-lookup"><span data-stu-id="da1b8-152">The default for this parameter is `false`.</span></span>

```csharp
[Parameter]
public SwitchParameter SimpleMatch
{
  get { return simpleMatch; }
  set { simpleMatch = value; }
}
private bool simpleMatch;
```

<span data-ttu-id="da1b8-153">Il parametro `CaseSensitive` è un parametro switch che indica se viene eseguita una ricerca con distinzione tra maiuscole e minuscole.</span><span class="sxs-lookup"><span data-stu-id="da1b8-153">The `CaseSensitive` parameter is a switch parameter that indicates whether a case-sensitive search is performed.</span></span> <span data-ttu-id="da1b8-154">Quando l'utente specifica il parametro nella riga di comando (`true`), il cmdlet controlla la presenza di caratteri maiuscoli e minuscoli quando si confrontano i modelli.</span><span class="sxs-lookup"><span data-stu-id="da1b8-154">When the user specifies the parameter at the command line (`true`), the cmdlet checks for the uppercase and lowercase of characters when comparing patterns.</span></span> <span data-ttu-id="da1b8-155">Se il parametro non viene specificato (`false`), il cmdlet non distingue tra lettere maiuscole e minuscole.</span><span class="sxs-lookup"><span data-stu-id="da1b8-155">If the parameter is not specified (`false`), the cmdlet does not distinguish between uppercase and lowercase.</span></span> <span data-ttu-id="da1b8-156">Ad esempio, "MyFile" e "MyFile" verrebbero restituiti come risultati positivi.</span><span class="sxs-lookup"><span data-stu-id="da1b8-156">For example "MyFile" and "myfile" would both be returned as positive hits.</span></span> <span data-ttu-id="da1b8-157">Il valore predefinito per questo parametro è `false`.</span><span class="sxs-lookup"><span data-stu-id="da1b8-157">The default for this parameter is `false`.</span></span>

```csharp
[Parameter]
public SwitchParameter CaseSensitive
{
  get { return caseSensitive; }
  set { caseSensitive = value; }
}
private bool caseSensitive;
```

<span data-ttu-id="da1b8-158">I parametri `Exclude` e `Include` identificano gli elementi che sono esclusi esplicitamente da o inclusi nella ricerca.</span><span class="sxs-lookup"><span data-stu-id="da1b8-158">The `Exclude` and `Include` parameters identify items that are explicitly excluded from or included in the search.</span></span> <span data-ttu-id="da1b8-159">Per impostazione predefinita, il cmdlet eseguirà la ricerca di tutti gli elementi nell'archivio dati.</span><span class="sxs-lookup"><span data-stu-id="da1b8-159">By default, the cmdlet will search all items in the data store.</span></span> <span data-ttu-id="da1b8-160">Tuttavia, per limitare la ricerca eseguita dal cmdlet, questi parametri possono essere usati per indicare in modo esplicito gli elementi da includere nella ricerca o da omettere.</span><span class="sxs-lookup"><span data-stu-id="da1b8-160">However, to limit the search performed by the cmdlet, these parameters can be used to explicitly indicate items to be included in the search or omitted.</span></span>

```csharp
[Parameter]
public SwitchParameter CaseSensitive
{
  get { return caseSensitive; }
  set { caseSensitive = value; }
}
private bool caseSensitive;
```

```csharp
[Parameter]
[ValidateNotNullOrEmpty]
public string[] Include
{
  get
  {
    return includeStrings;
  }
  set
  {
    includeStrings = value;

    this.include = new WildcardPattern[includeStrings.Length];
    for (int i = 0; i < includeStrings.Length; i++)
    {
      this.include[i] = new WildcardPattern(includeStrings[i], WildcardOptions.IgnoreCase);
    }
  }
}

internal string[] includeStrings = null;
internal WildcardPattern[] include = null;
```

### <a name="declaring-parameter-sets"></a><span data-ttu-id="da1b8-161">Dichiarazione di set di parametri</span><span class="sxs-lookup"><span data-stu-id="da1b8-161">Declaring Parameter Sets</span></span>

<span data-ttu-id="da1b8-162">Questo cmdlet usa due set di parametri (`ScriptParameterSet` e `PatternParameterSet`, che è l'impostazione predefinita) come nomi di due set di parametri usati nell'accesso ai dati.</span><span class="sxs-lookup"><span data-stu-id="da1b8-162">This cmdlet uses two parameter sets (`ScriptParameterSet` and `PatternParameterSet`, which is the default) as the names of two parameter sets used in data access.</span></span> <span data-ttu-id="da1b8-163">`PatternParameterSet` è il set di parametri predefinito e viene usato quando viene specificato il parametro `Pattern`.</span><span class="sxs-lookup"><span data-stu-id="da1b8-163">`PatternParameterSet` is the default parameter set and is used when the `Pattern` parameter is specified.</span></span> <span data-ttu-id="da1b8-164">`ScriptParameterSet` viene utilizzato quando l'utente specifica un meccanismo di ricerca alternativo tramite il parametro `Script`.</span><span class="sxs-lookup"><span data-stu-id="da1b8-164">`ScriptParameterSet` is used when the user specifies an alternate search mechanism through the `Script` parameter.</span></span> <span data-ttu-id="da1b8-165">Per ulteriori informazioni sui set di parametri, vedere [aggiunta di set di parametri a un cmdlet](./adding-parameter-sets-to-a-cmdlet.md).</span><span class="sxs-lookup"><span data-stu-id="da1b8-165">For more information about parameter sets, see [Adding Parameter Sets to a Cmdlet](./adding-parameter-sets-to-a-cmdlet.md).</span></span>

## <a name="overriding-input-processing-methods"></a><span data-ttu-id="da1b8-166">Override dei metodi di elaborazione degli input</span><span class="sxs-lookup"><span data-stu-id="da1b8-166">Overriding Input Processing Methods</span></span>

<span data-ttu-id="da1b8-167">I cmdlet devono eseguire l'override di uno o più metodi di elaborazione dell'input per la classe [System. Management. Automation. PSCmdlet](/dotnet/api/System.Management.Automation.PSCmdlet) .</span><span class="sxs-lookup"><span data-stu-id="da1b8-167">Cmdlets must override one or more of the input processing methods for the [System.Management.Automation.PSCmdlet](/dotnet/api/System.Management.Automation.PSCmdlet) class.</span></span> <span data-ttu-id="da1b8-168">Per ulteriori informazioni sui metodi di elaborazione dell'input, vedere [creazione del primo cmdlet](./creating-a-cmdlet-without-parameters.md).</span><span class="sxs-lookup"><span data-stu-id="da1b8-168">For more information about the input processing methods, see [Creating Your First Cmdlet](./creating-a-cmdlet-without-parameters.md).</span></span>

<span data-ttu-id="da1b8-169">Questo cmdlet esegue l'override del metodo [System. Management. Automation. cmdlet. BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) per compilare una matrice di espressioni regolari compilate all'avvio.</span><span class="sxs-lookup"><span data-stu-id="da1b8-169">This cmdlet overrides the [System.Management.Automation.Cmdlet.BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) method to build an array of compiled regular expressions at startup.</span></span> <span data-ttu-id="da1b8-170">In questo modo si aumentano le prestazioni durante le ricerche che non utilizzano semplici corrispondenze.</span><span class="sxs-lookup"><span data-stu-id="da1b8-170">This increases performance during searches that do not use simple matching.</span></span>

```csharp
protected override void BeginProcessing()
{
  WriteDebug("Validating patterns.");
  if (patterns != null)
  {
    foreach(string pattern in patterns)
    {
      if (pattern == null)
      ThrowTerminatingError(new ErrorRecord(
                            new ArgumentNullException(
                            "Search pattern cannot be null."),
                            "NullSearchPattern",
                            ErrorCategory.InvalidArgument,
                            pattern)
                            );
    }

    WriteVerbose("Search pattern(s) are valid.");

    // If a simple match is not specified, then
    // compile the regular expressions once.
    if (!simpleMatch)
    {
      WriteDebug("Compiling search regular expressions.");

      RegexOptions regexOptions = RegexOptions.Compiled;
      if (!caseSensitive)
         regexOptions |= RegexOptions.Compiled;
      regexPattern = new Regex[patterns.Length];

      for (int i = 0; i < patterns.Length; i++)
      {
        try
        {
          regexPattern[i] = new Regex(patterns[i], regexOptions);
        }
        catch (ArgumentException ex)
        {
          ThrowTerminatingError(new ErrorRecord(
                        ex,
                        "InvalidRegularExpression",
                        ErrorCategory.InvalidArgument,
                        patterns[i]
                     ));
        }
      } //Loop through patterns to create RegEx objects.

      WriteVerbose("Pattern(s) compiled into regular expressions.");
    }// If not a simple match.

    // If a simple match is specified, then compile the
    // wildcard patterns once.
    else
    {
      WriteDebug("Compiling search wildcards.");

      WildcardOptions wildcardOptions = WildcardOptions.Compiled;

      if (!caseSensitive)
      {
        wildcardOptions |= WildcardOptions.IgnoreCase;
      }

      wildcardPattern = new WildcardPattern[patterns.Length];
      for (int i = 0; i < patterns.Length; i++)
      {
        wildcardPattern[i] =
                     new WildcardPattern(patterns[i], wildcardOptions);
      }

      WriteVerbose("Pattern(s) compiled into wildcard expressions.");
    }// If match is a simple match.
  }// If valid patterns are available.
}// End of function BeginProcessing().
```

<span data-ttu-id="da1b8-171">Questo cmdlet esegue anche l'override del metodo [System. Management. Automation. cmdlet. ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) per elaborare le selezioni di stringa che l'utente esegue nella riga di comando.</span><span class="sxs-lookup"><span data-stu-id="da1b8-171">This cmdlet also overrides the [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) method to process the string selections that the user makes on the command line.</span></span> <span data-ttu-id="da1b8-172">Scrive i risultati della selezione di stringa sotto forma di oggetto personalizzato chiamando un metodo **corrispondenza** privato.</span><span class="sxs-lookup"><span data-stu-id="da1b8-172">It writes the results of string selection in the form of a custom object by calling a private **MatchString** method.</span></span>

```csharp
protected override void ProcessRecord()
{
  UInt64 lineNumber = 0;
  MatchInfo result;
  ArrayList nonMatches = new ArrayList();

  // Walk the list of paths and search the contents for
  // any of the specified patterns.
  foreach (string psPath in paths)
  {
    // Once the filepaths are expanded, we may have more than one
    // path, so process all referenced paths.
    foreach(PathInfo path in
            SessionState.Path.GetResolvedPSPathFromPSPath(psPath)
           )
    {
      WriteVerbose("Processing path " + path.Path);

      // Check if the path represents one of the items to be
      // excluded. If so, continue to next path.
      if (!MeetsIncludeExcludeCriteria(path.ProviderPath))
         continue;

      // Get the content reader for the item(s) at the
      // specified path.
      Collection<IContentReader> readerCollection = null;
      try
      {
        readerCollection =
                    this.InvokeProvider.Content.GetReader(path.Path);
      }
      catch (PSNotSupportedException ex)
      {
        WriteError(new ErrorRecord(ex,
                   "ContentAccessNotSupported",
                    ErrorCategory.NotImplemented,
                    path.Path)
                   );
        return;
      }

      foreach(IContentReader reader in readerCollection)
      {
        // Reset the line number for this path.
        lineNumber = 0;

        // Read in a single block (line in case of a file)
        // from the object.
        IList items = reader.Read(1);

        // Read and process one block(line) at a time until
        // no more blocks(lines) exist.
        while (items != null && items.Count == 1)
        {
          // Increment the line number each time a line is
          // processed.
          lineNumber++;

          String message = String.Format("Testing line {0} : {1}",
                                        lineNumber, items[0]);

          WriteDebug(message);

          result = SelectString(items[0]);

          if (result != null)
          {
            result.Path = path.Path;
            result.LineNumber = lineNumber;

            WriteObject(result);
          }
          else
          {
            // Add the block(line) that did not match to the
            // collection of non matches , which will be stored
            // in the SessionState variable $NonMatches
            nonMatches.Add(items[0]);
          }

          // Get the next line from the object.
          items = reader.Read(1);

        }// While loop for reading one line at a time.
      }// Foreach loop for reader collection.
    }// Foreach loop for processing referenced paths.
  }// Foreach loop for walking of path list.

  // Store the list of non-matches in the
  // session state variable $NonMatches.
  try
  {
    this.SessionState.PSVariable.Set("NonMatches", nonMatches);
  }
  catch (SessionStateUnauthorizedAccessException ex)
  {
    WriteError(new ErrorRecord(ex,
               "CannotWriteVariableNonMatches",
               ErrorCategory.InvalidOperation,
               nonMatches)
              );
  }

}// End of protected override void ProcessRecord().
```

## <a name="accessing-content"></a><span data-ttu-id="da1b8-173">Accesso al contenuto</span><span class="sxs-lookup"><span data-stu-id="da1b8-173">Accessing Content</span></span>

<span data-ttu-id="da1b8-174">Il cmdlet deve aprire il provider indicato dal percorso di Windows PowerShell in modo che possa accedere ai dati.</span><span class="sxs-lookup"><span data-stu-id="da1b8-174">Your cmdlet must open the provider indicated by the Windows PowerShell path so that it can access the data.</span></span> <span data-ttu-id="da1b8-175">L'oggetto [System. Management. Automation. SessionState](/dotnet/api/System.Management.Automation.SessionState) per spazio viene usato per l'accesso al provider, mentre la proprietà [System. Management. Automation. PSCmdlet. Invokeprovider \*](/dotnet/api/System.Management.Automation.PSCmdlet.InvokeProvider) del cmdlet viene usata per aprire il provider.</span><span class="sxs-lookup"><span data-stu-id="da1b8-175">The [System.Management.Automation.Sessionstate](/dotnet/api/System.Management.Automation.SessionState) object for the runspace is used for access to the provider, while the [System.Management.Automation.PSCmdlet.Invokeprovider\*](/dotnet/api/System.Management.Automation.PSCmdlet.InvokeProvider) property of the cmdlet is used to open the provider.</span></span> <span data-ttu-id="da1b8-176">L'accesso al contenuto viene fornito tramite il recupero dell'oggetto [System. Management. Automation. Providerintrinsics](/dotnet/api/System.Management.Automation.ProviderIntrinsics) per il provider aperto.</span><span class="sxs-lookup"><span data-stu-id="da1b8-176">Access to content is provided by retrieval of the [System.Management.Automation.Providerintrinsics](/dotnet/api/System.Management.Automation.ProviderIntrinsics) object for the provider opened.</span></span>

<span data-ttu-id="da1b8-177">Questo cmdlet Select-Str di esempio usa la proprietà [System. Management. Automation. Providerintrinsics. Content \*](/dotnet/api/System.Management.Automation.ProviderIntrinsics.Content) per esporre il contenuto da analizzare.</span><span class="sxs-lookup"><span data-stu-id="da1b8-177">This sample Select-Str cmdlet uses the [System.Management.Automation.Providerintrinsics.Content\*](/dotnet/api/System.Management.Automation.ProviderIntrinsics.Content) property to expose the content to scan.</span></span> <span data-ttu-id="da1b8-178">Può quindi chiamare il metodo [System. Management. Automation. Contentcmdletproviderintrinsics. GetReader \*](/dotnet/api/System.Management.Automation.ContentCmdletProviderIntrinsics.GetReader) , passando il percorso necessario di Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="da1b8-178">It can then call the [System.Management.Automation.Contentcmdletproviderintrinsics.Getreader\*](/dotnet/api/System.Management.Automation.ContentCmdletProviderIntrinsics.GetReader) method, passing the required Windows PowerShell path.</span></span>

## <a name="code-sample"></a><span data-ttu-id="da1b8-179">Codice di esempio</span><span class="sxs-lookup"><span data-stu-id="da1b8-179">Code Sample</span></span>

<span data-ttu-id="da1b8-180">Il codice seguente illustra l'implementazione di questa versione di questo cmdlet Select-Str.</span><span class="sxs-lookup"><span data-stu-id="da1b8-180">The following code shows the implementation of this version of this Select-Str cmdlet.</span></span> <span data-ttu-id="da1b8-181">Si noti che questo codice include la classe cmdlet, i metodi privati utilizzati dal cmdlet e il codice di snap-in di Windows PowerShell utilizzato per registrare il cmdlet.</span><span class="sxs-lookup"><span data-stu-id="da1b8-181">Note that this code includes the cmdlet class, private methods used by the cmdlet, and the Windows PowerShell snap-in code used to register the cmdlet.</span></span> <span data-ttu-id="da1b8-182">Per ulteriori informazioni sulla registrazione del cmdlet, vedere [compilazione del cmdlet](#defining-the-cmdlet-class).</span><span class="sxs-lookup"><span data-stu-id="da1b8-182">For more information about registering the cmdlet, see [Building the Cmdlet](#defining-the-cmdlet-class).</span></span>

```csharp
//
// Copyright (c) 2006 Microsoft Corporation. All rights reserved.
//
// THIS CODE AND INFORMATION IS PROVIDED "AS IS" WITHOUT WARRANTY OF
// ANY KIND, EITHER EXPRESSED OR IMPLIED, INCLUDING BUT NOT LIMITED TO
// THE IMPLIED WARRANTIES OF MERCHANTABILITY AND/OR FITNESS FOR A
// PARTICULAR PURPOSE.
//
using System;
using System.Text.RegularExpressions;
using System.Collections;
using System.Collections.ObjectModel;
using System.Management.Automation;
using System.Management.Automation.Provider;
using System.ComponentModel;

namespace Microsoft.Samples.PowerShell.Commands
{
  #region SelectStringCommand
  /// <summary>
  /// This cmdlet searches through PSObjects for particular patterns.
  /// </summary>
  /// <remarks>
  /// This cmdlet can be used to search any object, such as a file or a
  /// variable, whose provider exposes methods for reading and writing
  /// content.
  /// </remarks>
  [Cmdlet(VerbsCommon.Select, "Str", DefaultParameterSetName="PatternParameterSet")]
  public class SelectStringCommand : PSCmdlet
  {
    #region Parameters
    /// <summary>
    /// Declare a Path parameter that specifies where the data is stored.
    /// This parameter must specify a PowerShell that indicates the
    /// PowerShell provider that is used to access the objects to be
    /// searched for matching patterns. This parameter should also have
    /// a PSPath alias to provide consistency with other cmdlets that use
    /// PowerShell providers.
    /// </summary>
    /// <value>Path of the object(s) to search.</value>
    [Parameter(
               Position = 0,
               ParameterSetName = "ScriptParameterSet",
               Mandatory = true)]
    [Parameter(
               Position = 0,
               ParameterSetName = "PatternParameterSet",
               ValueFromPipeline = true,
               Mandatory = true)]
               [Alias("PSPath")]
    public string[] Path
    {
      get { return paths; }
      set { paths = value; }
    }
    private string[] paths;

    /// <summary>
    /// Declare a Pattern parameter that specifies the pattern(s)
    /// used to find matching patterns in the string representation
    /// of the objects. A positive result will be returned
    /// if any of the patterns are found in the objects.
    /// </summary>
    /// <remarks>
    /// The patterns will be compiled into an array of wildcard
    /// patterns for a simple match (literal string matching),
    /// or the patterns will be converted into an array of compiled
    /// regular expressions.
    /// </remarks>
    /// <value>Array of patterns to search.</value>
    [Parameter(
               Position = 1,
               ParameterSetName = "PatternParameterSet",
               Mandatory = true)]
    public string[] Pattern
    {
      get { return patterns; }
      set { patterns = value; }
    }
    private string[] patterns;
    private Regex[] regexPattern;
    private WildcardPattern[] wildcardPattern;

    /// <summary>
    /// Declare a Script parameter that specifies a script block
    /// that is called to perform the matching operations
    /// instead of the matching performed by the cmdlet.
    /// </summary>
    /// <value>Script block that will be called for matching</value>
    [Parameter(
               Position = 1,
               ParameterSetName = "ScriptParameterSet",
               Mandatory = true)]
    public ScriptBlock Script
    {
      set { script = value; }
      get { return script; }
    }
    ScriptBlock script;

    /// <summary>
    /// Declare a switch parameter that specifies if the pattern(s) are used
    /// literally. If not (default), searching is
    /// done using regular expressions.
    /// </summary>
    /// <value>If True, a literal pattern is used.</value>
    [Parameter]
    public SwitchParameter SimpleMatch
    {
      get { return simpleMatch; }
      set { simpleMatch = value; }
    }
    private bool simpleMatch;

    /// <summary>
    /// Declare a switch parameter that specifies if a case-sensitive
    /// search is performed.  If not (default), a case-insensitive search
    /// is performed.
    /// </summary>
    /// <value>If True, a case-sensitive search is made.</value>
    [Parameter]
    public SwitchParameter CaseSensitive
    {
      get { return caseSensitive; }
      set { caseSensitive = value; }
    }
    private bool caseSensitive;

    /// <summary>
    /// Declare an Include parameter that species which
    /// specific items are searched.  When this parameter
    /// is used, items that are not listed here are omitted
    /// from the search.
    /// </summary>
    [Parameter]
    [ValidateNotNullOrEmpty]
    public string[] Include
    {
      get
      {
        return includeStrings;
      }
      set
      {
        includeStrings = value;

        this.include = new WildcardPattern[includeStrings.Length];
        for (int i = 0; i < includeStrings.Length; i++)
        {
          this.include[i] = new WildcardPattern(includeStrings[i], WildcardOptions.IgnoreCase);
        }
      }
    }

    internal string[] includeStrings = null;
    internal WildcardPattern[] include = null;

    /// <summary>
    /// Declare an Exclude parameter that species which
    /// specific items are omitted from the search.
    /// </summary>
    ///
    [Parameter]
    [ValidateNotNullOrEmpty]
    public string[] Exclude
    {
      get
      {
        return excludeStrings;
      }
      set
      {
        excludeStrings = value;

        this.exclude = new WildcardPattern[excludeStrings.Length];
        for (int i = 0; i < excludeStrings.Length; i++)
        {
          this.exclude[i] = new WildcardPattern(excludeStrings[i], WildcardOptions.IgnoreCase);
        }
      }
    }
    internal string[] excludeStrings;
    internal WildcardPattern[] exclude;

    #endregion Parameters

    #region Overrides
    /// <summary>
    /// If regular expressions are used for pattern matching,
    /// then build an array of compiled regular expressions
    /// at startup. This increases performance during scanning
    /// operations when simple matching is not used.
    /// </summary>
    protected override void BeginProcessing()
    {
      WriteDebug("Validating patterns.");
      if (patterns != null)
      {
        foreach(string pattern in patterns)
        {
          if (pattern == null)
          ThrowTerminatingError(new ErrorRecord(
                                new ArgumentNullException(
                                "Search pattern cannot be null."),
                                "NullSearchPattern",
                                ErrorCategory.InvalidArgument,
                                pattern)
                                );
        }

        WriteVerbose("Search pattern(s) are valid.");

        // If a simple match is not specified, then
        // compile the regular expressions once.
        if (!simpleMatch)
        {
          WriteDebug("Compiling search regular expressions.");

          RegexOptions regexOptions = RegexOptions.Compiled;
          if (!caseSensitive)
             regexOptions |= RegexOptions.Compiled;
          regexPattern = new Regex[patterns.Length];

          for (int i = 0; i < patterns.Length; i++)
          {
            try
            {
              regexPattern[i] = new Regex(patterns[i], regexOptions);
            }
            catch (ArgumentException ex)
            {
              ThrowTerminatingError(new ErrorRecord(
                            ex,
                            "InvalidRegularExpression",
                            ErrorCategory.InvalidArgument,
                            patterns[i]
                         ));
            }
          } //Loop through patterns to create RegEx objects.

          WriteVerbose("Pattern(s) compiled into regular expressions.");
        }// If not a simple match.

        // If a simple match is specified, then compile the
        // wildcard patterns once.
        else
        {
          WriteDebug("Compiling search wildcards.");

          WildcardOptions wildcardOptions = WildcardOptions.Compiled;

          if (!caseSensitive)
          {
            wildcardOptions |= WildcardOptions.IgnoreCase;
          }

          wildcardPattern = new WildcardPattern[patterns.Length];
          for (int i = 0; i < patterns.Length; i++)
          {
            wildcardPattern[i] =
                         new WildcardPattern(patterns[i], wildcardOptions);
          }

          WriteVerbose("Pattern(s) compiled into wildcard expressions.");
        }// If match is a simple match.
      }// If valid patterns are available.
    }// End of function BeginProcessing().

    /// <summary>
    /// Process the input and search for the specified patterns.
    /// </summary>
    protected override void ProcessRecord()
    {
      UInt64 lineNumber = 0;
      MatchInfo result;
      ArrayList nonMatches = new ArrayList();

      // Walk the list of paths and search the contents for
      // any of the specified patterns.
      foreach (string psPath in paths)
      {
        // Once the filepaths are expanded, we may have more than one
        // path, so process all referenced paths.
        foreach(PathInfo path in
                SessionState.Path.GetResolvedPSPathFromPSPath(psPath)
               )
        {
          WriteVerbose("Processing path " + path.Path);

          // Check if the path represents one of the items to be
          // excluded. If so, continue to next path.
          if (!MeetsIncludeExcludeCriteria(path.ProviderPath))
             continue;

          // Get the content reader for the item(s) at the
          // specified path.
          Collection<IContentReader> readerCollection = null;
          try
          {
            readerCollection =
                        this.InvokeProvider.Content.GetReader(path.Path);
          }
          catch (PSNotSupportedException ex)
          {
            WriteError(new ErrorRecord(ex,
                       "ContentAccessNotSupported",
                        ErrorCategory.NotImplemented,
                        path.Path)
                       );
            return;
          }

          foreach(IContentReader reader in readerCollection)
          {
            // Reset the line number for this path.
            lineNumber = 0;

            // Read in a single block (line in case of a file)
            // from the object.
            IList items = reader.Read(1);

            // Read and process one block(line) at a time until
            // no more blocks(lines) exist.
            while (items != null && items.Count == 1)
            {
              // Increment the line number each time a line is
              // processed.
              lineNumber++;

              String message = String.Format("Testing line {0} : {1}",
                                            lineNumber, items[0]);

              WriteDebug(message);

              result = SelectString(items[0]);

              if (result != null)
              {
                result.Path = path.Path;
                result.LineNumber = lineNumber;

                WriteObject(result);
              }
              else
              {
                // Add the block(line) that did not match to the
                // collection of non matches , which will be stored
                // in the SessionState variable $NonMatches
                nonMatches.Add(items[0]);
              }

              // Get the next line from the object.
              items = reader.Read(1);

            }// While loop for reading one line at a time.
          }// Foreach loop for reader collection.
        }// Foreach loop for processing referenced paths.
      }// Foreach loop for walking of path list.

      // Store the list of non-matches in the
      // session state variable $NonMatches.
      try
      {
        this.SessionState.PSVariable.Set("NonMatches", nonMatches);
      }
      catch (SessionStateUnauthorizedAccessException ex)
      {
        WriteError(new ErrorRecord(ex,
                   "CannotWriteVariableNonMatches",
                   ErrorCategory.InvalidOperation,
                   nonMatches)
                  );
      }

    }// End of protected override void ProcessRecord().
    #endregion Overrides

    #region PrivateMethods
    /// <summary>
    /// Check for a match using the input string and the pattern(s)
    /// specified.
    /// </summary>
    /// <param name="input">The string to test.</param>
    /// <returns>MatchInfo object containing information about
    /// result of a match</returns>
    private MatchInfo SelectString(object input)
    {
      string line = null;

      try
      {
        // Convert the object to a string type
        // safely using language support methods
        line = (string)LanguagePrimitives.ConvertTo(
                                                    input,
                                                    typeof(string)
                                                    );
        line = line.Trim(' ','\t');
      }
      catch (PSInvalidCastException ex)
      {
        WriteError(new ErrorRecord(
                   ex,
                   "CannotCastObjectToString",
                   ErrorCategory.InvalidOperation,
                   input)
                   );

        return null;
      }

      MatchInfo result = null;

      // If a scriptblock has been specified, call it
      // with the path for processing.  It will return
      // one object.
      if (script != null)
      {
        WriteDebug("Executing script block.");

        Collection<PSObject> psObjects =
                             script.Invoke(
                                           line,
                                           simpleMatch,
                                           caseSensitive
                                          );

        foreach (PSObject psObject in psObjects)
        {
          if (LanguagePrimitives.IsTrue(psObject))
          {
            result = new MatchInfo();
            result.Line = line;
            result.IgnoreCase = !caseSensitive;

            break;
          } //End of If.
        } //End ForEach loop.
      } // End of If if script exists.

      // If script block exists, see if this line matches any
      // of the match patterns.
      else
      {
        int patternIndex = 0;

        while (patternIndex < patterns.Length)
        {
          if ((simpleMatch &&
              wildcardPattern[patternIndex].IsMatch(line))
              || (regexPattern != null
              && regexPattern[patternIndex].IsMatch(line))
             )
          {
            result = new MatchInfo();
            result.IgnoreCase = !caseSensitive;
            result.Line = line;
            result.Pattern = patterns[patternIndex];

            break;
          }

          patternIndex++;

        }// While loop through patterns.
      }// Else for no script block specified.

      return result;

    }// End of SelectString

    /// <summary>
    /// Check whether the supplied name meets the include/exclude criteria.
    /// That is - it's on the include list if the include list was
    /// specified, and not on the exclude list if the exclude list was specified.
    /// </summary>
    /// <param name="path">path to validate</param>
    /// <returns>True if the path is acceptable.</returns>
    private bool MeetsIncludeExcludeCriteria(string path)
    {
      bool ok = false;

      // See if the file is on the include list.
      if (this.include != null)
      {
        foreach (WildcardPattern patternItem in this.include)
        {
          if (patternItem.IsMatch(path))
          {
            ok = true;
            break;
          }
        }
      }
      else
      {
        ok = true;
      }

      if (!ok)
         return false;

      // See if the file is on the exclude list.
      if (this.exclude != null)
      {
        foreach (WildcardPattern patternItem in this.exclude)
        {
          if (patternItem.IsMatch(path))
          {
            ok = false;
            break;
          }
        }
      }

      return ok;
    } //MeetsIncludeExcludeCriteria
    #endregion Private Methods

  }// class SelectStringCommand

  #endregion SelectStringCommand

  #region MatchInfo

  /// <summary>
  /// Class representing the result of a pattern/literal match
  /// that is passed through the pipeline by the Select-Str cmdlet.
  /// </summary>
  public class MatchInfo
  {
    /// <summary>
    /// Indicates if the match was done ignoring case.
    /// </summary>
    /// <value>True if case was ignored.</value>
    public bool IgnoreCase
    {
      get { return ignoreCase; }
      set { ignoreCase = value; }
    }
    private bool ignoreCase;

    /// <summary>
    /// Specifies the number of the matching line.
    /// </summary>
    /// <value>The number of the matching line.</value>
    public UInt64 LineNumber
    {
      get { return lineNumber; }
      set { lineNumber = value; }
    }
    private UInt64 lineNumber;

    /// <summary>
    /// Specifies the text of the matching line.
    /// </summary>
    /// <value>The text of the matching line.</value>
    public string Line
    {
      get { return line; }
      set { line = value; }
    }
    private string line;

    /// <summary>
    /// Specifies the full path of the object(file) containing the
    /// matching line.
    /// </summary>
    /// <remarks>
    /// It will be "inputStream" if the object came from the input
    /// stream.
    /// </remarks>
    /// <value>The path name</value>
    public string Path
    {
      get { return path; }
      set
      {
        pathSet = true;
        path = value;
      }
    }
    private string path;
    private bool pathSet;

    /// <summary>
    /// Specifies the pattern that was used in the match.
    /// </summary>
    /// <value>The pattern string</value>
    public string Pattern
    {
      get { return pattern; }
      set { pattern = value; }
    }
    private string pattern;

    private const string MatchFormat = "{0}:{1}:{2}";

    /// <summary>
    /// Returns the string representation of this object. The format
    /// depends on whether a path has been set for this object or
    /// not.
    /// </summary>
    /// <remarks>
    /// If the path component is set, as would be the case when
    /// matching in a file, ToString() returns the path, line
    /// number and line text.  If path is not set, then just the
    /// line text is presented.
    /// </remarks>
    /// <returns>The string representation of the match object.</returns>
    public override string ToString()
    {
      if (pathSet)
         return String.Format(
         System.Threading.Thread.CurrentThread.CurrentCulture,
         MatchFormat,
         this.path,
         this.lineNumber,
         this.line
         );
      else
         return this.line;
    }
  }// End class MatchInfo

  #endregion

  #region PowerShell snap-in

  /// <summary>
  /// Create a PowerShell snap-in for the Select-Str cmdlet.
  /// </summary>
  [RunInstaller(true)]
  public class SelectStringPSSnapIn : PSSnapIn
  {
    /// <summary>
    /// Create an instance of the SelectStrPSSnapin class.
    /// </summary>
    public SelectStringPSSnapIn()
           : base()
    {
    }

    /// <summary>
    /// Specify the name of the PowerShell snap-in.
    /// </summary>
    public override string Name
    {
      get
      {
        return "SelectStrPSSnapIn";
      }
    }

    /// <summary>
    /// Specify the vendor of the PowerShell snap-in.
    /// </summary>
    public override string Vendor
    {
      get
      {
        return "Microsoft";
      }
    }

    /// <summary>
    /// Specify the localization resource information for the vendor.
    /// Use the format: SnapinName,VendorName.
    /// </summary>
    public override string VendorResource
    {
      get
      {
        return "SelectStrSnapIn,Microsoft";
      }
    }

    /// <summary>
    /// Specify the description of the PowerShell snap-in.
    /// </summary>
    public override string Description
    {
      get
        {
          return "This is a PowerShell snap-in for the Select-Str cmdlet.";
        }
    }

    /// <summary>
    /// Specify the localization resource information for the description.
    /// Use the format: SnapinName,Description.

    /// </summary>
    public override string DescriptionResource
    {
      get
      {
          return "SelectStrSnapIn,This is a PowerShell snap-in for the Select-Str cmdlet.";
      }
    }
  }
  #endregion PowerShell snap-in

} //namespace Microsoft.Samples.PowerShell.Commands;
```

## <a name="building-the-cmdlet"></a><span data-ttu-id="da1b8-183">Compilazione del cmdlet</span><span class="sxs-lookup"><span data-stu-id="da1b8-183">Building the Cmdlet</span></span>

<span data-ttu-id="da1b8-184">Dopo l'implementazione di un cmdlet, è necessario registrarlo con Windows PowerShell tramite uno snap-in di Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="da1b8-184">After implementing a cmdlet, you must register it with Windows PowerShell through a Windows PowerShell snap-in.</span></span> <span data-ttu-id="da1b8-185">Per ulteriori informazioni sulla registrazione dei cmdlet, vedere [come registrare i cmdlet, i provider e le applicazioni host](/previous-versions//ms714644(v=vs.85)).</span><span class="sxs-lookup"><span data-stu-id="da1b8-185">For more information about registering cmdlets, see [How to Register Cmdlets, Providers, and Host Applications](/previous-versions//ms714644(v=vs.85)).</span></span>

## <a name="testing-the-cmdlet"></a><span data-ttu-id="da1b8-186">Test del cmdlet</span><span class="sxs-lookup"><span data-stu-id="da1b8-186">Testing the Cmdlet</span></span>

<span data-ttu-id="da1b8-187">Quando il cmdlet è stato registrato con Windows PowerShell, è possibile testarlo eseguendolo nella riga di comando.</span><span class="sxs-lookup"><span data-stu-id="da1b8-187">When your cmdlet has been registered with Windows PowerShell, you can test it by running it on the command line.</span></span> <span data-ttu-id="da1b8-188">La procedura seguente può essere usata per testare il cmdlet Select-Str di esempio.</span><span class="sxs-lookup"><span data-stu-id="da1b8-188">The following procedure can be used to test the sample Select-Str cmdlet.</span></span>

1. <span data-ttu-id="da1b8-189">Avviare Windows PowerShell ed eseguire una ricerca nel file delle note per individuare le occorrenze delle righe con l'espressione ".NET".</span><span class="sxs-lookup"><span data-stu-id="da1b8-189">Start Windows PowerShell, and search the Notes file for occurrences of lines with the expression ".NET".</span></span> <span data-ttu-id="da1b8-190">Si noti che le virgolette intorno al nome del percorso sono necessarie solo se il percorso è costituito da più di una parola.</span><span class="sxs-lookup"><span data-stu-id="da1b8-190">Note that the quotation marks around the name of the path are required only if the path consists of more than one word.</span></span>

    ```powershell
    select-str -Path "notes" -Pattern ".NET" -SimpleMatch=$false
    ```

    <span data-ttu-id="da1b8-191">Viene visualizzato l'output seguente:</span><span class="sxs-lookup"><span data-stu-id="da1b8-191">The following output appears.</span></span>

    ```output
    IgnoreCase   : True
    LineNumber   : 8
    Line         : Because Windows PowerShell works directly with .NET objects, there is often a .NET object
    Path         : C:\PowerShell-Progs\workspace\Samples\SelectStr\notes
    Pattern      : .NET
    IgnoreCase   : True
    LineNumber   : 21
    Line         : You should normally define the class for a cmdlet in a .NET namespace
    Path         : C:\PowerShell-Progs\workspace\Samples\SelectStr\notes
    Pattern      : .NET
    ```

2. <span data-ttu-id="da1b8-192">Cercare nel file delle note le occorrenze di righe con la parola "over", seguita da qualsiasi altro testo.</span><span class="sxs-lookup"><span data-stu-id="da1b8-192">Search the Notes file for occurrences of lines with the word "over", followed by any other text.</span></span> <span data-ttu-id="da1b8-193">Il parametro `SimpleMatch` usa il valore predefinito di `false`.</span><span class="sxs-lookup"><span data-stu-id="da1b8-193">The `SimpleMatch` parameter is using the default value of `false`.</span></span> <span data-ttu-id="da1b8-194">La ricerca non fa distinzione tra maiuscole e minuscole perché il parametro `CaseSensitive` è impostato su `false`.</span><span class="sxs-lookup"><span data-stu-id="da1b8-194">The search is case-insensitive because the `CaseSensitive` parameter is set to `false`.</span></span>

    ```powershell
    select-str -Path notes -Pattern "over*" -SimpleMatch -CaseSensitive:$false
    ```

    <span data-ttu-id="da1b8-195">Viene visualizzato l'output seguente:</span><span class="sxs-lookup"><span data-stu-id="da1b8-195">The following output appears.</span></span>

    ```output
    IgnoreCase   : True
    LineNumber   : 45
    Line         : Override StopProcessing
    Path         : C:\PowerShell-Progs\workspace\Samples\SelectStr\notes
    Pattern      : over*
    IgnoreCase   : True
    LineNumber   : 49
    Line         : overriding the StopProcessing method
    Path         : C:\PowerShell-Progs\workspace\Samples\SelectStr\notes
    Pattern      : over*
    ```

3. <span data-ttu-id="da1b8-196">Eseguire una ricerca nel file delle note usando un'espressione regolare come modello.</span><span class="sxs-lookup"><span data-stu-id="da1b8-196">Search the Notes file using a regular expression as the pattern.</span></span> <span data-ttu-id="da1b8-197">Tramite il cmdlet viene eseguita la ricerca di caratteri alfabetici e spazi vuoti racchiusi tra parentesi.</span><span class="sxs-lookup"><span data-stu-id="da1b8-197">The cmdlet searches for alphabetical characters and blank spaces enclosed in parentheses.</span></span>

    ```powershell
    select-str -Path notes -Pattern "\([A-Za-z:blank:]" -SimpleMatch:$false
    ```

    <span data-ttu-id="da1b8-198">Viene visualizzato l'output seguente:</span><span class="sxs-lookup"><span data-stu-id="da1b8-198">The following output appears.</span></span>

    ```output
    IgnoreCase   : True
    LineNumber   : 1
    Line         : Advisory Guidelines (Consider Following)
    Path         : C:\PowerShell-Progs\workspace\Samples\SelectStr\notes
    Pattern      : \([A-Za-z:blank:]
    IgnoreCase   : True
    LineNumber   : 53
    Line         : If your cmdlet has objects that are not disposed of (written to the pipeline)
    Path         : C:\PowerShell-Progs\workspace\Samples\SelectStr\notes
    Pattern      : \([A-Za-z:blank:]
    ```

4. <span data-ttu-id="da1b8-199">Eseguire una ricerca con distinzione tra maiuscole e minuscole del file di note per le occorrenze della parola "Parameter".</span><span class="sxs-lookup"><span data-stu-id="da1b8-199">Perform a case-sensitive search of the Notes file for occurrences of the word "Parameter".</span></span>

    ```powershell
    select-str -Path notes -Pattern Parameter -CaseSensitive
    ```

    <span data-ttu-id="da1b8-200">Viene visualizzato l'output seguente:</span><span class="sxs-lookup"><span data-stu-id="da1b8-200">The following output appears.</span></span>

    ```output
    IgnoreCase   : False
    LineNumber   : 6
    Line         : Support an InputObject Parameter
    Path         : C:\PowerShell-Progs\workspace\Samples\SelectStr\notes
    Pattern      : Parameter
    IgnoreCase   : False
    LineNumber   : 30
    Line         : Support Force Parameter
    Path         : C:\PowerShell-Progs\workspace\Samples\SelectStr\notes
    Pattern      : Parameter
    ```

5. <span data-ttu-id="da1b8-201">Eseguire una ricerca nel provider di variabili fornito con Windows PowerShell per le variabili con valori numerici compresi tra 0 e 9.</span><span class="sxs-lookup"><span data-stu-id="da1b8-201">Search the variable provider shipped with Windows PowerShell for variables that have numerical values from 0 through 9.</span></span>

    ```powershell
    select-str -Path * -Pattern "[0-9]"
    ```

    <span data-ttu-id="da1b8-202">Viene visualizzato l'output seguente:</span><span class="sxs-lookup"><span data-stu-id="da1b8-202">The following output appears.</span></span>

    ```output
    IgnoreCase   : True
    LineNumber   : 1
    Line         : 64
    Path         : Variable:\MaximumHistoryCount
    Pattern      : [0-9]
    ```

6. <span data-ttu-id="da1b8-203">Usare un blocco di script per cercare il file SelectStrCommandSample.cs per la stringa "pos".</span><span class="sxs-lookup"><span data-stu-id="da1b8-203">Use a script block to search the file SelectStrCommandSample.cs for the string "Pos".</span></span> <span data-ttu-id="da1b8-204">La funzione **cmatch** per lo script esegue una corrispondenza del modello senza distinzione tra maiuscole e minuscole.</span><span class="sxs-lookup"><span data-stu-id="da1b8-204">The **cmatch** function for the script performs a case-insensitive pattern match.</span></span>

    ```powershell
    select-str -Path "SelectStrCommandSample.cs" -Script { if ($args[0] -cmatch "Pos"){ return $true } return $false }
    ```

    <span data-ttu-id="da1b8-205">Viene visualizzato l'output seguente:</span><span class="sxs-lookup"><span data-stu-id="da1b8-205">The following output appears.</span></span>

    ```output
    IgnoreCase   : True
    LineNumber   : 37
    Line         :    Position = 0.
    Path         : C:\PowerShell-Progs\workspace\Samples\SelectStr\SelectStrCommandSample.cs
    Pattern      :
    ```

## <a name="see-also"></a><span data-ttu-id="da1b8-206">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="da1b8-206">See Also</span></span>

[<span data-ttu-id="da1b8-207">Come creare un cmdlet di Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="da1b8-207">How to Create a Windows PowerShell Cmdlet</span></span>](/powershell/scripting/developer/cmdlet/writing-a-windows-powershell-cmdlet)

[<span data-ttu-id="da1b8-208">Creazione del primo cmdlet</span><span class="sxs-lookup"><span data-stu-id="da1b8-208">Creating Your First Cmdlet</span></span>](./creating-a-cmdlet-without-parameters.md)

[<span data-ttu-id="da1b8-209">Creazione di un cmdlet che modifica il sistema</span><span class="sxs-lookup"><span data-stu-id="da1b8-209">Creating a Cmdlet that Modifies the System</span></span>](./creating-a-cmdlet-that-modifies-the-system.md)

[<span data-ttu-id="da1b8-210">Progettare il provider di Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="da1b8-210">Design Your Windows PowerShell Provider</span></span>](../prog-guide/designing-your-windows-powershell-provider.md)

<span data-ttu-id="da1b8-211">[Funzionamento di Windows PowerShell](/previous-versions//ms714658(v=vs.85))</span><span class="sxs-lookup"><span data-stu-id="da1b8-211">[How Windows PowerShell Works](/previous-versions//ms714658(v=vs.85))</span></span>

<span data-ttu-id="da1b8-212">[Come registrare cmdlet, provider e applicazioni host](/previous-versions//ms714644(v=vs.85))</span><span class="sxs-lookup"><span data-stu-id="da1b8-212">[How to Register Cmdlets, Providers, and Host Applications](/previous-versions//ms714644(v=vs.85))</span></span>

[<span data-ttu-id="da1b8-213">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="da1b8-213">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)
