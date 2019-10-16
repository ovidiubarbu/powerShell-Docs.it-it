---
title: Panoramica sui cmdlet | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- cmdlets [PowerShell SDK]
- cmdlets [PowerShell SDK], described
ms.assetid: 0aa32589-4447-4ead-a5dd-a3be99113140
caps.latest.revision: 21
ms.openlocfilehash: 14200aed2fb94c37c8b8af29650f602945e7ac1c
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/15/2019
ms.locfileid: "72365890"
---
# <a name="cmdlet-overview"></a>Informazioni generali sui cmdlet

Un cmdlet è un comando leggero usato nell'ambiente Windows PowerShell. Il runtime di Windows PowerShell richiama questi cmdlet all'interno del contesto degli script di automazione forniti dalla riga di comando. Il runtime di Windows PowerShell li richiama anche a livello di codice tramite le API di Windows PowerShell.

## <a name="cmdlets"></a>Cmdlet

I cmdlet eseguono un'azione e in genere restituiscono un oggetto Microsoft .NET Framework al comando successivo nella pipeline. Per scrivere un cmdlet, è necessario implementare una classe di cmdlet che deriva da una delle due classi di base di cmdlet specializzate. La classe derivata deve:

- Dichiarare un attributo che identifichi la classe derivata come cmdlet.

- Definire le proprietà pubbliche che sono decorate con attributi che identificano le proprietà pubbliche come parametri dei cmdlet.

- Eseguire l'override di uno o più metodi di elaborazione dell'input per elaborare i record.

È possibile caricare l'assembly che contiene la classe direttamente usando il cmdlet [Import-Module](/powershell/module/microsoft.powershell.core/import-module) oppure è possibile creare un'applicazione host che carica l'assembly usando l'API [System. Management. Automation. Runspaces. InitialSessionState](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) . Entrambi i metodi forniscono l'accesso a livello di codice e da riga di comando alla funzionalità del cmdlet.

## <a name="cmdlet-terms"></a>Termini cmdlet

I termini seguenti vengono usati di frequente nella documentazione dei cmdlet di Windows PowerShell:

### <a name="cmdlet-attribute"></a>Attributo cmdlet

