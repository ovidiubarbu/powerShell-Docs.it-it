---
ms.date: 2017-06-12
author: JKeithB
ms.topic: reference
keywords: wmf,powershell,impostazione
ms.openlocfilehash: 968e78beb8df77588a08a9ce8732e4abcadde4d0
ms.sourcegitcommit: a5c0795ca6ec9332967bff9c151a8572feb1a53a
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 07/27/2017
---
# <a name="declare-implemented-interface"></a><span data-ttu-id="b76c5-102">Dichiarare l'interfaccia implementata</span><span class="sxs-lookup"><span data-stu-id="b76c5-102">Declare Implemented Interface</span></span>

<span data-ttu-id="b76c5-103">È possibile dichiarare le interfacce implementate dopo i tipi di base o subito dopo i due punti (:), se non è specificato alcun tipo di base.</span><span class="sxs-lookup"><span data-stu-id="b76c5-103">You can declare implemented interfaces after base types, or immediately after a colon (:), if there is no base type specified.</span></span> <span data-ttu-id="b76c5-104">Usare le virgole per separare tutti i nomi di tipo.</span><span class="sxs-lookup"><span data-stu-id="b76c5-104">Separate all type names by using commas.</span></span> <span data-ttu-id="b76c5-105">La sintassi è molto simile a quella di C#.</span><span class="sxs-lookup"><span data-stu-id="b76c5-105">It’s very similar to C# syntax.</span></span>

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

