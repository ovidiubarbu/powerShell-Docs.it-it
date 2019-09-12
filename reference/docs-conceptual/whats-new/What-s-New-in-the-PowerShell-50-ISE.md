---
ms.date: 09/06/2019
keywords: powershell,cmdlet
title: Novità di PowerShell 5.0 ISE
ms.openlocfilehash: a719baef0da1600f0a5377e1b72c81b67e37eef2
ms.sourcegitcommit: a74ae7ed089301992fed201fbe55d827a622afa0
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 09/06/2019
ms.locfileid: "70746215"
---
# <a name="whats-new-in-the-windows-powershell-50-ise"></a><span data-ttu-id="7d52b-103">Novità di Windows PowerShell 5.0 ISE</span><span class="sxs-lookup"><span data-stu-id="7d52b-103">What's New in the Windows PowerShell 5.0 ISE</span></span>

<span data-ttu-id="7d52b-104">Questo argomento illustra le funzionalità nuove e aggiornate introdotte nelle versioni di Windows PowerShell Integrated Scripting Environment (ISE).</span><span class="sxs-lookup"><span data-stu-id="7d52b-104">This topic explains the new and updated features that have been introduced in versions of Windows PowerShell Integrated Scripting Environment (ISE).</span></span>

## <a name="feature-description"></a><span data-ttu-id="7d52b-105">Descrizione delle funzionalità</span><span class="sxs-lookup"><span data-stu-id="7d52b-105">Feature description</span></span>

<span data-ttu-id="7d52b-106">Windows PowerShell ISE è un'applicazione host che consente di scrivere, eseguire e testare script e moduli in un ambiente grafico e intuitivo.</span><span class="sxs-lookup"><span data-stu-id="7d52b-106">The Windows PowerShell ISE is a host application that enables you to write, run, and test scripts and modules in a graphical and intuitive environment.</span></span> <span data-ttu-id="7d52b-107">Le principali funzionalità, come la sintassi contraddistinta dal colore, la funzionalità di completamento tramite tasto TAB, il debug visivo, la conformità a Unicode e la Guida sensibile al contesto garantiscono un'esperienza di scripting più dettagliata.</span><span class="sxs-lookup"><span data-stu-id="7d52b-107">Key features such as syntax-coloring, tab completion, visual debugging, Unicode compliance, and context-sensitive Help provide a rich scripting experience.</span></span>

<span data-ttu-id="7d52b-108">Per altre informazioni, vedere [Introduzione a Windows PowerShell ISE](../components/ise/Introducing-the-Windows-PowerShell-ISE.md).</span><span class="sxs-lookup"><span data-stu-id="7d52b-108">For more information, see [Introducing the Windows PowerShell ISE](../components/ise/Introducing-the-Windows-PowerShell-ISE.md).</span></span>

<span data-ttu-id="7d52b-109">Nella tabella seguente sono elencate alcune delle funzionalità nuove e modificate per questa versione di Windows PowerShell ISE in Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="7d52b-109">The following table lists the new and changed features for this release of Windows PowerShell ISE in Windows PowerShell.</span></span>

## <a name="intellisense"></a><span data-ttu-id="7d52b-110">IntelliSense</span><span class="sxs-lookup"><span data-stu-id="7d52b-110">IntelliSense</span></span>

> <span data-ttu-id="7d52b-111">Funzionalità aggiunta in ISE 3.0</span><span class="sxs-lookup"><span data-stu-id="7d52b-111">Added in ISE 3.0</span></span>

<span data-ttu-id="7d52b-112">IntelliSense è una funzionalità di assistenza per il completamento automatico che fa parte di Windows PowerShell ISE.</span><span class="sxs-lookup"><span data-stu-id="7d52b-112">IntelliSense is an automatic-completion assistance feature that is part of Windows PowerShell ISE.</span></span>
<span data-ttu-id="7d52b-113">IntelliSense consente di visualizzare menu selezionabili di cmdlet, parametri, valori di parametri, file o cartelle potenzialmente corrispondenti durante la digitazione.</span><span class="sxs-lookup"><span data-stu-id="7d52b-113">IntelliSense displays clickable menus of potentially matching cmdlets, parameters, parameter values, files, or folders as you type.</span></span>

<span data-ttu-id="7d52b-114">**Valore aggiunto da queste modifiche**</span><span class="sxs-lookup"><span data-stu-id="7d52b-114">**What value does this change add?**</span></span>

<span data-ttu-id="7d52b-115">Con l'aggiunta di IntelliSense è più semplice individuare i cmdlet e la sintassi durante l'uso di Windows PowerShell ISE per creare script.</span><span class="sxs-lookup"><span data-stu-id="7d52b-115">With the addition of IntelliSense, it's easier to discover cmdlets and syntax when you use Windows PowerShell ISE to create scripts.</span></span> <span data-ttu-id="7d52b-116">È anche possibile usare Windows PowerShell ISE per imparare a usare Windows PowerShell durante la creazione di nuovi script.</span><span class="sxs-lookup"><span data-stu-id="7d52b-116">You can also use Windows PowerShell ISE to learn Windows PowerShell while you create new scripts.</span></span>

<span data-ttu-id="7d52b-117">**Differenze di funzionamento**</span><span class="sxs-lookup"><span data-stu-id="7d52b-117">**What works differently?**</span></span>

