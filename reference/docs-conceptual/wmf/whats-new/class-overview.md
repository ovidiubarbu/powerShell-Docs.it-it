---
ms.date: 06/12/2017
keywords: wmf,powershell,installazione
title: Creazione di tipi personalizzati con le classi di PowerShell
ms.openlocfilehash: c2c50fb65ce4931fcf6ae529b4146df391c831c4
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 12/05/2019
ms.locfileid: "71147841"
---
# <a name="creating-custom-types-using-powershell-classes"></a><span data-ttu-id="d80a3-103">Creazione di tipi personalizzati con le classi di PowerShell</span><span class="sxs-lookup"><span data-stu-id="d80a3-103">Creating Custom Types using PowerShell Classes</span></span>

<span data-ttu-id="d80a3-104">In PowerShell 5.0 è stata aggiunta la possibilità di definire classi e altri tipi definiti dall'utente usando sintassi e semantica formali simili ad altri linguaggi di programmazione orientata agli oggetti.</span><span class="sxs-lookup"><span data-stu-id="d80a3-104">PowerShell 5.0 added the ability to define classes and other user-defined types using formal syntax and semantics like other object-oriented programming languages.</span></span> <span data-ttu-id="d80a3-105">L'obiettivo è consentire agli sviluppatori e ai professionisti IT di adottare PowerShell per una vasta gamma di casi d'uso, semplificare lo sviluppo di artefatti di PowerShell (ad esempio risorse DSC) e velocizzare la copertura delle aree di gestione.</span><span class="sxs-lookup"><span data-stu-id="d80a3-105">The goal is to enable developers and IT professionals to embrace PowerShell for a wider range of use cases, simplify development of PowerShell artifacts (such as DSC resources), and accelerate coverage of management surfaces.</span></span>

## <a name="supported-scenarios-in-this-release"></a><span data-ttu-id="d80a3-106">Scenari supportati in questa versione</span><span class="sxs-lookup"><span data-stu-id="d80a3-106">Supported scenarios in this release</span></span>

- <span data-ttu-id="d80a3-107">Definire risorse DSC e i relativi tipi associati usando il linguaggio di PowerShell</span><span class="sxs-lookup"><span data-stu-id="d80a3-107">Define DSC resources and their associated types by using the PowerShell language</span></span>
- <span data-ttu-id="d80a3-108">Definire tipi personalizzati in PowerShell usando costrutti noti della programmazione orientata agli oggetti, come classi, proprietà, metodi e così via.</span><span class="sxs-lookup"><span data-stu-id="d80a3-108">Define custom types in PowerShell by using familiar object-oriented programming constructs, such as classes, properties, methods, etc.</span></span>
- <span data-ttu-id="d80a3-109">Supporto dell'ereditarietà con le classi in PowerShell e le risorse DSC basate su classi</span><span class="sxs-lookup"><span data-stu-id="d80a3-109">Inheritance support with class in PowerShell and class base DSC resource</span></span>
- <span data-ttu-id="d80a3-110">Eseguire il debug di tipi con il linguaggio di PowerShell</span><span class="sxs-lookup"><span data-stu-id="d80a3-110">Debug types by using the PowerShell language</span></span>
- <span data-ttu-id="d80a3-111">Generare e gestire le eccezioni tramite meccanismi formali, al giusto livello</span><span class="sxs-lookup"><span data-stu-id="d80a3-111">Generate and handle exceptions by using formal mechanisms, and at the right level</span></span>

## <a name="declare-base-class"></a><span data-ttu-id="d80a3-112">Dichiarare una classe di base</span><span class="sxs-lookup"><span data-stu-id="d80a3-112">Declare Base Class</span></span>

<span data-ttu-id="d80a3-113">È possibile dichiarare una classe di PowerShell come tipo di base per un'altra classe di PowerShell.</span><span class="sxs-lookup"><span data-stu-id="d80a3-113">You can declare a PowerShell class as a base type for another PowerShell class.</span></span>

