---
title: Elenco di controllo editoriale
description: Elenco riassuntivo delle regole per la modifica della documentazione di PowerShell.
ms.date: 03/05/2020
ms.topic: conceptual
ms.openlocfilehash: 511e0c323e1a3256039e819d06f32f6e1ac42767
ms.sourcegitcommit: 18d832858a7b8ea094763afa753e0f48f01372e7
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 03/10/2020
ms.locfileid: "79060336"
---
# <a name="editors-checklist"></a><span data-ttu-id="d5f7d-103">Elenco di controllo del redattore</span><span class="sxs-lookup"><span data-stu-id="d5f7d-103">Editor's checklist</span></span>

<span data-ttu-id="d5f7d-104">Di seguito è riportato un riepilogo delle regole da applicare quando si scrivono nuovi articoli o si aggiornano quelli esistenti.</span><span class="sxs-lookup"><span data-stu-id="d5f7d-104">This is a summary of rules to apply when writing new or updating existing articles.</span></span> <span data-ttu-id="d5f7d-105">Per spiegazioni dettagliate ed esempi di queste regole, vedere gli altri articoli della Guida per i collaboratori.</span><span class="sxs-lookup"><span data-stu-id="d5f7d-105">See other articles in the Contributor's Guide for detailed explanations and examples of these rules.</span></span>

## <a name="metadata"></a><span data-ttu-id="d5f7d-106">Metadati</span><span class="sxs-lookup"><span data-stu-id="d5f7d-106">Metadata</span></span>

- <span data-ttu-id="d5f7d-107">`ms.date`: il formato deve essere **MM/DD/YYYY**</span><span class="sxs-lookup"><span data-stu-id="d5f7d-107">`ms.date`: must be in the format **MM/DD/YYYY**</span></span>
  - <span data-ttu-id="d5f7d-108">Cambiare la data in presenza di un aggiornamento reale o significativo</span><span class="sxs-lookup"><span data-stu-id="d5f7d-108">Change the date when there is a significant or factual update</span></span>
    - <span data-ttu-id="d5f7d-109">Riorganizzazione dell'articolo</span><span class="sxs-lookup"><span data-stu-id="d5f7d-109">Reorganizing the article</span></span>
    - <span data-ttu-id="d5f7d-110">Correzione di errori reali</span><span class="sxs-lookup"><span data-stu-id="d5f7d-110">Fixing factual errors</span></span>
    - <span data-ttu-id="d5f7d-111">Aggiunta di nuove informazioni</span><span class="sxs-lookup"><span data-stu-id="d5f7d-111">Adding new information</span></span>
  - <span data-ttu-id="d5f7d-112">Non cambiare la data se l'aggiornamento non è significativo</span><span class="sxs-lookup"><span data-stu-id="d5f7d-112">Do not change the date if the update is insignificant</span></span>
    - <span data-ttu-id="d5f7d-113">Correzione di errori di digitazione e formattazione</span><span class="sxs-lookup"><span data-stu-id="d5f7d-113">Fixing typos and formatting</span></span>
- <span data-ttu-id="d5f7d-114">`title`: stringa univoca di 43-59 caratteri, spazi inclusi</span><span class="sxs-lookup"><span data-stu-id="d5f7d-114">`title`: unique string of 43-59 chars including spaces</span></span>
  - <span data-ttu-id="d5f7d-115">Non includere l'identificatore del sito (viene generato automaticamente)</span><span class="sxs-lookup"><span data-stu-id="d5f7d-115">Do not include site identifier (it is auto-generated)</span></span>
  - <span data-ttu-id="d5f7d-116">Usare la maiuscola a inizio frase, ovvero usare la maiuscola solo per la prima parola ed eventuali nomi propri</span><span class="sxs-lookup"><span data-stu-id="d5f7d-116">Use sentence case - capitalize only the first word and any proper nouns</span></span>
- <span data-ttu-id="d5f7d-117">`description`: 115-145 caratteri, spazi inclusi; questo sunto viene visualizzato nei risultati della ricerca</span><span class="sxs-lookup"><span data-stu-id="d5f7d-117">`description`: 115-145 characters including spaces - this abstract displays in the search result</span></span>

## <a name="formatting"></a><span data-ttu-id="d5f7d-118">Formattazione</span><span class="sxs-lookup"><span data-stu-id="d5f7d-118">Formatting</span></span>

