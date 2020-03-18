---
title: Guida di stile per la documentazione di PowerShell
description: Questo articolo include le regole di stile per la scrittura della documentazione di PowerShell.
ms.date: 03/05/2020
ms.topic: conceptual
ms.openlocfilehash: 964536c5195c3bb8abd98b5996a96fc7b9362489
ms.sourcegitcommit: c97dcf1e00ef540e7464c36c88f841474060044c
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 03/15/2020
ms.locfileid: "79402578"
---
# <a name="powershell-docs-style-guide"></a>Guida di stile per la documentazione di PowerShell

Questo articolo è una guida di stile specifica per il contenuto di documentazione di PowerShell. Le linee guida si basano sulle informazioni incluse nella [Panoramica ](overview.md#get-started-writing-docs).

## <a name="product-terminology"></a>Terminologia del prodotto

Sono disponibili diverse varianti di PowerShell.
Questa tabella definisce alcuni termini usati nel contesto di PowerShell.

- **PowerShell**: è la definizione predefinita. Da questo punto in poi, per PowerShell si intende PowerShell 7 e versioni successive.

- **PowerShell Core**: PowerShell basato su .NET Core. L'uso del termine **Core** deve essere limitato ai casi in cui è necessario distinguere da Windows PowerShell.

- **Windows PowerShell**: PowerShell basato su .NET Framework. Windows PowerShell è disponibile solo in Windows e richiede il framework completo.

In generale i riferimenti a "Windows PowerShell" nella documentazione possono essere modificati in "PowerShell".
La dicitura "Windows PowerShell" **non** deve essere modificata quando si cita tecnologia specifica per Windows.

## <a name="markdown-specifics"></a>Specifiche di Markdown

Il sistema Microsoft Open Publishing (OPS) che compila la documentazione usa [markdig][] per elaborare i documenti Markdown. Markdig analizza i documenti in base alle regole della specifica [CommonMark][] più recente.

La nuova specifica CommonMark è molto più restrittiva in merito alla costruzione di alcuni elementi Markdown. Prestare particolare attenzione ai dettagli inclusi in questo documento.

### <a name="blank-lines-spaces-and-tabs"></a>Righe vuote, spazi e tabulazioni

Rimuovere le righe vuote duplicate. Più righe vuote vengono sottoposte a rendering come una singola riga vuota in HTML, quindi non necessario usare più righe vuote.

Le righe vuote segnalano anche la fine di un blocco in Markdown. Deve essere presente un solo spazio vuoto tra i blocchi Markdown di tipi diversi, ad esempio tra un paragrafo e un elenco o un'intestazione.

> [!NOTE]
> La spaziatura è importante in Markdown. Usare sempre gli spazi anziché le tabulazioni hard. Rimuovere gli spazi aggiuntivi alla fine delle righe.

### <a name="titles-and-headings"></a>Titoli e intestazioni

Usare solo [intestazioni ATX][atx] (con lo stile #, anziché intestazioni con stile `=` o `-`).

- Usare la maiuscola a inizio frase: solo i nomi propri e la prima lettera di un titolo o di un'intestazione devono essere in maiuscole
- Deve essere presente uno spazio singolo tra `#` e la prima lettera dell'intestazione
- Le intestazioni devono essere racchiuse da una sola riga vuota
- Ogni documento deve includere un solo titolo H1
- I livelli di intestazione devono avere incrementi di uno. Non ignorare i livelli
- Non usare il grassetto o altri markup nelle intestazioni

### <a name="limit-line-length-to-100-characters"></a>Limitare la lunghezza della riga a 100 caratteri

Questo vale per gli articoli concettuali e i riferimenti ai cmdlet. Il testo dei titoli Informazioni su può avere una lunghezza massima di 80 caratteri.
La limitazione della lunghezza della riga migliora i diff e la cronologia dei GIT in termini di leggibilità. Semplifica anche i contributi da parte di altri writer.

Usare l'estensione [Reflow Markdown][reflow] in Visual Studio Code per reimpostare facilmente il flusso dei paragrafi, in modo da adattarlo alla lunghezza di riga prescritta.

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

### <a name="formatting-command-syntax-elements"></a>Formattazione degli elementi della sintassi del comando

- Usare sempre il nome completo per i cmdlet e i parametri. Evitare di usare alias, a meno che non si stia dimostrando in modo specifico l'alias.

- All'interno di un paragrafo le parole chiave del linguaggio, i nomi dei cmdlet, le variabili e i percorsi di file devono essere racchiusi tra caratteri accento grave (`` ` ``). I nomi di proprietà, parametri e classi devono essere in **grassetto**.

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

- Quando si fa riferimento a comandi esterni (exe, script e così via), il nome del comando deve essere in grassetto, tutto in minuscolo (o con iniziale maiuscola se all'inizio di una frase) e includere l'estensione di file appropriata. Ad esempio:

  ```markdown
  For example, on Windows systems, you can use the `net start` and `net stop` commands
  to start and stop a service. **Sc.exe** is another service control tool for Windows.
  That name does not fit into the naming pattern for the **net.exe** service commands.
  ```

- Quando si visualizza un esempio d'uso di un comando esterno, l'esempio deve essere racchiuso tra caratteri accento grave.
  In caso di conflitto di nomi con un alias, è necessario includere l'estensione file nell'esempio di comando. Ad esempio:

  ```markdown
  To start the spooler service on a remote computer named DC01, you type `sc.exe \\DC01 start spooler`.
  ```

- Durante la scrittura di un articolo concettuale (diversamente dal contenuto di riferimento), la prima istanza del nome di un cmdlet deve essere un collegamento alla documentazione del cmdlet. Non usare accenti gravi, grassetto o altri elementi di markup all'interno delle parentesi quadre di un collegamento ipertestuale.

  Ad esempio:

  ```markdown
  This [Write-Host](/powershell/module/Microsoft.PowerShell.Utility/Write-Host) cmdlet
  uses the **Object** parameter to ...
  ```

  Per altre informazioni, vedere la sezione [Collegamenti ipertestuali](#hyperlinks) di questo articolo.

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

[Microsoft Docs Authoring Pack](/contribute/how-to-write-docs-auth-pack) contiene strumenti che supportano funzionalità specifiche del sistema di pubblicazione. Gli avvisi sono un'estensione Markdown per la creazione di citazioni che vengono restituite in docs.microsoft.com con colori e icone che evidenziano il significato del contenuto. Sono supportati i tipi di avviso seguenti:

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

> [!NOTE]
> Informazioni che l'utente deve notare anche in una consultazione veloce.

> [!TIP]
> Informazioni facoltative che consentono a un utente di ottenere risultati più efficaci.

> [!IMPORTANT]
> Informazioni essenziali necessarie per l'esito positivo.

> [!CAUTION]
> Potenziali conseguenze negative di un'azione.

> [!WARNING]
> Conseguenze pericolose certe di un'azione.

## <a name="hyperlinks"></a>Collegamenti ipertestuali

- Evitare l'uso di URL semplici. I collegamenti devono usare la sintassi Markdown `[friendlyname](url-or-path)`
- Gli URL semplici possono essere usati quando necessario, ma devono essere racchiusi tra caratteri accento grave. Ad esempio:

  ```markdown
  By default, if you do not specify this parameter, the DMTF standard resource URI
  `http://schemas.dmtf.org/wbem/wscim/1/cim-schema/2/` is used and the class name is appended to it.
  ```

- Se possibile, i collegamenti URL devono essere di tipo HTTPS.
- I collegamenti devono avere un nome descrittivo, in genere il titolo dell'argomento collegato
- Tutti gli elementi nella sezione "Collegamenti correlati" in fondo all'articolo devono essere impostati come collegamenti ipertestuali.
- Non usare accenti gravi, grassetto o altri elementi di markup all'interno delle parentesi quadre di un collegamento ipertestuale.

### <a name="linking-to-other-content"></a>Collegamento a contenuto diverso

Il sistema di pubblicazione supporta due tipi di collegamenti ipertestuali: URL e collegamenti a file.

Un collegamento URL può essere un percorso URL relativo alla radice docs.microsoft.com. Oppure può essere un URL assoluto, che include la sintassi completa dell'URL. (Ad esempio: `https:/github.com/MicrosoftDocs/PowerShell-Docs`)

- Usare i collegamenti URL per il collegamento a contenuto esterno a PowerShell-Docs o il collegamento tra riferimenti ai cmdlet e articoli concettuali in PowerShell-Docs.
- Il modo più semplice per creare un collegamento relativo consiste nel copiare l'URL dal browser, quindi rimuovere `https://docs.microsoft.com/en-us` dal valore incollato in Markdown.
   - Non includere le impostazioni locali negli URL nelle proprietà Microsoft (ad esempio, rimuovere "/it-IT" dall'URL).
- Tutti gli URL che puntano a siti Web esterni devono usare HTTPS, a meno che ciò non sia valido per il sito di destinazione.

Un collegamento file viene usato per il collegamento da un articolo di riferimento a un altro o da un articolo concettuale a un altro. Per creare un collegamento a un articolo di riferimento per una versione specifica di PowerShell, è necessario usare un collegamento URL.

- I collegamenti file contengono un percorso di file relativo (ad esempio: `../folder/file.md`)
- Tutti i percorsi di file usano caratteri barra (`/`)

## <a name="formatting-code-samples"></a>Esempi di formattazione del codice

Markdown supporta due stili di codice:

- Intervalli di codice (inline): contrassegnati da un singolo carattere accento grave (`` ` ``). Sono usati all'interno di un paragrafo anziché come blocchi autonomi.
- Blocchi di codice: blocchi a più righe racchiusi fra stringhe con triplo carattere accento grave (`` ``` ``). I blocchi di codice possono anche avere un'etichetta di linguaggio dopo i caratteri accento grave. L'etichetta di linguaggio consente l'evidenziazione della sintassi per il contenuto del blocco di codice.

### <a name="using-code-blocks"></a>Uso dei blocchi di codice

Markdown consente l'uso dei rientri per indicare un blocco di codice, ma questo criterio può essere problematico e deve essere evitato. Tutti i blocchi di codice devono essere inclusi in un intervallo di codice. Un intervallo di codice è un blocco di codice racchiuso fra stringhe con triplo accento grave (`` ``` ``). I marcatori dell'intervallo di codice devono trovarsi su una riga a parte, prima e dopo l'esempio di codice. Il marcatore all'inizio del blocco di codice può avere un'etichetta del linguaggio facoltativa. Microsoft Open Publishing System (OPS) usa l'etichetta del linguaggio per supportare la funzionalità di evidenziazione della sintassi.

OPS aggiunge anche un pulsante **Copy** (Copia) che copia il contenuto del blocco di codice negli Appunti. In questo modo è possibile incollare rapidamente il codice in uno script per eseguire il test dell'esempio di codice. Ma non tutti gli esempi nella documentazione sono destinati all'esecuzione. Alcuni blocchi di codice sono semplici illustrazioni di un concetto di PowerShell.

Nella documentazione vengono usati due tipi di blocchi di codice:

1. Esempi illustrativi
2. Esempi eseguibili

### <a name="syntax-code-blocks"></a>Blocchi di codice di sintassi

Questo esempio illustra tutti i possibili parametri del cmdlet `Get-Command`.

~~~markdown
```
Get-Command [-Verb <String[]>] [-Noun <String[]>] [-Module <String[]>]
  [-FullyQualifiedModule <ModuleSpecification[]>] [-TotalCount <Int32>] [-Syntax] [-ShowCommandInfo]
  [[-ArgumentList] <Object[]>] [-All] [-ListImported] [-ParameterName <String[]>]
  [-ParameterType <PSTypeName[]>] [<CommonParameters>]
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

Gli esempi illustrativi vengono usati per descrivere un concetto di PowerShell. Non sono pensati per essere copiati negli Appunti per l'esecuzione. Vengono usati soprattutto per esempi semplici e facili da digitare.
Vengono anche usati per esempi di sintassi quando si vuole illustrare la sintassi di un comando. Il blocco di codice può contenere output di esempio del comando che viene illustrato.

Ecco un esempio semplice che presenta gli operatori di confronto di PowerShell:

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

Si noti che questo esempio include il prompt di PowerShell semplificato e visualizza l'output risultante. In questo caso, non è previsto che l'utente copi ed esegua l'esempio.

### <a name="executable-examples"></a>Esempi eseguibili

Gli esempi più complessi o quelli da usare per la copia e l'esecuzione devono usare il markup di stile del blocco seguente:

~~~markdown
```powershell
<PowerShell code goes here>
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

È consigliabile usare sempre il nome completo di tutti i cmdlet e i parametri, salvo quando si vuole specificare l'alias stesso. I nomi di cmdlet e parametri devono usare l'ortografia corretta definita nel codice.

### <a name="using-parameters-in-examples"></a>Uso di parametri negli esempi

Evitare l'uso di parametri posizionali. In generale è consigliabile usare sempre il nome del parametro in un esempio, anche se il parametro è posizionale. Questo riduce la possibilità di confusione negli esempi.

## <a name="next-steps"></a>Passaggi successivi

[Modifica delle informazioni di riferimento sui cmdlet](editing-cmdlet-ref.md)

<!-- External URLs -->
[platyPS]: https://github.com/PowerShell/platyPS
[markdig]: https://github.com/lunet-io/markdig
[CommonMark]: https://spec.commonmark.org/
[atx]: https://github.github.com/gfm/#atx-headings
[pascal-case]: https://en.wikipedia.org/wiki/PascalCase
[reflow]: https://marketplace.visualstudio.com/items?itemName=marvhen.reflow-markdown
