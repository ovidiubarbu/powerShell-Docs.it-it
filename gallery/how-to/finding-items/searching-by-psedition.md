---
ms.date: 06/12/2017
contributor: JKeithB
keywords: gallery,powershell,cmdlet,psgallery
title: Elementi con versioni di PowerShell compatibili
ms.openlocfilehash: f661c2cd076acb9c11394ba0b752ebd154965ff4
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/16/2018
---
# <a name="items-with-compatible-powershell-editions"></a>Elementi con versioni di PowerShell compatibili

A partire dalla versione 5.1, PowerShell è disponibile in diverse edizioni che indicano vari set di funzionalità e compatibilità della piattaforma.

- **Desktop Edition:** è basata su .NET Framework e fornisce compatibilità con script e moduli destinati a versioni di PowerShell che eseguono edizioni footprint complete di Windows, ad esempio Server Core e Windows Desktop.
- **Core Edition:** è basata su .NET Core e fornisce compatibilità con script e moduli destinati a versioni di PowerShell che eseguono edizioni footprint ridotte di Windows, ad esempio Nano Server e Windows IoT.

## <a name="powershell-gallery-extracts-supported-pseditions-metadata-and-allows-you-to-filters-the-items-compatible-for-specific-powershell-editions"></a>PowerShell Gallery estrae i metadati PSEditions supportati e consente di filtrare gli elementi compatibili per specifiche le edizioni di PowerShell

Se per un elemento è specificato un valore PSEditions compatibile, verrà elencato come parte di "Edizioni di PowerShell" nella pagina di visualizzazione dell'elemento e anche nei risultati degli elementi.

![Pagina di visualizzazione dell'elemento con PSEditions](../../Images/ItemDisplayPageWithPSEditions.PNG)

## <a name="search-for-items-in-the-gallery-ui-which-works-on-powershellcore"></a>Cercare elementi compatibili con PowerShellCore nell'interfaccia utente della raccolta

Usare Tags:"PSEdition_Desktop" e Tags:"PSEdition_Core" per filtrare gli elementi in PowerShell Gallery.

### <a name="use-tagspseditioncore-to-search-items-compatible-with-powershell-core-edition"></a>Usare Tags:"PSEdition_Core" per cercare elementi compatibili con l'edizione Core di PowerShell.

![Cercare elementi compatibili con l'edizione Core di PowerShell nei risultati](../../Images/SearchResultsWithPSEditions.PNG)

### <a name="use-tagspseditiondesktop-to-search-items-compatible-with-powershell-desktop-edition"></a>Usare Tags:"PSEdition_Desktop" per cercare elementi compatibili con l'edizione Desktop di PowerShell.

![Cercare elementi compatibili con l'edizione Desktop di PowerShell nei risultati](../../Images/SearchResultsWithPSEdition-Desktop.PNG)

## <a name="more-details-on-authoring-and-finding-the-items-with-compatible-powershell-editions"></a>Altre informazioni sulla creazione e la ricerca di elementi con versioni di PowerShell compatibili

- [Moduli con edizioni di PS](../../concepts/module-psedition-support.md)
- [Script con PSEditions](../../concepts/script-psedition-support.md)