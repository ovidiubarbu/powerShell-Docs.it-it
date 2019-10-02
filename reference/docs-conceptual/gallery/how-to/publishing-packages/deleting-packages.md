---
ms.date: 06/12/2017
contributor: JKeithB
keywords: gallery,powershell,cmdlet,psgallery
title: Eliminazione di pacchetti
ms.openlocfilehash: 6bfb43b95e51d38bd606198cb8d2d9af0aa0be1e
ms.sourcegitcommit: 4a2cf30351620a58ba95ff5d76b247e601907589
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 09/27/2019
ms.locfileid: "71327932"
---
# <a name="deleting-packages"></a>Eliminazione di pacchetti

PowerShell Gallery non supporta l'eliminazione permanente di pacchetti perché questo causerebbe interruzioni per altri pacchetti dipendenti.

PowerShell Gallery supporta invece un modo per 'escludere dall'elenco' un pacchetto, operazione che può essere eseguita nella pagina di gestione del pacchetto nel sito Web.
Quando un pacchetto viene escluso dall'elenco, non compare più nelle ricerche e non viene visualizzato in nessun elenco di pacchetti, né in PowerShell Gallery né usando i comandi PowerShellGet.
È tuttavia possibile scaricarlo specificandone la versione esatta. Questo consente agli script automatizzati di continuare a funzionare.

Se si verifica una situazione eccezionale che richiede l'eliminazione di un pacchetto, tale operazione può essere eseguita manualmente dal team di PowerShell Gallery.
Una violazione di copyright o la presenza di contenuto potenzialmente dannoso è una ragione valida per procedere all'eliminazione.
In questo caso, è necessario inviare una richiesta di supporto tramite [PowerShell Gallery](https://www.PowerShellGallery.com).
