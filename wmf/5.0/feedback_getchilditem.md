---
ms.date: 06/12/2017
keywords: wmf,powershell,installazione
ms.openlocfilehash: d9f1ca10c948b06b234e17f688b8f899ed41c5d6
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/17/2018
ms.locfileid: "34221902"
---
# <a name="get-childitem-has--depth-parameter"></a>Parametro -Depth per Get-ChildItem
**Get-ChildItem** include ora un parametro **-Depth** utilizzabile con **-Recurse** per limitare la ricorsione:

PS C:\\Users\\slee\\Downloads\\Example&gt; Get-ChildItem -Recurse -Depth 0

Directory: C:\\Users\\slee\\Downloads\\Example

Mode LastWriteTime Length Name

---- ------------- ------ ----

d----- 14/04/2015 17.36 Depth0

-a---- 14/04/2015 1.19 0 File1.txt

-a---- 14/04/2015 1.19 0 File2.txt

-a---- 14/04/2015 1.19 0 File3.txt

PS C:\\Users\\slee\\Downloads\\Example&gt; Get-ChildItem -Recurse -Depth 1

Directory: C:\\Users\\slee\\Downloads\\Example

Mode LastWriteTime Length Name

---- ------------- ------ ----

d----- 14/04/2015 17.36 Depth0

-a---- 14/04/2015 1.19 0 File1.txt

-a---- 14/04/2015 1.19 0 File2.txt

-a---- 14/04/2015 1.19 0 File3.txt

Directory: C:\\Users\\slee\\Downloads\\Example\\Depth0

Mode LastWriteTime Length Name

---- ------------- ------ ----

d----- 14/04/2015 17.33 Depth1
