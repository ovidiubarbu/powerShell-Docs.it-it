---
ms.date: 12/12/2018
keywords: dsc,powershell,risorsa,raccolta,configurazione
title: Installare risorse DSC aggiuntive
ms.openlocfilehash: 7a6a935349358e11a77d2f00c0bf88e0ad18c097
ms.sourcegitcommit: d43f66071f1f33b350d34fa1f46f3a35910c5d24
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 11/23/2019
ms.locfileid: "74417789"
---
# <a name="install-additional-dsc-resources"></a><span data-ttu-id="d72a2-103">Installare risorse DSC aggiuntive</span><span class="sxs-lookup"><span data-stu-id="d72a2-103">Install Additional DSC Resources</span></span>

<span data-ttu-id="d72a2-104">PowerShell include varie risorse predefinite per Desired State Configuration (DSC).</span><span class="sxs-lookup"><span data-stu-id="d72a2-104">PowerShell includes several Out-of-the-box resources for Desired State Configuration (DSC).</span></span> <span data-ttu-id="d72a2-105">Il modulo **PSDesiredStateConfiguration** contiene tutte le risorse DSC predefinite disponibili nell'istanza specifica di PowerShell.</span><span class="sxs-lookup"><span data-stu-id="d72a2-105">The **PSDesiredStateConfiguration** module contains all of the OOB DSC resources available on your specific instance of PowerShell.</span></span>

<span data-ttu-id="d72a2-106">Questo è un elenco delle risorse OOB incluse in PowerShell 4.0 e una descrizione delle funzionalità della risorsa.</span><span class="sxs-lookup"><span data-stu-id="d72a2-106">This is a list of the OOB resources included in PowerShell 4.0 and a description of the resource's capabilities.</span></span>

> [!NOTE]
> <span data-ttu-id="d72a2-107">Si tratta di un elenco incompleto, in quanto il numero di risorse OOB è aumentato con ogni versione di PowerShell.</span><span class="sxs-lookup"><span data-stu-id="d72a2-107">This is an incomplete list, as the number of OOB resources has grown with each version of PowerShell.</span></span>

