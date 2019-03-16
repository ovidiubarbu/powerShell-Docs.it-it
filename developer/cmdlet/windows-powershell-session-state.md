---
title: Lo stato della sessione di Windows PowerShell | Microsoft Docs
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
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/16/2019
ms.locfileid: "58059542"
---
# <a name="windows-powershell-session-state"></a>Stato della sessione di Windows PowerShell

Lo stato della sessione si riferisce alla configurazione corrente di una sessione di Windows PowerShell o un modulo. Una sessione di Windows PowerShell è l'ambiente operativo che viene usato in modo interattivo dall'utente della riga di comando o a livello di codice da un'applicazione host. Lo stato della sessione per una sessione è detto lo stato sessione globale.

Dalla prospettiva dello sviluppatore, una sessione di Windows PowerShell si intende il tempo tra un'applicazione host all'apertura di uno spazio di esecuzione di Windows PowerShell e quando chiude lo spazio di esecuzione. Preso in esame un altro modo, la sessione è la durata di un'istanza del motore di Windows PowerShell che viene richiamato mentre è presente lo spazio di esecuzione.

## <a name="module-session-state"></a>Stato sessione modulo

Stato dei moduli della sessione viene creati ogni volta che viene importato il modulo o uno dei relativi moduli annidati nella sessione. Quando un modulo Esporta un elemento, ad esempio un cmdlet, funzione o script, un riferimento a tale elemento viene aggiunto allo stato sessione globale della sessione. Tuttavia, quando si esegue l'elemento, viene eseguita nello stato della sessione del modulo.

## <a name="session-state-data"></a>Dati dello stato della sessione

I dati dello stato della sessione possono essere pubblico o privato. Dati pubblici sono disponibili per le chiamate dall'esterno dello stato della sessione mentre sono disponibili solo per le chiamate da all'interno dello stato della sessione dati privati. Ad esempio, un modulo può avere una funzione privata che può essere chiamata solo dal modulo o solo internamente da un elemento pubblico che è stato esportato. È simile ai membri privati e pubblici di un tipo .NET Framework.

Dati dello stato della sessione vengono archiviati per l'istanza corrente del motore di esecuzione all'interno del contesto della sessione di Windows PowerShell corrente. I dati dello stato della sessione prevede i seguenti elementi:

- Informazioni sul percorso

- Informazioni sull'unità

- Informazioni sul provider di Windows PowerShell

- Informazioni sui moduli importati e i riferimenti agli elementi di modulo (ad esempio cmdlet, funzioni e script) che vengono esportati dal modulo. Queste informazioni e questi riferimenti sono per solo lo stato sessione globale.

- Informazioni sulle variabili dello stato della sessione

## <a name="accessing-session-state-data-within-cmdlets"></a>L'accesso ai dati dello stato sessione all'interno di cmdlet

I cmdlet possono accedere ai dati dello stato della sessione sia indirettamente tramite il [System.Management.Automation.PSCmdlet.Sessionstate*](/dotnet/api/System.Management.Automation.PSCmdlet.SessionState) proprietà di classe del cmdlet o direttamente tramite il [ System.Management.Automation.Sessionstate](/dotnet/api/System.Management.Automation.SessionState) classe. Il [System.Management.Automation.Sessionstate](/dotnet/api/System.Management.Automation.SessionState) classe fornisce proprietà che può essere utilizzata per analizzare diversi tipi di dati dello stato della sessione.

## <a name="see-also"></a>Vedere anche

[System.Management.Automation.PSCmdlet.Sessionstate](/dotnet/api/System.Management.Automation.PSCmdlet.SessionState)

[System.Management.Automation.Sessionstate?Displayproperty=Fullname](/dotnet/api/System.Management.Automation.SessionState)

[Cmdlet di Windows PowerShell](./cmdlet-overview.md)

[Scrittura di un cmdlet di Windows PowerShell](./writing-a-windows-powershell-cmdlet.md)

[Windows PowerShell Shell SDK](../windows-powershell-reference.md)
