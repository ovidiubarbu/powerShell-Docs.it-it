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
# <a name="installing-powershellget"></a><span data-ttu-id="5cb7b-103">Installazione di PowerShellGet</span><span class="sxs-lookup"><span data-stu-id="5cb7b-103">Installing PowerShellGet</span></span>

## <a name="powershellget-is-an-in-box-module-in-the-following-releases"></a><span data-ttu-id="5cb7b-104">PowerShellGet è un modulo incluso nelle seguenti versioni</span><span class="sxs-lookup"><span data-stu-id="5cb7b-104">PowerShellGet is an in-box module in the following releases</span></span>

- <span data-ttu-id="5cb7b-105">[Windows 10](https://www.microsoft.com/windows) o successive</span><span class="sxs-lookup"><span data-stu-id="5cb7b-105">[Windows 10](https://www.microsoft.com/windows) or newer</span></span>
- <span data-ttu-id="5cb7b-106">[Windows Server 2016](/windows-server/windows-server) o successive</span><span class="sxs-lookup"><span data-stu-id="5cb7b-106">[Windows Server 2016](/windows-server/windows-server) or newer</span></span>
- <span data-ttu-id="5cb7b-107">[Windows Management Framework (WMF) 5.0](https://www.microsoft.com/download/details.aspx?id=50395) o successive</span><span class="sxs-lookup"><span data-stu-id="5cb7b-107">[Windows Management Framework (WMF) 5.0](https://www.microsoft.com/download/details.aspx?id=50395) or newer</span></span>
- [<span data-ttu-id="5cb7b-108">PowerShell 6</span><span class="sxs-lookup"><span data-stu-id="5cb7b-108">PowerShell 6</span></span>](https://github.com/PowerShell/PowerShell/releases)

## <a name="get-the-latest-version-from-powershell-gallery"></a><span data-ttu-id="5cb7b-109">Ottenere la versione più recente da PowerShell Gallery</span><span class="sxs-lookup"><span data-stu-id="5cb7b-109">Get the latest version from PowerShell Gallery</span></span>

<span data-ttu-id="5cb7b-110">Prima di aggiornare **PowerShellGet** è sempre consigliabile installare il provider **NuGet** più recente.</span><span class="sxs-lookup"><span data-stu-id="5cb7b-110">Before updating **PowerShellGet**, you should always install the latest **NuGet** provider.</span></span> <span data-ttu-id="5cb7b-111">Eseguire il codice seguente in una sessione di PowerShell con privilegi elevati.</span><span class="sxs-lookup"><span data-stu-id="5cb7b-111">From an elevated PowerShell session, run the following command.</span></span>

```powershell
Install-PackageProvider -Name NuGet -Force
Exit
```

### <a name="for-systems-with-powershell-50-or-newer-you-can-install-the-latest-powershellget"></a><span data-ttu-id="5cb7b-112">Per i sistemi con PowerShell 5.0 (o versione successiva) è possibile installare la versione più recente di PowerShellGet</span><span class="sxs-lookup"><span data-stu-id="5cb7b-112">For systems with PowerShell 5.0 (or newer) you can install the latest PowerShellGet</span></span>

<span data-ttu-id="5cb7b-113">Per installare PowerShellGet in Windows 10, Windows Server 2016, nei sistemi con WMF 5.0 o 5.1 o nei sistemi con PowerShell 6, eseguire i comandi seguenti in una sessione di PowerShell con privilegi elevati.</span><span class="sxs-lookup"><span data-stu-id="5cb7b-113">To install PowerShellGet on Windows 10, Windows Server 2016, any system with WMF 5.0 or 5.1 installed, or any system with PowerShell 6, run the following commands from an elevated PowerShell session.</span></span>

```powershell
Install-Module -Name PowerShellGet -Force
Exit
```

<span data-ttu-id="5cb7b-114">Usare `Update-Module` per ottenere le versioni più recenti.</span><span class="sxs-lookup"><span data-stu-id="5cb7b-114">Use `Update-Module` to get newer versions.</span></span>

```powershell
Update-Module -Name PowerShellGet
Exit
```

### <a name="for-systems-running-powershell-3-or-powershell-4-that-have-installed-the-packagemanagement-preview"></a><span data-ttu-id="5cb7b-115">Per i sistemi con PowerShell 3 o PowerShell 4 nei quali è installata l'anteprima di PackageManagement</span><span class="sxs-lookup"><span data-stu-id="5cb7b-115">For systems running PowerShell 3 or PowerShell 4, that have installed the PackageManagement Preview</span></span>

1. <span data-ttu-id="5cb7b-116">Usare `Save-Module` in una sessione di PowerShell con privilegi elevati per salvare i moduli in una directory locale.</span><span class="sxs-lookup"><span data-stu-id="5cb7b-116">From an elevated PowerShell session, use `Save-Module` to save the modules to a local directory.</span></span>

   ```powershell
   Save-Module -Name PowerShellGet -Path C:\LocalFolder
   Exit
   ```

1. <span data-ttu-id="5cb7b-117">Verificare che i moduli **PowerShellGet** e **PackageManagement** non siano caricati in altri processi.</span><span class="sxs-lookup"><span data-stu-id="5cb7b-117">Ensure that the **PowerShellGet** and **PackageManagement** modules aren't loaded in any other processes.</span></span>
1. <span data-ttu-id="5cb7b-118">Eliminare il contenuto delle cartelle: `$env:ProgramFiles\WindowsPowerShell\Modules\PowerShellGet\` e `$env:ProgramFiles\WindowsPowerShell\Modules\PackageManagement\`.</span><span class="sxs-lookup"><span data-stu-id="5cb7b-118">Delete the contents of the folders: `$env:ProgramFiles\WindowsPowerShell\Modules\PowerShellGet\` and `$env:ProgramFiles\WindowsPowerShell\Modules\PackageManagement\`.</span></span>
1. <span data-ttu-id="5cb7b-119">Riaprire la console di PowerShell con privilegi elevati ed eseguire i comandi seguenti.</span><span class="sxs-lookup"><span data-stu-id="5cb7b-119">Reopen the PowerShell console with elevated permissions and run the following commands.</span></span>

   ```powershell
   Copy-Item "C:\LocalFolder\PowerShellGet\*" "$env:ProgramFiles\WindowsPowerShell\Modules\PowerShellGet\" -Recurse -Force
   Copy-Item "C:\LocalFolder\PackageManagement\*" "$env:ProgramFiles\WindowsPowerShell\Modules\PackageManagement\" -Recurse -Force
   ```
