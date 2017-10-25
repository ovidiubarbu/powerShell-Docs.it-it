---
ms.date: 2017-06-12
contributor: JKeithB
ms.topic: conceptual
keywords: raccolta,powershell,cmdlet,psgallery
title: psgallery_items_tab
ms.openlocfilehash: 8424c4729436a78fec3fdbb405591fcd3c6bc6a6
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 06/12/2017
---
<a name="items-tab"></a>Scheda Items (Elementi)
==========

La scheda Items (Elementi) visualizza tutti gli elementi disponibili in PowerShell Gallery.

Per visualizzare solo i moduli in PowerShell Gallery, fare clic su Modules (Moduli) nell'elenco a discesa della scheda Items (Elementi).  Analogamente, per visualizzare solo gli script in PowerShell Gallery, fare clic su Script nell'elenco a discesa della scheda Items (Elementi).  

Per altri dettagli su un particolare elemento, selezionarlo.

Esistono diversi modi per ordinare gli elementi:

##<a name="filter-by"></a>Filter By (Filtro)##
La sezione Filter By (Filtro) consente agli utenti di filtrare i risultati in base a:
* Item Types (Tipi di elemento):
    * Moduli
    * Script
* Categoria:
    * Cmdlet
    * DSC Resource (Risorsa DSC)
    * Function
    * Flusso di lavoro

Nota: i filtri sono inclusivi.  
Esempio: un elemento che include sia cmdlet che funzioni viene visualizzato sia quando è selezionato Cmdlet che Function (o entrambi).  Se non è selezionato nessuno dei due tipi, l'elemento non viene visualizzato.  
Analogamente, se vengono selezionate tutte le categorie, verranno visualizzati solo gli elementi che contengono una di queste categorie. **Non verranno visualizzati gli elementi che non appartengono ad alcuna di queste categorie.**

##<a name="sort-by"></a>Sort By (Ordina per)## 
L'elenco a discesa Sort By (Ordina per) consente agli utenti di ordinare i risultati in base a:
* Popularity (Popolarità): la popolarità viene determinata dal numero di download.
* A-Z: in ordine alfabetico in base al nome dell'elemento.
* Recent (Recenti): gli elementi vengono ordinati in base alla data di pubblicazione.


##<a name="search-box"></a>Casella di ricerca##
La casella di ricerca consente di cercare gli elementi in base a parole chiave.  
Vedere [Sintassi di ricerca di PowerShell Gallery](./psgallery_search_syntax.md) per altre informazioni.

