---
title: Esempio di codice RunSpace08 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 0f286201-8a02-4b00-9a2c-1b833ccdbdbf
caps.latest.revision: 7
ms.openlocfilehash: 2e9cd80f1869e0d859187eea89eca414a84cb4ab
ms.sourcegitcommit: d97b200e7a49315ce6608cd619e3e2fd99193edd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/10/2020
ms.locfileid: "75870584"
---
# <a name="runspace08-code-sample"></a>Codice di esempio di Runspace08

Ecco il codice sorgente per l'esempio Runspace08 descritto in [creazione di un'applicazione console che aggiunge parametri a un comando](https://msdn.microsoft.com/848b2b46-60f1-4a86-b448-cfc7c0cccfba).
Questa applicazione di esempio crea un spazio, crea una pipeline, aggiunge due comandi alla pipeline, aggiunge due parametri al secondo comando e quindi esegue la pipeline. I comandi aggiunti alla pipeline sono i cmdlet `Get-Process` e `Sort-Object`.

## <a name="code-sample"></a>Codice di esempio

[!code-csharp[Runspace08.cs](../../../../powershell-sdk-samples/SDK-2.0/csharp/Runspace08/Runspace08.cs#L11-L86 "Runspace08.cs")]

## <a name="see-also"></a>Vedere anche

[Windows PowerShell SDK](../windows-powershell-reference.md)
