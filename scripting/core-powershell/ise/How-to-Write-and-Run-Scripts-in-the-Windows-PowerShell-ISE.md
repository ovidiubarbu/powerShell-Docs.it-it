---
title: Come scrivere ed eseguire script in Windows PowerShell ISE
ms.date: 2016-05-11
keywords: powershell,cmdlet
description: 
ms.topic: article
author: jpjofre
manager: dongill
ms.prod: powershell
ms.assetid: 62f916d9-b3a1-484a-bdfb-41f57112c22b
translationtype: Human Translation
ms.sourcegitcommit: 03ac4b90d299b316194f1fa932e7dbf62d4b1c8e
ms.openlocfilehash: 1c1534bc37d0a53262caffdfa60400e1ff8d98e7

---

# Come scrivere ed eseguire script in Windows PowerShell ISE
Questo argomento descrive come creare, modificare, eseguire e salvare gli script nel riquadro di script.

-   [Come creare ed eseguire script](#bkmk_1)

-   [Come scrivere e modificare testo nel riquadro di script](#bkmk_2)

-   [Come salvare uno script](#bkmk_3)

## <a name="bkmk_1"></a>Come creare ed eseguire script
È possibile aprire e modificare i file di Windows PowerShell® nel riquadro di script. Tipi di file di particolare interesse in Windows PowerShell® sono i file di script (con estensione ps1), i file di dati degli script (con estensione psd1) e i file di modulo di script (con estensione psm1). In questi file per la visualizzazione della sintassi nell'editor del riquadro di script vengono utilizzati i colori. Altri tipi di file comuni che è possibile aprire nel riquadro di script sono file di configurazione (con estensione ps1xml), file XML e file di testo.

> [!NOTE]
> I criteri di esecuzione di Windows PowerShell determinano se è possibile eseguire script e caricare profili e file di configurazione di Windows PowerShell. I criteri di esecuzione predefiniti prevedono restrizioni e impediscono l'esecuzione di tutti gli script e il caricamento di profili. Per modificare i criteri di esecuzione per consentire il caricamento e l'uso di profili, vedere [Set-ExecutionPolicy[PSITPro5_Security]](https://technet.microsoft.com/en-us/library/5690a0e1-495b-4e63-8280-65ead7bf01ab) e [about_Signing [v4]](https://technet.microsoft.com/en-us/library/fcbdd3b9-0b9f-4734-b5c7-e0dcc304fa1d).

### Per creare un nuovo file di script
Sulla barra degli strumenti fare clic su **Nuovo** o scegliere **Nuovo** dal menu **File**. Il file creato viene visualizzato in una nuova scheda file nella scheda di PowerShell corrente. Tenere presente che le schede di PowerShell sono visibili solo se ne sono presenti più di una. Per impostazione predefinita viene creato un file di tipo script (con estensione ps1), ma è possibile salvarlo con un nuovo nome e un'altra estensione. Nella stessa scheda di PowerShell si possono creare più file di script.

### Per aprire uno script esistente
Sulla barra degli strumenti fare clic su **Apri...** o scegliere **Apri** dal menu **File**. Nella finestra di dialogo **Apri** selezionare il file da aprire. Il file aperto viene visualizzato in una nuova scheda.

### Per chiudere la scheda di uno script
Fare clic sulla scheda dello script che si vuole chiudere, quindi eseguire una delle operazioni seguenti:

1.  Fare clic sull'icona **Chiudi** (X) nella scheda dello script.

2.  Scegliere **Chiudi** dal menu **File**.

Se il file è stato modificato dall'ultimo salvataggio, verrà chiesto se salvare le modifiche o ignorarle.

### Per visualizzare il percorso del file
Nella scheda del file posizionare il puntatore del mouse sul nome del file. Il percorso completo del file di script appare in una descrizione comando.

### Per eseguire uno script
Sulla barra degli strumenti fare clic su **Esegui script** o scegliere **Esegui** dal menu **File**.

### Per eseguire una parte di uno script

1.  Nel riquadro di script selezionare una parte di uno script.

2.  Sulla barra degli strumenti fare clic su **Esegui selezione** o scegliere **Esegui selezione** dal menu **File**.

### Per arrestare l'esecuzione di uno script
Sulla barra degli strumenti fare clic su **Arresta operazione**, premere CTRL\+INTERR oppure dal menu **File** scegliere **Arresta operazione**. È anche possibile premere **CTRL\+C**, a meno che non sia selezionata parte del testo. In questo caso **CTRL\+C** corrisponderà alla funzione di copia del testo selezionato.

## <a name="bkmk_2"></a>Come scrivere e modificare testo nel riquadro di script
Per modificare il testo nel riquadro di script, usare la procedura seguente. È possibile copiare, tagliare, incollare, trovare e sostituire testo. È anche possibile annullare e ripetere l'ultima operazione eseguita. I tasti di scelta rapida per eseguire queste operazioni sono identici a quelli usati in tutte le applicazioni di Windows.

### Per immettere testo nel riquadro di script

1.  Spostare il cursore sul riquadro di script facendo clic in un punto qualsiasi al suo interno o scegliendo **Vai al riquadro di script** dal menu **Visualizza**.

2.  Creare uno script. La colorazione della sintassi e la funzionalità di completamento tramite tasto TAB semplificano notevolmente l'esperienza in Windows PowerShell ISE.

3.  Per maggiori informazioni sull'uso di questa funzionalità, vedere [Come usare la funzionalità di completamento tramite TAB nel riquadro di script e nel riquadro della console](How-to-Use-Tab-Completion-in-the-Script-Pane-and-Console-Pane.md).

### Per trovare testo nel riquadro di script

1.  Per trovare testo in qualsiasi punto, premere **CTRL\+F** oppure dal menu **Modifica** scegliere **Trova nello script**.

2.  Per trovare testo dopo il cursore, premere **F3** o scegliere **Trova successivo nello script** dal menu **Modifica**.

3.  Per trovare testo prima del cursore, premere **MAIUSC\+F3** oppure dal menu **Modifica** scegliere **Trova precedente nello script**.

### Per trovare e sostituire testo nel riquadro di script
Premere **CRTL\+H** oppure dal menu **Modifica** scegliere **Sostituisci nello script**. Immettere sia il testo da trovare che il testo con cui sostituirlo e quindi premere **INVIO**.

### Per passare a una specifica riga di testo nel riquadro di script

1.  Nel riquadro di script premere **CTRL\+G** oppure dal menu **Modifica** scegliere **Vai alla riga**.

2.  Immettere un numero di riga.

### Per copiare testo nel riquadro di script

1.  Nel riquadro di script selezionare il testo da copiare.

2.  Premere **CTRL\+C**. In alternativa, sulla barra degli strumenti fare clic sull'icona **Copia** oppure dal menu **Modifica** scegliere **Copia**.

### Per tagliare testo nel riquadro di script

1.  Nel riquadro di script selezionare il testo da tagliare.

2.  Premere **CTRL\+X**. In alternativa, sulla barra degli strumenti fare clic sull'icona **Taglia** oppure dal menu **Modifica** scegliere **Taglia**.

### Per incollare testo nel riquadro di script
Premere **CTRL\+V**. In alternativa, sulla barra degli strumenti fare clic sull'icona **Incolla** oppure dal menu **Modifica** scegliere **Incolla**.

### Per annullare un'azione nel riquadro di script
Premere **CTRL\+Z**. In alternativa, sulla barra degli strumenti fare clic sull'icona **Annulla** oppure dal menu **Modifica** scegliere **Annulla**.

### Per ripetere un'azione nel riquadro di script
Premere **CTRL\+Y**. In alternativa, sulla barra degli strumenti fare clic sull'icona **Ripeti** oppure dal menu **Modifica** scegliere **Ripeti**.

## <a name="bkmk_3"></a>Come salvare uno script
Per salvare uno script e assegnargli un nome, usare la procedura seguente. Accanto al nome di uno script che non è stato ancora salvato dopo una modifica, compare un asterisco. L'asterisco sparirà dopo il salvataggio del file.

### Per salvare uno script
Premere **CTRL\+S**. In alternativa, sulla barra degli strumenti fare clic sull'icona **Salva** oppure dal menu **File** scegliere **Salva**.

### Per salvare uno script e assegnargli un nome

1.  Scegliere **Salva con nome** dal menu **File**. Verrà visualizzata la finestra di dialogo **Salva con nome**.

2.  Nella casella **Nome file** immettere un nome per il file.

3.  Nella casella **Salva come** selezionare un tipo di file. Ad esempio, nella casella **Salva come** selezionare "Script di PowerShell (\* .ps1)".

4.  Fare clic su **Salva**.

### Per salvare uno script nella codifica ASCII
Per impostazione predefinita, Windows PowerShell ISE salva i file di script (con estensione ps1), i file di dati degli script (con estensione psd1) e i file di modulo di script ( con estensione psm1) in formato Unicode (BigEndianUnicode). Per salvare uno script in un'altra codifica, ad esempio ASCII (ANSI), usare i metodi **Save** o **SaveAs** sull'oggetto [$psISE.CurrentFile](https://technet.microsoft.com/en-us/library/bc3300e4-9c17-4f00-a621-c8867126e3b3#CurrentFile).

Il comando che segue salva un nuovo script con il nome MyScript.ps1 nella codifica ASCII.

```
$psise.CurrentFile.SaveAs("MyScript.ps1", [System.Text.Encoding]::ASCII)
```

Il comando che segue sostituisce il file di script corrente con un file con lo stesso nome, ma con codifica ASCII.

```
$psise.CurrentFile.Save([System.Text.Encoding]::ASCII)
```

Il comando seguente ottiene la codifica del file corrente.

```
$psise.CurrentFile.encoding
```

Windows PowerShell ISE supporta le opzioni di codifica seguenti: ASCII, BigEndianUnicode, Unicode, UTF32, UTF7, UTF8 e predefinita. Il valore dell'opzione di codifica predefinita varia in base al sistema.

Windows PowerShell ISE non modifica la codifica degli script creati in altri editor, anche se si usano i comandi Salva o Salva con nome in Windows PowerShell ISE.

## Vedere anche
[Uso di Windows PowerShell ISE](Using-the-Windows-PowerShell-ISE.md)




<!--HONumber=Jun16_HO4-->


