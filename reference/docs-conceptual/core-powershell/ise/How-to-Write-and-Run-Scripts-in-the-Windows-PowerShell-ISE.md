---
ms.date: 06/05/2017
keywords: powershell,cmdlet
title: Come scrivere ed eseguire script in Windows PowerShell ISE
ms.assetid: 62f916d9-b3a1-484a-bdfb-41f57112c22b
ms.openlocfilehash: 4d7c5352ef1dac6f63a50433676068f83a920db5
ms.sourcegitcommit: 01d6985ed190a222e9da1da41596f524f607a5bc
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 06/07/2018
ms.locfileid: "34483118"
---
# <a name="how-to-write-and-run-scripts-in-the-windows-powershell-ise"></a><span data-ttu-id="e02b2-103">Come scrivere ed eseguire script in Windows PowerShell ISE</span><span class="sxs-lookup"><span data-stu-id="e02b2-103">How to Write and Run Scripts in the Windows PowerShell ISE</span></span>

<span data-ttu-id="e02b2-104">Questo argomento descrive come creare, modificare, eseguire e salvare gli script nel riquadro di script.</span><span class="sxs-lookup"><span data-stu-id="e02b2-104">This topic describes how to create, edit, run, and save scripts in the Script Pane.</span></span>

## <a name="how-to-create-and-run-scripts"></a><span data-ttu-id="e02b2-105">Come creare ed eseguire script</span><span class="sxs-lookup"><span data-stu-id="e02b2-105">How to create and run scripts</span></span>

<span data-ttu-id="e02b2-106">È possibile aprire e modificare i file di Windows PowerShell nel riquadro di script.</span><span class="sxs-lookup"><span data-stu-id="e02b2-106">You can open and edit Windows PowerShell files in the Script Pane.</span></span> <span data-ttu-id="e02b2-107">Tipi di file di particolare interesse in Windows PowerShell sono i file di script (con estensione PS1), i file di dati degli script (con estensione PSD1) e i file di modulo di script (con estensione PSM1).</span><span class="sxs-lookup"><span data-stu-id="e02b2-107">Specific file types of interest in Windows PowerShell are script files (.ps1), script data files (.psd1), and script module files (.psm1).</span></span> <span data-ttu-id="e02b2-108">In questi file per la visualizzazione della sintassi nell'editor del riquadro di script vengono utilizzati i colori.</span><span class="sxs-lookup"><span data-stu-id="e02b2-108">These file types are syntax colored in the Script Pane editor.</span></span> <span data-ttu-id="e02b2-109">Altri tipi di file comuni che è possibile aprire nel riquadro di script sono file di configurazione (con estensione ps1xml), file XML e file di testo.</span><span class="sxs-lookup"><span data-stu-id="e02b2-109">Other common file types you may open in the Script Pane are configuration files (.ps1xml), XML files, and text files.</span></span>

