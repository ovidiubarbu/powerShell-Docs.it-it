---
title: Esempio di codice RunSpace09 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 136e451f-767b-42e0-bd6f-6486693abd5e
caps.latest.revision: 6
ms.openlocfilehash: 2f447fd0ce21c5bca8abe1fddb4e3c7025b70ef1
ms.sourcegitcommit: d97b200e7a49315ce6608cd619e3e2fd99193edd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/10/2020
ms.locfileid: "75870583"
---
# <a name="runspace09-code-sample"></a>Codice di esempio di Runspace09

Ecco il codice sorgente per l'esempio Runspace09 descritto in [creazione di un'applicazione console che richiama una pipeline in modo asincrono](https://msdn.microsoft.com/198c1c94-2a06-457e-93ce-c0d910618e47).
Questa applicazione di esempio crea e apre un spazio, crea e richiama in modo asincrono una pipeline, quindi usa gli eventi della pipeline per elaborare lo script in modo asincrono. Lo script eseguito da questa applicazione crea i numeri interi da 1 a 10 in intervalli di 0,5 secondi (500 ms).

## <a name="code-sample"></a>Codice di esempio

[!code-csharp[Runspace09.cs](../../../../powershell-sdk-samples/SDK-2.0/csharp/Runspace09/Runspace09.cs#L11-L113 "Runspace09.cs")]

## <a name="see-also"></a>Vedere anche

[Windows PowerShell SDK](../windows-powershell-reference.md)
