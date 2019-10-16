---
title: Parametri della proprietà | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d17e0d66-42ea-4e4c-a85b-3ca09b146492
caps.latest.revision: 6
ms.openlocfilehash: cc0742b86a7a36e5712707c077fd1952691f3f4b
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/15/2019
ms.locfileid: "72369580"
---
# <a name="property-parameters"></a>Parametri delle proprietà

Nella tabella seguente sono elencati i nomi e le funzionalità consigliati per i parametri delle proprietà.

|Parametro|Funzionalità|
|---|---|
|**Conteggio**<br>Tipo di dati: Int32|Implementare questo parametro in modo che l'utente possa specificare il numero di oggetti da elaborare.|
|**Descrizione**<br>Tipo di dati: String|Implementare questo parametro in modo che l'utente possa specificare una descrizione per una risorsa.|
|**Da**<br>Tipo di dati: String|Implementare questo parametro in modo che l'utente possa specificare l'oggetto di riferimento da cui ottenere le informazioni.|
|**ID**<br>Tipo di dati: dipendente dalla risorsa|Implementare questo parametro in modo che l'utente possa specificare l'identificatore di una risorsa.|
|**Input**<br>Tipo di dati: String|Implementare questo parametro in modo che l'utente possa specificare la specifica del file di input.|
|**Posizione**<br>Tipo di dati: String|Implementare questo parametro in modo che l'utente possa specificare il percorso della risorsa.|
|**LogName**<br>Tipo di dati: String|Implementare questo parametro in modo che l'utente possa specificare il nome del file di log da elaborare o utilizzare.|
|**Nome**<br>Tipo di dati: String|Implementare questo parametro in modo che l'utente possa specificare il nome della risorsa.|
|**Output**<br>Tipo di dati: String|Implementare questo parametro in modo che l'utente possa specificare il file di output.|
|**Proprietario**<br>Tipo di dati: String|Implementare questo parametro in modo che l'utente possa specificare il nome del proprietario della risorsa.|
|**Proprietà**<br>Tipo di dati: String|Implementare questo parametro in modo che l'utente possa specificare il nome o i nomi delle proprietà da utilizzare.|
|**Motivo**<br>Tipo di dati: String|Implementare questo parametro in modo che l'utente possa specificare il motivo per cui viene richiamato questo cmdlet.|
|**Regex**<br>Tipo di dati: SwitchParameter|Implementare questo parametro in modo che le espressioni regolari vengano utilizzate quando si specifica il parametro. Quando si specifica questo parametro, i caratteri jolly non vengono risolti.|
|**Velocità**<br>Tipo di dati: Int32|Implementare questo parametro in modo che l'utente possa specificare la velocità in baud. L'utente imposta questo parametro sulla velocità della risorsa.|
|**Stato**<br>Tipo di dati: matrice di parole chiave|Implementare questo parametro in modo che l'utente possa specificare i nomi degli Stati, ad esempio KEYDOWN.|
|**Valore**<br>Tipo di dati: Object|Implementare questo parametro in modo che l'utente possa specificare un valore da fornire al cmdlet.|
|**Versione**<br>Tipo di dati: String|Implementare questo parametro in modo che l'utente possa specificare la versione della proprietà.|

## <a name="see-also"></a>Vedere anche

[Parametri dei cmdlet](./cmdlet-parameters.md)

[Scrittura di un cmdlet di Windows PowerShell](./writing-a-windows-powershell-cmdlet.md)

[Windows PowerShell SDK](../windows-powershell-reference.md)
