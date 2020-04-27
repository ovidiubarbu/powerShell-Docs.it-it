---
title: Modifica degli articoli di riferimento
description: Questo articolo illustra i requisiti specifici per la modifica delle informazioni di riferimento sui cmdlet e degli argomenti About nella documentazione di PowerShell.
ms.date: 03/05/2020
ms.topic: conceptual
ms.openlocfilehash: e135f6cc81ba7537a535a08421e1ca9b2b2af573
ms.sourcegitcommit: 6545c60578f7745be015111052fd7769f8289296
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/22/2020
ms.locfileid: "81624772"
---
# <a name="editing-reference-articles"></a><span data-ttu-id="b7943-103">Modifica degli articoli di riferimento</span><span class="sxs-lookup"><span data-stu-id="b7943-103">Editing reference articles</span></span>

<span data-ttu-id="b7943-104">Gli articoli di riferimento sui cmdlet hanno una struttura specifica.</span><span class="sxs-lookup"><span data-stu-id="b7943-104">Cmdlet reference articles have a specific structure.</span></span> <span data-ttu-id="b7943-105">Questa struttura è definita da [PlatyPS][].</span><span class="sxs-lookup"><span data-stu-id="b7943-105">This structure is defined by [PlatyPS][].</span></span>
<span data-ttu-id="b7943-106">PlatyPS genera la Guida del cmdlet per i moduli di PowerShell in Markdown.</span><span class="sxs-lookup"><span data-stu-id="b7943-106">PlatyPS generates the cmdlet help for PowerShell modules in Markdown.</span></span> <span data-ttu-id="b7943-107">Dopo la modifica dei file markdown, PlatyPS viene usato per creare i file della Guida MAML usati dal cmdlet `Get-Help`.</span><span class="sxs-lookup"><span data-stu-id="b7943-107">After editing the Markdown files, PlatyPS is used create the MAML help files used by the `Get-Help` cmdlet.</span></span>

<span data-ttu-id="b7943-108">PlatyPS ha uno schema hardcoded per le informazioni di riferimento del cmdlet scritte nel codice.</span><span class="sxs-lookup"><span data-stu-id="b7943-108">PlatyPS has a hard-coded schema for cmdlet reference that is written into the code.</span></span> <span data-ttu-id="b7943-109">Il documento [platyPS.schema.md][] tenta di descrivere questa struttura.</span><span class="sxs-lookup"><span data-stu-id="b7943-109">The [platyPS.schema.md][] document attempts to describe this structure.</span></span> <span data-ttu-id="b7943-110">Le violazioni dello schema causano errori di compilazione che è necessario correggere prima che il contributo sia accettato.</span><span class="sxs-lookup"><span data-stu-id="b7943-110">Schema violations cause build errors that must be fixed before we can accept your contribution.</span></span>

## <a name="general-guidelines"></a><span data-ttu-id="b7943-111">Linee guida generali</span><span class="sxs-lookup"><span data-stu-id="b7943-111">General guidelines</span></span>

