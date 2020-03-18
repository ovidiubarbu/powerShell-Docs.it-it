---
title: Modifica degli articoli di riferimento
description: Questo articolo illustra i requisiti specifici per la modifica delle informazioni di riferimento sui cmdlet e degli argomenti About nella documentazione di PowerShell.
ms.date: 03/05/2020
ms.topic: conceptual
ms.openlocfilehash: 3c6f1b4fc27ca8ece7ec30317daf4ed2a6bc9228
ms.sourcegitcommit: 18d832858a7b8ea094763afa753e0f48f01372e7
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 03/10/2020
ms.locfileid: "79060326"
---
# <a name="editing-reference-articles"></a><span data-ttu-id="b61eb-103">Modifica degli articoli di riferimento</span><span class="sxs-lookup"><span data-stu-id="b61eb-103">Editing reference articles</span></span>

<span data-ttu-id="b61eb-104">Gli articoli di riferimento sui cmdlet hanno una struttura specifica.</span><span class="sxs-lookup"><span data-stu-id="b61eb-104">Cmdlet reference articles have a specific structure.</span></span> <span data-ttu-id="b61eb-105">Questa struttura è definita da [PlatyPS][].</span><span class="sxs-lookup"><span data-stu-id="b61eb-105">This structure is defined by [PlatyPS][].</span></span>
<span data-ttu-id="b61eb-106">PlatyPS genera la Guida del cmdlet per i moduli di PowerShell in Markdown.</span><span class="sxs-lookup"><span data-stu-id="b61eb-106">PlatyPS generates the cmdlet help for PowerShell modules in Markdown.</span></span> <span data-ttu-id="b61eb-107">Dopo la modifica dei file markdown, PlatyPS viene usato per creare i file della Guida MAML usati dal cmdlet `Get-Help`.</span><span class="sxs-lookup"><span data-stu-id="b61eb-107">After editing the Markdown files, PlatyPS is used create the MAML help files used by the `Get-Help` cmdlet.</span></span>

<span data-ttu-id="b61eb-108">PlatyPS ha uno schema hardcoded per le informazioni di riferimento del cmdlet scritte nel codice.</span><span class="sxs-lookup"><span data-stu-id="b61eb-108">PlatyPS has a hard-coded schema for cmdlet reference that is written into the code.</span></span> <span data-ttu-id="b61eb-109">Il documento [platyPS.schema.md][] tenta di descrivere questa struttura.</span><span class="sxs-lookup"><span data-stu-id="b61eb-109">The [platyPS.schema.md][] document attempts to describe this structure.</span></span> <span data-ttu-id="b61eb-110">Le violazioni dello schema causano errori di compilazione che è necessario correggere prima che il contributo sia accettato.</span><span class="sxs-lookup"><span data-stu-id="b61eb-110">Schema violations cause build errors that must be fixed before we can accept your contribution.</span></span>

## <a name="general-guidelines"></a><span data-ttu-id="b61eb-111">Linee guida generali</span><span class="sxs-lookup"><span data-stu-id="b61eb-111">General guidelines</span></span>

