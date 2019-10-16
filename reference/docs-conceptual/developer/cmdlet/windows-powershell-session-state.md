---
title: Stato sessione di Windows PowerShell | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Cmdlets [PowerShell], session state
- session state [PowerShell]
ms.assetid: 74912940-2b10-4a76-b174-6d035d71c02b
caps.latest.revision: 8
ms.openlocfilehash: fa207130bbb120750780bb0aa9b32150a32daaa2
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/15/2019
ms.locfileid: "72369100"
---
# <a name="windows-powershell-session-state"></a>Stato della sessione di Windows PowerShell

Stato sessione si riferisce alla configurazione corrente di una sessione o di un modulo di Windows PowerShell. Una sessione di Windows PowerShell è l'ambiente operativo usato in modo interattivo dall'utente dalla riga di comando o a livello di codice da un'applicazione host. Lo stato della sessione per una sessione viene definito stato sessione globale.

Dal punto di vista dello sviluppatore, una sessione di Windows PowerShell si riferisce al tempo che intercorre tra l'apertura di un spazio di Windows PowerShell da parte di un'applicazione host e la chiusura del spazio. Osservando un altro modo, la sessione è la durata di un'istanza del motore di Windows PowerShell che viene richiamata mentre è presente spazio.

## <a name="module-session-state"></a>Stato sessione modulo

Gli Stati della sessione del modulo vengono creati ogni volta che il modulo o uno dei moduli nidificati viene importato nella sessione. Quando un modulo Esporta un elemento, ad esempio un cmdlet, una funzione o uno script, un riferimento a tale elemento viene aggiunto allo stato della sessione globale della sessione. Tuttavia, quando l'elemento viene eseguito, viene eseguito nello stato della sessione del modulo.

## <a name="session-state-data"></a>Dati dello stato sessione

I dati relativi allo stato della sessione possono essere pubblici o privati. I dati pubblici sono disponibili per le chiamate dall'esterno dello stato della sessione mentre i dati privati sono disponibili solo per le chiamate dall'interno dello stato della sessione. Un modulo, ad esempio, può avere una funzione privata che può essere chiamata solo dal modulo o solo internamente da un elemento pubblico che è stato esportato. Questa operazione è simile ai membri privati e pubblici di un tipo di .NET Framework.

I dati relativi allo stato sessione vengono archiviati dall'istanza corrente del motore di esecuzione all'interno del contesto della sessione corrente di Windows PowerShell. I dati relativi allo stato sessione sono costituiti dagli elementi seguenti:

- Informazioni sul percorso

- Informazioni sull'unità

- Informazioni sul provider di Windows PowerShell

- Informazioni sui moduli importati e i riferimenti agli elementi del modulo (ad esempio cmdlet, funzioni e script) esportati dal modulo. Queste informazioni e questi riferimenti sono solo per lo stato della sessione globale.

- Informazioni sulle variabili dello stato sessione

## <a name="accessing-session-state-data-within-cmdlets"></a>Accesso ai dati dello stato sessione nei cmdlet

I cmdlet possono accedere ai dati dello stato sessione indirettamente tramite la proprietà [System. Management. Automation. PSCmdlet. SessionState *](/dotnet/api/System.Management.Automation.PSCmdlet.SessionState) della classe cmdlet o direttamente tramite la classe [System. Management. Automation. SessionState](/dotnet/api/System.Management.Automation.SessionState) . La classe [System. Management. Automation. SessionState](/dotnet/api/System.Management.Automation.SessionState) fornisce proprietà che possono essere usate per analizzare diversi tipi di dati relativi allo stato sessione.

## <a name="see-also"></a>Vedere anche

[System. Management. Automation. PSCmdlet. SessionState](/dotnet/api/System.Management.Automation.PSCmdlet.SessionState)

[System. Management. Automation. SessionState? DisplayProperty = FullName](/dotnet/api/System.Management.Automation.SessionState)

[Cmdlet di Windows PowerShell](./cmdlet-overview.md)

[Scrittura di un cmdlet di Windows PowerShell](./writing-a-windows-powershell-cmdlet.md)

[SDK della shell di Windows PowerShell](../windows-powershell-reference.md)
