---
title: Informazioni sulla codifica di file in VSCode e PowerShell
description: Configurare la codifica di file in VS Code e PowerShell
ms.date: 02/28/2019
ms.openlocfilehash: 3283e1262c8eb26906429ecf195cfa0b122b330f
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 12/05/2019
ms.locfileid: "74117417"
---
# <a name="understanding-file-encoding-in-vscode-and-powershell"></a><span data-ttu-id="face9-103">Informazioni sulla codifica di file in VSCode e PowerShell</span><span class="sxs-lookup"><span data-stu-id="face9-103">Understanding file encoding in VSCode and PowerShell</span></span>

<span data-ttu-id="face9-104">Quando si usa VS Code per creare e modificare gli script di PowerShell, è importante che i file vengano salvati usando il formato corretto della codifica dei caratteri.</span><span class="sxs-lookup"><span data-stu-id="face9-104">When using VS Code to create and edit PowerShell scripts, it is important that your files are saved using the correct character encoding format.</span></span>

## <a name="what-is-file-encoding-and-why-is-it-important"></a><span data-ttu-id="face9-105">Che cos'è la codifica dei file e perché è importante?</span><span class="sxs-lookup"><span data-stu-id="face9-105">What is file encoding and why is it important?</span></span>

<span data-ttu-id="face9-106">VS Code gestisce l'interfaccia tra una persona che immette stringhe di caratteri in un buffer e i blocchi di lettura/scrittura di byte nel File system.</span><span class="sxs-lookup"><span data-stu-id="face9-106">VSCode manages the interface between a human entering strings of characters into a buffer and reading/writing blocks of bytes to the filesystem.</span></span> <span data-ttu-id="face9-107">Durante il salvataggio di un file da parte di VS Code, viene usata una codifica del testo per definire i byte in cui viene convertito ogni carattere.</span><span class="sxs-lookup"><span data-stu-id="face9-107">When VSCode saves a file, it uses a text encoding to decide what bytes each character becomes.</span></span>

<span data-ttu-id="face9-108">Analogamente, quando PowerShell esegue uno script deve convertire i byte di un file in caratteri per ricostruire il file in un programma di PowerShell.</span><span class="sxs-lookup"><span data-stu-id="face9-108">Similarly, when PowerShell runs a script it must convert the bytes in a file to characters to reconstruct the file into a PowerShell program.</span></span> <span data-ttu-id="face9-109">Poiché VS Code scrive il file e PowerShell legge il file, devono usare lo stesso sistema di codifica.</span><span class="sxs-lookup"><span data-stu-id="face9-109">Since VSCode writes the file and PowerShell reads the file, they need to use the same encoding system.</span></span> <span data-ttu-id="face9-110">Il processo di analisi di uno script di PowerShell script è: *byte* -> *caratteri* -> *token* -> *albero sintattico astratto* -> *esecuzione*.</span><span class="sxs-lookup"><span data-stu-id="face9-110">This process of parsing a PowerShell script goes: *bytes* -> *characters* -> *tokens* -> *abstract syntax tree* -> *execution*.</span></span>

<span data-ttu-id="face9-111">Sia VS Code che PowerShell vengono installati con una configurazione di codifica predefinita appropriata.</span><span class="sxs-lookup"><span data-stu-id="face9-111">Both VSCode and PowerShell are installed with a sensible default encoding configuration.</span></span> <span data-ttu-id="face9-112">Tuttavia la codifica predefinita usata da PowerShell è cambiata con il rilascio di PowerShell Core (v6.x).</span><span class="sxs-lookup"><span data-stu-id="face9-112">However, the default encoding used by PowerShell has changed with the release of PowerShell Core (v6.x).</span></span> <span data-ttu-id="face9-113">Per assicurarsi di non avere problemi usando PowerShell o l'estensione di PowerShell in VS Code, è necessario configurare le impostazioni di VS Code e di PowerShell in modo corretto.</span><span class="sxs-lookup"><span data-stu-id="face9-113">To ensure you have no problems using PowerShell or the PowerShell extension in VSCode, you need to configure your VSCode and PowerShell settings properly.</span></span>

## <a name="common-causes-of-encoding-issues"></a><span data-ttu-id="face9-114">Cause più comuni dei problemi di codifica</span><span class="sxs-lookup"><span data-stu-id="face9-114">Common causes of encoding issues</span></span>

<span data-ttu-id="face9-115">I problemi di codifica si verificano se la codifica di VS Code o il file di script non corrisponde alla codifica prevista di PowerShell.</span><span class="sxs-lookup"><span data-stu-id="face9-115">Encoding problems occur when the encoding of VSCode or your script file does not match the expected encoding of PowerShell.</span></span> <span data-ttu-id="face9-116">Non è possibile per PowerShell determinare automaticamente la codifica del file.</span><span class="sxs-lookup"><span data-stu-id="face9-116">There is no way for PowerShell to automatically determine the file encoding.</span></span>

