---
ms.date: 08/14/2018
keywords: powershell,cmdlet
title: Come scrivere ed eseguire script in Windows PowerShell ISE
ms.assetid: 62f916d9-b3a1-484a-bdfb-41f57112c22b
ms.openlocfilehash: 61db5e18f05e8e334cd9ba6dab2cf15dee7390cc
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MTE95
ms.contentlocale: it-IT
ms.lasthandoff: 12/14/2018
ms.locfileid: "53401464"
---
# <a name="how-to-write-and-run-scripts-in-the-windows-powershell-ise"></a><span data-ttu-id="4c152-103">Come scrivere ed eseguire script in Windows PowerShell ISE</span><span class="sxs-lookup"><span data-stu-id="4c152-103">How to Write and Run Scripts in the Windows PowerShell ISE</span></span>

<span data-ttu-id="4c152-104">Questo articolo descrive come creare, modificare, eseguire e salvare script nel riquadro Script.</span><span class="sxs-lookup"><span data-stu-id="4c152-104">This article describes how to create, edit, run, and save scripts in the Script Pane.</span></span>

## <a name="how-to-create-and-run-scripts"></a><span data-ttu-id="4c152-105">Come creare ed eseguire script</span><span class="sxs-lookup"><span data-stu-id="4c152-105">How to create and run scripts</span></span>

<span data-ttu-id="4c152-106">È possibile aprire e modificare i file di Windows PowerShell nel riquadro di script.</span><span class="sxs-lookup"><span data-stu-id="4c152-106">You can open and edit Windows PowerShell files in the Script Pane.</span></span> <span data-ttu-id="4c152-107">Tipi di file di particolare interesse in Windows PowerShell sono i file di script (con estensione PS1), i file di dati degli script (con estensione PSD1) e i file di modulo di script (con estensione PSM1).</span><span class="sxs-lookup"><span data-stu-id="4c152-107">Specific file types of interest in Windows PowerShell are script files (.ps1), script data files (.psd1), and script module files (.psm1).</span></span> <span data-ttu-id="4c152-108">In questi file per la visualizzazione della sintassi nell'editor del riquadro di script vengono utilizzati i colori.</span><span class="sxs-lookup"><span data-stu-id="4c152-108">These file types are syntax colored in the Script Pane editor.</span></span> <span data-ttu-id="4c152-109">Altri tipi di file comuni che è possibile aprire nel riquadro di script sono file di configurazione (con estensione ps1xml), file XML e file di testo.</span><span class="sxs-lookup"><span data-stu-id="4c152-109">Other common file types you may open in the Script Pane are configuration files (.ps1xml), XML files, and text files.</span></span>

> [!NOTE]
> <span data-ttu-id="4c152-110">I criteri di esecuzione di Windows PowerShell determinano se è possibile eseguire script e caricare profili e file di configurazione di Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="4c152-110">The Windows PowerShell execution policy determines whether you can run scripts and load Windows PowerShell profiles and configuration files.</span></span> <span data-ttu-id="4c152-111">I criteri di esecuzione predefiniti prevedono restrizioni e impediscono l'esecuzione di tutti gli script e il caricamento di profili.</span><span class="sxs-lookup"><span data-stu-id="4c152-111">The default execution policy, Restricted, prevents all scripts from running, and prevents loading profiles.</span></span> <span data-ttu-id="4c152-112">Per modificare i criteri di esecuzione in modo da consentire il caricamento e l'uso di profili, vedere [Set-ExecutionPolicy](/powershell/module/microsoft.powershell.security/set-executionpolicy) e [about_Signing](/powershell/module/microsoft.powershell.core/about/about_signing).</span><span class="sxs-lookup"><span data-stu-id="4c152-112">To change the execution policy to allow profiles to load and be used, see [Set-ExecutionPolicy](/powershell/module/microsoft.powershell.security/set-executionpolicy) and [about_Signing](/powershell/module/microsoft.powershell.core/about/about_signing).</span></span>

