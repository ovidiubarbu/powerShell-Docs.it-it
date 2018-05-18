
---
<span data-ttu-id="63df4-101">ms.date :  06/12/2017 collaboratore:  manikb ms.topic:  parole chiave di riferimento:  gallery,powershell,cmdlet,psget titolo:  Bootstrap di NuGet</span><span class="sxs-lookup"><span data-stu-id="63df4-101">ms.date :  06/12/2017 contributor:  manikb ms.topic:  reference keywords:  gallery,powershell,cmdlet,psget title:  Bootstrapping NuGet</span></span>
---
# <a name="bootstrap-the-nuget-provider-and-nugetexe"></a><span data-ttu-id="63df4-102">Bootstrap del provider NuGet e di NuGet.exe</span><span class="sxs-lookup"><span data-stu-id="63df4-102">Bootstrap the NuGet provider and NuGet.exe</span></span>

<span data-ttu-id="63df4-103">Il file NuGet.exe non è incluso nella versione più recente del provider NuGet.</span><span class="sxs-lookup"><span data-stu-id="63df4-103">NuGet.exe is not included in the latest NuGet provider.</span></span>
<span data-ttu-id="63df4-104">Per le operazioni di pubblicazione di un modulo o uno script, PowerShellGet richiede il file NuGet.exe eseguibile binario.</span><span class="sxs-lookup"><span data-stu-id="63df4-104">For publish operations of either a module or script, PowerShellGet requires the binary executable NuGet.exe.</span></span>
<span data-ttu-id="63df4-105">Per tutte le altre operazioni, che includono la *ricerca*,l' *installazione*, il *salvataggio* e la *disinstallazione*, è necessario soltanto il provider NuGet.</span><span class="sxs-lookup"><span data-stu-id="63df4-105">Only the NuGet provider is required for all other operations, including *find*, *install*, *save*, and *uninstall*.</span></span>
<span data-ttu-id="63df4-106">PowerShellGet include la logica per gestire un bootstrap combinato del provider NuGet e di NuGet.exe o un bootstrap del solo provider NuGet.</span><span class="sxs-lookup"><span data-stu-id="63df4-106">PowerShellGet includes logic to handle either a combined bootstrap of the NuGet provider and NuGet.exe, or bootstrap of only the NuGet provider.</span></span>
<span data-ttu-id="63df4-107">In entrambi i casi deve essere visualizzato un solo messaggio di richiesta.</span><span class="sxs-lookup"><span data-stu-id="63df4-107">In either case, only a single prompt message should occur.</span></span>
<span data-ttu-id="63df4-108">Se il computer non è connesso a Internet, è necessario che l'utente o un amministratore copi un'istanza attendibile del provider NuGet e/o del file NuGet.exe nel computer disconnesso.</span><span class="sxs-lookup"><span data-stu-id="63df4-108">If the machine is not connected to the Internet, the user or an administrator must copy a trusted instance of the NuGet provider and/or the NuGet.exe file to the disconnected machine.</span></span>

><span data-ttu-id="63df4-109">**Nota**: a partire dalla versione 6, il provider NuGet è incluso nell'installazione di PowerShell.</span><span class="sxs-lookup"><span data-stu-id="63df4-109">**Note**: Starting with version 6, the NuGet provider is included in the installation of PowerShell.</span></span> [http://github.com/powershell/powershell](http://github.com/powershell/powershell)

## <a name="resolving-error-when-the-nuget-provider-has-not-been-installed-on-a-machine-that-is-internet-connected"></a><span data-ttu-id="63df4-110">Risoluzione dell'errore se il provider NuGet non è stato installato in un computer connesso a Internet</span><span class="sxs-lookup"><span data-stu-id="63df4-110">Resolving error when the NuGet provider has not been installed on a machine that is Internet connected</span></span>

