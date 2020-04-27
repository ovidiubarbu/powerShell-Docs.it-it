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
# <a name="powershell-docs-style-guide"></a><span data-ttu-id="f877c-103">Guida di stile per la documentazione di PowerShell</span><span class="sxs-lookup"><span data-stu-id="f877c-103">PowerShell-Docs style guide</span></span>

<span data-ttu-id="f877c-104">Questo articolo è una guida di stile specifica per il contenuto di documentazione di PowerShell.</span><span class="sxs-lookup"><span data-stu-id="f877c-104">This article provides style guidance specific to the PowerShell-Docs content.</span></span> <span data-ttu-id="f877c-105">Le linee guida si basano sulle informazioni incluse nella [Panoramica ](overview.md#get-started-writing-docs).</span><span class="sxs-lookup"><span data-stu-id="f877c-105">This builds on the information outlined in the [Overview](overview.md#get-started-writing-docs).</span></span>

## <a name="product-terminology"></a><span data-ttu-id="f877c-106">Terminologia del prodotto</span><span class="sxs-lookup"><span data-stu-id="f877c-106">Product Terminology</span></span>

<span data-ttu-id="f877c-107">Sono disponibili diverse varianti di PowerShell.</span><span class="sxs-lookup"><span data-stu-id="f877c-107">There are several variants of PowerShell.</span></span>

- <span data-ttu-id="f877c-108">**PowerShell**: è la definizione predefinita.</span><span class="sxs-lookup"><span data-stu-id="f877c-108">**PowerShell** - This is the default.</span></span> <span data-ttu-id="f877c-109">Da questo punto in poi, per PowerShell si intende PowerShell 7 e versioni successive.</span><span class="sxs-lookup"><span data-stu-id="f877c-109">We consider PowerShell 7 and beyond to be the one, true PowerShell going forward.</span></span>
- <span data-ttu-id="f877c-110">**PowerShell Core**: PowerShell basato su .NET Core.</span><span class="sxs-lookup"><span data-stu-id="f877c-110">**PowerShell Core** - PowerShell built on .NET Core.</span></span> <span data-ttu-id="f877c-111">L'uso del termine **Core** deve essere limitato ai casi in cui è necessario distinguere da Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="f877c-111">Usage of the term **Core** should be limited to cases where it is necessary to differentiate it from Windows PowerShell.</span></span>
- <span data-ttu-id="f877c-112">**Windows PowerShell**: PowerShell basato su .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="f877c-112">**Windows PowerShell** - PowerShell built on .NET Framework.</span></span> <span data-ttu-id="f877c-113">Windows PowerShell è disponibile solo in Windows e richiede il framework completo.</span><span class="sxs-lookup"><span data-stu-id="f877c-113">Windows PowerShell ships only on Windows and requires the complete Framework.</span></span>

  <span data-ttu-id="f877c-114">In generale i riferimenti a "Windows PowerShell" nella documentazione possono essere modificati in "PowerShell".</span><span class="sxs-lookup"><span data-stu-id="f877c-114">In general, references to "Windows PowerShell" in documentation can be changed to "PowerShell".</span></span>
  <span data-ttu-id="f877c-115">Deve essere usata la dicitura "Windows PowerShell" quando si parla di un comportamento specifico di "Windows PowerShell".</span><span class="sxs-lookup"><span data-stu-id="f877c-115">"Windows PowerShell" should be used when "Windows PowerShell"-specific behavior is being discussed.</span></span>

<span data-ttu-id="f877c-116">Prodotti correlati</span><span class="sxs-lookup"><span data-stu-id="f877c-116">Related products</span></span>

- <span data-ttu-id="f877c-117">**Visual Studio Code (VS Code)** - Editor open source gratuito di Microsoft.</span><span class="sxs-lookup"><span data-stu-id="f877c-117">**Visual Studio Code (VS Code)** - This is Microsoft's free, open source editor.</span></span> <span data-ttu-id="f877c-118">Per la prima citazione, è necessario usare il nome completo.</span><span class="sxs-lookup"><span data-stu-id="f877c-118">At first mention, the full name should be used.</span></span> <span data-ttu-id="f877c-119">Successivamente, è possibile usare **VS Code**.</span><span class="sxs-lookup"><span data-stu-id="f877c-119">After that you may use **VS Code**.</span></span> <span data-ttu-id="f877c-120">Non usare "VSCode".</span><span class="sxs-lookup"><span data-stu-id="f877c-120">Do not use "VSCode".</span></span>
- <span data-ttu-id="f877c-121">**Estensione PowerShell per Visual Studio Code** - Estensione che trasforma VS Code nell'ambiente IDE preferito per PowerShell.</span><span class="sxs-lookup"><span data-stu-id="f877c-121">**PowerShell Extension for Visual Studio Code** - The extension turns VS Code into the preferred IDE for PowerShell.</span></span> <span data-ttu-id="f877c-122">Per la prima citazione, è necessario usare il nome completo.</span><span class="sxs-lookup"><span data-stu-id="f877c-122">At first mention, the full name should be used.</span></span> <span data-ttu-id="f877c-123">Successivamente è possibile usare **estensione PowerShell**.</span><span class="sxs-lookup"><span data-stu-id="f877c-123">After that you may use **PowerShell extension**.</span></span>
- <span data-ttu-id="f877c-124">**Azure PowerShell** - Raccolta di moduli di PowerShell usati per gestire i servizi di Azure.</span><span class="sxs-lookup"><span data-stu-id="f877c-124">**Azure PowerShell** - This is the collection of PowerShell modules used to manage Azure services.</span></span>
- <span data-ttu-id="f877c-125">**PowerShell Azure Stack** - Raccolta di moduli di PowerShell usati per gestire la soluzione cloud ibrida di Microsoft.</span><span class="sxs-lookup"><span data-stu-id="f877c-125">**Azure Stack PowerShell** - This is the collection of PowerShell modules used to manage Microsoft's hybrid cloud solution.</span></span>

## <a name="markdown-specifics"></a><span data-ttu-id="f877c-126">Specifiche di Markdown</span><span class="sxs-lookup"><span data-stu-id="f877c-126">Markdown specifics</span></span>

<span data-ttu-id="f877c-127">Il sistema Microsoft Open Publishing (OPS) che compila la documentazione usa [markdig][] per elaborare i documenti Markdown.</span><span class="sxs-lookup"><span data-stu-id="f877c-127">The Microsoft Open Publishing System (OPS) that builds our documentation uses [markdig][] to process the Markdown documents.</span></span> <span data-ttu-id="f877c-128">Markdig analizza i documenti in base alle regole della specifica [CommonMark][] più recente.</span><span class="sxs-lookup"><span data-stu-id="f877c-128">Markdig parses the documents based on the rules of the latest [CommonMark][] specification.</span></span>

<span data-ttu-id="f877c-129">La nuova specifica CommonMark è molto più restrittiva in merito alla costruzione di alcuni elementi Markdown.</span><span class="sxs-lookup"><span data-stu-id="f877c-129">The new CommonMark spec is much stricter about the construction of some Markdown elements.</span></span> <span data-ttu-id="f877c-130">Prestare particolare attenzione ai dettagli inclusi in questo documento.</span><span class="sxs-lookup"><span data-stu-id="f877c-130">Pay close attention to the details provided in this document.</span></span>

### <a name="blank-lines-spaces-and-tabs"></a><span data-ttu-id="f877c-131">Righe vuote, spazi e tabulazioni</span><span class="sxs-lookup"><span data-stu-id="f877c-131">Blank lines, spaces, and tabs</span></span>

<span data-ttu-id="f877c-132">Le righe vuote segnalano anche la fine di un blocco in Markdown.</span><span class="sxs-lookup"><span data-stu-id="f877c-132">Blank lines also signal the end of a block in Markdown.</span></span> <span data-ttu-id="f877c-133">Deve essere presente un solo spazio vuoto tra i blocchi Markdown di tipi diversi, ad esempio tra un paragrafo e un elenco o un'intestazione.</span><span class="sxs-lookup"><span data-stu-id="f877c-133">There should be a single blank between Markdown blocks of different types (for example, between a paragraph and a list or header).</span></span>

<span data-ttu-id="f877c-134">Rimuovere le righe vuote duplicate.</span><span class="sxs-lookup"><span data-stu-id="f877c-134">Remove duplicate blank lines.</span></span> <span data-ttu-id="f877c-135">Il rendering di più righe vuote in HTML corrisponde a un'unica riga vuota. Non è quindi utile usare più righe vuote.</span><span class="sxs-lookup"><span data-stu-id="f877c-135">Multiple blank lines render as a single blank line in HTML so there is no purpose for multiple blank lines.</span></span> <span data-ttu-id="f877c-136">Più righe vuote in un blocco di codice interrompono quest'ultimo.</span><span class="sxs-lookup"><span data-stu-id="f877c-136">Multiple blank lines within a code block break the code block.</span></span>

<span data-ttu-id="f877c-137">Rimuovere gli spazi aggiuntivi alla fine delle righe.</span><span class="sxs-lookup"><span data-stu-id="f877c-137">Remove extra spaces at the end of lines.</span></span>

> [!NOTE]
> <span data-ttu-id="f877c-138">La spaziatura è importante in Markdown.</span><span class="sxs-lookup"><span data-stu-id="f877c-138">Spacing is significant in Markdown.</span></span> <span data-ttu-id="f877c-139">Usare sempre gli spazi anziché le tabulazioni hard.</span><span class="sxs-lookup"><span data-stu-id="f877c-139">Always uses spaces instead of hard tabs.</span></span> <span data-ttu-id="f877c-140">Gli spazi finali possono modificare il rendering del codice Markdown.</span><span class="sxs-lookup"><span data-stu-id="f877c-140">Trailing spaces can change how Markdown renders.</span></span>

### <a name="titles-and-headings"></a><span data-ttu-id="f877c-141">Titoli e intestazioni</span><span class="sxs-lookup"><span data-stu-id="f877c-141">Titles and headings</span></span>

<span data-ttu-id="f877c-142">Usare solo [intestazioni ATX][atx] (con lo stile #, anziché intestazioni con stile `=` o `-`).</span><span class="sxs-lookup"><span data-stu-id="f877c-142">Only use [ATX headings][atx] (# style, as opposed to `=` or `-` style headers).</span></span>

- <span data-ttu-id="f877c-143">Usare la maiuscola a inizio frase: solo i nomi propri e la prima lettera di un titolo o di un'intestazione devono essere in maiuscole</span><span class="sxs-lookup"><span data-stu-id="f877c-143">Use sentence case - only proper nouns and the first letter of a title or header should be capitalized</span></span>
- <span data-ttu-id="f877c-144">Deve essere presente uno spazio singolo tra `#` e la prima lettera dell'intestazione</span><span class="sxs-lookup"><span data-stu-id="f877c-144">There must be a single space between the `#` and the first letter of the heading</span></span>
- <span data-ttu-id="f877c-145">Le intestazioni devono essere racchiuse da una sola riga vuota</span><span class="sxs-lookup"><span data-stu-id="f877c-145">Headings should be surrounded by a single blank line</span></span>
- <span data-ttu-id="f877c-146">Ogni documento deve includere un solo titolo H1</span><span class="sxs-lookup"><span data-stu-id="f877c-146">Only one H1 per document</span></span>
- <span data-ttu-id="f877c-147">I livelli di intestazione devono avere incrementi di uno.</span><span class="sxs-lookup"><span data-stu-id="f877c-147">Header levels should increment by one.</span></span> <span data-ttu-id="f877c-148">Non ignorare i livelli</span><span class="sxs-lookup"><span data-stu-id="f877c-148">Do not skip levels</span></span>
- <span data-ttu-id="f877c-149">Non usare il grassetto o altri markup nelle intestazioni</span><span class="sxs-lookup"><span data-stu-id="f877c-149">Do not use bold or other markup in headers</span></span>

### <a name="limit-line-length-to-100-characters"></a><span data-ttu-id="f877c-150">Limitare la lunghezza della riga a 100 caratteri</span><span class="sxs-lookup"><span data-stu-id="f877c-150">Limit line length to 100 characters</span></span>

<span data-ttu-id="f877c-151">Questo vale per gli articoli concettuali e i riferimenti ai cmdlet.</span><span class="sxs-lookup"><span data-stu-id="f877c-151">This applies to conceptual articles and cmdlet reference.</span></span> <span data-ttu-id="f877c-152">La limitazione della lunghezza delle righe migliora la leggibilità dei diff e della cronologia GIT.</span><span class="sxs-lookup"><span data-stu-id="f877c-152">Limiting the line length improves the readability of git diffs and history.</span></span> <span data-ttu-id="f877c-153">Semplifica anche i contributi da parte di altri writer.</span><span class="sxs-lookup"><span data-stu-id="f877c-153">It also makes it easier for other writers to make contributions.</span></span>

<span data-ttu-id="f877c-154">Usare l'estensione [Reflow Markdown][reflow] in Visual Studio Code per reimpostare facilmente il flusso dei paragrafi, in modo da adattarlo alla lunghezza di riga prescritta.</span><span class="sxs-lookup"><span data-stu-id="f877c-154">Use the [Reflow Markdown][reflow] extension in Visual Studio Code to easily reflow paragraphs to fit the prescribed line length.</span></span>

<span data-ttu-id="f877c-155">Il testo dei titoli Informazioni su può avere una lunghezza massima di 80 caratteri.</span><span class="sxs-lookup"><span data-stu-id="f877c-155">About_topics are limited to 80 characters.</span></span> <span data-ttu-id="f877c-156">Per informazioni più specifiche, vedere [Modifica degli articoli di riferimento](./editing-cmdlet-ref.md#formatting-about_-files).</span><span class="sxs-lookup"><span data-stu-id="f877c-156">For more specific information, see [Editing reference articles](./editing-cmdlet-ref.md#formatting-about_-files).</span></span>

### <a name="lists"></a><span data-ttu-id="f877c-157">Elenchi</span><span class="sxs-lookup"><span data-stu-id="f877c-157">Lists</span></span>

<span data-ttu-id="f877c-158">Se l'elenco contiene più frasi o paragrafi, prendere in considerazione l'uso di un'intestazione di sottolivello anziché di un elenco.</span><span class="sxs-lookup"><span data-stu-id="f877c-158">If your list contains multiple sentences or paragraphs, consider using a sub-level header rather than a list.</span></span>

<span data-ttu-id="f877c-159">Gli elenchi devono essere racchiusi da una sola riga vuota.</span><span class="sxs-lookup"><span data-stu-id="f877c-159">List should be surrounded by a single blank line.</span></span>

#### <a name="unordered-lists"></a><span data-ttu-id="f877c-160">Elenchi non ordinati</span><span class="sxs-lookup"><span data-stu-id="f877c-160">Unordered lists</span></span>

<span data-ttu-id="f877c-161">Non terminare gli elementi elenco con un punto (a meno che non contengano più frasi).</span><span class="sxs-lookup"><span data-stu-id="f877c-161">Do not end list items with a period unless they contain multiple sentences.</span></span> <span data-ttu-id="f877c-162">Usare il trattino (`-`) per gli elementi di elenchi puntati.</span><span class="sxs-lookup"><span data-stu-id="f877c-162">Use the hyphen character (`-`) for list item bullets.</span></span> <span data-ttu-id="f877c-163">In questo modo si evita confusione con i markup di grassetto o corsivo che usano l'asterisco (`*`).</span><span class="sxs-lookup"><span data-stu-id="f877c-163">This avoids confusion with bold or italic markup that uses the asterisk [`*`].</span></span> <span data-ttu-id="f877c-164">Per includere un paragrafo o altri elementi sotto un punto elenco, inserire un'interruzione di riga e allineare il rientro con il primo carattere dopo il punto elenco.</span><span class="sxs-lookup"><span data-stu-id="f877c-164">To include a paragraph or other elements under a bullet item, insert a line break and align indentation with the first character after the bullet.</span></span>

<span data-ttu-id="f877c-165">Ad esempio:</span><span class="sxs-lookup"><span data-stu-id="f877c-165">For example:</span></span>

```markdown
This is a list that contain sub-elements under a bullet item.

- First bullet item

  Sentence explaining the first bullet.

  - Sub-bullet item

    Sentence explaining the sub-bullet.

- Second bullet item
- Third bullet item
```

<span data-ttu-id="f877c-166">Questo è un elenco che contiene sottoelementi sotto un elemento punto elenco.</span><span class="sxs-lookup"><span data-stu-id="f877c-166">This is a list that contains sub-elements under a bullet item.</span></span>

- <span data-ttu-id="f877c-167">Primo elemento punto elenco</span><span class="sxs-lookup"><span data-stu-id="f877c-167">First bullet item</span></span>

  <span data-ttu-id="f877c-168">Frase che spiega il primo punto elenco.</span><span class="sxs-lookup"><span data-stu-id="f877c-168">Sentence explaining the first bullet.</span></span>

  - <span data-ttu-id="f877c-169">Sottoelemento punto elenco</span><span class="sxs-lookup"><span data-stu-id="f877c-169">Sub-bullet item</span></span>

    <span data-ttu-id="f877c-170">Frase che spiega il sottoelemento punto elenco.</span><span class="sxs-lookup"><span data-stu-id="f877c-170">Sentence explaining the sub-bullet.</span></span>

- <span data-ttu-id="f877c-171">Secondo elemento punto elenco</span><span class="sxs-lookup"><span data-stu-id="f877c-171">Second bullet item</span></span>
- <span data-ttu-id="f877c-172">Terzo elemento punto elenco</span><span class="sxs-lookup"><span data-stu-id="f877c-172">Third bullet item</span></span>

#### <a name="ordered-lists"></a><span data-ttu-id="f877c-173">Elenchi ordinati</span><span class="sxs-lookup"><span data-stu-id="f877c-173">Ordered lists</span></span>

<span data-ttu-id="f877c-174">Per includere un paragrafo o altri elementi sotto un elemento numerato, allineare il rientro con il primo carattere dopo il numero dell'elemento.</span><span class="sxs-lookup"><span data-stu-id="f877c-174">To include a paragraph or other elements under a numbered item, align indentation with the first character after the item number.</span></span> <span data-ttu-id="f877c-175">Tutti gli elementi di un elenco numerato devono usare il numero `1.` anziché incrementare ogni elemento.</span><span class="sxs-lookup"><span data-stu-id="f877c-175">All items in a numbered listed should use the number `1.` rather than incrementing each item.</span></span> <span data-ttu-id="f877c-176">Il rendering di Markdown incrementa automaticamente il valore.</span><span class="sxs-lookup"><span data-stu-id="f877c-176">Markdown rendering increments the value automatically.</span></span> <span data-ttu-id="f877c-177">Questo semplifica il riordino degli elementi e standardizza il rientro del contenuto subordinato.</span><span class="sxs-lookup"><span data-stu-id="f877c-177">This makes reordering items easier and standardizes the indentation of subordinate content.</span></span>

<span data-ttu-id="f877c-178">Ad esempio:</span><span class="sxs-lookup"><span data-stu-id="f877c-178">For example:</span></span>

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

<span data-ttu-id="f877c-179">Il testo Markdown risultante viene restituito come segue:</span><span class="sxs-lookup"><span data-stu-id="f877c-179">The resulting Markdown is rendered as follows:</span></span>

1. <span data-ttu-id="f877c-180">Per il primo elemento inserire uno spazio singolo dopo 1.</span><span class="sxs-lookup"><span data-stu-id="f877c-180">For the first element, insert a single space after the 1.</span></span> <span data-ttu-id="f877c-181">Le frasi lunghe vanno mandate a capo alla riga successiva e devono essere allineate con il primo carattere dopo il marcatore di elenco numerato.</span><span class="sxs-lookup"><span data-stu-id="f877c-181">Long sentences should be wrapped to the next line and must line up with the first character after the numbered list marker.</span></span>

   <span data-ttu-id="f877c-182">Per includere un secondo elemento (come questo), inserire un'interruzione di riga dopo il primo elemento e allineare i rientri.</span><span class="sxs-lookup"><span data-stu-id="f877c-182">To include a second element (like this one), insert a line break after the first and align indentations.</span></span> <span data-ttu-id="f877c-183">Il rientro del secondo elemento deve essere allineato con il primo carattere dopo il marcatore dell'elenco numerato.</span><span class="sxs-lookup"><span data-stu-id="f877c-183">The indentation of the second element must line up with the first character after the numbered list marker.</span></span> <span data-ttu-id="f877c-184">Per gli elementi a cifra singola come questo, si applica un rientro alla colonna 4.</span><span class="sxs-lookup"><span data-stu-id="f877c-184">For single digit items, like this one, you indent to column 4.</span></span> <span data-ttu-id="f877c-185">Per gli elementi a doppia cifra, ad esempio l'elemento numero 10, si applica un rientro alla colonna 5.</span><span class="sxs-lookup"><span data-stu-id="f877c-185">For double digits items, for example item number 10, you indent to column 5.</span></span>

1. <span data-ttu-id="f877c-186">Il successivo elemento numerato inizia qui.</span><span class="sxs-lookup"><span data-stu-id="f877c-186">The next numbered item starts here.</span></span>

### <a name="images"></a><span data-ttu-id="f877c-187">Immagini</span><span class="sxs-lookup"><span data-stu-id="f877c-187">Images</span></span>

<span data-ttu-id="f877c-188">La sintassi per includere un'immagine è la seguente:</span><span class="sxs-lookup"><span data-stu-id="f877c-188">The syntax to include an image is:</span></span>

```markdown
![[alt text]](<folderPath>)

Example:
![Introduction](./media/overview/Introduction.png)
```

<span data-ttu-id="f877c-189">`alt text` è una breve descrizione dell'immagine e `<folder path>` è un percorso relativo all'immagine.</span><span class="sxs-lookup"><span data-stu-id="f877c-189">Where `alt text` is a brief description of the image and `<folder path>` is a relative path to the image.</span></span> <span data-ttu-id="f877c-190">È necessario testo alternativo per le utilità per la lettura dello schermo destinate a utenti con problemi visivi.</span><span class="sxs-lookup"><span data-stu-id="f877c-190">Alternate text is required for screen readers for the visually impaired.</span></span> <span data-ttu-id="f877c-191">Tale testo è utile anche quando a causa di un bug del sito non è possibile eseguire il rendering dell'immagine.</span><span class="sxs-lookup"><span data-stu-id="f877c-191">It is also useful in case there is a site bug where the image cannot be rendered.</span></span>

<span data-ttu-id="f877c-192">Le immagini devono essere archiviate in una cartella `media/<article-name>` all'interno della cartella che contiene l'articolo.</span><span class="sxs-lookup"><span data-stu-id="f877c-192">Images should be stored in a `media/<article-name>` folder within the folder containing the article.</span></span>
<span data-ttu-id="f877c-193">Le immagini non devono essere condivise tra gli articoli.</span><span class="sxs-lookup"><span data-stu-id="f877c-193">Images should not be shared between articles.</span></span> <span data-ttu-id="f877c-194">Creare una cartella corrispondente al nome file dell'articolo sotto la cartella `media`.</span><span class="sxs-lookup"><span data-stu-id="f877c-194">Create a folder that matches the filename of your article under the `media` folder.</span></span> <span data-ttu-id="f877c-195">Copiare le immagini per l'articolo nella nuova cartella.</span><span class="sxs-lookup"><span data-stu-id="f877c-195">Copy the images for that article to that new folder.</span></span> <span data-ttu-id="f877c-196">Se un'immagine viene usata da più articoli, ogni cartella di immagini deve avere una copia di quel file di immagine.</span><span class="sxs-lookup"><span data-stu-id="f877c-196">If an image is used by multiple articles, each image folder must have a copy of that image file.</span></span> <span data-ttu-id="f877c-197">Questa procedura impedisce che la modifica di un'immagine in un articolo abbia effetto su un altro articolo.</span><span class="sxs-lookup"><span data-stu-id="f877c-197">This practice prevents a change to an image in one article affecting another article.</span></span>

<span data-ttu-id="f877c-198">Sono supportati i tipi di file immagine seguenti: `*.png`, `*.gif`, `*.jpeg`, `*.jpg`, `*.svg`</span><span class="sxs-lookup"><span data-stu-id="f877c-198">The following image file types are supported: `*.png`, `*.gif`, `*.jpeg`, `*.jpg`, `*.svg`</span></span>

### <a name="markdown-extensions-supported-by-open-publishing"></a><span data-ttu-id="f877c-199">Estensioni Markdown supportate da Open Publishing</span><span class="sxs-lookup"><span data-stu-id="f877c-199">Markdown extensions supported by Open Publishing</span></span>

<span data-ttu-id="f877c-200">[Microsoft Docs Authoring Pack](/contribute/how-to-write-docs-auth-pack) contiene strumenti che supportano funzionalità specifiche del sistema di pubblicazione.</span><span class="sxs-lookup"><span data-stu-id="f877c-200">The [Microsoft Docs Authoring Pack](/contribute/how-to-write-docs-auth-pack) contains tools that support features unique to our publishing system.</span></span> <span data-ttu-id="f877c-201">Gli avvisi sono un'estensione Markdown per la creazione di citazioni di cui viene eseguito il rendering in docs.microsoft.com con colori e icone che evidenziano il significato del contenuto.</span><span class="sxs-lookup"><span data-stu-id="f877c-201">Alerts are a Markdown extension to create blockquotes that render on docs.microsoft.com with colors and icons that highlight the significance of the content.</span></span> <span data-ttu-id="f877c-202">Sono supportati i tipi di avviso seguenti:</span><span class="sxs-lookup"><span data-stu-id="f877c-202">The following alert types are supported:</span></span>

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

<span data-ttu-id="f877c-203">Questi avvisi hanno un aspetto simile al seguente in docs.microsoft.com:</span><span class="sxs-lookup"><span data-stu-id="f877c-203">These alerts look like this on docs.microsoft.com:</span></span>

<span data-ttu-id="f877c-204">Blocco Nota</span><span class="sxs-lookup"><span data-stu-id="f877c-204">Note block</span></span>

> [!NOTE]
> <span data-ttu-id="f877c-205">Informazioni che l'utente deve notare anche in una consultazione veloce.</span><span class="sxs-lookup"><span data-stu-id="f877c-205">Information the user should notice even if skimming.</span></span>

<span data-ttu-id="f877c-206">Blocco Suggerimento</span><span class="sxs-lookup"><span data-stu-id="f877c-206">Tip block</span></span>

> [!TIP]
> <span data-ttu-id="f877c-207">Informazioni facoltative che consentono a un utente di ottenere risultati più efficaci.</span><span class="sxs-lookup"><span data-stu-id="f877c-207">Optional information to help a user be more successful.</span></span>

<span data-ttu-id="f877c-208">Blocco Importante</span><span class="sxs-lookup"><span data-stu-id="f877c-208">Important block</span></span>

> [!IMPORTANT]
> <span data-ttu-id="f877c-209">Informazioni essenziali necessarie per l'esito positivo.</span><span class="sxs-lookup"><span data-stu-id="f877c-209">Essential information required for user success.</span></span>

<span data-ttu-id="f877c-210">Blocco Attenzione</span><span class="sxs-lookup"><span data-stu-id="f877c-210">Caution block</span></span>

> [!CAUTION]
> <span data-ttu-id="f877c-211">Potenziali conseguenze negative di un'azione.</span><span class="sxs-lookup"><span data-stu-id="f877c-211">Negative potential consequences of an action.</span></span>

<span data-ttu-id="f877c-212">Blocco Avviso</span><span class="sxs-lookup"><span data-stu-id="f877c-212">Warning block</span></span>

> [!WARNING]
> <span data-ttu-id="f877c-213">Conseguenze pericolose certe di un'azione.</span><span class="sxs-lookup"><span data-stu-id="f877c-213">Dangerous certain consequences of an action.</span></span>

### <a name="hyperlinks"></a><span data-ttu-id="f877c-214">Collegamenti ipertestuali</span><span class="sxs-lookup"><span data-stu-id="f877c-214">Hyperlinks</span></span>

- <span data-ttu-id="f877c-215">I collegamenti ipertestuali devono usare la sintassi Markdown `[friendlyname](url-or-path)`</span><span class="sxs-lookup"><span data-stu-id="f877c-215">Hyperlinks must use Markdown syntax `[friendlyname](url-or-path)`</span></span>
- <span data-ttu-id="f877c-216">Se possibile, i collegamenti devono essere di tipo HTTPS.</span><span class="sxs-lookup"><span data-stu-id="f877c-216">Links should be HTTPS when possible.</span></span>
- <span data-ttu-id="f877c-217">I collegamenti devono avere un nome descrittivo, in genere il titolo dell'argomento collegato</span><span class="sxs-lookup"><span data-stu-id="f877c-217">Links must have a friendly name, usually the title of the linked topic</span></span>
- <span data-ttu-id="f877c-218">Tutti gli elementi nella sezione "Collegamenti correlati" alla fine degli articoli devono essere impostati come collegamenti ipertestuali</span><span class="sxs-lookup"><span data-stu-id="f877c-218">All items in the "related links" section at the bottom should be hyperlinked</span></span>
- <span data-ttu-id="f877c-219">Non usare accenti gravi, grassetto o altri elementi di markup all'interno delle parentesi quadre di un collegamento ipertestuale.</span><span class="sxs-lookup"><span data-stu-id="f877c-219">Do not use backticks, bold, or other markup inside the brackets of a hyperlink.</span></span>
- <span data-ttu-id="f877c-220">Quando si parla di un URI specifico, è possibile usare URL semplici.</span><span class="sxs-lookup"><span data-stu-id="f877c-220">Bare URLs may be used when you are talking about a specific URI.</span></span> <span data-ttu-id="f877c-221">L'URI deve essere racchiuso tra apici inversi.</span><span class="sxs-lookup"><span data-stu-id="f877c-221">The URI must be enclosed in backticks.</span></span> <span data-ttu-id="f877c-222">Ad esempio:</span><span class="sxs-lookup"><span data-stu-id="f877c-222">For example:</span></span>

  ```markdown
  By default, if you do not specify this parameter, the DMTF standard resource URI
  `http://schemas.dmtf.org/wbem/wscim/1/cim-schema/2/` is used and the class name is appended to it.
  ```

#### <a name="linking-to-other-content"></a><span data-ttu-id="f877c-223">Collegamento a contenuto diverso</span><span class="sxs-lookup"><span data-stu-id="f877c-223">Linking to other content</span></span>

<span data-ttu-id="f877c-224">Il sistema di pubblicazione supporta due tipi di collegamenti ipertestuali:</span><span class="sxs-lookup"><span data-stu-id="f877c-224">There are two types of hyperlinks supported by the publishing system:</span></span>

<span data-ttu-id="f877c-225">Un **collegamento URL** può essere un percorso URL relativo alla radice docs.microsoft.com.</span><span class="sxs-lookup"><span data-stu-id="f877c-225">A **URL link** can be a URL path that is relative to the root of docs.microsoft.com.</span></span> <span data-ttu-id="f877c-226">Oppure può essere un URL assoluto, che include la sintassi completa dell'URL.</span><span class="sxs-lookup"><span data-stu-id="f877c-226">Or an absolute URL that include the full URL syntax.</span></span> <span data-ttu-id="f877c-227">Ad esempio: `https:/github.com/MicrosoftDocs/PowerShell-Docs`</span><span class="sxs-lookup"><span data-stu-id="f877c-227">For example: `https:/github.com/MicrosoftDocs/PowerShell-Docs`</span></span>

- <span data-ttu-id="f877c-228">Usare i collegamenti URL per il collegamento a contenuto esterno a PowerShell-Docs o il collegamento tra riferimenti ai cmdlet e articoli concettuali in PowerShell-Docs. Il modo più semplice per creare un collegamento relativo consiste nel copiare l'URL dal browser e quindi rimuovere `https://docs.microsoft.com/en-us` dal valore incollato in Markdown.</span><span class="sxs-lookup"><span data-stu-id="f877c-228">Use URL links when linking to content outside of PowerShell-Docs or between cmdlet reference and conceptual articles within PowerShell-docs. The simplest way to create a relative link is to copy the URL from your browser then remove `https://docs.microsoft.com/en-us` from the value you paste into markdown.</span></span>
- <span data-ttu-id="f877c-229">Non includere le impostazioni locali negli URL nelle proprietà Microsoft (ad esempio,</span><span class="sxs-lookup"><span data-stu-id="f877c-229">Do not include locales in URLs on Microsoft properties (eg.</span></span> <span data-ttu-id="f877c-230">rimuovere `/en-us` dall'URL).</span><span class="sxs-lookup"><span data-stu-id="f877c-230">remove `/en-us` from URL).</span></span>
- <span data-ttu-id="f877c-231">Rimuovere dall'URL tutti i parametri di query non necessari, a meno che non sia necessario creare un collegamento a una versione specifica di un articolo.</span><span class="sxs-lookup"><span data-stu-id="f877c-231">Remove any unnecessary query parameters from the URL unless you need to link to a specific version of an article.</span></span> <span data-ttu-id="f877c-232">Esempi:</span><span class="sxs-lookup"><span data-stu-id="f877c-232">Examples:</span></span>
  - <span data-ttu-id="f877c-233">`?view=powershell-5.1` - Parametro usato in un collegamento a una versione specifica di PowerShell</span><span class="sxs-lookup"><span data-stu-id="f877c-233">`?view=powershell-5.1` - this is used to link to a specific version of PowerShell</span></span>
  - <span data-ttu-id="f877c-234">`?redirectedfrom=MSDN` - Parametro aggiunto all'URL per il reindirizzamento dalla vecchia versione di un vecchio articolo alla nuova posizione di questo</span><span class="sxs-lookup"><span data-stu-id="f877c-234">`?redirectedfrom=MSDN` - this is added to the URL when you get redirected from an old article to its new location</span></span>
- <span data-ttu-id="f877c-235">Tutti gli URL che puntano a siti Web esterni devono usare HTTPS, a meno che ciò non sia valido per il sito di destinazione.</span><span class="sxs-lookup"><span data-stu-id="f877c-235">All URLs to external websites should use HTTPS unless that is not valid for the target site.</span></span>

<span data-ttu-id="f877c-236">Un **collegamento file** viene usato per collegare un articolo di riferimento a un altro o un articolo concettuale a un altro.</span><span class="sxs-lookup"><span data-stu-id="f877c-236">A **file link** is used to link from one reference article to another, or from one conceptual article to another.</span></span> <span data-ttu-id="f877c-237">Per creare un collegamento a un articolo di riferimento per una versione specifica di PowerShell, è necessario usare un collegamento URL.</span><span class="sxs-lookup"><span data-stu-id="f877c-237">If you need to link to a reference article for a specific version of PowerShell, then you must use a URL link.</span></span>

- <span data-ttu-id="f877c-238">I collegamenti file contengono un percorso di file relativo (ad esempio: `../folder/file.md`)</span><span class="sxs-lookup"><span data-stu-id="f877c-238">File links contain a relative file path (for example: `../folder/file.md`)</span></span>
- <span data-ttu-id="f877c-239">Tutti i percorsi di file usano caratteri barra (`/`)</span><span class="sxs-lookup"><span data-stu-id="f877c-239">All file paths use forward-slash (`/`) characters</span></span>

<span data-ttu-id="f877c-240">Sono consentite operazioni di deep linking sia negli URL che nei collegamenti file.</span><span class="sxs-lookup"><span data-stu-id="f877c-240">Deep linking is allowed on both URL and file links.</span></span> <span data-ttu-id="f877c-241">Aggiungere l'ancoraggio alla fine del percorso di destinazione.</span><span class="sxs-lookup"><span data-stu-id="f877c-241">Add the anchor to the end of the target path.</span></span>
<span data-ttu-id="f877c-242">Ad esempio:</span><span class="sxs-lookup"><span data-stu-id="f877c-242">For example:</span></span>

- `[about_Splatting](about_Splatting.md#splatting-with-arrays)`
- `[custom key bindings](https://code.visualstudio.com/docs/getstarted/keybindings#_custom-keybindings-for-refactorings)`

<span data-ttu-id="f877c-243">Per altre informazioni, vedere [Usare collegamenti nella documentazione](https://docs.microsoft.com/contribute/how-to-write-links).</span><span class="sxs-lookup"><span data-stu-id="f877c-243">For more information, see [Use links in documentation](https://docs.microsoft.com/contribute/how-to-write-links).</span></span>

## <a name="formatting-command-syntax-elements"></a><span data-ttu-id="f877c-244">Formattazione degli elementi della sintassi del comando</span><span class="sxs-lookup"><span data-stu-id="f877c-244">Formatting command syntax elements</span></span>

- <span data-ttu-id="f877c-245">Usare sempre il nome completo per i cmdlet e i parametri.</span><span class="sxs-lookup"><span data-stu-id="f877c-245">Always use the full name for cmdlets and parameters.</span></span> <span data-ttu-id="f877c-246">Evitare di usare alias, a meno che non si stia dimostrando in modo specifico l'alias.</span><span class="sxs-lookup"><span data-stu-id="f877c-246">Avoid using aliases unless you are specifically demonstrating the alias.</span></span>

- <span data-ttu-id="f877c-247">Proprietà, parametri, oggetti, nomi di tipi, nomi di classi e metodi di classe devono essere in **grassetto**.</span><span class="sxs-lookup"><span data-stu-id="f877c-247">Property, parameter, object, type names, class names, class methods should be **bold**.</span></span>
  - <span data-ttu-id="f877c-248">I valori delle proprietà e dei parametri devono essere racchiusi tra apici inversi (`` ` ``).</span><span class="sxs-lookup"><span data-stu-id="f877c-248">Property and parameter values should be wrapped in backticks (`` ` ``).</span></span>
  - <span data-ttu-id="f877c-249">Quando si fa riferimento a tipi racchiudendoli tra parentesi quadre, usare apici inversi.</span><span class="sxs-lookup"><span data-stu-id="f877c-249">When referring to types using the bracketed style, use backticks.</span></span> <span data-ttu-id="f877c-250">Ad esempio: `[System.Io.FileInfo]`</span><span class="sxs-lookup"><span data-stu-id="f877c-250">For example: `[System.Io.FileInfo]`</span></span>

- <span data-ttu-id="f877c-251">Le parole chiave del linguaggio, i nomi dei cmdlet, le funzioni, le variabili, i file EXE nativi, i percorsi di file e gli esempi di sintassi inline devono essere racchiusi tra apici inversi (`` ` ``).</span><span class="sxs-lookup"><span data-stu-id="f877c-251">Language keywords, cmdlet names, functions, variables, native EXEs, file paths, and inline syntax examples should be wrapped in backtick (`` ` ``) characters.</span></span>

  <span data-ttu-id="f877c-252">Ad esempio:</span><span class="sxs-lookup"><span data-stu-id="f877c-252">For example:</span></span>

  ~~~markdown
  The following code uses `Get-ChildItem` to list the contents of `C:\Windows` and assigns
  the output to the `$files` variable.

  ```powershell
  $files = Get-ChildItem C:\Windows
  ```
  ~~~

  - <span data-ttu-id="f877c-253">Quando si fa riferimento a un parametro con il nome, questo deve essere in **grassetto**.</span><span class="sxs-lookup"><span data-stu-id="f877c-253">When referring to a parameter by name, the name should be **bold**.</span></span> <span data-ttu-id="f877c-254">Quando si illustra l'uso di un parametro con il prefisso trattino, il parametro deve essere racchiuso tra caratteri accento grave.</span><span class="sxs-lookup"><span data-stu-id="f877c-254">When illustrating the use of a parameter with the hyphen prefix, the parameter should be wrapped in backticks.</span></span> <span data-ttu-id="f877c-255">Ad esempio:</span><span class="sxs-lookup"><span data-stu-id="f877c-255">For example:</span></span>

    ```markdown
    The parameter's name is **Name**, but it is typed as `-Name` when used on the command
    line as a parameter.
    ```

  - <span data-ttu-id="f877c-256">Quando si visualizza un esempio d'uso di un comando esterno, l'esempio deve essere racchiuso tra caratteri accento grave.</span><span class="sxs-lookup"><span data-stu-id="f877c-256">When showing example usage of an external command, the example should be wrapped in backticks.</span></span>
    <span data-ttu-id="f877c-257">Includere sempre l'estensione file nel comando nativo.</span><span class="sxs-lookup"><span data-stu-id="f877c-257">Always include the file extension in the native command.</span></span> <span data-ttu-id="f877c-258">Ad esempio:</span><span class="sxs-lookup"><span data-stu-id="f877c-258">For example:</span></span>

    ```markdown
    To start the spooler service on a remote computer named DC01, you type `sc.exe \\DC01 start spooler`.
    ```

    <span data-ttu-id="f877c-259">In questo modo ci si assicura che venga eseguito il comando corretto in base alle regole di precedenza dei comandi di PowerShell.</span><span class="sxs-lookup"><span data-stu-id="f877c-259">Including the file extension ensures that the correct command is executed according PowerShell's command precedence.</span></span>

- <span data-ttu-id="f877c-260">Durante la scrittura di un articolo concettuale (diversamente dal contenuto di riferimento), la prima istanza del nome di un cmdlet deve essere un collegamento alla documentazione del cmdlet.</span><span class="sxs-lookup"><span data-stu-id="f877c-260">When writing a conceptual article (as opposed to reference content), the first instance of a cmdlet name should be hyperlinked to the cmdlet documentation.</span></span> <span data-ttu-id="f877c-261">Non usare accenti gravi, grassetto o altri elementi di markup all'interno delle parentesi quadre di un collegamento ipertestuale.</span><span class="sxs-lookup"><span data-stu-id="f877c-261">Do not use backticks, bold, or other markup inside the brackets of a hyperlink.</span></span>

  <span data-ttu-id="f877c-262">Ad esempio:</span><span class="sxs-lookup"><span data-stu-id="f877c-262">For example:</span></span>

  ```markdown
  This [Write-Host](/powershell/module/Microsoft.PowerShell.Utility/Write-Host) cmdlet
  uses the **Object** parameter to ...
  ```

  <span data-ttu-id="f877c-263">Per altre informazioni, vedere la sezione [Collegamenti ipertestuali](#hyperlinks) di questo articolo.</span><span class="sxs-lookup"><span data-stu-id="f877c-263">For more information, see [Hyperlinks](#hyperlinks) section of this article.</span></span>

## <a name="markdown-for-code-samples"></a><span data-ttu-id="f877c-264">Markdown per esempi di codice</span><span class="sxs-lookup"><span data-stu-id="f877c-264">Markdown for code samples</span></span>

<span data-ttu-id="f877c-265">Markdown supporta due stili di codice:</span><span class="sxs-lookup"><span data-stu-id="f877c-265">Markdown supports two different code styles:</span></span>

- <span data-ttu-id="f877c-266">**Intervalli di codice (inline)** - Contrassegnati da un singolo carattere apice inverso (`` ` ``).</span><span class="sxs-lookup"><span data-stu-id="f877c-266">**Code spans (inline)** - marked by a single backtick (`` ` ``) character.</span></span> <span data-ttu-id="f877c-267">Sono usati all'interno di un paragrafo anziché come blocchi autonomi.</span><span class="sxs-lookup"><span data-stu-id="f877c-267">Used within a paragraph rather than as a standalone block.</span></span>
- <span data-ttu-id="f877c-268">**Blocchi di codice** - Blocchi a più righe racchiusi fra stringhe costituite da un triplo apice inverso (`` ``` ``).</span><span class="sxs-lookup"><span data-stu-id="f877c-268">**Code blocks** - a multi-line block surrounded by triple-backtick (`` ``` ``) strings.</span></span> <span data-ttu-id="f877c-269">I blocchi di codice possono anche avere un'etichetta di linguaggio dopo i caratteri accento grave.</span><span class="sxs-lookup"><span data-stu-id="f877c-269">Code blocks may also have a language label following the backticks.</span></span> <span data-ttu-id="f877c-270">L'etichetta di linguaggio consente l'evidenziazione della sintassi per il contenuto del blocco di codice.</span><span class="sxs-lookup"><span data-stu-id="f877c-270">The language label enables syntax highlighting for the contents of the code block.</span></span>

<span data-ttu-id="f877c-271">Tutti i blocchi di codice devono essere inclusi in un intervallo di codice.</span><span class="sxs-lookup"><span data-stu-id="f877c-271">All code blocks should be contained in a code fence.</span></span> <span data-ttu-id="f877c-272">Non usare mai rientri per i blocchi di codice.</span><span class="sxs-lookup"><span data-stu-id="f877c-272">Never use indentation for code blocks.</span></span> <span data-ttu-id="f877c-273">Il linguaggio Markdown le consente, ma possono creare problemi e devono essere evitati.</span><span class="sxs-lookup"><span data-stu-id="f877c-273">Markdown allows this pattern but it can be problematic and should be avoided.</span></span>

<span data-ttu-id="f877c-274">Un blocco di codice è costituito da una o più righe di codice comprese in un intervallo di codice racchiuso tra caratteri triplo apice inverso (`` ``` ``).</span><span class="sxs-lookup"><span data-stu-id="f877c-274">A code block is one or more lines of code surrounded by a triple-backtick (`` ``` ``) code fence.</span></span>
<span data-ttu-id="f877c-275">I marcatori dell'intervallo di codice devono trovarsi su una riga a parte, prima e dopo l'esempio di codice.</span><span class="sxs-lookup"><span data-stu-id="f877c-275">The code fence markers must be on their own line before and after the code sample.</span></span> <span data-ttu-id="f877c-276">Il marcatore all'inizio del blocco di codice può avere un'etichetta del linguaggio facoltativa.</span><span class="sxs-lookup"><span data-stu-id="f877c-276">The marker at the start of the code block may have an optional language label.</span></span> <span data-ttu-id="f877c-277">Microsoft Open Publishing System (OPS) usa l'etichetta del linguaggio per supportare la funzionalità di evidenziazione della sintassi.</span><span class="sxs-lookup"><span data-stu-id="f877c-277">Microsoft's Open Publishing System (OPS) uses the language label to support the syntax highlighting feature.</span></span>

<span data-ttu-id="f877c-278">Per l'elenco completo dei tag supportati dal linguaggio, vedere [Blocchi di codice delimitati](/contribute/code-in-docs#fenced-code-blocks) nella guida per i collaboratori centralizzata.</span><span class="sxs-lookup"><span data-stu-id="f877c-278">For a full list of supported language tags, see [Fenced code blocks](/contribute/code-in-docs#fenced-code-blocks) in the centralized contributor guide.</span></span>

<span data-ttu-id="f877c-279">OPS aggiunge anche un pulsante **Copy** (Copia) che copia il contenuto del blocco di codice negli Appunti.</span><span class="sxs-lookup"><span data-stu-id="f877c-279">OPS also adds a **Copy** button that copies the contents of the code block to the clipboard.</span></span> <span data-ttu-id="f877c-280">In questo modo è possibile incollare rapidamente il codice in uno script per eseguire il test dell'esempio di codice.</span><span class="sxs-lookup"><span data-stu-id="f877c-280">This allows you to quickly paste the code into a script to test the code sample.</span></span> <span data-ttu-id="f877c-281">Non tutti gli esempi nella documentazione, tuttavia, sono destinati a essere eseguiti così come sono.</span><span class="sxs-lookup"><span data-stu-id="f877c-281">However, not all examples in our documentation are intended to be run as-is.</span></span> <span data-ttu-id="f877c-282">Alcuni blocchi di codice sono semplici illustrazioni di un concetto di PowerShell.</span><span class="sxs-lookup"><span data-stu-id="f877c-282">Some code blocks are simple illustrations of a PowerShell concept.</span></span>

<span data-ttu-id="f877c-283">Nella documentazione vengono usati tre tipi di blocchi di codice:</span><span class="sxs-lookup"><span data-stu-id="f877c-283">There are three types code blocks used in our documentation:</span></span>

1. <span data-ttu-id="f877c-284">Blocchi di sintassi</span><span class="sxs-lookup"><span data-stu-id="f877c-284">Syntax blocks</span></span>
1. <span data-ttu-id="f877c-285">Esempi illustrativi</span><span class="sxs-lookup"><span data-stu-id="f877c-285">Illustrative examples</span></span>
1. <span data-ttu-id="f877c-286">Esempi eseguibili</span><span class="sxs-lookup"><span data-stu-id="f877c-286">Executable examples</span></span>

### <a name="syntax-code-blocks"></a><span data-ttu-id="f877c-287">Blocchi di codice di sintassi</span><span class="sxs-lookup"><span data-stu-id="f877c-287">Syntax code blocks</span></span>

<span data-ttu-id="f877c-288">I blocchi di codice di sintassi vengono usati per descrivere la struttura sintattica di un comando.</span><span class="sxs-lookup"><span data-stu-id="f877c-288">Syntax code blocks are used to describe the syntactic structure of a command.</span></span> <span data-ttu-id="f877c-289">Non usare un tag di linguaggio nella delimitazione del codice.</span><span class="sxs-lookup"><span data-stu-id="f877c-289">Do not use a language tag on the code fence.</span></span> <span data-ttu-id="f877c-290">Questo esempio illustra tutti i possibili parametri del cmdlet `Get-Command`.</span><span class="sxs-lookup"><span data-stu-id="f877c-290">This example illustrates all the possible parameters of the `Get-Command` cmdlet.</span></span>

~~~markdown
```
Get-Command [-Verb <String[]>] [-Noun <String[]>] [-Module <String[]>]
  [-FullyQualifiedModule <ModuleSpecification[]>] [-TotalCount <Int32>] [-Syntax]
  [-ShowCommandInfo] [[-ArgumentList] <Object[]>] [-All] [-ListImported]
  [-ParameterName <String[]>] [-ParameterType <PSTypeName[]>] [<CommonParameters>]
```
~~~

<span data-ttu-id="f877c-291">Questo esempio illustra l'istruzione `for` in termini generici:</span><span class="sxs-lookup"><span data-stu-id="f877c-291">This example describes the `for` statement in generalized terms:</span></span>

~~~markdown
```
for (<init>; <condition>; <repeat>)
{<statement list>}
```
~~~

### <a name="illustrative-examples"></a><span data-ttu-id="f877c-292">Esempi illustrativi</span><span class="sxs-lookup"><span data-stu-id="f877c-292">Illustrative examples</span></span>

<span data-ttu-id="f877c-293">Gli esempi illustrativi vengono usati per descrivere un concetto di PowerShell.</span><span class="sxs-lookup"><span data-stu-id="f877c-293">Illustrative examples are used to explain a PowerShell concept.</span></span> <span data-ttu-id="f877c-294">Non sono pensati per essere copiati negli Appunti per l'esecuzione.</span><span class="sxs-lookup"><span data-stu-id="f877c-294">They are not meant to be copied to the clipboard for execution.</span></span> <span data-ttu-id="f877c-295">Vengono usati soprattutto per esempi semplici, facili da digitare e da comprendere.</span><span class="sxs-lookup"><span data-stu-id="f877c-295">These are most commonly used for simple examples that are easy to type and easy to understand.</span></span> <span data-ttu-id="f877c-296">Un blocco di codice può includere il prompt di PowerShell e output di esempio.</span><span class="sxs-lookup"><span data-stu-id="f877c-296">The code block can include the PowerShell prompt and example output.</span></span>

<span data-ttu-id="f877c-297">Ecco un esempio semplice che illustra gli operatori di confronto di PowerShell.</span><span class="sxs-lookup"><span data-stu-id="f877c-297">Here is a simple example illustrating the PowerShell comparison operators.</span></span> <span data-ttu-id="f877c-298">In questo caso, non è previsto che l'utente copi ed esegua l'esempio.</span><span class="sxs-lookup"><span data-stu-id="f877c-298">In this case, we don't intend the reader to copy and run this example.</span></span>

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

### <a name="executable-examples"></a><span data-ttu-id="f877c-299">Esempi eseguibili</span><span class="sxs-lookup"><span data-stu-id="f877c-299">Executable examples</span></span>

<span data-ttu-id="f877c-300">Gli esempi complessi o quelli destinati a essere copiati e incollati per l'esecuzione devono usare il markup di stile del blocco seguente:</span><span class="sxs-lookup"><span data-stu-id="f877c-300">Complex examples, or examples that are intended to be copied and executed, should use the following block-style markup:</span></span>

~~~markdown
```powershell
<Your PowerShell code goes here>
```
~~~

<span data-ttu-id="f877c-301">L'output visualizzato dai comandi di PowerShell deve essere racchiuso in un blocco di codice **Output** per evitare l'evidenziazione della sintassi.</span><span class="sxs-lookup"><span data-stu-id="f877c-301">The output displayed by PowerShell commands should be enclosed in an **Output** code block to prevent syntax highlighting.</span></span> <span data-ttu-id="f877c-302">Ad esempio:</span><span class="sxs-lookup"><span data-stu-id="f877c-302">For example:</span></span>

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

<span data-ttu-id="f877c-303">L'etichetta del codice **Output** non corrisponde a un "linguaggio" ufficiale supportato dal sistema di evidenziazione della sintassi.</span><span class="sxs-lookup"><span data-stu-id="f877c-303">The **Output** code label is not an official "language" supported by the syntax highlighting system.</span></span>
<span data-ttu-id="f877c-304">Questa etichetta è tuttavia utile perché OPS aggiunge l'etichetta "Output" al frame della casella di codice nella pagina Web.</span><span class="sxs-lookup"><span data-stu-id="f877c-304">However, this label is useful because OPS adds the "Output" label to the code box frame on the web page.</span></span> <span data-ttu-id="f877c-305">La casella di codice "Output" non presenta l'evidenziazione della sintassi.</span><span class="sxs-lookup"><span data-stu-id="f877c-305">The "Output" code box has no syntax highlighting.</span></span>

## <a name="coding-style-rules"></a><span data-ttu-id="f877c-306">Regole dello stile di codifica</span><span class="sxs-lookup"><span data-stu-id="f877c-306">Coding style rules</span></span>

### <a name="avoid-line-continuation-in-code-samples"></a><span data-ttu-id="f877c-307">Evitare la continuazione di riga negli esempi di codice</span><span class="sxs-lookup"><span data-stu-id="f877c-307">Avoid line continuation in code samples</span></span>

<span data-ttu-id="f877c-308">Evitare di usare i caratteri di continuazione di riga (`` ` ``) negli esempi di codice PowerShell.</span><span class="sxs-lookup"><span data-stu-id="f877c-308">Avoid using line continuation characters (`` ` ``) in PowerShell code examples.</span></span> <span data-ttu-id="f877c-309">Questi caratteri sono difficili da visualizzare e possono causare problemi se alla fine della riga sono presenti spazi aggiuntivi.</span><span class="sxs-lookup"><span data-stu-id="f877c-309">These are hard to see and can cause problems if there are extra spaces at the end of the line.</span></span>

- <span data-ttu-id="f877c-310">Usare lo splatting di PowerShell per ridurre la lunghezza della riga per i cmdlet che hanno numerosi parametri.</span><span class="sxs-lookup"><span data-stu-id="f877c-310">Use PowerShell splatting to reduce line length for cmdlets that have a lot of parameters.</span></span>
- <span data-ttu-id="f877c-311">Sfruttare i vantaggi delle opportunità naturali di interruzione riga di PowerShell, ad esempio dopo i caratteri pipe (`|`), le parentesi graffe di apertura, le parentesi tonde e le parentesi quadre.</span><span class="sxs-lookup"><span data-stu-id="f877c-311">Take advantage of PowerShell's natural line break opportunities, like after pipe (`|`) characters, opening braces, parentheses, and brackets.</span></span>

### <a name="avoid-using-powershell-prompts-in-examples"></a><span data-ttu-id="f877c-312">Evitare di usare le richieste di PowerShell negli esempi</span><span class="sxs-lookup"><span data-stu-id="f877c-312">Avoid using PowerShell prompts in examples</span></span>

<span data-ttu-id="f877c-313">L'uso della stringa di richiesta è sconsigliato e deve essere limitato agli scenari che hanno lo scopo di illustrare l'uso della riga di comando.</span><span class="sxs-lookup"><span data-stu-id="f877c-313">Use of the prompt string is discouraged and should be limited to scenarios that are meant to illustrate command line usage.</span></span> <span data-ttu-id="f877c-314">Per la maggior parte di questi esempi, la stringa di richiesta dovrebbe essere `PS>`.</span><span class="sxs-lookup"><span data-stu-id="f877c-314">For most of these examples, the prompt string should be `PS>`.</span></span> <span data-ttu-id="f877c-315">Questa richiesta è indipendente dagli indicatori specifici del sistema operativo.</span><span class="sxs-lookup"><span data-stu-id="f877c-315">This prompt is independent of OS-specific indicators.</span></span>

<span data-ttu-id="f877c-316">Le richieste sono necessarie per gli esempi con comandi che modificano la richiesta stessa o quando il percorso visualizzato è significativo per lo scenario illustrato.</span><span class="sxs-lookup"><span data-stu-id="f877c-316">Prompts are required for examples that illustrate commands that alter the prompt or when the path displayed is significant to the scenario being illustrated.</span></span> <span data-ttu-id="f877c-317">L'esempio seguente illustra come viene modificata la richiesta quando si usa il provider del Registro di sistema.</span><span class="sxs-lookup"><span data-stu-id="f877c-317">The following example illustrates how the prompt changes when using the Registry provider.</span></span>

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

### <a name="do-not-use-aliases-in-examples"></a><span data-ttu-id="f877c-318">Non usare alias negli esempi</span><span class="sxs-lookup"><span data-stu-id="f877c-318">Do not use aliases in examples</span></span>

<span data-ttu-id="f877c-319">È consigliabile usare sempre il nome completo di tutti i cmdlet e i parametri, salvo quando si vuole specificare l'alias stesso.</span><span class="sxs-lookup"><span data-stu-id="f877c-319">You should always use the full name of all cmdlets and parameters unless you are specifically talking about the alias.</span></span> <span data-ttu-id="f877c-320">I nomi di cmdlet e parametri devono usare nomi definiti in base alle convenzioni Pascal.</span><span class="sxs-lookup"><span data-stu-id="f877c-320">Cmdlet and parameter names must use the proper Pascal-cased names.</span></span>

### <a name="using-parameters-in-examples"></a><span data-ttu-id="f877c-321">Uso di parametri negli esempi</span><span class="sxs-lookup"><span data-stu-id="f877c-321">Using parameters in examples</span></span>

<span data-ttu-id="f877c-322">Evitare l'uso di parametri posizionali.</span><span class="sxs-lookup"><span data-stu-id="f877c-322">Avoid using positional parameters.</span></span> <span data-ttu-id="f877c-323">È in genere consigliabile includere sempre il nome del parametro in un esempio, anche se il parametro è posizionale.</span><span class="sxs-lookup"><span data-stu-id="f877c-323">In general, you should always include the parameter name in an example, even if the parameter is positional.</span></span> <span data-ttu-id="f877c-324">Questo riduce la possibilità di confusione negli esempi.</span><span class="sxs-lookup"><span data-stu-id="f877c-324">This reduces the chance of confusion in your examples.</span></span>

## <a name="next-steps"></a><span data-ttu-id="f877c-325">Passaggi successivi</span><span class="sxs-lookup"><span data-stu-id="f877c-325">Next steps</span></span>

[<span data-ttu-id="f877c-326">Modifica delle informazioni di riferimento sui cmdlet</span><span class="sxs-lookup"><span data-stu-id="f877c-326">Editing cmdlet reference</span></span>](editing-cmdlet-ref.md)

<!-- External URLs -->
[platyPS]: https://github.com/PowerShell/platyPS
[markdig]: https://github.com/lunet-io/markdig
[CommonMark]: https://spec.commonmark.org/
[atx]: https://github.github.com/gfm/#atx-headings
[pascal-case]: https://en.wikipedia.org/wiki/PascalCase
[reflow]: https://marketplace.visualstudio.com/items?itemName=marvhen.reflow-markdown
