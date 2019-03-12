---
title: Informazioni sulla codifica di file in VSCode e PowerShell
description: Configurare la codifica di file in Visual Studio code e PowerShell
ms.date: 02/28/2019
ms.openlocfilehash: 9cf445ebd0c2bb2dbdf4438f02dafe3df3a5d1e2
ms.sourcegitcommit: 69abc5ad16e5dd29ddfb1853e266a4bfd1d59d59
ms.translationtype: MTE95
ms.contentlocale: it-IT
ms.lasthandoff: 03/05/2019
ms.locfileid: "57429806"
---
# <a name="understanding-file-encoding-in-vscode-and-powershell"></a>Informazioni sulla codifica di file in VSCode e PowerShell

Quando si usa Visual Studio Code per creare e modificare gli script di PowerShell, è importante che i file vengono salvati utilizzando il formato di codifica di carattere corretto.

## <a name="what-is-file-encoding-and-why-is-it-important"></a>Che cos'è la codifica dei file e perché è importante?

Visual Studio code gestisce l'interfaccia tra una risorse umane immettendo stringhe di caratteri in un buffer e blocchi di lettura/scrittura di byte nel file System. Quando Visual Studio code consente di salvare un file, Usa un codifica a tale scopo del testo.

Allo stesso modo, quando si esegue uno script di PowerShell è necessario convertire i byte in un file in caratteri per ricostruire il file in un programma di PowerShell. Poiché Visual Studio code scrive il file e PowerShell legge il file, devono usare lo stesso sistema di codifica. Questo processo di analisi di uno script di PowerShell passa: *byte* -> *caratteri* -> *token*  ->   *albero sintattico astratto* -> *esecuzione*.

Visual Studio code sia PowerShell vengono installati con una configurazione di codifica predefinito adeguato. Tuttavia, la codifica predefinita utilizzata da PowerShell è stato modificato con la versione di PowerShell Core (v6.x). Per assicurarsi di non aver problemi tramite PowerShell o l'estensione di PowerShell in Visual Studio code, è necessario configurare le impostazioni di Visual Studio code e PowerShell in modo corretto.

## <a name="common-causes-of-encoding-issues"></a>Cause più comuni dei problemi di codifica

Problemi di codifica si verificano durante la codifica di Visual Studio code o file di script non corrispondono alla codifica prevista di PowerShell. Non è possibile per PowerShell determinare automaticamente la codifica del file.

