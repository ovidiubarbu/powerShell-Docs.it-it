---
ms.date: 06/12/2017
contributor: JKeithB
keywords: gallery,powershell,cmdlet,psgallery
title: Funzionalità FileList in PowerShell Gallery
ms.openlocfilehash: 5f372c943c73fa8e1014657394e40eaedef5d045
ms.sourcegitcommit: 4a2cf30351620a58ba95ff5d76b247e601907589
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 09/27/2019
ms.locfileid: "71328242"
---
# <a name="filelist-feature-in-the-gallery"></a>Funzionalità FileList in PowerShell Gallery

È possibile visualizzare il contenuto di tutti i pacchetti pubblicati in PowerShell Gallery.

Questa funzionalità è articolata in due parti: elenco dei file all'interno del pacchetto e visualizzazione del contenuto dei file per i tipi di file supportati. Attualmente è supportata la visualizzazione del contenuto per le estensioni di file seguenti: ps1, psm1, psd1, ps1xml, xml e txt. Nelle prossime versioni saranno supportate altre estensioni di file.

## <a name="where-to-find-filelist"></a>Posizione di FileList

Nella pagina di ogni singolo pacchetto sono presenti la sezione FileList e il collegamento **Mostra**. Fare clic su Mostra per visualizzare l'elenco completo degli elementi contenuti nel pacchetto.

Ogni tipo di file supportato viene visualizzato come collegamento ipertestuale. Se si fa clic su di esso, viene aperta una nuova pagina con il contenuto dei file con la sintassi PowerShell evidenziata. Se si fa clic sul titolo o sulla versione del pacchetto, disponibile nella parte superiore della schermata, viene di nuovo visualizzata la pagina dei dettagli del pacchetto.
