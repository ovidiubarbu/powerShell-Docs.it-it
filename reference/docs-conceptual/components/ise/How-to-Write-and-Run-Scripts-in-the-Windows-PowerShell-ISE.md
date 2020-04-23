---
ms.date: 01/02/2020
keywords: powershell,cmdlet
title: Come scrivere ed eseguire script in Windows PowerShell ISE
ms.openlocfilehash: 2e3122a3b436ba878d2c5f9d72d4f9e024d4d031
ms.sourcegitcommit: 6545c60578f7745be015111052fd7769f8289296
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/22/2020
ms.locfileid: "79402528"
---
# <a name="how-to-write-and-run-scripts-in-the-windows-powershell-ise"></a><span data-ttu-id="f1c7e-103">Come scrivere ed eseguire script in Windows PowerShell ISE</span><span class="sxs-lookup"><span data-stu-id="f1c7e-103">How to Write and Run Scripts in the Windows PowerShell ISE</span></span>

<span data-ttu-id="f1c7e-104">Questo articolo descrive come creare, modificare, eseguire e salvare script nel riquadro Script.</span><span class="sxs-lookup"><span data-stu-id="f1c7e-104">This article describes how to create, edit, run, and save scripts in the Script Pane.</span></span>

## <a name="how-to-create-and-run-scripts"></a><span data-ttu-id="f1c7e-105">Come creare ed eseguire script</span><span class="sxs-lookup"><span data-stu-id="f1c7e-105">How to create and run scripts</span></span>

<span data-ttu-id="f1c7e-106">È possibile aprire e modificare i file di Windows PowerShell nel riquadro di script.</span><span class="sxs-lookup"><span data-stu-id="f1c7e-106">You can open and edit Windows PowerShell files in the Script Pane.</span></span> <span data-ttu-id="f1c7e-107">Tipi di file di particolare interesse in Windows PowerShell sono i file di script (`.ps1`), i file di dati degli script (`.psd1`) e i file di modulo di script (`.psm1`).</span><span class="sxs-lookup"><span data-stu-id="f1c7e-107">Specific file types of interest in Windows PowerShell are script files (`.ps1`), script data files (`.psd1`), and script module files (`.psm1`).</span></span> <span data-ttu-id="f1c7e-108">In questi file per la visualizzazione della sintassi nell'editor del riquadro di script vengono utilizzati i colori.</span><span class="sxs-lookup"><span data-stu-id="f1c7e-108">These file types are syntax colored in the Script Pane editor.</span></span> <span data-ttu-id="f1c7e-109">Altri tipi di file comuni che è possibile aprire nel riquadro di script sono file di configurazione (`.ps1xml`), file XML e file di testo.</span><span class="sxs-lookup"><span data-stu-id="f1c7e-109">Other common file types you may open in the Script Pane are configuration files (`.ps1xml`), XML files, and text files.</span></span>

> [!NOTE]
> <span data-ttu-id="f1c7e-110">I criteri di esecuzione di Windows PowerShell determinano se è possibile eseguire script e caricare profili e file di configurazione di Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="f1c7e-110">The Windows PowerShell execution policy determines whether you can run scripts and load Windows PowerShell profiles and configuration files.</span></span> <span data-ttu-id="f1c7e-111">I criteri di esecuzione predefiniti prevedono restrizioni e impediscono l'esecuzione di tutti gli script e il caricamento di profili.</span><span class="sxs-lookup"><span data-stu-id="f1c7e-111">The default execution policy, Restricted, prevents all scripts from running, and prevents loading profiles.</span></span> <span data-ttu-id="f1c7e-112">Per modificare i criteri di esecuzione in modo da consentire il caricamento e l'uso di profili, vedere [Set-ExecutionPolicy](/powershell/module/microsoft.powershell.security/set-executionpolicy) e [about_Signing](/powershell/module/microsoft.powershell.core/about/about_signing).</span><span class="sxs-lookup"><span data-stu-id="f1c7e-112">To change the execution policy to allow profiles to load and be used, see [Set-ExecutionPolicy](/powershell/module/microsoft.powershell.security/set-executionpolicy) and [about_Signing](/powershell/module/microsoft.powershell.core/about/about_signing).</span></span>

