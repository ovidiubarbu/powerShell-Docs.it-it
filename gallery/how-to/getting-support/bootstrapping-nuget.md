---
ms.date: 06/12/2017
contributor: manikb
keywords: raccolta,powershell,cmdlet,psget
title: Bootstrap di NuGet
ms.openlocfilehash: 2d321097fda201c0d8f843b2194a161eceabe4e1
ms.sourcegitcommit: 77f62a55cac8c13d69d51eef5fade18f71d66955
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 07/17/2018
ms.locfileid: "39094018"
---
# <a name="bootstrap-the-nuget-provider-and-nugetexe"></a><span data-ttu-id="6ee99-103">Bootstrap del provider NuGet e di NuGet.exe</span><span class="sxs-lookup"><span data-stu-id="6ee99-103">Bootstrap the NuGet provider and NuGet.exe</span></span>

<span data-ttu-id="6ee99-104">Il file NuGet.exe non è incluso nella versione più recente del provider NuGet.</span><span class="sxs-lookup"><span data-stu-id="6ee99-104">NuGet.exe is not included in the latest NuGet provider.</span></span>
<span data-ttu-id="6ee99-105">Per le operazioni di pubblicazione di un modulo o uno script, PowerShellGet richiede il file NuGet.exe eseguibile binario.</span><span class="sxs-lookup"><span data-stu-id="6ee99-105">For publish operations of either a module or script, PowerShellGet requires the binary executable NuGet.exe.</span></span>
<span data-ttu-id="6ee99-106">Per tutte le altre operazioni, che includono la *ricerca*,l' *installazione*, il *salvataggio* e la *disinstallazione*, è necessario soltanto il provider NuGet.</span><span class="sxs-lookup"><span data-stu-id="6ee99-106">Only the NuGet provider is required for all other operations, including *find*, *install*, *save*, and *uninstall*.</span></span>
<span data-ttu-id="6ee99-107">PowerShellGet include la logica per gestire un bootstrap combinato del provider NuGet e di NuGet.exe o un bootstrap del solo provider NuGet.</span><span class="sxs-lookup"><span data-stu-id="6ee99-107">PowerShellGet includes logic to handle either a combined bootstrap of the NuGet provider and NuGet.exe, or bootstrap of only the NuGet provider.</span></span>
<span data-ttu-id="6ee99-108">In entrambi i casi deve essere visualizzato un solo messaggio di richiesta.</span><span class="sxs-lookup"><span data-stu-id="6ee99-108">In either case, only a single prompt message should occur.</span></span>
<span data-ttu-id="6ee99-109">Se il computer non è connesso a Internet, è necessario che l'utente o un amministratore copi un'istanza attendibile del provider NuGet e/o del file NuGet.exe nel computer disconnesso.</span><span class="sxs-lookup"><span data-stu-id="6ee99-109">If the machine is not connected to the Internet, the user or an administrator must copy a trusted instance of the NuGet provider and/or the NuGet.exe file to the disconnected machine.</span></span>

> [!NOTE]
> <span data-ttu-id="6ee99-110">A partire dalla versione 6, il provider NuGet è incluso nell'installazione di PowerShell.</span><span class="sxs-lookup"><span data-stu-id="6ee99-110">Starting with version 6, the NuGet provider is included in the installation of PowerShell.</span></span> [http://github.com/powershell/powershell](http://github.com/powershell/powershell)

## <a name="resolving-error-when-the-nuget-provider-has-not-been-installed-on-a-machine-that-is-internet-connected"></a><span data-ttu-id="6ee99-111">Risoluzione dell'errore se il provider NuGet non è stato installato in un computer connesso a Internet</span><span class="sxs-lookup"><span data-stu-id="6ee99-111">Resolving error when the NuGet provider has not been installed on a machine that is Internet connected</span></span>

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

## <a name="resolving-error-when-the-nuget-provider-is-available-and-nugetexe-is-not-available-during-the-publish-operation-on-a-machine-that-is-internet-connected"></a><span data-ttu-id="6ee99-112">Risoluzione dell'errore se il provider NuGet è disponibile e NuGet.exe non è disponibile durante l'operazione di pubblicazione in un computer connesso a Internet</span><span class="sxs-lookup"><span data-stu-id="6ee99-112">Resolving error when the NuGet provider is available and NuGet.exe is not available during the publish operation on a machine that is Internet connected</span></span>

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

