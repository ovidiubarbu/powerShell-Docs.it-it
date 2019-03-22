---
title: Informazioni sulla codifica di file in VSCode e PowerShell
description: Configurare la codifica di file in VS Code e PowerShell
ms.date: 02/28/2019
ms.openlocfilehash: 73e766832d56a08bd5ef16df11899a0aab0badae
ms.sourcegitcommit: 5990f04b8042ef2d8e571bec6d5b051e64c9921c
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 03/12/2019
ms.locfileid: "57795116"
---
# <a name="understanding-file-encoding-in-vscode-and-powershell"></a>Informazioni sulla codifica di file in VSCode e PowerShell

Quando si usa VS Code per creare e modificare gli script di PowerShell, è importante che i file vengano salvati usando il formato corretto della codifica dei caratteri.

## <a name="what-is-file-encoding-and-why-is-it-important"></a>Che cos'è la codifica dei file e perché è importante?

VS Code gestisce l'interfaccia tra una persona che immette stringhe di caratteri in un buffer e i blocchi di lettura/scrittura di byte nel File system. Quando VS Code salva un file, usa un codifica di testo per eseguire l'operazione.

Analogamente, quando PowerShell esegue uno script deve convertire i byte di un file in caratteri per ricostruire il file in un programma di PowerShell. Poiché VS Code scrive il file e PowerShell legge il file, devono usare lo stesso sistema di codifica. Il processo di analisi di uno script di PowerShell script è: *byte* -> *caratteri* -> *token* -> *albero sintattico astratto* -> *esecuzione*.

Sia VS Code che PowerShell vengono installati con una configurazione di codifica predefinita appropriata. Tuttavia la codifica predefinita usata da PowerShell è cambiata con il rilascio di PowerShell Core (v6.x). Per assicurarsi di non avere problemi usando PowerShell o l'estensione di PowerShell in VS Code, è necessario configurare le impostazioni di VS Code e di PowerShell in modo corretto.

## <a name="common-causes-of-encoding-issues"></a>Cause più comuni dei problemi di codifica

I problemi di codifica si verificano se la codifica di VS Code o il file di script non corrisponde alla codifica prevista di PowerShell. Non è possibile per PowerShell determinare automaticamente la codifica del file.

