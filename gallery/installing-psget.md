---
ms.date: 06/12/2017
contributor: manikb
keywords: raccolta,powershell,cmdlet,psget
title: Installazione di PowerShellGet
ms.openlocfilehash: a0ef46a9ee4bbf668a58067256d098967bde48c5
ms.sourcegitcommit: 0a6b562a497860caadba754c75a83215315d37a1
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 09/19/2019
ms.locfileid: "71143604"
---
# <a name="installing-powershellget"></a>Installazione di PowerShellGet

## <a name="powershellget-is-an-in-box-module-in-the-following-releases"></a>PowerShellGet è un modulo incluso nelle seguenti versioni

- [Windows 10](https://www.microsoft.com/windows) o successive
- [Windows Server 2016](/windows-server/windows-server) o successive
- [Windows Management Framework (WMF) 5.0](https://www.microsoft.com/download/details.aspx?id=50395) o successive
- [PowerShell 6](https://github.com/PowerShell/PowerShell/releases)

## <a name="get-the-latest-version-from-powershell-gallery"></a>Ottenere la versione più recente da PowerShell Gallery

Prima di aggiornare **PowerShellGet** è sempre consigliabile installare il provider **NuGet** più recente. Eseguire il codice seguente in una sessione di PowerShell con privilegi elevati.

```powershell
Install-PackageProvider -Name NuGet -Force
Exit
```

### <a name="for-systems-with-powershell-50-or-newer-you-can-install-the-latest-powershellget"></a>Per i sistemi con PowerShell 5.0 (o versione successiva) è possibile installare la versione più recente di PowerShellGet

Per installare PowerShellGet in Windows 10, Windows Server 2016, nei sistemi con WMF 5.0 o 5.1 o nei sistemi con PowerShell 6, eseguire i comandi seguenti in una sessione di PowerShell con privilegi elevati.

```powershell
Install-Module -Name PowerShellGet -Force
Exit
```

Usare `Update-Module` per ottenere le versioni più recenti.

```powershell
Update-Module -Name PowerShellGet
Exit
```

### <a name="for-systems-running-powershell-3-or-powershell-4-that-have-installed-the-packagemanagement-preview"></a>Per i sistemi con PowerShell 3 o PowerShell 4 nei quali è installata l'anteprima di PackageManagement

1. Usare `Save-Module` in una sessione di PowerShell con privilegi elevati per salvare i moduli in una directory locale.

   ```powershell
   Save-Module -Name PowerShellGet -Path C:\LocalFolder
   Exit
   ```

1. Verificare che i moduli **PowerShellGet** e **PackageManagement** non siano caricati in altri processi.
1. Eliminare il contenuto delle cartelle: `$env:ProgramFiles\WindowsPowerShell\Modules\PowerShellGet\` e `$env:ProgramFiles\WindowsPowerShell\Modules\PackageManagement\`.
1. Riaprire la console di PowerShell con privilegi elevati ed eseguire i comandi seguenti.

   ```powershell
   Copy-Item "C:\LocalFolder\PowerShellGet\*" "$env:ProgramFiles\WindowsPowerShell\Modules\PowerShellGet\" -Recurse -Force
   Copy-Item "C:\LocalFolder\PackageManagement\*" "$env:ProgramFiles\WindowsPowerShell\Modules\PackageManagement\" -Recurse -Force
   ```