- <span data-ttu-id="b61eb-112">Non rimuovere le strutture di intestazione.</span><span class="sxs-lookup"><span data-stu-id="b61eb-112">Do not remove any of the header structures.</span></span> <span data-ttu-id="b61eb-113">PlatyPS accetta uno specifico set di intestazioni.</span><span class="sxs-lookup"><span data-stu-id="b61eb-113">PlatyPS expects a specific set of headers.</span></span>
- <span data-ttu-id="b61eb-114">Le intestazioni **Input type** e **Output type** devono avere un tipo.</span><span class="sxs-lookup"><span data-stu-id="b61eb-114">The **Input type** and **Output type** headers must have a type.</span></span> <span data-ttu-id="b61eb-115">Se il cmdlet non accetta input o restituisce un valore, usare il valore `None`.</span><span class="sxs-lookup"><span data-stu-id="b61eb-115">If the cmdlet does not take input or return a value then use the value `None`.</span></span>
- <span data-ttu-id="b61eb-116">I blocchi di codice delimitati sono consentiti solo nella sezione [Examples](#structuring-examples).</span><span class="sxs-lookup"><span data-stu-id="b61eb-116">Fenced code blocks are only allowed in the [Examples](#structuring-examples) section.</span></span>
- <span data-ttu-id="b61eb-117">Gli intervalli di codice incorporati possono essere usati in qualsiasi paragrafo.</span><span class="sxs-lookup"><span data-stu-id="b61eb-117">Inline code spans can be used in any paragraph.</span></span>

## <a name="formatting-about_-files"></a><span data-ttu-id="b61eb-118">Formattazione dei file About_</span><span class="sxs-lookup"><span data-stu-id="b61eb-118">Formatting About_ files</span></span>

<span data-ttu-id="b61eb-119">I file `About_*` vengono ora elaborati da [Pandoc][], anziché da PlatyPS.</span><span class="sxs-lookup"><span data-stu-id="b61eb-119">`About_*` files are now processed by [Pandoc][], instead of PlatyPS.</span></span> <span data-ttu-id="b61eb-120">I file `About_*` sono formattati in modo da ottenere la massima compatibilità con tutte le versioni di PowerShell e con gli strumenti di pubblicazione.</span><span class="sxs-lookup"><span data-stu-id="b61eb-120">`About_*` files are formatted for the best compatibility across all versions of PowerShell and with the publishing tools.</span></span>

<span data-ttu-id="b61eb-121">Linee guida di base per la formattazione:</span><span class="sxs-lookup"><span data-stu-id="b61eb-121">Basic formatting guidelines:</span></span>

- <span data-ttu-id="b61eb-122">Limitare le righe a 80 caratteri</span><span class="sxs-lookup"><span data-stu-id="b61eb-122">Limit lines to 80 characters</span></span>
- <span data-ttu-id="b61eb-123">Il limite per i blocchi di codice e le tabelle è di 76 caratteri perché Pandoc imposta un rientro di quattro spazi durante la conversione in testo normale</span><span class="sxs-lookup"><span data-stu-id="b61eb-123">Code blocks and tables are limited to 76 characters because Pandoc indents these by four spaces during conversion to plain text</span></span>
- <span data-ttu-id="b61eb-124">Le tabelle devono rientrare nei 76 caratteri</span><span class="sxs-lookup"><span data-stu-id="b61eb-124">Tables need to fit within 76 characters</span></span>
  - <span data-ttu-id="b61eb-125">Mandare a capo manualmente il contenuto delle celle su più righe</span><span class="sxs-lookup"><span data-stu-id="b61eb-125">Manually wrap contents of cells across multiple lines</span></span>
  - <span data-ttu-id="b61eb-126">Usare i caratteri `|` di apertura e chiusura in ogni riga</span><span class="sxs-lookup"><span data-stu-id="b61eb-126">Use opening and closing `|` characters on each line</span></span>
  - <span data-ttu-id="b61eb-127">Vedere un esempio funzionante in [about_Comparison_Operators][about-example]</span><span class="sxs-lookup"><span data-stu-id="b61eb-127">See a working example in [about_Comparison_Operators][about-example]</span></span>
- <span data-ttu-id="b61eb-128">Uso dei caratteri speciali Pandoc `\`,`$` e `<`</span><span class="sxs-lookup"><span data-stu-id="b61eb-128">Using Pandoc special characters `\`,`$`, and `<`</span></span>
  - <span data-ttu-id="b61eb-129">All'interno di un'intestazione, questi caratteri devono essere preceduti dal carattere di escape `\` o racchiusi tra apici inversi (`` ` ``)</span><span class="sxs-lookup"><span data-stu-id="b61eb-129">Within a header - these characters must be escaped using a leading `\` character or enclosed in backticks (`` ` ``)</span></span>
  - <span data-ttu-id="b61eb-130">All'interno di un paragrafo, questi caratteri devono essere inseriti in intervalli di codice.</span><span class="sxs-lookup"><span data-stu-id="b61eb-130">Within a paragraph, these characters should be put into code spans.</span></span> <span data-ttu-id="b61eb-131">Ad esempio:</span><span class="sxs-lookup"><span data-stu-id="b61eb-131">For example:</span></span>

    ~~~markdown
    ### The purpose of the \$foo variable

    The `$foo` variable is used to store ...
    ~~~