Si è più soggetto a problemi di codifica quando si usano caratteri non nel [set di caratteri ASCII a 7 bit](https://ascii.cl/). Ad esempio:

- I caratteri latin accentati (`É`, `ü`)
- Caratteri non latini come cirillico (`Д`, `Ц`)
- Han cinese (`脚`, `本`)

Motivi comuni per i problemi di codifica sono:

- Le codifiche di VSCode e PowerShell non sono state modificate i valori predefiniti. Per PowerShell 5.1 e versioni precedenti, il valore predefinito è diversa da VSCode codifica.
- Un altro editor è aperto e sovrascrivere il file in una nuova codifica. Ciò si verifica spesso con ISE.
- Il file è archiviato nel controllo del codice sorgente in una codifica diversa dal quale Visual Studio code o da PowerShell prevede. Questa situazione può verificarsi quando i collaboratori usano l'editor con diverse configurazioni di codifica.

### <a name="how-to-tell-when-you-have-encoding-issues"></a>Come sapere quando hai i problemi di codifica

Errori di codifica spesso vengono visualizzati come analizzare gli errori negli script. Se le sequenze di caratteri insoliti si trova nello script, ciò può rappresentare il problema. Nell'esempio seguente, un trattino (`–`) viene visualizzato come i caratteri `â€“`:

```Output
Send-MailMessage : A positional parameter cannot be found that accepts argument 'Testing FuseMail SMTP...'.
At C:\Users\<User>\<OneDrive>\Development\PowerShell\Scripts\Send-EmailUsingSmtpRelay.ps1:6 char:1
+ Send-MailMessage â€“From $from â€“To $recipient1 â€“Subject $subject  ...
+ ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
    + CategoryInfo          : InvalidArgument: (:) [Send-MailMessage], ParameterBindingException
    + FullyQualifiedErrorId : PositionalParameterNotFound,Microsoft.PowerShell.Commands.SendMailMessage
```

Questo problema si verifica perché Visual Studio code consente di codificare il carattere `–` in formato UTF-8 come i byte `0xE2 0x80 0x93`.
Quando questi byte vengono decodificati come Windows-1252, vengono interpretate come caratteri `â€“`.

Alcune sequenze di caratteri insoliti che potrebbero essere visualizzati includono:

- `â€“` invece di `–`
- `â€”` invece di `—`
- `Ã„2` invece di `Ä`
- `Â` invece di ` ` (spazi unificatori)
- `Ã©` invece di `é`

Questo utile [riferimento](https://www.i18nqa.com/debug/utf8-debug.html) sono elencati i modelli comuni che indicano un problema di codifica UTF-8 o Windows-1252.

## <a name="how-the-powershell-extension-in-vscode-interacts-with-encodings"></a>Modalità di interazione con codifiche l'estensione di PowerShell in Visual Studio code

L'estensione di PowerShell interagisce con gli script in numerosi modi:

1. Quando gli script vengono modificati in Visual Studio code, i contenuti vengono inviati tramite Visual Studio code per l'estensione. Il [protocollo di Server di linguaggio][] impone che questo contenuto è stato trasferito in UTF-8. Non è pertanto possibile che l'estensione ottenere la codifica non corretta.
2. Quando gli script vengono eseguiti direttamente nella Console integrata, vengono letti dal file di PowerShell direttamente. Se la codifica PowerShell differisce di VSCode, un elemento può essere inserito errato qui.
3. Quando uno script che viene aperto in VSCode fa riferimento a un altro script che non sia aperto in Visual Studio code, l'estensione per il fallback al caricamento del contenuto dello script che dal file system. L'estensione di PowerShell per impostazione predefinita la codifica UTF-8, ma utilizza [BOM][], o indicatore ordine byte, il rilevamento per selezionare la codifica corretta.

Il problema si verifica quando presupponendo che la codifica dei formati senza BOM (ad esempio [UTF-8][] con alcun BOM e [Windows-1252][]).
L'estensione di PowerShell viene impostato su UTF-8. L'estensione non è possibile modificare le impostazioni di codifica di Visual Studio code.
Per altre informazioni, vedere [problema #824](https://github.com/Microsoft/vscode/issues/824).

## <a name="choosing-the-right-encoding"></a>Scegliere la codifica a destra

Le applicazioni e sistemi diversi possono utilizzare codifiche differenti:

- In .NET Standard, sul web e nel mondo Linux, UTF-8 è ora dominante codifica.
- Molte applicazioni .NET Framework usano [UTF-16][]. Per motivi di cronologia, è talvolta definito "Unicode", un termine che ora si riferisce a un'ampia [standard](https://en.wikipedia.org/wiki/Unicode) che include sia UTF-8 e UTF-16.
- In Windows, molte applicazioni native risalenti a Unicode continuano a usare Windows-1252 per impostazione predefinita.

Le codifiche Unicode prevedono inoltre il concetto di un byte order mark (BOM). DB verificano all'inizio del testo per indicare a quale codifica il testo è tramite un decodificatore. Per le codifiche multibyte, indica anche il carattere BOM [ordine dei byte](https://en.wikipedia.org/wiki/Endianness) della codifica. DB sono progettate per essere byte che si verificano raramente in testo non Unicode, che consente di stimare ragionevolmente anche che il testo è Unicode quando è presente un carattere BOM.

DB sono facoltative e non è la loro adozione più famosi nel mondo Linux perché viene utilizzata una convenzione affidabile UTF-8 ovunque. La maggior parte delle applicazioni Linux presumono che l'input di testo è codificato in UTF-8. Mentre molte applicazioni di Linux riconoscerà e gestire correttamente un carattere BOM, un numero, non sono iniziali agli elementi nel testo manipolati con tali applicazioni.

**Di conseguenza**:

- Se si lavora principalmente con le applicazioni di Windows e Windows PowerShell, è preferibile una codifica come UTF-8 con BOM o UTF-16.
- Se si lavora su piattaforme, è preferibile UTF-8 con BOM.
- Se si lavora principalmente in contesti associati a Linux, è preferibile UTF-8 senza BOM.
- Windows-1252 e latino 1 sono essenzialmente le codifiche legacy che è necessario evitare se possibile.
  Tuttavia, alcune applicazioni di Windows precedenti potrebbero dipendono da tali.
- È anche importante notare che la firma degli script [dipendente dalla codifica](https://github.com/PowerShell/PowerShell/issues/3466), vale a dire una modifica della codifica in uno script firmato richiederanno riapposizione della firma.

## <a name="configuring-vscode"></a>Configurazione di Visual Studio code

Della VSCode codifica predefinita è UTF-8 senza BOM.

Per impostare [Codifica di Visual Studio code][], passare alle impostazioni di Visual Studio code (<kbd>Ctrl<kbd>+</kbd>,</kbd>) e impostare il `"files.encoding"` impostazione:

```json
"files.encoding": "utf8bom"
```

Alcuni valori possibili sono:

- `utf8`: [UTF-8] senza BOM
- `utf8bom`: [UTF-8] con BOM
- `utf16le`: Little endian [UTF-16]
- `utf16be`: Big endian [UTF-16]
- `windows1252`: [Windows-1252]

È necessario ottenere un elenco a discesa per questo oggetto nella visualizzazione GUI o visualizzare i completamenti per tale nel file JSON.

È anche possibile aggiungere quanto segue per rilevare automaticamente la codifica quando è possibile:

```json
"files.autoGuessEncoding": true
```

Se non si vuole queste impostazioni interessano tutti i tipi di file, Visual Studio code consente inoltre alle configurazioni per ogni lingua. Creare un'impostazione specifica del linguaggio inserendo le impostazioni in un `[<language-name>]` campo. Ad esempio:

```json
"[powershell]": {
    "files.encoding": "utf8bom",
    "files.autoGuessEncoding": true
}
```

## <a name="configuring-powershell"></a>Configurazione di PowerShell

Della PowerShell codifica predefinita varia a seconda della versione:

- In PowerShell 6 o versione successiva, la codifica predefinita è UTF-8 senza BOM in tutte le piattaforme.
- In Windows PowerShell, la codifica predefinita è in genere sui Windows-1252, un'estensione della [latin-1][], noto anche come ISO 8859-1.

In PowerShell 5 o versione successiva è possibile trovare la codifica predefinita con questo:

```powershell
[psobject].Assembly.GetTypes() | Where-Object { $_.Name -eq 'ClrFacade'} |
  ForEach-Object {
    $_.GetMethod('GetDefaultEncoding', [System.Reflection.BindingFlags]'nonpublic,static').Invoke($null, @())
  }
```

Quanto segue [script](https://gist.github.com/rjmholt/3d8dd4849f718c914132ce3c5b278e0e) può essere utilizzato per determinare ciò che codifica la sessione di PowerShell viene dedotto per uno script senza un carattere BOM.

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

È possibile configurare PowerShell per usare una codifica specificata in termini più generali tramite le impostazioni del profilo. Vedere gli articoli seguenti:

- [@mklement0]del [risposte sulla codifica di PowerShell su StackOverflow](https://stackoverflow.com/a/40098904).
- [@rkeithhill]del [post di blog sulla gestione dell'input senza BOM UTF-8 in PowerShell](https://rkeithhill.wordpress.com/2010/05/26/handling-native-exe-output-encoding-in-utf8-with-no-bom/).

Non è possibile forzare di PowerShell per usare una codifica input specifico. PowerShell 5.1 e versioni precedenti per impostazione predefinita a Windows-1252 codifica quando non è presente alcun BOM. Per motivi di interoperabilità, è consigliabile salvare gli script in formato Unicode con un carattere BOM.

> [!IMPORTANT]
> Qualsiasi altro strumento, è necessario un tocco PowerShell script può essere influenzato dalle scelte di codifica o codificare di nuovo gli script a un'altra codifica.

### <a name="existing-scripts"></a>Script esistenti

Gli script già presente nel file system potrebbero dover essere codificata nuovamente per la nuova codifica scelta. Nella barra nella parte inferiore di VSCode, verrà visualizzata l'etichetta UTF-8. Fare clic per aprire la barra delle azioni e selezionare **Salva con codifica**. È ora possibile selezionare una nuova codifica per il file. Visualizzare [Codifica di Visual Studio code][] per le istruzioni complete.

Se è necessario codificare di nuovo più file, è possibile usare lo script seguente:

```powershell
Get-ChildItem *.ps1 -Recurse | ForEach-Object {
    $content = Get-Content -Path $_
    Set-Content -Path $_.Fullname -Value $content -Encoding UTF8 -PassThru -Force
}
```

### <a name="the-powershell-integrated-scripting-environment-ise"></a>PowerShell Integrated Scripting Environment (ISE)

Se è anche possibile modificare gli script con PowerShell ISE, è necessario sincronizzare le impostazioni di codifica non esiste.

ISE deve rispettare un indicatore ordine byte, ma è anche possibile usare la reflection per [impostare la codifica](https://bensonxion.wordpress.com/2012/04/25/powershell-ise-default-saveas-encoding/).
Si noti che questo non sarebbe vengano resi persistenti tra le Startup.

### <a name="source-control-software"></a>Software per il controllo origine

Alcuni strumenti di controllo di origine, ad esempio git, ignorare le codifiche; GIT tiene traccia solo i byte.
Altri, come TFS o Mercurial, non potranno essere. Anche alcuni strumenti basati su git si basano su decodifica il testo.

In questo caso, assicurarsi di:

- Configurare la codifica nel controllo del codice sorgente per corrispondano alla configurazione di Visual Studio code di testo.
- Verificare che tutti i file vengono archiviati nel controllo del codice sorgente nella codifica pertinenti.
- Essere ben consapevoli delle modifiche per la codifica ricevuta tramite controllo del codice sorgente. Un segno di questa chiave è delle differenze che indica le modifiche, ma non sembra in cui sono stati modificati (perché è stato byte ma non hanno caratteri).

### <a name="collaborators-environments"></a>Ambienti dei collaboratori

Nella parte superiore di configurazione di controllo del codice sorgente, verificare che i collaboratori in qualsiasi file che condivisi non siano le impostazioni di cui eseguire l'override di codifica per codificare di nuovo i file di PowerShell.

### <a name="other-programs"></a>Altri programmi

Qualsiasi altro programma che legge o scrive uno script di PowerShell potrebbe codificarli nuovamente.

Di seguito sono riportati alcuni esempi:

- Usando gli Appunti per copiare e incollare uno script. Questo è comune in scenari come:
  - Copia di uno script in una macchina virtuale
  - Copia di uno script all'esterno di un messaggio di posta elettronica o una pagina Web
  - Copia di uno script all'interno o all'esterno di un documento Microsoft Word o PowerPoint.
- Altri editor di testo, ad esempio:
  - Blocco note
  - vim
  - Qualsiasi altro editor di script di PowerShell
- Modifica delle utilità, ad esempio testo:
  - `Get-Content`/`Set-Content`/`Out-File`
  - Operatori di reindirizzamento di PowerShell, ad esempio `>` e `>>`
  - `sed`/`awk`
- I programmi di trasferimento del file, ad esempio:
  - Un web browser, durante il download degli script
  - Una condivisione file

Alcuni di questi strumenti gestiscono in byte anziché di testo, ma altri offrono configurazioni di codifica. In questi casi in cui è necessario configurare una codifica, è necessario renderlo lo stesso come editor di codifica per evitare eventuali problemi.

## <a name="other-resources-on-encoding-in-powershell"></a>Altre risorse sulla codifica in PowerShell

Esistono alcuni altri post interessante su codifica e la configurazione di codifica in PowerShell che vale la pena di un'operazione di lettura:

- [@mklement0]del [riepilogo della codifica di PowerShell su StackOverflow](https://stackoverflow.com/questions/40098771/changing-powershells-default-output-encoding-to-utf-8)
- Problemi precedenti aperto in vscode-PowerShell per la codifica dei problemi:
  - [#1308](https://github.com/PowerShell/vscode-powershell/issues/1308)
  - [#1628](https://github.com/PowerShell/vscode-powershell/issues/1628)
  - [#1680](https://github.com/PowerShell/vscode-powershell/issues/1680)
  - [#1744](https://github.com/PowerShell/vscode-powershell/issues/1744)
  - [#1751](https://github.com/PowerShell/vscode-powershell/issues/1751)
- [Il modello di distribuzione classica *opinione di Joel su Software* scriviamo su Unicode](https://www.joelonsoftware.com/2003/10/08/the-absolute-minimum-every-software-developer-absolutely-positively-must-know-about-unicode-and-character-sets-no-excuses/)
- [Codifica in .NET Standard](https://github.com/dotnet/standard/issues/260#issuecomment-289549508)


[@mklement0]: https://github.com/mklement0
[@rkeithhill]: https://github.com/rkeithhill
[Windows-1252]: https://wikipedia.org/wiki/Windows-1252
[latin-1]: https://wikipedia.org/wiki/ISO/IEC_8859-1
[UTF-8]: https://wikipedia.org/wiki/UTF-8
[BOM]: https://wikipedia.org/wiki/Byte_order_mark
[UTF-16]: https://wikipedia.org/wiki/UTF-16
[Protocollo di Server di linguaggio]: https://microsoft.github.io/language-server-protocol/
[Codifica di Visual Studio code]: https://code.visualstudio.com/docs/editor/codebasics#_file-encoding-support
