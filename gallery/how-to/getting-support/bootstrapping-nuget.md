---
ms.date: 06/12/2017
contributor: manikb
keywords: raccolta,powershell,cmdlet,psget
title: Bootstrap di NuGet
ms.openlocfilehash: 6d8f106bc3b8741203e87e4c097948a843f06d6e
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62084386"
---
# <a name="bootstrap-the-nuget-provider-and-nugetexe"></a>Bootstrap del provider NuGet e di NuGet.exe

Il file NuGet.exe non è incluso nella versione più recente del provider NuGet. Per le operazioni di pubblicazione di un modulo o uno script, PowerShellGet richiede il file NuGet.exe eseguibile binario. Per tutte le altre operazioni, che includono la *ricerca*,l' *installazione*, il *salvataggio* e la *disinstallazione*, è necessario soltanto il provider NuGet.
PowerShellGet include la logica per gestire un bootstrap combinato del provider NuGet e di NuGet.exe o un bootstrap del solo provider NuGet. In entrambi i casi deve essere visualizzato un solo messaggio di richiesta. Se il computer non è connesso a Internet, è necessario che l'utente o un amministratore copi un'istanza attendibile del provider NuGet e/o del file NuGet.exe nel computer disconnesso.

> [!NOTE]
> A partire dalla versione 6, il provider NuGet è incluso nell'installazione di PowerShell.

## <a name="resolving-error-when-the-nuget-provider-has-not-been-installed-on-a-machine-that-is-internet-connected"></a>Risoluzione dell'errore se il provider NuGet non è stato installato in un computer connesso a Internet

```powershell
Find-Module -Repository PSGallery -Verbose -Name Contoso
```

```output
NuGet provider is required to continue
PowerShellGet requires NuGet provider version '2.8.5.201' or newer to interact with NuGet-based repositories. The NuGet provider must be available in 'C:\Program Files\PackageManagement\ProviderAssemblies' or
'C:\Users\manikb\AppData\Local\PackageManagement\ProviderAssemblies'. You can also install the NuGet provider by running 'Install-PackageProvider -Name NuGet -MinimumVersion 2.8.5.201 -Force'. Do you want PowerShellGet to install and import the NuGet provider
now?
[Y] Yes  [N] No  [S] Suspend  [?] Help (default is "Y"): n
Find-Module : NuGet provider is required to interact with NuGet-based repositories. Please ensure that '2.8.5.201' or newer version of NuGet provider is installed.
At line:1 char:1
+ Find-Module -Repository PSGallery -Verbose -Name Contoso
+ ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
    + CategoryInfo          : InvalidOperation: (:) [Find-Module], InvalidOperationException
   + FullyQualifiedErrorId : CouldNotInstallNuGetProvider,Find-Module
```

```powershell
Find-Module -Repository PSGallery -Verbose -Name Contoso
```

```output
NuGet provider is required to continue
PowerShellGet requires NuGet provider version '2.8.5.201' or newer to interact with NuGet-based repositories. The NuGet provider must be available in 'C:\Program Files\PackageManagement\ProviderAssemblies' or
'C:\Users\manikb\AppData\Local\PackageManagement\ProviderAssemblies'. You can also install the NuGet provider by running 'Install-PackageProvider -Name NuGet -MinimumVersion 2.8.5.201 -Force'. Do you want PowerShellGet to install and import the NuGet provider
now?
[Y] Yes  [N] No  [S] Suspend  [?] Help (default is "Y"): Y
VERBOSE: Installing NuGet provider.

Version    Name                                Type       Repository           Description
-------    ----                                ----       ----------           -----------
2.5        Contoso                             Module     PSGallery        Contoso module
```

## <a name="resolving-error-when-the-nuget-provider-is-available-and-nugetexe-is-not-available-during-the-publish-operation-on-a-machine-that-is-internet-connected"></a>Risoluzione dell'errore se il provider NuGet è disponibile e NuGet.exe non è disponibile durante l'operazione di pubblicazione in un computer connesso a Internet

```powershell
Publish-Module -Name Contoso -Repository PSGallery -Verbose
```

```output
NuGet.exe is required to continue
PowerShellGet requires NuGet.exe to publish an item to the NuGet-based repositories. NuGet.exe must be available under one of the paths specified in PATH environment variable value. Do you want PowerShellGet to install NuGet.exe now?
[Y] Yes  [N] No  [S] Suspend  [?] Help (default is "Y"): N
Publish-Module : NuGet.exe is required to interact with NuGet-based repositories. Please ensure that NuGet.exe is available under one of the paths specified in PATH environment variable value.
At line:1 char:1
+ Publish-Module -Name Contoso -Repository PSGallery -Verbose
+ ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
    + CategoryInfo          : InvalidOperation: (:) [Publish-Module], InvalidOperationException
    + FullyQualifiedErrorId : CouldNotInstallNuGetExe,Publish-Module
```

```powershell
Publish-Module -Name Contoso -Repository PSGallery -Verbose
```

```output
NuGet.exe is required to continue
PowerShellGet requires NuGet.exe to publish an item to the NuGet-based repositories. NuGet.exe must be available under one of the paths specified in PATH environment variable value. Do you want PowerShellGet to install NuGet.exe now?
[Y] Yes  [N] No  [S] Suspend  [?] Help (default is "Y"): Y
VERBOSE: Installing NuGet.exe.
VERBOSE: Successfully published module 'Contoso' to the module publish location 'https://www.powershellgallery.com/api/v2/'. Please allow few minutes for 'Contoso' to show up in the search results.
```