### <a name="to-create-a-new-script-file"></a><span data-ttu-id="4c152-113">Per creare un nuovo file di script</span><span class="sxs-lookup"><span data-stu-id="4c152-113">To create a new script file</span></span>

<span data-ttu-id="4c152-114">Sulla barra degli strumenti fare clic su **Nuovo** oppure scegliere **Nuovo** dal menu **File**.</span><span class="sxs-lookup"><span data-stu-id="4c152-114">On the toolbar, click **New**, or on the **File** menu, click **New**.</span></span> <span data-ttu-id="4c152-115">Il file creato viene visualizzato in una nuova scheda file nella scheda di PowerShell corrente. Tenere presente che le schede di PowerShell sono visibili solo se ne sono presenti più di una.</span><span class="sxs-lookup"><span data-stu-id="4c152-115">The created file appears in a new file tab under the current PowerShell tab. Remember that the PowerShell tabs are only visible when there are more than one.</span></span> <span data-ttu-id="4c152-116">Per impostazione predefinita viene creato un file di tipo script (con estensione ps1), ma è possibile salvarlo con un nuovo nome e un'altra estensione.</span><span class="sxs-lookup"><span data-stu-id="4c152-116">By default a file of type script (.ps1) is created, but it can be saved with a new name and extension.</span></span> <span data-ttu-id="4c152-117">Nella stessa scheda di PowerShell si possono creare più file di script.</span><span class="sxs-lookup"><span data-stu-id="4c152-117">Multiple script files can be created in the same PowerShell tab.</span></span>

### <a name="to-open-an-existing-script"></a><span data-ttu-id="4c152-118">Per aprire uno script esistente</span><span class="sxs-lookup"><span data-stu-id="4c152-118">To open an existing script</span></span>

<span data-ttu-id="4c152-119">Sulla barra degli strumenti fare clic su **Apri** o scegliere **Apri** dal menu **File**.</span><span class="sxs-lookup"><span data-stu-id="4c152-119">On the toolbar, click **Open**, or on the **File** menu, click **Open**.</span></span> <span data-ttu-id="4c152-120">Nella finestra di dialogo **Apri** selezionare il file da aprire.</span><span class="sxs-lookup"><span data-stu-id="4c152-120">In the **Open** dialog box, select the file you want to open.</span></span> <span data-ttu-id="4c152-121">Il file aperto viene visualizzato in una nuova scheda.</span><span class="sxs-lookup"><span data-stu-id="4c152-121">The opened file appears in a new tab.</span></span>

### <a name="to-close-a-script-tab"></a><span data-ttu-id="4c152-122">Per chiudere la scheda di uno script</span><span class="sxs-lookup"><span data-stu-id="4c152-122">To close a script tab</span></span>

<span data-ttu-id="4c152-123">Fare clic sull'icona **Chiudi** (X) della scheda del file che si vuole chiudere o selezionare il menu **File**e fare clic su **Chiudi**.</span><span class="sxs-lookup"><span data-stu-id="4c152-123">Click the **Close** icon (X) of the file tab you want to close or select the **File** menu and click **Close**.</span></span>

<span data-ttu-id="4c152-124">Se il file è stato modificato dall'ultimo salvataggio, viene chiesto se salvare le modifiche o ignorarle.</span><span class="sxs-lookup"><span data-stu-id="4c152-124">If the file has been altered since it was last saved, you're prompted to save or discard it.</span></span>

### <a name="to-display-the-file-path"></a><span data-ttu-id="4c152-125">Per visualizzare il percorso del file</span><span class="sxs-lookup"><span data-stu-id="4c152-125">To display the file path</span></span>