<span data-ttu-id="7d52b-118">Quando si digitano cmdlet in Windows PowerShell ISE viene visualizzato un menu scorrevole e selezionabile, che consente di cercare e selezionare i comandi appropriati.</span><span class="sxs-lookup"><span data-stu-id="7d52b-118">When you type cmdlets in the Windows PowerShell ISE, a scrollable and clickable menu displays, allowing you to browse and select the appropriate commands.</span></span>

## <a name="snippets"></a><span data-ttu-id="7d52b-119">Frammenti di codice</span><span class="sxs-lookup"><span data-stu-id="7d52b-119">Snippets</span></span>

> <span data-ttu-id="7d52b-120">Funzionalità aggiunta in ISE 3.0</span><span class="sxs-lookup"><span data-stu-id="7d52b-120">Added in ISE 3.0</span></span>

<span data-ttu-id="7d52b-121">I *frammenti di codice* sono brevi sezioni di codice di Windows PowerShell che è possibile inserire negli script creati in Windows PowerShell ISE.</span><span class="sxs-lookup"><span data-stu-id="7d52b-121">*Snippets* are short sections of Windows PowerShell code that you can insert into the scripts you create in Windows PowerShell ISE.</span></span> <span data-ttu-id="7d52b-122">Windows PowerShell ISE include un set predefinito di frammenti di codice.</span><span class="sxs-lookup"><span data-stu-id="7d52b-122">Windows PowerShell ISE comes with a default set of snippets.</span></span> <span data-ttu-id="7d52b-123">È possibile aggiungere frammenti di codice con il cmdlet `New-Snippet` mentre si lavora in Windows PowerShell ISE.</span><span class="sxs-lookup"><span data-stu-id="7d52b-123">You can add snippets by using the `New-Snippet` cmdlet while working in Windows PowerShell ISE.</span></span>

<span data-ttu-id="7d52b-124">**Valore aggiunto da queste modifiche**</span><span class="sxs-lookup"><span data-stu-id="7d52b-124">**What value does this change add?**</span></span>

<span data-ttu-id="7d52b-125">Con i frammenti di codice è possibile assemblare e creare script rapidamente per automatizzare l'ambiente.</span><span class="sxs-lookup"><span data-stu-id="7d52b-125">By using snippets, you can quickly assemble and create scripts to automate your environment.</span></span>

<span data-ttu-id="7d52b-126">**Differenze di funzionamento**</span><span class="sxs-lookup"><span data-stu-id="7d52b-126">**What works differently?**</span></span>

<span data-ttu-id="7d52b-127">Per usare i frammenti di codice in Windows PowerShell 3.0 o versione successiva, scegliere **Avvia frammenti** dal menu **Modifica** o premere <kbd>CTRL</kbd>+<kbd>J</kbd>.</span><span class="sxs-lookup"><span data-stu-id="7d52b-127">To use snippets in Windows PowerShell 3.0 or later, on the **Edit** menu, click **Start Snippets**, or press <kbd>Ctrl</kbd>+<kbd>J</kbd>.</span></span>

## <a name="add-on-tools"></a><span data-ttu-id="7d52b-128">Strumenti aggiuntivi</span><span class="sxs-lookup"><span data-stu-id="7d52b-128">Add-on tools</span></span>

> <span data-ttu-id="7d52b-129">Funzionalità aggiunta in PowerShell 3.0</span><span class="sxs-lookup"><span data-stu-id="7d52b-129">Added in PowerShell 3.0</span></span>

<span data-ttu-id="7d52b-130">Windows PowerShell ISE supporta ora strumenti aggiuntivi che usano il modello a oggetti.</span><span class="sxs-lookup"><span data-stu-id="7d52b-130">Windows PowerShell ISE now supports add-on tools using the object model.</span></span> <span data-ttu-id="7d52b-131">Questi componenti aggiuntivi sono controlli di Windows Presentation Foundation (WPF) che vengono visualizzati come riquadro verticale o orizzontale nella console.</span><span class="sxs-lookup"><span data-stu-id="7d52b-131">These add-ons are Windows Presentation Foundation (WPF) controls that are displayed as a vertical or horizontal pane in the console.</span></span> <span data-ttu-id="7d52b-132">Più strumenti aggiuntivi di un riquadro vengono visualizzati come controllo a schede.</span><span class="sxs-lookup"><span data-stu-id="7d52b-132">Multiple add-on tools in a pane are displayed as a tabbed control.</span></span> <span data-ttu-id="7d52b-133">È inoltre possibile aggiungere o rimuovere strumenti aggiuntivi prodotti da fornitori non Microsoft.</span><span class="sxs-lookup"><span data-stu-id="7d52b-133">You can also add or remove add-on tools that are produced by non-Microsoft parties.</span></span> <span data-ttu-id="7d52b-134">Per altre informazioni, vedere [Scopo del modello a oggetti di scripting di Windows PowerShell ISE](../components/ise/object-model/Purpose-of-the-Windows-PowerShell-ISE-Scripting-Object-Model.md).</span><span class="sxs-lookup"><span data-stu-id="7d52b-134">For more information, see [The Purpose of the Windows PowerShell ISE Scripting Object Model](../components/ise/object-model/Purpose-of-the-Windows-PowerShell-ISE-Scripting-Object-Model.md).</span></span>

