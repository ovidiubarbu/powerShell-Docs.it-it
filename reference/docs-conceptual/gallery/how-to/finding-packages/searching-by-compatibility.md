---
ms.date: 12/11/2018
contributor: JKeithB, SydneyhSmith
keywords: gallery,powershell,cmdlet,psgallery
title: Pacchetti con edizioni di PowerShell o sistema operativo compatibili
ms.openlocfilehash: b414ce2c2b189e9da150cbe612e0bb2572d39e76
ms.sourcegitcommit: 01c60c0c97542dbad48ae34339cddbd813f1353b
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 03/04/2020
ms.locfileid: "78278367"
---
# <a name="packages-with-compatible-powershell-editions-or-operating-systems"></a>Pacchetti con edizioni di PowerShell o sistemi operativi compatibili

A partire dalla versione 5.1, PowerShell è disponibile in diverse edizioni che indicano vari set di funzionalità e compatibilità della piattaforma.

## <a name="searching-by-powershell-edition"></a>Ricerca in base all'edizione di PowerShell

Le edizioni di PowerShell sono due:
- **Desktop Edition:** si basa su .NET Framework e garantisce compatibilità con script e moduli destinati a versioni di PowerShell eseguiti in edizioni di Windows con footprint completo, ad esempio Server Core e Windows Desktop.
- **Core Edition:** si basa su .NET Core e garantisce compatibilità con script e moduli destinati a versioni di PowerShell eseguiti in edizioni di Windows con footprint ridotto, ad esempio Nano Server e Windows IoT.

### <a name="powershell-gallery-allows-you-to-filter-packages-compatible-for-specific-powershell-editions"></a>PowerShell Gallery consente di filtrare i pacchetti compatibili in base a edizioni specifiche di PowerShell

Se per un pacchetto viene specificato un valore PSEditions compatibile, viene elencato come parte di "PowerShell Editions" nella pagina di visualizzazione del pacchetto e anche nei risultati dei pacchetti.
È anche possibile cercare i pacchetti compatibili usando PowerShell.

![Pagina di visualizzazione dell'elemento con PSEditions](media/searching-by-compatibility/packagedisplaypagewithpseditions.PNG)

### <a name="search-for-packages-in-the-gallery-ui-that-work-on-powershell-core"></a>Cercare pacchetti compatibili con PowerShellCore nell'interfaccia utente di PowerShell Gallery

Usare Tags:"PSEdition_Desktop" e Tags:"PSEdition_Core" per filtrare i pacchetti in PowerShell Gallery.

### <a name="use-tagspsedition_core-to-search-items-compatible-with-powershell-core-edition"></a>Usare Tags:"PSEdition_Core" per cercare elementi compatibili con l'edizione Core di PowerShell.

![Cercare elementi compatibili con l'edizione Core di PowerShell nei risultati](media/searching-by-compatibility/searchresultswithpseditions.PNG)

### <a name="use-tagspsedition_desktop-to-search-items-compatible-with-powershell-desktop-edition"></a>Usare Tags:"PSEdition_Desktop" per cercare elementi compatibili con l'edizione Desktop di PowerShell.

![Cercare elementi compatibili con l'edizione Desktop di PowerShell nei risultati](media/searching-by-compatibility/searchresultswithpseditionsdesktop.PNG)

### <a name="search-for-packages-to-find-compatible-editions-using-powershell"></a>Cercare i pacchetti per trovare le edizioni compatibili usando PowerShell
È possibile specificare i tag per filtrare per l'edizione di PowerShell e il sistema operativo.
Usare il cmdlet `Find-Package` specificando il parametro `-Tag` per cercare l'edizione e il sistemo operativo di destinazione,
nel modo seguente:

```powershell
# Find modules compatible with PowerShell Core:
Find-Module -Tag PSEdition_Core

# Find modules compatible with PowerShell Core on Linux:
Find-Module -Tag PSEdition_Core, Linux
```

## <a name="searching-by-operating-system"></a>Ricerca in base al sistema operativo

PowerShell Core è disponibile per Windows, Linux e MacOS, quindi in PowerShell Gallery i pacchetti possono essere progettati per una qualsiasi combinazione di questi sistemi operativi. Nell'interfaccia utente di PowerShell Gallery usare i tag di ricerca seguenti per trovare i pacchetti contrassegnati dal sistema operativo:

- Tag: "Windows"
- Tag: "Linux"
- Tag: "MacOS"

È possibile specificare questi tag in `Find-Module` e altri cmdlet nel modulo PowerShellGet, nel modo seguente:

```powershell
# Find Modules compatible with Windows
Find-Module -Tag Linux
```

## <a name="searching-for-multiple-compatibilities"></a>Ricerca in base a compatibilità multiple

È possibile cercare un pacchetto con più compatibilità usando la sintassi seguente:

Tag: "Compatibility1" "Compatibility2"

Ad esempio, se si sta cercando un pacchetto compatibile con PowerShell Core che viene eseguito sia in computer Windows sia in computer Linux, usare i tag di ricerca seguenti:

Tag: "PSEdition_Core" "Windows" "Linux"

Per eseguire una ricerca tramite PowerShell, è possibile usare il cmdlet `Find-Module` e altri cmdlet nel modulo PowerShellGet, nel modo seguente:

```powershell
# Find scripts compatible with PowerShell Core, Windows, and Linux
Find-Script -Tag PSEdition_Core,Linux,Windows

# Find modules compatible with PowerSHellCore and MacOS
Find-Module -Tag PSEdition_Core,MacOS
```

## <a name="more-details-on-authoring-and-finding-the-packages-with-compatible-powershell-editions"></a>Altre informazioni sulla creazione e la ricerca di pacchetti con edizioni di PowerShell compatibili

- [Moduli con edizioni di PS](../../concepts/module-psedition-support.md)
- [Script con PSEditions](../../concepts/script-psedition-support.md)
