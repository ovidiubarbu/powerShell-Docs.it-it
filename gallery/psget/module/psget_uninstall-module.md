---
ms.date: 06/12/2017
contributor: manikb
ms.topic: reference
keywords: raccolta,powershell,cmdlet,psget
title: Uninstall-Module
ms.openlocfilehash: 90f26e64a8a6bc95faf444b1d3ce82a8e3bbefc1
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/09/2018
---
# <a name="uninstall-module"></a><span data-ttu-id="8d845-103">Uninstall-Module</span><span class="sxs-lookup"><span data-stu-id="8d845-103">Uninstall-Module</span></span>

<span data-ttu-id="8d845-104">Disinstalla un modulo installato con i cmdlet PowerShellGet.</span><span class="sxs-lookup"><span data-stu-id="8d845-104">Uninstalls a module which was installed using PowerShellGet cmdlets.</span></span>

## <a name="description"></a><span data-ttu-id="8d845-105">Description</span><span class="sxs-lookup"><span data-stu-id="8d845-105">Description</span></span>

<span data-ttu-id="8d845-106">Il cmdlet Uninstall-Module consente di disinstallare il modulo specificato dal computer locale.</span><span class="sxs-lookup"><span data-stu-id="8d845-106">The Uninstall-Module cmdlet uninstalls the specified module from the local computer.</span></span>
<span data-ttu-id="8d845-107">Non è possibile disinstallare un modulo se altri moduli dipendono da esso.</span><span class="sxs-lookup"><span data-stu-id="8d845-107">You cannot uninstall a module if some other modules have a dependency on it.</span></span>
<span data-ttu-id="8d845-108">I cmdlet Uninstall-Module verificano anche se il modulo che si sta disinstallando è in uso o meno.</span><span class="sxs-lookup"><span data-stu-id="8d845-108">The Uninstall-Module cmdlets also validates if the module being uninstalled is in-use or not.</span></span> <span data-ttu-id="8d845-109">Se il modulo è in uso viene generato un errore.</span><span class="sxs-lookup"><span data-stu-id="8d845-109">An error will be thrown if the module is in use.</span></span>

## <a name="cmdlet-syntax"></a><span data-ttu-id="8d845-110">Sintassi del cmdlet</span><span class="sxs-lookup"><span data-stu-id="8d845-110">Cmdlet syntax</span></span>
```powershell
Get-Command -Name Uninstall-Module -Module PowerShellGet -Syntax
```

## <a name="cmdlet-online-help-reference"></a><span data-ttu-id="8d845-111">Riferimento per la Guida online sui cmdlet</span><span class="sxs-lookup"><span data-stu-id="8d845-111">Cmdlet online help reference</span></span>