<span data-ttu-id="7d52b-135">**Valore aggiunto da queste modifiche**</span><span class="sxs-lookup"><span data-stu-id="7d52b-135">**What value does this change add?**</span></span>

<span data-ttu-id="7d52b-136">I componenti aggiuntivi consentono di estendere e personalizzare Windows PowerShell ISE con strumenti che aggiungono funzionalità e migliorano l'esperienza di scripting.</span><span class="sxs-lookup"><span data-stu-id="7d52b-136">Add-ons allow you to extend and customize Windows PowerShell ISE with tools that add functionality and enhance your scripting experience.</span></span>

<span data-ttu-id="7d52b-137">**Differenze di funzionamento**</span><span class="sxs-lookup"><span data-stu-id="7d52b-137">**What works differently?**</span></span>

<span data-ttu-id="7d52b-138">Windows PowerShell ISE 3.0 e le versioni successive includono il componente aggiuntivo **Comandi**.</span><span class="sxs-lookup"><span data-stu-id="7d52b-138">Windows PowerShell ISE 3.0 and later come with the **Commands** add-on.</span></span> <span data-ttu-id="7d52b-139">Il componente aggiuntivo **Comandi** consente di esplorare i cmdlet e accedere alla Guida sui cmdlet a fianco dei riquadri **Script** e **Console**.</span><span class="sxs-lookup"><span data-stu-id="7d52b-139">The **Commands** add-on allows you to browse cmdlets, and access help about the cmdlets side-by-side with the **Script** and **Console** Panes.</span></span>

<span data-ttu-id="7d52b-140">È possibile trovare altri componenti aggiuntivi tramite il comando **Apri sito Web strumenti aggiuntivi** nel menu **Componenti aggiuntivi**.</span><span class="sxs-lookup"><span data-stu-id="7d52b-140">Additional add-ons can be found by using the **Open Add-on Tools Website** command on the **Add-ons** menu.</span></span>

## <a name="restart-manager-and-auto-save"></a><span data-ttu-id="7d52b-141">Gestione riavvio e salvataggio automatico</span><span class="sxs-lookup"><span data-stu-id="7d52b-141">Restart manager and auto-save</span></span>

> <span data-ttu-id="7d52b-142">Funzionalità aggiunta in PowerShell 3.0</span><span class="sxs-lookup"><span data-stu-id="7d52b-142">Added in PowerShell 3.0</span></span>

<span data-ttu-id="7d52b-143">Windows PowerShell ISE ora salva gli script aperti automaticamente ogni due minuti, in una posizione separata.</span><span class="sxs-lookup"><span data-stu-id="7d52b-143">Windows PowerShell ISE now automatically saves your open scripts every two minutes, in a separate location.</span></span> <span data-ttu-id="7d52b-144">Quando Windows PowerShell ISE viene riavviato dopo un arresto anomalo o un riavvio imprevisto, ripristina gli script aperti nell'ultima sessione, anche se non sono stati salvati.</span><span class="sxs-lookup"><span data-stu-id="7d52b-144">When Windows PowerShell ISE restarts after an unexpected crash or reboot, it recovers scripts that were open in the last session, even if the scripts weren't saved.</span></span>

<span data-ttu-id="7d52b-145">Per modificare l'intervallo di salvataggio automatico eseguire il comando seguente nel riquadro della console: `$psise.Options.AutoSaveMinuteInterval`.</span><span class="sxs-lookup"><span data-stu-id="7d52b-145">To change the automatic saving interval, run the following command in the Console pane: `$psise.Options.AutoSaveMinuteInterval`.</span></span>

<span data-ttu-id="7d52b-146">**Valore aggiunto da queste modifiche**</span><span class="sxs-lookup"><span data-stu-id="7d52b-146">**What value does this change add?**</span></span>

<span data-ttu-id="7d52b-147">È ora possibile lavorare all'interno di Windows PowerShell ISE sapendo che gli script aperti vengono salvati automaticamente.</span><span class="sxs-lookup"><span data-stu-id="7d52b-147">You can now work within Windows PowerShell ISE knowing that your open scripts are automatically saved.</span></span>

<span data-ttu-id="7d52b-148">**Differenze di funzionamento**</span><span class="sxs-lookup"><span data-stu-id="7d52b-148">**What works differently?**</span></span>

<span data-ttu-id="7d52b-149">Windows PowerShell ISE 2.0 non salva gli script automaticamente.</span><span class="sxs-lookup"><span data-stu-id="7d52b-149">Windows PowerShell ISE 2.0 doesn't save the scripts automatically.</span></span>

## <a name="most-recently-used-list"></a><span data-ttu-id="7d52b-150">Elenco degli elementi usati di recente</span><span class="sxs-lookup"><span data-stu-id="7d52b-150">Most-recently used list</span></span>

> <span data-ttu-id="7d52b-151">Funzionalità aggiunta in PowerShell 3.0</span><span class="sxs-lookup"><span data-stu-id="7d52b-151">Added in PowerShell 3.0</span></span>

