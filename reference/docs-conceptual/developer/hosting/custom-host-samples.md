---
title: Esempi di host personalizzati | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 55aee25b-bbcb-4d41-a4c0-fb8e30c4cdc1
caps.latest.revision: 11
ms.openlocfilehash: 1e58b74cf1c37c70ebfb0f4970cfbf8a8263ec5c
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/05/2019
ms.locfileid: "72367510"
---
# <a name="custom-host-samples"></a>Esempi di host personalizzati

In questa sezione è incluso il codice di esempio per la scrittura di un host personalizzato. È possibile utilizzare Microsoft Visual Studio per creare un'applicazione console e quindi copiare il codice dagli argomenti in questa sezione nell'applicazione host.

## <a name="in-this-section"></a>Contenuto della sezione

 [Esempio host01](./host01-sample.md) Questo esempio illustra come implementare un'applicazione host che usa un host personalizzato di base.

 [Esempio Host02](./host02-sample.md) Questo esempio illustra come scrivere un'applicazione host che usa il runtime di Windows PowerShell insieme a un'implementazione host personalizzata. L'applicazione host imposta le impostazioni cultura dell'host su tedesco, esegue il cmdlet [Get-Process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) e Visualizza i risultati come verrebbero visualizzati utilizzando pwrsh. exe, quindi stampa i dati e l'ora correnti in tedesco.

 [Esempio Host03](./host03-sample.md) Questo esempio illustra come compilare un'applicazione host basata su console interattiva che legge i comandi dalla riga di comando, esegue i comandi e quindi Visualizza i risultati nella console.

 [Esempio Host04](./host04-sample.md) Questo esempio illustra come compilare un'applicazione host basata su console interattiva che legge i comandi dalla riga di comando, esegue i comandi e quindi Visualizza i risultati nella console. L'applicazione host supporta anche la visualizzazione di messaggi di richiesta che consentono all'utente di specificare più opzioni.

 [Esempio Host05](./host05-sample.md) Questo esempio illustra come compilare un'applicazione host basata su console interattiva che legge i comandi dalla riga di comando, esegue i comandi e quindi Visualizza i risultati nella console. Questa applicazione host supporta anche le chiamate a computer remoti tramite i cmdlet [Enter-PSSession](/powershell/module/Microsoft.PowerShell.Core/Enter-PSSession) e [Exit-PSSession](/powershell/module/Microsoft.PowerShell.Core/Exit-PSSession)

 [Esempio Host06](./host06-sample.md) Questo esempio illustra come compilare un'applicazione host basata su console interattiva che legge i comandi dalla riga di comando, esegue i comandi e quindi Visualizza i risultati nella console. Questo esempio usa inoltre le API del tokenizer per specificare il colore del testo immesso dall'utente.

## <a name="see-also"></a>Vedere anche
