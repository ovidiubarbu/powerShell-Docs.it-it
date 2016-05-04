---
title: Come creare una scheda di PowerShell in Windows PowerShell ISE
ms.custom: na
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: c10c18c7-9ece-4fd0-83dc-a19c53d4fd83
---
# Come creare una scheda di PowerShell in Windows PowerShell ISE
Le schede in [!INCLUDE[ise_1](../Token/ise_1_md.md)] consentono di creare e usare simultaneamente diversi ambienti di esecuzione all'interno della stessa applicazione. Ogni scheda di PowerShell corrisponde a una sessione o a un ambiente di esecuzione separato.

> [!NOTE]
> Variabili, funzioni e alias creati in una scheda non vengono riportati in un'altra scheda. Si tratta di diverse sessioni di Windows PowerShell.

Usare la procedura seguente per aprire o chiudere una scheda in [!INCLUDE[wps_2](../Token/wps_2_md.md)]. Per rinominare una scheda, impostare la proprietà [DisplayName](https://technet.microsoft.com/en-us/library/a9b58556-951b-4f48-b3ae-b351b7564360#Displayname) nell'oggetto di scripting della scheda di [!INCLUDE[wps_2](../Token/wps_2_md.md)].

## Per creare e usare una nuova scheda di PowerShell
Nel menu **File** fare clic su **Nuova scheda di PowerShell**. La nuova scheda di PowerShell viene visualizzata sempre come finestra attiva. Le schede di PowerShell sono numerate in modo incrementale nell'ordine di apertura. Ogni scheda è associata alla propria finestra della console di Windows PowerShell. È possibile tenere aperte fino a 32 schede di PowerShell con le rispettive sessioni per volta (è previsto un limite di 8 in [!INCLUDE[ise_2](../Token/ise_2_md.md)] 2.0.)

Tenere presente che, facendo clic sulle icone **Nuova** o **Apri** nella barra degli strumenti, non verrà creata una nuova scheda con una sessione distinta.  Al contrario, questi pulsanti aprono un file di script nuovo o esistente nella scheda attualmente attiva con una sessione. È possibile tenere aperti più file di script con ogni scheda e sessione. Le schede degli script per una sessione vengono visualizzate sotto le schede di sessione solo quando la sessione associata è attiva.

Per rendere attiva una scheda di PowerShell, fare clic sulla scheda. Per scegliere fra tutte le schede di PowerShell aperte, nel menu **Visualizza** fare clic sulla scheda di PowerShell da usare.

## Per creare e usare una nuova scheda di PowerShell remota
Nel menu **File** fare clic su **Scheda Nuova sessione PowerShell remota** per stabilire una sessione in un computer remoto. Verrà visualizzata una finestra di dialogo che richiede di immettere i dettagli necessari per stabilire la connessione remota. La scheda remota funziona come una scheda di PowerShell locale, ma i comandi e gli script vengono eseguiti nel computer remoto.

## Per chiudere una scheda di PowerShell
Per chiudere una scheda, è possibile usare una delle tecniche seguenti:

-   Fare clic sulla scheda che si vuole chiudere.

-   Nel menu **File** fare clic su **Chiudi scheda di PowerShell** o fare clic sul pulsante Chiudi (**X**) in una scheda attiva per chiuderla.

Se sono presenti file non salvati aperti nella scheda di PowerShell che si vuole chiudere, viene richiesto di salvare o rimuovere tali file. Per altre informazioni su come salvare uno script, vedere [Come salvare uno script](https://technet.microsoft.com/en-us/library/162f594d-efd3-4234-9960-45e56e6eadc8).

## Vedere anche
[Uso di Windows PowerShell ISE](../Topic/Using-the-Windows-PowerShell-ISE.md)
[Come usare il riquadro della console in Windows PowerShell ISE](../Topic/How-to-Use-the-Console-Pane-in-the-Windows-PowerShell-ISE.md)



<!--HONumber=Apr16_HO2-->


