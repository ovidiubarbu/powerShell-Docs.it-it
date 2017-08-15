---
ms.date: 2017-06-05T00:00:00.000Z
keywords: powershell,cmdlet
title: Informazioni sui concetti importanti di Windows PowerShell
ms.assetid: 3e601e38-4520-4578-a48d-b6779f1d35ee
ms.openlocfilehash: 1ffcfefcc7ffc7c98ba4d1e3ccc9a59cd9b0baac
ms.sourcegitcommit: 74255f0b5f386a072458af058a15240140acb294
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 08/03/2017
---
# <a name="understanding-important-windows-powershell-concepts"></a>Informazioni sui concetti importanti di Windows PowerShell
La progettazione di Windows PowerShell integra concetti relativi a molti ambienti diversi. Alcuni di essi sono già noti agli utenti con esperienza di shell o ambienti di programmazione specifici, ma in pochi li conosceranno tutti. La comprensione di alcuni di questi concetti assicura un'utile conoscenza generale della shell.

### <a name="commands-are-not-text-based"></a>I comandi non sono basati su testo
A differenza dei comandi dell'interfaccia della riga di comando tradizionale, i cmdlet di Windows PowerShell sono progettati per gestire gli oggetti, vale a dire informazioni strutturate che sono molto più di una stringa di caratteri visualizzati sullo schermo. L'output del comando riporta sempre informazioni aggiuntive utilizzabili in caso di necessità. Questo argomento verrà illustrato in dettaglio in questo articolo.

Se in precedenza sono stati usati strumenti di elaborazione del testo per elaborare i dati della riga di comando, si noterà che hanno un comportamento diverso se si usano in Windows PowerShell. Nella maggior parte dei casi non sono necessari strumenti di elaborazione del testo per estrarre informazioni specifiche. È possibile accedere direttamente a una parte dei dati usando i comandi standard di manipolazione degli oggetti di Windows PowerShell.

### <a name="the-command-family-is-extensible"></a>La famiglia di comandi è estendibile
Le interfacce come Cmd.exe non consentono di estendere direttamente il set di comandi predefinito. È possibile creare strumenti da riga di comando esterni eseguibili in Cmd.exe, ma questi strumenti esterni non hanno servizi, come l'integrazione della Guida, e Cmd.exe non li riconosce automaticamente come comandi validi.

I comandi binari nativi di Windows PowerShell, noti come *cmdlet* (pronunciato command-let), possono essere integrati con cmdlet creati e aggiunti a Windows PowerShell usando gli snap-in. Gli *snap-in* di Windows PowerShell sono compilati, proprio come strumenti binari di qualsiasi altra interfaccia. Possono essere usati per aggiungere provider di Windows PowerShell e nuovi cmdlet. alla shell.

A causa della speciale natura dei comandi interni di Windows PowerShell, saranno indicati come *cmdlet*.

> [!NOTE]
> Windows PowerShell può eseguire comandi diversi dai cmdlet. Non verranno esaminati in dettaglio nel Manuale dell'utente di Windows PowerShell, ma è utile conoscerli come categorie di tipi di comando. Windows PowerShell supporta script che sono analoghi a quelli della shell UNIX e ai file batch di Cmd.exe, ma che hanno l'estensione di file ps1. Windows PowerShell consente inoltre di creare funzioni interne utilizzabili direttamente nell'interfaccia o negli script.

### <a name="windows-powershell-handles-console-input-and-display"></a>Windows PowerShell gestisce l'input e la visualizzazione della console
Quando si digita un comando, l'input della riga di comando viene sempre elaborato direttamente. Windows PowerShell formatta inoltre l'output visualizzato sullo schermo. Questo aspetto è fondamentale perché riduce il lavoro richiesto a ogni cmdlet e assicura di poter sempre eseguire le operazioni nello stesso modo, indipendentemente dal cmdlet usato. Un esempio di come ciò semplifichi le cose per gli sviluppatori di strumenti e gli utenti è costituito dalla Guida della riga di comando.

Gli strumenti da riga di comando tradizionali hanno i propri schemi per la richiesta e la visualizzazione della Guida. Alcuni strumenti da riga di comando usano **/?** per attivare la visualizzazione della Guida, altri usano **-?**, **/H** o addirittura **//**. Alcuni visualizzano la Guida in una finestra GUI, invece che nella visualizzazione della console. Alcuni strumenti complessi, come quelli di aggiornamento delle applicazioni, decomprimono i file interni prima di visualizzare la Guida. Se si usa il parametro sbagliato, lo strumento potrebbe ignorare quanto è stato digitato e iniziare a eseguire automaticamente un'attività.

Quando si immette un comando in Windows PowerShell, tutto ciò che si digita viene analizzato e pre-elaborato automaticamente. Se si usa il parametro **-?** con un cmdlet di Windows PowerShell, significa sempre "Mostra Guida per il comando". Gli sviluppatori di cmdlet non devono analizzare il comando, ma si limitano a fornire il testo della Guida.

È importante comprendere che le funzionalità della Guida di Windows PowerShell sono disponibili anche quando si eseguono strumenti tradizionali da riga di comando in Windows PowerShell. Windows PowerShell elabora i parametri e passa i risultati agli strumenti esterni.

> [!NOTE]
> Se si esegue un'applicazione grafica in Windows PowerShell, verrà visualizzata la finestra dell'applicazione. Windows PowerShell interviene solo per l'elaborazione dell'input della riga di comando immesso o dell'output dell'applicazione restituito nella finestra della console, senza influire sul funzionamento interno dell'applicazione.

### <a name="windows-powershell-uses-some-c-syntax"></a>Windows PowerShell usa parte della sintassi di C#
Essendo basato su .NET Framework, Windows PowerShell include parole chiave e funzionalità della sintassi molto simili a quelle usate nel linguaggio di programmazione C#. Imparare a usare Windows PowerShell renderà molto più facile apprendere C#, nel caso si abbia interesse per questo linguaggio.

Per chi non programma in C#, questa analogia non è importante. Se tuttavia si ha già familiarità con C#, questi aspetti in comune possono rendere molto più semplice imparare a usare Windows PowerShell.