<span data-ttu-id="4c152-126">Nella scheda del file posizionare il puntatore del mouse sul nome del file.</span><span class="sxs-lookup"><span data-stu-id="4c152-126">On the file tab, point to the file name.</span></span> <span data-ttu-id="4c152-127">Il percorso completo del file di script appare in una descrizione comando.</span><span class="sxs-lookup"><span data-stu-id="4c152-127">The fully qualified path to the script file appears in a tooltip.</span></span>

### <a name="to-run-a-script"></a><span data-ttu-id="4c152-128">Per eseguire uno script</span><span class="sxs-lookup"><span data-stu-id="4c152-128">To run a script</span></span>

<span data-ttu-id="4c152-129">Sulla barra degli strumenti fare clic su **Esegui script** o scegliere **Esegui** dal menu **File**.</span><span class="sxs-lookup"><span data-stu-id="4c152-129">On the toolbar, click **Run Script**, or on the **File** menu, click **Run**.</span></span>

### <a name="to-run-a-portion-of-a-script"></a><span data-ttu-id="4c152-130">Per eseguire una parte di uno script</span><span class="sxs-lookup"><span data-stu-id="4c152-130">To run a portion of a script</span></span>

1. <span data-ttu-id="4c152-131">Nel riquadro di script selezionare una parte di uno script.</span><span class="sxs-lookup"><span data-stu-id="4c152-131">In the Script Pane, select a portion of a script.</span></span>
2. <span data-ttu-id="4c152-132">Sulla barra degli strumenti fare clic su **Esegui selezione** o scegliere **Esegui selezione** dal menu **File**.</span><span class="sxs-lookup"><span data-stu-id="4c152-132">On the **File** menu, click **Run Selection**, or on the toolbar, click **Run Selection**.</span></span>

### <a name="to-stop-a-running-script"></a><span data-ttu-id="4c152-133">Per arrestare l'esecuzione di uno script</span><span class="sxs-lookup"><span data-stu-id="4c152-133">To stop a running script</span></span>

<span data-ttu-id="4c152-134">È possibile arrestare uno script in esecuzione in diversi modi.</span><span class="sxs-lookup"><span data-stu-id="4c152-134">There are several ways to stop a running script.</span></span>

- <span data-ttu-id="4c152-135">Fare clic su **Arresta operazione** sulla barra degli strumenti</span><span class="sxs-lookup"><span data-stu-id="4c152-135">Click **Stop Operation** on the toolbar</span></span>
- <span data-ttu-id="4c152-136">Premere CTRL+INTERR</span><span class="sxs-lookup"><span data-stu-id="4c152-136">Press CTRL+BREAK</span></span>
- <span data-ttu-id="4c152-137">Selezionare il menu **File** e fare clic su **Arresta operazione**.</span><span class="sxs-lookup"><span data-stu-id="4c152-137">Select the **File** menu and click **Stop Operation**.</span></span>

<span data-ttu-id="4c152-138">È anche possibile premere **CTRL+C**, a meno che non sia attualmente selezionato del testo. In quel caso, **CTRL+C** corrisponderà alla funzione di copia del testo selezionato.</span><span class="sxs-lookup"><span data-stu-id="4c152-138">Pressing **CTRL+C** also works unless some text is currently selected, in which case **CTRL+C** maps to the copy function for the selected text.</span></span>

## <a name="how-to-write-and-edit-text-in-the-script-pane"></a><span data-ttu-id="4c152-139">Come scrivere e modificare testo nel riquadro di script</span><span class="sxs-lookup"><span data-stu-id="4c152-139">How to write and edit text in the Script Pane</span></span>

<span data-ttu-id="4c152-140">È possibile copiare, tagliare, incollare, trovare e sostituire testo nel riquadro Script.</span><span class="sxs-lookup"><span data-stu-id="4c152-140">You can copy, cut, paste, find, and replace text in the Script Pane.</span></span> <span data-ttu-id="4c152-141">È anche possibile annullare e ripetere l'ultima operazione eseguita.</span><span class="sxs-lookup"><span data-stu-id="4c152-141">You can also undo and redo the last action you just performed.</span></span> <span data-ttu-id="4c152-142">I tasti di scelta rapida per eseguire queste operazioni sono identici a quelli usati in tutte le applicazioni di Windows.</span><span class="sxs-lookup"><span data-stu-id="4c152-142">The keyboard shortcuts for these actions are the same shortcuts used for all Windows applications.</span></span>

