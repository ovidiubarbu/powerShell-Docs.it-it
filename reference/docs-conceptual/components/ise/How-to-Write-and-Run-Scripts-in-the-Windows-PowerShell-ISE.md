---
ms.date: 01/02/2020
keywords: powershell,cmdlet
title: Come scrivere ed eseguire script in Windows PowerShell ISE
ms.openlocfilehash: 2e3122a3b436ba878d2c5f9d72d4f9e024d4d031
ms.sourcegitcommit: 6545c60578f7745be015111052fd7769f8289296
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/22/2020
ms.locfileid: "79402528"
---
# <a name="how-to-write-and-run-scripts-in-the-windows-powershell-ise"></a>Come scrivere ed eseguire script in Windows PowerShell ISE

Questo articolo descrive come creare, modificare, eseguire e salvare script nel riquadro Script.

## <a name="how-to-create-and-run-scripts"></a>Come creare ed eseguire script

È possibile aprire e modificare i file di Windows PowerShell nel riquadro di script. Tipi di file di particolare interesse in Windows PowerShell sono i file di script (`.ps1`), i file di dati degli script (`.psd1`) e i file di modulo di script (`.psm1`). In questi file per la visualizzazione della sintassi nell'editor del riquadro di script vengono utilizzati i colori. Altri tipi di file comuni che è possibile aprire nel riquadro di script sono file di configurazione (`.ps1xml`), file XML e file di testo.

> [!NOTE]
> I criteri di esecuzione di Windows PowerShell determinano se è possibile eseguire script e caricare profili e file di configurazione di Windows PowerShell. I criteri di esecuzione predefiniti prevedono restrizioni e impediscono l'esecuzione di tutti gli script e il caricamento di profili. Per modificare i criteri di esecuzione in modo da consentire il caricamento e l'uso di profili, vedere [Set-ExecutionPolicy](/powershell/module/microsoft.powershell.security/set-executionpolicy) e [about_Signing](/powershell/module/microsoft.powershell.core/about/about_signing).

### <a name="to-create-a-new-script-file"></a>Per creare un nuovo file di script

Sulla barra degli strumenti fare clic su **Nuovo** oppure scegliere **Nuovo** dal menu **File**. Il file creato viene visualizzato in una nuova scheda file nella scheda di PowerShell corrente. Tenere presente che le schede di PowerShell sono visibili solo se ne sono presenti più di una. Per impostazione predefinita viene creato un file di tipo script (`.ps1`), ma è possibile salvarlo con un nuovo nome e un'altra estensione. Nella stessa scheda di PowerShell si possono creare più file di script.

### <a name="to-open-an-existing-script"></a>Per aprire uno script esistente

Sulla barra degli strumenti fare clic su **Apri** o scegliere **Apri** dal menu **File**. Nella finestra di dialogo **Apri** selezionare il file da aprire. Il file aperto viene visualizzato in una nuova scheda.

### <a name="to-close-a-script-tab"></a>Per chiudere la scheda di uno script

Fare clic sull'icona **Chiudi** (**X**) della scheda del file che si vuole chiudere o selezionare il menu **File** e fare clic su **Chiudi**.

Se il file è stato modificato dall'ultimo salvataggio, viene chiesto se salvare le modifiche o ignorarle.

### <a name="to-display-the-file-path"></a>Per visualizzare il percorso del file

Nella scheda del file posizionare il puntatore del mouse sul nome del file. Il percorso completo del file di script appare in una descrizione comando.

### <a name="to-run-a-script"></a>Per eseguire uno script

Sulla barra degli strumenti fare clic su **Esegui script** o scegliere **Esegui** dal menu **File**.

### <a name="to-run-a-portion-of-a-script"></a>Per eseguire una parte di uno script

1. Nel riquadro di script selezionare una parte di uno script.
2. Sulla barra degli strumenti fare clic su **Esegui selezione** o scegliere **Esegui selezione** dal menu **File**.

### <a name="to-stop-a-running-script"></a>Per arrestare l'esecuzione di uno script

È possibile arrestare uno script in esecuzione in diversi modi.

- Fare clic su **Arresta operazione** sulla barra degli strumenti
- Premere <kbd>CTRL</kbd>+<kbd>INTERR</kbd>
- Selezionare il menu **File** e fare clic su **Arresta operazione**.

È anche possibile premere <kbd>CTRL</kbd>+<kbd>C</kbd>, a meno che non sia selezionata parte del testo. In questo caso <kbd>CTRL</kbd>+<kbd>C</kbd> corrisponderà alla funzione di copia del testo selezionato.

## <a name="how-to-write-and-edit-text-in-the-script-pane"></a>Come scrivere e modificare testo nel riquadro di script

È possibile copiare, tagliare, incollare, trovare e sostituire testo nel riquadro Script. È anche possibile annullare e ripetere l'ultima operazione eseguita. I tasti di scelta rapida per eseguire queste operazioni sono identici a quelli usati in tutte le applicazioni di Windows.

### <a name="to-enter-text-in-the-script-pane"></a>Per immettere testo nel riquadro di script

1. Spostare il cursore sul riquadro di script facendo clic in un punto qualsiasi al suo interno o scegliendo **Vai al riquadro di script** dal menu **Visualizza**.
2. Creare uno script. La colorazione della sintassi e la funzionalità di completamento tramite tasto TAB offrono un'esperienza di modifica più avanzata in Windows PowerShell ISE.
3. Per maggiori informazioni sull'uso di questa funzionalità, vedere [Come usare la funzionalità di completamento tramite TAB nel riquadro di script e nel riquadro della console](How-to-Use-Tab-Completion-in-the-Script-Pane-and-Console-Pane.md).

