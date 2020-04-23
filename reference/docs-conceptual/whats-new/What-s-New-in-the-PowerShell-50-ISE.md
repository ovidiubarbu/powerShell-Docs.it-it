---
ms.date: 09/06/2019
keywords: powershell,cmdlet
title: Novità di PowerShell 5.0 ISE
ms.openlocfilehash: 8f15e99c5a6ae33aeae9bd33eb0cf58fb27e3b90
ms.sourcegitcommit: 6545c60578f7745be015111052fd7769f8289296
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/22/2020
ms.locfileid: "74416636"
---
# <a name="whats-new-in-the-windows-powershell-50-ise"></a>Novità di Windows PowerShell 5.0 ISE

Questo argomento illustra le funzionalità nuove e aggiornate introdotte nella versione 5.0 di Windows PowerShell Integrated Scripting Environment (ISE).

> [!NOTE]
> Le funzionalità di PowerShell ISE non vengono più sviluppate in modo attivo. Questo componente distribuito con Windows continua a essere supportato per la sicurezza e per le correzioni a priorità elevata.
> Attualmente non è prevista la rimozione di ISE da Windows.
>
> Non è previsto il supporto per l'ambiente ISE in PowerShell v6 e versioni successive. Gli utenti che vogliono sostituire ISE possono usare [Visual Studio Code](https://code.visualstudio.com/) con l'[estensione PowerShell](https://marketplace.visualstudio.com/items?itemName=ms-vscode.PowerShell).

## <a name="feature-description"></a>Descrizione delle funzionalità

Windows PowerShell ISE è un'applicazione host che consente di scrivere, eseguire e testare script e moduli in un ambiente grafico e intuitivo. Le principali funzionalità, come la sintassi contraddistinta dal colore, la funzionalità di completamento tramite tasto TAB, il debug visivo, la conformità a Unicode e la Guida sensibile al contesto garantiscono un'esperienza di scripting più dettagliata.

Per altre informazioni, vedere [Introduzione a Windows PowerShell ISE](../components/ise/Introducing-the-Windows-PowerShell-ISE.md).

Nella tabella seguente sono elencate alcune delle funzionalità nuove e modificate per questa versione di Windows PowerShell ISE in Windows PowerShell.

## <a name="intellisense"></a>IntelliSense

> Funzionalità aggiunta in ISE 3.0

IntelliSense è una funzionalità di assistenza per il completamento automatico che fa parte di Windows PowerShell ISE.
IntelliSense consente di visualizzare menu selezionabili di cmdlet, parametri, valori di parametri, file o cartelle potenzialmente corrispondenti durante la digitazione.

**Valore aggiunto da queste modifiche**

Con l'aggiunta di IntelliSense è più semplice individuare i cmdlet e la sintassi durante l'uso di Windows PowerShell ISE per creare script. È anche possibile usare Windows PowerShell ISE per imparare a usare Windows PowerShell durante la creazione di nuovi script.

**Differenze di funzionamento**

Quando si digitano cmdlet in Windows PowerShell ISE viene visualizzato un menu scorrevole e selezionabile, che consente di cercare e selezionare i comandi appropriati.

## <a name="snippets"></a>Frammenti di codice

> Funzionalità aggiunta in ISE 3.0

I *frammenti di codice* sono brevi sezioni di codice di Windows PowerShell che è possibile inserire negli script creati in Windows PowerShell ISE. Windows PowerShell ISE include un set predefinito di frammenti di codice. È possibile aggiungere frammenti di codice con il cmdlet `New-Snippet` mentre si lavora in Windows PowerShell ISE.

**Valore aggiunto da queste modifiche**

Con i frammenti di codice è possibile assemblare e creare script rapidamente per automatizzare l'ambiente.

**Differenze di funzionamento**

Per usare i frammenti di codice in Windows PowerShell 3.0 o versione successiva, scegliere **Avvia frammenti** dal menu **Modifica** o premere <kbd>CTRL</kbd>+<kbd>J</kbd>.

## <a name="add-on-tools"></a>Strumenti aggiuntivi

> Funzionalità aggiunta in PowerShell 3.0

Windows PowerShell ISE supporta ora strumenti aggiuntivi che usano il modello a oggetti. Questi componenti aggiuntivi sono controlli di Windows Presentation Foundation (WPF) che vengono visualizzati come riquadro verticale o orizzontale nella console. Più strumenti aggiuntivi di un riquadro vengono visualizzati come controllo a schede. È inoltre possibile aggiungere o rimuovere strumenti aggiuntivi prodotti da fornitori non Microsoft. Per altre informazioni, vedere [Scopo del modello a oggetti di scripting di Windows PowerShell ISE](../components/ise/object-model/Purpose-of-the-Windows-PowerShell-ISE-Scripting-Object-Model.md).

**Valore aggiunto da queste modifiche**

I componenti aggiuntivi consentono di estendere e personalizzare Windows PowerShell ISE con strumenti che aggiungono funzionalità e migliorano l'esperienza di scripting.

**Differenze di funzionamento**

Windows PowerShell ISE 3.0 e le versioni successive includono il componente aggiuntivo **Comandi**. Il componente aggiuntivo **Comandi** consente di esplorare i cmdlet e accedere alla Guida sui cmdlet a fianco dei riquadri **Script** e **Console**.

È possibile trovare altri componenti aggiuntivi tramite il comando **Apri sito Web strumenti aggiuntivi** nel menu **Componenti aggiuntivi**.

## <a name="restart-manager-and-auto-save"></a>Gestione riavvio e salvataggio automatico

> Funzionalità aggiunta in PowerShell 3.0

Windows PowerShell ISE ora salva gli script aperti automaticamente ogni due minuti, in una posizione separata. Quando Windows PowerShell ISE viene riavviato dopo un arresto anomalo o un riavvio imprevisto, ripristina gli script aperti nell'ultima sessione, anche se non sono stati salvati.

Per modificare l'intervallo di salvataggio automatico eseguire il comando seguente nel riquadro della console: `$psise.Options.AutoSaveMinuteInterval`.

**Valore aggiunto da queste modifiche**

È ora possibile lavorare all'interno di Windows PowerShell ISE sapendo che gli script aperti vengono salvati automaticamente.

**Differenze di funzionamento**

Windows PowerShell ISE 2.0 non salva gli script automaticamente.

## <a name="most-recently-used-list"></a>Elenco degli elementi usati di recente

> Funzionalità aggiunta in PowerShell 3.0

Windows PowerShell ISE ora include un elenco dei file usati di recente. Quando si apre un file in Windows PowerShell ISE, il file viene aggiunto all'elenco degli elementi usati di recente nel menu **File**.

Per modificare il numero predefinito di file nell'elenco degli elementi usati di recente, eseguire il comando seguente nel riquadro della console: `$psise.Options.MruCount`.

**Valore aggiunto da queste modifiche**

Con l'elenco degli elementi usati di recente ora è possibile accedere facilmente ai file usati più di frequente.

**Differenze di funzionamento**

Windows PowerShell ISE 2.0 non include un elenco degli elementi usati di recente.

## <a name="console-pane"></a>Riquadro della console

> Funzionalità aggiunta in PowerShell 3.0

I riquadri distinti di comandi e output disponibili nella prima versione di Windows PowerShell ISE sono stati riuniti in un singolo riquadro della console. Il funzionamento e l'aspetto del riquadro della console sono simili a quelli di una tipica console di Windows PowerShell, ma con i miglioramenti seguenti:

- Colorazione della sintassi per il testo di input (non per il testo di output), inclusa la sintassi XML
- IntelliSense
- Corrispondenza parentesi graffe
- Indicazione degli errori
- Supporto completo per Unicode
- Guida sensibile al contesto tramite <kbd>F1</kbd>
- Show-Command sensibile al contesto con <kbd>CTRL</kbd>+<kbd>F1</kbd>
- Supporto per script complessi e con scrittura da destra a sinistra
- Supporto per tipi di carattere
- Zoom
- Modalità selezione riga e selezione blocco
- Conservazione del contenuto digitato nella riga di comando quando si preme la freccia <kbd>SU</kbd> per visualizzare la cronologia nella console

**Valore aggiunto da queste modifiche**

L'aggiunta di queste modifiche del riquadro della console offre un'esperienza di scripting più coerente con l'interfaccia della console.

**Differenze di funzionamento**

Windows PowerShell ISE 2.0 ha riquadri separati per comandi e output.

## <a name="command-line-switches"></a>Opzioni della riga di comando

> Funzionalità aggiunta in PowerShell 3.0

Se si avvia Windows PowerShell ISE dalla riga di comando digitando **Powershell_ise.exe**, è possibile aggiungere le nuove opzioni da riga di comando seguenti.

- `-NoProfile`: Avvia Windows PowerShell ISE senza eseguire `$profile`
- `-Help`: visualizza una finestra della Guida.
- `-mta`: avvia Windows PowerShell ISE in modalità apartment a thread multipli. La modalità operativa predefinita per Windows PowerShell ISE è apartment a thread singolo o `-sta`.

**Valore aggiunto da queste modifiche**

L'aggiunta di queste opzioni da riga di comando consente di controllare l'ambiente di esecuzione di Windows PowerShell ISE.

**Differenze di funzionamento**

Windows PowerShell ISE 2.0 non riconosce queste opzioni da riga di comando.

## <a name="new-editor-features"></a>Nuove funzionalità dell'editor

> Funzionalità aggiunta in PowerShell 3.0

Altre funzionalità di modifica di Windows PowerShell ISE includono:

- **Colorazione della sintassi XML** Windows PowerShell ISE ora applica colori alla sintassi XML nello stesso modo usato per la sintassi di Windows PowerShell.
- **Corrispondenza delle parentesi graffe** Windows PowerShell ISE include l'individuazione e l'evidenziazione delle parentesi graffe corrispondenti che si possono usare in vari modi. Ad esempio, se si usa il comando **Vai a corrispondenza** o <kbd>CTRL</kbd>+<kbd>]</kbd> si trova la parentesi graffa di chiusura, se è selezionata una parentesi graffa di apertura.
- **Visualizzazione struttura** Il riquadro di script supporta la struttura delle sezioni, che consente di comprimere o espandere sezioni di codice facendo clic sui segni più o meno nel margine sinistro. È possibile usare le parentesi graffe oppure i tag `#region` e `#endregion` per contrassegnare l'inizio o la fine di una sezione comprimibile. Per espandere o comprimere tutte le aree, premere <kbd>CTRL</kbd>+<kbd>M</kbd>.
- **Modifica del testo con trascinamento della selezione** Windows PowerShell ISE supporta ora il trascinamento del testo per la modifica. È possibile selezionare qualsiasi blocco di testo e trascinarlo in un'altra posizione nell'editor o nella console per spostarlo. Se si tiene premuto il tasto <kbd>CTRL</kbd> mentre si trascina il testo selezionato, quando si rilascia il pulsante del mouse il testo viene copiato nella nuova posizione. In questa versione di Windows PowerShell ISE i file trascinati in Windows PowerShell ISE vengono aperti.
- **Visualizzazione degli errori di analisi** Gli errori di analisi sono indicati da sottolineature rosse. Quando si passa il mouse su un errore indicato, il testo della descrizione comando visualizza il problema rilevato nel codice.
- **Zoom** È possibile impostare la percentuale di zoom del contenuto della console con il dispositivo di scorrimento zoom, nell'angolo inferiore destro della finestra di Windows PowerShell ISE, oppure immettendo il comando `$psise.options.Zoom` nel riquadro della console.
- **Operazioni di copia e incolla di testo formattato** Con la copia negli Appunti in Windows PowerShell ISE vengono mantenute le informazioni relative a tipo di carattere, dimensioni e colore della selezione originale.
- **Selezione di blocchi** È possibile selezionare un blocco di testo tenendo premuto <kbd>ALT</kbd> mentre si seleziona il testo nel riquadro di script con il mouse oppure premendo <kbd>ALT</kbd>+<kbd>MAIUSC</kbd>+<kbd>FRECCIA</kbd>.

