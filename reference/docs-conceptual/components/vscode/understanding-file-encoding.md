---
title: Informazioni sulla codifica di file in VSCode e PowerShell
description: Configurare la codifica di file in Visual Studio code e PowerShell
ms.date: 02/28/2019
ms.openlocfilehash: f3b133b4bee7688821a5960429e2f26b69b01e12
ms.sourcegitcommit: ce46e5098786e19d521b4bf948ff62d2b90bc53e
ms.translationtype: MTE95
ms.contentlocale: it-IT
ms.lasthandoff: 03/02/2019
ms.locfileid: "57251473"
---
# <a name="understanding-file-encoding-in-vscode-and-powershell"></a><span data-ttu-id="ea138-103">Informazioni sulla codifica di file in VSCode e PowerShell</span><span class="sxs-lookup"><span data-stu-id="ea138-103">Understanding file encoding in VSCode and PowerShell</span></span>

<span data-ttu-id="ea138-104">Quando si usa Visual Studio Code per creare e modificare gli script di PowerShell, è importante che i file vengono salvati utilizzando il formato di codifica di carattere corretto.</span><span class="sxs-lookup"><span data-stu-id="ea138-104">When using VS Code to create and edit PowerShell scripts, it is important that your files are saved using the correct character encoding format.</span></span>

## <a name="what-is-file-encoding-and-why-is-it-important"></a><span data-ttu-id="ea138-105">Che cos'è la codifica dei file e perché è importante?</span><span class="sxs-lookup"><span data-stu-id="ea138-105">What is file encoding and why is it important?</span></span>

<span data-ttu-id="ea138-106">Visual Studio code gestisce l'interfaccia tra una risorse umane immettendo stringhe di caratteri in un buffer e blocchi di lettura/scrittura di byte nel file System.</span><span class="sxs-lookup"><span data-stu-id="ea138-106">VSCode manages the interface between a human entering strings of characters into a buffer and reading/writing blocks of bytes to the filesystem.</span></span> <span data-ttu-id="ea138-107">Quando Visual Studio code consente di salvare un file, Usa un codifica a tale scopo del testo.</span><span class="sxs-lookup"><span data-stu-id="ea138-107">When VSCode saves a file, it uses a text encoding to do this.</span></span>

<span data-ttu-id="ea138-108">Allo stesso modo, quando si esegue uno script di PowerShell è necessario convertire i byte in un file in caratteri per ricostruire il file in un programma di PowerShell.</span><span class="sxs-lookup"><span data-stu-id="ea138-108">Similarly, when PowerShell runs a script it must convert the bytes in a file to characters to reconstruct the file into a PowerShell program.</span></span> <span data-ttu-id="ea138-109">Poiché Visual Studio code scrive il file e PowerShell legge il file, devono usare lo stesso sistema di codifica.</span><span class="sxs-lookup"><span data-stu-id="ea138-109">Since VSCode writes the file and PowerShell reads the file, they need to use the same encoding system.</span></span> <span data-ttu-id="ea138-110">Questo processo di analisi di uno script di PowerShell passa: *byte* -> *caratteri* -> *token*  ->   *albero sintattico astratto* -> *esecuzione*.</span><span class="sxs-lookup"><span data-stu-id="ea138-110">This process of parsing a PowerShell script goes: *bytes* -> *characters* -> *tokens* -> *abstract syntax tree* -> *execution*.</span></span>

<span data-ttu-id="ea138-111">Visual Studio code sia PowerShell vengono installati con una configurazione di codifica predefinito adeguato.</span><span class="sxs-lookup"><span data-stu-id="ea138-111">Both VSCode and PowerShell are installed with a sensible default encoding configuration.</span></span> <span data-ttu-id="ea138-112">Tuttavia, la codifica predefinita utilizzata da PowerShell è stato modificato con la versione di PowerShell Core (v6.x).</span><span class="sxs-lookup"><span data-stu-id="ea138-112">However, the default encoding used by PowerShell has changed with the release of PowerShell Core (v6.x).</span></span> <span data-ttu-id="ea138-113">Per assicurarsi di non aver problemi tramite PowerShell o l'estensione di PowerShell in Visual Studio code, è necessario configurare le impostazioni di Visual Studio code e PowerShell in modo corretto.</span><span class="sxs-lookup"><span data-stu-id="ea138-113">To ensure you have no problems using PowerShell or the PowerShell extension in VSCode, you need to configure your VSCode and PowerShell settings properly.</span></span>

## <a name="common-causes-of-encoding-issues"></a><span data-ttu-id="ea138-114">Cause più comuni dei problemi di codifica</span><span class="sxs-lookup"><span data-stu-id="ea138-114">Common causes of encoding issues</span></span>

<span data-ttu-id="ea138-115">Problemi di codifica si verificano durante la codifica di Visual Studio code o file di script non corrispondono alla codifica prevista di PowerShell.</span><span class="sxs-lookup"><span data-stu-id="ea138-115">Encoding problems occur when the encoding of VSCode or your script file does not match the expected encoding of PowerShell.</span></span> <span data-ttu-id="ea138-116">Non è possibile per PowerShell determinare automaticamente la codifica del file.</span><span class="sxs-lookup"><span data-stu-id="ea138-116">There is no way for PowerShell to automatically determine the file encoding.</span></span>

