---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: wmf,powershell,installazione
title: Note sulla versione per WMF 5.x
ms.openlocfilehash: 3fc712dbcbe184c60ae248b260c8f6800f111fdd
ms.sourcegitcommit: 6545c60578f7745be015111052fd7769f8289296
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/22/2020
ms.locfileid: "79402358"
---
# <a name="windows-management-framework-wmf-5x-release-notes"></a><span data-ttu-id="f44a8-103">Note sulla versione di Windows Management Framework (WMF) 5.x</span><span class="sxs-lookup"><span data-stu-id="f44a8-103">Windows Management Framework (WMF) 5.x Release Notes</span></span>

## <a name="wmf-50-changes"></a><span data-ttu-id="f44a8-104">Modifiche di WMF 5.0</span><span class="sxs-lookup"><span data-stu-id="f44a8-104">WMF 5.0 Changes</span></span>

- <span data-ttu-id="f44a8-105">In PowerShell 5.0 è stato aggiunto un nuovo flusso di **informazioni** strutturato</span><span class="sxs-lookup"><span data-stu-id="f44a8-105">PowerShell 5.0 adds a new structured **Information** stream</span></span>
- <span data-ttu-id="f44a8-106">I miglioramenti di DSC includono quattro nuove risorse DSC:</span><span class="sxs-lookup"><span data-stu-id="f44a8-106">Improvements to DSC including four new DSC resources:</span></span>
  - <span data-ttu-id="f44a8-107">WindowsFeatureSet</span><span class="sxs-lookup"><span data-stu-id="f44a8-107">WindowsFeatureSet</span></span>
  - <span data-ttu-id="f44a8-108">WindowsOptionalFeatureSet</span><span class="sxs-lookup"><span data-stu-id="f44a8-108">WindowsOptionalFeatureSet</span></span>
  - <span data-ttu-id="f44a8-109">ServiceSet</span><span class="sxs-lookup"><span data-stu-id="f44a8-109">ServiceSet</span></span>
  - <span data-ttu-id="f44a8-110">ProcessSet</span><span class="sxs-lookup"><span data-stu-id="f44a8-110">ProcessSet</span></span>
- <span data-ttu-id="f44a8-111">Aggiunta della funzionalità JEA (Just Enough Administration) per consentire l'amministrazione basata su ruoli tramite la comunicazione remota di PowerShell</span><span class="sxs-lookup"><span data-stu-id="f44a8-111">Added Just Enough Administration to enable role-based administration through PowerShell remoting</span></span>
- <span data-ttu-id="f44a8-112">PowerShell 5.0 estende il linguaggio in modo da includere le enumerazioni e le classi definiti dall'utente</span><span class="sxs-lookup"><span data-stu-id="f44a8-112">PowerShell 5.0 extends the language to include user-defined classes and enumerations</span></span>
- <span data-ttu-id="f44a8-113">Miglioramento delle funzionalità di debug in PowerShell ISE e aggiunta del debug remoto</span><span class="sxs-lookup"><span data-stu-id="f44a8-113">Improved debugging features in PowerShell ISE and added remote debugging</span></span>
- <span data-ttu-id="f44a8-114">Aggiunta dei moduli PowerShellGet e PackageManagement</span><span class="sxs-lookup"><span data-stu-id="f44a8-114">Added the PowerShellGet and PackageManagement modules</span></span>
- <span data-ttu-id="f44a8-115">Miglioramento della registrazione e delle trascrizioni per gli script di PowerShell</span><span class="sxs-lookup"><span data-stu-id="f44a8-115">Enhanced PowerShell script logging and transcripts</span></span>
- <span data-ttu-id="f44a8-116">Aggiunta di cmdlet CMS (Cryptographic Message Syntax)</span><span class="sxs-lookup"><span data-stu-id="f44a8-116">Add Cryptographic Message Syntax cmdlets</span></span>
- <span data-ttu-id="f44a8-117">WMF 5.0 include il modulo NetworkSwitchManager per Windows</span><span class="sxs-lookup"><span data-stu-id="f44a8-117">WMF 5.0 includes the NetworkSwitchManager module for Windows</span></span>
- <span data-ttu-id="f44a8-118">Aggiunta del modulo Microsoft.PowerShell.ODataUtils</span><span class="sxs-lookup"><span data-stu-id="f44a8-118">Added the Microsoft.PowerShell.ODataUtils module</span></span>
- <span data-ttu-id="f44a8-119">Aggiunta del supporto per Registrazione inventario software (SIL)</span><span class="sxs-lookup"><span data-stu-id="f44a8-119">Added support for Software Inventory Logging (SIL)</span></span>
- <span data-ttu-id="f44a8-120">Vari cmdlet nuovi o aggiornati in risposta alle richieste e alle segnalazioni di problemi degli utenti</span><span class="sxs-lookup"><span data-stu-id="f44a8-120">Sever new or update cmdlets in response to user requests and issues</span></span>

