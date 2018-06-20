---
ms.date: 06/12/2017
keywords: wmf,powershell,installazione
ms.openlocfilehash: 116f79a95126d0a1c579a95ec99eb5d8b75cc1e0
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/17/2018
ms.locfileid: "34225488"
---
# <a name="declare-implemented-interface"></a><span data-ttu-id="c8fe1-102">Dichiarare l'interfaccia implementata</span><span class="sxs-lookup"><span data-stu-id="c8fe1-102">Declare Implemented Interface</span></span>

<span data-ttu-id="c8fe1-103">È possibile dichiarare le interfacce implementate dopo i tipi di base o subito dopo i due punti (:), se non è specificato alcun tipo di base.</span><span class="sxs-lookup"><span data-stu-id="c8fe1-103">You can declare implemented interfaces after base types, or immediately after a colon (:), if there is no base type specified.</span></span> <span data-ttu-id="c8fe1-104">Usare le virgole per separare tutti i nomi di tipo.</span><span class="sxs-lookup"><span data-stu-id="c8fe1-104">Separate all type names by using commas.</span></span> <span data-ttu-id="c8fe1-105">La sintassi è molto simile a quella di C#.</span><span class="sxs-lookup"><span data-stu-id="c8fe1-105">It’s very similar to C# syntax.</span></span>

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