<span data-ttu-id="7d52b-152">Windows PowerShell ISE ora include un elenco dei file usati di recente.</span><span class="sxs-lookup"><span data-stu-id="7d52b-152">Windows PowerShell ISE now has a most-recently used list for files.</span></span> <span data-ttu-id="7d52b-153">Quando si apre un file in Windows PowerShell ISE, il file viene aggiunto all'elenco degli elementi usati di recente nel menu **File**.</span><span class="sxs-lookup"><span data-stu-id="7d52b-153">When you open a file in Windows PowerShell ISE, the file is added to the most-recently used list on the **File** menu.</span></span>

<span data-ttu-id="7d52b-154">Per modificare il numero predefinito di file nell'elenco degli elementi usati di recente, eseguire il comando seguente nel riquadro della console: `$psise.Options.MruCount`.</span><span class="sxs-lookup"><span data-stu-id="7d52b-154">To change the default number of files in the most-recently used list, run the following command in the Console Pane: `$psise.Options.MruCount`.</span></span>

<span data-ttu-id="7d52b-155">**Valore aggiunto da queste modifiche**</span><span class="sxs-lookup"><span data-stu-id="7d52b-155">**What value does this change add?**</span></span>

<span data-ttu-id="7d52b-156">Con l'elenco degli elementi usati di recente ora è possibile accedere facilmente ai file usati più di frequente.</span><span class="sxs-lookup"><span data-stu-id="7d52b-156">You can now use the most-recently used list to easily access your frequently used files.</span></span>

<span data-ttu-id="7d52b-157">**Differenze di funzionamento**</span><span class="sxs-lookup"><span data-stu-id="7d52b-157">**What works differently?**</span></span>

<span data-ttu-id="7d52b-158">Windows PowerShell ISE 2.0 non include un elenco degli elementi usati di recente.</span><span class="sxs-lookup"><span data-stu-id="7d52b-158">Windows PowerShell ISE 2.0 doesn't have a most-recently used list.</span></span>

## <a name="console-pane"></a><span data-ttu-id="7d52b-159">Riquadro della console</span><span class="sxs-lookup"><span data-stu-id="7d52b-159">Console Pane</span></span>

> <span data-ttu-id="7d52b-160">Funzionalità aggiunta in PowerShell 3.0</span><span class="sxs-lookup"><span data-stu-id="7d52b-160">Added in PowerShell 3.0</span></span>

<span data-ttu-id="7d52b-161">I riquadri distinti di comandi e output disponibili nella prima versione di Windows PowerShell ISE sono stati riuniti in un singolo riquadro della console.</span><span class="sxs-lookup"><span data-stu-id="7d52b-161">The separate Command and Output Panes that were available in the first release of Windows PowerShell ISE have been combined into a single Console Pane.</span></span> <span data-ttu-id="7d52b-162">Il funzionamento e l'aspetto del riquadro della console sono simili a quelli di una tipica console di Windows PowerShell, ma con i miglioramenti seguenti:</span><span class="sxs-lookup"><span data-stu-id="7d52b-162">The Console Pane is similar in function and appearance to a typical Windows PowerShell console, but it includes the following enhancements:</span></span>

- <span data-ttu-id="7d52b-163">Colorazione della sintassi per il testo di input (non per il testo di output), inclusa la sintassi XML</span><span class="sxs-lookup"><span data-stu-id="7d52b-163">Syntax coloring for input text (not output text), including XML syntax</span></span>
- <span data-ttu-id="7d52b-164">IntelliSense</span><span class="sxs-lookup"><span data-stu-id="7d52b-164">IntelliSense</span></span>
- <span data-ttu-id="7d52b-165">Corrispondenza parentesi graffe</span><span class="sxs-lookup"><span data-stu-id="7d52b-165">Brace matching</span></span>
- <span data-ttu-id="7d52b-166">Indicazione degli errori</span><span class="sxs-lookup"><span data-stu-id="7d52b-166">Error indication</span></span>
- <span data-ttu-id="7d52b-167">Supporto completo per Unicode</span><span class="sxs-lookup"><span data-stu-id="7d52b-167">Full Unicode support</span></span>
- <span data-ttu-id="7d52b-168">Guida sensibile al contesto tramite <kbd>F1</kbd></span><span class="sxs-lookup"><span data-stu-id="7d52b-168"><kbd>F1</kbd> context-sensitive help</span></span>
- <span data-ttu-id="7d52b-169">Show-Command sensibile al contesto con <kbd>CTRL</kbd>+<kbd>F1</kbd></span><span class="sxs-lookup"><span data-stu-id="7d52b-169"><kbd>Ctrl</kbd>+<kbd>F1</kbd> context-sensitive Show-Command</span></span>
- <span data-ttu-id="7d52b-170">Supporto per script complessi e con scrittura da destra a sinistra</span><span class="sxs-lookup"><span data-stu-id="7d52b-170">Complex script and right-to-left support</span></span>
- <span data-ttu-id="7d52b-171">Supporto per tipi di carattere</span><span class="sxs-lookup"><span data-stu-id="7d52b-171">Font support</span></span>
- <span data-ttu-id="7d52b-172">Zoom</span><span class="sxs-lookup"><span data-stu-id="7d52b-172">Zoom</span></span>
- <span data-ttu-id="7d52b-173">Modalità selezione riga e selezione blocco</span><span class="sxs-lookup"><span data-stu-id="7d52b-173">Line-select and block-select modes</span></span>
- <span data-ttu-id="7d52b-174">Conservazione del contenuto digitato nella riga di comando quando si preme la freccia <kbd>SU</kbd> per visualizzare la cronologia nella console</span><span class="sxs-lookup"><span data-stu-id="7d52b-174">Preservation of typed content at the command line when you press the <kbd>UpArrow</kbd> to view history in the console</span></span>

