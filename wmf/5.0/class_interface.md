---
ms.date: 06/12/2017
keywords: wmf,powershell,installazione
ms.openlocfilehash: 4b593e9a1eca43ee7ad85fc921ae3c1d62722db9
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62085862"
---
# <a name="declare-implemented-interface"></a><span data-ttu-id="2d61f-102">Dichiarare l'interfaccia implementata</span><span class="sxs-lookup"><span data-stu-id="2d61f-102">Declare Implemented Interface</span></span>

<span data-ttu-id="2d61f-103">È possibile dichiarare le interfacce implementate dopo i tipi di base o subito dopo i due punti (:), se non è specificato alcun tipo di base.</span><span class="sxs-lookup"><span data-stu-id="2d61f-103">You can declare implemented interfaces after base types, or immediately after a colon (:), if there is no base type specified.</span></span> <span data-ttu-id="2d61f-104">Usare le virgole per separare tutti i nomi di tipo.</span><span class="sxs-lookup"><span data-stu-id="2d61f-104">Separate all type names by using commas.</span></span> <span data-ttu-id="2d61f-105">La sintassi è molto simile a quella di C#.</span><span class="sxs-lookup"><span data-stu-id="2d61f-105">It’s very similar to C# syntax.</span></span>

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
