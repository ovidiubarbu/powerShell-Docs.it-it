---
ms.date: 2017-06-05
keywords: powershell,cmdlet
title: Come scrivere ed eseguire script in Windows PowerShell ISE
ms.assetid: 62f916d9-b3a1-484a-bdfb-41f57112c22b
ms.openlocfilehash: 77d8ae81cb03f03b3b5d044e6503bbb23cb5b771
ms.sourcegitcommit: 99227f62dcf827354770eb2c3e95c5cf6a3118b4
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 03/15/2018
---
# <a name="how-to-write-and-run-scripts-in-the-windows-powershell-ise"></a>Come scrivere ed eseguire script in Windows PowerShell ISE
Questo argomento descrive come creare, modificare, eseguire e salvare gli script nel riquadro di script.

## <a name="how-to-create-and-run-scripts"></a>Come creare ed eseguire script
È possibile aprire e modificare i file di Windows PowerShell nel riquadro di script. Tipi di file di particolare interesse in Windows PowerShell sono i file di script (con estensione PS1), i file di dati degli script (con estensione PSD1) e i file di modulo di script (con estensione PSM1). In questi file per la visualizzazione della sintassi nell'editor del riquadro di script vengono utilizzati i colori. Altri tipi di file comuni che è possibile aprire nel riquadro di script sono file di configurazione (con estensione ps1xml), file XML e file di testo.