- <span data-ttu-id="b7943-112">Non rimuovere le strutture di intestazione.</span><span class="sxs-lookup"><span data-stu-id="b7943-112">Do not remove any of the header structures.</span></span> <span data-ttu-id="b7943-113">PlatyPS accetta uno specifico set di intestazioni.</span><span class="sxs-lookup"><span data-stu-id="b7943-113">PlatyPS expects a specific set of headers.</span></span>
- <span data-ttu-id="b7943-114">Le intestazioni **Input type** e **Output type** devono avere un tipo.</span><span class="sxs-lookup"><span data-stu-id="b7943-114">The **Input type** and **Output type** headers must have a type.</span></span> <span data-ttu-id="b7943-115">Se il cmdlet non accetta input o restituisce un valore, usare il valore `None`.</span><span class="sxs-lookup"><span data-stu-id="b7943-115">If the cmdlet does not take input or return a value then use the value `None`.</span></span>
- <span data-ttu-id="b7943-116">I blocchi di codice delimitati sono consentiti solo nella sezione [Examples](#structuring-examples).</span><span class="sxs-lookup"><span data-stu-id="b7943-116">Fenced code blocks are only allowed in the [Examples](#structuring-examples) section.</span></span>
- <span data-ttu-id="b7943-117">Gli intervalli di codice incorporati possono essere usati in qualsiasi paragrafo.</span><span class="sxs-lookup"><span data-stu-id="b7943-117">Inline code spans can be used in any paragraph.</span></span>

## <a name="formatting-about_-files"></a><span data-ttu-id="b7943-118">Formattazione dei file About_</span><span class="sxs-lookup"><span data-stu-id="b7943-118">Formatting About_ files</span></span>

<span data-ttu-id="b7943-119">I file `About_*` sono scritti in Markdown ma vengono spediti come file di testo normale.</span><span class="sxs-lookup"><span data-stu-id="b7943-119">`About_*` files are written in Markdown but are shipped as plain text files.</span></span> <span data-ttu-id="b7943-120">Per convertire il Markdown in testo normale si usa [Pandoc][].</span><span class="sxs-lookup"><span data-stu-id="b7943-120">We use [Pandoc][] to convert the Markdown to plain text.</span></span> <span data-ttu-id="b7943-121">I file `About_*` sono formattati in modo da ottenere la massima compatibilità con tutte le versioni di PowerShell e con gli strumenti di pubblicazione.</span><span class="sxs-lookup"><span data-stu-id="b7943-121">`About_*` files are formatted for the best compatibility across all versions of PowerShell and with the publishing tools.</span></span>

<span data-ttu-id="b7943-122">Linee guida di base per la formattazione:</span><span class="sxs-lookup"><span data-stu-id="b7943-122">Basic formatting guidelines:</span></span>

- <span data-ttu-id="b7943-123">Limitare le righe a 80 caratteri.</span><span class="sxs-lookup"><span data-stu-id="b7943-123">Limit lines to 80 characters.</span></span> <span data-ttu-id="b7943-124">In Pandoc alcuni blocchi Markdown vengono rientrati e devono quindi essere modificati.</span><span class="sxs-lookup"><span data-stu-id="b7943-124">Pandoc indents some Markdown blocks so those block must be adjusted.</span></span>
  - <span data-ttu-id="b7943-125">I blocchi di codice sono limitati a 76 caratteri</span><span class="sxs-lookup"><span data-stu-id="b7943-125">Code blocks are limited to 76 characters</span></span>
  - <span data-ttu-id="b7943-126">Le tabelle sono limitate a 76 caratteri</span><span class="sxs-lookup"><span data-stu-id="b7943-126">Tables are limited 76 characters</span></span>
  - <span data-ttu-id="b7943-127">Le citazioni e gli avvisi sono limitati a 78 caratteri</span><span class="sxs-lookup"><span data-stu-id="b7943-127">Blockquotes (and Alerts) are limited 78 characters</span></span>

- <span data-ttu-id="b7943-128">Uso dei metacaratteri speciali Pandoc `\`,`$` e `<`</span><span class="sxs-lookup"><span data-stu-id="b7943-128">Using Pandoc's special meta-characters `\`,`$`, and `<`</span></span>
  - <span data-ttu-id="b7943-129">All'interno di un'intestazione, questi caratteri devono essere preceduti dal carattere di escape `\` o racchiusi in intervalli di codice con apici inversi (`` ` ``)</span><span class="sxs-lookup"><span data-stu-id="b7943-129">Within a header - these characters must be escaped using a leading `\` character or enclosed in code spans using backticks (`` ` ``)</span></span>
  - <span data-ttu-id="b7943-130">All'interno di un paragrafo, questi caratteri devono essere inseriti in intervalli di codice.</span><span class="sxs-lookup"><span data-stu-id="b7943-130">Within a paragraph, these characters should be put into code spans.</span></span> <span data-ttu-id="b7943-131">Ad esempio:</span><span class="sxs-lookup"><span data-stu-id="b7943-131">For example:</span></span>

    ~~~markdown
    ### The purpose of the \$foo variable

    The `$foo` variable is used to store ...
    ~~~