I problemi di codifica si verificano con maggiore probabilità quando si usano caratteri non del [set di caratteri ASCII a 7 bit](https://ascii.cl/). Ad esempio:

- Caratteri latini accentati (`É`, `ü`)
- Caratteri non latini, ad esempio cirillico (`Д`, `Ц`)
- Cinese Han (`脚`, `本`)

I motivi comuni per i problemi di codifica sono:

- Le codifiche di VSCode e PowerShell non sono state modificate rispetto ai valori predefiniti. Per PowerShell 5.1 e versioni precedenti la codifica predefinita è diversa da quella di VSCode.
- Un altro editor ha aperto e sovrascritto il file in una nuova codifica. Ciò si verifica spesso con ISE.
- Il file è sottoposto al controllo del codice sorgente in una codifica diversa da quella prevista da VS Code o PowerShell. Questa situazione può verificarsi quando i collaboratori usano editor con diverse configurazioni di codifica.

### <a name="how-to-tell-when-you-have-encoding-issues"></a>Come sapere quando sono presenti problemi di codifica

Spesso gli errori di codifica si presentano come errori di analisi negli script. Se si rilevano strane sequenze di caratteri nello script, questo può essere il problema. Nell'esempio seguente un trattino (`–`) viene visualizzato come i caratteri `â€“`:

```Output
Send-MailMessage : A positional parameter cannot be found that accepts argument 'Testing FuseMail SMTP...'.
At C:\Users\<User>\<OneDrive>\Development\PowerShell\Scripts\Send-EmailUsingSmtpRelay.ps1:6 char:1
+ Send-MailMessage â€“From $from â€“To $recipient1 â€“Subject $subject  ...
+ ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
    + CategoryInfo          : InvalidArgument: (:) [Send-MailMessage], ParameterBindingException
    + FullyQualifiedErrorId : PositionalParameterNotFound,Microsoft.PowerShell.Commands.SendMailMessage
```

Questo problema si verifica perché VS Code codifica il carattere `–` in formato UTF-8 come i byte `0xE2 0x80 0x93`.
Quando questi byte vengono decodificati come Windows-1252, vengono interpretati come caratteri `â€“`.

Di seguito sono riportate alcune sequenze di caratteri insolite che potrebbero essere visualizzate:

<!-- markdownlint-disable MD038 -->
- `â€“` invece di `–`
- `â€”` invece di `—`
- `Ã„2` invece di `Ä`
- `Â` invece di ` ` (spazio unificatore)
- `Ã©` invece di `é`
<!-- markdownlint-enable MD038 -->

In questo utile [riferimento](https://www.i18nqa.com/debug/utf8-debug.html) sono elencati i modelli che più spesso indicano un problema di codifica UTF-8 o Windows-1252.

## <a name="how-the-powershell-extension-in-vscode-interacts-with-encodings"></a>Modalità di interazione con le codifiche dell'estensione di PowerShell in VS Code

L'estensione di PowerShell interagisce con gli script in diversi modi:

1. Quando gli script vengono modificati in VS Code, i contenuti vengono inviati da VS Code all'estensione. Il [protocollo di server di linguaggio][] impone che il contenuto venga trasferito in UTF-8. Di conseguenza, non è possibile che l'estensione riceva la codifica non corretta.
2. Quando gli script vengono eseguiti direttamente nella console integrata, vengono letti da PowerShell direttamente dal file. Se la codifica di PowerShell è diversa da quella di VSCode, si può verificare un problema.
3. Quando uno script aperto in VSCode fa riferimento a un altro script che non è aperto in VS Code, l'estensione esegue il fallback al caricamento del contenuto dello script dal File system. L'estensione di PowerShell per impostazione predefinita usa la codifica UTF-8, ma usa il rilevamento [byte order mark][], o BOM, per selezionare la codifica corretta.

Il problema si verifica quando si presuppone l'uso della codifica dei formati senza BOM, ad esempio [UTF-8][] senza BOM e [Windows-1252][].
L'estensione di PowerShell usa UTF-8 come valore predefinito. L'estensione non è in grado di modificare le impostazioni di codifica di VS Code.
Per altre informazioni, vedere il [problema n. 824](https://github.com/Microsoft/vscode/issues/824).

## <a name="choosing-the-right-encoding"></a>Scelta della codifica corretta

Applicazioni e sistemi diversi possono usare codifiche diverse:

- In .NET Standard, sul Web e nel mondo Linux, UTF-8 è ora la codifica dominante.
- Molte applicazioni .NET Framework usano la codifica [UTF-16][]. Per motivi storici, a volte viene definita "Unicode", un termine che ora si riferisce a uno [standard](https://en.wikipedia.org/wiki/Unicode) diffuso che include sia UTF-8 che UTF-16.
- In Windows molte applicazioni native precedenti a Unicode continuano a usare Windows-1252 per impostazione predefinita.

Le codifiche Unicode prevedono inoltre il concetto di un byte order mark (BOM). I BOM si trovano all'inizio del testo per indicare a un decodificatore quale codifica sta usando il testo. Per le codifiche multibyte, il BOM indica anche l'[ordine dei byte](https://en.wikipedia.org/wiki/Endianness) della codifica. I BOM sono progettati come byte che si verificano raramente nel testo non Unicode e la presenza di un BOM suggerisce che un testo è Unicode.

I BOM sono facoltativi e la loro adozione non è altrettanto diffusa nel mondo Linux perché viene usata ovunque una convenzione affidabile di UTF-8. La maggior parte delle applicazioni Linux presume che l'input di testo sia codificato in UTF-8. Benché molte applicazioni di Linux siano in grado di riconoscere e gestire correttamente un BOM, alcune non lo sono e la manipolazione del testo in queste applicazioni produce degli artefatti.

**Di conseguenza**:

- Se si lavora principalmente con le applicazioni Windows e Windows PowerShell, è preferibile la codifica UTF-8 con BOM o UTF-16.
- Se si lavora su varie piattaforme, è preferibile usare UTF-8 con BOM.
- Se si lavora principalmente in contesti associati a Linux, è preferibile usare UTF-8 senza BOM.
- Windows-1252 e latin-1 sono essenzialmente le codifiche legacy che è opportuno evitare, se possibile.
  Tuttavia, alcune applicazioni Windows più datate possono dipendere da esse.
- È anche importante notare che la firma degli script [dipende dalla codifica](https://github.com/PowerShell/PowerShell/issues/3466), ovvero una modifica della codifica in uno script firmato richiede una nuova operazione di firma.

## <a name="configuring-vscode"></a>Configurazione di VS Code

La codifica predefinita di VS Code è UTF-8 senza BOM.

Per impostare la [codifica di VS Code][], accedere alle impostazioni di VS Code (<kbd>CTRL<kbd>+</kbd>,</kbd>) e specificare l'impostazione `"files.encoding"`:

```json
"files.encoding": "utf8bom"
```

Alcuni valori possibili sono:

- `utf8`: [UTF-8] senza BOM
- `utf8bom`: [UTF-8] con BOM
- `utf16le`: [UTF-16] little endian
- `utf16be`: [UTF-16] big endian
- `windows1252`: [Windows-1252]

Per questo oggetto è possibile ottenere un elenco a discesa nella visualizzazione GUI o i relativi completamenti nella visualizzazione JSON.

È anche possibile aggiungere quanto segue per rilevare automaticamente la codifica quando è possibile:

```json
"files.autoGuessEncoding": true
```

Se si vuole evitare che queste impostazioni influiscano su tutti i tipi di file, VS Code consente anche di definire configurazioni diverse in base al linguaggio. Per creare un'impostazione specifica del linguaggio, inserire le impostazioni in un campo `[<language-name>]`. Ad esempio:

```json
"[powershell]": {
    "files.encoding": "utf8bom",
    "files.autoGuessEncoding": true
}
```

## <a name="configuring-powershell"></a>Configurazione di PowerShell

La codifica predefinita di PowerShell varia a seconda della versione:

- In PowerShell 6 o versione successiva la codifica predefinita è UTF-8 senza BOM su tutte le piattaforme.
- In Windows PowerShell la codifica predefinita normalmente è Windows-1252, un'estensione di [latin-1][], nota anche come ISO 8859-1.

In PowerShell 5 o versione successiva è possibile trovare la codifica predefinita in questo modo:

```powershell
[psobject].Assembly.GetTypes() | Where-Object { $_.Name -eq 'ClrFacade'} |
  ForEach-Object {
    $_.GetMethod('GetDefaultEncoding', [System.Reflection.BindingFlags]'nonpublic,static').Invoke($null, @())
  }
```

Lo [script](https://gist.github.com/rjmholt/3d8dd4849f718c914132ce3c5b278e0e) seguente può essere usato per determinare ciò che deduce la codifica della sessione di PowerShell per uno script senza BOM.

```powershell
$badBytes = [byte[]]@(0xC3, 0x80)
$utf8Str = [System.Text.Encoding]::UTF8.GetString($badBytes)
$bytes = [System.Text.Encoding]::ASCII.GetBytes('Write-Output "') + [byte[]]@(0xC3, 0x80) + [byte[]]@(0x22)
$path = Join-Path ([System.IO.Path]::GetTempPath()) 'encodingtest.ps1'

try
{
    [System.IO.File]::WriteAllBytes($path, $bytes)

    switch (& $path)
    {
        $utf8Str
        {
            return 'UTF-8'
            break
        }

        default
        {
            return 'Windows-1252'
            break
        }
    }
}
finally
{
    Remove-Item $path
}
```

È possibile configurare PowerShell in modo che usi una codifica specifica più in generale usando le impostazioni del profilo. Vedere gli articoli seguenti:

- [@mklement0]: [risposta sulla codifica di PowerShell per StackOverflow](https://stackoverflow.com/a/40098904).
- [@rkeithhill]: [post di blog sulla gestione dell'input UTF-8 senza BOM in PowerShell](https://rkeithhill.wordpress.com/2010/05/26/handling-native-exe-output-encoding-in-utf8-with-no-bom/).

Non è possibile forzare PowerShell perché usi una codifica specifica per l'input. PowerShell 5.1 e versioni precedenti per impostazione predefinita usa la codifica Windows-1252 quando non è presente alcun BOM. Per motivi di interoperabilità, è preferibile salvare gli script in formato Unicode con BOM.

> [!IMPORTANT]
> Le scelte in termini di codifica possono influire su eventuali altri strumenti che usano gli script di PowerShell o può essere opportuno codificare di nuovo gli script usando un'altra codifica.

### <a name="existing-scripts"></a>Script esistenti

Può essere necessario ricodificare gli script già presenti nel file system in base alla nuova codifica scelta. Nella barra inferiore di VS Code viene visualizzata l'etichetta UTF-8. Fare clic sull'etichetta per aprire la barra delle azioni e selezionare **Salva con codifica**. È ora possibile selezionare una nuova codifica per il file. Vedere [Codifica di VS Code][] per le istruzioni complete.

Se è necessario codificare di nuovo più file, è possibile usare lo script seguente:

```powershell
Get-ChildItem *.ps1 -Recurse | ForEach-Object {
    $content = Get-Content -Path $_
    Set-Content -Path $_.Fullname -Value $content -Encoding UTF8 -PassThru -Force
}
```

### <a name="the-powershell-integrated-scripting-environment-ise"></a>PowerShell Integrated Scripting Environment (ISE)

Se inoltre si modificano gli script con l'ISE di PowerShell, è necessario sincronizzare le impostazioni di codifica nell'ISE.

L'ISE deve rispettare un BOM, ma è anche possibile usare la reflection per [impostare la codifica](https://bensonxion.wordpress.com/2012/04/25/powershell-ise-default-saveas-encoding/).
Si noti che questa condizione non sarebbe persistente da un avvio all'altro.

### <a name="source-control-software"></a>Software di controllo del codice sorgente

Alcuni strumenti per il controllo del codice sorgente ignorano le codifiche, ad esempio GIT tiene traccia solo dei byte.
Altri strumenti, ad esempio TFS o Mercurial, si comportano diversamente. Anche alcuni strumenti basati su GIT usano la decodifica del testo.

In questo caso verificare quanto segue:

- Configurare la codifica del testo nel controllo del codice sorgente in modo che corrisponda alla configurazione di VS Code.
- Verificare che tutti i file vengano sottoposti al controllo del codice sorgente con la codifica pertinente.
- Fare attenzione alle modifiche della codifica segnalate dal controllo del codice sorgente. Un segno evidente è un diff che indica la presenza di modifiche quando apparentemente non ce ne sono (perché i byte sono cambiati e i caratteri no).

### <a name="collaborators-environments"></a>Ambienti dei collaboratori

Oltre a configurare il controllo del codice sorgente, verificare che i collaboratori che accedono ai file condivisi non usino impostazioni che sostituiscono la codifica in uso ricodificando i file di PowerShell.

### <a name="other-programs"></a>Altri programmi

Qualsiasi altro programma che legge o scrive uno script di PowerShell può ricodificarlo.

Di seguito sono riportati alcuni esempi:

- Uso degli Appunti per copiare e incollare uno script. Questa situazione è comune in scenari come:
  - Copia di uno script in una macchina virtuale
  - Copia di uno script da un messaggio di posta elettronica o una pagina Web
  - Copia di uno script in o da un documento Microsoft Word o PowerPoint
- Altri editor di testo, ad esempio:
  - Blocco note
  - vim
  - Qualsiasi altro editor di script di PowerShell
- Utilità di modifica del testo, ad esempio:
  - `Get-Content`/`Set-Content`/`Out-File`
  - Operatori di reindirizzamento di PowerShell, ad esempio `>` e `>>`
  - `sed`/`awk`
- Programmi di trasferimento file, ad esempio:
  - Un Web browser, durante il download degli script
  - Una condivisione file

Alcuni di questi strumenti gestiscono i byte anziché il testo, ma altri offrono configurazioni di codifica. Nei casi in cui è necessario configurare una codifica, tenere presente che deve essere la stessa codifica usata dall'editor per evitare problemi.

## <a name="other-resources-on-encoding-in-powershell"></a>Altre risorse per la codifica in PowerShell

Esistono alcuni post interessanti sulla codifica e la configurazione della codifica in PowerShell che vale la pena leggere:

- [@mklement0]: [riepilogo della codifica di PowerShell per StackOverflow](https://stackoverflow.com/questions/40098771/changing-powershells-default-output-encoding-to-utf-8)
- Problemi segnalati in precedenza in vscode-PowerShell riguardo alla codifica dei problemi:
  - [#1308](https://github.com/PowerShell/vscode-powershell/issues/1308)
  - [#1628](https://github.com/PowerShell/vscode-powershell/issues/1628)
  - [#1680](https://github.com/PowerShell/vscode-powershell/issues/1680)
  - [#1744](https://github.com/PowerShell/vscode-powershell/issues/1744)
  - [#1751](https://github.com/PowerShell/vscode-powershell/issues/1751)
- [Il classico documento *Joel on Software* su Unicode](https://www.joelonsoftware.com/2003/10/08/the-absolute-minimum-every-software-developer-absolutely-positively-must-know-about-unicode-and-character-sets-no-excuses/)
- [Codifica in .NET Standard](https://github.com/dotnet/standard/issues/260#issuecomment-289549508)


[@mklement0]: https://github.com/mklement0
[@rkeithhill]: https://github.com/rkeithhill
[Windows-1252]: https://wikipedia.org/wiki/Windows-1252
[latin-1]: https://wikipedia.org/wiki/ISO/IEC_8859-1
[UTF-8]: https://wikipedia.org/wiki/UTF-8
[byte order mark]: https://wikipedia.org/wiki/Byte_order_mark
[UTF-16]: https://wikipedia.org/wiki/UTF-16
[Protocollo di server di linguaggio]: https://microsoft.github.io/language-server-protocol/
[Codifica di VS Code]: https://code.visualstudio.com/docs/editor/codebasics#_file-encoding-support
