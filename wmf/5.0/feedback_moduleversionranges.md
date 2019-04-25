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
# <a name="modules-support-for-declaring-version-ranges-1-etc"></a>Supporto di moduli per la dichiarazione di intervalli di versione (1.* e così via)
In combinazione con **-MinimumVersion**, **-MaximumVersion** consente ora agli utenti di recuperare/importare un modulo entro un intervallo specifico. Il parametro supporta anche **.**\*. L'esempio seguente mostra come funziona:

A questo punto è possibile combinare **-MinimumVersion** e **-MaximumVersion** per importare un modulo entro un intervallo specifico:

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
