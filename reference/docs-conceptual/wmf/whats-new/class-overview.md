---
ms.date: 06/12/2017
keywords: wmf,powershell,installazione
title: Creazione di tipi personalizzati con le classi di PowerShell
ms.openlocfilehash: c2c50fb65ce4931fcf6ae529b4146df391c831c4
ms.sourcegitcommit: 6545c60578f7745be015111052fd7769f8289296
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/22/2020
ms.locfileid: "71147841"
---
# <a name="creating-custom-types-using-powershell-classes"></a>Creazione di tipi personalizzati con le classi di PowerShell

In PowerShell 5.0 è stata aggiunta la possibilità di definire classi e altri tipi definiti dall'utente usando sintassi e semantica formali simili ad altri linguaggi di programmazione orientata agli oggetti. L'obiettivo è consentire agli sviluppatori e ai professionisti IT di adottare PowerShell per una vasta gamma di casi d'uso, semplificare lo sviluppo di artefatti di PowerShell (ad esempio risorse DSC) e velocizzare la copertura delle aree di gestione.

## <a name="supported-scenarios-in-this-release"></a>Scenari supportati in questa versione

- Definire risorse DSC e i relativi tipi associati usando il linguaggio di PowerShell
- Definire tipi personalizzati in PowerShell usando costrutti noti della programmazione orientata agli oggetti, come classi, proprietà, metodi e così via.
- Supporto dell'ereditarietà con le classi in PowerShell e le risorse DSC basate su classi
- Eseguire il debug di tipi con il linguaggio di PowerShell
- Generare e gestire le eccezioni tramite meccanismi formali, al giusto livello

## <a name="declare-base-class"></a>Dichiarare una classe di base

È possibile dichiarare una classe di PowerShell come tipo di base per un'altra classe di PowerShell.

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

Si possono anche usare i tipi .NET Framework esistenti come classi di base:

```powershell
class MyIntList : system.collections.generic.list[int]
{

}

$list = [MyIntList]::new()

$list.Add(100)

$list[0] # return 100
```

### <a name="call-base-class-constructor"></a>Chiamare il costruttore della classe di base

Per chiamare un costruttore di classe di base da una sottoclasse, usare la parola chiave **base**:

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

Se una classe di base ha un costruttore predefinito (nessun parametro), è possibile omettere una chiamata esplicita al costruttore:

```powershell
class C : B
{
    C([int]$c) {}
}
```

### <a name="call-base-class-method"></a>Chiamare il metodo della classe di base

È possibile eseguire l'override di metodi esistenti nelle sottoclassi. A tale scopo, dichiarare metodi con lo stesso nome e firma:

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

Per chiamare metodi della classe di base da implementazioni sottoposte a override, eseguire il cast della classe di base (`[baseClass]$this`) nella chiamata:

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

Tutti i metodi di PowerShell sono virtuali. È possibile nascondere i metodi .NET non virtuali in una sottoclasse con la stessa sintassi usata per un override, ovvero dichiarando i metodi con lo stesso nome e firma.

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

### <a name="declare-implemented-interface"></a>Dichiarare l'interfaccia implementata

È possibile dichiarare le interfacce implementate dopo i tipi di base o subito dopo i due punti (:), se non è specificato alcun tipo di base. Usare le virgole per separare tutti i nomi di tipo. La sintassi è simile a quella di C#.

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

## <a name="new-language-features-in-powershell-50"></a>Nuove funzionalità del linguaggio in PowerShell 5.0

Con PowerShell 5.0 sono stati introdotti i seguenti elementi del linguaggio nuovi in PowerShell:

### <a name="class-keyword"></a>Parola chiave class

La parola chiave `class` definisce una nuova classe. Si tratta di un vero tipo .NET Framework. I membri di classe sono pubblici, ma solo all'interno dell'ambito del modulo. È possibile fare riferimento al nome del tipo come stringa (ad esempio, `New-Object` non funziona) e, in questa versione, è possibile usare un valore letterale di tipo (ad esempio, `[MyClass]`) all'esterno del file di script o modulo in cui è definita la classe.

```powershell
class MyClass
{
    ...
}
```

### <a name="enum-keyword-and-enumerations"></a>Parola chiave enum ed enumerazioni

È stato aggiunto il supporto della parola chiave `enum`, che usa il carattere di nuova riga come delimitatore. Attualmente, non è possibile definire un enumeratore in termini di se stesso. Tuttavia, è possibile inizializzare un enum in termini di un altro enum, come illustrato nell'esempio seguente. Inoltre, non è attualmente possibile specificare il tipo di base, che è sempre `[int]`.

```powershell
enum Color2
{
    Yellow = [Color]::Blue
}
```

Un valore di enumeratore deve essere una costante in fase di analisi. Non è possibile impostarlo sul risultato di un comando richiamato.

```powershell
enum MyEnum
{
    Enum1
    Enum2
    Enum3 = 42
    Enum4 = [int]::MaxValue
}
```

Gli enumeratori supportano operazioni aritmetiche, come mostrato nell'esempio seguente.

```powershell
enum SomeEnum { Max = 42 }
enum OtherEnum { Max = [SomeEnum]::Max + 1 }
```

### <a name="import-dscresource"></a>Import-DscResource

`Import-DscResource` è ora una parola chiave effettivamente dinamica. PowerShell analizza il modulo radice del modulo specificato, alla ricerca delle classi che contengono l'attributo **DscResource**.

### <a name="implementingassembly"></a>ImplementingAssembly

