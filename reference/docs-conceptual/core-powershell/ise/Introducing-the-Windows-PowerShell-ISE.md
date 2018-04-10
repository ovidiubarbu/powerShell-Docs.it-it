---
ms.date: 06/05/2017
keywords: powershell,cmdlet
title: Introduzione a Windows PowerShell ISE
ms.openlocfilehash: b09e64d0258d11f1f16f96b319ef232ebdfa0c49
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/09/2018
---
# <a name="introducing-the-windows-powershell-ise"></a>Introduzione a Windows PowerShell ISE

Windows PowerShell Integrated Scripting Environment (ISE) è un'applicazione host per Windows PowerShell. In Windows PowerShell ISE è possibile eseguire comandi, nonché scrivere script, testarli e sottoporli a debug in una singola interfaccia utente grafica basata su Windows con funzionalità di modifica su più righe, completamento tramite tasto TAB, colorazione della sintassi, esecuzione selettiva, Guida sensibile al contesto e supporto per lingue da destra a sinistra. È possibile usare voci di menu e tasti di scelta rapida per completare molte delle stesse attività eseguibili nella console di Windows PowerShell. Ad esempio, durante il debug di uno script in Windows PowerShell ISE, per impostare un punto di interruzione riga in uno script, fare clic con il pulsante destro del mouse sulla riga di codice e quindi fare clic su **Attiva/disattiva punto di interruzione**.

Provare queste funzionalità in Windows PowerShell ISE.

- Modifica su più righe: per inserire una riga vuota sotto la riga corrente nel riquadro dei comandi, premere MAIUSC+INVIO.
- Esecuzione selettiva: per eseguire parte di uno script, selezionare il testo da eseguire e quindi fare clic sul pulsante **Esegui script**. Oppure premere F5.
- Guida sensibile al contesto: digitare **Invoke-Item** e quindi premere F1. Il file della Guida si apre in corrispondenza dell'argomento relativo al cmdlet **Invoke-Item**.

Windows PowerShell ISE consente di personalizzarne l'aspetto in vari modi. Include anche uno specifico profilo di Windows PowerShell in cui è possibile archiviare funzioni, alias, variabili e comandi da usare in Windows PowerShell ISE.

## <a name="to-start-the-windows-powershell-ise"></a>Per avviare Windows PowerShell ISE

Eseguire una delle operazioni seguenti:

- Fare clic sul pulsante **Start**, selezionare **Tutti i programmi**, selezionare **Windows PowerShell V2** e quindi fare clic su **Windows PowerShell ISE**.
- In Cmd.exe della console di Windows PowerShell oppure nella casella Esegui digitare **powershell_ise.exe**.

## <a name="to-get-help-in-the-windows-powershell-ise"></a>Per visualizzare la Guida in Windows PowerShell ISE

Nel menu **?** fare clic su **Guida di Windows PowerShell**. Oppure premere F1. Si apre un file che descrive Windows PowerShell ISE e Windows PowerShell, con tutti gli argomenti disponibili tramite il cmdlet Get-Help.