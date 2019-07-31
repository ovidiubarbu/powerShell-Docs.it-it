---
ms.date: 06/12/2017
contributor: manikb
keywords: raccolta,powershell,cmdlet,psget
title: Installazione di PowerShellGet
ms.openlocfilehash: 2d3ba8c4d4d4c7ee023c7e6a948a29d8f47ea242
ms.sourcegitcommit: 8d47eb41445ffaf10fcd68874e397c9a1703d898
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 07/29/2019
ms.locfileid: "68601427"
---
# <a name="installing-powershellget"></a>Installazione di PowerShellGet

## <a name="powershellget-is-an-in-box-module-in-the-following-releases"></a>PowerShellGet è un modulo incluso nelle seguenti versioni

- [Windows 10](https://www.microsoft.com/windows) o successive
- [Windows Server 2016](/windows-server/windows-server) o successive
- [Windows Management Framework (WMF) 5.0](https://www.microsoft.com/download/details.aspx?id=50395) o successive
- [PowerShell 6](https://github.com/PowerShell/PowerShell/releases)

## <a name="get-powershellget-module-for-powershell-versions-30-and-40"></a>Ottenere il modulo PowerShellGet per PowerShell 3.0 e 4.0

- [MSI PackageManagement](https://www.microsoft.com/download/details.aspx?id=51451)

## <a name="get-the-latest-version-from-powershell-gallery"></a>Ottenere la versione più recente da PowerShell Gallery

- Prima di aggiornare PowerShellGet è sempre consigliabile installare il provider Nuget più recente. A tale scopo eseguire il seguente codice in una sessione di PowerShell con privilegi elevati.

  ```powershell
  Install-PackageProvider Nuget -Force
  Exit
  ```

### <a name="for-systems-with-powershell-50-or-newer-you-can-install-the-latest-powershellget"></a>Per i sistemi con PowerShell 5.0 (o versione successiva) è possibile installare la versione più recente di PowerShellGet

- Per eseguire questa operazione in Windows 10, Windows Server 2016, nei sistemi con WMF 5.0 o 5.1 o nei sistemi con PowerShell 6 eseguire i seguenti comandi in una sessione di PowerShell con privilegi elevati.

  ```powershell
  Install-Module -Name PowerShellGet -Force
  Exit
  ```

- Usare `Update-Module` per ottenere le versioni più recenti.

  ```powershell
  Update-Module -Name PowerShellGet
  Exit
  ```

### <a name="for-systems-running-powershell-3-or-powershell-4-that-have-installed-the-packagemanagement-msihttpswwwmicrosoftcomdownloaddetailsaspxid51451"></a>Per i sistemi con PowerShell 3 o PowerShell 4 nei quali è installato il [MSI PackageManagement](https://www.microsoft.com/download/details.aspx?id=51451)

- Usare il seguente cmdlet PowerShellGet in una sessione di PowerShell con privilegi elevati per salvare i moduli in una directory locale.

  ```powershell
  Save-Module PowerShellGet -Path C:\LocalFolder
  Exit
  ```

- Verificare che i moduli PowerShellGet e PackageManagement non siano caricati in altri processi.
- Eliminare il contenuto delle cartelle `$env:ProgramFiles\WindowsPowerShell\Modules\PowerShellGet\` e `$env:ProgramFiles\WindowsPowerShell\Modules\PackageManagement\`.
- Riaprire la console di PowerShell con privilegi elevati ed eseguire i comandi seguenti.

  ```powershell
  Copy-Item "C:\LocalFolder\PowerShellGet\*" "$env:ProgramFiles\WindowsPowerShell\Modules\PowerShellGet\" -Recurse -Force
  Copy-Item "C:\LocalFolder\PackageManagement\*" "$env:ProgramFiles\WindowsPowerShell\Modules\PackageManagement\" -Recurse -Force
  ```
