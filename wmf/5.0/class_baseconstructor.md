---
ms.date: 06/12/2017
keywords: wmf,powershell,installazione
ms.openlocfilehash: 9486fdbaeca66c83551564c76ce47482f77c36b9
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/17/2018
ms.locfileid: "34225607"
---
# <a name="call-base-class-constructor"></a><span data-ttu-id="b231e-102">Chiamare il costruttore della classe di base</span><span class="sxs-lookup"><span data-stu-id="b231e-102">Call Base Class Constructor</span></span>

<span data-ttu-id="b231e-103">Per chiamare un costruttore di classe di base da una sottoclasse, usare la parola chiave **base**:</span><span class="sxs-lookup"><span data-stu-id="b231e-103">To call a base class constructor from a subclass, use the keyword **base**:</span></span>

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

<span data-ttu-id="b231e-104">Se una classe di base ha un costruttore predefinito (nessun parametro), è possibile omettere una chiamata esplicita al costruttore:</span><span class="sxs-lookup"><span data-stu-id="b231e-104">If a base class has a default (no parameter) constructor, you can omit an explicit constructor call:</span></span>

```powershell
class C : B
{
    C([int]$c) {}
}
```
