---
ms.date: 2017-06-12
contributor: JKeithB
ms.topic: conceptual
keywords: raccolta,powershell,cmdlet,psgallery
title: Eliminazione di elementi
ms.openlocfilehash: 00452f9b6625a51e95f3f46dbd66291fa20e17ad
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 06/12/2017
---
<a id="deleting-items" class="xliff"></a>
# Eliminazione di elementi

PowerShell Gallery non supporta l'eliminazione permanente di elementi perché questo impedirebbe la disponibilità di altri elementi dipendenti da quelli eliminati.

PowerShell Gallery supporta invece un modo per "escludere dall'elenco" un elemento, operazione che può essere eseguita nella pagina di gestione dell'elemento sul sito Web. Quando un elemento viene escluso dall'elenco, non viene più individuato dalle ricerche e non viene visualizzato in nessun elenco di elementi, né in PowerShell Gallery né usando i comandi PowerShellGet. È tuttavia possibile scaricarlo specificandone la versione esatta. Questo consente agli script automatizzati di continuare a funzionare.

Se si verifica una situazione eccezionale che richiede l'eliminazione di un elemento, tale operazione può essere eseguita manualmente dal team di PowerShell Gallery. Una violazione di copyright o la presenza di contenuto potenzialmente dannoso è una ragione valida per procedere all'eliminazione. In questo caso, è necessario inviare una richiesta di supporto tramite [PowerShell Gallery] (http://www.PowerShellGallery.com).

