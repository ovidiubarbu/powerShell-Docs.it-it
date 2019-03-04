---
title: I parametri di proprietà | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d17e0d66-42ea-4e4c-a85b-3ca09b146492
caps.latest.revision: 6
ms.openlocfilehash: cc0742b86a7a36e5712707c077fd1952691f3f4b
ms.sourcegitcommit: ce46e5098786e19d521b4bf948ff62d2b90bc53e
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/02/2019
ms.locfileid: "57251422"
---
# <a name="property-parameters"></a>Parametri delle proprietà

La tabella seguente elenca i nomi consigliati e funzionalità per i parametri di proprietà.

|Parametro|Funzionalità|
|---|---|
|**conteggio**<br>Tipo di dati: Int32|Implementare questo parametro in modo che l'utente può specificare il numero di oggetti da elaborare.|
|**Descrizione**<br>Tipo di dati: String|Implementare questo parametro in modo che l'utente può specificare una descrizione per una risorsa.|
|**Da**<br>Tipo di dati: String|Implementare questo parametro in modo che l'utente può specificare l'oggetto di riferimento per ottenere informazioni.|
|**Id**<br>Tipo di dati: Risorse dipendenti|Implementare questo parametro in modo che l'utente può specificare l'identificatore di una risorsa.|
|**Input**<br>Tipo di dati: String|Implementare questo parametro in modo che l'utente può specificare la specifica di file di input.|
|**Posizione**<br>Tipo di dati: String|Implementare questo parametro in modo che l'utente può specificare il percorso della risorsa.|
|**LogName**<br>Tipo di dati: String|Implementare questo parametro in modo che l'utente può specificare il nome del file di log da elaborare o usare.|
|**Name**<br>Tipo di dati: String|Implementare questo parametro in modo che l'utente può specificare il nome della risorsa.|
|**Output**<br>Tipo di dati: String|Implementare questo parametro in modo che l'utente può specificare il file di output.|
|**Owner**<br>Tipo di dati: String|Implementare questo parametro in modo che l'utente può specificare il nome del proprietario della risorsa.|
|**Proprietà**<br>Tipo di dati: String|Implementare questo parametro in modo che l'utente può specificare il nome o i nomi delle proprietà da utilizzare.|
|**motivo**<br>Tipo di dati: String|Implementare questo parametro in modo che l'utente può specificare il motivo per cui viene chiamato questo cmdlet.|
|**Regex**<br>Tipo di dati: SwitchParameter|Implementare questo parametro in modo che le espressioni regolari vengono utilizzate quando viene specificato il parametro. Quando questo parametro è specificato, i caratteri jolly non vengono risolti.|
|**Velocità**<br>Tipo di dati: Int32|Implementare questo parametro in modo che l'utente può specificare la velocità in baud. L'utente imposta questo parametro per la velocità della risorsa.|
|**Stato**<br>Tipo di dati: Array (parola chiave)|Implementare questo parametro in modo che l'utente può specificare i nomi degli Stati, ad esempio KEYDOWN.|
|**Valore**<br>Tipo di dati: Oggetto|Implementare questo parametro in modo che l'utente può specificare un valore da fornire al cmdlet.|
|**Versione**<br>Tipo di dati: String|Implementare questo parametro in modo che l'utente può specificare la versione della proprietà.|

## <a name="see-also"></a>Vedere anche

[Parametri del cmdlet](./cmdlet-parameters.md)

[Scrittura di un cmdlet di Windows PowerShell](./writing-a-windows-powershell-cmdlet.md)

[Windows PowerShell SDK](../windows-powershell-reference.md)
