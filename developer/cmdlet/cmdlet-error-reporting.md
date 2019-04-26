---
title: La funzionalità di segnalazione degli errori dei cmdlet | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- error records [PowerShell], terminating
- non-terminating errors [PowerShell]
- error records [PowerShell]
- terminating errors [PowerShell]
- error records [PowerShell], non-terminating
ms.assetid: 0b014035-52ea-44cb-ab38-bbe463c5465a
caps.latest.revision: 8
ms.openlocfilehash: 45f5934314a2871ceb921c7a66b9dfb658d0bd99
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62068590"
---
# <a name="cmdlet-error-reporting"></a>Segnalazione di errori dei cmdlet

I cmdlet dovrebbero segnalare gli errori in modo diverso a seconda del fatto che gli errori sono irreversibili o errori non fatali. Gli errori sono errori che causano la pipeline a essere terminata immediatamente o errori che si verificano quando non c'è nessun motivo per continuare l'elaborazione. Errori non fatali sono gli errori che segnalano una condizione di errore corrente, ma il cmdlet può continuare a elaborare gli oggetti di input. Con errori non fatali, in genere l'utente viene notificato il problema, ma il cmdlet continua a elaborare l'oggetto di input successivo.

## <a name="terminating-and-nonterminating-errors"></a>Errori non fatali e terminazione

Le linee guida seguenti sono utilizzabile per determinare se una condizione di errore è un errore o un errore non fatali.

- La condizione di errore impedisce il cmdlet correttamente l'elaborazione degli oggetti di input ulteriormente? In questo caso, si tratta di un errore irreversibile.

- La condizione di errore è correlata a un oggetto di input specifico o un subset di oggetti di input? In questo caso, si tratta di un errore non fatali.

- Il cmdlet accetta più oggetti di input, ad esempio che l'elaborazione potrebbe avere esito positivo su un altro oggetto di input? In questo caso, si tratta di un errore non fatali.

- I cmdlet che possono accettare più oggetti di input devono decidere tra ciò che rappresenta l'ultima e gli errori non fatali, anche quando una determinata situazione si applica a un singolo oggetto di input.

- I cmdlet possono ricevere un numero qualsiasi di oggetti di input e inviare un numero qualsiasi di oggetti di esito positivo o errore prima che venga generata un'eccezione di terminazione. Non c'è alcuna relazione tra il numero di oggetti di input ricevuti e il numero di oggetti di esito positivo e negativo inviati.

- I cmdlet che possono accettare solo 0 e 1 gli oggetti di input e generare solo 0-1 output oggetti devono considerare gli errori come gli errori irreversibili e generare eccezioni di terminazione.

## <a name="reporting-nonterminating-errors"></a>Segnalazione di errori non fatali

La segnalazione di un errore non fatali deve sempre essere eseguita all'interno di implementazione del cmdlet del [System.Management.Automation.Cmdlet.BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) metodo, il [ System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) metodo, o il [System.Management.Automation.Cmdlet.EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) (metodo). Questi tipi di errori vengono segnalati tramite la chiamata di [System.Management.Automation.Cmdlet.WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) metodo che a sua volta invia un record di errore nel flusso di errori.

## <a name="reporting-terminating-errors"></a>Segnalazione di errori di terminazione

Gli errori vengono segnalati mediante la generazione di eccezioni o chiamando il [System.Management.Automation.Cmdlet.Throwterminatingerror*](/dotnet/api/System.Management.Automation.Cmdlet.ThrowTerminatingError) (metodo). Tenere presente che i cmdlet possono inoltre rilevare e generare nuovamente le eccezioni, ad esempio OutOfMemory, tuttavia, che non sono necessari per generare nuovamente le eccezioni come il runtime di Windows PowerShell li rileverà anche.

È anche possibile definire eccezioni personalizzate per i problemi specifici alla propria situazione, o aggiungere ulteriori informazioni su un'eccezione esistente tramite il relativo record di errore.

## <a name="error-records"></a>Record degli errori

Windows PowerShell descrive una condizione di errore non fatali tramite l'uso di [System.Management.Automation.ErrorRecord](/dotnet/api/System.Management.Automation.ErrorRecord) oggetti. Ciascuna [System.Management.Automation.ErrorRecord](/dotnet/api/System.Management.Automation.ErrorRecord) oggetto fornisce le informazioni sulle categorie di errore, un oggetto di destinazione facoltativo e dettagli sulla condizione di errore.

### <a name="error-identifiers"></a>Identificatori degli errori

Identificatore dell'errore è una semplice stringa che identifica la condizione di errore all'interno di cmdlet. Windows PowerShell combina questo identificatore con un identificatore di cmdlet per creare un identificatore di errore completo che può essere utilizzato in un secondo momento, quando si filtrano i flussi di errore o la registrazione errori, quando si risponde a errori specifici o con altre attività specifiche dell'utente.

Le seguenti linee guida da seguire quando si specificano gli identificatori degli errori.

- Assegnare gli identificatori di errore diversi, estremamente specifici, ai percorsi del codice diversi. Ogni percorso di codice che chiama [System.Management.Automation.Cmdlet.WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) oppure [System.Management.Automation.Cmdlet.Throwterminatingerror*](/dotnet/api/System.Management.Automation.Cmdlet.ThrowTerminatingError) deve avere un proprio identificatore dell'errore.

- Gli identificatori degli errori deve essere univoci a tipi di eccezione CLR per errori sia irreversibili che non fatali.

- Non modificare la semantica di un identificatore di errore tra le versioni del cmdlet o del provider di Windows PowerShell. Dopo aver stabilita la semantica di un identificatore di errore, dovrebbero rimanere costante durante il ciclo di vita del cmdlet.

- Per gli errori irreversibili, usare un identificatore univoco di errore per un particolare tipo di eccezione CLR. Se viene modificato il tipo di eccezione, usare un nuovo identificatore di errore.

- Per gli errori non fatali, usare un identificatore di errore specifico per un oggetto di input specifico.

- Scegliere il testo per l'identificatore che fornisce risposte superficiali corrispondente all'errore segnalato. Non usare spazi vuoti o punteggiatura.

- Non generare identificatori errori non riproducibili. Ad esempio, non generano gli identificatori che includono un identificatore di processo. Gli identificatori di errore sono utili solo se corrispondono agli identificatori visualizzate da altri utenti a cui vengono riscontrato il problema stesso.

### <a name="error-categories"></a>Categorie di errore

Categorie di errore vengono utilizzate per raggruppare gli errori per l'utente finale. Windows PowerShell consente di definire queste categorie e i cmdlet e provider Windows PowerShell deve scegliere tra di essi durante la generazione di record error.

Per una descrizione delle categorie di errore che sono disponibili, vedere la [System.Management.Automation.Errorcategory](/dotnet/api/System.Management.Automation.ErrorCategory) enumerazione. In generale, è consigliabile non utilizzare NoError UndefinedError e errore generico quando possibile.

Gli utenti possono visualizzare gli errori in base alla categoria durante l'impostazione "`$ErrorView`" a "CategoryView".

## <a name="see-also"></a>Vedere anche

[Cmdlet di Windows PowerShell](./cmdlet-overview.md)

[Output del cmdlet](./types-of-cmdlet-output.md)

[Windows PowerShell Shell SDK](../windows-powershell-reference.md)
