---
ms.date: 2017-06-12
author: JKeithB
ms.topic: reference
keywords: wmf,powershell,installazione
ms.openlocfilehash: 403a79e17b832b5c58fd21a138fcebb8adb76d40
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 06/12/2017
---
<a id="call-base-class-constructor" class="xliff"></a>
# Chiamare il costruttore della classe di base

Per chiamare un costruttore di classe di base da una sottoclasse, usare la parola chiave **base**:

```PowerShell
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

```PowerShell
class C : B
{
    C([int]$c) {}
}
```