## <a name="structuring-examples"></a><span data-ttu-id="b61eb-132">Formato per gli esempi</span><span class="sxs-lookup"><span data-stu-id="b61eb-132">Structuring examples</span></span>

<span data-ttu-id="b61eb-133">Nello schema PlatyPS l'intestazione **EXAMPLES** è un'intestazione H2 e ogni esempio è un'intestazione H3.</span><span class="sxs-lookup"><span data-stu-id="b61eb-133">In the PlatyPS schema, the **EXAMPLES** header is an H2 header and each example is an H3 header.</span></span>

<span data-ttu-id="b61eb-134">All'interno di un esempio, lo schema non consente la separazione dei blocchi di codice tramite paragrafi.</span><span class="sxs-lookup"><span data-stu-id="b61eb-134">Within an example, the schema does not allow code blocks to be separated by paragraphs.</span></span> <span data-ttu-id="b61eb-135">Lo schema supportato è:</span><span class="sxs-lookup"><span data-stu-id="b61eb-135">The supported schema is:</span></span>

```
### Example #X title

0 or more paragraphs
1 or more code blocks
0 or more paragraphs.
```

<span data-ttu-id="b61eb-136">Numerare ogni esempio e aggiungere un breve titolo.</span><span class="sxs-lookup"><span data-stu-id="b61eb-136">Number each example and add a brief title.</span></span>

<span data-ttu-id="b61eb-137">Ad esempio:</span><span class="sxs-lookup"><span data-stu-id="b61eb-137">For example:</span></span>

### <a name="example-1-get-cmdlets-functions-and-aliases"></a><span data-ttu-id="b61eb-138">Esempio 1: Ottenere cmdlet, funzioni e alias</span><span class="sxs-lookup"><span data-stu-id="b61eb-138">Example 1: Get cmdlets, functions, and aliases</span></span>

<span data-ttu-id="b61eb-139">Questo comando ottiene i cmdlet, le funzioni e gli alias di PowerShell installati nel computer.</span><span class="sxs-lookup"><span data-stu-id="b61eb-139">This command gets the PowerShell cmdlets, functions, and aliases that are installed on the computer.</span></span>

```powershell
Get-Command
```

### <a name="example-2-get-commands-in-the-current-session"></a><span data-ttu-id="b61eb-140">Esempio 2: Ottenere i comandi nella sessione corrente</span><span class="sxs-lookup"><span data-stu-id="b61eb-140">Example 2: Get commands in the current session</span></span>

```powershell
Get-Command -ListImported
```

## <a name="next-steps"></a><span data-ttu-id="b61eb-141">Passaggi successivi</span><span class="sxs-lookup"><span data-stu-id="b61eb-141">Next steps</span></span>

[<span data-ttu-id="b61eb-142">Elenco di controllo editoriale</span><span class="sxs-lookup"><span data-stu-id="b61eb-142">Editorial checklist</span></span>](editorial-checklist.md)

<!-- link references -->
[PlatyPS]: https://github.com/powershell/platyps
[platyPS.schema.md]: https://github.com/PowerShell/platyPS/blob/master/platyPS.schema.md
[issue1806]: https://github.com/MicrosoftDocs/PowerShell-Docs/issues/1806
[about-example]: https://github.com/MicrosoftDocs/PowerShell-Docs/reference/5.1/Microsoft.PowerShell.Core/About/about_Comparison_Operators.md
[Pandoc]: https://pandoc.org
