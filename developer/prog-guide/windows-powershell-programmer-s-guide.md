---
title: Programmatore di Windows PowerShell&#39;Guida s | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Windows PowerShell Programmer's Guide
ms.assetid: f3aaf667-af84-4ea8-a5ad-d454d0d700b8
caps.latest.revision: 9
ms.openlocfilehash: 75425fbd38141fc82dd834835912c357ecfa6d2b
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62081088"
---
# <a name="windows-powershell-programmer39s-guide"></a>Programmatore di Windows PowerShell&#39;Guida

Guida per programmatori, questo è rivolto agli sviluppatori che desiderano fornire un ambiente di gestione da riga di comando per gli amministratori di sistema. Windows PowerShell fornisce un modo semplice per creare i comandi di gestione che espongono gli oggetti .NET, consentendo a Windows PowerShell per eseguire la maggior parte del lavoro per l'utente.

Nello sviluppo di comando tradizionali, è necessario scrivere un parser di parametri, uno strumento di associazione di parametri, filtri e tutte le altre funzionalità esposte da ogni comando. Windows PowerShell fornisce il comando seguente per semplificare la scrittura di comandi:

- Un potente PowerShell di Windows runtime (motore di esecuzione) con il proprio parser e un meccanismo per l'associazione automatica tra i parametri di comando.

- Utilità per formattare e visualizzare i risultati del comando con un interprete della riga di comando (CLI).

- Supporto per alti livelli di funzionalità (tramite il provider di Windows PowerShell) che rendono più semplice accedere ai dati archiviati.

  Costo minimo, è possibile rappresentare un oggetto .NET da un comando complesso o un set di comandi che offrirà un'esperienza da riga di comando completa all'amministratore.

  Nella sezione successiva illustra i concetti principali di Windows PowerShell e le condizioni. Acquisire familiarità con questi concetti e termini prima di iniziare lo sviluppo.

## <a name="about-windows-powershell"></a>Informazioni su Windows PowerShell

Windows PowerShell definisce diversi tipi di comandi che è possibile usare in fase di sviluppo. Questi comandi includono: le funzioni, filtri, script, alias e file eseguibili (applicazioni). Il tipo di comando principale illustrato in questa guida è un comando semplice di piccole dimensioni denominato "cmdlet". Windows PowerShell offre un sistema di un set di cmdlet e supporta completamente la personalizzazione di cmdlet in base all'ambiente. Il runtime di Windows PowerShell elabora tutti i tipi di comandi come i cmdlet di, con le pipeline.

Oltre ai comandi, Windows PowerShell supporta diversi provider di Windows PowerShell personalizzabile che rendono disponibili insiemi di cmdlet specifici. La shell viene eseguito all'interno dell'applicazione host fornita da Windows PowerShell (Windows PowerShell.exe), ma è ugualmente accessibile da un'applicazione host personalizzato che è possibile sviluppare per soddisfare requisiti specifici. Per altre informazioni, vedere [modalità di funzionamento di Windows PowerShell](http://msdn.microsoft.com/en-us/ced30e23-10af-4700-8933-49873bd84d58).

### <a name="windows-powershell-cmdlets"></a>Cmdlet di Windows PowerShell

Un cmdlet è un comando semplice che viene usato nell'ambiente di Windows PowerShell. Il runtime di Windows PowerShell vengono richiamati i cmdlet nel contesto di script di automazione che vengono forniti alla riga di comando e il runtime di Windows PowerShell che richiama anche loro a livello di programmazione tramite Windows PowerShell APIs.

Per altre informazioni sui cmdlet, vedere [scrittura di un Cmdlet di Windows PowerShell](../cmdlet/writing-a-windows-powershell-cmdlet.md).

### <a name="windows-powershell-providers"></a>Provider di Windows PowerShell

Esecuzione delle attività amministrative, l'utente potrebbe essere necessario esaminare i dati archiviati in un archivio dati (ad esempio, nel file system, Registro di sistema di Windows o un archivio certificati). Per semplificare queste operazioni, Windows PowerShell consente di definire un modulo, denominato un provider di Windows PowerShell che può essere utilizzato per accedere a un archivio dati specifico, ad esempio il Registro di sistema di Windows. Ogni provider supporta un set di cmdlet correlati per consentire all'utente una visualizzazione dei dati nell'archivio simmetrica.

Windows PowerShell fornisce predefiniti diversi provider di Windows PowerShell. Ad esempio, il provider del Registro di sistema supporta la navigazione e modifica del Registro di sistema Windows. Le chiavi del Registro di sistema sono rappresentate come elementi e i valori del Registro di sistema vengono considerati come proprietà.

Se si espone un archivio dati che l'utente dovrà accedere, si potrebbe essere necessario scrivere il proprio provider di Windows PowerShell, come descritto in [creazione di provider di Windows PowerShell](./how-to-create-a-windows-powershell-provider.md). Per altre informazioni aboutWindows provider PowerShell, vedere [modalità di funzionamento di Windows PowerShell](http://msdn.microsoft.com/en-us/ced30e23-10af-4700-8933-49873bd84d58).

### <a name="host-application"></a>Applicazione host

Windows PowerShell include powershell.exe l'applicazione host predefinito, ovvero un'applicazione console che interagisce con l'utente e che ospita il runtime di Windows PowerShell usando una finestra della console.

