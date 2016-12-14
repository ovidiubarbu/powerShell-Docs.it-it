---
description: 
manager: carolz
ms.topic: article
author: jpjofre
ms.prod: powershell
keywords: powershell,cmdlet,gallery
ms.date: 2016-10-14
contributor: manikb
title: psgallery_items_tab
ms.technology: powershell
ms.openlocfilehash: 32f28df7318472f34f79c61f19f33016cf73f517
ms.sourcegitcommit: c732e3ee6d2e0e9cd8c40105d6fbfd4d207b730d
translationtype: HT
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

