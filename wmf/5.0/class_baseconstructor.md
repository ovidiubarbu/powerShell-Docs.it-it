---
ms.date: 06/12/2017
keywords: wmf,powershell,installazione
ms.openlocfilehash: 424e0b7a4d62fc35e5040a7e425950e887021d7e
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62085882"
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