## <a name="wmf-51-changes"></a><span data-ttu-id="f44a8-121">Modifiche di WMF 5.1</span><span class="sxs-lookup"><span data-stu-id="f44a8-121">WMF 5.1 Changes</span></span>

<span data-ttu-id="f44a8-122">WMF 5.1 include i componenti PowerShell, WMI, WinRM e Registrazione inventario software (SIL) rilasciati con Windows Server 2016.</span><span class="sxs-lookup"><span data-stu-id="f44a8-122">WMF 5.1 includes the PowerShell, WMI, WinRM, and Software Inventory Logging (SIL) components that were released with Windows Server 2016.</span></span> <span data-ttu-id="f44a8-123">WMF 5.1 può essere installato in Windows 7, Windows 8.1, Windows Server 2008 R2, 2012 e 2012 R2 e offre vari miglioramenti rispetto a WMF 5.0, tra cui:</span><span class="sxs-lookup"><span data-stu-id="f44a8-123">WMF 5.1 can be installed on Windows 7, Windows 8.1, Windows Server 2008 R2, 2012, and 2012 R2, and provides several improvements over WMF 5.0 including:</span></span>

- <span data-ttu-id="f44a8-124">Nuovi cmdlet</span><span class="sxs-lookup"><span data-stu-id="f44a8-124">New cmdlets</span></span>
- <span data-ttu-id="f44a8-125">I miglioramenti apportati a PowerShellGet includono l'applicazione di moduli firmati e l'installazione di moduli JEA</span><span class="sxs-lookup"><span data-stu-id="f44a8-125">PowerShellGet improvements include enforcing signed modules, and installing JEA modules</span></span>
- <span data-ttu-id="f44a8-126">È stato aggiunto il supporto di PackageManagement per i contenitori, l'installazione di CBS, l'installazione basata su EXE e i pacchetti CAB</span><span class="sxs-lookup"><span data-stu-id="f44a8-126">PackageManagement added support for Containers, CBS Setup, EXE-based setup, CAB packages</span></span>
- <span data-ttu-id="f44a8-127">Miglioramenti del debug per le classi DSC e PowerShell</span><span class="sxs-lookup"><span data-stu-id="f44a8-127">Debugging improvements for DSC and PowerShell classes</span></span>
- <span data-ttu-id="f44a8-128">Miglioramenti relativi alla sicurezza, incluso quando si usano i cmdlet PowerShellGet e quando si applicano i moduli firmati da catalogo provenienti dal server di pull</span><span class="sxs-lookup"><span data-stu-id="f44a8-128">Security enhancements including enforcement of catalog-signed modules coming from the Pull Server and when using PowerShellGet cmdlets</span></span>
- <span data-ttu-id="f44a8-129">Risposte ad alcune richieste o problemi segnalati da utenti</span><span class="sxs-lookup"><span data-stu-id="f44a8-129">Responses to a number of user requests and issues</span></span>

> [!IMPORTANT]
> <span data-ttu-id="f44a8-130">Prima di installare WMF 5.1 in Windows Server 2008 o Windows 7, verificare che WMF 3.0 non sia installato.</span><span class="sxs-lookup"><span data-stu-id="f44a8-130">Before you install WMF 5.1 on Windows Server 2008 or Windows 7, confirm that WMF 3.0 isn't installed.</span></span> <span data-ttu-id="f44a8-131">Per altre informazioni, vedere [Prerequisiti di WMF 5.1 per Windows Server 2008 R2 SP1 e Windows 7 SP1](../setup/install-configure.md#wmf-51-prerequisites-for-windows-server-2008-r2-sp1-and-windows-7-sp1).</span><span class="sxs-lookup"><span data-stu-id="f44a8-131">For more information, see [WMF 5.1 Prerequisites for Windows Server 2008 R2 SP1 and Windows 7 SP1](../setup/install-configure.md#wmf-51-prerequisites-for-windows-server-2008-r2-sp1-and-windows-7-sp1).</span></span>

