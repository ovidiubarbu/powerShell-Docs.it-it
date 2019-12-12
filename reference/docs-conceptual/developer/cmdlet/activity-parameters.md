---
title: Parametri dell'attività | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 6e4e0cf6-19e0-44b8-8b40-d6f6075276cf
caps.latest.revision: 5
ms.openlocfilehash: 489d8bcdabe904d6a3d2bc6cdb9d7e23d09cbef2
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/05/2019
ms.locfileid: "72364640"
---
# <a name="activity-parameters"></a>Parametri dell'attività

Nella tabella seguente sono elencati i nomi e le funzionalità consigliati per i parametri di attività.

|Parametro|Funzionalità|
|---|---|
|**Accoda**<br>Tipo di dati: SwitchParameter|Implementare questo parametro in modo che l'utente possa aggiungere il contenuto alla fine di una risorsa quando viene specificato il parametro.|
|**CaseSensitive**<br>Tipo di dati: SwitchParameter|Implementare questo parametro in modo che l'utente possa richiedere la distinzione tra maiuscole e minuscole quando viene specificato il parametro.|
|**Command**<br>Tipo di dati: stringa|Implementare questo parametro in modo che l'utente possa specificare una stringa di comando da eseguire.|
|**CompatibleVersion**<br>Tipo di dati: oggetto System. Version|Implementare questo parametro in modo che l'utente possa specificare la semantica con cui il cmdlet deve essere compatibile per la compatibilità con le versioni precedenti.|
|**Compressione**<br>Tipo di dati: SwitchParameter|Implementare questo parametro in modo che venga utilizzata la compressione dei dati quando si specifica il parametro.|
|**Compressione**<br>Tipo di dati: parola chiave|Implementare questo parametro in modo che l'utente possa specificare l'algoritmo da utilizzare per la compressione dei dati.|
|**Continuo**<br>Tipo di dati: SwitchParameter|Implementare questo parametro in modo che i dati vengano elaborati fino a quando l'utente non termina il cmdlet quando viene specificato il parametro. Se il parametro non è specificato, il cmdlet elabora una quantità predefinita di dati e quindi termina l'operazione.|
|**Create**<br>Tipo di dati: SwitchParameter|Implementare questo parametro per indicare che una risorsa viene creata se non ne è già presente una quando si specifica il parametro.|
|**Elimina**<br>Tipo di dati: SwitchParameter|Implementare questo parametro in modo che le risorse vengano eliminate quando il cmdlet ha completato l'operazione quando viene specificato il parametro.|
|**Scarico**<br>Tipo di dati: SwitchParameter|Implementare questo parametro per indicare che gli elementi di lavoro in attesa vengono elaborati prima che il cmdlet elabori i nuovi dati quando viene specificato il parametro. Se il parametro non è specificato, gli elementi di lavoro vengono elaborati immediatamente.|
|**Erase**<br>Tipo di dati: Int32|Implementare questo parametro in modo che l'utente possa specificare il numero di volte in cui una risorsa viene cancellata prima di essere eliminata.|
|**ErrorLevel**<br>Tipo di dati: Int32|Implementare questo parametro in modo che l'utente possa specificare il livello di errori da segnalare.|
|**Exclude** (Escludi)<br>Tipo di dati: String []|Implementare questo parametro in modo che l'utente possa escludere qualcosa da un'attività. Per ulteriori informazioni sull'utilizzo dei filtri di input, vedere [parametri di filtro di input](input-filter-parameters.md).|
|**Filtra**<br>Tipo di dati: parola chiave|Implementare questo parametro in modo che l'utente possa specificare un filtro che seleziona le risorse su cui eseguire l'azione del cmdlet. Per ulteriori informazioni sull'utilizzo dei filtri di input, vedere [parametri di filtro di input](./input-filter-parameters.md).|
|**Seguire**<br>Tipo di dati: SwitchParameter|Implementare questo parametro in modo che lo stato di avanzamento venga rilevato quando si specifica il parametro.|
|**Forzare**<br>Tipo di dati: SwitchParameter|Implementare questo parametro per indicare che l'utente può eseguire un'azione anche se vengono rilevate restrizioni quando si specifica il parametro. Il parametro non consente la compromissione della sicurezza. Questo parametro, ad esempio, consente a un utente di sovrascrivere un file di sola lettura.|
|**Include** (Includi)<br>Tipo di dati: String []|Implementare questo parametro in modo che l'utente possa includere elementi in un'attività. Per ulteriori informazioni sull'utilizzo dei filtri di input, vedere [parametri di filtro di input](input-filter-parameters.md).|
|**Incrementale**<br>Tipo di dati: SwitchParameter|Implementare questo parametro per indicare che l'elaborazione viene eseguita in modo incrementale quando viene specificato il parametro. Questo parametro, ad esempio, consente a un utente di eseguire backup incrementali che eseguono il backup dei file solo dopo l'ultimo backup.|
|**InputObject**<br>Tipo di dati: Object|Implementare questo parametro quando il cmdlet accetta input da altri cmdlet. Quando si definisce un parametro **InputObject** , specificare sempre la parola chiave **ValueFromPipeline** quando si dichiara l'attributo **Parameter** . Per ulteriori informazioni sull'utilizzo dei filtri di input, vedere [parametri di filtro di input](./input-filter-parameters.md).|
|**Insert**<br>Tipo di dati: SwitchParameter|Implementare questo parametro in modo che il cmdlet inserisca un elemento quando viene specificato il parametro.|
|**Interactive**<br>Tipo di dati: SwitchParameter|Implementare questo parametro in modo che il cmdlet funzioni in modo interattivo con l'utente quando viene specificato il parametro.|
|**Intervallo**<br>Tipo di dati: HashTable|Implementare questo parametro in modo che l'utente possa specificare una tabella hash di parole chiave che contiene i valori. Nell'esempio seguente vengono illustrati i valori di esempio per il parametro **Interval** : `-interval @{ResumeScan=15; Retry=3}`.|
|**Log**<br>Tipo di dati: SwitchParameter|Implementare questo parametro per controllare le azioni del cmdlet quando viene specificato il parametro.|
|**NoClobber**<br>Tipo di dati: SwitchParameter|Implementare questo parametro in modo che la risorsa non verrà sovrascritta quando viene specificato il parametro. Questo parametro è in genere applicabile ai cmdlet che creano nuovi oggetti in modo che possano impedire la sovrascrittura degli oggetti esistenti con lo stesso nome.|
|**Comunica**<br>Tipo di dati: SwitchParameter|Implementare questo parametro in modo che l'utente riceverà una notifica che indica che l'attività è stata completata quando viene specificato il parametro.|
|**NotifyAddress**<br>Tipo di dati: indirizzo di posta elettronica|Implementare questo parametro in modo che l'utente possa specificare l'indirizzo di posta elettronica da usare per inviare una notifica quando viene specificato il parametro **Notify** .|
|**Overwrite**<br>Tipo di dati: SwitchParameter|Implementare questo parametro in modo che il cmdlet sovrascriva tutti i dati esistenti quando viene specificato il parametro.|
|**Messaggio di richiesta**<br>Tipo di dati: stringa|Implementare questo parametro in modo che l'utente possa specificare una richiesta per il cmdlet.|
|**Quiet**<br>Tipo di dati: SwitchParameter|Implementare questo parametro in modo che il cmdlet elimini il feedback dell'utente durante le azioni quando viene specificato il parametro.|
|**Recurse**<br>Tipo di dati: SwitchParameter|Implementare questo parametro in modo che il cmdlet esegua in modo ricorsivo le proprie azioni sulle risorse quando viene specificato il parametro.|
|**Repair**<br>Tipo di dati: SwitchParameter|Implementare questo parametro in modo che il cmdlet tenti di correggere qualcosa da uno stato di interruzione quando viene specificato il parametro.|
|**RepairString**<br>Tipo di dati: stringa|Implementare questo parametro in modo che l'utente possa specificare una stringa da usare quando viene specificato il parametro **Repair** .|
|**Nuovo tentativo**<br>Tipo di dati: Int32|Implementare questo parametro in modo che l'utente possa specificare il numero di volte in cui il cmdlet tenterà un'azione.|
|**Selezione**<br>Tipo di dati: matrice di parole chiave|Implementare questo parametro in modo che l'utente possa specificare una matrice dei tipi di elementi.|
|**Stream**<br>Tipo di dati: SwitchParameter|Implementare questo parametro in modo che l'utente possa trasmettere più oggetti di output attraverso la pipeline quando viene specificato il parametro.|
|**Strict**<br>Tipo di dati: SwitchParameter|Implementare questo parametro in modo che tutti gli errori vengano gestiti come errori di terminazione quando si specifica il parametro.|
|**TempLocation**<br>Tipo di dati: stringa|Implementare questo parametro in modo che l'utente possa specificare il percorso dei dati temporanei utilizzati durante l'operazione del cmdlet.|
|**Timeout**<br>Tipo di dati: Int32|Implementare questo parametro in modo che l'utente possa specificare l'intervallo di timeout (in millisecondi).|
|**Troncare**<br>Tipo di dati: SwitchParameter|Implementare questo parametro in modo che il cmdlet tronca le proprie azioni quando viene specificato il parametro. Se il parametro non è specificato, il cmdlet esegue un'altra azione.|
|**Verificare**<br>Tipo di dati: SwitchParameter|Implementare questo parametro in modo che il cmdlet proverà a determinare se si è verificata un'azione quando viene specificato il parametro.|
|**Wait**<br>Tipo di dati: SwitchParameter|Implementare questo parametro in modo che il cmdlet attenda l'input dell'utente prima di continuare quando viene specificato il parametro.
|**Tempo attesa**<br>Tipo di dati: Int32|Implementare questo parametro in modo che l'utente possa specificare la durata (in secondi) in cui il cmdlet attenderà l'input dell'utente quando viene specificato il parametro **wait** .|

## <a name="see-also"></a>Vedere anche

[Parametri dei cmdlet](./cmdlet-parameters.md)

[Scrittura di un cmdlet di Windows PowerShell](./writing-a-windows-powershell-cmdlet.md)

[Windows PowerShell SDK](../windows-powershell-reference.md)
