---
ms.date: 2017-06-12
contributor: manikb
ms.topic: reference
keywords: gallery,powershell,cmdlet,psget
title: Ottenere il modulo PowerShellGet
ms.openlocfilehash: a5a323b17709e519ec57623a9dd7499e591bbed5
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 06/12/2017
---
<a id="get-powershellget-module" class="xliff"></a>
Ottenere il modulo PowerShellGet
========================

<a id="powershellget-is-an-in-box-module-in-the-following-releases" class="xliff"></a>
### PowerShellGet è un modulo incluso nelle seguenti versioni
- [Windows 10](https://www.microsoft.com/en-us/windows/get-windows-10) o successive
- [Windows Server 2016](https://technet.microsoft.com/en-us/windows-server-docs/get-started/windows-server-2016) o successive
- [Windows Management Framework (WMF) 5.0](https://www.microsoft.com/en-us/download/details.aspx?id=50395) o successive
- [PowerShell 6](https://github.com/PowerShell/PowerShell/releases)

<a id="get-powershellget-module-for-powershell-versions-30-and-40" class="xliff"></a>
### Ottenere il modulo PowerShellGet per PowerShell 3.0 e 4.0
- [MSI PackageManagement](http://go.microsoft.com/fwlink/?LinkID=746217&clcid=0x409) 

<a id="get-the-latest-version-from-powershell-gallery" class="xliff"></a>
### Ottenere la versione più recente da PowerShell Gallery

- Prima di aggiornare PowerShellGet è sempre consigliabile installare il provider Nuget più recente. A tale scopo eseguire il seguente codice in una sessione di PowerShell con privilegi elevati.
```powershell
Install-PackageProvider Nuget –Force
Exit
```

<a id="for-systems-with-powershell-50-or-newer-you-can-install-the-latest-powershellget" class="xliff"></a>
#### Per i sistemi con PowerShell 5.0 (o versione successiva) è possibile installare la versione più recente di PowerShellGet 
- Per eseguire questa operazione in Windows 10, Windows Server 2016, nei sistemi con WMF 5.0 o 5.1 o nei sistemi con PowerShell 6 eseguire i seguenti comandi in una sessione di PowerShell con privilegi elevati.
```powershell
Install-Module –Name PowerShellGet –Force
Exit
```

- Per ottenere le versioni più recenti usare Update-Module.
```powershell
Update-Module -Name PowerShellGet
Exit
```

<a id="for-systems-running-powershell-3-or-powershell-4-that-have-installed-the-packagemanagement-msihttpgomicrosoftcomfwlinklinkid746217clcid0x409" class="xliff"></a>
#### Per i sistemi con PowerShell 3 o PowerShell 4 nei quali è installato il [MSI PackageManagement](http://go.microsoft.com/fwlink/?LinkID=746217&clcid=0x409)

- Usare il seguente cmdlet PowerShellGet in una sessione di PowerShell con privilegi elevati per salvare i moduli in una directory locale.

```powershell
Save-Module PowerShellGet -Path C:\LocalFolder
Exit
```

- Verificare che i moduli PowerShellGet e PackageManagement non siano caricati in nessun altro processo.
- Eliminare il contenuto delle cartelle `$env:ProgramFiles\WindowsPowerShell\Modules\PowerShellGet\` e `$env:ProgramFiles\WindowsPowerShell\Modules\PackageManagement\`.
- Riaprire la console di PowerShell con privilegi elevati ed eseguire i comandi seguenti.

```powershell
Copy-Item "C:\LocalFolder\PowerShellGet\*" "$env:ProgramFiles\WindowsPowerShell\Modules\PowerShellGet\" -Recurse -Force
Copy-Item "C:\LocalFolder\PackageManagement\*" "$env:ProgramFiles\WindowsPowerShell\Modules\PackageManagement\" -Recurse -Force