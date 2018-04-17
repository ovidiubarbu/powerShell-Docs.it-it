---
ms.date: 06/12/2017
author: JKeithB
ms.topic: reference
keywords: wmf,powershell,installazione
ms.openlocfilehash: 89e908969641afd9ad9541dcfedcc8eb6315d07c
ms.sourcegitcommit: ece1794c94be4880a2af5a2605ed4721593643b6
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="modules-support-for-declaring-version-ranges-1-etc"></a><span data-ttu-id="2a4d8-102">Supporto di moduli per la dichiarazione di intervalli di versione (1.\* e così via)</span><span class="sxs-lookup"><span data-stu-id="2a4d8-102">Modules support for declaring version ranges (1.\*, etc)</span></span>
<span data-ttu-id="2a4d8-103">In combinazione con **-MinimumVersion**, **-MaximumVersion** consente ora agli utenti di recuperare/importare un modulo entro un intervallo specifico.</span><span class="sxs-lookup"><span data-stu-id="2a4d8-103">Combined with **-MinimumVersion**, **-MaximumVersion** now allows user to get/import module within specific range.</span></span> <span data-ttu-id="2a4d8-104">Il parametro supporta anche **.** \*.</span><span class="sxs-lookup"><span data-stu-id="2a4d8-104">The parameter also support **.**\*.</span></span> <span data-ttu-id="2a4d8-105">L'esempio seguente mostra come funziona:</span><span class="sxs-lookup"><span data-stu-id="2a4d8-105">The following example shows how it works:</span></span>

<span data-ttu-id="2a4d8-106">A questo punto, è possibile combinare **- MinimumVersion** e **- MaximumVersion** per importare un modulo entro un intervallo specifico:</span><span class="sxs-lookup"><span data-stu-id="2a4d8-106">Now, you can combine **-MinimumVersion** and **-MaximumVersion** to import module within specific range:</span></span>

```powershell
PS C:\> Import-Module psreadline -Verbose -MinimumVersion 1.0 -MaximumVersion 1.2.*

VERBOSE: Loading module from path 'C:\Program Files\WindowsPowerShell\Modules\psreadline\1.1\psreadline.psd1'.
VERBOSE: Importing cmdlet 'Get-PSReadlineKeyHandler'.
VERBOSE: Importing cmdlet 'Get-PSReadlineOption'.
VERBOSE: Importing cmdlet 'Remove-PSReadlineKeyHandler'.
VERBOSE: Importing cmdlet 'Set-PSReadlineKeyHandler'.
VERBOSE: Importing cmdlet 'Set-PSReadlineOption'.
VERBOSE: Importing function 'PSConsoleHostReadline'.
```
