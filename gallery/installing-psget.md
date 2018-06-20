---
ms.date: 06/12/2017
contributor: manikb
keywords: raccolta,powershell,cmdlet,psget
title: Installazione di PowerShellGet
ms.openlocfilehash: 35be7d02ea856ea39218f05d32b43c60fa1bd53e
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/17/2018
ms.locfileid: "34219352"
---
# <a name="installing-powershellget"></a><span data-ttu-id="4c4ab-103">Installazione di PowerShellGet</span><span class="sxs-lookup"><span data-stu-id="4c4ab-103">Installing PowerShellGet</span></span>

## <a name="powershellget-is-an-in-box-module-in-the-following-releases"></a><span data-ttu-id="4c4ab-104">PowerShellGet è un modulo incluso nelle seguenti versioni</span><span class="sxs-lookup"><span data-stu-id="4c4ab-104">PowerShellGet is an in-box module in the following releases</span></span>

- <span data-ttu-id="4c4ab-105">[Windows 10](https://www.microsoft.com/windows/get-windows-10) o successive</span><span class="sxs-lookup"><span data-stu-id="4c4ab-105">[Windows 10](https://www.microsoft.com/windows/get-windows-10) or newer</span></span>
- <span data-ttu-id="4c4ab-106">[Windows Server 2016](https://technet.microsoft.com/windows-server-docs/get-started/windows-server-2016) o successive</span><span class="sxs-lookup"><span data-stu-id="4c4ab-106">[Windows Server 2016](https://technet.microsoft.com/windows-server-docs/get-started/windows-server-2016) or newer</span></span>
- <span data-ttu-id="4c4ab-107">[Windows Management Framework (WMF) 5.0](https://www.microsoft.com/download/details.aspx?id=50395) o successive</span><span class="sxs-lookup"><span data-stu-id="4c4ab-107">[Windows Management Framework (WMF) 5.0](https://www.microsoft.com/download/details.aspx?id=50395) or newer</span></span>
- [<span data-ttu-id="4c4ab-108">PowerShell 6</span><span class="sxs-lookup"><span data-stu-id="4c4ab-108">PowerShell 6</span></span>](https://github.com/PowerShell/PowerShell/releases)

## <a name="get-powershellget-module-for-powershell-versions-30-and-40"></a><span data-ttu-id="4c4ab-109">Ottenere il modulo PowerShellGet per PowerShell 3.0 e 4.0</span><span class="sxs-lookup"><span data-stu-id="4c4ab-109">Get PowerShellGet module for PowerShell versions 3.0 and 4.0</span></span>

- [<span data-ttu-id="4c4ab-110">MSI PackageManagement</span><span class="sxs-lookup"><span data-stu-id="4c4ab-110">PackageManagement MSI</span></span>](http://go.microsoft.com/fwlink/?LinkID=746217&clcid=0x409)

## <a name="get-the-latest-version-from-powershell-gallery"></a><span data-ttu-id="4c4ab-111">Ottenere la versione più recente da PowerShell Gallery</span><span class="sxs-lookup"><span data-stu-id="4c4ab-111">Get the latest version from PowerShell Gallery</span></span>

- <span data-ttu-id="4c4ab-112">Prima di aggiornare PowerShellGet è sempre consigliabile installare il provider Nuget più recente.</span><span class="sxs-lookup"><span data-stu-id="4c4ab-112">Before updating PowerShellGet, you should always install the latest Nuget provider.</span></span> <span data-ttu-id="4c4ab-113">A tale scopo eseguire il seguente codice in una sessione di PowerShell con privilegi elevati.</span><span class="sxs-lookup"><span data-stu-id="4c4ab-113">To do that, run the following in an elevated PowerShell session.</span></span>

```powershell
Install-PackageProvider Nuget –Force
Exit
```

### <a name="for-systems-with-powershell-50-or-newer-you-can-install-the-latest-powershellget"></a><span data-ttu-id="4c4ab-114">Per i sistemi con PowerShell 5.0 (o versione successiva) è possibile installare la versione più recente di PowerShellGet</span><span class="sxs-lookup"><span data-stu-id="4c4ab-114">For systems with PowerShell 5.0 (or newer) you can install the latest PowerShellGet</span></span>

- <span data-ttu-id="4c4ab-115">Per eseguire questa operazione in Windows 10, Windows Server 2016, nei sistemi con WMF 5.0 o 5.1 o nei sistemi con PowerShell 6 eseguire i seguenti comandi in una sessione di PowerShell con privilegi elevati.</span><span class="sxs-lookup"><span data-stu-id="4c4ab-115">To do this on Windows 10, Windows Server 2016, any system with WMF 5.0 or 5.1 installed, or any system with PowerShell 6, run the following commands from an elevated PowerShell session.</span></span>

```powershell
Install-Module –Name PowerShellGet –Force
Exit
```

- <span data-ttu-id="4c4ab-116">Per ottenere le versioni più recenti usare Update-Module.</span><span class="sxs-lookup"><span data-stu-id="4c4ab-116">Use Update-Module to get newer versions.</span></span>

```powershell
Update-Module -Name PowerShellGet
Exit
```

### <a name="for-systems-running-powershell-3-or-powershell-4-that-have-installed-the-packagemanagement-msihttpgomicrosoftcomfwlinklinkid746217clcid0x409"></a><span data-ttu-id="4c4ab-117">Per i sistemi con PowerShell 3 o PowerShell 4 nei quali è installato il [MSI PackageManagement](http://go.microsoft.com/fwlink/?LinkID=746217&clcid=0x409)</span><span class="sxs-lookup"><span data-stu-id="4c4ab-117">For systems running PowerShell 3 or PowerShell 4, that have installed the [PackageManagement MSI](http://go.microsoft.com/fwlink/?LinkID=746217&clcid=0x409)</span></span>

- <span data-ttu-id="4c4ab-118">Usare il seguente cmdlet PowerShellGet in una sessione di PowerShell con privilegi elevati per salvare i moduli in una directory locale.</span><span class="sxs-lookup"><span data-stu-id="4c4ab-118">Use below PowerShellGet cmdlet from an elevated PowerShell session to save the modules to a local directory</span></span>

```powershell
Save-Module PowerShellGet -Path C:\LocalFolder
Exit
```

- <span data-ttu-id="4c4ab-119">Verificare che i moduli PowerShellGet e PackageManagement non siano caricati in nessun altro processo.</span><span class="sxs-lookup"><span data-stu-id="4c4ab-119">Ensure that PowerShellGet and PackageManagment modules are not loaded in any other processes.</span></span>
- <span data-ttu-id="4c4ab-120">Eliminare il contenuto delle cartelle `$env:ProgramFiles\WindowsPowerShell\Modules\PowerShellGet\` e `$env:ProgramFiles\WindowsPowerShell\Modules\PackageManagement\`.</span><span class="sxs-lookup"><span data-stu-id="4c4ab-120">Delete contents of `$env:ProgramFiles\WindowsPowerShell\Modules\PowerShellGet\` and  `$env:ProgramFiles\WindowsPowerShell\Modules\PackageManagement\` folders.</span></span>
- <span data-ttu-id="4c4ab-121">Riaprire la console di PowerShell con privilegi elevati ed eseguire i comandi seguenti.</span><span class="sxs-lookup"><span data-stu-id="4c4ab-121">Re-open the PS Console with elevated permissions then run the following commands.</span></span>

```powershell
Copy-Item "C:\LocalFolder\PowerShellGet\*" "$env:ProgramFiles\WindowsPowerShell\Modules\PowerShellGet\" -Recurse -Force
Copy-Item "C:\LocalFolder\PackageManagement\*" "$env:ProgramFiles\WindowsPowerShell\Modules\PackageManagement\" -Recurse -Force
```