> [!NOTE]
> <span data-ttu-id="e02b2-110">I criteri di esecuzione di Windows PowerShell determinano se è possibile eseguire script e caricare profili e file di configurazione di Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="e02b2-110">The Windows PowerShell execution policy determines whether you can run scripts and load Windows PowerShell profiles and configuration files.</span></span> <span data-ttu-id="e02b2-111">I criteri di esecuzione predefiniti prevedono restrizioni e impediscono l'esecuzione di tutti gli script e il caricamento di profili.</span><span class="sxs-lookup"><span data-stu-id="e02b2-111">The default execution policy, Restricted, prevents all scripts from running, and prevents loading profiles.</span></span> <span data-ttu-id="e02b2-112">Per modificare i criteri di esecuzione per consentire il caricamento e l'uso di profili, vedere [Set-ExecutionPolicy[PSITPro5_Security]](https://technet.microsoft.com/library/5690a0e1-495b-4e63-8280-65ead7bf01ab) e [about_Signing [v4]](https://technet.microsoft.com/library/fcbdd3b9-0b9f-4734-b5c7-e0dcc304fa1d).</span><span class="sxs-lookup"><span data-stu-id="e02b2-112">To change the execution policy to allow profiles to load and be used, see [Set-ExecutionPolicy[PSITPro5_Security]](https://technet.microsoft.com/library/5690a0e1-495b-4e63-8280-65ead7bf01ab) and [about_Signing [v4]](https://technet.microsoft.com/library/fcbdd3b9-0b9f-4734-b5c7-e0dcc304fa1d).</span></span>

### <a name="to-create-a-new-script-file"></a><span data-ttu-id="e02b2-113">Per creare un nuovo file di script</span><span class="sxs-lookup"><span data-stu-id="e02b2-113">To create a new script file</span></span>

<span data-ttu-id="e02b2-114">Sulla barra degli strumenti fare clic su **Nuovo** o scegliere **Nuovo** dal menu **File**.</span><span class="sxs-lookup"><span data-stu-id="e02b2-114">On the toolbar, click **New** , or on the **File** menu, click **New**.</span></span> <span data-ttu-id="e02b2-115">Il file creato viene visualizzato in una nuova scheda file nella scheda di PowerShell corrente. Tenere presente che le schede di PowerShell sono visibili solo se ne sono presenti più di una.</span><span class="sxs-lookup"><span data-stu-id="e02b2-115">The created file appears in a new file tab under the current PowerShell tab. Remember that the PowerShell tabs are only visible when there are more than one.</span></span> <span data-ttu-id="e02b2-116">Per impostazione predefinita viene creato un file di tipo script (con estensione ps1), ma è possibile salvarlo con un nuovo nome e un'altra estensione.</span><span class="sxs-lookup"><span data-stu-id="e02b2-116">By default a file of type script (.ps1) is created, but it can be saved with a new name and extension.</span></span> <span data-ttu-id="e02b2-117">Nella stessa scheda di PowerShell si possono creare più file di script.</span><span class="sxs-lookup"><span data-stu-id="e02b2-117">Multiple script files can be created in the same PowerShell tab.</span></span>

### <a name="to-open-an-existing-script"></a><span data-ttu-id="e02b2-118">Per aprire uno script esistente</span><span class="sxs-lookup"><span data-stu-id="e02b2-118">To open an existing script</span></span>

<span data-ttu-id="e02b2-119">Sulla barra degli strumenti fare clic su **Apri** o scegliere **Apri** dal menu **File**.</span><span class="sxs-lookup"><span data-stu-id="e02b2-119">On the toolbar, click **Open**, or on the **File** menu, click **Open**.</span></span> <span data-ttu-id="e02b2-120">Nella finestra di dialogo **Apri** selezionare il file da aprire.</span><span class="sxs-lookup"><span data-stu-id="e02b2-120">In the **Open** dialog box, select the file you want to open.</span></span> <span data-ttu-id="e02b2-121">Il file aperto viene visualizzato in una nuova scheda.</span><span class="sxs-lookup"><span data-stu-id="e02b2-121">The opened file appears in a new tab.</span></span>

### <a name="to-close-a-script-tab"></a><span data-ttu-id="e02b2-122">Per chiudere la scheda di uno script</span><span class="sxs-lookup"><span data-stu-id="e02b2-122">To close a script tab</span></span>

<span data-ttu-id="e02b2-123">Fare clic sulla scheda dello script che si vuole chiudere, quindi eseguire una delle operazioni seguenti:</span><span class="sxs-lookup"><span data-stu-id="e02b2-123">Click the script tab of the script you want to close, then do one of the following:</span></span>

1. <span data-ttu-id="e02b2-124">Fare clic sull'icona **Chiudi** (X) nella scheda dello script.</span><span class="sxs-lookup"><span data-stu-id="e02b2-124">Click the **Close** icon (X) on the script tab.</span></span>

2. <span data-ttu-id="e02b2-125">Scegliere **Chiudi** dal menu **File**.</span><span class="sxs-lookup"><span data-stu-id="e02b2-125">On the **File** menu, click **Close**.</span></span>

<span data-ttu-id="e02b2-126">Se il file è stato modificato dall'ultimo salvataggio, verrà chiesto se salvare le modifiche o ignorarle.</span><span class="sxs-lookup"><span data-stu-id="e02b2-126">If the file has been altered since it was last saved, you are prompted to save or discard it.</span></span>

### <a name="to-display-the-file-path"></a><span data-ttu-id="e02b2-127">Per visualizzare il percorso del file</span><span class="sxs-lookup"><span data-stu-id="e02b2-127">To display the file path</span></span>

<span data-ttu-id="e02b2-128">Nella scheda del file posizionare il puntatore del mouse sul nome del file.</span><span class="sxs-lookup"><span data-stu-id="e02b2-128">On the file tab, point to the file name.</span></span> <span data-ttu-id="e02b2-129">Il percorso completo del file di script appare in una descrizione comando.</span><span class="sxs-lookup"><span data-stu-id="e02b2-129">The fully qualified path to the script file appears in a tooltip.</span></span>

### <a name="to-run-a-script"></a><span data-ttu-id="e02b2-130">Per eseguire uno script</span><span class="sxs-lookup"><span data-stu-id="e02b2-130">To run a script</span></span>

<span data-ttu-id="e02b2-131">Sulla barra degli strumenti fare clic su **Esegui script** o scegliere **Esegui** dal menu **File**.</span><span class="sxs-lookup"><span data-stu-id="e02b2-131">On the toolbar, click **Run Script**, or on the **File** menu, click **Run**.</span></span>

### <a name="to-run-a-portion-of-a-script"></a><span data-ttu-id="e02b2-132">Per eseguire una parte di uno script</span><span class="sxs-lookup"><span data-stu-id="e02b2-132">To run a portion of a script</span></span>

1. <span data-ttu-id="e02b2-133">Nel riquadro di script selezionare una parte di uno script.</span><span class="sxs-lookup"><span data-stu-id="e02b2-133">In the Script Pane, select a portion of a script.</span></span>

2. <span data-ttu-id="e02b2-134">Sulla barra degli strumenti fare clic su **Esegui selezione** o scegliere **Esegui selezione** dal menu **File**.</span><span class="sxs-lookup"><span data-stu-id="e02b2-134">On the **File** menu, click **Run Selection**, or on the toolbar, click **Run Selection**.</span></span>

### <a name="to-stop-a-running-script"></a><span data-ttu-id="e02b2-135">Per arrestare l'esecuzione di uno script</span><span class="sxs-lookup"><span data-stu-id="e02b2-135">To stop a running script</span></span>

<span data-ttu-id="e02b2-136">Sulla barra degli strumenti fare clic su **Arresta operazione**, premere CTRL+INTERR o scegliere **Arresta operazione** dal menu **File**.</span><span class="sxs-lookup"><span data-stu-id="e02b2-136">On the toolbar, click **Stop Operation**, press CTRL+BREAK, or on the **File** menu, click **Stop Operation**.</span></span> <span data-ttu-id="e02b2-137">È anche possibile premere **CTRL+C**, a meno che non sia attualmente selezionato del testo. In quel caso, **CTRL+C** corrisponderà alla funzione di copia del testo selezionato.</span><span class="sxs-lookup"><span data-stu-id="e02b2-137">Pressing **CTRL+C** also works unless some text is currently selected, in which case **CTRL+C** maps to the copy function for the selected text.</span></span>

## <a name="how-to-write-and-edit-text-in-the-script-pane"></a><span data-ttu-id="e02b2-138">Come scrivere e modificare testo nel riquadro di script</span><span class="sxs-lookup"><span data-stu-id="e02b2-138">How to write and edit text in the Script Pane</span></span>

<span data-ttu-id="e02b2-139">Per modificare il testo nel riquadro di script, usare la procedura seguente.</span><span class="sxs-lookup"><span data-stu-id="e02b2-139">Use the following steps to edit text in the Script Pane.</span></span> <span data-ttu-id="e02b2-140">È possibile copiare, tagliare, incollare, trovare e sostituire testo.</span><span class="sxs-lookup"><span data-stu-id="e02b2-140">You can copy, cut, paste, find, and replace text.</span></span> <span data-ttu-id="e02b2-141">È anche possibile annullare e ripetere l'ultima operazione eseguita.</span><span class="sxs-lookup"><span data-stu-id="e02b2-141">You can also undo and redo the last action you just performed.</span></span> <span data-ttu-id="e02b2-142">I tasti di scelta rapida per eseguire queste operazioni sono identici a quelli usati in tutte le applicazioni di Windows.</span><span class="sxs-lookup"><span data-stu-id="e02b2-142">The keyboard shortcuts for performing these actions are the same as those used for all Windows applications.</span></span>

### <a name="to-enter-text-in-the-script-pane"></a><span data-ttu-id="e02b2-143">Per immettere testo nel riquadro di script</span><span class="sxs-lookup"><span data-stu-id="e02b2-143">To enter text in the Script Pane</span></span>

1. <span data-ttu-id="e02b2-144">Spostare il cursore sul riquadro di script facendo clic in un punto qualsiasi al suo interno o scegliendo **Vai al riquadro di script** dal menu **Visualizza**.</span><span class="sxs-lookup"><span data-stu-id="e02b2-144">Move the cursor to the Script Pane by clicking anywhere in the Script Pane, or by clicking **Go to Script Pane** in the **View** menu.</span></span>

2. <span data-ttu-id="e02b2-145">Creare uno script.</span><span class="sxs-lookup"><span data-stu-id="e02b2-145">Create a script.</span></span> <span data-ttu-id="e02b2-146">La colorazione della sintassi e la funzionalità di completamento tramite tasto TAB semplificano notevolmente l'esperienza in Windows PowerShell ISE.</span><span class="sxs-lookup"><span data-stu-id="e02b2-146">Syntax coloring and tab completion make this a richer experience in Windows PowerShell ISE.</span></span>

3. <span data-ttu-id="e02b2-147">Per maggiori informazioni sull'uso di questa funzionalità, vedere [Come usare la funzionalità di completamento tramite TAB nel riquadro di script e nel riquadro della console](How-to-Use-Tab-Completion-in-the-Script-Pane-and-Console-Pane.md).</span><span class="sxs-lookup"><span data-stu-id="e02b2-147">See [How to Use Tab Completion in the Script Pane and Console Pane](How-to-Use-Tab-Completion-in-the-Script-Pane-and-Console-Pane.md) for details about using the tab completion feature to help in typing.</span></span>

### <a name="to-find-text-in-the-script-pane"></a><span data-ttu-id="e02b2-148">Per trovare testo nel riquadro di script</span><span class="sxs-lookup"><span data-stu-id="e02b2-148">To find text in the Script Pane</span></span>

1. <span data-ttu-id="e02b2-149">Per trovare testo in qualsiasi punto, premere **CTRL+F** o scegliere **Trova nello script** dal menu **Modifica**.</span><span class="sxs-lookup"><span data-stu-id="e02b2-149">To find text anywhere, press **CTRL+F** or, on the **Edit** menu, click **Find in Script**.</span></span>

2. <span data-ttu-id="e02b2-150">Per trovare testo dopo il cursore, premere **F3** o scegliere **Trova successivo nello script** dal menu **Modifica**.</span><span class="sxs-lookup"><span data-stu-id="e02b2-150">To find text after the cursor, press **F3** or, on the **Edit** menu, click **Find Next in Script**.</span></span>

3. <span data-ttu-id="e02b2-151">Per trovare testo prima del cursore, premere **MAIUSC+F3** o scegliere **Trova precedente nello script** dal menu **Modifica**.</span><span class="sxs-lookup"><span data-stu-id="e02b2-151">To find text before the cursor, press **SHIFT+F3** or, on the **Edit** menu, click **Find Previous in Script**.</span></span>

### <a name="to-find-and-replace-text-in-the-script-pane"></a><span data-ttu-id="e02b2-152">Per trovare e sostituire testo nel riquadro di script</span><span class="sxs-lookup"><span data-stu-id="e02b2-152">To find and replace text in the Script Pane</span></span>

<span data-ttu-id="e02b2-153">Premere **CTRL+H** o scegliere **Sostituisci nello script** dal menu **Modifica**.</span><span class="sxs-lookup"><span data-stu-id="e02b2-153">Press **CTRL+H** or, on the **Edit** menu, click **Replace in Script**.</span></span> <span data-ttu-id="e02b2-154">Immettere sia il testo da trovare che il testo con cui sostituirlo e quindi premere **INVIO**.</span><span class="sxs-lookup"><span data-stu-id="e02b2-154">Enter both the text you want to find and the text with which you want to replace it, and then press **ENTER**.</span></span>

### <a name="to-go-to-a-particular-line-of-text-in-the-script-pane"></a><span data-ttu-id="e02b2-155">Per passare a una specifica riga di testo nel riquadro di script</span><span class="sxs-lookup"><span data-stu-id="e02b2-155">To go to a particular line of text in the Script Pane</span></span>

1. <span data-ttu-id="e02b2-156">Nel riquadro di script premere **CTRL+G** o scegliere **Vai alla riga** dal menu **Modifica**.</span><span class="sxs-lookup"><span data-stu-id="e02b2-156">In the Script Pane, press **CTRL+G** or, on the **Edit** menu, click **Go to Line**.</span></span>

2. <span data-ttu-id="e02b2-157">Immettere un numero di riga.</span><span class="sxs-lookup"><span data-stu-id="e02b2-157">Enter a line number.</span></span>

### <a name="to-copy-text-in-the-script-pane"></a><span data-ttu-id="e02b2-158">Per copiare testo nel riquadro di script</span><span class="sxs-lookup"><span data-stu-id="e02b2-158">To copy text in the Script Pane</span></span>

1. <span data-ttu-id="e02b2-159">Nel riquadro di script selezionare il testo da copiare.</span><span class="sxs-lookup"><span data-stu-id="e02b2-159">In the Script Pane, select the text that you want to copy.</span></span>

2. <span data-ttu-id="e02b2-160">Premere **CTRL+C**, fare clic sull'icona **Copia** sulla barra degli strumenti o scegliere **Copia** dal menu **Modifica**.</span><span class="sxs-lookup"><span data-stu-id="e02b2-160">Press **CTRL+C** or, on the toolbar, click the **Copy** icon, or on the **Edit** menu, click **Copy**.</span></span>

### <a name="to-cut-text-in-the-script-pane"></a><span data-ttu-id="e02b2-161">Per tagliare testo nel riquadro di script</span><span class="sxs-lookup"><span data-stu-id="e02b2-161">To cut text in the Script Pane</span></span>

1. <span data-ttu-id="e02b2-162">Nel riquadro di script selezionare il testo da tagliare.</span><span class="sxs-lookup"><span data-stu-id="e02b2-162">In the Script Pane, select the text that you want to cut.</span></span>

2. <span data-ttu-id="e02b2-163">Premere **CTRL+X**, fare clic sull'icona **Taglia** sulla barra degli strumenti o scegliere **Taglia** dal menu **Modifica**.</span><span class="sxs-lookup"><span data-stu-id="e02b2-163">Press **CTRL+X** or, on the toolbar, click the **Cut** icon, or on the **Edit** menu, click **Cut**.</span></span>

### <a name="to-paste-text-into-the-script-pane"></a><span data-ttu-id="e02b2-164">Per incollare testo nel riquadro di script</span><span class="sxs-lookup"><span data-stu-id="e02b2-164">To paste text into the Script Pane</span></span>

<span data-ttu-id="e02b2-165">Premere **CTRL+V**, fare clic sull'icona **Incolla** sulla barra degli strumenti o scegliere **Incolla** dal menu **Modifica**.</span><span class="sxs-lookup"><span data-stu-id="e02b2-165">Press **CTRL+V** or, on the toolbar, click the **Paste** icon, or on the **Edit** menu, click **Paste**.</span></span>

### <a name="to-undo-an-action-in-the-script-pane"></a><span data-ttu-id="e02b2-166">Per annullare un'azione nel riquadro di script</span><span class="sxs-lookup"><span data-stu-id="e02b2-166">To undo an action in the Script Pane</span></span>

<span data-ttu-id="e02b2-167">Premere **CTRL+Z**, fare clic sull'icona **Annulla** sulla barra degli strumenti o scegliere **Annulla** dal menu **Modifica**.</span><span class="sxs-lookup"><span data-stu-id="e02b2-167">Press **CTRL+Z** or, on the toolbar, click the **Undo** icon, or on the **Edit** menu, click **Undo**.</span></span>

### <a name="to-redo-an-action-in-the-script-pane"></a><span data-ttu-id="e02b2-168">Per ripetere un'azione nel riquadro di script</span><span class="sxs-lookup"><span data-stu-id="e02b2-168">To redo an action in the Script Pane</span></span>

<span data-ttu-id="e02b2-169">Premere **CTRL+Y**, fare clic sull'icona **Ripeti** sulla barra degli strumenti o scegliere **Ripeti** dal menu **Modifica**.</span><span class="sxs-lookup"><span data-stu-id="e02b2-169">Press **CTRL+Y** or, on the toolbar, click the **Redo** icon, or on the **Edit** menu, click **Redo**.</span></span>

## <a name="how-to-save-a-script"></a><span data-ttu-id="e02b2-170">Come salvare uno script</span><span class="sxs-lookup"><span data-stu-id="e02b2-170">How to save a script</span></span>

<span data-ttu-id="e02b2-171">Per salvare uno script e assegnargli un nome, usare la procedura seguente.</span><span class="sxs-lookup"><span data-stu-id="e02b2-171">Use the following steps to save and name a script.</span></span> <span data-ttu-id="e02b2-172">Accanto al nome di uno script che non è stato ancora salvato dopo una modifica, compare un asterisco.</span><span class="sxs-lookup"><span data-stu-id="e02b2-172">An asterisk appears next to the script name to mark a file that has not been saved since it was altered.</span></span> <span data-ttu-id="e02b2-173">L'asterisco sparirà dopo il salvataggio del file.</span><span class="sxs-lookup"><span data-stu-id="e02b2-173">The asterisk disappears when the file is saved.</span></span>

### <a name="to-save-a-script"></a><span data-ttu-id="e02b2-174">Per salvare uno script</span><span class="sxs-lookup"><span data-stu-id="e02b2-174">To save a script</span></span>

<span data-ttu-id="e02b2-175">Premere **CTRL+S**, fare clic sull'icona **Salva** sulla barra degli strumenti o scegliere **Salva** dal menu **File**.</span><span class="sxs-lookup"><span data-stu-id="e02b2-175">Press **CTRL+S** or, on the toolbar, click the **Save** icon, or on the **File** menu, click **Save**.</span></span>

### <a name="to-save-and-name-a-script"></a><span data-ttu-id="e02b2-176">Per salvare uno script e assegnargli un nome</span><span class="sxs-lookup"><span data-stu-id="e02b2-176">To save and name a script</span></span>

1. <span data-ttu-id="e02b2-177">Scegliere **Salva con nome** dal menu **File**.</span><span class="sxs-lookup"><span data-stu-id="e02b2-177">On the **File** menu, click **Save As**.</span></span> <span data-ttu-id="e02b2-178">Verrà visualizzata la finestra di dialogo **Salva con nome**.</span><span class="sxs-lookup"><span data-stu-id="e02b2-178">The **Save As** dialog box will appear.</span></span>

2. <span data-ttu-id="e02b2-179">Nella casella **Nome file** immettere un nome per il file.</span><span class="sxs-lookup"><span data-stu-id="e02b2-179">In the **File name** box, enter a name for the file.</span></span>

3. <span data-ttu-id="e02b2-180">Nella casella **Salva come** selezionare un tipo di file.</span><span class="sxs-lookup"><span data-stu-id="e02b2-180">In the **Save as type** box, select a file type.</span></span> <span data-ttu-id="e02b2-181">Ad esempio, nella casella **Salva come** selezionare 'Script di PowerShell (\* .ps1)'.</span><span class="sxs-lookup"><span data-stu-id="e02b2-181">For example, in the **Save as type** box, select 'œPowerShell Scripts (\* .ps1)'.</span></span>

4. <span data-ttu-id="e02b2-182">Fare clic su **Salva**.</span><span class="sxs-lookup"><span data-stu-id="e02b2-182">Click **Save**.</span></span>

### <a name="to-save-a-script-in-ascii-encoding"></a><span data-ttu-id="e02b2-183">Per salvare uno script nella codifica ASCII</span><span class="sxs-lookup"><span data-stu-id="e02b2-183">To save a script in ASCII encoding</span></span>

<span data-ttu-id="e02b2-184">Per impostazione predefinita, Windows PowerShell ISE salva i nuovi file di script (con estensione PS1), i file di dati di script (con estensione PSD1) e i file di modulo di script (con estensione PSM1) in formato Unicode (BigEndianUnicode). Â Per salvare uno script in un'altra codifica, ad esempio ASCII (ANSI), utilizzare i metodi **Save** o **SaveAs** nell’oggetto [$psISE.CurrentFile](https://technet.microsoft.com/library/bc3300e4-9c17-4f00-a621-c8867126e3b3#CurrentFile).</span><span class="sxs-lookup"><span data-stu-id="e02b2-184">By default, Windows PowerShell ISE saves new script files (.ps1), script data files (.psd1), and script module files (.psm1) as Unicode (BigEndianUnicode) by default.Â To save a script in another encoding, such as ASCII (ANSI), use the **Save** or **SaveAs** methods on the [$psISE.CurrentFile](https://technet.microsoft.com/library/bc3300e4-9c17-4f00-a621-c8867126e3b3#CurrentFile) object.</span></span>

<span data-ttu-id="e02b2-185">Il comando che segue salva un nuovo script con il nome MyScript.ps1 nella codifica ASCII.</span><span class="sxs-lookup"><span data-stu-id="e02b2-185">The following command saves a new script as MyScript.ps1 with ASCII encoding.</span></span>

```powershell
$psISE.CurrentFile.SaveAs("MyScript.ps1", [System.Text.Encoding]::ASCII)
```

<span data-ttu-id="e02b2-186">Il comando che segue sostituisce il file di script corrente con un file con lo stesso nome, ma con codifica ASCII.</span><span class="sxs-lookup"><span data-stu-id="e02b2-186">The following command replaces the current script file with a file with the same name, but with ASCII encoding.</span></span>

```powershell
$psISE.CurrentFile.Save([System.Text.Encoding]::ASCII)
```

<span data-ttu-id="e02b2-187">Il comando seguente ottiene la codifica del file corrente.</span><span class="sxs-lookup"><span data-stu-id="e02b2-187">The following command gets the encoding of the current file.</span></span>

```powershell
$psISE.CurrentFile.encoding
```

<span data-ttu-id="e02b2-188">Windows PowerShell ISE supporta le opzioni di codifica seguenti: ASCII, BigEndianUnicode, Unicode, UTF32, UTF7, UTF8 e predefinita.</span><span class="sxs-lookup"><span data-stu-id="e02b2-188">Windows PowerShell ISE supports the following encoding options: ASCII, BigEndianUnicode, Unicode, UTF32, UTF7, UTF8 and Default.</span></span> <span data-ttu-id="e02b2-189">Il valore dell'opzione di codifica predefinita varia in base al sistema.</span><span class="sxs-lookup"><span data-stu-id="e02b2-189">The value of the Default option varies with the system.</span></span>

<span data-ttu-id="e02b2-190">Windows PowerShell ISE non modifica la codifica degli script creati in altri editor, anche se si usano i comandi Salva o Salva con nome in Windows PowerShell ISE.</span><span class="sxs-lookup"><span data-stu-id="e02b2-190">Windows PowerShell ISE does not change the encoding of scripts that were created by in other editors, even when you use the Save or Save As commands in Windows PowerShell ISE.</span></span>

## <a name="see-also"></a><span data-ttu-id="e02b2-191">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="e02b2-191">See Also</span></span>

- [<span data-ttu-id="e02b2-192">Esplorazione di Windows PowerShell ISE</span><span class="sxs-lookup"><span data-stu-id="e02b2-192">Exploring the Windows PowerShell ISE</span></span>](../../getting-started/fundamental/exploring-the-windows-powershell-ise.md)