|<span data-ttu-id="d72a2-108">Resource</span><span class="sxs-lookup"><span data-stu-id="d72a2-108">Resource</span></span>  |<span data-ttu-id="d72a2-109">Description</span><span class="sxs-lookup"><span data-stu-id="d72a2-109">Description</span></span>  |
|---------|---------|
|<span data-ttu-id="d72a2-110">**File**</span><span class="sxs-lookup"><span data-stu-id="d72a2-110">**File**</span></span>|<span data-ttu-id="d72a2-111">Controlla lo stato dei file e delle directory.</span><span class="sxs-lookup"><span data-stu-id="d72a2-111">Controls the state of files and directories.</span></span> <span data-ttu-id="d72a2-112">Copia i file da un'**origine** a una **destinazione** e li aggiorna quando l'**origine** viene modificata confrontando le date, i valori di checksum e gli hash.</span><span class="sxs-lookup"><span data-stu-id="d72a2-112">Copies files from a **Source** to a **Destination** and updates them when the **Source** changes by comparing dates, checksums, and hashes.</span></span>|
|<span data-ttu-id="d72a2-113">**Archive**</span><span class="sxs-lookup"><span data-stu-id="d72a2-113">**Archive**</span></span>|<span data-ttu-id="d72a2-114">Decomprime archivi e una posizione specificata.</span><span class="sxs-lookup"><span data-stu-id="d72a2-114">Unpacks archives and a specified location.</span></span> <span data-ttu-id="d72a2-115">Convalida gli archivi con un oggetto **Checksum** specificato.</span><span class="sxs-lookup"><span data-stu-id="d72a2-115">Validates the archives with a specified **Checksum**.</span></span>|
|<span data-ttu-id="d72a2-116">**Environment**</span><span class="sxs-lookup"><span data-stu-id="d72a2-116">**Environment**</span></span>|<span data-ttu-id="d72a2-117">Gestisce le variabili di ambiente.</span><span class="sxs-lookup"><span data-stu-id="d72a2-117">Manages environment variables.</span></span>|
|<span data-ttu-id="d72a2-118">**Gruppo**</span><span class="sxs-lookup"><span data-stu-id="d72a2-118">**Group**</span></span>|<span data-ttu-id="d72a2-119">Gestisce i gruppi locali e controlla l'appartenenza al gruppo.</span><span class="sxs-lookup"><span data-stu-id="d72a2-119">Manages local groups and controls group membership.</span></span>|
|<span data-ttu-id="d72a2-120">**Log**</span><span class="sxs-lookup"><span data-stu-id="d72a2-120">**Log**</span></span>|<span data-ttu-id="d72a2-121">Scrive i messaggi sul registro eventi `Microsoft-Windows-Desired State Configuration/Analytic`.</span><span class="sxs-lookup"><span data-stu-id="d72a2-121">Writes messages to the `Microsoft-Windows-Desired State Configuration/Analytic` event log.</span></span>|
|<span data-ttu-id="d72a2-122">**Pacchetto**</span><span class="sxs-lookup"><span data-stu-id="d72a2-122">**Package**</span></span>|<span data-ttu-id="d72a2-123">Installa o disinstalla i pacchetti usando **Arguments**, **LogPath**, **ReturnCode** e altre impostazioni.</span><span class="sxs-lookup"><span data-stu-id="d72a2-123">Installs or uninstalls packages using **Arguments**, **LogPath**, **ReturnCode**, other settings.</span></span>|
|<span data-ttu-id="d72a2-124">**Registry**</span><span class="sxs-lookup"><span data-stu-id="d72a2-124">**Registry**</span></span>|<span data-ttu-id="d72a2-125">Gestisce i valori e le chiavi del Registro di sistema.</span><span class="sxs-lookup"><span data-stu-id="d72a2-125">Manages registry keys and values.</span></span>|
|<span data-ttu-id="d72a2-126">**Script**</span><span class="sxs-lookup"><span data-stu-id="d72a2-126">**Script**</span></span>|<span data-ttu-id="d72a2-127">Consente di progettare il propri blocchi di script [get-test-set](../resources/get-test-set.md).</span><span class="sxs-lookup"><span data-stu-id="d72a2-127">Allows you to design your own [get-test-set](../resources/get-test-set.md) script blocks.</span></span>|
|<span data-ttu-id="d72a2-128">**Service**</span><span class="sxs-lookup"><span data-stu-id="d72a2-128">**Service**</span></span>|<span data-ttu-id="d72a2-129">Configura i servizi di Windows.</span><span class="sxs-lookup"><span data-stu-id="d72a2-129">Configures Windows services.</span></span>|
|<span data-ttu-id="d72a2-130">**User**</span><span class="sxs-lookup"><span data-stu-id="d72a2-130">**User**</span></span> |<span data-ttu-id="d72a2-131">Gestisce gli utenti e gli attributi locali.</span><span class="sxs-lookup"><span data-stu-id="d72a2-131">Manages local users and attributes.</span></span>|
|<span data-ttu-id="d72a2-132">**WindowsFeature**</span><span class="sxs-lookup"><span data-stu-id="d72a2-132">**WindowsFeature**</span></span>|<span data-ttu-id="d72a2-133">Gestisce i ruoli e le funzionalità.</span><span class="sxs-lookup"><span data-stu-id="d72a2-133">Manages roles and features.</span></span>|
|<span data-ttu-id="d72a2-134">**WindowsProcess**</span><span class="sxs-lookup"><span data-stu-id="d72a2-134">**WindowsProcess**</span></span>|<span data-ttu-id="d72a2-135">Configura i processi di Windows.</span><span class="sxs-lookup"><span data-stu-id="d72a2-135">Configures Windows processes.</span></span>|

<span data-ttu-id="d72a2-136">Le risorse OOB sono un buon punto di partenza per le operazioni comuni.</span><span class="sxs-lookup"><span data-stu-id="d72a2-136">The OOB resources allow a good starting point for common operations.</span></span> <span data-ttu-id="d72a2-137">Se le risorse OOB non soddisfano le proprie esigenze, è possibile scrivere una propria [risorsa personalizzata](../resources/authoringResource.md).</span><span class="sxs-lookup"><span data-stu-id="d72a2-137">If the OOB resources do not meet your needs, you can write your own [Custom Resource](../resources/authoringResource.md).</span></span> <span data-ttu-id="d72a2-138">Prima di scrivere una risorsa personalizzata per risolvere i problemi, è necessario esaminare l'elevato numero di risorse DSC che sono già state create dalla community Microsoft e PowerShell.</span><span class="sxs-lookup"><span data-stu-id="d72a2-138">Before you write a custom resource to solve your problem, you should look through the vast number of DSC resources that have already been created by both Microsoft and the PowerShell community.</span></span>

