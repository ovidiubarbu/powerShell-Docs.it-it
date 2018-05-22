---
ms.date: 06/12/2017
contributor: JKeithB
keywords: gallery,powershell,cmdlet,psgallery
title: Filtro dei risultati della ricerca
ms.openlocfilehash: eafbc993a37eaee7413102ef9d669a6b07d6ff6e
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/16/2018
---
# <a name="filtering-search-results"></a>Filtro dei risultati della ricerca

La [scheda Items](https://www.powershellgallery.com/items) (Elementi) visualizza tutti gli elementi disponibili in PowerShell Gallery.

Esistono diversi modi per filtrare, ordinare e cercare gli elementi.
Per altri dettagli su un particolare elemento, selezionarlo.

## <a name="filter-by"></a>Filter By (Filtro)

L'elenco a discesa in Filter By (Filtro) consente agli utenti di filtrare i risultati in base a:
- Includi versione preliminare
- Solo stabile

Per informazioni sui concetti di "versione preliminare" e "versione stabile", vedere [Prerelease Versioning Added to PowerShellGet and PowerShell Gallery](https://blogs.msdn.microsoft.com/powershell/2017/12/05/prerelease-versioning-added-to-powershellget-and-powershell-gallery/) (Aggiunta delle versioni preliminari a PowerShellGet e PowerShell Gallery) nel blog del team di PowerShell.

Le caselle di controllo sotto l'elenco a discesa consentono agli utenti di filtrare i risultati in base a:
- Tipi di elemento
  - Modulo
  - Script
- Categorie
  - Cmdlet
  - DSC Resource (Risorsa DSC)
  - Function
  - Funzionalità di ruolo
  - Flusso di lavoro

Per visualizzare solo i moduli in PowerShell Gallery, selezionare Module (Modulo) nell'elenco a discesa Item Types (Tipi di elemento).
In modo analogo, per visualizzare solo gli script in PowerShell Gallery, selezionare Script nell'elenco a discesa Item Types (Tipi di elemento).

> [!NOTE]
> I filtri sono inclusivi.
> Esempio: un elemento che include sia cmdlet che funzioni viene visualizzato sia quando è selezionato Cmdlet che Function (o entrambi).
> Se non è selezionato nessuno dei due tipi, l'elemento non viene visualizzato.
> Analogamente, se vengono selezionate tutte le categorie, verranno visualizzati solo gli elementi che contengono una di queste categorie.
> **Non verranno visualizzati gli elementi che non appartengono ad alcuna di queste categorie.**

## <a name="sort-by"></a>Sort By (Ordina per)

L'elenco a discesa Sort By (Ordina per) consente agli utenti di ordinare i risultati in base a:
- Popularity (Popolarità): la popolarità viene determinata dal numero di download
- A-Z: in ordine alfabetico in base al nome dell'elemento
- Recent (Recenti): gli elementi vengono ordinati in base alla data di pubblicazione

## <a name="search-box"></a>Casella di ricerca

La casella di ricerca consente di cercare gli elementi in base a parole chiave.
Per altre informazioni, vedere [Sintassi di ricerca di PowerShell Gallery](search-syntax.md).