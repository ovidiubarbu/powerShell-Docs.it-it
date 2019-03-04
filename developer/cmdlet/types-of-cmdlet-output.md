---
title: Tipi di Output del Cmdlet | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2019
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- cmdlets [PowerShell SDK], output
ms.assetid: 547e6695-e936-4cac-a90b-417d0dab393d
caps.latest.revision: 12
ms.openlocfilehash: 3efa98c7aa22fdaee8042bae99282aea0618ef5f
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/03/2019
ms.locfileid: "56853927"
---
# <a name="types-of-cmdlet-output"></a>Tipi di output del cmdlet

PowerShell fornisce diversi metodi che possono essere chiamati dai cmdlet per generare l'output. Questi metodi usano un'operazione specifica per scrivere l'output in un flusso di dati specifico, ad esempio il flusso di dati di successo o il flusso di dati di errore. Questo articolo descrive i tipi di output e i metodi utilizzati per generarli.

## <a name="types-of-output"></a>Tipi di output

### <a name="success-output"></a>Output di

I cmdlet possono segnalato l'esito positivo, restituendo un oggetto che può essere elaborato dal comando successivo nella pipeline. Il cmdlet correttamente una volta eseguita l'azione corrispondente, il cmdlet chiama il [System.Management.Automation.Cmdlet.WriteObject](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject) (metodo). Si consiglia di chiamare questo metodo anziché il [WriteLine](/dotnet/api/System.Console.WriteLine) oppure [System.Management.Automation.Host.PSHostUserInterface.WriteLine](/dotnet/api/System.Management.Automation.Host.PSHostUserInterface.WriteLine) metodi.

È possibile specificare una **PassThru** passare parametri per i cmdlet che non restituiscono in genere gli oggetti.
Quando la **PassThru** parametro opzionale viene specificato nella riga di comando, il cmdlet viene richiesto di restituire un oggetto. Per un esempio di un cmdlet con un **PassThru** parametro, vedere [Add-History](/powershell/module/Microsoft.PowerShell.Core/Add-History).

### <a name="error-output"></a>Output degli errori

I cmdlet possono segnalare gli errori. Quando si verifica un errore irreversibile, il cmdlet genera un'eccezione. Quando si verifica un errore non fatale, chiama il cmdlet di [System.Management.Automation.Provider.CmdletProvider.WriteError](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.WriteError) metodo per inviare un record di errore al flusso di dati di errore. Per altre informazioni sulla segnalazione degli errori, vedere [concetti relativi a Reporting errore](./error-reporting-concepts.md).

### <a name="verbose-output"></a>Output dettagliato

I cmdlet possono fornire informazioni utili all'utente mentre il cmdlet viene corretta elaborazione dei record chiamando il [System.Management.Automation.Cmdlet.WriteVerbose](/dotnet/api/System.Management.Automation.Cmdlet.WriteVerbose) (metodo). Il metodo genera messaggi dettagliati che indicano il modo in cui l'azione di procedere.

Per impostazione predefinita, i messaggi dettagliati non vengono visualizzati. È possibile specificare il **Verbose** parametro quando viene eseguito il cmdlet per visualizzare questi messaggi. **Verbose** è un parametro comune che è disponibile per tutti i cmdlet.

### <a name="progress-output"></a>Output di stato di avanzamento

I cmdlet possono fornire informazioni sullo stato all'utente quando il cmdlet esegue le attività che richiedere molto tempo per completare, ad esempio la copia di una directory in modo ricorsivo. Per visualizzare le informazioni sullo stato di cmdlet chiama il [System.Management.Automation.Cmdlet.WriteProgress](/dotnet/api/System.Management.Automation.Cmdlet.WriteProgress) (metodo).

### <a name="debug-output"></a>L'output di debug

I cmdlet possono fornire messaggi di debug che sono utili per risolvere il problema del codice del cmdlet. Per visualizzare le informazioni di debug cmdlet chiama il [System.Management.Automation.Cmdlet.WriteDebug](/dotnet/api/System.Management.Automation.Cmdlet.WriteDebug) (metodo).

Per impostazione predefinita, non vengono visualizzati i messaggi di debug. È possibile specificare il **Debug** parametro quando viene eseguito il cmdlet per visualizzare questi messaggi. **Eseguire il debug** è un parametro comune che è disponibile per tutti i cmdlet.

### <a name="warning-output"></a>Output di avviso

I cmdlet possono visualizzare i messaggi di avviso chiamando il [System.Management.Automation.Cmdlet.WriteWarning](/dotnet/api/System.Management.Automation.Cmdlet.WriteWarning) (metodo).

Per impostazione predefinita, vengono visualizzati i messaggi di avviso. Tuttavia, è possibile configurare i messaggi di avviso tramite il `$WarningPreference` variabile oppure usando la **Verbose** e **eseguire il Debug** parametri quando viene chiamato il cmdlet.

## <a name="displaying-output"></a>Visualizzazione dell'output

Per tutte le chiamate di metodo di scrittura, la visualizzazione del contenuto è determinata dalle variabili di runtime specifico. L'eccezione è il [System.Management.Automation.Cmdlet.WriteObject](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject) (metodo). Usando queste variabili, è possibile rendere appropriato, scrivere chiamata nella posizione appropriata nel codice e senza doversi preoccupare quando o se l'output dovrebbe essere visualizzato.

## <a name="accessing-the-output-functionality-of-a-host-application"></a>Accedere alla funzionalità output di un'applicazione host

È anche possibile progettare un cmdlet per accedere direttamente alla funzionalità di output di un'applicazione host tramite il runtime di PowerShell. Utilizzando le API fornite da PowerShell anziché l'host [System. console](/dotnet/api/System.Console) oppure [Forms](/dotnet/api/System.Windows.Forms) assicura che il cmdlet funzionerà con un'ampia gamma di host. Ad esempio: la **powershell.exe** host della console, il **powershell_ise.exe** host con interfaccia grafica, l'host di comunicazione remota di PowerShell e gli host di terze parti.

## <a name="see-also"></a>Vedere anche

[Concetti di segnalazione errori](./error-reporting-concepts.md)

[Panoramica su cmdlet](./cmdlet-overview.md)

[Scrittura di un cmdlet di Windows PowerShell](./writing-a-windows-powershell-cmdlet.md)