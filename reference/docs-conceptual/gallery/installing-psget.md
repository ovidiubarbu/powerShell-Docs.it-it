---
ms.date: 09/19/2019
contributor: manikb
keywords: raccolta,powershell,cmdlet,psget
title: Installazione di PowerShellGet
ms.openlocfilehash: 69dc851c54089b47fb19e5b32990d579d26effb9
ms.sourcegitcommit: 4a2cf30351620a58ba95ff5d76b247e601907589
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 09/27/2019
ms.locfileid: "71328202"
---
# <a name="installing-powershellget"></a><span data-ttu-id="f2564-103">Installazione di PowerShellGet</span><span class="sxs-lookup"><span data-stu-id="f2564-103">Installing PowerShellGet</span></span>

## <a name="powershellget-is-an-in-box-module-in-the-following-releases"></a><span data-ttu-id="f2564-104">PowerShellGet è un modulo incluso nelle seguenti versioni</span><span class="sxs-lookup"><span data-stu-id="f2564-104">PowerShellGet is an in-box module in the following releases</span></span>

- <span data-ttu-id="f2564-105">[Windows 10](https://www.microsoft.com/windows) o successive</span><span class="sxs-lookup"><span data-stu-id="f2564-105">[Windows 10](https://www.microsoft.com/windows) or newer</span></span>
- <span data-ttu-id="f2564-106">[Windows Server 2016](/windows-server/windows-server) o successive</span><span class="sxs-lookup"><span data-stu-id="f2564-106">[Windows Server 2016](/windows-server/windows-server) or newer</span></span>
- <span data-ttu-id="f2564-107">[Windows Management Framework (WMF) 5.0](https://www.microsoft.com/download/details.aspx?id=50395) o successive</span><span class="sxs-lookup"><span data-stu-id="f2564-107">[Windows Management Framework (WMF) 5.0](https://www.microsoft.com/download/details.aspx?id=50395) or newer</span></span>
- [<span data-ttu-id="f2564-108">PowerShell 6</span><span class="sxs-lookup"><span data-stu-id="f2564-108">PowerShell 6</span></span>](https://github.com/PowerShell/PowerShell/releases)

## <a name="get-the-latest-version-from-powershell-gallery"></a><span data-ttu-id="f2564-109">Ottenere la versione più recente da PowerShell Gallery</span><span class="sxs-lookup"><span data-stu-id="f2564-109">Get the latest version from PowerShell Gallery</span></span>

<span data-ttu-id="f2564-110">Prima di aggiornare **PowerShellGet** è sempre consigliabile installare il provider **NuGet** più recente.</span><span class="sxs-lookup"><span data-stu-id="f2564-110">Before updating **PowerShellGet**, you should always install the latest **NuGet** provider.</span></span> <span data-ttu-id="f2564-111">Eseguire il codice seguente in una sessione di PowerShell con privilegi elevati.</span><span class="sxs-lookup"><span data-stu-id="f2564-111">From an elevated PowerShell session, run the following command.</span></span>

```powershell
Install-PackageProvider -Name NuGet -Force
Exit
```

### <a name="for-systems-with-powershell-50-or-newer-you-can-install-the-latest-powershellget"></a><span data-ttu-id="f2564-112">Per i sistemi con PowerShell 5.0 (o versione successiva) è possibile installare la versione più recente di PowerShellGet</span><span class="sxs-lookup"><span data-stu-id="f2564-112">For systems with PowerShell 5.0 (or newer) you can install the latest PowerShellGet</span></span>

<span data-ttu-id="f2564-113">Per installare PowerShellGet in Windows 10, Windows Server 2016, nei sistemi con WMF 5.0 o 5.1 o nei sistemi con PowerShell 6, eseguire i comandi seguenti in una sessione di PowerShell con privilegi elevati.</span><span class="sxs-lookup"><span data-stu-id="f2564-113">To install PowerShellGet on Windows 10, Windows Server 2016, any system with WMF 5.0 or 5.1 installed, or any system with PowerShell 6, run the following commands from an elevated PowerShell session.</span></span>

```powershell
Install-Module -Name PowerShellGet -Force
Exit
```

<span data-ttu-id="f2564-114">Usare `Update-Module` per ottenere le versioni più recenti.</span><span class="sxs-lookup"><span data-stu-id="f2564-114">Use `Update-Module` to get newer versions.</span></span>

```powershell
Update-Module -Name PowerShellGet
Exit
```

### <a name="for-computers-running-powershell-30-or-powershell-40"></a><span data-ttu-id="f2564-115">Per i computer che eseguono PowerShell 3.0 o PowerShell 4.0</span><span class="sxs-lookup"><span data-stu-id="f2564-115">For computers running PowerShell 3.0 or PowerShell 4.0</span></span>

<span data-ttu-id="f2564-116">Queste istruzioni si applicano ai computer in cui è installata l'**anteprima di PackageManagement** oppure in cui non è installata alcuna versione di **PowerShellGet**.</span><span class="sxs-lookup"><span data-stu-id="f2564-116">These instructions apply to computers that have the **PackageManagement Preview** installed or don't have any version of **PowerShellGet** installed.</span></span>

<span data-ttu-id="f2564-117">Il cmdlet `Save-Module` viene usato in entrambi i set di istruzioni.</span><span class="sxs-lookup"><span data-stu-id="f2564-117">The `Save-Module` cmdlet is used in both sets of instructions.</span></span> <span data-ttu-id="f2564-118">`Save-Module` scarica e salva un modulo e le eventuali dipendenze da un repository registrato.</span><span class="sxs-lookup"><span data-stu-id="f2564-118">`Save-Module` downloads and saves a module and any dependencies from a registered repository.</span></span> <span data-ttu-id="f2564-119">La versione più recente del modulo viene salvata in un percorso specificato nel computer locale, ma non viene installata.</span><span class="sxs-lookup"><span data-stu-id="f2564-119">The module's most current version is saved to a specified path on the local computer, but isn't installed.</span></span> <span data-ttu-id="f2564-120">Per altre informazioni, vedere [Save-Module](/powershell/module/PowershellGet/Save-Module).</span><span class="sxs-lookup"><span data-stu-id="f2564-120">For more information, see [Save-Module](/powershell/module/PowershellGet/Save-Module).</span></span>

#### <a name="computers-with-the-packagemanagement-preview-installed"></a><span data-ttu-id="f2564-121">Computer con l'anteprima di PackageManagement installata</span><span class="sxs-lookup"><span data-stu-id="f2564-121">Computers with the PackageManagement Preview installed</span></span>

1. <span data-ttu-id="f2564-122">Usare `Save-Module` in una sessione di PowerShell per salvare i moduli in una directory locale.</span><span class="sxs-lookup"><span data-stu-id="f2564-122">From a PowerShell session, use `Save-Module` to save the modules to a local directory.</span></span>

   ```powershell
   Save-Module -Name PowerShellGet -Path C:\LocalFolder -Repository PSGallery
   ```

1. <span data-ttu-id="f2564-123">Verificare che i moduli **PowerShellGet** e **PackageManagement** non siano caricati in altri processi.</span><span class="sxs-lookup"><span data-stu-id="f2564-123">Ensure that the **PowerShellGet** and **PackageManagement** modules aren't loaded in any other processes.</span></span>
1. <span data-ttu-id="f2564-124">Eliminare il contenuto delle cartelle: `$env:ProgramFiles\WindowsPowerShell\Modules\PowerShellGet\` e `$env:ProgramFiles\WindowsPowerShell\Modules\PackageManagement\`.</span><span class="sxs-lookup"><span data-stu-id="f2564-124">Delete the contents of the folders: `$env:ProgramFiles\WindowsPowerShell\Modules\PowerShellGet\` and `$env:ProgramFiles\WindowsPowerShell\Modules\PackageManagement\`.</span></span>
1. <span data-ttu-id="f2564-125">Riaprire la console di PowerShell con privilegi elevati ed eseguire i comandi seguenti.</span><span class="sxs-lookup"><span data-stu-id="f2564-125">Reopen the PowerShell console with elevated permissions and run the following commands.</span></span>

   ```powershell
   Copy-Item "C:\LocalFolder\PowerShellGet\*" "$env:ProgramFiles\WindowsPowerShell\Modules\PowerShellGet\" -Recurse -Force
   Copy-Item "C:\LocalFolder\PackageManagement\*" "$env:ProgramFiles\WindowsPowerShell\Modules\PackageManagement\" -Recurse -Force
   ```

#### <a name="computers-without-powershellget"></a><span data-ttu-id="f2564-126">Computer senza PowerShellGet</span><span class="sxs-lookup"><span data-stu-id="f2564-126">Computers without PowerShellGet</span></span>

<span data-ttu-id="f2564-127">Per i computer senza una versione di **PowerShellGet** installata, per scaricare i moduli è necessario un computer con **PowerShellGet** installato.</span><span class="sxs-lookup"><span data-stu-id="f2564-127">For computer's without any version of **PowerShellGet** installed, a computer with **PowerShellGet** installed is needed to download the modules.</span></span>

1. <span data-ttu-id="f2564-128">Dal computer in cui è installato **PowerShellGet** usare `Save-Module` per scaricare la versione corrente di **PowerShellGet**.</span><span class="sxs-lookup"><span data-stu-id="f2564-128">From the computer that has **PowerShellGet** installed, use `Save-Module` to download the current version of **PowerShellGet**.</span></span> <span data-ttu-id="f2564-129">Vengono scaricate due cartelle: **PowerShellGet** e **PackageManagement**.</span><span class="sxs-lookup"><span data-stu-id="f2564-129">Two folders are downloaded: **PowerShellGet** and **PackageManagement**.</span></span> <span data-ttu-id="f2564-130">Ogni cartella contiene una sottocartella con un numero di versione.</span><span class="sxs-lookup"><span data-stu-id="f2564-130">Each folder contains a subfolder with a version number.</span></span>

   ```powershell
   Save-Module -Name PowerShellGet -Path C:\LocalFolder -Repository PSGallery
   ```

1. <span data-ttu-id="f2564-131">Copiare le cartelle **PowerShellGet** e **PackageManagement** nel computer in cui non è installato **PowerShellGet**.</span><span class="sxs-lookup"><span data-stu-id="f2564-131">Copy the **PowerShellGet** and **PackageManagement** folders to the computer that doesn't have **PowerShellGet** installed.</span></span>

   <span data-ttu-id="f2564-132">La directory di destinazione è: `$env:ProgramFiles\WindowsPowerShell\Modules`</span><span class="sxs-lookup"><span data-stu-id="f2564-132">The destination directory is: `$env:ProgramFiles\WindowsPowerShell\Modules`</span></span>
