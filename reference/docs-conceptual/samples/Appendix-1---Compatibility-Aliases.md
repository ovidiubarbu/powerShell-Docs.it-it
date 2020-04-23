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
# <a name="appendix-1---compatibility-aliases"></a><span data-ttu-id="8711b-103">Appendice 1 - Alias per la compatibilità</span><span class="sxs-lookup"><span data-stu-id="8711b-103">Appendix 1 - Compatibility Aliases</span></span>

<span data-ttu-id="8711b-104">PowerShell include diversi alias che consentono agli utenti di **UNIX** e **cmd.exe** di usare comandi con cui hanno dimestichezza.</span><span class="sxs-lookup"><span data-stu-id="8711b-104">PowerShell has several aliases that allow **UNIX** and **cmd.exe** users to use familiar commands.</span></span>
<span data-ttu-id="8711b-105">I comandi sono riportati nella tabella seguente con i relativi cmdlet e alias di PowerShell:</span><span class="sxs-lookup"><span data-stu-id="8711b-105">The commands and their related PowerShell cmdlet and PowerShell alias are shown in the following table:</span></span>

|<span data-ttu-id="8711b-106">Comando cmd.exe</span><span class="sxs-lookup"><span data-stu-id="8711b-106">cmd.exe command</span></span>|<span data-ttu-id="8711b-107">Comando UNIX</span><span class="sxs-lookup"><span data-stu-id="8711b-107">UNIX command</span></span>|<span data-ttu-id="8711b-108">Cmdlet di PowerShell</span><span class="sxs-lookup"><span data-stu-id="8711b-108">PowerShell cmdlet</span></span>|<span data-ttu-id="8711b-109">Alias di PowerShell</span><span class="sxs-lookup"><span data-stu-id="8711b-109">PowerShell alias</span></span>|
|---------------|----------------|--------------|------------|
|<span data-ttu-id="8711b-110">**cls**</span><span class="sxs-lookup"><span data-stu-id="8711b-110">**cls**</span></span>|<span data-ttu-id="8711b-111">**deselezionare**</span><span class="sxs-lookup"><span data-stu-id="8711b-111">**clear**</span></span>|<span data-ttu-id="8711b-112">`Clear-Host` (funzione)</span><span class="sxs-lookup"><span data-stu-id="8711b-112">`Clear-Host` (function)</span></span>|`cls`|
|<span data-ttu-id="8711b-113">**copy**</span><span class="sxs-lookup"><span data-stu-id="8711b-113">**copy**</span></span>|<span data-ttu-id="8711b-114">**cp**</span><span class="sxs-lookup"><span data-stu-id="8711b-114">**cp**</span></span>|`Copy-Item`|`cpi`|
|<span data-ttu-id="8711b-115">**dir**</span><span class="sxs-lookup"><span data-stu-id="8711b-115">**dir**</span></span>|<span data-ttu-id="8711b-116">**ls**</span><span class="sxs-lookup"><span data-stu-id="8711b-116">**ls**</span></span>|`Get-ChildItem`|`gci`|
|<span data-ttu-id="8711b-117">**type**</span><span class="sxs-lookup"><span data-stu-id="8711b-117">**type**</span></span>|<span data-ttu-id="8711b-118">**cat**</span><span class="sxs-lookup"><span data-stu-id="8711b-118">**cat**</span></span>|`Get-Content`|`gc`|
|<span data-ttu-id="8711b-119">**move**</span><span class="sxs-lookup"><span data-stu-id="8711b-119">**move**</span></span>|<span data-ttu-id="8711b-120">**mv**</span><span class="sxs-lookup"><span data-stu-id="8711b-120">**mv**</span></span>|`Move-Item`|`mi`|
|<span data-ttu-id="8711b-121">**md**</span><span class="sxs-lookup"><span data-stu-id="8711b-121">**md**</span></span>|<span data-ttu-id="8711b-122">**mkdir**</span><span class="sxs-lookup"><span data-stu-id="8711b-122">**mkdir**</span></span>|`New-Item`|`ni`|
|<span data-ttu-id="8711b-123">**pushd**</span><span class="sxs-lookup"><span data-stu-id="8711b-123">**pushd**</span></span>|<span data-ttu-id="8711b-124">**pushd**</span><span class="sxs-lookup"><span data-stu-id="8711b-124">**pushd**</span></span>|`Push-Location`|`pushd`|
|<span data-ttu-id="8711b-125">**popd**</span><span class="sxs-lookup"><span data-stu-id="8711b-125">**popd**</span></span>|<span data-ttu-id="8711b-126">**popd**</span><span class="sxs-lookup"><span data-stu-id="8711b-126">**popd**</span></span>|`Pop-Location`|`popd`|
|<span data-ttu-id="8711b-127">**del**, **erase**, **rd**, **rmdir**</span><span class="sxs-lookup"><span data-stu-id="8711b-127">**del**, **erase**, **rd**, **rmdir**</span></span>|<span data-ttu-id="8711b-128">**rm**</span><span class="sxs-lookup"><span data-stu-id="8711b-128">**rm**</span></span>|`Remove-Item`|`ri`|
|<span data-ttu-id="8711b-129">**ren**</span><span class="sxs-lookup"><span data-stu-id="8711b-129">**ren**</span></span>|<span data-ttu-id="8711b-130">**mv**</span><span class="sxs-lookup"><span data-stu-id="8711b-130">**mv**</span></span>|`Rename-Item`|`rni`|
|<span data-ttu-id="8711b-131">**cd**, **chdir**</span><span class="sxs-lookup"><span data-stu-id="8711b-131">**cd**, **chdir**</span></span>|<span data-ttu-id="8711b-132">**cd**</span><span class="sxs-lookup"><span data-stu-id="8711b-132">**cd**</span></span>|`Set-Location`|`sl`|

<span data-ttu-id="8711b-133">Per trovare gli alias di PowerShell, usare il cmdlet [Get-Alias](/powershell/module/Microsoft.PowerShell.Utility/Get-Alias).</span><span class="sxs-lookup"><span data-stu-id="8711b-133">To find the PowerShell aliases, use the [Get-Alias](/powershell/module/Microsoft.PowerShell.Utility/Get-Alias) cmdlet.</span></span> <span data-ttu-id="8711b-134">Per visualizzare gli alias di un cmdlet, usare il parametro **Definition** e specificare il nome del cmdlet.</span><span class="sxs-lookup"><span data-stu-id="8711b-134">To display a cmdlet's aliases, use the **Definition** parameter and specify the cmdlet name.</span></span>
<span data-ttu-id="8711b-135">Oppure, per trovare il nome del cmdlet di un alias, usare il parametro **Name** e specificare l'alias.</span><span class="sxs-lookup"><span data-stu-id="8711b-135">Or, to find an alias's cmdlet name, use the **Name** parameter and specify the alias.</span></span>

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
