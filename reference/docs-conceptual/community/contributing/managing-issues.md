---
title: Modalità di gestione dei problemi
description: Questo articolo illustra in che modo il team PowerShell-Docs gestisce le richieste pull.
ms.date: 03/05/2020
ms.topic: conceptual
ms.openlocfilehash: cd7aba83d42a6a2eba1ce73910fdd34096342c21
ms.sourcegitcommit: 6545c60578f7745be015111052fd7769f8289296
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/22/2020
ms.locfileid: "79060276"
---
# <a name="how-we-manage-issues"></a>Modalità di gestione dei problemi

Questo articolo descrive come vengono gestiti i problemi nel repository PowerShell-Docs. Concepito come strumento di lavoro per i membri del team PowerShell-Docs, viene pubblicato qui per garantire la trasparenza dei processi per i collaboratori pubblici.

## <a name="sources-of-issues"></a>Origini delle segnalazioni dei problemi

- Collaboratori della community
- Collaboratori interni
- Trascrizioni di commenti dai canali di social media
- Feedback tramite il modulo di feedback di Docs

## <a name="response-time-targets"></a>Obiettivi per il tempo di risposta

- Valutazione: 5 giorni lavorativi
- Correzione o modifica: nessun obiettivo specifico, si segue solo il principio del massimo sforzo

### <a name="labeling--milestones"></a>Etichettatura e attività cardine

#### <a name="label-types"></a>Tipi di etichetta

|Prefisso  | Descrizione                                                         |
|------- | --------------------------------------------------------------------|
|Area    | Usato per indicare la parte di PowerShell o della documentazione che tratta il problema.<br>Utile per i proprietari di funzionalità per individuare i problemi correlati alla propria funzionalità.|
|Pri     | Usato per indicare la priorità del problema. Intervallo dei valori: 0-4.        |
|Problema   | Usato per classificare il tipo di feedback per il problema                     |
|Verifica  | Usato per i problemi che richiedono un ulteriore esame da parte del team              |
|Stato  | Usato per indicare lo stato dell'elemento di lavoro                        |
|Waiting | Usato per indicare l'attesa in corso                   |

#### <a name="milestones"></a>Milestones

I problemi e le richieste pull devono essere contrassegnati con l'attività cardine appropriata. Se il problema non riguarda una versione specifica, non viene usata alcuna attività cardine. I problemi delle richieste pull di Docs per le modifiche che devono ancora essere unite alla codebase di PowerShell devono essere assegnati all'attività cardine **Futuro**. Dopo l'unione della modifica del codice, impostare l'attività cardine sulla versione appropriata.

|    Attività cardine     |                    Descrizione                     |
| ---------------- | -------------------------------------------------- |
| 6.x              | Elementi di lavoro correlati a PowerShell versioni 6.0 - 6.2. x |
| 7.0.0            | Elementi di lavoro correlati a PowerShell 7.0               |
| 7.1.0            | Elementi di lavoro correlati a PowerShell 7.1               |
| In futuro           | Elementi di lavoro per una versione futura di PowerShell          |
| PSReadline-vNext | Elementi di lavoro per una versione futura di PSReadline          |

## <a name="triage-process"></a>Processo di valutazione

Il team PowerShell-Docs si incontra una volta alla settimana per parlare degli eventuali problemi che si sono aggiunti dall'ultima riunione. Un problema è considerato valutato se a questo sono state assegnate etichette o un proprietario. I membri del team PowerShell-Docs sono invitati a esaminare i problemi quotidianamente e a valutare i nuovi problemi man mano che arrivano. La riunione settimanale di valutazione può quindi essere usata per trattare i nuovi problemi in modo più dettagliato, a seconda delle esigenze.

### <a name="misplaced-product-feedback"></a>Feedback sul prodotto indicato in un punto non corretto

- Immettere un commento per il cliente specificando che si tratta di feedback sul prodotto e indicando il collegamento al canale di feedback appropriato.
- Facoltativo: copiare il problema nella posizione appropriata per il feedback sul prodotto, aggiungere un collegamento all'elemento copiato e chiudere il problema. NON copiare problemi in UserVoice.

  | DocSet    | URL di feedback sul prodotto                                         |
  | --------- | ------------------------------------------------------------ |
  | developer | https://github.com/PowerShell/PowerShell/issues/new/choose   |
  | dsc       | https://windowsserver.uservoice.com/forums/301869-powershell |
  | gallery   | https://github.com/powershell/powershellgallery/issues/new   |
  | jea       | https://github.com/powershell/jea/issues/new                 |
  | reference | https://github.com/PowerShell/PowerShell/issues/new/choose   |
  | wmf       | https://windowsserver.uservoice.com/forums/301869-powershell |

### <a name="support-requests"></a>Richieste di supporto

- Se la domanda è semplice, rispondere gentilmente e chiudere il problema.
- Se la domanda è più complessa o se il mittente risponde con altre domande, reindirizzarlo ai forum e ai canali di supporto. Testo suggerito per il reindirizzamento ai forum:

    > Questo non è il forum appropriato per domande di questo tipo. Provare a pubblicare la domanda in un forum di supporto della community. Per un elenco di forum della community, vedere: https://docs.microsoft.com/powershell/scripting/community/community-support

### <a name="code-of-conduct-violations"></a>Violazioni del codice di comportamento

- Modificare il problema per rimuovere eventuale contenuto offensivo, se necessario.
- Immettere un commento indicando che il problema costituisce posta indesiderata, chiudere il problema e quindi bloccarlo per evitare altri commenti.
- Ogni occorrenza deve essere discussa nella riunione settimanale di valutazione per determinare la necessità di altre azioni (segnalazione in GitHub o al team legale di Microsoft).
