---
title: Migrazione da Windows PowerShell 5.1 a PowerShell 7
description: Aggiornamento da PowerShell 5.1 a PowerShell 7 per le piattaforme Windows.
ms.date: 03/25/2020
ms.openlocfilehash: 8f19297bdb4825f3bbd50544dc5737997e3c83e3
ms.sourcegitcommit: 6545c60578f7745be015111052fd7769f8289296
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/22/2020
ms.locfileid: "81440493"
---
# <a name="migrating-from-windows-powershell-51-to-powershell-7"></a><span data-ttu-id="0b4aa-103">Migrazione da Windows PowerShell 5.1 a PowerShell 7</span><span class="sxs-lookup"><span data-stu-id="0b4aa-103">Migrating from Windows PowerShell 5.1 to PowerShell 7</span></span>

<span data-ttu-id="0b4aa-104">PowerShell 7 è progettato per ambienti cloud, locali e ibridi e include miglioramenti e [nuove funzionalità](What-s-New-in-PowerShell-70.md).</span><span class="sxs-lookup"><span data-stu-id="0b4aa-104">Designed for cloud, on-premises, and hybrid environments, PowerShell 7 is packed with enhancements and [new features](What-s-New-in-PowerShell-70.md).</span></span>

- <span data-ttu-id="0b4aa-105">Installazione ed esecuzione side-by-side con Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="0b4aa-105">Installs and runs side-by-side with Windows PowerShell</span></span>
- <span data-ttu-id="0b4aa-106">Compatibilità migliorata con i moduli di Windows PowerShell esistenti</span><span class="sxs-lookup"><span data-stu-id="0b4aa-106">Improved compatibility with existing Windows PowerShell modules</span></span>
- <span data-ttu-id="0b4aa-107">Nuove funzionalità di linguaggio, come operatori ternari e `ForEach-Object -Parallel`</span><span class="sxs-lookup"><span data-stu-id="0b4aa-107">New language features, like ternary operators and `ForEach-Object -Parallel`</span></span>
- <span data-ttu-id="0b4aa-108">prestazioni migliorate</span><span class="sxs-lookup"><span data-stu-id="0b4aa-108">Improved performance</span></span>
- <span data-ttu-id="0b4aa-109">Comunicazione remota basata su SSH</span><span class="sxs-lookup"><span data-stu-id="0b4aa-109">SSH-based remoting</span></span>
- <span data-ttu-id="0b4aa-110">Interoperabilità tra piattaforme</span><span class="sxs-lookup"><span data-stu-id="0b4aa-110">Cross-platform interoperability</span></span>
- <span data-ttu-id="0b4aa-111">Supporto per i contenitori Docker</span><span class="sxs-lookup"><span data-stu-id="0b4aa-111">Support for Docker containers</span></span>

<span data-ttu-id="0b4aa-112">PowerShell 7 viene eseguito side-by-side con Windows PowerShell in modo da consentire l'esecuzione semplificata di test e confronti tra le edizioni prima della distribuzione.</span><span class="sxs-lookup"><span data-stu-id="0b4aa-112">PowerShell 7 works side-by-side with Windows PowerShell letting you easily test and compare between editions before deployment.</span></span> <span data-ttu-id="0b4aa-113">La migrazione è semplice, rapida e sicura.</span><span class="sxs-lookup"><span data-stu-id="0b4aa-113">Migration is simple, quick, and safe.</span></span> <span data-ttu-id="0b4aa-114">Le probabilità di esito negativo sono molto ridotte.</span><span class="sxs-lookup"><span data-stu-id="0b4aa-114">failure.</span></span>

<span data-ttu-id="0b4aa-115">PowerShell 7 è supportato nei sistemi operativi Windows seguenti:</span><span class="sxs-lookup"><span data-stu-id="0b4aa-115">PowerShell 7 is supported on the following Windows operating systems:</span></span>

- <span data-ttu-id="0b4aa-116">Windows 8.1 e 10</span><span class="sxs-lookup"><span data-stu-id="0b4aa-116">Windows 8.1 and 10</span></span>
- <span data-ttu-id="0b4aa-117">Windows Server 2012, 2012 R2, 2016 e 2019</span><span class="sxs-lookup"><span data-stu-id="0b4aa-117">Windows Server 2012, 2012 R2, 2016, and 2019</span></span>

<span data-ttu-id="0b4aa-118">PowerShell 7 viene eseguito anche in macOS e in diverse distribuzioni di Linux.</span><span class="sxs-lookup"><span data-stu-id="0b4aa-118">PowerShell 7 also runs on macOS and several Linux distributions.</span></span> <span data-ttu-id="0b4aa-119">Per un elenco dei sistemi operativi supportati e informazioni sul ciclo di vita del supporto, vedere [Ciclo di vita del supporto di PowerShell](/powershell/scripting/powershell-support-lifecycle).</span><span class="sxs-lookup"><span data-stu-id="0b4aa-119">For a list of supported operating systems and information about the support lifecycle, see the [PowerShell Support Lifecycle](/powershell/scripting/powershell-support-lifecycle).</span></span>

## <a name="installing-powershell-7"></a><span data-ttu-id="0b4aa-120">Installazione di PowerShell 7</span><span class="sxs-lookup"><span data-stu-id="0b4aa-120">Installing PowerShell 7</span></span>

<span data-ttu-id="0b4aa-121">Per garantire flessibilità e per supportare le esigenze dell'IT, dei i tecnici DevOps e degli sviluppatori, sono disponibili diverse opzioni per l'installazione di PowerShell 7.</span><span class="sxs-lookup"><span data-stu-id="0b4aa-121">For flexibility and to support the needs of IT, DevOps engineers, and developers, there are several options available to install PowerShell 7.</span></span> <span data-ttu-id="0b4aa-122">Nella maggior parte dei casi le opzioni di installazione possono essere ridotte ai metodi seguenti:</span><span class="sxs-lookup"><span data-stu-id="0b4aa-122">In most cases, the installation options can be reduced to the following methods:</span></span>

