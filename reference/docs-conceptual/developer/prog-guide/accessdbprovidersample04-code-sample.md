---
title: Esempio di codice AccessDbProviderSample04 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f9374c4a-e499-4516-9eb6-107c59df98d9
caps.latest.revision: 7
ms.openlocfilehash: ff43286bc90c1a4d2270be0ee03ca5910867cec2
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/05/2019
ms.locfileid: "72366970"
---
# <a name="accessdbprovidersample04-code-sample"></a>Codice di esempio di AccessDbProviderSample04

Il codice seguente illustra l'implementazione del provider di Windows PowerShell descritto in [creazione di un provider di contenitori di Windows PowerShell](./creating-a-windows-powershell-container-provider.md). Questo provider funziona in archivi dati a più livelli. Per questo tipo di archivio dati, il livello principale dell'archivio contiene gli elementi radice e ogni livello successivo viene definito nodo di elementi figlio. Consentendo all'utente di lavorare su questi nodi figlio, un utente può interagire gerarchicamente con l'archivio dati.

## <a name="code-sample"></a>Codice di esempio

[!code-csharp[AccessDBProviderSample04.cs](../../../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample04/AccessDBProviderSample04.cs#L11-L1635 "AccessDBProviderSample04.cs")]

## <a name="see-also"></a>Vedere anche

[Windows PowerShell SDK](../windows-powershell-reference.md)
