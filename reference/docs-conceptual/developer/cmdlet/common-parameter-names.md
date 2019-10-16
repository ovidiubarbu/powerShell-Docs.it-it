---
title: Nomi di parametro comuni | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 0db9f54c-4014-4450-9e81-c9f5fe562a0e
caps.latest.revision: 12
ms.openlocfilehash: c65deeda6b2ef1b52de55035dc606259a7f2d232
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/15/2019
ms.locfileid: "72365740"
---
# <a name="common-parameter-names"></a>Nomi dei parametri comuni

I parametri descritti in questo argomento sono definiti *parametri comuni*. Vengono aggiunti ai cmdlet dal runtime di Windows PowerShell e non possono essere dichiarati dal cmdlet.

> [!NOTE]
> Questi parametri vengono inoltre aggiunti ai cmdlet del provider e alle funzioni decorate con l'attributo `CmdletBinding`.

## <a name="general-common-parameters"></a>Parametri comuni generali

I parametri seguenti vengono aggiunti a tutti i cmdlet ed è possibile accedervi ogni volta che viene eseguito il cmdlet. Questi parametri sono definiti dalla classe [System. Management. Automation. Internal. parametricomuni](/dotnet/api/System.Management.Automation.Internal.CommonParameters) .

### <a name="debug-alias-db"></a>Debug (alias: DB)

Tipo di dati: SwitchParameter

Questo parametro specifica se i messaggi di debug a livello di programmatore possono essere visualizzati nella riga di comando. Questi messaggi sono intesi per la risoluzione dei problemi relativi al funzionamento del cmdlet e vengono generati dalle chiamate al metodo [System. Management. Automation. cmdlet. WriteDebug](/dotnet/api/System.Management.Automation.Cmdlet.WriteDebug) . Non è necessario localizzare i messaggi di debug.

### <a name="erroraction-alias-ea"></a>ErrorAction (alias: EA)

Tipo di dati: enumerazione

Questo parametro specifica l'azione che deve essere eseguita quando si verifica un errore. I valori possibili per questo parametro sono definiti dall'enumerazione [System. Management. Automation. preferenzaazione](/dotnet/api/System.Management.Automation.ActionPreference) .

### <a name="errorvariable-alias-ev"></a>ErrorVariable (alias: EV)

Tipo di dati: String

Questo parametro specifica la variabile in cui inserire gli oggetti quando si verifica un errore. Per accodare questa variabile, utilizzare +*VarName* anziché cancellare e impostare la variabile.

### <a name="outvariable-alias-ov"></a>OutVariable (alias: OV)

Tipo di dati: String

Questo parametro specifica la variabile in cui inserire tutti gli oggetti di output generati dal cmdlet. Per accodare questa variabile, utilizzare +*VarName* anziché cancellare e impostare la variabile.

### <a name="outbuffer-alias-ob"></a>OutBuffer (alias: ob)

Tipo di dati: Int32

Questo parametro definisce il numero di oggetti da archiviare nel buffer di output prima che gli oggetti vengano passati alla pipeline. Per impostazione predefinita, gli oggetti vengono passati immediatamente alla pipeline.

### <a name="verbose-alias-vb"></a>Verbose (alias: VB)

Tipo di dati: SwitchParameter

Questo parametro specifica se il cmdlet scrive messaggi esplicativi che possono essere visualizzati dalla riga di comando. Questi messaggi hanno lo scopo di fornire ulteriore assistenza all'utente e vengono generati dalle chiamate al metodo [System. Management. Automation. cmdlet. WriteVerbose](/dotnet/api/System.Management.Automation.Cmdlet.WriteVerbose) .

### <a name="warningaction-alias-wa"></a>WarningAction (alias: WA)

Tipo di dati: enumerazione

Questo parametro specifica l'azione che deve essere eseguita quando il cmdlet scrive un messaggio di avviso. I valori possibili per questo parametro sono definiti dall'enumerazione [System. Management. Automation. preferenzaazione](/dotnet/api/System.Management.Automation.ActionPreference) .

### <a name="warningvariable-alias-wv"></a>WarningVariable (alias: WV)

Tipo di dati: String

Questo parametro specifica la variabile in cui è possibile salvare i messaggi di avviso. Per accodare questa variabile, utilizzare +*VarName* anziché cancellare e impostare la variabile.

## <a name="risk-mitigation-parameters"></a>Parametri di mitigazione dei rischi

I parametri seguenti vengono aggiunti ai cmdlet che richiedono la conferma prima di eseguire l'azione. Per ulteriori informazioni sulle richieste di conferma, vedere [richiesta di conferma](./requesting-confirmation-from-cmdlets.md). Questi parametri sono definiti dalla classe [System. Management. Automation. Internal. Shouldprocessparameters](/dotnet/api/System.Management.Automation.Internal.ShouldProcessParameters) .

### <a name="confirm-alias-cf"></a>Conferma (alias: CF)

Tipo di dati: SwitchParameter

Questo parametro specifica se il cmdlet visualizza un messaggio che chiede se l'utente è sicuro di voler continuare.

### <a name="whatif-alias-wi"></a>WhatIf (alias: Wi)

Tipo di dati: SwitchParameter

Questo parametro specifica se il cmdlet scrive un messaggio che descrive gli effetti dell'esecuzione del cmdlet senza eseguire effettivamente alcuna azione.

## <a name="transaction-parameters"></a>Parametri di transazione

Il parametro seguente viene aggiunto ai cmdlet che supportano le transazioni. Questi parametri sono definiti dalla classe [System. Management. Automation. Internal. Transactionparameters](/dotnet/api/System.Management.Automation.Internal.TransactionParameters) .

### <a name="usetransaction-alias-usetx"></a>UseTransaction (alias: UseTx)

Tipo di dati: SwitchParameter

Questo parametro specifica se il cmdlet utilizzerà la transazione corrente per eseguire l'azione.

## <a name="see-also"></a>Vedere anche

[System. Management. Automation. Internal. Parametricomuni](/dotnet/api/System.Management.Automation.Internal.CommonParameters)

[System. Management. Automation. Internal. Shouldprocessparameters](/dotnet/api/System.Management.Automation.Internal.ShouldProcessParameters)

[System. Management. Automation. Internal. Transactionparameters](/dotnet/api/System.Management.Automation.Internal.TransactionParameters)

[Scrittura di un cmdlet di Windows PowerShell](./writing-a-windows-powershell-cmdlet.md)

[Windows PowerShell SDK](../windows-powershell-reference.md)