<span data-ttu-id="face9-117">I problemi di codifica si verificano con maggiore probabilità quando si usano caratteri non del [set di caratteri ASCII a 7 bit](https://ascii.cl/).</span><span class="sxs-lookup"><span data-stu-id="face9-117">You're more likely to have encoding problems when you're using characters not in the [7-bit ASCII character set](https://ascii.cl/).</span></span> <span data-ttu-id="face9-118">Ad esempio:</span><span class="sxs-lookup"><span data-stu-id="face9-118">For example:</span></span>

- <span data-ttu-id="face9-119">Caratteri non letterali estesi, ad esempio la lineetta (`—`), lo spazio unificatore (` `) o le virgolette inglesi aperte (`“`)</span><span class="sxs-lookup"><span data-stu-id="face9-119">Extended non-letter characters like em-dash (`—`), non-breaking space (` `) or left double quotation mark (`“`)</span></span>
- <span data-ttu-id="face9-120">Caratteri latini accentati (`É`, `ü`)</span><span class="sxs-lookup"><span data-stu-id="face9-120">Accented latin characters (`É`, `ü`)</span></span>
- <span data-ttu-id="face9-121">Caratteri non latini, ad esempio cirillico (`Д`, `Ц`)</span><span class="sxs-lookup"><span data-stu-id="face9-121">Non-latin characters like Cyrillic (`Д`, `Ц`)</span></span>
- <span data-ttu-id="face9-122">Caratteri CJK (`本`, `화`, `が`)</span><span class="sxs-lookup"><span data-stu-id="face9-122">CJK characters (`本`, `화`, `が`)</span></span>

<span data-ttu-id="face9-123">I motivi comuni per i problemi di codifica sono:</span><span class="sxs-lookup"><span data-stu-id="face9-123">Common reasons for encoding issues are:</span></span>

- <span data-ttu-id="face9-124">Le codifiche di VSCode e PowerShell non sono state modificate rispetto ai valori predefiniti.</span><span class="sxs-lookup"><span data-stu-id="face9-124">The encodings of VSCode and PowerShell have not been changed from their defaults.</span></span> <span data-ttu-id="face9-125">Per PowerShell 5.1 e versioni precedenti la codifica predefinita è diversa da quella di VSCode.</span><span class="sxs-lookup"><span data-stu-id="face9-125">For PowerShell 5.1 and below, the default encoding is different from VSCode's.</span></span>
- <span data-ttu-id="face9-126">Un altro editor ha aperto e sovrascritto il file in una nuova codifica.</span><span class="sxs-lookup"><span data-stu-id="face9-126">Another editor has opened and overwritten the file in a new encoding.</span></span> <span data-ttu-id="face9-127">Ciò si verifica spesso con ISE.</span><span class="sxs-lookup"><span data-stu-id="face9-127">This often happens with the ISE.</span></span>
- <span data-ttu-id="face9-128">Il file è sottoposto al controllo del codice sorgente in una codifica diversa da quella prevista da VS Code o PowerShell.</span><span class="sxs-lookup"><span data-stu-id="face9-128">The file is checked into source control in an encoding that is different from what VSCode or PowerShell expects.</span></span> <span data-ttu-id="face9-129">Questa situazione può verificarsi quando i collaboratori usano editor con diverse configurazioni di codifica.</span><span class="sxs-lookup"><span data-stu-id="face9-129">This can happen when collaborators use editors with different encoding configurations.</span></span>

### <a name="how-to-tell-when-you-have-encoding-issues"></a><span data-ttu-id="face9-130">Come sapere quando sono presenti problemi di codifica</span><span class="sxs-lookup"><span data-stu-id="face9-130">How to tell when you have encoding issues</span></span>

<span data-ttu-id="face9-131">Spesso gli errori di codifica si presentano come errori di analisi negli script.</span><span class="sxs-lookup"><span data-stu-id="face9-131">Often encoding errors present themselves as parse errors in scripts.</span></span> <span data-ttu-id="face9-132">Se si rilevano strane sequenze di caratteri nello script, questo può essere il problema.</span><span class="sxs-lookup"><span data-stu-id="face9-132">If you find strange character sequences in your script, this can be the problem.</span></span> <span data-ttu-id="face9-133">Nell'esempio seguente un trattino (`–`) viene visualizzato come i caratteri `â€“`:</span><span class="sxs-lookup"><span data-stu-id="face9-133">In the example below, an en-dash (`–`) appears as the characters `â€“`:</span></span>

```Output
Send-MailMessage : A positional parameter cannot be found that accepts argument 'Testing FuseMail SMTP...'.
At C:\Users\<User>\<OneDrive>\Development\PowerShell\Scripts\Send-EmailUsingSmtpRelay.ps1:6 char:1
+ Send-MailMessage â€“From $from â€“To $recipient1 â€“Subject $subject  ...
+ ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
    + CategoryInfo          : InvalidArgument: (:) [Send-MailMessage], ParameterBindingException
    + FullyQualifiedErrorId : PositionalParameterNotFound,Microsoft.PowerShell.Commands.SendMailMessage
```

<span data-ttu-id="face9-134">Questo problema si verifica perché VS Code codifica il carattere `–` in formato UTF-8 come i byte `0xE2 0x80 0x93`.</span><span class="sxs-lookup"><span data-stu-id="face9-134">This problem occurs because VSCode encodes the character `–` in UTF-8 as the bytes `0xE2 0x80 0x93`.</span></span>
<span data-ttu-id="face9-135">Quando questi byte vengono decodificati come Windows-1252, vengono interpretati come caratteri `â€“`.</span><span class="sxs-lookup"><span data-stu-id="face9-135">When these bytes are decoded as Windows-1252, they are interpreted as the characters `â€“`.</span></span>

<span data-ttu-id="face9-136">Di seguito sono riportate alcune sequenze di caratteri insolite che potrebbero essere visualizzate:</span><span class="sxs-lookup"><span data-stu-id="face9-136">Some strange character sequences that you might see include:</span></span>

<!-- markdownlint-disable MD038 -->
- <span data-ttu-id="face9-137">`â€“` invece di `–`</span><span class="sxs-lookup"><span data-stu-id="face9-137">`â€“` instead of `–`</span></span>
- <span data-ttu-id="face9-138">`â€”` invece di `—`</span><span class="sxs-lookup"><span data-stu-id="face9-138">`â€”` instead of `—`</span></span>
- <span data-ttu-id="face9-139">`Ã„2` invece di `Ä`</span><span class="sxs-lookup"><span data-stu-id="face9-139">`Ã„2` instead of `Ä`</span></span>
- <span data-ttu-id="face9-140">`Â` invece di ` ` (spazio unificatore)</span><span class="sxs-lookup"><span data-stu-id="face9-140">`Â` instead of ` `  (a non-breaking space)</span></span>
- <span data-ttu-id="face9-141">`Ã©` invece di `é`</span><span class="sxs-lookup"><span data-stu-id="face9-141">`Ã©` instead of `é`</span></span>
<!-- markdownlint-enable MD038 -->

<span data-ttu-id="face9-142">In questo utile [riferimento](https://www.i18nqa.com/debug/utf8-debug.html) sono elencati i modelli che più spesso indicano un problema di codifica UTF-8 o Windows-1252.</span><span class="sxs-lookup"><span data-stu-id="face9-142">This handy [reference](https://www.i18nqa.com/debug/utf8-debug.html) lists the common patterns that indicate a UTF-8/Windows-1252 encoding problem.</span></span>

## <a name="how-the-powershell-extension-in-vscode-interacts-with-encodings"></a><span data-ttu-id="face9-143">Modalità di interazione con le codifiche dell'estensione di PowerShell in VS Code</span><span class="sxs-lookup"><span data-stu-id="face9-143">How the PowerShell extension in VSCode interacts with encodings</span></span>

<span data-ttu-id="face9-144">L'estensione di PowerShell interagisce con gli script in diversi modi:</span><span class="sxs-lookup"><span data-stu-id="face9-144">The PowerShell extension interacts with scripts in a number of ways:</span></span>

1. <span data-ttu-id="face9-145">Quando gli script vengono modificati in VS Code, i contenuti vengono inviati da VS Code all'estensione.</span><span class="sxs-lookup"><span data-stu-id="face9-145">When scripts are edited in VSCode, the contents are sent by VSCode to the extension.</span></span> <span data-ttu-id="face9-146">Il [protocollo di server di linguaggio][] impone che il contenuto venga trasferito in UTF-8.</span><span class="sxs-lookup"><span data-stu-id="face9-146">The [Language Server Protocol][] mandates that this content is transferred in UTF-8.</span></span> <span data-ttu-id="face9-147">Di conseguenza, non è possibile che l'estensione riceva la codifica non corretta.</span><span class="sxs-lookup"><span data-stu-id="face9-147">Therefore, it is not possible for the extension to get the wrong encoding.</span></span>
2. <span data-ttu-id="face9-148">Quando gli script vengono eseguiti direttamente nella console integrata, vengono letti da PowerShell direttamente dal file.</span><span class="sxs-lookup"><span data-stu-id="face9-148">When scripts are executed directly in the Integrated Console, they're read from the file by PowerShell directly.</span></span> <span data-ttu-id="face9-149">Se la codifica di PowerShell è diversa da quella di VSCode, si può verificare un problema.</span><span class="sxs-lookup"><span data-stu-id="face9-149">If PowerShell's encoding differs from VSCode's, something can go wrong here.</span></span>
3. <span data-ttu-id="face9-150">Quando uno script aperto in VSCode fa riferimento a un altro script che non è aperto in VS Code, l'estensione esegue il fallback al caricamento del contenuto dello script dal File system.</span><span class="sxs-lookup"><span data-stu-id="face9-150">When a script that is open in VSCode references another script that is not open in VSCode, the extension falls back to loading that script's content from the file system.</span></span> <span data-ttu-id="face9-151">L'estensione di PowerShell per impostazione predefinita usa la codifica UTF-8, ma usa il rilevamento [byte order mark][], o BOM, per selezionare la codifica corretta.</span><span class="sxs-lookup"><span data-stu-id="face9-151">The PowerShell extension defaults to UTF-8 encoding, but uses [byte-order mark][], or BOM, detection to select the correct encoding.</span></span>

<span data-ttu-id="face9-152">Il problema si verifica quando si presuppone l'uso della codifica dei formati senza BOM, ad esempio [UTF-8][] senza BOM e [Windows-1252][].</span><span class="sxs-lookup"><span data-stu-id="face9-152">The problem occurs when assuming the encoding of BOM-less formats (like [UTF-8][] with no BOM and [Windows-1252][]).</span></span>
<span data-ttu-id="face9-153">L'estensione di PowerShell usa UTF-8 come valore predefinito.</span><span class="sxs-lookup"><span data-stu-id="face9-153">The PowerShell extension defaults to UTF-8.</span></span> <span data-ttu-id="face9-154">L'estensione non è in grado di modificare le impostazioni di codifica di VS Code.</span><span class="sxs-lookup"><span data-stu-id="face9-154">The extension cannot change VSCode's encoding settings.</span></span>
<span data-ttu-id="face9-155">Per altre informazioni, vedere il [problema n. 824](https://github.com/Microsoft/vscode/issues/824).</span><span class="sxs-lookup"><span data-stu-id="face9-155">For more information, see [issue #824](https://github.com/Microsoft/vscode/issues/824).</span></span>

## <a name="choosing-the-right-encoding"></a><span data-ttu-id="face9-156">Scelta della codifica corretta</span><span class="sxs-lookup"><span data-stu-id="face9-156">Choosing the right encoding</span></span>

<span data-ttu-id="face9-157">Applicazioni e sistemi diversi possono usare codifiche diverse:</span><span class="sxs-lookup"><span data-stu-id="face9-157">Different systems and applications can use different encodings:</span></span>

- <span data-ttu-id="face9-158">In .NET Standard, sul Web e nel mondo Linux, UTF-8 è ora la codifica dominante.</span><span class="sxs-lookup"><span data-stu-id="face9-158">In .NET Standard, on the web, and in the Linux world, UTF-8 is now the dominant encoding.</span></span>
- <span data-ttu-id="face9-159">Molte applicazioni .NET Framework usano la codifica [UTF-16][].</span><span class="sxs-lookup"><span data-stu-id="face9-159">Many .NET Framework applications use [UTF-16][].</span></span> <span data-ttu-id="face9-160">Per motivi storici, a volte viene definita "Unicode", un termine che ora si riferisce a uno [standard](https://en.wikipedia.org/wiki/Unicode) diffuso che include sia UTF-8 che UTF-16.</span><span class="sxs-lookup"><span data-stu-id="face9-160">For historical reasons, this is sometimes called "Unicode", a term that now refers to a broad [standard](https://en.wikipedia.org/wiki/Unicode) that includes both UTF-8 and UTF-16.</span></span>
- <span data-ttu-id="face9-161">In Windows molte applicazioni native precedenti a Unicode continuano a usare Windows-1252 per impostazione predefinita.</span><span class="sxs-lookup"><span data-stu-id="face9-161">On Windows, many native applications that predate Unicode continue to use Windows-1252 by default.</span></span>

<span data-ttu-id="face9-162">Le codifiche Unicode prevedono inoltre il concetto di un byte order mark (BOM).</span><span class="sxs-lookup"><span data-stu-id="face9-162">Unicode encodings also have the concept of a byte-order mark (BOM).</span></span> <span data-ttu-id="face9-163">I BOM si trovano all'inizio del testo per indicare a un decodificatore quale codifica sta usando il testo.</span><span class="sxs-lookup"><span data-stu-id="face9-163">BOMs occur at the beginning of text to tell a decoder which encoding the text is using.</span></span> <span data-ttu-id="face9-164">Per le codifiche multibyte, il BOM indica anche l'[ordine dei byte](https://en.wikipedia.org/wiki/Endianness) della codifica.</span><span class="sxs-lookup"><span data-stu-id="face9-164">For multi-byte encodings, the BOM also indicates [endianness](https://en.wikipedia.org/wiki/Endianness) of the encoding.</span></span> <span data-ttu-id="face9-165">I BOM sono progettati come byte che si verificano raramente nel testo non Unicode e la presenza di un BOM suggerisce che un testo è Unicode.</span><span class="sxs-lookup"><span data-stu-id="face9-165">BOMs are designed to be bytes that rarely occur in non-Unicode text, allowing a reasonable guess that text is Unicode when a BOM is present.</span></span>

<span data-ttu-id="face9-166">I BOM sono facoltativi e la loro adozione non è altrettanto diffusa nel mondo Linux perché viene usata ovunque una convenzione affidabile di UTF-8.</span><span class="sxs-lookup"><span data-stu-id="face9-166">BOMs are optional and their adoption isn't as popular in the Linux world because a dependable convention of UTF-8 is used everywhere.</span></span> <span data-ttu-id="face9-167">La maggior parte delle applicazioni Linux presume che l'input di testo sia codificato in UTF-8.</span><span class="sxs-lookup"><span data-stu-id="face9-167">Most Linux applications presume that text input is encoded in UTF-8.</span></span> <span data-ttu-id="face9-168">Benché molte applicazioni di Linux siano in grado di riconoscere e gestire correttamente un BOM, alcune non lo sono e la manipolazione del testo in queste applicazioni produce degli artefatti.</span><span class="sxs-lookup"><span data-stu-id="face9-168">While many Linux applications will recognize and correctly handle a BOM, a number do not, leading to artifacts in text manipulated with those applications.</span></span>

<span data-ttu-id="face9-169">**Di conseguenza**:</span><span class="sxs-lookup"><span data-stu-id="face9-169">**Therefore**:</span></span>

- <span data-ttu-id="face9-170">Se si lavora principalmente con le applicazioni Windows e Windows PowerShell, è preferibile la codifica UTF-8 con BOM o UTF-16.</span><span class="sxs-lookup"><span data-stu-id="face9-170">If you work primarily with Windows applications and Windows PowerShell, you should prefer an encoding like UTF-8 with BOM or UTF-16.</span></span>
- <span data-ttu-id="face9-171">Se si lavora su varie piattaforme, è preferibile usare UTF-8 con BOM.</span><span class="sxs-lookup"><span data-stu-id="face9-171">If you work across platforms, you should prefer UTF-8 with BOM.</span></span>
- <span data-ttu-id="face9-172">Se si lavora principalmente in contesti associati a Linux, è preferibile usare UTF-8 senza BOM.</span><span class="sxs-lookup"><span data-stu-id="face9-172">If you work mainly in Linux-associated contexts, you should prefer UTF-8 without BOM.</span></span>
- <span data-ttu-id="face9-173">Windows-1252 e latin-1 sono essenzialmente le codifiche legacy che è opportuno evitare, se possibile.</span><span class="sxs-lookup"><span data-stu-id="face9-173">Windows-1252 and latin-1 are essentially legacy encodings that you should avoid if possible.</span></span>
  <span data-ttu-id="face9-174">Tuttavia, alcune applicazioni Windows più datate possono dipendere da esse.</span><span class="sxs-lookup"><span data-stu-id="face9-174">However, some older Windows applications may depend on them.</span></span>
- <span data-ttu-id="face9-175">È anche importante notare che la firma degli script [dipende dalla codifica](https://github.com/PowerShell/PowerShell/issues/3466), ovvero una modifica della codifica in uno script firmato richiede una nuova operazione di firma.</span><span class="sxs-lookup"><span data-stu-id="face9-175">It's also worth noting that script signing is [encoding-dependent](https://github.com/PowerShell/PowerShell/issues/3466), meaning a change of encoding on a signed script will require resigning.</span></span>

## <a name="configuring-vscode"></a><span data-ttu-id="face9-176">Configurazione di VS Code</span><span class="sxs-lookup"><span data-stu-id="face9-176">Configuring VSCode</span></span>

<span data-ttu-id="face9-177">La codifica predefinita di VS Code è UTF-8 senza BOM.</span><span class="sxs-lookup"><span data-stu-id="face9-177">VSCode's default encoding is UTF-8 without BOM.</span></span>

<span data-ttu-id="face9-178">Per impostare la [codifica di VS Code][], accedere alle impostazioni di VS Code (<kbd>CTRL</kbd>+<kbd>,</kbd>) e specificare l'impostazione `"files.encoding"`:</span><span class="sxs-lookup"><span data-stu-id="face9-178">To set [VSCode's encoding][], go to the VSCode settings (<kbd>Ctrl</kbd>+<kbd>,</kbd>) and set the `"files.encoding"` setting:</span></span>

```json
"files.encoding": "utf8bom"
```

<span data-ttu-id="face9-179">Alcuni valori possibili sono:</span><span class="sxs-lookup"><span data-stu-id="face9-179">Some possible values are:</span></span>

- <span data-ttu-id="face9-180">`utf8`: [UTF-8] senza BOM</span><span class="sxs-lookup"><span data-stu-id="face9-180">`utf8`: [UTF-8] without BOM</span></span>
- <span data-ttu-id="face9-181">`utf8bom`: [UTF-8] con BOM</span><span class="sxs-lookup"><span data-stu-id="face9-181">`utf8bom`: [UTF-8] with BOM</span></span>
- <span data-ttu-id="face9-182">`utf16le`: [UTF-16] little endian</span><span class="sxs-lookup"><span data-stu-id="face9-182">`utf16le`: Little endian [UTF-16]</span></span>
- <span data-ttu-id="face9-183">`utf16be`: [UTF-16] big endian</span><span class="sxs-lookup"><span data-stu-id="face9-183">`utf16be`: Big endian [UTF-16]</span></span>
- <span data-ttu-id="face9-184">`windows1252`: [Windows-1252]</span><span class="sxs-lookup"><span data-stu-id="face9-184">`windows1252`: [Windows-1252]</span></span>

<span data-ttu-id="face9-185">Per questo oggetto è possibile ottenere un elenco a discesa nella visualizzazione GUI o i relativi completamenti nella visualizzazione JSON.</span><span class="sxs-lookup"><span data-stu-id="face9-185">You should get a dropdown for this in the GUI view, or completions for it in the JSON view.</span></span>

<span data-ttu-id="face9-186">È anche possibile aggiungere quanto segue per rilevare automaticamente la codifica quando è possibile:</span><span class="sxs-lookup"><span data-stu-id="face9-186">You can also add the following to autodetect encoding when possible:</span></span>

```json
"files.autoGuessEncoding": true
```

<span data-ttu-id="face9-187">Se si vuole evitare che queste impostazioni influiscano su tutti i tipi di file, VS Code consente anche di definire configurazioni diverse in base al linguaggio.</span><span class="sxs-lookup"><span data-stu-id="face9-187">If you don't want these settings to affect all files types, VSCode also allows per-language configurations.</span></span> <span data-ttu-id="face9-188">Per creare un'impostazione specifica del linguaggio, inserire le impostazioni in un campo `[<language-name>]`.</span><span class="sxs-lookup"><span data-stu-id="face9-188">Create a language-specific setting by putting settings in a `[<language-name>]` field.</span></span> <span data-ttu-id="face9-189">Ad esempio:</span><span class="sxs-lookup"><span data-stu-id="face9-189">For example:</span></span>

```json
"[powershell]": {
    "files.encoding": "utf8bom",
    "files.autoGuessEncoding": true
}
```

## <a name="configuring-powershell"></a><span data-ttu-id="face9-190">Configurazione di PowerShell</span><span class="sxs-lookup"><span data-stu-id="face9-190">Configuring PowerShell</span></span>

<span data-ttu-id="face9-191">La codifica predefinita di PowerShell varia a seconda della versione:</span><span class="sxs-lookup"><span data-stu-id="face9-191">PowerShell's default encoding varies depending on version:</span></span>

- <span data-ttu-id="face9-192">In PowerShell 6 o versione successiva la codifica predefinita è UTF-8 senza BOM su tutte le piattaforme.</span><span class="sxs-lookup"><span data-stu-id="face9-192">In PowerShell 6+, the default encoding is UTF-8 without BOM on all platforms.</span></span>
- <span data-ttu-id="face9-193">In Windows PowerShell la codifica predefinita normalmente è Windows-1252, un'estensione di [latin-1][], nota anche come ISO 8859-1.</span><span class="sxs-lookup"><span data-stu-id="face9-193">In Windows PowerShell, the default encoding is usually Windows-1252, an extension of [latin-1][], also known as ISO 8859-1.</span></span>

<span data-ttu-id="face9-194">In PowerShell 5 o versione successiva è possibile trovare la codifica predefinita in questo modo:</span><span class="sxs-lookup"><span data-stu-id="face9-194">In PowerShell 5+ you can find your default encoding with this:</span></span>

```powershell
[psobject].Assembly.GetTypes() | Where-Object { $_.Name -eq 'ClrFacade'} |
  ForEach-Object {
    $_.GetMethod('GetDefaultEncoding', [System.Reflection.BindingFlags]'nonpublic,static').Invoke($null, @())
  }
```

<span data-ttu-id="face9-195">Lo [script](https://gist.github.com/rjmholt/3d8dd4849f718c914132ce3c5b278e0e) seguente può essere usato per determinare ciò che deduce la codifica della sessione di PowerShell per uno script senza BOM.</span><span class="sxs-lookup"><span data-stu-id="face9-195">The following [script](https://gist.github.com/rjmholt/3d8dd4849f718c914132ce3c5b278e0e) can be used to determine what encoding your PowerShell session infers for a script without a BOM.</span></span>

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

<span data-ttu-id="face9-196">È possibile configurare PowerShell in modo che usi una codifica specifica più in generale usando le impostazioni del profilo.</span><span class="sxs-lookup"><span data-stu-id="face9-196">It's possible to configure PowerShell to use a given encoding more generally using profile settings.</span></span> <span data-ttu-id="face9-197">Vedere gli articoli seguenti:</span><span class="sxs-lookup"><span data-stu-id="face9-197">See the following articles:</span></span>

- <span data-ttu-id="face9-198">[@mklement0]: [risposta sulla codifica di PowerShell per StackOverflow](https://stackoverflow.com/a/40098904).</span><span class="sxs-lookup"><span data-stu-id="face9-198">[@mklement0]'s [answer about PowerShell encoding on StackOverflow](https://stackoverflow.com/a/40098904).</span></span>
- <span data-ttu-id="face9-199">[@rkeithhill]: [post di blog sulla gestione dell'input UTF-8 senza BOM in PowerShell](https://rkeithhill.wordpress.com/2010/05/26/handling-native-exe-output-encoding-in-utf8-with-no-bom/).</span><span class="sxs-lookup"><span data-stu-id="face9-199">[@rkeithhill]'s [blog post about dealing with BOM-less UTF-8 input in PowerShell](https://rkeithhill.wordpress.com/2010/05/26/handling-native-exe-output-encoding-in-utf8-with-no-bom/).</span></span>

<span data-ttu-id="face9-200">Non è possibile forzare PowerShell perché usi una codifica specifica per l'input.</span><span class="sxs-lookup"><span data-stu-id="face9-200">It's not possible to force PowerShell to use a specific input encoding.</span></span> <span data-ttu-id="face9-201">PowerShell 5.1 e versioni precedenti per impostazione predefinita usa la codifica Windows-1252 quando non è presente alcun BOM.</span><span class="sxs-lookup"><span data-stu-id="face9-201">PowerShell 5.1 and below default to Windows-1252 encoding when there's no BOM.</span></span> <span data-ttu-id="face9-202">Per motivi di interoperabilità, è preferibile salvare gli script in formato Unicode con BOM.</span><span class="sxs-lookup"><span data-stu-id="face9-202">For interoperability reasons, it's best to save scripts in a Unicode format with a BOM.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="face9-203">Le scelte in termini di codifica possono influire su eventuali altri strumenti che usano gli script di PowerShell o può essere opportuno codificare di nuovo gli script usando un'altra codifica.</span><span class="sxs-lookup"><span data-stu-id="face9-203">Any other tools you have that touch PowerShell scripts may be affected by your encoding choices or re-encode your scripts to another encoding.</span></span>

### <a name="existing-scripts"></a><span data-ttu-id="face9-204">Script esistenti</span><span class="sxs-lookup"><span data-stu-id="face9-204">Existing scripts</span></span>

<span data-ttu-id="face9-205">Può essere necessario ricodificare gli script già presenti nel file system in base alla nuova codifica scelta.</span><span class="sxs-lookup"><span data-stu-id="face9-205">Scripts already on the file system may need to be re-encoded to your new chosen encoding.</span></span> <span data-ttu-id="face9-206">Nella barra inferiore di VS Code viene visualizzata l'etichetta UTF-8.</span><span class="sxs-lookup"><span data-stu-id="face9-206">In the bottom bar of VSCode, you'll see the label UTF-8.</span></span> <span data-ttu-id="face9-207">Fare clic sull'etichetta per aprire la barra delle azioni e selezionare **Salva con codifica**.</span><span class="sxs-lookup"><span data-stu-id="face9-207">Click it to open the action bar and select **Save with encoding**.</span></span> <span data-ttu-id="face9-208">È ora possibile selezionare una nuova codifica per il file.</span><span class="sxs-lookup"><span data-stu-id="face9-208">You can now pick a new encoding for that file.</span></span> <span data-ttu-id="face9-209">Vedere [Codifica di VS Code][] per le istruzioni complete.</span><span class="sxs-lookup"><span data-stu-id="face9-209">See [VSCode's encoding][] for full instructions.</span></span>

<span data-ttu-id="face9-210">Se è necessario codificare di nuovo più file, è possibile usare lo script seguente:</span><span class="sxs-lookup"><span data-stu-id="face9-210">If you need to re-encode multiple files, you can use the following script:</span></span>

```powershell
Get-ChildItem *.ps1 -Recurse | ForEach-Object {
    $content = Get-Content -Path $_
    Set-Content -Path $_.Fullname -Value $content -Encoding UTF8 -PassThru -Force
}
```

### <a name="the-powershell-integrated-scripting-environment-ise"></a><span data-ttu-id="face9-211">PowerShell Integrated Scripting Environment (ISE)</span><span class="sxs-lookup"><span data-stu-id="face9-211">The PowerShell Integrated Scripting Environment (ISE)</span></span>

<span data-ttu-id="face9-212">Se inoltre si modificano gli script con l'ISE di PowerShell, è necessario sincronizzare le impostazioni di codifica nell'ISE.</span><span class="sxs-lookup"><span data-stu-id="face9-212">If you also edit scripts using the PowerShell ISE, you need to synchronize your encoding settings there.</span></span>

<span data-ttu-id="face9-213">L'ISE deve rispettare un BOM, ma è anche possibile usare la reflection per [impostare la codifica](https://bensonxion.wordpress.com/2012/04/25/powershell-ise-default-saveas-encoding/).</span><span class="sxs-lookup"><span data-stu-id="face9-213">The ISE should honor a BOM, but it's also possible to use reflection to [set the encoding](https://bensonxion.wordpress.com/2012/04/25/powershell-ise-default-saveas-encoding/).</span></span>
<span data-ttu-id="face9-214">Si noti che questa condizione non sarebbe persistente da un avvio all'altro.</span><span class="sxs-lookup"><span data-stu-id="face9-214">Note that this wouldn't be persisted between startups.</span></span>

### <a name="source-control-software"></a><span data-ttu-id="face9-215">Software di controllo del codice sorgente</span><span class="sxs-lookup"><span data-stu-id="face9-215">Source control software</span></span>

<span data-ttu-id="face9-216">Alcuni strumenti per il controllo del codice sorgente ignorano le codifiche, ad esempio GIT tiene traccia solo dei byte.</span><span class="sxs-lookup"><span data-stu-id="face9-216">Some source control tools, such as git, ignore encodings; git just tracks the bytes.</span></span>
<span data-ttu-id="face9-217">Altri strumenti, ad esempio Azure DevOps o Mercurial, si comportano diversamente.</span><span class="sxs-lookup"><span data-stu-id="face9-217">Others, like Azure DevOps or Mercurial, may not.</span></span> <span data-ttu-id="face9-218">Anche alcuni strumenti basati su GIT usano la decodifica del testo.</span><span class="sxs-lookup"><span data-stu-id="face9-218">Even some git-based tools rely on decoding text.</span></span>

<span data-ttu-id="face9-219">In questo caso verificare quanto segue:</span><span class="sxs-lookup"><span data-stu-id="face9-219">When this is the case, make sure you:</span></span>

- <span data-ttu-id="face9-220">Configurare la codifica del testo nel controllo del codice sorgente in modo che corrisponda alla configurazione di VS Code.</span><span class="sxs-lookup"><span data-stu-id="face9-220">Configure the text encoding in your source control to match your VSCode configuration.</span></span>
- <span data-ttu-id="face9-221">Verificare che tutti i file vengano sottoposti al controllo del codice sorgente con la codifica pertinente.</span><span class="sxs-lookup"><span data-stu-id="face9-221">Ensure all your files are checked into source control in the relevant encoding.</span></span>
- <span data-ttu-id="face9-222">Fare attenzione alle modifiche della codifica segnalate dal controllo del codice sorgente.</span><span class="sxs-lookup"><span data-stu-id="face9-222">Be wary of changes to the encoding received through source control.</span></span> <span data-ttu-id="face9-223">Un segno evidente è un diff che indica la presenza di modifiche quando apparentemente non ce ne sono (perché i byte sono cambiati e i caratteri no).</span><span class="sxs-lookup"><span data-stu-id="face9-223">A key sign of this is a diff indicating changes but where nothing seems to have changed (because bytes have but characters have not).</span></span>

### <a name="collaborators-environments"></a><span data-ttu-id="face9-224">Ambienti dei collaboratori</span><span class="sxs-lookup"><span data-stu-id="face9-224">Collaborators' environments</span></span>

<span data-ttu-id="face9-225">Oltre a configurare il controllo del codice sorgente, verificare che i collaboratori che accedono ai file condivisi non usino impostazioni che sostituiscono la codifica in uso ricodificando i file di PowerShell.</span><span class="sxs-lookup"><span data-stu-id="face9-225">On top of configuring source control, ensure that your collaborators on any files you share don't have settings that override your encoding by re-encoding PowerShell files.</span></span>

### <a name="other-programs"></a><span data-ttu-id="face9-226">Altri programmi</span><span class="sxs-lookup"><span data-stu-id="face9-226">Other programs</span></span>

<span data-ttu-id="face9-227">Qualsiasi altro programma che legge o scrive uno script di PowerShell può ricodificarlo.</span><span class="sxs-lookup"><span data-stu-id="face9-227">Any other program that reads or writes a PowerShell script may re-encode it.</span></span>

<span data-ttu-id="face9-228">Di seguito sono riportati alcuni esempi:</span><span class="sxs-lookup"><span data-stu-id="face9-228">Some examples are:</span></span>

- <span data-ttu-id="face9-229">Uso degli Appunti per copiare e incollare uno script.</span><span class="sxs-lookup"><span data-stu-id="face9-229">Using the clipboard to copy and paste a script.</span></span> <span data-ttu-id="face9-230">Questa situazione è comune in scenari come:</span><span class="sxs-lookup"><span data-stu-id="face9-230">This is common in scenarios like:</span></span>
  - <span data-ttu-id="face9-231">Copia di uno script in una macchina virtuale</span><span class="sxs-lookup"><span data-stu-id="face9-231">Copying a script into a VM</span></span>
  - <span data-ttu-id="face9-232">Copia di uno script da un messaggio di posta elettronica o una pagina Web</span><span class="sxs-lookup"><span data-stu-id="face9-232">Copying a script out of an email or webpage</span></span>
  - <span data-ttu-id="face9-233">Copia di uno script in o da un documento Microsoft Word o PowerPoint</span><span class="sxs-lookup"><span data-stu-id="face9-233">Copying a script into or out of a Microsoft Word or PowerPoint document</span></span>
- <span data-ttu-id="face9-234">Altri editor di testo, ad esempio:</span><span class="sxs-lookup"><span data-stu-id="face9-234">Other text editors, such as:</span></span>
  - <span data-ttu-id="face9-235">Blocco note</span><span class="sxs-lookup"><span data-stu-id="face9-235">Notepad</span></span>
  - <span data-ttu-id="face9-236">vim</span><span class="sxs-lookup"><span data-stu-id="face9-236">vim</span></span>
  - <span data-ttu-id="face9-237">Qualsiasi altro editor di script di PowerShell</span><span class="sxs-lookup"><span data-stu-id="face9-237">Any other PowerShell script editor</span></span>
- <span data-ttu-id="face9-238">Utilità di modifica del testo, ad esempio:</span><span class="sxs-lookup"><span data-stu-id="face9-238">Text editing utilities, like:</span></span>
  - `Get-Content`/`Set-Content`/`Out-File`
  - <span data-ttu-id="face9-239">Operatori di reindirizzamento di PowerShell, ad esempio `>` e `>>`</span><span class="sxs-lookup"><span data-stu-id="face9-239">PowerShell redirection operators like `>` and `>>`</span></span>
  - `sed`/`awk`
- <span data-ttu-id="face9-240">Programmi di trasferimento file, ad esempio:</span><span class="sxs-lookup"><span data-stu-id="face9-240">File transfer programs, like:</span></span>
  - <span data-ttu-id="face9-241">Un Web browser, durante il download degli script</span><span class="sxs-lookup"><span data-stu-id="face9-241">A web browser, when downloading scripts</span></span>
  - <span data-ttu-id="face9-242">Una condivisione file</span><span class="sxs-lookup"><span data-stu-id="face9-242">A file share</span></span>

<span data-ttu-id="face9-243">Alcuni di questi strumenti gestiscono i byte anziché il testo, ma altri offrono configurazioni di codifica.</span><span class="sxs-lookup"><span data-stu-id="face9-243">Some of these tools deal in bytes rather than text, but others offer encoding configurations.</span></span> <span data-ttu-id="face9-244">Nei casi in cui è necessario configurare una codifica, tenere presente che deve essere la stessa codifica usata dall'editor per evitare problemi.</span><span class="sxs-lookup"><span data-stu-id="face9-244">In those cases where you need to configure an encoding, you need to make it the same as your editor encoding to prevent problems.</span></span>

## <a name="other-resources-on-encoding-in-powershell"></a><span data-ttu-id="face9-245">Altre risorse per la codifica in PowerShell</span><span class="sxs-lookup"><span data-stu-id="face9-245">Other resources on encoding in PowerShell</span></span>

<span data-ttu-id="face9-246">Esistono alcuni post interessanti sulla codifica e la configurazione della codifica in PowerShell che vale la pena leggere:</span><span class="sxs-lookup"><span data-stu-id="face9-246">There are a few other nice posts on encoding and configuring encoding in PowerShell that are worth a read:</span></span>

- <span data-ttu-id="face9-247">[@mklement0]: [riepilogo della codifica di PowerShell per StackOverflow](https://stackoverflow.com/questions/40098771/changing-powershells-default-output-encoding-to-utf-8)</span><span class="sxs-lookup"><span data-stu-id="face9-247">[@mklement0]'s [summary of PowerShell encoding on StackOverflow](https://stackoverflow.com/questions/40098771/changing-powershells-default-output-encoding-to-utf-8)</span></span>
- <span data-ttu-id="face9-248">Problemi segnalati in precedenza in vscode-PowerShell riguardo alla codifica dei problemi:</span><span class="sxs-lookup"><span data-stu-id="face9-248">Previous issues opened on vscode-PowerShell for encoding problems:</span></span>
  - [<span data-ttu-id="face9-249">#1308</span><span class="sxs-lookup"><span data-stu-id="face9-249">#1308</span></span>](https://github.com/PowerShell/vscode-powershell/issues/1308)
  - [<span data-ttu-id="face9-250">#1628</span><span class="sxs-lookup"><span data-stu-id="face9-250">#1628</span></span>](https://github.com/PowerShell/vscode-powershell/issues/1628)
  - [<span data-ttu-id="face9-251">#1680</span><span class="sxs-lookup"><span data-stu-id="face9-251">#1680</span></span>](https://github.com/PowerShell/vscode-powershell/issues/1680)
  - [<span data-ttu-id="face9-252">#1744</span><span class="sxs-lookup"><span data-stu-id="face9-252">#1744</span></span>](https://github.com/PowerShell/vscode-powershell/issues/1744)
  - [<span data-ttu-id="face9-253">#1751</span><span class="sxs-lookup"><span data-stu-id="face9-253">#1751</span></span>](https://github.com/PowerShell/vscode-powershell/issues/1751)
- [<span data-ttu-id="face9-254">Il classico documento *Joel on Software* su Unicode</span><span class="sxs-lookup"><span data-stu-id="face9-254">The classic *Joel on Software* write up about Unicode</span></span>](https://www.joelonsoftware.com/2003/10/08/the-absolute-minimum-every-software-developer-absolutely-positively-must-know-about-unicode-and-character-sets-no-excuses/)
- [<span data-ttu-id="face9-255">Codifica in .NET Standard</span><span class="sxs-lookup"><span data-stu-id="face9-255">Encoding in .NET Standard</span></span>](https://github.com/dotnet/standard/issues/260#issuecomment-289549508)


[@mklement0]: https://github.com/mklement0
[@rkeithhill]: https://github.com/rkeithhill
[Windows-1252]: https://wikipedia.org/wiki/Windows-1252
[latin-1]: https://wikipedia.org/wiki/ISO/IEC_8859-1
[UTF-8]: https://wikipedia.org/wiki/UTF-8
[byte order mark]: https://wikipedia.org/wiki/Byte_order_mark
[byte-order mark]: https://wikipedia.org/wiki/Byte_order_mark
[UTF-16]: https://wikipedia.org/wiki/UTF-16
[Protocollo di server di linguaggio]: https://microsoft.github.io/language-server-protocol/
[Language Server Protocol]: https://microsoft.github.io/language-server-protocol/
[Codifica di VS Code]: https://code.visualstudio.com/docs/editor/codebasics#_file-encoding-support
[VSCode's encoding]: https://code.visualstudio.com/docs/editor/codebasics#_file-encoding-support
