---
ms.date: 06/05/2017
keywords: powershell,cmdlet
title: Scripting di PowerShell
ms.openlocfilehash: c6ba3abc2544834e2cbec16a524f79399a1d2599
ms.sourcegitcommit: 77f62a55cac8c13d69d51eef5fade18f71d66955
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 07/17/2018
ms.locfileid: "39094052"
---
# <a name="powershell"></a>PowerShell

PowerShell, basato su .NET Framework, è una shell da riga di comando basata su attività nonché un linguaggio di scripting progettato espressamente per consentire agli amministratori di sistema e agli utenti avanzati di automatizzare rapidamente l'amministrazione di più sistemi operativi (Linux, macOS, Unix e Windows) e i processi correlati alle applicazioni eseguite su tali sistemi operativi.

## <a name="powershell-is-open-source"></a>PowerShell è open source

Il codice open source di base di PowerShell ora è disponibile su GitHub e aperto ai contributi della community.
Vedere il [codice open source di PowerShell su GitHub](https://github.com/powershell/powershell).

Per iniziare, è possibile [ottenere PowerShell](https://github.com/PowerShell/PowerShell#get-powershell).
In alternativa, è possibile iniziare da una rapida panoramica di [introduzione](https://github.com/PowerShell/PowerShell/blob/master/docs/learning-powershell)

## <a name="powershell-design-goals"></a>Obiettivi di progettazione di PowerShell
PowerShell è progettato per migliorare la riga di comando e l'ambiente di scripting eliminando problemi di lunga data e aggiungendo nuove funzionalità.

### <a name="discoverability"></a>Individuabilità
È facile individuare le funzionalità di PowerShell. Ad esempio, per trovare un elenco dei cmdlet che consentono di visualizzare e modificare i servizi di Windows, digitare:

```powershell
Get-Command *-Service
```

Dopo aver individuato il cmdlet che esegue un'attività, è possibile ottenere altre informazioni con il cmdlet `Get-Help`.
Per visualizzare la Guida per il cmdlet `Get-Service`, ad esempio, digitare:

```powershell
Get-Help Get-Service
```
La maggior parte dei cmdlet genera oggetti che possono essere modificati e di cui è possibile eseguire il rendering in testo per la visualizzazione.
Per una migliore comprensione dell'output del cmdlet, inviarne l'output tramite pipe al cmdlet `Get-Member`.
Il comando seguente, ad esempio, visualizza informazioni sui membri dell'oggetto restituito dal cmdlet `Get-Service`.

```powershell
Get-Service | Get-Member
```

### <a name="consistency"></a>Coerenza
La gestione dei sistemi può essere un'impresa complicata e gli strumenti con un'interfaccia coerente sono utili per esercitare un maggiore controllo sulla complessità intrinseca.
Sfortunatamente, gli strumenti da riga di comando o gli oggetti COM gestibili tramite script non sono certo noti per la loro coerenza.

La coerenza di PowerShell è una delle sue principali risorse.
Ad esempio, dopo aver imparato a usare il cmdlet `Sort-Object`, è possibile usare tali conoscenze per ordinare l'output di qualsiasi cmdlet.
Non occorre imparare le diverse routine di ordinamento di ogni cmdlet.

Gli sviluppatori di cmdlet, inoltre, non devono progettare funzionalità di ordinamento per i loro cmdlet.
PowerShell offre loro un framework che fornisce le funzionalità di base e impone la coerenza per molti aspetti dell'interfaccia.
Il framework elimina alcune delle scelte che sono in genere compito dello sviluppatore, ma, in cambio, semplifica notevolmente lo sviluppo di cmdlet affidabili e facili da usare.

### <a name="interactive-and-scripting-environments"></a>Ambienti interattivi e di scripting
PowerShell è un ambiente interattivo e di scripting combinato che offre l'accesso a strumenti da riga di comando e oggetti COM, oltre a consentire l'uso della potente libreria di classi .NET Framework.

Questo ambiente rappresenta un miglioramento del prompt dei comandi Windows, che rende disponibile un ambiente interattivo con più strumenti da riga di comando.
Si tratta di un miglioramento anche rispetto agli script di Windows Script Host (WSH), che consentono di usare più strumenti da riga di comando e oggetti di automazione COM, ma non offrono un ambiente interattivo.

Combinando l'accesso a tutte queste funzionalità, PowerShell amplia le potenzialità dell'utente interattivo e dell'autore di script, oltre a rendere più gestibile l'amministrazione del sistema.

### <a name="object-orientation"></a>Orientamento agli oggetti
Sebbene le interazioni con PowerShell avvengano tramite la digitazione di comandi testuali, PowerShell è basato su oggetti e non sul testo.
L'output di un comando è un oggetto.
È possibile inviare l'oggetto di output a un altro comando come input.
Di conseguenza, PowerShell offre un'interfaccia familiare agli utenti esperti di altre shell, introducendo allo stesso tempo un paradigma di riga di comando nuovo e potente.
Estende il concetto di invio dei dati tra i comandi grazie alla possibilità di inviare oggetti invece di testo.

### <a name="easy-transition-to-scripting"></a>Facile transizione verso la creazione di script
Con PowerShell è facile passare dalla digitazione interattiva di comandi alla creazione ed esecuzione di script.
È possibile digitare i comandi al prompt dei comandi di PowerShell per individuare i comandi che eseguono un'attività.
Questi comandi possono essere poi salvati in una trascrizione o una cronologia prima di copiarli in un file per l'uso come script.
