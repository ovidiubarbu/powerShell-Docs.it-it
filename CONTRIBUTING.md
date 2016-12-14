# <a name="contributing-to-powershell-documentation"></a>Contributi alla documentazione di PowerShell

Grazie per l'interesse dimostrato nella documentazione di PowerShell. Di seguito vengono fornite informazioni dettagliate su come è possibile contribuire alla documentazione tecnica.

>Per informazioni generali sull'utilizzo di Git e GitHub, vedere la [guida di GitHub](https://help.github.com/). 

## <a name="sign-a-cla"></a>Firmare un contratto di licenza per i contributi

Per aggiungere contributi ai repository di PowerShell, è necessario prima [firmare un contratto di licenza Microsoft per i contributi](https://cla.microsoft.com/). Se in passato sono stati già aggiunti contributi al repository di PowerShell, questo passaggio è stato già completato.

## <a name="providing-feedback-on-powershell-documentation"></a>Commenti e suggerimenti sulla documentazione di PowerShell

È possibile sottolineare errori, suggerire modifiche o richiedere nuovi argomenti [segnalando il problema](https://help.github.com/articles/creating-an-issue/) nella [pagina appropriata del repository PowerShell-Docs](https://github.com/PowerShell/PowerShell-Docs/issues).

I problemi vengono esaminati periodicamente dai membri del team della documentazione di PowerShell e quindi vengono valutati, assegnati e risolti di conseguenza.

## <a name="writing-powershell-documentation"></a>Scrittura della documentazione di PowerShell

Uno dei modi più semplici per offrire un contributo a PowerShell è collaborare alla scrittura e alla modifica della documentazione. Tutta la documentazione ospitata in GitHub viene scritta mediante [GitHub Flavored Markdown](https://help.github.com/articles/github-flavored-markdown/).

## <a name="making-minor-edits-to-existing-topics"></a>Come apportare modifiche di lieve entità agli argomenti esistenti

Per [modificare un file esistente](https://help.github.com/articles/editing-files-in-another-user-s-repository/), accedere semplicemente al file e fare clic sul pulsante "Modifica". GitHub creerà automaticamente una fork personale del repository in cui è possibile apportare le modifiche. Al termine, salvare le modifiche e inviare una [richiesta pull](https://help.github.com/articles/creating-a-pull-request/) al ramo di *staging* del repository [PowerShell-Docs](https://github.com/PowerShell/PowerShell-Docs). Dopo aver creato la richiesta pull, un membro del team della documentazione di PowerShell esaminerà le modifiche prima di unirle al ramo di *staging*.

## <a name="making-major-edits-to-existing-topics"></a>Come apportare modifiche di maggiore entità agli argomenti esistenti

Se si apportano modifiche sostanziali a un articolo esistente, si aggiungono o modificano immagini oppure si contribuisce aggiungendo un nuovo articolo, è necessario creare manualmente una fork GitHub, quindi clonare la fork nel computer locale. Una fork è una replica basata su GitHub del repository principale, con l'account GitHub, che fornisce una copia di lavoro da usare indipendentemente. È possibile creare le richieste pull dalla fork. Analogamente, un clone è una replica locale del repository che, in questo caso, sarà un clone della fork. Il clone consente di lavorare nei repository Git offline usando il software e/o gli strumenti nativi più potenti.

Di seguito è riportato il flusso di lavoro per apportare modifiche di maggiore entità alla documentazione esistente:

1. [Creare una fork](https://help.github.com/articles/fork-a-repo/) del repository [PowerShell-Docs](https://github.com/PowerShell/PowerShell-Docs).
2. [Creare un clone della fork](https://help.github.com/articles/cloning-a-repository/) nel computer locale.
3. Creare un nuovo ramo locale nel repository clonato.
4. Apportare modifiche ai file che si vuole aggiornare in un editor Markdown. 
   Di seguito sono riportati gli editor Markdown usati più frequentemente.
5. [Eseguire il push del ramo locale](https://help.github.com/articles/pushing-to-a-remote/) nella fork.
6. [Creare una richiesta pull](https://help.github.com/articles/creating-a-pull-request/) nel ramo di *staging* del repository [PowerShell-Docs](https://github.com/PowerShell/PowerShell-Docs).

## <a name="creating-new-topics"></a>Creazione di nuovi argomenti

Se si vuole contribuire aggiungendo nuova documentazione, controllare innanzitutto se sono presenti [problemi contrassegnati come "in corso"](https://github.com/PowerShell/PowerShell-Docs/labels/in%20progress) per assicurarsi di non creare duplicati.
Dopo aver verificato che nessun altro membro stia lavorando allo stesso argomento eseguire le operazioni seguenti:

* Aprire un nuovo problema e contrassegnarlo come "in corso" (se si è un membro dell'organizzazione PowerShell) o aggiungere "in corso" come commento per indicare agli altri utenti l'argomento a cui si sta lavorando
* Seguire lo stesso flusso di lavoro come descritto in precedenza per apportare modifiche di maggiore entità agli argomenti esistenti.
* Modificare l'argomento `TOC.md` (situato nella cartella di primo livello per ogni set di documentazione) per aggiungere i nuovi argomenti al sommario. 
  Determinare il punto in cui inserire il nuovo argomento nel sommario e aggiungere un'intestazione del livello appropriato con un collegamento all'argomento (`[My topic title](relative path to my topic)`).

## <a name="markdown-editors"></a>Editor Markdown

Di seguito sono riportati alcuni editor Markdown che è possibile usare:

* [Visual Studio Code](https://code.visualstudio.com)
* [Markdown Pad](http://markdownpad.com/)
* [Atom](https://atom.io/)
* [Sublime Text](http://www.sublimetext.com/)


## <a name="github-flavored-markdown-gfm"></a>GitHub Flavored Markdown (GFM)

Tutti gli articoli di questo repository usano [GitHub Flavored Markdown (GFM)](https://help.github.com/articles/github-flavored-markdown/).

Alcune regole della sintassi GFM di base includono:

* **Interruzioni di riga e paragrafi:** in Markdown non vengono usati gli elementi HTML `<br />` né `<p />`. Un nuovo paragrafo viene indicato da una riga vuota tra due blocchi di testo.

> **Nota**: aggiungere una nuova riga dopo ogni frase per semplificare l'output della riga di comando di diff e cronologia.
Tale regola non è attualmente adottata in tutti i documenti di PowerShell, ma verrà applicata nel tempo. È possibile contribuire all'implementazione. 

* **Corsivo:** l'elemento HTML `<em>some text</em>` viene scritto come `*some text*`
* **Grassetto:** l'elemento HTML `<strong>some text</strong>` viene scritto come `**some text**`
* **Intestazioni:** le intestazioni HTML sono indicate con i caratteri `#` all'inizio della riga. 
  Il numero di caratteri `#` corrisponde al livello gerarchico dell'intestazione (ad esempio, `#` = `<h1>` e `###` = ```<h3>```).
* **Elenchi numerati:** per rendere un elenco numerato (ordinato) iniziare la riga con `1. `.  
  Per includere più elementi all'interno di un singolo elemento di elenco, applicare il formato seguente:
```        
1.  For the first element (like this one), insert a tab stop after the 1. 

    To include a second element (like this one), insert a line break after the first and align indentations.
```
per ottenere questo output:

1.  Per il primo elemento (come questo), inserire un punto di tabulazione dopo 1. 

    Per includere un secondo elemento (come questo), inserire un'interruzione di riga dopo il primo elemento e allineare i rientri.

* **Elenchi puntati:** gli elenchi puntati (non ordinati) sono quasi identici agli elenchi ordinati con la differenza che `1. ` viene sostituito con `* `, `- ` o `+ `. La procedura per includere più elementi all'interno di un singolo elemento di elenco è uguale a quella usata per gli elenchi ordinati.
* **Collegamenti:** la sintassi per un collegamento ipertestuale è `[visible link text](link URL)`.
* **Collegamento a un altro argomento all'interno dello stesso set di documenti:** un set di documenti è una cartella di primo livello in questo repository (ad esempio, "dsc", "scripting").
    La sintassi per un collegamento ipertestuale a un argomento all'interno dello stesso set di documenti è `[topic title](relative path to topic)`. 
    Per altre informazioni, vedere [Relative links in READMEs](https://help.github.com/articles/relative-links-in-readmes/) (Collegamenti correlati nei file README). 
    Per creare un collegamento a un argomento in un'altra cartella di primo livello, usare l'URL della pagina pubblicata, come descritto in precedenza.
