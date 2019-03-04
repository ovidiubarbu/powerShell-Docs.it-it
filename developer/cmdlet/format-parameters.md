---
title: Formattare i parametri | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 10e025c5-9aa6-45a5-b851-23d14db1f4cc
caps.latest.revision: 7
ms.openlocfilehash: 0bd3888d81aa6d1dde26c0066f7bca9dac8a8bca
ms.sourcegitcommit: ce46e5098786e19d521b4bf948ff62d2b90bc53e
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/02/2019
ms.locfileid: "57251184"
---
# <a name="format-parameters"></a>Parametri di formattazione

La tabella seguente elenca i nomi consigliati e funzionalità per i parametri che vengono usate per formattare o per generare i dati.

|Parametro|Funzionalità|
|---|---|
|**come**<br>Tipo di dati: Parola chiave|Implementare questo parametro per specificare il formato di output del cmdlet. I valori possibili, ad esempio, potrebbero essere testo o uno Script.|
|**file binario**<br>Tipo di dati: SwitchParameter|Implementare questo parametro per indicare che il cmdlet gestisce i valori binari.|
|**Codifica**<br>Tipo di dati: Parola chiave|Implementare questo parametro per specificare il tipo di codifica supportato. I valori possibili, ad esempio, potrebbero essere ASCII, UTF8, Unicode, UTF7, BigEndianUnicode, Byte e stringa.|
|**NewLine**<br>Tipo di dati: SwitchParameter|Implementare questo parametro in modo che i caratteri di nuova riga sono supportati quando il parametro è specificato.|
|**ShortName**<br>Tipo di dati: SwitchParameter|Implementare questo parametro in modo che i nomi brevi sono supportati quando il parametro è specificato.|
|**Width**<br>Tipo di dati: Int32|Implementare questo parametro in modo che l'utente può specificare la larghezza della periferica di output.|
|**Eseguire il wrapping**<br>Tipo di dati: SwitchParameter|Implementare questo parametro in modo che la disposizione del testo è supportato quando viene specificato il parametro.|
## <a name="see-also"></a>Vedere anche

[Parametri del cmdlet](./cmdlet-parameters.md)

[Scrittura di un cmdlet di Windows PowerShell](./writing-a-windows-powershell-cmdlet.md)

[Windows PowerShell SDK](../windows-powershell-reference.md)
