---
ms.date: 06/12/2017
keywords: wmf,powershell,installazione
ms.openlocfilehash: e01f6ceea361f5a9b3de645346d0652986b6267d
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62057231"
---
# <a name="nonewline-parameter"></a><span data-ttu-id="e5b7a-102">Parametro NoNewLine</span><span class="sxs-lookup"><span data-stu-id="e5b7a-102">NoNewLine parameter</span></span>
<span data-ttu-id="e5b7a-103">Per **Out-File**, **Add-Content** e **Set-Content** è ora disponibile una nuova opzione **-NoNewline** che omette semplicemente una nuova riga dopo l'output.</span><span class="sxs-lookup"><span data-stu-id="e5b7a-103">**Out-File**, **Add-Content**, and **Set-Content** now have a new **–NoNewline** switch which simply omits a new line after the output.</span></span>
```powershell
PS C:\> "This is " | Out-File -FilePath Example.txt -NoNewline

PS C:\>; "a single " | Add-Content -Path Example.txt -NoNewline

PS C:\> "sentence." | Add-Content -Path Example.txt -NoNewline

PS C:\> Get-Content .\Example.txt

This is a single sentence.
```
<span data-ttu-id="e5b7a-104">Senza specificare **-NoNewline**, ogni frammento sarebbe su una riga separata:</span><span class="sxs-lookup"><span data-stu-id="e5b7a-104">Without **–NoNewline** specified, each fragment would be on a separate line:</span></span>
```powershell
PS C:\> "This is " | Out-File -FilePath Example.txt

PS C:\> "a single " | Add-Content -Path Example.txt

PS C:\> "sentence." | Add-Content -Path Example.txt

PS C:\> Get-Content .\Example.txt

This is

a single

sentence.
```
