---
title: Panoramica su cmdlet | Microsoft Docs
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
ms.openlocfilehash: a53b1ada46ad614af3522e6cc11e187afb76e7b1
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/03/2019
ms.locfileid: "56855317"
---
# <a name="cmdlet-overview"></a>Informazioni generali sui cmdlet

Un cmdlet è un comando semplice che viene usato nell'ambiente di Windows PowerShell. Il runtime di Windows PowerShell richiama questi cmdlet nel contesto di script di automazione che vengono forniti alla riga di comando. Il runtime di Windows PowerShell che richiama anche loro a livello di codice tramite Windows PowerShell APIs.

## <a name="cmdlets"></a>Cmdlet

I cmdlet di eseguono un'azione e restituiscono in genere un oggetto Microsoft .NET Framework per il comando successivo nella pipeline. Per scrivere un cmdlet, è necessario implementare una classe di cmdlet che deriva da una delle due classi di base di un cmdlet specifico. La classe derivata deve:

- Dichiarare un attributo che identifica la classe derivata come cmdlet.

- Definire le proprietà pubbliche che vengono decorate con gli attributi che identificano le proprietà pubbliche come parametri del cmdlet.

- Eseguire l'override di uno o più i metodi di elaborazione dei record di elaborazione dell'input.

È possibile caricare l'assembly che contiene la classe direttamente tramite il [Import-Module](/powershell/module/microsoft.powershell.core/import-module) cmdlet oppure è possibile creare un'applicazione host che carica l'assembly utilizzando il [ System.Management.Automation.Runspaces.Initialsessionstate](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) API. Entrambi i metodi forniscono accesso a livello di codice e della riga di comando per la funzionalità del cmdlet.

## <a name="cmdlet-terms"></a>Condizioni di cmdlet

I termini seguenti vengono usati frequentemente nella documentazione di cmdlet di Windows PowerShell:

- **Attributo cmdlet**: Un attributo di .NET Framework che viene usato per dichiarare una classe cmdlet come un cmdlet. Anche se Windows PowerShell Usa diversi altri attributi che sono facoltativi, è richiesto l'attributo Cmdlet. Per altre informazioni su questo attributo, vedere [dichiarazione di attributo Cmdlet](./cmdlet-attribute-declaration.md).

- **Parametro del cmdlet**: Le proprietà pubbliche che definiscono i parametri disponibili all'utente o all'applicazione che esegue il cmdlet. Sono necessari i cmdlet, denominata, posizionali, e *commutatore* parametri. Parametri opzionali consentono di definire i parametri che vengono valutati solo se vengono specificati i parametri nella chiamata. Per altre informazioni sui diversi tipi di parametri, vedere [parametri del Cmdlet](./cmdlet-parameters.md).

- **Set di parametri**: Gruppo di parametri utilizzabili nello stesso comando per eseguire un'azione specifica. Un cmdlet può avere più set di parametri, ma ogni set di parametri deve avere almeno un parametro che è univoco. Progettazione dei cmdlet buona fortemente ne consegue che il parametro unique anche un parametro obbligatorio. Per altre informazioni sui set di parametri, vedere [imposta parametro di Cmdlet](./cmdlet-parameter-sets.md).

- **Parametro dinamico**: Un parametro che viene aggiunto al cmdlet in fase di esecuzione. In genere, i parametri dinamici vengono aggiunti al cmdlet quando un altro parametro è impostato su un valore specifico. Per altre informazioni sui parametri dinamici, vedere [Cmdlet i parametri dinamici](./cmdlet-dynamic-parameters.md).

- **Metodo di elaborazione di input**: Metodo utilizzabile da un cmdlet per elaborare i record ricevuti come input. I metodi di elaborazione dell'input includono la [System.Management.Automation.Cmdlet.Beginprocessing*](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) metodo, il [System.Management.Automation.Cmdlet.Processrecord*](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) metodo, il [System.Management.Automation.Cmdlet.Endprocessing*](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) metodo e il [System.Management.Automation.Cmdlet.Stopprocessing*](/dotnet/api/System.Management.Automation.Cmdlet.StopProcessing) (metodo). Quando si implementa un cmdlet, è necessario eseguire l'override di almeno il [System.Management.Automation.Cmdlet.Beginprocessing*](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing), [System.Management.Automation.Cmdlet.Processrecord*](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord)e [ System.Management.Automation.Cmdlet.Endprocessing*](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) metodi. In genere, il [System.Management.Automation.Cmdlet.Processrecord*](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) è il metodo che si esegue l'override perché viene chiamato per ogni record elaborati dal cmdlet. Al contrario, il [System.Management.Automation.Cmdlet.Beginprocessing*](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) metodo e il [System.Management.Automation.Cmdlet.Endprocessing*](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) metodo viene chiamato una volta per eseguire pre-elaborazione o post-elaborazione dei record. Per altre informazioni su questi metodi, vedere [metodi di elaborazione di Input](./cmdlet-input-processing-methods.md).

