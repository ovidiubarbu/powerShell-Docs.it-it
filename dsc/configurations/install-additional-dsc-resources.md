---
ms.date: 12/12/2018
keywords: DSC, powershell, resource, raccolta, il programma di installazione
title: Installare risorse DSC aggiuntive
ms.openlocfilehash: ecaf176230ccd934b57b1c27d72ff83e6ba906e9
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MTE95
ms.contentlocale: it-IT
ms.lasthandoff: 12/14/2018
ms.locfileid: "53401693"
---
# <a name="install-additional-dsc-resources"></a><span data-ttu-id="dddc4-103">Installare risorse DSC aggiuntive</span><span class="sxs-lookup"><span data-stu-id="dddc4-103">Install Additional DSC Resources</span></span>

<span data-ttu-id="dddc4-104">PowerShell include varie risorse di Out-of-the-box per Desired State Configuration (DSC).</span><span class="sxs-lookup"><span data-stu-id="dddc4-104">PowerShell includes several Out-of-the-box resources for Desired State Configuration (DSC).</span></span> <span data-ttu-id="dddc4-105">Il **PSDesiredStateConfiguration** modulo contiene tutte le risorse DSC OOB disponibili nell'istanza specifica di PowerShell.</span><span class="sxs-lookup"><span data-stu-id="dddc4-105">The **PSDesiredStateConfiguration** module contains all of the OOB DSC resources available on your specific instance of PowerShell.</span></span>

<span data-ttu-id="dddc4-106">Questo è un elenco delle risorse OOB incluse in PowerShell 4.0 e una descrizione delle funzionalità della risorsa.</span><span class="sxs-lookup"><span data-stu-id="dddc4-106">This is a list of the OOB resources included in PowerShell 4.0 and a description of the resource's capabilities.</span></span>

> [!NOTE]
> <span data-ttu-id="dddc4-107">Si tratta di un elenco incompleto, come il numero di risorse OOB è cresciuto con ogni versione di PowerShell.</span><span class="sxs-lookup"><span data-stu-id="dddc4-107">This is an incomplete list, as the number of OOB resources has grown with each version of PowerShell.</span></span>

