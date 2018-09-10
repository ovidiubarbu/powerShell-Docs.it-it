---
ms.date: 08/14/2018
keywords: powershell,cmdlet
title: Introduzione a Windows PowerShell ISE
ms.openlocfilehash: d27a0eb594d7271121cee59f38d096995cc98648
ms.sourcegitcommit: 56b9be8503a5a1342c0b85b36f5ba6f57c281b63
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 08/21/2018
ms.locfileid: "43133157"
---
# <a name="introducing-the-windows-powershell-ise"></a>Introduzione a Windows PowerShell ISE

Windows PowerShell Integrated Scripting Environment (ISE) è un'applicazione host per Windows PowerShell. In Windows PowerShell ISE è possibile eseguire comandi e scrivere, testare e sottoporre a debug gli script in un'unica interfaccia utente grafica basata su Windows. L'interfaccia offre modifica multirighe, completamento tramite tasto TAB, colorazione della sintassi, esecuzione selettiva, Guida sensibile al contesto e supporto per lingue da destra a sinistra. Le voci di menu e i tasti di scelta rapida corrispondono a molte delle stesse attività eseguibili nella console di Windows PowerShell. Ad esempio, quando si esegue il debug di uno script in Windows PowerShell ISE, è possibile fare clic con il pulsante destro del mouse sulla riga di codice per impostare un punto di interruzione.

Provare queste funzionalità in Windows PowerShell ISE.

- Modifica su più righe: per inserire una riga vuota sotto la riga corrente nel riquadro dei comandi, premere MAIUSC+INVIO.
- Esecuzione selettiva: per eseguire parte di uno script, selezionare il testo da eseguire e quindi fare clic sul pulsante **Esegui script**. Oppure premere F5.
- Guida sensibile al contesto: digitare **Invoke-Item** e quindi premere F1. Il file della Guida viene aperto in corrispondenza dell'articolo relativo al cmdlet **Invoke-Item**.

Windows PowerShell ISE consente di personalizzarne l'aspetto in vari modi. Include anche lo script del proprio profilo Windows PowerShell.

## <a name="to-start-the-windows-powershell-ise"></a>Per avviare Windows PowerShell ISE

Fare clic su **Start**, selezionare **Windows PowerShell** e quindi fare clic su **Windows PowerShell ISE**.
In alternativa, è possibile digitare `powershell_ise.exe` in qualsiasi shell di comandi o nella casella Esegui.

## <a name="to-get-help-in-the-windows-powershell-ise"></a>Per visualizzare la Guida in Windows PowerShell ISE

Nel menu **?** fare clic su **Guida di Windows PowerShell**. Oppure premere F1. Si apre un file che descrive Windows PowerShell ISE e Windows PowerShell, con tutti gli argomenti disponibili tramite il cmdlet Get-Help.