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
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/15/2019
ms.locfileid: "72361070"
---
# <a name="writing-help-for-powershell-cmdlets"></a>Scrittura della Guida per i cmdlet di PowerShell

I cmdlet di PowerShell possono essere utili, ma a meno che gli argomenti della guida non spieghino chiaramente cosa fa il cmdlet e come usarlo, è possibile che il cmdlet non venga usato o, anche peggio, che possa frustrare gli utenti.
Il formato di file della guida del cmdlet basato su XML migliora la coerenza, ma è molto utile.

Se non è mai stata scritta la guida dei cmdlet, consultare le linee guida seguenti.
La XML Schema necessaria per creare l'argomento della guida del cmdlet è descritta nella sezione seguente.
Iniziare con [la creazione del file della guida del cmdlet](./how-to-create-the-cmdlet-help-file.md).
Questo argomento include una descrizione dei nodi XML di primo livello.

## <a name="writing-guidelines-for-cmdlet-help"></a>Guida alla scrittura della Guida per i cmdlet

### <a name="write-well"></a>Scrivi bene
Niente sostituisce un argomento ben scritto.
Se non si è un writer professionale, trovare un writer o un editor per aiutarti.
Un'altra alternativa consiste nel copiare il testo della Guida in Microsoft Word e usare i controlli di grammatica e ortografia per migliorare il lavoro.

### <a name="write-simply"></a>Scrivi semplicemente
Usare parole e frasi semplici.
Evitare il gergo.
Tenere presente che molti Reader sono dotati solo di un dizionario in lingua straniera e dell'argomento della guida.

### <a name="write-consistently"></a>Scrittura coerente
La guida per i cmdlet correlati dovrebbe essere simile, ad esempio Get-x e set-x.
Usare le descrizioni standard per i parametri standard, ad esempio **Force** e **InputObject**.
(Copiarli dalla guida per i cmdlet di base). Usare i termini standard.
Ad esempio, usare "Parameter", non "argument" e usare "cmdlet" non "Command" o "command-let".

### <a name="start-the-synopsis-with-a-verb"></a>Avviare la sintrama con un verbo
Il campo Sinossi informa l'utente dell'operazione eseguita dal cmdlet, non di come è o come funziona.
I verbi creano un'istruzione basata su attività che informa gli utenti se il cmdlet soddisfa i requisiti.
Usare verbi semplici come "Get", "create" e "Change".
Evitare "set", che può essere un testo vago e un'immaginazione come "Modify".

### <a name="focus-on-objects"></a>Concentrarsi sugli oggetti
Per la maggior parte dei cmdlet "Get" viene visualizzato un elemento, ma la funzione principale è quella di ottenere un oggetto.
Nella Guida concentrarsi sull'oggetto, in modo che gli utenti capiscano che la visualizzazione predefinita è una delle numerose e che possono usare i metodi e le proprietà dell'oggetto recuperato in modi diversi.

### <a name="write-detailed-descriptions"></a>Scrivi descrizioni dettagliate
Elencare brevemente tutti gli elementi che il cmdlet può eseguire nella descrizione dettagliata.
Se la funzione principale prevede la modifica di una proprietà, ma il cmdlet può modificare tutte le proprietà, elencarlo nella descrizione dettagliata.

### <a name="use-conventional-syntax"></a>USA sintassi convenzionale
Usare il formato Backus-Naur standard comune per la guida della riga di comando di Windows e UNIX.

### <a name="use-microsoft-net-framework-types-for-parameter-values"></a>Usare Microsoft .NET tipi di Framework per i valori dei parametri
I segnaposto per i valori dei parametri (nella sintassi e nelle descrizioni dei parametri) mostrano i tipi di .NET Framework degli oggetti accettati dal parametro.
Il team di PowerShell ha sviluppato questa convenzione per aiutare gli utenti a insegnare i .NET Framework.

### <a name="write-complete-parameter-descriptions"></a>Scrivi descrizioni dei parametri completi
Le descrizioni dei parametri devono informare gli utenti di due cose: cosa fa il parametro (effetto) e cosa devono digitare per i valori dei parametri.

### <a name="write-practical-examples"></a>Scrivi esempi pratici
Gli esempi illustrano come usare tutti i parametri, ma la cosa più importante è illustrare come usare il cmdlet in attività reali.
Inizia con un semplice esempio e Scrivi esempi sempre più complessi.
Nell'esempio finale, Mostra come usare il cmdlet in una pipeline.

### <a name="use-the-notes-field"></a>Usare il campo note
Usare il campo note per spiegare i concetti necessari agli utenti per comprendere il cmdlet.
È inoltre possibile utilizzare note per aiutare gli utenti a evitare errori comuni.
Evitare gli URL Man mano che cambiano.
Fornire invece i termini degli utenti per la ricerca.

### <a name="test-your-help"></a>Testare la guida
Testare la guida esattamente come si esegue il test del codice.
Chiedere a amici e colleghi di leggere il contenuto della guida e fornire commenti e suggerimenti.
È anche possibile richiedere commenti e suggerimenti da newsgroup.

## <a name="see-also"></a>Vedere anche

 [Come creare il file della guida del cmdlet](./how-to-create-the-cmdlet-help-file.md)

 [Come aggiungere il nome del cmdlet e la sintrama a un argomento della guida del cmdlet](./how-to-add-the-cmdlet-name-and-synopsis-to-a-cmdlet-help-topic.md)

 [Come aggiungere la descrizione dettagliata a un argomento della guida del cmdlet](./how-to-add-a-cmdlet-description.md)

 [Come aggiungere la sintassi a un argomento della guida del cmdlet](./how-to-add-syntax-to-a-cmdlet-help-topic.md)

 [Come aggiungere parametri a un argomento della guida del cmdlet](./how-to-add-parameter-information.md)

 [Come aggiungere tipi di input a un argomento della guida del cmdlet](./how-to-add-input-types-to-a-cmdlet-help-topic.md)

 [Come aggiungere valori restituiti a un argomento della guida del cmdlet](./how-to-add-return-values-to-a-cmdlet-help-topic.md)

 [Come aggiungere note a un argomento della guida del cmdlet](./how-to-add-notes-to-a-cmdlet-help-topic.md)

 [Come aggiungere esempi a un argomento della guida del cmdlet](./how-to-add-examples-to-a-cmdlet-help-topic.md)

 [Come aggiungere collegamenti correlati a un argomento della guida del cmdlet](./how-to-add-related-links-to-a-cmdlet-help-topic.md)

 [Windows PowerShell SDK](../windows-powershell-reference.md)