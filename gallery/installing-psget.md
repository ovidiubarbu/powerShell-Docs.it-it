---
ms.date: 06/12/2017
contributor: manikb
keywords: raccolta,powershell,cmdlet,psget
title: Installazione di PowerShellGet
ms.openlocfilehash: c385f7fbf6b688a11face9c3ebf4e6475a7b4c33
ms.sourcegitcommit: 8b076ebde7ef971d7465bab834a3c2a32471ef6f
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 07/06/2018
ms.locfileid: "37893961"
---
# <a name="installing-powershellget"></a><span data-ttu-id="b1ce5-103">Installazione di PowerShellGet</span><span class="sxs-lookup"><span data-stu-id="b1ce5-103">Installing PowerShellGet</span></span>

## <a name="powershellget-is-an-in-box-module-in-the-following-releases"></a><span data-ttu-id="b1ce5-104">PowerShellGet è un modulo incluso nelle seguenti versioni</span><span class="sxs-lookup"><span data-stu-id="b1ce5-104">PowerShellGet is an in-box module in the following releases</span></span>

- <span data-ttu-id="b1ce5-105">[Windows 10](https://www.microsoft.com/en-us/windows) o successive</span><span class="sxs-lookup"><span data-stu-id="b1ce5-105">[Windows 10](https://www.microsoft.com/en-us/windows) or newer</span></span>
- <span data-ttu-id="b1ce5-106">[Windows Server 2016](/windows-server/windows-server) o successive</span><span class="sxs-lookup"><span data-stu-id="b1ce5-106">[Windows Server 2016](/windows-server/windows-server) or newer</span></span>
- <span data-ttu-id="b1ce5-107">[Windows Management Framework (WMF) 5.0](https://www.microsoft.com/en-us/download/details.aspx?id=50395) o successive</span><span class="sxs-lookup"><span data-stu-id="b1ce5-107">[Windows Management Framework (WMF) 5.0](https://www.microsoft.com/en-us/download/details.aspx?id=50395) or newer</span></span>
- [<span data-ttu-id="b1ce5-108">PowerShell 6</span><span class="sxs-lookup"><span data-stu-id="b1ce5-108">PowerShell 6</span></span>](https://github.com/PowerShell/PowerShell/releases)

## <a name="get-powershellget-module-for-powershell-versions-30-and-40"></a><span data-ttu-id="b1ce5-109">Ottenere il modulo PowerShellGet per PowerShell 3.0 e 4.0</span><span class="sxs-lookup"><span data-stu-id="b1ce5-109">Get PowerShellGet module for PowerShell versions 3.0 and 4.0</span></span>

- [<span data-ttu-id="b1ce5-110">MSI PackageManagement</span><span class="sxs-lookup"><span data-stu-id="b1ce5-110">PackageManagement MSI</span></span>](https://www.microsoft.com/en-us/download/details.aspx?id=51451)

## <a name="get-the-latest-version-from-powershell-gallery"></a><span data-ttu-id="b1ce5-111">Ottenere la versione più recente da PowerShell Gallery</span><span class="sxs-lookup"><span data-stu-id="b1ce5-111">Get the latest version from PowerShell Gallery</span></span>

- <span data-ttu-id="b1ce5-112">Prima di aggiornare PowerShellGet è sempre consigliabile installare il provider Nuget più recente.</span><span class="sxs-lookup"><span data-stu-id="b1ce5-112">Before updating PowerShellGet, you should always install the latest Nuget provider.</span></span> <span data-ttu-id="b1ce5-113">A tale scopo eseguire il seguente codice in una sessione di PowerShell con privilegi elevati.</span><span class="sxs-lookup"><span data-stu-id="b1ce5-113">To do that, run the following in an elevated PowerShell session.</span></span>

  ```powershell
  Install-PackageProvider Nuget –Force
  Exit
  ```

### <a name="for-systems-with-powershell-50-or-newer-you-can-install-the-latest-powershellget"></a><span data-ttu-id="b1ce5-114">Per i sistemi con PowerShell 5.0 (o versione successiva) è possibile installare la versione più recente di PowerShellGet</span><span class="sxs-lookup"><span data-stu-id="b1ce5-114">For systems with PowerShell 5.0 (or newer) you can install the latest PowerShellGet</span></span>

- <span data-ttu-id="b1ce5-115">Per eseguire questa operazione in Windows 10, Windows Server 2016, nei sistemi con WMF 5.0 o 5.1 o nei sistemi con PowerShell 6 eseguire i seguenti comandi in una sessione di PowerShell con privilegi elevati.</span><span class="sxs-lookup"><span data-stu-id="b1ce5-115">To do this on Windows 10, Windows Server 2016, any system with WMF 5.0 or 5.1 installed, or any system with PowerShell 6, run the following commands from an elevated PowerShell session.</span></span>

  ```powershell
  Install-Module –Name PowerShellGet –Force
  Exit
  ```

- <span data-ttu-id="b1ce5-116">Usare `Update-Module` per ottenere le versioni più recenti.</span><span class="sxs-lookup"><span data-stu-id="b1ce5-116">Use `Update-Module` to get newer versions.</span></span>

  ```powershell
  Update-Module -Name PowerShellGet
  Exit
  ```

### <a name="for-systems-running-powershell-3-or-powershell-4-that-have-installed-the-packagemanagement-msihttpswwwmicrosoftcomen-usdownloaddetailsaspxid51451"></a><span data-ttu-id="b1ce5-117">Per i sistemi con PowerShell 3 o PowerShell 4 nei quali è installato il [MSI PackageManagement](https://www.microsoft.com/en-us/download/details.aspx?id=51451)</span><span class="sxs-lookup"><span data-stu-id="b1ce5-117">For systems running PowerShell 3 or PowerShell 4, that have installed the [PackageManagement MSI](https://www.microsoft.com/en-us/download/details.aspx?id=51451)</span></span>

- <span data-ttu-id="b1ce5-118">Usare il seguente cmdlet PowerShellGet in una sessione di PowerShell con privilegi elevati per salvare i moduli in una directory locale.</span><span class="sxs-lookup"><span data-stu-id="b1ce5-118">Use below PowerShellGet cmdlet from an elevated PowerShell session to save the modules to a local directory</span></span>

  ```powershell
  Save-Module PowerShellGet -Path C:\LocalFolder
  Exit
  ```

- <span data-ttu-id="b1ce5-119">Verificare che i moduli PowerShellGet e PackageManagement non siano caricati in nessun altro processo.</span><span class="sxs-lookup"><span data-stu-id="b1ce5-119">Ensure that PowerShellGet and PackageManagment modules are not loaded in any other processes.</span></span>
- <span data-ttu-id="b1ce5-120">Eliminare il contenuto delle cartelle `$env:ProgramFiles\WindowsPowerShell\Modules\PowerShellGet\` e `$env:ProgramFiles\WindowsPowerShell\Modules\PackageManagement\`.</span><span class="sxs-lookup"><span data-stu-id="b1ce5-120">Delete contents of `$env:ProgramFiles\WindowsPowerShell\Modules\PowerShellGet\` and  `$env:ProgramFiles\WindowsPowerShell\Modules\PackageManagement\` folders.</span></span>
- <span data-ttu-id="b1ce5-121">Riaprire la console di PowerShell con privilegi elevati ed eseguire i comandi seguenti.</span><span class="sxs-lookup"><span data-stu-id="b1ce5-121">Re-open the PS Console with elevated permissions then run the following commands.</span></span>

  ```powershell
  Copy-Item "C:\LocalFolder\PowerShellGet\*" "$env:ProgramFiles\WindowsPowerShell\Modules\PowerShellGet\" -Recurse -Force
  Copy-Item "C:\LocalFolder\PackageManagement\*" "$env:ProgramFiles\WindowsPowerShell\Modules\PackageManagement\" -Recurse -Force
  ```