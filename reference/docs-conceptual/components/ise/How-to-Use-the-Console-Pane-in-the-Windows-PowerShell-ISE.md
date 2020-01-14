---
ms.date: 01/02/2020
keywords: powershell,cmdlet
title: Come usare il riquadro della console in Windows PowerShell ISE
ms.openlocfilehash: f0ef07e410ed494f5732eab360c4e050c9c09a7f
ms.sourcegitcommit: 058a6e86eac1b27ca57a11687019df98709ed709
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/08/2020
ms.locfileid: "75736148"
---
# <a name="how-to-use-the-console-pane-in-the-windows-powershell-ise"></a>Come usare il riquadro della console in Windows PowerShell ISE

Il riquadro della console in Windows PowerShell Integrated Scripting Environment (ISE) funziona esattamente come la finestra della console di Windows PowerShell ISE autonoma.

Per eseguire un comando nel riquadro della console, digitare un comando e quindi premere <kbd>INVIO</kbd>. Per immettere più comandi da eseguire in sequenza, premere <kbd>MAIUSC</kbd>+<kbd>INVIO</kbd> tra un comando e l'altro. Per informazioni su come digitare i comandi, vedere [Come usare la funzionalità di completamento tramite TAB nel riquadro di script e nel riquadro della console](How-to-Use-Tab-Completion-in-the-Script-Pane-and-Console-Pane.md).

Per interrompere un comando, sulla barra degli strumenti fare clic su **Arresta operazione** oppure premere <kbd>CTRL</kbd>+<kbd>INTERR</kbd>. Per interrompere un comando è anche possibile usare <kbd>CTRL</kbd>+<kbd>C</kbd> se il contesto non è ambiguo. Se ad esempio nel riquadro corrente è stato selezionato del testo, <kbd>CTRL</kbd>+<kbd>C</kbd> corrisponde all'operazione di copia.

A partire da Windows PowerShell v3, il riquadro di output è unito al riquadro della console. I vantaggi che ne conseguono sono un comportamento analogo alla console di Windows PowerShell autonoma e l'eliminazione delle differenze nelle procedure, necessarie quando i riquadri erano separati. È possibile:

- Selezionare e copiare il testo dal riquadro della console negli Appunti per incollarlo in un'altra finestra. Per selezionare il testo, fare clic tenendo premuto il pulsante del mouse nel riquadro di output e trascinare nel frattempo il mouse sopra il testo che si vuole acquisire. È anche possibile usare i tasti di direzione del cursore tenendo premuto il tasto <kbd>MAIUSC</kbd> per selezionare il testo. Quindi premere <kbd>CTRL</kbd>+<kbd>C</kbd> o fare clic sull'icona **Copia** sulla barra degli strumenti.

- Incollare il testo selezionato in una posizione corrente del cursore. Fare clic sull'icona **Incolla** nella barra degli strumenti.

- Cancellare tutto il testo nel riquadro della console. Per cancellare il contenuto del riquadro della console, è possibile fare clic sull'icona **Cancella riquadro Console** sulla barra degli strumenti oppure eseguire il comando `Clear-Host` o il relativo alias `cls`.

## <a name="see-also"></a>Vedere anche

- [Introduzione a Windows PowerShell ISE](Introducing-the-Windows-PowerShell-ISE.md)
