---
ms.date: 11/06/2018
contributor: JKeithB
keywords: raccolta,powershell,cmdlet,psgallery, psget
title: Uso dei repository PowerShell locali
ms.openlocfilehash: 94824ea584c097838b24c6f2cd02407b6147a781
ms.sourcegitcommit: 4a2cf30351620a58ba95ff5d76b247e601907589
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 09/27/2019
ms.locfileid: "71327992"
---
# <a name="working-with-local-powershellget-repositories"></a><span data-ttu-id="b7b3c-103">Uso dei repository PowerShellGet locali</span><span class="sxs-lookup"><span data-stu-id="b7b3c-103">Working with local PowerShellGet Repositories</span></span>

<span data-ttu-id="b7b3c-104">Il modulo PowerShellGet supporta repository diversi da PowerShell Gallery.</span><span class="sxs-lookup"><span data-stu-id="b7b3c-104">The PowerShellGet module support repositories other than the PowerShell Gallery.</span></span>
<span data-ttu-id="b7b3c-105">Questi cmdlet consentono gli scenari seguenti:</span><span class="sxs-lookup"><span data-stu-id="b7b3c-105">These cmdlets enable the following scenarios:</span></span>

- <span data-ttu-id="b7b3c-106">Supporto di un set attendibile e pre-convalidato di moduli PowerShell per l'uso nell'ambiente</span><span class="sxs-lookup"><span data-stu-id="b7b3c-106">Support a trusted, pre-validated set of PowerShell modules for use in your environment</span></span>
- <span data-ttu-id="b7b3c-107">Test di una pipeline CI/CD che compila moduli o script PowerShell</span><span class="sxs-lookup"><span data-stu-id="b7b3c-107">Testing a CI/CD pipeline that builds PowerShell modules or scripts</span></span>
- <span data-ttu-id="b7b3c-108">Distribuzione di moduli e script PowerShell in sistemi che non possono accedere a Internet</span><span class="sxs-lookup"><span data-stu-id="b7b3c-108">Deliver PowerShell scripts and modules to systems that can't access the internet</span></span>

<span data-ttu-id="b7b3c-109">Questo articolo descrive come configurare un repository PowerShell locale.</span><span class="sxs-lookup"><span data-stu-id="b7b3c-109">This article describes how to set up a local PowerShell repository.</span></span> <span data-ttu-id="b7b3c-110">L'articolo riguarda anche il modulo [OfflinePowerShellGetDeploy][] disponibile in PowerShell Gallery.</span><span class="sxs-lookup"><span data-stu-id="b7b3c-110">The article also covers the [OfflinePowerShellGetDeploy][] module available from the PowerShell Gallery.</span></span> <span data-ttu-id="b7b3c-111">Questo modulo contiene i cmdlet per installare la versione più recente di PowerShellGet nel repository locale.</span><span class="sxs-lookup"><span data-stu-id="b7b3c-111">This module contains cmdlets to install the latest version of PowerShellGet into your local repository.</span></span>

## <a name="local-repository-types"></a><span data-ttu-id="b7b3c-112">Tipi di repository locali</span><span class="sxs-lookup"><span data-stu-id="b7b3c-112">Local repository types</span></span>

<span data-ttu-id="b7b3c-113">È possibile creare un repository PowerShell in due modi: Server NuGet o condivisione file.</span><span class="sxs-lookup"><span data-stu-id="b7b3c-113">There are two ways to create a local PSRepository: NuGet server or file share.</span></span> <span data-ttu-id="b7b3c-114">Ogni tipo presenta vantaggi e svantaggi.</span><span class="sxs-lookup"><span data-stu-id="b7b3c-114">Each type has advantages and disadvantages:</span></span>

<span data-ttu-id="b7b3c-115">Server NuGet</span><span class="sxs-lookup"><span data-stu-id="b7b3c-115">NuGet Server</span></span>