<span data-ttu-id="7d52b-175">**Valore aggiunto da queste modifiche**</span><span class="sxs-lookup"><span data-stu-id="7d52b-175">**What value does this change add?**</span></span>

<span data-ttu-id="7d52b-176">L'aggiunta di queste modifiche del riquadro della console offre un'esperienza di scripting più coerente con l'interfaccia della console.</span><span class="sxs-lookup"><span data-stu-id="7d52b-176">The addition of these Console Pane changes provides a scripting experience that is more consistent with the console interface.</span></span>

<span data-ttu-id="7d52b-177">**Differenze di funzionamento**</span><span class="sxs-lookup"><span data-stu-id="7d52b-177">**What works differently?**</span></span>

<span data-ttu-id="7d52b-178">Windows PowerShell ISE 2.0 ha riquadri separati per comandi e output.</span><span class="sxs-lookup"><span data-stu-id="7d52b-178">Windows PowerShell ISE 2.0 has separate Command and Output Panes.</span></span>

## <a name="command-line-switches"></a><span data-ttu-id="7d52b-179">Opzioni della riga di comando</span><span class="sxs-lookup"><span data-stu-id="7d52b-179">Command-line switches</span></span>

> <span data-ttu-id="7d52b-180">Funzionalità aggiunta in PowerShell 3.0</span><span class="sxs-lookup"><span data-stu-id="7d52b-180">Added in PowerShell 3.0</span></span>

<span data-ttu-id="7d52b-181">Se si avvia Windows PowerShell ISE dalla riga di comando digitando **Powershell_ise.exe**, è possibile aggiungere le nuove opzioni da riga di comando seguenti.</span><span class="sxs-lookup"><span data-stu-id="7d52b-181">If you start Windows PowerShell ISE from the command line (by typing **powershell_ise.exe**), you can add the following new command-line switches.</span></span>

- <span data-ttu-id="7d52b-182">`-NoProfile`: Avvia Windows PowerShell ISE senza eseguire `$profile`</span><span class="sxs-lookup"><span data-stu-id="7d52b-182">`-NoProfile`: Starts Windows PowerShell ISE without running `$profile`</span></span>
- <span data-ttu-id="7d52b-183">`-Help`: visualizza una finestra della Guida.</span><span class="sxs-lookup"><span data-stu-id="7d52b-183">`-Help`: Displays a Help window</span></span>
- <span data-ttu-id="7d52b-184">`-mta`: avvia Windows PowerShell ISE in modalità apartment a thread multipli.</span><span class="sxs-lookup"><span data-stu-id="7d52b-184">`-mta`: Starts Windows PowerShell ISE in multithreaded apartment mode.</span></span> <span data-ttu-id="7d52b-185">La modalità operativa predefinita per Windows PowerShell ISE è apartment a thread singolo o `-sta`.</span><span class="sxs-lookup"><span data-stu-id="7d52b-185">The default operation mode for Windows PowerShell ISE is single-threaded apartment mode, or `-sta`.</span></span>

<span data-ttu-id="7d52b-186">**Valore aggiunto da queste modifiche**</span><span class="sxs-lookup"><span data-stu-id="7d52b-186">**What value does this change add?**</span></span>

<span data-ttu-id="7d52b-187">L'aggiunta di queste opzioni da riga di comando consente di controllare l'ambiente di esecuzione di Windows PowerShell ISE.</span><span class="sxs-lookup"><span data-stu-id="7d52b-187">The addition of these command-line switches allows you to control the environment in which the Windows PowerShell ISE runs.</span></span>

<span data-ttu-id="7d52b-188">**Differenze di funzionamento**</span><span class="sxs-lookup"><span data-stu-id="7d52b-188">**What works differently?**</span></span>

<span data-ttu-id="7d52b-189">Windows PowerShell ISE 2.0 non riconosce queste opzioni da riga di comando.</span><span class="sxs-lookup"><span data-stu-id="7d52b-189">Windows PowerShell ISE 2.0 doesn't recognize these command-line switches.</span></span>

## <a name="new-editor-features"></a><span data-ttu-id="7d52b-190">Nuove funzionalità dell'editor</span><span class="sxs-lookup"><span data-stu-id="7d52b-190">New editor features</span></span>

> <span data-ttu-id="7d52b-191">Funzionalità aggiunta in PowerShell 3.0</span><span class="sxs-lookup"><span data-stu-id="7d52b-191">Added in PowerShell 3.0</span></span>

<span data-ttu-id="7d52b-192">Altre funzionalità di modifica di Windows PowerShell ISE includono:</span><span class="sxs-lookup"><span data-stu-id="7d52b-192">Other Windows PowerShell ISE editing features include:</span></span>

