---
title: I parametri delle risorse | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 460c43aa-f5c5-4a1a-a6f2-5e07db143de1
caps.latest.revision: 5
ms.openlocfilehash: 9752570e5c997ef4da56a08df14f39b77ba37a4a
ms.sourcegitcommit: ce46e5098786e19d521b4bf948ff62d2b90bc53e
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/02/2019
ms.locfileid: "57251201"
---
# <a name="resource-parameters"></a>Parametri delle risorse

La tabella seguente elenca i nomi consigliati e funzionalità per i parametri delle risorse. Per questi parametri, le risorse possono essere assembly che contiene la classe cmdlet o l'applicazione host che esegue il cmdlet.

|Parametro|Funzionalità|
|---|---|
|**Applicazione**<br>Tipo di dati: String|Implementare questo parametro in modo che l'utente può specificare un'applicazione.|
|**Assembly**<br>Tipo di dati: String|Implementare questo parametro in modo che l'utente può specificare un assembly.|
|**Attributo**<br>Tipo di dati: String|Implementare questo parametro in modo che l'utente può specificare un attributo.|
|**Classe**<br>Tipo di dati: String|Implementare questo parametro in modo che l'utente può specificare una classe di Microsoft .NET Framework.|
|**Cluster**<br>Tipo di dati: String|Implementare questo parametro in modo che l'utente può specificare un cluster.|
|**Impostazioni cultura**<br>Tipo di dati: String|Implementare questo parametro in modo che l'utente può specificare le impostazioni cultura in cui eseguire il cmdlet.|
|**Domain**<br>Tipo di dati: String|Implementare questo parametro in modo che l'utente può specificare il nome di dominio.|
|**Drive**<br>Tipo di dati: String|Implementare questo parametro in modo che l'utente può specificare un nome di unità.|
|**Event**<br>Tipo di dati: String|Implementare questo parametro in modo che l'utente può specificare un nome dell'evento.|
|**Interfaccia**<br>Tipo di dati: String|Implementare questo parametro in modo che l'utente può specificare un nome di interfaccia di rete.|
|**IpAddress**<br>Tipo di dati: String|Implementare questo parametro in modo che l'utente può specificare un indirizzo IP.|
|**Job**<br>Tipo di dati: String|Implementare questo parametro in modo che l'utente può specificare un processo.|
|**LiteralPath**<br>Tipo di dati: String|Implementare questo parametro in modo che l'utente può specificare il percorso di una risorsa quando non sono supportati i caratteri jolly. (Usare il **percorso** parametro quando i caratteri jolly sono supportati.)|
|**Mac**<br>Tipo di dati: String|Implementare questo parametro in modo che l'utente può specificare un indirizzo media access controller (MAC).|
|**ParentId**<br>Tipo di dati: String|Implementare questo parametro in modo che l'utente può specificare l'identificatore padre.|
|**Path**<br>Tipo di dati: String, String[]|Implementare questo parametro in modo che l'utente può indicare i percorsi a una risorsa quando i caratteri jolly sono supportati. (Usare il **LiteralPath** parametro quando non sono supportati caratteri jolly.) È consigliabile sviluppare questo parametro in modo che supporti la versione completa `provider:path` sintassi utilizzata dai provider. È inoltre consigliabile svilupparlo in modo che funziona con i provider di tanti possibili.|
|**Porta**<br>Tipo di dati: Numero intero, stringa|Implementare questo parametro in modo che l'utente può specificare un valore integer per la rete o un valore di stringa, ad esempio "biztalk" per altri tipi di porta.|
|**Stampante**<br>Tipo di dati: Numero intero, stringa|Implementare questo parametro in modo che l'utente può specificare la stampante per il cmdlet da usare.|
|**Dimensioni**<br>Tipo di dati: Int32|Implementare questo parametro in modo che l'utente può specificare una dimensione.|
|**TID**<br>Tipo di dati: String|Implementare questo parametro in modo che l'utente può specificare un identificatore di transazione (TID) per il cmdlet.|
|**Tipo**<br>Tipo di dati: String|Implementare questo parametro in modo che l'utente può specificare il tipo di risorsa su cui operare.|
|**URL**<br>Tipo di dati: String|Implementare questo parametro in modo che l'utente può specificare un Uniform Resource Locator (URL).|
|**User**<br>Tipo di dati: String|Implementare questo parametro in modo che l'utente può specificare il nome o il nome di un altro utente.|

## <a name="see-also"></a>Vedere anche

[Parametri del cmdlet](./cmdlet-parameters.md)

[Scrittura di un cmdlet di Windows PowerShell](./writing-a-windows-powershell-cmdlet.md)

[Windows PowerShell SDK](../windows-powershell-reference.md)