### <a name="to-create-a-new-script-file"></a><span data-ttu-id="f1c7e-113">Per creare un nuovo file di script</span><span class="sxs-lookup"><span data-stu-id="f1c7e-113">To create a new script file</span></span>

<span data-ttu-id="f1c7e-114">Sulla barra degli strumenti fare clic su **Nuovo** oppure scegliere **Nuovo** dal menu **File**.</span><span class="sxs-lookup"><span data-stu-id="f1c7e-114">On the toolbar, click **New**, or on the **File** menu, click **New**.</span></span> <span data-ttu-id="f1c7e-115">Il file creato viene visualizzato in una nuova scheda file nella scheda di PowerShell corrente. Tenere presente che le schede di PowerShell sono visibili solo se ne sono presenti più di una.</span><span class="sxs-lookup"><span data-stu-id="f1c7e-115">The created file appears in a new file tab under the current PowerShell tab. Remember that the PowerShell tabs are only visible when there are more than one.</span></span> <span data-ttu-id="f1c7e-116">Per impostazione predefinita viene creato un file di tipo script (`.ps1`), ma è possibile salvarlo con un nuovo nome e un'altra estensione.</span><span class="sxs-lookup"><span data-stu-id="f1c7e-116">By default a file of type script (`.ps1`) is created, but it can be saved with a new name and extension.</span></span> <span data-ttu-id="f1c7e-117">Nella stessa scheda di PowerShell si possono creare più file di script.</span><span class="sxs-lookup"><span data-stu-id="f1c7e-117">Multiple script files can be created in the same PowerShell tab.</span></span>

### <a name="to-open-an-existing-script"></a><span data-ttu-id="f1c7e-118">Per aprire uno script esistente</span><span class="sxs-lookup"><span data-stu-id="f1c7e-118">To open an existing script</span></span>

<span data-ttu-id="f1c7e-119">Sulla barra degli strumenti fare clic su **Apri** o scegliere **Apri** dal menu **File**.</span><span class="sxs-lookup"><span data-stu-id="f1c7e-119">On the toolbar, click **Open**, or on the **File** menu, click **Open**.</span></span> <span data-ttu-id="f1c7e-120">Nella finestra di dialogo **Apri** selezionare il file da aprire.</span><span class="sxs-lookup"><span data-stu-id="f1c7e-120">In the **Open** dialog box, select the file you want to open.</span></span> <span data-ttu-id="f1c7e-121">Il file aperto viene visualizzato in una nuova scheda.</span><span class="sxs-lookup"><span data-stu-id="f1c7e-121">The opened file appears in a new tab.</span></span>

### <a name="to-close-a-script-tab"></a><span data-ttu-id="f1c7e-122">Per chiudere la scheda di uno script</span><span class="sxs-lookup"><span data-stu-id="f1c7e-122">To close a script tab</span></span>

<span data-ttu-id="f1c7e-123">Fare clic sull'icona **Chiudi** (**X**) della scheda del file che si vuole chiudere o selezionare il menu **File** e fare clic su **Chiudi**.</span><span class="sxs-lookup"><span data-stu-id="f1c7e-123">Click the **Close** icon (**X**) of the file tab you want to close or select the **File** menu and click **Close**.</span></span>

<span data-ttu-id="f1c7e-124">Se il file è stato modificato dall'ultimo salvataggio, viene chiesto se salvare le modifiche o ignorarle.</span><span class="sxs-lookup"><span data-stu-id="f1c7e-124">If the file has been altered since it was last saved, you're prompted to save or discard it.</span></span>

### <a name="to-display-the-file-path"></a><span data-ttu-id="f1c7e-125">Per visualizzare il percorso del file</span><span class="sxs-lookup"><span data-stu-id="f1c7e-125">To display the file path</span></span>

<span data-ttu-id="f1c7e-126">Nella scheda del file posizionare il puntatore del mouse sul nome del file.</span><span class="sxs-lookup"><span data-stu-id="f1c7e-126">On the file tab, point to the file name.</span></span> <span data-ttu-id="f1c7e-127">Il percorso completo del file di script appare in una descrizione comando.</span><span class="sxs-lookup"><span data-stu-id="f1c7e-127">The fully qualified path to the script file appears in a tooltip.</span></span>