### <a name="to-enter-text-in-the-script-pane"></a><span data-ttu-id="4c152-143">Per immettere testo nel riquadro di script</span><span class="sxs-lookup"><span data-stu-id="4c152-143">To enter text in the Script Pane</span></span>

1. <span data-ttu-id="4c152-144">Spostare il cursore sul riquadro di script facendo clic in un punto qualsiasi al suo interno o scegliendo **Vai al riquadro di script** dal menu **Visualizza**.</span><span class="sxs-lookup"><span data-stu-id="4c152-144">Move the cursor to the Script Pane by clicking anywhere in the Script Pane, or by clicking **Go to Script Pane** in the **View** menu.</span></span>
2. <span data-ttu-id="4c152-145">Creare uno script.</span><span class="sxs-lookup"><span data-stu-id="4c152-145">Create a script.</span></span> <span data-ttu-id="4c152-146">La colorazione della sintassi e la funzionalità di completamento tramite tasto TAB offrono un'esperienza di modifica più avanzata in Windows PowerShell ISE.</span><span class="sxs-lookup"><span data-stu-id="4c152-146">Syntax coloring and tab completion provide a richer editing experience in Windows PowerShell ISE.</span></span>
3. <span data-ttu-id="4c152-147">Per maggiori informazioni sull'uso di questa funzionalità, vedere [Come usare la funzionalità di completamento tramite TAB nel riquadro di script e nel riquadro della console](How-to-Use-Tab-Completion-in-the-Script-Pane-and-Console-Pane.md).</span><span class="sxs-lookup"><span data-stu-id="4c152-147">See [How to Use Tab Completion in the Script Pane and Console Pane](How-to-Use-Tab-Completion-in-the-Script-Pane-and-Console-Pane.md) for details about using the tab completion feature to help in typing.</span></span>

### <a name="to-find-text-in-the-script-pane"></a><span data-ttu-id="4c152-148">Per trovare testo nel riquadro di script</span><span class="sxs-lookup"><span data-stu-id="4c152-148">To find text in the Script Pane</span></span>

1. <span data-ttu-id="4c152-149">Per trovare testo in qualsiasi punto, premere **CTRL+F** o scegliere **Trova nello script** dal menu **Modifica**.</span><span class="sxs-lookup"><span data-stu-id="4c152-149">To find text anywhere, press **CTRL+F** or, on the **Edit** menu, click **Find in Script**.</span></span>
2. <span data-ttu-id="4c152-150">Per trovare testo dopo il cursore, premere **F3** o scegliere **Trova successivo nello script** dal menu **Modifica**.</span><span class="sxs-lookup"><span data-stu-id="4c152-150">To find text after the cursor, press **F3** or, on the **Edit** menu, click **Find Next in Script**.</span></span>
3. <span data-ttu-id="4c152-151">Per trovare testo prima del cursore, premere **MAIUSC+F3** o scegliere **Trova precedente nello script** dal menu **Modifica**.</span><span class="sxs-lookup"><span data-stu-id="4c152-151">To find text before the cursor, press **SHIFT+F3** or, on the **Edit** menu, click **Find Previous in Script**.</span></span>

### <a name="to-find-and-replace-text-in-the-script-pane"></a><span data-ttu-id="4c152-152">Per trovare e sostituire testo nel riquadro di script</span><span class="sxs-lookup"><span data-stu-id="4c152-152">To find and replace text in the Script Pane</span></span>

