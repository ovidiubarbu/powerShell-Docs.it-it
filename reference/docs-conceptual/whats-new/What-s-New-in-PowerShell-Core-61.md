---
title: Novità di PowerShell Core 6.1
description: Nuove funzionalità e modifiche rilasciate in PowerShell Core 6.1
ms.date: 09/13/2018
ms.openlocfilehash: 3d836a24b494df9c7f6ebe994386e2a0297521fa
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 12/05/2019
ms.locfileid: "62086139"
---
# <a name="whats-new-in-powershell-core-61"></a><span data-ttu-id="ae1ac-103">Novità di PowerShell Core 6.1</span><span class="sxs-lookup"><span data-stu-id="ae1ac-103">What's New in PowerShell Core 6.1</span></span>

<span data-ttu-id="ae1ac-104">Di seguito è riportata una selezione di alcune delle nuove funzionalità e modifiche più importanti introdotte in PowerShell Core 6.1.</span><span class="sxs-lookup"><span data-stu-id="ae1ac-104">Below is a selection of some of the major new features and changes that have been introduced in PowerShell Core 6.1.</span></span>

<span data-ttu-id="ae1ac-105">Sono state introdotte anche **moltissime** "cose noiose" che rendono PowerShell più veloce e più stabile, oltre ad altrettante correzioni di bug.</span><span class="sxs-lookup"><span data-stu-id="ae1ac-105">There's also **tons** of "boring stuff" that make PowerShell faster and more stable (plus lots and lots of bug fixes)!</span></span>
<span data-ttu-id="ae1ac-106">Per un elenco completo delle modifiche, consultare il [log delle modifiche](https://github.com/PowerShell/PowerShell/blob/master/CHANGELOG.md) su GitHub.</span><span class="sxs-lookup"><span data-stu-id="ae1ac-106">For a full list of changes, check out our [changelog on GitHub](https://github.com/PowerShell/PowerShell/blob/master/CHANGELOG.md).</span></span>

<span data-ttu-id="ae1ac-107">Riportiamo alcuni nomi di seguito, ma vogliamo ringraziare [tutti i collaboratori della community](https://github.com/PowerShell/PowerShell/graphs/contributors) che hanno reso possibile questa versione.</span><span class="sxs-lookup"><span data-stu-id="ae1ac-107">And while we call out some names below, thank you to [all of the community contributors](https://github.com/PowerShell/PowerShell/graphs/contributors) that made this release possible.</span></span>

## <a name="net-core-21"></a><span data-ttu-id="ae1ac-108">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="ae1ac-108">.NET Core 2.1</span></span>

<span data-ttu-id="ae1ac-109">PowerShell Core 6.1 è passato a .NET Core 2.1 dopo il [rilascio di maggio](https://blogs.msdn.microsoft.com/dotnet/2018/05/30/announcing-net-core-2-1/), con l'introduzione di una serie di miglioramenti in PowerShell, tra cui:</span><span class="sxs-lookup"><span data-stu-id="ae1ac-109">PowerShell Core 6.1 moved to .NET Core 2.1 after it was [released in May](https://blogs.msdn.microsoft.com/dotnet/2018/05/30/announcing-net-core-2-1/), resulting in a number of improvements to PowerShell, including:</span></span>

- <span data-ttu-id="ae1ac-110">miglioramenti delle prestazioni (vedere [di seguito](#performance-improvements))</span><span class="sxs-lookup"><span data-stu-id="ae1ac-110">performance improvements (see [below](#performance-improvements))</span></span>
- <span data-ttu-id="ae1ac-111">supporto per Alpine Linux (anteprima)</span><span class="sxs-lookup"><span data-stu-id="ae1ac-111">Alpine Linux support (preview)</span></span>
- <span data-ttu-id="ae1ac-112">[supporto globale per lo strumento di .NET](/dotnet/core/tools/global-tools), prossimamente in PowerShell</span><span class="sxs-lookup"><span data-stu-id="ae1ac-112">[.NET global tool support](/dotnet/core/tools/global-tools) - coming soon to PowerShell</span></span>
- [`Span<T>`](/dotnet/api/system.span-1?view=netcore-2.1)

## <a name="windows-compatibility-pack-for-net-core"></a><span data-ttu-id="ae1ac-113">Windows Compatibility Pack per .NET Core</span><span class="sxs-lookup"><span data-stu-id="ae1ac-113">Windows Compatibility Pack for .NET Core</span></span>

<span data-ttu-id="ae1ac-114">In Windows il team di .NET ha rilasciato il [Windows Compatibility Pack per .NET Core](https://blogs.msdn.microsoft.com/dotnet/2017/11/16/announcing-the-windows-compatibility-pack-for-net-core/), un set di assembly che ha aggiunto di nuovo diverse API rimosse a .NET Core in Windows.</span><span class="sxs-lookup"><span data-stu-id="ae1ac-114">On Windows, the .NET team shipped the [Windows Compatibility Pack for .NET Core](https://blogs.msdn.microsoft.com/dotnet/2017/11/16/announcing-the-windows-compatibility-pack-for-net-core/), a set of assemblies that add a number of removed APIs back to .NET Core on Windows.</span></span>

<span data-ttu-id="ae1ac-115">Il Windows Compatibility Pack è stato aggiunto alla versione 6.1 di PowerShell Core in modo che tutti i moduli o script che usano tali API possano contare sulla disponibilità delle stesse.</span><span class="sxs-lookup"><span data-stu-id="ae1ac-115">We've added the Windows Compatibility Pack to PowerShell Core 6.1 release so that any modules or scripts that use these APIs can rely on them being available.</span></span>

<span data-ttu-id="ae1ac-116">Il Windows Compatibility Pack consente a PowerShell Core di usare **più di 1900 cmdlet accluse all'aggiornamento di ottobre 2018 di Windows 10 e a Windows Server 2019**.</span><span class="sxs-lookup"><span data-stu-id="ae1ac-116">The Windows Compatibility Pack enables PowerShell Core to use **more than 1900 cmdlets that ship with Windows 10 October 2018 Update and Windows Server 2019**.</span></span>

## <a name="support-for-application-whitelisting"></a><span data-ttu-id="ae1ac-117">Supporto per l'inserimento delle applicazioni nell'elenco degli elementi consentiti</span><span class="sxs-lookup"><span data-stu-id="ae1ac-117">Support for Application Whitelisting</span></span>

<span data-ttu-id="ae1ac-118">PowerShell Core 6.1 offre lo stesso supporto di Windows PowerShell 5.1 per l'inserimento delle applicazioni nell'elenco elementi consentiti con [AppLocker](https://docs.microsoft.com/windows/security/threat-protection/windows-defender-application-control/applocker/applocker-overview) e [Device Guard](https://docs.microsoft.com/windows/security/threat-protection/device-guard/introduction-to-device-guard-virtualization-based-security-and-windows-defender-application-control).</span><span class="sxs-lookup"><span data-stu-id="ae1ac-118">PowerShell Core 6.1 has parity with Windows PowerShell 5.1 supporting [AppLocker](https://docs.microsoft.com/windows/security/threat-protection/windows-defender-application-control/applocker/applocker-overview) and [Device Guard](https://docs.microsoft.com/windows/security/threat-protection/device-guard/introduction-to-device-guard-virtualization-based-security-and-windows-defender-application-control) application whitelisting.</span></span>
<span data-ttu-id="ae1ac-119">L'inserimento delle applicazioni nell'elenco degli elementi consentiti offre un controllo granulare dei file binari di cui è consentita l'esecuzione con la sono possono essere eseguiti usato con il [linguaggio vincolato](https://blogs.msdn.microsoft.com/powershell/2017/11/02/powershell-constrained-language-mode/) di PowerShell.</span><span class="sxs-lookup"><span data-stu-id="ae1ac-119">Application whitelisting allows granular control of what binaries are allowed to be executed used with PowerShell [Constrained Language mode](https://blogs.msdn.microsoft.com/powershell/2017/11/02/powershell-constrained-language-mode/).</span></span>

## <a name="performance-improvements"></a><span data-ttu-id="ae1ac-120">Miglioramenti delle prestazioni</span><span class="sxs-lookup"><span data-stu-id="ae1ac-120">Performance improvements</span></span>

<span data-ttu-id="ae1ac-121">In PowerShell Core 6.0 sono stati apportati alcuni miglioramenti significativi delle prestazioni.</span><span class="sxs-lookup"><span data-stu-id="ae1ac-121">PowerShell Core 6.0 made some significant performance improvements.</span></span>
<span data-ttu-id="ae1ac-122">PowerShell Core 6.1 continua a migliorare la velocità di determinate operazioni.</span><span class="sxs-lookup"><span data-stu-id="ae1ac-122">PowerShell Core 6.1 continues to improve the speed of certain operations.</span></span>

<span data-ttu-id="ae1ac-123">Ad esempio, la velocità di `Group-Object` è aumentata del 66%:</span><span class="sxs-lookup"><span data-stu-id="ae1ac-123">For example, `Group-Object` has been sped up by 66%:</span></span>

```powershell
Measure-Command { 1..100000 | % {Get-Random -Minimum 1 -Maximum 10000} | Group-Object }
```

|              | <span data-ttu-id="ae1ac-124">Windows PowerShell 5.1</span><span class="sxs-lookup"><span data-stu-id="ae1ac-124">Windows PowerShell 5.1</span></span> | <span data-ttu-id="ae1ac-125">PowerShell Core 6.0</span><span class="sxs-lookup"><span data-stu-id="ae1ac-125">PowerShell Core 6.0</span></span> | <span data-ttu-id="ae1ac-126">PowerShell Core 6.1</span><span class="sxs-lookup"><span data-stu-id="ae1ac-126">PowerShell Core 6.1</span></span> |
|--------------|------------------------|---------------------|---------------------|
| <span data-ttu-id="ae1ac-127">Tempo (sec)</span><span class="sxs-lookup"><span data-stu-id="ae1ac-127">Time (sec)</span></span>   | <span data-ttu-id="ae1ac-128">25,178</span><span class="sxs-lookup"><span data-stu-id="ae1ac-128">25.178</span></span>                 | <span data-ttu-id="ae1ac-129">19,653</span><span class="sxs-lookup"><span data-stu-id="ae1ac-129">19.653</span></span>              | <span data-ttu-id="ae1ac-130">6,641</span><span class="sxs-lookup"><span data-stu-id="ae1ac-130">6.641</span></span>               |
| <span data-ttu-id="ae1ac-131">Accelerazione (%)</span><span class="sxs-lookup"><span data-stu-id="ae1ac-131">Speed-up (%)</span></span> | <span data-ttu-id="ae1ac-132">N/D</span><span class="sxs-lookup"><span data-stu-id="ae1ac-132">N/A</span></span>                    | <span data-ttu-id="ae1ac-133">21,9%</span><span class="sxs-lookup"><span data-stu-id="ae1ac-133">21.9%</span></span>               | <span data-ttu-id="ae1ac-134">66,2%</span><span class="sxs-lookup"><span data-stu-id="ae1ac-134">66.2%</span></span>               |

<span data-ttu-id="ae1ac-135">Analogamente, gli scenari di ordinamento come questo sono stati migliorati di oltre il 15%:</span><span class="sxs-lookup"><span data-stu-id="ae1ac-135">Similarly, sorting scenarios like this one have improved by more than 15%:</span></span>

```powershell
Measure-Command { 1..100000 | % {Get-Random -Minimum 1 -Maximum 10000} | Sort-Object }
```

|              | <span data-ttu-id="ae1ac-136">Windows PowerShell 5.1</span><span class="sxs-lookup"><span data-stu-id="ae1ac-136">Windows PowerShell 5.1</span></span> | <span data-ttu-id="ae1ac-137">PowerShell Core 6.0</span><span class="sxs-lookup"><span data-stu-id="ae1ac-137">PowerShell Core 6.0</span></span> | <span data-ttu-id="ae1ac-138">PowerShell Core 6.1</span><span class="sxs-lookup"><span data-stu-id="ae1ac-138">PowerShell Core 6.1</span></span> |
|--------------|------------------------|---------------------|---------------------|
| <span data-ttu-id="ae1ac-139">Tempo (sec)</span><span class="sxs-lookup"><span data-stu-id="ae1ac-139">Time (sec)</span></span>   | <span data-ttu-id="ae1ac-140">12,170</span><span class="sxs-lookup"><span data-stu-id="ae1ac-140">12.170</span></span>                 | <span data-ttu-id="ae1ac-141">8,493</span><span class="sxs-lookup"><span data-stu-id="ae1ac-141">8.493</span></span>               | <span data-ttu-id="ae1ac-142">7,08</span><span class="sxs-lookup"><span data-stu-id="ae1ac-142">7.08</span></span>                |
| <span data-ttu-id="ae1ac-143">Accelerazione (%)</span><span class="sxs-lookup"><span data-stu-id="ae1ac-143">Speed-up (%)</span></span> | <span data-ttu-id="ae1ac-144">N/D</span><span class="sxs-lookup"><span data-stu-id="ae1ac-144">N/A</span></span>                    | <span data-ttu-id="ae1ac-145">30,2%</span><span class="sxs-lookup"><span data-stu-id="ae1ac-145">30.2%</span></span>               | <span data-ttu-id="ae1ac-146">16,6%</span><span class="sxs-lookup"><span data-stu-id="ae1ac-146">16.6%</span></span>               |

<span data-ttu-id="ae1ac-147">`Import-Csv` è stato accelerato notevolmente anche dopo una regressione da Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="ae1ac-147">`Import-Csv` has also been sped up significantly after a regression from Windows PowerShell.</span></span>
<span data-ttu-id="ae1ac-148">L'esempio seguente usa un CSV di prova con 26.616 righe e sei colonne:</span><span class="sxs-lookup"><span data-stu-id="ae1ac-148">The following example uses a test CSV with 26,616 rows and six columns:</span></span>

```powershell
Measure-Command {$a = Import-Csv foo.csv}
```

|              | <span data-ttu-id="ae1ac-149">Windows PowerShell 5.1</span><span class="sxs-lookup"><span data-stu-id="ae1ac-149">Windows PowerShell 5.1</span></span> | <span data-ttu-id="ae1ac-150">PowerShell Core 6.0</span><span class="sxs-lookup"><span data-stu-id="ae1ac-150">PowerShell Core 6.0</span></span> | <span data-ttu-id="ae1ac-151">PowerShell Core 6.1</span><span class="sxs-lookup"><span data-stu-id="ae1ac-151">PowerShell Core 6.1</span></span>    |
|--------------|------------------------|---------------------|------------------------|
| <span data-ttu-id="ae1ac-152">Tempo (sec)</span><span class="sxs-lookup"><span data-stu-id="ae1ac-152">Time (sec)</span></span>   | <span data-ttu-id="ae1ac-153">0,441</span><span class="sxs-lookup"><span data-stu-id="ae1ac-153">0.441</span></span>                  | <span data-ttu-id="ae1ac-154">1,069</span><span class="sxs-lookup"><span data-stu-id="ae1ac-154">1.069</span></span>               | <span data-ttu-id="ae1ac-155">0,268</span><span class="sxs-lookup"><span data-stu-id="ae1ac-155">0.268</span></span>                  |
| <span data-ttu-id="ae1ac-156">Accelerazione (%)</span><span class="sxs-lookup"><span data-stu-id="ae1ac-156">Speed-up (%)</span></span> | <span data-ttu-id="ae1ac-157">N/D</span><span class="sxs-lookup"><span data-stu-id="ae1ac-157">N/A</span></span>                    | <span data-ttu-id="ae1ac-158">-142,4%</span><span class="sxs-lookup"><span data-stu-id="ae1ac-158">-142.4%</span></span>             | <span data-ttu-id="ae1ac-159">74,9% (39,2% da WPS)</span><span class="sxs-lookup"><span data-stu-id="ae1ac-159">74.9% (39.2% from WPS)</span></span> |

<span data-ttu-id="ae1ac-160">Infine, la conversione da JSON in `PSObject` è stata accelerata di oltre il 50% dopo Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="ae1ac-160">Lastly, conversion from JSON into `PSObject` has been sped up by more than 50% since Windows PowerShell.</span></span>
<span data-ttu-id="ae1ac-161">L'esempio seguente usa un file JSON di test di ~ 2MB:</span><span class="sxs-lookup"><span data-stu-id="ae1ac-161">The following example uses a ~2MB test JSON file:</span></span>

```powershell
Measure-Command {Get-Content .\foo.json | ConvertFrom-Json}
```

|              | <span data-ttu-id="ae1ac-162">Windows PowerShell 5.1</span><span class="sxs-lookup"><span data-stu-id="ae1ac-162">Windows PowerShell 5.1</span></span> | <span data-ttu-id="ae1ac-163">PowerShell Core 6.0</span><span class="sxs-lookup"><span data-stu-id="ae1ac-163">PowerShell Core 6.0</span></span> | <span data-ttu-id="ae1ac-164">PowerShell Core 6.1</span><span class="sxs-lookup"><span data-stu-id="ae1ac-164">PowerShell Core 6.1</span></span>    |
|--------------|------------------------|---------------------|------------------------|
| <span data-ttu-id="ae1ac-165">Tempo (sec)</span><span class="sxs-lookup"><span data-stu-id="ae1ac-165">Time (sec)</span></span>   | <span data-ttu-id="ae1ac-166">0,259</span><span class="sxs-lookup"><span data-stu-id="ae1ac-166">0.259</span></span>                  | <span data-ttu-id="ae1ac-167">0,577</span><span class="sxs-lookup"><span data-stu-id="ae1ac-167">0.577</span></span>               | <span data-ttu-id="ae1ac-168">0,125</span><span class="sxs-lookup"><span data-stu-id="ae1ac-168">0.125</span></span>                  |
| <span data-ttu-id="ae1ac-169">Accelerazione (%)</span><span class="sxs-lookup"><span data-stu-id="ae1ac-169">Speed-up (%)</span></span> | <span data-ttu-id="ae1ac-170">N/D</span><span class="sxs-lookup"><span data-stu-id="ae1ac-170">N/A</span></span>                    | <span data-ttu-id="ae1ac-171">-122,8%</span><span class="sxs-lookup"><span data-stu-id="ae1ac-171">-122.8%</span></span>             | <span data-ttu-id="ae1ac-172">78,3% (51,7% da WPS)</span><span class="sxs-lookup"><span data-stu-id="ae1ac-172">78.3% (51.7% from WPS)</span></span> |

## <a name="check-system32-for-compatible-in-box-modules-on-windows"></a><span data-ttu-id="ae1ac-173">Verificare in `system32` se sono inclusi moduli compatibili in Windows</span><span class="sxs-lookup"><span data-stu-id="ae1ac-173">Check `system32` for compatible in-box modules on Windows</span></span>

<span data-ttu-id="ae1ac-174">Nell'aggiornamento 1809 di Windows 10 e in Windows Server 2019 sono stati aggiornati diversi moduli inclusi in PowerShell in modo da contrassegnarli come compatibili con PowerShell Core.</span><span class="sxs-lookup"><span data-stu-id="ae1ac-174">In the Windows 10 1809 update and Windows Server 2019, we updated a number of in-box PowerShell modules to mark them as compatible with PowerShell Core.</span></span>

<span data-ttu-id="ae1ac-175">All'avvio, PowerShell Core 6.1 includerà automaticamente `$windir\System32` come parte della variabile di ambiente `PSModulePath`.</span><span class="sxs-lookup"><span data-stu-id="ae1ac-175">When PowerShell Core 6.1 starts up, it will automatically include `$windir\System32` as part of the `PSModulePath` environment variable.</span></span>
<span data-ttu-id="ae1ac-176">Tuttavia, espone solo i moduli a `Get-Module` e `Import-Module` se i relativi `CompatiblePSEdition` sono contrassegnati come compatibili con `Core`.</span><span class="sxs-lookup"><span data-stu-id="ae1ac-176">However, it only exposes modules to `Get-Module` and `Import-Module` if its `CompatiblePSEdition` is marked as compatible with `Core`.</span></span>


```powershell
Get-Module -ListAvailable
```

> [!NOTE]
> <span data-ttu-id="ae1ac-177">È possibile che vengano visualizzati come disponibili moduli diversi, a seconda delle funzionalità e dei ruoli installati.</span><span class="sxs-lookup"><span data-stu-id="ae1ac-177">You may see different available modules depending on what roles and features are installed.</span></span>

```Output
...
    Directory: C:\WINDOWS\system32\WindowsPowerShell\v1.0\Modules

ModuleType Version    Name                                PSEdition ExportedCommands
---------- -------    ----                                --------- ----------------
Manifest   2.0.1.0    Appx                                Core,Desk {Add-AppxPackage, Get-AppxPackage, Get-AppxPacka...
Manifest   1.0.0.0    BitLocker                           Core,Desk {Unlock-BitLocker, Suspend-BitLocker, Resume-Bit...
Manifest   1.0.0.0    DnsClient                           Core,Desk {Resolve-DnsName, Clear-DnsClientCache, Get-DnsC...
Manifest   1.0.0.0    HgsDiagnostics                      Core,Desk {New-HgsTraceTarget, Get-HgsTrace, Get-HgsTraceF...
Binary     2.0.0.0    Hyper-V                             Core,Desk {Add-VMAssignableDevice, Add-VMDvdDrive, Add-VMF...
Binary     1.1        Hyper-V                             Core,Desk {Add-VMDvdDrive, Add-VMFibreChannelHba, Add-VMHa...
Manifest   2.0.0.0    NetAdapter                          Core,Desk {Disable-NetAdapter, Disable-NetAdapterBinding, ...
Manifest   1.0.0.0    NetEventPacketCapture               Core,Desk {New-NetEventSession, Remove-NetEventSession, Ge...
Manifest   2.0.0.0    NetLbfo                             Core,Desk {Add-NetLbfoTeamMember, Add-NetLbfoTeamNic, Get-...
Manifest   1.0.0.0    NetNat                              Core,Desk {Get-NetNat, Get-NetNatExternalAddress, Get-NetN...
Manifest   2.0.0.0    NetQos                              Core,Desk {Get-NetQosPolicy, Set-NetQosPolicy, Remove-NetQ...
Manifest   2.0.0.0    NetSecurity                         Core,Desk {Get-DAPolicyChange, New-NetIPsecAuthProposal, N...
Manifest   1.0.0.0    NetSwitchTeam                       Core,Desk {New-NetSwitchTeam, Remove-NetSwitchTeam, Get-Ne...
Manifest   1.0.0.0    NetWNV                              Core,Desk {Get-NetVirtualizationProviderAddress, Get-NetVi...
Manifest   2.0.0.0    TrustedPlatformModule               Core,Desk {Get-Tpm, Initialize-Tpm, Clear-Tpm, Unblock-Tpm...
...
```

<span data-ttu-id="ae1ac-178">Si può eseguire l'override di questo comportamento con il parametro opzionale `-SkipEditionCheck` in modo da visualizzare tutti i moduli.</span><span class="sxs-lookup"><span data-stu-id="ae1ac-178">You can override this behavior to show all modules using the `-SkipEditionCheck` switch parameter.</span></span>
<span data-ttu-id="ae1ac-179">È stata anche aggiunta una proprietà `PSEdition` all'output della tabella.</span><span class="sxs-lookup"><span data-stu-id="ae1ac-179">We've also added a `PSEdition` property to the table output.</span></span>

```powershell
Get-Module Net* -ListAvailable -SkipEditionCheck
```

```Output
    Directory: C:\WINDOWS\system32\WindowsPowerShell\v1.0\Modules

ModuleType Version    Name                        PSEdition ExportedCommands
---------- -------    ----                        --------- ----------------
Manifest   2.0.0.0    NetAdapter                  Core,Desk {Disable-NetAdapter, Disable-NetAdapterBinding, ...
Manifest   1.0.0.0    NetConnection               Core,Desk {Get-NetConnectionProfile, Set-NetConnectionProf...
Manifest   1.0.0.0    NetDiagnostics              Desk      Get-NetView
Manifest   1.0.0.0    NetEventPacketCapture       Core,Desk {New-NetEventSession, Remove-NetEventSession, Ge...
Manifest   2.0.0.0    NetLbfo                     Core,Desk {Add-NetLbfoTeamMember, Add-NetLbfoTeamNic, Get-...
Manifest   1.0.0.0    NetNat                      Core,Desk {Get-NetNat, Get-NetNatExternalAddress, Get-NetN...
Manifest   2.0.0.0    NetQos                      Core,Desk {Get-NetQosPolicy, Set-NetQosPolicy, Remove-NetQ...
Manifest   2.0.0.0    NetSecurity                 Core,Desk {Get-DAPolicyChange, New-NetIPsecAuthProposal, N...
Manifest   1.0.0.0    NetSwitchTeam               Core,Desk {New-NetSwitchTeam, Remove-NetSwitchTeam, Get-Ne...
Manifest   1.0.0.0    NetTCPIP                    Core,Desk {Get-NetIPAddress, Get-NetIPInterface, Get-NetIP...
Manifest   1.0.0.0    NetWNV                      Core,Desk {Get-NetVirtualizationProviderAddress, Get-NetVi...
Manifest   1.0.0.0    NetworkConnectivityStatus   Core,Desk {Get-DAConnectionStatus, Get-NCSIPolicyConfigura...
Manifest   1.0.0.0    NetworkSwitchManager        Core,Desk {Disable-NetworkSwitchEthernetPort, Enable-Netwo...
Manifest   1.0.0.0    NetworkTransition           Core,Desk {Add-NetIPHttpsCertBinding, Disable-NetDnsTransi...
```

<span data-ttu-id="ae1ac-180">Per altre informazioni su questo comportamento, vedere [PowerShell RFC0025](https://github.com/PowerShell/PowerShell-RFC/blob/master/5-Final/RFC0025-PSCore6-and-Windows-Modules.md).</span><span class="sxs-lookup"><span data-stu-id="ae1ac-180">For more information about this behavior, check out [PowerShell RFC0025](https://github.com/PowerShell/PowerShell-RFC/blob/master/5-Final/RFC0025-PSCore6-and-Windows-Modules.md).</span></span>

## <a name="markdown-cmdlets-and-rendering"></a><span data-ttu-id="ae1ac-181">Cmdlet e rendering di markdown</span><span class="sxs-lookup"><span data-stu-id="ae1ac-181">Markdown cmdlets and rendering</span></span>

<span data-ttu-id="ae1ac-182">Il markdown è uno standard per la creazione di documenti di testo normale leggibili con formattazione di base di cui si può eseguire il rendering in HTML.</span><span class="sxs-lookup"><span data-stu-id="ae1ac-182">Markdown is a standard for creating readable plaintext documents with basic formatting that can be rendered into HTML.</span></span>

<span data-ttu-id="ae1ac-183">Sono stati aggiunti alcuni cmdlet in 6.1 che consentono di convertire ed eseguire il rendering di documenti di markdown nella console, tra cui:</span><span class="sxs-lookup"><span data-stu-id="ae1ac-183">We've added some cmdlets in 6.1 that allow you to convert and render Markdown documents in the console, including:</span></span>

- `ConvertFrom-Markdown`
- `Get-MarkdownOption`
- `Set-MarkdownOption`
- `Show-Markdown`

<span data-ttu-id="ae1ac-184">Ad esempio, `Show-Markdown` esegue il rendering di un file di markdown nella console:</span><span class="sxs-lookup"><span data-stu-id="ae1ac-184">For example, `Show-Markdown` renders a Markdown file in the console:</span></span>

![Esempio di visualizzazione di markdown](./images/markdown_example.png)

<span data-ttu-id="ae1ac-186">Per altre informazioni sul funzionamento di questi cmdlet, consultare [questo documento RFC](https://github.com/PowerShell/PowerShell-RFC/blob/master/5-Final/RFC0025-Native-Markdown-Rendering.md).</span><span class="sxs-lookup"><span data-stu-id="ae1ac-186">For more information about how these cmdlets work, check out [this RFC](https://github.com/PowerShell/PowerShell-RFC/blob/master/5-Final/RFC0025-Native-Markdown-Rendering.md).</span></span>

## <a name="experimental-feature-flags"></a><span data-ttu-id="ae1ac-187">Flag di funzionalità sperimentali</span><span class="sxs-lookup"><span data-stu-id="ae1ac-187">Experimental feature flags</span></span>

<span data-ttu-id="ae1ac-188">È stato abilitato il supporto per le [funzionalità sperimentali][].</span><span class="sxs-lookup"><span data-stu-id="ae1ac-188">We enabled support for [Experimental Features][].</span></span> <span data-ttu-id="ae1ac-189">Ciò consente agli sviluppatori di PowerShell di offrire nuove funzionalità e ottenere commenti e suggerimenti prima di completare la progettazione.</span><span class="sxs-lookup"><span data-stu-id="ae1ac-189">This allows PowerShell developers to deliver new features and get feedback before the design is complete.</span></span> <span data-ttu-id="ae1ac-190">In questo modo si evita l'introduzione di modifiche che causano un'interruzione con l'evolversi della progettazione.</span><span class="sxs-lookup"><span data-stu-id="ae1ac-190">This way we avoid making breaking changes as the design evolves.</span></span>

<span data-ttu-id="ae1ac-191">Usare `Get-ExperimentalFeature` per ottenere un elenco delle funzionalità sperimentali disponibili.</span><span class="sxs-lookup"><span data-stu-id="ae1ac-191">Use `Get-ExperimentalFeature` to get a list of available experimental features.</span></span> <span data-ttu-id="ae1ac-192">È possibile abilitare o disabilitare queste funzionalità con `Enable-ExperimentalFeature` e `Disable-ExperimentalFeature`.</span><span class="sxs-lookup"><span data-stu-id="ae1ac-192">You can enable or disable these features with `Enable-ExperimentalFeature` and `Disable-ExperimentalFeature`.</span></span>

<span data-ttu-id="ae1ac-193">Altre informazioni su questa funzionalità sono disponibili in [PowerShell RFC0029](https://github.com/PowerShell/PowerShell-RFC/blob/master/5-Final/RFC0029-Support-Experimental-Features.md).</span><span class="sxs-lookup"><span data-stu-id="ae1ac-193">You can learn more about this feature in [PowerShell RFC0029](https://github.com/PowerShell/PowerShell-RFC/blob/master/5-Final/RFC0029-Support-Experimental-Features.md).</span></span>

## <a name="web-cmdlet-improvements"></a><span data-ttu-id="ae1ac-194">Miglioramenti dei cmdlet Web</span><span class="sxs-lookup"><span data-stu-id="ae1ac-194">Web cmdlet improvements</span></span>

<span data-ttu-id="ae1ac-195">Grazie a [@markekraus](https://github.com/markekraus), sono stati apportati numerosi miglioramenti ai cmdlet Web: [`Invoke-WebRequest`](/powershell/module/microsoft.powershell.utility/invoke-webrequest)</span><span class="sxs-lookup"><span data-stu-id="ae1ac-195">Thanks to [@markekraus](https://github.com/markekraus), a whole slew of improvements have been made to our web cmdlets: [`Invoke-WebRequest`](/powershell/module/microsoft.powershell.utility/invoke-webrequest)</span></span>
<span data-ttu-id="ae1ac-196">e [`Invoke-RestMethod`](/powershell/module/microsoft.powershell.utility/invoke-restmethod).</span><span class="sxs-lookup"><span data-stu-id="ae1ac-196">and [`Invoke-RestMethod`](/powershell/module/microsoft.powershell.utility/invoke-restmethod).</span></span>

- <span data-ttu-id="ae1ac-197">[PR #6109](https://github.com/PowerShell/PowerShell/pull/6109) - codifica predefinita impostata su UTF-8 per le risposte `application-json`</span><span class="sxs-lookup"><span data-stu-id="ae1ac-197">[PR #6109](https://github.com/PowerShell/PowerShell/pull/6109) - default encoding set to UTF-8 for `application-json` responses</span></span>
- <span data-ttu-id="ae1ac-198">[PR #6018](https://github.com/PowerShell/PowerShell/pull/6018) - parametro `-SkipHeaderValidation` per consentire intestazioni `Content-Type` che non sono conformi agli standard</span><span class="sxs-lookup"><span data-stu-id="ae1ac-198">[PR #6018](https://github.com/PowerShell/PowerShell/pull/6018) - `-SkipHeaderValidation` parameter to allow `Content-Type` headers that aren't standards-compliant</span></span>
- <span data-ttu-id="ae1ac-199">[PR #5972](https://github.com/PowerShell/PowerShell/pull/5972) - parametro `Form` per supportare il supporto `multipart/form-data` semplificato</span><span class="sxs-lookup"><span data-stu-id="ae1ac-199">[PR #5972](https://github.com/PowerShell/PowerShell/pull/5972) - `Form` parameter to support simplified `multipart/form-data` support</span></span>
- <span data-ttu-id="ae1ac-200">[PR #6338](https://github.com/PowerShell/PowerShell/pull/6338) - gestione conforme e senza distinzione tra maiuscole e minuscole delle chiavi di relazione</span><span class="sxs-lookup"><span data-stu-id="ae1ac-200">[PR #6338](https://github.com/PowerShell/PowerShell/pull/6338) - Compliant, case-insensitive handling of relation keys</span></span>
- <span data-ttu-id="ae1ac-201">[PR #6447](https://github.com/PowerShell/PowerShell/pull/6447) - aggiunta del parametro `-Resume` per i cmdlet Web</span><span class="sxs-lookup"><span data-stu-id="ae1ac-201">[PR #6447](https://github.com/PowerShell/PowerShell/pull/6447) - Add `-Resume` parameter for web cmdlets</span></span>

## <a name="remoting-improvements"></a><span data-ttu-id="ae1ac-202">Miglioramenti della comunicazione remota</span><span class="sxs-lookup"><span data-stu-id="ae1ac-202">Remoting improvements</span></span>

### <a name="powershell-direct-for-containers-tries-to-use-powershell-core-first"></a><span data-ttu-id="ae1ac-203">PowerShell Direct per i contenitori prova prima a usare PowerShell Core</span><span class="sxs-lookup"><span data-stu-id="ae1ac-203">PowerShell Direct for Containers tries to use PowerShell Core first</span></span>

<span data-ttu-id="ae1ac-204">[PowerShell Direct](/virtualization/hyper-v-on-windows/user-guide/powershell-direct) è una funzionalità di PowerShell e Hyper-V che consente di connettersi a una macchina virtuale Hyper-V o contenitore senza connettività di rete o altri servizi di gestione remota.</span><span class="sxs-lookup"><span data-stu-id="ae1ac-204">[PowerShell Direct](/virtualization/hyper-v-on-windows/user-guide/powershell-direct) is a feature of PowerShell and Hyper-V that allows you to connect to a Hyper-V VM or Container without network connectivity or other remote management services.</span></span>

<span data-ttu-id="ae1ac-205">In passato, PowerShell Direct si collegava usando l'istanza di posta in arrivo inclusa in Windows PowerShell nel contenitore.</span><span class="sxs-lookup"><span data-stu-id="ae1ac-205">In the past, PowerShell Direct connected using the inbox Windows PowerShell instance on the Container.</span></span>
<span data-ttu-id="ae1ac-206">Ora PowerShell Direct per prima cosa tenta di connettersi usando qualsiasi variabile `pwsh.exe` nella variabile di ambiente `PATH`.</span><span class="sxs-lookup"><span data-stu-id="ae1ac-206">Now, PowerShell Direct first attempts to connect using any available `pwsh.exe` on the `PATH` environment variable.</span></span>
<span data-ttu-id="ae1ac-207">Se `pwsh.exe` non è disponibile, PowerShell Direct esegue il fallback per usare `powershell.exe`.</span><span class="sxs-lookup"><span data-stu-id="ae1ac-207">If `pwsh.exe` isn't available, PowerShell Direct falls back to use `powershell.exe`.</span></span>

### <a name="enable-psremoting-now-creates-separate-remoting-endpoints-for-preview-versions"></a><span data-ttu-id="ae1ac-208">`Enable-PSRemoting` ora crea endpoint di comunicazione remota separati per le versioni di anteprima</span><span class="sxs-lookup"><span data-stu-id="ae1ac-208">`Enable-PSRemoting` now creates separate remoting endpoints for preview versions</span></span>

<span data-ttu-id="ae1ac-209">`Enable-PSRemoting` ora crea due configurazioni della sessione di comunicazione remota:</span><span class="sxs-lookup"><span data-stu-id="ae1ac-209">`Enable-PSRemoting` now creates two remoting session configurations:</span></span>

- <span data-ttu-id="ae1ac-210">Una per la versione principale di PowerShell.</span><span class="sxs-lookup"><span data-stu-id="ae1ac-210">One for the major version of PowerShell.</span></span> <span data-ttu-id="ae1ac-211">Ad esempio, `PowerShell.6`</span><span class="sxs-lookup"><span data-stu-id="ae1ac-211">For example, `PowerShell.6`.</span></span> <span data-ttu-id="ae1ac-212">Questo endpoint può essere usato come base per gli aggiornamenti di versioni secondarie come configurazione di sessione di PowerShell 6 "a livello di sistema"</span><span class="sxs-lookup"><span data-stu-id="ae1ac-212">This endpoint that can be relied upon across minor version updates as the "system-wide" PowerShell 6 session configuration</span></span>
- <span data-ttu-id="ae1ac-213">Una configurazione di sessione specifica della versione, ad esempio: `PowerShell.6.1.0`</span><span class="sxs-lookup"><span data-stu-id="ae1ac-213">One version-specific session configuration, for example: `PowerShell.6.1.0`</span></span>

<span data-ttu-id="ae1ac-214">Questo comportamento è utile se si prevede di avere più versioni di PowerShell 6 installate e accessibili nello stesso computer.</span><span class="sxs-lookup"><span data-stu-id="ae1ac-214">This behavior is useful if you want to have multiple PowerShell 6 versions installed and accessible on the same machine.</span></span>

<span data-ttu-id="ae1ac-215">Inoltre, le versioni di anteprima di PowerShell ora ottengono le proprie configurazioni di sessione remota dopo l'esecuzione del cmdlet `Enable-PSRemoting`:</span><span class="sxs-lookup"><span data-stu-id="ae1ac-215">Additionally, preview versions of PowerShell now get their own remoting session configurations after running the `Enable-PSRemoting` cmdlet:</span></span>

```powershell
C:\WINDOWS\system32> Enable-PSRemoting
```

<span data-ttu-id="ae1ac-216">L'output può essere diverso se prima non è stato configurato WinRM.</span><span class="sxs-lookup"><span data-stu-id="ae1ac-216">Your output may be different if you haven't set up WinRM before.</span></span>

```Output
WinRM is already set up to receive requests on this computer.
WinRM is already set up for remote management on this computer.
```

<span data-ttu-id="ae1ac-217">Quindi è possibile visualizzare configurazioni di sessione di PowerShell separate per l'anteprima e le build stabili di PowerShell 6 e per ogni versione specifica.</span><span class="sxs-lookup"><span data-stu-id="ae1ac-217">Then you can see separate PowerShell session configurations for the preview and stable builds of PowerShell 6, and for each specific version.</span></span>

```powershell
Get-PSSessionConfiguration
```

```Output
Name          : PowerShell.6.2-preview.1
PSVersion     : 6.2
StartupScript :
RunAsUser     :
Permission    : NT AUTHORITY\INTERACTIVE AccessAllowed, BUILTIN\Administrators AccessAllowed, BUILTIN\Remote Management Users AccessAllowed

Name          : PowerShell.6-preview
PSVersion     : 6.2
StartupScript :
RunAsUser     :
Permission    : NT AUTHORITY\INTERACTIVE AccessAllowed, BUILTIN\Administrators AccessAllowed, BUILTIN\Remote Management Users AccessAllowed

Name          : powershell.6
PSVersion     : 6.1
StartupScript :
RunAsUser     :
Permission    : NT AUTHORITY\INTERACTIVE AccessAllowed, BUILTIN\Administrators AccessAllowed, BUILTIN\Remote Management Users AccessAllowed

Name          : powershell.6.1.0
PSVersion     : 6.1
StartupScript :
RunAsUser     :
Permission    : NT AUTHORITY\INTERACTIVE AccessAllowed, BUILTIN\Administrators AccessAllowed, BUILTIN\Remote Management Users AccessAllowed
```

### <a name="userhostport-syntax-supported-for-ssh"></a><span data-ttu-id="ae1ac-218">Sintassi di `user@host:port` supportata per SSH</span><span class="sxs-lookup"><span data-stu-id="ae1ac-218">`user@host:port` syntax supported for SSH</span></span>

<span data-ttu-id="ae1ac-219">I client SSH in genere supportano una stringa di connessione nel formato `user@host:port`.</span><span class="sxs-lookup"><span data-stu-id="ae1ac-219">SSH clients typically support a connection string in the format `user@host:port`.</span></span>
<span data-ttu-id="ae1ac-220">Con l'aggiunta di SSH come protocollo per la comunicazione remota di PowerShell, è stato aggiunto il supporto per questo formato della stringa di connessione:</span><span class="sxs-lookup"><span data-stu-id="ae1ac-220">With the addition of SSH as a protocol for PowerShell Remoting, we've added support for this format of connection string:</span></span>

`Enter-PSSession -HostName fooUser@ssh.contoso.com:2222`

## <a name="msi-option-to-add-explorer-shell-context-menu-on-windows"></a><span data-ttu-id="ae1ac-221">Opzione di MSI per l'aggiunta del menu di scelta rapida della shell di Esplora risorse in Windows</span><span class="sxs-lookup"><span data-stu-id="ae1ac-221">MSI option to add explorer shell context menu on Windows</span></span>

<span data-ttu-id="ae1ac-222">Grazie a [@bergmeister](https://github.com/bergmeister), ora è possibile attivare un menu di scelta rapida in Windows.</span><span class="sxs-lookup"><span data-stu-id="ae1ac-222">Thanks to [@bergmeister](https://github.com/bergmeister), now you can enable a context menu on Windows.</span></span> <span data-ttu-id="ae1ac-223">È ora possibile aprire l'installazione a livello di sistema di PowerShell 6.1 da qualsiasi cartella in Esplora risorse:</span><span class="sxs-lookup"><span data-stu-id="ae1ac-223">Now you can open your system-wide installation of PowerShell 6.1 from any folder in the Windows Explorer:</span></span>

![Menu di scelta rapida della shell per PowerShell 6](./images/shell_context_menu.png)

## <a name="goodies"></a><span data-ttu-id="ae1ac-225">Novità</span><span class="sxs-lookup"><span data-stu-id="ae1ac-225">Goodies</span></span>

### <a name="run-as-administrator-in-the-windows-shortcut-jump-list"></a><span data-ttu-id="ae1ac-226">Opzione "Run as Administrator" (Esegui come amministratore) nel menu di scelta rapida di Windows</span><span class="sxs-lookup"><span data-stu-id="ae1ac-226">"Run as Administrator" in the Windows shortcut jump list</span></span>

<span data-ttu-id="ae1ac-227">Grazie a [@bergmeister](https://github.com/bergmeister), il menu di scelta rapida di PowerShell Core ora include una voce che consente di eseguire PowerShell come amministratore:</span><span class="sxs-lookup"><span data-stu-id="ae1ac-227">Thanks to [@bergmeister](https://github.com/bergmeister), the PowerShell Core shortcut's jump list now includes "Run as Administrator":</span></span>

!["Run as administrator" nel menu di scelta rapida di PowerShell 6](./images/jumplist.png)

### <a name="cd---returns-to-previous-directory"></a><span data-ttu-id="ae1ac-229">`cd -` consente di tornare alla directory precedente</span><span class="sxs-lookup"><span data-stu-id="ae1ac-229">`cd -` returns to previous directory</span></span>

```powershell
C:\Windows\System32> cd C:\
C:\> cd -
C:\Windows\System32>
```

<span data-ttu-id="ae1ac-230">O in Linux:</span><span class="sxs-lookup"><span data-stu-id="ae1ac-230">Or on Linux:</span></span>

```ShellSession
PS /etc> cd /usr/bin
PS /usr/bin> cd -
PS /etc>
```

<span data-ttu-id="ae1ac-231">Inoltre `cd` e `cd --` diventano `$HOME`.</span><span class="sxs-lookup"><span data-stu-id="ae1ac-231">Also, `cd` and `cd --` change to `$HOME`.</span></span>

### `Test-Connection`

<span data-ttu-id="ae1ac-232">Grazie a [@iSazonov](https://github.com/iSazonov), il cmdlet [`Test-Connection`](/powershell/module/microsoft.powershell.management/test-connection) è stato portato in PowerShell Core.</span><span class="sxs-lookup"><span data-stu-id="ae1ac-232">Thanks to [@iSazonov](https://github.com/iSazonov), the [`Test-Connection`](/powershell/module/microsoft.powershell.management/test-connection) cmdlet has been ported to PowerShell Core.</span></span>

### <a name="update-help-as-non-admin"></a><span data-ttu-id="ae1ac-233">`Update-Help` come non amministratore</span><span class="sxs-lookup"><span data-stu-id="ae1ac-233">`Update-Help` as non-admin</span></span>

<span data-ttu-id="ae1ac-234">A grande richiesta, `Update-Help` non deve più essere eseguito come amministratore.</span><span class="sxs-lookup"><span data-stu-id="ae1ac-234">By popular demand, `Update-Help` no longer needs to be run as an administrator.</span></span>
<span data-ttu-id="ae1ac-235">`Update-Help` ora per impostazione predefinita salva la Guida in una cartella con ambito di utente.</span><span class="sxs-lookup"><span data-stu-id="ae1ac-235">`Update-Help` now defaults to saving help to a user-scoped folder.</span></span>

### <a name="new-methodsproperties-on-pscustomobject"></a><span data-ttu-id="ae1ac-236">Nuovi metodi e proprietà per `PSCustomObject`</span><span class="sxs-lookup"><span data-stu-id="ae1ac-236">New methods/properties on `PSCustomObject`</span></span>

<span data-ttu-id="ae1ac-237">Grazie a [@iSazonov](https://github.com/iSazonov), sono stati aggiunti nuovi metodi e proprietà a `PSCustomObject`.</span><span class="sxs-lookup"><span data-stu-id="ae1ac-237">Thanks to [@iSazonov](https://github.com/iSazonov), we've added new methods and properties to `PSCustomObject`.</span></span>
<span data-ttu-id="ae1ac-238">`PSCustomObject` include ora una proprietà `Count`/`Length` come altri oggetti.</span><span class="sxs-lookup"><span data-stu-id="ae1ac-238">`PSCustomObject` now includes a `Count`/`Length` property like other objects.</span></span>

```powershell
$PSCustomObject = [pscustomobject]@{foo = 1}

$PSCustomObject.Length
```

```Output
1
```

```powershell
$PSCustomObject.Count
```

```Output
1
```

<span data-ttu-id="ae1ac-239">Questa attività include inoltre i metodi `ForEach` e `Where`, che consentono di usare e filtrare gli elementi `PSCustomObject`:</span><span class="sxs-lookup"><span data-stu-id="ae1ac-239">This work also includes `ForEach` and `Where` methods that allow you to operate and filter on `PSCustomObject` items:</span></span>

```powershell
$PSCustomObject.ForEach({$_.foo + 1})
```

```Output
2
```

```powershell
$PSCustomObject.Where({$_.foo -gt 0})
```

```Output
foo
---
  1
```

### `Where-Object -Not`

<span data-ttu-id="ae1ac-240">Grazie a @SimonWahlin, è stato aggiunto il parametro `-Not` a `Where-Object`.</span><span class="sxs-lookup"><span data-stu-id="ae1ac-240">Thanks to @SimonWahlin, we've added the `-Not` parameter to `Where-Object`.</span></span>
<span data-ttu-id="ae1ac-241">Ora è possibile filtrare un oggetto in corrispondenza della pipeline per la non esistenza di una proprietà o un valore della proprietà null/vuoto.</span><span class="sxs-lookup"><span data-stu-id="ae1ac-241">Now you can filter an object at the pipeline for the non-existence of a property, or a null/empty property value.</span></span>

<span data-ttu-id="ae1ac-242">Ad esempio, questo comando restituisce tutti i servizi per cui non sono definiti servizi dipendenti:</span><span class="sxs-lookup"><span data-stu-id="ae1ac-242">For example, this command returns all services that don't have any dependent services defined:</span></span>

```powershell
Get-Service | Where-Object -Not DependentServices
```

### <a name="new-modulemanifest-creates-a-bom-less-utf-8-document"></a><span data-ttu-id="ae1ac-243">`New-ModuleManifest` crea un documento UTF-8 senza BOM</span><span class="sxs-lookup"><span data-stu-id="ae1ac-243">`New-ModuleManifest` creates a BOM-less UTF-8 document</span></span>

<span data-ttu-id="ae1ac-244">Con il passaggio a UTF-8 senza BOM in PowerShell 6.0, il cmdlet `New-ModuleManifest` è stato aggiornato per creare un documento UTF-8 senza BOM anziché un documento UTF-16.</span><span class="sxs-lookup"><span data-stu-id="ae1ac-244">Given our move to BOM-less UTF-8 in PowerShell 6.0, we've updated the `New-ModuleManifest` cmdlet to create a BOM-less UTF-8 document instead of a UTF-16 one.</span></span>

### <a name="conversions-from-psmethod-to-delegate"></a><span data-ttu-id="ae1ac-245">Conversioni da PSMethod in delegato</span><span class="sxs-lookup"><span data-stu-id="ae1ac-245">Conversions from PSMethod to Delegate</span></span>

<span data-ttu-id="ae1ac-246">Grazie a [@powercode](https://github.com/powercode), è ora supportata la conversione di un `PSMethod` in un delegato.</span><span class="sxs-lookup"><span data-stu-id="ae1ac-246">Thanks to [@powercode](https://github.com/powercode), we now support the conversion of a `PSMethod` into a delegate.</span></span>
<span data-ttu-id="ae1ac-247">Ciò consente di eseguire operazioni come il passaggio del `PSMethod` `[M]::DoubleStrLen` come valore delegato in `[M]::AggregateString`:</span><span class="sxs-lookup"><span data-stu-id="ae1ac-247">This allows you to do things like passing `PSMethod` `[M]::DoubleStrLen` as a delegate value into `[M]::AggregateString`:</span></span>

```powershell
class M {
    static [int] DoubleStrLen([string] $value) { return 2 * $value.Length }

    static [long] AggregateString([string[]] $values, [func[string, int]] $selector) {
        [long] $res = 0
        foreach($s in $values){
            $res += $selector.Invoke($s)
        }
        return $res
    }
}

[M]::AggregateString((gci).Name, [M]::DoubleStrLen)
```

<span data-ttu-id="ae1ac-248">Per altre informazioni su questa modifica, consultare [PR #5287](https://github.com/PowerShell/PowerShell/pull/5287).</span><span class="sxs-lookup"><span data-stu-id="ae1ac-248">For more info on this change, check out [PR #5287](https://github.com/PowerShell/PowerShell/pull/5287).</span></span>

### <a name="standard-deviation-in-measure-object"></a><span data-ttu-id="ae1ac-249">Deviazione standard in `Measure-Object`</span><span class="sxs-lookup"><span data-stu-id="ae1ac-249">Standard deviation in `Measure-Object`</span></span>

<span data-ttu-id="ae1ac-250">Grazie a [@CloudyDino](https://github.com/CloudyDino), è stata aggiunta una proprietà `StandardDeviation` a `Measure-Object`:</span><span class="sxs-lookup"><span data-stu-id="ae1ac-250">Thanks to [@CloudyDino](https://github.com/CloudyDino), we've added a `StandardDeviation` property to `Measure-Object`:</span></span>

```powershell
Get-Process | Measure-Object -Property CPU -AllStats
```

```Output
Count             : 308
Average           : 31.3720576298701
Sum               : 9662.59375
Maximum           : 4416.046875
Minimum           :
StandardDeviation : 264.389544720926
Property          : CPU
```

### `GetPfxCertificate -Password`

<span data-ttu-id="ae1ac-251">Grazie a [@maybe-hello-world](https://github.com/maybe-hello-world), `Get-PfxCertificate` include ora il parametro `Password`, che accetta un `SecureString`.</span><span class="sxs-lookup"><span data-stu-id="ae1ac-251">Thanks to [@maybe-hello-world](https://github.com/maybe-hello-world), `Get-PfxCertificate` now has the `Password` parameter, which takes a `SecureString`.</span></span> <span data-ttu-id="ae1ac-252">In questo modo è possibile usarlo in modo non interattivo:</span><span class="sxs-lookup"><span data-stu-id="ae1ac-252">This allows you to use it non-interactively:</span></span>

```powershell
$certFile = '\\server\share\pwd-protected.pfx'
$certPass = Read-Host -AsSecureString -Prompt 'Enter the password for certificate: '

$certThumbPrint = (Get-PfxCertificate -FilePath $certFile -Password $certPass ).ThumbPrint
```

### <a name="removal-of-the-more-function"></a><span data-ttu-id="ae1ac-253">Rimozione della funzione `more`</span><span class="sxs-lookup"><span data-stu-id="ae1ac-253">Removal of the `more` function</span></span>

<span data-ttu-id="ae1ac-254">In precedenza PowerShell rendeva disponibile in Windows la funzione `more` che eseguiva il wrapping di `more.com`.</span><span class="sxs-lookup"><span data-stu-id="ae1ac-254">In the past, PowerShell shipped a function on Windows called `more` that wrapped `more.com`.</span></span>
<span data-ttu-id="ae1ac-255">Tale funzione è stata ora rimossa.</span><span class="sxs-lookup"><span data-stu-id="ae1ac-255">That function has now been removed.</span></span>

<span data-ttu-id="ae1ac-256">Inoltre, la funzione `help` ora usa `more.com` in Windows o il pager predefinito del sistema specificato da `$env:PAGER` nelle piattaforme non Windows.</span><span class="sxs-lookup"><span data-stu-id="ae1ac-256">Also, the `help` function changed to use `more.com` on Windows, or the system's default pager specified by `$env:PAGER` on non-Windows platforms.</span></span>

### <a name="cd-drivename-now-returns-users-to-the-current-working-directory-in-that-drive"></a><span data-ttu-id="ae1ac-257">`cd DriveName:` ora riporta gli utenti alla directory di lavoro corrente in quell'unità</span><span class="sxs-lookup"><span data-stu-id="ae1ac-257">`cd DriveName:` now returns users to the current working directory in that drive</span></span>

<span data-ttu-id="ae1ac-258">In precedenza, usando `Set-Location` o `cd` per tornare a un PSDrive, gli utenti tornavano al percorso predefinito per tale unità.</span><span class="sxs-lookup"><span data-stu-id="ae1ac-258">Previously, using `Set-Location` or `cd` to return to a PSDrive sent users to the default location for that drive.</span></span>

<span data-ttu-id="ae1ac-259">Grazie a [@mcbobke](https://github.com/mcbobke), gli utenti ora vengono inviati all'ultima directory di lavoro corrente nota per tale sessione.</span><span class="sxs-lookup"><span data-stu-id="ae1ac-259">Thanks to [@mcbobke](https://github.com/mcbobke), users are now sent to the last known current working directory for that session.</span></span>

### <a name="windows-powershell-type-accelerators"></a><span data-ttu-id="ae1ac-260">Acceleratori del tipo di Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="ae1ac-260">Windows PowerShell type accelerators</span></span>

<span data-ttu-id="ae1ac-261">In Windows PowerShell sono inclusi i seguenti acceleratori del tipo, che semplificano il lavoro con i rispettivi tipi:</span><span class="sxs-lookup"><span data-stu-id="ae1ac-261">In Windows PowerShell, we included the following type accelerators to make it easier to work with their respective types:</span></span>

- <span data-ttu-id="ae1ac-262">`[adsi]`: `System.DirectoryServices.DirectoryEntry`</span><span class="sxs-lookup"><span data-stu-id="ae1ac-262">`[adsi]`: `System.DirectoryServices.DirectoryEntry`</span></span>
- <span data-ttu-id="ae1ac-263">`[adsisearcher]`: `System.DirectoryServices.DirectorySearcher`</span><span class="sxs-lookup"><span data-stu-id="ae1ac-263">`[adsisearcher]`: `System.DirectoryServices.DirectorySearcher`</span></span>
- <span data-ttu-id="ae1ac-264">`[wmi]`: `System.Management.ManagementObject`</span><span class="sxs-lookup"><span data-stu-id="ae1ac-264">`[wmi]`: `System.Management.ManagementObject`</span></span>
- <span data-ttu-id="ae1ac-265">`[wmiclass]`: `System.Management.ManagementClass`</span><span class="sxs-lookup"><span data-stu-id="ae1ac-265">`[wmiclass]`: `System.Management.ManagementClass`</span></span>
- <span data-ttu-id="ae1ac-266">`[wmisearcher]`: `System.Management.ManagementObjectSearcher`</span><span class="sxs-lookup"><span data-stu-id="ae1ac-266">`[wmisearcher]`: `System.Management.ManagementObjectSearcher`</span></span>

<span data-ttu-id="ae1ac-267">Questi acceleratori del tipo non erano inclusi in PowerShell 6, ma sono stati aggiunti a PowerShell 6.1 eseguito in Windows.</span><span class="sxs-lookup"><span data-stu-id="ae1ac-267">These type accelerators were not included in PowerShell 6, but have been added to PowerShell 6.1 running on Windows.</span></span>

<span data-ttu-id="ae1ac-268">Questi tipi sono utili per costruire facilmente oggetti AD e WMI.</span><span class="sxs-lookup"><span data-stu-id="ae1ac-268">These types are useful in easily constructing AD and WMI objects.</span></span>

<span data-ttu-id="ae1ac-269">Ad esempio, è possibile eseguire una query con LDAP:</span><span class="sxs-lookup"><span data-stu-id="ae1ac-269">For example, you can query using LDAP:</span></span>

```powershell
[adsi]'LDAP://CN=FooUse,OU=People,DC=contoso,DC=com'
```

<span data-ttu-id="ae1ac-270">Nell'esempio seguente viene creato un oggetto CIM Win32_OperatingSystem:</span><span class="sxs-lookup"><span data-stu-id="ae1ac-270">Following example creates a Win32_OperatingSystem CIM object:</span></span>

```powershell
[wmi]"Win32_OperatingSystem=@"
```

```Output
SystemDirectory : C:\WINDOWS\system32
Organization    : Contoso IT
BuildNumber     : 18234
RegisteredUser  : Contoso Corp.
SerialNumber    : 12345-67890-ABCDE-F0123
Version         : 10.0.18234
```

<span data-ttu-id="ae1ac-271">Questo esempio restituisce un oggetto ManagementClass per la classe Win32_OperatingSystem.</span><span class="sxs-lookup"><span data-stu-id="ae1ac-271">This example returns a ManagementClass object for Win32_OperatingSystem class.</span></span>

```powershell
[wmiclass]"Win32_OperatingSystem"
```

```Output
   NameSpace: ROOT\cimv2

Name                                Methods              Properties
----                                -------              ----------
Win32_OperatingSystem               {Reboot, Shutdown... {BootDevice, BuildNumber, BuildType, Caption...}
```

### <a name="-lp-alias-for-all--literalpath-parameters"></a><span data-ttu-id="ae1ac-272">Alias `-lp` per tutti i parametri `-LiteralPath`</span><span class="sxs-lookup"><span data-stu-id="ae1ac-272">`-lp` alias for all `-LiteralPath` parameters</span></span>

<span data-ttu-id="ae1ac-273">Grazie a [@kvprasoon](https://github.com/kvprasoon), è ora disponibile un alias del parametro `-lp` per tutti i cmdlet predefiniti di PowerShell che hanno un parametro `-LiteralPath`.</span><span class="sxs-lookup"><span data-stu-id="ae1ac-273">Thanks to [@kvprasoon](https://github.com/kvprasoon), we now have a parameter alias `-lp` for all the built-in PowerShell cmdlets that have a `-LiteralPath` parameter.</span></span>

## <a name="breaking-changes"></a><span data-ttu-id="ae1ac-274">Modifiche che causano un'interruzione</span><span class="sxs-lookup"><span data-stu-id="ae1ac-274">Breaking Changes</span></span>

### <a name="msi-based-installation-paths-on-windows"></a><span data-ttu-id="ae1ac-275">Percorsi di installazione basati su MSI in Windows</span><span class="sxs-lookup"><span data-stu-id="ae1ac-275">MSI-based installation paths on Windows</span></span>

<span data-ttu-id="ae1ac-276">In Windows il pacchetto MSI ora esegue l'installazione nel percorso seguente:</span><span class="sxs-lookup"><span data-stu-id="ae1ac-276">On Windows, the MSI package now installs to the following path:</span></span>

- <span data-ttu-id="ae1ac-277">`$env:ProgramFiles\PowerShell\6\` per l'installazione stabile di 6.x</span><span class="sxs-lookup"><span data-stu-id="ae1ac-277">`$env:ProgramFiles\PowerShell\6\` for the stable installation of 6.x</span></span>
- <span data-ttu-id="ae1ac-278">`$env:ProgramFiles\PowerShell\6-preview\` per l'installazione di anteprima di 6.x</span><span class="sxs-lookup"><span data-stu-id="ae1ac-278">`$env:ProgramFiles\PowerShell\6-preview\` for the preview installation of 6.x</span></span>

<span data-ttu-id="ae1ac-279">Questa modifica assicura che PowerShell Core possa essere aggiornato/gestito da Microsoft Update.</span><span class="sxs-lookup"><span data-stu-id="ae1ac-279">This change ensures that PowerShell Core can be updated/serviced by Microsoft Update.</span></span>

<span data-ttu-id="ae1ac-280">Per altre informazioni, consultare [PowerShell RFC0026](https://github.com/PowerShell/PowerShell-RFC/blob/master/5-Final/RFC0026-MSI-Installation-Path.md).</span><span class="sxs-lookup"><span data-stu-id="ae1ac-280">For more information, check out [PowerShell RFC0026](https://github.com/PowerShell/PowerShell-RFC/blob/master/5-Final/RFC0026-MSI-Installation-Path.md).</span></span>

### <a name="telemetry-can-only-be-disabled-with-an-environment-variable"></a><span data-ttu-id="ae1ac-281">La telemetria può essere disabilitata solo con una variabile di ambiente</span><span class="sxs-lookup"><span data-stu-id="ae1ac-281">Telemetry can only be disabled with an environment variable</span></span>

<span data-ttu-id="ae1ac-282">PowerShell Core invia i dati di telemetria di base a Microsoft all'avvio.</span><span class="sxs-lookup"><span data-stu-id="ae1ac-282">PowerShell Core sends basic telemetry data to Microsoft when it is launched.</span></span> <span data-ttu-id="ae1ac-283">I dati includono il nome del sistema operativo, la versione del sistema operativo e la versione di PowerShell.</span><span class="sxs-lookup"><span data-stu-id="ae1ac-283">The data includes the OS name, OS version, and PowerShell version.</span></span> <span data-ttu-id="ae1ac-284">Questi dati consentono di comprendere meglio gli ambienti in cui si usa PowerShell e di assegnare priorità alle nuove funzionalità e correzioni.</span><span class="sxs-lookup"><span data-stu-id="ae1ac-284">This data allows us to better understand the environments where PowerShell is used and enables us to prioritize new features and fixes.</span></span>

<span data-ttu-id="ae1ac-285">Per rifiutare esplicitamente questa telemetria, impostare la variabile di ambiente `POWERSHELL_TELEMETRY_OPTOUT` su `true`, `yes` o `1`.</span><span class="sxs-lookup"><span data-stu-id="ae1ac-285">To opt-out of this telemetry, set the environment variable `POWERSHELL_TELEMETRY_OPTOUT` to `true`, `yes`, or `1`.</span></span> <span data-ttu-id="ae1ac-286">Non è più supportata l'eliminazione del file `DELETE_ME_TO_DISABLE_CONSOLEHOST_TELEMETRY` per disabilitare la telemetria.</span><span class="sxs-lookup"><span data-stu-id="ae1ac-286">We no longer support deletion of the file `DELETE_ME_TO_DISABLE_CONSOLEHOST_TELEMETRY` to disable telemetry.</span></span>

### <a name="disallowed-basic-auth-over-http-in-powershell-remoting-on-unix-platforms"></a><span data-ttu-id="ae1ac-287">Non è più consentita l'autenticazione di base via HTTP nella comunicazione remota di PowerShell sulle piattaforme Unix</span><span class="sxs-lookup"><span data-stu-id="ae1ac-287">Disallowed Basic Auth over HTTP in PowerShell Remoting on Unix platforms</span></span>

<span data-ttu-id="ae1ac-288">Per evitare l'uso di traffico non crittografato, la comunicazione remota di PowerShell su piattaforme Unix richiede ora l'uso di NTLM/Negotiate o HTTPS.</span><span class="sxs-lookup"><span data-stu-id="ae1ac-288">To prevent the use of unencrypted traffic, PowerShell Remoting on Unix platforms now requires usage of NTLM/Negotiate or HTTPS.</span></span>

<span data-ttu-id="ae1ac-289">Per altre informazioni su queste modifiche, vedere il [problema #6779](https://github.com/PowerShell/PowerShell/issues/6779).</span><span class="sxs-lookup"><span data-stu-id="ae1ac-289">For more information on these changes, check out [Issue #6779](https://github.com/PowerShell/PowerShell/issues/6779).</span></span>

### <a name="removed-visualbasic-as-a-supported-language-in-add-type"></a><span data-ttu-id="ae1ac-290">Rimosso `VisualBasic` come linguaggio supportato in Add-Type</span><span class="sxs-lookup"><span data-stu-id="ae1ac-290">Removed `VisualBasic` as a supported language in Add-Type</span></span>

<span data-ttu-id="ae1ac-291">In passato era possibile compilare il codice Visual Basic usando il cmdlet `Add-Type`.</span><span class="sxs-lookup"><span data-stu-id="ae1ac-291">In the past, you could compile Visual Basic code using the `Add-Type` cmdlet.</span></span>
<span data-ttu-id="ae1ac-292">Visual Basic veniva usato raramente con `Add-Type`.</span><span class="sxs-lookup"><span data-stu-id="ae1ac-292">Visual Basic was rarely used with `Add-Type`.</span></span> <span data-ttu-id="ae1ac-293">Questa funzionalità è stata rimossa per ridurre le dimensioni di PowerShell.</span><span class="sxs-lookup"><span data-stu-id="ae1ac-293">We removed this feature to reduce the size of PowerShell.</span></span>

### <a name="cleaned-up-uses-of-commandtypesworkflow-and-workflowinfocleaned"></a><span data-ttu-id="ae1ac-294">Pulizia di `CommandTypes.Workflow` e `WorkflowInfoCleaned`</span><span class="sxs-lookup"><span data-stu-id="ae1ac-294">Cleaned up uses of `CommandTypes.Workflow` and `WorkflowInfoCleaned`</span></span>

<span data-ttu-id="ae1ac-295">Per altre informazioni su queste modifiche, vedere [PR #6708](https://github.com/PowerShell/PowerShell/pull/6708).</span><span class="sxs-lookup"><span data-stu-id="ae1ac-295">For more information on these changes, check out [PR #6708](https://github.com/PowerShell/PowerShell/pull/6708).</span></span>

### <a name="group-object-now-sorts-the-groups"></a><span data-ttu-id="ae1ac-296">Group-Object ordina ora i gruppi</span><span class="sxs-lookup"><span data-stu-id="ae1ac-296">Group-Object now sorts the groups</span></span>

<span data-ttu-id="ae1ac-297">Come parte del miglioramento delle prestazioni, `Group-Object` ora restituisce un elenco ordinato dei gruppi.</span><span class="sxs-lookup"><span data-stu-id="ae1ac-297">As part of the performance improvement, `Group-Object` now returns a sorted listing of the groups.</span></span>
<span data-ttu-id="ae1ac-298">Anche se è consigliabile non fare affidamento sull'ordine, questa modifica potrebbe causare problemi se si volesse il primo gruppo.</span><span class="sxs-lookup"><span data-stu-id="ae1ac-298">Although you should not rely on the order, you could be broken by this change if you wanted the first group.</span></span> <span data-ttu-id="ae1ac-299">È stato deciso che valeva la pena introdurre questo miglioramento delle prestazioni perché l'impatto dell'eventuale dipendenza dal comportamento precedente è basso.</span><span class="sxs-lookup"><span data-stu-id="ae1ac-299">We decided that this performance improvement was worth the change since the impact of being dependent on previous behavior is low.</span></span>

<span data-ttu-id="ae1ac-300">Per altre informazioni su questa modifica, vedere [Problema n. 7409](https://github.com/PowerShell/PowerShell/issues/7409).</span><span class="sxs-lookup"><span data-stu-id="ae1ac-300">For more information on this change, see [Issue #7409](https://github.com/PowerShell/PowerShell/issues/7409).</span></span>

<!-- URL references -->
[Funzionalità sperimentali]: /powershell/module/Microsoft.PowerShell.Core/About/about_Experimental_Features
[Experimental Features]: /powershell/module/Microsoft.PowerShell.Core/About/about_Experimental_Features