```powershell
PS> Find-Module -Repository PSGallery -Verbose -Name Contoso

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

PS> Find-Module -Repository PSGallery -Verbose -Name Contoso

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

## <a name="resolving-error-when-the-nuget-provider-is-available-and-nugetexe-is-not-available-during-the-publish-operation-on-a-machine-that-is-internet-connected"></a><span data-ttu-id="63df4-111">Risoluzione dell'errore se il provider NuGet è disponibile e NuGet.exe non è disponibile durante l'operazione di pubblicazione in un computer connesso a Internet</span><span class="sxs-lookup"><span data-stu-id="63df4-111">Resolving error when the NuGet provider is available and NuGet.exe is not available during the publish operation on a machine that is Internet connected</span></span>

```powershell
PS> Publish-Module -Name Contoso -Repository PSGallery -Verbose

NuGet.exe is required to continue
PowerShellGet requires NuGet.exe to publish an item to the NuGet-based repositories. NuGet.exe must be available under one of the paths specified in PATH environment variable value. Do you want PowerShellGet to install NuGet.exe now?
[Y] Yes  [N] No  [S] Suspend  [?] Help (default is "Y"): N
Publish-Module : NuGet.exe is required to interact with NuGet-based repositories. Please ensure that NuGet.exe is available under one of the paths specified in PATH environment variable value.
At line:1 char:1
+ Publish-Module -Name Contoso -Repository PSGallery -Verbose
+ ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
    + CategoryInfo          : InvalidOperation: (:) [Publish-Module], InvalidOperationException
    + FullyQualifiedErrorId : CouldNotInstallNuGetExe,Publish-Module

PS> Publish-Module -Name Contoso -Repository PSGallery -Verbose

NuGet.exe is required to continue
PowerShellGet requires NuGet.exe to publish an item to the NuGet-based repositories. NuGet.exe must be available under one of the paths specified in PATH environment variable value. Do you want PowerShellGet to install NuGet.exe now?
[Y] Yes  [N] No  [S] Suspend  [?] Help (default is "Y"): Y
VERBOSE: Installing NuGet.exe.
VERBOSE: Successfully published module 'Contoso' to the module publish location 'https://www.powershellgallery.com/api/v2/'. Please allow few minutes for 'Contoso' to show up in the search results.
```

## <a name="resolving-error-when-both-nuget-provider-and-nugetexe-are-not-available-during-the-publish-operation-on-a-machine-that-is-internet-connected"></a><span data-ttu-id="63df4-112">Risoluzione dell'errore se il provider NuGet e NuGet.exe non sono disponibili durante l'operazione di pubblicazione in un computer connesso a Internet</span><span class="sxs-lookup"><span data-stu-id="63df4-112">Resolving error when both NuGet provider and NuGet.exe are not available during the publish operation on a machine that is Internet connected</span></span>

```powershell
PS> Publish-Module -Name Contoso -Repository PSGallery -Verbose

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

PS> Publish-Module -Name Contoso -Repository PSGallery -Verbose

