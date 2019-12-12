---
title: Guida per programmatori&#39;di Windows PowerShell | Microsoft Docs
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
ms.openlocfilehash: f8cbaf464345b8f2b693e72f3dbe781a47605b28
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/05/2019
ms.locfileid: "74417781"
---
# <a name="windows-powershell-programmer39s-guide"></a>Guida per programmatori&#39;di Windows PowerShell

Questa guida per i programmatori è destinata agli sviluppatori interessati a fornire un ambiente di gestione da riga di comando per gli amministratori di sistema. Windows PowerShell fornisce un modo semplice per creare comandi di gestione che espongono oggetti .NET, consentendo allo stesso tempo a Windows PowerShell di eseguire la maggior parte delle operazioni.

Nello sviluppo di comandi tradizionale, è necessario scrivere un parser di parametri, uno strumento di associazione di parametri, filtri e tutte le altre funzionalità esposte da ogni comando. Windows PowerShell offre le funzionalità seguenti per semplificare la scrittura dei comandi:

- Un potente runtime di Windows PowerShell (motore di esecuzione) con il proprio parser e un meccanismo per l'associazione automatica dei parametri di comando.

- Utilità per la formattazione e la visualizzazione dei risultati del comando mediante un interprete della riga di comando (CLI).

- Supporto per livelli elevati di funzionalità (tramite i provider di Windows PowerShell) che facilitano l'accesso ai dati archiviati.

  A un costo ridotto, è possibile rappresentare un oggetto .NET tramite un comando o un set di comandi avanzati che offrirà all'amministratore un'esperienza completa da riga di comando.

  La sezione successiva illustra i concetti e i termini principali di Windows PowerShell. Prima di iniziare lo sviluppo, acquisire familiarità con questi concetti e termini.

## <a name="about-windows-powershell"></a>Informazioni su Windows PowerShell

Windows PowerShell definisce diversi tipi di comandi che è possibile usare in fase di sviluppo. Questi comandi includono funzioni, filtri, script, alias ed eseguibili (applicazioni). Il tipo di comando principale illustrato in questa guida è un semplice e piccolo comando denominato "cmdlet". Windows PowerShell fornisce un set di cmdlet e supporta completamente la personalizzazione dei cmdlet per adattarla all'ambiente in uso. Il runtime di Windows PowerShell elabora tutti i tipi di comando Analogamente ai cmdlet, usando le pipeline.

Oltre ai comandi, Windows PowerShell supporta diversi provider di Windows PowerShell personalizzabili che rendono disponibili set di cmdlet specifici. La shell funziona all'interno dell'applicazione host fornita da Windows PowerShell (Windows PowerShell. exe), ma è ugualmente accessibile da un'applicazione host personalizzata che è possibile sviluppare per soddisfare requisiti specifici. Per ulteriori informazioni, vedere funzionamento di [Windows PowerShell](/previous-versions//ms714658(v=vs.85)).

### <a name="windows-powershell-cmdlets"></a>Cmdlet Windows PowerShell

Un cmdlet è un comando leggero usato nell'ambiente Windows PowerShell. Il runtime di Windows PowerShell richiama questi cmdlet all'interno del contesto degli script di automazione forniti dalla riga di comando e il runtime di Windows PowerShell li richiama anche a livello di codice tramite le API di Windows PowerShell.

Per ulteriori informazioni sui cmdlet, vedere [scrittura di un cmdlet di Windows PowerShell](../cmdlet/writing-a-windows-powershell-cmdlet.md).

### <a name="windows-powershell-providers"></a>Provider di Windows PowerShell

Durante l'esecuzione di attività amministrative, l'utente potrebbe dover esaminare i dati archiviati in un archivio dati, ad esempio il file system, il registro di sistema di Windows o un archivio certificati. Per semplificare queste operazioni, Windows PowerShell definisce un modulo denominato provider di Windows PowerShell che può essere usato per accedere a un archivio dati specifico, ad esempio il registro di sistema di Windows. Ogni provider supporta un set di cmdlet correlati per fornire all'utente una visualizzazione simmetrica dei dati nell'archivio.

Windows PowerShell offre diversi provider predefiniti di Windows PowerShell. Il provider del registro di sistema, ad esempio, supporta la navigazione e la manipolazione del registro di sistema di Windows. Le chiavi del registro di sistema sono rappresentate come elementi e i valori del registro di sistema vengono considerati come proprietà.

Se si espone un archivio dati a cui l'utente deve accedere, potrebbe essere necessario scrivere un provider di Windows PowerShell personalizzato, come descritto in [creazione di provider di Windows PowerShell](./how-to-create-a-windows-powershell-provider.md). Per ulteriori informazioni sui provider aboutWindows PowerShell, vedere funzionamento di [Windows PowerShell](/previous-versions//ms714658(v=vs.85)).

### <a name="host-application"></a>Applicazione host

Windows PowerShell include l'applicazione host predefinita PowerShell. exe, che è un'applicazione console che interagisce con l'utente e ospita il runtime di Windows PowerShell usando una finestra della console.

Solo raramente è necessario scrivere una propria applicazione host per Windows PowerShell, anche se è supportata la personalizzazione. Un caso in cui potrebbe essere necessaria un'applicazione personalizzata è quando si ha un requisito per un'interfaccia GUI più ricca rispetto all'interfaccia fornita dall'applicazione host predefinita. È anche possibile che si desideri un'applicazione personalizzata quando si basa la GUI nella riga di comando. Per ulteriori informazioni, vedere [come creare un'applicazione host di Windows PowerShell](/powershell/scripting/developer/hosting/writing-a-windows-powershell-host-application).