## <a name="resolving-error-when-both-nuget-provider-and-nugetexe-are-not-available-during-the-publish-operation-on-a-machine-that-is-internet-connected"></a><span data-ttu-id="6ee99-113">Risoluzione dell'errore se il provider NuGet e NuGet.exe non sono disponibili durante l'operazione di pubblicazione in un computer connesso a Internet</span><span class="sxs-lookup"><span data-stu-id="6ee99-113">Resolving error when both NuGet provider and NuGet.exe are not available during the publish operation on a machine that is Internet connected</span></span>

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

## <a name="manually-bootstrapping-the-nuget-provider-on-a-machine-that-is-not-connected-to-the-internet"></a><span data-ttu-id="6ee99-114">Bootstrap manuale del provider NuGet in un computer non connesso a Internet</span><span class="sxs-lookup"><span data-stu-id="6ee99-114">Manually bootstrapping the NuGet provider on a machine that is not connected to the Internet</span></span>

<span data-ttu-id="6ee99-115">I processi illustrati in precedenza presuppongono che il computer sia connesso a Internet e in grado di scaricare file da un percorso pubblico.</span><span class="sxs-lookup"><span data-stu-id="6ee99-115">The processes demonstrated above assume the machine is connected to the Internet and can download files from a public location.</span></span>
<span data-ttu-id="6ee99-116">Se il download non è possibile, l'unica opzione consiste nell'eseguire il bootstrap di un computer usando i processi descritti in precedenza e nel copiare manualmente il provider nel nodo isolato tramite un processo attendibile offline.</span><span class="sxs-lookup"><span data-stu-id="6ee99-116">If that is not possible, the only option is to bootstrap a machine using the processes given above, and manually copy the provider to the isolated node through an offline trusted process.</span></span>
<span data-ttu-id="6ee99-117">Il caso d'uso più comune per questo scenario è rappresentato da una raccolta privata disponibile per il supporto di un ambiente isolato.</span><span class="sxs-lookup"><span data-stu-id="6ee99-117">The most common use case for this scenario is when a private gallery is available to support an isolated environment.</span></span>

<span data-ttu-id="6ee99-118">Dopo aver completato il processo precedente per eseguire il bootstrap di un computer connesso a Internet, i file del provider saranno disponibili nel percorso seguente:</span><span class="sxs-lookup"><span data-stu-id="6ee99-118">After following the process above to bootstrap an Internet connected machine, you will find provider files in the location:</span></span>

```
C:\Program Files\PackageManagement\ProviderAssemblies\
```

<span data-ttu-id="6ee99-119">La struttura di cartelle e file del provider NuGet sarà la seguente (eventualmente con un numero di versione diverso):</span><span class="sxs-lookup"><span data-stu-id="6ee99-119">The folder/file structure of the NuGet provider will be (possibly with a different version number):</span></span>

```
NuGet
--2.8.5.208
----Microsoft.PackageManagement.NuGetProvider.dll
```

<span data-ttu-id="6ee99-120">Copiare le cartelle e il file usando un processo attendibile nei computer offline.</span><span class="sxs-lookup"><span data-stu-id="6ee99-120">Copy these folders and file using a trusted process to the offline machines.</span></span>

## <a name="manually-bootstrapping-nugetexe-to-support-publish-operations-on-a-machine-that-is-not-connected-to-the-internet"></a><span data-ttu-id="6ee99-121">Bootstrap manuale di NuGet.exe per il supporto delle operazioni di pubblicazione in un computer non connesso a Internet</span><span class="sxs-lookup"><span data-stu-id="6ee99-121">Manually bootstrapping NuGet.exe to support publish operations on a machine that is not connected to the Internet</span></span>

<span data-ttu-id="6ee99-122">In aggiunta al processo per il bootstrap manuale del provider NuGet, se il computer verrà usato per pubblicare moduli o script in una raccolta privata usando il cmdlet `Publish-Module` o `Publish-Script`, sarà necessario il file eseguibile binario NuGet.exe.</span><span class="sxs-lookup"><span data-stu-id="6ee99-122">In addition to the process to manually bootstrap the NuGet provider, if the machine will be used to publish modules or scripts to a private gallery using the `Publish-Module` or `Publish-Script` cmdlets, the NuGet.exe binary executable file will be required.</span></span>