### <a name="to-run-a-script"></a><span data-ttu-id="f1c7e-128">Per eseguire uno script</span><span class="sxs-lookup"><span data-stu-id="f1c7e-128">To run a script</span></span>

<span data-ttu-id="f1c7e-129">Sulla barra degli strumenti fare clic su **Esegui script** o scegliere **Esegui** dal menu **File**.</span><span class="sxs-lookup"><span data-stu-id="f1c7e-129">On the toolbar, click **Run Script**, or on the **File** menu, click **Run**.</span></span>

### <a name="to-run-a-portion-of-a-script"></a><span data-ttu-id="f1c7e-130">Per eseguire una parte di uno script</span><span class="sxs-lookup"><span data-stu-id="f1c7e-130">To run a portion of a script</span></span>

1. <span data-ttu-id="f1c7e-131">Nel riquadro di script selezionare una parte di uno script.</span><span class="sxs-lookup"><span data-stu-id="f1c7e-131">In the Script Pane, select a portion of a script.</span></span>
2. <span data-ttu-id="f1c7e-132">Sulla barra degli strumenti fare clic su **Esegui selezione** o scegliere **Esegui selezione** dal menu **File**.</span><span class="sxs-lookup"><span data-stu-id="f1c7e-132">On the **File** menu, click **Run Selection**, or on the toolbar, click **Run Selection**.</span></span>

### <a name="to-stop-a-running-script"></a><span data-ttu-id="f1c7e-133">Per arrestare l'esecuzione di uno script</span><span class="sxs-lookup"><span data-stu-id="f1c7e-133">To stop a running script</span></span>

<span data-ttu-id="f1c7e-134">È possibile arrestare uno script in esecuzione in diversi modi.</span><span class="sxs-lookup"><span data-stu-id="f1c7e-134">There are several ways to stop a running script.</span></span>

- <span data-ttu-id="f1c7e-135">Fare clic su **Arresta operazione** sulla barra degli strumenti</span><span class="sxs-lookup"><span data-stu-id="f1c7e-135">Click **Stop Operation** on the toolbar</span></span>
- <span data-ttu-id="f1c7e-136">Premere <kbd>CTRL</kbd>+<kbd>INTERR</kbd></span><span class="sxs-lookup"><span data-stu-id="f1c7e-136">Press <kbd>CTRL</kbd>+<kbd>BREAK</kbd></span></span>
- <span data-ttu-id="f1c7e-137">Selezionare il menu **File** e fare clic su **Arresta operazione**.</span><span class="sxs-lookup"><span data-stu-id="f1c7e-137">Select the **File** menu and click **Stop Operation**.</span></span>

<span data-ttu-id="f1c7e-138">È anche possibile premere <kbd>CTRL</kbd>+<kbd>C</kbd>, a meno che non sia selezionata parte del testo. In questo caso <kbd>CTRL</kbd>+<kbd>C</kbd> corrisponderà alla funzione di copia del testo selezionato.</span><span class="sxs-lookup"><span data-stu-id="f1c7e-138">Pressing <kbd>CTRL</kbd>+<kbd>C</kbd> also works unless some text is currently selected, in which case <kbd>CTRL</kbd>+<kbd>C</kbd> maps to the copy function for the selected text.</span></span>

## <a name="how-to-write-and-edit-text-in-the-script-pane"></a><span data-ttu-id="f1c7e-139">Come scrivere e modificare testo nel riquadro di script</span><span class="sxs-lookup"><span data-stu-id="f1c7e-139">How to write and edit text in the Script Pane</span></span>

<span data-ttu-id="f1c7e-140">È possibile copiare, tagliare, incollare, trovare e sostituire testo nel riquadro Script.</span><span class="sxs-lookup"><span data-stu-id="f1c7e-140">You can copy, cut, paste, find, and replace text in the Script Pane.</span></span> <span data-ttu-id="f1c7e-141">È anche possibile annullare e ripetere l'ultima operazione eseguita.</span><span class="sxs-lookup"><span data-stu-id="f1c7e-141">You can also undo and redo the last action you just performed.</span></span> <span data-ttu-id="f1c7e-142">I tasti di scelta rapida per eseguire queste operazioni sono identici a quelli usati in tutte le applicazioni di Windows.</span><span class="sxs-lookup"><span data-stu-id="f1c7e-142">The keyboard shortcuts for these actions are the same shortcuts used for all Windows applications.</span></span>

