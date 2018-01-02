---
ms.date: 2017-06-12
contributor: manikb
ms.topic: reference
keywords: raccolta,powershell,cmdlet,psget
title: Update-Module
ms.openlocfilehash: 66535cd5b1f44e108c2bc47fa343c77c86bb21dc
ms.sourcegitcommit: 58371abe9db4b9a0e4e1eb82d39a9f9e187355f9
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 12/05/2017
---
# <a name="update-module"></a><span data-ttu-id="0a13f-103">Update-Module</span><span class="sxs-lookup"><span data-stu-id="0a13f-103">Update-Module</span></span>

<span data-ttu-id="0a13f-104">Scarica e installa la versione più recente dei moduli specificati da una raccolta online nel computer locale.</span><span class="sxs-lookup"><span data-stu-id="0a13f-104">Downloads and installs the newest version of specified modules from an online gallery to the local computer.</span></span>

## <a name="description"></a><span data-ttu-id="0a13f-105">Descrizione</span><span class="sxs-lookup"><span data-stu-id="0a13f-105">Description</span></span>

<span data-ttu-id="0a13f-106">Il cmdlet Update-Module consente di installare una versione più recente di un modulo di Windows PowerShell installato dalla raccolta online eseguendo Install-Module nel computer locale.</span><span class="sxs-lookup"><span data-stu-id="0a13f-106">The Update-Module cmdlet installs a newer version of a Windows PowerShell module that was installed from the online gallery by running Install-Module on the local computer.</span></span>

<span data-ttu-id="0a13f-107">Per impostazione predefinita, viene installata la versione più recente del modulo specificato nella raccolta online, a meno che non sia specificata una versione richiesta.</span><span class="sxs-lookup"><span data-stu-id="0a13f-107">By default, the newest version of the specified module available in online gallery is installed, unless you specify a required version.</span></span> <span data-ttu-id="0a13f-108">È possibile aggiornare un modulo esistente installato specificando il nome del modulo. Update-Module cerca $env:PSModulePath per il modulo da aggiornare.</span><span class="sxs-lookup"><span data-stu-id="0a13f-108">You can update an existing, installed module by specifying the name of the module; Update-Module searches $env:PSModulePath for the module that you want to update.</span></span>

<span data-ttu-id="0a13f-109">L'esecuzione di Update-Module senza il parametro Name aggiorna tutti i moduli che possono essere aggiornati nel computer locale.</span><span class="sxs-lookup"><span data-stu-id="0a13f-109">Running Update-Module without the Name parameter updates all modules that can be updated on the local computer.</span></span>

### <a name="notes"></a><span data-ttu-id="0a13f-110">Note</span><span class="sxs-lookup"><span data-stu-id="0a13f-110">Notes</span></span>

