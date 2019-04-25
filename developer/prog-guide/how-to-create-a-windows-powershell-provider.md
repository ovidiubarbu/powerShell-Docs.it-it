---
title: Come creare un Provider PowerShell per Windows | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- providers [PowerShell Programmer's Guide]
- providers [PowerShellProgrammer's Guide], creating
- Windows PowerShell Programmer's Guide, providers
ms.assetid: 863e48e9-7206-4c6a-a59a-2ab2d30396bc
caps.latest.revision: 5
ms.openlocfilehash: 06910f32752668f13400f9be0767a2179133df04
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62081751"
---
# <a name="how-to-create-a-windows-powershell-provider"></a>Come creare un provider di Windows PowerShell

Questa sezione descrive come creare un provider di Windows PowerShell. Un provider di Windows PowerShell può essere considerato in due modi. All'utente, il provider rappresenta un set di dati archiviati. Ad esempio, i dati archiviati possono essere la Metabase di Internet Information Services (IIS), il Registro di sistema di Microsoft Windows, il file system di Windows, Active Directory e la variabile e alias dati archiviati da Windows PowerShell.

Agli sviluppatori, il provider di Windows PowerShell è l'interfaccia tra l'utente e i dati che l'utente deve accedere. Da questa prospettiva, ogni tipo di provider descritte in questa sezione supporta un set di specifiche classi di base e interfacce che consentono al runtime di Windows PowerShell di esporre alcuni cmdlet per l'utente in un modo comune.

## <a name="providers-provided-by-windows-powershell"></a>Provider di Windows PowerShell

Windows PowerShell sono disponibili diversi provider (ad esempio il provider FileSystem, provider del Registro di sistema e provider Alias) che consentono di accedere ad archivi dati noti. Per altre informazioni sui provider forniti da Windows PowerShell, usare il comando seguente per accedere alla Guida in linea:

**PS > get-help about_providers**

## <a name="accessing-the-stored-data-using-windows-powershell-paths"></a>L'accesso ai dati archiviati mediante i percorsi di Windows PowerShell

Provider di Windows PowerShell sono accessibili per il runtime di Windows PowerShell e comandi a livello di codice tramite l'uso di percorsi di Windows PowerShell. La maggior parte dei casi, questi percorsi vengono utilizzati per accedere direttamente ai dati tramite il provider. Tuttavia, alcuni percorsi possono essere risolti ai percorsi del provider interne che consentono un cmdlet per usare application programming interface (API) non Windows PowerShell per accedere ai dati. Per altre informazioni sul funzionamento di provider di Windows PowerShell all'interno di Windows PowerShell, vedere [modalità di funzionamento di Windows PowerShell](http://msdn.microsoft.com/en-us/ced30e23-10af-4700-8933-49873bd84d58).

## <a name="exposing-provider-cmdlets-using-windows-powershell-drives"></a>Unità di esporre i cmdlet del Provider usando Windows PowerShell

Un provider di Windows PowerShell espone i relativi cmdlet supportati tramite unità virtuali di Windows PowerShell. Windows PowerShell applica le regole seguenti per un'unità di Windows PowerShell:

- Il nome di un'unità può essere qualsiasi sequenza di caratteri alfanumerico.

- Un'unità può essere specificata in qualsiasi momento valido in un percorso, detta "radice".

- Un'unità può essere implementata per tutti i dati archiviati, non solo nel file system.

- Ogni unità consente di mantenere il proprio percorso di lavoro corrente, consentendo all'utente di mantenere contesto quando lo spostamento tra le unità.

## <a name="in-this-section"></a>Contenuto della sezione

La tabella seguente Elenca argomenti che includono esempi di codice che compilano a vicenda. Iniziando con il secondo argomento, il provider di Windows PowerShell di base può essere inizializzato e non inizializzati dal runtime di Windows PowerShell, l'argomento successivo aggiunge funzionalità per l'accesso ai dati, l'argomento successivo aggiunge funzionalità per la modifica dei dati ( gli elementi di dati archiviati), e così via.

|Argomento|Definizione|
|-----------|----------------|
|[Progettazione del Provider di Windows PowerShell](./designing-your-windows-powershell-provider.md)|In questo argomento vengono illustrati i fattori da considerare prima di implementare un provider di Windows PowerShell. Sono riepilogate le classi di base di provider di Windows PowerShell e le interfacce che vengono usate.|
|[Creazione di un Provider PowerShell di Windows di base](./creating-a-basic-windows-powershell-provider.md)|In questo argomento viene illustrato come creare un provider di Windows PowerShell che consente al runtime di Windows PowerShell inizializzare e annullare l'inizializzazione del provider.|
|[Creazione di un Provider di unità di PowerShell di Windows](./creating-a-windows-powershell-drive-provider.md)|In questo argomento viene illustrato come creare un provider di Windows PowerShell che consente all'utente di accedere a un archivio dati tramite un'unità di Windows PowerShell.|
|[Creazione di un Provider Windows PowerShell](./creating-a-windows-powershell-item-provider.md)|In questo argomento viene illustrato come creare un provider di Windows PowerShell che consente all'utente di modificare gli elementi in un archivio dati.|
|[Creazione di un Provider di contenitore di Windows PowerShell](./creating-a-windows-powershell-container-provider.md)|In questo argomento viene illustrato come creare un provider di Windows PowerShell che consente all'utente di usare gli archivi dati multilivello.|
|[Creazione di un Provider di navigazione di Windows PowerShell](./creating-a-windows-powershell-navigation-provider.md)|In questo argomento viene illustrato come creare un provider di Windows PowerShell che consente all'utente di esplorare gli elementi di un archivio dati in modo gerarchico.|
|[Creazione di un Provider di contenuto di PowerShell di Windows](./creating-a-windows-powershell-content-provider.md)|In questo argomento viene illustrato come creare un provider di Windows PowerShell che consente all'utente di modificare il contenuto degli elementi in un archivio dati.|
|[Creazione di un Provider di proprietà di PowerShell di Windows](./creating-a-windows-powershell-property-provider.md)|In questo argomento viene illustrato come creare un provider di Windows PowerShell che consente all'utente di modificare le proprietà degli elementi in un archivio dati.|

## <a name="see-also"></a>Vedere anche

[Funzionamento di Windows PowerShell](http://msdn.microsoft.com/en-us/ced30e23-10af-4700-8933-49873bd84d58)

[Windows PowerShell SDK](../windows-powershell-reference.md)

[Guida per programmatori di Windows PowerShell](./windows-powershell-programmer-s-guide.md)