| <span data-ttu-id="b7b3c-116">Vantaggi</span><span class="sxs-lookup"><span data-stu-id="b7b3c-116">Advantages</span></span>| <span data-ttu-id="b7b3c-117">Svantaggi</span><span class="sxs-lookup"><span data-stu-id="b7b3c-117">Disadvantages</span></span> |
| --- | --- |
| <span data-ttu-id="b7b3c-118">Simula quasi perfettamente la funzionalità di PowerShell Gallery</span><span class="sxs-lookup"><span data-stu-id="b7b3c-118">Closely mimics PowerShellGallery functionality</span></span> | <span data-ttu-id="b7b3c-119">L'app a più livelli richiede la pianificazione e il supporto delle operazioni</span><span class="sxs-lookup"><span data-stu-id="b7b3c-119">Multi-tier app requires operations planning & support</span></span> |
| <span data-ttu-id="b7b3c-120">NuGet si integra con Visual Studio e altri strumenti</span><span class="sxs-lookup"><span data-stu-id="b7b3c-120">NuGet integrates with Visual Studio, other tools</span></span> | <span data-ttu-id="b7b3c-121">È necessario gestire il modello di autenticazione e gli account NuGet</span><span class="sxs-lookup"><span data-stu-id="b7b3c-121">Authentication model and NuGet accounts management needed</span></span> |
| <span data-ttu-id="b7b3c-122">NuGet supporta i metadati in pacchetti `.Nupkg`</span><span class="sxs-lookup"><span data-stu-id="b7b3c-122">NuGet supports metadata in `.Nupkg` packages</span></span> | <span data-ttu-id="b7b3c-123">La pubblicazione richiede la gestione e la manutenzione delle chiavi API</span><span class="sxs-lookup"><span data-stu-id="b7b3c-123">Publishing requires API Key management & maintenance</span></span> |
| <span data-ttu-id="b7b3c-124">Fornisce ricerca, amministrazione dei pacchetti e così via.</span><span class="sxs-lookup"><span data-stu-id="b7b3c-124">Provides search, package administration, etc.</span></span> | |

<span data-ttu-id="b7b3c-125">Condivisione file</span><span class="sxs-lookup"><span data-stu-id="b7b3c-125">File Share</span></span>

| <span data-ttu-id="b7b3c-126">Vantaggi</span><span class="sxs-lookup"><span data-stu-id="b7b3c-126">Advantages</span></span>| <span data-ttu-id="b7b3c-127">Svantaggi</span><span class="sxs-lookup"><span data-stu-id="b7b3c-127">Disadvantages</span></span> |
| --- | --- |
| <span data-ttu-id="b7b3c-128">Semplice da configurare, sottoporre a backup e gestire</span><span class="sxs-lookup"><span data-stu-id="b7b3c-128">Easy to set up, back up, and maintain</span></span> | <span data-ttu-id="b7b3c-129">I metadati usati da PowerShellGet non sono disponibili</span><span class="sxs-lookup"><span data-stu-id="b7b3c-129">Metadata used by PowerShellGet isn't available</span></span> |
| <span data-ttu-id="b7b3c-130">Modello di sicurezza semplice, autorizzazioni utente sulla condivisione</span><span class="sxs-lookup"><span data-stu-id="b7b3c-130">Simple security model - user permissions on the share</span></span> | <span data-ttu-id="b7b3c-131">Nessuna interfaccia utente oltre la condivisione file di base</span><span class="sxs-lookup"><span data-stu-id="b7b3c-131">No UI beyond basic file share</span></span> |
| <span data-ttu-id="b7b3c-132">Nessun vincolo, ad esempio la sostituzione degli elementi esistenti</span><span class="sxs-lookup"><span data-stu-id="b7b3c-132">No constraints such as replacing existing items</span></span> | <span data-ttu-id="b7b3c-133">Sicurezza limitata e nessuna registrazione degli utenti e degli aggiornamenti che eseguono</span><span class="sxs-lookup"><span data-stu-id="b7b3c-133">Limited security and no recording of who updates what</span></span> |

<span data-ttu-id="b7b3c-134">PowerShellGet è compatibile con entrambi i tipi e supporta l'individuazione delle versioni e l'installazione delle dipendenze.</span><span class="sxs-lookup"><span data-stu-id="b7b3c-134">PowerShellGet works with either type and supports locating versions and dependency installation.</span></span>
<span data-ttu-id="b7b3c-135">Tuttavia, alcune funzionalità compatibili con PowerShell Gallery non sono disponibili per le condivisioni file o i server NuGet di base.</span><span class="sxs-lookup"><span data-stu-id="b7b3c-135">However, some features that work for the PowerShell Gallery aren't available for base NuGet servers or file shares.</span></span>