- <span data-ttu-id="0a13f-111">Questo cmdlet viene eseguito in Windows PowerShell 3.0 o versioni successive di Windows PowerShell, in Windows 7 o Windows 2008 R2 e nelle versioni successive di Windows.</span><span class="sxs-lookup"><span data-stu-id="0a13f-111">This cmdlet runs on Windows PowerShell 3.0 or later releases of Windows PowerShell, on Windows 7 or Windows 2008 R2 and later releases of Windows.</span></span>
- <span data-ttu-id="0a13f-112">Se il modulo specificato con il parametro Name non è stato installato con Install-Module, si verifica un errore.</span><span class="sxs-lookup"><span data-stu-id="0a13f-112">If the module that you specify with the Name parameter was not installed by using Install-Module, an error occurs.</span></span> <span data-ttu-id="0a13f-113">È possibile eseguire Update-Module solo nei moduli installati dalla raccolta online eseguendo Install-Module.</span><span class="sxs-lookup"><span data-stu-id="0a13f-113">You can only run Update-Module on modules that you installed from the online gallery by running Install-Module.</span></span>
- <span data-ttu-id="0a13f-114">Se Update-Module prova ad aggiornare i file binari in uso, restituisce un errore che identifica i processi che causano il problema e indica all'utente di rieseguire Update-Module dopo l'arresto dei processi.</span><span class="sxs-lookup"><span data-stu-id="0a13f-114">If Update-Module attempts to update binaries that are in use, Update-Module returns an error that identifies the problem processes, and informs the user to retry Update-Module after stopping the processes.</span></span>
- <span data-ttu-id="0a13f-115">In PowerShell 5.0 o versioni successive, quando Update-Module aggiorna un modulo, aggiunge la versione più recente o quella specificata del modulo, in modo che le versioni precedenti e più recenti siano visualizzate side-by-side nella stessa directory.</span><span class="sxs-lookup"><span data-stu-id="0a13f-115">On PowerShell 5.0 or newer versions, when Update-Module updates a module, it adds the latest (or specified) version of the module, so the older and newer versions are now side-by-side in the same directory.</span></span> <span data-ttu-id="0a13f-116">Sarebbe utile avere un esempio dell'output di questi comandi.</span><span class="sxs-lookup"><span data-stu-id="0a13f-116">It would be useful to say so and to show an example of the output from these commands.</span></span>


## <a name="cmdlet-syntax"></a><span data-ttu-id="0a13f-117">Sintassi del cmdlet</span><span class="sxs-lookup"><span data-stu-id="0a13f-117">Cmdlet syntax</span></span>
```powershell
Get-Command -Name Update-Module -Module PowerShellGet -Syntax
```

## <a name="cmdlet-online-help-reference"></a><span data-ttu-id="0a13f-118">Riferimento per la Guida online sui cmdlet</span><span class="sxs-lookup"><span data-stu-id="0a13f-118">Cmdlet online help reference</span></span>

