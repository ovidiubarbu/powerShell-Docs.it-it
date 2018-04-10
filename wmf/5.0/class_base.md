---
ms.date: 06/12/2017
author: JKeithB
ms.topic: reference
keywords: wmf,powershell,installazione
ms.openlocfilehash: 43b26426a76b6503a83e35ae0c02a0af69902ed6
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/09/2018
---
# <a name="declare-base-class"></a><span data-ttu-id="72175-102">Dichiarare una classe di base</span><span class="sxs-lookup"><span data-stu-id="72175-102">Declare Base Class</span></span>
<span data-ttu-id="72175-103">È possibile dichiarare una classe di Windows PowerShell come tipo di base per un'altra classe di Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="72175-103">You can declare a Windows PowerShell class as a base type for another Windows PowerShell class.</span></span>

```powershell
class bar
{
   [int]foo()
       {
           return 100500
       }
}

class baz : bar {}

[baz]::new().foo() # return 100500
```

<span data-ttu-id="72175-104">Si possono anche usare i tipi .NET Framework esistenti come classi di base:</span><span class="sxs-lookup"><span data-stu-id="72175-104">You can also use existing .NET Framework types as base classes:</span></span>

```powershell
class MyIntList : system.collections.generic.list[int]
{

}

$list = [MyIntList]::new()

$list.Add(100)

$list[0] # return 100
```