- <span data-ttu-id="b7b3c-136">Tutti gli elementi sono costituiti da pacchetti, senza distinzione tra script, moduli, risorse DSC o funzionalità di ruoli.</span><span class="sxs-lookup"><span data-stu-id="b7b3c-136">Everything is a package - no differentiation of scripts, modules, DSC resources, or role capabilities.</span></span>
- <span data-ttu-id="b7b3c-137">I server di condivisione file non possono visualizzare i metadati del pacchetto, inclusi i tag.</span><span class="sxs-lookup"><span data-stu-id="b7b3c-137">File share servers can't see package metadata, including tags.</span></span>

## <a name="creating-a-local-repository"></a><span data-ttu-id="b7b3c-138">Creazione di un repository locale</span><span class="sxs-lookup"><span data-stu-id="b7b3c-138">Creating a local repository</span></span>

<span data-ttu-id="b7b3c-139">L'articolo seguente elenca i passaggi per la configurazione di un server NuGet personalizzato.</span><span class="sxs-lookup"><span data-stu-id="b7b3c-139">The following article lists the steps for setting up your own NuGet Server.</span></span>

- <span data-ttu-id="b7b3c-140">[NuGet.Server][]</span><span class="sxs-lookup"><span data-stu-id="b7b3c-140">[NuGet.Server][]</span></span>

<span data-ttu-id="b7b3c-141">Seguire i passaggi fino al momento dell'aggiunta di pacchetti.</span><span class="sxs-lookup"><span data-stu-id="b7b3c-141">Follow the steps up to the point of adding packages.</span></span> <span data-ttu-id="b7b3c-142">I passaggi per la [pubblicazione di un pacchetto](#publishing-to-a-local-repository) sono trattati più avanti in questo articolo.</span><span class="sxs-lookup"><span data-stu-id="b7b3c-142">The steps for [publishing a package](#publishing-to-a-local-repository) are covered later in this article.</span></span>

<span data-ttu-id="b7b3c-143">Per un repository basato su condivisione file, assicurarsi che gli utenti dispongano delle autorizzazioni per accedere alla condivisione file.</span><span class="sxs-lookup"><span data-stu-id="b7b3c-143">For a file share-based repository, make sure that your users have permissions to access the file share.</span></span>

## <a name="registering-a-local-repository"></a><span data-ttu-id="b7b3c-144">Registrazione di un repository locale</span><span class="sxs-lookup"><span data-stu-id="b7b3c-144">Registering a local repository</span></span>

<span data-ttu-id="b7b3c-145">Prima di poter usare un repository, è necessario registrarlo con il comando `Register-PSRepository`.</span><span class="sxs-lookup"><span data-stu-id="b7b3c-145">Before a repository can be used, it must be registered using the `Register-PSRepository` command.</span></span>
<span data-ttu-id="b7b3c-146">Negli esempi seguenti, **InstallationPolicy** è impostato su *Trusted*, presupponendo che si ritenga attendibile il repository.</span><span class="sxs-lookup"><span data-stu-id="b7b3c-146">In the examples below, the **InstallationPolicy** is set to *Trusted*, on the assumption that you trust your own repository.</span></span>

```powershell
# Register a NuGet-based server
Register-PSRepository -Name LocalPSRepo -SourceLocation http://MyLocalNuget/Api/V2/ -ScriptSourceLocation http://MyLocalNuget/Api/V2 -InstallationPolicy Trusted

# Register a file share on my local machine
Register-PSRepository -Name LocalPSRepo -SourceLocation '\\localhost\PSRepoLocal\' -ScriptSourceLocation '\\localhost\PSRepoLocal\' -InstallationPolicy Trusted
```

