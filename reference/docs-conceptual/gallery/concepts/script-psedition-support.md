---
ms.date: 06/12/2017
contributor: manikb
keywords: raccolta,powershell,cmdlet,psget
title: Script con versioni di PowerShell compatibili
ms.openlocfilehash: e364879f611429a8583e550fb7704431e456fbb1
ms.sourcegitcommit: 4a2cf30351620a58ba95ff5d76b247e601907589
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 09/27/2019
ms.locfileid: "71328062"
---
# <a name="script-with-compatible-powershell-editions"></a>Script con versioni di PowerShell compatibili

A partire dalla versione 5.1, PowerShell è disponibile in diverse edizioni che indicano vari set di funzionalità e compatibilità della piattaforma.

- **Desktop Edition:** si basa su .NET Framework e garantisce compatibilità con script e moduli destinati a versioni di PowerShell eseguiti in edizioni di Windows con footprint completo, ad esempio Server Core e Windows Desktop.

- **Core Edition:** si basa su .NET Core e garantisce compatibilità con script e moduli destinati a versioni di PowerShell eseguiti in edizioni di Windows con footprint ridotto, ad esempio Nano Server e Windows IoT.

L'edizione di PowerShell in esecuzione viene visualizzata nella proprietà PSEdition di $PSVersionTable.

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

Gli autori di script possono impedire l'esecuzione di uno script a meno che non venga eseguito in una versione compatibile di PowerShell usando il parametro PSEdition in un'istruzione `#requires`.

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

Gli utenti di PowerShell Gallery possono trovare l'elenco degli script supportati in una determinata edizione di PowerShell.
Gli script senza tag PSEdition_Desktop e PSEditon_Core sono considerati idonei per l'edizione Desktop di PowerShell.

```powershell
# Find scripts supported on PowerShell Desktop edition
Find-Script -Tag PSEdition_Desktop

# Find scripts supported on PowerShell Core edition
Find-Script -Tag PSEdition_Core
```

## <a name="more-details"></a>Altri dettagli

- [Moduli con edizioni di PS](module-psedition-support.md)
- [Supporto di PSEditions nella raccolta di PowerShell](../how-to/finding-packages/searching-by-compatibility.md)