- <span data-ttu-id="d5f7d-119">Elementi di sintassi apice inverso visualizzati, incorporati, all'interno di un paragrafo</span><span class="sxs-lookup"><span data-stu-id="d5f7d-119">Backtick syntax elements that appear, inline, within a paragraph</span></span>
  - <span data-ttu-id="d5f7d-120">Nomi di cmdlet `Verb-Noun`</span><span class="sxs-lookup"><span data-stu-id="d5f7d-120">Cmdlet names `Verb-Noun`</span></span>
  - <span data-ttu-id="d5f7d-121">Variabile `$counter`</span><span class="sxs-lookup"><span data-stu-id="d5f7d-121">Variable `$counter`</span></span>
  - <span data-ttu-id="d5f7d-122">Esempi sintattici `Verb-Noun -Parameter`</span><span class="sxs-lookup"><span data-stu-id="d5f7d-122">Syntactic examples `Verb-Noun -Parameter`</span></span>
  - <span data-ttu-id="d5f7d-123">Percorsi di file `C:\Program Files\PowerShell`, `/usr/bin/pwsh`</span><span class="sxs-lookup"><span data-stu-id="d5f7d-123">File paths `C:\Program Files\PowerShell`, `/usr/bin/pwsh`</span></span>
  - <span data-ttu-id="d5f7d-124">URL non selezionabili nel documento</span><span class="sxs-lookup"><span data-stu-id="d5f7d-124">URLs that are not meant to be clickable in the document</span></span>
- <span data-ttu-id="d5f7d-125">Usare il grassetto per nomi di proprietà, valori di parametri, nomi di parametri, nomi di classi, nomi di moduli, nomi di entità, nomi di oggetti o tipi</span><span class="sxs-lookup"><span data-stu-id="d5f7d-125">Use bold for property names, parameter values, parameter names, class names, module names, entity names, object or type names</span></span>
  - <span data-ttu-id="d5f7d-126">Il grassetto viene usato per il markup semantico, non per dare enfasi</span><span class="sxs-lookup"><span data-stu-id="d5f7d-126">Bold is used for semantic markup, not emphasis</span></span>
  - <span data-ttu-id="d5f7d-127">Grassetto: usare gli asterischi `**`</span><span class="sxs-lookup"><span data-stu-id="d5f7d-127">Bold - use asterisks `**`</span></span>
- <span data-ttu-id="d5f7d-128">Corsivo: usare il carattere di sottolineatura `_`</span><span class="sxs-lookup"><span data-stu-id="d5f7d-128">Italic - use underscore `_`</span></span>
  - <span data-ttu-id="d5f7d-129">Usato solo per dare enfasi, non per il markup semantico</span><span class="sxs-lookup"><span data-stu-id="d5f7d-129">Only used for emphasis, not for semantic markup</span></span>
- <span data-ttu-id="d5f7d-130">Interruzioni di riga a 100 colonne (o a 80 per **about_Topics**)</span><span class="sxs-lookup"><span data-stu-id="d5f7d-130">Line breaks at 100 columns (or at 80 for **about_Topics**)</span></span>
- <span data-ttu-id="d5f7d-131">Nessuna tabulazione, usare solo spazi</span><span class="sxs-lookup"><span data-stu-id="d5f7d-131">No hard tabs - use spaces only</span></span>
- <span data-ttu-id="d5f7d-132">Niente spazi finali nelle righe</span><span class="sxs-lookup"><span data-stu-id="d5f7d-132">No trailing spaces on lines</span></span>

### <a name="headers"></a><span data-ttu-id="d5f7d-133">Headers</span><span class="sxs-lookup"><span data-stu-id="d5f7d-133">Headers</span></span>

