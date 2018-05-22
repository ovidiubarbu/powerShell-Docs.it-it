---
ms.date: 06/12/2017
keywords: wmf,powershell,installazione
ms.openlocfilehash: 116f79a95126d0a1c579a95ec99eb5d8b75cc1e0
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/17/2018
---
# <a name="declare-implemented-interface"></a>Dichiarare l'interfaccia implementata

È possibile dichiarare le interfacce implementate dopo i tipi di base o subito dopo i due punti (:), se non è specificato alcun tipo di base. Usare le virgole per separare tutti i nomi di tipo. La sintassi è molto simile a quella di C#.

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
