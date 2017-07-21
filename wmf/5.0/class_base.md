---
ms.date: 2017-06-12
author: JKeithB
ms.topic: reference
keywords: wmf,powershell,installazione
ms.openlocfilehash: fc517cd204b8f2647b824f0b9ee8f0f8f62fb821
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 06/12/2017
---
# <a name="declare-base-class"></a><span data-ttu-id="38d3f-102">Dichiarare una classe di base</span><span class="sxs-lookup"><span data-stu-id="38d3f-102">Declare Base Class</span></span>
<span data-ttu-id="38d3f-103">È possibile dichiarare una classe di Windows PowerShell come tipo di base per un'altra classe di Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="38d3f-103">You can declare a Windows PowerShell class as a base type for another Windows PowerShell class.</span></span>

```PowerShell
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

<span data-ttu-id="38d3f-104">Si possono anche usare i tipi .NET Framework esistenti come classi di base:</span><span class="sxs-lookup"><span data-stu-id="38d3f-104">You can also use existing .NET Framework types as base classes:</span></span>

```PowerShell
class MyIntList : system.collections.generic.list[int]
{
    
}

$list = [MyIntList]::new()

$list.Add(100)

$list[0] # return 100
```

