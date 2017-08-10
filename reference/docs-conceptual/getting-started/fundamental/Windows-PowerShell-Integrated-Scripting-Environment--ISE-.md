---
ms.date: 2017-06-05
keywords: powershell,cmdlet
title: Windows PowerShell Integrated Scripting Environment ISE
ms.assetid: f156b92d-0203-46d2-89c7-b4989d32e3d2
ms.openlocfilehash: 93b3322ae5634d3611f3c2743e7460e266dc7ab8
ms.sourcegitcommit: 598b7835046577841aea2211d613bb8513271a8b
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 06/08/2017
---
# <a name="windows-powershell-integrated-scripting-environment-ise"></a><span data-ttu-id="b45ae-103">Windows PowerShell Integrated Scripting Environment (ISE)</span><span class="sxs-lookup"><span data-stu-id="b45ae-103">Windows PowerShell Integrated Scripting Environment (ISE)</span></span>
<span data-ttu-id="b45ae-104">Windows PowerShell Integrated Scripting Environment (ISE) è uno dei due host per il motore e il linguaggio di Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="b45ae-104">The Windows PowerShell Integrated Scripting Environment (ISE) is one of two hosts for the Windows PowerShell engine and language.</span></span> <span data-ttu-id="b45ae-105">È possibile usarlo per scrivere, eseguire e testare script in modi non disponibili nella console di Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="b45ae-105">With it you can write, run, and test scripts in ways that are not available in the Windows PowerShell Console.</span></span> <span data-ttu-id="b45ae-106">ISE aggiunge la colorazione della sintassi, il completamento tramite TAB, IntelliSense, il debug visivo e la Guida sensibile al contesto.</span><span class="sxs-lookup"><span data-stu-id="b45ae-106">The ISE adds syntax-coloring, tab completion, IntelliSense, visual debugging, and context sensitive Help.</span></span>

<span data-ttu-id="b45ae-107">Con ISE è possibile eseguire i comandi in un riquadro della console, ma sono supportati anche riquadri che consentono di visualizzare contemporaneamente il codice sorgente dello script e altri strumenti integrabili in ISE.</span><span class="sxs-lookup"><span data-stu-id="b45ae-107">The ISE lets you run commands in a console pane, but it also supports panes that you can use to simultaneously view the source code of your script and other tools that can plug into the ISE.</span></span> <span data-ttu-id="b45ae-108">È anche possibile aprire più finestre di script contemporaneamente, opzione particolarmente utile quando si esegue il debug di uno script che usa funzioni definite in altri script o moduli.</span><span class="sxs-lookup"><span data-stu-id="b45ae-108">You can even open up multiple script windows at the same time, which is especially helpful when you are debugging a script that uses functions defined in other scripts or modules.</span></span>

## <a name="whats-new"></a><span data-ttu-id="b45ae-109">Novità</span><span class="sxs-lookup"><span data-stu-id="b45ae-109">What’s New</span></span>
<span data-ttu-id="b45ae-110">Ecco alcune delle funzionalità che sono state aggiunte in ISE nelle versioni più recenti di PowerShell.</span><span class="sxs-lookup"><span data-stu-id="b45ae-110">Here are some of the features that have been added to the ISE in the most recent releases of PowerShell.</span></span>

### <a name="added-in-powershell-30-windows-server-2012-windows-8"></a><span data-ttu-id="b45ae-111">Aggiunta in PowerShell 3.0 (Windows Server 2012, Windows 8)</span><span class="sxs-lookup"><span data-stu-id="b45ae-111">Added in PowerShell 3.0 (Windows Server 2012, Windows 8)</span></span>
<span data-ttu-id="b45ae-112">**IntelliSense** consente di completare automaticamente i comandi visualizzando menu di cmdlet, parametri, valori di parametri, file o cartelle corrispondenti durante la digitazione.</span><span class="sxs-lookup"><span data-stu-id="b45ae-112">**IntelliSense** automatically completes your commands by displaying menus of matching cmdlets, parameters, parameter values, files, or folders as you type.</span></span>

<span data-ttu-id="b45ae-113">**Frammenti di codice**, ovvero brevi sezioni di codice che è possibile inserire facilmente negli script durante la scrittura.</span><span class="sxs-lookup"><span data-stu-id="b45ae-113">**Snippets** are short sections of code that you can easily insert into the scripts your write.</span></span> <span data-ttu-id="b45ae-114">È disponibile una raccolta predefinita di utili frammenti di codice ed è possibile aggiungerne altri tramite il cmdlet **New-Snippet**.</span><span class="sxs-lookup"><span data-stu-id="b45ae-114">A collection of useful snippets is included in the box and you can more by using the **New-Snippet** cmdlet.</span></span>

