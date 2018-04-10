---
ms.date: 06/05/2017
keywords: powershell,cmdlet
title: Come creare una scheda di PowerShell in Windows PowerShell ISE
ms.assetid: c10c18c7-9ece-4fd0-83dc-a19c53d4fd83
ms.openlocfilehash: 4d4388d889f2178b2cd24cb0f3350aee37327625
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/09/2018
---
# <a name="how-to-create-a-powershell-tab-in-windows-powershell-ise"></a>Come creare una scheda di PowerShell in Windows PowerShell ISE

Le schede in Windows PowerShell Integrated Scripting Environment (ISE) consentono di creare e usare simultaneamente diversi ambienti di esecuzione all'interno della stessa applicazione.
Ogni scheda di PowerShell corrisponde a una sessione o a un ambiente di esecuzione separato.

> **NOTA**:
>
> Variabili, funzioni e alias creati in una scheda non vengono riportati in un'altra scheda. Si tratta di diverse sessioni di Windows PowerShell.

Usare la procedura seguente per aprire o chiudere una scheda in Windows PowerShell.
Per rinominare una scheda, impostare la proprietà [DisplayName](The-PowerShellTab-Object.md#displayname) nell'oggetto di scripting della scheda di Windows PowerShell.

## <a name="to-create-and-use-a-new-powershell-tab"></a>Per creare e usare una nuova scheda di PowerShell

Nel menu **File** fare clic su **Nuova scheda di PowerShell**. La nuova scheda di PowerShell viene visualizzata sempre come finestra attiva.
Le schede di PowerShell sono numerate in modo incrementale nell'ordine di apertura.
Ogni scheda è associata alla propria finestra della console di Windows PowerShell.
È possibile tenere aperte fino a 32 schede di PowerShell con le rispettive sessioni per volta. In Windows PowerShell ISE 2.0 questa opzione è limitata a 8 schede.

Tenere presente che, facendo clic sulle icone **Nuova** o **Apri** nella barra degli strumenti, non verrà creata una nuova scheda con una sessione distinta.
Al contrario, questi pulsanti aprono un file di script nuovo o esistente nella scheda attualmente attiva con una sessione.
È possibile tenere aperti più file di script con ogni scheda e sessione.
Le schede degli script per una sessione vengono visualizzate sotto le schede di sessione solo quando la sessione associata è attiva.

Per rendere attiva una scheda di PowerShell, fare clic sulla scheda. Per scegliere fra tutte le schede di PowerShell aperte, nel menu **Visualizza** fare clic sulla scheda di PowerShell da usare.

## <a name="to-create-and-use-a-new-remote-powershell-tab"></a>Per creare e usare una nuova scheda di PowerShell remota

Nel menu **File** fare clic su **Scheda Nuova sessione PowerShell remota** per stabilire una sessione in un computer remoto.
Verrà visualizzata una finestra di dialogo che richiede di immettere i dettagli necessari per stabilire la connessione remota.
La scheda remota funziona come una scheda di PowerShell locale, ma i comandi e gli script vengono eseguiti nel computer remoto.

## <a name="to-close-a-powershell-tab"></a>Per chiudere una scheda di PowerShell

Per chiudere una scheda, è possibile usare una delle tecniche seguenti:

- Fare clic sulla scheda che si vuole chiudere.

- Nel menu **File** fare clic su **Chiudi scheda di PowerShell** o fare clic sul pulsante Chiudi (**X**) in una scheda attiva per chiuderla.

Se sono presenti file non salvati aperti nella scheda di PowerShell che si vuole chiudere, viene richiesto di salvare o rimuovere tali file.
Per altre informazioni su come salvare uno script, vedere [Come salvare uno script](How-to-Write-and-Run-Scripts-in-the-Windows-PowerShell-ISE.md#how-to-save-a-script).

## <a name="see-also"></a>Vedere anche

- [Introduzione a Windows PowerShell ISE](Introducing-the-Windows-PowerShell-ISE.md)
- [Come usare il riquadro della console in Windows PowerShell ISE](How-to-Use-the-Console-Pane-in-the-Windows-PowerShell-ISE.md)