<span data-ttu-id="4c152-153">Premere **CTRL+H** o scegliere **Sostituisci nello script** dal menu **Modifica**.</span><span class="sxs-lookup"><span data-stu-id="4c152-153">Press **CTRL+H** or, on the **Edit** menu, click **Replace in Script**.</span></span> <span data-ttu-id="4c152-154">Immettere il testo che si vuole trovare e il testo sostitutivo e quindi premere **INVIO**.</span><span class="sxs-lookup"><span data-stu-id="4c152-154">Enter the text you want to find and the replacement text, then press **ENTER**.</span></span>

### <a name="to-go-to-a-particular-line-of-text-in-the-script-pane"></a><span data-ttu-id="4c152-155">Per passare a una specifica riga di testo nel riquadro di script</span><span class="sxs-lookup"><span data-stu-id="4c152-155">To go to a particular line of text in the Script Pane</span></span>

1. <span data-ttu-id="4c152-156">Nel riquadro di script premere **CTRL+G** o scegliere **Vai alla riga** dal menu **Modifica**.</span><span class="sxs-lookup"><span data-stu-id="4c152-156">In the Script Pane, press **CTRL+G** or, on the **Edit** menu, click **Go to Line**.</span></span>

2. <span data-ttu-id="4c152-157">Immettere un numero di riga.</span><span class="sxs-lookup"><span data-stu-id="4c152-157">Enter a line number.</span></span>

### <a name="to-copy-text-in-the-script-pane"></a><span data-ttu-id="4c152-158">Per copiare testo nel riquadro di script</span><span class="sxs-lookup"><span data-stu-id="4c152-158">To copy text in the Script Pane</span></span>

1. <span data-ttu-id="4c152-159">Nel riquadro di script selezionare il testo da copiare.</span><span class="sxs-lookup"><span data-stu-id="4c152-159">In the Script Pane, select the text that you want to copy.</span></span>

2. <span data-ttu-id="4c152-160">Premere **CTRL+C**, fare clic sull'icona **Copia** sulla barra degli strumenti o scegliere **Copia** dal menu **Modifica**.</span><span class="sxs-lookup"><span data-stu-id="4c152-160">Press **CTRL+C** or, on the toolbar, click the **Copy** icon, or on the **Edit** menu, click **Copy**.</span></span>

### <a name="to-cut-text-in-the-script-pane"></a><span data-ttu-id="4c152-161">Per tagliare testo nel riquadro di script</span><span class="sxs-lookup"><span data-stu-id="4c152-161">To cut text in the Script Pane</span></span>

1. <span data-ttu-id="4c152-162">Nel riquadro di script selezionare il testo da tagliare.</span><span class="sxs-lookup"><span data-stu-id="4c152-162">In the Script Pane, select the text that you want to cut.</span></span>
2. <span data-ttu-id="4c152-163">Premere **CTRL+X**, fare clic sull'icona **Taglia** sulla barra degli strumenti o scegliere **Taglia** dal menu **Modifica**.</span><span class="sxs-lookup"><span data-stu-id="4c152-163">Press **CTRL+X** or, on the toolbar, click the **Cut** icon, or on the **Edit** menu, click **Cut**.</span></span>

### <a name="to-paste-text-into-the-script-pane"></a><span data-ttu-id="4c152-164">Per incollare testo nel riquadro di script</span><span class="sxs-lookup"><span data-stu-id="4c152-164">To paste text into the Script Pane</span></span>

<span data-ttu-id="4c152-165">Premere **CTRL+V**, fare clic sull'icona **Incolla** sulla barra degli strumenti o scegliere **Incolla** dal menu **Modifica**.</span><span class="sxs-lookup"><span data-stu-id="4c152-165">Press **CTRL+V** or, on the toolbar, click the **Paste** icon, or on the **Edit** menu, click **Paste**.</span></span>

### <a name="to-undo-an-action-in-the-script-pane"></a><span data-ttu-id="4c152-166">Per annullare un'azione nel riquadro di script</span><span class="sxs-lookup"><span data-stu-id="4c152-166">To undo an action in the Script Pane</span></span>

