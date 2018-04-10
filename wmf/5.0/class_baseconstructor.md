---
ms.date: 06/12/2017
author: JKeithB
ms.topic: reference
keywords: wmf,powershell,installazione
ms.openlocfilehash: 3269c8cc871f22488b64fb072dac72698983f360
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/09/2018
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