[<span data-ttu-id="8d845-112">Uninstall-Module</span><span class="sxs-lookup"><span data-stu-id="8d845-112">Uninstall-Module</span></span>](http://go.microsoft.com/fwlink/?LinkId=526864)


## <a name="example-commands"></a><span data-ttu-id="8d845-113">Comandi di esempio</span><span class="sxs-lookup"><span data-stu-id="8d845-113">Example commands</span></span>

###  <a name="run-the-uninstall-module-cmdlet-to-uninstall-a-module-that-you-installed-by-using-powershellget"></a><span data-ttu-id="8d845-114">Eseguire il cmdlet Uninstall-Module per disinstallare un modulo installato con PowerShellGet.</span><span class="sxs-lookup"><span data-stu-id="8d845-114">Run the Uninstall-Module cmdlet to uninstall a module that you installed by using PowerShellGet.</span></span>
<span data-ttu-id="8d845-115">Se qualsiasi altro modulo dipende dal modulo che vuoi eliminare, PowerShellGet genera un errore.</span><span class="sxs-lookup"><span data-stu-id="8d845-115">If any other module depends on the module that you want to delete, PowerShellGet throws an error.</span></span>
```powershell
Get-InstalledModule -Name RequiredModule1 | Uninstall-Module

PackageManagement\Uninstall-Package : The module 'RequiredModule1' of version '2.5' in module base folder 'C:\Program Files\WindowsPowerShell\Modules\RequiredModule1\2.5' cannot be uninstalled, because one or more other modules 'ModuleWithDependencies2' are dependent on this module. Uninstall the modules that depend on this module before uninstalling module 'RequiredModule1'.
At C:\Program Files\WindowsPowerShell\Modules\PowerShellGet\PSGet.psm1:1303 char:25
+ ... $null = PackageManagement\\Uninstall-Package @PSBoundParameters
+ ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
+ CategoryInfo : InvalidOperation: (Microsoft.Power...ninstallPackage:UninstallPackage) [Uninstall-Package], Exception
+ FullyQualifiedErrorId : UnableToUninstallAsOtherModulesNeedThisModule,Uninstall-Package,Microsoft.PowerShell.PackageManagement.Cmdlets.UninstallPackage
```

### <a name="uninstalling-a-module-when-some-other-modules-have-a-dependency-on-it"></a><span data-ttu-id="8d845-116">Disinstallazione di un modulo da cui dipendono altri moduli.</span><span class="sxs-lookup"><span data-stu-id="8d845-116">Uninstalling a module when some other modules have a dependency on it.</span></span>

```powershell
Uninstall-Module SnippetPx

PackageManagement\Uninstall-Package : The module 'SnippetPx' of version '1.0.5.18' in module base folder 'C:\ProgramFiles\WindowsPowerShell\Modules\SnippetPx\1.0.5.18' cannot be uninstalled, because one or more other modules 'TypePx' are dependent on this module. Uninstall the modules that depend on this module before uninstalling module 'SnippetPx'.
At C:\Program Files\WindowsPowerShell\Modules\PowerShellGet\1.0.0.3\PSModule.psm1:1803 char:21
+ ...        $null = PackageManagement\Uninstall-Package @PSBoundParameters
+                    ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
    + CategoryInfo          : InvalidOperation: (Microsoft.Power...ninstallPackage:UninstallPackage) [Uninstall-Packag
   e], Exception
    + FullyQualifiedErrorId : UnableToUninstallAsOtherModulesNeedThisModule,Uninstall-Package,Microsoft.PowerShell.Pac
   kageManagement.Cmdlets.UninstallPackage
```

### <a name="you-can-override-this-by-specify--force-option-on-uninstall-module-cmdlet"></a><span data-ttu-id="8d845-117">Per eseguire l'override di questo comportamento, specificare l'opzione -Force nel cmdlet Uninstall-Module</span><span class="sxs-lookup"><span data-stu-id="8d845-117">You can override this by specify -Force option on Uninstall-Module cmdlet</span></span>
<span data-ttu-id="8d845-118">**NOTA:** non è una procedura consigliata.</span><span class="sxs-lookup"><span data-stu-id="8d845-118">**NOTE:** This is not a recommended practice.</span></span> <span data-ttu-id="8d845-119">Con questa azione verranno interrotti altri moduli.</span><span class="sxs-lookup"><span data-stu-id="8d845-119">Other modules will break with this action.</span></span>

```powershell
Uninstall-Module SnippetPx -Force
```

### <a name="uninstall-a-module-which-is-already-in-use"></a><span data-ttu-id="8d845-120">Disinstallare un modulo già in uso</span><span class="sxs-lookup"><span data-stu-id="8d845-120">Uninstall a module which is already in use</span></span>

```powershell
Get-InstalledModule TypePx,SnippetPx

Version    Name                                Repository           Description
-------    ----                                ----------           -----------
2.0.1.20   TypePx                              PSGallery            The TypePx module adds properties and methods to...
1.0.5.18   SnippetPx                           PSGallery            The SnippetPx module enhances the snippet experi...
```

### <a name="uninstall-snippetpx-fails-due-to-the-dependent-module"></a><span data-ttu-id="8d845-121">La disinstallazione di SnippetPx non riesce a causa del modulo dipendente</span><span class="sxs-lookup"><span data-stu-id="8d845-121">Uninstall SnippetPx fails due to the dependent module</span></span>

```powershell
Uninstall-Module SnippetPx

PackageManagement\Uninstall-Package : The module 'SnippetPx' of version '1.0.5.18' in module base folder 'C:\Program
Files\WindowsPowerShell\Modules\SnippetPx\1.0.5.18' cannot be uninstalled, because one or more other modules 'TypePx'
are dependent on this module. Uninstall the modules that depend on this module before uninstalling module 'SnippetPx'.
At C:\Program Files\WindowsPowerShell\Modules\PowerShellGet\1.0.0.1\PSModule.psm1:1914 char:21
+ ...        $null = PackageManagement\Uninstall-Package @PSBoundParameters
+                    ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
    + CategoryInfo          : InvalidOperation: (Microsoft.Power...ninstallPackage:UninstallPackage) [Uninstall-Packag
   e], Exception
    + FullyQualifiedErrorId : UnableToUninstallAsOtherModulesNeedThisModule,Uninstall-Package,Microsoft.PowerShell.Pac
   kageManagement.Cmdlets.UninstallPackage
```

### <a name="uninstall-typepx-then-uninstall-the-snippetpx"></a><span data-ttu-id="8d845-122">Disinstallare TypePx, quindi SnippetPx</span><span class="sxs-lookup"><span data-stu-id="8d845-122">Uninstall TypePx then uninstall the SnippetPx</span></span>

```powershell
Uninstall-Module TypePx
Uninstall-Module SnippetPx

WARNING: The version '1.0.5.18' of module 'SnippetPx' is currently in use. Retry the operation after closing the
applications.
PackageManagement\Uninstall-Package : Module 'SnippetPx' is in currently in use.
At C:\Program Files\WindowsPowerShell\Modules\PowerShellGet\1.0.0.1\PSModule.psm1:1914 char:21
+ ...        $null = PackageManagement\Uninstall-Package @PSBoundParameters
+                    ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
    + CategoryInfo          : InvalidOperation: (Microsoft.Power...ninstallPackage:UninstallPackage) [Uninstall-Packag
   e], Exception
    + FullyQualifiedErrorId : ModuleIsInUse,Uninstall-Package,Microsoft.PowerShell.PackageManagement.Cmdlets.Uninstall
   Package
```


### <a name="for-a-module-name-which-is-not-installed-using-powershellget-cmdlets"></a><span data-ttu-id="8d845-123">Per un nome del modulo non installato con i cmdlet PowerShellGet</span><span class="sxs-lookup"><span data-stu-id="8d845-123">For a module name which is not installed using PowerShellGet cmdlets</span></span>

```powershell
Uninstall-Module SnipptPx

PackageManagement\Uninstall-Package : No match was found for the specified search criteria and module names 'SnipptPx'.
At C:\Program Files\WindowsPowerShell\Modules\PowerShellGet\1.0.0.1\PSModule.psm1:1914 char:21
+ ...        $null = PackageManagement\Uninstall-Package @PSBoundParameters
+                    ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
    + CategoryInfo          : ObjectNotFound: (Microsoft.Power...ninstallPackage:UninstallPackage) [Uninstall-Package]
   , Exception
    + FullyQualifiedErrorId : NoMatchFound,Microsoft.PowerShell.PackageManagement.Cmdlets.UninstallPackage
```