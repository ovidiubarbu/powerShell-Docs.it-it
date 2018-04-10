---
ms.date: 06/12/2017
author: JKeithB
ms.topic: reference
keywords: wmf,powershell,installazione
ms.openlocfilehash: 62cccabd7c63c6ba928fc2bf8addd3d11483e90f
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/09/2018
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