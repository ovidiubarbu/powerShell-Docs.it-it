---
ms.date: 06/12/2017
author: JKeithB
ms.topic: reference
keywords: wmf,powershell,installazione
ms.openlocfilehash: 2c007321789ae22b4a2e048d2d64162b065f9a75
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/09/2018
---
# <a name="declare-implemented-interface"></a><span data-ttu-id="1d1f7-102">Dichiarare l'interfaccia implementata</span><span class="sxs-lookup"><span data-stu-id="1d1f7-102">Declare Implemented Interface</span></span>

<span data-ttu-id="1d1f7-103">È possibile dichiarare le interfacce implementate dopo i tipi di base o subito dopo i due punti (:), se non è specificato alcun tipo di base.</span><span class="sxs-lookup"><span data-stu-id="1d1f7-103">You can declare implemented interfaces after base types, or immediately after a colon (:), if there is no base type specified.</span></span> <span data-ttu-id="1d1f7-104">Usare le virgole per separare tutti i nomi di tipo.</span><span class="sxs-lookup"><span data-stu-id="1d1f7-104">Separate all type names by using commas.</span></span> <span data-ttu-id="1d1f7-105">La sintassi è molto simile a quella di C#.</span><span class="sxs-lookup"><span data-stu-id="1d1f7-105">It’s very similar to C# syntax.</span></span>

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