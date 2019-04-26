---
title: Scrittura della Guida per i cmdlet di PowerShell | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 55908d67-7cbe-482a-a105-5a6da93c5311
caps.latest.revision: 4
ms.openlocfilehash: 8d692cf88d1d356886ef973f0989294d6b51ee6d
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62083162"
---
# <a name="writing-help-for-powershell-cmdlets"></a>La scrittura Guida per i cmdlet di PowerShell

I cmdlet di PowerShell possono essere utili, ma, a meno che gli argomenti della Guida spiegano chiaramente il cmdlet non e come usarlo, il cmdlet non può ottenere usato o, peggio ancora, potrebbe causare frustrazione gli utenti.
Il formato del file della Guida cmdlet basato su XML migliora la coerenza, ma richiede molto più di grande aiuto.

Se è mai stata scritta Guida dei cmdlet, esaminare le indicazioni seguenti.
Lo schema XML necessario per creare l'argomento della Guida cmdlet è descritto nella sezione seguente.
Per iniziare [la creazione del File della Guida dei Cmdlet](./how-to-create-the-cmdlet-help-file.md).
Questo argomento include una descrizione dei nodi XML principale.

## <a name="writing-guidelines-for-cmdlet-help"></a>Linee guida di scrittura per la Guida dei Cmdlet

### <a name="write-well"></a>Scriverne
Non sostituisce un argomento ben scritto.
Se non si dispone di un writer professionista, trovare un writer o un editor che consentono di.
Un'altra alternativa consiste nel copiare il testo della Guida in Microsoft Word e usare la grammatica e ortografia controlla per migliorare il proprio lavoro.

### <a name="write-simply"></a>Scrivere semplicemente
Usa semplici parole e frasi.
Evitare di terminologia.
Considerare che molti lettori siano dotati solo un dizionario di lingua straniera e l'argomento della Guida.

### <a name="write-consistently"></a>Scrivere in modo coerente
La Guida per cmdlet correlati dovrebbe essere simile (ad esempio, get-x e set-x).
Usare le descrizioni di standard per i parametri standard, ad esempio **Force** e **InputObject**.
(Copiarli dalla Guida per i cmdlet core.) Usare termini standard.
Ad esempio, usare "parametro", non "argomento" e utilizzare "cmdlet" non "command" o "command-let".

### <a name="start-the-synopsis-with-a-verb"></a>Avviare il riepilogo con un verbo
Il campo Riepilogo informa l'utente non quali cmdlet, che cos'è o come funziona.
Verbi di creare un'istruzione basato su attività che gli utenti vengono informati se questo cmdlet adatta alle proprie esigenze.
Usare verbi semplici, ad esempio "get", "Crea" e "Modifica".
Evitare di "set", che può essere vaga e fantasiosi parole come "Modifica".

### <a name="focus-on-objects"></a>Concentrarsi sugli oggetti
La maggior parte "get" cmdlet Visualizza un elemento, ma la cui funzione principale è ottenere un oggetto.
Il vostro aiuto, incentrata sull'oggetto, in modo che gli utenti comprendano che la visualizzazione predefinita è uno dei numerosi e che è possibile usare i metodi e proprietà dell'oggetto recuperato per loro in modi diversi.

### <a name="write-detailed-descriptions"></a>Scrivere una descrizione dettagliata
Brevemente elencare tutti gli elementi che può eseguire il cmdlet nella descrizione dettagliata.
Se la funzione principale consiste nel modificare una proprietà, ma il cmdlet può modificare tutte le proprietà, è elencato nella descrizione dettagliata.

### <a name="use-conventional-syntax"></a>Utilizzare la sintassi tradizionale
Usare il formato Backus-Naur standard che è comune per Windows e la Guida della riga di comando UNIX.

### <a name="use-microsoft-net-framework-types-for-parameter-values"></a>Usare tipi di Microsoft .NET Framework per i valori dei parametri
I segnaposto per i valori di parametro (nella sintassi e descrizioni dei parametri) mostrano i tipi di .NET Framework degli oggetti che accetta il parametro.
Il team di PowerShell ha sviluppato questa convenzione per aiutare gli utenti su .NET Framework.

### <a name="write-complete-parameter-descriptions"></a>Scrivere le descrizioni dei parametri completo
Le descrizioni dei parametri è necessario informare gli utenti delle due operazioni seguenti: il parametro non (relativo effetto) e ciò che è necessario digitare i valori dei parametri.

### <a name="write-practical-examples"></a>Scrittura di esempi pratici
Gli esempi devono illustrano come usare tutti i parametri, ma la cosa più importante è per mostrare come utilizzare il cmdlet di attività reali.
Iniziare con un semplice esempio e scrittura di esempi sempre più complessi.
Nell'esempio finale, Mostra come usare il cmdlet in una pipeline.

### <a name="use-the-notes-field"></a>Usare il campo Note
Usare il campo Note per spiegare i concetti che gli utenti devono conoscere il cmdlet.
È anche possibile usare note per consentire agli utenti di evitare errori comuni.
Evitare gli URL poiché viene modificato.
In alternativa, fornire le condizioni di utenti per la ricerca.

### <a name="test-your-help"></a>L'intervento dell'utente di test
Testare il supporto esattamente come è testare il codice.
Dispone gli amici e colleghi leggere il contenuto della Guida e forniscono commenti e suggerimenti.
È anche possibile richiedere commenti dai newsgroup.

## <a name="see-also"></a>Vedere anche

 [Come creare il File della Guida dei Cmdlet](./how-to-create-the-cmdlet-help-file.md)

 [Come aggiungere il nome di Cmdlet e il riepilogo per un argomento della Guida del Cmdlet](./how-to-add-the-cmdlet-name-and-synopsis-to-a-cmdlet-help-topic.md)

 [Come aggiungere la descrizione dettagliata per un argomento della Guida del Cmdlet](./how-to-add-a-cmdlet-description.md)

 [Come aggiungere la sintassi per un argomento della Guida del Cmdlet](./how-to-add-syntax-to-a-cmdlet-help-topic.md)

 [Come aggiungere parametri a un argomento della Guida del Cmdlet](./how-to-add-parameter-information.md)

 [Come aggiungere tipi di Input a un argomento della Guida Cmdlet](./how-to-add-input-types-to-a-cmdlet-help-topic.md)

 [Come aggiungere i valori restituiti per un argomento della Guida del Cmdlet](./how-to-add-return-values-to-a-cmdlet-help-topic.md)

 [Come aggiungere le note in un argomento della Guida del Cmdlet](./how-to-add-notes-to-a-cmdlet-help-topic.md)

 [Come aggiungere esempi per un argomento della Guida del Cmdlet](./how-to-add-examples-to-a-cmdlet-help-topic.md)

 [Come aggiungere collegamenti correlati a un argomento della Guida del Cmdlet](./how-to-add-related-links-to-a-cmdlet-help-topic.md)

 [Windows PowerShell SDK](../windows-powershell-reference.md)