### <a name="windows-powershell-runtime"></a>Runtime di Windows PowerShell

Il runtime di Windows PowerShell è il motore di esecuzione che implementa l'elaborazione del comando. Sono incluse le classi che forniscono l'interfaccia tra l'applicazione host e i comandi e i provider di Windows PowerShell. Il runtime di Windows PowerShell viene implementato come oggetto spazio per la sessione corrente di Windows PowerShell, ovvero l'ambiente operativo in cui vengono eseguiti la shell e i comandi. Per informazioni operative, vedere funzionamento di [Windows PowerShell](/previous-versions//ms714658(v=vs.85)).

### <a name="windows-powershell-language"></a>Linguaggio di Windows PowerShell

Il linguaggio di Windows PowerShell fornisce funzioni di script e meccanismi per richiamare i comandi. Per informazioni complete sullo scripting, vedere la Guida di riferimento al linguaggio Windows PowerShell fornita con Windows PowerShell.

### <a name="extended-type-system-ets"></a>Sistema di tipi estesi (ETS)

Windows PowerShell consente di accedere a un'ampia gamma di oggetti diversi, ad esempio oggetti .NET e XML. Di conseguenza, per presentare un'astrazione comune per tutti i tipi di oggetto, la shell usa il sistema di tipi esteso (ETS). La maggior parte delle funzionalità ETS è trasparente per l'utente, ma lo script o lo sviluppatore .NET lo usa per gli scopi seguenti:

- Visualizzazione di un subset dei membri di oggetti specifici. Windows PowerShell fornisce una visualizzazione "adattata" di diversi tipi di oggetti specifici.

- Aggiunta di membri a oggetti esistenti.

- Accesso agli oggetti serializzati.

- Scrittura di oggetti personalizzati.

  Con ETS è possibile creare nuovi "tipi" flessibili compatibili con il linguaggio di Windows PowerShell. Gli sviluppatori .NET possono utilizzare gli oggetti utilizzando la stessa semantica del linguaggio di Windows PowerShell per lo scripting, ad esempio, per determinare se un oggetto restituisce `true`.

  Per altre informazioni su ETS e sul modo in cui Windows PowerShell usa gli oggetti, vedere Concetti relativi agli oggetti di [Windows PowerShell](/powershell/scripting/learn/understanding-important-powershell-concepts?view=powershell-6).

## <a name="programming-for-windows-powershell"></a>Programmazione per Windows PowerShell

Windows PowerShell definisce il codice per i comandi, i provider e altri moduli di programma usando il .NET Framework. Non si è limitati all'uso di Microsoft Visual Studio per la creazione di moduli personalizzati per Windows PowerShell, anche se gli esempi forniti in questa guida sono noti per essere eseguiti in questo strumento. È possibile usare qualsiasi linguaggio .NET che supporta l'ereditarietà delle classi e l'uso di attributi. In alcuni casi, le API di Windows PowerShell richiedono che il linguaggio di programmazione sia in grado di accedere ai tipi generici.

## <a name="programmers-reference"></a>Guida di riferimento per programmatori

Per informazioni di riferimento sullo sviluppo per Windows PowerShell, vedere [Windows PowerShell SDK](../windows-powershell-reference.md).

## <a name="getting-started-using-windows-powershell"></a>Introduzione tramite Windows PowerShell

Per ulteriori informazioni sull'avvio dell'utilizzo della shell di Windows PowerShell, vedere la [Introduzione con Windows PowerShell](/powershell/scripting/getting-started/getting-started-with-windows-powershell) fornito con Windows PowerShell. Un documento di riferimento rapido a tre riduzioni viene inoltre fornito come introduzione per l'utilizzo dei cmdlet.

## <a name="contents-of-this-guide"></a>Contenuto della Guida

|Argomento|Definizione|
|-----------|----------------|
|[Come creare un provider di Windows PowerShell](./how-to-create-a-windows-powershell-provider.md)|Questa sezione descrive come compilare un provider di Windows PowerShell per Windows PowerShell.|
|[Come creare un'applicazione host di Windows PowerShell](/powershell/scripting/developer/hosting/writing-a-windows-powershell-host-application)|In questa sezione viene descritto come scrivere un'applicazione host che manipola un spazio e come scrivere un'applicazione host che implementa il proprio host personalizzato.|
|[Come creare uno snap-in di Windows PowerShell](../cmdlet/how-to-create-a-windows-powershell-snap-in.md)|In questa sezione viene descritto come creare uno snap-in utilizzato per registrare tutti i cmdlet e i provider in un assembly e come creare uno snap-in personalizzato.|
|[Come creare una shell della console](./how-to-create-a-console-shell.md)|In questa sezione viene descritto come creare una shell della console non estendibile.|
|[Concetti di Windows PowerShell](./windows-powershell-concepts.md)|In questa sezione vengono fornite informazioni concettuali che consentono di comprendere Windows PowerShell dal punto di vista di uno sviluppatore.|

## <a name="see-also"></a>Vedere anche

[Windows PowerShell SDK](../windows-powershell-reference.md)
