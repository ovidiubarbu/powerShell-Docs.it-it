---
ms.date: 06/12/2017
keywords: wmf,powershell,installazione
ms.openlocfilehash: 64a00e041bbeeea117db43116b486e83dfe923b0
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62085831"
---
# <a name="new-built-in-dsc-resources"></a><span data-ttu-id="107af-102">Nuove risorse DSC predefinite</span><span class="sxs-lookup"><span data-stu-id="107af-102">New built-in DSC resources</span></span>

<span data-ttu-id="107af-103">WMF 5.0 RTM include 4 nuove risorse DSC:</span><span class="sxs-lookup"><span data-stu-id="107af-103">WMF 5.0 RTM has 4 new DSC resources:</span></span>
* <span data-ttu-id="107af-104">WindowsFeatureSet</span><span class="sxs-lookup"><span data-stu-id="107af-104">WindowsFeatureSet</span></span>
* <span data-ttu-id="107af-105">WindowsOptionalFeatureSet</span><span class="sxs-lookup"><span data-stu-id="107af-105">WindowsOptionalFeatureSet</span></span>
* <span data-ttu-id="107af-106">ServiceSet</span><span class="sxs-lookup"><span data-stu-id="107af-106">ServiceSet</span></span>
* <span data-ttu-id="107af-107">ProcessSet</span><span class="sxs-lookup"><span data-stu-id="107af-107">ProcessSet</span></span>

<span data-ttu-id="107af-108">Queste risorse forniscono un modo semplice per configurare più istanze tramite una singola chiamata di risorsa.</span><span class="sxs-lookup"><span data-stu-id="107af-108">These resources provide an easy way to configure multiple instances using a single resource call.</span></span>

## <a name="windowsfeatureset"></a><span data-ttu-id="107af-109">WindowsFeatureSet</span><span class="sxs-lookup"><span data-stu-id="107af-109">WindowsFeatureSet</span></span>

```powershell
# Get the syntax of WindowsFeatureSet resource
Get-DscResource -Module psdesiredstateconfiguration -Name WindowsFeatureSet -Syntax

WindowsFeatureSet [String] #ResourceName
{
    [DependsOn = [String[]]]
    Name = [String[]]
    [Ensure = [String]]
    [Source = [String]]
    [IncludeAllSubFeature = [Boolean]]
    [Credential = [PSCredential]]
    [LogPath = [String]]
}
```

## <a name="windowsoptionalfeatureset"></a><span data-ttu-id="107af-110">WindowsOptionalFeatureSet</span><span class="sxs-lookup"><span data-stu-id="107af-110">WindowsOptionalFeatureSet</span></span>

```powershell
# Get the syntax of WindowsOptionalFeatureSet resource
Get-DscResource -Module psdesiredstateconfiguration -Name WindowsOptionalFeatureSet -Syntax

WindowsOptionalFeatureSet [String] #ResourceName
{
    [DependsOn = [String[]]]
    Name = [String[]]
    Ensure = [String]
    [Source = [String[]]]
    [RemoveFilesOnDisable = [Boolean]]
    [LogPath = [String]]
    [NoWindowsUpdateCheck = [Boolean]]
    [LogLevel = [String]]
}
```

## <a name="serviceset"></a><span data-ttu-id="107af-111">ServiceSet</span><span class="sxs-lookup"><span data-stu-id="107af-111">ServiceSet</span></span>

```powershell
# Get the syntax of ServiceSet resource
Get-DscResource -Module psdesiredstateconfiguration -Name ServiceSet -Syntax

ServiceSet [String] #ResourceName
{
    [DependsOn = [String[]]]
    Name = [String[]]
    [StartupType = [String]]
    [BuiltInAccount = [String]]
    [State = [String]]
    [Ensure = [String]]
    [Credential = [PSCredential]]
}
```

## <a name="processset"></a><span data-ttu-id="107af-112">ProcessSet</span><span class="sxs-lookup"><span data-stu-id="107af-112">ProcessSet</span></span>

```powershell
# Get the syntax of ProcessSet resource
Get-DscResource -Module psdesiredstateconfiguration -Name ProcessSet -Syntax

ProcessSet [String] #ResourceName
{
    [DependsOn = [String[]]]
    Path = [String[]]
    [Credential = [PSCredential]]
    [Ensure = [String]]
    [StandardOutputPath = [String]]
    [StandardErrorPath = [String]]
    [StandardInputPath = [String]]
    [WorkingDirectory = [String]]
}
```