<span data-ttu-id="4c152-167">Premere **CTRL+Z**, fare clic sull'icona **Annulla** sulla barra degli strumenti o scegliere **Annulla** dal menu **Modifica**.</span><span class="sxs-lookup"><span data-stu-id="4c152-167">Press **CTRL+Z** or, on the toolbar, click the **Undo** icon, or on the **Edit** menu, click **Undo**.</span></span>

### <a name="to-redo-an-action-in-the-script-pane"></a><span data-ttu-id="4c152-168">Per ripetere un'azione nel riquadro di script</span><span class="sxs-lookup"><span data-stu-id="4c152-168">To redo an action in the Script Pane</span></span>

<span data-ttu-id="4c152-169">Premere **CTRL+Y**, fare clic sull'icona **Ripeti** sulla barra degli strumenti o scegliere **Ripeti** dal menu **Modifica**.</span><span class="sxs-lookup"><span data-stu-id="4c152-169">Press **CTRL+Y** or, on the toolbar, click the **Redo** icon, or on the **Edit** menu, click **Redo**.</span></span>

## <a name="how-to-save-a-script"></a><span data-ttu-id="4c152-170">Come salvare uno script</span><span class="sxs-lookup"><span data-stu-id="4c152-170">How to save a script</span></span>

<span data-ttu-id="4c152-171">Accanto al nome dello script che non è stato ancora salvato dopo una modifica compare un asterisco.</span><span class="sxs-lookup"><span data-stu-id="4c152-171">An asterisk appears next to the script name to mark a file that hasn't been saved since it was changed.</span></span> <span data-ttu-id="4c152-172">L'asterisco sparirà dopo il salvataggio del file.</span><span class="sxs-lookup"><span data-stu-id="4c152-172">The asterisk disappears when the file is saved.</span></span>

### <a name="to-save-a-script"></a><span data-ttu-id="4c152-173">Per salvare uno script</span><span class="sxs-lookup"><span data-stu-id="4c152-173">To save a script</span></span>

<span data-ttu-id="4c152-174">Premere **CTRL+S**, fare clic sull'icona **Salva** sulla barra degli strumenti o scegliere **Salva** dal menu **File**.</span><span class="sxs-lookup"><span data-stu-id="4c152-174">Press **CTRL+S** or, on the toolbar, click the **Save** icon, or on the **File** menu, click **Save**.</span></span>

### <a name="to-save-and-name-a-script"></a><span data-ttu-id="4c152-175">Per salvare uno script e assegnargli un nome</span><span class="sxs-lookup"><span data-stu-id="4c152-175">To save and name a script</span></span>

1. <span data-ttu-id="4c152-176">Scegliere **Salva con nome** dal menu **File**.</span><span class="sxs-lookup"><span data-stu-id="4c152-176">On the **File** menu, click **Save As**.</span></span> <span data-ttu-id="4c152-177">Verrà visualizzata la finestra di dialogo **Salva con nome**.</span><span class="sxs-lookup"><span data-stu-id="4c152-177">The **Save As** dialog box will appear.</span></span>
2. <span data-ttu-id="4c152-178">Nella casella **Nome file** immettere un nome per il file.</span><span class="sxs-lookup"><span data-stu-id="4c152-178">In the **File name** box, enter a name for the file.</span></span>
3. <span data-ttu-id="4c152-179">Nella casella **Salva come** selezionare un tipo di file.</span><span class="sxs-lookup"><span data-stu-id="4c152-179">In the **Save as type** box, select a file type.</span></span> <span data-ttu-id="4c152-180">Ad esempio, nella casella **Tipo file** selezionare "Script di PowerShell (\*.ps1)".</span><span class="sxs-lookup"><span data-stu-id="4c152-180">For example, in the **Save as type** box, select 'PowerShell Scripts (\*.ps1)'.</span></span>
4. <span data-ttu-id="4c152-181">Fare clic su **Salva**.</span><span class="sxs-lookup"><span data-stu-id="4c152-181">Click **Save**.</span></span>

