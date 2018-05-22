---
ms.date: 06/12/2017
keywords: wmf,powershell,installazione
ms.openlocfilehash: 9486fdbaeca66c83551564c76ce47482f77c36b9
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/17/2018
---
# <a name="call-base-class-constructor"></a>Chiamare il costruttore della classe di base

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
