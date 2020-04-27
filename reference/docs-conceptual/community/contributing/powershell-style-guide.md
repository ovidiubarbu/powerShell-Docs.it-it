---
title: Guida di stile per la documentazione di PowerShell
description: Questo articolo include le regole di stile per la scrittura della documentazione di PowerShell.
ms.date: 03/05/2020
ms.topic: conceptual
ms.openlocfilehash: 90dc93d608440ce7388614b552c0cd873a385cd9
ms.sourcegitcommit: 6545c60578f7745be015111052fd7769f8289296
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/22/2020
ms.locfileid: "81624789"
---
# <a name="powershell-docs-style-guide"></a>Guida di stile per la documentazione di PowerShell

Questo articolo è una guida di stile specifica per il contenuto di documentazione di PowerShell. Le linee guida si basano sulle informazioni incluse nella [Panoramica ](overview.md#get-started-writing-docs).

## <a name="product-terminology"></a>Terminologia del prodotto

Sono disponibili diverse varianti di PowerShell.

- **PowerShell**: è la definizione predefinita. Da questo punto in poi, per PowerShell si intende PowerShell 7 e versioni successive.
- **PowerShell Core**: PowerShell basato su .NET Core. L'uso del termine **Core** deve essere limitato ai casi in cui è necessario distinguere da Windows PowerShell.
- **Windows PowerShell**: PowerShell basato su .NET Framework. Windows PowerShell è disponibile solo in Windows e richiede il framework completo.

  In generale i riferimenti a "Windows PowerShell" nella documentazione possono essere modificati in "PowerShell".
  Deve essere usata la dicitura "Windows PowerShell" quando si parla di un comportamento specifico di "Windows PowerShell".

Prodotti correlati

- **Visual Studio Code (VS Code)** - Editor open source gratuito di Microsoft. Per la prima citazione, è necessario usare il nome completo. Successivamente, è possibile usare **VS Code**. Non usare "VSCode".
- **Estensione PowerShell per Visual Studio Code** - Estensione che trasforma VS Code nell'ambiente IDE preferito per PowerShell. Per la prima citazione, è necessario usare il nome completo. Successivamente è possibile usare **estensione PowerShell**.
- **Azure PowerShell** - Raccolta di moduli di PowerShell usati per gestire i servizi di Azure.
- **PowerShell Azure Stack** - Raccolta di moduli di PowerShell usati per gestire la soluzione cloud ibrida di Microsoft.

## <a name="markdown-specifics"></a>Specifiche di Markdown

Il sistema Microsoft Open Publishing (OPS) che compila la documentazione usa [markdig][] per elaborare i documenti Markdown. Markdig analizza i documenti in base alle regole della specifica [CommonMark][] più recente.

La nuova specifica CommonMark è molto più restrittiva in merito alla costruzione di alcuni elementi Markdown. Prestare particolare attenzione ai dettagli inclusi in questo documento.

### <a name="blank-lines-spaces-and-tabs"></a>Righe vuote, spazi e tabulazioni

Le righe vuote segnalano anche la fine di un blocco in Markdown. Deve essere presente un solo spazio vuoto tra i blocchi Markdown di tipi diversi, ad esempio tra un paragrafo e un elenco o un'intestazione.

Rimuovere le righe vuote duplicate. Il rendering di più righe vuote in HTML corrisponde a un'unica riga vuota. Non è quindi utile usare più righe vuote. Più righe vuote in un blocco di codice interrompono quest'ultimo.

Rimuovere gli spazi aggiuntivi alla fine delle righe.

> [!NOTE]
> La spaziatura è importante in Markdown. Usare sempre gli spazi anziché le tabulazioni hard. Gli spazi finali possono modificare il rendering del codice Markdown.

### <a name="titles-and-headings"></a>Titoli e intestazioni

Usare solo [intestazioni ATX][atx] (con lo stile #, anziché intestazioni con stile `=` o `-`).

- Usare la maiuscola a inizio frase: solo i nomi propri e la prima lettera di un titolo o di un'intestazione devono essere in maiuscole
- Deve essere presente uno spazio singolo tra `#` e la prima lettera dell'intestazione
- Le intestazioni devono essere racchiuse da una sola riga vuota
- Ogni documento deve includere un solo titolo H1
- I livelli di intestazione devono avere incrementi di uno. Non ignorare i livelli
- Non usare il grassetto o altri markup nelle intestazioni

### <a name="limit-line-length-to-100-characters"></a>Limitare la lunghezza della riga a 100 caratteri

Questo vale per gli articoli concettuali e i riferimenti ai cmdlet. La limitazione della lunghezza delle righe migliora la leggibilità dei diff e della cronologia GIT. Semplifica anche i contributi da parte di altri writer.

Usare l'estensione [Reflow Markdown][reflow] in Visual Studio Code per reimpostare facilmente il flusso dei paragrafi, in modo da adattarlo alla lunghezza di riga prescritta.

Il testo dei titoli Informazioni su può avere una lunghezza massima di 80 caratteri. Per informazioni più specifiche, vedere [Modifica degli articoli di riferimento](./editing-cmdlet-ref.md#formatting-about_-files).

### <a name="lists"></a>Elenchi

Se l'elenco contiene più frasi o paragrafi, prendere in considerazione l'uso di un'intestazione di sottolivello anziché di un elenco.

Gli elenchi devono essere racchiusi da una sola riga vuota.

#### <a name="unordered-lists"></a>Elenchi non ordinati

Non terminare gli elementi elenco con un punto (a meno che non contengano più frasi). Usare il trattino (`-`) per gli elementi di elenchi puntati. In questo modo si evita confusione con i markup di grassetto o corsivo che usano l'asterisco (`*`). Per includere un paragrafo o altri elementi sotto un punto elenco, inserire un'interruzione di riga e allineare il rientro con il primo carattere dopo il punto elenco.

Ad esempio:

```markdown
This is a list that contain sub-elements under a bullet item.

- First bullet item

  Sentence explaining the first bullet.

  - Sub-bullet item

    Sentence explaining the sub-bullet.

- Second bullet item
- Third bullet item
```

Questo è un elenco che contiene sottoelementi sotto un elemento punto elenco.

- Primo elemento punto elenco

  Frase che spiega il primo punto elenco.

  - Sottoelemento punto elenco

    Frase che spiega il sottoelemento punto elenco.

- Secondo elemento punto elenco
- Terzo elemento punto elenco

#### <a name="ordered-lists"></a>Elenchi ordinati

Per includere un paragrafo o altri elementi sotto un elemento numerato, allineare il rientro con il primo carattere dopo il numero dell'elemento. Tutti gli elementi di un elenco numerato devono usare il numero `1.` anziché incrementare ogni elemento. Il rendering di Markdown incrementa automaticamente il valore. Questo semplifica il riordino degli elementi e standardizza il rientro del contenuto subordinato.

Ad esempio:

```markdown
1. For the first element, insert a single space after the 1. Long sentences should be
   wrapped to the next line and must line up with the first character after the numbered
   list marker.

   To include a second element (like this one), insert a line break after the first
   and align indentations. The indentation of the second element must line up with
   the first character after the numbered list marker. For single digit items, like
   this one, you indent to column 4. For double digits items, for example item number
   10, you indent to column 5.

1. The next numbered item starts here.
```

Il testo Markdown risultante viene restituito come segue:

1. Per il primo elemento inserire uno spazio singolo dopo 1. Le frasi lunghe vanno mandate a capo alla riga successiva e devono essere allineate con il primo carattere dopo il marcatore di elenco numerato.

   Per includere un secondo elemento (come questo), inserire un'interruzione di riga dopo il primo elemento e allineare i rientri. Il rientro del secondo elemento deve essere allineato con il primo carattere dopo il marcatore dell'elenco numerato. Per gli elementi a cifra singola come questo, si applica un rientro alla colonna 4. Per gli elementi a doppia cifra, ad esempio l'elemento numero 10, si applica un rientro alla colonna 5.

1. Il successivo elemento numerato inizia qui.

### <a name="images"></a>Immagini

La sintassi per includere un'immagine è la seguente:

```markdown
![[alt text]](<folderPath>)

Example:
![Introduction](./media/overview/Introduction.png)
```

`alt text` è una breve descrizione dell'immagine e `<folder path>` è un percorso relativo all'immagine. È necessario testo alternativo per le utilità per la lettura dello schermo destinate a utenti con problemi visivi. Tale testo è utile anche quando a causa di un bug del sito non è possibile eseguire il rendering dell'immagine.

Le immagini devono essere archiviate in una cartella `media/<article-name>` all'interno della cartella che contiene l'articolo.
Le immagini non devono essere condivise tra gli articoli. Creare una cartella corrispondente al nome file dell'articolo sotto la cartella `media`. Copiare le immagini per l'articolo nella nuova cartella. Se un'immagine viene usata da più articoli, ogni cartella di immagini deve avere una copia di quel file di immagine. Questa procedura impedisce che la modifica di un'immagine in un articolo abbia effetto su un altro articolo.

Sono supportati i tipi di file immagine seguenti: `*.png`, `*.gif`, `*.jpeg`, `*.jpg`, `*.svg`

### <a name="markdown-extensions-supported-by-open-publishing"></a>Estensioni Markdown supportate da Open Publishing

[Microsoft Docs Authoring Pack](/contribute/how-to-write-docs-auth-pack) contiene strumenti che supportano funzionalità specifiche del sistema di pubblicazione. Gli avvisi sono un'estensione Markdown per la creazione di citazioni di cui viene eseguito il rendering in docs.microsoft.com con colori e icone che evidenziano il significato del contenuto. Sono supportati i tipi di avviso seguenti:

```markdown
> [!NOTE]
> Information the user should notice even if skimming.

> [!TIP]
> Optional information to help a user be more successful.

> [!IMPORTANT]
> Essential information required for user success.

> [!CAUTION]
> Negative potential consequences of an action.

> [!WARNING]
> Dangerous certain consequences of an action.
```

Questi avvisi hanno un aspetto simile al seguente in docs.microsoft.com:

Blocco Nota

> [!NOTE]
> Informazioni che l'utente deve notare anche in una consultazione veloce.

Blocco Suggerimento

> [!TIP]
> Informazioni facoltative che consentono a un utente di ottenere risultati più efficaci.

Blocco Importante

> [!IMPORTANT]
> Informazioni essenziali necessarie per l'esito positivo.

Blocco Attenzione

> [!CAUTION]
> Potenziali conseguenze negative di un'azione.

Blocco Avviso

> [!WARNING]
> Conseguenze pericolose certe di un'azione.

### <a name="hyperlinks"></a>Collegamenti ipertestuali

- I collegamenti ipertestuali devono usare la sintassi Markdown `[friendlyname](url-or-path)`
- Se possibile, i collegamenti devono essere di tipo HTTPS.
- I collegamenti devono avere un nome descrittivo, in genere il titolo dell'argomento collegato
- Tutti gli elementi nella sezione "Collegamenti correlati" alla fine degli articoli devono essere impostati come collegamenti ipertestuali
- Non usare accenti gravi, grassetto o altri elementi di markup all'interno delle parentesi quadre di un collegamento ipertestuale.
- Quando si parla di un URI specifico, è possibile usare URL semplici. L'URI deve essere racchiuso tra apici inversi. Ad esempio:

  ```markdown
  By default, if you do not specify this parameter, the DMTF standard resource URI
  `http://schemas.dmtf.org/wbem/wscim/1/cim-schema/2/` is used and the class name is appended to it.
  ```

#### <a name="linking-to-other-content"></a>Collegamento a contenuto diverso

Il sistema di pubblicazione supporta due tipi di collegamenti ipertestuali:

Un **collegamento URL** può essere un percorso URL relativo alla radice docs.microsoft.com. Oppure può essere un URL assoluto, che include la sintassi completa dell'URL. Ad esempio: `https:/github.com/MicrosoftDocs/PowerShell-Docs`

- Usare i collegamenti URL per il collegamento a contenuto esterno a PowerShell-Docs o il collegamento tra riferimenti ai cmdlet e articoli concettuali in PowerShell-Docs. Il modo più semplice per creare un collegamento relativo consiste nel copiare l'URL dal browser e quindi rimuovere `https://docs.microsoft.com/en-us` dal valore incollato in Markdown.
- Non includere le impostazioni locali negli URL nelle proprietà Microsoft (ad esempio, rimuovere `/en-us` dall'URL).
- Rimuovere dall'URL tutti i parametri di query non necessari, a meno che non sia necessario creare un collegamento a una versione specifica di un articolo. Esempi:
  - `?view=powershell-5.1` - Parametro usato in un collegamento a una versione specifica di PowerShell
  - `?redirectedfrom=MSDN` - Parametro aggiunto all'URL per il reindirizzamento dalla vecchia versione di un vecchio articolo alla nuova posizione di questo
- Tutti gli URL che puntano a siti Web esterni devono usare HTTPS, a meno che ciò non sia valido per il sito di destinazione.

Un **collegamento file** viene usato per collegare un articolo di riferimento a un altro o un articolo concettuale a un altro. Per creare un collegamento a un articolo di riferimento per una versione specifica di PowerShell, è necessario usare un collegamento URL.

- I collegamenti file contengono un percorso di file relativo (ad esempio: `../folder/file.md`)
- Tutti i percorsi di file usano caratteri barra (`/`)

Sono consentite operazioni di deep linking sia negli URL che nei collegamenti file. Aggiungere l'ancoraggio alla fine del percorso di destinazione.
Ad esempio:

- `[about_Splatting](about_Splatting.md#splatting-with-arrays)`
- `[custom key bindings](https://code.visualstudio.com/docs/getstarted/keybindings#_custom-keybindings-for-refactorings)`

Per altre informazioni, vedere [Usare collegamenti nella documentazione](https://docs.microsoft.com/contribute/how-to-write-links).

## <a name="formatting-command-syntax-elements"></a>Formattazione degli elementi della sintassi del comando

- Usare sempre il nome completo per i cmdlet e i parametri. Evitare di usare alias, a meno che non si stia dimostrando in modo specifico l'alias.

- Proprietà, parametri, oggetti, nomi di tipi, nomi di classi e metodi di classe devono essere in **grassetto**.
  - I valori delle proprietà e dei parametri devono essere racchiusi tra apici inversi (`` ` ``).
  - Quando si fa riferimento a tipi racchiudendoli tra parentesi quadre, usare apici inversi. Ad esempio: `[System.Io.FileInfo]`

- Le parole chiave del linguaggio, i nomi dei cmdlet, le funzioni, le variabili, i file EXE nativi, i percorsi di file e gli esempi di sintassi inline devono essere racchiusi tra apici inversi (`` ` ``).

  Ad esempio:

  ~~~markdown
  The following code uses `Get-ChildItem` to list the contents of `C:\Windows` and assigns
  the output to the `$files` variable.

  ```powershell
  $files = Get-ChildItem C:\Windows
  ```
  ~~~

  - Quando si fa riferimento a un parametro con il nome, questo deve essere in **grassetto**. Quando si illustra l'uso di un parametro con il prefisso trattino, il parametro deve essere racchiuso tra caratteri accento grave. Ad esempio:

    ```markdown
    The parameter's name is **Name**, but it is typed as `-Name` when used on the command
    line as a parameter.
    ```

  - Quando si visualizza un esempio d'uso di un comando esterno, l'esempio deve essere racchiuso tra caratteri accento grave.
    Includere sempre l'estensione file nel comando nativo. Ad esempio:

    ```markdown
    To start the spooler service on a remote computer named DC01, you type `sc.exe \\DC01 start spooler`.
    ```

    In questo modo ci si assicura che venga eseguito il comando corretto in base alle regole di precedenza dei comandi di PowerShell.

- Durante la scrittura di un articolo concettuale (diversamente dal contenuto di riferimento), la prima istanza del nome di un cmdlet deve essere un collegamento alla documentazione del cmdlet. Non usare accenti gravi, grassetto o altri elementi di markup all'interno delle parentesi quadre di un collegamento ipertestuale.

  Ad esempio:

  ```markdown
  This [Write-Host](/powershell/module/Microsoft.PowerShell.Utility/Write-Host) cmdlet
  uses the **Object** parameter to ...
  ```

  Per altre informazioni, vedere la sezione [Collegamenti ipertestuali](#hyperlinks) di questo articolo.

## <a name="markdown-for-code-samples"></a>Markdown per esempi di codice

Markdown supporta due stili di codice:

- **Intervalli di codice (inline)** - Contrassegnati da un singolo carattere apice inverso (`` ` ``). Sono usati all'interno di un paragrafo anziché come blocchi autonomi.
- **Blocchi di codice** - Blocchi a più righe racchiusi fra stringhe costituite da un triplo apice inverso (`` ``` ``). I blocchi di codice possono anche avere un'etichetta di linguaggio dopo i caratteri accento grave. L'etichetta di linguaggio consente l'evidenziazione della sintassi per il contenuto del blocco di codice.

Tutti i blocchi di codice devono essere inclusi in un intervallo di codice. Non usare mai rientri per i blocchi di codice. Il linguaggio Markdown le consente, ma possono creare problemi e devono essere evitati.

Un blocco di codice è costituito da una o più righe di codice comprese in un intervallo di codice racchiuso tra caratteri triplo apice inverso (`` ``` ``).
I marcatori dell'intervallo di codice devono trovarsi su una riga a parte, prima e dopo l'esempio di codice. Il marcatore all'inizio del blocco di codice può avere un'etichetta del linguaggio facoltativa. Microsoft Open Publishing System (OPS) usa l'etichetta del linguaggio per supportare la funzionalità di evidenziazione della sintassi.

Per l'elenco completo dei tag supportati dal linguaggio, vedere [Blocchi di codice delimitati](/contribute/code-in-docs#fenced-code-blocks) nella guida per i collaboratori centralizzata.

OPS aggiunge anche un pulsante **Copy** (Copia) che copia il contenuto del blocco di codice negli Appunti. In questo modo è possibile incollare rapidamente il codice in uno script per eseguire il test dell'esempio di codice. Non tutti gli esempi nella documentazione, tuttavia, sono destinati a essere eseguiti così come sono. Alcuni blocchi di codice sono semplici illustrazioni di un concetto di PowerShell.

Nella documentazione vengono usati tre tipi di blocchi di codice:

1. Blocchi di sintassi
1. Esempi illustrativi
1. Esempi eseguibili

### <a name="syntax-code-blocks"></a>Blocchi di codice di sintassi

I blocchi di codice di sintassi vengono usati per descrivere la struttura sintattica di un comando. Non usare un tag di linguaggio nella delimitazione del codice. Questo esempio illustra tutti i possibili parametri del cmdlet `Get-Command`.

~~~markdown
```
Get-Command [-Verb <String[]>] [-Noun <String[]>] [-Module <String[]>]
  [-FullyQualifiedModule <ModuleSpecification[]>] [-TotalCount <Int32>] [-Syntax]
  [-ShowCommandInfo] [[-ArgumentList] <Object[]>] [-All] [-ListImported]
  [-ParameterName <String[]>] [-ParameterType <PSTypeName[]>] [<CommonParameters>]
```
~~~

Questo esempio illustra l'istruzione `for` in termini generici:

~~~markdown
```
for (<init>; <condition>; <repeat>)
{<statement list>}
```
~~~

### <a name="illustrative-examples"></a>Esempi illustrativi

Gli esempi illustrativi vengono usati per descrivere un concetto di PowerShell. Non sono pensati per essere copiati negli Appunti per l'esecuzione. Vengono usati soprattutto per esempi semplici, facili da digitare e da comprendere. Un blocco di codice può includere il prompt di PowerShell e output di esempio.

Ecco un esempio semplice che illustra gli operatori di confronto di PowerShell. In questo caso, non è previsto che l'utente copi ed esegua l'esempio.

~~~markdown
```powershell
PS> 2 -eq 2
True

PS> 2 -eq 3
False

PS>  1,2,3 -eq 2
2

PS> "abc" -eq "abc"
True

PS> "abc" -eq "abc", "def"
False

PS> "abc", "def" -eq "abc"
abc
```
~~~

### <a name="executable-examples"></a>Esempi eseguibili

Gli esempi complessi o quelli destinati a essere copiati e incollati per l'esecuzione devono usare il markup di stile del blocco seguente:

~~~markdown
```powershell
<Your PowerShell code goes here>
```
~~~

L'output visualizzato dai comandi di PowerShell deve essere racchiuso in un blocco di codice **Output** per evitare l'evidenziazione della sintassi. Ad esempio:

~~~markdown
```powershell
Get-Command -Module Microsoft.PowerShell.Security
```

```Output
CommandType  Name                        Version    Source
-----------  ----                        -------    ------
Cmdlet       ConvertFrom-SecureString    3.0.0.0    Microsoft.PowerShell.Security
Cmdlet       ConvertTo-SecureString      3.0.0.0    Microsoft.PowerShell.Security
Cmdlet       Get-Acl                     3.0.0.0    Microsoft.PowerShell.Security
Cmdlet       Get-AuthenticodeSignature   3.0.0.0    Microsoft.PowerShell.Security
Cmdlet       Get-CmsMessage              3.0.0.0    Microsoft.PowerShell.Security
Cmdlet       Get-Credential              3.0.0.0    Microsoft.PowerShell.Security
Cmdlet       Get-ExecutionPolicy         3.0.0.0    Microsoft.PowerShell.Security
Cmdlet       Get-PfxCertificate          3.0.0.0    Microsoft.PowerShell.Security
Cmdlet       New-FileCatalog             3.0.0.0    Microsoft.PowerShell.Security
Cmdlet       Protect-CmsMessage          3.0.0.0    Microsoft.PowerShell.Security
Cmdlet       Set-Acl                     3.0.0.0    Microsoft.PowerShell.Security
Cmdlet       Set-AuthenticodeSignature   3.0.0.0    Microsoft.PowerShell.Security
Cmdlet       Set-ExecutionPolicy         3.0.0.0    Microsoft.PowerShell.Security
Cmdlet       Test-FileCatalog            3.0.0.0    Microsoft.PowerShell.Security
Cmdlet       Unprotect-CmsMessage        3.0.0.0    Microsoft.PowerShell.Security
```
~~~

L'etichetta del codice **Output** non corrisponde a un "linguaggio" ufficiale supportato dal sistema di evidenziazione della sintassi.
Questa etichetta è tuttavia utile perché OPS aggiunge l'etichetta "Output" al frame della casella di codice nella pagina Web. La casella di codice "Output" non presenta l'evidenziazione della sintassi.

## <a name="coding-style-rules"></a>Regole dello stile di codifica

### <a name="avoid-line-continuation-in-code-samples"></a>Evitare la continuazione di riga negli esempi di codice

Evitare di usare i caratteri di continuazione di riga (`` ` ``) negli esempi di codice PowerShell. Questi caratteri sono difficili da visualizzare e possono causare problemi se alla fine della riga sono presenti spazi aggiuntivi.

- Usare lo splatting di PowerShell per ridurre la lunghezza della riga per i cmdlet che hanno numerosi parametri.
- Sfruttare i vantaggi delle opportunità naturali di interruzione riga di PowerShell, ad esempio dopo i caratteri pipe (`|`), le parentesi graffe di apertura, le parentesi tonde e le parentesi quadre.

### <a name="avoid-using-powershell-prompts-in-examples"></a>Evitare di usare le richieste di PowerShell negli esempi

L'uso della stringa di richiesta è sconsigliato e deve essere limitato agli scenari che hanno lo scopo di illustrare l'uso della riga di comando. Per la maggior parte di questi esempi, la stringa di richiesta dovrebbe essere `PS>`. Questa richiesta è indipendente dagli indicatori specifici del sistema operativo.

Le richieste sono necessarie per gli esempi con comandi che modificano la richiesta stessa o quando il percorso visualizzato è significativo per lo scenario illustrato. L'esempio seguente illustra come viene modificata la richiesta quando si usa il provider del Registro di sistema.

```powershell
PS C:\> cd HKCU:\System\
PS HKCU:\System\> dir

    Hive: HKEY_CURRENT_USER\System

Name                   Property
----                   --------
CurrentControlSet
GameConfigStore        GameDVR_Enabled                       : 1
                       GameDVR_FSEBehaviorMode               : 2
                       Win32_AutoGameModeDefaultProfile      : {2, 0, 1, 0...}
                       Win32_GameModeRelatedProcesses        : {1, 0, 1, 0...}
                       GameDVR_HonorUserFSEBehaviorMode      : 0
                       GameDVR_DXGIHonorFSEWindowsCompatible : 0
```

### <a name="do-not-use-aliases-in-examples"></a>Non usare alias negli esempi

È consigliabile usare sempre il nome completo di tutti i cmdlet e i parametri, salvo quando si vuole specificare l'alias stesso. I nomi di cmdlet e parametri devono usare nomi definiti in base alle convenzioni Pascal.

### <a name="using-parameters-in-examples"></a>Uso di parametri negli esempi

Evitare l'uso di parametri posizionali. È in genere consigliabile includere sempre il nome del parametro in un esempio, anche se il parametro è posizionale. Questo riduce la possibilità di confusione negli esempi.

## <a name="next-steps"></a>Passaggi successivi

[Modifica delle informazioni di riferimento sui cmdlet](editing-cmdlet-ref.md)

<!-- External URLs -->
[platyPS]: https://github.com/PowerShell/platyPS
[markdig]: https://github.com/lunet-io/markdig
[CommonMark]: https://spec.commonmark.org/
[atx]: https://github.github.com/gfm/#atx-headings
[pascal-case]: https://en.wikipedia.org/wiki/PascalCase
[reflow]: https://marketplace.visualstudio.com/items?itemName=marvhen.reflow-markdown