- <span data-ttu-id="7d52b-193">**Colorazione della sintassi XML** Windows PowerShell ISE ora applica colori alla sintassi XML nello stesso modo usato per la sintassi di Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="7d52b-193">**XML syntax coloring** - Windows PowerShell ISE now colors XML syntax in the same way as it colors Windows PowerShell syntax.</span></span>
- <span data-ttu-id="7d52b-194">**Corrispondenza delle parentesi graffe** Windows PowerShell ISE include l'individuazione e l'evidenziazione delle parentesi graffe corrispondenti che si possono usare in vari modi. Ad esempio, se si usa il comando **Vai a corrispondenza** o <kbd>CTRL</kbd>+<kbd>]</kbd> si trova la parentesi graffa di chiusura, se è selezionata una parentesi graffa di apertura.</span><span class="sxs-lookup"><span data-stu-id="7d52b-194">**Brace matching** - Windows PowerShell ISE includes brace matching and highlighting, and can be used in the following ways: (for example, using the **Go to Match** command or <kbd>Ctrl</kbd>+<kbd>]</kbd> locates the closing brace, if you have an opening brace selected).</span></span>
- <span data-ttu-id="7d52b-195">**Visualizzazione struttura** Il riquadro di script supporta la struttura delle sezioni, che consente di comprimere o espandere sezioni di codice facendo clic sui segni più o meno nel margine sinistro.</span><span class="sxs-lookup"><span data-stu-id="7d52b-195">**Outline view** The Script Pane supports outlining, which allows collapsing or expanding sections of code by clicking plus or minus signs in the left margin.</span></span> <span data-ttu-id="7d52b-196">È possibile usare le parentesi graffe oppure i tag `#region` e `#endregion` per contrassegnare l'inizio o la fine di una sezione comprimibile.</span><span class="sxs-lookup"><span data-stu-id="7d52b-196">You can use braces or the `#region` and `#endregion` tags to mark the beginning or end of a collapsible section.</span></span> <span data-ttu-id="7d52b-197">Per espandere o comprimere tutte le aree, premere <kbd>CTRL</kbd>+<kbd>M</kbd>.</span><span class="sxs-lookup"><span data-stu-id="7d52b-197">To expand or collapse all regions, press <kbd>Ctrl</kbd>+<kbd>M</kbd>.</span></span>
- <span data-ttu-id="7d52b-198">**Modifica del testo con trascinamento della selezione** Windows PowerShell ISE supporta ora il trascinamento del testo per la modifica.</span><span class="sxs-lookup"><span data-stu-id="7d52b-198">**Drag and drop text editing** - Windows PowerShell ISE now supports drag and drop text editing.</span></span> <span data-ttu-id="7d52b-199">È possibile selezionare qualsiasi blocco di testo e trascinarlo in un'altra posizione nell'editor o nella console per spostarlo.</span><span class="sxs-lookup"><span data-stu-id="7d52b-199">You can select any block of text and drag that text to another location in the editor or the console to move the text.</span></span> <span data-ttu-id="7d52b-200">Se si tiene premuto il tasto <kbd>CTRL</kbd> mentre si trascina il testo selezionato, quando si rilascia il pulsante del mouse il testo viene copiato nella nuova posizione.</span><span class="sxs-lookup"><span data-stu-id="7d52b-200">If you hold down the <kbd>Ctrl</kbd> key while you drag the selected text, when you release the mouse button the text is copied to the new location.</span></span> <span data-ttu-id="7d52b-201">In questa versione di Windows PowerShell ISE i file trascinati in Windows PowerShell ISE vengono aperti.</span><span class="sxs-lookup"><span data-stu-id="7d52b-201">In this version of Windows PowerShell ISE, when you drag and drop files onto Windows PowerShell ISE, Windows PowerShell ISE opens the file.</span></span>
- <span data-ttu-id="7d52b-202">**Visualizzazione degli errori di analisi** Gli errori di analisi sono indicati da sottolineature rosse.</span><span class="sxs-lookup"><span data-stu-id="7d52b-202">**Parse error display** - Parse errors are indicated with red underlines.</span></span> <span data-ttu-id="7d52b-203">Quando si passa il mouse su un errore indicato, il testo della descrizione comando visualizza il problema rilevato nel codice.</span><span class="sxs-lookup"><span data-stu-id="7d52b-203">When you hover over an indicated error, tooltip text displays the problem that was found in the code.</span></span>
- <span data-ttu-id="7d52b-204">**Zoom** È possibile impostare la percentuale di zoom del contenuto della console con il dispositivo di scorrimento zoom, nell'angolo inferiore destro della finestra di Windows PowerShell ISE, oppure immettendo il comando `$psise.options.Zoom` nel riquadro della console.</span><span class="sxs-lookup"><span data-stu-id="7d52b-204">**Zoom** - The zoom percentage of the console's content can be set by using the zoom slider (in the lower right corner of Windows PowerShell ISE window), or by entering the command `$psise.options.Zoom` in the Console Pane.</span></span>
- <span data-ttu-id="7d52b-205">**Operazioni di copia e incolla di testo formattato** Con la copia negli Appunti in Windows PowerShell ISE vengono mantenute le informazioni relative a tipo di carattere, dimensioni e colore della selezione originale.</span><span class="sxs-lookup"><span data-stu-id="7d52b-205">**Rich text copy and paste** - Copying to the clipboard in Windows PowerShell ISE preserves the font, size, and color information of the original selection.</span></span>
- <span data-ttu-id="7d52b-206">**Selezione di blocchi** È possibile selezionare un blocco di testo tenendo premuto <kbd>ALT</kbd> mentre si seleziona il testo nel riquadro di script con il mouse oppure premendo <kbd>ALT</kbd>+<kbd>MAIUSC</kbd>+<kbd>FRECCIA</kbd>.</span><span class="sxs-lookup"><span data-stu-id="7d52b-206">**Block selection** - You can select a block of text by holding down the <kbd>ALT</kbd> key while selecting text in the Script Pane with your mouse, or by pressing <kbd>Alt</kbd>+<kbd>Shift</kbd>+<kbd>Arrow</kbd>.</span></span>