### <a name="to-enter-text-in-the-script-pane"></a><span data-ttu-id="f1c7e-143">Per immettere testo nel riquadro di script</span><span class="sxs-lookup"><span data-stu-id="f1c7e-143">To enter text in the Script Pane</span></span>

1. <span data-ttu-id="f1c7e-144">Spostare il cursore sul riquadro di script facendo clic in un punto qualsiasi al suo interno o scegliendo **Vai al riquadro di script** dal menu **Visualizza**.</span><span class="sxs-lookup"><span data-stu-id="f1c7e-144">Move the cursor to the Script Pane by clicking anywhere in the Script Pane, or by clicking **Go to Script Pane** in the **View** menu.</span></span>
2. <span data-ttu-id="f1c7e-145">Creare uno script.</span><span class="sxs-lookup"><span data-stu-id="f1c7e-145">Create a script.</span></span> <span data-ttu-id="f1c7e-146">La colorazione della sintassi e la funzionalità di completamento tramite tasto TAB offrono un'esperienza di modifica più avanzata in Windows PowerShell ISE.</span><span class="sxs-lookup"><span data-stu-id="f1c7e-146">Syntax coloring and tab completion provide a richer editing experience in Windows PowerShell ISE.</span></span>
3. <span data-ttu-id="f1c7e-147">Per maggiori informazioni sull'uso di questa funzionalità, vedere [Come usare la funzionalità di completamento tramite TAB nel riquadro di script e nel riquadro della console](How-to-Use-Tab-Completion-in-the-Script-Pane-and-Console-Pane.md).</span><span class="sxs-lookup"><span data-stu-id="f1c7e-147">See [How to Use Tab Completion in the Script Pane and Console Pane](How-to-Use-Tab-Completion-in-the-Script-Pane-and-Console-Pane.md) for details about using the tab completion feature to help in typing.</span></span>

### <a name="to-find-text-in-the-script-pane"></a><span data-ttu-id="f1c7e-148">Per trovare testo nel riquadro di script</span><span class="sxs-lookup"><span data-stu-id="f1c7e-148">To find text in the Script Pane</span></span>

1. <span data-ttu-id="f1c7e-149">Per trovare testo in qualsiasi punto, premere <kbd>CTRL</kbd>+<kbd>F</kbd> oppure dal menu **Modifica** scegliere **Trova nello script**.</span><span class="sxs-lookup"><span data-stu-id="f1c7e-149">To find text anywhere, press <kbd>CTRL</kbd>+<kbd>F</kbd> or, on the **Edit** menu, click **Find in Script**.</span></span>
2. <span data-ttu-id="f1c7e-150">Per trovare testo dopo il cursore, premere <kbd>F3</kbd> o scegliere **Trova successivo nello script** dal menu **Modifica**.</span><span class="sxs-lookup"><span data-stu-id="f1c7e-150">To find text after the cursor, press <kbd>F3</kbd> or, on the **Edit** menu, click **Find Next in Script**.</span></span>
3. <span data-ttu-id="f1c7e-151">Per trovare testo prima del cursore, premere <kbd>MAIUSC</kbd>+<kbd>F3</kbd> oppure dal menu **Modifica** scegliere **Trova precedente nello script**.</span><span class="sxs-lookup"><span data-stu-id="f1c7e-151">To find text before the cursor, press <kbd>SHIFT</kbd>+<kbd>F3</kbd> or, on the **Edit** menu, click **Find Previous in Script**.</span></span>

### <a name="to-find-and-replace-text-in-the-script-pane"></a><span data-ttu-id="f1c7e-152">Per trovare e sostituire testo nel riquadro di script</span><span class="sxs-lookup"><span data-stu-id="f1c7e-152">To find and replace text in the Script Pane</span></span>

<span data-ttu-id="f1c7e-153">Premere <kbd>CTRL</kbd>+<kbd>H</kbd> o scegliere **Sostituisci nello script** dal menu **Modifica**.</span><span class="sxs-lookup"><span data-stu-id="f1c7e-153">Press <kbd>CTRL</kbd>+<kbd>H</kbd> or, on the **Edit** menu, click **Replace in Script**.</span></span> <span data-ttu-id="f1c7e-154">Immettere il testo che si vuole trovare e il testo sostitutivo e quindi premere <kbd>INVIO</kbd>.</span><span class="sxs-lookup"><span data-stu-id="f1c7e-154">Enter the text you want to find and the replacement text, then press <kbd>ENTER</kbd>.</span></span>

