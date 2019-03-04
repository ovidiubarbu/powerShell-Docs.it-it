---
title: Parametri di attività | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 6e4e0cf6-19e0-44b8-8b40-d6f6075276cf
caps.latest.revision: 5
ms.openlocfilehash: 489d8bcdabe904d6a3d2bc6cdb9d7e23d09cbef2
ms.sourcegitcommit: ce46e5098786e19d521b4bf948ff62d2b90bc53e
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/02/2019
ms.locfileid: "57251218"
---
# <a name="activity-parameters"></a>Parametri dell'attività

La tabella seguente elenca i nomi consigliati e funzionalità per i parametri di attività.

|Parametro|Funzionalità|
|---|---|
|**Append**<br>Tipo di dati: SwitchParameter|Implementare questo parametro in modo che l'utente può aggiungere contenuto alla fine di una risorsa quando viene specificato il parametro.|
|**CaseSensitive**<br>Tipo di dati: SwitchParameter|Implementare questo parametro in modo che l'utente può richiedere distinzione maiuscole/minuscole quando viene specificato il parametro.|
|**Comando**<br>Tipo di dati: String|Implementare questo parametro in modo che l'utente può specificare una stringa di comando da eseguire.|
|**CompatibleVersion**<br>Tipo di dati: Oggetto Version|Implementare questo parametro in modo che l'utente può specificare la semantica che il cmdlet deve essere compatibile con la compatibilità con le versioni precedenti.|
|**Comprimi**<br>Tipo di dati: SwitchParameter|Implementare questo parametro in modo che la compressione dei dati viene usato quando viene specificato il parametro.|
|**Comprimi**<br>Tipo di dati: Parola chiave|Implementare questo parametro in modo che l'utente può specificare l'algoritmo da utilizzare per la compressione dei dati.|
|**continua**<br>Tipo di dati: SwitchParameter|Implementare questo parametro in modo che i dati vengono elaborati fino a quando l'utente termina il cmdlet quando viene specificato il parametro. Se il parametro viene omesso, il cmdlet elabora una quantità di dati predefinita e quindi termina l'operazione.|
|**creare**<br>Tipo di dati: SwitchParameter|Implementare questo parametro per indicare che viene creata una risorsa se non è già esistente quando viene specificato il parametro.|
|**Delete**<br>Tipo di dati: SwitchParameter|Implementare questo parametro in modo che le risorse vengono eliminate quando il cmdlet è stata completata l'operazione quando viene specificato il parametro.|
|**Svuotamento**<br>Tipo di dati: SwitchParameter|Implementare questo parametro per indicare che gli elementi di lavoro in sospeso vengono elaborati prima che il cmdlet elabora i nuovi dati quando viene specificato il parametro. Se il parametro viene omesso, gli elementi di lavoro vengono elaborati immediatamente.|
|**cancellazione**<br>Tipo di dati: Int32|Implementare questo parametro in modo che l'utente può specificare il numero di volte in cui che una risorsa viene cancellata prima che venga eliminato.|
|**ErrorLevel**<br>Tipo di dati: Int32|Implementare questo parametro in modo che l'utente può specificare il livello di errori da segnalare.|
|**Exclude**<br>Tipo di dati: String[]|Implementare questo parametro in modo che l'utente può escludere un elemento da un'attività. Per altre informazioni su come usare i filtri di input, vedere [Input ai parametri di filtro](input-filter-parameters.md).|
|**Filtro**<br>Tipo di dati: Parola chiave|Implementare questo parametro in modo che l'utente può specificare un filtro per selezionare le risorse in base al quale eseguire l'azione di cmdlet. Per altre informazioni su come usare i filtri di input, vedere [Input ai parametri di filtro](./input-filter-parameters.md).|
|**Follow**<br>Tipo di dati: SwitchParameter|Implementare questo parametro in modo che lo stato di avanzamento verrà rilevata quando viene specificato il parametro.|
|**Force**<br>Tipo di dati: SwitchParameter|Implementare questo parametro per indicare che l'utente può eseguire un'azione anche se le restrizioni vengono rilevate quando viene specificato il parametro. Il parametro non consente la sicurezza sia compromessa. Ad esempio, questo parametro consente di sovrascrivere un file di sola lettura.|
|**Include**<br>Tipo di dati: String[]|Implementare questo parametro in modo che l'utente può includere un elemento in un'attività. Per altre informazioni su come usare i filtri di input, vedere [Input ai parametri di filtro](input-filter-parameters.md).|
|**Incrementale**<br>Tipo di dati: SwitchParameter|Implementare questo parametro per indicare che l'elaborazione viene eseguita in modo incrementale quando viene specificato il parametro. Ad esempio, questo parametro consente un utente di eseguire i backup incrementali che eseguire il backup di file solo dopo l'ultimo backup.|
|**InputObject**<br>Tipo di dati: Oggetto|Implementare questo parametro quando il cmdlet accetta input da altri cmdlet. Quando si definisce un **InputObject** parametro, specificare sempre il **ValueFromPipeline** parola chiave quando si dichiara il **parametro** attributo. Per altre informazioni sull'utilizzo dei filtri di input, vedere [Input ai parametri di filtro](./input-filter-parameters.md).|
|**Insert**<br>Tipo di dati: SwitchParameter|Implementare questo parametro in modo che il cmdlet viene inserito un elemento quando viene specificato il parametro.|
|**Interactive**<br>Tipo di dati: SwitchParameter|Implementare questo parametro in modo che il cmdlet funziona in modo interattivo con l'utente quando viene specificato il parametro.|
|**Interval**<br>Tipo di dati: HashTable|Implementare questo parametro in modo che l'utente può specificare una tabella hash delle parole chiave che contiene i valori. L'esempio seguente mostra i valori di esempio per la **Interval** parametro: `-interval @{ResumeScan=15; Retry=3}`.|
|**Log**<br>Tipo di dati: SwitchParameter|Implementare questo controllo del parametro del cmdlet le azioni quando viene specificato il parametro.|
|**NoClobber**<br>Tipo di dati: SwitchParameter|Implementare questo parametro in modo che la risorsa non verrà sovrascritto quando viene specificato il parametro. Questo parametro si applica a livello generale per i cmdlet che creano nuovi oggetti in modo che può essere evitati sovrascrivano gli oggetti esistenti con lo stesso nome.|
|**Inviare una notifica**<br>Tipo di dati: SwitchParameter|Implementare questo parametro in modo che l'utente riceverà una notifica che l'attività è completata quando viene specificato il parametro.|
|**NotifyAddress**<br>Tipo di dati: Indirizzo di posta elettronica|Implementare questo parametro in modo che l'utente può specificare l'indirizzo di posta elettronica da usare per inviare una notifica quando la **Notify** parametro è specificato.|
|**Overwrite**<br>Tipo di dati: SwitchParameter|Implementare questo parametro in modo che il cmdlet sovrascrive eventuali dati esistenti quando viene specificato il parametro.|
|**Prompt**<br>Tipo di dati: String|Implementare questo parametro in modo che l'utente può specificare una richiesta per il cmdlet.|
|**Quiet**<br>Tipo di dati: SwitchParameter|Implementare questo parametro in modo che il cmdlet Elimina commenti degli utenti durante le azioni quando viene specificato il parametro.|
|**Recurse**<br>Tipo di dati: SwitchParameter|Implementare questo parametro in modo che quando viene specificato il parametro, in modo ricorsivo il cmdlet esegue le azioni sulle risorse.|
|**Repair**<br>Tipo di dati: SwitchParameter|Implementare questo parametro in modo che il cmdlet tenterà di correggere un elemento da uno stato danneggiato quando viene specificato il parametro.|
|**RepairString**<br>Tipo di dati: String|Implementare questo parametro in modo che l'utente può specificare una stringa da utilizzare quando le **Repair** parametro è specificato.|
|**Ripetizione dei tentativi**<br>Tipo di dati: Int32|Implementare questo parametro in modo che l'utente può specificare il numero di volte in cui che il cmdlet tenterà di un'azione.|
|**Selezionare**<br>Tipo di dati: Array (parola chiave)|Implementare questo parametro in modo che l'utente può specificare una matrice dei tipi di elementi.|
|**Stream**<br>Tipo di dati: SwitchParameter|Implementare questo parametro in modo che l'utente può eseguire il flusso più oggetti di output tramite la pipeline quando viene specificato il parametro.|
|**Strict**<br>Tipo di dati: SwitchParameter|Implementare questo parametro in modo che tutti gli errori vengono gestiti come errori terminazione quando viene specificato il parametro.|
|**TempLocation**<br>Tipo di dati: String|Implementare questo parametro in modo che l'utente può specificare il percorso dei dati temporanei che viene usati durante l'operazione del cmdlet.|
|**Timeout**<br>Tipo di dati: Int32|Implementare questo parametro in modo che l'utente può specificare l'intervallo di timeout (in millisecondi).|
|**TRUNCATE**<br>Tipo di dati: SwitchParameter|Implementare questo parametro in modo che il cmdlet verrà troncate le proprie azioni quando viene specificato il parametro. Se il parametro viene omesso, il cmdlet esegue un'altra azione.|
|**Verify**<br>Tipo di dati: SwitchParameter|Implementare questo parametro in modo che il cmdlet eseguirà il test per determinare se si è verificata un'azione quando viene specificato il parametro.|
|**Attendere**<br>Tipo di dati: SwitchParameter|Implementare questo parametro in modo che il cmdlet attenderà per l'input utente prima di continuare quando viene specificato il parametro.
|**WaitTime**<br>Tipo di dati: Int32|Implementare questo parametro in modo che l'utente può specificare la durata (in secondi) che il cmdlet attenderà per l'utente di input quando le **attesa** parametro è specificato.|

## <a name="see-also"></a>Vedere anche

[Parametri del cmdlet](./cmdlet-parameters.md)

[Scrittura di un cmdlet di Windows PowerShell](./writing-a-windows-powershell-cmdlet.md)

[Windows PowerShell SDK](../windows-powershell-reference.md)
