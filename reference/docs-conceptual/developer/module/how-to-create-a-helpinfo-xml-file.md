---
title: Come creare un file XML HelpInfo | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 3971ce1f-271c-4938-a9d3-47ff3aaf7219
caps.latest.revision: 9
ms.openlocfilehash: 7df9764fd573b75f285fec592448a550e481bea3
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/05/2019
ms.locfileid: "72367320"
---
# <a name="how-to-create-a-helpinfo-xml-file"></a>Come creare un file XML HelpInfo

Negli argomenti di questa sezione viene illustrato come creare e popolare un file di informazioni della guida, comunemente noto come "file XML HelpInfo", per la funzionalità della Guida aggiornabile di Windows PowerShell.

## <a name="helpinfo-xml-file-overview"></a>Panoramica del file XML HelpInfo

Il file XML HelpInfo è la fonte principale di informazioni sulla guida aggiornabile per il modulo. Include il percorso dei file della Guida per i moduli, le impostazioni cultura dell'interfaccia utente supportate e i numeri di versione utilizzati dalla guida aggiornabile per determinare se l'utente dispone dei file della guida più recenti.

Ogni modulo dispone di un solo file XML HelpInfo, anche se il modulo include più file della Guida per più impostazioni cultura dell'interfaccia utente. L'autore del modulo Crea il file XML HelpInfo e lo inserisce nel percorso Internet specificato dalla chiave **HelpInfoUri** nel manifesto del modulo. Quando i file della guida del modulo vengono aggiornati e caricati, l'autore del modulo Aggiorna il file XML HelpInfo e sostituisce il file XML HelpInfo originale con la nuova versione.

È fondamentale che il file XML HelpInfo venga mantenuto con attenzione. Se si caricano nuovi file, ma si dimentica di incrementare i numeri di versione, la guida aggiornabile non scaricherà i nuovi file nei computer degli utenti. Se si aggiungono i file della Guida per una nuova lingua dell'interfaccia utente, ma non si aggiorna il file XML HelpInfo o lo si inserisce nella posizione corretta, la guida aggiornabile non scaricherà i nuovi file.

## <a name="in-this-section"></a>Contenuto della sezione

Questa sezione include gli argomenti seguenti.

- [XML Schema HelpInfo](./helpinfo-xml-schema.md)

- [File di esempio XML HelpInfo](./helpinfo-xml-sample-file.md)

- [Come assegnare un nome a un file XML HelpInfo](./how-to-name-a-helpinfo-xml-file.md)

- [Come impostare i numeri di versione XML di HelpInfo](./how-to-set-helpinfo-xml-version-numbers.md)

## <a name="see-also"></a>Vedere anche

[Supporto della Guida aggiornabile](./supporting-updatable-help.md)