<span data-ttu-id="b7b3c-147">Notare la differenza nel modo in cui i due comandi gestiscono **ScriptSourceLocation**.</span><span class="sxs-lookup"><span data-stu-id="b7b3c-147">Take note of the difference between how the two commands handle **ScriptSourceLocation**.</span></span> <span data-ttu-id="b7b3c-148">Per repository basati su condivisione file, **SourceLocation** e **ScriptSourceLocation** devono corrispondere.</span><span class="sxs-lookup"><span data-stu-id="b7b3c-148">For a file share-based repositories, the **SourceLocation** and **ScriptSourceLocation** must match.</span></span> <span data-ttu-id="b7b3c-149">Per un repository basato sul Web, devono essere diversi, quindi in questo esempio viene aggiunto un carattere "/" finale a **SourceLocation**.</span><span class="sxs-lookup"><span data-stu-id="b7b3c-149">For a web-based repository, they must be different, so in this example a trailing "/" is added to the **SourceLocation**.</span></span>

<span data-ttu-id="b7b3c-150">Se si intende rendere predefinito il repository PowerShell appena creato, è necessario annullare la registrazione di tutti gli altri repository PowerShell.</span><span class="sxs-lookup"><span data-stu-id="b7b3c-150">If you want the newly created PSRepository to be the default repository, you must unregister all other PSRepositories.</span></span> <span data-ttu-id="b7b3c-151">Ad esempio:</span><span class="sxs-lookup"><span data-stu-id="b7b3c-151">For example:</span></span>

```powershell
Unregister-PSRepository -Name PSGallery
```

> [!NOTE]
> <span data-ttu-id="b7b3c-152">Il nome di repository 'PSGallery' è riservato per l'uso da parte di PowerShell Gallery.</span><span class="sxs-lookup"><span data-stu-id="b7b3c-152">The repository name 'PSGallery' is reserved for use by the PowerShell Gallery.</span></span> <span data-ttu-id="b7b3c-153">È possibile annullare la registrazione di PSGallery, ma non è possibile riutilizzare il nome PSGallery per un altro repository.</span><span class="sxs-lookup"><span data-stu-id="b7b3c-153">You can unregister PSGallery, but you cannot reuse the name PSGallery for any other repository.</span></span>

<span data-ttu-id="b7b3c-154">Se è necessario ripristinare PSGallery, eseguire il comando seguente:</span><span class="sxs-lookup"><span data-stu-id="b7b3c-154">If you need to restore the PSGallery, run the following command:</span></span>

```powershell
Register-PSRepository -Default
```

## <a name="publishing-to-a-local-repository"></a><span data-ttu-id="b7b3c-155">Pubblicazione in un repository locale</span><span class="sxs-lookup"><span data-stu-id="b7b3c-155">Publishing to a local repository</span></span>

<span data-ttu-id="b7b3c-156">Dopo aver registrato il repository PowerShell locale, sarà possibile eseguire pubblicazioni al suo interno.</span><span class="sxs-lookup"><span data-stu-id="b7b3c-156">Once you've registered the local PSRepository, you can publish to your local PSRepository.</span></span> <span data-ttu-id="b7b3c-157">Esistono due scenari di pubblicazione principali: pubblicazione del proprio modulo e pubblicazione di un modulo da PSGallery.</span><span class="sxs-lookup"><span data-stu-id="b7b3c-157">There are two main publishing scenarios: publishing your own module and publishing a module from the PSGallery.</span></span>

### <a name="publishing-a-module-you-authored"></a><span data-ttu-id="b7b3c-158">Pubblicazione di un modulo creato dall'utente</span><span class="sxs-lookup"><span data-stu-id="b7b3c-158">Publishing a module you authored</span></span>

<span data-ttu-id="b7b3c-159">Usare `Publish-Module` e `Publish-Script` per pubblicare un modulo nel repository PowerShell locale con la stessa procedura valida per PowerShell Gallery.</span><span class="sxs-lookup"><span data-stu-id="b7b3c-159">Use `Publish-Module` and `Publish-Script` to publish your module to your local PSRepository the same way you do for the PowerShell Gallery.</span></span>