Un nuovo campo, **ImplementingAssembly**, è stato aggiunto a **ModuleInfo**. Viene impostato sull'assembly dinamico creato per un modulo di script se lo script definisce classi oppure sull'assembly caricato per moduli binari. Non viene impostato quando **ModuleType** è **Manifest**.

La reflection sul campo **ImplementingAssembly** consente di individuare le risorse in un modulo. Ciò significa che è possibile individuare le risorse scritte in PowerShell o altri linguaggi gestiti.

Campi con inizializzatori:

```powershell
[int] $i = 5
```

`Static` è supportato. Funziona come un attributo, come i vincoli di tipo. Può essere specificato in qualsiasi ordine.

```powershell
static [int] $count = 0
```

Il tipo è facoltativo.

```powershell
$s = "hello"
```

Tutti i membri sono pubblici.

### <a name="constructors-and-instantiation"></a>Costruttori e creazione di istanze

Le classi di PowerShell possono avere costruttori. Hanno lo stesso nome della rispettiva classe. I costruttori possono essere sottoposti a overload. Sono supportati i costruttori statici. Le proprietà con espressioni di inizializzazione vengono inizializzate prima di eseguire qualsiasi codice in un costruttore. Le proprietà statiche vengono inizializzate prima del corpo di un costruttore statico e le proprietà dell'istanza vengono inizializzate prima del corpo del costruttore non statico. Attualmente non è disponibile alcuna sintassi per chiamare un costruttore da un altro costruttore (analoga alla sintassi C\# ": this()"). La soluzione consiste nel definire un metodo `Init()` comune.

#### <a name="creating-instances"></a>Creazione di istanze

> [!NOTE]
> In PowerShell 5.0, `New-Object` non funziona con classi definite in PowerShell. Inoltre, il nome del tipo è visibile solo a livello lessicale, vale a dire che non è visibile all'esterno del modulo o dello script che definisce la classe. Le funzioni possono restituire istanze di una classe definita in PowerShell. Tali istanze funzionano all'esterno del modulo o dello script.

1. Creazione di un'istanza con il costruttore predefinito.

   ```powershell
   $a = [MyClass]::new()
   ```

1. Chiamata di un costruttore con un parametro

   ```powershell
   $b = [MyClass]::new(42)
   ```

1. Passaggio di una matrice a un costruttore con più parametri.

   ```powershell
   $c = [MyClass]::new(@(42,43,44), "Hello")
   ```

Il metodo pseudo-statico `new()` funziona con i tipi .NET, come illustrato nell'esempio seguente.

```powershell
[hashtable]::new()
```

#### <a name="discovering-constructors"></a>Individuazione dei costruttori

È ora possibile visualizzare gli overload del costruttore con `Get-Member` o come illustrato in questo esempio:

```powershell
PS> [hashtable]::new
OverloadDefinitions
-------------------
hashtable new()
hashtable new(int capacity)
hashtable new(int capacity, float loadFactor)
```

`Get-Member -Static` elenca i costruttori, quindi è possibile visualizzare gli overload come qualsiasi altro metodo. Le prestazioni di questa sintassi sono anche notevolmente più veloci rispetto a `New-Object`.

### <a name="methods"></a>Metodi

Un metodo della classe di PowerShell viene implementato come **ScriptBlock** con solo un blocco finale. Tutti i metodi sono pubblici. L'esempio seguente illustra la definizione di un metodo denominato **DoSomething**.

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

Chiamata del metodo:

```powershell
$b = [MyClass]::new()
$b.DoSomething(42)
```

Sono supportati anche i metodi in overload.

### <a name="properties"></a>Proprietà

Tutte le proprietà sono pubbliche. Le proprietà richiedono un carattere di nuova riga o un punto e virgola. Se non viene specificato alcun tipo di oggetto, il tipo della proprietà è object.

Le proprietà che usano gli attributi di convalida o di trasformazione degli argomenti (ad esempio `[ValidateSet("aaa")]`) funzionano come previsto.

### <a name="hidden"></a>Nascosto

È stata aggiunta la nuova parola chiave `Hidden`. È possibile applicare `Hidden` alle proprietà e ai metodi (inclusi i costruttori).

I membri nascosti sono pubblici, ma non vengono visualizzati nell'output di `Get-Member`, a meno che non venga aggiunto il parametro `-Force`. I membri nascosti non vengono inclusi quando si usa il completamento con TAB o Intellisense, a meno che il completamento non avvenga nella classe che definisce il membro nascosto.

È stato aggiunto un nuovo attributo, **System.Management.Automation.HiddenAttribute** in modo che il codice C\# possa avere la stessa semantica all'interno di PowerShell.

### <a name="return-types"></a>Tipi restituiti

Il tipo restituito è un contratto. Il valore restituito viene convertito nel tipo previsto. Se non viene specificato alcun tipo restituito, il tipo restituito è **void**. Non sono supportati flussi di oggetti. Non è possibile scrivere gli oggetti nella pipeline intenzionalmente o accidentalmente.

### <a name="attributes"></a>Attributes

Sono stati aggiunti due nuovi attributi, **DscResource** e **DscProperty**.

### <a name="lexical-scoping-of-variables"></a>Ambito lessicale delle variabili

Di seguito viene riportato un esempio di come funziona l'assegnazione dell'ambito lessicale in questa versione.

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

## <a name="end-to-end-example"></a>Esempio end-to-end

L'esempio seguente crea alcune classi personalizzate per implementare un documento DSL (Dynamic Stylesheet Language) HTML. L'esempio aggiunge quindi funzioni helper per creare tipi di elemento specifici come parte della classe Element, ad esempio stili del titolo e tabelle, poiché i tipi non possono essere usati all'esterno dell'ambito di un modulo.

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
