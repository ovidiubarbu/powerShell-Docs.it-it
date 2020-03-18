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
# <a name="powershell-docs-style-guide"></a><span data-ttu-id="4e794-103">Guida di stile per la documentazione di PowerShell</span><span class="sxs-lookup"><span data-stu-id="4e794-103">PowerShell-Docs style guide</span></span>

<span data-ttu-id="4e794-104">Questo articolo è una guida di stile specifica per il contenuto di documentazione di PowerShell.</span><span class="sxs-lookup"><span data-stu-id="4e794-104">This article provides style guidance specific to the PowerShell-Docs content.</span></span> <span data-ttu-id="4e794-105">Le linee guida si basano sulle informazioni incluse nella [Panoramica ](overview.md#get-started-writing-docs).</span><span class="sxs-lookup"><span data-stu-id="4e794-105">This builds on the information outlined in the [Overview](overview.md#get-started-writing-docs).</span></span>

## <a name="product-terminology"></a><span data-ttu-id="4e794-106">Terminologia del prodotto</span><span class="sxs-lookup"><span data-stu-id="4e794-106">Product Terminology</span></span>

<span data-ttu-id="4e794-107">Sono disponibili diverse varianti di PowerShell.</span><span class="sxs-lookup"><span data-stu-id="4e794-107">There are several variants of PowerShell.</span></span>
<span data-ttu-id="4e794-108">Questa tabella definisce alcuni termini usati nel contesto di PowerShell.</span><span class="sxs-lookup"><span data-stu-id="4e794-108">This table defines some of the different terms used to discuss PowerShell.</span></span>

- <span data-ttu-id="4e794-109">**PowerShell**: è la definizione predefinita.</span><span class="sxs-lookup"><span data-stu-id="4e794-109">**PowerShell** - This is the default.</span></span> <span data-ttu-id="4e794-110">Da questo punto in poi, per PowerShell si intende PowerShell 7 e versioni successive.</span><span class="sxs-lookup"><span data-stu-id="4e794-110">We consider PowerShell 7 and beyond to be the one, true PowerShell going forward.</span></span>

- <span data-ttu-id="4e794-111">**PowerShell Core**: PowerShell basato su .NET Core.</span><span class="sxs-lookup"><span data-stu-id="4e794-111">**PowerShell Core** - PowerShell built on .NET Core.</span></span> <span data-ttu-id="4e794-112">L'uso del termine **Core** deve essere limitato ai casi in cui è necessario distinguere da Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="4e794-112">Usage of the term **Core** should be limited to cases where it is necessary to differentiate it from Windows PowerShell.</span></span>

- <span data-ttu-id="4e794-113">**Windows PowerShell**: PowerShell basato su .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="4e794-113">**Windows PowerShell** - PowerShell built on .NET Framework.</span></span> <span data-ttu-id="4e794-114">Windows PowerShell è disponibile solo in Windows e richiede il framework completo.</span><span class="sxs-lookup"><span data-stu-id="4e794-114">Windows PowerShell ships only on Windows and requires the complete Framework.</span></span>

<span data-ttu-id="4e794-115">In generale i riferimenti a "Windows PowerShell" nella documentazione possono essere modificati in "PowerShell".</span><span class="sxs-lookup"><span data-stu-id="4e794-115">In general, references to "Windows PowerShell" in documentation can be changed to "PowerShell".</span></span>
<span data-ttu-id="4e794-116">La dicitura "Windows PowerShell" **non** deve essere modificata quando si cita tecnologia specifica per Windows.</span><span class="sxs-lookup"><span data-stu-id="4e794-116">"Windows PowerShell" should **not** be changed when Windows-specific technology is being discussed.</span></span>

## <a name="markdown-specifics"></a><span data-ttu-id="4e794-117">Specifiche di Markdown</span><span class="sxs-lookup"><span data-stu-id="4e794-117">Markdown specifics</span></span>

<span data-ttu-id="4e794-118">Il sistema Microsoft Open Publishing (OPS) che compila la documentazione usa [markdig][] per elaborare i documenti Markdown.</span><span class="sxs-lookup"><span data-stu-id="4e794-118">The Microsoft Open Publishing System (OPS) that builds our documentation uses [markdig][] to process the Markdown documents.</span></span> <span data-ttu-id="4e794-119">Markdig analizza i documenti in base alle regole della specifica [CommonMark][] più recente.</span><span class="sxs-lookup"><span data-stu-id="4e794-119">Markdig parses the documents based on the rules of the latest [CommonMark][] specification.</span></span>

<span data-ttu-id="4e794-120">La nuova specifica CommonMark è molto più restrittiva in merito alla costruzione di alcuni elementi Markdown.</span><span class="sxs-lookup"><span data-stu-id="4e794-120">The new CommonMark spec is much stricter about the construction of some Markdown elements.</span></span> <span data-ttu-id="4e794-121">Prestare particolare attenzione ai dettagli inclusi in questo documento.</span><span class="sxs-lookup"><span data-stu-id="4e794-121">Pay close attention to the details provided in this document.</span></span>

### <a name="blank-lines-spaces-and-tabs"></a><span data-ttu-id="4e794-122">Righe vuote, spazi e tabulazioni</span><span class="sxs-lookup"><span data-stu-id="4e794-122">Blank lines, spaces, and tabs</span></span>

<span data-ttu-id="4e794-123">Rimuovere le righe vuote duplicate.</span><span class="sxs-lookup"><span data-stu-id="4e794-123">Remove duplicate blank lines.</span></span> <span data-ttu-id="4e794-124">Più righe vuote vengono sottoposte a rendering come una singola riga vuota in HTML, quindi non necessario usare più righe vuote.</span><span class="sxs-lookup"><span data-stu-id="4e794-124">Multiple blank lines render as a single blank line in HTML so there is not purpose for multiple blank lines.</span></span>

<span data-ttu-id="4e794-125">Le righe vuote segnalano anche la fine di un blocco in Markdown.</span><span class="sxs-lookup"><span data-stu-id="4e794-125">Blank lines also signal the end of a block in Markdown.</span></span> <span data-ttu-id="4e794-126">Deve essere presente un solo spazio vuoto tra i blocchi Markdown di tipi diversi, ad esempio tra un paragrafo e un elenco o un'intestazione.</span><span class="sxs-lookup"><span data-stu-id="4e794-126">There should be a single blank between Markdown blocks of different types (for example, between a paragraph and a list or header).</span></span>

> [!NOTE]
> <span data-ttu-id="4e794-127">La spaziatura è importante in Markdown.</span><span class="sxs-lookup"><span data-stu-id="4e794-127">Spacing is significant in Markdown.</span></span> <span data-ttu-id="4e794-128">Usare sempre gli spazi anziché le tabulazioni hard.</span><span class="sxs-lookup"><span data-stu-id="4e794-128">Always uses spaces instead of hard tabs.</span></span> <span data-ttu-id="4e794-129">Rimuovere gli spazi aggiuntivi alla fine delle righe.</span><span class="sxs-lookup"><span data-stu-id="4e794-129">Remove extra spaces at the end of lines.</span></span>

### <a name="titles-and-headings"></a><span data-ttu-id="4e794-130">Titoli e intestazioni</span><span class="sxs-lookup"><span data-stu-id="4e794-130">Titles and headings</span></span>

<span data-ttu-id="4e794-131">Usare solo [intestazioni ATX][atx] (con lo stile #, anziché intestazioni con stile `=` o `-`).</span><span class="sxs-lookup"><span data-stu-id="4e794-131">Only use [ATX headings][atx] (# style, as opposed to `=` or `-` style headers).</span></span>

- <span data-ttu-id="4e794-132">Usare la maiuscola a inizio frase: solo i nomi propri e la prima lettera di un titolo o di un'intestazione devono essere in maiuscole</span><span class="sxs-lookup"><span data-stu-id="4e794-132">Use sentence case - only proper nouns and the first letter of a title or header should be capitalized</span></span>
- <span data-ttu-id="4e794-133">Deve essere presente uno spazio singolo tra `#` e la prima lettera dell'intestazione</span><span class="sxs-lookup"><span data-stu-id="4e794-133">There must be a single space between the `#` and the first letter of the heading</span></span>
- <span data-ttu-id="4e794-134">Le intestazioni devono essere racchiuse da una sola riga vuota</span><span class="sxs-lookup"><span data-stu-id="4e794-134">Headings should be surrounded by a single blank line</span></span>
- <span data-ttu-id="4e794-135">Ogni documento deve includere un solo titolo H1</span><span class="sxs-lookup"><span data-stu-id="4e794-135">Only one H1 per document</span></span>
- <span data-ttu-id="4e794-136">I livelli di intestazione devono avere incrementi di uno.</span><span class="sxs-lookup"><span data-stu-id="4e794-136">Header levels should increment by one.</span></span> <span data-ttu-id="4e794-137">Non ignorare i livelli</span><span class="sxs-lookup"><span data-stu-id="4e794-137">Do not skip levels</span></span>
- <span data-ttu-id="4e794-138">Non usare il grassetto o altri markup nelle intestazioni</span><span class="sxs-lookup"><span data-stu-id="4e794-138">Do not use bold or other markup in headers</span></span>

### <a name="limit-line-length-to-100-characters"></a><span data-ttu-id="4e794-139">Limitare la lunghezza della riga a 100 caratteri</span><span class="sxs-lookup"><span data-stu-id="4e794-139">Limit line length to 100 characters</span></span>

<span data-ttu-id="4e794-140">Questo vale per gli articoli concettuali e i riferimenti ai cmdlet.</span><span class="sxs-lookup"><span data-stu-id="4e794-140">This applies to conceptual articles and cmdlet reference.</span></span> <span data-ttu-id="4e794-141">Il testo dei titoli Informazioni su può avere una lunghezza massima di 80 caratteri.</span><span class="sxs-lookup"><span data-stu-id="4e794-141">About_topics are limited to 80 characters.</span></span>
<span data-ttu-id="4e794-142">La limitazione della lunghezza della riga migliora i diff e la cronologia dei GIT in termini di leggibilità.</span><span class="sxs-lookup"><span data-stu-id="4e794-142">Limiting the line length improves the readability git diffs and history.</span></span> <span data-ttu-id="4e794-143">Semplifica anche i contributi da parte di altri writer.</span><span class="sxs-lookup"><span data-stu-id="4e794-143">It also makes it easier for other writers to make contributions.</span></span>

<span data-ttu-id="4e794-144">Usare l'estensione [Reflow Markdown][reflow] in Visual Studio Code per reimpostare facilmente il flusso dei paragrafi, in modo da adattarlo alla lunghezza di riga prescritta.</span><span class="sxs-lookup"><span data-stu-id="4e794-144">Use the [Reflow Markdown][reflow] extension in Visual Studio Code to easily reflow paragraphs to fit the prescribed line length.</span></span>

### <a name="lists"></a><span data-ttu-id="4e794-145">Elenchi</span><span class="sxs-lookup"><span data-stu-id="4e794-145">Lists</span></span>

<span data-ttu-id="4e794-146">Se l'elenco contiene più frasi o paragrafi, prendere in considerazione l'uso di un'intestazione di sottolivello anziché di un elenco.</span><span class="sxs-lookup"><span data-stu-id="4e794-146">If your list contains multiple sentences or paragraphs, consider using a sub-level header rather than a list.</span></span>

<span data-ttu-id="4e794-147">Gli elenchi devono essere racchiusi da una sola riga vuota.</span><span class="sxs-lookup"><span data-stu-id="4e794-147">List should be surrounded by a single blank line.</span></span>

#### <a name="unordered-lists"></a><span data-ttu-id="4e794-148">Elenchi non ordinati</span><span class="sxs-lookup"><span data-stu-id="4e794-148">Unordered lists</span></span>

<span data-ttu-id="4e794-149">Non terminare gli elementi elenco con un punto (a meno che non contengano più frasi).</span><span class="sxs-lookup"><span data-stu-id="4e794-149">Do not end list items with a period unless they contain multiple sentences.</span></span> <span data-ttu-id="4e794-150">Usare il trattino (`-`) per gli elementi di elenchi puntati.</span><span class="sxs-lookup"><span data-stu-id="4e794-150">Use the hyphen character (`-`) for list item bullets.</span></span> <span data-ttu-id="4e794-151">In questo modo si evita confusione con i markup di grassetto o corsivo che usano l'asterisco (`*`).</span><span class="sxs-lookup"><span data-stu-id="4e794-151">This avoids confusion with bold or italic markup that uses the asterisk [`*`].</span></span> <span data-ttu-id="4e794-152">Per includere un paragrafo o altri elementi sotto un punto elenco, inserire un'interruzione di riga e allineare il rientro con il primo carattere dopo il punto elenco.</span><span class="sxs-lookup"><span data-stu-id="4e794-152">To include a paragraph or other elements under a bullet item, insert a line break and align indentation with the first character after the bullet.</span></span>

<span data-ttu-id="4e794-153">Ad esempio:</span><span class="sxs-lookup"><span data-stu-id="4e794-153">For example:</span></span>

```markdown
This is a list that contain sub-elements under a bullet item.

- First bullet item

  Sentence explaining the first bullet.

  - Sub-bullet item

    Sentence explaining the sub-bullet.

- Second bullet item
- Third bullet item
```

<span data-ttu-id="4e794-154">Questo è un elenco che contiene sottoelementi sotto un elemento punto elenco.</span><span class="sxs-lookup"><span data-stu-id="4e794-154">This is a list that contains sub-elements under a bullet item.</span></span>

- <span data-ttu-id="4e794-155">Primo elemento punto elenco</span><span class="sxs-lookup"><span data-stu-id="4e794-155">First bullet item</span></span>

  <span data-ttu-id="4e794-156">Frase che spiega il primo punto elenco.</span><span class="sxs-lookup"><span data-stu-id="4e794-156">Sentence explaining the first bullet.</span></span>

  - <span data-ttu-id="4e794-157">Sottoelemento punto elenco</span><span class="sxs-lookup"><span data-stu-id="4e794-157">Sub-bullet item</span></span>

    <span data-ttu-id="4e794-158">Frase che spiega il sottoelemento punto elenco.</span><span class="sxs-lookup"><span data-stu-id="4e794-158">Sentence explaining the sub-bullet.</span></span>

- <span data-ttu-id="4e794-159">Secondo elemento punto elenco</span><span class="sxs-lookup"><span data-stu-id="4e794-159">Second bullet item</span></span>
- <span data-ttu-id="4e794-160">Terzo elemento punto elenco</span><span class="sxs-lookup"><span data-stu-id="4e794-160">Third bullet item</span></span>

#### <a name="ordered-lists"></a><span data-ttu-id="4e794-161">Elenchi ordinati</span><span class="sxs-lookup"><span data-stu-id="4e794-161">Ordered lists</span></span>

<span data-ttu-id="4e794-162">Per includere un paragrafo o altri elementi sotto un elemento numerato, allineare il rientro con il primo carattere dopo il numero dell'elemento.</span><span class="sxs-lookup"><span data-stu-id="4e794-162">To include a paragraph or other elements under a numbered item, align indentation with the first character after the item number.</span></span> <span data-ttu-id="4e794-163">Tutti gli elementi di un elenco numerato devono usare il numero `1.` anziché incrementare ogni elemento.</span><span class="sxs-lookup"><span data-stu-id="4e794-163">All items in a numbered listed should use the number `1.` rather than incrementing each item.</span></span> <span data-ttu-id="4e794-164">Il rendering di Markdown incrementa automaticamente il valore.</span><span class="sxs-lookup"><span data-stu-id="4e794-164">Markdown rendering increments the value automatically.</span></span> <span data-ttu-id="4e794-165">Questo semplifica il riordino degli elementi e standardizza il rientro del contenuto subordinato.</span><span class="sxs-lookup"><span data-stu-id="4e794-165">This makes reordering items easier and standardizes the indentation of subordinate content.</span></span>

<span data-ttu-id="4e794-166">Ad esempio:</span><span class="sxs-lookup"><span data-stu-id="4e794-166">For example:</span></span>

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

<span data-ttu-id="4e794-167">Il testo Markdown risultante viene restituito come segue:</span><span class="sxs-lookup"><span data-stu-id="4e794-167">The resulting Markdown is rendered as follows:</span></span>

1. <span data-ttu-id="4e794-168">Per il primo elemento inserire uno spazio singolo dopo 1.</span><span class="sxs-lookup"><span data-stu-id="4e794-168">For the first element, insert a single space after the 1.</span></span> <span data-ttu-id="4e794-169">Le frasi lunghe vanno mandate a capo alla riga successiva e devono essere allineate con il primo carattere dopo il marcatore di elenco numerato.</span><span class="sxs-lookup"><span data-stu-id="4e794-169">Long sentences should be wrapped to the next line and must line up with the first character after the numbered list marker.</span></span>

   <span data-ttu-id="4e794-170">Per includere un secondo elemento (come questo), inserire un'interruzione di riga dopo il primo elemento e allineare i rientri.</span><span class="sxs-lookup"><span data-stu-id="4e794-170">To include a second element (like this one), insert a line break after the first and align indentations.</span></span> <span data-ttu-id="4e794-171">Il rientro del secondo elemento deve essere allineato con il primo carattere dopo il marcatore dell'elenco numerato.</span><span class="sxs-lookup"><span data-stu-id="4e794-171">The indentation of the second element must line up with the first character after the numbered list marker.</span></span> <span data-ttu-id="4e794-172">Per gli elementi a cifra singola come questo, si applica un rientro alla colonna 4.</span><span class="sxs-lookup"><span data-stu-id="4e794-172">For single digit items, like this one, you indent to column 4.</span></span> <span data-ttu-id="4e794-173">Per gli elementi a doppia cifra, ad esempio l'elemento numero 10, si applica un rientro alla colonna 5.</span><span class="sxs-lookup"><span data-stu-id="4e794-173">For double digits items, for example item number 10, you indent to column 5.</span></span>

1. <span data-ttu-id="4e794-174">Il successivo elemento numerato inizia qui.</span><span class="sxs-lookup"><span data-stu-id="4e794-174">The next numbered item starts here.</span></span>

### <a name="formatting-command-syntax-elements"></a><span data-ttu-id="4e794-175">Formattazione degli elementi della sintassi del comando</span><span class="sxs-lookup"><span data-stu-id="4e794-175">Formatting command syntax elements</span></span>

- <span data-ttu-id="4e794-176">Usare sempre il nome completo per i cmdlet e i parametri.</span><span class="sxs-lookup"><span data-stu-id="4e794-176">Always use the full name for cmdlets and parameters.</span></span> <span data-ttu-id="4e794-177">Evitare di usare alias, a meno che non si stia dimostrando in modo specifico l'alias.</span><span class="sxs-lookup"><span data-stu-id="4e794-177">Avoid using aliases unless you are specifically demonstrating the alias.</span></span>

- <span data-ttu-id="4e794-178">All'interno di un paragrafo le parole chiave del linguaggio, i nomi dei cmdlet, le variabili e i percorsi di file devono essere racchiusi tra caratteri accento grave (`` ` ``).</span><span class="sxs-lookup"><span data-stu-id="4e794-178">Within a paragraph, language keywords, cmdlet names, variables, and file paths should be wrapped in backtick (`` ` ``) characters.</span></span> <span data-ttu-id="4e794-179">I nomi di proprietà, parametri e classi devono essere in **grassetto**.</span><span class="sxs-lookup"><span data-stu-id="4e794-179">Property, parameter, and class names should be **bold**.</span></span>

  <span data-ttu-id="4e794-180">Ad esempio:</span><span class="sxs-lookup"><span data-stu-id="4e794-180">For example:</span></span>

  ~~~markdown
  The following code uses `Get-ChildItem` to list the contents of `C:\Windows` and assigns
  the output to the `$files` variable.

  ```powershell
  $files = Get-ChildItem C:\Windows
  ```
  ~~~

- <span data-ttu-id="4e794-181">Quando si fa riferimento a un parametro con il nome, questo deve essere in **grassetto**.</span><span class="sxs-lookup"><span data-stu-id="4e794-181">When referring to a parameter by name, the name should be **bold**.</span></span> <span data-ttu-id="4e794-182">Quando si illustra l'uso di un parametro con il prefisso trattino, il parametro deve essere racchiuso tra caratteri accento grave.</span><span class="sxs-lookup"><span data-stu-id="4e794-182">When illustrating the use of a parameter with the hyphen prefix, the parameter should be wrapped in backticks.</span></span> <span data-ttu-id="4e794-183">Ad esempio:</span><span class="sxs-lookup"><span data-stu-id="4e794-183">For example:</span></span>

  ```markdown
  The parameter's name is **Name**, but it is typed as `-Name` when used on the command
  line as a parameter.
  ```

- <span data-ttu-id="4e794-184">Quando si fa riferimento a comandi esterni (exe, script e così via), il nome del comando deve essere in grassetto, tutto in minuscolo (o con iniziale maiuscola se all'inizio di una frase) e includere l'estensione di file appropriata.</span><span class="sxs-lookup"><span data-stu-id="4e794-184">When referring to external commands (EXEs, scripts, etc.), the command name should be bold, all lowercase (or capitalized if at the beginning of a sentence), and include the appropriate file extension.</span></span> <span data-ttu-id="4e794-185">Ad esempio:</span><span class="sxs-lookup"><span data-stu-id="4e794-185">For example:</span></span>

  ```markdown
  For example, on Windows systems, you can use the `net start` and `net stop` commands
  to start and stop a service. **Sc.exe** is another service control tool for Windows.
  That name does not fit into the naming pattern for the **net.exe** service commands.
  ```

- <span data-ttu-id="4e794-186">Quando si visualizza un esempio d'uso di un comando esterno, l'esempio deve essere racchiuso tra caratteri accento grave.</span><span class="sxs-lookup"><span data-stu-id="4e794-186">When showing example usage of an external command, the example should be wrapped in backticks.</span></span>
  <span data-ttu-id="4e794-187">In caso di conflitto di nomi con un alias, è necessario includere l'estensione file nell'esempio di comando.</span><span class="sxs-lookup"><span data-stu-id="4e794-187">When there is a name collisions with an alias you must include the file extension in the command example.</span></span> <span data-ttu-id="4e794-188">Ad esempio:</span><span class="sxs-lookup"><span data-stu-id="4e794-188">For example:</span></span>

  ```markdown
  To start the spooler service on a remote computer named DC01, you type `sc.exe \\DC01 start spooler`.
  ```

- <span data-ttu-id="4e794-189">Durante la scrittura di un articolo concettuale (diversamente dal contenuto di riferimento), la prima istanza del nome di un cmdlet deve essere un collegamento alla documentazione del cmdlet.</span><span class="sxs-lookup"><span data-stu-id="4e794-189">When writing a conceptual article (as opposed to reference content), the first instance of a cmdlet name should be hyperlinked to the cmdlet documentation.</span></span> <span data-ttu-id="4e794-190">Non usare accenti gravi, grassetto o altri elementi di markup all'interno delle parentesi quadre di un collegamento ipertestuale.</span><span class="sxs-lookup"><span data-stu-id="4e794-190">Do not use backticks, bold, or other markup inside the brackets of a hyperlink.</span></span>

  <span data-ttu-id="4e794-191">Ad esempio:</span><span class="sxs-lookup"><span data-stu-id="4e794-191">For example:</span></span>

  ```markdown
  This [Write-Host](/powershell/module/Microsoft.PowerShell.Utility/Write-Host) cmdlet
  uses the **Object** parameter to ...
  ```

  <span data-ttu-id="4e794-192">Per altre informazioni, vedere la sezione [Collegamenti ipertestuali](#hyperlinks) di questo articolo.</span><span class="sxs-lookup"><span data-stu-id="4e794-192">For more information, see [Hyperlinks](#hyperlinks) section of this article.</span></span>

### <a name="images"></a><span data-ttu-id="4e794-193">Immagini</span><span class="sxs-lookup"><span data-stu-id="4e794-193">Images</span></span>

<span data-ttu-id="4e794-194">La sintassi per includere un'immagine è la seguente:</span><span class="sxs-lookup"><span data-stu-id="4e794-194">The syntax to include an image is:</span></span>

```markdown
![[alt text]](<folderPath>)

Example:
![Introduction](./media/overview/Introduction.png)
```

<span data-ttu-id="4e794-195">`alt text` è una breve descrizione dell'immagine e `<folder path>` è un percorso relativo all'immagine.</span><span class="sxs-lookup"><span data-stu-id="4e794-195">Where `alt text` is a brief description of the image and `<folder path>` is a relative path to the image.</span></span> <span data-ttu-id="4e794-196">È necessario testo alternativo per le utilità per la lettura dello schermo destinate a utenti con problemi visivi.</span><span class="sxs-lookup"><span data-stu-id="4e794-196">Alternate text is required for screen readers for the visually impaired.</span></span> <span data-ttu-id="4e794-197">Tale testo è utile anche quando a causa di un bug del sito non è possibile eseguire il rendering dell'immagine.</span><span class="sxs-lookup"><span data-stu-id="4e794-197">It is also useful in case there is a site bug where the image cannot be rendered.</span></span>

<span data-ttu-id="4e794-198">Le immagini devono essere archiviate in una cartella `media/<article-name>` all'interno della cartella che contiene l'articolo.</span><span class="sxs-lookup"><span data-stu-id="4e794-198">Images should be stored in a `media/<article-name>` folder within the folder containing the article.</span></span>
<span data-ttu-id="4e794-199">Le immagini non devono essere condivise tra gli articoli.</span><span class="sxs-lookup"><span data-stu-id="4e794-199">Images should not be shared between articles.</span></span> <span data-ttu-id="4e794-200">Creare una cartella corrispondente al nome file dell'articolo sotto la cartella `media`.</span><span class="sxs-lookup"><span data-stu-id="4e794-200">Create a folder that matches the filename of your article under the `media` folder.</span></span> <span data-ttu-id="4e794-201">Copiare le immagini per l'articolo nella nuova cartella.</span><span class="sxs-lookup"><span data-stu-id="4e794-201">Copy the images for that article to that new folder.</span></span> <span data-ttu-id="4e794-202">Se un'immagine viene usata da più articoli, ogni cartella di immagini deve avere una copia di quel file di immagine.</span><span class="sxs-lookup"><span data-stu-id="4e794-202">If an image is used by multiple articles, each image folder must have a copy of that image file.</span></span> <span data-ttu-id="4e794-203">Questa procedura impedisce che la modifica di un'immagine in un articolo abbia effetto su un altro articolo.</span><span class="sxs-lookup"><span data-stu-id="4e794-203">This practice prevents a change to an image in one article affecting another article.</span></span>

<span data-ttu-id="4e794-204">Sono supportati i tipi di file immagine seguenti: `*.png`, `*.gif`, `*.jpeg`, `*.jpg`, `*.svg`</span><span class="sxs-lookup"><span data-stu-id="4e794-204">The following image file types are supported: `*.png`, `*.gif`, `*.jpeg`, `*.jpg`, `*.svg`</span></span>

### <a name="markdown-extensions-supported-by-open-publishing"></a><span data-ttu-id="4e794-205">Estensioni Markdown supportate da Open Publishing</span><span class="sxs-lookup"><span data-stu-id="4e794-205">Markdown extensions supported by Open Publishing</span></span>

<span data-ttu-id="4e794-206">[Microsoft Docs Authoring Pack](/contribute/how-to-write-docs-auth-pack) contiene strumenti che supportano funzionalità specifiche del sistema di pubblicazione.</span><span class="sxs-lookup"><span data-stu-id="4e794-206">The [Microsoft Docs Authoring Pack](/contribute/how-to-write-docs-auth-pack) contains tools that support features unique to our publishing system.</span></span> <span data-ttu-id="4e794-207">Gli avvisi sono un'estensione Markdown per la creazione di citazioni che vengono restituite in docs.microsoft.com con colori e icone che evidenziano il significato del contenuto.</span><span class="sxs-lookup"><span data-stu-id="4e794-207">Alerts are a Markdown extension to create block quotes that render on docs.microsoft.com with colors and icons that indicate the significance of the content.</span></span> <span data-ttu-id="4e794-208">Sono supportati i tipi di avviso seguenti:</span><span class="sxs-lookup"><span data-stu-id="4e794-208">The following alert types are supported:</span></span>

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

<span data-ttu-id="4e794-209">Questi avvisi hanno un aspetto simile al seguente in docs.microsoft.com:</span><span class="sxs-lookup"><span data-stu-id="4e794-209">These alerts look like this on docs.microsoft.com:</span></span>

> [!NOTE]
> <span data-ttu-id="4e794-210">Informazioni che l'utente deve notare anche in una consultazione veloce.</span><span class="sxs-lookup"><span data-stu-id="4e794-210">Information the user should notice even if skimming.</span></span>

> [!TIP]
> <span data-ttu-id="4e794-211">Informazioni facoltative che consentono a un utente di ottenere risultati più efficaci.</span><span class="sxs-lookup"><span data-stu-id="4e794-211">Optional information to help a user be more successful.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="4e794-212">Informazioni essenziali necessarie per l'esito positivo.</span><span class="sxs-lookup"><span data-stu-id="4e794-212">Essential information required for user success.</span></span>

> [!CAUTION]
> <span data-ttu-id="4e794-213">Potenziali conseguenze negative di un'azione.</span><span class="sxs-lookup"><span data-stu-id="4e794-213">Negative potential consequences of an action.</span></span>

> [!WARNING]
> <span data-ttu-id="4e794-214">Conseguenze pericolose certe di un'azione.</span><span class="sxs-lookup"><span data-stu-id="4e794-214">Dangerous certain consequences of an action.</span></span>

## <a name="hyperlinks"></a><span data-ttu-id="4e794-215">Collegamenti ipertestuali</span><span class="sxs-lookup"><span data-stu-id="4e794-215">Hyperlinks</span></span>

- <span data-ttu-id="4e794-216">Evitare l'uso di URL semplici.</span><span class="sxs-lookup"><span data-stu-id="4e794-216">Avoid using bare URLs.</span></span> <span data-ttu-id="4e794-217">I collegamenti devono usare la sintassi Markdown `[friendlyname](url-or-path)`</span><span class="sxs-lookup"><span data-stu-id="4e794-217">Links should use Markdown syntax `[friendlyname](url-or-path)`</span></span>
- <span data-ttu-id="4e794-218">Gli URL semplici possono essere usati quando necessario, ma devono essere racchiusi tra caratteri accento grave.</span><span class="sxs-lookup"><span data-stu-id="4e794-218">Bare URLs may be used when necessary, but should be enclosed in backticks.</span></span> <span data-ttu-id="4e794-219">Ad esempio:</span><span class="sxs-lookup"><span data-stu-id="4e794-219">For example:</span></span>

  ```markdown
  By default, if you do not specify this parameter, the DMTF standard resource URI
  `http://schemas.dmtf.org/wbem/wscim/1/cim-schema/2/` is used and the class name is appended to it.
  ```

- <span data-ttu-id="4e794-220">Se possibile, i collegamenti URL devono essere di tipo HTTPS.</span><span class="sxs-lookup"><span data-stu-id="4e794-220">URL links should be HTTPS when possible.</span></span>
- <span data-ttu-id="4e794-221">I collegamenti devono avere un nome descrittivo, in genere il titolo dell'argomento collegato</span><span class="sxs-lookup"><span data-stu-id="4e794-221">Links must have a friendly name, usually the title of the linked topic</span></span>
- <span data-ttu-id="4e794-222">Tutti gli elementi nella sezione "Collegamenti correlati" in fondo all'articolo devono essere impostati come collegamenti ipertestuali.</span><span class="sxs-lookup"><span data-stu-id="4e794-222">All items in the "related links" section at the bottom should be hyperlinked.</span></span>
- <span data-ttu-id="4e794-223">Non usare accenti gravi, grassetto o altri elementi di markup all'interno delle parentesi quadre di un collegamento ipertestuale.</span><span class="sxs-lookup"><span data-stu-id="4e794-223">Do not use backticks, bold, or other markup inside the brackets of a hyperlink.</span></span>

### <a name="linking-to-other-content"></a><span data-ttu-id="4e794-224">Collegamento a contenuto diverso</span><span class="sxs-lookup"><span data-stu-id="4e794-224">Linking to other content</span></span>

<span data-ttu-id="4e794-225">Il sistema di pubblicazione supporta due tipi di collegamenti ipertestuali: URL e collegamenti a file.</span><span class="sxs-lookup"><span data-stu-id="4e794-225">There are two types of hyperlinks supported by the publishing system: URLs and file links.</span></span>

<span data-ttu-id="4e794-226">Un collegamento URL può essere un percorso URL relativo alla radice docs.microsoft.com.</span><span class="sxs-lookup"><span data-stu-id="4e794-226">A URL link can be a URL path that is relative to the root of docs.microsoft.com.</span></span> <span data-ttu-id="4e794-227">Oppure può essere un URL assoluto, che include la sintassi completa dell'URL.</span><span class="sxs-lookup"><span data-stu-id="4e794-227">Or an absolute URL that include the full URL syntax.</span></span> <span data-ttu-id="4e794-228">(Ad esempio: `https:/github.com/MicrosoftDocs/PowerShell-Docs`)</span><span class="sxs-lookup"><span data-stu-id="4e794-228">(For example: `https:/github.com/MicrosoftDocs/PowerShell-Docs`)</span></span>

- <span data-ttu-id="4e794-229">Usare i collegamenti URL per il collegamento a contenuto esterno a PowerShell-Docs o il collegamento tra riferimenti ai cmdlet e articoli concettuali in PowerShell-Docs.</span><span class="sxs-lookup"><span data-stu-id="4e794-229">Use URL links when linking to content outside of PowerShell-Docs or between cmdlet reference and conceptual articles within PowerShell-docs.</span></span>
- <span data-ttu-id="4e794-230">Il modo più semplice per creare un collegamento relativo consiste nel copiare l'URL dal browser, quindi rimuovere `https://docs.microsoft.com/en-us` dal valore incollato in Markdown.</span><span class="sxs-lookup"><span data-stu-id="4e794-230">The simplest way to link create a relative link is to copy the URL from your browser then remove `https://docs.microsoft.com/en-us` from the value you paste into markdown.</span></span>
   - <span data-ttu-id="4e794-231">Non includere le impostazioni locali negli URL nelle proprietà Microsoft (ad esempio,</span><span class="sxs-lookup"><span data-stu-id="4e794-231">Do not include locales in URLs on Microsoft properties (eg.</span></span> <span data-ttu-id="4e794-232">rimuovere "/it-IT" dall'URL).</span><span class="sxs-lookup"><span data-stu-id="4e794-232">remove "/en-us" from URL).</span></span>
- <span data-ttu-id="4e794-233">Tutti gli URL che puntano a siti Web esterni devono usare HTTPS, a meno che ciò non sia valido per il sito di destinazione.</span><span class="sxs-lookup"><span data-stu-id="4e794-233">All URLs to external websites should use HTTPS unless that is not valid for the target site.</span></span>

<span data-ttu-id="4e794-234">Un collegamento file viene usato per il collegamento da un articolo di riferimento a un altro o da un articolo concettuale a un altro.</span><span class="sxs-lookup"><span data-stu-id="4e794-234">A file link is used to link from one reference article to another, or from one conceptual article to another.</span></span> <span data-ttu-id="4e794-235">Per creare un collegamento a un articolo di riferimento per una versione specifica di PowerShell, è necessario usare un collegamento URL.</span><span class="sxs-lookup"><span data-stu-id="4e794-235">If you need to link to a reference article for a specific version of PowerShell, then you need to use a URL link.</span></span>

- <span data-ttu-id="4e794-236">I collegamenti file contengono un percorso di file relativo (ad esempio: `../folder/file.md`)</span><span class="sxs-lookup"><span data-stu-id="4e794-236">File links contain a relative file path (for example: `../folder/file.md`)</span></span>
- <span data-ttu-id="4e794-237">Tutti i percorsi di file usano caratteri barra (`/`)</span><span class="sxs-lookup"><span data-stu-id="4e794-237">All file paths use forward-slash (`/`) characters</span></span>

## <a name="formatting-code-samples"></a><span data-ttu-id="4e794-238">Esempi di formattazione del codice</span><span class="sxs-lookup"><span data-stu-id="4e794-238">Formatting code samples</span></span>

<span data-ttu-id="4e794-239">Markdown supporta due stili di codice:</span><span class="sxs-lookup"><span data-stu-id="4e794-239">Markdown supports two different code styles:</span></span>

- <span data-ttu-id="4e794-240">Intervalli di codice (inline): contrassegnati da un singolo carattere accento grave (`` ` ``).</span><span class="sxs-lookup"><span data-stu-id="4e794-240">Code spans (inline) - marked by a single backtick (`` ` ``) character.</span></span> <span data-ttu-id="4e794-241">Sono usati all'interno di un paragrafo anziché come blocchi autonomi.</span><span class="sxs-lookup"><span data-stu-id="4e794-241">Used within a paragraph rather than as a standalone block.</span></span>
- <span data-ttu-id="4e794-242">Blocchi di codice: blocchi a più righe racchiusi fra stringhe con triplo carattere accento grave (`` ``` ``).</span><span class="sxs-lookup"><span data-stu-id="4e794-242">Code blocks - a multi-line block surrounded by triple-backtick (`` ``` ``) strings.</span></span> <span data-ttu-id="4e794-243">I blocchi di codice possono anche avere un'etichetta di linguaggio dopo i caratteri accento grave.</span><span class="sxs-lookup"><span data-stu-id="4e794-243">Code blocks may also have a language label following the backticks.</span></span> <span data-ttu-id="4e794-244">L'etichetta di linguaggio consente l'evidenziazione della sintassi per il contenuto del blocco di codice.</span><span class="sxs-lookup"><span data-stu-id="4e794-244">The language label enables syntax highlighting for the contents of the code block.</span></span>

### <a name="using-code-blocks"></a><span data-ttu-id="4e794-245">Uso dei blocchi di codice</span><span class="sxs-lookup"><span data-stu-id="4e794-245">Using code blocks</span></span>

<span data-ttu-id="4e794-246">Markdown consente l'uso dei rientri per indicare un blocco di codice, ma questo criterio può essere problematico e deve essere evitato.</span><span class="sxs-lookup"><span data-stu-id="4e794-246">Markdown allows for indentation to signify a code block, but this pattern can be problematic and should be avoided.</span></span> <span data-ttu-id="4e794-247">Tutti i blocchi di codice devono essere inclusi in un intervallo di codice.</span><span class="sxs-lookup"><span data-stu-id="4e794-247">All code blocks should be contained in a code fence.</span></span> <span data-ttu-id="4e794-248">Un intervallo di codice è un blocco di codice racchiuso fra stringhe con triplo accento grave (`` ``` ``).</span><span class="sxs-lookup"><span data-stu-id="4e794-248">A code fence is a block of code surrounded by triple-backtick (`` ``` ``) strings.</span></span> <span data-ttu-id="4e794-249">I marcatori dell'intervallo di codice devono trovarsi su una riga a parte, prima e dopo l'esempio di codice.</span><span class="sxs-lookup"><span data-stu-id="4e794-249">The code fence markers must be on their own line before and after the code sample.</span></span> <span data-ttu-id="4e794-250">Il marcatore all'inizio del blocco di codice può avere un'etichetta del linguaggio facoltativa.</span><span class="sxs-lookup"><span data-stu-id="4e794-250">The marker at the start of the code block may have an optional language label.</span></span> <span data-ttu-id="4e794-251">Microsoft Open Publishing System (OPS) usa l'etichetta del linguaggio per supportare la funzionalità di evidenziazione della sintassi.</span><span class="sxs-lookup"><span data-stu-id="4e794-251">Microsoft's Open Publishing System (OPS) uses the language label to support the syntax highlighting feature.</span></span>

<span data-ttu-id="4e794-252">OPS aggiunge anche un pulsante **Copy** (Copia) che copia il contenuto del blocco di codice negli Appunti.</span><span class="sxs-lookup"><span data-stu-id="4e794-252">OPS also adds a **Copy** button that copies the contents of the code block to the clipboard.</span></span> <span data-ttu-id="4e794-253">In questo modo è possibile incollare rapidamente il codice in uno script per eseguire il test dell'esempio di codice.</span><span class="sxs-lookup"><span data-stu-id="4e794-253">This allows you to quickly paste the code into a script for testing the code example.</span></span> <span data-ttu-id="4e794-254">Ma non tutti gli esempi nella documentazione sono destinati all'esecuzione.</span><span class="sxs-lookup"><span data-stu-id="4e794-254">However, not all examples in our documentation are intended to be run.</span></span> <span data-ttu-id="4e794-255">Alcuni blocchi di codice sono semplici illustrazioni di un concetto di PowerShell.</span><span class="sxs-lookup"><span data-stu-id="4e794-255">Some code blocks are simple illustrations of a PowerShell concept.</span></span>

<span data-ttu-id="4e794-256">Nella documentazione vengono usati due tipi di blocchi di codice:</span><span class="sxs-lookup"><span data-stu-id="4e794-256">There are two types code blocks used in our documentation:</span></span>

1. <span data-ttu-id="4e794-257">Esempi illustrativi</span><span class="sxs-lookup"><span data-stu-id="4e794-257">Illustrative examples</span></span>
2. <span data-ttu-id="4e794-258">Esempi eseguibili</span><span class="sxs-lookup"><span data-stu-id="4e794-258">Executable examples</span></span>

### <a name="syntax-code-blocks"></a><span data-ttu-id="4e794-259">Blocchi di codice di sintassi</span><span class="sxs-lookup"><span data-stu-id="4e794-259">Syntax code blocks</span></span>

<span data-ttu-id="4e794-260">Questo esempio illustra tutti i possibili parametri del cmdlet `Get-Command`.</span><span class="sxs-lookup"><span data-stu-id="4e794-260">This example illustrates all the possible parameters of the `Get-Command` cmdlet.</span></span>

~~~markdown
```
Get-Command [-Verb <String[]>] [-Noun <String[]>] [-Module <String[]>]
  [-FullyQualifiedModule <ModuleSpecification[]>] [-TotalCount <Int32>] [-Syntax] [-ShowCommandInfo]
  [[-ArgumentList] <Object[]>] [-All] [-ListImported] [-ParameterName <String[]>]
  [-ParameterType <PSTypeName[]>] [<CommonParameters>]
```
~~~

<span data-ttu-id="4e794-261">Questo esempio illustra l'istruzione `for` in termini generici:</span><span class="sxs-lookup"><span data-stu-id="4e794-261">This example describes the `for` statement in generalized terms:</span></span>

~~~markdown
```
for (<init>; <condition>; <repeat>)
{<statement list>}
```
~~~

### <a name="illustrative-examples"></a><span data-ttu-id="4e794-262">Esempi illustrativi</span><span class="sxs-lookup"><span data-stu-id="4e794-262">Illustrative examples</span></span>

<span data-ttu-id="4e794-263">Gli esempi illustrativi vengono usati per descrivere un concetto di PowerShell.</span><span class="sxs-lookup"><span data-stu-id="4e794-263">Illustrative examples are used to explain a PowerShell concept.</span></span> <span data-ttu-id="4e794-264">Non sono pensati per essere copiati negli Appunti per l'esecuzione.</span><span class="sxs-lookup"><span data-stu-id="4e794-264">They are not meant to be copied to the clipboard for execution.</span></span> <span data-ttu-id="4e794-265">Vengono usati soprattutto per esempi semplici e facili da digitare.</span><span class="sxs-lookup"><span data-stu-id="4e794-265">These are most commonly used for simple examples that are easy to type.</span></span>
<span data-ttu-id="4e794-266">Vengono anche usati per esempi di sintassi quando si vuole illustrare la sintassi di un comando.</span><span class="sxs-lookup"><span data-stu-id="4e794-266">They are also used for syntax examples where you are illustrating the syntax of a command.</span></span> <span data-ttu-id="4e794-267">Il blocco di codice può contenere output di esempio del comando che viene illustrato.</span><span class="sxs-lookup"><span data-stu-id="4e794-267">The code block may contain example output from the command being illustrated.</span></span>

<span data-ttu-id="4e794-268">Ecco un esempio semplice che presenta gli operatori di confronto di PowerShell:</span><span class="sxs-lookup"><span data-stu-id="4e794-268">Here is a simple example illustrating a PowerShell comparison operators:</span></span>

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

<span data-ttu-id="4e794-269">Si noti che questo esempio include il prompt di PowerShell semplificato e visualizza l'output risultante.</span><span class="sxs-lookup"><span data-stu-id="4e794-269">Note that this example has the simplified PowerShell prompt and shows the resulting output.</span></span> <span data-ttu-id="4e794-270">In questo caso, non è previsto che l'utente copi ed esegua l'esempio.</span><span class="sxs-lookup"><span data-stu-id="4e794-270">In this case, we don't intend the reader to copy and run this example.</span></span>

### <a name="executable-examples"></a><span data-ttu-id="4e794-271">Esempi eseguibili</span><span class="sxs-lookup"><span data-stu-id="4e794-271">Executable examples</span></span>

<span data-ttu-id="4e794-272">Gli esempi più complessi o quelli da usare per la copia e l'esecuzione devono usare il markup di stile del blocco seguente:</span><span class="sxs-lookup"><span data-stu-id="4e794-272">More complex examples or examples that are intended to be useful to copy and execute should use the following block-style markup:</span></span>

~~~markdown
```powershell
<PowerShell code goes here>
```
~~~

<span data-ttu-id="4e794-273">L'output visualizzato dai comandi di PowerShell deve essere racchiuso in un blocco di codice **Output** per evitare l'evidenziazione della sintassi.</span><span class="sxs-lookup"><span data-stu-id="4e794-273">The output displayed by PowerShell commands should be enclosed in an **Output** code block to prevent syntax highlighting.</span></span> <span data-ttu-id="4e794-274">Ad esempio:</span><span class="sxs-lookup"><span data-stu-id="4e794-274">For example:</span></span>

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

<span data-ttu-id="4e794-275">L'etichetta del codice **Output** non corrisponde a un "linguaggio" ufficiale supportato dal sistema di evidenziazione della sintassi.</span><span class="sxs-lookup"><span data-stu-id="4e794-275">The **Output** code label is not an official "language" supported by the syntax highlighting system.</span></span>
<span data-ttu-id="4e794-276">Questa etichetta è tuttavia utile perché OPS aggiunge l'etichetta "Output" al frame della casella di codice nella pagina Web.</span><span class="sxs-lookup"><span data-stu-id="4e794-276">However, this label is useful because OPS adds the "Output" label to the code box frame on the web page.</span></span> <span data-ttu-id="4e794-277">La casella di codice "Output" non presenta l'evidenziazione della sintassi.</span><span class="sxs-lookup"><span data-stu-id="4e794-277">The "Output" code box has no syntax highlighting.</span></span>

## <a name="coding-style-rules"></a><span data-ttu-id="4e794-278">Regole dello stile di codifica</span><span class="sxs-lookup"><span data-stu-id="4e794-278">Coding style rules</span></span>

### <a name="avoid-line-continuation-in-code-samples"></a><span data-ttu-id="4e794-279">Evitare la continuazione di riga negli esempi di codice</span><span class="sxs-lookup"><span data-stu-id="4e794-279">Avoid line continuation in code samples</span></span>

<span data-ttu-id="4e794-280">Evitare di usare i caratteri di continuazione di riga (`` ` ``) negli esempi di codice PowerShell.</span><span class="sxs-lookup"><span data-stu-id="4e794-280">Avoid using line continuation characters (`` ` ``) in PowerShell code examples.</span></span> <span data-ttu-id="4e794-281">Questi caratteri sono difficili da visualizzare e possono causare problemi se alla fine della riga sono presenti spazi aggiuntivi.</span><span class="sxs-lookup"><span data-stu-id="4e794-281">These are hard to see and can cause problems if there are extra spaces at the end of the line.</span></span>

- <span data-ttu-id="4e794-282">Usare lo splatting di PowerShell per ridurre la lunghezza della riga per i cmdlet che hanno numerosi parametri.</span><span class="sxs-lookup"><span data-stu-id="4e794-282">Use PowerShell splatting to reduce line length for cmdlets that have a lot of parameters.</span></span>
- <span data-ttu-id="4e794-283">Sfruttare i vantaggi delle opportunità naturali di interruzione riga di PowerShell, ad esempio dopo i caratteri pipe (`|`), le parentesi graffe di apertura, le parentesi tonde e le parentesi quadre.</span><span class="sxs-lookup"><span data-stu-id="4e794-283">Take advantage of PowerShell's natural line break opportunities, like after pipe (`|`) characters, opening braces, parentheses, and brackets.</span></span>

### <a name="avoid-using-powershell-prompts-in-examples"></a><span data-ttu-id="4e794-284">Evitare di usare le richieste di PowerShell negli esempi</span><span class="sxs-lookup"><span data-stu-id="4e794-284">Avoid using PowerShell prompts in examples</span></span>

<span data-ttu-id="4e794-285">L'uso della stringa di richiesta è sconsigliato e deve essere limitato agli scenari che hanno lo scopo di illustrare l'uso della riga di comando.</span><span class="sxs-lookup"><span data-stu-id="4e794-285">Use of the prompt string is discouraged and should be limited to scenarios that are meant to illustrate command line usage.</span></span> <span data-ttu-id="4e794-286">Per la maggior parte di questi esempi, la stringa di richiesta dovrebbe essere `PS>`.</span><span class="sxs-lookup"><span data-stu-id="4e794-286">For most of these examples, the prompt string should be `PS>`.</span></span> <span data-ttu-id="4e794-287">Questa richiesta è indipendente dagli indicatori specifici del sistema operativo.</span><span class="sxs-lookup"><span data-stu-id="4e794-287">This prompt is independent of OS-specific indicators.</span></span>

<span data-ttu-id="4e794-288">Le richieste sono necessarie per gli esempi con comandi che modificano la richiesta stessa o quando il percorso visualizzato è significativo per lo scenario illustrato.</span><span class="sxs-lookup"><span data-stu-id="4e794-288">Prompts are required for examples that illustrate commands that alter the prompt or when the path displayed is significant to the scenario being illustrated.</span></span> <span data-ttu-id="4e794-289">L'esempio seguente illustra come viene modificata la richiesta quando si usa il provider del Registro di sistema.</span><span class="sxs-lookup"><span data-stu-id="4e794-289">The following example illustrates how the prompt changes when using the Registry provider.</span></span>

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

### <a name="do-not-use-aliases-in-examples"></a><span data-ttu-id="4e794-290">Non usare alias negli esempi</span><span class="sxs-lookup"><span data-stu-id="4e794-290">Do not use aliases in examples</span></span>

<span data-ttu-id="4e794-291">È consigliabile usare sempre il nome completo di tutti i cmdlet e i parametri, salvo quando si vuole specificare l'alias stesso.</span><span class="sxs-lookup"><span data-stu-id="4e794-291">You should always use the full name of all cmdlets and parameters unless you are specifically talking about the alias.</span></span> <span data-ttu-id="4e794-292">I nomi di cmdlet e parametri devono usare l'ortografia corretta definita nel codice.</span><span class="sxs-lookup"><span data-stu-id="4e794-292">Cmdlet and parameter names must use the proper spelling defined in the code.</span></span>

### <a name="using-parameters-in-examples"></a><span data-ttu-id="4e794-293">Uso di parametri negli esempi</span><span class="sxs-lookup"><span data-stu-id="4e794-293">Using parameters in examples</span></span>

<span data-ttu-id="4e794-294">Evitare l'uso di parametri posizionali.</span><span class="sxs-lookup"><span data-stu-id="4e794-294">Avoid using positional parameters.</span></span> <span data-ttu-id="4e794-295">In generale è consigliabile usare sempre il nome del parametro in un esempio, anche se il parametro è posizionale.</span><span class="sxs-lookup"><span data-stu-id="4e794-295">In general, you should use always include the parameter name in an example, even if the parameter positional.</span></span> <span data-ttu-id="4e794-296">Questo riduce la possibilità di confusione negli esempi.</span><span class="sxs-lookup"><span data-stu-id="4e794-296">This reduces the chance of confusion in your examples.</span></span>

## <a name="next-steps"></a><span data-ttu-id="4e794-297">Passaggi successivi</span><span class="sxs-lookup"><span data-stu-id="4e794-297">Next steps</span></span>

[<span data-ttu-id="4e794-298">Modifica delle informazioni di riferimento sui cmdlet</span><span class="sxs-lookup"><span data-stu-id="4e794-298">Editing cmdlet reference</span></span>](editing-cmdlet-ref.md)

<!-- External URLs -->
[platyPS]: https://github.com/PowerShell/platyPS
[markdig]: https://github.com/lunet-io/markdig
[CommonMark]: https://spec.commonmark.org/
[atx]: https://github.github.com/gfm/#atx-headings
[pascal-case]: https://en.wikipedia.org/wiki/PascalCase
[reflow]: https://marketplace.visualstudio.com/items?itemName=marvhen.reflow-markdown
