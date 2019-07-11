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
ms.openlocfilehash: 1a21af4b48a414d9c9fee57871eacb0a39c9ab11
ms.sourcegitcommit: 46bebe692689ebedfe65ff2c828fe666b443198d
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/10/2019
ms.locfileid: "67734902"
---
# <a name="runspace09-code-sample"></a>Codice di esempio di Runspace09

Ecco il codice sorgente per l'esempio Runspace09 descritto in [la creazione di una Console dell'applicazione che richiama una Pipeline in modo asincrono](https://msdn.microsoft.com/en-us/198c1c94-2a06-457e-93ce-c0d910618e47). Questa applicazione di esempio crea e apre uno spazio di esecuzione, viene creata e richiama in modo asincrono una pipeline e quindi utilizza pipeline di eventi per elaborare lo script in modo asincrono. Lo script che viene eseguito da questa applicazione crea i numeri interi compresi tra 1 e 10 in intervalli di 0,5 secondi (500 ms).

## <a name="code-sample"></a>Esempio di codice

[!code-csharp[Runspace09.cs](../../powershell-sdk-samples/SDK-2.0/csharp/Runspace09/Runspace09.cs#L11-L113 "Runspace09.cs")]

## <a name="see-also"></a>Vedere anche

[Windows PowerShell SDK](../windows-powershell-reference.md)