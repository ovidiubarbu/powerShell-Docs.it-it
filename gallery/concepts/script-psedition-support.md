---
ms.date: 06/12/2017
contributor: manikb
keywords: raccolta,powershell,cmdlet,psget
title: Script con versioni di PowerShell compatibili
ms.openlocfilehash: e364879f611429a8583e550fb7704431e456fbb1
ms.sourcegitcommit: 548547b2d5fc73e726bb9fec6175d452a351d975
ms.translationtype: MTE95
ms.contentlocale: it-IT
ms.lasthandoff: 12/20/2018
ms.locfileid: "53655277"
---
# <a name="script-with-compatible-powershell-editions"></a><span data-ttu-id="6e86e-103">Script con versioni di PowerShell compatibili</span><span class="sxs-lookup"><span data-stu-id="6e86e-103">Script with compatible PowerShell editions</span></span>

<span data-ttu-id="6e86e-104">A partire dalla versione 5.1, PowerShell è disponibile in diverse edizioni che indicano vari set di funzionalità e compatibilità della piattaforma.</span><span class="sxs-lookup"><span data-stu-id="6e86e-104">Starting with version 5.1, PowerShell is available in different editions which denote varying feature sets and platform compatibility.</span></span>

- <span data-ttu-id="6e86e-105">Desktop Edition Basato su .NET Framework e fornisce compatibilità con script e moduli destinati a versioni di PowerShell che eseguono edizioni footprint complete di Windows, ad esempio Server Core e Windows Desktop.</span><span class="sxs-lookup"><span data-stu-id="6e86e-105">**Desktop Edition:** Built on .NET Framework and provides compatibility with scripts and modules targeting versions of PowerShell running on full footprint editions of Windows such as Server Core and Windows Desktop.</span></span>

- <span data-ttu-id="6e86e-106">**Core Edition:** Basata su .NET Core e fornisce compatibilità con script e moduli destinati a versioni di PowerShell che eseguono edizioni footprint ridotte di Windows, ad esempio Nano Server e Windows IoT.</span><span class="sxs-lookup"><span data-stu-id="6e86e-106">**Core Edition:** Built on .NET Core and provides compatibility with scripts and modules targeting versions of PowerShell running on reduced footprint editions of Windows such as Nano Server and Windows IoT.</span></span>

<span data-ttu-id="6e86e-107">L'edizione di PowerShell in esecuzione viene visualizzata nella proprietà PSEdition di $PSVersionTable.</span><span class="sxs-lookup"><span data-stu-id="6e86e-107">The running edition of PowerShell is shown in the PSEdition property of $PSVersionTable.</span></span>

```powershell
$PSVersionTable

Name                           Value
----                           -----
PSVersion                      5.1.14300.1000
PSEdition                      Desktop
PSCompatibleVersions           {1.0, 2.0, 3.0, 4.0...}
CLRVersion                     4.0.30319.42000
BuildVersion                   10.0.14300.1000
WSManStackVersion              3.0
PSRemotingProtocolVersion      2.3
SerializationVersion           1.1.0.1
```

<span data-ttu-id="6e86e-108">Gli autori di script possono impedire l'esecuzione di uno script a meno che non venga eseguito in una versione compatibile di PowerShell usando il parametro PSEdition in un'istruzione `#requires`.</span><span class="sxs-lookup"><span data-stu-id="6e86e-108">Script authors can prevent a script from executing unless it is run on a compatible edition of PowerShell using the PSEdition parameter on a `#requires` statement.</span></span>

```powershell
Set-Content C:\script.ps1 -Value "#requires -PSEdition Core
Get-Process -Name PowerShell"
Get-Content C:\script.ps1
#requires -PSEdition Core
Get-Process -Name PowerShell

C:\script.ps1
C:\script.ps1 : The script 'script.ps1' cannot be run because it contained a "#requires" statement for PowerShell editions 'Core'. The edition of PowerShell that is required by the script does not match the currently running PowerShell Desktop edition.
At line:1 char:1
+ C:\script.ps1
+ ~~~~~~~~~~~~~
    + CategoryInfo          : NotSpecified: (script.ps1:String) [], RuntimeException
    + FullyQualifiedErrorId : ScriptRequiresUnmatchedPSEdition
```

<span data-ttu-id="6e86e-109">Gli utenti di PowerShell Gallery possono trovare l'elenco degli script supportati in una determinata edizione di PowerShell.</span><span class="sxs-lookup"><span data-stu-id="6e86e-109">PowerShell Gallery users can find the list of scripts supported on a specific PowerShell Edition.</span></span>
<span data-ttu-id="6e86e-110">Gli script senza tag PSEdition_Desktop e PSEditon_Core sono considerati idonei per l'edizione Desktop di PowerShell.</span><span class="sxs-lookup"><span data-stu-id="6e86e-110">Scripts without PSEdition_Desktop and PSEdition_Core tags are considered to work fine on PowerShell Desktop edition.</span></span>

```powershell
# Find scripts supported on PowerShell Desktop edition
Find-Script -Tag PSEdition_Desktop

# Find scripts supported on PowerShell Core edition
Find-Script -Tag PSEdition_Core
```

## <a name="more-details"></a><span data-ttu-id="6e86e-111">Altri dettagli</span><span class="sxs-lookup"><span data-stu-id="6e86e-111">More details</span></span>

- [<span data-ttu-id="6e86e-112">Moduli con edizioni di PS</span><span class="sxs-lookup"><span data-stu-id="6e86e-112">Modules with PSEditions</span></span>](module-psedition-support.md)
- [<span data-ttu-id="6e86e-113">Supporto di PSEditions nella raccolta di PowerShell</span><span class="sxs-lookup"><span data-stu-id="6e86e-113">PSEditions support on PowerShellGallery</span></span>](../how-to/finding-packages/searching-by-compatibility.md)
