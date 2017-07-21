---
ms.date: 2017-06-05
keywords: powershell,cmdlet
title: Come scrivere ed eseguire script in Windows PowerShell ISE
ms.assetid: 62f916d9-b3a1-484a-bdfb-41f57112c22b
ms.openlocfilehash: 871a4b6f4575af4f823a6957dc971335497320a4
ms.sourcegitcommit: 598b7835046577841aea2211d613bb8513271a8b
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 06/08/2017
---
# <a name="how-to-write-and-run-scripts-in-the-windows-powershell-ise"></a><span data-ttu-id="4441c-103">Come scrivere ed eseguire script in Windows PowerShell ISE</span><span class="sxs-lookup"><span data-stu-id="4441c-103">How to Write and Run Scripts in the Windows PowerShell ISE</span></span>
<span data-ttu-id="4441c-104">Questo argomento descrive come creare, modificare, eseguire e salvare gli script nel riquadro di script.</span><span class="sxs-lookup"><span data-stu-id="4441c-104">This topic describes how to create, edit, run, and save scripts in the Script Pane.</span></span>

-   [<span data-ttu-id="4441c-105">Come creare ed eseguire script</span><span class="sxs-lookup"><span data-stu-id="4441c-105">How to create and run scripts</span></span>](#bkmk_1)

-   [<span data-ttu-id="4441c-106">Come scrivere e modificare testo nel riquadro di script</span><span class="sxs-lookup"><span data-stu-id="4441c-106">How to write and edit text in the Script Pane</span></span>](#bkmk_2)

-   [<span data-ttu-id="4441c-107">Come salvare uno script</span><span class="sxs-lookup"><span data-stu-id="4441c-107">How to save a script</span></span>](#bkmk_3)

## <span data-ttu-id="4441c-108"><a name="bkmk_1"></a>Come creare ed eseguire script</span><span class="sxs-lookup"><span data-stu-id="4441c-108"><a name="bkmk_1"></a>How to create and run scripts</span></span>
<span data-ttu-id="4441c-109">È possibile aprire e modificare i file di Windows PowerShell® nel riquadro di script.</span><span class="sxs-lookup"><span data-stu-id="4441c-109">You can open and edit Windows PowerShell® files in the Script Pane.</span></span> <span data-ttu-id="4441c-110">Tipi di file di particolare interesse in Windows PowerShell® sono i file di script (con estensione PS1), i file di dati degli script (con estensione PSD1) e i file di modulo di script (con estensione PSM1).</span><span class="sxs-lookup"><span data-stu-id="4441c-110">Specific file types of interest in Windows PowerShell® are script files (.ps1), script data files (.psd1), and script module files (.psm1).</span></span> <span data-ttu-id="4441c-111">In questi file per la visualizzazione della sintassi nell'editor del riquadro di script vengono utilizzati i colori.</span><span class="sxs-lookup"><span data-stu-id="4441c-111">These file types are syntax colored in the Script Pane editor.</span></span> <span data-ttu-id="4441c-112">Altri tipi di file comuni che è possibile aprire nel riquadro di script sono file di configurazione (con estensione ps1xml), file XML e file di testo.</span><span class="sxs-lookup"><span data-stu-id="4441c-112">Other common file types you may open in the Script Pane are configuration files (.ps1xml), XML files, and text files.</span></span>

> [!NOTE]
> <span data-ttu-id="4441c-113">I criteri di esecuzione di Windows PowerShell determinano se è possibile eseguire script e caricare profili e file di configurazione di Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="4441c-113">The Windows PowerShell execution policy determines whether you can run scripts and load Windows PowerShell profiles and configuration files.</span></span> <span data-ttu-id="4441c-114">I criteri di esecuzione predefiniti prevedono restrizioni e impediscono l'esecuzione di tutti gli script e il caricamento di profili.</span><span class="sxs-lookup"><span data-stu-id="4441c-114">The default execution policy, Restricted, prevents all scripts from running, and prevents loading profiles.</span></span> <span data-ttu-id="4441c-115">Per modificare i criteri di esecuzione per consentire il caricamento e l'uso di profili, vedere [Set-ExecutionPolicy[PSITPro5_Security]](https://technet.microsoft.com/en-us/library/5690a0e1-495b-4e63-8280-65ead7bf01ab) e [about_Signing [v4]](https://technet.microsoft.com/en-us/library/fcbdd3b9-0b9f-4734-b5c7-e0dcc304fa1d).</span><span class="sxs-lookup"><span data-stu-id="4441c-115">To change the execution policy to allow profiles to load and be used, see [Set-ExecutionPolicy[PSITPro5_Security]](https://technet.microsoft.com/en-us/library/5690a0e1-495b-4e63-8280-65ead7bf01ab) and [about_Signing [v4]](https://technet.microsoft.com/en-us/library/fcbdd3b9-0b9f-4734-b5c7-e0dcc304fa1d).</span></span>

### <a name="to-create-a-new-script-file"></a><span data-ttu-id="4441c-116">Per creare un nuovo file di script</span><span class="sxs-lookup"><span data-stu-id="4441c-116">To create a new script file</span></span>
<span data-ttu-id="4441c-117">Sulla barra degli strumenti fare clic su **Nuovo** o scegliere **Nuovo** dal menu **File**.</span><span class="sxs-lookup"><span data-stu-id="4441c-117">On the toolbar, click **New** , or on the **File** menu, click **New**.</span></span> <span data-ttu-id="4441c-118">Il file creato viene visualizzato in una nuova scheda file nella scheda di PowerShell corrente.</span><span class="sxs-lookup"><span data-stu-id="4441c-118">The created file appears in a new file tab under the current PowerShell tab.</span></span> <span data-ttu-id="4441c-119">Tenere presente che le schede di PowerShell sono visibili solo se ne sono presenti più di una.</span><span class="sxs-lookup"><span data-stu-id="4441c-119">Remember that the PowerShell tabs are only visible when there are more than one.</span></span> <span data-ttu-id="4441c-120">Per impostazione predefinita viene creato un file di tipo script (con estensione ps1), ma è possibile salvarlo con un nuovo nome e un'altra estensione.</span><span class="sxs-lookup"><span data-stu-id="4441c-120">By default a file of type script (.ps1) is created, but it can be saved with a new name and extension.</span></span> <span data-ttu-id="4441c-121">Nella stessa scheda di PowerShell si possono creare più file di script.</span><span class="sxs-lookup"><span data-stu-id="4441c-121">Multiple script files can be created in the same PowerShell tab.</span></span>

### <a name="to-open-an-existing-script"></a><span data-ttu-id="4441c-122">Per aprire uno script esistente</span><span class="sxs-lookup"><span data-stu-id="4441c-122">To open an existing script</span></span>
<span data-ttu-id="4441c-123">Sulla barra degli strumenti fare clic su **Apri...** o scegliere **Apri** dal menu **File**.</span><span class="sxs-lookup"><span data-stu-id="4441c-123">On the toolbar, click **Open…**, or on the **File** menu, click **Open**.</span></span> <span data-ttu-id="4441c-124">Nella finestra di dialogo **Apri** selezionare il file da aprire.</span><span class="sxs-lookup"><span data-stu-id="4441c-124">In the **Open** dialog box, select the file you want to open.</span></span> <span data-ttu-id="4441c-125">Il file aperto viene visualizzato in una nuova scheda.</span><span class="sxs-lookup"><span data-stu-id="4441c-125">The opened file appears in a new tab.</span></span>

### <a name="to-close-a-script-tab"></a><span data-ttu-id="4441c-126">Per chiudere la scheda di uno script</span><span class="sxs-lookup"><span data-stu-id="4441c-126">To close a script tab</span></span>
<span data-ttu-id="4441c-127">Fare clic sulla scheda dello script che si vuole chiudere, quindi eseguire una delle operazioni seguenti:</span><span class="sxs-lookup"><span data-stu-id="4441c-127">Click the script tab of the script you want to close, then do one of the following:</span></span>

1.  <span data-ttu-id="4441c-128">Fare clic sull'icona **Chiudi** (X) nella scheda dello script.</span><span class="sxs-lookup"><span data-stu-id="4441c-128">Click the **Close** icon (X) on the script tab.</span></span>

2.  <span data-ttu-id="4441c-129">Scegliere **Chiudi** dal menu **File**.</span><span class="sxs-lookup"><span data-stu-id="4441c-129">On the **File** menu, click **Close**.</span></span>

<span data-ttu-id="4441c-130">Se il file è stato modificato dall'ultimo salvataggio, verrà chiesto se salvare le modifiche o ignorarle.</span><span class="sxs-lookup"><span data-stu-id="4441c-130">If the file has been altered since it was last saved, you are prompted to save or discard it.</span></span>

### <a name="to-display-the-file-path"></a><span data-ttu-id="4441c-131">Per visualizzare il percorso del file</span><span class="sxs-lookup"><span data-stu-id="4441c-131">To display the file path</span></span>
<span data-ttu-id="4441c-132">Nella scheda del file posizionare il puntatore del mouse sul nome del file.</span><span class="sxs-lookup"><span data-stu-id="4441c-132">On the file tab, point to the file name.</span></span> <span data-ttu-id="4441c-133">Il percorso completo del file di script appare in una descrizione comando.</span><span class="sxs-lookup"><span data-stu-id="4441c-133">The fully qualified path to the script file appears in a tooltip.</span></span>

### <a name="to-run-a-script"></a><span data-ttu-id="4441c-134">Per eseguire uno script</span><span class="sxs-lookup"><span data-stu-id="4441c-134">To run a script</span></span>
<span data-ttu-id="4441c-135">Sulla barra degli strumenti fare clic su **Esegui script** o scegliere **Esegui** dal menu **File**.</span><span class="sxs-lookup"><span data-stu-id="4441c-135">On the toolbar, click **Run Script**, or on the **File** menu, click **Run**.</span></span>

### <a name="to-run-a-portion-of-a-script"></a><span data-ttu-id="4441c-136">Per eseguire una parte di uno script</span><span class="sxs-lookup"><span data-stu-id="4441c-136">To run a portion of a script</span></span>

1.  <span data-ttu-id="4441c-137">Nel riquadro di script selezionare una parte di uno script.</span><span class="sxs-lookup"><span data-stu-id="4441c-137">In the Script Pane, select a portion of a script.</span></span>

2.  <span data-ttu-id="4441c-138">Sulla barra degli strumenti fare clic su **Esegui selezione** o scegliere **Esegui selezione** dal menu **File**.</span><span class="sxs-lookup"><span data-stu-id="4441c-138">On the **File** menu, click **Run Selection**, or on the toolbar, click **Run Selection**.</span></span>

### <a name="to-stop-a-running-script"></a><span data-ttu-id="4441c-139">Per arrestare l'esecuzione di uno script</span><span class="sxs-lookup"><span data-stu-id="4441c-139">To stop a running script</span></span>
<span data-ttu-id="4441c-140">Sulla barra degli strumenti fare clic su **Arresta operazione**, premere CTRL+INTERR o scegliere **Arresta operazione** dal menu **File**.</span><span class="sxs-lookup"><span data-stu-id="4441c-140">On the toolbar, click **Stop Operation**, press CTRL+BREAK, or on the **File** menu, click **Stop Operation**.</span></span> <span data-ttu-id="4441c-141">È anche possibile premere **CTRL+C**, a meno che non sia attualmente selezionato del testo. In quel caso, **CTRL+C** corrisponderà alla funzione di copia del testo selezionato.</span><span class="sxs-lookup"><span data-stu-id="4441c-141">Pressing **CTRL+C** also works unless some text is currently selected, in which case **CTRL+C** maps to the copy function for the selected text.</span></span>

## <span data-ttu-id="4441c-142"><a name="bkmk_2"></a>Come scrivere e modificare testo nel riquadro di script</span><span class="sxs-lookup"><span data-stu-id="4441c-142"><a name="bkmk_2"></a>How to write and edit text in the Script Pane</span></span>
<span data-ttu-id="4441c-143">Per modificare il testo nel riquadro di script, usare la procedura seguente.</span><span class="sxs-lookup"><span data-stu-id="4441c-143">Use the following steps to edit text in the Script Pane.</span></span> <span data-ttu-id="4441c-144">È possibile copiare, tagliare, incollare, trovare e sostituire testo.</span><span class="sxs-lookup"><span data-stu-id="4441c-144">You can copy, cut, paste, find, and replace text.</span></span> <span data-ttu-id="4441c-145">È anche possibile annullare e ripetere l'ultima operazione eseguita.</span><span class="sxs-lookup"><span data-stu-id="4441c-145">You can also undo and redo the last action you just performed.</span></span> <span data-ttu-id="4441c-146">I tasti di scelta rapida per eseguire queste operazioni sono identici a quelli usati in tutte le applicazioni di Windows.</span><span class="sxs-lookup"><span data-stu-id="4441c-146">The keyboard shortcuts for performing these actions are the same as those used for all Windows applications.</span></span>

### <a name="to-enter-text-in-the-script-pane"></a><span data-ttu-id="4441c-147">Per immettere testo nel riquadro di script</span><span class="sxs-lookup"><span data-stu-id="4441c-147">To enter text in the Script Pane</span></span>

1.  <span data-ttu-id="4441c-148">Spostare il cursore sul riquadro di script facendo clic in un punto qualsiasi al suo interno o scegliendo **Vai al riquadro di script** dal menu **Visualizza**.</span><span class="sxs-lookup"><span data-stu-id="4441c-148">Move the cursor to the Script Pane by clicking anywhere in the Script Pane, or by clicking **Go to Script Pane** in the **View** menu.</span></span>

2.  <span data-ttu-id="4441c-149">Creare uno script.</span><span class="sxs-lookup"><span data-stu-id="4441c-149">Create a script.</span></span> <span data-ttu-id="4441c-150">La colorazione della sintassi e la funzionalità di completamento tramite tasto TAB semplificano notevolmente l'esperienza in Windows PowerShell ISE.</span><span class="sxs-lookup"><span data-stu-id="4441c-150">Syntax coloring and tab completion make this a richer experience in Windows PowerShell ISE.</span></span>

3.  <span data-ttu-id="4441c-151">Per maggiori informazioni sull'uso di questa funzionalità, vedere [Come usare la funzionalità di completamento tramite TAB nel riquadro di script e nel riquadro della console](How-to-Use-Tab-Completion-in-the-Script-Pane-and-Console-Pane.md).</span><span class="sxs-lookup"><span data-stu-id="4441c-151">See [How to Use Tab Completion in the Script Pane and Console Pane](How-to-Use-Tab-Completion-in-the-Script-Pane-and-Console-Pane.md) for details about using the tab completion feature to help in typing.</span></span>

### <a name="to-find-text-in-the-script-pane"></a><span data-ttu-id="4441c-152">Per trovare testo nel riquadro di script</span><span class="sxs-lookup"><span data-stu-id="4441c-152">To find text in the Script Pane</span></span>

1.  <span data-ttu-id="4441c-153">Per trovare testo in qualsiasi punto, premere **CTRL+F** o scegliere **Trova nello script** dal menu **Modifica**.</span><span class="sxs-lookup"><span data-stu-id="4441c-153">To find text anywhere, press **CTRL+F** or, on the **Edit** menu, click **Find in Script**.</span></span>

2.  <span data-ttu-id="4441c-154">Per trovare testo dopo il cursore, premere **F3** o scegliere **Trova successivo nello script** dal menu **Modifica**.</span><span class="sxs-lookup"><span data-stu-id="4441c-154">To find text after the cursor, press **F3** or, on the **Edit** menu, click **Find Next in Script**.</span></span>

3.  <span data-ttu-id="4441c-155">Per trovare testo prima del cursore, premere **MAIUSC+F3** o scegliere **Trova precedente nello script** dal menu **Modifica**.</span><span class="sxs-lookup"><span data-stu-id="4441c-155">To find text before the cursor, press **SHIFT+F3** or, on the **Edit** menu, click **Find Previous in Script**.</span></span>

### <a name="to-find-and-replace-text-in-the-script-pane"></a><span data-ttu-id="4441c-156">Per trovare e sostituire testo nel riquadro di script</span><span class="sxs-lookup"><span data-stu-id="4441c-156">To find and replace text in the Script Pane</span></span>
<span data-ttu-id="4441c-157">Premere **CRTL+H** o scegliere **Sostituisci nello script** dal menu **Modifica**.</span><span class="sxs-lookup"><span data-stu-id="4441c-157">Press **CRTL+H** or, on the **Edit** menu, click **Replace in Script**.</span></span> <span data-ttu-id="4441c-158">Immettere sia il testo da trovare che il testo con cui sostituirlo e quindi premere **INVIO**.</span><span class="sxs-lookup"><span data-stu-id="4441c-158">Enter both the text you want to find and the text with which you want to replace it, and then press **ENTER**.</span></span>

### <a name="to-go-to-a-particular-line-of-text-in-the-script-pane"></a><span data-ttu-id="4441c-159">Per passare a una specifica riga di testo nel riquadro di script</span><span class="sxs-lookup"><span data-stu-id="4441c-159">To go to a particular line of text in the Script Pane</span></span>

1.  <span data-ttu-id="4441c-160">Nel riquadro di script premere **CTRL+G** o scegliere **Vai alla riga** dal menu **Modifica**.</span><span class="sxs-lookup"><span data-stu-id="4441c-160">In the Script Pane, press **CTRL+G** or, on the **Edit** menu, click **Go to Line**.</span></span>

2.  <span data-ttu-id="4441c-161">Immettere un numero di riga.</span><span class="sxs-lookup"><span data-stu-id="4441c-161">Enter a line number.</span></span>

### <a name="to-copy-text-in-the-script-pane"></a><span data-ttu-id="4441c-162">Per copiare testo nel riquadro di script</span><span class="sxs-lookup"><span data-stu-id="4441c-162">To copy text in the Script Pane</span></span>

1.  <span data-ttu-id="4441c-163">Nel riquadro di script selezionare il testo da copiare.</span><span class="sxs-lookup"><span data-stu-id="4441c-163">In the Script Pane, select the text that you want to copy.</span></span>

2.  <span data-ttu-id="4441c-164">Premere **CTRL+C**, fare clic sull'icona **Copia** sulla barra degli strumenti o scegliere **Copia** dal menu **Modifica**.</span><span class="sxs-lookup"><span data-stu-id="4441c-164">Press **CTRL+C** or, on the toolbar, click the **Copy** icon, or on the **Edit** menu, click **Copy**.</span></span>

### <a name="to-cut-text-in-the-script-pane"></a><span data-ttu-id="4441c-165">Per tagliare testo nel riquadro di script</span><span class="sxs-lookup"><span data-stu-id="4441c-165">To cut text in the Script Pane</span></span>

1.  <span data-ttu-id="4441c-166">Nel riquadro di script selezionare il testo da tagliare.</span><span class="sxs-lookup"><span data-stu-id="4441c-166">In the Script Pane, select the text that you want to cut.</span></span>

2.  <span data-ttu-id="4441c-167">Premere **CTRL+X**, fare clic sull'icona **Taglia** sulla barra degli strumenti o scegliere **Taglia** dal menu **Modifica**.</span><span class="sxs-lookup"><span data-stu-id="4441c-167">Press **CTRL+X** or, on the toolbar, click the **Cut** icon, or on the **Edit** menu, click **Cut**.</span></span>

### <a name="to-paste-text-into-the-script-pane"></a><span data-ttu-id="4441c-168">Per incollare testo nel riquadro di script</span><span class="sxs-lookup"><span data-stu-id="4441c-168">To paste text into the Script Pane</span></span>
<span data-ttu-id="4441c-169">Premere **CTRL+V**, fare clic sull'icona **Incolla** sulla barra degli strumenti o scegliere **Incolla** dal menu **Modifica**.</span><span class="sxs-lookup"><span data-stu-id="4441c-169">Press **CTRL+V** or, on the toolbar, click the **Paste** icon, or on the **Edit** menu, click **Paste**.</span></span>

### <a name="to-undo-an-action-in-the-script-pane"></a><span data-ttu-id="4441c-170">Per annullare un'azione nel riquadro di script</span><span class="sxs-lookup"><span data-stu-id="4441c-170">To undo an action in the Script Pane</span></span>
<span data-ttu-id="4441c-171">Premere **CTRL+Z**, fare clic sull'icona **Annulla** sulla barra degli strumenti o scegliere **Annulla** dal menu **Modifica**.</span><span class="sxs-lookup"><span data-stu-id="4441c-171">Press **CTRL+Z** or, on the toolbar, click the **Undo** icon, or on the **Edit** menu, click **Undo**.</span></span>

### <a name="to-redo-an-action-in-the-script-pane"></a><span data-ttu-id="4441c-172">Per ripetere un'azione nel riquadro di script</span><span class="sxs-lookup"><span data-stu-id="4441c-172">To redo an action in the Script Pane</span></span>
<span data-ttu-id="4441c-173">Premere **CTRL+Y**, fare clic sull'icona **Ripeti** sulla barra degli strumenti o scegliere **Ripeti** dal menu **Modifica**.</span><span class="sxs-lookup"><span data-stu-id="4441c-173">Press **CTRL+Y** or, on the toolbar, click the **Redo** icon, or on the **Edit** menu, click **Redo**.</span></span>

## <span data-ttu-id="4441c-174"><a name="bkmk_3"></a>Come salvare uno script</span><span class="sxs-lookup"><span data-stu-id="4441c-174"><a name="bkmk_3"></a>How to save a script</span></span>
<span data-ttu-id="4441c-175">Per salvare uno script e assegnargli un nome, usare la procedura seguente.</span><span class="sxs-lookup"><span data-stu-id="4441c-175">Use the following steps to save and name a script.</span></span> <span data-ttu-id="4441c-176">Accanto al nome di uno script che non è stato ancora salvato dopo una modifica, compare un asterisco.</span><span class="sxs-lookup"><span data-stu-id="4441c-176">An asterisk appears next to the script name to mark a file that has not been saved since it was altered.</span></span> <span data-ttu-id="4441c-177">L'asterisco sparirà dopo il salvataggio del file.</span><span class="sxs-lookup"><span data-stu-id="4441c-177">The asterisk disappears when the file is saved.</span></span>

### <a name="to-save-a-script"></a><span data-ttu-id="4441c-178">Per salvare uno script</span><span class="sxs-lookup"><span data-stu-id="4441c-178">To save a script</span></span>
<span data-ttu-id="4441c-179">Premere **CTRL+S**, fare clic sull'icona **Salva** sulla barra degli strumenti o scegliere **Salva** dal menu **File**.</span><span class="sxs-lookup"><span data-stu-id="4441c-179">Press **CTRL+S** or, on the toolbar, click the **Save** icon, or on the **File** menu, click **Save**.</span></span>

### <a name="to-save-and-name-a-script"></a><span data-ttu-id="4441c-180">Per salvare uno script e assegnargli un nome</span><span class="sxs-lookup"><span data-stu-id="4441c-180">To save and name a script</span></span>

1.  <span data-ttu-id="4441c-181">Scegliere **Salva con nome** dal menu **File**.</span><span class="sxs-lookup"><span data-stu-id="4441c-181">On the **File** menu, click **Save As**.</span></span> <span data-ttu-id="4441c-182">Verrà visualizzata la finestra di dialogo **Salva con nome**.</span><span class="sxs-lookup"><span data-stu-id="4441c-182">The **Save As** dialog box will appear.</span></span>

2.  <span data-ttu-id="4441c-183">Nella casella **Nome file** immettere un nome per il file.</span><span class="sxs-lookup"><span data-stu-id="4441c-183">In the **File name** box, enter a name for the file.</span></span>

3.  <span data-ttu-id="4441c-184">Nella casella **Salva come** selezionare un tipo di file.</span><span class="sxs-lookup"><span data-stu-id="4441c-184">In the **Save as type** box, select a file type.</span></span> <span data-ttu-id="4441c-185">Ad esempio, nella casella **Salva come** selezionare "Script di PowerShell (\* .ps1)".</span><span class="sxs-lookup"><span data-stu-id="4441c-185">For example, in the **Save as type** box, select “PowerShell Scripts (\* .ps1)”.</span></span>

4.  <span data-ttu-id="4441c-186">Fare clic su **Salva**.</span><span class="sxs-lookup"><span data-stu-id="4441c-186">Click **Save**.</span></span>

### <a name="to-save-a-script-in-ascii-encoding"></a><span data-ttu-id="4441c-187">Per salvare uno script nella codifica ASCII</span><span class="sxs-lookup"><span data-stu-id="4441c-187">To save a script in ASCII encoding</span></span>
<span data-ttu-id="4441c-188">Per impostazione predefinita, Windows PowerShell ISE salva i file di script (con estensione ps1), i file di dati degli script (con estensione psd1) e i file di modulo di script ( con estensione psm1) in formato Unicode (BigEndianUnicode).</span><span class="sxs-lookup"><span data-stu-id="4441c-188">By default, Windows PowerShell ISE saves new script files (.ps1), script data files (.psd1), and script module files (.psm1) as Unicode (BigEndianUnicode) by default.</span></span> <span data-ttu-id="4441c-189">Per salvare uno script in un'altra codifica, ad esempio ASCII (ANSI), usare i metodi **Save** o **SaveAs** sull'oggetto [$psISE.CurrentFile](https://technet.microsoft.com/en-us/library/bc3300e4-9c17-4f00-a621-c8867126e3b3#CurrentFile).</span><span class="sxs-lookup"><span data-stu-id="4441c-189">To save a script in another encoding, such as ASCII (ANSI), use the **Save** or **SaveAs** methods on the [$psISE.CurrentFile](https://technet.microsoft.com/en-us/library/bc3300e4-9c17-4f00-a621-c8867126e3b3#CurrentFile) object.</span></span>

<span data-ttu-id="4441c-190">Il comando che segue salva un nuovo script con il nome MyScript.ps1 nella codifica ASCII.</span><span class="sxs-lookup"><span data-stu-id="4441c-190">The following command saves a new script as MyScript.ps1 with ASCII encoding.</span></span>

```
$psise.CurrentFile.SaveAs("MyScript.ps1", [System.Text.Encoding]::ASCII)
```

<span data-ttu-id="4441c-191">Il comando che segue sostituisce il file di script corrente con un file con lo stesso nome, ma con codifica ASCII.</span><span class="sxs-lookup"><span data-stu-id="4441c-191">The following command replaces the current script file with a file with the same name, but with ASCII encoding.</span></span>

```
$psise.CurrentFile.Save([System.Text.Encoding]::ASCII)
```

<span data-ttu-id="4441c-192">Il comando seguente ottiene la codifica del file corrente.</span><span class="sxs-lookup"><span data-stu-id="4441c-192">The following command gets the encoding of the current file.</span></span>

```
$psise.CurrentFile.encoding
```

<span data-ttu-id="4441c-193">Windows PowerShell ISE supporta le opzioni di codifica seguenti: ASCII, BigEndianUnicode, Unicode, UTF32, UTF7, UTF8 e predefinita.</span><span class="sxs-lookup"><span data-stu-id="4441c-193">Windows PowerShell ISE supports the following encoding options: ASCII, BigEndianUnicode, Unicode, UTF32, UTF7, UTF8 and Default.</span></span> <span data-ttu-id="4441c-194">Il valore dell'opzione di codifica predefinita varia in base al sistema.</span><span class="sxs-lookup"><span data-stu-id="4441c-194">The value of the Default option varies with the system.</span></span>

<span data-ttu-id="4441c-195">Windows PowerShell ISE non modifica la codifica degli script creati in altri editor, anche se si usano i comandi Salva o Salva con nome in Windows PowerShell ISE.</span><span class="sxs-lookup"><span data-stu-id="4441c-195">Windows PowerShell ISE does not change the encoding of scripts that were created by in other editors, even when you use the Save or Save As commands in Windows PowerShell ISE.</span></span>

## <a name="see-also"></a><span data-ttu-id="4441c-196">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="4441c-196">See Also</span></span>
- [<span data-ttu-id="4441c-197">Uso di Windows PowerShell ISE</span><span class="sxs-lookup"><span data-stu-id="4441c-197">Using the Windows PowerShell ISE</span></span>](Using-the-Windows-PowerShell-ISE.md)