## <a name="resolving-error-when-both-nuget-provider-and-nugetexe-are-not-available-during-the-publish-operation-on-a-machine-that-is-internet-connected"></a>Risoluzione dell'errore se il provider NuGet e NuGet.exe non sono disponibili durante l'operazione di pubblicazione in un computer connesso a Internet

```powershell
Publish-Module -Name Contoso -Repository PSGallery -Verbose
```

```output
NuGet.exe and NuGet provider are required to continue
PowerShellGet requires NuGet.exe and NuGet provider version '2.8.5.201' or newer to interact with the NuGet-based repositories. Do you want PowerShellGet to install both NuGet.exe and NuGet provider now?
[Y] Yes  [N] No  [S] Suspend  [?] Help (default is "Y"): N
Publish-Module : PowerShellGet requires NuGet.exe and NuGet provider version '2.8.5.201' or newer to interact with the NuGet-based repositories. Please ensure that '2.8.5.201' or newer version of NuGet provider is installed and NuGet.exe is available under
one of the paths specified in PATH environment variable value.
At line:1 char:1
+ Publish-Module -Name Contoso -Repository PSGallery -Verbose
+ ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
    + CategoryInfo          : InvalidOperation: (:) [Publish-Module], InvalidOperationException
    + FullyQualifiedErrorId : CouldNotInstallNuGetBinaries,Publish-Module
```

```powershell
Publish-Module -Name Contoso -Repository PSGallery -Verbose
```

```output
NuGet.exe and NuGet provider are required to continue
PowerShellGet requires NuGet.exe and NuGet provider version '2.8.5.201' or newer to interact with the NuGet-based repositories. Do you want PowerShellGet to install both NuGet.exe and NuGet provider now?
[Y] Yes  [N] No  [S] Suspend  [?] Help (default is "Y"): Y
VERBOSE: Installing NuGet provider.
VERBOSE: Installing NuGet.exe.
VERBOSE: Successfully published module 'Contoso' to the module publish location 'https://www.powershellgallery.com/api/v2/'. Please allow few minutes for 'Contoso' to show up in the search results.
```

## <a name="manually-bootstrapping-the-nuget-provider-on-a-machine-that-is-not-connected-to-the-internet"></a>Bootstrap manuale del provider NuGet in un computer non connesso a Internet

I processi illustrati in precedenza presuppongono che il computer sia connesso a Internet e in grado di scaricare file da un percorso pubblico. Se il download non è possibile, l'unica opzione consiste nell'eseguire il bootstrap di un computer usando i processi descritti in precedenza e nel copiare manualmente il provider nel nodo isolato tramite un processo attendibile offline. Il caso d'uso più comune per questo scenario è rappresentato da una raccolta privata disponibile per il supporto di un ambiente isolato.

Dopo aver completato il processo precedente per eseguire il bootstrap di un computer connesso a Internet, i file del provider saranno disponibili nel percorso seguente:

`C:\Program Files\PackageManagement\ProviderAssemblies\`

La struttura di cartelle e file del provider NuGet sarà la seguente (eventualmente con un numero di versione diverso):

```
NuGet
--2.8.5.208
----Microsoft.PackageManagement.NuGetProvider.dll
```

Copiare le cartelle e il file usando un processo attendibile nei computer offline.

## <a name="manually-bootstrapping-nugetexe-to-support-publish-operations-on-a-machine-that-is-not-connected-to-the-internet"></a>Bootstrap manuale di NuGet.exe per il supporto delle operazioni di pubblicazione in un computer non connesso a Internet

In aggiunta al processo per il bootstrap manuale del provider NuGet, se il computer verrà usato per pubblicare moduli o script in una raccolta privata usando il cmdlet `Publish-Module` o `Publish-Script`, sarà necessario il file eseguibile binario NuGet.exe.

Il caso d'uso più comune per questo scenario è rappresentato da una raccolta privata disponibile per il supporto di un ambiente isolato. Sono disponibili due opzioni per ottenere il file NuGet.exe.

La prima opzione consiste nell'eseguire il bootstrap di un computer connesso a Internet e nel copiare i file nei computer offline usando un processo attendibile. Dopo aver eseguito il bootstrap del computer connesso a Internet, il file binario NuGet.exe si troverà in una delle due cartelle seguenti:

Se i cmdlet `Publish-Module` o `Publish-Script` sono stati eseguiti con autorizzazioni elevate (come amministratore):

```powershell
$env:ProgramData\Microsoft\Windows\PowerShell\PowerShellGet
```

Se i cmdlet sono stati eseguiti come utente senza autorizzazioni elevate:

```powershell
$env:userprofile\AppData\Local\Microsoft\Windows\PowerShell\PowerShellGet\
```

La seconda opzione consiste nello scaricare NuGet.exe dal sito Web NuGet.Org: [https://dist.nuget.org/index.html](https://www.nuget.org/downloads) Quando si seleziona una versione di NugGet per i computer di produzione, assicurarsi che sia successiva alla versione 2.8.5.208 e identificare la versione con etichetta "recommended" (consigliata). Ricordarsi di sbloccare il file se è stato scaricato tramite un browser. Questa operazione può essere eseguita usando il cmdlet `Unblock-File`.

In entrambi i casi, è possibile copiare il file di NuGet.exe in qualsiasi percorso in `$env:path`, ma i percorsi standard sono:

Per rendere disponibile il file eseguibile in modo che tutti gli utenti possano usare i cmdlet `Publish-Module` e `Publish-Script`:

```powershell
$env:ProgramData\Microsoft\Windows\PowerShell\PowerShellGet
```

Per rendere disponibile il file eseguibile solo per un utente specifico, copiare il percorso all'interno del profilo dell'utente:

```powershell
$env:userprofile\AppData\Local\Microsoft\Windows\PowerShell\PowerShellGet\
```
