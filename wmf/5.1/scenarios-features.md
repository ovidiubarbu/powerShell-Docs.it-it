---
ms.date: 2017-06-12
author: JKeithB
ms.topic: reference
keywords: wmf,powershell,installazione
title: "Nuovi scenari e funzionalità in WMF 5.1"
ms.openlocfilehash: da3dfb2243c00e3faf637d3dbcb70016cfabb011
ms.sourcegitcommit: 99227f62dcf827354770eb2c3e95c5cf6a3118b4
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 03/15/2018
---
# <a name="new-scenarios-and-features-in-wmf-51"></a><span data-ttu-id="d7a4b-103">Nuovi scenari e funzionalità in WMF 5.1</span><span class="sxs-lookup"><span data-stu-id="d7a4b-103">New Scenarios and Features in WMF 5.1</span></span> #

> <span data-ttu-id="d7a4b-104">Nota: queste informazioni sono provvisorie e soggette a modifiche.</span><span class="sxs-lookup"><span data-stu-id="d7a4b-104">Note: This information is preliminary and subject to change.</span></span>

## <a name="powershell-editions"></a><span data-ttu-id="d7a4b-105">Edizioni di PowerShell</span><span class="sxs-lookup"><span data-stu-id="d7a4b-105">PowerShell Editions</span></span> ##
<span data-ttu-id="d7a4b-106">A partire dalla versione 5.1, PowerShell è disponibile in diverse edizioni che indicano diversi set di funzionalità e compatibilità della piattaforma.</span><span class="sxs-lookup"><span data-stu-id="d7a4b-106">Starting with version 5.1, PowerShell is available in different editions which denote varying feature sets and platform compatibility.</span></span>

- <span data-ttu-id="d7a4b-107">**Desktop Edition:** è basata su .NET Framework e fornisce compatibilità con script e moduli destinati a versioni di PowerShell che eseguono edizioni footprint complete di Windows, ad esempio Server Core e Windows Desktop.</span><span class="sxs-lookup"><span data-stu-id="d7a4b-107">**Desktop Edition:** Built on .NET Framework and provides compatibility with scripts and modules targeting versions of PowerShell running on full footprint editions of Windows such as Server Core and Windows Desktop.</span></span>
- <span data-ttu-id="d7a4b-108">**Core Edition:** è basata su .NET Core e fornisce compatibilità con script e moduli destinati a versioni di PowerShell che eseguono edizioni footprint ridotte di Windows, ad esempio Nano Server e Windows IoT.</span><span class="sxs-lookup"><span data-stu-id="d7a4b-108">**Core Edition:** Built on .NET Core and provides compatibility with scripts and modules targeting versions of PowerShell running on reduced footprint editions of Windows such as Nano Server and Windows IoT.</span></span>