```powershell
class bar
{
   [int]foo()
       {
           return 100500
       }
}

class baz : bar {}

[baz]::new().foo() # return 100500
```

<span data-ttu-id="d80a3-114">Si possono anche usare i tipi .NET Framework esistenti come classi di base:</span><span class="sxs-lookup"><span data-stu-id="d80a3-114">You can also use existing .NET Framework types as base classes:</span></span>

```powershell
class MyIntList : system.collections.generic.list[int]
{

}

$list = [MyIntList]::new()

$list.Add(100)

$list[0] # return 100
```

### <a name="call-base-class-constructor"></a><span data-ttu-id="d80a3-115">Chiamare il costruttore della classe di base</span><span class="sxs-lookup"><span data-stu-id="d80a3-115">Call Base Class Constructor</span></span>

<span data-ttu-id="d80a3-116">Per chiamare un costruttore di classe di base da una sottoclasse, usare la parola chiave **base**:</span><span class="sxs-lookup"><span data-stu-id="d80a3-116">To call a base class constructor from a subclass, use the keyword **base**:</span></span>

```powershell
class A
{
    [int]$a

    A([int]$a)
    {
        $this.a = $a
    }
}

class B : A
{
    B() : base(103) {}
}

[B]::new().a # return 103
```

<span data-ttu-id="d80a3-117">Se una classe di base ha un costruttore predefinito (nessun parametro), è possibile omettere una chiamata esplicita al costruttore:</span><span class="sxs-lookup"><span data-stu-id="d80a3-117">If a base class has a default (no parameter) constructor, you can omit an explicit constructor call:</span></span>

```powershell
class C : B
{
    C([int]$c) {}
}
```

### <a name="call-base-class-method"></a><span data-ttu-id="d80a3-118">Chiamare il metodo della classe di base</span><span class="sxs-lookup"><span data-stu-id="d80a3-118">Call Base Class Method</span></span>

<span data-ttu-id="d80a3-119">È possibile eseguire l'override di metodi esistenti nelle sottoclassi.</span><span class="sxs-lookup"><span data-stu-id="d80a3-119">You can override existing methods in subclasses.</span></span> <span data-ttu-id="d80a3-120">A tale scopo, dichiarare metodi con lo stesso nome e firma:</span><span class="sxs-lookup"><span data-stu-id="d80a3-120">To do this, declare methods by using the same name and signature:</span></span>

```powershell
class baseClass
{
    [int]foo() {return 100500}
}

class childClass1 : baseClass
{
    [int]foo() {return 200600}
}

[childClass1]::new().foo() # return 200600
```

<span data-ttu-id="d80a3-121">Per chiamare metodi della classe di base da implementazioni sottoposte a override, eseguire il cast della classe di base (`[baseClass]$this`) nella chiamata:</span><span class="sxs-lookup"><span data-stu-id="d80a3-121">To call base class methods from overridden implementations, cast to the base class (`[baseClass]$this`) on invocation:</span></span>

```powershell
class childClass2 : baseClass
{
    [int]foo()
    {
        return 3 * ([baseClass]$this).foo()
    }
}

[childClass2]::new().foo() # return 301500
```

<span data-ttu-id="d80a3-122">Tutti i metodi di PowerShell sono virtuali.</span><span class="sxs-lookup"><span data-stu-id="d80a3-122">All PowerShell methods are virtual.</span></span> <span data-ttu-id="d80a3-123">È possibile nascondere i metodi .NET non virtuali in una sottoclasse con la stessa sintassi usata per un override, ovvero dichiarando i metodi con lo stesso nome e firma.</span><span class="sxs-lookup"><span data-stu-id="d80a3-123">You can hide non-virtual .NET methods in a subclass by using the same syntax as you do for an override, by declaring methods with same name and signature.</span></span>

```powershell
class MyIntList : system.collections.generic.list[int]
{
    # Add is final in system.collections.generic.list
    [void] Add([int]$arg)
    {
        ([system.collections.generic.list[int]]$this).Add($arg * 2)
    }
}

$list = [MyIntList]::new()
$list.Add(100)
$list[0] # return 200
```