- <span data-ttu-id="d5f7d-134">H1 per prima: una sola intestazione H1 per articolo</span><span class="sxs-lookup"><span data-stu-id="d5f7d-134">H1 is first - only one H1 per article</span></span>
- <span data-ttu-id="d5f7d-135">Usare solo [intestazioni ATX](https://github.github.com/gfm/#atx-headings)</span><span class="sxs-lookup"><span data-stu-id="d5f7d-135">Use [ATX Headers](https://github.github.com/gfm/#atx-headings) only</span></span>
- <span data-ttu-id="d5f7d-136">Usare la maiuscola a inizio frase per tutte le intestazioni</span><span class="sxs-lookup"><span data-stu-id="d5f7d-136">Use sentence case for all headers</span></span>
- <span data-ttu-id="d5f7d-137">Non saltare i livelli: non usare H3 senza H2</span><span class="sxs-lookup"><span data-stu-id="d5f7d-137">Do not skip levels - no H3 without an H2</span></span>
- <span data-ttu-id="d5f7d-138">Profondità massima di H3 o H4</span><span class="sxs-lookup"><span data-stu-id="d5f7d-138">Max depth of H3 or H4</span></span>
- <span data-ttu-id="d5f7d-139">Riga vuota prima e dopo</span><span class="sxs-lookup"><span data-stu-id="d5f7d-139">Blank line before and after</span></span>
- <span data-ttu-id="d5f7d-140">PlatyPS applica intestazioni specifiche nel proprio schema; non aggiungere o rimuovere intestazioni</span><span class="sxs-lookup"><span data-stu-id="d5f7d-140">PlatyPS enforces specific headers in its schema - do not add or remove headers</span></span>

### <a name="code-blocks"></a><span data-ttu-id="d5f7d-141">Blocchi di codice</span><span class="sxs-lookup"><span data-stu-id="d5f7d-141">Code blocks</span></span>

- <span data-ttu-id="d5f7d-142">Riga vuota prima e dopo</span><span class="sxs-lookup"><span data-stu-id="d5f7d-142">Blank line before and after</span></span>
- <span data-ttu-id="d5f7d-143">Usare blocchi di codice con tag: **powershell**, **Output** o altro ID di linguaggio appropriato</span><span class="sxs-lookup"><span data-stu-id="d5f7d-143">Use tagged code fences - **powershell**, **Output**, or other appropriate language ID</span></span>
- <span data-ttu-id="d5f7d-144">Blocco senza tag: blocchi di sintassi o altre shell</span><span class="sxs-lookup"><span data-stu-id="d5f7d-144">Untagged fence - syntax blocks or other shells</span></span>
- <span data-ttu-id="d5f7d-145">Inserire **Output** in un blocco di codice separato, ad eccezione di esempi semplici in cui non si vuole che il lettore usi il pulsante **Copy**</span><span class="sxs-lookup"><span data-stu-id="d5f7d-145">Put **Output** in separate code block except for simple examples where you don't intend the for the reader to use the **Copy** button</span></span>
- <span data-ttu-id="d5f7d-146">Vedere l'elenco dei [linguaggi supportati](/contribute/code-in-docs#supported-languages)</span><span class="sxs-lookup"><span data-stu-id="d5f7d-146">See list of [supported languages](/contribute/code-in-docs#supported-languages)</span></span>

### <a name="lists"></a><span data-ttu-id="d5f7d-147">Elenchi</span><span class="sxs-lookup"><span data-stu-id="d5f7d-147">Lists</span></span>

- <span data-ttu-id="d5f7d-148">Rientri impostati correttamente</span><span class="sxs-lookup"><span data-stu-id="d5f7d-148">Indented properly</span></span>
- <span data-ttu-id="d5f7d-149">Riga vuota prima del primo elemento e dopo l'ultimo elemento</span><span class="sxs-lookup"><span data-stu-id="d5f7d-149">Blank line before first item and after last item</span></span>
- <span data-ttu-id="d5f7d-150">Punto elenco: usare il segno meno (`-`) e non l'asterisco (`*`), troppo facile da confondere con l'enfasi</span><span class="sxs-lookup"><span data-stu-id="d5f7d-150">Bullet - use hyphen (`-`) not asterisk (`*`) - too easy to confuse with emphasis</span></span>
- <span data-ttu-id="d5f7d-151">Per gli elenchi numerati, tutti i numeri sono "1."</span><span class="sxs-lookup"><span data-stu-id="d5f7d-151">For numbered lists, all numbers are "1."</span></span>

## <a name="terminology"></a><span data-ttu-id="d5f7d-152">Terminologia</span><span class="sxs-lookup"><span data-stu-id="d5f7d-152">Terminology</span></span>

- <span data-ttu-id="d5f7d-153">PowerShell, Windows PowerShell e PowerShell Core</span><span class="sxs-lookup"><span data-stu-id="d5f7d-153">PowerShell vs. Windows PowerShell vs. PowerShell Core</span></span>
- <span data-ttu-id="d5f7d-154">Vedere [Terminologia dei prodotti](powershell-style-guide.md#product-terminology)</span><span class="sxs-lookup"><span data-stu-id="d5f7d-154">See [Product Terminology](powershell-style-guide.md#product-terminology)</span></span>

## <a name="cmdlet-reference-examples"></a><span data-ttu-id="d5f7d-155">Esempi di riferimento per i cmdlet</span><span class="sxs-lookup"><span data-stu-id="d5f7d-155">Cmdlet reference examples</span></span>

- <span data-ttu-id="d5f7d-156">Deve essere presente almeno un esempio nelle informazioni di riferimento sui cmdlet</span><span class="sxs-lookup"><span data-stu-id="d5f7d-156">Must have at least one example in cmdlet reference</span></span>
- <span data-ttu-id="d5f7d-157">Gli esempi devono riportare il codice sufficiente per illustrare l'utilizzo</span><span class="sxs-lookup"><span data-stu-id="d5f7d-157">Examples should be just enough code to demonstrate the usage</span></span>
- <span data-ttu-id="d5f7d-158">Sintassi di Powershell</span><span class="sxs-lookup"><span data-stu-id="d5f7d-158">PowerShell syntax</span></span>
  - <span data-ttu-id="d5f7d-159">Usare i nomi completi di cmdlet e parametri, non gli alias</span><span class="sxs-lookup"><span data-stu-id="d5f7d-159">Use full names of cmdlets and parameters - no aliases</span></span>
  - <span data-ttu-id="d5f7d-160">Usare lo splatting per i parametri quando la riga di comando diventa troppo lunga</span><span class="sxs-lookup"><span data-stu-id="d5f7d-160">Use splatting for parameters when the command line gets too long</span></span>
  - <span data-ttu-id="d5f7d-161">Evitare di usare apici inversi come caratteri di continuazione di riga; usare solo quando necessario</span><span class="sxs-lookup"><span data-stu-id="d5f7d-161">Avoid using line continuation backticks - only use when necessary</span></span>
- <span data-ttu-id="d5f7d-162">Rimuovere o semplificare il prompt di PowerShell (`PS>`) tranne nei casi in cui è necessario per l'esempio</span><span class="sxs-lookup"><span data-stu-id="d5f7d-162">Remove or simplify the PowerShell prompt (`PS>`) except where required for the example</span></span>
- <span data-ttu-id="d5f7d-163">L'esempio di riferimento per il cmdlet deve seguire lo schema PlatyPS seguente</span><span class="sxs-lookup"><span data-stu-id="d5f7d-163">Cmdlet reference example must follow the following PlatyPS schema</span></span>

  ~~~Markdown
  ### Example 1 - Descriptive title

  Zero or more short descriptive paragraphs explaining the context of the example followed by one or
  more code blocks. Recommend at least one and no more than two.

  ```powershell
  ... one or more PowerShell code statements ...
  ```

  ```Output
  Example output of the code above.
  ```

  Zero or more optional follow up paragraphs that explain the details of the code and output.
  ~~~

- <span data-ttu-id="d5f7d-164">Non inserire paragrafi tra i blocchi di codice.</span><span class="sxs-lookup"><span data-stu-id="d5f7d-164">Do not put paragraphs between the code blocks.</span></span> <span data-ttu-id="d5f7d-165">Tutto il contenuto descrittivo deve essere posizionato prima o dopo i blocchi di codice.</span><span class="sxs-lookup"><span data-stu-id="d5f7d-165">All descriptive content must come before or after the code blocks.</span></span>

## <a name="linking-to-other-documents"></a><span data-ttu-id="d5f7d-166">Collegamento ad altri documenti</span><span class="sxs-lookup"><span data-stu-id="d5f7d-166">Linking to other documents</span></span>

- <span data-ttu-id="d5f7d-167">Collegamento all'esterno del set di documenti o tra le informazioni di riferimento sui cmdlet e concettuali</span><span class="sxs-lookup"><span data-stu-id="d5f7d-167">Linking outside the docset or between cmdlet reference and conceptual</span></span>
  - <span data-ttu-id="d5f7d-168">Usare URL relativi per il collegamento a docs.microsoft.com (rimuovere `https://docs.microsoft.com/en-us`)</span><span class="sxs-lookup"><span data-stu-id="d5f7d-168">Use relative URLs when linking to docs.microsoft.com (remove `https://docs.microsoft.com/en-us`)</span></span>
  - <span data-ttu-id="d5f7d-169">Non includere le impostazioni locali negli URL nelle proprietà Microsoft (ad esempio,</span><span class="sxs-lookup"><span data-stu-id="d5f7d-169">Do not include locales in URLs on Microsoft properties (eg.</span></span> <span data-ttu-id="d5f7d-170">rimuovere `/en-us` dall'URL)</span><span class="sxs-lookup"><span data-stu-id="d5f7d-170">remove `/en-us` from URL)</span></span>
  - <span data-ttu-id="d5f7d-171">Tutti gli URL che puntano a siti Web esterni devono usare HTTPS, a meno che ciò non sia valido per il sito di destinazione</span><span class="sxs-lookup"><span data-stu-id="d5f7d-171">All URLs to external websites should use HTTPS unless that is not valid for the target site</span></span>
- <span data-ttu-id="d5f7d-172">All'interno del set di documenti</span><span class="sxs-lookup"><span data-stu-id="d5f7d-172">Within docset</span></span>
  - <span data-ttu-id="d5f7d-173">Collegare al percorso del file (ad esempio, `../folder/file.md`)</span><span class="sxs-lookup"><span data-stu-id="d5f7d-173">Link to file path (e.g. `../folder/file.md`)</span></span>
  - <span data-ttu-id="d5f7d-174">Tutti i percorsi di file usano caratteri barra (`/`)</span><span class="sxs-lookup"><span data-stu-id="d5f7d-174">All file paths use forward-slash (`/`) characters</span></span>
- <span data-ttu-id="d5f7d-175">I collegamenti alle immagini devono avere un testo alternativo univoco</span><span class="sxs-lookup"><span data-stu-id="d5f7d-175">Image links should have unique alt text</span></span>