|<span data-ttu-id="dddc4-108">Resource</span><span class="sxs-lookup"><span data-stu-id="dddc4-108">Resource</span></span>  |<span data-ttu-id="dddc4-109">Description</span><span class="sxs-lookup"><span data-stu-id="dddc4-109">Description</span></span>  |
|---------|---------|
|<span data-ttu-id="dddc4-110">**File**</span><span class="sxs-lookup"><span data-stu-id="dddc4-110">**File**</span></span>|<span data-ttu-id="dddc4-111">Controlla lo stato di file e directory.</span><span class="sxs-lookup"><span data-stu-id="dddc4-111">Controls the state of files and directories.</span></span> <span data-ttu-id="dddc4-112">Copia i file da un **origine** a un **destinazione** e li aggiorna quando il **origine** modifiche confrontando le date, i valori di checksum e hash.</span><span class="sxs-lookup"><span data-stu-id="dddc4-112">Copies files from a **Source** to a **Destination** and updates them when the **Source** changes by comparing dates, checksums, and hashes.</span></span>|
|<span data-ttu-id="dddc4-113">**Archive**</span><span class="sxs-lookup"><span data-stu-id="dddc4-113">**Archive**</span></span>|<span data-ttu-id="dddc4-114">È possibile decomprimere archivi e una posizione specificata.</span><span class="sxs-lookup"><span data-stu-id="dddc4-114">Unpacks archives and a specified location.</span></span> <span data-ttu-id="dddc4-115">Convalida gli archivi con un oggetto specificato **Checksum**.</span><span class="sxs-lookup"><span data-stu-id="dddc4-115">Validates the archives with a specified **Checksum**.</span></span>|
|<span data-ttu-id="dddc4-116">**Environment**</span><span class="sxs-lookup"><span data-stu-id="dddc4-116">**Environment**</span></span>|<span data-ttu-id="dddc4-117">Gestisce le variabili di ambiente.</span><span class="sxs-lookup"><span data-stu-id="dddc4-117">Manages environment variables.</span></span>|
|<span data-ttu-id="dddc4-118">**Gruppo**</span><span class="sxs-lookup"><span data-stu-id="dddc4-118">**Group**</span></span>|<span data-ttu-id="dddc4-119">Gestisce i gruppi locali e controlla l'appartenenza al gruppo.</span><span class="sxs-lookup"><span data-stu-id="dddc4-119">Manages local groups and controls group membership.</span></span>|
|<span data-ttu-id="dddc4-120">**Log**</span><span class="sxs-lookup"><span data-stu-id="dddc4-120">**Log**</span></span>|<span data-ttu-id="dddc4-121">Scrive i messaggi per il `Microsoft-Windows-Desired State Configuration/Analytic` registro eventi.</span><span class="sxs-lookup"><span data-stu-id="dddc4-121">Writes messages to the `Microsoft-Windows-Desired State Configuration/Analytic` event log.</span></span>|
|<span data-ttu-id="dddc4-122">**Pacchetto**</span><span class="sxs-lookup"><span data-stu-id="dddc4-122">**Package**</span></span>|<span data-ttu-id="dddc4-123">Installa o disinstalla pacchetti usando **argomenti**, **LogPath**, **ReturnCode**, le altre impostazioni.</span><span class="sxs-lookup"><span data-stu-id="dddc4-123">Installs or uninstalls packages using **Arguments**, **LogPath**, **ReturnCode**, other settings.</span></span>|
|<span data-ttu-id="dddc4-124">**Registry**</span><span class="sxs-lookup"><span data-stu-id="dddc4-124">**Registry**</span></span>|<span data-ttu-id="dddc4-125">Gestisce i valori e le chiavi del Registro di sistema.</span><span class="sxs-lookup"><span data-stu-id="dddc4-125">Manages registry keys and values.</span></span>|
|<span data-ttu-id="dddc4-126">**Script**</span><span class="sxs-lookup"><span data-stu-id="dddc4-126">**Script**</span></span>|<span data-ttu-id="dddc4-127">Consente di progettare il proprio [get-test-set](../resources/get-test-set.md) blocchi di script.</span><span class="sxs-lookup"><span data-stu-id="dddc4-127">Allows you to design your own [get-test-set](../resources/get-test-set.md) script blocks.</span></span>|
|<span data-ttu-id="dddc4-128">**Service**</span><span class="sxs-lookup"><span data-stu-id="dddc4-128">**Service**</span></span>|<span data-ttu-id="dddc4-129">Configura i servizi di Windows.</span><span class="sxs-lookup"><span data-stu-id="dddc4-129">Configures Windows services.</span></span>|
|<span data-ttu-id="dddc4-130">**User**</span><span class="sxs-lookup"><span data-stu-id="dddc4-130">**User**</span></span> |<span data-ttu-id="dddc4-131">Gestisce gli attributi e gli utenti locali.</span><span class="sxs-lookup"><span data-stu-id="dddc4-131">Manages local users and attributes.</span></span>|
|<span data-ttu-id="dddc4-132">**WindowsFeature**</span><span class="sxs-lookup"><span data-stu-id="dddc4-132">**WindowsFeature**</span></span>|<span data-ttu-id="dddc4-133">Consente di gestire ruoli e funzionalità.</span><span class="sxs-lookup"><span data-stu-id="dddc4-133">Manages roles and features.</span></span>|
|<span data-ttu-id="dddc4-134">**WindowsProcess**</span><span class="sxs-lookup"><span data-stu-id="dddc4-134">**WindowsProcess**</span></span>|<span data-ttu-id="dddc4-135">Configura i processi di Windows.</span><span class="sxs-lookup"><span data-stu-id="dddc4-135">Configures Windows processes.</span></span>|

<span data-ttu-id="dddc4-136">Le risorse OOB consentono un buon punto di partenza per le operazioni comuni.</span><span class="sxs-lookup"><span data-stu-id="dddc4-136">The OOB resources allow a good starting point for common operations.</span></span> <span data-ttu-id="dddc4-137">Se le risorse OOB non soddisfano le proprie esigenze, è possibile scrivere il proprio [risorsa personalizzata](../resources/authoringResource.md).</span><span class="sxs-lookup"><span data-stu-id="dddc4-137">If the OOB resources do not meet your needs, you can write your own [Custom Resource](../resources/authoringResource.md).</span></span> <span data-ttu-id="dddc4-138">Prima di scrivere una risorsa personalizzata per risolvere i problemi, è necessario esaminare l'elevato numero di risorse DSC che sono già stati creati da Microsoft e la community di PowerShell.</span><span class="sxs-lookup"><span data-stu-id="dddc4-138">Before you write a custom resource to solve your problem, you should look through the vast number of DSC resources that have already been created by both Microsoft and the PowerShell community.</span></span>