- <span data-ttu-id="b7b3c-160">Specificare la posizione per il codice</span><span class="sxs-lookup"><span data-stu-id="b7b3c-160">Specify the location for your code</span></span>
- <span data-ttu-id="b7b3c-161">Specificare una chiave API</span><span class="sxs-lookup"><span data-stu-id="b7b3c-161">Supply an API key</span></span>
- <span data-ttu-id="b7b3c-162">Specificare il nome del repository.</span><span class="sxs-lookup"><span data-stu-id="b7b3c-162">Specify the repository name.</span></span> <span data-ttu-id="b7b3c-163">Ad esempio, `-PSRepository LocalPSRepo`</span><span class="sxs-lookup"><span data-stu-id="b7b3c-163">For example, `-PSRepository LocalPSRepo`</span></span>

> [!NOTE]
> <span data-ttu-id="b7b3c-164">È necessario creare un account nel server NuGet, quindi eseguire l'accesso per generare e salvare la chiave API.</span><span class="sxs-lookup"><span data-stu-id="b7b3c-164">You must create an account in the NuGet server, then sign in to generate and save the API key.</span></span>
> <span data-ttu-id="b7b3c-165">Per una condivisione file, usare una stringa non vuota per il valore NuGetApiKey.</span><span class="sxs-lookup"><span data-stu-id="b7b3c-165">For a file share, use any non-blank string for the NuGetApiKey value.</span></span>

<span data-ttu-id="b7b3c-166">Di seguito sono riportati alcuni esempi.</span><span class="sxs-lookup"><span data-stu-id="b7b3c-166">Examples:</span></span>

```powershell
# Publish to a NuGet Server repository using my NuGetAPI key
Publish-Module -Path 'c:\projects\MyModule' -Repository LocalPsRepo -NuGetApiKey 'oy2bi4avlkjolp6bme6azdyssn6ps3iu7ib2qpiudrtbji'

# Publish to a file share repo - the NuGet API key must be a non-blank string
Publish-Module -Path 'c:\projects\MyModule' -Repository LocalPsRepo -NuGetApiKey 'AnyStringWillDo'
```

> [!IMPORTANT]
> <span data-ttu-id="b7b3c-167">Per garantire la sicurezza, le chiavi API non devono essere hardcoded negli script.</span><span class="sxs-lookup"><span data-stu-id="b7b3c-167">To ensure security, API keys should not be hard-coded in scripts.</span></span> <span data-ttu-id="b7b3c-168">Usare un sistema di gestione delle chiavi sicuro.</span><span class="sxs-lookup"><span data-stu-id="b7b3c-168">Use a secure key management system.</span></span>

### <a name="publishing-a-module-from-the-psgallery"></a><span data-ttu-id="b7b3c-169">Pubblicazione di un modulo da PSGallery</span><span class="sxs-lookup"><span data-stu-id="b7b3c-169">Publishing a module from the PSGallery</span></span>

<span data-ttu-id="b7b3c-170">Per pubblicare un modulo da PSGallery nel repository PowerShell locale, è possibile usare il cmdlet 'Save-Package'.</span><span class="sxs-lookup"><span data-stu-id="b7b3c-170">To publish a module from the PSGallery to your local PSRepository, you can use the 'Save-Package' cmdlet.</span></span>

