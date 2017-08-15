---
ms.date: 2017-06-12T00:00:00.000Z
author: JKeithB
ms.topic: reference
keywords: wmf,powershell,installazione
ms.openlocfilehash: 1fd6d80d6b7effb4bd98c1594d64e531c4e5c9b5
ms.sourcegitcommit: a5c0795ca6ec9332967bff9c151a8572feb1a53a
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 07/27/2017
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