- **Funzionalità di ShouldProcess**: Windows PowerShell consente di creare i cmdlet che richiede all'utente per commenti e suggerimenti prima che il cmdlet apporta una modifica al sistema. Per usare questa funzionalità, il cmdlet deve dichiarare che supporta la funzionalità di ShouldProcess quando si dichiara l'attributo Cmdlet e deve chiamare il cmdlet di [System.Management.Automation.Cmdlet.Shouldprocess*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) e [ System.Management.Automation.Cmdlet.Shouldcontinue*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) metodi all'interno di un metodo di elaborazione dell'input. Per altre informazioni su come supportare la funzionalità di ShouldProcess, vedere [richiesta di conferma](./requesting-confirmation-from-cmdlets.md).

- **Transazione**: Un gruppo logico di comandi che vengono considerati come una singola attività. L'attività viene eseguito automaticamente se un comando nel gruppo non riesce e l'utente può scegliere di accettare o rifiutare le azioni eseguite all'interno della transazione. Per partecipare a una transazione, il cmdlet deve dichiarare che supporta le transazioni quando viene dichiarato l'attributo Cmdlet. Supporto delle transazioni è stato introdotto in Windows PowerShell 2.0. Per altre informazioni sulle transazioni, vedere [Windows PowerShell transazioni](http://msdn.microsoft.com/en-us/74d7bac7-bc53-49f1-a47a-272e8da84710).

## <a name="how-cmdlets-differ-from-commands"></a>Le differenze tra i cmdlet e comandi

I cmdlet si differenziano dai comandi in altri ambienti shell dei comandi nei modi seguenti:

- I cmdlet sono istanze di classi .NET Framework. non sono file eseguibili autonomi.

- I cmdlet possono essere creati da soli decine di righe di codice.

- I cmdlet di non eseguire a livello generale le proprie analisi, presentazione di errore o la formattazione di output. L'analisi, presentazione di errore e la formattazione di output vengono gestiti dal runtime di Windows PowerShell.

- I cmdlet processo oggetti dalla pipeline anziché dai flussi di testo di input e i cmdlet di offrono in genere gli oggetti come output alla pipeline.

- I cmdlet sono orientati ai record poiché elaborano un solo oggetto alla volta.

## <a name="cmdlet-base-classes"></a>Classi di Base cmdlet

Windows PowerShell supporta i cmdlet che derivano da due classi base seguenti.

- La maggior parte dei cmdlet sono basati sulle classi di .NET Framework da cui deriva il [System.Management.Automation.Cmdlet](/dotnet/api/System.Management.Automation.Cmdlet) classe di base. Derivazione da questa classe consente a un cmdlet per usare il set minimo di dipendenze nel runtime di Windows PowerShell. Ciò comporta due vantaggi. Il primo vantaggio è che gli oggetti cmdlet sono più piccoli e hanno meno probabilità di essere interessati dalle modifiche al runtime di Windows PowerShell. Il secondo vantaggio è che, se è necessario, è possibile creare direttamente un'istanza dell'oggetto cmdlet e quindi richiamarlo direttamente invece che richiamarlo tramite il runtime di Windows PowerShell.

- I cmdlet più complessi sono basati sulle classi di .NET Framework da cui deriva il [System.Management.Automation.Pscmdlet](/dotnet/api/System.Management.Automation.PSCmdlet) classe di base. Derivazione da questa classe fornisce un accesso molto più al runtime di Windows PowerShell. Questo accesso consente i cmdlet di chiamare gli script, per accedere ai provider e per accedere allo stato sessione corrente. (Per visualizzare lo stato della sessione corrente, ottenere e impostare le variabili di sessione e le preferenze.) Tuttavia, che deriva da questa classe aumenta le dimensioni dell'oggetto cmdlet e significa che il cmdlet è più strettamente alla versione corrente del runtime di Windows PowerShell.

In generale, a meno che non è necessario l'accesso esteso al runtime di Windows PowerShell, è necessario derivare il [System.Management.Automation.Cmdlet](/dotnet/api/System.Management.Automation.Cmdlet) classe. Tuttavia, il runtime di Windows PowerShell ha funzionalità di registrazione estese per l'esecuzione dei cmdlet. Se il modello di controllo dipende da questa registrazione, è possibile impedire l'esecuzione del cmdlet all'interno di un altro cmdlet derivando dal [System.Management.Automation.Pscmdlet](/dotnet/api/System.Management.Automation.PSCmdlet) classe.

## <a name="input-processing-methods"></a>I metodi di elaborazione dell'input

Il [System.Management.Automation.Cmdlet](/dotnet/api/System.Management.Automation.Cmdlet) classe fornisce i seguenti metodi virtuali che vengono utilizzati per elaborare i record. Tutte le classi di cmdlet derivate devono eseguire l'override di uno o più dei primi tre metodi:

- [System.Management.Automation.Cmdlet.Beginprocessing*](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing): Utilizzato per fornire funzionalità facoltativa unica di pre-elaborazione per il cmdlet.

- [System.Management.Automation.Cmdlet.Processrecord*](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord): Utilizzato per fornire funzionalità di elaborazione record per record per il cmdlet. Il [System.Management.Automation.Cmdlet.Processrecord*](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) metodo potrebbe essere chiamato qualsiasi numero di volte o non è affatto, in base all'input del cmdlet.

- [System.Management.Automation.Cmdlet.Endprocessing*](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing): Utilizzato per fornire funzionalità facoltativa unica di post-elaborazione per il cmdlet.

- [System.Management.Automation.Cmdlet.Stopprocessing*](/dotnet/api/System.Management.Automation.Cmdlet.StopProcessing): Consente di arrestare l'elaborazione quando l'utente interrompe il cmdlet in modo asincrono (ad esempio, premendo CTRL + C).

Per altre informazioni su questi metodi, vedere [metodi di elaborazione di Cmdlet Input](./cmdlet-input-processing-methods.md).

## <a name="cmdlet-attributes"></a>Attributi dei cmdlet

Windows PowerShell consente di definire diversi attributi .NET Framework che vengono usati per gestire i cmdlet e per specificare le funzionalità comuni che viene fornito da Windows PowerShell e che possono essere necessarie dal cmdlet. Ad esempio, gli attributi vengono utilizzati per definire una classe come un cmdlet, per specificare i parametri del cmdlet e per richiedere la convalida dell'input in modo che gli sviluppatori di cmdlet non sono necessario implementare questa funzionalità nel proprio codice di cmdlet. Per altre informazioni sugli attributi, vedere [attributi di Windows PowerShell](./cmdlet-attributes.md).

## <a name="cmdlet-names"></a>Nomi dei cmdlet

Windows PowerShell Usa una coppia di verbo e sostantivo nome ai cmdlet di nome. Ad esempio, il `Get-Command` cmdlet incluso in Windows PowerShell viene usato per ottenere tutti i cmdlet che vengono registrati nella shell dei comandi. Il verbo identifica l'azione eseguita dal cmdlet e il sostantivo identifica la risorsa in cui il cmdlet esegue l'azione corrispondente.

Questi nomi vengono specificati quando la classe di .NET Framework è dichiarata come un cmdlet. Per altre informazioni su come dichiarare una classe .NET Framework come cmdlet, vedere [dichiarazione di attributo Cmdlet](./cmdlet-class-declaration.md).

## <a name="writing-cmdlet-code"></a>Scrittura di codice di Cmdlet

Questo documento offre due modi per individuare modalità di scrittura codice del cmdlet. Se si preferisce vedere il codice senza molte spiegazioni, vedere [esempi di codice del Cmdlet](./examples-of-cmdlet-code.md). Se si preferisce una spiegazione più approfondita sul codice, vedere la [esercitazione GetProc](./getproc-tutorial.md), [esercitazione StopProc](./stopproc-tutorial.md), o [SelectStr esercitazione](./selectstr-tutorial.md) argomenti.

Per altre informazioni sulle linee guida per la scrittura di cmdlet, vedere [linee guida sullo sviluppo di Cmdlet](./cmdlet-development-guidelines.md).

## <a name="see-also"></a>Vedere anche

[Concetti di Cmdlet di PowerShell di Windows](./windows-powershell-cmdlet-concepts.md)

[Scrittura di un cmdlet di Windows PowerShell](./writing-a-windows-powershell-cmdlet.md)

[Windows PowerShell SDK](../windows-powershell-reference.md)
