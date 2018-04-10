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
# <a name="call-base-class-constructor"></a><span data-ttu-id="964d9-102">Chiamare il costruttore della classe di base</span><span class="sxs-lookup"><span data-stu-id="964d9-102">Call Base Class Constructor</span></span>

<span data-ttu-id="964d9-103">Per chiamare un costruttore di classe di base da una sottoclasse, usare la parola chiave **base**:</span><span class="sxs-lookup"><span data-stu-id="964d9-103">To call a base class constructor from a subclass, use the keyword **base**:</span></span>

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

<span data-ttu-id="964d9-104">Se una classe di base ha un costruttore predefinito (nessun parametro), è possibile omettere una chiamata esplicita al costruttore:</span><span class="sxs-lookup"><span data-stu-id="964d9-104">If a base class has a default (no parameter) constructor, you can omit an explicit constructor call:</span></span>

```powershell
class C : B
{
    C([int]$c) {}
}
```