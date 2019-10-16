---
title: Parametri delle risorse | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 460c43aa-f5c5-4a1a-a6f2-5e07db143de1
caps.latest.revision: 5
ms.openlocfilehash: 9752570e5c997ef4da56a08df14f39b77ba37a4a
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/15/2019
ms.locfileid: "72369510"
---
# <a name="resource-parameters"></a>Parametri delle risorse

La tabella seguente elenca i nomi e le funzionalità consigliati per i parametri delle risorse. Per questi parametri, le risorse possono essere l'assembly che contiene la classe di cmdlet o l'applicazione host che esegue il cmdlet.

|Parametro|Funzionalità|
|---|---|
|**Applicazione**<br>Tipo di dati: String|Implementare questo parametro in modo che l'utente possa specificare un'applicazione.|
|**Assembly**<br>Tipo di dati: String|Implementare questo parametro in modo che l'utente possa specificare un assembly.|
|**Attributo**<br>Tipo di dati: String|Implementare questo parametro in modo che l'utente possa specificare un attributo.|
|**Classe**<br>Tipo di dati: String|Implementare questo parametro in modo che l'utente possa specificare una classe Microsoft .NET Framework.|
|**Cluster**<br>Tipo di dati: String|Implementare questo parametro in modo che l'utente possa specificare un cluster.|
|**Cultura**<br>Tipo di dati: String|Implementare questo parametro in modo che l'utente possa specificare le impostazioni cultura in cui eseguire il cmdlet.|
|**Dominio**<br>Tipo di dati: String|Implementare questo parametro in modo che l'utente possa specificare il nome di dominio.|
|**Unità**<br>Tipo di dati: String|Implementare questo parametro in modo che l'utente possa specificare un nome di unità.|
|**Evento**<br>Tipo di dati: String|Implementare questo parametro in modo che l'utente possa specificare un nome di evento.|
|**Interfaccia**<br>Tipo di dati: String|Implementare questo parametro in modo che l'utente possa specificare un nome di interfaccia di rete.|
|**IpAddress**<br>Tipo di dati: String|Implementare questo parametro in modo che l'utente possa specificare un indirizzo IP.|
|**Processo**<br>Tipo di dati: String|Implementare questo parametro in modo che l'utente possa specificare un processo.|
|**LiteralPath**<br>Tipo di dati: String|Implementare questo parametro in modo che l'utente possa specificare il percorso di una risorsa quando i caratteri jolly non sono supportati. Usare il parametro **path** quando sono supportati i caratteri jolly.|
|**Mac**<br>Tipo di dati: String|Implementare questo parametro in modo che l'utente possa specificare un indirizzo MAC (Media Access Controller).|
|**ParentId**<br>Tipo di dati: String|Implementare questo parametro in modo che l'utente possa specificare l'identificatore padre.|
|**Percorso**<br>Tipo di dati: String, String []|Implementare questo parametro in modo che l'utente possa indicare i percorsi di una risorsa quando sono supportati i caratteri jolly. Usare il parametro **LiteralPath** quando i caratteri jolly non sono supportati. Si consiglia di sviluppare questo parametro in modo che supporti la sintassi `provider:path` completa utilizzata dai provider. Si consiglia inoltre di svilupparlo in modo che funzioni con il maggior numero possibile di provider.|
|**Porta**<br>Tipo di dati: Integer, stringa|Implementare questo parametro in modo che l'utente possa specificare un valore intero per la rete o un valore stringa quale "BizTalk" per altri tipi di porta.|
|**Stampante**<br>Tipo di dati: Integer, stringa|Implementare questo parametro in modo che l'utente possa specificare la stampante per il cmdlet da usare.|
|**Dimensioni**<br>Tipo di dati: Int32|Implementare questo parametro in modo che l'utente possa specificare una dimensione.|
|**TID**<br>Tipo di dati: String|Implementare questo parametro in modo che l'utente possa specificare un identificatore di transazione (TID) per il cmdlet.|
|**Tipo**<br>Tipo di dati: String|Implementare questo parametro in modo che l'utente possa specificare il tipo di risorsa su cui operare.|
|**URL**<br>Tipo di dati: String|Implementare questo parametro in modo che l'utente possa specificare un Uniform Resource Locator (URL).|
|**User**<br>Tipo di dati: String|Implementare questo parametro in modo che l'utente possa specificare il nome o il nome di un altro utente.|

## <a name="see-also"></a>Vedere anche

[Parametri dei cmdlet](./cmdlet-parameters.md)

[Scrittura di un cmdlet di Windows PowerShell](./writing-a-windows-powershell-cmdlet.md)

[Windows PowerShell SDK](../windows-powershell-reference.md)