NuGet.exe and NuGet provider are required to continue
PowerShellGet requires NuGet.exe and NuGet provider version '2.8.5.201' or newer to interact with the NuGet-based repositories. Do you want PowerShellGet to install both NuGet.exe and NuGet provider now?
[Y] Yes  [N] No  [S] Suspend  [?] Help (default is "Y"): Y
VERBOSE: Installing NuGet provider.
VERBOSE: Installing NuGet.exe.
VERBOSE: Successfully published module 'Contoso' to the module publish location 'https://www.powershellgallery.com/api/v2/'. Please allow few minutes for 'Contoso' to show up in the search results.
```

## <a name="manually-bootstrapping-the-nuget-provider-on-a-machine-that-is-not-connected-to-the-internet"></a><span data-ttu-id="63df4-113">Bootstrap manuale del provider NuGet in un computer non connesso a Internet</span><span class="sxs-lookup"><span data-stu-id="63df4-113">Manually bootstrapping the NuGet provider on a machine that is not connected to the Internet</span></span>

<span data-ttu-id="63df4-114">I processi illustrati in precedenza presuppongono che il computer sia connesso a Internet e in grado di scaricare file da un percorso pubblico.</span><span class="sxs-lookup"><span data-stu-id="63df4-114">The processes demonstrated above assume the machine is connected to the Internet and can download files from a public location.</span></span>
<span data-ttu-id="63df4-115">Se il download non è possibile, l'unica opzione consiste nell'eseguire il bootstrap di un computer usando i processi descritti in precedenza e nel copiare manualmente il provider nel nodo isolato tramite un processo attendibile offline.</span><span class="sxs-lookup"><span data-stu-id="63df4-115">If that is not possible, the only option is to bootstrap a machine using the processes given above, and manually copy the provider to the isolated node through an offline trusted process.</span></span>
<span data-ttu-id="63df4-116">Il caso d'uso più comune per questo scenario è rappresentato da una raccolta privata disponibile per il supporto di un ambiente isolato.</span><span class="sxs-lookup"><span data-stu-id="63df4-116">The most common use case for this scenario is when a private gallery is available to support an isolated environment.</span></span>

<span data-ttu-id="63df4-117">Dopo aver completato il processo precedente per eseguire il bootstrap di un computer connesso a Internet, i file del provider saranno disponibili nel percorso seguente:</span><span class="sxs-lookup"><span data-stu-id="63df4-117">After following the process above to bootstrap an Internet connected machine, you will find provider files in the location:</span></span>

```
C:\Program Files\PackageManagement\ProviderAssemblies\
```

<span data-ttu-id="63df4-118">La struttura di cartelle e file del provider NuGet sarà la seguente (eventualmente con un numero di versione diverso):</span><span class="sxs-lookup"><span data-stu-id="63df4-118">The folder/file structure of the NuGet provider will be (possibly with a different version number):</span></span>

<span data-ttu-id="63df4-119">NuGet</span><span class="sxs-lookup"><span data-stu-id="63df4-119">NuGet</span></span><br>
<span data-ttu-id="63df4-120">--2.8.5.208</span><span class="sxs-lookup"><span data-stu-id="63df4-120">--2.8.5.208</span></span><br>
<span data-ttu-id="63df4-121">----Microsoft.PackageManagement.NuGetProvider.dll</span><span class="sxs-lookup"><span data-stu-id="63df4-121">----Microsoft.PackageManagement.NuGetProvider.dll</span></span>

<span data-ttu-id="63df4-122">Copiare le cartelle e il file usando un processo attendibile nei computer offline.</span><span class="sxs-lookup"><span data-stu-id="63df4-122">Copy these folders and file using a trusted process to the offline machines.</span></span>

## <a name="manually-bootstrapping-nugetexe-to-support-publish-operations-on-a-machine-that-is-not-connected-to-the-internet"></a><span data-ttu-id="63df4-123">Bootstrap manuale di NuGet.exe per il supporto delle operazioni di pubblicazione in un computer non connesso a Internet</span><span class="sxs-lookup"><span data-stu-id="63df4-123">Manually bootstrapping NuGet.exe to support publish operations on a machine that is not connected to the Internet</span></span>

<span data-ttu-id="63df4-124">In aggiunta al processo per il bootstrap manuale del provider NuGet, se il computer verrà usato per pubblicare moduli o script in una raccolta privata usando il cmdlet *Publish-Module* o *Publish-Script*, sarà necessario il file eseguibile binario NuGet.exe.</span><span class="sxs-lookup"><span data-stu-id="63df4-124">In addition to the process to manually bootstrap the NuGet provider, if the machine will be used to publish modules or scripts to a private gallery using the *Publish-Module* or *Publish-Script* cmdlets, the NuGet.exe binary executable file will be required.</span></span>
<span data-ttu-id="63df4-125">Il caso d'uso più comune per questo scenario è rappresentato da una raccolta privata disponibile per il supporto di un ambiente isolato.</span><span class="sxs-lookup"><span data-stu-id="63df4-125">The most common use case for this scenario is when a private gallery is available to support an isolated environment.</span></span>
<span data-ttu-id="63df4-126">Sono disponibili due opzioni per ottenere il file NuGet.exe.</span><span class="sxs-lookup"><span data-stu-id="63df4-126">There are two options to obtain the NuGet.exe file.</span></span>

<span data-ttu-id="63df4-127">La prima opzione consiste nell'eseguire il bootstrap di un computer connesso a Internet e nel copiare i file nei computer offline usando un processo attendibile.</span><span class="sxs-lookup"><span data-stu-id="63df4-127">One option is to bootstrap a machine that is Internet connected and copy the files to the offline machines using a trusted process.</span></span>
<span data-ttu-id="63df4-128">Dopo aver eseguito il bootstrap del computer connesso a Internet, il file binario NuGet.exe si troverà in una delle due cartelle seguenti:</span><span class="sxs-lookup"><span data-stu-id="63df4-128">After bootstrapping the Internet connected machine, the NuGet.exe binary will be located in one of two folders:</span></span>

<span data-ttu-id="63df4-129">Se i cmdlet *Publish-Module* o *Publish-Script* sono stati eseguiti con autorizzazioni elevate (come amministratore):</span><span class="sxs-lookup"><span data-stu-id="63df4-129">If the *Publish-Module* or *Publish-Script* cmdlets were executed with elevated permissions (As an Administrator):</span></span>

```
$env:ProgramData\Microsoft\Windows\PowerShell\PowerShellGet
```

<span data-ttu-id="63df4-130">Se i cmdlet sono stati eseguiti come utente senza autorizzazioni elevate:</span><span class="sxs-lookup"><span data-stu-id="63df4-130">If the cmdlets were executed as a user without elevated permissions:</span></span>

```
$env:userprofile\AppData\Local\Microsoft\Windows\PowerShell\PowerShellGet\
```

<span data-ttu-id="63df4-131">La seconda opzione consiste nello scaricare NuGet.exe dal sito Web NuGet.Org: [https://dist.nuget.org/index.html](https://dist.nuget.org/index.html)</span><span class="sxs-lookup"><span data-stu-id="63df4-131">A second option is to download NuGet.exe from the NuGet.Org website: [https://dist.nuget.org/index.html](https://dist.nuget.org/index.html)</span></span><br>
<span data-ttu-id="63df4-132">Quando si seleziona una versione NugGet per i computer di produzione, assicurarsi che sia successiva alla versione 2.8.5.208 e identificare la versione con etichetta "consigliata".</span><span class="sxs-lookup"><span data-stu-id="63df4-132">When selecting a NugGet version for production machines, make sure it is later than 2.8.5.208, and identify the version that has been labeled "recommended".</span></span>
<span data-ttu-id="63df4-133">Ricordarsi di sbloccare il file se è stato scaricato tramite un browser.</span><span class="sxs-lookup"><span data-stu-id="63df4-133">Remember to unblock the file if it was downloaded using a browser.</span></span>
<span data-ttu-id="63df4-134">Questa operazione può essere eseguita usando il cmdlet *Unblock-File*.</span><span class="sxs-lookup"><span data-stu-id="63df4-134">This can be performed by using the *Unblock-File* cmdlet.</span></span>

<span data-ttu-id="63df4-135">In entrambi i casi, è possibile copiare il file di NuGet.exe in qualsiasi percorso in *$env: percorso*, ma i percorsi standard sono:</span><span class="sxs-lookup"><span data-stu-id="63df4-135">In either case, the NuGet.exe file can be copied to any location in *$env:path*, but the standard locations are:</span></span>

<span data-ttu-id="63df4-136">Per rendere disponibile il file eseguibile in modo che tutti gli utenti possano usare i cmdlet *Publish-Module* e *Publish-Script*:</span><span class="sxs-lookup"><span data-stu-id="63df4-136">To make the executable available so that all users can use *Publish-Module* and *Publish-Script* cmdlets:</span></span>

```
$env:ProgramData\Microsoft\Windows\PowerShell\PowerShellGet
```

<span data-ttu-id="63df4-137">Per rendere disponibile il file eseguibile solo per un utente specifico, copiare il percorso all'interno del profilo dell'utente:</span><span class="sxs-lookup"><span data-stu-id="63df4-137">To make the executable available to only a specific user, copy to the location within only that user's profile:</span></span>

```
$env:userprofile\AppData\Local\Microsoft\Windows\PowerShell\PowerShellGet\
```