---
ms.date: 08/14/2018
keywords: powershell,cmdlet
title: Introduzione a Windows PowerShell ISE
ms.openlocfilehash: 09a28b295855fd2a3c62bba8a681399dae3454f8
ms.sourcegitcommit: 3402a478cf118c11a5642038eb117bc76553e3ab
ms.translationtype: MTE95
ms.contentlocale: it-IT
ms.lasthandoff: 12/14/2018
ms.locfileid: "53411583"
---
# <a name="the-windows-powershell-ise"></a>Windows PowerShell ISE

Windows PowerShell Integrated Scripting Environment (ISE) è un'applicazione host per Windows PowerShell. In ISE, è possibile eseguire comandi e scrittura, test e il debug degli script in una singola basata su Windows interfaccia utente grafica. ISE fornisce modifica su più righe, completamento tramite tasto tab, colorazione della sintassi, esecuzione selettiva, Guida sensibile al contesto e supporto per lingue da destra a sinistra. Le voci di menu e i tasti di scelta rapida corrispondono a molte delle stesse attività eseguibili nella console di Windows PowerShell. Ad esempio, quando si esegue il debug di uno script in ISE, è possibile fare doppio clic su una riga di codice nel riquadro di modifica per impostare un punto di interruzione.

## <a name="support"></a>Supporto

ISE è stato introdotto con Windows PowerShell V2 ed è stata riprogettata con PowerShell V3. ISE è supportata in tutte le versioni supportate di Windows PowerShell fino a e tra cui Windows PowerShell V5.1. ISE, tuttavia, è in modalità maintennce e non nuove funzionalità sono probabilmente da aggiungere.
Inoltre, non vi è alcun supporto per l'ambiente ISE con PowerShell v6 e altro ancora. Gli utenti che desiderano uno strumento grafico con cui si desidera gestire scrips PowerShell e così via, è necessario considerare [Visual Studio Code](https://code.visualstudio.com/).

## <a name="key-features"></a>Funzionalità principali

Le funzionalità principali di Windows PowerShell ISE includono:

- Modifica su più righe: per inserire una riga vuota sotto la riga corrente nel riquadro comandi, premere MAIUSC+INVIO.
- Esecuzione selettiva: per eseguire parte di uno script, selezionare il testo da eseguire e quindi fare clic sul pulsante **Esegui script**. Oppure premere F5.
- Guida sensibile al contesto: digitare **Invoke-Item** e quindi premere F1. Il file della Guida viene aperto in corrispondenza dell'articolo relativo al cmdlet **Invoke-Item**.

Windows PowerShell ISE consente di personalizzarne l'aspetto in vari modi. Include anche lo script del proprio profilo Windows PowerShell.

## <a name="to-start-the-windows-powershell-ise"></a>Per avviare Windows PowerShell ISE

Fare clic su **Start**, selezionare **Windows PowerShell** e quindi fare clic su **Windows PowerShell ISE**.
In alternativa, è possibile digitare `powershell_ise.exe` in qualsiasi shell di comandi o nella casella Esegui.

## <a name="to-get-help-in-the-windows-powershell-ise"></a>Per visualizzare la Guida in Windows PowerShell ISE

Nel menu **?** fare clic su **Guida di Windows PowerShell**. Oppure premere F1. Si apre un file che descrive Windows PowerShell ISE e Windows PowerShell, con tutti gli argomenti disponibili tramite il cmdlet Get-Help.
