---
ms.date: 08/14/2018
keywords: powershell,cmdlet
title: Introduzione a Windows PowerShell ISE
ms.openlocfilehash: 729c8535dbcfcd2c51070b8beac5d328375f36ae
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62057424"
---
# <a name="the-windows-powershell-ise"></a>Windows PowerShell ISE

Windows PowerShell Integrated Scripting Environment (ISE) è un'applicazione host per Windows PowerShell. Nell'ambiente ISE è possibile eseguire comandi e scrivere, testare e sottoporre a debug gli script in un'unica interfaccia utente grafica basata su Windows. L'ISE supporta modifica su più righe, completamento tramite tasto TAB, colorazione della sintassi, esecuzione selettiva, Guida sensibile al contesto e lingue da destra a sinistra. Le voci di menu e i tasti di scelta rapida corrispondono a molte delle stesse attività eseguibili nella console di Windows PowerShell. Ad esempio, quando si esegue il debug di uno script nell'ISE, è possibile fare clic con il pulsante destro del mouse su una riga di codice nel riquadro di modifica per impostare un punto di interruzione.

## <a name="support"></a>Supporto

L'ambiente ISE è stato introdotto con Windows PowerShell V2 ed è stato riprogettato con PowerShell V3. L'ISE è supportato in tutte le versioni supportate di Windows PowerShell fino a Windows PowerShell V5.1, inclusa. L'ISE è tuttavia in modalità di manutenzione ed è probabile che non vengano aggiunte nuove funzionalità.
Inoltre, non è previsto alcun supporto per l'ambiente ISE con PowerShell v6 e versioni successive. Gli utenti che vogliono usare uno strumento grafico per gestire gli script e altri aspetti di PowerShell, possono prendere in considerazione [Visual Studio Code](https://code.visualstudio.com/).

## <a name="key-features"></a>Funzionalità principali

Le funzionalità principali in Windows PowerShell ISE includono:

- Modifica su più righe: per inserire una riga vuota sotto la riga corrente nel riquadro comandi, premere MAIUSC+INVIO.
- Esecuzione selettiva: per eseguire parte di uno script, selezionare il testo da eseguire e quindi fare clic sul pulsante **Esegui script**. Oppure premere F5.
- Guida sensibile al contesto: digitare **Invoke-Item** e quindi premere F1. Il file della Guida viene aperto in corrispondenza dell'articolo relativo al cmdlet **Invoke-Item**.

Windows PowerShell ISE consente di personalizzarne l'aspetto in vari modi. Include anche lo script del proprio profilo Windows PowerShell.

## <a name="to-start-the-windows-powershell-ise"></a>Per avviare Windows PowerShell ISE

Fare clic su **Start**, selezionare **Windows PowerShell** e quindi fare clic su **Windows PowerShell ISE**.
In alternativa, è possibile digitare `powershell_ise.exe` in qualsiasi shell di comandi o nella casella Esegui.

## <a name="to-get-help-in-the-windows-powershell-ise"></a>Per visualizzare la Guida in Windows PowerShell ISE

Nel menu **?** fare clic su **Guida di Windows PowerShell**. Oppure premere F1. Si apre un file che descrive Windows PowerShell ISE e Windows PowerShell, con tutti gli argomenti disponibili tramite il cmdlet Get-Help.