<span data-ttu-id="6ee99-123">Il caso d'uso più comune per questo scenario è rappresentato da una raccolta privata disponibile per il supporto di un ambiente isolato.</span><span class="sxs-lookup"><span data-stu-id="6ee99-123">The most common use case for this scenario is when a private gallery is available to support an isolated environment.</span></span>
<span data-ttu-id="6ee99-124">Sono disponibili due opzioni per ottenere il file NuGet.exe.</span><span class="sxs-lookup"><span data-stu-id="6ee99-124">There are two options to obtain the NuGet.exe file.</span></span>

<span data-ttu-id="6ee99-125">La prima opzione consiste nell'eseguire il bootstrap di un computer connesso a Internet e nel copiare i file nei computer offline usando un processo attendibile.</span><span class="sxs-lookup"><span data-stu-id="6ee99-125">One option is to bootstrap a machine that is Internet connected and copy the files to the offline machines using a trusted process.</span></span>
<span data-ttu-id="6ee99-126">Dopo aver eseguito il bootstrap del computer connesso a Internet, il file binario NuGet.exe si troverà in una delle due cartelle seguenti:</span><span class="sxs-lookup"><span data-stu-id="6ee99-126">After bootstrapping the Internet connected machine, the NuGet.exe binary will be located in one of two folders:</span></span>

<span data-ttu-id="6ee99-127">Se i cmdlet `Publish-Module` o `Publish-Script` sono stati eseguiti con autorizzazioni elevate (come amministratore):</span><span class="sxs-lookup"><span data-stu-id="6ee99-127">If the `Publish-Module` or `Publish-Script` cmdlets were executed with elevated permissions (As an Administrator):</span></span>

```powershell
$env:ProgramData\Microsoft\Windows\PowerShell\PowerShellGet
```

<span data-ttu-id="6ee99-128">Se i cmdlet sono stati eseguiti come utente senza autorizzazioni elevate:</span><span class="sxs-lookup"><span data-stu-id="6ee99-128">If the cmdlets were executed as a user without elevated permissions:</span></span>

```powershell
$env:userprofile\AppData\Local\Microsoft\Windows\PowerShell\PowerShellGet\
```

<span data-ttu-id="6ee99-129">Una seconda alternativa è il download di NuGet.exe dal sito Web NuGet.Org: [https://dist.nuget.org/index.html](https://www.nuget.org/downloads) Quando si seleziona una versione NugGet per i computer di produzione, assicurarsi che sia successiva alla versione 2.8.5.208 e identificare la versione con etichetta "consigliata".</span><span class="sxs-lookup"><span data-stu-id="6ee99-129">A second option is to download NuGet.exe from the NuGet.Org website: [https://dist.nuget.org/index.html](https://www.nuget.org/downloads) When selecting a NugGet version for production machines, make sure it is later than 2.8.5.208, and identify the version that has been labeled "recommended".</span></span>
<span data-ttu-id="6ee99-130">Ricordarsi di sbloccare il file se è stato scaricato tramite un browser.</span><span class="sxs-lookup"><span data-stu-id="6ee99-130">Remember to unblock the file if it was downloaded using a browser.</span></span>
<span data-ttu-id="6ee99-131">Questa operazione può essere eseguita usando il cmdlet `Unblock-File`.</span><span class="sxs-lookup"><span data-stu-id="6ee99-131">This can be performed by using the `Unblock-File` cmdlet.</span></span>

<span data-ttu-id="6ee99-132">In entrambi i casi, è possibile copiare il file di NuGet.exe in qualsiasi percorso in `$env:path`, ma i percorsi standard sono:</span><span class="sxs-lookup"><span data-stu-id="6ee99-132">In either case, the NuGet.exe file can be copied to any location in `$env:path`, but the standard locations are:</span></span>

<span data-ttu-id="6ee99-133">Per rendere disponibile il file eseguibile in modo che tutti gli utenti possano usare i cmdlet `Publish-Module` e `Publish-Script`:</span><span class="sxs-lookup"><span data-stu-id="6ee99-133">To make the executable available so that all users can use `Publish-Module` and `Publish-Script` cmdlets:</span></span>

```powershell
$env:ProgramData\Microsoft\Windows\PowerShell\PowerShellGet
```

<span data-ttu-id="6ee99-134">Per rendere disponibile il file eseguibile solo per un utente specifico, copiare il percorso all'interno del profilo dell'utente:</span><span class="sxs-lookup"><span data-stu-id="6ee99-134">To make the executable available to only a specific user, copy to the location within only that user's profile:</span></span>

```powershell
$env:userprofile\AppData\Local\Microsoft\Windows\PowerShell\PowerShellGet\
```