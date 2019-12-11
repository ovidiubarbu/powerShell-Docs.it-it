---
ms.date: 09/19/2019
contributor: manikb
keywords: raccolta,powershell,cmdlet,psget
title: Installazione di PowerShellGet
ms.openlocfilehash: 69dc851c54089b47fb19e5b32990d579d26effb9
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 12/05/2019
ms.locfileid: "71328202"
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

### <a name="for-computers-running-powershell-30-or-powershell-40"></a>Per i computer che eseguono PowerShell 3.0 o PowerShell 4.0

Queste istruzioni si applicano ai computer in cui è installata l'**anteprima di PackageManagement** oppure in cui non è installata alcuna versione di **PowerShellGet**.

Il cmdlet `Save-Module` viene usato in entrambi i set di istruzioni. `Save-Module` scarica e salva un modulo e le eventuali dipendenze da un repository registrato. La versione più recente del modulo viene salvata in un percorso specificato nel computer locale, ma non viene installata. Per altre informazioni, vedere [Save-Module](/powershell/module/PowershellGet/Save-Module).

#### <a name="computers-with-the-packagemanagement-preview-installed"></a>Computer con l'anteprima di PackageManagement installata

1. Usare `Save-Module` in una sessione di PowerShell per salvare i moduli in una directory locale.

   ```powershell
   Save-Module -Name PowerShellGet -Path C:\LocalFolder -Repository PSGallery
   ```

1. Verificare che i moduli **PowerShellGet** e **PackageManagement** non siano caricati in altri processi.
1. Eliminare il contenuto delle cartelle: `$env:ProgramFiles\WindowsPowerShell\Modules\PowerShellGet\` e `$env:ProgramFiles\WindowsPowerShell\Modules\PackageManagement\`.
1. Riaprire la console di PowerShell con privilegi elevati ed eseguire i comandi seguenti.

   ```powershell
   Copy-Item "C:\LocalFolder\PowerShellGet\*" "$env:ProgramFiles\WindowsPowerShell\Modules\PowerShellGet\" -Recurse -Force
   Copy-Item "C:\LocalFolder\PackageManagement\*" "$env:ProgramFiles\WindowsPowerShell\Modules\PackageManagement\" -Recurse -Force
   ```

#### <a name="computers-without-powershellget"></a>Computer senza PowerShellGet

Per i computer senza una versione di **PowerShellGet** installata, per scaricare i moduli è necessario un computer con **PowerShellGet** installato.

1. Dal computer in cui è installato **PowerShellGet** usare `Save-Module` per scaricare la versione corrente di **PowerShellGet**. Vengono scaricate due cartelle: **PowerShellGet** e **PackageManagement**. Ogni cartella contiene una sottocartella con un numero di versione.

   ```powershell
   Save-Module -Name PowerShellGet -Path C:\LocalFolder -Repository PSGallery
   ```

1. Copiare le cartelle **PowerShellGet** e **PackageManagement** nel computer in cui non è installato **PowerShellGet**.

   La directory di destinazione è: `$env:ProgramFiles\WindowsPowerShell\Modules`