**Valore aggiunto da queste modifiche**

Le funzionalità di modifica aggiuntive rendono disponibile un ambiente di modifica più coerente e potente.

**Differenze di funzionamento**

Questi miglioramenti non erano presenti in Windows PowerShell ISE 2.0.

## <a name="new-help-viewer-window"></a>Nuova finestra di visualizzazione della Guida

> Funzionalità aggiunta in PowerShell 3.0

Se si preme <kbd>F1</kbd> mentre il cursore si trova in un cmdlet oppure si evidenzia parte di un cmdlet, nel nuovo visualizzatore della Guida verrà visualizzata la Guida sensibile al contesto del cmdlet evidenziato. Per visualizzare la guida **Informazioni su** Windows PowerShell, digitare `operators` nel riquadro della console e quindi premere <kbd>F1</kbd>.

Prima di usare questa funzionalità, scaricare la versione aggiornata degli argomenti della Guida di Windows PowerShell dal sito Web Microsoft. Il modo più semplice per scaricare gli argomenti della Guida consiste nell'eseguire il cmdlet `Update-Help` nel riquadro della console durante l'esecuzione di Windows PowerShell ISE come amministratore.

È possibile modificare la posizione in cui <kbd>F1</kbd> cerca la Guida. Nel menu **Strumenti**/**Opzioni**, nella scheda **Impostazioni generali**, in **Altre impostazioni** è possibile selezionare o deselezionare la casella di controllo **Usa contenuto della Guida locale anziché contenuto online**. Se si seleziona la casella di controllo, il client cerca la Guida per il cmdlet nella guida scaricata disponibile nella cartella dei moduli. Se la casella di controllo è deselezionata, il client cerca la guida online.

**Valore aggiunto da queste modifiche**

La possibilità di accedere alla Guida sensibile al contesto senza uscire dal cmdlet o dallo script corrente offre un'esperienza di apprendimento integrata.

**Differenze di funzionamento**

Premendo <kbd>F1</kbd> nelle versioni precedenti di Windows PowerShell ISE viene aperto il file della Guida nel computer locale. In Windows PowerShell ISE 3.0 e versioni successive viene visualizzata una finestra che contiene la Guida per il cmdlet, configurabile e nella quale è possibile eseguire ricerche. Questa esperienza della Guida è una novità di Windows PowerShell ISE 3.0 e la Guida aggiornabile è una novità di Windows PowerShell ISE 3.0.

## <a name="show-command-cmdlet"></a>Cmdlet Show-Command

> Funzionalità aggiunta in PowerShell 3.0

Il cmdlet `Show-Command` consente di comporre o eseguire un cmdlet o una funzione compilando un modulo grafico. Questo modulo consente agli utenti di usare Windows PowerShell in un ambiente grafico.
`Show-Command` consente inoltre agli utenti esperti di script di creare un'interfaccia utente grafica rapida basata su Windows PowerShell.

**Valore aggiunto da queste modifiche**

L'uso di `Show-Command` negli script di Windows PowerShell consente di offrire agli utenti l'ambiente grafico con cui hanno familiarità. `Show-Command` può anche essere utile agli utenti meno esperti per l'apprendimento di Windows PowerShell.

**Differenze di funzionamento**

`Show-Command` è nuovo in Windows PowerShell ISE 3.0.

## <a name="see-also"></a>Vedere anche

Per altre informazioni sull'uso di Windows PowerShell ISE, vedere [Esplorazione di Windows PowerShell ISE](../components/ise/exploring-the-windows-powershell-ise.md).
