---
ms.date: 2017-06-05
keywords: powershell,cmdlet
title: Come usare il riquadro della console in Windows PowerShell ISE
ms.assetid: 44d67705-87c7-4a69-a53e-6471fdebb757
ms.openlocfilehash: 1bb7a18c64fc12130b5af78ef55e68047d54da65
ms.sourcegitcommit: 598b7835046577841aea2211d613bb8513271a8b
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 06/08/2017
---
# <a name="how-to-use-the-console-pane-in-the-windows-powershell-ise"></a>Come usare il riquadro della console in Windows PowerShell ISE
Il riquadro della console in Windows PowerShell® Integrated Scripting Environment (ISE) funziona esattamente come la finestra della console di Windows PowerShell ISE autonoma.

Per eseguire un comando nel riquadro della console, digitare un comando e quindi premere INVIO. Per immettere più comandi da eseguire in sequenza, digitare MAIUSC+INVIO tra un comando e l'altro. Per informazioni su come digitare i comandi, vedere [Come usare la funzionalità di completamento tramite TAB nel riquadro di script e nel riquadro della console](How-to-Use-Tab-Completion-in-the-Script-Pane-and-Console-Pane.md).

Per interrompere un comando, nella barra degli strumenti fare clic su **Arresta operazione** oppure premere CTRL+INTERR. È anche possibile usare CTRL+C per interrompere un comando se il contesto non è ambiguo. Ad esempio, se nel riquadro corrente è stato selezionato testo, CTRL+C corrisponde all'operazione di copia.

A partire da Windows PowerShell v3, il riquadro di output è unito al riquadro della console. I vantaggi che ne conseguono sono un comportamento analogo alla console di Windows PowerShell autonoma e l'eliminazione delle differenze nelle procedure, necessarie quando i riquadri erano separati. È possibile:

-   Selezionare e copiare il testo dal riquadro della console negli Appunti per incollarlo in un'altra finestra. Per selezionare il testo, fare clic tenendo premuto il pulsante del mouse nel riquadro di output e trascinare nel frattempo il mouse sopra il testo che si vuole acquisire. È anche possibile usare i tasti di direzione del cursore tenendo premuto il tasto **MAIUSC** per selezionare il testo. Quindi premere CTRL+C o fare clic sull'icona **Copia** nella barra degli strumenti.

-   Incollare il testo selezionato in una posizione corrente del cursore. Fare clic sull'icona **Incolla** nella barra degli strumenti.

-   Cancellare tutto il testo nel riquadro della console. Per cancellare il contenuto del riquadro della console, è possibile fare clic sull'icona **Cancella riquadro Console** nella barra degli strumenti oppure eseguire il comando **Clear-Host** o il relativo alias, **cls**.

## <a name="see-also"></a>Vedere anche
- [Uso di Windows PowerShell ISE](Using-the-Windows-PowerShell-ISE.md)