- <span data-ttu-id="b7b3c-171">Specificare il nome del pacchetto</span><span class="sxs-lookup"><span data-stu-id="b7b3c-171">Specify the Name of the Package</span></span>
- <span data-ttu-id="b7b3c-172">Specificare 'NuGet' come provider</span><span class="sxs-lookup"><span data-stu-id="b7b3c-172">Specify 'NuGet' as the Provider</span></span>
- <span data-ttu-id="b7b3c-173">Specificare la posizione di PSGallery come origine (https://www.powershellgallery.com/api/v2)</span><span class="sxs-lookup"><span data-stu-id="b7b3c-173">Specify the PSGallery location as the source (https://www.powershellgallery.com/api/v2)</span></span>
- <span data-ttu-id="b7b3c-174">Specificare il percorso del repository locale</span><span class="sxs-lookup"><span data-stu-id="b7b3c-174">Specify the path to your local Repository</span></span>

<span data-ttu-id="b7b3c-175">Esempio:</span><span class="sxs-lookup"><span data-stu-id="b7b3c-175">Example:</span></span>

```powershell
# Publish from the PSGallery to your local Repository
Save-Package -Name 'PackageName' -Provider Nuget -Source https://www.powershellgallery.com/api/v2 -Path '\\localhost\PSRepoLocal\'
```

<span data-ttu-id="b7b3c-176">Se il repository PowerShell locale è basato sul Web, è necessario un passaggio aggiuntivo che preveda l'uso di nuget.exe per eseguire la pubblicazione.</span><span class="sxs-lookup"><span data-stu-id="b7b3c-176">If your local PSRepository is web-based, it requires an additional step that uses nuget.exe to publish.</span></span>

<span data-ttu-id="b7b3c-177">Vedere la documentazione per l'uso di [nuget.exe][].</span><span class="sxs-lookup"><span data-stu-id="b7b3c-177">See the documentation for using [nuget.exe][].</span></span>

## <a name="installing-powershellget-on-a-disconnected-system"></a><span data-ttu-id="b7b3c-178">Installazione di PowerShellGet in un sistema disconnesso</span><span class="sxs-lookup"><span data-stu-id="b7b3c-178">Installing PowerShellGet on a disconnected system</span></span>

<span data-ttu-id="b7b3c-179">La distribuzione di PowerShellGet è difficile in ambienti che richiedono sistemi disconnessi da Internet.</span><span class="sxs-lookup"><span data-stu-id="b7b3c-179">Deploying PowerShellGet is difficult in environments that require systems to be disconnected from the internet.</span></span> <span data-ttu-id="b7b3c-180">PowerShellGet include un processo bootstrap che installa la versione più recente al primo utilizzo.</span><span class="sxs-lookup"><span data-stu-id="b7b3c-180">PowerShellGet has a bootstrap process that installs the latest version the first time it's used.</span></span> <span data-ttu-id="b7b3c-181">Il modulo OfflinePowerShellGetDeploy in PowerShell Gallery include cmdlet che supportano questo processo di bootstrap.</span><span class="sxs-lookup"><span data-stu-id="b7b3c-181">The OfflinePowerShellGetDeploy module in the PowerShell Gallery provides cmdlets that support this bootstrap process.</span></span>

<span data-ttu-id="b7b3c-182">Per eseguire il bootstrap di una distribuzione offline, è necessario:</span><span class="sxs-lookup"><span data-stu-id="b7b3c-182">To bootstrap an offline deployment, you need to:</span></span>

- <span data-ttu-id="b7b3c-183">Scaricare e installare OfflinePowerShellGetDeploy nel sistema connesso a Internet e nei sistemi disconnessi</span><span class="sxs-lookup"><span data-stu-id="b7b3c-183">Download and install the OfflinePowerShellGetDeploy your internet-connected system and your disconnected systems</span></span>
- <span data-ttu-id="b7b3c-184">Scaricare PowerShellGet e le relative dipendenze nel sistema connesso a Internet usando i cmdlet `Save-PowerShellGetForOffline`</span><span class="sxs-lookup"><span data-stu-id="b7b3c-184">Download PowerShellGet and its dependencies on the internet-connected system using the `Save-PowerShellGetForOffline` cmdlet</span></span>
- <span data-ttu-id="b7b3c-185">Copiare PowerShellGet e le relative dipendenze dal sistema connesso a Internet al sistema disconnesso</span><span class="sxs-lookup"><span data-stu-id="b7b3c-185">Copy PowerShellGet and its dependencies from the internet-connected system to the disconnected system</span></span>
- <span data-ttu-id="b7b3c-186">Usare `Install-PowerShellGetOffline` nel sistema disconnesso per posizionare PowerShellGet e le relative dipendenze nelle cartelle appropriate</span><span class="sxs-lookup"><span data-stu-id="b7b3c-186">Use the `Install-PowerShellGetOffline` on the disconnected system to place PowerShellGet and its dependencies into the proper folders</span></span>

<span data-ttu-id="b7b3c-187">I comandi seguenti usano `Save-PowerShellGetForOffline` per inserire tutti i componenti in una cartella `f:\OfflinePowerShellGet`</span><span class="sxs-lookup"><span data-stu-id="b7b3c-187">The following commands use `Save-PowerShellGetForOffline` to put all the components into a folder `f:\OfflinePowerShellGet`</span></span>

```powershell
# Requires -RunAsAdministrator
#Download the OfflinePowerShellGetDeploy to a location that can be accessed
# by both the connected and disconnected systems.
Save-Module -Name OfflinePowerShellGetDeploy -Path 'F:\' -Repository PSGallery
Import-Module F:\OfflinePowerShellGetDeploy

# Put PowerShellGet somewhere locally
Save-PowerShellGetForOffline -LocalFolder 'F:\OfflinePowerShellGet'
```

<span data-ttu-id="b7b3c-188">A questo punto, è necessario rendere il contenuto di `F:\OfflinePowerShellGet` disponibile per i sistemi disconnessi.</span><span class="sxs-lookup"><span data-stu-id="b7b3c-188">At this point, you must make the contents of `F:\OfflinePowerShellGet` available to your disconnected systems.</span></span> <span data-ttu-id="b7b3c-189">Eseguire il cmdlet `Install-PowerShellGetOffline` per installare PowerShellGet nel sistema disconnesso.</span><span class="sxs-lookup"><span data-stu-id="b7b3c-189">Run the `Install-PowerShellGetOffline` cmdlet to install PowerShellGet on the disconnected system.</span></span>

> [!NOTE]
> <span data-ttu-id="b7b3c-190">È importante non eseguire PowerShellGet nella sessione di PowerShell prima di eseguire questi comandi.</span><span class="sxs-lookup"><span data-stu-id="b7b3c-190">It is important that you do not run PowerShellGet in the PowerShell session before running these commands.</span></span> <span data-ttu-id="b7b3c-191">Una volta caricato PowerShellGet nella sessione, non sarà possibile aggiornare i componenti.</span><span class="sxs-lookup"><span data-stu-id="b7b3c-191">Once PowerShellGet is loaded into the session, the components cannot be updated.</span></span> <span data-ttu-id="b7b3c-192">Se si avvia PowerShellGet per errore, chiuderlo e riavviarlo.</span><span class="sxs-lookup"><span data-stu-id="b7b3c-192">If you do start PowerShellGet by mistake, exit and restart PowerShell.</span></span>

```powershell
Import-Module F:\OfflinePowerShellGetDeploy

Install-PowerShellGetOffline -LocalFolder 'F:\OfflinePowerShellGet'
```

<span data-ttu-id="b7b3c-193">Dopo aver eseguito questi comandi, sarà possibile pubblicare PowerShellGet nel repository locale.</span><span class="sxs-lookup"><span data-stu-id="b7b3c-193">After running these commands, you are ready to publish PowerShellGet to your local repository.</span></span>

```powershell
# Publish to a NuGet Server repository using my NuGetAPI key
Publish-Module -Path 'F:\OfflinePowershellGet' -Repository LocalPsRepo -NuGetApiKey 'oy2bi4avlkjolp6bme6azdyssn6ps3iu7ib2qpiudrtbji'

# Publish to a file share repo - the NuGet API key must be a non-blank string
Publish-Module -Path 'F:\OfflinePowerShellGet' -Repository LocalPsRepo -NuGetApiKey 'AnyStringWillDo'
```

> [!IMPORTANT]
> <span data-ttu-id="b7b3c-194">Per garantire la sicurezza, le chiavi API non devono essere hardcoded negli script.</span><span class="sxs-lookup"><span data-stu-id="b7b3c-194">To ensure security, API keys should not be hard-coded in scripts.</span></span> <span data-ttu-id="b7b3c-195">Usare un sistema di gestione delle chiavi sicuro.</span><span class="sxs-lookup"><span data-stu-id="b7b3c-195">Use a secure key management system.</span></span>

<!-- external links -->
[OfflinePowerShellGetDeploy]: https://www.powershellgallery.com/packages/OfflinePowerShellGetDeploy/0.1.1
[Nuget.Server]: /nuget/hosting-packages/nuget-server
[nuget.exe]: /nuget/tools/nuget-exe-cli-reference
