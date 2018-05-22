---
ms.date: 06/12/2017
keywords: wmf,powershell,installazione
ms.openlocfilehash: d7aec1a2ba8964e877ddd7406609fe135b1eb462
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/17/2018
---
# <a name="call-base-class-method"></a>Chiamare il metodo della classe di base

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

Per chiamare metodi della classe di base da implementazioni sottoposte a override, eseguire il cast della classe di base ([baseClass]$this) nella chiamata:

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