## <a name="powershell-editions"></a><span data-ttu-id="f44a8-132">Edizioni di PowerShell</span><span class="sxs-lookup"><span data-stu-id="f44a8-132">PowerShell Editions</span></span>

<span data-ttu-id="f44a8-133">A partire dalla versione 5.1, PowerShell è disponibile in diverse edizioni che indicano vari set di funzionalità e compatibilità della piattaforma.</span><span class="sxs-lookup"><span data-stu-id="f44a8-133">Starting with version 5.1, PowerShell is available in different editions that denote varying feature sets and platform compatibility.</span></span>

- <span data-ttu-id="f44a8-134">**Desktop Edition:** è basata su .NET Framework e fornisce compatibilità con script e moduli destinati a versioni di PowerShell che eseguono edizioni footprint complete di Windows, ad esempio Server Core e Windows Desktop.</span><span class="sxs-lookup"><span data-stu-id="f44a8-134">**Desktop Edition:** Built on .NET Framework and provides compatibility with scripts and modules targeting versions of PowerShell running on full footprint editions of Windows such as Server Core and Windows Desktop.</span></span>
- <span data-ttu-id="f44a8-135">**Core Edition:** è basata su .NET Core e fornisce compatibilità con script e moduli destinati a versioni di PowerShell che eseguono edizioni footprint ridotte di Windows, ad esempio Nano Server e Windows IoT.</span><span class="sxs-lookup"><span data-stu-id="f44a8-135">**Core Edition:** Built on .NET Core and provides compatibility with scripts and modules targeting versions of PowerShell running on reduced footprint editions of Windows such as Nano Server and Windows IoT.</span></span>

### <a name="learn-more-about-using-powershell-editions"></a><span data-ttu-id="f44a8-136">Altre informazioni sull'uso delle edizioni di PowerShell</span><span class="sxs-lookup"><span data-stu-id="f44a8-136">Learn more about using PowerShell Editions</span></span>