<span data-ttu-id="d7a4b-109">**Altre informazioni sull'uso delle edizioni di PowerShell**</span><span class="sxs-lookup"><span data-stu-id="d7a4b-109">**Learn more about using PowerShell Editions**</span></span>
- [<span data-ttu-id="d7a4b-110">Determinare l'edizione di PowerShell in esecuzione</span><span class="sxs-lookup"><span data-stu-id="d7a4b-110">Determine running edition of PowerShell</span></span>]()
- [<span data-ttu-id="d7a4b-111">Dichiarare la compatibilità di un modulo con versioni specifiche di PowerShell</span><span class="sxs-lookup"><span data-stu-id="d7a4b-111">Declare a module's compatibility to specific PowerShell versions</span></span>]()
- [<span data-ttu-id="d7a4b-112">Filtrare i risultati di Get-Module in base a CompatiblePSEditions</span><span class="sxs-lookup"><span data-stu-id="d7a4b-112">Filter Get-Module results by CompatiblePSEditions</span></span>]()
- [<span data-ttu-id="d7a4b-113">Impedire l'esecuzione di script a meno che non vengano eseguiti in un'edizione compatibile di PowerShell</span><span class="sxs-lookup"><span data-stu-id="d7a4b-113">Prevent script execution unless run on a compatible edition of PowerShell</span></span>]()

## <a name="catalog-cmdlets"></a><span data-ttu-id="d7a4b-114">Cmdlet di catalogo</span><span class="sxs-lookup"><span data-stu-id="d7a4b-114">Catalog Cmdlets</span></span>  

<span data-ttu-id="d7a4b-115">Sono stati aggiunti due nuovi cmdlet nel modulo [Microsoft.PowerShell.Security](https://technet.microsoft.com/library/hh847877.aspx) che generano e convalidano i file di catalogo di Windows.</span><span class="sxs-lookup"><span data-stu-id="d7a4b-115">Two new cmdlets have been added in the [Microsoft.PowerShell.Security](https://technet.microsoft.com/library/hh847877.aspx) module; these generate and validate Windows catalog files.</span></span>  

###<a name="new-filecatalog"></a><span data-ttu-id="d7a4b-116">New-FileCatalog</span><span class="sxs-lookup"><span data-stu-id="d7a4b-116">New-FileCatalog</span></span> 
--------------------------------

<span data-ttu-id="d7a4b-117">New-FileCatalog crea un file di catalogo Windows per set di cartelle e file.</span><span class="sxs-lookup"><span data-stu-id="d7a4b-117">New-FileCatalog creates a Windows catalog file for set of folders and files.</span></span> <span data-ttu-id="d7a4b-118">Questo file di catalogo contiene gli hash per tutti i file nei percorsi specificati.</span><span class="sxs-lookup"><span data-stu-id="d7a4b-118">This catalog file contains hashes for all files in specified paths.</span></span> <span data-ttu-id="d7a4b-119">Gli utenti possono distribuire il gruppo di cartelle con il corrispondente file di catalogo che rappresenta le cartelle.</span><span class="sxs-lookup"><span data-stu-id="d7a4b-119">Users can distribute the set of folders along with corresponding catalog file representing those folders.</span></span> <span data-ttu-id="d7a4b-120">Queste informazioni sono utili per convalidare se sono state apportate modifiche alle cartelle dall'ora di creazione del catalogo.</span><span class="sxs-lookup"><span data-stu-id="d7a4b-120">This information is useful to validate whether any changes have been made to the folders since catalog creation time.</span></span>    

```powershell
New-FileCatalog [-CatalogFilePath] <string> [[-Path] <string[]>] [-CatalogVersion <int>] [-WhatIf] [-Confirm] [<CommonParameters>]
```
<span data-ttu-id="d7a4b-121">Sono supportate le versioni 1 e 2 del catalogo.</span><span class="sxs-lookup"><span data-stu-id="d7a4b-121">Catalog versions 1 and 2 are supported.</span></span> <span data-ttu-id="d7a4b-122">La versione 1 usa l'algoritmo di hash SHA1 per creare hash di file; la versione 2 usa SHA256.</span><span class="sxs-lookup"><span data-stu-id="d7a4b-122">Version 1 uses the SHA1 hashing algorithm to create file hashes; version 2 uses SHA256.</span></span> <span data-ttu-id="d7a4b-123">La versione 2 del catalogo non è supportata in *Windows Server 2008 R2* e in *Windows 7*.</span><span class="sxs-lookup"><span data-stu-id="d7a4b-123">Catalog version 2 is not supported on *Windows Server 2008 R2* or *Windows 7*.</span></span> <span data-ttu-id="d7a4b-124">È necessario usare la versione 2 del catalogo su *Windows 8*, *Windows Server 2012* e sistemi operativi successivi.</span><span class="sxs-lookup"><span data-stu-id="d7a4b-124">You should use catalog version 2 on *Windows 8*, *Windows Server 2012*, and later operating systems.</span></span>  

![](../images/NewFileCatalog.jpg)

<span data-ttu-id="d7a4b-125">Questa operazione crea il file di catalogo.</span><span class="sxs-lookup"><span data-stu-id="d7a4b-125">This creates the catalog file.</span></span> 

![](../images/CatalogFile1.jpg)  

![](../images/CatalogFile2.jpg) 

<span data-ttu-id="d7a4b-126">Per verificare l'integrità dei file di catalogo (Pester.cat nell'esempio precedente), accedere tramite il cmdlet [Set-AuthenticodeSignature](https://technet.microsoft.com/library/hh849819.aspx).</span><span class="sxs-lookup"><span data-stu-id="d7a4b-126">To verify the integrity of catalog file (Pester.cat in above example), sign it using [Set-AuthenticodeSignature](https://technet.microsoft.com/library/hh849819.aspx) cmdlet.</span></span>   


###<a name="test-filecatalog"></a><span data-ttu-id="d7a4b-127">Test-FileCatalog</span><span class="sxs-lookup"><span data-stu-id="d7a4b-127">Test-FileCatalog</span></span> 
--------------------------------

<span data-ttu-id="d7a4b-128">Test-FileCatalog convalida il catalogo che rappresenta un set di cartelle.</span><span class="sxs-lookup"><span data-stu-id="d7a4b-128">Test-FileCatalog validates the catalog representing a set of folders.</span></span> 

```powershell
Test-FileCatalog [-CatalogFilePath] <string> [[-Path] <string[]>] [-Detailed] [-FilesToSkip <string[]>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

![](../images/TestFileCatalog.jpg)

<span data-ttu-id="d7a4b-129">Questo cmdlet confronta tutti gli hash di file e i relativi percorsi trovati nel *catalogo* con altri sul *disco*.</span><span class="sxs-lookup"><span data-stu-id="d7a4b-129">This cmdlet compares all the files hashes and their relative paths found in *catalog* with ones on *disk*.</span></span> <span data-ttu-id="d7a4b-130">Se rileva eventuali mancate corrispondenze tra i percorsi e gli hash di file restituisce lo stato *ValidationFailed*.</span><span class="sxs-lookup"><span data-stu-id="d7a4b-130">If it detects any mismatch between file hashes and paths it returns the status as *ValidationFailed*.</span></span> <span data-ttu-id="d7a4b-131">Gli utenti possono recuperare tutte queste informazioni usando il parametro *-Detailed*.</span><span class="sxs-lookup"><span data-stu-id="d7a4b-131">Users can retrieve all this information by using the *-Detailed* parameter.</span></span> <span data-ttu-id="d7a4b-132">Visualizza inoltre lo stato di accesso al catalogo nella proprietà *Signature* che è equivalente alla chiamata del cmdlet [Get-AuthenticodeSignature](https://technet.microsoft.com/library/hh849805.aspx) nel file di catalogo.</span><span class="sxs-lookup"><span data-stu-id="d7a4b-132">It also displays signing status of catalog in *Signature* property which is equivalent to calling [Get-AuthenticodeSignature](https://technet.microsoft.com/library/hh849805.aspx) cmdlet on the catalog file.</span></span> <span data-ttu-id="d7a4b-133">Gli utenti possono inoltre ignorare alcuni file durante la convalida usando il parametro *- FilesToSkip*.</span><span class="sxs-lookup"><span data-stu-id="d7a4b-133">Users can also skip any file during validation by using the *-FilesToSkip* parameter.</span></span> 


## <a name="module-analysis-cache"></a><span data-ttu-id="d7a4b-134">Modulo Analysis Cache</span><span class="sxs-lookup"><span data-stu-id="d7a4b-134">Module Analysis Cache</span></span> ##
<span data-ttu-id="d7a4b-135">A partire da WMF 5.1, PowerShell fornisce il controllo sul file che viene usato per memorizzare nella cache i dati relativi a un modulo, ad esempio i comandi esportati.</span><span class="sxs-lookup"><span data-stu-id="d7a4b-135">Starting with WMF 5.1, PowerShell provides control over the file that is used to cache data about a module, such as the commands it exports.</span></span>

<span data-ttu-id="d7a4b-136">Per impostazione predefinita, questa cache è archiviata nel file `${env:LOCALAPPDATA}\Microsoft\Windows\PowerShell\ModuleAnalysisCache`.</span><span class="sxs-lookup"><span data-stu-id="d7a4b-136">By default, this cache is stored in the file `${env:LOCALAPPDATA}\Microsoft\Windows\PowerShell\ModuleAnalysisCache`.</span></span>
<span data-ttu-id="d7a4b-137">La cache viene in genere letta all'avvio durante la ricerca di un comando e viene scritta in un thread in background ad un certo punto dopo l'importazione di un modulo.</span><span class="sxs-lookup"><span data-stu-id="d7a4b-137">The cache is typically read at startup while searching for a command and is written on a background thread sometime after a module is imported.</span></span>

<span data-ttu-id="d7a4b-138">Per modificare il percorso predefinito della cache, impostare la variabile di ambiente `$env:PSModuleAnalysisCachePath` prima di avviare PowerShell.</span><span class="sxs-lookup"><span data-stu-id="d7a4b-138">To change the default location of the cache, set the `$env:PSModuleAnalysisCachePath` environment variable before starting PowerShell.</span></span> <span data-ttu-id="d7a4b-139">Le modifiche apportate a questa variabile di ambiente influiranno solo sui processi figlio.</span><span class="sxs-lookup"><span data-stu-id="d7a4b-139">Changes to this environment variable will only affect children processes.</span></span> <span data-ttu-id="d7a4b-140">Il valore deve denominare un percorso completo (nome di file incluso) per il quale PowerShell dispone dell'autorizzazione per creare e scrivere file.</span><span class="sxs-lookup"><span data-stu-id="d7a4b-140">The value should name a full path (including filename) that PowerShell has permission to create and write files.</span></span> <span data-ttu-id="d7a4b-141">Per disabilitare la cache del file, impostare questo valore su un percorso non valido, ad esempio:</span><span class="sxs-lookup"><span data-stu-id="d7a4b-141">To disable the file cache, set this value to an invalid location, for example:</span></span>

```powershell
$env:PSModuleAnalysisCachePath = 'nul'
```

<span data-ttu-id="d7a4b-142">Questo imposta il percorso su un dispositivo non valido.</span><span class="sxs-lookup"><span data-stu-id="d7a4b-142">This sets the path to an invalid device.</span></span> <span data-ttu-id="d7a4b-143">Se PowerShell non riesce a scrivere nel percorso, non verrà restituito alcun errore. Sarà tuttavia possibile visualizzare una segnalazione errori mediante un'utilità di traccia:</span><span class="sxs-lookup"><span data-stu-id="d7a4b-143">If PowerShell can't write to the path, no error is returned, but you can see error reporting by using a tracer:</span></span>

```powershell
Trace-Command -PSHost -Name Modules -Expression { Import-Module Microsoft.PowerShell.Management -Force }
```

<span data-ttu-id="d7a4b-144">Quando si scrive nella cache, PowerShell controllerà i moduli non più disponibili per evitare di aumentare inutilmente le dimensioni della cache.</span><span class="sxs-lookup"><span data-stu-id="d7a4b-144">When writing out the cache, PowerShell will check for modules that no longer exist to avoid an unnecessarily large cache.</span></span>
<span data-ttu-id="d7a4b-145">Talvolta questi controlli non sono consigliabili. In questo caso, è possibile disattivarli impostando:</span><span class="sxs-lookup"><span data-stu-id="d7a4b-145">Sometimes these checks are not desirable, in which case you can turn them off by setting:</span></span>

```powershell
$env:PSDisableModuleAnalysisCacheCleanup = 1
```

<span data-ttu-id="d7a4b-146">L'impostazione di questa variabile di ambiente avrà effetto immediato nel processo corrente.</span><span class="sxs-lookup"><span data-stu-id="d7a4b-146">Setting this environment variable will take effect immediately in the current process.</span></span>

##<a name="specifying-module-version"></a><span data-ttu-id="d7a4b-147">Specifica della versione del modulo</span><span class="sxs-lookup"><span data-stu-id="d7a4b-147">Specifying module version</span></span>

<span data-ttu-id="d7a4b-148">In WMF 5.1 `using module` si comporta esattamente come altre costruzioni correlate ai moduli di PowerShell.</span><span class="sxs-lookup"><span data-stu-id="d7a4b-148">In WMF 5.1, `using module` behaves the same way as other module-related constructions in PowerShell.</span></span> <span data-ttu-id="d7a4b-149">In precedenza, non era possibile specificare una versione particolare del modulo. Se erano presenti più versioni, veniva restituito un errore.</span><span class="sxs-lookup"><span data-stu-id="d7a4b-149">Previously, you had no way to specify a particular module version; if there were multiple versions present, this resulted in an error.</span></span>


<span data-ttu-id="d7a4b-150">In WMF 5.1:</span><span class="sxs-lookup"><span data-stu-id="d7a4b-150">In WMF 5.1:</span></span>

* <span data-ttu-id="d7a4b-151">È possibile usare il [costruttore ModuleSpecification (Hashtable)](https://msdn.microsoft.com/library/jj136290).</span><span class="sxs-lookup"><span data-stu-id="d7a4b-151">You can use [ModuleSpecification Constructor (Hashtable)](https://msdn.microsoft.com/library/jj136290).</span></span> <span data-ttu-id="d7a4b-152">Questa tabella hash ha lo stesso formato di `Get-Module -FullyQualifiedName`.</span><span class="sxs-lookup"><span data-stu-id="d7a4b-152">This hash table has the same format as `Get-Module -FullyQualifiedName`.</span></span>

<span data-ttu-id="d7a4b-153">**Esempio:** `using module @{ModuleName = 'PSReadLine'; RequiredVersion = '1.1'}`</span><span class="sxs-lookup"><span data-stu-id="d7a4b-153">**Example:** `using module @{ModuleName = 'PSReadLine'; RequiredVersion = '1.1'}`</span></span>

* <span data-ttu-id="d7a4b-154">Se sono presenti più versioni del modulo, PowerShell usa la **stessa logica di risoluzione** di `Import-Module` e non restituisce un errore. Comportamento analogo a `Import-Module` e `Import-DscResource`.</span><span class="sxs-lookup"><span data-stu-id="d7a4b-154">If there are multiple versions of the module, PowerShell uses the **same resolution logic** as `Import-Module` and doesn't return an error--the same behavior as `Import-Module` and `Import-DscResource`.</span></span>


##<a name="improvements-to-pester"></a><span data-ttu-id="d7a4b-155">Miglioramenti a Pester</span><span class="sxs-lookup"><span data-stu-id="d7a4b-155">Improvements to Pester</span></span>
<span data-ttu-id="d7a4b-156">In WMF 5.1 la versione di Pester acclusa a PowerShell è stata aggiornata dalla versione 3.3.5 alla 3.4.0 con l'aggiunta del commit https://github.com/pester/Pester/pull/484/commits/3854ae8a1f215b39697ac6c2607baf42257b102e, che migliora il comportamento di Pester su Nano Server.</span><span class="sxs-lookup"><span data-stu-id="d7a4b-156">In WMF 5.1, the version of Pester that ships with PowerShell has been updated from 3.3.5 to 3.4.0, with the addition of commit https://github.com/pester/Pester/pull/484/commits/3854ae8a1f215b39697ac6c2607baf42257b102e, which enables better behavior for Pester on Nano Server.</span></span> 

<span data-ttu-id="d7a4b-157">È possibile vedere quali modifiche sono state apportate nelle versioni dalla 3.3.5 alla 3.4.0 esaminando il file ChangeLog.md all'indirizzo https://github.com/pester/Pester/blob/master/CHANGELOG.md</span><span class="sxs-lookup"><span data-stu-id="d7a4b-157">You can review the changes in versions 3.3.5 to 3.4.0 by inspecting the ChangeLog.md file at: https://github.com/pester/Pester/blob/master/CHANGELOG.md</span></span>