<span data-ttu-id="dddc4-139">È possibile trovare risorse DSC in entrambe le [PowerShell Gallery](https://www.powershellgallery.com/) e [GitHub](https://github.com/).</span><span class="sxs-lookup"><span data-stu-id="dddc4-139">You can find DSC resources in both the [PowerShell Gallery](https://www.powershellgallery.com/) and [GitHub](https://github.com/).</span></span> <span data-ttu-id="dddc4-140">È anche possibile installare le risorse DSC direttamente dalla console di PowerShell usando [PowerShellGet](/powershell/module/powershellget/).</span><span class="sxs-lookup"><span data-stu-id="dddc4-140">You can also install DSC resources directly from the PowerShell console using [PowerShellGet](/powershell/module/powershellget/).</span></span>

## <a name="installing-powershellget"></a><span data-ttu-id="dddc4-141">Installazione di PowerShellGet</span><span class="sxs-lookup"><span data-stu-id="dddc4-141">Installing PowerShellGet</span></span>

<span data-ttu-id="dddc4-142">Per determinare se si ha già **PowerShell** ottenere o per ottenere assistenza installarlo, vedere la Guida seguente: [installazione PowerShellGet](/powershell/gallery/installing-psget).</span><span class="sxs-lookup"><span data-stu-id="dddc4-142">To determine if you already have **PowerShell** get, or to get help installing it, see the following guide: [Installing PowerShellGet](/powershell/gallery/installing-psget).</span></span>

## <a name="finding-dsc-resources-using-powershellget"></a><span data-ttu-id="dddc4-143">Trovare risorse DSC con PowerShellGet</span><span class="sxs-lookup"><span data-stu-id="dddc4-143">Finding DSC resources using PowerShellGet</span></span>

<span data-ttu-id="dddc4-144">Una volta **PowerShellGet** sia installato nel sistema, è possibile trovare e installare le risorse DSC ospitate nel [PowerShell Gallery](https://www.powershellgallery.com/).</span><span class="sxs-lookup"><span data-stu-id="dddc4-144">Once **PowerShellGet** is installed on your system, you can find and install DSC resources hosted in the [PowerShell Gallery](https://www.powershellgallery.com/).</span></span>

<span data-ttu-id="dddc4-145">In primo luogo, usare il [Find-DSCResource](/powershell/module/powershellget/find-dscresource) cmdlet per trovare le risorse DSC.</span><span class="sxs-lookup"><span data-stu-id="dddc4-145">First, use the [Find-DSCResource](/powershell/module/powershellget/find-dscresource) cmdlet to find DSC resources.</span></span> <span data-ttu-id="dddc4-146">Quando si esegue `Find-DSCResource` per la prima volta, viene visualizzata l'istruzione seguente per installare il provider"NuGet".</span><span class="sxs-lookup"><span data-stu-id="dddc4-146">When you run `Find-DSCResource` for the first time, you see the following prompt to install the "NuGet provider".</span></span>

```
PS> Find-DSCResource

NuGet provider is required to continue
PowerShellGet requires NuGet provider version '2.8.5.201' or newer to interact with NuGet-based repositories. The
NuGet provider must be available in 'C:\Program Files\PackageManagement\ProviderAssemblies' or
'C:\Users\xAdministrator\AppData\Local\PackageManagement\ProviderAssemblies'. You can also install the NuGet provider
 by running 'Install-PackageProvider -Name NuGet -MinimumVersion 2.8.5.201 -Force'. Do you want PowerShellGet to
install and import the NuGet provider now?
[Y] Yes  [N] No  [?] Help (default is "Y"):
```

<span data-ttu-id="dddc4-147">Dopo aver premuto "y", viene installato il provider "NuGet", viene visualizzato un elenco di risorse DSC che possano installare da PowerShell Gallery.</span><span class="sxs-lookup"><span data-stu-id="dddc4-147">After pressing 'y', the "NuGet" provider is installed, you see a list of DSC resources that you can install from the PowerShell Gallery.</span></span>

> [!NOTE]
> <span data-ttu-id="dddc4-148">Elenco non viene visualizzato perché è molto grande.</span><span class="sxs-lookup"><span data-stu-id="dddc4-148">List is not shown because it is very large.</span></span>

<span data-ttu-id="dddc4-149">È inoltre possibile specificare il `-Name` utilizzano caratteri jolly, parametro o `-Filter` parametro senza caratteri jolly per restringere la ricerca.</span><span class="sxs-lookup"><span data-stu-id="dddc4-149">You can also specify the `-Name` parameter using wildcards, or `-Filter` parameter without wildcards to narrow down your search.</span></span> <span data-ttu-id="dddc4-150">In questo esempio tenta di individuare una risorsa "Fuso orario" DSC usando i caratteri jolly.</span><span class="sxs-lookup"><span data-stu-id="dddc4-150">This example attempts to find a "TimeZone" DSC resource using the wildcards.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="dddc4-151">Attualmente c'è un bug nel `Find-DSCResource` cmdlet che impediscono di usare i caratteri jolly in entrambe le `-Name` e `-Filter` parametri.</span><span class="sxs-lookup"><span data-stu-id="dddc4-151">Currently there is a bug in the `Find-DSCResource` cmdlet that prevents using wildcards in both the `-Name` and `-Filter` parameters.</span></span> <span data-ttu-id="dddc4-152">Il secondo esempio riportato di seguito illustra una soluzione alternativa usando `Where-Object`.</span><span class="sxs-lookup"><span data-stu-id="dddc4-152">The second example below shows a workaround using `Where-Object`.</span></span>

```
PS> Find-DSCResource -Name *Time*

Name                                Version    ModuleName                          Repository
----                                -------    ----------                          ----------
Carbon_EnvironmentVariable          2.6.0      Carbon                              PSGallery
Carbon_FirewallRule                 2.6.0      Carbon                              PSGallery
Carbon_Group                        2.6.0      Carbon                              PSGallery
Carbon_IniFile                      2.6.0      Carbon                              PSGallery
Carbon_Permission                   2.6.0      Carbon                              PSGallery
Carbon_Privilege                    2.6.0      Carbon                              PSGallery
Carbon_ScheduledTask                2.6.0      Carbon                              PSGallery
Carbon_Service                      2.6.0      Carbon                              PSGallery
TimeZone                            6.0.0.0    ComputerManagementDsc               PSGallery
xTimeZone                           1.8.0.0    xTimeZone                           PSGallery
xSqlServerDefaultDir                1.0.0      mlSqlServerDSC                      PSGallery
xSqlServerMoveDatabaseFiles         1.0.0      mlSqlServerDSC                      PSGallery
xSqlServerSQLDataRoot               1.0.0      mlSqlServerDSC                      PSGallery
xSqlServerStartupParam              1.0.0      mlSqlServerDSC                      PSGallery
```

<span data-ttu-id="dddc4-153">È anche possibile usare `Where-Object` per trovare le risorse DSC con un filtro più granulare.</span><span class="sxs-lookup"><span data-stu-id="dddc4-153">You can also use `Where-Object` to find DSC resources with more granular filtering.</span></span> <span data-ttu-id="dddc4-154">Questo approccio sarà più lento rispetto all'uso di parametri di filtro incorporata.</span><span class="sxs-lookup"><span data-stu-id="dddc4-154">This approach will be slower than using built in filtering parameters.</span></span>

```
PS> Find-DSCResource | Where-Object {$_.Name -like "Time*"}

Name                                Version    ModuleName                          Repository
----                                -------    ----------                          ----------
TimeZone                            6.0.0.0    ComputerManagementDsc               PSGallery
```

<span data-ttu-id="dddc4-155">Per altre informazioni sui filtri, vedere [Where-Object](/powershell/module/microsoft.powershell.core/where-object).</span><span class="sxs-lookup"><span data-stu-id="dddc4-155">For more information on filtering, see [Where-Object](/powershell/module/microsoft.powershell.core/where-object).</span></span>

## <a name="installing-dsc-resources-using-powershellget"></a><span data-ttu-id="dddc4-156">Installazione di risorse DSC con PowerShellGet</span><span class="sxs-lookup"><span data-stu-id="dddc4-156">Installing DSC Resources using PowerShellGet</span></span>

<span data-ttu-id="dddc4-157">Per installare una risorsa DSC, usare il [Install-Module](/powershell/module/PowershellGet/Install-Module) cmdlet, che specifica il nome del modulo visualizzato sotto **modulo** nome nei risultati della ricerca.</span><span class="sxs-lookup"><span data-stu-id="dddc4-157">To install a DSC resource, use the [Install-Module](/powershell/module/PowershellGet/Install-Module) cmdlet, specifying the name of the module shown under **Module** name in your search results.</span></span>

<span data-ttu-id="dddc4-158">La risorsa "Fuso orario" presente nel modulo "ComputerManagementDSC", in modo che sia che il modulo viene installato in questo esempio.</span><span class="sxs-lookup"><span data-stu-id="dddc4-158">The "TimeZone" resource exists in the "ComputerManagementDSC" module, so that is the module this example installs.</span></span>

> [!NOTE]
> <span data-ttu-id="dddc4-159">Se PowerShell gallery non è considerato attendibile, viene visualizzato l'avviso seguente in cui viene chiesto di confermare l'operazione e che indica come evitare le richieste successive su Installa.</span><span class="sxs-lookup"><span data-stu-id="dddc4-159">If you have not trusted the PowerShell gallery, you see the warning below asking for confirmation, and instructing you how to avoid subsequent prompts on installs.</span></span>

```
PS> Install-Module -Name ComputerManagementDSC

Untrusted repository
You are installing the modules from an untrusted repository. If you trust this repository, change its
InstallationPolicy value by running the Set-PSRepository cmdlet. Are you sure you want to install the modules from
'PSGallery'?
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "N"):
```

<span data-ttu-id="dddc4-160">Premere 'y' per continuare a installare il modulo.</span><span class="sxs-lookup"><span data-stu-id="dddc4-160">Press 'y' to continue installing the module.</span></span> <span data-ttu-id="dddc4-161">Dopo l'installazione, è possibile verificare che la nuova risorsa venga installata seguendo [Get-DSCResource](/powershell/module/PSDesiredStateConfiguration/Get-DscResource).</span><span class="sxs-lookup"><span data-stu-id="dddc4-161">After install, you can verify that your new resource is installed using [Get-DSCResource](/powershell/module/PSDesiredStateConfiguration/Get-DscResource).</span></span>

```
PS> Get-DSCResource -Name TimeZone -Syntax

TimeZone [String] #ResourceName
{
    IsSingleInstance = [string]{ Yes }
    TimeZone = [string]
    [DependsOn = [string[]]]
    [PsDscRunAsCredential = [PSCredential]]
}
```

<span data-ttu-id="dddc4-162">È inoltre possibile visualizzare altre risorse nel modulo appena installato, specificando il `-ModuleName` parametro.</span><span class="sxs-lookup"><span data-stu-id="dddc4-162">You can also view other resources in your newly installed module, by specifying the `-ModuleName` parameter.</span></span>

```
PS> Get-DSCResource -Module ComputerManagementDSC

ImplementedAs   Name                      ModuleName                     Version    Properties
-------------   ----                      ----------                     -------    ----------
PowerShell      Computer                  ComputerManagementDsc          6.0.0.0    {Name, Credential, DependsOn, ...
PowerShell      OfflineDomainJoin         ComputerManagementDsc          6.0.0.0    {IsSingleInstance, RequestFile...
PowerShell      PowerPlan                 ComputerManagementDsc          6.0.0.0    {IsSingleInstance, Name, Depen...
PowerShell      PowerShellExecutionPolicy ComputerManagementDsc          6.0.0.0    {ExecutionPolicy, ExecutionPol...
PowerShell      ScheduledTask             ComputerManagementDsc          6.0.0.0    {TaskName, ActionArguments, Ac...
PowerShell      TimeZone                  ComputerManagementDsc          6.0.0.0    {IsSingleInstance, TimeZone, D...
PowerShell      VirtualMemory             ComputerManagementDsc          6.0.0.0    {Drive, Type, DependsOn, Initi...
```

## <a name="see-also"></a><span data-ttu-id="dddc4-163">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="dddc4-163">See also</span></span>

- [<span data-ttu-id="dddc4-164">Che cosa sono le risorse?</span><span class="sxs-lookup"><span data-stu-id="dddc4-164">What are Resources?</span></span>](../resources/resources.md)
