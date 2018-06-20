---
ms.date: 06/12/2017
contributor: JKeithB
keywords: gallery,powershell,cmdlet,psgallery
title: Esclusione di elementi dall'elenco
ms.openlocfilehash: bdcceba0ba18ade6a1d0f94602fd8d0f64af8936
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/16/2018
ms.locfileid: "34187535"
---
# <a name="unlisting-items"></a>Esclusione di elementi dall'elenco

**Perché la rimozione di un elemento da PowerShell Gallery non è disponibile come opzione?**

PowerShell Gallery non supporta l'eliminazione permanente di elementi da parte degli utenti.
Questo consente ad altre persone di creare dipendenze sugli elementi dell'utente senza preoccupazioni per possibili interruzioni nel futuro.
Se, ad esempio, il modulo Pester dipende dal modulo Azure e quest'ultimo viene rimosso da PowerShell Gallery, l'utente non può più usare il modulo Pester.

Anziché rimuovere un elemento, tuttavia, è possibile escluderlo dall'elenco.

**Quali sono le conseguenze dell'esclusione di un elemento dall'elenco in PowerShell Gallery?**

L'esclusione di un elemento dall'elenco, ad esempio un modulo o uno script, in PowerShell Gallery determina la rimozione di tale elemento dalla scheda Elementi. Gli elementi esclusi dall'elenco, inoltre, non possono essere individuati usando la barra di ricerca.
Il solo modo per scaricare un elemento escluso dall'elenco consiste nello specificarne esattamente il nome e la versione.
Per questo motivo, l'esclusione di un elemento dall'elenco non interrompe altri moduli o script che dipendono da esso.

Per escludere un elemento dall'elenco, visitare la relativa pagina dei dettagli e selezionare 'Elimina elemento'. Deselezionare la casella di controllo 'Listed' (Elencato) e fare clic su Salva.

**In che modo è possibile rimuovere un elemento?**

Se si verifica uno scenario in cui è necessario eliminare un elemento, contattare gli amministratori di PowerShell Gallery.
Gli scenari di eliminazione validi sono i seguenti:
- Problemi relativi alla violazione del copyright.
- Elementi con contenuto potenzialmente dannoso.
- Elementi contenenti dati sensibili.

Per inviare una richiesta di eliminazione di un elemento agli amministratori di PowerShell Gallery, visitare la pagina dei dettagli dell'elemento e selezionare Come contattare il supporto tecnico.