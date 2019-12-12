---
title: Parametri Quantity | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 8c0bd8a9-1749-4885-ab24-38c0a4d9f2cb
caps.latest.revision: 6
ms.openlocfilehash: 7a3efc60fcc8729d833f6de070016cfd08cc9b88
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/05/2019
ms.locfileid: "72369560"
---
# <a name="quantity-parameters"></a>Parametri delle quantità

Nella tabella seguente sono elencati i nomi e le funzionalità consigliati per i parametri di quantità.

|Parametro|Funzionalità|
|---|---|
|**Tutto**<br>Tipo di dati: Boolean|Implementare questo parametro in modo che `true` indichi che è necessario agire su tutte le risorse anziché su un subset predefinito di risorse. Implementare questo parametro in modo che `false` indichi un subset delle risorse.|
|**Allocation**<br>Tipo di dati: Int32|Implementare questo parametro in modo che l'utente possa specificare il numero di elementi da allocare.|
|**BlockCount**<br>Tipo di dati: Int64|Implementare questo parametro in modo che l'utente possa specificare il numero di blocchi.|
|**Count**<br>Tipo di dati: Int64|Implementare questo parametro in modo che l'utente possa specificare il conteggio.|
|**Ambito**<br>Tipo di dati: parola chiave|Implementare questo parametro in modo che l'utente possa specificare l'ambito su cui operare.|

## <a name="see-also"></a>Vedere anche

[Parametri dei cmdlet](./cmdlet-parameters.md)

[Scrittura di un cmdlet di Windows PowerShell](./writing-a-windows-powershell-cmdlet.md)

[Windows PowerShell SDK](../windows-powershell-reference.md)