> [!NOTE]
> I criteri di esecuzione di Windows PowerShell determinano se è possibile eseguire script e caricare profili e file di configurazione di Windows PowerShell. I criteri di esecuzione predefiniti prevedono restrizioni e impediscono l'esecuzione di tutti gli script e il caricamento di profili. Per modificare i criteri di esecuzione per consentire il caricamento e l'uso di profili, vedere [Set-ExecutionPolicy[PSITPro5_Security]](https://technet.microsoft.com/library/5690a0e1-495b-4e63-8280-65ead7bf01ab) e [about_Signing [v4]](https://technet.microsoft.com/library/fcbdd3b9-0b9f-4734-b5c7-e0dcc304fa1d).

### <a name="to-create-a-new-script-file"></a>Per creare un nuovo file di script
Sulla barra degli strumenti fare clic su **Nuovo** o scegliere **Nuovo** dal menu **File**. Il file creato viene visualizzato in una nuova scheda file nella scheda di PowerShell corrente. Tenere presente che le schede di PowerShell sono visibili solo se ne sono presenti più di una. Per impostazione predefinita viene creato un file di tipo script (con estensione ps1), ma è possibile salvarlo con un nuovo nome e un'altra estensione. Nella stessa scheda di PowerShell si possono creare più file di script.

### <a name="to-open-an-existing-script"></a>Per aprire uno script esistente
Sulla barra degli strumenti fare clic su **Apri** o scegliere **Apri** dal menu **File**. Nella finestra di dialogo **Apri** selezionare il file da aprire. Il file aperto viene visualizzato in una nuova scheda.

### <a name="to-close-a-script-tab"></a>Per chiudere la scheda di uno script
Fare clic sulla scheda dello script che si vuole chiudere, quindi eseguire una delle operazioni seguenti:

1. Fare clic sull'icona **Chiudi** (X) nella scheda dello script.

2. Scegliere **Chiudi** dal menu **File**.

Se il file è stato modificato dall'ultimo salvataggio, verrà chiesto se salvare le modifiche o ignorarle.

### <a name="to-display-the-file-path"></a>Per visualizzare il percorso del file
Nella scheda del file posizionare il puntatore del mouse sul nome del file. Il percorso completo del file di script appare in una descrizione comando.

### <a name="to-run-a-script"></a>Per eseguire uno script
Sulla barra degli strumenti fare clic su **Esegui script** o scegliere **Esegui** dal menu **File**.

### <a name="to-run-a-portion-of-a-script"></a>Per eseguire una parte di uno script

1. Nel riquadro di script selezionare una parte di uno script.

2. Sulla barra degli strumenti fare clic su **Esegui selezione** o scegliere **Esegui selezione** dal menu **File**.

### <a name="to-stop-a-running-script"></a>Per arrestare l'esecuzione di uno script
Sulla barra degli strumenti fare clic su **Arresta operazione**, premere CTRL+INTERR o scegliere **Arresta operazione** dal menu **File**. È anche possibile premere **CTRL+C**, a meno che non sia attualmente selezionato del testo. In quel caso, **CTRL+C** corrisponderà alla funzione di copia del testo selezionato.

## <a name="how-to-write-and-edit-text-in-the-script-pane"></a>Come scrivere e modificare testo nel riquadro di script
Per modificare il testo nel riquadro di script, usare la procedura seguente. È possibile copiare, tagliare, incollare, trovare e sostituire testo. È anche possibile annullare e ripetere l'ultima operazione eseguita. I tasti di scelta rapida per eseguire queste operazioni sono identici a quelli usati in tutte le applicazioni di Windows.

### <a name="to-enter-text-in-the-script-pane"></a>Per immettere testo nel riquadro di script

1. Spostare il cursore sul riquadro di script facendo clic in un punto qualsiasi al suo interno o scegliendo **Vai al riquadro di script** dal menu **Visualizza**.

2. Creare uno script. La colorazione della sintassi e la funzionalità di completamento tramite tasto TAB semplificano notevolmente l'esperienza in Windows PowerShell ISE.

3. Per maggiori informazioni sull'uso di questa funzionalità, vedere [Come usare la funzionalità di completamento tramite TAB nel riquadro di script e nel riquadro della console](How-to-Use-Tab-Completion-in-the-Script-Pane-and-Console-Pane.md).

### <a name="to-find-text-in-the-script-pane"></a>Per trovare testo nel riquadro di script

1. Per trovare testo in qualsiasi punto, premere **CTRL+F** o scegliere **Trova nello script** dal menu **Modifica**.

2. Per trovare testo dopo il cursore, premere **F3** o scegliere **Trova successivo nello script** dal menu **Modifica**.

3. Per trovare testo prima del cursore, premere **MAIUSC+F3** o scegliere **Trova precedente nello script** dal menu **Modifica**.

### <a name="to-find-and-replace-text-in-the-script-pane"></a>Per trovare e sostituire testo nel riquadro di script
Premere **CRTL+H** o scegliere **Sostituisci nello script** dal menu **Modifica**. Immettere sia il testo da trovare che il testo con cui sostituirlo e quindi premere **INVIO**.

### <a name="to-go-to-a-particular-line-of-text-in-the-script-pane"></a>Per passare a una specifica riga di testo nel riquadro di script

1. Nel riquadro di script premere **CTRL+G** o scegliere **Vai alla riga** dal menu **Modifica**.

2. Immettere un numero di riga.

### <a name="to-copy-text-in-the-script-pane"></a>Per copiare testo nel riquadro di script

1. Nel riquadro di script selezionare il testo da copiare.

2. Premere **CTRL+C**, fare clic sull'icona **Copia** sulla barra degli strumenti o scegliere **Copia** dal menu **Modifica**.

### <a name="to-cut-text-in-the-script-pane"></a>Per tagliare testo nel riquadro di script

1. Nel riquadro di script selezionare il testo da tagliare.

2. Premere **CTRL+X**, fare clic sull'icona **Taglia** sulla barra degli strumenti o scegliere **Taglia** dal menu **Modifica**.

### <a name="to-paste-text-into-the-script-pane"></a>Per incollare testo nel riquadro di script
Premere **CTRL+V**, fare clic sull'icona **Incolla** sulla barra degli strumenti o scegliere **Incolla** dal menu **Modifica**.

### <a name="to-undo-an-action-in-the-script-pane"></a>Per annullare un'azione nel riquadro di script
Premere **CTRL+Z**, fare clic sull'icona **Annulla** sulla barra degli strumenti o scegliere **Annulla** dal menu **Modifica**.

### <a name="to-redo-an-action-in-the-script-pane"></a>Per ripetere un'azione nel riquadro di script
Premere **CTRL+Y**, fare clic sull'icona **Ripeti** sulla barra degli strumenti o scegliere **Ripeti** dal menu **Modifica**.

## <a name="how-to-save-a-script"></a>Come salvare uno script
Per salvare uno script e assegnargli un nome, usare la procedura seguente. Accanto al nome di uno script che non è stato ancora salvato dopo una modifica, compare un asterisco. L'asterisco sparirà dopo il salvataggio del file.

### <a name="to-save-a-script"></a>Per salvare uno script
Premere **CTRL+S**, fare clic sull'icona **Salva** sulla barra degli strumenti o scegliere **Salva** dal menu **File**.

### <a name="to-save-and-name-a-script"></a>Per salvare uno script e assegnargli un nome

1. Scegliere **Salva con nome** dal menu **File**. Verrà visualizzata la finestra di dialogo **Salva con nome**.

2. Nella casella **Nome file** immettere un nome per il file.

3. Nella casella **Salva come** selezionare un tipo di file. Ad esempio, nella casella **Salva come** selezionare "Script di PowerShell (\* .ps1)".

4. Fare clic su **Salva**.

### <a name="to-save-a-script-in-ascii-encoding"></a>Per salvare uno script nella codifica ASCII
Per impostazione predefinita, Windows PowerShell ISE salva i nuovi file di script (con estensione PS1), i file di dati di script (con estensione PSD1) e i file di modulo di script (con estensione PSM1) in formato Unicode (BigEndianUnicode). Â Per salvare uno script in un'altra codifica, ad esempio ASCII (ANSI), utilizzare i metodi **Save** o **SaveAs** nell’oggetto [$psISE.CurrentFile](https://technet.microsoft.com/en-us/library/bc3300e4-9c17-4f00-a621-c8867126e3b3#CurrentFile).

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

## <a name="see-also"></a>Vedere anche
- [Esplorazione di Windows PowerShell ISE](../../getting-started/fundamental/exploring-the-windows-powershell-ise.md)