### <a name="declare-implemented-interface"></a><span data-ttu-id="d80a3-124">Dichiarare l'interfaccia implementata</span><span class="sxs-lookup"><span data-stu-id="d80a3-124">Declare Implemented Interface</span></span>

<span data-ttu-id="d80a3-125">È possibile dichiarare le interfacce implementate dopo i tipi di base o subito dopo i due punti (:), se non è specificato alcun tipo di base.</span><span class="sxs-lookup"><span data-stu-id="d80a3-125">You can declare implemented interfaces after base types, or immediately after a colon (:), if there is no base type specified.</span></span> <span data-ttu-id="d80a3-126">Usare le virgole per separare tutti i nomi di tipo.</span><span class="sxs-lookup"><span data-stu-id="d80a3-126">Separate all type names by using commas.</span></span> <span data-ttu-id="d80a3-127">La sintassi è simile a quella di C#.</span><span class="sxs-lookup"><span data-stu-id="d80a3-127">It's similar to C# syntax.</span></span>

```powershell
class MyComparable : system.IComparable
{
    [int] CompareTo([object] $obj)
    {
        return 0;
    }
}

class MyComparableBar : bar, system.IComparable
{
    [int] CompareTo([object] $obj)
    {
        return 0;
    }
}
```

## <a name="new-language-features-in-powershell-50"></a><span data-ttu-id="d80a3-128">Nuove funzionalità del linguaggio in PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="d80a3-128">New language features in PowerShell 5.0</span></span>

<span data-ttu-id="d80a3-129">Con PowerShell 5.0 sono stati introdotti i seguenti elementi del linguaggio nuovi in PowerShell:</span><span class="sxs-lookup"><span data-stu-id="d80a3-129">PowerShell 5.0 introduces the following new language elements in PowerShell:</span></span>

### <a name="class-keyword"></a><span data-ttu-id="d80a3-130">Parola chiave class</span><span class="sxs-lookup"><span data-stu-id="d80a3-130">Class keyword</span></span>

