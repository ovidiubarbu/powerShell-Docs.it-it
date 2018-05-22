---
ms.date: 06/12/2017
keywords: wmf,powershell,installazione
ms.openlocfilehash: 9aa7e92632c671751020687ddbfc374eeda7148b
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/16/2018
---
# <a name="new-language-features-in-powershell-50"></a><span data-ttu-id="48116-102">Nuove funzionalità del linguaggio in PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="48116-102">New language features in PowerShell 5.0</span></span>

<span data-ttu-id="48116-103">Con PowerShell 5.0 sono stati introdotti i seguenti elementi del linguaggio nuovi in Windows PowerShell:</span><span class="sxs-lookup"><span data-stu-id="48116-103">PowerShell 5.0 introduces the following new language elements in Windows PowerShell:</span></span>

## <a name="class-keyword"></a><span data-ttu-id="48116-104">Parola chiave class</span><span class="sxs-lookup"><span data-stu-id="48116-104">Class keyword</span></span>

<span data-ttu-id="48116-105">La parola chiave **class** definisce una nuova classe.</span><span class="sxs-lookup"><span data-stu-id="48116-105">The **class** keyword defines a new class.</span></span> <span data-ttu-id="48116-106">Si tratta di un vero tipo .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="48116-106">This is a true .NET Framework type.</span></span>
<span data-ttu-id="48116-107">I membri di classe sono pubblici, ma solo all'interno dell'ambito del modulo.</span><span class="sxs-lookup"><span data-stu-id="48116-107">Class members are public, but only public within the module scope.</span></span>
<span data-ttu-id="48116-108">È possibile fare riferimento al nome del tipo come stringa (ad esempio, `New-Object` non funziona) e, in questa versione, è possibile usare un valore letterale di tipo (ad esempio, `[MyClass]`) all'esterno del file di script o modulo in cui è definita la classe.</span><span class="sxs-lookup"><span data-stu-id="48116-108">You can't refer to the type name as a string (for example, `New-Object` doesn't work), and in this release, you can't use a type literal (for example, `[MyClass]`) outside the script/module file in which the class is defined.</span></span>

```powershell
class MyClass
{
    ...
}
```

## <a name="enum-keyword-and-enumerations"></a><span data-ttu-id="48116-109">Parola chiave enum ed enumerazioni</span><span class="sxs-lookup"><span data-stu-id="48116-109">Enum keyword and enumerations</span></span>

<span data-ttu-id="48116-110">È stato aggiunto il supporto della parola chiave **enum**, che usa il carattere di nuova riga come delimitatore.</span><span class="sxs-lookup"><span data-stu-id="48116-110">Support for the **enum** keyword has been added, which uses newline as the delimiter.</span></span>
<span data-ttu-id="48116-111">Esistono attualmente alcune limitazioni. Ad esempio, non è possibile definire un enumeratore in termini di se stesso, ma è possibile inizializzare un enum in termini di un altro enum, come illustrato nell'esempio seguente.</span><span class="sxs-lookup"><span data-stu-id="48116-111">Current limitations: you cannot define an enumerator in terms of itself, but you can initialize an enum in terms of another enum, as shown in the following example.</span></span>
<span data-ttu-id="48116-112">Inoltre, non è attualmente possibile specificare il tipo di base, che è sempre [int].</span><span class="sxs-lookup"><span data-stu-id="48116-112">Also, the base type cannot currently be specified; it is always [int].</span></span>

```powershell
enum Color2
{
    Yellow = [Color]::Blue
}
```

<span data-ttu-id="48116-113">Un valore di enumeratore deve essere una costante della fase di analisi. Non è possibile impostarlo sul risultato di un comando richiamato.</span><span class="sxs-lookup"><span data-stu-id="48116-113">An enumerator value must be a parse time constant; you cannot set it to the result of an invoked command.</span></span>

```powershell
enum MyEnum
{
    Enum1
    Enum2
    Enum3 = 42
    Enum4 = [int]::MaxValue
}
```

<span data-ttu-id="48116-114">Gli enumeratori supportano operazioni aritmetiche, come mostrato nell'esempio seguente.</span><span class="sxs-lookup"><span data-stu-id="48116-114">Enums support arithmetic operations, as shown in the following example.</span></span>

```powershell
enum SomeEnum { Max = 42 }
enum OtherEnum { Max = [SomeEnum]::Max + 1 }
```

## <a name="import-dscresource"></a><span data-ttu-id="48116-115">Import-DscResource</span><span class="sxs-lookup"><span data-stu-id="48116-115">Import-DscResource</span></span>

<span data-ttu-id="48116-116">**Import-DscResource** è ora una parola chiave veramente dinamica.</span><span class="sxs-lookup"><span data-stu-id="48116-116">**Import-DscResource** is now a true dynamic keyword.</span></span>
<span data-ttu-id="48116-117">PowerShell analizza il modulo radice del modulo specificato, alla ricerca delle classi che contengono l'attributo **DscResource**.</span><span class="sxs-lookup"><span data-stu-id="48116-117">PowerShell parses the specified module’s root module, searching for classes that contain the **DscResource** attribute.</span></span>

## <a name="implementingassembly"></a><span data-ttu-id="48116-118">ImplementingAssembly</span><span class="sxs-lookup"><span data-stu-id="48116-118">ImplementingAssembly</span></span>

<span data-ttu-id="48116-119">Un nuovo campo, **ImplementingAssembly**, è stato aggiunto a ModuleInfo.</span><span class="sxs-lookup"><span data-stu-id="48116-119">A new field, **ImplementingAssembly**, has been added to ModuleInfo.</span></span> <span data-ttu-id="48116-120">Viene impostato sull'assembly dinamico creato per un modulo di script se lo script definisce classi oppure sull'assembly caricato per moduli binari.</span><span class="sxs-lookup"><span data-stu-id="48116-120">It is set to the dynamic assembly created for a script module if the script defines classes, or the loaded assembly for binary modules.</span></span> <span data-ttu-id="48116-121">Non viene impostato quando ModuleType = Manifest.</span><span class="sxs-lookup"><span data-stu-id="48116-121">It is not set when ModuleType = Manifest.</span></span>

<span data-ttu-id="48116-122">La reflection sul campo **ImplementingAssembly** consente di individuare le risorse in un modulo.</span><span class="sxs-lookup"><span data-stu-id="48116-122">Reflection on the **ImplementingAssembly** field discovers resources in a module.</span></span> <span data-ttu-id="48116-123">Ciò significa che è possibile individuare le risorse scritte in PowerShell o altri linguaggi gestiti.</span><span class="sxs-lookup"><span data-stu-id="48116-123">This means you can discover resources written in either PowerShell or other managed languages.</span></span>

<span data-ttu-id="48116-124">Campi con inizializzatori:</span><span class="sxs-lookup"><span data-stu-id="48116-124">Fields with initializers:</span></span>

```powershell
[int] $i = 5
```

<span data-ttu-id="48116-125">È supportato static e funziona come un attributo, come i vincoli di tipo, pertanto può essere specificato in qualsiasi ordine.</span><span class="sxs-lookup"><span data-stu-id="48116-125">Static is supported; it works like an attribute, as do the type constraints, so it can be specified in any order.</span></span>

```powershell
static [int] $count = 0
```

<span data-ttu-id="48116-126">Il tipo è facoltativo.</span><span class="sxs-lookup"><span data-stu-id="48116-126">A type is optional.</span></span>

```powershell
$s = "hello"
```

<span data-ttu-id="48116-127">Tutti i membri sono pubblici.</span><span class="sxs-lookup"><span data-stu-id="48116-127">All members are public.</span></span>

## <a name="constructors-and-instantiation"></a><span data-ttu-id="48116-128">Costruttori e creazione di istanze</span><span class="sxs-lookup"><span data-stu-id="48116-128">Constructors and instantiation</span></span>

<span data-ttu-id="48116-129">Le classi di Windows PowerShell possono avere costruttori, con lo stesso nome della classe.</span><span class="sxs-lookup"><span data-stu-id="48116-129">Windows PowerShell classes can have constructors; they have the same name as their class.</span></span> <span data-ttu-id="48116-130">I costruttori possono essere sottoposti a overload.</span><span class="sxs-lookup"><span data-stu-id="48116-130">Constructors can be overloaded.</span></span> <span data-ttu-id="48116-131">Sono supportati i costruttori statici.</span><span class="sxs-lookup"><span data-stu-id="48116-131">Static constructors are supported.</span></span> <span data-ttu-id="48116-132">Le proprietà con espressioni di inizializzazione vengono inizializzate prima di eseguire qualsiasi codice in un costruttore.</span><span class="sxs-lookup"><span data-stu-id="48116-132">Properties with initialization expressions are initialized before running any code in a constructor.</span></span> <span data-ttu-id="48116-133">Le proprietà statiche vengono inizializzate prima del corpo di un costruttore statico e le proprietà dell'istanza vengono inizializzate prima del corpo del costruttore non statico.</span><span class="sxs-lookup"><span data-stu-id="48116-133">Static properties are initialized before the body of a static constructor, and instance properties are initialized before the body of the non-static constructor.</span></span> <span data-ttu-id="48116-134">Attualmente non è disponibile alcuna sintassi per chiamare un costruttore da un altro costruttore (analoga alla sintassi C\# ": this()").</span><span class="sxs-lookup"><span data-stu-id="48116-134">Currently, there is no syntax for calling a constructor from another constructor (like the C\# syntax ": this()").</span></span> <span data-ttu-id="48116-135">La soluzione consiste nel definire un metodo Init comune.</span><span class="sxs-lookup"><span data-stu-id="48116-135">The workaround is to define a common Init method.</span></span>

<span data-ttu-id="48116-136">Gli esempi seguenti illustrano i modi disponibili per la creazione di istanze di classi in questa versione.</span><span class="sxs-lookup"><span data-stu-id="48116-136">The following are ways of instantiating classes in this release.</span></span>

<span data-ttu-id="48116-137">Creazione di un'istanza con il costruttore predefinito.</span><span class="sxs-lookup"><span data-stu-id="48116-137">Instantiating by using the default constructor.</span></span> <span data-ttu-id="48116-138">Si noti che New-Object non è supportato in questa versione.</span><span class="sxs-lookup"><span data-stu-id="48116-138">Note that New-Object is not supported in this release.</span></span>

```powershell
$a = [MyClass]::new()
```

<span data-ttu-id="48116-139">Chiamata di un costruttore con un parametro</span><span class="sxs-lookup"><span data-stu-id="48116-139">Calling a constructor with a parameter</span></span>

```powershell
$b = [MyClass]::new(42)
```

<span data-ttu-id="48116-140">Passaggio di una matrice a un costruttore con più parametri</span><span class="sxs-lookup"><span data-stu-id="48116-140">Passing an array to a constructor with multiple parameters</span></span>
```powershell
$c = [MyClass]::new(@(42,43,44), "Hello")
```

<span data-ttu-id="48116-141">In questa versione, New-Object non funziona con classi definite in Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="48116-141">In this release, New-Object does not work with classes defined in Windows PowerShell.</span></span> <span data-ttu-id="48116-142">Per questa versione, inoltre, il nome del tipo è visibile solo a livello lessicale, vale a dire che non è visibile all'esterno del modulo o dello script che definisce la classe.</span><span class="sxs-lookup"><span data-stu-id="48116-142">Also for this release, the type name is only visible lexically, meaning it is not visible outside of the module or script that defines the class.</span></span> <span data-ttu-id="48116-143">Le funzioni possono restituire istanze di una classe definita in Windows PowerShell e le istanze funzionano in modo appropriato all'esterno del modulo o dello script.</span><span class="sxs-lookup"><span data-stu-id="48116-143">Functions can return instances of a class defined in Windows PowerShell, and instances work well outside of the module or script.</span></span>

<span data-ttu-id="48116-144">`Get-Member -Static` elenca i costruttori, quindi è possibile visualizzare gli overload come qualsiasi altro metodo.</span><span class="sxs-lookup"><span data-stu-id="48116-144">`Get-Member -Static` lists constructors, so you can view overloads like any other method.</span></span> <span data-ttu-id="48116-145">Le prestazioni di questa sintassi sono anche notevolmente più veloci rispetto a New-Object.</span><span class="sxs-lookup"><span data-stu-id="48116-145">The performance of this syntax is also considerably faster than New-Object.</span></span>

<span data-ttu-id="48116-146">Il metodo pseudo-statico denominato **new** funziona con i tipi .NET, come illustrato nell'esempio seguente.</span><span class="sxs-lookup"><span data-stu-id="48116-146">The pseudo-static method named **new** works with .NET types, as shown in the following example.</span></span>

```powershell
[hashtable]::new()
```

<span data-ttu-id="48116-147">È ora possibile visualizzare gli overload del costruttore con Get-Member o come illustrato in questo esempio:</span><span class="sxs-lookup"><span data-stu-id="48116-147">You can now see constructor overloads with Get-Member, or as shown in this example:</span></span>

```powershell
PS> [hashtable]::new
OverloadDefinitions
-------------------
hashtable new()
hashtable new(int capacity)
hashtable new(int capacity, float loadFactor)
```

## <a name="methods"></a><span data-ttu-id="48116-148">Metodi</span><span class="sxs-lookup"><span data-stu-id="48116-148">Methods</span></span>

<span data-ttu-id="48116-149">Un metodo della classe di Windows PowerShell viene implementato come ScriptBlock con solo un blocco finale.</span><span class="sxs-lookup"><span data-stu-id="48116-149">A Windows PowerShell class method is implemented as a ScriptBlock that has only an end block.</span></span> <span data-ttu-id="48116-150">Tutti i metodi sono pubblici.</span><span class="sxs-lookup"><span data-stu-id="48116-150">All methods are public.</span></span> <span data-ttu-id="48116-151">L'esempio seguente illustra la definizione di un metodo denominato **DoSomething**.</span><span class="sxs-lookup"><span data-stu-id="48116-151">The following shows an example of defining a method named **DoSomething**.</span></span>

```powershell
class MyClass
{
    DoSomething($x)
    {
        $this._doSomething($x) # method syntax
    }
    private _doSomething($a) {}
}
```

<span data-ttu-id="48116-152">Chiamata del metodo:</span><span class="sxs-lookup"><span data-stu-id="48116-152">Method invocation:</span></span>

```powershell
$b = [MyClass]::new()
$b.DoSomething(42)
```

<span data-ttu-id="48116-153">Sono supportati anche i metodi in overload, ossia quelli con lo stesso nome di un metodo esistente, ma diversi per i valori specificati.</span><span class="sxs-lookup"><span data-stu-id="48116-153">Overloaded methods--that is, those that are named the same as an existing method, but differentiated by their specified values--are also supported.</span></span>

## <a name="properties"></a><span data-ttu-id="48116-154">Proprietà</span><span class="sxs-lookup"><span data-stu-id="48116-154">Properties</span></span>

<span data-ttu-id="48116-155">Tutte le proprietà sono pubbliche.</span><span class="sxs-lookup"><span data-stu-id="48116-155">All properties are public.</span></span> <span data-ttu-id="48116-156">Le proprietà richiedono un carattere di nuova riga o un punto e virgola.</span><span class="sxs-lookup"><span data-stu-id="48116-156">Properties require either a newline or semicolon.</span></span> <span data-ttu-id="48116-157">Se non viene specificato alcun tipo di oggetto, il tipo della proprietà è object.</span><span class="sxs-lookup"><span data-stu-id="48116-157">If no object type is specified, the property type is object.</span></span>

<span data-ttu-id="48116-158">Le proprietà che usano gli attributi di convalida o gli attributi di trasformazione degli argomenti (ad esempio `[ValidateSet("aaa")]`) funzionano come previsto.</span><span class="sxs-lookup"><span data-stu-id="48116-158">Properties that use validation attributes or argument transformation attributes (e.g. `[ValidateSet("aaa")]`) work as expected.</span></span>

## <a name="hidden"></a><span data-ttu-id="48116-159">Hidden</span><span class="sxs-lookup"><span data-stu-id="48116-159">Hidden</span></span>

<span data-ttu-id="48116-160">È stata aggiunta la nuova parola chiave **Hidden**.</span><span class="sxs-lookup"><span data-stu-id="48116-160">A new keyword, **Hidden**, has been added.</span></span> <span data-ttu-id="48116-161">È possibile applicare **Hidden** alle proprietà e ai metodi (inclusi i costruttori).</span><span class="sxs-lookup"><span data-stu-id="48116-161">**Hidden** can be applied to properties and methods (including constructors).</span></span>

<span data-ttu-id="48116-162">I membri nascosti sono pubblici, ma non vengono visualizzati nell'output di Get-Member, a meno che non venga aggiunto il parametro -Force.</span><span class="sxs-lookup"><span data-stu-id="48116-162">Hidden members are public, but do not appear in the output of Get-Member unless the -Force parameter is added.</span></span>

<span data-ttu-id="48116-163">I membri nascosti non vengono inclusi quando si usa il completamento con TAB o Intellisense, a meno che il completamento non avvenga nella classe che definisce il membro nascosto.</span><span class="sxs-lookup"><span data-stu-id="48116-163">Hidden members are not included when tab completing or using Intellisense unless the completion occurs in the class defining the hidden member.</span></span>

<span data-ttu-id="48116-164">È stato aggiunto un nuovo attributo, **System.Management.Automation.HiddenAttribute** in modo che il codice C# possa avere la stessa semantica all'interno di Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="48116-164">A new attribute, **System.Management.Automation.HiddenAttribute** has been added so that C# code can have the same semantics within Windows PowerShell.</span></span>

## <a name="return-types"></a><span data-ttu-id="48116-165">Tipi restituiti</span><span class="sxs-lookup"><span data-stu-id="48116-165">Return types</span></span>

<span data-ttu-id="48116-166">Il tipo restituito è un contratto. Il valore restituito viene convertito nel tipo previsto.</span><span class="sxs-lookup"><span data-stu-id="48116-166">Return type is a contract; the return value is converted to the expected type.</span></span> <span data-ttu-id="48116-167">Se non viene specificato alcun tipo restituito, il tipo restituito è void.</span><span class="sxs-lookup"><span data-stu-id="48116-167">If no return type is specified, the return type is void.</span></span> <span data-ttu-id="48116-168">Non sono supportati flussi di oggetti. Non è possibile scrivere gli oggetti nella pipeline intenzionalmente o accidentalmente.</span><span class="sxs-lookup"><span data-stu-id="48116-168">There is no streaming of objects; objects cannot be written to the pipeline either intentionally or by accident.</span></span>

## <a name="attributes"></a><span data-ttu-id="48116-169">Attributes</span><span class="sxs-lookup"><span data-stu-id="48116-169">Attributes</span></span>

<span data-ttu-id="48116-170">Sono stati aggiunti due nuovi attributi, **DscResource** e **DscProperty**.</span><span class="sxs-lookup"><span data-stu-id="48116-170">Two new attributes, **DscResource** and **DscProperty** have been added.</span></span>

## <a name="lexical-scoping-of-variables"></a><span data-ttu-id="48116-171">Ambito lessicale delle variabili</span><span class="sxs-lookup"><span data-stu-id="48116-171">Lexical scoping of variables</span></span>

<span data-ttu-id="48116-172">Di seguito viene riportato un esempio di come funziona l'assegnazione dell'ambito lessicale in questa versione.</span><span class="sxs-lookup"><span data-stu-id="48116-172">The following shows an example of how lexical scoping works in this release.</span></span>

```powershell
$d = 42 # Script scope

function bar
{
    $d = 0 # Function scope
    [MyClass]::DoSomething()
}

class MyClass
{
    static [object] DoSomething()
    {
        return $d # error, not found dynamically
        return $script:d # no error
        $d = $script:d
        return $d # no error, found lexically
    }
}

$v = bar
$v -eq $d # true
```

## <a name="end-to-end-example"></a><span data-ttu-id="48116-173">Esempio end-to-end</span><span class="sxs-lookup"><span data-stu-id="48116-173">End-to-End Example</span></span>

<span data-ttu-id="48116-174">L'esempio seguente crea diverse classi nuove personalizzate per implementare un documento DSL (Dynamic Stylesheet Language) HTML.</span><span class="sxs-lookup"><span data-stu-id="48116-174">The following example creates several new, custom classes to implement an HTML dynamic style sheet language (DSL).</span></span>
<span data-ttu-id="48116-175">L'esempio aggiunge quindi funzioni helper per creare tipi di elemento specifici come parte della classe Element, ad esempio stili del titolo e tabelle, poiché i tipi non possono essere usati all'esterno dell'ambito di un modulo.</span><span class="sxs-lookup"><span data-stu-id="48116-175">Then, the example adds helper functions to create specific element types as part of the element class, such as heading styles and tables, because types cannot be used outside the scope of a module.</span></span>

```powershell
# Classes that define the structure of the document
#
class Html
{
    [string] $docType
    [HtmlHead] $Head
    [Element[]] $Body

    [string] Render()
    {
        $text = "<html>`n<head>`n"
        $text += $this.Head
        $text += "`n</head>`n<body>`n"
        $text += $this.Body -join "`n" # Render all of the body elements
        $text += "</body>`n</html>"
        return $text
    }
    [string] ToString() { return $this.Render() }
}

