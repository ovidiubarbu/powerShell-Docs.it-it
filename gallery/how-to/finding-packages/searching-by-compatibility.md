---
ms.date: 12/11/2018
contributor: JKeithB, SydneyhSmith
keywords: gallery,powershell,cmdlet,psgallery
title: Pacchetti con sistema operativo o le edizioni di PowerShell compatibili
ms.openlocfilehash: 8230866561d3021379a48cc2c83fb4104a4058c1
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MTE95
ms.contentlocale: it-IT
ms.lasthandoff: 02/03/2019
ms.locfileid: "55680932"
---
# <a name="packages-with-compatible-powershell-editions-or-operating-systems"></a>Pacchetti con i sistemi operativi o le edizioni di PowerShell compatibili

A partire dalla versione 5.1, PowerShell è disponibile in diverse edizioni che indicano vari set di funzionalità e compatibilità della piattaforma.

## <a name="searching-by-powershell-edition"></a>La ricerca per edizione di PowerShell 
Le due edizioni di Powershell sono:
- **Desktop Edition:** è basata su .NET Framework e fornisce compatibilità con script e moduli destinati a versioni di PowerShell che eseguono edizioni footprint complete di Windows, ad esempio Server Core e Windows Desktop.
- **Core Edition:** è basata su .NET Core e fornisce compatibilità con script e moduli destinati a versioni di PowerShell che eseguono edizioni footprint ridotte di Windows, ad esempio Nano Server e Windows IoT.

### <a name="powershell-gallery-allows-you-to-filter-packages-compatible-for-specific-powershell-editions"></a>PowerShell Gallery consente di filtrare i pacchetti compatibili per specifiche le edizioni di PowerShell

Se dispone di un pacchetto compatibile PSEditions specificato, sono elencati come parte di 'Edizioni di PowerShell' nella pagina di visualizzazione del pacchetto e anche nei risultati di pacchetti.
È anche possibile cercare pacchetti compatibili con PowerShell.

![Pagina di visualizzazione dell'elemento con PSEditions](../../Images/packagedisplaypagewithpseditions.PNG)

### <a name="search-for-packages-in-the-gallery-ui-that-work-on-powershell-core"></a>Cercare i pacchetti nell'interfaccia utente della raccolta che funzionano in PowerShell Core

Usare Tags:"PSEdition_Desktop" e Tags:"PSEdition_Core" per filtrare i pacchetti in PowerShell Gallery.

### <a name="use-tagspseditioncore-to-search-items-compatible-with-powershell-core-edition"></a>Usare Tags:"PSEdition_Core" per cercare elementi compatibili con l'edizione Core di PowerShell.

![Cercare elementi compatibili con l'edizione Core di PowerShell nei risultati](../../Images/searchresultswithpseditions.PNG)

### <a name="use-tagspseditiondesktop-to-search-items-compatible-with-powershell-desktop-edition"></a>Usare Tags:"PSEdition_Desktop" per cercare elementi compatibili con l'edizione Desktop di PowerShell.

![Cercare elementi compatibili con l'edizione Desktop di PowerShell nei risultati](../../Images/searchresultswithpseditionsdesktop.PNG)

### <a name="search-for-packages-to-find-compatible-editions-using-powershell"></a>Cercare i pacchetti da trovare compatibili con PowerShell
È possibile specificare i tag per filtrare per l'edizione di PowerShell e il sistema operativo. Si utilizza il `Find-Package` cmdlet specificando il `-Tag` parametro per specificare l'edizione (e sistemi operativi) di destinazione.
Così:

```powershell
# Find modules compatible with PowerShell Core:
Find-Module -Tag PSEdition_Core

# Find modules compatible with PowerShell Core on Linux:
Find-Module -Tag PSEdition_Core, Linux
```

## <a name="searching-by-operating-system"></a>La ricerca dal sistema operativo 

Poiché PowerShell Core è disponibile per Windows, Linux e MacOS, nella raccolta di pacchetti possono essere progettati per qualsiasi combinazione di questi sistemi operativi. Interfaccia utente della raccolta utilizzare i tag seguenti di ricerca per trovare i pacchetti contrassegnati dal sistema operativo:

- Tag: "Windows"
- Tag: "Linux"
- Tag: "MacOS" 

È possibile specificare questi tag nella `Find-Module` e altri cmdlet nel modulo PowerShellGet, simile al seguente:

```powershell
# Find Modules compatible with Windows
Find-Module -Tag Linux
```

## <a name="searching-for-multiple-compatibilities"></a>La ricerca di compatibilità più

È possibile cercare un pacchetto con più di compatibilità usando la sintassi: 

Tag: "Compatibility1" "Compatibility2" 

Ad esempio, se si sta cercando un pacchetto con compatibilità di Core di PowerShell che viene eseguito nei computer personali Windows e Linux, usare i tag di ricerca:

Tag: "PSEdition_Core" "Windows" "Linux" 

Per eseguire una ricerca tramite PowerShell, è possibile usare il `Find-Module` e gli altri cmdlet nel modulo PowerShellGet, simile al seguente:

```powewrshell
# Find scripts compatible with PowerShell Core, Windows, and Linux
Find-Script -Tag PSEdition_Core,Linux,Windows

# Find modules compatible with PowerSHellCore and MacOS
Find-Module -Tag PSEdition_Core,MacOS
```

## <a name="more-details-on-authoring-and-finding-the-packages-with-compatible-powershell-editions"></a>Altre informazioni sulla creazione e la ricerca di pacchetti con edizioni di PowerShell compatibili

- [Moduli con edizioni di PS](../../concepts/module-psedition-support.md)
- [Script con PSEditions](../../concepts/script-psedition-support.md)
