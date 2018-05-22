---
ms.date: 06/12/2017
keywords: wmf,powershell,installazione
ms.openlocfilehash: 188ede0c558210a746ad0f6c6cef6f571b280878
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/17/2018
---
# <a name="declare-base-class"></a><span data-ttu-id="99b32-102">Dichiarare una classe di base</span><span class="sxs-lookup"><span data-stu-id="99b32-102">Declare Base Class</span></span>
<span data-ttu-id="99b32-103">È possibile dichiarare una classe di Windows PowerShell come tipo di base per un'altra classe di Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="99b32-103">You can declare a Windows PowerShell class as a base type for another Windows PowerShell class.</span></span>

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

<span data-ttu-id="99b32-104">Si possono anche usare i tipi .NET Framework esistenti come classi di base:</span><span class="sxs-lookup"><span data-stu-id="99b32-104">You can also use existing .NET Framework types as base classes:</span></span>

```powershell
class MyIntList : system.collections.generic.list[int]
{

}

$list = [MyIntList]::new()

$list.Add(100)

$list[0] # return 100
```