<span data-ttu-id="ea138-117">Si è più soggetto a problemi di codifica quando si usano caratteri non nel [set di caratteri ASCII a 7 bit](https://ascii.cl/).</span><span class="sxs-lookup"><span data-stu-id="ea138-117">You're more likely to have encoding problems when you're using characters not in the [7-bit ASCII character set](https://ascii.cl/).</span></span> <span data-ttu-id="ea138-118">Ad esempio:</span><span class="sxs-lookup"><span data-stu-id="ea138-118">For example:</span></span>

- <span data-ttu-id="ea138-119">I caratteri latin accentati (`É`, `ü`)</span><span class="sxs-lookup"><span data-stu-id="ea138-119">Accented latin characters (`É`, `ü`)</span></span>
- <span data-ttu-id="ea138-120">Caratteri non latini come cirillico (`Д`, `Ц`)</span><span class="sxs-lookup"><span data-stu-id="ea138-120">Non-latin characters like Cyrillic (`Д`, `Ц`)</span></span>
- <span data-ttu-id="ea138-121">Han cinese (`脚`, `本`)</span><span class="sxs-lookup"><span data-stu-id="ea138-121">Han Chinese (`脚`, `本`)</span></span>

<span data-ttu-id="ea138-122">Motivi comuni per i problemi di codifica sono:</span><span class="sxs-lookup"><span data-stu-id="ea138-122">Common reasons for encoding issues are:</span></span>

- <span data-ttu-id="ea138-123">Le codifiche di VSCode e PowerShell non sono state modificate i valori predefiniti.</span><span class="sxs-lookup"><span data-stu-id="ea138-123">The encodings of VSCode and PowerShell have not been changed from their defaults.</span></span> <span data-ttu-id="ea138-124">Per PowerShell 5.1 e versioni precedenti, il valore predefinito è diversa da VSCode codifica.</span><span class="sxs-lookup"><span data-stu-id="ea138-124">For PowerShell 5.1 and below, the default encoding is different from VSCode's.</span></span>
- <span data-ttu-id="ea138-125">Un altro editor è aperto e sovrascrivere il file in una nuova codifica.</span><span class="sxs-lookup"><span data-stu-id="ea138-125">Another editor has opened and overwritten the file in a new encoding.</span></span> <span data-ttu-id="ea138-126">Ciò si verifica spesso con ISE.</span><span class="sxs-lookup"><span data-stu-id="ea138-126">This often happens with the ISE.</span></span>
- <span data-ttu-id="ea138-127">Il file è archiviato nel controllo del codice sorgente in una codifica diversa dal quale Visual Studio code o da PowerShell prevede.</span><span class="sxs-lookup"><span data-stu-id="ea138-127">The file is checked into source control in an encoding that is different from what VSCode or PowerShell expects.</span></span> <span data-ttu-id="ea138-128">Questa situazione può verificarsi quando i collaboratori usano l'editor con diverse configurazioni di codifica.</span><span class="sxs-lookup"><span data-stu-id="ea138-128">This can happen when collaborators use editors with different encoding configurations.</span></span>

### <a name="how-to-tell-when-you-have-encoding-issues"></a><span data-ttu-id="ea138-129">Come sapere quando hai i problemi di codifica</span><span class="sxs-lookup"><span data-stu-id="ea138-129">How to tell when you have encoding issues</span></span>

<span data-ttu-id="ea138-130">Errori di codifica spesso vengono visualizzati come analizzare gli errori negli script.</span><span class="sxs-lookup"><span data-stu-id="ea138-130">Often encoding errors present themselves as parse errors in scripts.</span></span> <span data-ttu-id="ea138-131">Se le sequenze di caratteri insoliti si trova nello script, ciò può rappresentare il problema.</span><span class="sxs-lookup"><span data-stu-id="ea138-131">If you find strange character sequences in your script, this can be the problem.</span></span> <span data-ttu-id="ea138-132">Nell'esempio seguente, un trattino (`–`) viene visualizzato come i caratteri `â€“`:</span><span class="sxs-lookup"><span data-stu-id="ea138-132">In the example below, an en-dash (`–`) appears as the characters `â€“`:</span></span>

```Output
Send-MailMessage : A positional parameter cannot be found that accepts argument 'Testing FuseMail SMTP...'.
At C:\Users\<User>\<OneDrive>\Development\PowerShell\Scripts\Send-EmailUsingSmtpRelay.ps1:6 char:1
+ Send-MailMessage â€“From $from â€“To $recipient1 â€“Subject $subject  ...
+ ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
    + CategoryInfo          : InvalidArgument: (:) [Send-MailMessage], ParameterBindingException
    + FullyQualifiedErrorId : PositionalParameterNotFound,Microsoft.PowerShell.Commands.SendMailMessage
```

<span data-ttu-id="ea138-133">Questo problema si verifica perché Visual Studio code consente di codificare il carattere `–` in formato UTF-8 come i byte `0xE2 0x80 0x93`.</span><span class="sxs-lookup"><span data-stu-id="ea138-133">This problem occurs because VSCode encodes the character `–` in UTF-8 as the bytes `0xE2 0x80 0x93`.</span></span>
<span data-ttu-id="ea138-134">Quando questi byte vengono decodificati come Windows-1252, vengono interpretate come caratteri `â€“`.</span><span class="sxs-lookup"><span data-stu-id="ea138-134">When these bytes are decoded as Windows-1252, they are interpreted as the characters `â€“`.</span></span>

<span data-ttu-id="ea138-135">Alcune sequenze di caratteri insoliti che potrebbero essere visualizzati includono:</span><span class="sxs-lookup"><span data-stu-id="ea138-135">Some strange character sequences that you might see include:</span></span>

- <span data-ttu-id="ea138-136">`â€“` invece di `–`</span><span class="sxs-lookup"><span data-stu-id="ea138-136">`â€“` instead of `–`</span></span>
- <span data-ttu-id="ea138-137">`â€”` invece di `—`</span><span class="sxs-lookup"><span data-stu-id="ea138-137">`â€”` instead of `—`</span></span>
- <span data-ttu-id="ea138-138">`Ã„2` invece di `Ä`</span><span class="sxs-lookup"><span data-stu-id="ea138-138">`Ã„2` instead of `Ä`</span></span>
- <span data-ttu-id="ea138-139">`Â` invece di ` ` (spazi unificatori)</span><span class="sxs-lookup"><span data-stu-id="ea138-139">`Â` instead of ` `  (a non-breaking space)</span></span>
- <span data-ttu-id="ea138-140">`Ã©` invece di `é`</span><span class="sxs-lookup"><span data-stu-id="ea138-140">`Ã©` instead of `é`</span></span>

<span data-ttu-id="ea138-141">Questo utile [riferimento](https://www.i18nqa.com/debug/utf8-debug.html) sono elencati i modelli comuni che indicano un problema di codifica UTF-8 o Windows-1252.</span><span class="sxs-lookup"><span data-stu-id="ea138-141">This handy [reference](https://www.i18nqa.com/debug/utf8-debug.html) lists the common patterns that indicate a UTF-8/Windows-1252 encoding problem.</span></span>

## <a name="how-the-powershell-extension-in-vscode-interacts-with-encodings"></a><span data-ttu-id="ea138-142">Modalità di interazione con codifiche l'estensione di PowerShell in Visual Studio code</span><span class="sxs-lookup"><span data-stu-id="ea138-142">How the PowerShell extension in VSCode interacts with encodings</span></span>

<span data-ttu-id="ea138-143">L'estensione di PowerShell interagisce con gli script in numerosi modi:</span><span class="sxs-lookup"><span data-stu-id="ea138-143">The PowerShell extension interacts with scripts in a number of ways:</span></span>

1. <span data-ttu-id="ea138-144">Quando gli script vengono modificati in Visual Studio code, i contenuti vengono inviati tramite Visual Studio code per l'estensione.</span><span class="sxs-lookup"><span data-stu-id="ea138-144">When scripts are edited in VSCode, the contents are sent by VSCode to the extension.</span></span> <span data-ttu-id="ea138-145">Il [protocollo di Server di linguaggio][] impone che questo contenuto è stato trasferito in UTF-8.</span><span class="sxs-lookup"><span data-stu-id="ea138-145">The [Language Server Protocol][] mandates that this content is transferred in UTF-8.</span></span> <span data-ttu-id="ea138-146">Non è pertanto possibile che l'estensione ottenere la codifica non corretta.</span><span class="sxs-lookup"><span data-stu-id="ea138-146">Therefore, it is not possible for the extension to get the wrong encoding.</span></span>
2. <span data-ttu-id="ea138-147">Quando gli script vengono eseguiti direttamente nella Console integrata, vengono letti dal file di PowerShell direttamente.</span><span class="sxs-lookup"><span data-stu-id="ea138-147">When scripts are executed directly in the Integrated Console, they're read from the file by PowerShell directly.</span></span> <span data-ttu-id="ea138-148">Tf PowerShell codifica è diverso da di VSCode, qualcosa può andare storto qui.</span><span class="sxs-lookup"><span data-stu-id="ea138-148">Tf PowerShell's encoding differs from VSCode's, something can go wrong here.</span></span>
3. <span data-ttu-id="ea138-149">Quando uno script che viene aperto in VSCode fa riferimento a un altro script che non sia aperto in Visual Studio code, l'estensione per il fallback al caricamento del contenuto dello script che dal file system.</span><span class="sxs-lookup"><span data-stu-id="ea138-149">When a script that is open in VSCode references another script that is not open in VSCode, the extension falls back to loading that script's content from the file system.</span></span> <span data-ttu-id="ea138-150">L'estensione di PowerShell per impostazione predefinita la codifica UTF-8, ma utilizza BOM, o [indicatore ordine byte][], il rilevamento per selezionare la codifica corretta.</span><span class="sxs-lookup"><span data-stu-id="ea138-150">The PowerShell extension defaults to UTF-8 encoding, but uses [byte-order mark][], or BOM, detection to select the correct encoding.</span></span>

<span data-ttu-id="ea138-151">Il problema si verifica quando presupponendo che la codifica dei formati senza BOM (ad esempio [UTF-8][] con alcun BOM e [Windows-1252][]).</span><span class="sxs-lookup"><span data-stu-id="ea138-151">The problem occurs when assuming the encoding of BOM-less formats (like [UTF-8][] with no BOM and [Windows-1252][]).</span></span>
<span data-ttu-id="ea138-152">L'estensione di PowerShell viene impostato su UTF-8.</span><span class="sxs-lookup"><span data-stu-id="ea138-152">The PowerShell extension defaults to UTF-8.</span></span> <span data-ttu-id="ea138-153">L'estensione non è possibile modificare le impostazioni di codifica di Visual Studio code.</span><span class="sxs-lookup"><span data-stu-id="ea138-153">The extension cannot change VSCode's encoding settings.</span></span>
<span data-ttu-id="ea138-154">Per altre informazioni, vedere [problema #824](https://github.com/Microsoft/vscode/issues/824).</span><span class="sxs-lookup"><span data-stu-id="ea138-154">For more information, see [issue #824](https://github.com/Microsoft/vscode/issues/824).</span></span>

## <a name="choosing-the-right-encoding"></a><span data-ttu-id="ea138-155">Scegliere la codifica a destra</span><span class="sxs-lookup"><span data-stu-id="ea138-155">Choosing the right encoding</span></span>

<span data-ttu-id="ea138-156">Le applicazioni e sistemi diversi possono utilizzare codifiche differenti:</span><span class="sxs-lookup"><span data-stu-id="ea138-156">Different systems and applications can use different encodings:</span></span>

- <span data-ttu-id="ea138-157">In .NET Standard, sul web e nel mondo Linux, UTF-8 è ora dominante codifica.</span><span class="sxs-lookup"><span data-stu-id="ea138-157">In .NET Standard, on the web, and in the Linux world, UTF-8 is now the dominant encoding.</span></span>
- <span data-ttu-id="ea138-158">Molte applicazioni .NET Framework usano [UTF-16][].</span><span class="sxs-lookup"><span data-stu-id="ea138-158">Many .NET Framework applications use [UTF-16][].</span></span> <span data-ttu-id="ea138-159">Per motivi di cronologia, è talvolta definito "Unicode", un termine che ora si riferisce a un'ampia [standard](https://en.wikipedia.org/wiki/Unicode) che include sia UTF-8 e UTF-16.</span><span class="sxs-lookup"><span data-stu-id="ea138-159">For historical reasons, this is sometimes called "Unicode", a term that now refers to a broad [standard](https://en.wikipedia.org/wiki/Unicode) that includes both UTF-8 and UTF-16.</span></span>
- <span data-ttu-id="ea138-160">In Windows, molte applicazioni native risalenti a Unicode continuano a usare Windows-1252 per impostazione predefinita.</span><span class="sxs-lookup"><span data-stu-id="ea138-160">On Windows, many native applications that predate Unicode continue to use Windows-1252 by default.</span></span>

<span data-ttu-id="ea138-161">Le codifiche Unicode prevedono inoltre il concetto di un byte order mark (BOM).</span><span class="sxs-lookup"><span data-stu-id="ea138-161">Unicode encodings also have the concept of a byte-order mark (BOM).</span></span> <span data-ttu-id="ea138-162">DB verificano all'inizio del testo per indicare a quale codifica il testo è tramite un decodificatore.</span><span class="sxs-lookup"><span data-stu-id="ea138-162">BOMs occur at the beginning of text to tell a decoder which encoding the text is using.</span></span> <span data-ttu-id="ea138-163">Per le codifiche multibyte, indica anche il carattere BOM [ordine dei byte](https://en.wikipedia.org/wiki/Endianness) della codifica.</span><span class="sxs-lookup"><span data-stu-id="ea138-163">For multi-byte encodings, the BOM also indicates [endianness](https://en.wikipedia.org/wiki/Endianness) of the encoding.</span></span> <span data-ttu-id="ea138-164">DB sono progettate per essere byte che si verificano raramente in testo non Unicode, che consente di stimare ragionevolmente anche che il testo è Unicode quando è presente un carattere BOM.</span><span class="sxs-lookup"><span data-stu-id="ea138-164">BOMs are designed to be bytes that rarely occur in non-Unicode text, allowing a reasonable guess that text is Unicode when a BOM is present.</span></span>

<span data-ttu-id="ea138-165">DB sono facoltative e non è la loro adozione più famosi nel mondo Linux perché viene utilizzata una convenzione affidabile UTF-8 ovunque.</span><span class="sxs-lookup"><span data-stu-id="ea138-165">BOMs are optional and their adoption isn't as popular in the Linux world because a dependable convention of UTF-8 is used everywhere.</span></span> <span data-ttu-id="ea138-166">La maggior parte delle applicazioni Linux presumono che l'input di testo è codificato in UTF-8.</span><span class="sxs-lookup"><span data-stu-id="ea138-166">Most Linux applications presume that text input is encoded in UTF-8.</span></span> <span data-ttu-id="ea138-167">Mentre molte applicazioni di Linux riconoscerà e gestire correttamente un carattere BOM, un numero, non sono iniziali agli elementi nel testo manipolati con tali applicazioni.</span><span class="sxs-lookup"><span data-stu-id="ea138-167">While many Linux applications will recognize and correctly handle a BOM, a number do not, leading to artifacts in text manipulated with those applications.</span></span>

<span data-ttu-id="ea138-168">**Di conseguenza**:</span><span class="sxs-lookup"><span data-stu-id="ea138-168">**Therefore**:</span></span>

- <span data-ttu-id="ea138-169">Se si lavora principalmente con le applicazioni di Windows e Windows PowerShell, è preferibile una codifica come UTF-8 con BOM o UTF-16.</span><span class="sxs-lookup"><span data-stu-id="ea138-169">If you work primarily with Windows applications and Windows PowerShell, you should prefer an encoding like UTF-8 with BOM or UTF-16.</span></span>
- <span data-ttu-id="ea138-170">Se si lavora su piattaforme, è preferibile UTF-8 con BOM.</span><span class="sxs-lookup"><span data-stu-id="ea138-170">If you work across platforms, you should prefer UTF-8 with BOM.</span></span>
- <span data-ttu-id="ea138-171">Se si lavora principalmente in contesti associati a Linux, è preferibile UTF-8 senza BOM.</span><span class="sxs-lookup"><span data-stu-id="ea138-171">If you work mainly in Linux-associated contexts, you should prefer UTF-8 without BOM.</span></span>
- <span data-ttu-id="ea138-172">Windows-1252 e latino 1 sono essenzialmente le codifiche legacy che è necessario evitare se possibile.</span><span class="sxs-lookup"><span data-stu-id="ea138-172">Windows-1252 and latin-1 are essentially legacy encodings that you should avoid if possible.</span></span>
  <span data-ttu-id="ea138-173">Tuttavia, alcune applicazioni di Windows precedenti potrebbero dipendono da tali.</span><span class="sxs-lookup"><span data-stu-id="ea138-173">However, some older Windows applications may depend on them.</span></span>
- <span data-ttu-id="ea138-174">È anche importante notare che la firma degli script [dipendente dalla codifica](https://github.com/PowerShell/PowerShell/issues/3466), vale a dire una modifica della codifica in uno script firmato richiederanno riapposizione della firma.</span><span class="sxs-lookup"><span data-stu-id="ea138-174">It's also worth noting that script signing is [encoding-dependent](https://github.com/PowerShell/PowerShell/issues/3466), meaning a change of encoding on a signed script will require resigning.</span></span>

## <a name="configuring-vscode"></a><span data-ttu-id="ea138-175">Configurazione di Visual Studio code</span><span class="sxs-lookup"><span data-stu-id="ea138-175">Configuring VSCode</span></span>

<span data-ttu-id="ea138-176">Della VSCode codifica predefinita è UTF-8 senza BOM.</span><span class="sxs-lookup"><span data-stu-id="ea138-176">VSCode's default encoding is UTF-8 without BOM.</span></span>

<span data-ttu-id="ea138-177">Per impostare [codifica VSCode][], passare alle impostazioni di Visual Studio code (<kbd>Ctrl<kbd>+</kbd>,</kbd>) e impostare il `"files.encoding"` impostazione:</span><span class="sxs-lookup"><span data-stu-id="ea138-177">To set [VSCode's encoding][], go to the VSCode settings (<kbd>Ctrl<kbd>+</kbd>,</kbd>) and set the `"files.encoding"` setting:</span></span>

```json
"files.encoding": "utf8bom"
```

<span data-ttu-id="ea138-178">Alcuni valori possibili sono:</span><span class="sxs-lookup"><span data-stu-id="ea138-178">Some possible values are:</span></span>

- <span data-ttu-id="ea138-179">`utf8`: [UTF-8] senza BOM</span><span class="sxs-lookup"><span data-stu-id="ea138-179">`utf8`: [UTF-8] without BOM</span></span>
- <span data-ttu-id="ea138-180">`utf8bom`: [UTF-8] con BOM</span><span class="sxs-lookup"><span data-stu-id="ea138-180">`utf8bom`: [UTF-8] with BOM</span></span>
- <span data-ttu-id="ea138-181">`utf16le`: Little endian [UTF-16]</span><span class="sxs-lookup"><span data-stu-id="ea138-181">`utf16le`: Little endian [UTF-16]</span></span>
- <span data-ttu-id="ea138-182">`utf16be`: Big endian [UTF-16]</span><span class="sxs-lookup"><span data-stu-id="ea138-182">`utf16be`: Big endian [UTF-16]</span></span>
- <span data-ttu-id="ea138-183">`windows1252`: [Windows-1252]</span><span class="sxs-lookup"><span data-stu-id="ea138-183">`windows1252`: [Windows-1252]</span></span>

<span data-ttu-id="ea138-184">È necessario ottenere un elenco a discesa per questo oggetto nella visualizzazione GUI o visualizzare i completamenti per tale nel file JSON.</span><span class="sxs-lookup"><span data-stu-id="ea138-184">You should get a dropdown for this in the GUI view, or completions for it in the JSON view.</span></span>

<span data-ttu-id="ea138-185">È anche possibile aggiungere quanto segue per rilevare automaticamente la codifica quando è possibile:</span><span class="sxs-lookup"><span data-stu-id="ea138-185">You can also add the following to autodetect encoding when possible:</span></span>

```json
"files.autoGuessEncoding": true
```

<span data-ttu-id="ea138-186">Se non si vuole queste impostazioni interessano tutti i tipi di file, Visual Studio code consente inoltre alle configurazioni per ogni lingua.</span><span class="sxs-lookup"><span data-stu-id="ea138-186">If you don't want these settings to affect all files types, VSCode also allows per-language configurations.</span></span> <span data-ttu-id="ea138-187">Creare un'impostazione specifica del linguaggio inserendo le impostazioni in un `[<language-name>]` campo.</span><span class="sxs-lookup"><span data-stu-id="ea138-187">Create a language-specific setting by putting settings in a `[<language-name>]` field.</span></span> <span data-ttu-id="ea138-188">Ad esempio:</span><span class="sxs-lookup"><span data-stu-id="ea138-188">For example:</span></span>

```json
"[powershell]": {
    "files.encoding": "utf8bom",
    "files.autoGuessEncoding": true
}
```

## <a name="configuring-powershell"></a><span data-ttu-id="ea138-189">Configurazione di PowerShell</span><span class="sxs-lookup"><span data-stu-id="ea138-189">Configuring PowerShell</span></span>

<span data-ttu-id="ea138-190">Della PowerShell codifica predefinita varia a seconda della versione:</span><span class="sxs-lookup"><span data-stu-id="ea138-190">PowerShell's default encoding varies depending on version:</span></span>

- <span data-ttu-id="ea138-191">In PowerShell 6 o versione successiva, la codifica predefinita è UTF-8 senza BOM in tutte le piattaforme.</span><span class="sxs-lookup"><span data-stu-id="ea138-191">In PowerShell 6+, the default encoding is UTF-8 without BOM on all platforms.</span></span>
- <span data-ttu-id="ea138-192">In Windows PowerShell, la codifica predefinita è in genere sui Windows-1252, un'estensione della [latin 1][], noto anche come ISO 8859-1.</span><span class="sxs-lookup"><span data-stu-id="ea138-192">In Windows PowerShell, the default encoding is usually Windows-1252, an extension of [latin-1][], also known as ISO 8859-1.</span></span>

<span data-ttu-id="ea138-193">In PowerShell 5 o versione successiva è possibile trovare la codifica predefinita con questo:</span><span class="sxs-lookup"><span data-stu-id="ea138-193">In PowerShell 5+ you can find your default encoding with this:</span></span>

```powershell
[psobject].Assembly.GetTypes() | Where-Object { $_.Name -eq 'ClrFacade'} |
  ForEach-Object {
    $_.GetMethod('GetDefaultEncoding', [System.Reflection.BindingFlags]'nonpublic,static').Invoke($null, @())
  }
```

<span data-ttu-id="ea138-194">Quanto segue [script](https://gist.github.com/rjmholt/3d8dd4849f718c914132ce3c5b278e0e) può essere utilizzato per determinare ciò che codifica la sessione di PowerShell viene dedotto per uno script senza un carattere BOM.</span><span class="sxs-lookup"><span data-stu-id="ea138-194">The following [script](https://gist.github.com/rjmholt/3d8dd4849f718c914132ce3c5b278e0e) can be used to determine what encoding your PowerShell session infers for a script without a BOM.</span></span>

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

<span data-ttu-id="ea138-195">È possibile configurare PowerShell per usare una codifica specificata in termini più generali tramite le impostazioni del profilo.</span><span class="sxs-lookup"><span data-stu-id="ea138-195">It's possible to configure PowerShell to use a given encoding more generally using profile settings.</span></span> <span data-ttu-id="ea138-196">Vedere gli articoli seguenti:</span><span class="sxs-lookup"><span data-stu-id="ea138-196">See the following articles:</span></span>

- <span data-ttu-id="ea138-197">[@mklement0]del [risposte sulla codifica di PowerShell su StackOverflow](https://stackoverflow.com/a/40098904).</span><span class="sxs-lookup"><span data-stu-id="ea138-197">[@mklement0]'s [answer about PowerShell encoding on StackOverflow](https://stackoverflow.com/a/40098904).</span></span>
- <span data-ttu-id="ea138-198">[@rkeithhill]del [post di blog sulla gestione dell'input senza BOM UTF-8 in PowerShell](https://rkeithhill.wordpress.com/2010/05/26/handling-native-exe-output-encoding-in-utf8-with-no-bom/).</span><span class="sxs-lookup"><span data-stu-id="ea138-198">[@rkeithhill]'s [blog post about dealing with BOM-less UTF-8 input in PowerShell](https://rkeithhill.wordpress.com/2010/05/26/handling-native-exe-output-encoding-in-utf8-with-no-bom/).</span></span>

<span data-ttu-id="ea138-199">Non è possibile forzare di PowerShell per usare una codifica input specifico.</span><span class="sxs-lookup"><span data-stu-id="ea138-199">It's not possible to force PowerShell to use a specific input encoding.</span></span> <span data-ttu-id="ea138-200">PowerShell 5.1 e versioni precedenti per impostazione predefinita a Windows-1252 codifica quando non è presente alcun BOM.</span><span class="sxs-lookup"><span data-stu-id="ea138-200">PowerShell 5.1 and below default to Windows-1252 encoding when there's no BOM.</span></span> <span data-ttu-id="ea138-201">Per motivi di interoperabilità, è consigliabile salvare gli script in formato Unicode con un carattere BOM.</span><span class="sxs-lookup"><span data-stu-id="ea138-201">For interoperability reasons, it's best to save scripts in a Unicode format with a BOM.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="ea138-202">Qualsiasi altro strumento, è necessario un tocco PowerShell script può essere influenzato dalle scelte di codifica o codificare di nuovo gli script a un'altra codifica.</span><span class="sxs-lookup"><span data-stu-id="ea138-202">Any other tools you have that touch PowerShell scripts may be affected by your encoding choices or re-encode your scripts to another encoding.</span></span>

### <a name="existing-scripts"></a><span data-ttu-id="ea138-203">Script esistenti</span><span class="sxs-lookup"><span data-stu-id="ea138-203">Existing scripts</span></span>

<span data-ttu-id="ea138-204">Gli script già presente nel file system potrebbero dover essere codificata nuovamente per la nuova codifica scelta.</span><span class="sxs-lookup"><span data-stu-id="ea138-204">Scripts already on the file system may need to be re-encoded to your new chosen encoding.</span></span> <span data-ttu-id="ea138-205">Nella barra nella parte inferiore di VSCode, verrà visualizzata l'etichetta UTF-8.</span><span class="sxs-lookup"><span data-stu-id="ea138-205">In the bottom bar of VSCode, you'll see the label UTF-8.</span></span> <span data-ttu-id="ea138-206">Fare clic per aprire la barra delle azioni e selezionare **Salva con codifica**.</span><span class="sxs-lookup"><span data-stu-id="ea138-206">Click it to open the action bar and select **Save with encoding**.</span></span> <span data-ttu-id="ea138-207">È ora possibile selezionare una nuova codifica per il file.</span><span class="sxs-lookup"><span data-stu-id="ea138-207">You can now pick a new encoding for that file.</span></span> <span data-ttu-id="ea138-208">Visualizzare [codifica VSCode][] per le istruzioni complete.</span><span class="sxs-lookup"><span data-stu-id="ea138-208">See [VSCode's encoding][] for full instructions.</span></span>

<span data-ttu-id="ea138-209">Se è necessario codificare di nuovo più file, è possibile usare lo script seguente:</span><span class="sxs-lookup"><span data-stu-id="ea138-209">If you need to re-encode multiple files, you can use the following script:</span></span>

```powershell
Get-ChildItem *.ps1 -Recurse | ForEach-Object {
    $content = Get-Content -Path $_
    Set-Content -Path $_.Fullname -Value $content -Encoding UTF8 -PassThru -Force
}
```

### <a name="the-powershell-integrated-scripting-environment-ise"></a><span data-ttu-id="ea138-210">PowerShell Integrated Scripting Environment (ISE)</span><span class="sxs-lookup"><span data-stu-id="ea138-210">The PowerShell Integrated Scripting Environment (ISE)</span></span>

<span data-ttu-id="ea138-211">Se è anche possibile modificare gli script con PowerShell ISE, è necessario sincronizzare le impostazioni di codifica non esiste.</span><span class="sxs-lookup"><span data-stu-id="ea138-211">If you also edit scripts using the PowerShell ISE, you need to synchronize your encoding settings there.</span></span>

<span data-ttu-id="ea138-212">ISE deve rispettare un indicatore ordine byte, ma è anche possibile usare la reflection per [impostare la codifica](https://bensonxion.wordpress.com/2012/04/25/powershell-ise-default-saveas-encoding/).</span><span class="sxs-lookup"><span data-stu-id="ea138-212">The ISE should honor a BOM, but it's also possible to use reflection to [set the encoding](https://bensonxion.wordpress.com/2012/04/25/powershell-ise-default-saveas-encoding/).</span></span>
<span data-ttu-id="ea138-213">Si noti che questo non sarebbe vengano resi persistenti tra le Startup.</span><span class="sxs-lookup"><span data-stu-id="ea138-213">Note that this wouldn't be persisted between startups.</span></span>

### <a name="source-control-software"></a><span data-ttu-id="ea138-214">Software per il controllo origine</span><span class="sxs-lookup"><span data-stu-id="ea138-214">Source control software</span></span>

<span data-ttu-id="ea138-215">Alcuni strumenti di controllo di origine, ad esempio git, ignorare le codifiche; GIT tiene traccia solo i byte.</span><span class="sxs-lookup"><span data-stu-id="ea138-215">Some source control tools, such as git, ignore encodings; git just tracks the bytes.</span></span>
<span data-ttu-id="ea138-216">Altri, come TFS o Mercurial, non potranno essere.</span><span class="sxs-lookup"><span data-stu-id="ea138-216">Others, like TFS or Mercurial, may not.</span></span> <span data-ttu-id="ea138-217">Anche alcuni strumenti basati su git si basano su decodifica il testo.</span><span class="sxs-lookup"><span data-stu-id="ea138-217">Even some git-based tools rely on decoding text.</span></span>

<span data-ttu-id="ea138-218">In questo caso, assicurarsi di:</span><span class="sxs-lookup"><span data-stu-id="ea138-218">When this is the case, make sure you:</span></span>

- <span data-ttu-id="ea138-219">Configurare la codifica nel controllo del codice sorgente per corrispondano alla configurazione di Visual Studio code di testo.</span><span class="sxs-lookup"><span data-stu-id="ea138-219">Configure the text encoding in your source control to match your VSCode configuration.</span></span>
- <span data-ttu-id="ea138-220">Verificare che tutti i file vengono archiviati nel controllo del codice sorgente nella codifica pertinenti.</span><span class="sxs-lookup"><span data-stu-id="ea138-220">Ensure all your files are checked into source control in the relevant encoding.</span></span>
- <span data-ttu-id="ea138-221">Essere ben consapevoli delle modifiche per la codifica ricevuta tramite controllo del codice sorgente.</span><span class="sxs-lookup"><span data-stu-id="ea138-221">Be wary of changes to the encoding received through source control.</span></span> <span data-ttu-id="ea138-222">Un segno di questa chiave è delle differenze che indica le modifiche, ma non sembra in cui sono stati modificati (perché è stato byte ma non hanno caratteri).</span><span class="sxs-lookup"><span data-stu-id="ea138-222">A key sign of this is a diff indicating changes but where nothing seems to have changed (because bytes have but characters have not).</span></span>

### <a name="collaborators-environments"></a><span data-ttu-id="ea138-223">Ambienti dei collaboratori</span><span class="sxs-lookup"><span data-stu-id="ea138-223">Collaborators' environments</span></span>

<span data-ttu-id="ea138-224">Nella parte superiore di configurazione di controllo del codice sorgente, verificare che i collaboratori in qualsiasi file che condivisi non siano le impostazioni di cui eseguire l'override di codifica per codificare di nuovo i file di PowerShell.</span><span class="sxs-lookup"><span data-stu-id="ea138-224">On top of configuring source control, ensure that your collaborators on any files you share don't have settings that override your encoding by re-encoding PowerShell files.</span></span>

### <a name="other-programs"></a><span data-ttu-id="ea138-225">Altri programmi</span><span class="sxs-lookup"><span data-stu-id="ea138-225">Other programs</span></span>

<span data-ttu-id="ea138-226">Qualsiasi altro programma che legge o scrive uno script di PowerShell potrebbe codificarli nuovamente.</span><span class="sxs-lookup"><span data-stu-id="ea138-226">Any other program that reads or writes a PowerShell script may re-encode it.</span></span>

<span data-ttu-id="ea138-227">Di seguito sono riportati alcuni esempi:</span><span class="sxs-lookup"><span data-stu-id="ea138-227">Some examples are:</span></span>

- <span data-ttu-id="ea138-228">Usando gli Appunti per copiare e incollare uno script.</span><span class="sxs-lookup"><span data-stu-id="ea138-228">Using the clipboard to copy and paste a script.</span></span> <span data-ttu-id="ea138-229">Questo è comune in scenari come:</span><span class="sxs-lookup"><span data-stu-id="ea138-229">This is common in scenarios like:</span></span>
  - <span data-ttu-id="ea138-230">Copia di uno script in una macchina virtuale</span><span class="sxs-lookup"><span data-stu-id="ea138-230">Copying a script into a VM</span></span>
  - <span data-ttu-id="ea138-231">Copia di uno script all'esterno di un messaggio di posta elettronica o una pagina Web</span><span class="sxs-lookup"><span data-stu-id="ea138-231">Copying a script out of an email or webpage</span></span>
  - <span data-ttu-id="ea138-232">Copia di uno script all'interno o all'esterno di un documento Microsoft Word o PowerPoint.</span><span class="sxs-lookup"><span data-stu-id="ea138-232">Copying a script into or out of a Microsoft Word or PowerPoint document</span></span>
- <span data-ttu-id="ea138-233">Altri editor di testo, ad esempio:</span><span class="sxs-lookup"><span data-stu-id="ea138-233">Other text editors, such as:</span></span>
  - <span data-ttu-id="ea138-234">Blocco note</span><span class="sxs-lookup"><span data-stu-id="ea138-234">Notepad</span></span>
  - <span data-ttu-id="ea138-235">vim</span><span class="sxs-lookup"><span data-stu-id="ea138-235">vim</span></span>
  - <span data-ttu-id="ea138-236">Qualsiasi altro editor di script di PowerShell</span><span class="sxs-lookup"><span data-stu-id="ea138-236">Any other PowerShell script editor</span></span>
- <span data-ttu-id="ea138-237">Modifica delle utilità, ad esempio testo:</span><span class="sxs-lookup"><span data-stu-id="ea138-237">Text editing utilities, like:</span></span>
  - `Get-Content`/`Set-Content`/`Out-File`
  - <span data-ttu-id="ea138-238">Operatori di reindirizzamento di PowerShell, ad esempio `>` e `>>`</span><span class="sxs-lookup"><span data-stu-id="ea138-238">PowerShell redirection operators like `>` and `>>`</span></span>
  - `sed`/`awk`
- <span data-ttu-id="ea138-239">I programmi di trasferimento del file, ad esempio:</span><span class="sxs-lookup"><span data-stu-id="ea138-239">File transfer programs, like:</span></span>
  - <span data-ttu-id="ea138-240">Un web browser, durante il download degli script</span><span class="sxs-lookup"><span data-stu-id="ea138-240">A web browser, when downloading scripts</span></span>
  - <span data-ttu-id="ea138-241">Una condivisione file</span><span class="sxs-lookup"><span data-stu-id="ea138-241">A file share</span></span>

<span data-ttu-id="ea138-242">Alcuni di questi strumenti gestiscono in byte anziché di testo, ma altri offrono configurazioni di codifica.</span><span class="sxs-lookup"><span data-stu-id="ea138-242">Some of these tools deal in bytes rather than text, but others offer encoding configurations.</span></span> <span data-ttu-id="ea138-243">In questi casi in cui è necessario configurare una codifica, è necessario renderlo lo stesso come editor di codifica per evitare eventuali problemi.</span><span class="sxs-lookup"><span data-stu-id="ea138-243">In those cases where you need to configure an encoding, you need to make it the same as your editor encoding to prevent problems.</span></span>

## <a name="other-resources-on-encoding-in-powershell"></a><span data-ttu-id="ea138-244">Altre risorse sulla codifica in PowerShell</span><span class="sxs-lookup"><span data-stu-id="ea138-244">Other resources on encoding in PowerShell</span></span>

<span data-ttu-id="ea138-245">Esistono alcuni altri post interessante su codifica e la configurazione di codifica in PowerShell che vale la pena di un'operazione di lettura:</span><span class="sxs-lookup"><span data-stu-id="ea138-245">There are a few other nice posts on encoding and configuring encoding in PowerShell that are worth a read:</span></span>

- <span data-ttu-id="ea138-246">[@mklement0]del [riepilogo della codifica di PowerShell su StackOverflow](https://stackoverflow.com/questions/40098771/changing-powershells-default-output-encoding-to-utf-8)</span><span class="sxs-lookup"><span data-stu-id="ea138-246">[@mklement0]'s [summary of PowerShell encoding on StackOverflow](https://stackoverflow.com/questions/40098771/changing-powershells-default-output-encoding-to-utf-8)</span></span>
- <span data-ttu-id="ea138-247">Problemi precedenti aperto in vscode-PowerShell per la codifica dei problemi:</span><span class="sxs-lookup"><span data-stu-id="ea138-247">Previous issues opened on vscode-PowerShell for encoding problems:</span></span>
  - [<span data-ttu-id="ea138-248">#1308</span><span class="sxs-lookup"><span data-stu-id="ea138-248">#1308</span></span>](https://github.com/PowerShell/vscode-powershell/issues/1308)
  - [<span data-ttu-id="ea138-249">#1628</span><span class="sxs-lookup"><span data-stu-id="ea138-249">#1628</span></span>](https://github.com/PowerShell/vscode-powershell/issues/1628)
  - [<span data-ttu-id="ea138-250">#1680</span><span class="sxs-lookup"><span data-stu-id="ea138-250">#1680</span></span>](https://github.com/PowerShell/vscode-powershell/issues/1680)
  - [<span data-ttu-id="ea138-251">#1744</span><span class="sxs-lookup"><span data-stu-id="ea138-251">#1744</span></span>](https://github.com/PowerShell/vscode-powershell/issues/1744)
  - [<span data-ttu-id="ea138-252">#1751</span><span class="sxs-lookup"><span data-stu-id="ea138-252">#1751</span></span>](https://github.com/PowerShell/vscode-powershell/issues/1751)
- [<span data-ttu-id="ea138-253">Il modello di distribuzione classica *opinione di Joel su Software* scriviamo su Unicode</span><span class="sxs-lookup"><span data-stu-id="ea138-253">The classic *Joel on Software* write up about Unicode</span></span>](https://www.joelonsoftware.com/2003/10/08/the-absolute-minimum-every-software-developer-absolutely-positively-must-know-about-unicode-and-character-sets-no-excuses/)
- [<span data-ttu-id="ea138-254">Codifica in .NET Standard</span><span class="sxs-lookup"><span data-stu-id="ea138-254">Encoding in .NET Standard</span></span>](https://github.com/dotnet/standard/issues/260#issuecomment-289549508)


[@mklement0]: https://github.com/mklement0
[@rkeithhill]: https://github.com/rkeithhill
[Windows-1252]: https://wikipedia.org/wiki/Windows-1252
[latin 1]: https://wikipedia.org/wiki/ISO/IEC_8859-1
[latin-1]: https://wikipedia.org/wiki/ISO/IEC_8859-1
[UTF-8]: https://wikipedia.org/wiki/UTF-8
[indicatore ordine byte]: https://wikipedia.org/wiki/Byte_order_mark
[byte-order mark]: https://wikipedia.org/wiki/Byte_order_mark
[UTF-16]: https://wikipedia.org/wiki/UTF-16
[Protocollo di Server di linguaggio]: https://microsoft.github.io/language-server-protocol/
[Language Server Protocol]: https://microsoft.github.io/language-server-protocol/
[codifica VSCode]: https://code.visualstudio.com/docs/editor/codebasics#_file-encoding-support
[VSCode's encoding]: https://code.visualstudio.com/docs/editor/codebasics#_file-encoding-support