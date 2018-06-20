---
ms.date: 06/12/2017
keywords: wmf,powershell,installazione
ms.openlocfilehash: d4168640f67cb1dd44e91d1867e87fd7a6b7f549
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/17/2018
ms.locfileid: "34218351"
---
# <a name="side-by-side-version-support-on-powershell-50-or-newer"></a><span data-ttu-id="c9c4d-102">Supporto delle versioni side-by-side in PowerShell 5.0 o versione successiva</span><span class="sxs-lookup"><span data-stu-id="c9c4d-102">Side-by-Side Version Support on PowerShell 5.0 or newer</span></span>

<span data-ttu-id="c9c4d-103">I cmdlet Install-Module, Update-Module e Publish-Module eseguiti in Windows PowerShell 5.0 o versione successiva supportano ora versioni del modulo side-by-side (SxS).</span><span class="sxs-lookup"><span data-stu-id="c9c4d-103">There is now side-by-side (SxS) module version support in Install-Module, Update-Module, and Publish-Module cmdlets that run in Windows PowerShell 5.0 or newer.</span></span>
<span data-ttu-id="c9c4d-104">È stato inoltre aggiunto il parametro -RequiredVersion al cmdlet Publish-Module per specificare la versione da pubblicare.</span><span class="sxs-lookup"><span data-stu-id="c9c4d-104">Also, we have added a -RequiredVersion parameter to the Publish-Module cmdlet to specify the version to be published.</span></span> <span data-ttu-id="c9c4d-105">Il parametro Path supporta ora il percorso di base del modulo con la cartella della versione.</span><span class="sxs-lookup"><span data-stu-id="c9c4d-105">The Path parameter now supports the module base path with the version folder.</span></span>

<span data-ttu-id="c9c4d-106">**Esempi di Install-Module:**</span><span class="sxs-lookup"><span data-stu-id="c9c4d-106">**Install-Module examples:**</span></span>
```powershell
Install-Module -Name PSScriptAnalyzer -RequiredVersion 1.1.0 -Repository PSGallery
Get-Module -ListAvailable -Name PSScriptAnalyzer | Format-List Name,Version,ModuleBase

Name : PSScriptAnalyzer
Version : 1.1.0
ModuleBase : C:\Program Files\WindowsPowerShell\Modules\PSScriptAnalyzer\1.1.0

Install-Module -Name PSScriptAnalyzer -RequiredVersion 1.1.1 -Repository PSGallery
Get-Module -ListAvailable -Name PSScriptAnalyzer | Format-List Name,Version,ModuleBase

Name       : PSScriptAnalyzer
Version    : 1.1.1
ModuleBase : C:\Program Files\WindowsPowerShell\Modules\PSScriptAnalyzer\1.1.1
Name       : PSScriptAnalyzer
Version    : 1.1.0
ModuleBase : C:\Program Files\WindowsPowerShell\Modules\PSScriptAnalyzer\1.1.0

Get-InstalledModule -Name PSScriptAnalyzer -AllVersions

Version    Name                                Type       Repository           Description
-------    ----                                ----       ----------           -----------
1.1.0      PSScriptAnalyzer                    Module     PSGallery            PSScriptAnalyzer provides script analysis...
1.1.1      PSScriptAnalyzer                    Module     PSGallery            PSScriptAnalyzer provides script analysis...
```
