---
ms.date: 06/12/2017
contributor: JKeithB
keywords: gallery,powershell,cmdlet,psgallery
title: Esclusione di pacchetti dall'elenco
ms.openlocfilehash: fb66fd23dae1d4640056a764c31426f61f56d910
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 12/05/2019
ms.locfileid: "71328272"
---
# <a name="unlisting-packages"></a>Esclusione di pacchetti dall'elenco

**Perché la rimozione di un pacchetto da PowerShell Gallery non è disponibile come opzione?**

PowerShell Gallery non supporta l'eliminazione permanente di pacchetti da parte degli utenti.
Questo consente ad altre persone di creare dipendenze dai pacchetti di un utente senza preoccupazioni per possibili interruzioni nel futuro.
Se, ad esempio, il modulo Pester dipende dal modulo Azure e quest'ultimo viene rimosso da PowerShell Gallery, l'utente non può più usare il modulo Pester.

Anziché rimuovere un pacchetto, tuttavia, è possibile escluderlo dall'elenco.

**Quali sono le conseguenze dell'esclusione di un pacchetto dall'elenco in PowerShell Gallery?**

L'esclusione di un pacchetto dall'elenco, ad esempio un modulo o uno script, in PowerShell Gallery determina la rimozione di tale elemento dalla scheda Packages (Pacchetti). I pacchetti esclusi dall'elenco, inoltre, non possono essere individuati usando la barra di ricerca.
Il solo modo per scaricare un pacchetto escluso dall'elenco consiste nello specificarne esattamente il nome e la versione.
Per questo motivo, l'esclusione di un pacchetto dall'elenco non causa interruzioni per altri moduli o script dipendenti.

Per escludere il pacchetto dall'elenco, visitare la pagina dei dettagli del pacchetto e selezionare 'Delete Module' (Elimina modulo). Deselezionare la casella di controllo 'Listed' (Elencato) e fare clic su Salva.

**In che modo è possibile rimuovere un pacchetto?**

Se si verifica uno scenario in cui è necessario eliminare un pacchetto, contattare gli amministratori di PowerShell Gallery.
Gli scenari di eliminazione validi sono i seguenti:
- Problemi relativi alla violazione del copyright.
- Pacchetti con contenuto potenzialmente dannoso.
- Pacchetti contenenti dati sensibili.

Per inviare una richiesta di eliminazione di un pacchetto agli amministratori di PowerShell Gallery, visitare la pagina dei dettagli del pacchetto e selezionare Contact Support (Contattare il supporto tecnico).