[<span data-ttu-id="0a13f-119">Update-Module</span><span class="sxs-lookup"><span data-stu-id="0a13f-119">Update-Module</span></span>](http://go.microsoft.com/fwlink/?LinkID=398576)


## <a name="example-commands"></a><span data-ttu-id="0a13f-120">Comandi di esempio</span><span class="sxs-lookup"><span data-stu-id="0a13f-120">Example commands</span></span>

```powershell
PS C:\windows\system32> Update-Module -Name ContosoServer -RequiredVersion 1.5
PS C:\windows\system32> Get-Module -ListAvailable -Name ContosoServer | Format-List Name,Version,ModuleBase
Name : ContosoServer
Version : 2.0
ModuleBase : C:\Program Files\WindowsPowerShell\Modules\ContosoServer\2.0
Name : ContosoServer
Version : 1.5
ModuleBase : C:\Program Files\WindowsPowerShell\Modules\ContosoServer\1.5
Name : ContosoServer
Version : 1.0
ModuleBase : C:\Program Files\WindowsPowerShell\Modules\ContosoServer\1.0
PS C:\windows\system32> Get-InstalledModule
Version Name Repository Description
------- ---- ---------- -----------
1.0 ContosoServer MSPSGallery ContosoServer module
1.5 ContosoServer MSPSGallery ContosoServer module
2.0 ContosoServer MSPSGallery ContosoServer module
PS C:\windows\system32> Update-Module -Name ContosoServer
PS C:\windows\system32> Get-Module -ListAvailable -Name ContosoServer | Format-List Name,Version,ModuleBase
Name : ContosoServer
Version : 2.8.1
ModuleBase : C:\Program Files\WindowsPowerShell\Modules\ContosoServer\2.8.1
Name : ContosoServer
Version : 2.0
ModuleBase : C:\Program Files\WindowsPowerShell\Modules\ContosoServer\2.0
Name : ContosoServer
Version : 1.5
ModuleBase : C:\Program Files\WindowsPowerShell\Modules\ContosoServer\1.5
Name : ContosoServer
Version : 1.0
ModuleBase : C:\Program Files\WindowsPowerShell\Modules\ContosoServer\1.0
PS C:\windows\system32> Get-InstalledModule
Version Name Repository Description
------- ---- ---------- -----------
1.0 ContosoServer MSPSGallery ContosoServer module
1.5 ContosoServer MSPSGallery ContosoServer module
2.0 ContosoServer MSPSGallery ContosoServer module
2.8.1 ContosoServer MSPSGallery ContosoServer module
```

### <a name="update-the-module-with-a-prerelease-version-requires--allowprerelease-flag"></a><span data-ttu-id="0a13f-121">L'aggiornamento del modulo con una versione provvisoria richiede il flag AllowPrerelease</span><span class="sxs-lookup"><span data-stu-id="0a13f-121">Update the module with a prerelease version, requires -AllowPrerelease flag</span></span>
```powershell
PS C:\windows\system32> Get-InstalledModule
Version Name Repository Description
------- ---- ---------- -----------
1.0 ContosoServer MSPSGallery ContosoServer module
1.5 ContosoServer MSPSGallery ContosoServer module
2.0 ContosoServer MSPSGallery ContosoServer module
2.8.1 ContosoServer MSPSGallery ContosoServer module

PS C:\windows\system32> Find-Module ContosoServer -AllowPrerelease

Version        Name                                Repository           Description
-------        ----                                ----------           -----------
3.0.0-alpha    ConstosoServer                      MSPSGallery          The PowerShell Contoso Server deployment tools...

PS C:\windows\system32> Update-Module -Name ContosoServer -AllowPrerelease
PS C:\windows\system32> Get-InstalledModule
Version Name Repository Description
------- ---- ---------- -----------
1.0 ContosoServer MSPSGallery ContosoServer module
1.5 ContosoServer MSPSGallery ContosoServer module
2.0 ContosoServer MSPSGallery ContosoServer module
2.8.1 ContosoServer MSPSGallery ContosoServer module
3.0.0-alpha ContosoServer MSPSGallery ContosoServer module

```


### <a name="update-the-testdepwithnestedrequiredmodules1-module-with-dependencies"></a><span data-ttu-id="0a13f-122">Aggiornare il modulo TestDepWithNestedRequiredModules1 con le dipendenze.</span><span class="sxs-lookup"><span data-stu-id="0a13f-122">Update the TestDepWithNestedRequiredModules1 module with dependencies.</span></span>
```powershell
Find-Module -Name TestDepWithNestedRequiredModules1 -Repository LocalRepo -AllVersions

Version    Name                                Repository  Description
-------    ----                                ----------  -----------
1.0        TestDepWithNestedRequiredModules1   LocalRepo   TestDepWithNestedRequiredModules1 module
2.0        TestDepWithNestedRequiredModules1   LocalRepo   TestDepWithNestedRequiredModules1 module

Update-Module -Name TestDepWithNestedRequiredModules1 -RequiredVersion 2.0
Get-InstalledModule

Version    Name                                Repository  Description
-------    ----                                ----------  -----------
1.0        NestedRequiredModule1               LocalRepo   NestedRequiredModule1 module
2.5        NestedRequiredModule2               LocalRepo   NestedRequiredModule2 module
2.0        NestedRequiredModule3               LocalRepo   NestedRequiredModule3 module
2.5        NestedRequiredModule3               LocalRepo   NestedRequiredModule3 module
1.0        RequiredModule1                     LocalRepo   RequiredModule1 module
2.5        RequiredModule2                     LocalRepo   RequiredModule2 module
2.0        RequiredModule3                     LocalRepo   RequiredModule3 module
2.5        RequiredModule3                     LocalRepo   RequiredModule3 module
1.0        TestDepWithNestedRequiredModules1   LocalRepo   TestDepWithNestedRequiredModules1 module
2.0        TestDepWithNestedRequiredModules1   LocalRepo   TestDepWithNestedRequiredModules1 module



```