<span data-ttu-id="d72a2-139">È possibile trovare risorse DSC sia in [PowerShell Gallery](https://www.powershellgallery.com/) che in [GitHub](https://github.com/).</span><span class="sxs-lookup"><span data-stu-id="d72a2-139">You can find DSC resources in both the [PowerShell Gallery](https://www.powershellgallery.com/) and [GitHub](https://github.com/).</span></span> <span data-ttu-id="d72a2-140">È anche possibile installare le risorse DSC direttamente dalla console di PowerShell usando [PowerShellGet](/powershell/module/powershellget/).</span><span class="sxs-lookup"><span data-stu-id="d72a2-140">You can also install DSC resources directly from the PowerShell console using [PowerShellGet](/powershell/module/powershellget/).</span></span>

## <a name="installing-powershellget"></a><span data-ttu-id="d72a2-141">Installazione di PowerShellGet</span><span class="sxs-lookup"><span data-stu-id="d72a2-141">Installing PowerShellGet</span></span>

<span data-ttu-id="d72a2-142">Per determinare se si ha già **PowerShellGet** o per ottenere assistenza nell'installazione, vedere la guida seguente: [Installazione di PowerShellGet](/powershell/scripting/gallery/installing-psget).</span><span class="sxs-lookup"><span data-stu-id="d72a2-142">To determine if you already have **PowerShell** get, or to get help installing it, see the following guide: [Installing PowerShellGet](/powershell/scripting/gallery/installing-psget).</span></span>

## <a name="finding-dsc-resources-using-powershellget"></a><span data-ttu-id="d72a2-143">Trovare risorse DSC con PowerShellGet</span><span class="sxs-lookup"><span data-stu-id="d72a2-143">Finding DSC resources using PowerShellGet</span></span>

<span data-ttu-id="d72a2-144">Una volta eseguita l'installazione di **PowerShellGet** nel sistema, è possibile trovare e installare le risorse DSC ospitate in [PowerShell Gallery](https://www.powershellgallery.com/).</span><span class="sxs-lookup"><span data-stu-id="d72a2-144">Once **PowerShellGet** is installed on your system, you can find and install DSC resources hosted in the [PowerShell Gallery](https://www.powershellgallery.com/).</span></span>

<span data-ttu-id="d72a2-145">In primo luogo, usare il cmdlet [Find-DSCResource](/powershell/module/powershellget/find-dscresource) per trovare le risorse DSC.</span><span class="sxs-lookup"><span data-stu-id="d72a2-145">First, use the [Find-DSCResource](/powershell/module/powershellget/find-dscresource) cmdlet to find DSC resources.</span></span> <span data-ttu-id="d72a2-146">Quando si esegue `Find-DSCResource` per la prima volta, viene visualizzato il seguente messaggio per installare il "provider NuGet".</span><span class="sxs-lookup"><span data-stu-id="d72a2-146">When you run `Find-DSCResource` for the first time, you see the following prompt to install the "NuGet provider".</span></span>

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

<span data-ttu-id="d72a2-147">Dopo aver premuto "Y", viene installato il provider "NuGet" e viene visualizzato un elenco di risorse DSC che è possibile installare da PowerShell Gallery.</span><span class="sxs-lookup"><span data-stu-id="d72a2-147">After pressing 'y', the "NuGet" provider is installed, you see a list of DSC resources that you can install from the PowerShell Gallery.</span></span>

> [!NOTE]
> <span data-ttu-id="d72a2-148">L'elenco non viene visualizzato perché è molto grande.</span><span class="sxs-lookup"><span data-stu-id="d72a2-148">List is not shown because it is very large.</span></span>

<span data-ttu-id="d72a2-149">È inoltre possibile specificare il parametro `-Name` usando caratteri jolly o il parametro `-Filter` senza caratteri jolly per restringere la ricerca.</span><span class="sxs-lookup"><span data-stu-id="d72a2-149">You can also specify the `-Name` parameter using wildcards, or `-Filter` parameter without wildcards to narrow down your search.</span></span> <span data-ttu-id="d72a2-150">Questo esempio tenta di individuare una risorsa DSC "TimeZone" usando i caratteri jolly.</span><span class="sxs-lookup"><span data-stu-id="d72a2-150">This example attempts to find a "TimeZone" DSC resource using the wildcards.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="d72a2-151">Attualmente nel cmdlet `Find-DSCResource` è presente un bug che impedisce di usare i caratteri jolly nei parametri `-Name` e `-Filter`.</span><span class="sxs-lookup"><span data-stu-id="d72a2-151">Currently there is a bug in the `Find-DSCResource` cmdlet that prevents using wildcards in both the `-Name` and `-Filter` parameters.</span></span> <span data-ttu-id="d72a2-152">Il secondo esempio riportato di seguito illustra una soluzione alternativa usando `Where-Object`.</span><span class="sxs-lookup"><span data-stu-id="d72a2-152">The second example below shows a workaround using `Where-Object`.</span></span>

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

<span data-ttu-id="d72a2-153">È anche possibile usare `Where-Object` per trovare le risorse DSC con un filtro più granulare.</span><span class="sxs-lookup"><span data-stu-id="d72a2-153">You can also use `Where-Object` to find DSC resources with more granular filtering.</span></span> <span data-ttu-id="d72a2-154">Questo approccio sarà più lento rispetto all'uso di parametri di filtro incorporati.</span><span class="sxs-lookup"><span data-stu-id="d72a2-154">This approach will be slower than using built in filtering parameters.</span></span>

```
PS> Find-DSCResource | Where-Object {$_.Name -like "Time*"}

Name                                Version    ModuleName                          Repository
----                                -------    ----------                          ----------
TimeZone                            6.0.0.0    ComputerManagementDsc               PSGallery
```

<span data-ttu-id="d72a2-155">Per altre informazioni sui filtri, vedere [Where-Object](/powershell/module/microsoft.powershell.core/where-object).</span><span class="sxs-lookup"><span data-stu-id="d72a2-155">For more information on filtering, see [Where-Object](/powershell/module/microsoft.powershell.core/where-object).</span></span>

## <a name="installing-dsc-resources-using-powershellget"></a><span data-ttu-id="d72a2-156">Installazione di risorse DSC con PowerShellGet</span><span class="sxs-lookup"><span data-stu-id="d72a2-156">Installing DSC Resources using PowerShellGet</span></span>

<span data-ttu-id="d72a2-157">Per installare una risorsa DSC, usare il cmdlet [Install-Module](/powershell/module/PowershellGet/Install-Module), che specifica il nome del modulo visualizzato nel nome **Modulo** nei risultati della ricerca.</span><span class="sxs-lookup"><span data-stu-id="d72a2-157">To install a DSC resource, use the [Install-Module](/powershell/module/PowershellGet/Install-Module) cmdlet, specifying the name of the module shown under **Module** name in your search results.</span></span>

<span data-ttu-id="d72a2-158">La risorsa "TimeZone" esiste nel modulo "ComputerManagementDSC", pertanto questo è il modulo installato in questo esempio.</span><span class="sxs-lookup"><span data-stu-id="d72a2-158">The "TimeZone" resource exists in the "ComputerManagementDSC" module, so that is the module this example installs.</span></span>

> [!NOTE]
> <span data-ttu-id="d72a2-159">Se PowerShell Gallery non è considerato attendibile, viene visualizzato l'avviso seguente in cui viene chiesto di confermare l'operazione e che indica come evitare le richieste successive durante le installazioni.</span><span class="sxs-lookup"><span data-stu-id="d72a2-159">If you have not trusted the PowerShell gallery, you see the warning below asking for confirmation, and instructing you how to avoid subsequent prompts on installs.</span></span>

```
PS> Install-Module -Name ComputerManagementDSC

Untrusted repository
You are installing the modules from an untrusted repository. If you trust this repository, change its
InstallationPolicy value by running the Set-PSRepository cmdlet. Are you sure you want to install the modules from
'PSGallery'?
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "N"):
```

<span data-ttu-id="d72a2-160">Premere 'y' per continuare l'installazione del modulo.</span><span class="sxs-lookup"><span data-stu-id="d72a2-160">Press 'y' to continue installing the module.</span></span> <span data-ttu-id="d72a2-161">Dopo l'installazione, è possibile verificare che la nuova risorsa sia installata mediante [Get-DSCResource](/powershell/module/PSDesiredStateConfiguration/Get-DscResource).</span><span class="sxs-lookup"><span data-stu-id="d72a2-161">After install, you can verify that your new resource is installed using [Get-DSCResource](/powershell/module/PSDesiredStateConfiguration/Get-DscResource).</span></span>

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

<span data-ttu-id="d72a2-162">È inoltre possibile visualizzare altre risorse nel modulo appena installato, specificando il parametro`-ModuleName`.</span><span class="sxs-lookup"><span data-stu-id="d72a2-162">You can also view other resources in your newly installed module, by specifying the `-ModuleName` parameter.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="d72a2-163">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="d72a2-163">See also</span></span>

- [<span data-ttu-id="d72a2-164">Che cosa sono le risorse?</span><span class="sxs-lookup"><span data-stu-id="d72a2-164">What are Resources?</span></span>](../resources/resources.md)