- <span data-ttu-id="b7943-132">Le tabelle devono rientrare nei 76 caratteri</span><span class="sxs-lookup"><span data-stu-id="b7943-132">Tables need to fit within 76 characters</span></span>
  - <span data-ttu-id="b7943-133">Mandare a capo manualmente il contenuto delle celle su più righe</span><span class="sxs-lookup"><span data-stu-id="b7943-133">Manually wrap contents of cells across multiple lines</span></span>
  - <span data-ttu-id="b7943-134">Usare i caratteri `|` di apertura e chiusura in ogni riga</span><span class="sxs-lookup"><span data-stu-id="b7943-134">Use opening and closing `|` characters on each line</span></span>
  - <span data-ttu-id="b7943-135">Nell'esempio seguente viene illustrato come costruire correttamente una tabella contenente informazioni in cui viene eseguito il wrapping su più righe all'interno di una cella.</span><span class="sxs-lookup"><span data-stu-id="b7943-135">The following example illustrates how to properly construct a table that contains information that wraps on multiple lines within a cell.</span></span>

    ~~~markdown
    ```
    |Operator|Description                |Example                          |
    |--------|---------------------------|---------------------------------|
    |`-is`   |Returns TRUE when the input|`(get-date) -is [DateTime]`      |
    |        |is an instance of the      |`True`                           |
    |        |specified .NET type.       |                                 |
    |`-isNot`|Returns TRUE when the input|`(get-date) -isNot [DateTime]`   |
    |        |not an instance of the     |`False`                          |
    |        |specified.NET type.        |                                 |
    |`-as`   |Converts the input to the  |`"5/7/07" -as [DateTime]`        |
    |        |specified .NET type.       |`Monday, May 7, 2007 12:00:00 AM`|
    ```
    ~~~

    > [!NOTE]
    > <span data-ttu-id="b7943-136">Il limite di 76 colonne si applica solo agli argomenti `About_*`.</span><span class="sxs-lookup"><span data-stu-id="b7943-136">The 76-column limitation applies only to `About_*` topics.</span></span> <span data-ttu-id="b7943-137">È possibile usare colonne di grandi dimensioni in articoli concettuali o di riferimento sui cmdlet.</span><span class="sxs-lookup"><span data-stu-id="b7943-137">You can use wide columns in conceptual or cmdlet reference articles.</span></span>

## <a name="structuring-examples"></a><span data-ttu-id="b7943-138">Formato per gli esempi</span><span class="sxs-lookup"><span data-stu-id="b7943-138">Structuring examples</span></span>

<span data-ttu-id="b7943-139">Nello schema PlatyPS l'intestazione **EXAMPLES** è un'intestazione H2 e ogni esempio è un'intestazione H3.</span><span class="sxs-lookup"><span data-stu-id="b7943-139">In the PlatyPS schema, the **EXAMPLES** header is an H2 header and each example is an H3 header.</span></span>

<span data-ttu-id="b7943-140">All'interno di un esempio, lo schema non consente la separazione dei blocchi di codice tramite paragrafi.</span><span class="sxs-lookup"><span data-stu-id="b7943-140">Within an example, the schema does not allow code blocks to be separated by paragraphs.</span></span> <span data-ttu-id="b7943-141">Lo schema supportato è:</span><span class="sxs-lookup"><span data-stu-id="b7943-141">The supported schema is:</span></span>

```
### Example #X title

0 or more paragraphs
1 or more code blocks
0 or more paragraphs.
```

<span data-ttu-id="b7943-142">Numerare ogni esempio e aggiungere un breve titolo.</span><span class="sxs-lookup"><span data-stu-id="b7943-142">Number each example and add a brief title.</span></span>

<span data-ttu-id="b7943-143">Ad esempio:</span><span class="sxs-lookup"><span data-stu-id="b7943-143">For example:</span></span>

### <a name="example-1-get-cmdlets-functions-and-aliases"></a><span data-ttu-id="b7943-144">Esempio 1: Ottenere cmdlet, funzioni e alias</span><span class="sxs-lookup"><span data-stu-id="b7943-144">Example 1: Get cmdlets, functions, and aliases</span></span>

<span data-ttu-id="b7943-145">Questo comando ottiene i cmdlet, le funzioni e gli alias di PowerShell installati nel computer.</span><span class="sxs-lookup"><span data-stu-id="b7943-145">This command gets the PowerShell cmdlets, functions, and aliases that are installed on the computer.</span></span>

```powershell
Get-Command
```

### <a name="example-2-get-commands-in-the-current-session"></a><span data-ttu-id="b7943-146">Esempio 2: Ottenere i comandi nella sessione corrente</span><span class="sxs-lookup"><span data-stu-id="b7943-146">Example 2: Get commands in the current session</span></span>

```powershell
Get-Command -ListImported
```

## <a name="next-steps"></a><span data-ttu-id="b7943-147">Passaggi successivi</span><span class="sxs-lookup"><span data-stu-id="b7943-147">Next steps</span></span>

[<span data-ttu-id="b7943-148">Elenco di controllo editoriale</span><span class="sxs-lookup"><span data-stu-id="b7943-148">Editorial checklist</span></span>](editorial-checklist.md)

<!-- link references -->
[PlatyPS]: https://github.com/powershell/platyps
[platyPS.schema.md]: https://github.com/PowerShell/platyPS/blob/master/platyPS.schema.md
[issue1806]: https://github.com/MicrosoftDocs/PowerShell-Docs/issues/1806
[about-example]: /PowerShell/module/Microsoft.PowerShell.Core/About/about_Comparison_Operators
[Pandoc]: https://pandoc.org
