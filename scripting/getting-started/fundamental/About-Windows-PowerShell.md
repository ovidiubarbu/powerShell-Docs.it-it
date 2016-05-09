---
title: Informazioni su Windows PowerShell
ms.custom: na
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 979654ae-7994-47f8-be43-d79e7a140143
---
# Informazioni su Windows PowerShell
Windows PowerShell è progettato per migliorare la riga di comando e l'ambiente di scripting eliminando problemi di lunga data e aggiungendo nuove funzionalità.

## Individuabilità
È facile individuare le funzionalità di Windows PowerShell. Ad esempio, per trovare un elenco dei cmdlet che consentono di visualizzare e modificare i servizi di Windows, digitare:

```
get-command *-service
```

Dopo aver individuato il cmdlet che esegue un'attività, è possibile ottenere altre informazioni con il cmdlet Get-Help. Per visualizzare la Guida per il cmdlet Get-Service, ad esempio, digitare:

```
get-help get-service
```

Per una migliore comprensione dell'output del cmdlet, inviarne l'output tramite pipe al cmdlet Get-Member. Il comando seguente, ad esempio, visualizza informazioni sui membri dell'oggetto restituito dal cmdlet Get-Service.

```
get-service | get-member
```

## Coerenza
La gestione dei sistemi può essere un'impresa complicata e gli strumenti con un'interfaccia coerente sono utili per esercitare un maggiore controllo sulla complessità intrinseca. Sfortunatamente, gli strumenti da riga di comando o gli oggetti COM gestibili tramite script non sono certo noti per la loro coerenza.

La coerenza di Windows PowerShell è una delle sue principali risorse. Ad esempio, dopo aver imparato a usare il cmdlet Sort-Object, è possibile usare tali conoscenze per ordinare l'output di qualsiasi cmdlet. Non occorre imparare le diverse routine di ordinamento di ogni cmdlet.

Gli sviluppatori di cmdlet, inoltre, non devono progettare funzionalità di ordinamento per i loro cmdlet. Windows PowerShell offre loro un framework che fornisce le funzionalità di base e impone la coerenza per molti aspetti dell'interfaccia. Il framework elimina alcune delle scelte che sono in genere compito dello sviluppatore, ma, in cambio, semplifica notevolmente lo sviluppo di cmdlet affidabili e facili da usare.

## Ambienti interattivi e di scripting
Windows PowerShell è un ambiente interattivo e di scripting combinato che offre l'accesso a strumenti da riga di comando e oggetti COM, oltre a consentire l'uso della potente libreria di classi .NET Framework.

Questo ambiente rappresenta un miglioramento del prompt dei comandi Windows, che rende disponibile un ambiente interattivo con più strumenti da riga di comando. Si tratta di un miglioramento anche rispetto agli script di Windows Script Host (WSH), che consentono di usare più strumenti da riga di comando e oggetti di automazione COM, ma non offrono un ambiente interattivo.

Combinando l'accesso a tutte queste funzionalità, Windows PowerShell amplia le potenzialità dell'utente interattivo e dell'autore di script, oltre a rendere più gestibile l'amministrazione del sistema.

## Orientamento agli oggetti
Sebbene le interazioni con Windows PowerShell avvengano tramite la digitazione di comandi testuali, Windows PowerShell è basato su oggetti e non sul testo. L'output di un comando è un oggetto. È possibile inviare l'oggetto di output a un altro comando come input. Di conseguenza, Windows PowerShell offre un'interfaccia familiare agli utenti esperti di altre shell, introducendo allo stesso tempo un paradigma di riga di comando nuovo e potente. Estende il concetto di invio dei dati tra i comandi grazie alla possibilità di inviare oggetti invece di testo.

## Facile transizione verso la creazione di script
Con Windows PowerShell è facile passare dalla digitazione interattiva di comandi alla creazione ed esecuzione di script. È possibile digitare i comandi al prompt dei comandi di Windows PowerShell per individuare i comandi che eseguono un'attività. Questi comandi possono essere poi salvati in una trascrizione o una cronologia prima di copiarli in un file per l'uso come script.



<!--HONumber=Apr16_HO1-->