### <a name="to-save-a-script-in-ascii-encoding"></a><span data-ttu-id="4c152-182">Per salvare uno script nella codifica ASCII</span><span class="sxs-lookup"><span data-stu-id="4c152-182">To save a script in ASCII encoding</span></span>

<span data-ttu-id="4c152-183">Per impostazione predefinita, Windows PowerShell ISE salva i nuovi file di script (con estensione PS1), i file di dati di script (con estensione PSD1) e i file di modulo di script (con estensione PSM1) in formato Unicode (BigEndianUnicode). Â Per salvare uno script in un'altra codifica, ad esempio ASCII (ANSI), utilizzare i metodi **Save** o **SaveAs** nell’oggetto [$psISE.CurrentFile](object-model/the-ise-object-model-hierarchy.md).</span><span class="sxs-lookup"><span data-stu-id="4c152-183">By default, Windows PowerShell ISE saves new script files (.ps1), script data files (.psd1), and script module files (.psm1) as Unicode (BigEndianUnicode) by default.Â To save a script in another encoding, such as ASCII (ANSI), use the **Save** or **SaveAs** methods on the [$psISE.CurrentFile](object-model/the-ise-object-model-hierarchy.md) object.</span></span>

<span data-ttu-id="4c152-184">Il comando che segue salva un nuovo script con il nome MyScript.ps1 nella codifica ASCII.</span><span class="sxs-lookup"><span data-stu-id="4c152-184">The following command saves a new script as MyScript.ps1 with ASCII encoding.</span></span>

```powershell
$psISE.CurrentFile.SaveAs("MyScript.ps1", [System.Text.Encoding]::ASCII)
```

<span data-ttu-id="4c152-185">Il comando che segue sostituisce il file di script corrente con un file con lo stesso nome, ma con codifica ASCII.</span><span class="sxs-lookup"><span data-stu-id="4c152-185">The following command replaces the current script file with a file with the same name, but with ASCII encoding.</span></span>

```powershell
$psISE.CurrentFile.Save([System.Text.Encoding]::ASCII)
```

<span data-ttu-id="4c152-186">Il comando seguente ottiene la codifica del file corrente.</span><span class="sxs-lookup"><span data-stu-id="4c152-186">The following command gets the encoding of the current file.</span></span>

```powershell
$psISE.CurrentFile.encoding
```

<span data-ttu-id="4c152-187">Windows PowerShell ISE supporta le opzioni di codifica seguenti: ASCII, BigEndianUnicode, Unicode, UTF32, UTF7, UTF8 e predefinita.</span><span class="sxs-lookup"><span data-stu-id="4c152-187">Windows PowerShell ISE supports the following encoding options: ASCII, BigEndianUnicode, Unicode, UTF32, UTF7, UTF8, and Default.</span></span> <span data-ttu-id="4c152-188">Il valore dell'opzione di codifica predefinita varia in base al sistema.</span><span class="sxs-lookup"><span data-stu-id="4c152-188">The value of the Default option varies with the system.</span></span>

<span data-ttu-id="4c152-189">Windows PowerShell ISE non modifica la codifica dei file script quando si usano i comandi Salva o Salva con nome.</span><span class="sxs-lookup"><span data-stu-id="4c152-189">Windows PowerShell ISE doesn't change the encoding of script files when you use the Save or Save As commands.</span></span>

## <a name="see-also"></a><span data-ttu-id="4c152-190">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="4c152-190">See Also</span></span>

- [<span data-ttu-id="4c152-191">Esplorazione di Windows PowerShell ISE</span><span class="sxs-lookup"><span data-stu-id="4c152-191">Exploring the Windows PowerShell ISE</span></span>](../../getting-started/fundamental/exploring-the-windows-powershell-ise.md)