<span data-ttu-id="7d52b-207">**Valore aggiunto da queste modifiche**</span><span class="sxs-lookup"><span data-stu-id="7d52b-207">**What value does this change add?**</span></span>

<span data-ttu-id="7d52b-208">Le funzionalità di modifica aggiuntive rendono disponibile un ambiente di modifica più coerente e potente.</span><span class="sxs-lookup"><span data-stu-id="7d52b-208">The additional editing features provide a more consistent and powerful editing environment.</span></span>

<span data-ttu-id="7d52b-209">**Differenze di funzionamento**</span><span class="sxs-lookup"><span data-stu-id="7d52b-209">**What works differently?**</span></span>

<span data-ttu-id="7d52b-210">Questi miglioramenti non erano presenti in Windows PowerShell ISE 2.0.</span><span class="sxs-lookup"><span data-stu-id="7d52b-210">These editing enhancements weren't present in Windows PowerShell ISE 2.0.</span></span>

## <a name="new-help-viewer-window"></a><span data-ttu-id="7d52b-211">Nuova finestra di visualizzazione della Guida</span><span class="sxs-lookup"><span data-stu-id="7d52b-211">New Help viewer window</span></span>

> <span data-ttu-id="7d52b-212">Funzionalità aggiunta in PowerShell 3.0</span><span class="sxs-lookup"><span data-stu-id="7d52b-212">Added in PowerShell 3.0</span></span>

<span data-ttu-id="7d52b-213">Se si preme <kbd>F1</kbd> mentre il cursore si trova in un cmdlet oppure si evidenzia parte di un cmdlet, nel nuovo visualizzatore della Guida verrà visualizzata la Guida sensibile al contesto del cmdlet evidenziato.</span><span class="sxs-lookup"><span data-stu-id="7d52b-213">If you press <kbd>F1</kbd> when your cursor is in a cmdlet, or you have part of a cmdlet highlighted, the new Help viewer opens context-sensitive Help about the highlighted cmdlet.</span></span> <span data-ttu-id="7d52b-214">Per visualizzare la guida **Informazioni su** Windows PowerShell, digitare `operators` nel riquadro della console e quindi premere <kbd>F1</kbd>.</span><span class="sxs-lookup"><span data-stu-id="7d52b-214">To display Windows PowerShell **About** help, type `operators` in the console pane, and then press <kbd>F1</kbd>.</span></span>

<span data-ttu-id="7d52b-215">Prima di usare questa funzionalità, scaricare la versione aggiornata degli argomenti della Guida di Windows PowerShell dal sito Web Microsoft.</span><span class="sxs-lookup"><span data-stu-id="7d52b-215">Before you use this feature, download the most current version of Windows PowerShell Help topics from the Microsoft website.</span></span> <span data-ttu-id="7d52b-216">Il modo più semplice per scaricare gli argomenti della Guida consiste nell'eseguire il cmdlet `Update-Help` nel riquadro della console durante l'esecuzione di Windows PowerShell ISE come amministratore.</span><span class="sxs-lookup"><span data-stu-id="7d52b-216">The simplest method for downloading the Help topics is to run the `Update-Help` cmdlet in the Console Pane when running Windows PowerShell ISE as administrator.</span></span>

<span data-ttu-id="7d52b-217">È possibile modificare la posizione in cui <kbd>F1</kbd> cerca la Guida.</span><span class="sxs-lookup"><span data-stu-id="7d52b-217">You can alter where the <kbd>F1</kbd> key looks for Help.</span></span> <span data-ttu-id="7d52b-218">Nel menu **Strumenti**/**Opzioni**, nella scheda **Impostazioni generali**, in **Altre impostazioni** è possibile selezionare o deselezionare la casella di controllo **Usa contenuto della Guida locale anziché contenuto online**.</span><span class="sxs-lookup"><span data-stu-id="7d52b-218">In the **Tools**/**Options** menu, on the **General Settings** tab, under **Other Settings**, you can set or clear the checkbox **Use local help content instead of online content**.</span></span> <span data-ttu-id="7d52b-219">Se si seleziona la casella di controllo, il client cerca la Guida per il cmdlet nella guida scaricata disponibile nella cartella dei moduli.</span><span class="sxs-lookup"><span data-stu-id="7d52b-219">When checked, the client looks for the cmdlet Help in the downloaded Help found in the modules folder.</span></span> <span data-ttu-id="7d52b-220">Se la casella di controllo è deselezionata, il client cerca la guida online.</span><span class="sxs-lookup"><span data-stu-id="7d52b-220">If the checkbox is cleared, the client looks for help online.</span></span>

