---
ms.date: 06/12/2017
contributor: JKeithB
keywords: gallery,powershell,cmdlet,psgallery
title: Eliminazione di elementi
ms.openlocfilehash: 454cd404437bf1c31b9a1b81cd9dd0ac81e6b0f6
ms.sourcegitcommit: 8b076ebde7ef971d7465bab834a3c2a32471ef6f
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 07/06/2018
ms.locfileid: "37893094"
---
# <a name="deleting-items"></a>Eliminazione di elementi

PowerShell Gallery non supporta l'eliminazione permanente di elementi perché questo impedirebbe la disponibilità di altri elementi dipendenti da quelli eliminati.

PowerShell Gallery supporta invece un modo per "escludere dall'elenco" un elemento, operazione che può essere eseguita nella pagina di gestione dell'elemento sul sito Web.
Quando un elemento viene escluso dall'elenco, non viene più individuato dalle ricerche e non viene visualizzato in nessun elenco di elementi, né in PowerShell Gallery né usando i comandi PowerShellGet.
È tuttavia possibile scaricarlo specificandone la versione esatta. Questo consente agli script automatizzati di continuare a funzionare.

Se si verifica una situazione eccezionale che richiede l'eliminazione di un elemento, tale operazione può essere eseguita manualmente dal team di PowerShell Gallery.
Una violazione di copyright o la presenza di contenuto potenzialmente dannoso è una ragione valida per procedere all'eliminazione.
In questo caso, è necessario inviare una richiesta di supporto tramite [PowerShell Gallery](http://www.PowerShellGallery.com).