Solo raramente è necessario scrivere la propria applicazione host per Windows PowerShell, anche se la personalizzazione è supportata. Un caso in cui un'applicazione personalizzata potrebbe essere necessario è quando si dispone di un requisito per un'interfaccia utente grafica che è più completa rispetto all'interfaccia fornita dall'applicazione host predefinito. Un'applicazione personalizzata è possibile anche quando si basa la relativa interfaccia grafica nella riga di comando. Per altre informazioni, vedere [come creare un'applicazione Host di Windows PowerShell](http://msdn.microsoft.com/en-us/d31355c9-a270-4b09-8f0c-35a7392a7d07).

### <a name="windows-powershell-runtime"></a>Runtime di Windows PowerShell

Il runtime di Windows PowerShell è il motore di esecuzione che implementa l'elaborazione del comando. Include le classi che forniscono l'interfaccia tra l'applicazione host e i comandi di Windows PowerShell e i provider. Il runtime di Windows PowerShell viene implementato come un oggetto dello spazio di esecuzione per la sessione di Windows PowerShell corrente, ovvero l'ambiente operativo in cui eseguire la shell e i comandi. Per i dettagli operativi, vedere [modalità di funzionamento di Windows PowerShell](http://msdn.microsoft.com/en-us/ced30e23-10af-4700-8933-49873bd84d58).

### <a name="windows-powershell-language"></a>Windows PowerShell Language

Il linguaggio di Windows PowerShell fornisce funzioni di scripting e un meccanismo per richiamare i comandi. Per informazioni sugli script completate, vedere che il riferimento al linguaggio di Windows PowerShell forniti con Windows PowerShell.

### <a name="extended-type-system-ets"></a>Sistema di tipi estesi (ETS)

Windows PowerShell fornisce l'accesso a una varietà di oggetti diversi, ad esempio .NET e gli oggetti XML. Di conseguenza, per presentare un'astrazione comune per tutti i tipi di oggetto shell utilizza un sistema di tipo esteso (ETS). La maggior parte delle funzionalità ETS è trasparente all'utente, ma lo script o per gli sviluppatori .NET lo usa per gli scopi seguenti:

- Visualizzazione di un sottoinsieme dei membri di oggetti specifici. Windows PowerShell fornisce una visualizzazione "adattata" per diversi tipi di oggetto specifico.

- Aggiunta di membri per gli oggetti esistenti.

- L'accesso a oggetti serializzati.

- Scrittura di oggetti personalizzati.

  Usa ETS, è possibile creare nuovi flessibili "tipi" che sono compatibili con il linguaggio di Windows PowerShell. Se sei uno sviluppatore .NET, si è in grado di utilizzare gli oggetti usando la stessa semantica come linguaggio di Windows PowerShell si applica alla creazione di script, ad esempio, per determinare se un oggetto viene valutato `true`.

  Per altre informazioni su ETS e come Windows PowerShell Usa gli oggetti, vedere [concetti di oggetti di Windows PowerShell](http://msdn.microsoft.com/en-us/12700631-be23-4e6b-9bf0-81ea0d166353).

## <a name="programming-for-windows-powershell"></a>Programmazione per Windows PowerShell

Windows PowerShell consente di definire il relativo codice per i comandi, provider e altri moduli di programma utilizzando .NET Framework. Non sono limitati all'utilizzo di Microsoft Visual Studio per la creazione di moduli personalizzati per Windows PowerShell, anche se gli esempi forniti in questa guida sono noti per l'esecuzione di questo strumento. È possibile usare qualsiasi linguaggio .NET che supporta l'ereditarietà di classe e l'utilizzo di attributi. In alcuni casi, Windows PowerShell APIs richiedono il linguaggio di programmazione sia in grado di accedere a tipi generici.

## <a name="programmers-reference"></a>Riferimento per programmatori

Come riferimento durante lo sviluppo per Windows PowerShell, vedere la [Windows PowerShell SDK](../windows-powershell-reference.md).

## <a name="getting-started-using-windows-powershell"></a>Introduzione all'uso di Windows PowerShell

Per altre informazioni su come iniziare a usare la shell di Windows PowerShell, vedere la [Introduzione a Windows PowerShell](/powershell/scripting/getting-started/getting-started-with-windows-powershell) forniti con Windows PowerShell. Nozioni di base per l'utilizzo di cmdlet viene fornito anche un documento di riferimento rapido in tre parti.

## <a name="contents-of-this-guide"></a>Contenuto della Guida

|Argomento|Definizione|
|-----------|----------------|
|[Come creare un Provider di Windows PowerShell](./how-to-create-a-windows-powershell-provider.md)|Questa sezione descrive come creare un provider di Windows PowerShell per Windows PowerShell.|
|[Come creare un'applicazione Host di PowerShell di Windows](http://msdn.microsoft.com/en-us/d31355c9-a270-4b09-8f0c-35a7392a7d07)|In questa sezione viene descritto come scrivere un'applicazione host che consente di modificare uno spazio di esecuzione e come scrivere un'applicazione host che implementa il proprio host personalizzato.|
|[Come creare uno Snap-in PowerShell di Windows](../cmdlet/how-to-create-a-windows-powershell-snap-in.md)|Questa sezione descrive come creare uno snap-in che consente di registrare tutti i cmdlet e provider in un assembly e come creare uno snap-in personalizzati.|
|[Come creare una Shell di Console](./how-to-create-a-console-shell.md)|Questa sezione descrive come creare una shell di console che non è estendibile.|
|[Concetti di Windows PowerShell](./windows-powershell-concepts.md)|In questa sezione contiene informazioni concettuali che consentiranno di comprendere Windows PowerShell dal punto di vista di uno sviluppatore.|

## <a name="see-also"></a>Vedere anche

[Windows PowerShell SDK](../windows-powershell-reference.md)