Attributo .NET Framework usato per dichiarare una classe di cmdlet come cmdlet.
Anche se PowerShell usa diversi altri attributi facoltativi, l'attributo del cmdlet è obbligatorio.
Per ulteriori informazioni su questo attributo, vedere [dichiarazione dell'attributo del cmdlet](cmdlet-attribute-declaration.md).

### <a name="cmdlet-parameter"></a>Parametro del cmdlet

Proprietà pubbliche che definiscono i parametri disponibili per l'utente o per l'applicazione che esegue il cmdlet.
I cmdlet possono avere parametri obbligatori, denominati, posizionali e *Switch* .
I parametri switch consentono di definire i parametri che vengono valutati solo se i parametri sono specificati nella chiamata.
Per ulteriori informazioni sui diversi tipi di parametri, vedere [parametri dei cmdlet](cmdlet-parameters.md).

### <a name="parameter-set"></a>Set di parametri

Gruppo di parametri utilizzabili nello stesso comando per eseguire un'azione specifica.
Un cmdlet può avere più set di parametri, ma ogni set di parametri deve avere almeno un parametro univoco.
Una progettazione di cmdlet efficace suggerisce fortemente che anche il parametro Unique sia un parametro obbligatorio.
Per ulteriori informazioni sui set di parametri, vedere [set di parametri del cmdlet](cmdlet-parameter-sets.md).

### <a name="dynamic-parameter"></a>Parametro dinamico

Parametro aggiunto al cmdlet in fase di esecuzione.
In genere, i parametri dinamici vengono aggiunti al cmdlet quando un altro parametro è impostato su un valore specifico.
Per altre informazioni sui parametri dinamici, vedere [parametri dinamici dei cmdlet](cmdlet-dynamic-parameters.md).

### <a name="input-processing-method"></a>Metodo di elaborazione dell'input

Metodo utilizzabile da un cmdlet per elaborare i record ricevuti come input.
I metodi di elaborazione dell'input includono il metodo [System. Management. Automation. cmdlet. BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) , il metodo [System. Management. Automation. cmdlet. ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) , [ System. Management. Automation. cmdlet. EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) e il metodo [System. Management. Automation. cmdlet. StopProcessing](/dotnet/api/System.Management.Automation.Cmdlet.StopProcessing) . Quando si implementa un cmdlet, è necessario eseguire l'override di almeno uno dei [System. Management. Automation. cmdlet. BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing), [System. Management. Automation. cmdlet. ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord)e [ Metodi System. Management. Automation. cmdlet. EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) .
In genere, il metodo [System. Management. Automation. cmdlet. ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) è il metodo di cui è stato eseguito l'override perché viene chiamato per ogni record elaborato dal cmdlet.
Al contrario, il metodo [System. Management. Automation. cmdlet. BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) e il metodo [System. Management. Automation. cmdlet. EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) vengono chiamati una volta per eseguire la pre-elaborazione o la post-elaborazione dei record.
Per ulteriori informazioni su questi metodi, vedere [input processing methods](cmdlet-input-processing-methods.md).

### <a name="shouldprocess-feature"></a>Funzionalità ShouldProcess

PowerShell consente di creare cmdlet che richiedono all'utente di inviare commenti e suggerimenti prima che il cmdlet modifichi il sistema.
Per usare questa funzionalità, il cmdlet deve dichiarare che supporta la funzionalità ShouldProcess quando si dichiara l'attributo del cmdlet e il cmdlet deve chiamare [System. Management. Automation. cmdlet. ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) e [ Metodi System. Management. Automation. cmdlet. ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) dall'interno di un metodo di elaborazione dell'input.
Per ulteriori informazioni su come supportare la funzionalità ShouldProcess, vedere [richiesta di conferma](requesting-confirmation-from-cmdlets.md).

### <a name="transaction"></a>Transazione

Gruppo logico di comandi considerati come una singola attività.
L'attività ha esito negativo automaticamente se un comando del gruppo ha esito negativo e l'utente ha la possibilità di accettare o rifiutare le azioni eseguite all'interno della transazione.
Per partecipare a una transazione, il cmdlet deve dichiarare che supporta le transazioni quando viene dichiarato l'attributo del cmdlet.
Il supporto per le transazioni è stato introdotto in Windows PowerShell 2,0.
Per ulteriori informazioni sulle transazioni, vedere [come supportare le transazioni](how-to-support-transactions.md).

## <a name="how-cmdlets-differ-from-commands"></a>Differenze tra i cmdlet e i comandi

I cmdlet di sono diversi da quelli di altri ambienti della shell dei comandi nei modi seguenti:

- I cmdlet sono istanze delle classi .NET Framework; non sono eseguibili autonomi.

- I cmdlet possono essere creati da un minimo di dozzine di righe di codice.

- I cmdlet in genere non eseguono l'analisi, la presentazione degli errori o la formattazione dell'output. L'analisi, la presentazione degli errori e la formattazione dell'output sono gestite dal runtime di Windows PowerShell.

- I cmdlet elaborano gli oggetti di input dalla pipeline anziché dai flussi di testo e i cmdlet di solito recapitano gli oggetti come output alla pipeline.

- I cmdlet sono orientati ai record perché elaborano un singolo oggetto alla volta.

## <a name="cmdlet-base-classes"></a>Classi base cmdlet

Windows PowerShell supporta i cmdlet derivati dalle due classi di base seguenti.

- La maggior parte dei cmdlet si basa su .NET Framework classi che derivano dalla classe di base [System. Management. Automation. cmdlet](/dotnet/api/System.Management.Automation.Cmdlet) . La derivazione da questa classe consente a un cmdlet di usare il set minimo di dipendenze nel runtime di Windows PowerShell. Questa operazione presenta due vantaggi. Il primo vantaggio è costituito dal fatto che gli oggetti cmdlet sono più piccoli ed è meno probabile che vengano modificati dal runtime di Windows PowerShell. Il secondo vantaggio è che, se necessario, è possibile creare direttamente un'istanza dell'oggetto cmdlet e richiamarla direttamente anziché richiamarla tramite il runtime di Windows PowerShell.

- I cmdlet più complessi sono basati su .NET Framework classi che derivano dalla classe di base [System. Management. Automation. PSCmdlet](/dotnet/api/System.Management.Automation.PSCmdlet) . La derivazione da questa classe offre un accesso molto maggiore al runtime di Windows PowerShell. Questo accesso consente al cmdlet di chiamare gli script, accedere ai provider e accedere allo stato della sessione corrente. Per accedere allo stato della sessione corrente, è possibile ottenere e impostare le variabili e le preferenze di sessione. Tuttavia, la derivazione da questa classe aumenta le dimensioni dell'oggetto cmdlet e significa che il cmdlet è strettamente associato alla versione corrente del runtime di Windows PowerShell.

In generale, a meno che non sia necessario l'accesso esteso al runtime di Windows PowerShell, è necessario derivare dalla classe [System. Management. Automation. cmdlet](/dotnet/api/System.Management.Automation.Cmdlet) . Tuttavia, il runtime di Windows PowerShell dispone di funzionalità di registrazione estese per l'esecuzione di cmdlet. Se il modello di controllo dipende da questa registrazione, è possibile impedire l'esecuzione del cmdlet all'interno di un altro cmdlet derivando dalla classe [System. Management. Automation. PSCmdlet](/dotnet/api/System.Management.Automation.PSCmdlet) .

## <a name="input-processing-methods"></a>Metodi di elaborazione dell'input

La classe [System. Management. Automation. cmdlet](/dotnet/api/System.Management.Automation.Cmdlet) fornisce i metodi virtuali seguenti usati per elaborare i record. Tutte le classi di cmdlet derivati devono eseguire l'override di uno o più dei primi tre metodi:

- [System. Management. Automation. cmdlet. BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing): usato per fornire una funzionalità facoltativa di pre-elaborazione monouso per il cmdlet.

- [System. Management. Automation. cmdlet. ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord): utilizzato per fornire funzionalità di elaborazione record per record per il cmdlet. Il metodo [System. Management. Automation. cmdlet. ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) può essere chiamato un numero qualsiasi di volte, o non, a seconda dell'input del cmdlet.

- [System. Management. Automation. cmdlet. EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing): usato per fornire una funzionalità facoltativa di post-elaborazione monouso per il cmdlet.

- [System. Management. Automation. cmdlet. StopProcessing](/dotnet/api/System.Management.Automation.Cmdlet.StopProcessing): usato per arrestare l'elaborazione quando l'utente arresta il cmdlet in modo asincrono, ad esempio premendo CTRL + C.

Per ulteriori informazioni su questi metodi, vedere [metodi di elaborazione dell'input del cmdlet](./cmdlet-input-processing-methods.md).

## <a name="cmdlet-attributes"></a>Attributi dei cmdlet

Windows PowerShell definisce diversi attributi .NET Framework utilizzati per gestire i cmdlet e per specificare funzionalità comuni fornite da Windows PowerShell e che potrebbero essere richieste dal cmdlet. Gli attributi, ad esempio, vengono utilizzati per definire una classe come un cmdlet, per specificare i parametri del cmdlet e per richiedere la convalida dell'input in modo che gli sviluppatori di cmdlet non debbano implementare tale funzionalità nel codice del cmdlet. Per ulteriori informazioni sugli attributi, vedere [attributi di Windows PowerShell](./cmdlet-attributes.md).

## <a name="cmdlet-names"></a>Nomi dei cmdlet

Windows PowerShell usa una coppia di nomi verbo-e-sostantivo per assegnare un nome ai cmdlet. Ad esempio, il cmdlet `Get-Command` incluso in Windows PowerShell viene usato per ottenere tutti i cmdlet registrati nella shell dei comandi. Il Verbo identifica l'azione eseguita dal cmdlet e il sostantivo identifica la risorsa su cui il cmdlet esegue l'azione.

Questi nomi vengono specificati quando la classe .NET Framework viene dichiarata come cmdlet. Per ulteriori informazioni su come dichiarare una classe .NET Framework come cmdlet, vedere Dichiarazione dell' [attributo del cmdlet](./cmdlet-class-declaration.md).

## <a name="writing-cmdlet-code"></a>Scrittura del codice del cmdlet

In questo documento vengono illustrati due modi per individuare la modalità di scrittura del codice del cmdlet. Se si preferisce visualizzare il codice senza molte spiegazioni, vedere [esempi di codice di cmdlet](./examples-of-cmdlet-code.md). Se si preferisce altre spiegazioni sul codice, vedere l'esercitazione [GetProc](./getproc-tutorial.md), l' [esercitazione StopProc](./stopproc-tutorial.md)o gli argomenti dell' [esercitazione su SelectStr](./selectstr-tutorial.md) .

Per ulteriori informazioni sulle linee guida per la scrittura di cmdlet, vedere [linee guida per lo sviluppo di cmdlet](./cmdlet-development-guidelines.md).

## <a name="see-also"></a>Vedere anche

[Concetti relativi ai cmdlet di Windows PowerShell](./windows-powershell-cmdlet-concepts.md)

[Scrittura di un cmdlet di Windows PowerShell](./writing-a-windows-powershell-cmdlet.md)

[Windows PowerShell SDK](../windows-powershell-reference.md)
