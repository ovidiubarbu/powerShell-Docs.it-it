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
ms.openlocfilehash: ec6aae544eafea1dedc1379dab00beeed2c7c436
ms.sourcegitcommit: 46bebe692689ebedfe65ff2c828fe666b443198d
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/10/2019
ms.locfileid: "67734909"
---
# <a name="runspace08-code-sample"></a>Codice di esempio di Runspace08

Ecco il codice sorgente per l'esempio Runspace08 descritto in [creazione di una Console che aggiunge i parametri dell'applicazione a un comando](https://msdn.microsoft.com/en-us/848b2b46-60f1-4a86-b448-cfc7c0cccfba). Questa applicazione di esempio crea uno spazio di esecuzione, viene creata una pipeline, aggiunge i due comandi alla pipeline, aggiunge due parametri per il secondo comando e quindi esegue la pipeline. I comandi che vengono aggiunti alla pipeline sono le `Get-Process` e `Sort-Object` cmdlet.

## <a name="code-sample"></a>Esempio di codice

[!code-csharp[Runspace08.cs](../../powershell-sdk-samples/SDK-2.0/csharp/Runspace08/Runspace08.cs#L11-L86 "Runspace08.cs")]

## <a name="see-also"></a>Vedere anche

[Windows PowerShell SDK](../windows-powershell-reference.md)