- [<span data-ttu-id="f44a8-137">Determinare l'edizione di PowerShell in esecuzione con $PSVersionTable</span><span class="sxs-lookup"><span data-stu-id="f44a8-137">Determine running edition of PowerShell using $PSVersionTable</span></span>](/powershell/module/microsoft.powershell.core/about/about_automatic_variables)
- [<span data-ttu-id="f44a8-138">Filtrare i risultati di Get-Module in base a CompatiblePSEditions con il parametro PSEdition</span><span class="sxs-lookup"><span data-stu-id="f44a8-138">Filter Get-Module results by CompatiblePSEditions using PSEdition parameter</span></span>](/powershell/module/microsoft.powershell.core/get-module)
- [<span data-ttu-id="f44a8-139">Impedire l'esecuzione di script a meno che non vengano eseguiti in un'edizione compatibile di PowerShell</span><span class="sxs-lookup"><span data-stu-id="f44a8-139">Prevent script execution unless run on a compatible edition of PowerShell</span></span>](/powershell/scripting/gallery/concepts/script-psedition-support)
- [<span data-ttu-id="f44a8-140">Dichiarare la compatibilità di un modulo con versioni specifiche di PowerShell</span><span class="sxs-lookup"><span data-stu-id="f44a8-140">Declare a module's compatibility to specific PowerShell versions</span></span>](/powershell/scripting/gallery/concepts/module-psedition-support)

## <a name="module-analysis-cache"></a><span data-ttu-id="f44a8-141">Modulo Analysis Cache</span><span class="sxs-lookup"><span data-stu-id="f44a8-141">Module Analysis Cache</span></span>

<span data-ttu-id="f44a8-142">A partire da WMF 5.1, PowerShell fornisce il controllo sul file che viene usato per memorizzare nella cache i dati relativi a un modulo, ad esempio i comandi esportati.</span><span class="sxs-lookup"><span data-stu-id="f44a8-142">Starting with WMF 5.1, PowerShell provides control over the file that is used to cache data about a module, such as the commands it exports.</span></span>

<span data-ttu-id="f44a8-143">Per impostazione predefinita, questa cache è archiviata nel file `${env:LOCALAPPDATA}\Microsoft\Windows\PowerShell\ModuleAnalysisCache`.</span><span class="sxs-lookup"><span data-stu-id="f44a8-143">By default, this cache is stored in the file `${env:LOCALAPPDATA}\Microsoft\Windows\PowerShell\ModuleAnalysisCache`.</span></span> <span data-ttu-id="f44a8-144">La cache viene in genere letta all'avvio durante la ricerca di un comando e viene scritta in un thread in background ad un certo punto dopo l'importazione di un modulo.</span><span class="sxs-lookup"><span data-stu-id="f44a8-144">The cache is typically read at startup while searching for a command and is written on a background thread sometime after a module is imported.</span></span>

<span data-ttu-id="f44a8-145">Per modificare il percorso predefinito della cache, impostare la variabile di ambiente `$env:PSModuleAnalysisCachePath` prima di avviare PowerShell.</span><span class="sxs-lookup"><span data-stu-id="f44a8-145">To change the default location of the cache, set the `$env:PSModuleAnalysisCachePath` environment variable before starting PowerShell.</span></span> <span data-ttu-id="f44a8-146">Le modifiche apportate a questa variabile di ambiente influiranno solo sui processi figlio.</span><span class="sxs-lookup"><span data-stu-id="f44a8-146">Changes to this environment variable will only affect children processes.</span></span> <span data-ttu-id="f44a8-147">Il valore deve denominare un percorso completo (nome di file incluso) per il quale PowerShell dispone dell'autorizzazione per creare e scrivere file.</span><span class="sxs-lookup"><span data-stu-id="f44a8-147">The value should name a full path (including filename) that PowerShell has permission to create and write files.</span></span> <span data-ttu-id="f44a8-148">Per disabilitare la cache del file, impostare questo valore su un percorso non valido, ad esempio:</span><span class="sxs-lookup"><span data-stu-id="f44a8-148">To disable the file cache, set this value to an invalid location, for example:</span></span>

```powershell
$env:PSModuleAnalysisCachePath = 'nul'
```

<span data-ttu-id="f44a8-149">Questo imposta il percorso su un dispositivo non valido.</span><span class="sxs-lookup"><span data-stu-id="f44a8-149">This sets the path to an invalid device.</span></span> <span data-ttu-id="f44a8-150">Se PowerShell non riesce a scrivere nel percorso, non verrà restituito alcun errore. Sarà tuttavia possibile visualizzare una segnalazione errori mediante un'utilità di traccia:</span><span class="sxs-lookup"><span data-stu-id="f44a8-150">If PowerShell can't write to the path, no error is returned, but you can see error reporting by using a tracer:</span></span>

```powershell
Trace-Command -PSHost -Name Modules -Expression { Import-Module Microsoft.PowerShell.Management -Force }
```

<span data-ttu-id="f44a8-151">Quando si scrive nella cache, PowerShell controllerà i moduli non più disponibili per evitare di aumentare inutilmente le dimensioni della cache.</span><span class="sxs-lookup"><span data-stu-id="f44a8-151">When writing out the cache, PowerShell will check for modules that no longer exist to avoid an unnecessarily large cache.</span></span> <span data-ttu-id="f44a8-152">Talvolta questi controlli non sono consigliabili. In questo caso, è possibile disattivarli impostando:</span><span class="sxs-lookup"><span data-stu-id="f44a8-152">Sometimes these checks are not desirable, in which case you can turn them off by setting:</span></span>

```powershell
$env:PSDisableModuleAnalysisCacheCleanup = 1
```

<span data-ttu-id="f44a8-153">L'impostazione di questa variabile di ambiente avrà effetto immediato nel processo corrente.</span><span class="sxs-lookup"><span data-stu-id="f44a8-153">Setting this environment variable will take effect immediately in the current process.</span></span>

## <a name="specifying-module-version"></a><span data-ttu-id="f44a8-154">Specifica della versione del modulo</span><span class="sxs-lookup"><span data-stu-id="f44a8-154">Specifying module version</span></span>

<span data-ttu-id="f44a8-155">In WMF 5.1 `using module` si comporta esattamente come altre costruzioni correlate ai moduli di PowerShell.</span><span class="sxs-lookup"><span data-stu-id="f44a8-155">In WMF 5.1, `using module` behaves the same way as other module-related constructions in PowerShell.</span></span>
<span data-ttu-id="f44a8-156">In precedenza, non era possibile specificare una versione particolare del modulo. Se erano presenti più versioni, veniva restituito un errore.</span><span class="sxs-lookup"><span data-stu-id="f44a8-156">Previously, you had no way to specify a particular module version; if there were multiple versions present, this resulted in an error.</span></span>

<span data-ttu-id="f44a8-157">In WMF 5.1:</span><span class="sxs-lookup"><span data-stu-id="f44a8-157">In WMF 5.1:</span></span>

- <span data-ttu-id="f44a8-158">È possibile usare il [costruttore ModuleSpecification (Hashtable)](/dotnet/api/microsoft.powershell.commands.modulespecification.-ctor?view=powershellsdk-1.1.0#Microsoft_PowerShell_Commands_ModuleSpecification__ctor_System_Collections_Hashtable_).</span><span class="sxs-lookup"><span data-stu-id="f44a8-158">You can use [ModuleSpecification Constructor (Hashtable)](/dotnet/api/microsoft.powershell.commands.modulespecification.-ctor?view=powershellsdk-1.1.0#Microsoft_PowerShell_Commands_ModuleSpecification__ctor_System_Collections_Hashtable_).</span></span>

  <span data-ttu-id="f44a8-159">Questa tabella hash ha lo stesso formato di `Get-Module -FullyQualifiedName`.</span><span class="sxs-lookup"><span data-stu-id="f44a8-159">This hash table has the same format as `Get-Module -FullyQualifiedName`.</span></span>

  <span data-ttu-id="f44a8-160">**Esempio:** `using module @{ModuleName = 'PSReadLine'; RequiredVersion = '1.1'}`</span><span class="sxs-lookup"><span data-stu-id="f44a8-160">**Example:** `using module @{ModuleName = 'PSReadLine'; RequiredVersion = '1.1'}`</span></span>

- <span data-ttu-id="f44a8-161">Se sono presenti più versioni del modulo, PowerShell usa la **stessa logica di risoluzione** di `Import-Module` e non restituisce un errore. Comportamento analogo a `Import-Module` e `Import-DscResource`.</span><span class="sxs-lookup"><span data-stu-id="f44a8-161">If there are multiple versions of the module, PowerShell uses the **same resolution logic** as `Import-Module` and doesn't return an error--the same behavior as `Import-Module` and `Import-DscResource`.</span></span>

## <a name="improvements-to-pester"></a><span data-ttu-id="f44a8-162">Miglioramenti a Pester</span><span class="sxs-lookup"><span data-stu-id="f44a8-162">Improvements to Pester</span></span>

<span data-ttu-id="f44a8-163">In WMF 5.1 la versione di Pester fornita con PowerShell è stata aggiornata dalla versione 3.3.5 alla 3.4.0.</span><span class="sxs-lookup"><span data-stu-id="f44a8-163">In WMF 5.1, the version of Pester that ships with PowerShell has been updated from 3.3.5 to 3.4.0.</span></span>
<span data-ttu-id="f44a8-164">Questo aggiornamento migliora il comportamento di Pester in Nano Server.</span><span class="sxs-lookup"><span data-stu-id="f44a8-164">This update enables better behavior for Pester on Nano Server.</span></span>

<span data-ttu-id="f44a8-165">È possibile vedere le modifiche apportate per Pester esaminando il file [ChangeLog](https://github.com/pester/Pester/blob/master/CHANGELOG.md) nel repository di GitHub.</span><span class="sxs-lookup"><span data-stu-id="f44a8-165">You can review the changes in Pest by inspecting the [ChangeLog](https://github.com/pester/Pester/blob/master/CHANGELOG.md) in the GitHub repository.</span></span>
