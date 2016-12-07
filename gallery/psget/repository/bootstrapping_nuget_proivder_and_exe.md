---
description: 
manager: carolz
ms.topic: article
author: jpjofre
ms.prod: powershell
keywords: powershell,cmdlet,gallery
ms.date: 2016-10-14
contributor: manikb
title: bootstrapping_nuget_proivder_and_exe
ms.technology: powershell
ms.openlocfilehash: 3ba2289f83f2de5f7be7e4e0cced1988ee17b466
ms.sourcegitcommit: c732e3ee6d2e0e9cd8c40105d6fbfd4d207b730d
translationtype: HT
---
# <a name="bootstrap-both-nuget-provider-and-nugetexe-for-publish-operations-with-single-prompt-message-and-bootstrap-only-nuget-provider-for-non-publish-operations"></a>Avviare sia il provider NuGet che il file NuGet.exe per operazioni di pubblicazione con messaggio di richiesta singolo e avviare solo il provider NuGet per operazioni non di pubblicazione

Il file NuGet.exe è stato rimosso dalla versione più recente del provider NuGet. Per la pubblicazione di un modulo o uno script con PowerShellGet, è necessario il file NuGet.exe per creare un file con estensione nupkg ed effettuarne il push nel repository. Il provider NuGet è necessario per eseguire operazioni non di pubblicazione come ricerca, installazione, aggiornamento e salvataggio.
È stata aggiunta la logica per avviare sia il provider NuGet che il file NuGet.exe per operazioni di pubblicazione con messaggio di richiesta singolo e avviare solo il provider NuGet per operazioni non di pubblicazione.

## <a name="when-nuget-provider-is-not-available"></a>Se il provider NuGet non è disponibile

```powershell                                
PS C:\windows\system32> find-module -Repository dtlgalleryint -verbose -name contoso

NuGet provider is required to continue
PowerShellGet requires NuGet provider version '2.8.5.201' or newer to interact with NuGet-based repositories. The NuGet provider must be available in 'C:\Program Files\PackageManagement\ProviderAssemblies' or
'C:\Users\manikb\AppData\Local\PackageManagement\ProviderAssemblies'. You can also install the NuGet provider by running 'Install-PackageProvider -Name NuGet -MinimumVersion 2.8.5.201 -Force'. Do you want PowerShellGet to install and import the NuGet provider
now?
[Y] Yes  [N] No  [S] Suspend  [?] Help (default is "Y"): n
find-module : NuGet provider is required to interact with NuGet-based repositories. Please ensure that '2.8.5.201' or newer version of NuGet provider is installed.
At line:1 char:1
+ find-module -Repository dtlgalleryint -verbose -name contoso
+ ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
    + CategoryInfo          : InvalidOperation: (:) [Find-Module], InvalidOperationException
   + FullyQualifiedErrorId : CouldNotInstallNuGetProvider,Find-Module

PS C:\windows\system32> find-module -Repository dtlgalleryint -verbose -name contoso

NuGet provider is required to continue
PowerShellGet requires NuGet provider version '2.8.5.201' or newer to interact with NuGet-based repositories. The NuGet provider must be available in 'C:\Program Files\PackageManagement\ProviderAssemblies' or
'C:\Users\manikb\AppData\Local\PackageManagement\ProviderAssemblies'. You can also install the NuGet provider by running 'Install-PackageProvider -Name NuGet -MinimumVersion 2.8.5.201 -Force'. Do you want PowerShellGet to install and import the NuGet provider
now?
[Y] Yes  [N] No  [S] Suspend  [?] Help (default is "Y"): Y
VERBOSE: Installing NuGet provider.

Version    Name                                Type       Repository           Description
-------    ----                                ----       ----------           -----------
2.5        Contoso                             Module     dtlgalleryint        Contoso module
```

## <a name="when-nuget-provider-is-available-and-nugetexe-is-not-available-during-the-publish-operation"></a>Se il provider NuGet è disponibile e il file NuGet.exe non è disponibile durante l'operazione di pubblicazione

```powershell
PS C:\windows\system32> Publish-Module -Name Contoso -Repository LocalRepo -Verbose

NuGet.exe is required to continue
PowerShellGet requires NuGet.exe to publish an item to the NuGet-based repositories. NuGet.exe must be available under one of the paths specified in PATH environment variable value. Do you want PowerShellGet to install NuGet.exe now?
[Y] Yes  [N] No  [S] Suspend  [?] Help (default is "Y"): N
Publish-Module : NuGet.exe is required to interact with NuGet-based repositories. Please ensure that NuGet.exe is available under one of the paths specified in PATH environment variable value.
At line:1 char:1
+ Publish-Module -Name Contoso -Repository LocalRepo -Verbose
+ ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
    + CategoryInfo          : InvalidOperation: (:) [Publish-Module], InvalidOperationException
    + FullyQualifiedErrorId : CouldNotInstallNuGetExe,Publish-Module

PS C:\windows\system32> Publish-Module -Name Contoso -Repository LocalRepo -Verbose

NuGet.exe is required to continue
PowerShellGet requires NuGet.exe to publish an item to the NuGet-based repositories. NuGet.exe must be available under one of the paths specified in PATH environment variable value. Do you want PowerShellGet to install NuGet.exe now?
[Y] Yes  [N] No  [S] Suspend  [?] Help (default is "Y"): Y
VERBOSE: Installing NuGet.exe.
VERBOSE: Successfully published module 'Contoso' to the module publish location 'C:\LocalGallery'. Please allow few minutes for 'Contoso' to show up in the search results.
```
                   
## <a name="when-both-nuget-provider-and-nugetexe-are-not-available-during-the-publish-operation"></a>Se il provider NuGet e il file NuGet.exe non sono disponibili durante l'operazione di pubblicazione

```powershell
PS C:\windows\system32> Publish-Module -Name Contoso -Repository LocalRepo -Verbose

NuGet.exe and NuGet provider are required to continue
PowerShellGet requires NuGet.exe and NuGet provider version '2.8.5.201' or newer to interact with the NuGet-based repositories. Do you want PowerShellGet to install both NuGet.exe and NuGet provider now?
[Y] Yes  [N] No  [S] Suspend  [?] Help (default is "Y"): N
Publish-Module : PowerShellGet requires NuGet.exe and NuGet provider version '2.8.5.201' or newer to interact with the NuGet-based repositories. Please ensure that '2.8.5.201' or newer version of NuGet provider is installed and NuGet.exe is available under 
one of the paths specified in PATH environment variable value.
At line:1 char:1
+ Publish-Module -Name Contoso -Repository LocalRepo -Verbose
+ ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
    + CategoryInfo          : InvalidOperation: (:) [Publish-Module], InvalidOperationException
    + FullyQualifiedErrorId : CouldNotInstallNuGetBinaries,Publish-Module

PS C:\windows\system32> Publish-Module -Name Contoso -Repository LocalRepo -Verbose

NuGet.exe and NuGet provider are required to continue
PowerShellGet requires NuGet.exe and NuGet provider version '2.8.5.201' or newer to interact with the NuGet-based repositories. Do you want PowerShellGet to install both NuGet.exe and NuGet provider now?
[Y] Yes  [N] No  [S] Suspend  [?] Help (default is "Y"): Y
VERBOSE: Installing NuGet provider.
VERBOSE: Installing NuGet.exe.
VERBOSE: Successfully published module 'Contoso' to the module publish location 'C:\LocalGallery'. Please allow few minutes for 'Contoso' to show up in the search results.
```