class HtmlHead
{
    $Title
    $Base
    $Link
    $Style
    $Meta
    $Script
    [string] Render() { return "<title>$($this.Title)</title>" }
    [string] ToString() { return $this.Render() }
}

class Element
{
    [string] $Tag
    [string] $Text
    [hashtable] $Attributes
    [string] Render() {
        $attributesText= ""
        if ($this.Attributes)
        {
            foreach ($attr in $this.Attributes.Keys)
            {
                #BUGBUG - need to validate keys against attribute
                $attributesText += " $attr=`"$($this.Attributes[$attr])\`""
            }
        }
        return "<$($this.tag)${attributesText}>$($this.text)</$($this.tag)>`n"
    }
[string] ToString() { return $this.Render() }
}

#
# Helper functions for creating specific element types on top of the classes.
# These are required because types aren’t visible outside of the module.
#

function H1 { [Element] @{ Tag = "H1" ; Text = $args.foreach{$_} -join " " }}
function H2 { [Element] @{ Tag = "H2" ; Text = $args.foreach{$_} -join " " }}
function H3 { [Element] @{ Tag = "H3" ; Text = $args.foreach{$_} -join " " }}
function P { [Element] @{ Tag = "P" ; Text = $args.foreach{$_} -join " " }}
function B { [Element] @{ Tag = "B" ; Text = $args.foreach{$_} -join " " }}
function I { [Element] @{ Tag = "I" ; Text = $args.foreach{$_} -join " " }}
function HREF
{
    param (
        $Name,
        $Link
    )
    return [Element] @{
        Tag = "A"
        Attributes = @{ HREF = $link }
        Text = $name
    }
}
function Table
{
    param (
    [Parameter(Mandatory)]
    [object[]]
        $Data,
    [Parameter()]
    [string[]]
        $Properties = "*",
    [Parameter()]
    [hashtable]
        $Attributes = @{ border=2; cellpadding=2; cellspacing=2 }
    )
$bodyText = ""
# Add the header tags
$bodyText += $Properties.foreach{TH $_}
# Add the rows
$bodyText += foreach ($row in $Data)
    {
        TR (-join $Properties.Foreach{ TD ($row.$\_) } )
    }

    $table = [Element] @{
        Tag = "Table"
        Attributes = $Attributes
        Text = $bodyText
    }
$table
}
function TH { ([Element] @{ Tag = "TH" ; Text = $args.foreach{$_} -join " " }) }
function TR { ([Element] @{ Tag = "TR" ; Text = $args.foreach{$_} -join " " }) }
function TD { ([Element] @{ Tag = "TD" ; Text = $args.foreach{$_} -join " " }) }
function Style

{
    return [Element] @{
        Tag = "style"
        Text = "$args"
    }
}

# Takes a hash table, casts it to and HTML document
# and then returns the resulting type.
#
function Html ([HTML] $doc) { return $doc }
```
