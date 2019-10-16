---
title: Tipi di output del cmdlet | Microsoft Docs
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
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/15/2019
ms.locfileid: "72369290"
---
# <a name="types-of-cmdlet-output"></a>Tipi di output del cmdlet

PowerShell offre diversi metodi che possono essere chiamati dai cmdlet per generare l'output. Questi metodi usano un'operazione specifica per scrivere l'output in un flusso di dati specifico, ad esempio il flusso di dati di esito positivo o il flusso di dati di errore. Questo articolo descrive i tipi di output e i metodi usati per generarli.

## <a name="types-of-output"></a>Tipi di output

### <a name="success-output"></a>Output riuscito

I cmdlet possono segnalare l'esito positivo restituendo un oggetto che può essere elaborato dal comando successivo nella pipeline. Dopo che l'azione è stata eseguita correttamente dal cmdlet, il cmdlet chiama il metodo [System. Management. Automation. cmdlet. WriteObject](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject) . Si consiglia di chiamare questo metodo anziché i metodi [System. Console. WriteLine](/dotnet/api/System.Console.WriteLine) o [System. Management. Automation. host. PSHostUserInterface. WriteLine](/dotnet/api/System.Management.Automation.Host.PSHostUserInterface.WriteLine) .

È possibile specificare un parametro di opzione **PassThru** per i cmdlet che in genere non restituiscono oggetti.
Quando il parametro **PassThru** switch viene specificato dalla riga di comando, al cmdlet viene richiesto di restituire un oggetto. Per un esempio di cmdlet con un parametro **PassThru** , vedere [Add-History](/powershell/module/Microsoft.PowerShell.Core/Add-History).

### <a name="error-output"></a>Output degli errori

I cmdlet possono segnalare errori. Quando si verifica un errore di terminazione, il cmdlet genera un'eccezione. Quando si verifica un errore non fatale, il cmdlet chiama il metodo [System. Management. Automation. provider. CmdletProvider. WriteError](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.WriteError) per inviare un record di errore al flusso di dati degli errori. Per ulteriori informazioni sulla segnalazione errori, vedere la pagina relativa ai [concetti relativi alla segnalazione degli errori](./error-reporting-concepts.md).

### <a name="verbose-output"></a>Output dettagliato

I cmdlet possono fornire informazioni utili quando il cmdlet esegue correttamente l'elaborazione dei record chiamando il metodo [System. Management. Automation. cmdlet. WriteVerbose](/dotnet/api/System.Management.Automation.Cmdlet.WriteVerbose) . Il metodo genera messaggi dettagliati che indicano il modo in cui l'azione sta procedendo.

Per impostazione predefinita, i messaggi dettagliati non vengono visualizzati. È possibile specificare il parametro **verbose** quando viene eseguito il cmdlet per visualizzare questi messaggi. **Verbose** è un parametro comune disponibile per tutti i cmdlet.

### <a name="progress-output"></a>Output di avanzamento

I cmdlet possono fornire informazioni sullo stato di avanzamento quando il cmdlet esegue attività che impostano molto tempo per essere completate, ad esempio la copia di una directory in modo ricorsivo. Per visualizzare le informazioni sullo stato di avanzamento, il cmdlet chiama il metodo [System. Management. Automation. cmdlet. WriteProgress](/dotnet/api/System.Management.Automation.Cmdlet.WriteProgress) .

### <a name="debug-output"></a>Output di debug

I cmdlet possono fornire messaggi di debug utili per la risoluzione dei problemi del codice del cmdlet. Per visualizzare le informazioni di debug, il cmdlet chiama il metodo [System. Management. Automation. cmdlet. WriteDebug](/dotnet/api/System.Management.Automation.Cmdlet.WriteDebug) .

Per impostazione predefinita, i messaggi di debug non vengono visualizzati. È possibile specificare il parametro **debug** quando viene eseguito il cmdlet per visualizzare questi messaggi. **Debug** è un parametro comune disponibile per tutti i cmdlet.

### <a name="warning-output"></a>Output avviso

I cmdlet possono visualizzare messaggi di avviso chiamando il metodo [System. Management. Automation. cmdlet. WriteWarning](/dotnet/api/System.Management.Automation.Cmdlet.WriteWarning) .

Per impostazione predefinita, vengono visualizzati i messaggi di avviso. Tuttavia, è possibile configurare i messaggi di avviso utilizzando la variabile `$WarningPreference` oppure i parametri **verbose** e **debug** quando viene chiamato il cmdlet.

## <a name="displaying-output"></a>Visualizzazione dell'output

Per tutte le chiamate al metodo Write, la visualizzazione del contenuto è determinata da specifiche variabili di Runtime. L'eccezione è il metodo [System. Management. Automation. cmdlet. WriteObject](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject) . Utilizzando queste variabili, è possibile effettuare la chiamata di scrittura appropriata nella posizione corretta nel codice e non preoccuparsi di quando o se l'output deve essere visualizzato.

## <a name="accessing-the-output-functionality-of-a-host-application"></a>Accesso alla funzionalità di output di un'applicazione host

È anche possibile progettare un cmdlet per accedere direttamente alla funzionalità di output di un'applicazione host tramite il runtime di PowerShell. L'uso delle API host fornite da PowerShell invece che da [System. console](/dotnet/api/System.Console) o [System. Windows. Forms](/dotnet/api/System.Windows.Forms) garantisce che il cmdlet funzionerà con una vasta gamma di host. Ad esempio: l'host della console **PowerShell. exe** , l'host grafico **powershell_ise. exe** , l'host di comunicazione remota di PowerShell e gli host di terze parti.

## <a name="see-also"></a>Vedere anche

[Concetti relativi alla segnalazione degli errori](./error-reporting-concepts.md)

[Panoramica sui cmdlet](./cmdlet-overview.md)

[Scrittura di un cmdlet di Windows PowerShell](./writing-a-windows-powershell-cmdlet.md)