### <a name="to-find-text-in-the-script-pane"></a>Per trovare testo nel riquadro di script

1. Per trovare testo in qualsiasi punto, premere <kbd>CTRL</kbd>+<kbd>F</kbd> oppure dal menu **Modifica** scegliere **Trova nello script**.
2. Per trovare testo dopo il cursore, premere <kbd>F3</kbd> o scegliere **Trova successivo nello script** dal menu **Modifica**.
3. Per trovare testo prima del cursore, premere <kbd>MAIUSC</kbd>+<kbd>F3</kbd> oppure dal menu **Modifica** scegliere **Trova precedente nello script**.

### <a name="to-find-and-replace-text-in-the-script-pane"></a>Per trovare e sostituire testo nel riquadro di script

Premere <kbd>CTRL</kbd>+<kbd>H</kbd> o scegliere **Sostituisci nello script** dal menu **Modifica**. Immettere il testo che si vuole trovare e il testo sostitutivo e quindi premere <kbd>INVIO</kbd>.

### <a name="to-go-to-a-particular-line-of-text-in-the-script-pane"></a>Per passare a una specifica riga di testo nel riquadro di script

1. Nel riquadro di script premere <kbd>CTRL</kbd>+<kbd>G</kbd> oppure dal menu **Modifica** scegliere **Vai alla riga**.

2. Immettere un numero di riga.

### <a name="to-copy-text-in-the-script-pane"></a>Per copiare testo nel riquadro di script

1. Nel riquadro di script selezionare il testo da copiare.

2. Premere <kbd>CTRL</kbd>+<kbd>C</kbd>. In alternativa, sulla barra degli strumenti fare clic sull'icona **Copia** oppure dal menu **Modifica** scegliere **Copia**.

### <a name="to-cut-text-in-the-script-pane"></a>Per tagliare testo nel riquadro di script

1. Nel riquadro di script selezionare il testo da tagliare.
2. Premere <kbd>CTRL</kbd>+<kbd>X</kbd>. In alternativa, sulla barra degli strumenti fare clic sull'icona **Taglia** oppure dal menu **Modifica** scegliere **Taglia**.

### <a name="to-paste-text-into-the-script-pane"></a>Per incollare testo nel riquadro di script

Premere <kbd>CTRL</kbd>+<kbd>V</kbd>. In alternativa, sulla barra degli strumenti fare clic sull'icona **Incolla** oppure dal menu **Modifica** scegliere **Incolla**.

### <a name="to-undo-an-action-in-the-script-pane"></a>Per annullare un'azione nel riquadro di script

Premere <kbd>CTRL</kbd>+<kbd>Z</kbd>. In alternativa, sulla barra degli strumenti fare clic sull'icona **Annulla** oppure dal menu **Modifica** scegliere **Annulla**.

### <a name="to-redo-an-action-in-the-script-pane"></a>Per ripetere un'azione nel riquadro di script

Premere <kbd>CTRL</kbd>+<kbd>Y</kbd>. In alternativa, sulla barra degli strumenti fare clic sull'icona **Ripeti** oppure dal menu **Modifica** scegliere **Ripeti**.

## <a name="how-to-save-a-script"></a>Come salvare uno script

Accanto al nome dello script che non è stato ancora salvato dopo una modifica compare un asterisco. L'asterisco sparirà dopo il salvataggio del file.

### <a name="to-save-a-script"></a>Per salvare uno script

Premere <kbd>CTRL</kbd>+<kbd>S</kbd>. In alternativa, sulla barra degli strumenti fare clic sull'icona **Salva** oppure dal menu **File** scegliere **Salva**.

### <a name="to-save-and-name-a-script"></a>Per salvare uno script e assegnargli un nome

1. Scegliere **Salva con nome** dal menu **File**. Verrà visualizzata la finestra di dialogo **Salva con nome**.
2. Nella casella **Nome file** immettere un nome per il file.
3. Nella casella **Salva come** selezionare un tipo di file. Ad esempio, nella casella **Tipo file** selezionare "Script di PowerShell (`*.ps1`)".
4. Fare clic su **Salva**.

### <a name="to-save-a-script-in-ascii-encoding"></a>Per salvare uno script nella codifica ASCII

Per impostazione predefinita, Windows PowerShell ISE salva i file di script (`.ps1`), i file di dati degli script (`.psd1`) e i file di modulo di script (`.psm1`) in formato Unicode (BigEndianUnicode). Per salvare uno script in un'altra codifica, ad esempio ASCII (ANSI), usare i metodi **Save** o **SaveAs** sull'oggetto [$psISE.CurrentFile](object-model/the-ise-object-model-hierarchy.md).

Il comando che segue salva un nuovo script con il nome MyScript.ps1 nella codifica ASCII.

```powershell
$psISE.CurrentFile.SaveAs("MyScript.ps1", [System.Text.Encoding]::ASCII)
```

Il comando che segue sostituisce il file di script corrente con un file con lo stesso nome, ma con codifica ASCII.

```powershell
$psISE.CurrentFile.Save([System.Text.Encoding]::ASCII)
```

Il comando seguente ottiene la codifica del file corrente.

```powershell
$psISE.CurrentFile.encoding
```

Windows PowerShell ISE supporta le opzioni di codifica seguenti: ASCII, BigEndianUnicode, Unicode, UTF32, UTF7, UTF8 e Default. Il valore dell'opzione di codifica predefinita varia in base al sistema.

Windows PowerShell ISE non modifica la codifica dei file script quando si usano i comandi Salva o Salva con nome.

## <a name="see-also"></a>Vedere anche

- [Esplorazione di Windows PowerShell ISE](exploring-the-windows-powershell-ise.md)
