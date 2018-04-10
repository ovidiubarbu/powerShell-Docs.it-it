---
ms.date: 06/12/2017
author: JKeithB
ms.topic: reference
keywords: wmf,powershell,installazione
ms.openlocfilehash: 1f165afbcd8fe8dc5f72cc7ea557d21ce2884e91
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/09/2018
---
# <a name="nonewline-parameter"></a><span data-ttu-id="a1cf3-102">Parametro NoNewLine</span><span class="sxs-lookup"><span data-stu-id="a1cf3-102">NoNewLine parameter</span></span>
<span data-ttu-id="a1cf3-103">Per **Out-File**, **Add-Content** e **Set-Content** è ora disponibile una nuova opzione **-NoNewline** che omette semplicemente una nuova riga dopo l'output.</span><span class="sxs-lookup"><span data-stu-id="a1cf3-103">**Out-File**, **Add-Content**, and **Set-Content** now have a new **–NoNewline** switch which simply omits a new line after the output.</span></span>
```powershell
PS C:\> "This is " | Out-File -FilePath Example.txt -NoNewline

PS C:\>; "a single " | Add-Content -Path Example.txt -NoNewline

PS C:\> "sentence." | Add-Content -Path Example.txt -NoNewline

PS C:\> Get-Content .\Example.txt

This is a single sentence.
```
<span data-ttu-id="a1cf3-104">Senza specificare **-NoNewline**, ogni frammento sarebbe su una riga separata:</span><span class="sxs-lookup"><span data-stu-id="a1cf3-104">Without **–NoNewline** specified, each fragment would be on a separate line:</span></span>
```powershell
PS C:\> "This is " | Out-File -FilePath Example.txt

PS C:\> "a single " | Add-Content -Path Example.txt

PS C:\> "sentence." | Add-Content -Path Example.txt

PS C:\> Get-Content .\Example.txt

This is

a single

sentence.
```