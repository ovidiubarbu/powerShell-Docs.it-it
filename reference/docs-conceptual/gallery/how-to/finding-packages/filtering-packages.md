---
ms.date: 06/12/2017
contributor: JKeithB
keywords: gallery,powershell,cmdlet,psgallery
title: Filtro dei risultati della ricerca
ms.openlocfilehash: 13270a310613a974e1588a9f56d443a936cfebb8
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 12/05/2019
ms.locfileid: "71328042"
---
# <a name="filtering-search-results"></a>Filtro dei risultati della ricerca

Nella [scheda Packages](https://www.powershellgallery.com/packages) (Pacchetti) vengono visualizzati tutti i pacchetti disponibili in PowerShell Gallery.

Esistono diversi modi per filtrare, ordinare e cercare i pacchetti.
Per visualizzare altri dettagli su un particolare pacchetto, fare clic sul pacchetto.

## <a name="filter-by"></a>Filter By (Filtro)

L'elenco a discesa in Filter By (Filtro) consente agli utenti di filtrare i risultati in base a:
- Includi versione preliminare
- Solo stabile

Per informazioni sui concetti di "versione preliminare" e "versione stabile", vedere [Prerelease Versioning Added to PowerShellGet and PowerShell Gallery](https://blogs.msdn.microsoft.com/powershell/2017/12/05/prerelease-versioning-added-to-powershellget-and-powershell-gallery/) (Aggiunta delle versioni preliminari a PowerShellGet e PowerShell Gallery) nel blog del team di PowerShell.

Le caselle di controllo sotto l'elenco a discesa consentono agli utenti di filtrare i risultati in base a:
- Tipi di pacchetto
  - Modulo
  - Script
- Categorie
  - Cmdlet
  - DSC Resource (Risorsa DSC)
  - Function
  - Funzionalità di ruolo
  - Flusso di lavoro

Per visualizzare solo i moduli in PowerShell Gallery, selezionare Module (Modulo) nell'elenco a discesa Package Types (Tipi di pacchetto).
In modo analogo, per visualizzare solo gli script in PowerShell Gallery, selezionare Script nell'elenco a discesa Package Types (Tipi di pacchetto).

> [!NOTE]
> I filtri sono inclusivi.
> Esempio: un pacchetto che include sia cmdlet che funzioni viene visualizzato sia quando è selezionato Cmdlet che Function (o entrambi).
> Se non è selezionato nessuno dei due tipi, il pacchetto non viene visualizzato.
> Analogamente, se vengono selezionate tutte le categorie, verranno visualizzati solo i pacchetti che contengono una di queste categorie.
> **Non verranno visualizzati i pacchetti che non appartengono ad alcuna di queste categorie.**

## <a name="sort-by"></a>Sort By (Ordina per)

L'elenco a discesa Sort By (Ordina per) consente agli utenti di ordinare i risultati in base a:
- Popularity (Popolarità): la popolarità viene determinata dal numero di download
- A-Z: in ordine alfabetico per nome del pacchetto
- Recent (Recenti): i pacchetti vengono ordinati in base alla data di pubblicazione

## <a name="search-box"></a>Casella di ricerca

La casella di ricerca consente di cercare i pacchetti in base a parole chiave.
Per altre informazioni, vedere [Sintassi di ricerca di PowerShell Gallery](search-syntax.md).