<span data-ttu-id="7d52b-221">**Valore aggiunto da queste modifiche**</span><span class="sxs-lookup"><span data-stu-id="7d52b-221">**What value does this change add?**</span></span>

<span data-ttu-id="7d52b-222">La possibilità di accedere alla Guida sensibile al contesto senza uscire dal cmdlet o dallo script corrente offre un'esperienza di apprendimento integrata.</span><span class="sxs-lookup"><span data-stu-id="7d52b-222">Context-sensitive Help without leaving your current cmdlet or script provides an integrated learning experience.</span></span>

<span data-ttu-id="7d52b-223">**Differenze di funzionamento**</span><span class="sxs-lookup"><span data-stu-id="7d52b-223">**What works differently?**</span></span>

<span data-ttu-id="7d52b-224">Premendo <kbd>F1</kbd> nelle versioni precedenti di Windows PowerShell ISE viene aperto il file della Guida nel computer locale.</span><span class="sxs-lookup"><span data-stu-id="7d52b-224">Pressing <kbd>F1</kbd> in previous versions of Windows PowerShell ISE opened the help file on the local computer.</span></span> <span data-ttu-id="7d52b-225">In Windows PowerShell ISE 3.0 e versioni successive viene visualizzata una finestra che contiene la Guida per il cmdlet, configurabile e nella quale è possibile eseguire ricerche.</span><span class="sxs-lookup"><span data-stu-id="7d52b-225">In Windows PowerShell ISE 3.0 and later, a window opens that contains the help for the cmdlet that is searchable and configurable.</span></span> <span data-ttu-id="7d52b-226">Questa esperienza della Guida è una novità di Windows PowerShell ISE 3.0 e la Guida aggiornabile è una novità di Windows PowerShell ISE 3.0.</span><span class="sxs-lookup"><span data-stu-id="7d52b-226">This Help experience is new for Windows PowerShell ISE 3.0, and Updatable Help is new for Windows PowerShell 3.0.</span></span>

## <a name="show-command-cmdlet"></a><span data-ttu-id="7d52b-227">Cmdlet Show-Command</span><span class="sxs-lookup"><span data-stu-id="7d52b-227">Show-Command cmdlet</span></span>

> <span data-ttu-id="7d52b-228">Funzionalità aggiunta in PowerShell 3.0</span><span class="sxs-lookup"><span data-stu-id="7d52b-228">Added in PowerShell 3.0</span></span>

<span data-ttu-id="7d52b-229">Il cmdlet `Show-Command` consente di comporre o eseguire un cmdlet o una funzione compilando un modulo grafico.</span><span class="sxs-lookup"><span data-stu-id="7d52b-229">The `Show-Command` cmdlet enables you to compose or run a cmdlet or function by filling in a graphical form.</span></span> <span data-ttu-id="7d52b-230">Questo modulo consente agli utenti di usare Windows PowerShell in un ambiente grafico.</span><span class="sxs-lookup"><span data-stu-id="7d52b-230">The form lets users work with Windows PowerShell in a graphical environment.</span></span>
<span data-ttu-id="7d52b-231">`Show-Command` consente inoltre agli utenti esperti di script di creare un'interfaccia utente grafica rapida basata su Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="7d52b-231">`Show-Command` also enables advanced scripters to create a quick Windows PowerShell-based GUI.</span></span>

<span data-ttu-id="7d52b-232">**Valore aggiunto da queste modifiche**</span><span class="sxs-lookup"><span data-stu-id="7d52b-232">**What value does this change add?**</span></span>

<span data-ttu-id="7d52b-233">L'uso di `Show-Command` negli script di Windows PowerShell consente di offrire agli utenti l'ambiente grafico con cui hanno familiarità.</span><span class="sxs-lookup"><span data-stu-id="7d52b-233">By using `Show-Command` in your Windows PowerShell scripts, you can provide your users with the graphical environment with which they're familiar.</span></span> <span data-ttu-id="7d52b-234">`Show-Command` può anche essere utile agli utenti meno esperti per l'apprendimento di Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="7d52b-234">`Show-Command` can also help introductory users learn Windows PowerShell.</span></span>

<span data-ttu-id="7d52b-235">**Differenze di funzionamento**</span><span class="sxs-lookup"><span data-stu-id="7d52b-235">**What works differently?**</span></span>

<span data-ttu-id="7d52b-236">`Show-Command` è nuovo in Windows PowerShell ISE 3.0.</span><span class="sxs-lookup"><span data-stu-id="7d52b-236">`Show-Command` is new Windows PowerShell ISE 3.0.</span></span>

## <a name="see-also"></a><span data-ttu-id="7d52b-237">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="7d52b-237">See also</span></span>

<span data-ttu-id="7d52b-238">Per altre informazioni sull'uso di Windows PowerShell ISE, vedere [Esplorazione di Windows PowerShell ISE](../getting-started/fundamental/exploring-the-windows-powershell-ise.md).</span><span class="sxs-lookup"><span data-stu-id="7d52b-238">For more information about using Windows PowerShell ISE, see [Exploring the Windows PowerShell Integrated Scripting Environment](../getting-started/fundamental/exploring-the-windows-powershell-ise.md).</span></span>
