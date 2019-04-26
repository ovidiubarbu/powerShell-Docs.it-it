---
title: Parametri di quantità | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 8c0bd8a9-1749-4885-ab24-38c0a4d9f2cb
caps.latest.revision: 6
ms.openlocfilehash: 7a3efc60fcc8729d833f6de070016cfd08cc9b88
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62067536"
---
# <a name="quantity-parameters"></a>Parametri delle quantità

La tabella seguente elenca i nomi consigliati e funzionalità per i parametri di quantità.

|Parametro|Funzionalità|
|---|---|
|**Tutti i**<br>Tipo di dati: Booleano|Implementare questo parametro in modo che `true` indica che tutte le risorse devono essere elaborate invece di un subset predefinito delle risorse. Implementare questo parametro in modo che `false` indica un subset delle risorse.|
|**Allocazione**<br>Tipo di dati: Int32|Implementare questo parametro in modo che l'utente può specificare il numero di elementi da allocare.|
|**BlockCount**<br>Tipo di dati: Int64|Implementare questo parametro in modo che l'utente può specificare il numero di blocchi.|
|**conteggio**<br>Tipo di dati: Int64|Implementare questo parametro in modo che l'utente può specificare il conteggio.|
|**Ambito**<br>Tipo di dati: Parola chiave|Implementare questo parametro in modo che l'utente può specificare l'ambito su cui operare.|

## <a name="see-also"></a>Vedere anche

[Parametri del cmdlet](./cmdlet-parameters.md)

[Scrittura di un cmdlet di Windows PowerShell](./writing-a-windows-powershell-cmdlet.md)

[Windows PowerShell SDK](../windows-powershell-reference.md)
