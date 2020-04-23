---
ms.date: 09/09/2019
keywords: powershell,cmdlet
title: Appendice 1 Alias per la compatibilità
ms.openlocfilehash: 2351fdf23711fe1417f7e3fc3cca5b642d5a59fc
ms.sourcegitcommit: 6545c60578f7745be015111052fd7769f8289296
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/22/2020
ms.locfileid: "70848169"
---
# <a name="appendix-1---compatibility-aliases"></a>Appendice 1 - Alias per la compatibilità

PowerShell include diversi alias che consentono agli utenti di **UNIX** e **cmd.exe** di usare comandi con cui hanno dimestichezza.
I comandi sono riportati nella tabella seguente con i relativi cmdlet e alias di PowerShell:

|Comando cmd.exe|Comando UNIX|Cmdlet di PowerShell|Alias di PowerShell|
|---------------|----------------|--------------|------------|
|**cls**|**deselezionare**|`Clear-Host` (funzione)|`cls`|
|**copy**|**cp**|`Copy-Item`|`cpi`|
|**dir**|**ls**|`Get-ChildItem`|`gci`|
|**type**|**cat**|`Get-Content`|`gc`|
|**move**|**mv**|`Move-Item`|`mi`|
|**md**|**mkdir**|`New-Item`|`ni`|
|**pushd**|**pushd**|`Push-Location`|`pushd`|
|**popd**|**popd**|`Pop-Location`|`popd`|
|**del**, **erase**, **rd**, **rmdir**|**rm**|`Remove-Item`|`ri`|
|**ren**|**mv**|`Rename-Item`|`rni`|
|**cd**, **chdir**|**cd**|`Set-Location`|`sl`|

Per trovare gli alias di PowerShell, usare il cmdlet [Get-Alias](/powershell/module/Microsoft.PowerShell.Utility/Get-Alias). Per visualizzare gli alias di un cmdlet, usare il parametro **Definition** e specificare il nome del cmdlet.
Oppure, per trovare il nome del cmdlet di un alias, usare il parametro **Name** e specificare l'alias.

```powershell
Get-Alias -Definition Get-ChildItem
```

```Output
CommandType     Name
-----------     ----
Alias           dir -> Get-ChildItem
Alias           gci -> Get-ChildItem
Alias           ls -> Get-ChildItem
```

```powershell
Get-Alias -Name gci
```

```Output
CommandType     Name
-----------     ----
Alias           gci -> Get-ChildItem
```