- <span data-ttu-id="0b4aa-123">Distribuire PowerShell usando il [pacchetto MSI](/powershell/scripting/install/installing-powershell-core-on-windows#installing-the-msi-package)</span><span class="sxs-lookup"><span data-stu-id="0b4aa-123">Deploy PowerShell using the [MSI package](/powershell/scripting/install/installing-powershell-core-on-windows#installing-the-msi-package)</span></span>
- <span data-ttu-id="0b4aa-124">Distribuire PowerShell usando il [ pacchetto ZIP](/powershell/scripting/install/installing-powershell-core-on-windows#installing-the-zip-package)</span><span class="sxs-lookup"><span data-stu-id="0b4aa-124">Deploy PowerShell using the [ZIP package](/powershell/scripting/install/installing-powershell-core-on-windows#installing-the-zip-package)</span></span>

> [!NOTE]
> <span data-ttu-id="0b4aa-125">Il pacchetto MSI può essere distribuito e aggiornato con prodotti gestionali come [System Center Configuration Manager (SCCM)](/configmgr/apps/).</span><span class="sxs-lookup"><span data-stu-id="0b4aa-125">The MSI package can be deployed and updated with management products such as [System Center Configuration Manager (SCCM)](/configmgr/apps/).</span></span> <span data-ttu-id="0b4aa-126">Scaricare i pacchetti dalla [pagina della versione di GitHub](https://github.com/PowerShell/PowerShell/releases).</span><span class="sxs-lookup"><span data-stu-id="0b4aa-126">Download the packages from [GitHub Release page](https://github.com/PowerShell/PowerShell/releases).</span></span>

<span data-ttu-id="0b4aa-127">La distribuzione del pacchetto MSI richiede l'autorizzazione di amministratore.</span><span class="sxs-lookup"><span data-stu-id="0b4aa-127">Deploying the MSI package requires Administrator permission.</span></span> <span data-ttu-id="0b4aa-128">Il pacchetto ZIP può essere distribuito da qualsiasi utente.</span><span class="sxs-lookup"><span data-stu-id="0b4aa-128">The ZIP package can be deployed by any user.</span></span> <span data-ttu-id="0b4aa-129">Il pacchetto ZIP è il modo più semplice per installare PowerShell 7 per i test, prima di eseguire il commit in un'installazione completa.</span><span class="sxs-lookup"><span data-stu-id="0b4aa-129">The ZIP package is the easiest way to install PowerShell 7 for testing, before committing to a full installation.</span></span>

## <a name="using-powershell-7-side-by-side-with-windows-powershell-51"></a><span data-ttu-id="0b4aa-130">Uso di PowerShell 7 side-by-side con Windows PowerShell 5.1</span><span class="sxs-lookup"><span data-stu-id="0b4aa-130">Using PowerShell 7 side-by-side with Windows PowerShell 5.1</span></span>

<span data-ttu-id="0b4aa-131">PowerShell 7 è progettato per coesistere con Windows PowerShell 5.1.</span><span class="sxs-lookup"><span data-stu-id="0b4aa-131">PowerShell 7 is designed to coexist with Windows PowerShell 5.1.</span></span> <span data-ttu-id="0b4aa-132">Le funzionalità seguenti garantiscono la protezione dell'investimento in PowerShell e la semplicità della migrazione a PowerShell 7.</span><span class="sxs-lookup"><span data-stu-id="0b4aa-132">The following features ensure that your investment in PowerShell is protected and your migration to PowerShell 7 is simple.</span></span>

- <span data-ttu-id="0b4aa-133">Percorso di installazione separato e nome dell'eseguibile</span><span class="sxs-lookup"><span data-stu-id="0b4aa-133">Separate installation path and executable name</span></span>
- <span data-ttu-id="0b4aa-134">PSModulePath separato</span><span class="sxs-lookup"><span data-stu-id="0b4aa-134">Separate PSModulePath</span></span>
- <span data-ttu-id="0b4aa-135">Profili separati per ogni versione</span><span class="sxs-lookup"><span data-stu-id="0b4aa-135">Separate profiles for each version</span></span>
- <span data-ttu-id="0b4aa-136">Compatibilità dei moduli migliorata</span><span class="sxs-lookup"><span data-stu-id="0b4aa-136">Improved module compatibility</span></span>
- <span data-ttu-id="0b4aa-137">Nuovi endpoint remoti</span><span class="sxs-lookup"><span data-stu-id="0b4aa-137">New remoting endpoints</span></span>
- <span data-ttu-id="0b4aa-138">Supporto di Criteri di gruppo</span><span class="sxs-lookup"><span data-stu-id="0b4aa-138">Group policy support</span></span>
- <span data-ttu-id="0b4aa-139">Registri eventi separati</span><span class="sxs-lookup"><span data-stu-id="0b4aa-139">Separate Event logs</span></span>

### <a name="separate-installation-path-and-executable-name"></a><span data-ttu-id="0b4aa-140">Percorso di installazione separato e nome dell'eseguibile</span><span class="sxs-lookup"><span data-stu-id="0b4aa-140">Separate installation path and executable name</span></span>

<span data-ttu-id="0b4aa-141">PowerShell 7 viene installato in una nuova directory, consentendo l'esecuzione side-by-side con Windows PowerShell 5.1.</span><span class="sxs-lookup"><span data-stu-id="0b4aa-141">PowerShell 7 installs to a new directory, enabling side-by-side execution with Windows PowerShell 5.1.</span></span>

<span data-ttu-id="0b4aa-142">Percorsi di installazione per versione:</span><span class="sxs-lookup"><span data-stu-id="0b4aa-142">Install locations by version:</span></span>

- <span data-ttu-id="0b4aa-143">Windows PowerShell 5.1: `$env:WINDIR\System32\WindowsPowerShell\v1.0`</span><span class="sxs-lookup"><span data-stu-id="0b4aa-143">Windows PowerShell 5.1: `$env:WINDIR\System32\WindowsPowerShell\v1.0`</span></span>
- <span data-ttu-id="0b4aa-144">PowerShell Core 6.x: `$env:ProgramFiles\PowerShell\6`</span><span class="sxs-lookup"><span data-stu-id="0b4aa-144">PowerShell Core 6.x: `$env:ProgramFiles\PowerShell\6`</span></span>
- <span data-ttu-id="0b4aa-145">PowerShell 7: `$env:ProgramFiles\PowerShell\7`</span><span class="sxs-lookup"><span data-stu-id="0b4aa-145">PowerShell 7: `$env:ProgramFiles\PowerShell\7`</span></span>

<span data-ttu-id="0b4aa-146">La nuova posizione viene aggiunta all'elemento PATH in modo che sia possibile eseguire sia Windows PowerShell 5.1 che PowerShell 7.</span><span class="sxs-lookup"><span data-stu-id="0b4aa-146">The new location is added to your PATH allowing you to run both Windows PowerShell 5.1 and PowerShell 7.</span></span> <span data-ttu-id="0b4aa-147">Se si sta eseguendo la migrazione da PowerShell Core 6.x a PowerShell 7, PowerShell 6 viene rimosso e l'elemento PATH viene sostituito.</span><span class="sxs-lookup"><span data-stu-id="0b4aa-147">If you're migrating from PowerShell Core 6.x to PowerShell 7, PowerShell 6 is removed and the PATH replaced.</span></span>

<span data-ttu-id="0b4aa-148">In Windows PowerShell l'eseguibile di PowerShell è denominato `powershell.exe`.</span><span class="sxs-lookup"><span data-stu-id="0b4aa-148">In Windows PowerShell, the PowerShell executable is named `powershell.exe`.</span></span> <span data-ttu-id="0b4aa-149">A partire dalla versione 6 l'eseguibile è denominato `pwsh.exe`.</span><span class="sxs-lookup"><span data-stu-id="0b4aa-149">In version 6 and above, the executable is named `pwsh.exe`.</span></span> <span data-ttu-id="0b4aa-150">Il nuovo nome consente di semplificare il supporto dell'esecuzione side-by-side di entrambe le versioni.</span><span class="sxs-lookup"><span data-stu-id="0b4aa-150">The new name makes it easy to support side-by-side execution of both versions.</span></span>

### <a name="separate-psmodulepath"></a><span data-ttu-id="0b4aa-151">PSModulePath separato</span><span class="sxs-lookup"><span data-stu-id="0b4aa-151">Separate PSModulePath</span></span>

<span data-ttu-id="0b4aa-152">Per impostazione predefinita, Windows PowerShell e PowerShell 7 archiviano i moduli in percorsi diversi.</span><span class="sxs-lookup"><span data-stu-id="0b4aa-152">By default, Windows PowerShell and PowerShell 7 store modules in different locations.</span></span> <span data-ttu-id="0b4aa-153">PowerShell 7 combina tali percorsi nella variabile di ambiente `$Env:PSModulePath`.</span><span class="sxs-lookup"><span data-stu-id="0b4aa-153">PowerShell 7 combines those locations in the `$Env:PSModulePath` environment variable.</span></span> <span data-ttu-id="0b4aa-154">Quando si importa un modulo in base al nome, PowerShell controlla il percorso specificato da `$Env:PSModulePath`.</span><span class="sxs-lookup"><span data-stu-id="0b4aa-154">When importing a module by name, PowerShell checks the location specified by `$Env:PSModulePath`.</span></span> <span data-ttu-id="0b4aa-155">Questo consente a PowerShell 7 di caricare sia i moduli Core che Desktop.</span><span class="sxs-lookup"><span data-stu-id="0b4aa-155">This allows PowerShell 7 to load both Core and Desktop modules.</span></span>

|            <span data-ttu-id="0b4aa-156">Ambito di installazione</span><span class="sxs-lookup"><span data-stu-id="0b4aa-156">Install Scope</span></span>            |                <span data-ttu-id="0b4aa-157">Windows PowerShell 5.1</span><span class="sxs-lookup"><span data-stu-id="0b4aa-157">Windows PowerShell 5.1</span></span>                 |             <span data-ttu-id="0b4aa-158">PowerShell 7.0</span><span class="sxs-lookup"><span data-stu-id="0b4aa-158">PowerShell 7.0</span></span>             |
| ----------------------------------- | ----------------------------------------------------- | -------------------------------------- |
| <span data-ttu-id="0b4aa-159">Moduli di PowerShell</span><span class="sxs-lookup"><span data-stu-id="0b4aa-159">PowerShell modules</span></span>                  | `$env:WINDIR\system32\WindowsPowerShell\v1.0\Modules` | `$PSHOME\Modules`                      |
| <span data-ttu-id="0b4aa-160">Installato da utente -</span><span class="sxs-lookup"><span data-stu-id="0b4aa-160">User installed</span></span><br><span data-ttu-id="0b4aa-161">Ambito AllUsers</span><span class="sxs-lookup"><span data-stu-id="0b4aa-161">AllUsers scope</span></span>    | `$env:ProgramFiles\WindowsPowerShell\Modules`         | `$env:ProgramFiles\PowerShell\Modules` |
| <span data-ttu-id="0b4aa-162">Installato da utente -</span><span class="sxs-lookup"><span data-stu-id="0b4aa-162">User installed</span></span><br><span data-ttu-id="0b4aa-163">Ambito CurrentUser</span><span class="sxs-lookup"><span data-stu-id="0b4aa-163">CurrentUser scope</span></span> | `$HOME\Documents\WindowsPowerShell\Modules`           | `$HOME\Documents\PowerShell\Modules`   |

<span data-ttu-id="0b4aa-164">Negli esempi seguenti vengono illustrati i valori predefiniti di `$Env:PSModulePath` per ogni versione.</span><span class="sxs-lookup"><span data-stu-id="0b4aa-164">The following examples show the default values of `$Env:PSModulePath` for each version.</span></span>

- <span data-ttu-id="0b4aa-165">Per Windows PowerShell 5.1:</span><span class="sxs-lookup"><span data-stu-id="0b4aa-165">For Windows PowerShell 5.1:</span></span>

  ```powershell
  $Env:PSModulePath -split (';')
  ```

  ```Output
  C:\Users\<user>\Documents\WindowsPowerShell\Modules
  C:\Program Files\WindowsPowerShell\Modules
  C:\WINDOWS\System32\WindowsPowerShell\v1.0\Modules
  ```

- <span data-ttu-id="0b4aa-166">Per PowerShell 7:</span><span class="sxs-lookup"><span data-stu-id="0b4aa-166">For PowerShell 7:</span></span>

  ```powershell
  $Env:PSModulePath -split (';')
  ```

  ```Output
  C:\Users\<user>\Documents\PowerShell\Modules
  C:\Program Files\PowerShell\Modules
  C:\Program Files\PowerShell\7\Modules
  C:\Program Files\WindowsPowerShell\Modules
  C:\WINDOWS\System32\WindowsPowerShell\v1.0\Modules
  ```

<span data-ttu-id="0b4aa-167">Si noti che PowerShell 7 include i percorsi di Windows PowerShell e i percorsi di PowerShell 7 per consentire il caricamento automatico dei moduli.</span><span class="sxs-lookup"><span data-stu-id="0b4aa-167">Notice that PowerShell 7 includes the Windows PowerShell paths and the PowerShell 7 paths to provide autoloading of modules.</span></span>

> [!NOTE]
> <span data-ttu-id="0b4aa-168">Potrebbero esistere percorsi aggiuntivi se è stata modificata la variabile di ambiente PSModulePath o se sono stati installati moduli o applicazioni personalizzati.</span><span class="sxs-lookup"><span data-stu-id="0b4aa-168">Additional paths may exist if you have changed the PSModulePath environment variable or installed custom modules or applications.</span></span>

<span data-ttu-id="0b4aa-169">Per altre informazioni, vedere `PSModulePath` in [Informazioni sulle variabili di ambiente](/powershell/module/microsoft.powershell.core/about/about_environment_variables#environment-variables-that-store-preferences).</span><span class="sxs-lookup"><span data-stu-id="0b4aa-169">For more information, see `PSModulePath` in [about_Environment_Variables](/powershell/module/microsoft.powershell.core/about/about_environment_variables#environment-variables-that-store-preferences).</span></span>

<span data-ttu-id="0b4aa-170">Per altre informazioni sui moduli, vedere [Informazioni sui moduli](/powershell/module/Microsoft.PowerShell.Core/About/about_Modules).</span><span class="sxs-lookup"><span data-stu-id="0b4aa-170">For more information about Modules, see [about_Modules](/powershell/module/Microsoft.PowerShell.Core/About/about_Modules).</span></span>

### <a name="separate-profiles"></a><span data-ttu-id="0b4aa-171">Profili separati</span><span class="sxs-lookup"><span data-stu-id="0b4aa-171">Separate profiles</span></span>

<span data-ttu-id="0b4aa-172">Il profilo di PowerShell è uno script che viene eseguito all'avvio di PowerShell.</span><span class="sxs-lookup"><span data-stu-id="0b4aa-172">A PowerShell profile is a script that executes when PowerShell starts.</span></span> <span data-ttu-id="0b4aa-173">Questo script personalizza l'ambiente tramite l'aggiunta di comandi, alias, funzioni, variabili, moduli e unità PowerShell.</span><span class="sxs-lookup"><span data-stu-id="0b4aa-173">This script customizes your environment by adding commands, aliases, functions, variables, modules, and PowerShell drives.</span></span> <span data-ttu-id="0b4aa-174">Lo script del profilo rende disponibili queste personalizzazioni in ogni sessione senza che sia necessario ricrearle manualmente.</span><span class="sxs-lookup"><span data-stu-id="0b4aa-174">The profile script makes these customizations available in every session without having to manually recreate them.</span></span>

<span data-ttu-id="0b4aa-175">Il percorso della posizione del profilo è stato modificato in PowerShell 7.</span><span class="sxs-lookup"><span data-stu-id="0b4aa-175">The path to the location of the profile has changed in PowerShell 7.</span></span>

- <span data-ttu-id="0b4aa-176">In Windows PowerShell 5.1 il percorso del profilo è `$HOME\Documents\WindowsPowerShell`.</span><span class="sxs-lookup"><span data-stu-id="0b4aa-176">In Windows PowerShell 5.1, the location of the profile is `$HOME\Documents\WindowsPowerShell`.</span></span>
- <span data-ttu-id="0b4aa-177">In PowerShell 7 il percorso del profilo è `$HOME\Documents\PowerShell`.</span><span class="sxs-lookup"><span data-stu-id="0b4aa-177">In PowerShell 7, the location of the profile is `$HOME\Documents\PowerShell`.</span></span>

<span data-ttu-id="0b4aa-178">Sono stati modificati anche i nomi file del profilo:</span><span class="sxs-lookup"><span data-stu-id="0b4aa-178">The profile filenames have also changed:</span></span>

   ```powershell
   PS> $PROFILE | Select-Object *Host* | Format-List

   AllUsersAllHosts       : C:\Program Files\PowerShell\7\profile.ps1
   AllUsersCurrentHost    : C:\Program Files\PowerShell\7\Microsoft.PowerShell_profile.ps1
   CurrentUserAllHosts    : C:\Users\<user>\Documents\PowerShell\profile.ps1
   CurrentUserCurrentHost : C:\Users\<user>\Documents\PowerShell\Microsoft.PowerShell_profile.ps1
   ```

<span data-ttu-id="0b4aa-179">Per altre informazioni, vedere [Informazioni sui profili](/powershell/module/microsoft.powershell.core/about/about_profiles).</span><span class="sxs-lookup"><span data-stu-id="0b4aa-179">For more information [about_Profiles](/powershell/module/microsoft.powershell.core/about/about_profiles).</span></span>

### <a name="powershell-7-compatibility-with-windows-powershell-51-modules"></a><span data-ttu-id="0b4aa-180">Compatibilità di PowerShell 7 con i moduli di Windows PowerShell 5.1</span><span class="sxs-lookup"><span data-stu-id="0b4aa-180">PowerShell 7 compatibility with Windows PowerShell 5.1 modules</span></span>

<span data-ttu-id="0b4aa-181">La maggior parte dei moduli usati in Windows PowerShell 5.1, tra cui Azure PowerShell e Active Directory, funziona già con PowerShell 7.</span><span class="sxs-lookup"><span data-stu-id="0b4aa-181">Most of the modules you use in Windows PowerShell 5.1 already work with PowerShell 7, including Azure PowerShell and Active Directory.</span></span> <span data-ttu-id="0b4aa-182">Stiamo continuando a collaborare con altri team per aggiungere il supporto nativo di PowerShell 7 per altri moduli, tra cui Microsoft Graph, Office 365 e altri ancora.</span><span class="sxs-lookup"><span data-stu-id="0b4aa-182">We're continuing to work with other teams to add native PowerShell 7 support for more modules including Microsoft Graph, Office 365, and others.</span></span> <span data-ttu-id="0b4aa-183">Per l'elenco corrente dei moduli supportati, vedere [Compatibilità dei moduli di PowerShell 7](/powershell/scripting/whats-new/module-compatibility).</span><span class="sxs-lookup"><span data-stu-id="0b4aa-183">For the current list of supported modules, see [PowerShell 7 module compatibility](/powershell/scripting/whats-new/module-compatibility).</span></span>

> [!NOTE]
> <span data-ttu-id="0b4aa-184">In Windows è stato aggiunto anche un commutatore **UseWindowsPowerShell** per `Import-Module` per semplificare la transizione a PowerShell 7 per chi usa moduli incompatibili.</span><span class="sxs-lookup"><span data-stu-id="0b4aa-184">On Windows, we've also added a **UseWindowsPowerShell** switch to `Import-Module` to ease the transition to PowerShell 7 for those using incompatible modules.</span></span> <span data-ttu-id="0b4aa-185">Per altre informazioni su questa funzionalità, vedere [Informazioni sulla compatibilità di Windows PowerShell](/powershell/module/Microsoft.PowerShell.Core/About/about_windows_powershell_compatibility).</span><span class="sxs-lookup"><span data-stu-id="0b4aa-185">For more information on this functionality, see [about_Windows_PowerShell_Compatibility](/powershell/module/Microsoft.PowerShell.Core/About/about_windows_powershell_compatibility).</span></span>

### <a name="powershell-remoting"></a><span data-ttu-id="0b4aa-186">Comunicazione remota di PowerShell</span><span class="sxs-lookup"><span data-stu-id="0b4aa-186">PowerShell Remoting</span></span>

<span data-ttu-id="0b4aa-187">La comunicazione remota di Windows PowerShell consente di eseguire qualsiasi comando di PowerShell in uno o più computer remoti.</span><span class="sxs-lookup"><span data-stu-id="0b4aa-187">PowerShell remoting lets you run any PowerShell command on one or more remote computers.</span></span> <span data-ttu-id="0b4aa-188">È possibile stabilire connessioni permanenti, avviare sessioni interattive ed eseguire script in computer remoti.</span><span class="sxs-lookup"><span data-stu-id="0b4aa-188">You can establish persistent connections, start interactive sessions, and run scripts on remote computers.</span></span>

#### <a name="ws-management-remoting"></a><span data-ttu-id="0b4aa-189">Comunicazione remota di WS-Management</span><span class="sxs-lookup"><span data-stu-id="0b4aa-189">WS-Management remoting</span></span>

<span data-ttu-id="0b4aa-190">Windows PowerShell 5.1 e versioni precedenti usano il protocollo WS-Management (WSMAN) per la negoziazione della connessione e il trasporto dei dati.</span><span class="sxs-lookup"><span data-stu-id="0b4aa-190">Windows PowerShell 5.1 and below use the WS-Management (WSMAN) protocol for connection negotiation and data transport.</span></span> <span data-ttu-id="0b4aa-191">Gestione remota Windows (WinRM) usa il protocollo WSMAN.</span><span class="sxs-lookup"><span data-stu-id="0b4aa-191">Windows Remote Management (WinRM) uses the WSMAN protocol.</span></span> <span data-ttu-id="0b4aa-192">Se WinRM è stato abilitato, PowerShell 7 usa l'endpoint di Windows PowerShell 5.1 esistente denominato `Microsoft.PowerShell` per le connessioni remote.</span><span class="sxs-lookup"><span data-stu-id="0b4aa-192">If WinRM has been enabled, PowerShell 7 uses the existing Windows PowerShell 5.1 endpoint named `Microsoft.PowerShell` for remoting connections.</span></span> <span data-ttu-id="0b4aa-193">Per aggiornare PowerShell 7 in modo da includere il proprio endpoint, eseguire il cmdlet `Enable-PSRemoting`.</span><span class="sxs-lookup"><span data-stu-id="0b4aa-193">To update PowerShell 7 to include its own endpoint, run the `Enable-PSRemoting` cmdlet.</span></span> <span data-ttu-id="0b4aa-194">Per informazioni sulla connessione a endpoint specifici, vedere [Comunicazione remota di WS-Management in PowerShell Core](/powershell/scripting/learn/remoting/wsman-remoting-in-powershell-core)</span><span class="sxs-lookup"><span data-stu-id="0b4aa-194">For information about connecting to specific endpoints, see [WS-Management Remoting in PowerShell Core](/powershell/scripting/learn/remoting/wsman-remoting-in-powershell-core)</span></span>

<span data-ttu-id="0b4aa-195">Per usare la comunicazione remota di Windows PowerShell, è necessario che il computer remoto sia configurato per la gestione remota.</span><span class="sxs-lookup"><span data-stu-id="0b4aa-195">To use Windows PowerShell remoting, the remote computer must be configured for remote management.</span></span>
<span data-ttu-id="0b4aa-196">Per altre informazioni, incluse le istruzioni, vedere [about_Remote_Requirements](/powershell/module/microsoft.powershell.core/about/about_remote_requirements).</span><span class="sxs-lookup"><span data-stu-id="0b4aa-196">For more information, including instructions, see [About Remote Requirements](/powershell/module/microsoft.powershell.core/about/about_remote_requirements).</span></span>

<span data-ttu-id="0b4aa-197">Per altre informazioni sull'uso della comunicazione remota, vedere [Informazioni sulla comunicazione remota](/powershell/module/microsoft.powershell.core/about/about_remote)</span><span class="sxs-lookup"><span data-stu-id="0b4aa-197">For more information about working with remoting, see [About Remote](/powershell/module/microsoft.powershell.core/about/about_remote)</span></span>

#### <a name="ssh-based-remoting"></a><span data-ttu-id="0b4aa-198">Comunicazione remota basata su SSH</span><span class="sxs-lookup"><span data-stu-id="0b4aa-198">SSH-based remoting</span></span>

<span data-ttu-id="0b4aa-199">La comunicazione remota basata su SSH è stata aggiunta in PowerShell Core 6.x per supportare altri sistemi operativi che non possono usare componenti nativi di Windows come **WinRM**.</span><span class="sxs-lookup"><span data-stu-id="0b4aa-199">SSH-based remoting was added in PowerShell Core 6.x to support other operating systems that can't use Windows native components like **WinRM**.</span></span> <span data-ttu-id="0b4aa-200">La comunicazione remota SSH crea un processo host di PowerShell nel computer di destinazione come sottosistema SSH.</span><span class="sxs-lookup"><span data-stu-id="0b4aa-200">SSH remoting creates a PowerShell host process on the target computer as an SSH subsystem.</span></span> <span data-ttu-id="0b4aa-201">Per informazioni dettagliate ed esempi su come configurare la comunicazione remota basata su SSH in Windows o Linux, vedere: [Comunicazione remota di PowerShell su SSH](/powershell/scripting/learn/remoting/ssh-remoting-in-powershell-core).</span><span class="sxs-lookup"><span data-stu-id="0b4aa-201">For details and examples on setting up SSH-based remoting on Windows or Linux, see: [PowerShell remoting over SSH](/powershell/scripting/learn/remoting/ssh-remoting-in-powershell-core).</span></span>

> [!NOTE]
> <span data-ttu-id="0b4aa-202">PowerShell Gallery (PSGallery) contiene un modulo e un cmdlet che configura automaticamente la comunicazione remota basata su SSH.</span><span class="sxs-lookup"><span data-stu-id="0b4aa-202">The PowerShell Gallery (PSGallery) contains a module and cmdlet that automatically configures SSH-based remoting.</span></span> <span data-ttu-id="0b4aa-203">Installare il modulo `Microsoft.PowerShell.RemotingTools` da [PSGallery](https://www.powershellgallery.com/packages/Microsoft.PowerShell.RemotingTools/0.1.0) ed eseguire il cmdlet `Enable-SSH`.</span><span class="sxs-lookup"><span data-stu-id="0b4aa-203">Install the `Microsoft.PowerShell.RemotingTools` module from the [PSGallery](https://www.powershellgallery.com/packages/Microsoft.PowerShell.RemotingTools/0.1.0) and run the `Enable-SSH` cmdlet.</span></span>

<span data-ttu-id="0b4aa-204">I cmdlet `New-PSSession`, `Enter-PSSession` e `Invoke-Command` includono nuovi set di parametri per supportare le connessioni SSH.</span><span class="sxs-lookup"><span data-stu-id="0b4aa-204">The `New-PSSession`, `Enter-PSSession`, and `Invoke-Command` cmdlets have new parameter sets to support SSH connections.</span></span>

```powershell
[-HostName <string>]  [-UserName <string>]  [-KeyFilePath <string>]
```

<span data-ttu-id="0b4aa-205">Per creare una sessione remota, specificare il computer di destinazione con il parametro **HostName** e il nome utente con il parametro **UserName**.</span><span class="sxs-lookup"><span data-stu-id="0b4aa-205">To create a remote session, specify the target computer with the **HostName** parameter and provide the user name with **UserName**.</span></span> <span data-ttu-id="0b4aa-206">Quando si eseguono i cmdlet in modo interattivo, viene chiesto di immettere una password.</span><span class="sxs-lookup"><span data-stu-id="0b4aa-206">When running the cmdlets interactively, you're prompted for a password.</span></span>

```powershell
Enter-PSSession -HostName <Computer> -UserName <Username>
```

<span data-ttu-id="0b4aa-207">In alternativa, quando si usa il parametro **HostName**, specificare le informazioni sul nome utente seguite dal simbolo di chiocciola (`@`), seguito dal nome del computer.</span><span class="sxs-lookup"><span data-stu-id="0b4aa-207">Alternatively, when using the **HostName** parameter, provide the username information followed by the at sign (`@`), followed by the computer name.</span></span>

```powershell
Enter-PSSession -HostName <Username>@<Computer>
```

<span data-ttu-id="0b4aa-208">È anche possibile configurare l'autenticazione con chiave SSH con il parametro **KeyFilePath**.</span><span class="sxs-lookup"><span data-stu-id="0b4aa-208">You may set up SSH key authentication using a private key file with the **KeyFilePath** parameter.</span></span>
<span data-ttu-id="0b4aa-209">Per altre informazioni, vedere [Gestione delle chiavi OpenSSH](/windows-server/administration/openssh/openssh_keymanagement).</span><span class="sxs-lookup"><span data-stu-id="0b4aa-209">For more information, see [OpenSSH Key Management](/windows-server/administration/openssh/openssh_keymanagement).</span></span>

### <a name="group-policy-supported"></a><span data-ttu-id="0b4aa-210">Supporto di Criteri di gruppo</span><span class="sxs-lookup"><span data-stu-id="0b4aa-210">Group Policy supported</span></span>

<span data-ttu-id="0b4aa-211">PowerShell include le impostazioni Criteri di gruppo che consentono di definire valori di opzioni coerenti per i server in un ambiente aziendale.</span><span class="sxs-lookup"><span data-stu-id="0b4aa-211">PowerShell includes Group Policy settings to help you define consistent option values for servers in an enterprise environment.</span></span> <span data-ttu-id="0b4aa-212">Tali impostazioni includono:</span><span class="sxs-lookup"><span data-stu-id="0b4aa-212">These settings include:</span></span>

- <span data-ttu-id="0b4aa-213">Configurazione della sessione della console: imposta un endpoint di configurazione in cui viene eseguito PowerShell.</span><span class="sxs-lookup"><span data-stu-id="0b4aa-213">Console session configuration: Sets a configuration endpoint in which PowerShell is run.</span></span>
- <span data-ttu-id="0b4aa-214">Attiva registrazione moduli: imposta la proprietà LogPipelineExecutionDetails dei moduli.</span><span class="sxs-lookup"><span data-stu-id="0b4aa-214">Turn on Module Logging: Sets the LogPipelineExecutionDetails property of modules.</span></span>
- <span data-ttu-id="0b4aa-215">Attiva la registrazione del blocco di script di PowerShell: abilita la registrazione dettagliata di tutti gli script di PowerShell.</span><span class="sxs-lookup"><span data-stu-id="0b4aa-215">Turn on PowerShell Script Block Logging: Enables detailed logging of all PowerShell scripts.</span></span>
- <span data-ttu-id="0b4aa-216">Attiva l'esecuzione di script: imposta i criteri di esecuzione di PowerShell.</span><span class="sxs-lookup"><span data-stu-id="0b4aa-216">Turn on Script Execution: Sets the PowerShell execution policy.</span></span>
- <span data-ttu-id="0b4aa-217">Attiva trascrizione di PowerShell: abilita l'acquisizione di input e output di comandi PowerShell in trascrizioni basate su testo.</span><span class="sxs-lookup"><span data-stu-id="0b4aa-217">Turn on PowerShell Transcription: enables capturing of input and output of PowerShell commands into text-based transcripts.</span></span>
- <span data-ttu-id="0b4aa-218">Imposta il percorso di origine predefinito per Update-Help: imposta l'origine per la Guida aggiornabile su una directory e non su Internet.</span><span class="sxs-lookup"><span data-stu-id="0b4aa-218">Set the default source path for Update-Help: Sets the source for Updatable Help to a directory, not the Internet.</span></span>

<span data-ttu-id="0b4aa-219">Per altre informazioni, vedere [Informazioni sulle impostazioni di Criteri di gruppo](/powershell/module/microsoft.powershell.core/about/about_group_policy_settings).</span><span class="sxs-lookup"><span data-stu-id="0b4aa-219">For more information, see [about_Group_Policy_Settings](/powershell/module/microsoft.powershell.core/about/about_group_policy_settings).</span></span>

<span data-ttu-id="0b4aa-220">PowerShell 7 include modelli di Criteri di gruppo e uno script di installazione in `$PSHOME`.</span><span class="sxs-lookup"><span data-stu-id="0b4aa-220">PowerShell 7 includes Group Policy templates and an installation script in `$PSHOME`.</span></span>

<span data-ttu-id="0b4aa-221">Gli strumenti di Criteri di gruppo usano i file di modello amministrativi (`.admx`, `.adml`) per popolare le impostazioni dei criteri nell'interfaccia utente.</span><span class="sxs-lookup"><span data-stu-id="0b4aa-221">Group Policy tools use administrative template files (`.admx`, `.adml`) to populate policy settings in the user interface.</span></span> <span data-ttu-id="0b4aa-222">Ciò consente agli amministratori di gestire le impostazioni dei criteri basate sul Registro di sistema.</span><span class="sxs-lookup"><span data-stu-id="0b4aa-222">This allows administrators to manage registry-based policy settings.</span></span> <span data-ttu-id="0b4aa-223">Lo script `InstallPSCorePolicyDefinitions.ps1` installa i modelli amministrativi di PowerShell Core nel computer locale.</span><span class="sxs-lookup"><span data-stu-id="0b4aa-223">The `InstallPSCorePolicyDefinitions.ps1` script installs PowerShell Core Administrative Templates on the local machine.</span></span>

```powershell
Get-ChildItem -Path $PSHOME -Filter *Core*Policy*
```

```Output
    Directory: C:\Program Files\PowerShell\7

Mode                 LastWriteTime         Length Name
----                 -------------         ------ ----
-a---           2/27/2020 12:38 AM          15861 InstallPSCorePolicyDefinitions.ps1
-a---           2/27/2020 12:28 AM           9675 PowerShellCoreExecutionPolicy.adml
-a---           2/27/2020 12:28 AM           6201 PowerShellCoreExecutionPolicy.admx
```

### <a name="separate-event-logs"></a><span data-ttu-id="0b4aa-224">Registri eventi separati</span><span class="sxs-lookup"><span data-stu-id="0b4aa-224">Separate Event Logs</span></span>

<span data-ttu-id="0b4aa-225">Gli eventi di registro di Windows PowerShell e PowerShell 7 consentono di separare i registri eventi.</span><span class="sxs-lookup"><span data-stu-id="0b4aa-225">Windows PowerShell and PowerShell 7 log events to separate event logs.</span></span> <span data-ttu-id="0b4aa-226">Usare il comando seguente per visualizzare un elenco dei registri di PowerShell.</span><span class="sxs-lookup"><span data-stu-id="0b4aa-226">Use the following command to get a list of the PowerShell logs.</span></span>

```powershell
Get-WinEvent -ListLog *PowerShell*
```

<span data-ttu-id="0b4aa-227">Per altre informazioni, vedere [Informazioni sui registri di Windows](/powershell/module/microsoft.powershell.core/about/about_logging_windows).</span><span class="sxs-lookup"><span data-stu-id="0b4aa-227">For more information, see [about_Logging_Windows](/powershell/module/microsoft.powershell.core/about/about_logging_windows).</span></span>

## <a name="improved-editing-experience-with-visual-studio-code"></a><span data-ttu-id="0b4aa-228">Esperienza di modifica migliorata con Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="0b4aa-228">Improved editing experience with Visual Studio Code</span></span>

<span data-ttu-id="0b4aa-229">[Visual Studio Code (VSCode)](https://code.visualstudio.com/) con l'[estensione PowerShell](https://code.visualstudio.com/docs/languages/powershell) è l'ambiente di scripting supportato per PowerShell 7.</span><span class="sxs-lookup"><span data-stu-id="0b4aa-229">[Visual Studio Code (VSCode)](https://code.visualstudio.com/) with the [PowerShell Extension](https://code.visualstudio.com/docs/languages/powershell) is the supported scripting environment for PowerShell 7.</span></span> <span data-ttu-id="0b4aa-230">Windows PowerShell Integrated Scripting Environment (ISE) supporta solo Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="0b4aa-230">The Windows PowerShell Integrated Scripting Environment (ISE) only supports Windows PowerShell.</span></span>

<span data-ttu-id="0b4aa-231">L'estensione di PowerShell aggiornata include:</span><span class="sxs-lookup"><span data-stu-id="0b4aa-231">The updated PowerShell extension includes:</span></span>

- <span data-ttu-id="0b4aa-232">Nuova modalità di compatibilità di ISE</span><span class="sxs-lookup"><span data-stu-id="0b4aa-232">New ISE compatibility mode</span></span>
- <span data-ttu-id="0b4aa-233">PSReadLine nella console integrata, inclusa l'evidenziazione della sintassi, la modifica a più righe e la ricerca a ritroso</span><span class="sxs-lookup"><span data-stu-id="0b4aa-233">PSReadLine in the Integrated Console, including syntax highlighting, multi-line editing, and back search</span></span>
- <span data-ttu-id="0b4aa-234">Miglioramenti alla stabilità e alle prestazioni</span><span class="sxs-lookup"><span data-stu-id="0b4aa-234">Stability and performance improvements</span></span>
- <span data-ttu-id="0b4aa-235">Nuova integrazione con CodeLens</span><span class="sxs-lookup"><span data-stu-id="0b4aa-235">New CodeLens integration</span></span>
- <span data-ttu-id="0b4aa-236">Completamento automatico del percorso migliorato</span><span class="sxs-lookup"><span data-stu-id="0b4aa-236">Improved path auto-completion</span></span>

<span data-ttu-id="0b4aa-237">Per semplificare la transizione a Visual Studio Code, usare la funzione **Enable ISE Mode** (Abilita modalità ISE) disponibile in **Riquadro comandi**.</span><span class="sxs-lookup"><span data-stu-id="0b4aa-237">To make the transition to Visual Studio Code easier, use the **Enable ISE Mode** function available in the **Command Palette**.</span></span> <span data-ttu-id="0b4aa-238">Questa funzione consente a VSCode di passare a un layout di tipo ISE.</span><span class="sxs-lookup"><span data-stu-id="0b4aa-238">This function switches VSCode into an ISE-style layout.</span></span> <span data-ttu-id="0b4aa-239">Il layout di tipo ISE offre tutte le nuove funzionalità di PowerShell in un'esperienza utente familiare.</span><span class="sxs-lookup"><span data-stu-id="0b4aa-239">The ISE-style layout gives you all the new features and capabilities of PowerShell in a familiar user experience.</span></span>

<span data-ttu-id="0b4aa-240">Per passare al nuovo layout ISE, premere <kbd>CTRL</kbd>+<kbd>MAIUSC</kbd>+<kbd>P</kbd> per aprire **Riquadro comandi**, digitare `PowerShell` e selezionare **PowerShell: Enable ISE Mode** (Abilita modalità ISE).</span><span class="sxs-lookup"><span data-stu-id="0b4aa-240">To switch to the new ISE layout, press <kbd>Ctrl</kbd>+<kbd>Shift</kbd>+<kbd>P</kbd> to open the **Command Palette**, type `PowerShell` and select **PowerShell: Enable ISE Mode**.</span></span>

<span data-ttu-id="0b4aa-241">Per impostare il layout sul layout originale, aprire **Riquadro comandi**, selezionare **PowerShell: Disable ISE Mode (restore to defaults)** (Disabilita modalità ISE - ripristino impostazioni predefinite).</span><span class="sxs-lookup"><span data-stu-id="0b4aa-241">To set the layout to the original layout, open the **Command Palette**, select **PowerShell: Disable ISE Mode (restore to defaults)**.</span></span>

<span data-ttu-id="0b4aa-242">Per informazioni dettagliate sulla personalizzazione del layout di VSCode in ISE, vedere [Come replicare l'esperienza ISE in Visual Studio Code](/powershell/scripting/components/vscode/how-to-replicate-the-ise-experience-in-vscode)</span><span class="sxs-lookup"><span data-stu-id="0b4aa-242">For details about customizing the VSCode layout to ISE, see [How to Replicate the ISE Experience in Visual Studio Code](/powershell/scripting/components/vscode/how-to-replicate-the-ise-experience-in-vscode)</span></span>

> [!NOTE]
> <span data-ttu-id="0b4aa-243">L'aggiornamento di ISE con le nuove funzionalità non è attualmente in programma.</span><span class="sxs-lookup"><span data-stu-id="0b4aa-243">There no plans to update the ISE with new features.</span></span> <span data-ttu-id="0b4aa-244">ISE è ora una funzionalità disinstallabile dall'utente nelle versioni più recenti di Windows 10 e Windows Server.</span><span class="sxs-lookup"><span data-stu-id="0b4aa-244">The ISE is now a user-uninstallable feature in the latest versions of Windows 10 and Windows Server.</span></span> <span data-ttu-id="0b4aa-245">La rimozione definitiva di ISE non è attualmente in programma.</span><span class="sxs-lookup"><span data-stu-id="0b4aa-245">There are no plans to permanently remove the ISE.</span></span> <span data-ttu-id="0b4aa-246">Il team di PowerShell e i relativi partner sono concentrati sul miglioramento dell'esperienza di scripting nell'estensione di PowerShell per Visual Studio Code.</span><span class="sxs-lookup"><span data-stu-id="0b4aa-246">The PowerShell Team and its partners are focused on improving the scripting experience in the PowerShell extension for Visual Studio Code.</span></span>

## <a name="next-steps"></a><span data-ttu-id="0b4aa-247">Passaggi successivi</span><span class="sxs-lookup"><span data-stu-id="0b4aa-247">Next Steps</span></span>

<span data-ttu-id="0b4aa-248">Una volta apprese le informazioni necessarie per eseguire la migrazione, è possibile [installare PowerShell 7](/powershell/scripting/install/installing-powershell-core-on-windows).</span><span class="sxs-lookup"><span data-stu-id="0b4aa-248">Armed with the knowledge to effectively migrate, [install PowerShell 7](/powershell/scripting/install/installing-powershell-core-on-windows) now!</span></span>