### <a name="to-go-to-a-particular-line-of-text-in-the-script-pane"></a><span data-ttu-id="f1c7e-155">Per passare a una specifica riga di testo nel riquadro di script</span><span class="sxs-lookup"><span data-stu-id="f1c7e-155">To go to a particular line of text in the Script Pane</span></span>

1. <span data-ttu-id="f1c7e-156">Nel riquadro di script premere <kbd>CTRL</kbd>+<kbd>G</kbd> oppure dal menu **Modifica** scegliere **Vai alla riga**.</span><span class="sxs-lookup"><span data-stu-id="f1c7e-156">In the Script Pane, press <kbd>CTRL</kbd>+<kbd>G</kbd> or, on the **Edit** menu, click **Go to Line**.</span></span>

2. <span data-ttu-id="f1c7e-157">Immettere un numero di riga.</span><span class="sxs-lookup"><span data-stu-id="f1c7e-157">Enter a line number.</span></span>

### <a name="to-copy-text-in-the-script-pane"></a><span data-ttu-id="f1c7e-158">Per copiare testo nel riquadro di script</span><span class="sxs-lookup"><span data-stu-id="f1c7e-158">To copy text in the Script Pane</span></span>

1. <span data-ttu-id="f1c7e-159">Nel riquadro di script selezionare il testo da copiare.</span><span class="sxs-lookup"><span data-stu-id="f1c7e-159">In the Script Pane, select the text that you want to copy.</span></span>

2. <span data-ttu-id="f1c7e-160">Premere <kbd>CTRL</kbd>+<kbd>C</kbd>. In alternativa, sulla barra degli strumenti fare clic sull'icona **Copia** oppure dal menu **Modifica** scegliere **Copia**.</span><span class="sxs-lookup"><span data-stu-id="f1c7e-160">Press <kbd>CTRL</kbd>+<kbd>C</kbd> or, on the toolbar, click the **Copy** icon, or on the **Edit** menu, click **Copy**.</span></span>

### <a name="to-cut-text-in-the-script-pane"></a><span data-ttu-id="f1c7e-161">Per tagliare testo nel riquadro di script</span><span class="sxs-lookup"><span data-stu-id="f1c7e-161">To cut text in the Script Pane</span></span>

1. <span data-ttu-id="f1c7e-162">Nel riquadro di script selezionare il testo da tagliare.</span><span class="sxs-lookup"><span data-stu-id="f1c7e-162">In the Script Pane, select the text that you want to cut.</span></span>
2. <span data-ttu-id="f1c7e-163">Premere <kbd>CTRL</kbd>+<kbd>X</kbd>. In alternativa, sulla barra degli strumenti fare clic sull'icona **Taglia** oppure dal menu **Modifica** scegliere **Taglia**.</span><span class="sxs-lookup"><span data-stu-id="f1c7e-163">Press <kbd>CTRL</kbd>+<kbd>X</kbd> or, on the toolbar, click the **Cut** icon, or on the **Edit** menu, click **Cut**.</span></span>

### <a name="to-paste-text-into-the-script-pane"></a><span data-ttu-id="f1c7e-164">Per incollare testo nel riquadro di script</span><span class="sxs-lookup"><span data-stu-id="f1c7e-164">To paste text into the Script Pane</span></span>

<span data-ttu-id="f1c7e-165">Premere <kbd>CTRL</kbd>+<kbd>V</kbd>. In alternativa, sulla barra degli strumenti fare clic sull'icona **Incolla** oppure dal menu **Modifica** scegliere **Incolla**.</span><span class="sxs-lookup"><span data-stu-id="f1c7e-165">Press <kbd>CTRL</kbd>+<kbd>V</kbd> or, on the toolbar, click the **Paste** icon, or on the **Edit** menu, click **Paste**.</span></span>

### <a name="to-undo-an-action-in-the-script-pane"></a><span data-ttu-id="f1c7e-166">Per annullare un'azione nel riquadro di script</span><span class="sxs-lookup"><span data-stu-id="f1c7e-166">To undo an action in the Script Pane</span></span>

