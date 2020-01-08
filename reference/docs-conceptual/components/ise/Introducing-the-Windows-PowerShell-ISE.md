---
ms.date: 08/14/2018
keywords: powershell,cmdlet
title: Introduzione a Windows PowerShell ISE
ms.openlocfilehash: 3e4471d0982ba4d7ef1a9d59906a9ff297f6f7cb
ms.sourcegitcommit: 058a6e86eac1b27ca57a11687019df98709ed709
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/08/2020
ms.locfileid: "75736199"
---
# <a name="the-windows-powershell-ise"></a>Windows PowerShell ISE

Windows PowerShell Integrated Scripting Environment (ISE) è un'applicazione host per Windows PowerShell. Nell'ambiente ISE è possibile eseguire comandi e scrivere, testare e sottoporre a debug gli script in un'unica interfaccia utente grafica basata su Windows. L'ISE supporta modifica su più righe, completamento tramite tasto TAB, colorazione della sintassi, esecuzione selettiva, Guida sensibile al contesto e lingue da destra a sinistra. Le voci di menu e i tasti di scelta rapida corrispondono a molte delle stesse attività eseguibili nella console di Windows PowerShell. Ad esempio, quando si esegue il debug di uno script nell'ISE, è possibile fare clic con il pulsante destro del mouse su una riga di codice nel riquadro di modifica per impostare un punto di interruzione.

## <a name="support"></a>Supporto

L'ambiente ISE è stato introdotto con Windows PowerShell V2 ed è stato riprogettato con PowerShell V3. L'ISE è supportato in tutte le versioni supportate di Windows PowerShell fino a Windows PowerShell V5.1, inclusa.

> [!NOTE]
> Le funzionalità di PowerShell ISE non vengono più sviluppate in modo attivo. Questo componente distribuito con Windows continua a essere supportato per la sicurezza e per le correzioni a priorità elevata.
> Attualmente non è prevista la rimozione di ISE da Windows.
>
> Non è previsto il supporto per l'ambiente ISE in PowerShell v6 e versioni successive. Gli utenti che vogliono sostituire ISE possono usare [Visual Studio Code](https://code.visualstudio.com/) con l'[estensione PowerShell](https://marketplace.visualstudio.com/items?itemName=ms-vscode.PowerShell).

## <a name="key-features"></a>Funzionalità principali

Le funzionalità principali in Windows PowerShell ISE includono:

- Modifica su più righe: per inserire una riga vuota sotto la riga corrente nel riquadro comandi, premere <kbd>MAIUSC</kbd>+<kbd>INVIO</kbd>.
- Esecuzione selettiva: per eseguire parte di uno script, selezionare il testo da eseguire e quindi fare clic sul pulsante **Esegui script**. Oppure premere <kbd>F5</kbd>.
- Guida sensibile al contesto: Digitare `Invoke-Item` e quindi premere <kbd>F1</kbd>. Il file della Guida viene aperto in corrispondenza dell'articolo relativo al cmdlet `Invoke-Item`.

Windows PowerShell ISE consente di personalizzarne l'aspetto in vari modi. Include anche lo script del proprio profilo Windows PowerShell.

## <a name="to-start-the-windows-powershell-ise"></a>Per avviare Windows PowerShell ISE

Fare clic su **Start**, selezionare **Windows PowerShell** e quindi fare clic su **Windows PowerShell ISE**.
In alternativa, è possibile digitare `powershell_ise.exe` in qualsiasi shell di comandi o nella casella Esegui.

## <a name="to-get-help-in-the-windows-powershell-ise"></a>Per visualizzare la Guida in Windows PowerShell ISE

Nel menu **?** fare clic su **Guida di Windows PowerShell**. Oppure premere <kbd>F1</kbd>. Si apre un file che descrive Windows PowerShell ISE e Windows PowerShell, con tutti gli argomenti della Guida disponibili tramite il cmdlet `Get-Help`.
