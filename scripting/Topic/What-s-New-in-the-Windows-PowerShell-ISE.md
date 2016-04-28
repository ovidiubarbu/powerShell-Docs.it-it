---
title: Novità di Windows PowerShell ISE
ms.custom: na
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 38648d47-7c27-4b37-a40e-ad29948519c2
---
# Novità di Windows PowerShell ISE
Questo argomento illustra le funzionalità nuove e aggiornate introdotte nelle varie versioni di [!INCLUDE[ise_1](../Token/ise_1_md.md)].

## <a name="overview"></a>Descrizione delle funzionalità
[!INCLUDE[ise_2](../Token/ise_2_md.md)] è un'applicazione host che consente di scrivere, eseguire e testare script e moduli in un ambiente grafico e intuitivo. Le principali funzionalità, come la colorazione della sintassi, il completamento tramite TAB, il debug visivo, la conformità a Unicode e la Guida sensibile al contesto garantiscono un'esperienza di scripting più avanzata.

Per un'introduzione a [!INCLUDE[ise_2](../Token/ise_2_md.md)], vedere [Panoramica di Windows PowerShell Integrated Scripting Environment](assetId:///3c1892c2-bf84-4cb6-af26-1f453be9e671).

## <a name="versions"></a>Funzionalità nuove e modificate in Windows PowerShell ISE
Nella tabella seguente sono elencate alcune delle funzionalità nuove e modificate per questa versione di [!INCLUDE[ise_2](../Token/ise_2_md.md)] in [!INCLUDE[wps_2](../Token/wps_2_md.md)].