<span data-ttu-id="f1c7e-167">Premere <kbd>CTRL</kbd>+<kbd>Z</kbd>. In alternativa, sulla barra degli strumenti fare clic sull'icona **Annulla** oppure dal menu **Modifica** scegliere **Annulla**.</span><span class="sxs-lookup"><span data-stu-id="f1c7e-167">Press <kbd>CTRL</kbd>+<kbd>Z</kbd> or, on the toolbar, click the **Undo** icon, or on the **Edit** menu, click **Undo**.</span></span>

### <a name="to-redo-an-action-in-the-script-pane"></a><span data-ttu-id="f1c7e-168">Per ripetere un'azione nel riquadro di script</span><span class="sxs-lookup"><span data-stu-id="f1c7e-168">To redo an action in the Script Pane</span></span>

<span data-ttu-id="f1c7e-169">Premere <kbd>CTRL</kbd>+<kbd>Y</kbd>. In alternativa, sulla barra degli strumenti fare clic sull'icona **Ripeti** oppure dal menu **Modifica** scegliere **Ripeti**.</span><span class="sxs-lookup"><span data-stu-id="f1c7e-169">Press <kbd>CTRL</kbd>+<kbd>Y</kbd> or, on the toolbar, click the **Redo** icon, or on the **Edit** menu, click **Redo**.</span></span>

## <a name="how-to-save-a-script"></a><span data-ttu-id="f1c7e-170">Come salvare uno script</span><span class="sxs-lookup"><span data-stu-id="f1c7e-170">How to save a script</span></span>

<span data-ttu-id="f1c7e-171">Accanto al nome dello script che non è stato ancora salvato dopo una modifica compare un asterisco.</span><span class="sxs-lookup"><span data-stu-id="f1c7e-171">An asterisk appears next to the script name to mark a file that hasn't been saved since it was changed.</span></span> <span data-ttu-id="f1c7e-172">L'asterisco sparirà dopo il salvataggio del file.</span><span class="sxs-lookup"><span data-stu-id="f1c7e-172">The asterisk disappears when the file is saved.</span></span>

### <a name="to-save-a-script"></a><span data-ttu-id="f1c7e-173">Per salvare uno script</span><span class="sxs-lookup"><span data-stu-id="f1c7e-173">To save a script</span></span>

<span data-ttu-id="f1c7e-174">Premere <kbd>CTRL</kbd>+<kbd>S</kbd>. In alternativa, sulla barra degli strumenti fare clic sull'icona **Salva** oppure dal menu **File** scegliere **Salva**.</span><span class="sxs-lookup"><span data-stu-id="f1c7e-174">Press <kbd>CTRL</kbd>+<kbd>S</kbd> or, on the toolbar, click the **Save** icon, or on the **File** menu, click **Save**.</span></span>

### <a name="to-save-and-name-a-script"></a><span data-ttu-id="f1c7e-175">Per salvare uno script e assegnargli un nome</span><span class="sxs-lookup"><span data-stu-id="f1c7e-175">To save and name a script</span></span>

1. <span data-ttu-id="f1c7e-176">Scegliere **Salva con nome** dal menu **File**.</span><span class="sxs-lookup"><span data-stu-id="f1c7e-176">On the **File** menu, click **Save As**.</span></span> <span data-ttu-id="f1c7e-177">Verrà visualizzata la finestra di dialogo **Salva con nome**.</span><span class="sxs-lookup"><span data-stu-id="f1c7e-177">The **Save As** dialog box will appear.</span></span>
2. <span data-ttu-id="f1c7e-178">Nella casella **Nome file** immettere un nome per il file.</span><span class="sxs-lookup"><span data-stu-id="f1c7e-178">In the **File name** box, enter a name for the file.</span></span>
3. <span data-ttu-id="f1c7e-179">Nella casella **Salva come** selezionare un tipo di file.</span><span class="sxs-lookup"><span data-stu-id="f1c7e-179">In the **Save as type** box, select a file type.</span></span> <span data-ttu-id="f1c7e-180">Ad esempio, nella casella **Tipo file** selezionare "Script di PowerShell (`*.ps1`)".</span><span class="sxs-lookup"><span data-stu-id="f1c7e-180">For example, in the **Save as type** box, select 'PowerShell Scripts (`*.ps1`)'.</span></span>
4. <span data-ttu-id="f1c7e-181">Fare clic su **Salva**.</span><span class="sxs-lookup"><span data-stu-id="f1c7e-181">Click **Save**.</span></span>

