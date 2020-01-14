---
ms.date: 12/19/2019
keywords: powershell,cmdlet
title: Accessibilità in Windows PowerShell ISE
ms.openlocfilehash: e618daca98d76f767a8b60a3425760bfc0bd0f64
ms.sourcegitcommit: 058a6e86eac1b27ca57a11687019df98709ed709
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/08/2020
ms.locfileid: "75736284"
---
# <a name="accessibility-in-windows-powershell-ise"></a>Accessibilità in Windows PowerShell ISE

Questo argomento descrive le funzionalità di accessibilità di Windows PowerShell Integrated Scripting Environment (ISE) che potrebbero risultare utili.

- [Come modificare le dimensioni e la posizione dei riquadri della console e di script](#how-to-change-the-size-and-location-of-the-console-and-script-panes)
- [Tasti di scelta rapida per la modifica del testo](#keyboard-shortcuts-for-editing-text)
- [Tasti di scelta rapida per l'esecuzione di script](#keyboard-shortcuts-for-running-scripts)
- [Tasti di scelta rapida per la personalizzazione della visualizzazione](#keyboard-shortcuts-for-customizing-the-view)
- [Tasti di scelta rapida per il debug di script](#keyboard-shortcuts-for-debugging-scripts)
- [Tasti di scelta rapida per le schede di Windows PowerShell](#keyboard-shortcuts-for-windows-powershell-tabs)
- [Tasti di scelta rapida per avvio e uscita](#keyboard-shortcuts-for-starting-and-exiting)
- [Gestione dei punti di interruzione con i cmdlet](#breakpoint-management)

Microsoft cerca di sviluppare prodotti e servizi che siano facili da utilizzare per chiunque. Gli argomenti seguenti forniscono informazioni sulle funzionalità, i prodotti e i servizi che migliorano l'accessibilità di Windows PowerShell ISE per gli utenti disabili.

Oltre alle funzionalità e utilità di accessibilità disponibili in Microsoft Windows, le funzionalità seguenti rendono Windows PowerShell ISE più accessibile agli utenti disabili:

- Tasti di scelta rapida

- Tabella di colorazione della sintassi e la possibilità di modificare diverse altre impostazioni di colore mediante l'oggetto di scripting [$psISE.Options](object-model/The-ISEOptions-Object.md).

- Modifica delle dimensioni del testo

## <a name="how-to-change-the-size-and-location-of-the-console-and-script-panes"></a>Come modificare le dimensioni e la posizione dei riquadri della console e di script

È possibile usare la procedura seguente per modificare le dimensioni e la posizione dei riquadri della console e di script Alla riapertura di Windows PowerShell ISE, le modifiche apportate a dimensioni e posizione verranno mantenute.

### <a name="to-resize-the-script-pane-and-console-pane"></a>Per ridimensionare il riquadro di script e il riquadro della console

1. Posizionare il puntatore sulla linea di divisione tra il riquadro di script e il riquadro della console.

2. Quando il puntatore del mouse assume la forma di una freccia a due punte, trascinare il bordo per modificare le dimensioni del riquadro.

### <a name="to-move-the-script-pane-and-console-pane"></a>Per spostare il riquadro di script e il riquadro della console

Eseguire una delle operazioni seguenti:

- Per spostare Riquadro di script sopra Riquadro console, premere <kbd>CTRL</kbd>+<kbd>1</kbd> o sulla barra degli strumenti fare clic sull'icona **Mostra riquadro di script in alto** oppure scegliere **Mostra riquadro di script in alto** dal menu **Visualizza**.

- Per spostare il riquadro di script a destra del riquadro della console, premere <kbd>CTRL</kbd>+<kbd>2</kbd> o sulla barra degli strumenti fare clic sull'icona **Mostra riquadro di script a destra** oppure scegliere **Mostra riquadro di script a destra** dal menu **Visualizza**.

- Per ingrandire il riquadro di script, premere <kbd>CTRL</kbd>+<kbd>3</kbd> o sulla barra degli strumenti fare clic sull'icona **Mostra riquadro di script ingrandito** oppure scegliere **Mostra riquadro di script ingrandito** dal menu **Visualizza**.

- Per ingrandire il riquadro della console e nascondere il riquadro di script, all'estrema destra della riga di schede fare clic sull'icona **Nascondi riquadro di script** oppure nel menu **Visualizza** fare clic per deselezionare l'opzione di menu **Mostra riquadro di script**.

- Per visualizzare il riquadro di script quando il riquadro della console è ingrandito, all'estrema destra della riga di schede fare clic sull'icona **Mostra riquadro di script** oppure nel menu **Visualizza** fare clic per selezionare l'opzione di menu **Mostra riquadro di script**.

## <a name="keyboard-shortcuts-for-editing-text"></a>Tasti di scelta rapida per la modifica del testo

È possibile usare i tasti di scelta rapida seguenti durante la modifica del testo.

|           Azione            |       Tasti di scelta rapida       |          Posizione           |
| --------------------------- | ------------------------------ | ------------------------- |
| **Copia**                    | <kbd>CTRL</kbd>+<kbd>C</kbd>   | Riquadro di script, Riquadro Console |
| **Taglia**                     | <kbd>CTRL</kbd>+<kbd>X</kbd>   | Riquadro di script, Riquadro Console |
| **Trova nello script**          | <kbd>CTRL</kbd>+<kbd>F</kbd>   | Riquadro di script               |
| **Trova successivo nello script**     | <kbd>F3</kbd>                  | Riquadro di script               |
| **Trova precedente nello script** | <kbd>MAIUSC</kbd>+<kbd>F3</kbd> | Riquadro di script               |
| **Incolla**                   | <kbd>CTRL</kbd>+<kbd>V</kbd>   | Riquadro di script, Riquadro Console |
| **Ripeti**                    | <kbd>CTRL</kbd>+<kbd>Y</kbd>   | Riquadro di script, Riquadro Console |
| **Sostituisci nello script**       | <kbd>CTRL</kbd>+<kbd>H</kbd>   | Riquadro di script               |
| **Salva**                    | <kbd>CTRL</kbd>+<kbd>S</kbd>   | Riquadro di script               |
| **Seleziona tutto**              | <kbd>CTRL</kbd>+<kbd>A</kbd>   | Riquadro di script, Riquadro Console |
| **Annulla**                    | <kbd>CTRL</kbd>+<kbd>Z</kbd>   | Riquadro di script, Riquadro Console |

## <a name="keyboard-shortcuts-for-running-scripts"></a>Tasti di scelta rapida per l'esecuzione di script

È possibile usare i tasti di scelta rapida seguenti durante l'esecuzione di script nel riquadro di script.

|            Azione            |                                                                                                     Tasto di scelta rapida                                                                                                      |
| ---------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **Nuovo**                      | <kbd>CTRL</kbd>+<kbd>N</kbd>                                                                                                                                                                                               |
| **Apri**                     | <kbd>CTRL</kbd>+<kbd>O</kbd>                                                                                                                                                                                               |
| **Esegui**                      | <kbd>F5</kbd>                                                                                                                                                                                                              |
| **Esegui selezione**            | <kbd>F8</kbd>                                                                                                                                                                                                              |
| **Arresta esecuzione**           | <kbd>CTRL</kbd>+<kbd>INTERR</kbd>. È possibile usare <kbd>CTRL</kbd>+<kbd>C</kbd> quando il contesto non è ambiguo (in assenza di testo selezionato).                                                                               |
| **TAB** (passaggio allo script successivo)     | <kbd>CTRL</kbd>+<kbd>TAB</kbd> **Nota:** la pressione di TAB per passare allo script successivo funziona solo quando è aperta una sola scheda di PowerShell o quando sono aperte più schede di PowerShell, ma lo stato attivo si trova nel riquadro di script.                |
| **TAB** (passaggio allo script precedente) | <kbd>CTRL</kbd>+<kbd>MAIUSC</kbd>+<kbd>TAB</kbd> **Nota:** la pressione di TAB per passare allo script precedente funziona quando è aperta una sola scheda di PowerShell o quando sono aperte più schede di PowerShell e lo stato attivo si trova nel riquadro di script. |

## <a name="keyboard-shortcuts-for-customizing-the-view"></a>Tasti di scelta rapida per la personalizzazione della visualizzazione

È possibile usare i tasti di scelta rapida seguenti per personalizzare la visualizzazione in Windows PowerShell ISE. Sono accessibili da tutti i riquadri nell'applicazione.

|           Azione           |         Tasto di scelta rapida        |
| -------------------------- | -------------------------------- |
| **Vai a riquadro Console**     | <kbd>CTRL</kbd>+<kbd>D</kbd>     |
| **Vai al riquadro di script**      | <kbd>CTRL</kbd>+<kbd>I</kbd>     |
| **Mostra riquadro di script**       | <kbd>CTRL</kbd>+<kbd>R</kbd>     |
| **Nascondi riquadro di script**       | <kbd>CTRL</kbd>+<kbd>R</kbd>     |
| **Sposta riquadro di script in alto**    | <kbd>CTRL</kbd>+<kbd>1</kbd>     |
| **Sposta riquadro di script a destra** | <kbd>CTRL</kbd>+<kbd>2</kbd>     |
| **Ingrandisci riquadro di script**   | <kbd>CTRL</kbd>+<kbd>3</kbd>     |
| **Zoom avanti**                | <kbd>CTRL</kbd>+<kbd>SEGNO PIÙ</kbd>  |
| **Zoom indietro**               | <kbd>CTRL</kbd>+<kbd>SEGNO MENO</kbd> |

## <a name="keyboard-shortcuts-for-debugging-scripts"></a>Tasti di scelta rapida per il debug di script

È possibile usare i tasti di scelta rapida seguenti durante il debug di script.

|           Azione           |               Tasto di scelta rapida                |                Posizione                |
| -------------------------- | ---------------------------------------------- | ------------------------------------ |
| **Esegui/Continua**           | <kbd>F5</kbd>                                  | Riquadro di script, durante il debug di uno script |
| **Esegui istruzione**              | <kbd>F11</kbd>                                 | Riquadro di script, durante il debug di uno script |
| **Esegui istruzione/routine**              | <kbd>F10</kbd>                                 | Riquadro di script, durante il debug di uno script |
| **Esci da istruzione/routine**               | <kbd>MAIUSC</kbd>+<kbd>F11</kbd>                | Riquadro di script, durante il debug di uno script |
| **Visualizza stack chiamate**     | <kbd>CTRL</kbd>+<kbd>MAIUSC</kbd>+<kbd>D</kbd>  | Riquadro di script, durante il debug di uno script |
| **Elenca punti di interruzione**       | <kbd>CTRL</kbd>+<kbd>MAIUSC</kbd>+<kbd>L</kbd>  | Riquadro di script, durante il debug di uno script |
| **Attiva/disattiva punto di interruzione**      | <kbd>F9</kbd>                                  | Riquadro di script, durante il debug di uno script |
| **Rimuovere tutti i punti di interruzione** | <kbd>CTRL</kbd>+<kbd>MAIUSC</kbd>+<kbd>F9</kbd> | Riquadro di script, durante il debug di uno script |
| **Arresta debugger**          | <kbd>MAIUSC</kbd>+<kbd>F5</kbd>                 | Riquadro di script, durante il debug di uno script |

> [!NOTE]
> È anche possibile usare i tasti di scelta rapida progettati per la console di Windows PowerShell durante il debug degli script in Windows PowerShell ISE. Per usare questi tasti di scelta rapida, è necessario digitarli in Riquadro console e premere INVIO.

|                 Azione                  |      Tasto di scelta rapida       |                Posizione                 |
| --------------------------------------- | ---------------------------- | ------------------------------------- |
| **Continua**                            | <kbd>C</kbd>                 | Riquadro della console, durante il debug di uno script |
| **Esegui istruzione**                           | <kbd>S</kbd>                 | Riquadro della console, durante il debug di uno script |
| **Esegui istruzione/routine**                           | <kbd>V</kbd>                 | Riquadro della console, durante il debug di uno script |
| **Esci da istruzione/routine**                            | <kbd>O</kbd>                 | Riquadro della console, durante il debug di uno script |
| **Ripeti ultimo comando**(Esegui istruzione/routine o Esci da istruzione/routine) | <kbd>INVIO</kbd>             | Riquadro della console, durante il debug di uno script |
| **Visualizza stack chiamate**                  | <kbd>K</kbd>                 | Riquadro della console, durante il debug di uno script |
| **Arresta debug**                      | <kbd>Q</kbd>                 | Riquadro della console, durante il debug di uno script |
| **Elenca lo script**                     | <kbd>L</kbd>                 | Riquadro della console, durante il debug di uno script |
| **Visualizza i comandi di debug della console**  | <kbd>H</kbd> o <kbd>?</kbd> | Riquadro della console, durante il debug di uno script |

## <a name="keyboard-shortcuts-for-windows-powershell-tabs"></a>Tasti di scelta rapida per le schede di Windows PowerShell

È possibile usare i tasti di scelta rapida seguenti durante l'uso delle schede di PowerShell.

|             Azione              |                                 Tasto di scelta rapida                                  |
| ------------------------------- | ---------------------------------------------------------------------------------- |
| **Chiudi scheda di PowerShell**        | <kbd>CTRL</kbd>+<kbd>W</kbd>                                                       |
| **Nuova scheda di PowerShell**          | <kbd>CTRL</kbd>+<kbd>T</kbd>                                                       |
| **Scheda precedente di PowerShell**     | <kbd>CTRL</kbd>+<kbd>MAIUSC</kbd>+<kbd>TAB</kbd> (Solo se non ci sono file aperti in alcuna scheda di PowerShell)                 |
| **Scheda successiva di Windows PowerShell** | <kbd>CTRL</kbd>+<kbd>TAB</kbd> (Solo se non ci sono file aperti in alcuna scheda di PowerShell) |

## <a name="keyboard-shortcuts-for-starting-and-exiting"></a>Tasti di scelta rapida per avvio e uscita

È possibile usare i tasti di scelta rapida seguenti per avviare la console di Windows PowerShell (**PowerShell.exe**) o per uscire da Windows PowerShell ISE.

|                        Azione                         |               Tasto di scelta rapida               |
| ----------------------------------------------------- | --------------------------------------------- |
| **Esci**                                              | <kbd>ALT</kbd>+<kbd>F4</kbd>                  |
| **Avviare PowerShell.exe** (console di Windows PowerShell). | <kbd>CTRL</kbd>+<kbd>MAIUSC</kbd>+<kbd>P</kbd> |

## <a name="breakpoint-management"></a>Gestione dei punti di interruzione

Per gli utenti con problemi di vista sono disponibili informazioni sui punti di interruzione tramite i cmdlet per la gestione dei punti di interruzione, come [Get-PSBreakpoint](/reference/6/Microsoft.PowerShell.Utility/Get-PSBreakpoint.md) e [Set-PSBreakpoint](/reference/6/Microsoft.PowerShell.Utility/Set-PSBreakpoint.md).
Per altre informazioni, vedere 'Come gestire i punti di interruzione' in [Modalità di esecuzione del debug degli script in Windows PowerShell ISE](How-to-Debug-Scripts-in-Windows-PowerShell-ISE.md).

## <a name="see-also"></a>Vedere anche

[Introduzione a Windows PowerShell ISE](Introducing-the-Windows-PowerShell-ISE.md)