<span data-ttu-id="b45ae-115">È possibile creare **strumenti aggiuntivi** per aggiungere funzionalità a ISE scrivendo codice che interagisce con il [Modello a oggetti di scripting di Windows PowerShell ISE](https://technet.microsoft.com/en-us/library/dd819478.aspx).</span><span class="sxs-lookup"><span data-stu-id="b45ae-115">**Add-on tools** that add features to the ISE can be created by writing code that interacts with the [The Windows PowerShell ISE Scripting Object Model](https://technet.microsoft.com/en-us/library/dd819478.aspx).</span></span> <span data-ttu-id="b45ae-116">Questi strumenti possono visualizzare i controlli in un riquadro a schede o funzionare in modo invisibile in background.</span><span class="sxs-lookup"><span data-stu-id="b45ae-116">These tools can display controls in a tabbed pane or work invisibly in the background.</span></span> <span data-ttu-id="b45ae-117">Il componente aggiuntivo **Comandi** è un buon esempio incluso nella versione 3.0 e successive, che consente di visualizzare un elenco di comandi disponibili e la rispettiva Guida.</span><span class="sxs-lookup"><span data-stu-id="b45ae-117">The **Commands** add-on is a good example and is included with version 3.0 and later that displays a list of the available commands and their Help.</span></span>

<span data-ttu-id="b45ae-118">Le funzionalità **Gestione riavvio e Salvataggio automatico** salvano automaticamente gli script ogni due minuti per evitare di perdere il lavoro in caso di arresto anomalo o di un riavvio imprevisto.</span><span class="sxs-lookup"><span data-stu-id="b45ae-118">**Restart Manager and Auto-save** automatically save your scripts every two minutes to help you avoid the loss of your work in the event of a crash or unexpected restart.</span></span>

<span data-ttu-id="b45ae-119">L'**elenco degli elementi usati di recente** fa ora parte del menu Apri File in modo da facilitare l'accesso ai file usati più frequentemente.</span><span class="sxs-lookup"><span data-stu-id="b45ae-119">**Most Recently Used list** is now part of the File Open menu to make it easier to get to the files you use most often.</span></span>

<span data-ttu-id="b45ae-120">**Riquadro della console unito**.</span><span class="sxs-lookup"><span data-stu-id="b45ae-120">**Merged Console pane**.</span></span> <span data-ttu-id="b45ae-121">Nelle versioni precedenti di ISE sono disponibili riquadri separati per i comandi e l'output.</span><span class="sxs-lookup"><span data-stu-id="b45ae-121">In previous versions of the ISE there were separate Command and Output panes.</span></span> <span data-ttu-id="b45ae-122">Questi riquadri sono ora riuniti in un unico riquadro che riproduce in modo più fedele la visualizzazione disponibile nella console di Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="b45ae-122">They are now combined into a single pane that more directly mimics what you see in the Windows Powershell Console.</span></span>

<span data-ttu-id="b45ae-123">**Opzioni della riga di comando**.</span><span class="sxs-lookup"><span data-stu-id="b45ae-123">**Command-line switches**.</span></span> <span data-ttu-id="b45ae-124">Diverse nuove opzioni della riga di comando offrono maggiore controllo sul funzionamento di ISE.</span><span class="sxs-lookup"><span data-stu-id="b45ae-124">Several new command-line switches give you more control over the way the ISE works.</span></span> <span data-ttu-id="b45ae-125">-NoProfile avvia ISE senza eseguire un profilo di script.</span><span class="sxs-lookup"><span data-stu-id="b45ae-125">-NoProfile starts the ISE without running a profile script.</span></span> <span data-ttu-id="b45ae-126">-Help apre una finestra della Guida con ISE.</span><span class="sxs-lookup"><span data-stu-id="b45ae-126">-Help opens up a help window with the ISE.</span></span> <span data-ttu-id="b45ae-127">-mta avvia ISE in "modalità apartment a thread multipli".</span><span class="sxs-lookup"><span data-stu-id="b45ae-127">-mta starts the ISE in “multi-threaded apartment mode”.</span></span> <span data-ttu-id="b45ae-128">L'impostazione predefinita è la modalità apartment a thread singolo.</span><span class="sxs-lookup"><span data-stu-id="b45ae-128">The default is single-threaded.</span></span>

<span data-ttu-id="b45ae-129">**Nuove funzionalità dell'editor** rendono più semplice creare e leggere il codice:</span><span class="sxs-lookup"><span data-stu-id="b45ae-129">**New editor features** make it easier to create and read your code:</span></span>

-   <span data-ttu-id="b45ae-130">**Colorazione della sintassi XML**.</span><span class="sxs-lookup"><span data-stu-id="b45ae-130">**XML syntax coloring**.</span></span> <span data-ttu-id="b45ae-131">L'editor ISE ora applica colori alla sintassi XML nello stesso modo usato per la sintassi del codice di Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="b45ae-131">The ISE editor now colors XML syntax in the same way as it colors Windows PowerShell code syntax.</span></span>

-   <span data-ttu-id="b45ae-132">**Corrispondenza delle parentesi graffe**.</span><span class="sxs-lookup"><span data-stu-id="b45ae-132">**Brace matching**.</span></span> <span data-ttu-id="b45ae-133">ISEWindows PowerShell ISE evidenzia le parentesi graffe corrispondenti per facilitare il controllo del numero corretto di parentesi graffe di chiusura corrispondenti a quelle di apertura.</span><span class="sxs-lookup"><span data-stu-id="b45ae-133">The ISEWindows PowerShell ISE highlights matching braces to help you ensure you have the right number of closing braces to match your opening ones.</span></span> <span data-ttu-id="b45ae-134">È possibile usare CTRL-\[ per individuare la parentesi graffa di chiusura corrispondente a quella di apertura su cui si trova il cursore.</span><span class="sxs-lookup"><span data-stu-id="b45ae-134">Use CTRL-\[ to locate the closing brace that matches the opening brace that the cursor is on.</span></span>

-   <span data-ttu-id="b45ae-135">**Visualizzazione struttura**.</span><span class="sxs-lookup"><span data-stu-id="b45ae-135">**Outline view**.</span></span> <span data-ttu-id="b45ae-136">È possibile comprimere o espandere sezioni del codice facendo clic sul segno più e meno nel margine sinistro.</span><span class="sxs-lookup"><span data-stu-id="b45ae-136">You can collapse or expand sections of your code by clicking the plus and minus signs in the left margin.</span></span> <span data-ttu-id="b45ae-137">In questo modo è più semplice trovare il codice che si sta cercando in uno script lungo.</span><span class="sxs-lookup"><span data-stu-id="b45ae-137">This makes it easier to find the code you’re looking for in a long script.</span></span>

-   <span data-ttu-id="b45ae-138">**Modifica del testo con trascinamento della selezione**.</span><span class="sxs-lookup"><span data-stu-id="b45ae-138">**Drag and drop text editing**.</span></span> <span data-ttu-id="b45ae-139">È possibile selezionare un blocco di testo e trascinarlo in un'altra posizione per spostarlo.</span><span class="sxs-lookup"><span data-stu-id="b45ae-139">You can select a block of text and drag it to another location to move it.</span></span> <span data-ttu-id="b45ae-140">Se si tiene premuto il tasto CTRL mentre si trascina il testo selezionato, si esegue una copia anziché uno spostamento.</span><span class="sxs-lookup"><span data-stu-id="b45ae-140">If you hold down the Ctrl key while you drag the selected text you copy instead of move.</span></span>

-   <span data-ttu-id="b45ae-141">**Visualizzazione degli errori di analisi**.</span><span class="sxs-lookup"><span data-stu-id="b45ae-141">**Parse error display**.</span></span> <span data-ttu-id="b45ae-142">Windows PowerShell esamina lo script durante la digitazione.</span><span class="sxs-lookup"><span data-stu-id="b45ae-142">Windows PowerShell examines your script as you type.</span></span> <span data-ttu-id="b45ae-143">Se viene rilevato un errore, verrà visualizzata una sottolineatura ondulata rossa sotto il codice che causa l'errore.</span><span class="sxs-lookup"><span data-stu-id="b45ae-143">If it detects an error, it shows a red squiggle under the offending code.</span></span> <span data-ttu-id="b45ae-144">Quando si passa il mouse sull'errore indicato, il problema rilevato viene indicato in una descrizione comando.</span><span class="sxs-lookup"><span data-stu-id="b45ae-144">When you hover over the indicated error, a tooltip shows you the problem that was found.</span></span>

-   <span data-ttu-id="b45ae-145">**Zoom**.</span><span class="sxs-lookup"><span data-stu-id="b45ae-145">**Zoom**.</span></span> <span data-ttu-id="b45ae-146">È possibile ingrandire il testo per facilitarne la lettura o ridurlo per ottenere un quadro d'insieme usando il dispositivo di scorrimento nell'angolo in basso a destra della finestra di ISE.</span><span class="sxs-lookup"><span data-stu-id="b45ae-146">You can zoom in on your text to make it easier to read or zoom out to see the bigger picture by using the slider in the bottom-right corner of the ISE window.</span></span>

-   <span data-ttu-id="b45ae-147">**Operazioni di copia e incolla di testo formattato**.</span><span class="sxs-lookup"><span data-stu-id="b45ae-147">**Rich text copy and paste**.</span></span> <span data-ttu-id="b45ae-148">Quando si esegue una copia negli Appunti da ISE vengono incluse le informazioni relative a tipo di carattere, dimensioni e colore del testo selezionato.</span><span class="sxs-lookup"><span data-stu-id="b45ae-148">When you copy from the ISE to the clipboard, the font, size, and color information of the selected text is included.</span></span>

-   <span data-ttu-id="b45ae-149">**Selezione di blocchi**.</span><span class="sxs-lookup"><span data-stu-id="b45ae-149">**Block selection**.</span></span> <span data-ttu-id="b45ae-150">È possibile selezionare una parte di testo a forma di blocco tenendo premuto ALT mentre si seleziona il testo nel riquadro di script con il mouse oppure premendo **ALT+MAIUSC+FRECCIA**.</span><span class="sxs-lookup"><span data-stu-id="b45ae-150">You can select a block-shaped chunk of text by holding down the ALT key while selecting text in the script pane with your mouse, or by pressing **Alt+Shift+Arrow**.</span></span>

### <a name="added-in-powershell-20-windows-server-2008-r2-windows-7"></a><span data-ttu-id="b45ae-151">Aggiunta in PowerShell 2.0 (Windows Server 2008 R2, Windows 7)</span><span class="sxs-lookup"><span data-stu-id="b45ae-151">Added in PowerShell 2.0 (Windows Server 2008 R2, Windows 7)</span></span>
<span data-ttu-id="b45ae-152">L'ambiente ISE è stato introdotto in PowerShell 2.0.</span><span class="sxs-lookup"><span data-stu-id="b45ae-152">The ISE was introduced with PowerShell v2.0.</span></span>

## <a name="requirements-for-running-the-windows-powershell-ise"></a><span data-ttu-id="b45ae-153">Requisiti per l'esecuzione di Windows PowerShell ISE</span><span class="sxs-lookup"><span data-stu-id="b45ae-153">Requirements for running the Windows PowerShell ISE</span></span>
<span data-ttu-id="b45ae-154">ISE è disponibile in qualsiasi computer che supporta l'esecuzione di Windows PowerShell 2.0 o versione successiva.</span><span class="sxs-lookup"><span data-stu-id="b45ae-154">The ISE is available on any computer that can run Windows PowerShell v2.0 or later.</span></span> <span data-ttu-id="b45ae-155">Ogni versione di Windows e Windows Server include una versione di Windows PowerShell e ISE, ma è possibile eseguire l'aggiornamento alla versione più recente disponibile tramite l'installazione di Windows Management Framework.</span><span class="sxs-lookup"><span data-stu-id="b45ae-155">Each version of Windows and Windows Server includes a version of Windows PowerShell and the ISE, but you can upgrade to the latest available by installing the Windows Management Framework.</span></span> <span data-ttu-id="b45ae-156">Eseguire questa ricerca per trovare l'ultima versione disponibile: [Download](http://www.microsoft.com/en-us/search/DownloadResults.aspx?q=%22windows%20management%20framework%22%20PowerShell&sortby=Relevancy~Descending).</span><span class="sxs-lookup"><span data-stu-id="b45ae-156">Run this search to find the latest version available: [Downloads](http://www.microsoft.com/en-us/search/DownloadResults.aspx?q=%22windows%20management%20framework%22%20PowerShell&sortby=Relevancy~Descending).</span></span> <span data-ttu-id="b45ae-157">Si noti che tutte le voci con etichetta "Preview" rappresentano codice preliminare e non includono funzionalità complete.</span><span class="sxs-lookup"><span data-stu-id="b45ae-157">Note that any entries labelled "Preview" are pre-release code and are not feature complete.</span></span>

> [!NOTE]
> <span data-ttu-id="b45ae-158">Windows PowerShell ISE richiede un'interfaccia utente grafica, quindi non è possibile eseguirlo nell'opzione Server Core di Windows Server.</span><span class="sxs-lookup"><span data-stu-id="b45ae-158">Because Windows PowerShell ISE requires a graphical user interface, you can’t run it on the Server Core option of Windows Server.</span></span>

## <a name="see-also"></a><span data-ttu-id="b45ae-159">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="b45ae-159">See also</span></span>
- [<span data-ttu-id="b45ae-160">Uso di Windows PowerShell ISE (Integrated Scripting Environment)</span><span class="sxs-lookup"><span data-stu-id="b45ae-160">Using the Windows PowerShell Integrated Scripting Environment</span></span>](http://technet.microsoft.com/library/cc732148.aspx)