### <a name="to-save-a-script-in-ascii-encoding"></a><span data-ttu-id="f1c7e-182">Per salvare uno script nella codifica ASCII</span><span class="sxs-lookup"><span data-stu-id="f1c7e-182">To save a script in ASCII encoding</span></span>

<span data-ttu-id="f1c7e-183">Per impostazione predefinita, Windows PowerShell ISE salva i file di script (`.ps1`), i file di dati degli script (`.psd1`) e i file di modulo di script (`.psm1`) in formato Unicode (BigEndianUnicode).</span><span class="sxs-lookup"><span data-stu-id="f1c7e-183">By default, Windows PowerShell ISE saves new script files (`.ps1`), script data files (`.psd1`), and script module files (`.psm1`) as Unicode (BigEndianUnicode) by default.</span></span> <span data-ttu-id="f1c7e-184">Per salvare uno script in un'altra codifica, ad esempio ASCII (ANSI), usare i metodi **Save** o **SaveAs** sull'oggetto [$psISE.CurrentFile](object-model/the-ise-object-model-hierarchy.md).</span><span class="sxs-lookup"><span data-stu-id="f1c7e-184">To save a script in another encoding, such as ASCII (ANSI), use the **Save** or **SaveAs** methods on the [$psISE.CurrentFile](object-model/the-ise-object-model-hierarchy.md) object.</span></span>

<span data-ttu-id="f1c7e-185">Il comando che segue salva un nuovo script con il nome MyScript.ps1 nella codifica ASCII.</span><span class="sxs-lookup"><span data-stu-id="f1c7e-185">The following command saves a new script as MyScript.ps1 with ASCII encoding.</span></span>

```powershell
$psISE.CurrentFile.SaveAs("MyScript.ps1", [System.Text.Encoding]::ASCII)
```

<span data-ttu-id="f1c7e-186">Il comando che segue sostituisce il file di script corrente con un file con lo stesso nome, ma con codifica ASCII.</span><span class="sxs-lookup"><span data-stu-id="f1c7e-186">The following command replaces the current script file with a file with the same name, but with ASCII encoding.</span></span>

```powershell
$psISE.CurrentFile.Save([System.Text.Encoding]::ASCII)
```

<span data-ttu-id="f1c7e-187">Il comando seguente ottiene la codifica del file corrente.</span><span class="sxs-lookup"><span data-stu-id="f1c7e-187">The following command gets the encoding of the current file.</span></span>

```powershell
$psISE.CurrentFile.encoding
```

<span data-ttu-id="f1c7e-188">Windows PowerShell ISE supporta le opzioni di codifica seguenti: ASCII, BigEndianUnicode, Unicode, UTF32, UTF7, UTF8 e Default.</span><span class="sxs-lookup"><span data-stu-id="f1c7e-188">Windows PowerShell ISE supports the following encoding options: ASCII, BigEndianUnicode, Unicode, UTF32, UTF7, UTF8, and Default.</span></span> <span data-ttu-id="f1c7e-189">Il valore dell'opzione di codifica predefinita varia in base al sistema.</span><span class="sxs-lookup"><span data-stu-id="f1c7e-189">The value of the Default option varies with the system.</span></span>

<span data-ttu-id="f1c7e-190">Windows PowerShell ISE non modifica la codifica dei file script quando si usano i comandi Salva o Salva con nome.</span><span class="sxs-lookup"><span data-stu-id="f1c7e-190">Windows PowerShell ISE doesn't change the encoding of script files when you use the Save or Save As commands.</span></span>

## <a name="see-also"></a><span data-ttu-id="f1c7e-191">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="f1c7e-191">See Also</span></span>

- [<span data-ttu-id="f1c7e-192">Esplorazione di Windows PowerShell ISE</span><span class="sxs-lookup"><span data-stu-id="f1c7e-192">Exploring the Windows PowerShell ISE</span></span>](exploring-the-windows-powershell-ise.md)
