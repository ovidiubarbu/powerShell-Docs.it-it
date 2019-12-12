---
title: Parametri di formato | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 10e025c5-9aa6-45a5-b851-23d14db1f4cc
caps.latest.revision: 7
ms.openlocfilehash: 0bd3888d81aa6d1dde26c0066f7bca9dac8a8bca
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/05/2019
ms.locfileid: "72369750"
---
# <a name="format-parameters"></a>Parametri di formattazione

Nella tabella seguente sono elencati i nomi e le funzionalità consigliati per i parametri utilizzati per formattare o generare dati.

|Parametro|Funzionalità|
|---|---|
|**As**<br>Tipo di dati: parola chiave|Implementare questo parametro per specificare il formato di output del cmdlet. Ad esempio, i valori possibili potrebbero essere testo o script.|
|**Binario**<br>Tipo di dati: SwitchParameter|Implementare questo parametro per indicare che il cmdlet gestisce i valori binari.|
|**Codifica**<br>Tipo di dati: parola chiave|Implementare questo parametro per specificare il tipo di codifica supportata. Ad esempio, i valori possibili sono ASCII, UTF8, Unicode, UTF7, BigEndianUnicode, byte e String.|
|**NewLine**<br>Tipo di dati: SwitchParameter|Implementare questo parametro in modo che i caratteri di nuova riga siano supportati quando si specifica il parametro.|
|**Nome breve**<br>Tipo di dati: SwitchParameter|Implementare questo parametro in modo che i nomi brevi siano supportati quando si specifica il parametro.|
|**Width**<br>Tipo di dati: Int32|Implementare questo parametro in modo che l'utente possa specificare la larghezza del dispositivo di output.|
|**Avvolgere**<br>Tipo di dati: SwitchParameter|Implementare questo parametro in modo che il ritorno a capo del testo sia supportato quando si specifica il parametro.|
## <a name="see-also"></a>Vedere anche

[Parametri dei cmdlet](./cmdlet-parameters.md)

[Scrittura di un cmdlet di Windows PowerShell](./writing-a-windows-powershell-cmdlet.md)

[Windows PowerShell SDK](../windows-powershell-reference.md)
