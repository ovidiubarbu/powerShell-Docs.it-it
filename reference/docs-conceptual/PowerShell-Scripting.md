---
ms.date: 08/27/2018
keywords: powershell,cmdlet
title: Scripting di PowerShell
ms.openlocfilehash: 754805148dc815a12c5c77e4894fb598c6927f7e
ms.sourcegitcommit: 59727f71dc204785a1bcdedc02716d8340a77aeb
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 08/28/2018
ms.locfileid: "43133994"
---
# <a name="powershell"></a>PowerShell

PowerShell è una shell della riga di comando basata su attività e un linguaggio di scripting basato su .NET Framework.
PowerShell aiuta gli amministratori di sistema e gli utenti esperti ad automatizzare rapidamente attività che gestiscono i sistemi operativi (Linux, macOS e Windows) e i processi.

I comandi di PowerShell permettono di gestire i computer dalla riga di comando. I provider di PowerShell permettono di accedere ad archivi dati, come il Registro di sistema e l'archivio certificati, con la stessa semplicità con cui si accede al file system. PowerShell include un parser di espressioni avanzato e un linguaggio di scripting completamente sviluppato.

## <a name="powershell-is-open-source"></a>PowerShell è open source

Il codice open source di base di PowerShell ora è disponibile su GitHub e aperto ai contributi della community.
Vedere il [codice open source di PowerShell su GitHub](https://github.com/powershell/powershell).

Per iniziare, è possibile [ottenere PowerShell](https://github.com/PowerShell/PowerShell#get-powershell).
In alternativa, è possibile iniziare da una rapida [panoramica introduttiva](https://github.com/PowerShell/PowerShell/blob/master/docs/learning-powershell)

## <a name="powershell-design-goals"></a>Obiettivi di progettazione di PowerShell

PowerShell è progettato per migliorare la riga di comando e l'ambiente di scripting eliminando problemi di lunga data e aggiungendo nuove funzionalità.

### <a name="discoverability"></a>Individuabilità

È facile individuare le funzionalità di PowerShell. Ad esempio, per trovare un elenco dei cmdlet che consentono di visualizzare e modificare i servizi di Windows, digitare:

```powershell
Get-Command *-Service
```

Dopo aver individuato il cmdlet che esegue un'attività, è possibile ottenere altre informazioni con il cmdlet `Get-Help`. Per visualizzare la Guida per il cmdlet `Get-Service`, ad esempio, digitare:

```powershell
Get-Help Get-Service
```

La maggior parte dei cmdlet restituisce oggetti che possono essere modificati e di cui è possibile eseguire il rendering come testo per la visualizzazione. Per una migliore comprensione dell'output di un cmdlet, inviare l'output tramite pipe al cmdlet `Get-Member`. Il comando seguente, ad esempio, visualizza informazioni sui membri dell'oggetto restituito dal cmdlet `Get-Service`.

```powershell
Get-Service | Get-Member
```

### <a name="consistency"></a>Coerenza

La gestione dei sistemi può essere un'attività complessa. Gli strumenti con un'interfaccia coerente sono utili per assicurare un maggiore controllo sulla complessità intrinseca. Sfortunatamente, gli strumenti da riga di comando o gli oggetti COM gestibili tramite script non sono certo noti per la loro coerenza.

La coerenza di PowerShell è una delle sue principali risorse. Ad esempio, dopo aver imparato a usare il cmdlet `Sort-Object`, è possibile usare tali conoscenze per ordinare l'output di qualsiasi cmdlet. Non è necessario apprendere le diverse routine di ordinamento di ogni cmdlet.

Inoltre, gli sviluppatori di cmdlet non devono progettare funzionalità di ordinamento per i propri cmdlet. PowerShell offre un framework con le funzionalità di base per garantire la coerenza. Il framework elimina alcune possibilità di scelta lasciate allo sviluppatore. In cambio, tuttavia, semplifica notevolmente lo sviluppo di cmdlet.

### <a name="interactive-and-scripting-environments"></a>Ambienti interattivi e di scripting

Il prompt dei comandi di Windows offre una shell interattiva con accesso a strumenti da riga di comando e funzionalità di scripting di base. Windows Script Host (WSH) include strumenti da riga di comando configurabili tramite script e oggetti di automazione COM, ma non offre una shell interattiva.

PowerShell integra una shell interattiva e un ambiente di scripting. PowerShell può accedere a strumenti da riga di comando, oggetti COM e librerie di classi .NET. Questa combinazione di funzionalità estende le capacità dell'utente interattivo, dell'autore di script e dell'amministratore di sistema.

### <a name="object-orientation"></a>Orientamento agli oggetti

PowerShell è basato su oggetti e non sul testo. L'output di un comando è un oggetto. È possibile inviare l'oggetto di output, tramite la pipeline, a un altro comando come input.

Questa pipeline offre un'interfaccia familiare per gli utenti che sanno usare altre shell. PowerShell estende questo concetto inviando oggetti anziché testo.

### <a name="easy-transition-to-scripting"></a>Semplice transizione allo scripting

La possibilità di individuare i comandi di PowerShell semplifica il passaggio dalla digitazione interattiva dei comandi alla creazione e all'esecuzione di script. Le trascrizioni e la cronologia di PowerShell semplificano la copia di comandi in un file da usare come script.
