---
title: Segnalazione errori cmdlet | Microsoft Docs
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
ms.openlocfilehash: 5dfec318438ca139518c596011ac5e56445738ea
ms.sourcegitcommit: 5a004064f33acc0145ccd414535763e95f998c89
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/23/2019
ms.locfileid: "69986325"
---
# <a name="cmdlet-error-reporting"></a>Segnalazione errori cmdlet

I cmdlet dovrebbero segnalare errori in modo diverso a seconda che gli errori interrompano errori o errori non fatali. Gli errori di terminazione sono errori che causano la terminazione immediata della pipeline o errori che si verificano quando non è necessario continuare l'elaborazione. Gli errori che non terminano sono gli errori che segnalano una condizione di errore corrente, ma il cmdlet può continuare a elaborare gli oggetti di input. Con gli errori non fatali, l'utente viene in genere notificato al problema, ma il cmdlet continua a elaborare l'oggetto di input successivo.

## <a name="terminating-and-nonterminating-errors"></a>Errori di terminazione e non fatale

Le linee guida seguenti possono essere utilizzate per determinare se una condizione di errore è un errore di terminazione o un errore non fatale.

- La condizione di errore impedisce al cmdlet di elaborare correttamente altri oggetti di input? In caso affermativo, si tratta di un errore fatale.

- Condizione di errore correlata a un oggetto di input specifico o a un subset di oggetti di input. In caso affermativo, si tratta di un errore non fatale.

- Il cmdlet accetta più oggetti di input, in modo che l'elaborazione possa avere esito positivo su un altro oggetto di input? In caso affermativo, si tratta di un errore non fatale.

- I cmdlet che possono accettare più oggetti di input devono decidere tra gli errori fatali e non fatali, anche quando una particolare situazione si applica solo a un singolo oggetto di input.

- I cmdlet possono ricevere un numero qualsiasi di oggetti di input e inviare un numero qualsiasi di oggetti Success o Error prima di generare un'eccezione di terminazione. Non esiste alcuna relazione tra il numero di oggetti di input ricevuti e il numero di oggetti Success e Error inviati.

- I cmdlet che accettano solo oggetti di input 0-1 e generano solo 0-1 oggetti di output devono considerare gli errori come errori di terminazione e generare eccezioni di terminazione.

## <a name="reporting-nonterminating-errors"></a>Segnalazione di errori non fatali

La creazione di report di un errore non fatale dovrebbe essere sempre eseguita nell'implementazione del cmdlet del metodo [System. Management. Automation. cmdlet. BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) , il metodo [System. Management. Automation. cmdlet. ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) o metodo [System. Management. Automation. cmdlet. EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) . Questi tipi di errori vengono segnalati chiamando il metodo [System. Management. Automation. cmdlet. WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) che a sua volta invia un record di errore al flusso di errore.

## <a name="reporting-terminating-errors"></a>Segnalazione degli errori di terminazione

Gli errori di terminazione vengono segnalati generando eccezioni oppure chiamando il metodo [System. Management. Automation. cmdlet. ThrowTerminatingError](/dotnet/api/System.Management.Automation.Cmdlet.ThrowTerminatingError) . Tenere presente che i cmdlet possono anche intercettare e rigenerare eccezioni, ad esempio **OutOfMemory**, ma non sono necessarie per rigenerare le eccezioni perché il runtime di PowerShell li rileverà.

È anche possibile definire eccezioni personalizzate per i problemi specifici della situazione o aggiungere informazioni aggiuntive a un'eccezione esistente usando il relativo record di errore.

## <a name="error-records"></a>Record degli errori

PowerShell descrive una condizione di errore non fatale con gli oggetti [System. Management. Automation. ErrorRecord](/dotnet/api/System.Management.Automation.ErrorRecord) . Ogni oggetto fornisce informazioni sulla categoria di errore, un oggetto di destinazione facoltativo e informazioni dettagliate sulla condizione di errore.

### <a name="error-identifiers"></a>Identificatori di errore

L'identificatore di errore è una stringa semplice che identifica la condizione di errore nel cmdlet.
PowerShell combina questo identificatore con un identificatore di cmdlet per creare un identificatore di errore completo che può essere usato in un secondo momento durante il filtraggio dei flussi di errore o la registrazione degli errori, quando risponde a errori specifici o con altre attività specifiche dell'utente.

Quando si specificano gli identificatori di errore, è necessario attenersi alle linee guida seguenti:

- Assegnare identificatori di errore diversi, altamente specifici, a percorsi di codice diversi. Ogni percorso di codice che chiama [System. Management. Automation. cmdlet. WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) o [System. Management. Automation. cmdlet. ThrowTerminatingError](/dotnet/api/System.Management.Automation.Cmdlet.ThrowTerminatingError) deve avere un identificatore di errore proprio.

- Gli identificatori di errore devono essere univoci per i tipi di eccezione CLR (Common Language Runtime) per gli errori di terminazione e non fatale.

- Non modificare la semantica di un identificatore errore tra le versioni del cmdlet o del provider PowerShell. Una volta stabilita la semantica di un identificatore di errore, deve rimanere costante per tutto il ciclo di vita del cmdlet.

- Per gli errori di terminazione, utilizzare un identificatore di errore univoco per un particolare tipo di eccezione CLR. Se il tipo di eccezione cambia, utilizzare un nuovo identificatore di errore.

- Per gli errori non fatali, usare un identificatore di errore specifico per un oggetto di input specifico.

- Scegliere il testo per l'identificatore che laconicamente corrisponde all'errore segnalato. Non usare spazi vuoti o segni di punteggiatura.

- Non generare identificatori di errore non riproducibili. Ad esempio, non generare identificatori che includono un identificatore di processo. Gli identificatori di errore sono utili solo quando corrispondono agli identificatori visualizzati da altri utenti che hanno riscontrato lo stesso problema.

### <a name="error-categories"></a>Categorie di errore

Le categorie di errore vengono utilizzate per raggruppare gli errori dell'utente. PowerShell definisce queste categorie e i cmdlet e i provider PowerShell devono scegliere tra di essi quando generano il record di errore.

Per una descrizione delle categorie di errore disponibili, vedere l'enumerazione [System. Management. Automation. ErrorCategory](/dotnet/api/System.Management.Automation.ErrorCategory) . In generale, è consigliabile evitare diusare NOERROR, **UndefinedError**e **errore generico** quando possibile.

Gli utenti possono visualizzare gli errori in base alla categoria `$ErrorView` quando sono impostati su **CategoryView**.

## <a name="see-also"></a>Vedere anche

[Panoramica sui cmdlet](./cmdlet-overview.md)

[Tipi di output del cmdlet](./types-of-cmdlet-output.md)

[Windows PowerShell Reference](../windows-powershell-reference.md) (Guida di riferimento di PowerShell)
