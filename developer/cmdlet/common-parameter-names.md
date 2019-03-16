---
title: I nomi dei parametri comuni | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 0db9f54c-4014-4450-9e81-c9f5fe562a0e
caps.latest.revision: 12
ms.openlocfilehash: c65deeda6b2ef1b52de55035dc606259a7f2d232
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/16/2019
ms.locfileid: "58059661"
---
# <a name="common-parameter-names"></a>Nomi dei parametri comuni

I parametri descritti in questo argomento sono dette *parametri comuni*. Essi vengono aggiunti ai cmdlet per il runtime di Windows PowerShell e non può essere dichiarati dal cmdlet.

> [!NOTE]
> Questi parametri vengono aggiunti anche al cmdlet del provider e alle funzioni che sono decorate con il `CmdletBinding` attributo.

## <a name="general-common-parameters"></a>Parametri comuni di generale

I parametri seguenti vengono aggiunti a tutti i cmdlet e accessibili ogni volta che viene eseguito il cmdlet. Questi parametri vengono definiti per il [System.Management.Automation.Internal.Commonparameters](/dotnet/api/System.Management.Automation.Internal.CommonParameters) classe.

### <a name="debug-alias-db"></a>Eseguire il debug (alias: db)

Tipo di dati: SwitchParameter

Questo parametro specifica se il debug a livello di programmazione dei messaggi che possono essere visualizzati nella riga di comando. Questi messaggi sono per la risoluzione dei problemi di funzionamento del cmdlet e vengono generati da chiamate al [System.Management.Automation.Cmdlet.WriteDebug](/dotnet/api/System.Management.Automation.Cmdlet.WriteDebug) (metodo). I messaggi di debug non sono necessario essere localizzati.

### <a name="erroraction-alias-ea"></a>ErrorAction (alias: con contratto Enterprise Agreement)

Tipo di dati: Enumerazione

Questo parametro specifica l'azione da eseguire quando si verifica un errore. I valori possibili per questo parametro sono definiti per il [System.Management.Automation.Actionpreference](/dotnet/api/System.Management.Automation.ActionPreference) enumerazione.

### <a name="errorvariable-alias-ev"></a>ErrorVariable (alias: ev)

Tipo di dati: String

Questo parametro specifica la variabile in cui inserire gli oggetti quando si verifica un errore. Per aggiungere questa variabile, usare +*varname* invece che con la cancellazione e impostazione della variabile.

### <a name="outvariable-alias-ov"></a>OutVariable (alias: ov)

Tipo di dati: String

Questo parametro specifica la variabile in cui inserire tutti gli oggetti generati dal cmdlet di output. Per aggiungere questa variabile, usare +*varname* invece che con la cancellazione e impostazione della variabile.

### <a name="outbuffer-alias-ob"></a>OutBuffer (alias: ob)

Tipo di dati: Int32

Questo parametro definisce il numero di oggetti da memorizzare nel buffer di output prima di tutti gli oggetti vengono passati alla pipeline. Per impostazione predefinita, gli oggetti vengono passati alla pipeline immediatamente.

### <a name="verbose-alias-vb"></a>Verbose (alias: Visual Basic)

Tipo di dati: SwitchParameter

Questo parametro specifica se il cmdlet scrive esplicativi messaggi che possono essere visualizzati nella riga di comando. Questi messaggi sono destinati a fornire informazioni aggiuntive all'utente e vengono generati da chiamate al [System.Management.Automation.Cmdlet.WriteVerbose](/dotnet/api/System.Management.Automation.Cmdlet.WriteVerbose) (metodo).

### <a name="warningaction-alias-wa"></a>WarningAction (alias: wa)

Tipo di dati: Enumerazione

Questo parametro specifica l'azione da eseguire quando il cmdlet scrive un messaggio di avviso. I valori possibili per questo parametro sono definiti per il [System.Management.Automation.Actionpreference](/dotnet/api/System.Management.Automation.ActionPreference) enumerazione.

### <a name="warningvariable-alias-wv"></a>WarningVariable (alias: wv)

Tipo di dati: String

Questo parametro specifica la variabile in cui possono essere salvati i messaggi di avviso. Per aggiungere questa variabile, usare +*varname* invece che con la cancellazione e impostazione della variabile.

## <a name="risk-mitigation-parameters"></a>Parametri di attenuazione dei rischi

I parametri seguenti vengono aggiunti ai cmdlet che richiede una conferma prima di eseguire l'azione. Per altre informazioni sulle richieste di conferma, vedere [richiesta di conferma](./requesting-confirmation-from-cmdlets.md). Questi parametri vengono definiti per il [System.Management.Automation.Internal.Shouldprocessparameters](/dotnet/api/System.Management.Automation.Internal.ShouldProcessParameters) classe.

### <a name="confirm-alias-cf"></a>Verificare (alias: cloud Foundry)

Tipo di dati: SwitchParameter

Questo parametro specifica se il cmdlet Visualizza un messaggio che richiede se l'utente è un'operazione che si vuole continuare.

### <a name="whatif-alias-wi"></a>WhatIf (alias: wi)

Tipo di dati: SwitchParameter

Questo parametro specifica se il cmdlet scrive un messaggio che descrive gli effetti dell'esecuzione del cmdlet senza effettivamente eseguire alcuna azione.

## <a name="transaction-parameters"></a>Parametri delle transazioni

Il parametro seguente viene aggiunto ai cmdlet che supportano le transazioni. Questi parametri vengono definiti per il [System.Management.Automation.Internal.Transactionparameters](/dotnet/api/System.Management.Automation.Internal.TransactionParameters) classe.

### <a name="usetransaction-alias-usetx"></a>UseTransaction (alias: usetx)

Tipo di dati: SwitchParameter

Questo parametro specifica se il cmdlet userà la transazione corrente per eseguire l'azione.

## <a name="see-also"></a>Vedere anche

[System.Management.Automation.Internal.Commonparameters](/dotnet/api/System.Management.Automation.Internal.CommonParameters)

[System.Management.Automation.Internal.Shouldprocessparameters](/dotnet/api/System.Management.Automation.Internal.ShouldProcessParameters)

[System.Management.Automation.Internal.Transactionparameters](/dotnet/api/System.Management.Automation.Internal.TransactionParameters)

[Scrittura di un cmdlet di Windows PowerShell](./writing-a-windows-powershell-cmdlet.md)

[Windows PowerShell SDK](../windows-powershell-reference.md)
