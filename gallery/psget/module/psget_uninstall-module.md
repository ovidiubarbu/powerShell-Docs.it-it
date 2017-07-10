---
ms.date: 2017-06-12
contributor: manikb
ms.topic: reference
keywords: raccolta,powershell,cmdlet,psget
title: Uninstall-Module
ms.openlocfilehash: 3c4d8faa63aba6b4434d42a19a219baf84122591
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 06/12/2017
---
<a id="uninstall-module" class="xliff"></a>
# Uninstall-Module

Disinstalla un modulo installato con i cmdlet PowerShellGet.

<a id="description" class="xliff"></a>
## Descrizione

Il cmdlet Uninstall-Module consente di disinstallare il modulo specificato dal computer locale. Non è possibile disinstallare un modulo se altri moduli dipendono da esso.
I cmdlet Uninstall-Module verificano anche se il modulo che si sta disinstallando è in uso o meno. Se il modulo è in uso viene generato un errore.

<a id="cmdlet-syntax" class="xliff"></a>
## Sintassi del cmdlet
```powershell
Get-Command -Name Uninstall-Module -Module PowerShellGet -Syntax
```

<a id="cmdlet-online-help-reference" class="xliff"></a>
## Riferimento per la Guida online sui cmdlet

[Uninstall-Module](http://go.microsoft.com/fwlink/?LinkId=526864)


<a id="example-commands" class="xliff"></a>
## Comandi di esempio

<a id="run-the-uninstall-module-cmdlet-to-uninstall-a-module-that-you-installed-by-using-powershellget" class="xliff"></a>
###  Eseguire il cmdlet Uninstall-Module per disinstallare un modulo installato con PowerShellGet.
Se qualsiasi altro modulo dipende dal modulo che vuoi eliminare, PowerShellGet genera un errore.
```powershell
Get-InstalledModule -Name RequiredModule1 | Uninstall-Module

PackageManagement\Uninstall-Package : The module 'RequiredModule1' of version '2.5' in module base folder 'C:\Program Files\WindowsPowerShell\Modules\RequiredModule1\2.5' cannot be uninstalled, because one or more other modules 'ModuleWithDependencies2' are dependent on this module. Uninstall the modules that depend on this module before uninstalling module 'RequiredModule1'.
At C:\Program Files\WindowsPowerShell\Modules\PowerShellGet\PSGet.psm1:1303 char:25
+ ... $null = PackageManagement\\Uninstall-Package @PSBoundParameters
+ ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
+ CategoryInfo : InvalidOperation: (Microsoft.Power...ninstallPackage:UninstallPackage) [Uninstall-Package], Exception
+ FullyQualifiedErrorId : UnableToUninstallAsOtherModulesNeedThisModule,Uninstall-Package,Microsoft.PowerShell.PackageManagement.Cmdlets.UninstallPackage
```

<a id="uninstalling-a-module-when-some-other-modules-have-a-dependency-on-it" class="xliff"></a>
### Disinstallazione di un modulo da cui dipendono altri moduli.

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

<a id="you-can-override-this-by-specify--force-option-on-uninstall-module-cmdlet" class="xliff"></a>
### Per eseguire l'override di questo comportamento, specificare l'opzione -Force nel cmdlet Uninstall-Module
**NOTA:** non è una procedura consigliata. Con questa azione verranno interrotti altri moduli.

```powershell
Uninstall-Module SnippetPx -Force
```

<a id="uninstall-a-module-which-is-already-in-use" class="xliff"></a>
### Disinstallare un modulo già in uso

```powershell
Get-InstalledModule TypePx,SnippetPx

Version    Name                                Repository           Description
-------    ----                                ----------           -----------
2.0.1.20   TypePx                              PSGallery            The TypePx module adds properties and methods to...
1.0.5.18   SnippetPx                           PSGallery            The SnippetPx module enhances the snippet experi...
```

<a id="uninstall-snippetpx-fails-due-to-the-dependent-module" class="xliff"></a>
### La disinstallazione di SnippetPx non riesce a causa del modulo dipendente

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

<a id="uninstall-typepx-then-uninstall-the-snippetpx" class="xliff"></a>
### Disinstallare TypePx, quindi SnippetPx

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


<a id="for-a-module-name-which-is-not-installed-using-powershellget-cmdlets" class="xliff"></a>
### Per un nome del modulo non installato con i cmdlet PowerShellGet

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