<span data-ttu-id="d80a3-131">La parola chiave `class` definisce una nuova classe.</span><span class="sxs-lookup"><span data-stu-id="d80a3-131">The `class` keyword defines a new class.</span></span> <span data-ttu-id="d80a3-132">Si tratta di un vero tipo .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="d80a3-132">This is a true .NET Framework type.</span></span> <span data-ttu-id="d80a3-133">I membri di classe sono pubblici, ma solo all'interno dell'ambito del modulo.</span><span class="sxs-lookup"><span data-stu-id="d80a3-133">Class members are public, but only public within the module scope.</span></span> <span data-ttu-id="d80a3-134">È possibile fare riferimento al nome del tipo come stringa (ad esempio, `New-Object` non funziona) e, in questa versione, è possibile usare un valore letterale di tipo (ad esempio, `[MyClass]`) all'esterno del file di script o modulo in cui è definita la classe.</span><span class="sxs-lookup"><span data-stu-id="d80a3-134">You can't refer to the type name as a string (for example, `New-Object` doesn't work), and in this release, you can't use a type literal (for example, `[MyClass]`) outside the script or module file in which the class is defined.</span></span>

```powershell
class MyClass
{
    ...
}
```

### <a name="enum-keyword-and-enumerations"></a><span data-ttu-id="d80a3-135">Parola chiave enum ed enumerazioni</span><span class="sxs-lookup"><span data-stu-id="d80a3-135">Enum keyword and enumerations</span></span>

<span data-ttu-id="d80a3-136">È stato aggiunto il supporto della parola chiave `enum`, che usa il carattere di nuova riga come delimitatore.</span><span class="sxs-lookup"><span data-stu-id="d80a3-136">Support for the `enum` keyword has been added, which uses newline as the delimiter.</span></span> <span data-ttu-id="d80a3-137">Attualmente, non è possibile definire un enumeratore in termini di se stesso.</span><span class="sxs-lookup"><span data-stu-id="d80a3-137">Currently, you cannot define an enumerator in terms of itself.</span></span> <span data-ttu-id="d80a3-138">Tuttavia, è possibile inizializzare un enum in termini di un altro enum, come illustrato nell'esempio seguente.</span><span class="sxs-lookup"><span data-stu-id="d80a3-138">However, you can initialize an enum in terms of another enum, as shown in the following example.</span></span> <span data-ttu-id="d80a3-139">Inoltre, non è attualmente possibile specificare il tipo di base, che è sempre `[int]`.</span><span class="sxs-lookup"><span data-stu-id="d80a3-139">Also, the base type cannot be specified; it is always `[int]`.</span></span>

```powershell
enum Color2
{
    Yellow = [Color]::Blue
}
```

<span data-ttu-id="d80a3-140">Un valore di enumeratore deve essere una costante in fase di analisi.</span><span class="sxs-lookup"><span data-stu-id="d80a3-140">An enumerator value must be a parse time constant.</span></span> <span data-ttu-id="d80a3-141">Non è possibile impostarlo sul risultato di un comando richiamato.</span><span class="sxs-lookup"><span data-stu-id="d80a3-141">You cannot set it to the result of an invoked command.</span></span>

```powershell
enum MyEnum
{
    Enum1
    Enum2
    Enum3 = 42
    Enum4 = [int]::MaxValue
}
```

<span data-ttu-id="d80a3-142">Gli enumeratori supportano operazioni aritmetiche, come mostrato nell'esempio seguente.</span><span class="sxs-lookup"><span data-stu-id="d80a3-142">Enums support arithmetic operations, as shown in the following example.</span></span>

```powershell
enum SomeEnum { Max = 42 }
enum OtherEnum { Max = [SomeEnum]::Max + 1 }
```

### <a name="import-dscresource"></a><span data-ttu-id="d80a3-143">Import-DscResource</span><span class="sxs-lookup"><span data-stu-id="d80a3-143">Import-DscResource</span></span>

<span data-ttu-id="d80a3-144">`Import-DscResource` è ora una parola chiave effettivamente dinamica.</span><span class="sxs-lookup"><span data-stu-id="d80a3-144">`Import-DscResource` is now a true dynamic keyword.</span></span> <span data-ttu-id="d80a3-145">PowerShell analizza il modulo radice del modulo specificato, alla ricerca delle classi che contengono l'attributo **DscResource**.</span><span class="sxs-lookup"><span data-stu-id="d80a3-145">PowerShell parses the specified module's root module, searching for classes that contain the **DscResource** attribute.</span></span>

### <a name="implementingassembly"></a><span data-ttu-id="d80a3-146">ImplementingAssembly</span><span class="sxs-lookup"><span data-stu-id="d80a3-146">ImplementingAssembly</span></span>

<span data-ttu-id="d80a3-147">Un nuovo campo, **ImplementingAssembly**, è stato aggiunto a **ModuleInfo**.</span><span class="sxs-lookup"><span data-stu-id="d80a3-147">A new field, **ImplementingAssembly**, has been added to **ModuleInfo**.</span></span> <span data-ttu-id="d80a3-148">Viene impostato sull'assembly dinamico creato per un modulo di script se lo script definisce classi oppure sull'assembly caricato per moduli binari.</span><span class="sxs-lookup"><span data-stu-id="d80a3-148">It is set to the dynamic assembly created for a script module if the script defines classes, or the loaded assembly for binary modules.</span></span> <span data-ttu-id="d80a3-149">Non viene impostato quando **ModuleType** è **Manifest**.</span><span class="sxs-lookup"><span data-stu-id="d80a3-149">It is not set when **ModuleType** is **Manifest**.</span></span>

<span data-ttu-id="d80a3-150">La reflection sul campo **ImplementingAssembly** consente di individuare le risorse in un modulo.</span><span class="sxs-lookup"><span data-stu-id="d80a3-150">Reflection on the **ImplementingAssembly** field discovers resources in a module.</span></span> <span data-ttu-id="d80a3-151">Ciò significa che è possibile individuare le risorse scritte in PowerShell o altri linguaggi gestiti.</span><span class="sxs-lookup"><span data-stu-id="d80a3-151">This means you can discover resources written in either PowerShell or other managed languages.</span></span>

<span data-ttu-id="d80a3-152">Campi con inizializzatori:</span><span class="sxs-lookup"><span data-stu-id="d80a3-152">Fields with initializers:</span></span>

```powershell
[int] $i = 5
```

<span data-ttu-id="d80a3-153">`Static` è supportato.</span><span class="sxs-lookup"><span data-stu-id="d80a3-153">`Static` is supported.</span></span> <span data-ttu-id="d80a3-154">Funziona come un attributo, come i vincoli di tipo.</span><span class="sxs-lookup"><span data-stu-id="d80a3-154">It works like an attribute, as do the type constraints.</span></span> <span data-ttu-id="d80a3-155">Può essere specificato in qualsiasi ordine.</span><span class="sxs-lookup"><span data-stu-id="d80a3-155">It can be specified in any order.</span></span>

```powershell
static [int] $count = 0
```

<span data-ttu-id="d80a3-156">Il tipo è facoltativo.</span><span class="sxs-lookup"><span data-stu-id="d80a3-156">A type is optional.</span></span>

```powershell
$s = "hello"
```

<span data-ttu-id="d80a3-157">Tutti i membri sono pubblici.</span><span class="sxs-lookup"><span data-stu-id="d80a3-157">All members are public.</span></span>

### <a name="constructors-and-instantiation"></a><span data-ttu-id="d80a3-158">Costruttori e creazione di istanze</span><span class="sxs-lookup"><span data-stu-id="d80a3-158">Constructors and instantiation</span></span>

<span data-ttu-id="d80a3-159">Le classi di PowerShell possono avere costruttori.</span><span class="sxs-lookup"><span data-stu-id="d80a3-159">PowerShell classes can have constructors.</span></span> <span data-ttu-id="d80a3-160">Hanno lo stesso nome della rispettiva classe.</span><span class="sxs-lookup"><span data-stu-id="d80a3-160">They have the same name as their class.</span></span> <span data-ttu-id="d80a3-161">I costruttori possono essere sottoposti a overload.</span><span class="sxs-lookup"><span data-stu-id="d80a3-161">Constructors can be overloaded.</span></span> <span data-ttu-id="d80a3-162">Sono supportati i costruttori statici.</span><span class="sxs-lookup"><span data-stu-id="d80a3-162">Static constructors are supported.</span></span> <span data-ttu-id="d80a3-163">Le proprietà con espressioni di inizializzazione vengono inizializzate prima di eseguire qualsiasi codice in un costruttore.</span><span class="sxs-lookup"><span data-stu-id="d80a3-163">Properties with initialization expressions are initialized before running any code in a constructor.</span></span> <span data-ttu-id="d80a3-164">Le proprietà statiche vengono inizializzate prima del corpo di un costruttore statico e le proprietà dell'istanza vengono inizializzate prima del corpo del costruttore non statico.</span><span class="sxs-lookup"><span data-stu-id="d80a3-164">Static properties are initialized before the body of a static constructor, and instance properties are initialized before the body of the non-static constructor.</span></span> <span data-ttu-id="d80a3-165">Attualmente non è disponibile alcuna sintassi per chiamare un costruttore da un altro costruttore (analoga alla sintassi C\# ": this()").</span><span class="sxs-lookup"><span data-stu-id="d80a3-165">Currently, there is no syntax for calling a constructor from another constructor (like the C\# syntax ": this()").</span></span> <span data-ttu-id="d80a3-166">La soluzione consiste nel definire un metodo `Init()` comune.</span><span class="sxs-lookup"><span data-stu-id="d80a3-166">The workaround is to define a common `Init()` method.</span></span>

#### <a name="creating-instances"></a><span data-ttu-id="d80a3-167">Creazione di istanze</span><span class="sxs-lookup"><span data-stu-id="d80a3-167">Creating instances</span></span>

> [!NOTE]
> <span data-ttu-id="d80a3-168">In PowerShell 5.0, `New-Object` non funziona con classi definite in PowerShell.</span><span class="sxs-lookup"><span data-stu-id="d80a3-168">In PowerShell 5.0, `New-Object` does not work with classes defined in PowerShell.</span></span> <span data-ttu-id="d80a3-169">Inoltre, il nome del tipo è visibile solo a livello lessicale, vale a dire che non è visibile all'esterno del modulo o dello script che definisce la classe.</span><span class="sxs-lookup"><span data-stu-id="d80a3-169">Also, the type name is only visible lexically, meaning it is not visible outside of the module or script that defines the class.</span></span> <span data-ttu-id="d80a3-170">Le funzioni possono restituire istanze di una classe definita in PowerShell.</span><span class="sxs-lookup"><span data-stu-id="d80a3-170">Functions can return instances of a class defined in PowerShell.</span></span> <span data-ttu-id="d80a3-171">Tali istanze funzionano all'esterno del modulo o dello script.</span><span class="sxs-lookup"><span data-stu-id="d80a3-171">Those instances work outside of the module or script.</span></span>

1. <span data-ttu-id="d80a3-172">Creazione di un'istanza con il costruttore predefinito.</span><span class="sxs-lookup"><span data-stu-id="d80a3-172">Instantiating by using the default constructor.</span></span>

   ```powershell
   $a = [MyClass]::new()
   ```

1. <span data-ttu-id="d80a3-173">Chiamata di un costruttore con un parametro</span><span class="sxs-lookup"><span data-stu-id="d80a3-173">Calling a constructor with a parameter</span></span>

   ```powershell
   $b = [MyClass]::new(42)
   ```

1. <span data-ttu-id="d80a3-174">Passaggio di una matrice a un costruttore con più parametri.</span><span class="sxs-lookup"><span data-stu-id="d80a3-174">Passing an array to a constructor with multiple parameters.</span></span>

   ```powershell
   $c = [MyClass]::new(@(42,43,44), "Hello")
   ```

<span data-ttu-id="d80a3-175">Il metodo pseudo-statico `new()` funziona con i tipi .NET, come illustrato nell'esempio seguente.</span><span class="sxs-lookup"><span data-stu-id="d80a3-175">The pseudo-static method `new()` works with .NET types, as shown in the following example.</span></span>

```powershell
[hashtable]::new()
```

#### <a name="discovering-constructors"></a><span data-ttu-id="d80a3-176">Individuazione dei costruttori</span><span class="sxs-lookup"><span data-stu-id="d80a3-176">Discovering constructors</span></span>

<span data-ttu-id="d80a3-177">È ora possibile visualizzare gli overload del costruttore con `Get-Member` o come illustrato in questo esempio:</span><span class="sxs-lookup"><span data-stu-id="d80a3-177">You can now see constructor overloads with `Get-Member`, or as shown in this example:</span></span>

```powershell
PS> [hashtable]::new
OverloadDefinitions
-------------------
hashtable new()
hashtable new(int capacity)
hashtable new(int capacity, float loadFactor)
```

<span data-ttu-id="d80a3-178">`Get-Member -Static` elenca i costruttori, quindi è possibile visualizzare gli overload come qualsiasi altro metodo.</span><span class="sxs-lookup"><span data-stu-id="d80a3-178">`Get-Member -Static` lists constructors, so you can view overloads like any other method.</span></span> <span data-ttu-id="d80a3-179">Le prestazioni di questa sintassi sono anche notevolmente più veloci rispetto a `New-Object`.</span><span class="sxs-lookup"><span data-stu-id="d80a3-179">The performance of this syntax is also considerably faster than `New-Object`.</span></span>

### <a name="methods"></a><span data-ttu-id="d80a3-180">Metodi</span><span class="sxs-lookup"><span data-stu-id="d80a3-180">Methods</span></span>

<span data-ttu-id="d80a3-181">Un metodo della classe di PowerShell viene implementato come **ScriptBlock** con solo un blocco finale.</span><span class="sxs-lookup"><span data-stu-id="d80a3-181">A PowerShell class method is implemented as a **ScriptBlock** that has only an end block.</span></span> <span data-ttu-id="d80a3-182">Tutti i metodi sono pubblici.</span><span class="sxs-lookup"><span data-stu-id="d80a3-182">All methods are public.</span></span> <span data-ttu-id="d80a3-183">L'esempio seguente illustra la definizione di un metodo denominato **DoSomething**.</span><span class="sxs-lookup"><span data-stu-id="d80a3-183">The following shows an example of defining a method named **DoSomething**.</span></span>

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

<span data-ttu-id="d80a3-184">Chiamata del metodo:</span><span class="sxs-lookup"><span data-stu-id="d80a3-184">Method invocation:</span></span>

```powershell
$b = [MyClass]::new()
$b.DoSomething(42)
```

<span data-ttu-id="d80a3-185">Sono supportati anche i metodi in overload.</span><span class="sxs-lookup"><span data-stu-id="d80a3-185">Overloaded methods are also supported.</span></span>

### <a name="properties"></a><span data-ttu-id="d80a3-186">Proprietà</span><span class="sxs-lookup"><span data-stu-id="d80a3-186">Properties</span></span>

<span data-ttu-id="d80a3-187">Tutte le proprietà sono pubbliche.</span><span class="sxs-lookup"><span data-stu-id="d80a3-187">All properties are public.</span></span> <span data-ttu-id="d80a3-188">Le proprietà richiedono un carattere di nuova riga o un punto e virgola.</span><span class="sxs-lookup"><span data-stu-id="d80a3-188">Properties require either a newline or semicolon.</span></span> <span data-ttu-id="d80a3-189">Se non viene specificato alcun tipo di oggetto, il tipo della proprietà è object.</span><span class="sxs-lookup"><span data-stu-id="d80a3-189">If no object type is specified, the property type is object.</span></span>

<span data-ttu-id="d80a3-190">Le proprietà che usano gli attributi di convalida o di trasformazione degli argomenti (ad esempio `[ValidateSet("aaa")]`) funzionano come previsto.</span><span class="sxs-lookup"><span data-stu-id="d80a3-190">Properties that use validation or argument transformation attributes (like `[ValidateSet("aaa")]`) work as expected.</span></span>

### <a name="hidden"></a><span data-ttu-id="d80a3-191">Hidden</span><span class="sxs-lookup"><span data-stu-id="d80a3-191">Hidden</span></span>

<span data-ttu-id="d80a3-192">È stata aggiunta la nuova parola chiave `Hidden`.</span><span class="sxs-lookup"><span data-stu-id="d80a3-192">A new keyword, `Hidden`, has been added.</span></span> <span data-ttu-id="d80a3-193">È possibile applicare `Hidden` alle proprietà e ai metodi (inclusi i costruttori).</span><span class="sxs-lookup"><span data-stu-id="d80a3-193">`Hidden` can be applied to properties and methods (including constructors).</span></span>

<span data-ttu-id="d80a3-194">I membri nascosti sono pubblici, ma non vengono visualizzati nell'output di `Get-Member`, a meno che non venga aggiunto il parametro `-Force`.</span><span class="sxs-lookup"><span data-stu-id="d80a3-194">Hidden members are public, but do not appear in the output of `Get-Member` unless the `-Force` parameter is added.</span></span> <span data-ttu-id="d80a3-195">I membri nascosti non vengono inclusi quando si usa il completamento con TAB o Intellisense, a meno che il completamento non avvenga nella classe che definisce il membro nascosto.</span><span class="sxs-lookup"><span data-stu-id="d80a3-195">Hidden members are not included when tab completing or using Intellisense unless the completion occurs in the class defining the hidden member.</span></span>

<span data-ttu-id="d80a3-196">È stato aggiunto un nuovo attributo, **System.Management.Automation.HiddenAttribute** in modo che il codice C\# possa avere la stessa semantica all'interno di PowerShell.</span><span class="sxs-lookup"><span data-stu-id="d80a3-196">A new attribute, **System.Management.Automation.HiddenAttribute** has been added so that C\# code can have the same semantics within PowerShell.</span></span>

### <a name="return-types"></a><span data-ttu-id="d80a3-197">Tipi restituiti</span><span class="sxs-lookup"><span data-stu-id="d80a3-197">Return types</span></span>

<span data-ttu-id="d80a3-198">Il tipo restituito è un contratto.</span><span class="sxs-lookup"><span data-stu-id="d80a3-198">Return type is a contract.</span></span> <span data-ttu-id="d80a3-199">Il valore restituito viene convertito nel tipo previsto.</span><span class="sxs-lookup"><span data-stu-id="d80a3-199">The return value is converted to the expected type.</span></span> <span data-ttu-id="d80a3-200">Se non viene specificato alcun tipo restituito, il tipo restituito è **void**.</span><span class="sxs-lookup"><span data-stu-id="d80a3-200">If no return type is specified, the return type is **void**.</span></span> <span data-ttu-id="d80a3-201">Non sono supportati flussi di oggetti.</span><span class="sxs-lookup"><span data-stu-id="d80a3-201">There is no streaming of objects.</span></span> <span data-ttu-id="d80a3-202">Non è possibile scrivere gli oggetti nella pipeline intenzionalmente o accidentalmente.</span><span class="sxs-lookup"><span data-stu-id="d80a3-202">Objects cannot be written to the pipeline either intentionally or by accident.</span></span>

### <a name="attributes"></a><span data-ttu-id="d80a3-203">Attributes</span><span class="sxs-lookup"><span data-stu-id="d80a3-203">Attributes</span></span>

<span data-ttu-id="d80a3-204">Sono stati aggiunti due nuovi attributi, **DscResource** e **DscProperty**.</span><span class="sxs-lookup"><span data-stu-id="d80a3-204">Two new attributes, **DscResource** and **DscProperty** have been added.</span></span>

### <a name="lexical-scoping-of-variables"></a><span data-ttu-id="d80a3-205">Ambito lessicale delle variabili</span><span class="sxs-lookup"><span data-stu-id="d80a3-205">Lexical scoping of variables</span></span>

<span data-ttu-id="d80a3-206">Di seguito viene riportato un esempio di come funziona l'assegnazione dell'ambito lessicale in questa versione.</span><span class="sxs-lookup"><span data-stu-id="d80a3-206">The following shows an example of how lexical scoping works in this release.</span></span>

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

## <a name="end-to-end-example"></a><span data-ttu-id="d80a3-207">Esempio end-to-end</span><span class="sxs-lookup"><span data-stu-id="d80a3-207">End-to-End Example</span></span>

<span data-ttu-id="d80a3-208">L'esempio seguente crea alcune classi personalizzate per implementare un documento DSL (Dynamic Stylesheet Language) HTML.</span><span class="sxs-lookup"><span data-stu-id="d80a3-208">The following example creates some custom classes to implement an HTML dynamic style sheet language (DSL).</span></span> <span data-ttu-id="d80a3-209">L'esempio aggiunge quindi funzioni helper per creare tipi di elemento specifici come parte della classe Element, ad esempio stili del titolo e tabelle, poiché i tipi non possono essere usati all'esterno dell'ambito di un modulo.</span><span class="sxs-lookup"><span data-stu-id="d80a3-209">Then, the example adds helper functions to create specific element types as part of the element class, such as heading styles and tables, because types cannot be used outside the scope of a module.</span></span>

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
# These are required because types aren't visible outside of the module.
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
        TR (-join $Properties.Foreach{ TD ($row.$_) } )
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
