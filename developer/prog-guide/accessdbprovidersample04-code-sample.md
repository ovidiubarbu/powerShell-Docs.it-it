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
ms.openlocfilehash: 43f01b9cd6af3ab6c26f88ee0c1e9269499b2bc3
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/03/2019
ms.locfileid: "56853607"
---
# <a name="accessdbprovidersample04-code-sample"></a>Codice di esempio di AccessDbProviderSample04

Il codice seguente viene illustrata l'implementazione del provider di Windows PowerShell descritto nella [creazione di un Provider di contenitore di Windows PowerShell](./creating-a-windows-powershell-container-provider.md). Questo provider funziona in archivi dati a più livelli. Per questo tipo di archivio dati, il livello principale dell'archivio contiene gli elementi radice e ogni livello successivo viene considerato come un nodo di elementi figlio. Tramite l'archivio dati, consentendo all'utente di lavorare su questi nodi figlio, un utente può interagire in modo gerarchico.

## <a name="code-sample"></a>Esempio di codice

[!code-csharp[AccessDBProviderSample04.cs](../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample04/AccessDBProviderSample04.cs#L11-L1635 "AccessDBProviderSample04.cs")]

## <a name="see-also"></a>Vedere anche

[Windows PowerShell SDK](../windows-powershell-reference.md)