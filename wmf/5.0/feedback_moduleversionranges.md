---
ms.date: 06/12/2017
keywords: wmf,powershell,installazione
ms.openlocfilehash: e2c9233734a6ede04e8ec2bbad05950cbb31cbba
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62057508"
---
# <a name="modules-support-for-declaring-version-ranges-1-etc"></a><span data-ttu-id="11f18-102">Supporto di moduli per la dichiarazione di intervalli di versione (1.\* e così via)</span><span class="sxs-lookup"><span data-stu-id="11f18-102">Modules support for declaring version ranges (1.\*, etc)</span></span>
<span data-ttu-id="11f18-103">In combinazione con **-MinimumVersion**, **-MaximumVersion** consente ora agli utenti di recuperare/importare un modulo entro un intervallo specifico.</span><span class="sxs-lookup"><span data-stu-id="11f18-103">Combined with **-MinimumVersion**, **-MaximumVersion** now allows user to get/import module within specific range.</span></span> <span data-ttu-id="11f18-104">Il parametro supporta anche **.**\*.</span><span class="sxs-lookup"><span data-stu-id="11f18-104">The parameter also support **.**\*.</span></span> <span data-ttu-id="11f18-105">L'esempio seguente mostra come funziona:</span><span class="sxs-lookup"><span data-stu-id="11f18-105">The following example shows how it works:</span></span>

<span data-ttu-id="11f18-106">A questo punto è possibile combinare **-MinimumVersion** e **-MaximumVersion** per importare un modulo entro un intervallo specifico:</span><span class="sxs-lookup"><span data-stu-id="11f18-106">Now, you can combine **-MinimumVersion** and **-MaximumVersion** to import module within specific range:</span></span>

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
