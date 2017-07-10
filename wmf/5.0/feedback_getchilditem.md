---
ms.date: 2017-06-12
author: JKeithB
ms.topic: reference
keywords: wmf,powershell,installazione
ms.openlocfilehash: 4185d9395f2f3e5ba1c8daa0c365cb2bf322936b
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 06/12/2017
---
<a id="get-childitem-has--depth-parameter" class="xliff"></a>
# Parametro -Depth per Get-ChildItem
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