|Funzionalità|[!INCLUDE[ise_2](../Token/ise_2_md.md)] 4.0|[!INCLUDE[ise_2](../Token/ise_2_md.md)] 3.0|[!INCLUDE[ise_2](../Token/ise_2_md.md)] 2.0|
|--------------------------|-----------------------------------------------|-----------------------------------------------|-----------------------------------------------|
|**[Intellisense](#BKMK_Intellisense)**|X|X||
|**[Frammenti di codice](#bkmk_snippets)**|X|X||
|**[Strumenti aggiuntivi](#BKMK_AddOnTools)**|X|X||
|**[Gestione riavvio e salvataggio automatico](#BKMK_RestartMgr)**|X|X||
|**[Riquadro della console](#BKMK_ConsolePane)**|X|X||
|**[Elenco degli elementi usati di recente](#BKMK_MRU)**|X|X||
|**[Opzioni della riga di comando](#BKMK_CommandLine)**|X|X||
|**[Nuove funzionalità dell'editor](#BKMK_NewEditorFeatures)**|X|X||
|**[Nuova finestra di visualizzazione della Guida](#BKMK_NewHelpViewer)**|X|X||
|**[Cmdlet Show-Command](#BKMK_ShowCommand)**|X|X||

### <a name="BKMK_Intellisense"></a>IntelliSense
**Funzionalità aggiunta in ISE 3.0**

IntelliSense è una funzionalità di assistenza per il completamento automatico che fa parte di [!INCLUDE[ise_2](../Token/ise_2_md.md)]. IntelliSense consente di visualizzare menu selezionabili di cmdlet, parametri, valori di parametri, file o cartelle potenzialmente corrispondenti durante la digitazione.

**Valore aggiunto da queste modifiche**

Con l'aggiunta di IntelliSense, risulta più semplice individuare i cmdlet e la sintassi durante l'uso di [!INCLUDE[ise_2](../Token/ise_2_md.md)] per creare script. È anche possibile usare [!INCLUDE[ise_2](../Token/ise_2_md.md)] per imparare a usare [!INCLUDE[wps_2](../Token/wps_2_md.md)] durante la creazione di nuovi script.

**Differenze di funzionamento**

Quando si digitano un cmdlet in [!INCLUDE[ise_2](../Token/ise_2_md.md)] 3.0 o versione successiva viene visualizzato un menu scorrevole e selezionabile tramite clic, che consente di individuare e selezionare i comandi appropriati.

### <a name="BKMK_Snippets"></a>Frammenti di codice
**Funzionalità aggiunta in ISE 3.0**

I *frammenti di codice* sono brevi sezioni di codice [!INCLUDE[wps_2](../Token/wps_2_md.md)] che è possibile inserire negli script creati in [!INCLUDE[ise_2](../Token/ise_2_md.md)]. [!INCLUDE[ise_2](../Token/ise_2_md.md)] include un set predefinito di frammenti di codice. È possibile aggiungere frammenti di codice con il cmdlet **New-Snippet** mentre si lavora in [!INCLUDE[ise_2](../Token/ise_2_md.md)].

**Valore aggiunto da queste modifiche**

Con i frammenti di codice è possibile assemblare e creare script rapidamente per automatizzare l'ambiente.

**Differenze di funzionamento**

Per usare i frammenti di codice in [!INCLUDE[wps_2](../Token/wps_2_md.md)] 3.0 o versione successiva, scegliere **Avvia frammenti** dal menu **Modifica** o premere **CTRL+J**.

### <a name="BKMK_AddOnTools"></a>Strumenti aggiuntivi
**Funzionalità aggiunta in PowerShell 3.0**

[!INCLUDE[ise_2](../Token/ise_2_md.md)] supporta ora strumenti aggiuntivi, ovvero controlli Windows Presentation Foundation (WPF) aggiunti usando il modello a oggetti. Gli strumenti aggiuntivi possono essere visualizzati nella console come riquadro verticale o orizzontale. Più strumenti aggiuntivi in un riquadro vengono visualizzati come controllo a schede. È anche possibile aggiungere o rimuovere strumenti aggiuntivi prodotti da fornitori non Microsoft. Per altre informazioni su come importare o rimuovere strumenti aggiuntivi, vedere [Operazioni di Windows PowerShell ISE](http://technet.microsoft.com/library/cc732148.aspx).

**Valore aggiunto da queste modifiche**

I componenti aggiuntivi consentono di estendere e personalizzare [!INCLUDE[ise_2](../Token/ise_2_md.md)] con strumenti che possono migliorare l'esperienza di scripting o aggiungere funzionalità a [!INCLUDE[ise_2](../Token/ise_2_md.md)].

**Differenze di funzionamento**

[!INCLUDE[ise_2](../Token/ise_2_md.md)] 3.0 e versioni successive includono il componente aggiuntivo **Comandi**. Il componente aggiuntivo **Comandi** consente di esplorare i cmdlet e accedere alla Guida sui cmdlet a fianco dei riquadri **Script** e **Console**.

È possibile trovare altri componenti aggiuntivi tramite il comando **Apri sito Web strumenti aggiuntivi** nel menu **Componenti aggiuntivi**.

### <a name="BKMK_RestartMgr"></a>Gestione riavvio e salvataggio automatico
**Funzionalità aggiunta in PowerShell 3.0**

[!INCLUDE[ise_2](../Token/ise_2_md.md)] ora salva gli script aperti automaticamente ogni due minuti, in una posizione separata.  Se [!INCLUDE[ise_2](../Token/ise_2_md.md)] si interrompe o il sistema operativo viene riavviato, dopo il riavvio di [!INCLUDE[ise_2](../Token/ise_2_md.md)] vengono ripristinati gli script aperti nell'ultima sessione, anche se non erano stati salvati.

Per modificare l'intervallo di salvataggio automatico eseguire il comando seguente nel riquadro della console: **$psise.Options.AutoSaveMinuteInterval**.

**Valore aggiunto da queste modifiche**

È ora possibile lavorare all'interno di [!INCLUDE[ise_2](../Token/ise_2_md.md)] sapendo che gli script aperti vengono salvati automaticamente in caso di un riavvio imprevisto.

**Differenze di funzionamento**

[!INCLUDE[ise_2](../Token/ise_2_md.md)] 2.0 non salva gli script automaticamente in caso di riavvio.

### <a name="BKMK_MRU"></a>Elenco degli elementi usati di recente
**Funzionalità aggiunta in PowerShell 3.0**

[!INCLUDE[ise_2](../Token/ise_2_md.md)] ora include un elenco dei file usati di recente. Quando si apre un file in [!INCLUDE[ise_2](../Token/ise_2_md.md)], il file viene aggiunto all'elenco degli elementi usati di recente nel menu **File**.

Per modificare il numero predefinito di file nell'elenco degli elementi usati di recente, eseguire il comando seguente nel riquadro della console: **$psise.Options.MruCount**.

**Valore aggiunto da queste modifiche**

È ora possibile usare l'elenco degli elementi usati di recente per accedere facilmente ai file usati frequentemente.

**Differenze di funzionamento**

[!INCLUDE[ise_2](../Token/ise_2_md.md)] 2.0 non include un elenco degli elementi usati di recente.

### <a name="BKMK_ConsolePane"></a>Riquadro della console
**Funzionalità aggiunta in PowerShell 3.0**

I riquadri distinti di comandi e output disponibili nella prima versione di [!INCLUDE[ise_2](../Token/ise_2_md.md)] sono stati riuniti in un singolo riquadro della console. Il funzionamento e l'aspetto del riquadro della console sono simili a quelli di una tipica console di [!INCLUDE[wps_2](../Token/wps_2_md.md)], ma con i miglioramenti seguenti (la maggior parte descritti in questo argomento).

-   Colorazione della sintassi per il testo di input (non per il testo di output), inclusa la sintassi XML

-   Intellisense

-   Corrispondenza parentesi graffe

-   Indicazione degli errori

-   Supporto completo per Unicode

-   Guida sensibile al contesto con **F1**

-   Show-Command sensibile al contesto con **CTRL+F1**

-   Supporto per script complessi e con scrittura da destra a sinistra

-   Supporto per tipi di carattere

-   Zoom

-   Modalità selezione di riga e selezione di blocchi

-   Conservazione del contenuto digitato nella riga di comando quando si preme freccia **SU** per visualizzare la cronologia nella console

**Valore aggiunto da queste modifiche**

L'aggiunta di queste modifiche del riquadro della console offre un'esperienza di scripting più coerente con l'interfaccia della console.

**Differenze di funzionamento**

[!INCLUDE[ise_2](../Token/ise_2_md.md)] 2.0 include riquadri separati per comandi e output.

### <a name="BKMK_CommandLine"></a>Opzioni della riga di comando
**Funzionalità aggiunta in PowerShell 3.0**

Se si avvia [!INCLUDE[ise_2](../Token/ise_2_md.md)] dalla riga di comando digitando **Powershell_ise.exe**, è possibile aggiungere le nuove opzioni della riga di comando seguenti:

-   *-NoProfile*: avvia [!INCLUDE[ise_2](../Token/ise_2_md.md)] senza eseguire **$profile**

-   *-Help*: visualizza una finestra della Guida

-   *-mta*: avvia [!INCLUDE[ise_2](../Token/ise_2_md.md)] in modalità apartment a thread multipli. La modalità operativa predefinita per [!INCLUDE[ise_2](../Token/ise_2_md.md)] è apartment a thread singolo o *-sta*.

**Valore aggiunto da queste modifiche**

L'aggiunta di queste opzioni della riga di comando consente di controllare l'ambiente di esecuzione di [!INCLUDE[ise_2](../Token/ise_2_md.md)].

**Differenze di funzionamento**

[!INCLUDE[ise_2](../Token/ise_2_md.md)] 2.0 non riconosce queste opzioni della riga di comando.

### <a name="BKMK_NewEditorFeatures"></a>Nuove funzionalità dell'editor
**Funzionalità aggiunta in PowerShell 3.0**

Alte funzionalità di modifica di [!INCLUDE[ise_2](../Token/ise_2_md.md)] includono:

-   La **colorazione della sintassi XML**[!INCLUDE[ise_2](../Token/ise_2_md.md)] ora applica colori alla sintassi XML nello stesso modo usato per la sintassi di [!INCLUDE[wps_2](../Token/wps_2_md.md)].

-   La funzionalità di **corrispondenza delle parentesi graffe** [!INCLUDE[ise_2](../Token/ise_2_md.md)] include l'individuazione delle parentesi graffe corrispondenti e la loro evidenziazione e può essere usata in vari modi. Ad esempio, è possibile usare il comando **Vai a corrispondenza** o **CTRL+]** per individuare la parentesi graffa di chiusura, se è selezionata una parentesi graffa di apertura.

-   **Visualizzazione struttura** Il riquadro di script supporta la struttura, che consente di comprimere o espandere sezioni di codice facendo clic sui segni più o meno nel margine sinistro. È possibile usare le parentesi graffe oppure i tag **\#region** ed **\#endregion** per contrassegnare l'inizio o la fine di una sezione comprimibile. Per espandere o comprimere tutte le aree, premere **CTRL+M**.

-   La **modifica del testo con trascinamento della selezione**[!INCLUDE[ise_2](../Token/ise_2_md.md)] supporta ora il trascinamento del testo per la modifica. È possibile selezionare qualsiasi blocco di testo e trascinarlo in un'altra posizione nell'editor o nella console per spostarlo. Se si tiene premuto il tasto CTRL mentre si trascina il testo selezionato, quando si rilascia il pulsante del mouse il testo viene copiato nella nuova posizione. In questa versione di [!INCLUDE[ise_2](../Token/ise_2_md.md)], come nella versione precedente di [!INCLUDE[ise_2](../Token/ise_2_md.md)], quando si trascina un file in [!INCLUDE[ise_2](../Token/ise_2_md.md)], [!INCLUDE[ise_2](../Token/ise_2_md.md)] apre il file.

-   **Visualizzazione degli errori di analisi** Gli errori di analisi sono indicati da sottolineature rosse. Quando si passa il mouse su un errore indicato, il testo della descrizione comando visualizza il problema rilevato nel codice.

-   **Zoom** È possibile impostare la percentuale di zoom del contenuto della console mediante il dispositivo di scorrimento zoom, nell'angolo inferiore destro della finestra di [!INCLUDE[ise_2](../Token/ise_2_md.md)], oppure immettendo il comando **$psise.options.Zoom** nel riquadro della console.

-   **Operazioni di copia e incolla di testo formattato** Con la copia negli Appunti in [!INCLUDE[ise_2](../Token/ise_2_md.md)] vengono mantenute le informazioni relative a tipo di carattere, dimensioni e colore della selezione originale.

-   **Selezione di blocchi** È possibile selezionare un blocco di testo tenendo premuto ALT mentre si seleziona il testo nel riquadro di script con il mouse oppure premendo **ALT+MAIUSC+FRECCIA**.

**Valore aggiunto da queste modifiche**

Le funzionalità di modifica aggiuntive rendono disponibile un ambiente di modifica più coerente e potente.

**Differenze di funzionamento**

Questi miglioramenti non erano presenti in [!INCLUDE[ise_2](../Token/ise_2_md.md)] 2.0.

### <a name="BKMK_NewHelpViewer"></a>Nuova finestra di visualizzazione della Guida
**Funzionalità aggiunta in PowerShell 3.0**

Se si preme **F1** mentre il cursore si trova in un cmdlet oppure si evidenzia parte di un cmdlet, nel nuovo visualizzatore della Guida verrà visualizzata la Guida sensibile al contesto per il cmdlet evidenziato. Per visualizzare la Guida Informazioni su [!INCLUDE[wps_2](../Token/wps_2_md.md)], digitare **operators** nel riquadro della console e quindi premere **F1**.

Prima di utilizzare questa funzionalità, scaricare la versione aggiornata degli argomenti della Guida di [!INCLUDE[wps_2](../Token/wps_2_md.md)] dal sito Web Microsoft. Il modo più semplice per scaricare gli argomenti della Guida consiste nell'eseguire il cmdlet **Update-Help** nel riquadro della console durante l'esecuzione di [!INCLUDE[ise_2](../Token/ise_2_md.md)] come amministratore.

È possibile modificare la posizione in cui **F1** cerca la Guida. Nel menu **Strumenti**/**Opzioni**, nella scheda **Impostazioni generali**, in **Altre impostazioni** è possibile selezionare o deselezionare la casella di controllo **Usa contenuto della Guida locale anziché contenuto online**. Se si seleziona la casella di controllo, il client cerca la Guida per il cmdlet nella Guida scaricata disponibile nella cartella dei moduli.  Se la casella di controllo viene deselezionata, il client cerca la Guida per il cmdlet nella libreria TechNet.

**Valore aggiunto da queste modifiche**

La possibilità di accedere alla Guida sensibile al contesto senza uscire dal cmdlet o dallo script corrente offre un'esperienza di apprendimento semplificata.

**Differenze di funzionamento**

Premendo F1 nelle versioni precedenti di [!INCLUDE[ise_2](../Token/ise_2_md.md)] viene aperto il file della Guida nel computer locale. In [!INCLUDE[ise_2](../Token/ise_2_md.md)] 3.0 e versioni successive viene visualizzata una finestra che contiene la Guida per il cmdlet, configurabile e nella quale è possibile eseguire ricerche. Questa esperienza della Guida è una novità di [!INCLUDE[ise_2](../Token/ise_2_md.md)] 3.0 e la Guida aggiornabile è una novità di [!INCLUDE[wps_2](../Token/wps_2_md.md)] 3.0.

### <a name="BKMK_ShowCommand"></a>Cmdlet Show-Command
**Funzionalità aggiunta in PowerShell 3.0**

Il cmdlet **Show-Command** consente di comporre o eseguire un cmdlet o una funzione compilando un modulo grafico. Questo modulo consente agli utenti di usare [!INCLUDE[wps_2](../Token/wps_2_md.md)] in un ambiente grafico. **Show-Command** consente anche agli utenti esperti di script di creare un'interfaccia utente grafica rapida basata su [!INCLUDE[wps_2](../Token/wps_2_md.md)].

**Valore aggiunto da queste modifiche**

L'uso di **Show-Command** negli script di [!INCLUDE[wps_2](../Token/wps_2_md.md)] consente di offrire agli utenti l'ambiente grafico con cui hanno familiarità. **Show-Command** può anche essere utile agli utenti meno esperti per l'apprendimento di [!INCLUDE[wps_2](../Token/wps_2_md.md)].

**Differenze di funzionamento**

Show-Command è una novità di [!INCLUDE[ise_2](../Token/ise_2_md.md)] 3.0.

## <a name="BKMK_LINKS"></a>Vedere anche
Per altre informazioni sull'uso di [!INCLUDE[ise_2](../Token/ise_2_md.md)] in [!INCLUDE[wps_2](../Token/wps_2_md.md)], vedere i collegamenti seguenti.

-   [Uso di Windows PowerShell ISE (Integrated Scripting Environment)](assetId:///777ea82b-dd73-4269-b61a-69a17e6ff16f)

-   [ISE nel Wiki di TechNet](http://social.technet.microsoft.com/wiki/search/searchresults.aspx?q=ISE)

-   [Script Center](http://technet.microsoft.com/scriptcenter/default)



<!--HONumber=Apr16_HO1-->


